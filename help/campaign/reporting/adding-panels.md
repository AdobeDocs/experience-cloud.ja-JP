---
title: パネルの追加
description: 動的レポートを使用すると、パネルを追加して、選択した期間に応じてデータをより適切にフィルタリングできます。
audience: end-user
badge: label="限定提供（LA）" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Campaign Standard移行済みユーザーに制限"
level: Intermediate
source-git-commit: 3f4400f24b75e8e435610afbe49e9d9444dbf563
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 1%

---

# パネルの追加{#adding-panels}

## 空のパネルの追加 {#adding-a-blank-panel}

レポートを開始するには、一連のパネルを標準またはカスタムレポートに追加します。 各パネルには、様々なデータセットが含まれ、フリーフォームテーブルおよびビジュアライゼーションで構成されます。

このパネルを使用すると、必要に応じてレポートを作成できます。 異なる期間でデータをフィルタリングするために、レポートに必要な数のパネルを追加できます。

1. 「」をクリックします **パネル** アイコン。 をクリックしてパネルを追加することもできます **「挿入」タブ** および選択 **新しい空のパネル**.

   ![](assets/dynamic_report_panel_1.png)

1. をドラッグ&amp;ドロップ **空のパネル** をダッシュボードに追加します。

   ![](assets/dynamic_report_panel.png)

これで、フリーフォームテーブルをパネルに追加して、データのターゲット設定を開始できます。

## フリーフォームテーブルの追加 {#adding-a-freeform-table}

フリーフォームテーブルを使用すると、で使用可能な様々な指標やディメンションを使用して、データを分析するテーブルを作成できます **コンポーネント** テーブル。

各テーブルとビジュアライゼーションはサイズ変更可能で、移動してレポートをカスタマイズできます。

1. 「」をクリックします **[!UICONTROL パネル]** アイコン。

   ![](assets/dynamic_report_panel_1.png)

1. をドラッグ&amp;ドロップ **[!UICONTROL フリーフォーム]** 項目をダッシュボードに追加します。

   をクリックしてテーブルを追加することもできます **[!UICONTROL 挿入]** タブと選択 **[!UICONTROL 新しいフリーフォーム]** または、 **[!UICONTROL フリーフォームテーブルの追加]** 空のパネルに移動します。

   ![](assets/dynamic_report_panel_2.png)

1. が含まれる **[!UICONTROL ここにセグメントをドロップ]** フィールド、を追加 **[!UICONTROL セグメント]** から **[!UICONTROL Components]** 上部バーに Tab キーを押します。

   ![](assets/dynamic_report_panel_3.png)

1. からの項目のドラッグ&amp;ドロップ **[!UICONTROL Components]** 列と行に Tab キーを押して、テーブルを作成します。

   ![](assets/dynamic_report_freeform_3.png)

1. 「」をクリックします **[!UICONTROL 設定]** アイコンをクリックして、列でのデータの表示方法を変更します。

   ![](assets/dynamic_report_freeform_4.png)

   この **[!UICONTROL 列設定]** 次の要素で構成されます。

   * **[!UICONTROL 数値]**：列の概要数値の表示と非表示を切り替えることができます。
   * **[!UICONTROL 割合]**：列内のパーセントの表示と非表示を切り替えることができます。
   * **[!UICONTROL ゼロを値なしで解釈]**：値が 0 に等しい場合に表示または非表示にできます。
   * **[!UICONTROL 背景・経緯]**：セル内の水平プログレスバーの表示と非表示を切り替えることができます。
   * **[!UICONTROL 再試行を含める]**：再試行を結果に含めることができます。 これは、次の場合にのみ使用できます **[!UICONTROL 送信済み]** および **[!UICONTROL バウンス + エラー]**.

1. 1 つまたは複数の行を選択し、 **[!UICONTROL 視覚化]** アイコン。 ビジュアライゼーションが追加され、選択した行が反映されます。

   ![](assets/dynamic_report_freeform_5.png)

必要な数のコンポーネントを追加し、ビジュアライゼーションを追加して、データをグラフで表示できるようになりました。
