---
title: スタートアップガイド
description: アクセスのリクエストから最初の機能フラグの作成まで、アプリケーションをAdobe Experience ロールアウトと統合するには、次の手順に従います。
source-git-commit: 9bfe0e55e89c1d7fbd77cde63831a6a186820e24
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 1%

---


# スタートアップガイド {#startup-guide}

エクスペリエンスのロールアウトをアプリケーションに統合するには、次の手順に従います。

## 手順1：アクセスのリクエスト {#step-1-access}

Experience Rollouts コンソールへのアクセスをリクエストし、チームに参加します。 詳細な手順については、[ アクセスを要求](../console/request-access.md)を参照してください。

## 手順2：アプリケーションのオンボーディング {#step-2-onboard}

アクセスを取得したら、Experience Rollouts コンソールにログインし、アプリケーションがチームの下に表示されていることを確認します。 そうでない場合は、チーム管理者に追加を依頼してください。 [ アプリケーションのオンボーディング ](../applications/onboard-your-application.md)を参照してください。

オンボーディングの前に、次の手順に従います。

| 要件 | 詳細 |
|---|---|
| **アプリケーション ID** | Experience Rollouts APIの呼び出し時に使用される一意のクライアント ID。 使用可能な場合は、アプリケーションの既存のクライアント IDを使用します。 |
| **サーバーサイドのクライアント** | サーバーサイドのSDKと統合する場合は、適切な権限を持つ管理者クライアント IDが必要です。 |
| **デスクトップクライアント** | クライアント IDの代わりに、製品コードと製品バージョンを使用できます。 |

## 手順3:Experience Rollouts APIの購読 {#step-3-subscribe}

Adobe Developer Consoleを介してExperience Rollouts APIを購読し、アプリケーションが機能フラグエンドポイントを呼び出せるようにします。 Adobe Developer Console](subscribe-to-api-application.md)でのAPI アプリケーションの登録を参照してください。[

>[!NOTE]
>
>サーバーサイド SDKを介して統合する場合は、サービストークンのクライアント IDが必要です。 Experience Rollouts サポートに問い合わせて、クライアント IDを許可リストに加えるしてください。

## 手順4:SDKまたはAPIを使用した統合 {#step-4-integrate}

アプリケーションの種類に応じて[統合手順](integration-steps.md)に従います。 スタックに合ったパスを選択：

* **Web サービス** → Java SDKまたはNode.js SDK
* **Webおよびモバイルアプリ** →機能API V3
* **デスクトップアプリ** →機能API V2

## 手順5：最初の機能フラグを作成してテストする {#step-5-feature-flag}

統合が完了したら、コンソールに最初の機能フラグを作成してテストします。

* [最初の機能フラグを作成](../feature-flags/create-your-first-feature-flag.md)

## 関連トピック {#see-also}

* [アプリにエクスペリエンスのロールアウトを統合する](integrating-in-your-app.md)
* [統合ステップ](integration-steps.md)
* [SDK](sdks.md)
