---
title: ブランディング
description: ブランドの割り当て方法について説明します。
audience: administration
context-tags: branding,overview;branding,main
role: Admin
level: Experienced
badge: label="限定提供" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Campaign Standard移行済みユーザーに制限"
exl-id: 8f6a5255-0245-497b-880f-d91ea82ee19e
TQID: https://experienceleague.adobe.com/aL-I6JknWhDoCob136gJB5Ier2a-T0oMiVFn1ZnRw0s
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
feature_v2:
  - id: fdbb8fc9-ffa3-4b86-88fe-aa4c5a3e1bc6
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: ad84694f2f6f45e4ee30fc51379106835ac302be
workflow-type: tm+mt
source-wordcount: 513
ht-degree: 94%

---

# ブランドの割り当て {#branding-assign}

## テンプレートへのブランドのリンク {#linking-a-brand-to-a-template}

ブランドに定義したパラメーターを使用するには、そのブランドが配信テンプレートにリンクされている必要があります。 それには、テンプレートを作成または編集する必要があります。

これで、テンプレートはブランドにリンクされます。 メールエディターでは、「**Email address of default sender**」、「**Default sender name**」、「**Logo**」などの要素では、設定済みのブランドデータが使用されます。

>[!BEGINTABS]

>[!TAB Adobe Campaign v8]

配信テンプレートを作成するには、組み込みテンプレートの複製、既存の配信のテンプレートへの変換またはゼロから配信テンプレートの作成を行います。 [詳細情報](https://experienceleague.adobe.com/ja/docs/campaign/campaign-v8/send/create-templates)

テンプレートを作成したら、それをブランドにリンクできます。 その手順は次のとおりです。

1. Adobe Campaign エクスプローラーで、**[!UICONTROL リソース]** `>` **[!UICONTROL テンプレート]** `>` **[!UICONTROL 配信テンプレート]**&#x200B;に移動します。

1. 配信テンプレートを選択するか、既存の配信テンプレートを複製します。

   ![](assets/branding_assign_V8_1.png)

1. 選択した配信テンプレートの&#x200B;**[!UICONTROL プロパティ]**&#x200B;にアクセスします。

   ![](assets/branding_assign_V8_2.png)

1. 「**[!UICONTROL 一般]**」タブの&#x200B;**[!UICONTROL ブランディング]**&#x200B;ドロップダウンからブランドを選択します。

   ![](assets/branding_assign_V8_3.png)

1. 設定が完了したら、「**OK**」を選択します。

これで、このテンプレートを使用して配信を送信できるようになりました。

>[!TAB Adobe Campaign web]

配信テンプレートを作成するには、組み込みテンプレートの複製、既存の配信のテンプレートへの変換またはゼロから配信テンプレートの作成を行います。 [詳細情報](https://experienceleague.adobe.com/ja/docs/campaign-web/v8/msg/delivery-template)

テンプレートを作成したら、それをブランドにリンクできます。 その手順は次のとおりです。

1. **[!UICONTROL 配信]**&#x200B;の左側のメニューから、「**[!UICONTROL テンプレート]**」タブに移動し、配信テンプレートを選択します。

   ![](assets/branding_assign_web_1.png)

1. 「**[!UICONTROL 設定]**」をクリックします。

   ![](assets/branding_assign_web_2.png)

1. 「**[!UICONTROL 配信]**」タブから、「**[!UICONTROL ブランディング]**」フィールドにアクセスし、テンプレートにリンクするブランドを選択します。

   ![](assets/branding_assign_web_3.png)

1. 選択内容を確定し、テンプレートを保存します。

これで、このテンプレートを使用して配信を送信できるようになりました。

>[!ENDTABS]

## 配信へのブランドの割り当て {#assigning-a-brand-to-an-email}

>[!BEGINTABS]

>[!TAB Adobe Campaign v8]

新しいスタンドアロン配信を作成するには、次の手順に従います。

1. 新しい配信を作成するには、「**[!UICONTROL キャンペーン]**」タブに移動します。

1. 「**[!UICONTROL 配信]**」をクリックし、既存の配信リストの上にある「**[!UICONTROL 作成]**」ボタンをクリックします。

   ![](assets/branding_assign_V8_4.png)

1. 配信テンプレートを選択します。

1. 選択した配信テンプレートの&#x200B;**[!UICONTROL プロパティ]**&#x200B;にアクセスします。

   ![](assets/branding_assign_V8_5.png)

1. 「**[!UICONTROL 一般]**」タブの&#x200B;**[!UICONTROL ブランディング]**&#x200B;ドロップダウンからブランドを選択します。

   ![](assets/branding_assign_V8_6.png)

1. 設定が完了したら、「**OK**」を選択します。

1. 配信をさらにパーソナライズします。 メールの作成について詳しくは、[メールのデザインと送信](https://experienceleague.adobe.com/en/docs/campaign-web/v8/msg/email/create-email)の節を参照してください。

>[!TAB Adobe Campaign web]

新しいスタンドアロン配信を作成するには、次の手順に従います。

1. 左側のパネルの&#x200B;**[!UICONTROL 配信]**&#x200B;メニューを参照し、「**[!UICONTROL 配信を作成]**」ボタンをクリックします。

   ![](assets/branding_assign_web_4.png)

1. 「メール」または「プッシュ通知」をチャネルとして選択し、リストから配信テンプレートを選択します。

1. 「**[!UICONTROL 配信を作成]**」ボタンをクリックして、確定します。

1. **[!UICONTROL プロパティ]**&#x200B;ページから、「**[!UICONTROL 設定]**」をクリックします。

   ![](assets/branding_assign_web_5.png)

1. 「**[!UICONTROL 配信]**」タブから、「**[!UICONTROL ブランディング]**」フィールドにアクセスします。

   ![](assets/branding_assign_web_6.png)

1. テンプレートにリンクするブランドを選択します。

   ![](assets/branding_assign_web_7.png)

1. 配信をさらにパーソナライズします。 メールの作成について詳しくは、[最初のメールの作成](https://experienceleague.adobe.com/en/docs/campaign-web/v8/msg/email/create-email)の節を参照してください。

>[!ENDTABS]
