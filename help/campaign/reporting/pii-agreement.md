---
title: 動的レポートの基本を学ぶ
description: 動的レポートの使用契約の詳細情報
level: Beginner
badge: label="限定提供" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Campaign Standard移行済みユーザーに制限"
audience: end-user
exl-id: 9fcef466-f306-480e-b42e-d18daa8bcf06
TQID: https://experienceleague.adobe.com/AGXqq-XOQU8SmHobDIA-nZqw3eNSa2THnw2jQQP54YA
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
feature_v2:
  - id: fdbb8fc9-ffa3-4b86-88fe-aa4c5a3e1bc6
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
level_v2:
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: ad84694f2f6f45e4ee30fc51379106835ac302be
workflow-type: tm+mt
source-wordcount: 549
ht-degree: 86%

---

# 動的レポートの使用契約 {#pii-agreement}

動的レポートの使用契約の目的は、データ処理のポップアップ同意として機能することです。 デフォルトでは、この契約書は表示のみ可能で、管理権限を割り当てられたユーザーのみが承諾または拒否できます。

動的レポートの使用契約にアクセスするには、**[!UICONTROL ツール]**／**[!UICONTROL 詳細]**／**[!UICONTROL デプロイメントウィザード]**&#x200B;を選択します。

![](assets/pii-agreement.png)

選択肢は次の 3 つあります。

* **[!UICONTROL 後で確認する]**：契約を承諾または拒否するまで、プロファイルディメンションはレポートに表示されず、顧客の個人情報は収集または送信されません。
* **[!UICONTROL 承諾する]**：本契約を承諾することにより、ユーザーは、Adobe Campaign が顧客の個人情報を収集し、それをレポートセンターまたはデータセンターに転送することを許可するものとします。
* **[!UICONTROL 拒否する]**：本契約を拒否すると、プロファイルディメンションはレポートに表示されず、顧客の個人情報は収集または送信されません。 この場合でも、externalID は引き続き収集され、エンドユーザーの識別に使用されます。

次の表には、この契約書を承諾した後に行われる内容が地域別に表示されています。

|  | 動的レポート | Microsoft Dynamics 365 コネクタ |
|---|---|---|
| 南北アメリカおよび APAC（アジア太平洋） | **利用可能な機能**。 <br>米国レポートセンターにプッシュされるすべての標準（市区町村、国／地域、都道府県、性別、年齢ベースのセグメント）およびカスタムのプロファイル。 | **利用可能な機能**。 <br>すべての標準およびカスタムのプロファイルフィールドとAdobe Campaign イベントフィールドは、米国データセンターで処理されます。 |
| EMEA（ヨーロッパ、中東、アフリカ） | **利用可能な機能**。 <br>EMEA レポートセンターにプッシュされるすべての標準（市区町村、国／地域、都道府県、性別、年齢ベースのセグメント）とカスタムのプロファイル。 | **機能を利用できます。** <br>すべての標準およびカスタムプロファイルフィールドと、EMEA データセンターで処理されたAdobe Campaign イベントフィールド。 米国データセンターで送信および保存される、Adobe I/O の登録データと顧客のエンドユーザーイベントの ID が含まれる<br>**[!UICONTROL コントロールデータ&#x200B;]**。 |

次の表には、この契約を拒否した後に行われる内容が地域別に表示されています。 この契約を拒否した場合でも、配信と Microsoft Dynamics 365 の統合に関するレポートは引き続き使用できます。

| 領域 | 動的レポート | Microsoft Dynamics 365 コネクタ |
|---|---|---|
| 南北アメリカおよび APAC（アジア太平洋） | **使用可能な機能**。<br> ExternalIDを除き、米国のレポートセンターにプッシュされる、すぐに使用できるカスタムプロファイル情報はありません。 | **利用可能な機能**。 <br>外部 ID と受信者 ID を除き、米国データセンターに送信される標準またはカスタムのプロファイルフィールドはありません。 <br>米国データセンターで処理されるすべての Adobe Campaign イベントフィールド（ミラーページ ID を除く）。 |
| EMEA（ヨーロッパ、中東、アフリカ） | **利用可能な機能**。 <br>ExternalID を除き、EMEA のレポートセンターにプッシュされる標準およびカスタムのプロファイル情報はありません。 | **機能を利用できます。** <br>外部IDと受信者IDを除き、標準またはカスタムのプロファイルフィールドをEMEA データセンターに送信しません。 <br>EMEA データセンターで処理されるすべての Adobe Campaign イベントフィールド（ミラーページ ID を除く）。 |

この選択は最終的なものではありません。**[!UICONTROL 管理]**／**[!UICONTROL プラットフォーム]**／**[!UICONTROL オプション]** の順にクリックし、**[!UICONTROL realtimeReporting_collectPII]** オプションを選択することで、いつでも変更できます。

この値はいつでも変更できます。 値 1 は&#x200B;**[!UICONTROL 後で確認する]**、値 2 は&#x200B;**[!UICONTROL 拒否する]**、値 3 は&#x200B;**[!UICONTROL 承諾する]**&#x200B;にそれぞれ対応します。
