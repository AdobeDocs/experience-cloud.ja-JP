---
title: 徐々にロールアウトする機能を設定する
description: Adobe Experience Rolloutsの機能フラグに対してパーセンテーションベースの段階的なロールアウトを設定する方法について説明します。
source-git-commit: 9bfe0e55e89c1d7fbd77cde63831a6a186820e24
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 3%

---


# 徐々にロールアウトする機能を設定する {#gradual-rollout-feature}

機能フラグのパーセンテージのロールアウトは、**基本詳細** タブで設定されます。 ロールアウトの進行状況に応じて、この値を上下に調整できます。

## 仕組み {#how-it-works}

ロールアウト率（25%など）を設定すると、定義したオーディエンスの割合が機能に公開されます。 残りの割合は&#x200B;**コントロールグループ**&#x200B;に配置され、デフォルトエクスペリエンスが受け取られます。

ロールアウトを拡大または縮小するには、時間の経過に伴って割合を増減できます。 パーセンテージを0%に減らすと、フラグを削除することなく、オーディエンス全員の機能が効果的にオフになります。

## 関連トピック {#see-also}

* [段階的な展開](../../concepts/gradual-rollout.md)
* [機能グループを設定し](set-feature-group-gradual-rollout.md)
* [最初の機能フラグを作成](create-your-first-feature-flag.md)
