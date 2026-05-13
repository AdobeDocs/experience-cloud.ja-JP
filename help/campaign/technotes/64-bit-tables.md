---
title: Adobe Campaign Web ユーザーインターフェイス
description: 64 ビットテーブル
badge: label="限定提供" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Campaign Standard移行済みユーザーに制限"
exl-id: ab5f01fd-4ad5-46e9-b132-011fe0f7bbd2
TQID: https://experienceleague.adobe.com/D0f4gYkyUcNVpGxpvj3JrBGRyIAgSq1mF7R4ld5COmk
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
source-git-commit: ad84694f2f6f45e4ee30fc51379106835ac302be
workflow-type: tm+mt
source-wordcount: 175
ht-degree: 17%

---

# 64 ビットスキーマ {#sixty-four-bit-tables}

Campaign StandardからCampaign v8への移行を容易にするために、いくつかのテーブルが32 ビットから64 ビットに変更されました。 実際、Campaign Standardでは、64 ビット PKを複数の標準スキーマでサポートしていますが、Campaign v8ではほとんどのスキーマで32 ビット PKをサポートしています。

## 制限事項

* この技術的な変更は、Campaign Standardから移行するお客様にのみ適用されます。
* スキーマおよびブロードログ拡張は、64 ビットではサポートされていません。 それは32 ビットのままになります。
* テクニカルユーザーに送信された配信に関連するログは、Campaign v8では使用できません。
* PostgreSQLのみがサポートされます。

## 変更されたスキーマ

以下は、64 ビットに変更されたスキーマとその変更された属性のリストです。

| スキーマ名 | 属性名 |
|--- |--- |
| nms:broadLogRcp | ID |
| nms:trackingLogRcp | ID |
| nms:excludeLogRcp | ID |
| nms:broadLogVisitor | ID |
| nms:trackingLogVisitor | ID |
| nms:propositionRcp | interactionId |
| nms:propositionVisitor | interactionId |
| nms:webTrackingLog | ID |
| nms:tmpBroadcast | message-id |
| nms:tmpMarketingPressure | message-id |
| nms:tmpBroadcastExclusion | message-id |
| nms:tmpBroadcastPaper | message-id |
| nms:broadLogAppSubRcp | ID |
| nms:trackingLogAppSubRcp | ID |
| nms:excludeLogAppSubRcp | ID |
| nms:webEvent | broadLogSrc-id, broadLogRemkt-id |
| nms:broadLogMid | mktBroadLogId |
| nms:mirrorPageSearch | remoteMessageId |
