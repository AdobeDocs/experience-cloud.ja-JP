---
title: ブランディング
description: ブランドの設定方法について説明します。
audience: administration
context-tags: branding,overview;branding,main
role: Admin
level: Experienced
badge: label="限定提供" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Campaign Standard移行済みユーザーに制限"
exl-id: 7afc802d-e90c-48c8-aa04-3ea543dfdfbc
TQID: https://experienceleague.adobe.com/hnN2EgVkkBA0Zp6NYqk2ID2XgHjv1EBDrWRW7k7qJ7Q
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
source-wordcount: 380
ht-degree: 97%

---

# ブランドの設定 {#branding-configure}

>[!IMPORTANT]
>
>ブランドは、エンドユーザーが作成または変更することはできません。これらの操作は、Adobe Campaign の技術管理者が実行する必要があります。 ご要望がある場合は、アドビカスタマーケアにお問合せください。

Adobe Campaign v8 では、ブランドは&#x200B;**[!UICONTROL 管理／プラットフォーム／ブランディング]**&#x200B;メニューにあります。

**[!UICONTROL ブランドは]**、次の特性によって定義されます。

* **[!UICONTROL Identity]**：ブランドを定義しパーソナライズします。 このセクションには、次のフィールドが含まれています。

   * **[!UICONTROL Label]**：インターフェイスに表示されます。
   * **[!UICONTROL ID]**
   * **[!UICONTROL Brand name]**
   * **[!UICONTROL Website URL]** と **[!UICONTROL Website label]**
   * **[!UICONTROL Logo URL]**

  ![](assets/branding_1.png)

* **[!UICONTROL 送信メールのヘッダーパラメーター]**：キャンペーンの受信者に表示される内容をパーソナライズします。 このセクションには、次のフィールドが含まれています。

   * **[!UICONTROL Sender (email address)]**：ブランドの電子メールアドレスです。
   * **[!UICONTROL Sender (name)]**：ブランドの名前です。
   * **[!UICONTROL Reply to (email address)]**：ユーザーからの返信先のメールアドレスです。
   * ブランド名を含む&#x200B;**[!UICONTROL Reply to (name)]**：ユーザーからの返信先（ブランド）の名前です。
   * **[!UICONTROL ）Error (email address)]**：エラーの場合に使用するメールアドレスです。

  >[!IMPORTANT]
  >
  >メールのヘッダーパラメーターを更新した後、送信者の名前とメールアドレスが、テンプレートから作成されたメール内で変更されていない場合は、テンプレートの詳細設定を確認します。

  ![](assets/branding_2.png)

* **[!UICONTROL ブランド設定]**：ランディングページへのアクセスのトラッキングにも使用するサーバーを定義します。 このセクションには、次のフィールドが含まれています。

   * **[!UICONTROL ブランドサブドメイン]**：アドビからのデリゲーションをリクエストされた、このブランドに固有の指定されたサブドメイン URL を指します。

  トラッキング、ミラー、アプリケーションサーバーの設定は、ルーティングに関連付けられた個別の外部アカウントに保存されます。 これらの設定は、プロビジョニング中に適用されるので、変更しないでください。 URL を表示するには、外部アカウントから「**[!UICONTROL ブランディングプレフィックス]**」タブにアクセスします。

  ![](assets/branding_3.png)

* **[!UICONTROL トラッキング URL 設定]**&#x200B;メニューを使用すると、Adobe Analytics や Google Analytics などの web 分析ツールとの統合の追加パラメーターを定義して、URL トラッキングを強化できます。

  **[!UICONTROL 追加の URL パラメーター]**&#x200B;メニューを使用して、適用条件と共にキーと値のペアとして追加のパラメーターを作成します。 各パラメーター名は一意で空でない必要があり、各パラメーター値は空でない必要があります。 適用条件は空にすることができますが、これらの値には JST タグを含めることはできません。

  これらのパラメーターは、**[!UICONTROL ドメイン名のリスト]**&#x200B;で指定したドメイン名（正規表現を含めることができる）に一致するトラッキング対象 URL に適用されます。
