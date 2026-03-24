---
title: 環境の概要
description: Adobe Experience ロールアウトのステージング環境と実稼動環境、および各環境を使用するタイミングについて説明します。
source-git-commit: 9bfe0e55e89c1d7fbd77cde63831a6a186820e24
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 4%

---


# 環境の概要 {#environments}

Experience Rolloutsには個別の環境が用意されているので、ライブユーザーに変更を反映させる前に機能フラグを検証できます。

## 利用可能な環境 {#available-environments}

| 環境 | 目的 |
|---|---|
| **ステージ** | テストと検証： この環境を使用して、実稼動環境で機能フラグを有効にする前に、機能フラグを設定してテストします。 |
| **本番** | ライブロールアウト： ここで設定された機能フラグは、実際のユーザーベースに対して評価されます。 |

>[!IMPORTANT]
>
>ステージで行った変更は、自動的に実稼動環境に引き継がれません。 機能フラグとオーディエンスルールは、各環境で個別に設定する必要があります。

## 環境の選択 {#selecting}

Experience Rollouts コンソールにログインした後、インターフェイスの上部にある環境スイッチャーから環境を選択します。 フィーチャーフラグを作成または変更する前に、正しい環境で作業していることを確認してください。

## ベストプラクティス {#best-practices}

設定エラーを回避し、本番オーディエンスを保護するには、次の推奨事項に従ってください。

* 常に最初に&#x200B;**ステージ**&#x200B;で機能フラグを作成してテストします。
* 実稼動環境でレプリケートする前に、ステージでオーディエンスルール、パーセンテージのロールアウト、ターゲティングロジックを検証します。
* [環境をまたいだワークフロー](../cross-environment/cross-environment-concept.md)を使用して、環境間でフラグのステータスを表示および管理します。

## 関連トピック {#see-also}

* [コンソールにログインします](log-in-to-the-console.md)
* [環境をアプリケーションに関連付ける](../cross-environment/associate-environments.md)
* [環境をまたいで機能フラグを表示](../cross-environment/view-feature-flags-across-environments.md)
