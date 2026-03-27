---
title: Java SDK統合ガイド
description: エクスペリエンスロールアウト Java SDKをバックエンドサービスに統合して、機能フラグを取得および評価する方法について説明します。
exl-id: 7c12bd6c-1883-4f1c-985f-a2b0432e61ce
source-git-commit: 2a946868f58e25f8aafbf3ccfcf6571e7d0d8d20
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 2%

---

# Java SDK統合ガイド {#java-sdk-integration-guide}

Experience Rollouts Java SDKは、機能フラグデータをローカルにキャッシュし、すべてのリクエストで同期API呼び出しなしでフラグを評価するサーバーサイドライブラリです。 このガイドでは、現在のSDK（4.x）について説明します。

## 前提条件 {#prerequisites}

Java SDKを統合する前に、次のことを確認してください。

* JDK 11以降（SDK バージョン 3.0.0以降で必要。以前のバージョンはJDK 8以降をサポート）
* Maven ベースのビルドシステム
* Adobe Developer Console プロジェクトの&#x200B;**API キー**&#x200B;および&#x200B;**サービストークン**&#x200B;のクライアント ID — Experience Rollouts サポートに連絡して、クライアント IDを許可リストに加えるしてください
* Experience Rollouts コンソールに登録されている&#x200B;**アプリケーションクライアント ID**&#x200B;は、[&#x200B; アプリケーションのオンボーディング &#x200B;](../../applications/onboard-your-application.md)を参照してください。

## Maven依存関係の追加 {#maven-dependency}

エクスペリエンスのロールアウト Java SDKをプロジェクトの`pom.xml`に追加します。

```xml
<dependency>
  <groupId>com.adobe.cloudtech</groupId>
  <artifactId>fg-client-sdk</artifactId>
  <version>4.0.6</version>
</dependency>
```

## SDKの初期化 {#initialize}

SDKは、`FloodgateClient.createInstance()`を使用してアプリケーションの起動時に1回初期化されます。 このメソッドは、設定ビルダーで構築した`FloodgateConfiguration` オブジェクトを受け取ります。

### サービストークンのコールバックを実装する {#service-token-callback}

SDKでは、コールバックインターフェイスを使用して、実行時に新しいサービストークンを取得します。

```java
private class FgConfigCallBack implements FGConfigBaseCallBack {

  @Override
  public String getIMSServiceToken() {
    // Fetch and return a valid service token
  }

  @Override
  public boolean isAnalyticsEnabled() {
    return false; // Set to true to enable analytics
  }
}
```

### 設定オブジェクトの作成 {#configuration}

SDKを設定するには、設定ビルダーを使用します。

```java
FloodgateConfiguration configuration = FloodgateConfiguration.FloodgateConfigurationBuilder
    .aFloodgateConfiguration(
        FgEnv.PRD,                   // Use FgEnv.STG for Stage
        "<YOUR_API_KEY>",
        Set.of("<CLIENT_ID_1>", "<CLIENT_ID_2>"),
        new FgConfigCallBack(),
        CallType.ASYNC
    )
    .withRetryPolicy(retryPolicy)    // Optional: defaults to 5 retries, 10s interval
    .build();
```

ステージ環境には`FgEnv.STG`を、実稼動環境には`FgEnv.PRD`を使用します。

### クライアントインスタンスの作成 {#client-instance}

```java
FloodgateClient fgClient = FloodgateClient.createInstance(configuration);
```

## 機能フラグの取得 {#retrieve-features}

### 認証済みユーザー {#authenticated-user}

IMS アクセストークンを使用して、現在のユーザーの機能フラグを取得します。

```java
GetFeatureRequest request = GetFeatureRequestBuilder
    .aGetFeatureRequest("<CLIENT_ID>")
    .withAccessToken("<USER_ACCESS_TOKEN>")
    .withContext(context)
    .build();

FeaturesResponse[] features = fgClient.getFeatures(request);
```

### 匿名ユーザー {#anonymous-user}

未認証のユーザーの場合は、訪問者IDとサービストークンを渡します。

```java
GetFeatureRequest request = GetFeatureRequestBuilder
    .aGetFeatureRequest("<CLIENT_ID>")
    .withServiceToken("<SERVICE_TOKEN>")
    .withVisitorId("<VISITOR_ID>")
    .withContext(context)
    .build();

FeaturesResponse[] features = fgClient.getFeatures(request);
```

### 特定の機能フラグまたはリリースの取得 {#specific-feature}

キーで単一の機能フラグを取得するには：

```java
GetFeatureRequest request = GetFeatureRequestBuilder
    .aGetFeatureRequest("<CLIENT_ID>")
    .withAccessToken("<ACCESS_TOKEN>")
    .withFeatureKey("<FEATURE_KEY>")
    .build();
```

リリースキーで取得するには、`.withFeatureKey()`を`.withReleaseKey()`に置き換えます。

## 機能が有効になっているかどうかを確認する {#check-feature}

```java
boolean isEnabled = FloodgateClient.isFeatureEnabled(features, "MY_FEATURE_FLAG");

if (isEnabled) {
  // Serve the new experience
} else {
  // Serve the default experience
}
```

リリースベースのチェックの場合：

```java
boolean isEnabled = FloodgateClient.isFeatureEnabled(features, "MY_RELEASE", "MY_FEATURE_FLAG");
```

## キャッシュ管理 {#cache-management}

SDKは、機能フラグデータをキャッシュし、コンソールのアプリケーションごとに設定されたポーリング間隔で更新します。 オンデマンドキャッシュの更新をトリガーするには：

```java
fgClient.refreshClientCache("<CLIENT_ID>");
```

### キャッシュできないクライアント {#non-cacheable}

キャッシュできないクライアントの場合、`getFeature()`は毎回ライブ API呼び出しを行います。 SDKはバックグラウンドポーリングを継続し、クライアントがキャッシュ可能になるとキャッシュベースのサービスに切り替えます。 SDK バージョン 0.8以降でサポートされています。

## 設定オプション {#configuration-options}

ビルダーでは、次のオプションの設定方法を使用できます。

| オプション | メソッド | 説明 |
|---|---|---|
| 常にキャッシュを使用 | `.alwaysCache()` | APIからのキャッシュ応答を回避します。オーディエンスルールのないフラグに使用します。 |
| キャッシュを無効にする | `.neverCache()` | デフォルトのキャッシュを無効にします。カスタムキャッシュの更新ロジックに便利です |
| カスタム HTTP クライアント | `.withHttpClient(client)` | 独自のHTTP クライアントを使用 |
| カスタムエグゼキュータ | `.withScheduledExecutorService(executor)` | バックグラウンドポーリングに独自のスケジュール済みエグゼクターを使用する |
| コントロール母集団を含める | `.includeControlGroup()` | 機能応答のコントロール グループ データを返します |

## エラーの処理 {#error-handling}

SDKの例外を検出するために`getFeatures()`件の呼び出しをラップ：

```java
try {
  features = fgClient.getFeatures(request);
} catch (FgClientException e) {
  int statusCode = e.getStatusCode();
  // Handle error and serve default experience
} catch (FgInitException e) {
  e.printStackTrace();
}
```

## 関連トピック {#see-also}

* [Java SDK リリースノート](java-sdk-release-notes.md)
* [SDK](../../integrate/sdks.md)
* [統合ステップ](../../integrate/integration-steps.md)
