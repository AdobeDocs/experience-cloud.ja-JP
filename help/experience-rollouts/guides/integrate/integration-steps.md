---
title: 統合ステップ
description: アプリケーションタイプの統合手順に従って、Adobe Experience Rolloutsをweb サービス、web アプリ、モバイルアプリ、デスクトップアプリケーションに接続します。
source-git-commit: b82520eebe0070b5f76e0f7daeb2bb79a4bccca0
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 3%

---


# 統合ステップ {#integration-steps}

アプリケーションの種類に一致する統合パスを選択します。

## Web サービス {#web-services}

バックエンドサービスは、サーバーサイドのSDKを使用して統合されます。 テクノロジースタックに最適なSDKの選定：

**Java**

セットアップ、依存関係の設定、および初期化については、[Java SDK統合ガイド &#x200B;](../sdk-releases/java/java-sdk-integration-guide.md)に従ってください。

**Node.js**

セットアップと初期化については、[Node.js SDK統合ガイド &#x200B;](../sdk-releases/nodejs/nodejs-sdk-integration-guide.md)に従ってください。

**その他の言語**

お使いのスタックが上記にリストされていない場合は、**Feature API V3**&#x200B;と直接統合してください（このガイドのFeature API セクションを参照）。 ガイダンスが必要な場合は、Experience Rollouts サポートにお問い合わせください。

## webおよびモバイルアプリケーション {#web-mobile}

Webおよびモバイルアプリケーションは&#x200B;**Feature API V3**&#x200B;を呼び出して、現在のユーザーの機能フラグを取得し、アプリケーションに条件付きロジックを適用します。

完全なAPI リファレンスについては、このガイドの機能API セクションの&#x200B;**GET機能API V3**&#x200B;を参照してください。

## デスクトップアプリケーション {#desktop}

デスクトップアプリケーションは、**機能API V2**&#x200B;を呼び出して、機能フラグを取得します。

完全なAPI リファレンスについては、このガイドの機能API セクションの&#x200B;**GET機能API V2**&#x200B;を参照してください。

>[!IMPORTANT]
>
>デスクトップクライアントは、API応答のTTL値を尊重し、APIが使用できないときに適切なエラー処理を実装する必要があります。 要件については、[&#x200B; デスクトップアプリケーション &#x200B;](desktop-applications.md)を参照してください。

## 関連トピック {#see-also}

* [スタートアップガイド](startup-guide.md)
* [SDK](sdks.md)
* [Web サービス](web-services.md)
* [デスクトップアプリケーション](desktop-applications.md)
