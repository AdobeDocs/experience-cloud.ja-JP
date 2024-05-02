---
title: カスタムプロファイルディメンションの作成
description: カスタムプロファイルデータに基づいてカスタムプロファイルディメンションを作成する方法を説明します。
audience: reporting
content-type: reference
level: Intermediate
source-git-commit: 5a7337c44d6ca5ee4403d9fe0b65246b629afacd
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 3%

---

# カスタムプロファイルディメンションの作成{#creating-a-custom-profile-dimension}

レポートは、受信者スキーマの拡張時に作成したカスタムプロファイルデータに基づいて作成および管理することもできます。

* [手順 1：受信者スキーマを拡張する](##extend-schema)
* [手順 2：新しいカスタムフィールドをリンクする](#link-custom)
* [手順 3：カスタムプロファイルディメンションを使用して受信者をフィルタリングするための動的レポートの作成](#create-report)

## 手順 1：受信者スキーマを拡張する {#extend-schema}

新しいプロファイルフィールドを追加するには、スキーマを拡張する必要があります。次の手順に従います。

1. に移動します。 **[!UICONTROL 管理]** > **[!UICONTROL 設定]** > **[!UICONTROL データスキーマ]** エクスプローラーのフォルダー。

   ![](assets/custom_field_1.png)

1. カスタム受信者スキーマを特定して選択します。 組み込みの nms:recipient スキーマをまだ拡張していない場合は、を参照してください。 [この手順](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/shemas-forms/extend-schema).

1. カスタムフィールドをスキーマエディターに追加します。

   例えば、受信者スキーマにロイヤルティのカスタムフィールドを追加するには、次のようにします。

   ```
   <attribute label="Loyalty" name="loyalty" type="string"/>
   ```

   ![](assets/custom_field_2.png)

1. 「**[!UICONTROL 保存]**」をクリックします。

1. 次に、カスタム broadLogRcp スキーマを特定して選択します。 ビルトインの配信ログスキーマをまだ拡張していない場合は、次を参照してください。 [この手順](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/shemas-forms/extend-schema).

1. 受信者スキーマと同じカスタムフィールドをスキーマエディターに追加します。

   ![](assets/custom_field_3.png)

1. 「**[!UICONTROL 保存]**」をクリックします。

1. スキーマに加えた変更を適用するには、を使用してデータベースのアップデートウィザードを起動します。 **[!UICONTROL ツール]** > **[!UICONTROL 詳細]** > **[!UICONTROL データベース構造を更新]** データベース構造の更新を実行します。 [詳細情報](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/shemas-forms/update-database-structure)

   ![](assets/custom_field_4.png)

これで、受信者が新しいプロファイルフィールドを使用して選択する準備が整いました。

## 手順 2：新しいカスタムフィールドをリンクする {#link-custom}

>[!NOTE]
>
> 動的レポートには、最大 20 個のカスタムフィールドを追加できます。

プロファイルフィールドを作成したので、対応する動的レポートディメンションにリンクする必要があります。

1. に移動します。 **[!UICONTROL 管理]** > **[!UICONTROL 設定]** > **[!UICONTROL データスキーマ]** > **[!UICONTROL 追加のレポートフィールド]** エクスプローラーのフォルダー。

   ![](assets/custom_field_5.png)

1. クリック **[!UICONTROL 新規]** 対応する動的レポートディメンションを作成します。

1. を選択 **[!UICONTROL 式を編集]** そして、受信者スキーマを参照して、以前に作成したカスタムプロファイルフィールドを見つけます。

   ![](assets/custom_field_6.png)

1. 「**[!UICONTROL 完了]**」をクリックします。

1. ディメンションを入力 **[!UICONTROL ラベル]**（動的レポートに表示され、をクリックします） **[!UICONTROL 保存]**.

   ![](assets/custom_field_7.png)

カスタムプロファイルフィールドが、レポートのカスタムプロファイルディメンションとして使用できるようになりました。 カスタムプロファイルディメンションを削除するには、カスタムプロファイルディメンションを選択し、 **[!UICONTROL 削除]** アイコン。

これで、このプロファイルフィールドとカスタムディメンションを作成して受信者スキーマを拡張したので、配信での受信者のターゲティングを開始できます。

## 手順 3：カスタムプロファイルディメンションを使用して受信者をフィルタリングするための動的レポートの作成 {#create-report}

配信を送信したら、カスタムプロファイルディメンションを使用してレポートを分類できます。

1. から **[!UICONTROL 報告書]** タブを使用して標準提供のレポートを選択するか、 **[!UICONTROL 作成]** 最初から 1 つを開始するボタン。

   ![](assets/custom_field_8.png)

1. が含まれる **[!UICONTROL Dimension]** カテゴリ、クリック **[!UICONTROL Profile]** 次に、カスタムプロファイルディメンションをフリーフォームテーブルにドラッグ&amp;ドロップします。

   ![](assets/custom_field_9.png)

1. 指標をドラッグ&amp;ドロップして、データのフィルタリングを開始します。

1. 必要に応じて、ビジュアライゼーションをワークスペースにドラッグ&amp;ドロップします。
