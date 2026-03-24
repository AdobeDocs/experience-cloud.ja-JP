---
title: 管理パッチ API
description: Experience Rollouts PATCH APIを使用すると、完全なオブジェクトを渡さずに、機能フラグ、機能グループ、またはチーム間の機能グループの個々のフィールドを更新できます。
source-git-commit: 6ecedbfc6c7de392f214f3f8f2e71aa18e1bacb9
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 4%

---


# 管理パッチ API {#management-patch-api}

PATCH APIを使用すると、リクエスト本文に完全なオブジェクトを送信することなく、機能フラグ、機能グループ、またはチーム間の機能グループの特定のフィールドを更新できます。 これは、オーディエンスルールの変更、ステートの切り替え、バリエーションの割合の調整など、ターゲットを絞った更新に役立ちます。

## 機能フラグ PATCH {#feature-flag-patch}

機能フラグの1つ以上のフィールドを更新します。

| | |
|---|---|
| **エンドポイント** | `PATCH /m/api/v1/mgmt/feature/{featureFlagId}` |
| **メソッド** | PATCH |

### リクエストヘッダー {#ff-request-headers}

すべてのリクエストには、[一般的な要件](feature-management-apis-overview.md#common-requirements)に記載されているヘッダーが必要です。

### パスパラメーター {#ff-path-param}

| パラメーター | タイプ | 説明 | 必須 |
|---|---|---|---|
| `featureFlagId` | 整数 | 更新する機能フラグの数値ID。 | ○ |

### リクエスト本文 {#ff-request-body}

更新するフィールドのみを渡します。 応答は常に、完全に更新された機能フラグオブジェクトを返します。

**例 – アップデートの説明のみ：**

```json
{
  "description": "Updated description"
}
```

**例 – 既存のオーディエンスを削除：**

```json
{
  "audience": null
}
```

**例 – オーディエンスが存在しない場合に新しいオーディエンスを追加：**

```json
{
  "audience": [
    {
      "criteria": {
        "and": [
          { "operator": "EQ", "attr": "sandboxType", "val": "DEVELOPMENT", "ruleId": 1, "category": "contextual" }
        ]
      }
    }
  ]
}
```

**例 – 既存のオーディエンスルールを更新：**

```json
{
  "audience": [
    {
      "id": 10020035,
      "criteria": {
        "and": [
          { "operator": "EQ", "attr": "sandboxType", "val": "PRODUCTION", "ruleId": 1, "category": "contextual" }
        ]
      }
    }
  ]
}
```

**例 – ステートの変更とバリエーションの割合：**

```json
{
  "state": "disabled",
  "variations": [
    {
      "id": 10017188,
      "variantName": "Variation 1",
      "variantPercentage": 80.0
    }
  ]
}
```

>[!NOTE]
>
>既存のオーディエンスルールを更新する場合は、ルールの`id` （GET機能のレスポンスから使用可能）を含めて、そのルールを適切に更新します。 バリエーションを更新する際は、重複を避けるためにバリエーションの`id`を含めてください。

### 応答 {#ff-response}

| ステータス | 説明 |
|---|---|
| `200` | 成功です。 応答本文は、完全に更新された機能フラグオブジェクトです。 |
| `400` | 無効なペイロードです。 |
| `403` | 不十分な権限： |
| `417` | 同時更新の競合。 現在の機能を取得して再試行してください。 |

## 機能グループ PATCH {#feature-group-patch}

機能グループの1つ以上のフィールドを更新します。 リクエストとレスポンスの構造は機能フラグ PATCHと同じで、エンドポイントのみが異なります。

| | |
|---|---|
| **エンドポイント** | `PATCH /m/api/v1/mgmt/group/{featureGroupId}` |
| **メソッド** | PATCH |

## Adobe PATCHのチーム間の機能グループ {#ctfg-patch}

チーム間の機能グループの1つ以上のフィールドを更新します。 v2 リリースエンドポイントを使用します。

| | |
|---|---|
| **エンドポイント** | `PATCH /m/api/v2/mgmt/release/{CTFGId}` |
| **メソッド** | PATCH |

## 関連トピック {#see-also}

* [機能フラグ管理API](feature-flags-management-api.md)
* [機能グループ管理API](feature-group-management-api.md)
* [リリース管理API](release-management-apis.md)
* [機能管理APIの概要](feature-management-apis-overview.md)
