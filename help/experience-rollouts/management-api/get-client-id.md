---
title: アプリケーションのクライアント IDを取得
description: 管理APIを呼び出す際に必要なExperience Rollouts コンソールで、アプリケーションの数値クライアント IDを見つける方法について説明します。
source-git-commit: 6ecedbfc6c7de392f214f3f8f2e71aa18e1bacb9
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 1%

---


# アプリケーションのクライアント IDを取得 {#get-client-id}

機能フラグと機能グループ管理APIには、機能がどのアプリケーションに属しているかを識別するための数値`clientId`が必要です。 これは、API認証に使用される文字列ベースのIMS クライアント IDとは異なります。

アプリケーションの数値クライアント IDを見つけるには、次の手順に従います。

## 手順 {#steps}

アプリケーションの数値クライアント IDを検索するには、次の手順に従います。

1. Experience Rollouts コンソールにログインします。
2. **機能とリリース**&#x200B;に移動します。
3. 「**機能フラグ**」タブを選択します。
4. **アプリケーション** ドロップダウンを開き、必要なクライアント IDを持つアプリケーションを選択します。
5. ブラウザーのアドレスバーにあるURLを見てください。 `feature-flags/`の後、表示される番号は、そのアプリケーションのクライアント IDの数値です。

例えば、URLが`.../feature-flags/1191/...`で終わる場合、クライアント IDは`1191`です。

## API呼び出しでクライアント IDを使用する {#use-in-api}

この値を管理API リクエストの`clientId` パラメーターとして渡します。 例えば、機能フラグを作成する場合は次のようになります。

```json
{
  "name": "my-feature-flag",
  "clientId": 1191,
  "state": "disabled"
}
```

## 関連トピック {#see-also}

* [機能フラグ管理API](feature-flags-management-api.md)
* [機能グループ管理API](feature-group-management-api.md)
* [必要なオーディエンス条件を取得](get-audience-criteria.md)
