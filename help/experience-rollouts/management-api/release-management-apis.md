---
title: リリース管理API
description: リリースとチーム間の機能グループを取得、作成、編集するエンドポイントを含む、Experience Rollouts リリース管理APIのAPI リファレンス。
exl-id: e8d1d025-0645-4cf2-921f-d94c9f71282d
source-git-commit: 454b5c719a5f8be82d1ed835da58bfca6316def2
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 14%

---

# リリース管理API {#release-management-apis}

リリース管理APIを使用すると、リリースとチーム間の機能グループ（CTFG）をプログラムで取得、作成、編集できます。 これらのAPIは、v2管理エンドポイントを使用します。

**基本パス：** `/m/api/v2/mgmt/release`

すべてのリクエストには、[common requirements](feature-management-apis-overview.md#common-requirements)に記載されているヘッダーと、以下に示す追加ヘッダーが必要です。

## 追加の必須ヘッダー {#additional-header}

| ヘッダー | 説明 | 必須 |
|---|---|---|
| `x-user-context-org` | 組織の数値チーム ID。 この値は、Experience Rollouts コンソールのチーム設定で確認できます。 | ○ |

## IDでリリースを取得 {#get-release}

単一のリリースまたはチーム間の機能グループを数値IDで取得します。

| | |
|---|---|
| **エンドポイント** | `GET /m/api/v2/mgmt/release/{id}` |
| **メソッド** | GET |

### クエリパラメーター {#get-query-params}

| パラメーター | タイプ | 説明 | デフォルト |
|---|---|---|---|
| `includePermissions` | ブール | このリリースを更新または削除する権限を含めます。 | `true` |
| `includeOrg` | ブール | このリリースの組織情報を含めます。 | `true` |
| `includeAnalyzeInfo` | ブール | 分析情報を含めます。 | `false` |

### 応答 {#get-response}

| ステータス | 説明 |
|---|---|
| `200` | 成功です。 応答本文はリリースオブジェクトです。[ リリースオブジェクト参照](#release-object)を参照してください。 |
| `400` | 無効なリリース IDまたは形式が正しくないリクエストです。 |

## リリースを作成 {#create-release}

新しいリリースまたはチーム間の機能グループを作成します。

| | |
|---|---|
| **エンドポイント** | `POST /m/api/v2/mgmt/release` |
| **メソッド** | 投稿する |

### リクエスト本文 {#create-request-body}

リクエスト本文では、[ リリースオブジェクト ](#release-object)を使用しています。 作成するには、チーム間の機能グループ （`CROSS_TEAM_FEATURE_GROUP` タイプ）の`status`を`"SAVED"`に、標準リリース （`RELEASE` タイプ）の`"DRAFT"`に設定する必要があります。

**サンプル – チーム間の機能グループの作成：**

```json
{
  "params": {
    "rolloutType": "manual",
    "cohortingType": "guid",
    "tags": [],
    "canContextOverridePUP": false,
    "label": "my-cross-team-group"
  },
  "status": "SAVED",
  "type": "CROSS_TEAM_FEATURE_GROUP",
  "name": "my-cross-team-group",
  "description": null,
  "meta": "",
  "variations": [{ "variantPercentage": 100, "variantName": "Variant 1", "features": [] }],
  "audience": [{}],
  "clients": [],
  "pollInterval": 300,
  "org": { "id": "95" },
  "comment": ""
}
```

### 応答 {#create-response}

| ステータス | 説明 |
|---|---|
| `200` | 成功です。 応答本文は、作成されたリリースオブジェクトです。 |
| `400` | 無効なペイロードです。 |

## リリースを編集 {#edit-release}

既存のリリースまたはチーム間の機能グループを更新します。 `id` フィールドを含む完全なリリースオブジェクトを渡します。

| | |
|---|---|
| **エンドポイント** | `PUT /m/api/v2/mgmt/release/{id}` |
| **メソッド** | PUT |

### 応答 {#edit-response}

| ステータス | 説明 |
|---|---|
| `200` | 成功です。 応答本文は、更新されたリリースオブジェクトです。 |
| `417` | 同時更新の競合。 GETとPUTの呼び出しの間でリリースが変更されました。 現在のリリースを取得して再試行してください。 |

## リリースオブジェクト参照 {#release-object}

| フィールド | タイプ | 説明 | 必須 |
|---|---|---|---|
| `id` | 整数 | リリース ID。 更新呼び出しにのみ必要です。 | 条件 |
| `name` | 文字列 | リリース名。 最大50文字。 パターン：`^[a-zA-Z0-9_ ,.:()-]*$`。 一意である必要があります。 | ○ |
| `description` | 文字列 | オプションの説明： 最大255文字。 | × |
| `type` | 文字列 | 標準リリースの`"RELEASE"`、チーム間の機能グループの`"CROSS_TEAM_FEATURE_GROUP"`。 | ○ |
| `status` | 文字列 | リリースの状態： IMSの場合：作成時に`"DRAFT"`、更新時に`"DRAFT"`、`"SAVED"`、`"PUBLISHED"`。 CTFGの場合：作成時に`"SAVED"`、更新時に`"SAVED"`、`"PUBLISHED"`。 | ○ |
| `clients` | 配列 | このリリースに関連するアプリケーション。 各エントリには`id` （数値）と`imsClientId` （文字列）が必要です。 | × |
| `audience` | 配列 | オーディエンスルールのリスト。 [条件オブジェクト ](feature-flags-management-api.md#condition-object)を参照してください。 | × |
| `variations` | 配列 | バリエーションのリスト： 送信中にサポートされるバリエーションは1つだけです。 | 送信に必要 |
| `params` | オブジェクト | リリースパラメーター： [ サポートされているパラメーターのフィールド ](#supported-params)を参照してください。 | 送信に必要 |
| `org` | オブジェクト | 組織オブジェクト： `id`を含める必要があります。 | × |

### サポートされているパラメーターのフィールド {#supported-params}

| フィールド | タイプ | 説明 | 必須 |
|---|---|---|---|
| `label` | 文字列 | 表示名。 最大50文字。 | ○ |
| `tags` | Array\&lt;String\> | オプションタグ： それぞれ最大50文字。 | × |
| `canContextOverridePUP` | ブール | `true`の場合、コンテキストルールはプロファイルルールを上書きします。 既定：`false`。 | ○ |
| `isBetaRelease` | ブール | `true`の場合、これをベータリリースとしてマークします。 既定：`false`。 | × |

### Variation オブジェクト {#variation-object}

| フィールド | タイプ | 説明 | 必須 |
|---|---|---|---|
| `id` | 整数 | バリエーション ID。 更新呼び出しにのみ必要です。 | 条件 |
| `variantName` | 文字列 | バリアント名： 最大50文字。 | ○ |
| `variantPercentage` | Double | このバリエーションを受け取るオーディエンスの割合。 範囲：[0、100]。 | ○ |
| `features` | 配列 | このバリエーションに含まれる機能。 各エントリには、`id`、`name`、`clientId`および`state`を含める必要があります。 | × |

## 関連トピック {#see-also}

* [機能管理APIの概要](feature-management-apis-overview.md)
* [機能フラグ管理API](feature-flags-management-api.md)
* [機能グループ管理API](feature-group-management-api.md)
