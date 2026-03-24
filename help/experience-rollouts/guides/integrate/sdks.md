---
title: SDK
description: Adobe Experience RolloutsのSDK アーキテクチャと、JavaおよびNode.jsで使用可能なSDKについて説明します。
source-git-commit: b82520eebe0070b5f76e0f7daeb2bb79a4bccca0
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 2%

---


# SDK {#sdks}

Experience Rolloutsは、バックエンドサービス統合用のサーバーサイド SDKを提供します。 このページでは、SDKのアーキテクチャと使用可能なオプションについて説明します。

## SDK アーキテクチャ {#architecture}

すべてのExperience Rollouts SDKは、同じコアアーキテクチャを共有しています。

* **Initialization** — SDKは、シングルトン オブジェクトを返す`createInstance()`呼び出しを介して設定されます。
* **機能の取得** — `getFeatures()` メソッドは、SDKから機能フラグデータを取得します。
* **Caching** — SDKは、Experience Rollouts サービスからの応答をキャッシュします。 キャッシュマネージャーは、設定可能なポーリング間隔（TTL）でキャッシュを更新します。
* **エラー処理** — サービスが503を返す場合、Cache Managerは既存のキャッシュ データを保持し、機能フラグ評価を引き続き提供します。 前回の呼び出し（304）以降にデータが変更されていない場合、キャッシュは更新されません。

## 前提条件 {#prerequisites}

SDKを統合する前に、以下を確認してください。

1. **アプリケーション ID** — Experience Rollouts コンソールでオンボーディングされた各アプリケーションのクライアント ID。
2. **サービストークン** — SDKがバックグラウンドでエクスペリエンスロールアウト APIを呼び出すために使用します。
3. **API キー** — API認証用のサービストークンと共に使用されます。

## 利用可能なSDK {#available-sdks}

### Java SDK {#java-sdk}

Java SDKは、Mavenを介して配布されます。 プロジェクトの`pom.xml`に依存関係を追加して統合します。 Spring ベースのアプリケーションの場合、Maven依存関係は、アプリケーションが完全に読み込まれる前に、SDK キャッシュを自動的に設定します。

Java SDKの主な仕様：

* **サポートされているJDK:** JDK 8以降
* **キャッシュできないクライアント：** SDK バージョン 0.8以降でサポートされています。 キャッシュできないクライアントの場合、`getFeature()`はキャッシュから読み取る代わりにライブ API呼び出しを行います。 SDKはバックグラウンドでポーリングを続け、クライアントがキャッシュ可能になった場合にキャッシュベースのサービスに切り替えます。

設定手順については、[Java SDK統合ガイド &#x200B;](../sdk-releases/java/java-sdk-integration-guide.md)を参照してください。

### Node.js SDK {#nodejs-sdk}

Node.js SDKは、npmを介して配布されます。

設定手順については、[Node.js SDK統合ガイド &#x200B;](../sdk-releases/nodejs/nodejs-sdk-integration-guide.md)を参照してください。

## SDKとREST APIの選択 {#sdk-vs-api}

| シナリオ | レコメンデーション |
|---|---|
| バックエンド JavaまたはNode.js サービス | 自動キャッシュと簡素化された統合に適切なSDKを使用する |
| その他のバックエンド言語 | Feature API V3を直接使用する – このガイドのFeature API セクションを参照してください |
| webまたはモバイルアプリケーション | Feature API V3を直接使用する – このガイドのFeature API セクションを参照してください |
| デスクトップアプリケーション | Feature API V2を直接使用する – このガイドのFeature API セクションを参照してください |

## 関連トピック {#see-also}

* [Web サービス](web-services.md)
* [統合ステップ](integration-steps.md)
* [Java SDK統合ガイド](../sdk-releases/java/java-sdk-integration-guide.md)
* [Node.js SDK統合ガイド](../sdk-releases/nodejs/nodejs-sdk-integration-guide.md)
