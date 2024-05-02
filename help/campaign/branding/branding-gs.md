---
title: ブランディング
description: ブランド ID の管理に使用できるすべてのツールを確認する
audience: administration
context-tags: branding,overview;branding,main
role: Admin
level: Experienced
badge: label="限定提供（LA）" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Campaign Standard移行済みユーザーに制限"
source-git-commit: 51abadc86b97097d13824651d8c50d4ddd014a51
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

1. **新しいサブドメインの設定** - Adobeで新しいサブドメインを使用する場合、最初の手順としてそのサブドメインを設定します。 これは、から実行できます。 [キャンペーンCampaign コントロールパネル](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/subdomains-branding.html?lang=ja) または、Adobeの技術担当者にお問い合わせください。 サブドメイン設定の詳細情報 [このページ内](https://experienceleague.adobe.com/en/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/campaign/ac-domain-name-setup).

   >[!NOTE]
   >
   >コントロールパネルは、すべての管理者ユーザーがアクセスできます。 ユーザーに管理者アクセス権を付与する手順については、[このページ](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=ja#discover-control-panel)で詳しく説明しています。

1. **配信テンプレートの作成**  – 新しいブランドが使用可能になったら、この新しいブランドを参照する新しい空白の配信テンプレートを 1 つ以上作成することをお勧めします。 [詳細情報](branding-assign.md)。

1. **配信品質のガイドラインの確認**  – 新しいドメインの使用を開始する前に、Adobe配信品質チームと戦略について話し合う必要があります。 ドメイン間で IP を分割するために新しいアフィニティを作成する必要がある場合（例：や、ランプアッププランを定義する必要がある場合）は、ベストプラクティスの定義に役立ちます。

