---
title: Adobe Campaign Web ユーザーインターフェイス
description: 64 ビットテーブル
badge: label="限定提供" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Campaign Standard移行済みユーザーに制限"
exl-id: ab5f01fd-4ad5-46e9-b132-011fe0f7bbd2
source-git-commit: 6baa9bef7eae1ab8ffe9ecd426c6ba4580e8c9d7
workflow-type: tm+mt
source-wordcount: '175'
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
