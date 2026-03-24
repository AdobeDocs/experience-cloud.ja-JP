---
title: 機能管理APIの概要
description: 機能フラグ、機能グループ、リリースをプログラムで作成、読み取り、更新、削除できるExperience Rollouts管理APIの概要。
source-git-commit: 6ecedbfc6c7de392f214f3f8f2e71aa18e1bacb9
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 0%

---


# 機能管理APIの概要 {#feature-management-apis-overview}

Experience Rollouts Management APIを使用すると、機能フラグ、機能グループ、リリースをプログラムで管理できます。 ワークフローを自動化したり、エクスペリエンスのロールアウトを既存のデプロイメントパイプラインに統合したりする必要があるチームは、コンソールの代わりにこれらのAPIを使用できます。

>[!NOTE]
>
>サービストークンを使用した管理APIへのアクセスは、リクエストに応じて付与されます。 エクスペリエンスのロールアウトのサポートに連絡し、アクセスをリクエストするためのビジネス上の理由を提供してください。

## 利用可能な管理API {#available-apis}

次の管理APIを使用できます。

* [機能フラグ管理API](feature-flags-management-api.md) — アプリケーションの機能フラグを作成、読み取り、更新、削除します。
* [機能グループ管理API](feature-group-management-api.md) – 機能グループの自動ロールアウト プランを作成、読み取り、更新、削除、制御します。
* [&#x200B; リリース管理API](release-management-apis.md) — チーム間の機能グループとリリースを作成および編集します。

## 共通の要件 {#common-requirements}

すべての管理API呼び出しには次のものが必要です。

* Adobe Developer Consoleの&#x200B;**API キー** — [API アプリケーションのサブスクリプション &#x200B;](../guides/integrate/subscribe-to-api-application.md)を参照してください。
* **IMS ユーザーアクセストークン**&#x200B;または&#x200B;**サービストークン**&#x200B;が`Authorization` ヘッダーの`Bearer <token>`として渡されました。
* `Content-Type: application/json` ヘッダー。

API キーとトークンは、ステージング環境と実稼動環境に対して個別にプロビジョニングする必要があります。

## ヘルパーガイド {#helper-guides}

次のガイドは、正しいAPI ペイロードの構築に役立ちます。

* [&#x200B; アプリケーションのクライアント IDを取得](get-client-id.md) – 機能フラグと機能グループ管理APIで必要な数値のクライアント IDを検索します。
* [目的のオーディエンス条件を取得](get-audience-criteria.md) — コンソールとGET APIを使用して、適切なオーディエンス条件JSON構造を生成します。
* [管理パッチ API](management-patch-api.md) – 完全なオブジェクトを渡さずに、機能フラグ、機能グループ、またはチーム間の機能グループの個々のフィールドを更新します。

## 関連トピック {#see-also}

* [GET Feature API V3](../feature-api/get-feature-api-v3.md)
* [GET Feature API V2](../feature-api/get-feature-api-v2.md)
* [API アプリケーションの購読](../guides/integrate/subscribe-to-api-application.md)
