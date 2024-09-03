---
title: ブランディング
description: ブランドの設定方法を確認
audience: administration
context-tags: branding,overview;branding,main
role: Admin
level: Experienced
badge: label="限定提供（LA）" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Campaign Standard移行済みユーザーに制限"
exl-id: 7afc802d-e90c-48c8-aa04-3ea543dfdfbc
source-git-commit: 62c2f2e7a6f5dd347749e963a655b717cd5c7310
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 42%

---

# ブランドの設定 {#branding-configure}

>[!IMPORTANT]
>
>ブランドは、エンドユーザーが作成または変更することはできません。これらの操作は、Adobe Campaign の技術管理者が実行する必要があります。ご要望がある場合は、アドビカスタマーケアにお問合せください。

Adobe Campaign V8 では、ブランドは **[!UICONTROL 管理/プラットフォーム/ブランディング]** メニューにあります。

**[!UICONTROL ブランドは]**、次の特性によって定義されます。

* **[!UICONTROL Identity]**：ブランドを定義しパーソナライズします。このセクションには、次のフィールドが含まれています。

   * **[!UICONTROL Label]**：インターフェイスに表示されます。
   * **[!UICONTROL ID]**
   * **[!UICONTROL Brand name]**
   * **[!UICONTROL Website URL]** と **[!UICONTROL Website label]**
   * **[!UICONTROL Logo URL]**

  ![](assets/branding_1.png)

* **[!UICONTROL 送信済みメールのヘッダーパラメーター]** キャンペーンの受信者に表示される内容をパーソナライズします。 このセクションには、次のフィールドが含まれています。

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

   * **[!UICONTROL ブランドサブドメイン]** とは、Adobeからのデリゲーションをリクエストされる、このブランドに固有の、指定されたサブドメイン URL を指します。

  トラッキング、ミラー、アプリケーションサーバーの設定は、ルーティングに関連付けられた個別の外部アカウントに保存されます。 これらの設定は、プロビジョニング中に適用されるので、変更しないでください。 URL を表示するには、外部アカウントから **[!UICONTROL ブランディングプレフィックス]** タブにアクセスします。

  ![](assets/branding_3.png)

* **[!UICONTROL トラッキング URL 設定]** メニューを使用すると、Adobe AnalyticsやGoogle Analyticsなどの web 分析ツールと統合するための追加パラメーターを定義することで、URL トラッキングを強化できます。

  **[!UICONTROL 追加の URL パラメーター]** メニューを使用して、追加のパラメーターをキーと値のペアとして、適用性の条件と共に作成します。 各パラメーター名は一意で、空であってはならず、各パラメーター値は空であってはなりません。 適用条件は空にすることができますが、これらの値には JST タグを含めることはできません。

  これらのパラメーターは、「**[!UICONTROL ドメイン名のリスト]**」で指定されたドメイン名に一致するトラッキング対象 URL に適用されます。ドメイン名には、正規表現を含めることができます。
