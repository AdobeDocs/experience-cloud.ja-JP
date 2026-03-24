---
title: 必要なオーディエンス条件を取得
description: コンソールとGET機能APIを使用して、Experience Rollouts management APIで使用するための正しいオーディエンス条件JSON構造を生成する方法を説明します。
source-git-commit: 6ecedbfc6c7de392f214f3f8f2e71aa18e1bacb9
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 1%

---


# 必要なオーディエンス条件を取得 {#get-audience-criteria}

管理APIの「オーディエンス条件」フィールドでは、手作業で記述する場合に複雑になる可能性のある構造化JSON形式を使用します。 推奨されるアプローチは、コンソールを使用して目的のオーディエンスを構築し、APIを介してJSON表現を取得することです。

## 手順 {#steps}

必要なオーディエンス条件のJSONを取得するには、次の手順に従います。

1. Experience Rollouts コンソールで、API呼び出しで使用するオーディエンス条件を含む一時的な機能フラグを作成します。
2. 保存後、ブラウザーURLから機能フラグ IDをメモします。 IDは、クライアント IDの後のURLに表示されます。 例えば、`.../feature-flags/1191/22080`では、機能IDは`22080`です。
3. その機能IDで[Get Feature by ID](feature-flags-management-api.md#get-feature-by-id) エンドポイントを呼び出します。
4. 応答JSONで、`audience` フィールドを見つけます。 これには、必要なオーディエンス条件構造が正確に含まれています。
5. `audience`値をコピーし、各ルールオブジェクトから`id`属性を削除します。 これを作成または更新機能API呼び出しで使用します。

## 例 {#example}

GET `/m/api/v1/mgmt/feature/22080`を呼び出した後、次の応答が返されます。

```json
{
  "audience": [
    {
      "id": 10034665,
      "criteria": {
        "and": [
          {
            "operator": "EQ",
            "attr": "LOCALE",
            "val": "EN",
            "ruleId": 1,
            "category": "default"
          }
        ]
      }
    }
  ]
}
```

これを作成機能呼び出しで使用するには、オーディエンスオブジェクトから`id` フィールドを削除します。

```json
{
  "audience": [
    {
      "criteria": {
        "and": [
          {
            "operator": "EQ",
            "attr": "LOCALE",
            "val": "EN",
            "ruleId": 1,
            "category": "default"
          }
        ]
      }
    }
  ]
}
```

## 関連トピック {#see-also}

* [機能フラグ管理API](feature-flags-management-api.md)
* [アプリケーションのクライアント IDを取得](get-client-id.md)
* [管理パッチ API](management-patch-api.md)
