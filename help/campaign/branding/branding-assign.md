---
title: ブランディング
description: ブランドの割り当て方法を確認
audience: administration
context-tags: branding,overview;branding,main
role: Admin
level: Experienced
badge: label="限定提供（LA）" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Campaign Standard移行済みユーザーに制限"
exl-id: 8f6a5255-0245-497b-880f-d91ea82ee19e
source-git-commit: 62c2f2e7a6f5dd347749e963a655b717cd5c7310
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 19%

---

# ブランドの割り当て {#branding-assign}

## テンプレートへのブランドのリンク {#linking-a-brand-to-a-template}

ブランド用に定義したパラメーターを使用するには、配信テンプレートにリンクする必要があります。 それには、テンプレートを作成または編集する必要があります。

テンプレートはブランドにリンクされます。 メールエディターでは、「**Email address of default sender**」、「**Default sender name**」、「**Logo**」などの要素では、設定済みのブランドデータが使用されます。

>[!BEGINTABS]

>[!TAB Adobe Campaign V8]

配信テンプレートを作成するには、組み込みテンプレートの複製、既存の配信のテンプレートへの変換、最初からの配信テンプレートの作成を行います。 [詳細情報](https://experienceleague.adobe.com/ja/docs/campaign/campaign-v8/send/create-templates)

テンプレートを作成したら、それをブランドにリンクできます。その手順は次のとおりです。

1. Adobe Campaign エクスプローラーで、**[!UICONTROL リソース]**`>`**[!UICONTROL テンプレート]**`>`**[!UICONTROL 配信テンプレート]** を参照します。

1. 配信テンプレートを選択するか、既存の配信テンプレートを複製します。

   ![](assets/branding_assign_V8_1.png)

1. 選択した配信テンプレートの **[!UICONTROL プロパティ]** にアクセスします。

   ![](assets/branding_assign_V8_2.png)

1. 「**[!UICONTROL 一般]**」タブの「**[!UICONTROL ブランディング]**」ドロップダウンでブランドを選択します。

   ![](assets/branding_assign_V8_3.png)

1. 設定が完了したら「**OK**」を選択します。

これで、このテンプレートを使用して配信を送信できます。

>[!TAB Adobe Campaign Web]

配信テンプレートを作成するには、組み込みテンプレートの複製、既存の配信のテンプレートへの変換、最初からの配信テンプレートの作成を行います。 [詳細情報](https://experienceleague.adobe.com/ja/docs/campaign-web/v8/msg/delivery-template)

テンプレートを作成したら、それをブランドにリンクできます。その手順は次のとおりです。

1. **[!UICONTROL 配信]** 左側のメニューから「**[!UICONTROL テンプレート]**」タブを参照し、配信テンプレートを選択します。

   ![](assets/branding_assign_web_1.png)

1. 「**[!UICONTROL 設定]**」をクリックします。

   ![](assets/branding_assign_web_2.png)

1. 「**[!UICONTROL 配信]**」タブから「**[!UICONTROL ブランディング]**」フィールドにアクセスし、テンプレートにリンクするブランドを選択します。

   ![](assets/branding_assign_web_3.png)

1. 選択内容を確定し、テンプレートを保存します。

これで、このテンプレートを使用して配信を送信できます。

>[!ENDTABS]

## 配信へのブランドの割り当て {#assigning-a-brand-to-an-email}

>[!BEGINTABS]

>[!TAB Adobe Campaign V8]

新しいスタンドアロン配信を作成するには、次の手順に従います。

1. 新しい配信を作成するには、「**[!UICONTROL Campaigns]**」タブを参照します。

1. 「**[!UICONTROL 配信]**」をクリックし、既存の配信リストの上にある「**[!UICONTROL 作成]**」ボタンをクリックします。

   ![](assets/branding_assign_V8_4.png)

1. 配信テンプレートを選択します。

1. 選択した配信テンプレートの **[!UICONTROL プロパティ]** にアクセスします。

   ![](assets/branding_assign_V8_5.png)

1. 「**[!UICONTROL 一般]**」タブの「**[!UICONTROL ブランディング]**」ドロップダウンでブランドを選択します。

   ![](assets/branding_assign_V8_6.png)

1. 設定が完了したら「**OK**」を選択します。

1. 配信をさらにパーソナライズします。 メールの作成について詳しくは、[ メールのデザインと送信 ](https://experienceleague.adobe.com/ja/docs/campaign-web/v8/msg/email/create-email) の節を参照してください。

>[!TAB Adobe Campaign Web]

新しいスタンドアロン配信を作成するには、次の手順に従います。

1. 左側のパネルの **[!UICONTROL 配信]** メニューを参照し、「**[!UICONTROL 配信を作成]**」ボタンをクリックします。

   ![](assets/branding_assign_web_4.png)

1. 「メール」または「プッシュ通知」をチャネルとして選択し、リストから配信テンプレートを選択します。

1. 「**[!UICONTROL 配信を作成]**」ボタンをクリックして、確定します。

1. **[!UICONTROL プロパティ]** ページで、「**[!UICONTROL 設定]**」をクリックします。

   ![](assets/branding_assign_web_5.png)

1. 「**[!UICONTROL 配信]**」タブから、「**[!UICONTROL ブランディング]**」フィールドにアクセスします。

   ![](assets/branding_assign_web_6.png)

1. テンプレートにリンクするブランドを選択します。

   ![](assets/branding_assign_web_7.png)

1. 配信をさらにパーソナライズします。 メールの作成について詳しくは、[ 最初のメールの作成 ](https://experienceleague.adobe.com/ja/docs/campaign-web/v8/msg/email/create-email) の節を参照してください。

>[!ENDTABS]
