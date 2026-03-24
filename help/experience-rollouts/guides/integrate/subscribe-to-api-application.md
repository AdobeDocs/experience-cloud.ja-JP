---
title: Adobe Developer ConsoleでAPI アプリケーションを購読する
description: Adobe Developer Consoleを通じてExperience Rollouts APIにアプリケーションを登録し、機能フラグエンドポイントを呼び出す方法について説明します。
source-git-commit: 120a2ea34682c878aaf6f6cb75504a8704d10e3d
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 3%

---


# Adobe Developer ConsoleでAPI アプリケーションを購読する {#subscribe-to-api}

アプリケーションからExperience Rollouts APIを呼び出すには、[Adobe Developer Console](https://developer.adobe.com/console)を通じてそれを購読する必要があります。 これにより、エクスペリエンスロールアウトが呼び出し元の識別に使用するクライアント IDがアプリケーションに付与されます。

## 前提条件 {#prerequisites}

購読する前に、以下を確認してください。

* アプリケーションはExperience Rollouts コンソールでオンボーディングされます。[ アプリケーションのオンボーディング ](../applications/onboard-your-application.md)を参照してください。
* お客様の組織のAdobe Developer Consoleにアクセスできます

## Experience Rollouts APIの購入 {#subscribe}

Experience Rollouts APIにアプリケーションを登録するには、次の手順に従います。

1. [Adobe Developer Console](https://developer.adobe.com/console)に移動し、組織の資格情報でログインします。
2. プロジェクトを選択するか、新しいプロジェクトを作成します。
3. **Add API**&#x200B;を選択します。
4. 「**Experience Rollouts API**」を検索して選択します。
5. プロンプトに従ってAPIを設定し、資格情報を生成します。
6. プロジェクト用に生成された&#x200B;**クライアント ID**&#x200B;に注意してください。 これは、Experience Rollouts APIの呼び出し時およびExperience Rollouts コンソールでのアプリケーションのオンボーディング時に使用する識別子です。

## サーバーサイドのSDKとの統合 {#server-sdk}

Java SDKまたはNode.js SDKを使用して統合する場合は、API キーに加えて&#x200B;**サービストークン**&#x200B;のクライアント IDが必要です。 サービストークンを使用すると、SDKはバックグラウンドでエクスペリエンスロールアウト APIを呼び出すことができます。

>[!NOTE]
>
>サーバーサイドのSDK クライアント IDは、API呼び出しを行う前に、Experience Rollouts サポートで許可リストに加えるする必要があります。 Developer Consoleの設定が完了したら、サポートにお問い合わせください。

## 関連トピック {#see-also}

* [スタートアップガイド](startup-guide.md)
* [SDK](sdks.md)
* [アプリケーションのオンボーディング](../applications/onboard-your-application.md)
* [統合ステップ](integration-steps.md)
