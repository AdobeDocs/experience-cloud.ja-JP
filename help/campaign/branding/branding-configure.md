---
title: ブランディング
description: ブランドの設定方法を確認
audience: administration
context-tags: branding,overview;branding,main
role: Admin
level: Experienced
badge: label="限定提供（LA）" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Campaign Standard移行済みユーザーに制限"
source-git-commit: 56f2d2ff4b2ba4184629615a14724e6640df6961
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 57%

---

# ブランドの設定 {#branding-configure}

>[!IMPORTANT]
>
>ブランドは、エンドユーザーが作成または変更することはできません。これらの操作は、Adobe Campaign の技術管理者が実行する必要があります。ご要望がある場合は、アドビカスタマーケアにお問合せください。

Adobe Campaign V8 では、Brands は以下で見つけることができます。 **[!UICONTROL 管理/ プラットフォーム / ブランディング]** メニュー。

**[!UICONTROL ブランドは]**、次の特性によって定義されます。

* **[!UICONTROL Identity]**：ブランドを定義しパーソナライズします。このセクションには、次のフィールドが含まれています。

   * **[!UICONTROL Label]**：インターフェイスに表示されます。
   * **[!UICONTROL ID]**
   * **[!UICONTROL Brand name]**
   * **[!UICONTROL Website URL]** と **[!UICONTROL Website label]**
   * **[!UICONTROL Logo URL]**

  ![](assets/branding_1.png)

* **[!UICONTROL 送信済み E メールのヘッダーパラメーター]** これにより、キャンペーンの受信者に表示される内容がパーソナライズされます。 このセクションには、次のフィールドが含まれています。

   * **[!UICONTROL Sender (email address)]**：ブランドの電子メールアドレスです。
   * **[!UICONTROL Sender (name)]**：ブランドの名前です。
   * **[!UICONTROL Reply to (email address)]**：ユーザーからの返信先のメールアドレスです。
   * ブランド名を含む&#x200B;**[!UICONTROL Reply to (name)]**：ユーザーからの返信先（ブランド）の名前です。
   * **[!UICONTROL ）Error (email address)]**：エラーの場合に使用するメールアドレスです。

  >[!IMPORTANT]
  >
  >メールのヘッダーパラメーターを更新した後、送信者の名前とメールアドレスが、テンプレートから作成されたメール内で変更されていない場合は、テンプレートの詳細設定を確認します。

  ![](assets/branding_2.png)

* **[!UICONTROL ブランド設定]** ランディングページアクセスのトラッキングにも使用するサーバーを定義します。 このセクションには、次のフィールドが含まれています。

   * **[!UICONTROL ブランドサブドメイン]** は、Adobeからのデリゲーションをリクエストされた、このブランドに固有の、指定されたサブドメイン URL を参照します。

  トラッキング、ミラー、アプリケーションサーバーの設定は、ルーティングに関連付けられた個別の外部アカウントに保存されます。 これらの設定は、プロビジョニング中に適用されるので、変更しないでください。 URL を表示するには、にアクセスします **[!UICONTROL ブランディングプレフィックス]** 外部アカウントから tab キーを押します。

  ![](assets/branding_3.png)

<!--![](assets/branding_05.png)-->

<!--
* **[!UICONTROL Tracking URL configs]**, which defines the configuration of the URLs tracking for your brand.

  The additional parameters that allow the links to be tracked on external systems such as Web Analytics tools like Adobe Analytics or Google Analytics are defined here.
-->
