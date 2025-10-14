---
title: ブランディング
description: ブランド ID の管理に使用できるすべてのツールを確認する
audience: administration
context-tags: branding,overview;branding,main
role: Admin
level: Experienced
badge: label="限定提供（LA）" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Campaign Standard移行済みユーザーに制限"
exl-id: f6438303-5ae8-47c6-8c34-8e586f4b6fe7
source-git-commit: 34c6f8a137a9085b26c0ea8f78930cff6192cfc9
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 18%

---

# ブランディングの概要 {#branding-gs}

>[!IMPORTANT]
>
>ブランドは、エンドユーザーが作成または変更することはできません。これらの操作は、Adobe Campaign の技術管理者が実行する必要があります。ご要望がある場合は、アドビカスタマーケアにお問合せください。

どの会社にも、視覚的要素と技術的な詳細の両方を定義したブランドガイドラインがあります。 Adobe Campaignを使用すると、これらのガイドラインを一元管理できるので、メールのロゴやキャンペーンで使用される URL やドメインなど、すべての操作で、顧客に一貫したブランドイメージを提示できます。

技術管理者は、Adobe Campaign内で複数のブランドを作成および管理できます。 これにより、ロゴやメールトラッキング設定など、ブランド ID を構成するすべての要素を定義できます。 作成したブランドは、配信に簡単にリンクできます。

Campaign で組織の新しいエンティティを追加したり、新しいタイプのメールを作成したりできます。このメールは、別のサブドメインで送信する必要があります。 手順は次のとおりです。

1. **新しいサブドメインの設定** - Adobeで新しいサブドメインを使用する場合、最初の手順としてそのサブドメインを設定します。 これは、[Campaign Campaign コントロールパネル](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/subdomains-branding.html?lang=ja) を通じて実行するか、Adobeの技術担当者にお問い合わせください。 サブドメイン設定について詳しくは [&#x200B; このページ &#x200B;](https://experienceleague.adobe.com/ja/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/campaign/ac-domain-name-setup) を参照してください。

   >[!NOTE]
   >
   >コントロールパネルは、すべての管理者ユーザーがアクセスできます。 ユーザーに管理者アクセス権を付与する手順については、[このページ](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=ja#discover-control-panel)で詳しく説明しています。

1. **配信テンプレートの作成** – 新しいブランドが使用可能になったら、この新しいブランドを参照する新しい空白の配信テンプレートを少なくとも 1 つ作成することをお勧めします。 [詳細情報](branding-assign.md)

1. **配信品質のガイドラインを確認する** – 新しいドメインの使用を開始する前に、戦略についてAdobe配信品質チームに問い合わせる必要があります。 ドメイン間で IP を分割するために新しいアフィニティを作成する必要がある場合（例：や、ランプアッププランを定義する必要がある場合）は、ベストプラクティスの定義に役立ちます。
