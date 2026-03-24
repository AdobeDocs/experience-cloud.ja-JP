---
title: GET Feature API V3
description: エクスペリエンスロールアウト機能API V3のAPI リファレンス。webおよびモバイルアプリケーションの機能フラグを取得するために使用します。
source-git-commit: 6ecedbfc6c7de392f214f3f8f2e71aa18e1bacb9
workflow-type: tm+mt
source-wordcount: '679'
ht-degree: 9%

---


# GET Feature API V3 {#get-feature-api-v3}

機能API V3は、web アプリケーションおよびモバイルアプリケーションで機能フラグを取得するためのプライマリエンドポイントです。 ユーザーのIDとコンソールで設定されたオーディエンスルールに基づいて、ユーザーが対象とする機能とリリースを返します。

**エンドポイント：** `GET {HOST}/fg/api/v3/feature`

ステージには`https://p13-stage.adobe.io`を、実稼動用には`https://p13n.adobe.io`を使用します。

## リクエスト {#request}

### リクエストヘッダー {#request-headers}

| ヘッダー | タイプ | 説明 | 必須 |
|---|---|---|---|
| `x-api-key` | 文字列 | Adobe Developer ConsoleからのアプリケーションのAPI キー。 ステージングと実稼動用に別々にプロビジョニングする必要があります。 | ○ |
| `Authorization` | 文字列 | 未認証のシナリオには&#x200B;**不要**&#x200B;です。 認証済みユーザーに`Bearer <AccessToken>`を使用します。 サーバーサイドのSDK キャッシュ シナリオに`Bearer <ServiceToken>`を使用します。 | × |
| `x-adobe-uuid` | 文字列 | 一意の訪問者またはデバイス ID。 未認証のユーザーのロールアウト率をサポートし、セッション間および未認証から認証済みの移行をまたいで整合性を維持するために使用されます。 | × |

### クエリパラメーター {#query-parameters}

| パラメーター | タイプ | 説明 | 必須 |
|---|---|---|---|
| `clientId` | 文字列 | Experience Rollouts コンソールでオンボーディングされた、アプリケーションのクライアント ID。 | ○ |
| `ignore_rf` | ブール | `true`の場合、リリースフラグは無視され、クライアントのすべてのリリースが返されます。 既定：`false`。 | × |
| `rf` | 文字列 | リリースフラグ： `ignore_rf`が`false`の場合にのみ使用されます。 | × |
| `meta` | ブール | `true`の場合、各機能のメタデータが応答に含まれ、値がBase64でエンコードされたキーと値のペアとして返されます。 既定：`false`。 | × |
| `userId` | 文字列 | サービストークンが必要です。 機能フラグを取得するユーザーのGUID。 | × |
| *コンテキストパラメーター* | なし | 上記に記載されていないクエリパラメーターは、コンテキスト変数として扱われ、オーディエンスルールの評価に使用されます。 複数の値を`?key1=val1&key2=val2`として渡します。 例：`?clientLanguage=ja_JP&contractCurrency=JPY`。 | × |

## 応答 {#response}

### 応答ステータスコード {#response-status}

| ステータスコード | 説明 |
|---|---|
| `200 OK` | 応答ボディに返される機能フラグデータ。 |
| `304 Not Modified` | クライアントによって渡されたETagは、最新のサーバー状態と一致します。 これをノープ（変更なし）として扱います。 |
| `400 Bad Request` | `clientId`がオンボーディングされていないか、リクエストの形式が正しくありません。 |
| `403 Forbidden` | 無効なAPI キーか、アプリケーションがAdobe Developer ConsoleのExperience Rollouts APIに登録されていません。 |

### 応答ヘッダー {#response-headers}

| ヘッダー | 説明 |
|---|---|
| `x-request-id` | デバッグ用の一意のリクエスト ID。 これを任意のサポートリクエストに含めます。 |
| `ETag` | このユーザーの機能の現在のサーバー状態を表すトークン。 この値を後続のリクエストで`If-None-Match`として渡します。 状態が変更されていない場合、APIは`304`を返します。 |
| `x-adobe-fg-poll-interval` | クライアントのローカルキャッシュのTTL （秒単位）。 この間隔が経過した後にのみAPIを再呼び出しします。 |

### 応答本文 {#response-body}

応答は、次の最上位フィールドを持つJSON オブジェクトです。

| フィールド | タイプ | 説明 |
|---|---|---|
| `api_version` | 文字列 | API バージョン： 内部フィールド – 処理は必要ありません。 |
| `json_version` | 文字列 | JSON スキーマバージョン。 内部フィールド – 処理は必要ありません。 |
| `ttl` | 整数 | TTLを数秒でキャッシュします。 `x-adobe-fg-poll-interval`応答ヘッダーと同じ値です。 デフォルト：300。 |
| `caching_enabled` | ブール | `true`の場合、機能の評価はクライアント上でローカルに行われます。 `false`の場合、評価は各リクエストでサーバーサイドで行われます。 |
| `client_analytics_params` | オブジェクト | アプリケーションの分析設定。 以下の[client_analytics_params フィールド ](#client-analytics-params)を参照してください。 |
| `releases` | 配列 | ユーザーが対象とするリリースと機能フラグのリスト。 以下の[ リリースフィールド ](#releases-fields)を参照してください。 |

#### client_analytics_params フィールド {#client-analytics-params}

| フィールド | 説明 |
|---|---|
| `app_id` | アプリケーションの数値ID。 |
| `safe_event_required` | このクライアントに対してリターゲティングイベントが有効になっている場合は`true`。 |
| `analytics_required` | V3の応答は常に`false`です。 |

#### リリースフィールド {#releases-fields}

| フィールド | 説明 |
|---|---|
| `release_name` | ユーザーが対象とするリリースまたは機能グループの名前。 |
| `bit_index` | リリースビットインデックス。 負の値は、フルロールアウト状態を示します。 |
| `features` | ユーザーが対象とする機能フラグキーの配列。 機能キーは、ユーザーが資格を持ち、フラグが有効な状態にある場合にのみ返されます。 これは、アプリケーションロジックを構築する必要がある主要なフィールドです。 |
| `meta` | オプションのBase64 エンコードされたメタデータが機能に関連付けられます。 使用する前にデコードします。 |
| `release_analytics_params` | 各対象機能のAnalytics メタデータオブジェクトの配列。 以下の[release_analytics_params フィールド ](#release-analytics-params)を参照してください。 コントロール グループのシナリオでは、`features`は空です。 |

#### release_analytics_params フィールド {#release-analytics-params}

| フィールド | タイプ | 説明 |
|---|---|---|
| `app_id` | 整数 | アプリケーション ID。 |
| `release_id` | 整数 | リリース ID。 |
| `bit_index` | 整数 | リリースビットインデックス。 非推奨（廃止予定）: |
| `variant_id` | 整数 | ユーザーがコントロール グループ内にある場合は`0`。それ以外の場合は0以外です。 |
| `feature_id` | 整数 | 内部機能ID。 |
| `f_key` | 文字列 | 機能フラグキー。 |

## リクエストとレスポンスの例 {#sample}

### リクエストのサンプル {#sample-request}

```http
GET /fg/api/v3/feature?clientId=MyWebApp&meta=true HTTP/1.1
Host: p13n.adobe.io
Authorization: Bearer <ACCESS_TOKEN>
x-api-key: <YOUR_API_KEY>
If-None-Match: <ETAG>
```

### サンプル応答 – テストグループ内のユーザー {#sample-response-test}

```json
{
  "api_version": "0.1",
  "json_version": "0.1",
  "clients": {
    "MyWebApp": {
      "analyticsVersion": "2.0",
      "client_analytics_params": {
        "app_id": 1378,
        "safe_event_required": false,
        "analytics_required": false
      },
      "releases": [
        {
          "bit_index": -160,
          "release_name": "||features||",
          "features": ["ff1", "ff2", "ff3"],
          "release_analytics_params": [
            {
              "app_id": 1378,
              "release_id": -1,
              "bit_index": -160,
              "variant_id": 10040476,
              "feature_id": 26059,
              "f_key": "ff1",
              "analytics_required": true
            }
          ]
        }
      ]
    }
  },
  "ttl": 60
}
```

### 応答のサンプル – コントロール母集団のユーザー {#sample-response-control}

ユーザーがコントロール グループ内にある場合、`features`配列は空で、`variant_id`は`0`です。

```json
{
  "api_version": "0.1",
  "json_version": "0.1",
  "clients": {
    "MyWebApp": {
      "releases": [
        {
          "bit_index": -160,
          "release_name": "||features||",
          "features": [],
          "release_analytics_params": [
            {
              "app_id": 1378,
              "release_id": -1,
              "bit_index": -160,
              "variant_id": 0,
              "feature_id": 26059,
              "f_key": "ff1"
            }
          ]
        }
      ]
    }
  },
  "ttl": 60
}
```

## 関連トピック {#see-also}

* [GET Feature API V2](get-feature-api-v2.md)
* [web アプリケーション](../guides/integrate/web-applications.md)
* [モバイルアプリ](../guides/integrate/mobile-applications.md)
* [統合ステップ](../guides/integrate/integration-steps.md)
