---
title: SDK
description: Adobe Experience RolloutsのSDK アーキテクチャと、Androidで利用できるモバイル SDK拡張機能について説明します。
hide: true
exl-id: 110a440d-b52a-4e1e-a94f-86f9741a223a
source-git-commit: 12032cbed45e694a3f25f16afe80308b3eb82924
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 3%

---

# SDK {#sdks}

Experience Rolloutsには、機能フラグをアプリケーションに統合するためのSDKが用意されています。 このページでは、SDKのアーキテクチャと使用可能なオプションについて説明します。

## SDK アーキテクチャ {#architecture}

すべてのExperience Rollouts SDKは、同じコアアーキテクチャを共有しています。

* **Initialization** — SDKは起動時に設定され、Experience Rollouts サービスに登録されます。
* **機能の取得** — SDKは機能フラグデータを取得し、フラグをローカルで評価します。
* **キャッシュ** — SDKは機能フラグデータをキャッシュし、設定可能なポーリング間隔（TTL）で更新します。
* **エラー処理** — サービスが利用できない場合、SDKは引き続きローカルキャッシュから機能フラグ評価を提供します。

## 利用可能なSDK {#available-sdks}

### Android拡張機能 {#android-extension}

AndroidのExperience Rollout拡張機能は、Adobe Experience Platform Mobile SDKと統合されています。

設定手順については、[Android拡張機能の統合ガイド &#x200B;](../sdk-releases/android/android-extension-integration-guide.md)を参照してください。

>[!NOTE]
>
>webやその他のモバイルプラットフォーム用のAdobe SDKオプションも準備中であり、近日中に提供開始予定です。 早期アクセスガイダンスについては、Adobe担当者にお問い合わせください。

## 関連トピック {#see-also}

* [Android拡張機能の統合ガイド](../sdk-releases/android/android-extension-integration-guide.md)
* [Web サービス](web-services.md)
* [統合ステップ](integration-steps.md)

<!-- -->
