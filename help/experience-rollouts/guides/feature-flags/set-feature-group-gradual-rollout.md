---
title: 機能グループを設定し
description: Adobe Experience Rolloutsの機能グループに対してパーセンテーションベースの段階的なロールアウトを設定する方法について説明します。
hide: true
exl-id: fcf187f1-2f33-4e3a-b740-985d5bc0bcdc
source-git-commit: 12032cbed45e694a3f25f16afe80308b3eb82924
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 3%

---

# 機能グループを設定し {#gradual-rollout-feature-group}

機能グループのロールアウト率は、**基本詳細** タブで設定されています。 ロールアウトの進行状況に応じて、この値を上下に調整できます。

## 仕組み {#how-it-works}

ロールアウトの割合（60%など）を設定すると、定義したオーディエンスのその割合が機能グループに公開されます。 残りの40%は&#x200B;**コントロールグループ**&#x200B;に配置され、デフォルトの動作が適用されます。

複数のバリエーションを設定した場合（A/B テスト用）、露出の割合はバリエーション間で均等に分配されます。 例えば、3つのバリアントで60%の暴露は、1つのバリアントにつき20%、コントロール群では40%になる。

ロールアウトを拡張、縮小、または一時停止するには、いつでもパーセンテージを増減できます。

## 関連トピック {#see-also}

* [機能グループの作成](create-a-feature-group.md)
* [機能フラグによるA/B テスト](a-b-testing.md)
* [段階的な展開](../../concepts/gradual-rollout.md)

<!-- -->
