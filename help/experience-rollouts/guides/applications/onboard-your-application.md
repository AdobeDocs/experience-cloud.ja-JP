---
title: アプリケーションのオンボーディング
description: 新しいアプリケーションをAdobe Experience Rolloutsにオンボーディングして、機能フラグの作成と管理を開始する方法について説明します。
exl-id: d88c27a5-f490-4504-9764-5e4ce98fdf20
source-git-commit: fcb1d36fc92b3954a902d818a98f579672c577e9
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 2%

---

# アプリケーションのオンボーディング {#onboard-your-application}

新しいアプリケーションを追加するには、**管理者**&#x200B;の役割が必要です。 役割を確認または更新する必要がある場合は、管理者にお問い合わせください。

## 新しいアプリケーションを追加 {#add-application}

1. Experience Rollouts コンソールにログインし、**Experience Rollout > Applications**&#x200B;に移動します。

   >[!NOTE]
   >
   >**新しいアプリケーション** ボタンが表示されない場合は、**Floodgate Admin**&#x200B;の役割があることを確認してください。

2. **新しいアプリケーション**&#x200B;を選択します。

3. アプリケーションの種類（webまたはモバイル）に一致する&#x200B;**platform**&#x200B;を選択します。

4. 次の情報を入力します。

   | フィールド | 説明 |
   |---|---|
   | **アプリケーション ID** | コードからエクスペリエンスロールアウトを呼び出す際に使用される一意の識別子。 アプリケーションのクライアント IDを使用します。 |
   | **TTL** | アプリケーションごとのキャッシュを更新するためのポーリング間隔（秒単位）。 サーバーサイド SDKにのみ適用されます。 |

5. 「**追加**」を選択します。 これで、アプリケーションが登録され、機能フラグ設定の準備が整いました。

## 次のステップ {#next-steps}

アプリケーションをオンボーディングしたら、機能フラグの作成を開始できます。

* [最初の機能フラグを作成](../feature-flags/create-your-first-feature-flag.md)
* [アプリにエクスペリエンスのロールアウトを統合する](../integrate/integrating-in-your-app.md)

## 関連トピック {#see-also}

* [アプリケーションの管理](manage-applications.md)
* [コンソールにログインします](../console/log-in-to-the-console.md)
