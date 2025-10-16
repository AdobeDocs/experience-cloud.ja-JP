---
title: Adobe Campaign Web ユーザーインターフェイス
description: 64 ビットテーブル
badge: label="限定提供（LA）" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Campaign Standardに移行されたユーザーに制限"
exl-id: ab5f01fd-4ad5-46e9-b132-011fe0f7bbd2
source-git-commit: 11c49b273164b632bcffb7de01890c6f9d7ae9c2
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 18%

---

# 64 ビットスキーマ {#sixty-four-bit-tables}

Campaign Standardから Campaign v8 への移行を容易にするために、複数のテーブルが 32 ビットから 64 ビットに変更されました。 実際、Campaign Standardは、いくつかの標準スキーマで 64 ビット PK をサポートしているのに対して、Campaign v8 は、ほとんどのスキーマで 32 ビット PK をサポートしています。

## 制限および制約事項

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
| nms:webEvent | broadLogSrc-id、broadLogRemkt-id |
| nms:broadLogMid | mktBroadLogId |
| nms:mirrorPageSearch | remoteMessageId |
