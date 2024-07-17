---
title: Adobe Campaign Web ユーザーインターフェイス
description: 64 ビットテーブル
badge: label="限定提供（LA）" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Campaign Standard移行済みユーザーに制限"
exl-id: ab5f01fd-4ad5-46e9-b132-011fe0f7bbd2
source-git-commit: 34c6f8a137a9085b26c0ea8f78930cff6192cfc9
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 7%

---

# 64 ビットスキーマ {#64-bit-tables}

Campaign Standardから Campaign v8 への移行を容易にするために、複数のテーブルが 32 ビットから 64 ビットに変更されました。 実際、Campaign Standardはいくつかの標準スキーマで 64 ビット PK をサポートしているのに対して、Campaign v8 はほとんどのスキーマで 32 ビット PK をサポートしています。

## 制限事項

* この技術的な変更は、Campaign Standardから移行するお客様にのみ適用されます。
* スキーマと broadlog の拡張は 64 ビットではサポートされていません。 それは 32 ビットのままになります。
* 技術ユーザーに送信された配信に関連するログは、Campaign v8 では使用できません。
* PostgreSQL のみがサポートされています。

## 変更されたスキーマ

次に、64 ビットに変更されたスキーマとその変更された属性のリストを示します。

| スキーマ名 | 属性名 |
|--- |--- |
| nms:broadLogRcp | ID |
| nms:trackingLogRcp | ID |
| nms:excludeLogRcp | ID |
| nms:broadLogVisit | ID |
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
| nms:webEvent | broadLogSrc-id、broadLogRemkt-id |
| nms:broadLogMid | mktBroadLogId |
| nms:mirrorPageSearch | remoteMessageId |
