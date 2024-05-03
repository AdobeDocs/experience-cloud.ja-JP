---
title: エンドポイント
description: API エンドポイントの詳細情報。
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="限定提供（LA）" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Campaign Standard移行済みユーザーに制限"
source-git-commit: 84b72258789ba61016deb813e93bdca0ea142712
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 9%

---

# エンドポイント {#endpoints}

Adobe Campaign REST API で使用可能なエンドポイントは次のとおりです。

* **/profileAndServices**：標準フィールドの操作。 このエンドポイントでは、拡張フィールドにアクセスできません。
* **/profileAndServicesExt**：プロファイルまたはサービスのカスタムリソース拡張時に追加されたカスタムフィールドを操作します。 カスタムリソースについて詳しくは、次を参照してください [この節](custom-resources.md).
* **/&lt;transactionalapi>**：トランザクションメッセージ API を操作します（トランザクションメッセージ API エンドポイントの名前は、インスタンス設定によって異なります）。 詳しくは、[この節](managing-transactional-messages.md)を参照してください。
* **/workflow/execution**：ワークフローとのインタラクション。 詳しくは、[この節](controlling-a-workflow.md)を参照してください。

デフォルトでは、で使用できるメインリソースは **profileAndServices** および **profileAndServicesExt** API は次のとおりです。

* **/profile**:Campaign データベース内のプロファイルの操作。 サービスにプロファイルを追加するには、を使用します **/service** エンドポイント。 Campaign のプロファイルについて詳しくは、 [Campaign ドキュメント](https://helpx.adobe.com/campaign/standard/audiences/using/about-profiles.html).
* **/service**：購読サービスの管理。 Campaign のサービスについて詳しくは、 [Campaign ドキュメント](https://helpx.adobe.com/campaign/standard/audiences/using/creating-a-service.html).

>[!NOTE]
>
>拡張または作成されたその他すべてのリソースは、 **ProfileAndServicesExt** API のみ。 これらは、 **Profile** リソースにアクセスできるようにします。
