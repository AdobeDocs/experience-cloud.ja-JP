---
title: Node.js SDK統合ガイド
description: Experience Rollouts Node.js SDKをバックエンドサービスに統合して、機能フラグを取得および評価する方法について説明します。
exl-id: 063829fe-6933-45ff-add4-285ca7391778
source-git-commit: 2a946868f58e25f8aafbf3ccfcf6571e7d0d8d20
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 2%

---

# Node.js SDK統合ガイド {#nodejs-sdk-integration-guide}

Experience Rollouts Node.js SDKは、Node.js サービス用のサーバーサイドライブラリです。 機能フラグデータをローカルにキャッシュし、あらゆるリクエストで同期API呼び出しなしでフラグを評価します。

>[!NOTE]
>
>Node.js SDKは、サーバーサイドでのみ使用できるように設計されています。 クライアントサイド web アプリケーションの場合は、web SDKを使用します。 Web SDKのドキュメントは現在準備中であり、近日中に公開される予定です。

## 前提条件 {#prerequisites}

Node.js SDKを統合する前に、次のことを確認してください。

* Node.js サーバーサイドアプリケーション
* Adobe Developer Consoleを通じて取得した&#x200B;**API キー**&#x200B;および&#x200B;**サービストークン** — Experience Rollouts サポートに連絡して、クライアント IDを許可リストに加えるしてください
* Experience Rollouts コンソールに登録されている&#x200B;**アプリケーションクライアント ID**&#x200B;は、[&#x200B; アプリケーションのオンボーディング &#x200B;](../../applications/onboard-your-application.md)を参照してください。

## SDK のインストール {#install}

プロジェクトの`package.json`にSDKを追加します。

```json
"@floodgate/fg-client-sdk": "~1.0.10"
```

次に、コードに必要なコードを入力します。

```javascript
const { floodgateClient } = require('@floodgate/fg-client-sdk');
```

## SDKの初期化 {#initialize}

アプリケーションの起動時に`createInstance()`を1回呼び出します：

```javascript
floodgateClient.createInstance(
  {
    adobeIoApiKey: "<YOUR_API_KEY>",
    clientIds: ["<CLIENT_ID_1>", "<CLIENT_ID_2>"],
    env: "PRD",    // Use "STG" for Stage
    featureRequestHttpParams: {
      timeout: 60 * 1000  // Optional: request timeout in ms
    },
    ingestAnalyticsHttpParams: {
      timeout: 5 * 1000   // Optional: analytics timeout in ms
    }
  },
  function(cb) {
    // Fetch a fresh service token from IMS and pass it in the callback
    cb(null, SERVICE_TOKEN);
  },
  function() {
    return true;  // Return false to disable analytics
  },
  function(response) {
    // Called when the SDK initializes successfully
    console.log("SDK initialized");
  },
  function(err) {
    // Called if initialization fails
    console.error("SDK init error:", err);
  }
);
```

## 機能フラグの取得 {#retrieve-features}

機能フラグは、コールバックで非同期的に返されます。 ユーザーコンテキストに基づいて適切な方法を選択します。

### 認証済みユーザー {#authenticated-user}

```javascript
floodgateClient.getFeatures(
  {
    userAccessToken: "<USER_ACCESS_TOKEN>",
    visitorId: "<VISITOR_ID>",
    clientId1: "<CLIENT_ID>",
    meta: true
  },
  function(err, features) {
    if (err) {
      // Handle error and serve default experience
      return;
    }
    const isEnabled = floodgateClient.isFeatureEnabled(features, "MY_FEATURE_FLAG");
    // Serve experience based on isEnabled
  }
);
```

### 匿名ユーザー {#anonymous-user}

ユーザーアクセストークンが使用できない場合は、リリースフラグを使用するか、トークンを省略してフルロールアウトリリースを受け取ります。

```javascript
floodgateClient.getFeatures(
  {
    releaseFlag: "<RELEASE_FLAG>",
    visitorId: "<VISITOR_ID>",
    clientId1: "<CLIENT_ID>",
    meta: false
  },
  callback
);
```

### デフォルトのフルロールアウトリリース {#default-releases}

アクセストークンもリリースフラグも指定されていない場合、SDKは&#x200B;**フルロールアウト**&#x200B;または&#x200B;**ベースライン**&#x200B;状態で機能を返します。

```javascript
floodgateClient.getFeatures(
  {
    clientId1: "<CLIENT_ID>",
    visitorId: "<VISITOR_ID>",
    meta: false
  },
  callback
);
```

## 機能が有効になっているかどうかを確認する {#check-feature}

```javascript
const isEnabled = floodgateClient.isFeatureEnabled(features, "MY_FEATURE_FLAG");

if (isEnabled) {
  // Serve the new experience
} else {
  // Serve the default experience
}
```

## デバッグログを有効にする {#debug-logging}

詳細なSDK ログを有効にするには、`createInstance()`の呼び出し時にデバッグレベルのロガーインスタンスを渡します。

```javascript
const bunyan = require('bunyan');
const logger = bunyan.createLogger({ name: "fg", sourceType: "SDK", level: "debug" });

floodgateClient.createInstance(
  { ..., log: logger },
  ...
);
```

## 関連トピック {#see-also}

* [Node.js SDK リリースノート](nodejs-sdk-release-notes.md)
* [SDK](../../integrate/sdks.md)
* [統合ステップ](../../integrate/integration-steps.md)
