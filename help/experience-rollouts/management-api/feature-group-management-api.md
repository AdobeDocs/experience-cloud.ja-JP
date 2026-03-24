---
title: 機能グループ管理API
description: エクスペリエンスロールアウト機能グループ管理APIのAPI リファレンス。機能グループのロールアウトプランの取得、作成、更新、削除、制御を行うエンドポイントが含まれます。
source-git-commit: db719ba7b9db91aea818d8ef216a28fcedc6aa65
workflow-type: tm+mt
source-wordcount: '575'
ht-degree: 16%

---


# 機能グループ管理API {#feature-group-management-api}

機能グループ管理APIを使用すると、自動テストおよびA/B テストのロールアウトプランを含む、エクスペリエンスロールアウトの機能グループをプログラムで作成、読み取り、更新および削除できます。

**基本パス：** `/m/api/v1/mgmt/group`

すべてのリクエストには、[一般的な要件](feature-management-apis-overview.md#common-requirements)に記載されているヘッダーが必要です。

## すべての機能グループを見る {#get-all-groups}

組織のすべての機能グループを取得します。

| | |
|---|---|
| **エンドポイント** | `GET /m/api/v1/mgmt/group` |
| **メソッド** | GET |

### クエリパラメーター {#get-all-query-params}

| パラメーター | タイプ | 説明 | 必須 |
|---|---|---|---|
| `myOrg` | ブール | 組織情報を含めるには、`true`に設定します。 | ○ |
| `includeClientInfo` | ブール | 各グループのアプリケーション情報を含めるには、`true`に設定します。 | ○ |

### 応答 {#get-all-response}

| ステータス | 説明 |
|---|---|
| `200` | 成功です。 応答ボディは、フィーチャ グループ オブジェクトの配列です。 |

## IDによる機能グループの取得 {#get-group-by-id}

単一の機能グループを数値IDで取得します。

| | |
|---|---|
| **エンドポイント** | `GET /m/api/v1/mgmt/group/{groupId}` |
| **メソッド** | GET |
| **クエリパラメーター** | `includeAnalyzeInfo=true` （オプション – 応答に分析データを追加します） |

### 応答 {#get-by-id-response}

| ステータス | 説明 |
|---|---|
| `200` | 成功です。 応答ボディは機能グループオブジェクトです。 |
| `400` | 無効な機能グループ IDです。 |

## 機能グループの作成 {#create-group}

手動、自動、またはA/B テストのロールアウト タイプを使用して、新しい機能グループを作成します。

| | |
|---|---|
| **エンドポイント** | `POST /m/api/v1/mgmt/group` |
| **メソッド** | 投稿する |

### リクエスト本文 {#create-request-body}

リクエスト本文は[機能グループオブジェクト &#x200B;](#feature-group-object)を使用します。 `params`内の`rolloutType`は必須であり、ペイロードの構造を決定します。

**サンプル – 手動ロールアウト：**

```json
{
  "params": {
    "rolloutType": "manual",
    "label": "my-feature-group",
    "tags": [],
    "canContextOverridePUP": false
  },
  "status": "SAVED",
  "type": "group",
  "name": "my.feature.group",
  "description": "A manual feature group",
  "variations": [{ "variantPercentage": 100, "variantName": "Variant 1", "features": [] }],
  "audience": [{ "criteria": { "and": [{ "operator": "EQ", "attr": "COUNTRY", "val": "US", "ruleId": 1, "category": "default" }] } }],
  "clients": [],
  "org": { "id": 95 }
}
```

### 応答 {#create-response}

| ステータス | 説明 |
|---|---|
| `200` | 成功です。 応答本文は、作成された機能グループオブジェクトです。 |
| `400` | ペイロードが無効です。詳しくは、[&#x200B; エラーメッセージ &#x200B;](#error-messages)を参照してください。 |
| `403` | 不十分な権限： |

## 機能グループを更新 {#update-group}

既存の機能グループを更新します。 create リクエスト本文と同じ構造（`id` フィールドを含む）を渡します。

| | |
|---|---|
| **エンドポイント** | `PUT /m/api/v1/mgmt/group` |
| **メソッド** | PUT |

### 応答 {#update-response}

| ステータス | 説明 |
|---|---|
| `200` | 成功です。 応答本文は、更新された機能グループオブジェクトです。 |
| `400` | 無効なペイロードです。 |
| `403` | 不十分な権限： |

## 機能グループの削除 {#delete-group}

フィーチャ グループを数値IDで削除します。

| | |
|---|---|
| **エンドポイント** | `DELETE /m/api/v1/mgmt/group/{groupId}` |
| **メソッド** | DELETE |

### 応答 {#delete-response}

| ステータス | 説明 |
|---|---|
| `204` | 成功です。 応答ボディがありません。 |
| `403` | 不十分な権限： |

## 機能グループオブジェクト参照 {#feature-group-object}

| フィールド | タイプ | 説明 | 必須 |
|---|---|---|---|
| `id` | 整数 | 機能グループ ID。 更新呼び出しにのみ必要です。 | 条件 |
| `name` | 文字列 | 機能グループキー： 最大50文字。 パターン：`^[a-zA-Z0-9_.-]*$` | はい（作成） |
| `clients` | 配列 | グループに関連付けられているアプリケーション。 各エントリには`id`と`imsClientId`を含める必要があります。 | ○ |
| `status` | 文字列 | `"SAVED"` または `"PUBLISHED"` | ○ |
| `type` | 文字列 | 機能グループに対しては常に`"group"`です。 | ○ |
| `org` | オブジェクト | 組織の詳細： `id`を含める必要があります。 | ○ |
| `params` | オブジェクト | グループパラメーター：`rolloutType` は必須です（`"manual"`、`"automated"`または`"ab-testing"`）。 `label`と`tags`もサポートしています。 | ○ |
| `audience` | 配列 | 手動ロールアウトタイプのオーディエンスルール。 | × |
| `variations` | 配列 | バリエーションのリスト： [FeatureGroupVariation オブジェクト &#x200B;](#featuregroupvariation-object)を参照してください。 | × |
| `phaseRollOutPlan` | オブジェクト | フェーズの導入計画： 自動化されたA/B テストの種類に必要です。 [PhaseRollOutPlan オブジェクト &#x200B;](#phaserolloutplan-object)を参照してください。 | 条件 |
| `description` | 文字列 | オプションの表示説明。 最大225文字。 | × |

### FeatureGroupVariation オブジェクト {#featuregroupvariation-object}

| フィールド | タイプ | 説明 | 必須 |
|---|---|---|---|
| `id` | 整数 | バリエーション ID。 更新呼び出しにのみ必要です。 | 条件 |
| `variantName` | 文字列 | バリアント名： `"Variant 1"`にハードコードされました。 | ○ |
| `variantPercentage` | 小数 | このバリエーションを受け取るオーディエンスの割合。 0より大きく100以下でなければなりません。 | ○ |

### PhaseRollOutPlan オブジェクト {#phaserolloutplan-object}

| フィールド | タイプ | 説明 | 必須 |
|---|---|---|---|
| `phaseRollOutBlocks` | 配列 | フェーズ ブロックと待機ブロックの順序付きリスト。 最後のブロックはフェーズ ブロックである必要があります。 | ○ |
| `rollOutPlanState` | 文字列 | `"DRAFT"`、`"RUNNING"`、`"PAUSED"`または`"ABORTED"` | ○ |

`phaseRollOutBlocks`の各ブロックは、オーディエンス条件を持つ`phaseRule`を含む&#x200B;**フェーズ ブロック** （`isPhaseBlock: true`）か、`waitDuration` （相対）または`executionDate` （固定タイムスタンプ）を持つ`waitRule`を含む&#x200B;**待機ブロック** （`isPhaseBlock: false`）のいずれかです。

## エラーメッセージ {#error-messages}

| 条件 | ステータス | エラーメッセージ |
|---|---|---|
| 名前が無効または空です | 400 | `Error: Invalid value for release name.` |
| 空のオーディエンス条件 | 400 | `Error: Release is not valid` |
| 自動タイプ用の複数のバリエーション | 400 | `Error: Feature variation is not valid. Variation name should be unique across variations` |
| クライアントのない公開済みグループ | 400 | `Error: At least one client must be associated with enabled feature group.` |
| プランの最後のブロックはフェーズ ブロックではありません | 400 | `Error: The last block in the Phase Rollout plan should be phase block` |
| 待機ブロックのタイミングが正しくありません | 400 | `Error: Wait block timings are not in order in the phase rollout plan` |
| 一貫性のない待機ブロックタイプ | 400 | `Error: Wait block should be of same type.` |
| アクティブ化されたフェーズ ブロックの編集 | 400 | `Error: Activated phase block should not be changed` |
| 空のロールアウトタイプ | 400 | `Error: Rollout type cannot be empty while feature group creation` |
| 手動タイプでフェーズ計画を渡しました | 400 | `Error: PhaseRollOutPlan can't be added with manual rollout type while feature group creation` |
| 公開済みステータスでスケジュールが渡されました | 400 | `Error: Schedule can't be added in published state while release/group creation` |

## 関連トピック {#see-also}

* [機能管理APIの概要](feature-management-apis-overview.md)
* [機能フラグ管理API](feature-flags-management-api.md)
* [管理パッチ API](management-patch-api.md)
