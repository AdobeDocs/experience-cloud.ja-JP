---
title: ブランディング
description: ブランドアイデンティティの管理に使用できるすべてのツールについて説明します。
audience: administration
context-tags: branding,overview;branding,main
role: Admin
level: Experienced
badge: label="限定提供" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Campaign Standard移行済みユーザーに制限"
exl-id: f6438303-5ae8-47c6-8c34-8e586f4b6fe7
TQID: https://experienceleague.adobe.com/El7fE2aveS9C67b8B8fkMpiwMaMx-9aWpW4-3Ev7mG4
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
feature_v2:
  - id: fdbb8fc9-ffa3-4b86-88fe-aa4c5a3e1bc6
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: ad84694f2f6f45e4ee30fc51379106835ac302be
workflow-type: tm+mt
source-wordcount: 363
ht-degree: 97%

---

# ブランディングの基本を学ぶ {#branding-gs}

>[!IMPORTANT]
>
>ブランドは、エンドユーザーが作成または変更することはできません。これらの操作は、Adobe Campaign の技術管理者が実行する必要があります。 ご要望がある場合は、アドビカスタマーケアにお問合せください。

どの会社にも、視覚的要素と技術的な詳細の両方を定義するブランドガイドラインがあります。 Adobe Campaign では、これらのガイドラインを一元的に管理できるので、メールのロゴからキャンペーンで使用する URL やドメインまで、すべての操作で一貫したブランドイメージを顧客に提供できます。

技術管理者は、Adobe Campaign 内で複数のブランドを作成および管理できます。 これにより、ロゴやメールトラッキング設定など、ブランドアイデンティティを設定するすべての要素を定義できます。 作成したら、これらのブランドは配信に簡単にリンクできます。

Campaign で組織の新しいエンティティを追加することや、別のサブドメインで送信する必要がある新しいタイプのメールを作成できます。 手順は次のとおりです。

1. **新しいサブドメインの設定** - アドビで使用する新しいサブドメインの場合、最初の手順は設定することです。 これは、[Campaign コントロールパネル](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/subdomains-branding.html?lang=ja)を通じて実行することも、アドビの技術担当者に問い合わせることもできます。 サブドメインの設定について詳しくは、[このページ](https://experienceleague.adobe.com/ja/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/campaign/ac-domain-name-setup)を参照してください。

   >[!NOTE]
   >
   >コントロールパネルは、すべての管理者ユーザーがアクセスできます。 ユーザーに管理者アクセス権を付与する手順については、[このページ](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=ja#discover-control-panel)で詳しく説明しています。

1. **配信テンプレートの作成** - 新しいブランドが使用できるようになったら、この新しいブランドを参照する新しい空白の配信テンプレートを 1 つ以上作成することがベストプラクティスです。 [詳細情報](branding-assign.md)

1. **配信品質ガイドラインの確認** - 新しいドメインの使用を開始する前に、アドビの配信品質チームと戦略について相談する必要があります。 チームは、ベストプラクティスの定義（例えば、ドメイン間で IP を分割する新しいアフィニティを作成する必要があるかどうか、ランプアッププランを定義する必要があるかどうか）を支援します。
