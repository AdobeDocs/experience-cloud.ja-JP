---
title: Campaign REST API の概要
description: Campaign にテクノロジーのパネルを搭載することで、統合を作成し、独自のエコシステムを構築します。
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="限定提供（LA）" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Campaign Standard移行済みユーザーに制限"
exl-id: c6968252-a012-4029-bbb8-66f4f693e99b
source-git-commit: 3f4400f24b75e8e435610afbe49e9d9444dbf563
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 48%

---

# Campaign REST API の概要 {#get-started-apis}

>[!CAUTION]
>
>このドキュメントは、Campaign v8 に移行するAdobe Campaign Standardのお客様を対象としています。
>
>API 呼び出しを実行する前に、使用許諾契約に対応する拡張制限を確認してください。詳しくは、[このページ](https://helpx.adobe.com/jp/legal/product-descriptions/campaign-standard.html#ITInfrastructureResourcesbyActiveProfilesTiers)を参照してください。

Campaign REST API は、以下を可能にすることを目的としています **統合の作成** Adobe Campaignの場合 **独自のエコシステムの構築** Adobe Campaignを使用するテクノロジーのパネルと統合する。

Adobe Campaign REST API を使用すると、次の機能にアクセスできます。

<table><tr>
 <td valign="top"><a href="retrieving-profiles.md"><img width="60px" alt="conditions" src="assets/icon_profile.svg"/></a><p><a href="retrieving-profiles.md">プロファイル</a></p></td>
<td valign="top"><a href="creating-a-service.md"><img width="60px" alt="conditions" src="assets/icon_services.svg"/></a><p><a href="creating-a-service.md">サービスと購読</a></p></td>
<td valign="top"><a href="interacting-with-custom-resources.md"><img width="60px" alt="conditions" src="assets/icon_customresources.svg"/></a><p><a href="interacting-with-custom-resources.md">カスタムリソース</a></p></td>
<td valign="top"><a href="controlling-a-workflow.md"><img width="60px" alt="conditions" src="assets/icon_workflows.svg"/></a><p><a href="controlling-a-workflow.md">ワークフロー</a></p></td>
</tr></table>

Campaign REST API を使用するには、Adobe I/Oアカウントが必要です。 これは、適切な API 機能を探し、利用するために必須となる最初の手順です。
詳しくは、[この節](setting-up-api-access.md)を参照してください。

アドビが提供する API は、REST インターフェイスと JSON ペイロードを備えた&#x200B;**標準的な概念**&#x200B;を使用します 。

すべてのエンドポイントについて、このドキュメントで大幅に説明し、API の操作に関して知っておくべき一般的な概念、完全な API リファレンス、コード例、クイックスタートガイドを示します。 これらの例はすべて Postman で使用できますが、任意の REST クライアントをご利用いただけます。

API について不明な点や問題がある場合は、[アドビコミュニティ](https://experienceleaguecommunities.adobe.com/t5/adobe-campaign-standard/ct-p/adobe-campaign-standard-community)で質問してください。
