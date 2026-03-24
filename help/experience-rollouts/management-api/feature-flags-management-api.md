---
title: 機能フラグ管理API
description: エクスペリエンスロールアウト機能のAPI リファレンスでは、アプリケーションの機能フラグを取得、作成、更新、削除するエンドポイントなど、管理APIにフラグが付けられます。
source-git-commit: 8a92b7a3e8c52da8bb2474f52c831e159420b878
workflow-type: tm+mt
source-wordcount: '650'
ht-degree: 14%

---


# 機能フラグ管理API {#feature-flags-management-api}

機能フラグ管理APIを使用すると、Experience Rolloutsのアプリケーションの機能フラグをプログラムで作成、読み取り、更新、削除できます。

**基本パス：** `/m/api/v1/mgmt/feature`

すべてのリクエストには、[一般的な要件](feature-management-apis-overview.md#common-requirements)に記載されているヘッダーが必要です。

## すべての機能フラグを入手 {#get-all-features}

指定したアプリケーションのすべての機能フラグを取得します。

| | |
|---|---|
| **エンドポイント** | `GET /m/api/v1/mgmt/feature` |
| **メソッド** | GET |

### クエリパラメーター {#get-all-query-params}

| パラメーター | タイプ | 説明 | 必須 |
|---|---|---|---|
| `clientId` | 整数 | アプリケーションの数値ID。 [ クライアント IDの取得](get-client-id.md)を参照してください。 `imsClientId`が指定されていない場合は必須です。 | 条件 |
| `imsClientId` | 文字列 | アプリケーションの文字列形式のクライアント ID。 `clientId`が指定されていない場合は必須です。 | 条件 |
| `nonReleaseFeature` | ブール | グループまたはリリースに関連付けられていない独立した機能フラグを含めるには、`true`に設定します。 API ベースのワークフローに必要です。 | ○ |

### 応答 {#get-all-response}

| ステータス | 説明 |
|---|---|
| `200` | 成功です。 応答ボディには、機能フラグオブジェクトのリストが含まれます。 |

応答ボディに`features`配列が含まれています。 各要素は、[FeatureDTO オブジェクト参照](#featuredto-object)で説明されているフィールドを持つ機能フラグオブジェクトです。

**回答例：**

```json
{
  "features": [
    {
      "id": 22079,
      "name": "new.FF.1",
      "clientId": 1191,
      "state": "enabled",
      "description": "first feature flag",
      "release": { "id": 2631, "name": "FF.group", "status": "SAVED" },
      "audience": null,
      "params": { "label": "new FF 1", "rolloutType": "manual" }
    },
    {
      "id": 22080,
      "name": "new.FF.2",
      "clientId": 1191,
      "state": "enabled",
      "description": "second feature flag",
      "audience": [
        {
          "id": 10034665,
          "criteria": { "and": [{ "operator": "EQ", "attr": "LOCALE", "val": "EN" }] }
        }
      ]
    }
  ]
}
```

## IDによる機能フラグの取得 {#get-feature-by-id}

単一の機能フラグを数値IDで取得します。

| | |
|---|---|
| **エンドポイント** | `GET /m/api/v1/mgmt/feature/{featureId}` |
| **メソッド** | GET |

### 応答 {#get-by-id-response}

| ステータス | 説明 |
|---|---|
| `200` | 成功です。 応答本文は、単一の[FeatureDTO オブジェクト ](#featuredto-object)です。 |
| `400` | 無効な機能ID。 |

## 機能フラグを作成 {#create-feature}

新機能フラグを作成します。

| | |
|---|---|
| **エンドポイント** | `POST /m/api/v1/mgmt/feature` |
| **メソッド** | 投稿する |

### リクエスト本文 {#create-request-body}

リクエスト本文は[FeatureDTO オブジェクト ](#featuredto-object)です。 作成には次のフィールドが必要です。

| フィールド | 必須 | メモ |
|---|---|---|
| `name` | ○ | 機能フラグキー。 最大50文字。 パターン：`^[a-zA-Z0-9_.-]*$` |
| `clientId` | ○ | 数値アプリケーション ID。 [ クライアント IDの取得](get-client-id.md)を参照してください。 |
| `state` | ○ | `"enabled"` または `"disabled"` |

### 応答 {#create-response}

| ステータス | 説明 |
|---|---|
| `200` | 成功です。 応答の本文に`{ "generatedFeatureId": <id> }`が含まれています。 |
| `400` | 無効なペイロードです。 |
| `403` | このクライアントまたはオーディエンス ルールに対する権限が不十分です。 |
| `417` | 開発者の役割を持つユーザーは、公開ルールを持つ機能を保存できません。少なくとも1つのオーディエンスルールが必要です。 |

**サンプルリクエスト：**

```json
{
  "name": "my-new-feature",
  "clientId": 1191,
  "state": "disabled",
  "description": "A new feature flag",
  "meta": "VGVzdA==",
  "audience": [
    {
      "criteria": {
        "and": [{ "operator": "EQ", "attr": "COUNTRY", "category": "default", "ruleId": 1, "val": "US" }]
      }
    }
  ],
  "variations": [{ "variantPercentage": 100, "variantName": "Variation 1" }],
  "params": { "label": "My New Feature", "tags": [] }
}
```

## 機能フラグを更新 {#update-feature}

既存の機能フラグを更新します。 `id` フィールドを含む完全な[FeatureDTO オブジェクト ](#featuredto-object)を渡します。

| | |
|---|---|
| **エンドポイント** | `PUT /m/api/v1/mgmt/feature` |
| **メソッド** | PUT |

### 応答 {#update-response}

| ステータス | 説明 |
|---|---|
| `200` | 成功です。 応答ボディは、更新されたFeatureDTO オブジェクトです。 |
| `400` | 無効なペイロードです。 |
| `403` | 不十分な権限： |
| `417` | 同時更新の競合。 最初に現在の機能を取得し、`params`から最新の`version`値で再試行してください。 |

## 機能フラグを削除 {#delete-feature}

機能フラグを数値IDで削除します。

| | |
|---|---|
| **エンドポイント** | `DELETE /m/api/v1/mgmt/feature/{featureId}` |
| **メソッド** | DELETE |

### 応答 {#delete-response}

| ステータス | 説明 |
|---|---|
| `204` | 成功です。 応答ボディがありません。 |
| `403` | 不十分な権限： |

## FeatureDTO オブジェクト参照 {#featuredto-object}

| フィールド | タイプ | 説明 | 必須 |
|---|---|---|---|
| `id` | 整数 | 機能フラグ ID。 更新呼び出しにのみ必要です。 | 条件 |
| `name` | 文字列 | 機能フラグキー（API応答で返されます）。 最大50文字。 パターン：`^[a-zA-Z0-9_.-]*$` | はい（作成） |
| `clientId` | 整数 | 数値アプリケーション ID。 | ○ |
| `state` | 文字列 | `"enabled"` または `"disabled"` | ○ |
| `meta` | 文字列 | API応答の機能で返されるBase64 エンコードされたメタデータ。 最大1024文字。 | × |
| `description` | 文字列 | 説明を表示します。 最大225文字。 | × |
| `audience` | 配列 | オーディエンスルールのリスト。 [FeatureRule オブジェクト ](#featurerule-object)を参照してください。 この生成には、[目的のオーディエンス条件を取得](get-audience-criteria.md)を使用します。 | × |
| `variations` | 配列 | バリエーションのリスト： 最大3。 [FeatureVariation オブジェクト ](#featurevariation-object)を参照してください。 | × |
| `params` | オブジェクト | 追加のメタデータ： サポートされているキー：`label` （UIの表示名）、`tags` （文字列配列）。 | × |
| `release` | オブジェクト | リリース/グループの関連付け：`null` フラグがグループ内にない場合。 読み取り専用： | × |

### FeatureVariation オブジェクト {#featurevariation-object}

| フィールド | タイプ | 説明 | 必須 |
|---|---|---|---|
| `id` | 整数 | バリエーション ID。 更新呼び出しにのみ必要です。 | 条件 |
| `variantName` | 文字列 | バリアント名： 固定値：`"Variation 1"`、`"Variation 2"`、`"Variation 3"`。 | ○ |
| `variantPercentage` | 小数 | このバリエーションを受け取るオーディエンスの割合。 0より大きく100以下で、小数点以下桁が2つまでである必要があります。 | ○ |

### FeatureRule オブジェクト {#featurerule-object}

| フィールド | タイプ | 説明 | 必須 |
|---|---|---|---|
| `id` | 整数 | ルール ID。 更新呼び出しにのみ必要です。 新しいルールの追加時に`null`に設定します。 | 条件 |
| `criteria` | オブジェクト | オーディエンスルールを定義する条件オブジェクト。 [条件オブジェクト ](#condition-object)を参照してください。 | ○ |

### 状況オブジェクト {#condition-object}

| フィールド | タイプ | 説明 |
|---|---|---|
| `and` | 配列\&lt;条件\> | すべての条件は真でなければならない。 |
| `or` | 配列\&lt;条件\> | 少なくとも1つの条件がtrueである必要があります。 |
| `not` | 条件 | この条件はfalseである必要があります。 |
| `attr` | 文字列 | 評価するユーザー属性（例：`COUNTRY`、`LOCALE`）。 |
| `operator` | 文字列 | 比較演算子（例：`EQ`、`IN`、`LT`）。 |
| `val` | 文字列 | 比較する値。 |
| `meta` | オブジェクト | オプションの条件メタデータ：`desc` フィールドは、UIの表示ラベルを設定します。 |

`and`、`or`、`not`のいずれか、または`attr`、`operator`、`val`の組み合わせは、各条件で指定する必要があります。

## 関連トピック {#see-also}

* [機能管理APIの概要](feature-management-apis-overview.md)
* [管理パッチ API](management-patch-api.md)
* [アプリケーションのクライアント IDを取得](get-client-id.md)
* [必要なオーディエンス条件を取得](get-audience-criteria.md)
