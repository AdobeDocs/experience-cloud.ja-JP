---
title: バウンス概要
description: 標準のバウンス概要レポートでは、送信済みキャンペーンのステータスと、発生した可能性のあるエラーについて確認できます。
audience: end-user
level: Intermediate
badge: label="限定提供" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Campaign Standard移行済みユーザーに制限"
exl-id: b341edad-aa82-43d8-a5a1-b33a19973a1a
TQID: https://experienceleague.adobe.com/gfOXWpdQvONw72sdpnGehwpXcgte16B6dLiWV2LZXOc
product_v2: id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: ad84694f2f6f45e4ee30fc51379106835ac302be
workflow-type: tm+mt
source-wordcount: 298
ht-degree: 97%

---

# バウンス概要{#bounce-summary}

このレポートには、配信中に発生したハードエラーとソフトエラーの全般、およびバウンスの自動処理の詳細が記載されます。

![](assets/campaign_reports_bounces.png)

各テーブルは、概要の数値とグラフで表されています。 それぞれのビジュアライゼーション設定で、詳細の表示方法を変更できます。

**フロップ 5 の再区分**&#x200B;には、強制隔離数が最も多い 5 つの配信が一覧表示されます。

**バウンスの理由**&#x200B;テーブルには、各配信でバウンスの原因となったエラーの種類に関する利用可能なデータが含まれています。

* **[!UICONTROL 不明なユーザー]**：配信が無効なメールアドレスに送信されたときに生成されるエラーの種類。
* **[!UICONTROL 無効なドメイン]**：ドメインが正しくないか、存在しないメールアドレスに配信が送信されたときに生成されるエラーの種類。
* **[!UICONTROL 未到達]**：ドメインに一時的にアクセスできないなど、メッセージ配信文字列で発生したエラーの種類。
* **[!UICONTROL 無効なアカウント]**：存在しないメールアドレスに配信が送信された場合に生成されるエラーの種類。
* **[!UICONTROL メールボックス容量超過]**：受信者のインボックスがいっぱいであるときに生成されるエラーの種類。 このエラーが生成されるまで、メッセージを配信する試みは 5 回あります。
* **[!UICONTROL 未接続]**：受信者の携帯電話がオフになっているか、メッセージの送信時にネットワークに接続されていない場合に生成されるエラーの種類。

  >[!NOTE]
  >
  >この種のエラーは、モバイルチャネルでの配信のみに該当します。

* **[!UICONTROL 拒否]**：アドレスがインターネットサービスプロバイダー（ISP）によって拒否される場合に生成されるエラーの種類。 例えば、スパム対策ソフトウェアによってセキュリティルールが適用された場合などです。

**ドメインの再区分**&#x200B;テーブルには、受信者ドメインに応じた、配信中に発生した全体的な問題が表示されます。
