---
title: GET Feature API V2
description: エクスペリエンスロールアウト機能API V2のAPI リファレンス。デスクトップアプリケーションの機能フラグを取得するために使用します。
source-git-commit: 6ecedbfc6c7de392f214f3f8f2e71aa18e1bacb9
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 12%

---


# GET Feature API V2 {#get-feature-api-v2}

機能API V2は、デスクトップアプリケーション統合用に設計されています。 認証されたユーザーの機能フラグとリリースデータを取得し、標準のクライアント IDに加えて、アプリケーション識別子として製品コードと製品バージョンをサポートします。

**エンドポイント：** `GET {HOST}/fg/api/v2/feature`

ステージには`https://p13-stage.adobe.io`を、実稼動用には`https://p13n.adobe.io`を使用します。

## リクエスト {#request}

### リクエストヘッダー {#request-headers}

| ヘッダー | タイプ | 説明 | 必須 |
|---|---|---|---|
| `x-api-key` | 文字列 | Adobe Developer ConsoleからのアプリケーションのAPI キー。 ステージングと実稼動用に別々にプロビジョニングする必要があります。 | ○ |
| `Authorization` | 文字列 | `Bearer <AccessToken>` または `Bearer <ServiceToken>`。 | ○ |
| `x-adobe-uuid` | 文字列 | 一意の訪問者またはデバイス ID。 未認証のシナリオでのパーセンテージのロールアウトに使用し、セッションの整合性を維持します。 | × |

### クエリパラメーター {#query-parameters}

| パラメーター | タイプ | 説明 | 必須 |
|---|---|---|---|
| `clientId` | 文字列 | Experience Rollouts コンソールでオンボーディングされた、アプリケーションのクライアント ID。 複数の値を渡すことができます：`clientId=C1&clientId=C2`。 | × |
| `p` | 文字列 | 製品、バージョン、プラットフォーム、ロケール文字列（PVPL形式）。 例：`PHSP:17.0:WIN:en_US`。 複数の値を渡すことができます：`p=PHSP:17.0:WIN:en_US&p=PPRO:8:WIN:en_US`。 評価では、製品コードと製品バージョンのみが使用されます。 | × |
| `meta` | ブール | `true`の場合、各機能に対してBase64 エンコードされたメタデータが返されます。 既定：`false`。 | × |
| *コンテキストパラメーター* | なし | 追加のキーと値のペアは、オーディエンスルール評価用のコンテキスト変数として扱われます。 例：`clientLanguage=ja_JP&contractCurrency=JPY`。 | × |

>[!NOTE]
>
>アプリケーションを識別するには、`clientId`または`p`のうち1つ以上が必要です。

## 応答 {#response}

### 応答ステータスコード {#response-status}

| ステータスコード | 説明 |
|---|---|
| `200 OK` | 応答ボディに返される機能フラグデータ。 |
| `304 Not Modified` | ETagは現在のサーバー状態と一致します。 作業の省力化：変更の適用なし |
| `401 Unauthorized` | 認証トークンが無効です。 |

### 応答ヘッダー {#response-headers}

| ヘッダー | 説明 |
|---|---|
| `x-request-id` | デバッグ用の一意のリクエスト ID。 これを任意のサポートリクエストに含めます。 |
| `ETag` | ユーザーの現在の機能状態を表すトークン。 後続のリクエストで`If-None-Match`として渡します。 変更しない場合は`304`を返します。 |
| `x-adobe-fg-poll-interval` | クライアントのローカルキャッシュのTTL （秒単位）。 この間隔が経過した後にのみAPIを再度呼び出します。 |

### 応答本文 {#response-body}

応答は、次の最上位フィールドを持つJSON オブジェクトです。

| フィールド | タイプ | 説明 |
|---|---|---|
| `api_version` | 文字列 | API バージョン： 内部フィールド – 処理は必要ありません。 |
| `json_version` | 文字列 | JSON スキーマバージョン。 内部フィールド – 処理は必要ありません。 |
| `ttl` | 整数 | TTLを数秒でキャッシュします。 デフォルト：300。 |
| `clients` | オブジェクト | クライアント ID （またはPVPL文字列）をリリースデータにマッピングします。 各キーには、以下に説明するフィールドが含まれています。 |

#### クライアントごとの応答フィールド {#per-client-fields}

| フィールド | 説明 |
|---|---|
| `releases` | ユーザーが対象とするリリースの配列。 以下の[&#x200B; リリースフィールド &#x200B;](#releases-fields)を参照してください。 |
| `client_analytics_params` | Analytics設定オブジェクト。 以下の[client_analytics_params フィールド &#x200B;](#analytics-fields)を参照してください。 |

#### リリースフィールド {#releases-fields}

| フィールド | 説明 |
|---|---|
| `release_name` | リリースまたは機能グループの名前。 |
| `bit_index` | リリースビットインデックス。 非推奨（廃止予定）: リリースの状態によっては`null`または負の値を指定できます。 |
| `features` | ユーザーが対象とする機能フラグキーの配列。 機能キーは、ユーザーの資格があり、フラグが有効になっている場合にのみ表示されます。 |
| `meta` | オプションのBase64 エンコード メタデータ。 使用する前にデコードします。 |
| `release_analytics_params` | 適格な機能のAnalytics メタデータ。 コントロール グループのシナリオでは、`features`は空です。 |

#### release_analytics_params フィールド {#release-analytics-params}

| フィールド | タイプ | 説明 |
|---|---|---|
| `app_id` | 整数 | アプリケーション ID。 |
| `release_id` | 整数 | リリース ID。 |
| `bit_index` | 整数 | 非推奨（廃止予定）: |
| `variant_id` | 整数 | コントロール グループの場合は`0`。それ以外の場合は0以外です。 |
| `feature_id` | 整数 | 内部機能ID。 |
| `f_key` | 文字列 | 機能フラグキー。 |

#### client_analytics_params フィールド {#analytics-fields}

| フィールド | タイプ | 説明 |
|---|---|---|
| `app_id` | 整数 | アプリケーション ID。 |
| `safe_event_required` | ブール | リターゲティングイベントが有効になっている場合は`true`。 |
| `analytics_required` | ブール | Analyticsが無効な場合、またはデフォルトのフローの場合は`false`、Kinesis フローが有効な場合は`true`。 |

## リクエストとレスポンスの例 {#sample}

### リクエストのサンプル {#sample-request}

```http
GET /fg/api/v2/feature?clientId=MyDesktopApp&p=PHSP:17.0:WIN:en_US&meta=true HTTP/1.1
Host: p13n.adobe.io
Authorization: Bearer <ACCESS_TOKEN>
x-api-key: <YOUR_API_KEY>
If-None-Match: <ETAG>
```

### レスポンスのサンプル {#sample-response}

```json
{
  "api_version": "0.1",
  "json_version": "0.1",
  "clients": {
    "PHSP:17.0:WIN:en_US": {
      "analyticsVersion": "1.0",
      "releases": []
    },
    "MyDesktopApp": {
      "analyticsVersion": "1.0",
      "client_analytics_params": {
        "app_id": 388,
        "safe_event_required": false,
        "analytics_required": false
      },
      "releases": [
        {
          "bit_index": 160,
          "release_name": "||features||",
          "features": ["feature_a", "feature_b"],
          "release_analytics_params": [
            {
              "app_id": 388,
              "release_id": -1,
              "bit_index": 160,
              "variant_id": 10031741,
              "feature_id": 2918,
              "f_key": "feature_a"
            }
          ],
          "meta": []
        }
      ]
    }
  },
  "ttl": 300
}
```

## 関連トピック {#see-also}

* [GET Feature API V3](get-feature-api-v3.md)
* [デスクトップアプリケーション](../guides/integrate/desktop-applications.md)
* [統合ステップ](../guides/integrate/integration-steps.md)
