---
title: 指標の計算
description: 各指標の式のリストを使用して、レポートの結果を把握できます。
level: Intermediate
audience: end-user
badge: label="限定提供（LA）" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Campaign Standard移行済みユーザーに制限"
source-git-commit: 031d5b692d9b9e4420b14ba1ab892fbafed57ec0
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 9%

---

# 指標の計算{#indicator-calculation}

>[!NOTE]
>
>大量の分析とリアルタイム分析をより適切に処理および管理するために、動的レポートでは個別カウントの予測に概算集計を使用します。 概算集計は、制限付きメモリ使用量を提供し、多くの場合、正確な計算よりも高速です。

次の表に、様々なレポートで使用される指標のリストと、配信タイプに応じた計算式を示します。

## メール配信 {#email-delivery}

<table> 
 <thead> 
  <tr> 
   <th> <strong>ラベル</strong> <br/> </th> 
   <th> <strong>フィールド名</strong> <br/> </th> 
   <th> <strong>指標の計算式</strong> <br/> </th> 
   <th> <strong>コメント</strong><br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 無効なアカウント<br/> </td> 
   <td> @disabled<br/> </td> 
   <td> count （@failureReason=4）<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> On^ブロックリスト<br/> </td> 
   <td> @blacklisted<br/> </td> 
   <td> count （@failureReason=8, @failureType=2）<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> ブロックリスト率<br/> </td> 
   <td> @rateBlacklisted<br/> </td> 
   <td> @blacklisted/@sent<br/> </td> 
   <td> レート計算の分母は、送信済みカウント（配信済み+ バウンス）に基づいています。<br/> </td> 
  </tr> 
  <tr> 
   <td> バウンス + エラー<br/> </td> 
   <td> @bounces<br/> </td> 
   <td> count （@status=2）<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> バウンス率+ エラー率<br/> </td> 
   <td> @rateBounces<br/> </td> 
   <td> @bounces/@sent<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> クリック<br/> </td> 
   <td> @clicks<br/> </td> 
   <td> count （@trackingUrlType=1 または 10 または 11）<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> クリックスルー率<br/> </td> 
   <td> @clickthrough<br/> </td> 
   <td> @uniqueclicks/@delivered<br/> </td> 
   <td> レート計算の分母は、配信済みに基づいています。<br/> </td> 
  </tr> 
  <tr> 
   <td> 配信済み<br/> </td> 
   <td> @delivered<br/> </td> 
   <td> count （@status=1）<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 配信率<br/> </td> 
   <td> @rateDelivered<br/> </td> 
   <td> @delivered/@sent<br/> </td> 
   <td> レート計算の分母は、送信済みカウント（配信済み+ バウンス）に基づいています。<br/> </td> 
  </tr> 
  <tr> 
   <td> ハードバウンス<br/> </td> 
   <td> @hardBounces<br/> </td> 
   <td> count （@failureType=2 および@failureReason=8）<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> ハードバウンス率<br/> </td> 
   <td> @rateHardBounces<br/> </td> 
   <td> @hardBounces/@sent<br/> </td> 
   <td> レート計算の分母は、送信済みカウント（配信済み+ バウンス）に基づいています。<br/> </td> 
  </tr> 
  <tr> 
   <td> 無効なドメイン<br/> </td> 
   <td> @invalidDomain<br/> </td> 
   <td> count （@failureReason=2）<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> メールボックス容量超過<br/> </td> 
   <td> @mailBoxFull<br/> </td> 
   <td> count （@failureReason=5）<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> ミラーページ<br/> </td> 
   <td> @mirrorPage<br/> </td> 
   <td> count （@trackingUrlType=6）<br/> </td> 
   <td> レート計算の分母は、配信済みに基づいています。<br/> </td> 
  </tr> 
  <tr> 
   <td> ミラーページ率<br/> </td> 
   <td> @rateMirrorPage<br/> </td> 
   <td> @mirrorPage/@delivered<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 未接続<br/> </td> 
   <td> @notConnected<br/> </td> 
   <td> count （@failureReason=6）<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 開封数<br/> </td> 
   <td> @uniqueOpens<br/> </td> 
   <td> count （@trackingUrlType=2 + unique （@trackingUrlType=1,2,3,6,10,11） - unique （@trackingUrlType=2））<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 開封率<br/> </td> 
   <td> @rateOpens<br/> </td> 
   <td> @opens/@delivered<br/> </td> 
   <td> レート計算の分母は、配信済みに基づいています。<br/> </td> 
  </tr> 
  <tr> 
   <td> 強制隔離<br/> </td> 
   <td> @quarantine<br/> </td> 
   <td> isQuarantine=true<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 強制隔離率<br/> </td> 
   <td> @rateQuarantine<br/> </td> 
   <td> @quarantine/@sent<br/> </td> 
   <td> レート計算の分母は、送信済みカウント（配信済み+ バウンス）に基づいています。<br/> </td> 
  </tr>
  <tr> 
   <td> 却下<br/> </td> 
   <td> @rejected<br/> </td> 
   <td> count （@failureReason=20, @failureType=2）<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 却下率<br/> </td> 
   <td> @rateRejected<br/> </td> 
   <td> @rejected/@sent<br/> </td> 
   <td> レート計算の分母は、送信済みカウント（配信済み+ バウンス）に基づいています。<br/> </td> 
  </tr> 
  <tr> 
   <td> 処理/送信済み<br/> </td> 
   <td> @sent<br/> </td> 
   <td> @delivered + @bounces<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> ソフトバウンス<br/> </td> 
   <td> @softBounces<br/> </td> 
   <td> count （@failureType=1）<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> ソフトバウンス率<br/> </td> 
   <td> @rateSoftBounces<br/> </td> 
   <td> @softBounces/@sent<br/> </td> 
   <td> レート計算の分母は、送信済みカウント（配信済み+ バウンス）に基づいています。<br/> </td> 
  </tr> 
  <tr> 
   <td> ユニーククリック数<br/> </td> 
   <td> @uniqueclicks<br/> </td> 
   <td> ユニーククリック数は、ThetaSketch の概念を使用して計算されます。 </a>.<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> ユニーク開封数<br/> </td> 
   <td> @uniqueopens<br/> </td> 
   <td> 一意（@trackingUrlType=1,2,3,6,10,11）<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 未到達 <br/> </td> 
   <td> @未到達<br/> </td> 
   <td> count （@failureReason=3）<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 購読解除<br/> </td> 
   <td> @unsubscribes<br/> </td> 
   <td> count （@trackingUrlType=3）<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 登録解除率<br/> </td> 
   <td> @rateUnsubscribes<br/> </td> 
   <td> @unsubscribes/@delivered<br/> </td> 
   <td> レート計算の分母は、配信済みに基づいています。<br/> </td> 
  </tr> 
  <tr> 
   <td> 不明なユーザー<br/> </td> 
   <td> @unknownUser<br/> </td> 
   <td> count （@failureReason=1）<br/> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

<!--
## Push notification delivery {#push-notification-delivery}

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br/> </th> 
   <th> <strong>Field name</strong> <br/> </th> 
   <th> <strong>Indicator calculation formula</strong> <br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Processed/sent<br/> </td> 
   <td> @sent<br/> </td> 
   <td> @count(status=sent)<br/> </td> 
  </tr> 
  <tr> 
   <td> Delivered<br/> </td> 
   <td> @delivered<br/> </td> 
   <td> @count(status=delivered)<br/> </td> 
  </tr> 
  <tr> 
   <td> Delivered rate<br/> </td> 
   <td> @rateDelivered<br/> </td> 
   <td> (@delivered/@sent)*100<br/> </td> 
  </tr> 
  <tr> 
   <td> Bounce + Error rate<br/> </td> 
   <td> @rateBounces<br/> </td> 
   <td> (@delivered/@sent)*100<br/> </td> 
  </tr> 
  <tr> 
   <td> Open<br/> </td> 
   <td> @opens<br/> </td> 
   <td> @count(status=open)<br/> </td> 
  </tr> 
  <tr> 
   <td> Open rate<br/> </td> 
   <td> @rateOpens<br/> </td> 
   <td> (@opens/@delivered)*100<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique opens<br/> </td> 
   <td> @uniqueopens<br/> </td> 
   <td> Unique opens is calculated using ThetaSketch concepts of unique RecipientIds.<br/> </td> 
  </tr> 
  <tr> 
   <td> Impressions<br/> </td> 
   <td> @impressions<br/> </td> 
   <td> @count(status=delivered)<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique impressions<br/> </td> 
   <td> @uniqueimpressions<br/> </td> 
   <td> @unique(@count(status=view))<br/> </td> 
  </tr> 
  <tr> 
   <td> Click<br/> </td> 
   <td> @clicks<br/> </td> 
   <td> @count(status=interact)<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique clicks<br/> </td> 
   <td> @uniqueclicks<br/> </td> 
   <td> Unique clicks is calculated using ThetaSketch concepts.<br/> </td> 
  </tr> 
  <tr> 
   <td> Click through rate<br/> </td> 
   <td> @clickthrough<br/> </td> 
   <td> (@interact/@delivered)*100<br/> </td> 
  </tr> 
 </tbody> 
</table>

## In-App delivery {#in-app-delivery}

<table> 
 <thead> 
  <tr> 
   <th> <strong>Label</strong> <br/> </th> 
   <th> <strong>Field name</strong> <br/> </th> 
   <th> <strong>Indicator calculation formula</strong> <br/> </th> 
   <th> <strong>Comments</strong><br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Processed/sent<br/> </td> 
   <td> @sent<br/> </td> 
   <td> @count(status=sent)<br/> </td> 
   <td> sent=delivered<br/> </td> 
  </tr> 
  <tr> 
   <td> Delivered<br/> </td> 
   <td> @delivered<br/> </td> 
   <td> @count(status=delivered)<br/> </td> 
   <td> delivered=sent<br/> </td> 
  </tr> 
  <tr> 
   <td> Impressions<br/> </td> 
   <td> @impressions<br/> </td> 
   <td> @count(status=view) or @count(status=button 1 click + button 2 click + dismissals)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Unique impressions<br/> </td> 
   <td> @uniqueimpressions<br/> </td> 
   <td> @unique(@count(status=view))<br/> </td> 
   <td> For <span class="uicontrol">Target users based on their Campaign profile (inAppProfile)</span> template, user = Recipient Id.<br/> For <span class="uicontrol">Target all users of a Mobile app (inAppBroadcast)</span> and <span class="uicontrol">Target users based on their Mobile profile (inApp)</span> templates, user = MC Id or equivalent that represents a unique combination of user, mobile app and device.<br/> </td> 
  </tr> 
  <tr> 
   <td> In-App clicks <br/> </td> 
   <td> @inappclicks<br/> </td> 
   <td> @count (status=click)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Unique In-App clicks<br/> </td> 
   <td> @uniqueinapp<br/> </td> 
   <td> @unique(@count (status=clicks))<br/> </td> 
   <td> For <span class="uicontrol">Target users based on their Campaign profile (inAppProfile)</span> template, user = Recipient Id.<br/> For <span class="uicontrol">Target all users of a Mobile app (inAppBroadcast)</span> and <span class="uicontrol">Target users based on their Mobile profile (inApp)</span> templates, user = MC Id or equivalent that represents a unique combination of user, mobile app and device.<br/> </td> 
  </tr> 
  <tr> 
   <td> In-App click through rate<br/> </td> 
   <td> @inappclickthrough<br/> </td> 
   <td> Total clicks on Button 1 or Button 2/total impressions*100<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> In-App dismissal<br/> </td> 
   <td> @dismissal<br/> </td> 
   <td> @count (status=close)<br/> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Unique In-App dismissals<br/> </td> 
   <td> @uniquedismissal<br/> </td> 
   <td> @unique(@count (status=close))<br/> </td> 
   <td> For <span class="uicontrol">Target users based on their Campaign profile (inAppProfile)</span> template, user = Recipient Id.<br/> For <span class="uicontrol">Target all users of a Mobile app (inAppBroadcast)</span> and <span class="uicontrol">Target users based on their Mobile profile (inApp)</span> templates, user = MC Id or equivalent that represents a unique combination of user, mobile app and device.<br/> </td> 
  </tr> 
  <tr> 
   <td> In-App dismissal rate<br/> </td> 
   <td> @dismissalrate<br/> </td> 
   <td> Total close/total impressions*100<br/> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>
-->