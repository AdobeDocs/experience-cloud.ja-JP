---
title: コンポーネントのリスト
description: で使用可能なすべてのコンポーネントのリストを以下に示します     動的レポートとその定義。
level: Beginner
audience: end-user
badge: label="限定提供（LA）" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Campaign Standard移行済みユーザーに制限"
exl-id: 5c58db92-7878-4c70-b076-a393f1cda8b7
source-git-commit: 34c6f8a137a9085b26c0ea8f78930cff6192cfc9
workflow-type: tm+mt
source-wordcount: '770'
ht-degree: 15%

---

# コンポーネントのリスト {#list-of-components}

2 つのコンポーネントに互換性がない場合、セルには値 **なし** が表示されます。

## ディメンション {#dimensions}

次の表に、レポートで使用されるディメンションとその定義のリストを示します。

<table> 
 <thead> 
  <tr> 
   <th> Dimension<br/> </th> 
   <th> 定義<br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> ブラウザー <br/> </td> 
   <td> メッセージを開いた、またはクリックしたブラウザー。<br/> </td> 
  </tr> 
  <tr> 
   <td> Campaign<br/> </td> 
   <td> キャンペーンのラベルと ID。<br/> </td> 
  </tr> 
  <tr> 
   <td> 配信<br/> </td> 
   <td> 配信のラベルと ID。<br/> </td> 
  </tr> 
  <tr> 
   <td> デバイス <br/> </td> 
   <td> メール / SMS / プッシュ通知が開封/表示/クリックされた元のデバイス。<br/> </td> 
  </tr> 
  <tr> 
   <td> エラーの理由 <br/> </td> 
   <td> 各配信でバウンスを発生させたエラーのタイプ （不明なユーザー、無効なドメイン、メールボックス容量超過など）。<br/> </td> 
  </tr> 
  <tr> 
   <td> モバイルアプリ名 <br/> </td> 
   <td> モバイルアプリケーションの名前 <br/> </td> 
  </tr>
  <tr> 
   <td> プラットフォーム <br/> </td> 
   <td> メッセージが開封/表示/クリックされた元のデバイスのプラットフォーム。<br/> </td> 
  </tr> 
  <tr> 
   <td> プロファイル <br/> </td> 
   <td> プロファイルリソースの拡張時に作成された標準およびカスタムプロファイルフィールドを再グループ化します。<br/> </td> 
  </tr> 
  <tr> 
   <td> 受信者ドメイン <br/> </td> 
   <td> メールを開くために使用されるドメイン。<br/> </td> 
  </tr> 
  <tr> 
   <td> 繰り返し配信<br/> </td> 
   <td> 繰り返し配信のラベルと ID。<br/> </td> 
  </tr> 
  <tr> 
   <td> 送信者ドメイン <br/> </td> 
   <td> E メールの送信に使用されるドメイン。<br/> </td> 
  </tr> 
  <tr> 
   <td> 送信者 IP<br/> </td> 
   <td> E メールの送信に使用する IP。<br/> </td> 
  </tr> 
  <tr> 
   <td> トラッキング URL<br/> </td> 
   <td> ユーザーがメッセージからクリックした URL。<br/> </td> 
  </tr> 
  <tr> 
   <td> トラッキング URL カテゴリ <br/> </td> 
   <td> トラッキング URL に割り当てられているカテゴリ。<br/> </td> 
  </tr> 
  <tr> 
   <td> トラッキング URL ラベル <br/> </td> 
   <td> ミラーページ、お問い合わせ、オープンなど、URL に付与されるラベル。<br/> </td> 
  </tr> 
  <tr> 
   <td> トランザクション配信 <br/> </td> 
   <td> トランザクション配信のラベルと ID。<br/> </td> 
  </tr> 
  <tr> 
   <td> バリアント型 <br/> </td> 
   <td> A/B テストの場合の E メールのバリアント。<br/> </td> 
  </tr> 
 </tbody> 
</table>

## 指標 {#metrics}

次の表に、レポートで使用される指標のリストと、配信タイプに応じた定義を示します。

### メール指標 {#email-and-sms-metrics}

<table> 
 <thead> 
  <tr> 
   <th> 指標<br/> </th> 
   <th> 定義<br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> On^ブロックリスト<br/> </td> 
   <td> E メールをスパムまたはジャンクとして宣言した受信者の数。<br/> </td> 
  </tr> 
  <tr> 
   <td> ブロックリスト率 <br/> </td> 
   <td> マークされた配信の割合（^ブロックリスト.<br/>） </td> 
  </tr> 
  <tr> 
   <td> バウンス + エラー <br/> </td> 
   <td> 送信されたメッセージの総数に対して、配信と自動返信の処理中に発生したエラーの累計。<br/> </td> 
  </tr> 
  <tr> 
   <td> バウンス率+ エラー率 <br/> </td> 
   <td> 送信メールに対するバウンスメールの割合。<br/> </td> 
  </tr> 
  <tr> 
   <td> クリック <br/> </td> 
   <td> 配信でコンテンツがクリックされた回数。<br/> </td> 
  </tr> 
  <tr> 
   <td> クリックスルー率 <br/> </td> 
   <td> 配信でのクリック率。<br/> </td> 
  </tr> 
  <tr> 
   <td> 配信済み<br/> </td> 
   <td> 送信されたメッセージの総数に対する、正常に送信されたメッセージの数。<br/> </td> 
  </tr> 
  <tr> 
   <td> 配信率 <br/> </td> 
   <td> 正常に送信されたメッセージの割合。<br/> </td> 
  </tr> 
  <tr> 
   <td> ハードバウンス<br/> </td> 
   <td> 永続的なエラー（メールアドレスの間違いなど）の合計数。<br/> </td> 
  </tr> 
  <tr> 
   <td> ハードバウンス率 <br/> </td> 
   <td> 永続的なエラーが原因で失敗した配信の割合。<br/> </td> 
  </tr> 
  <tr> 
   <td> ミラーページ <br/> </td> 
   <td> ミラーページのリンクをクリックした受信者の数。<br/> </td> 
  </tr> 
  <tr> 
   <td> ミラーページ率 <br/> </td> 
   <td> 合計配信メッセージに対する、ミラーページリンクのクリック数の割合。<br/> </td> 
  </tr> 
  <tr> 
   <td> オファークリック数 <br/> </td> 
   <td> 配信でオファーがクリックされた回数。<br/> </td> 
  </tr> 
  <tr> 
   <td> オファークリック率<br/> </td> 
   <td> オファーのクリック率。<br/> </td> 
  </tr> 
  <tr> 
   <td> 開封数<br/> </td> 
   <td> 配信でメッセージが開かれた回数。<br/> </td> 
  </tr> 
  <tr> 
   <td> 開封率<br/> </td> 
   <td> 開封されたメッセージの割合。<br/> </td> 
  </tr> 
  <tr> 
   <td> 処理済み/送信済み <br/> </td> 
   <td> 配信の送信の合計数。<br/> </td> 
  </tr> 
  <tr> 
   <td> 強制隔離 <br/> </td> 
   <td> バウンスし、アドレスの強制隔離に至ったメッセージの数。<br/> </td> 
  </tr> 
  <tr> 
   <td> 強制隔離率 <br/> </td> 
   <td> 送信されたメッセージに対する強制隔離の割合。<br/> </td> 
  </tr> 
  <tr> 
   <td> 却下<br/> </td> 
   <td> SMTP サーバーによってスパムとして分類されたメッセージの数。<br/> </td> 
  </tr> 
  <tr> 
   <td> 却下率 <br/> </td> 
   <td> 拒否とマークされたメッセージの割合。<br/> </td> 
  </tr> 
  <tr> 
   <td> ソフトバウンス<br/> </td> 
   <td> 一時的なエラー（インボックスがいっぱいであるなど）の合計数。<br/> </td> 
  </tr> 
  <tr> 
   <td> ソフトバウンス率 <br/> </td> 
   <td> 一時的な理由で失敗した配信の割合。<br/> </td> 
  </tr> 
  <tr> 
   <td> ユニーククリック数 <br/> </td> 
   <td> 配信のコンテンツをクリックした受信者の数。<br/> </td> 
  </tr> 
  <tr> 
   <td> ユニーク開封数 <br/> </td> 
   <td> 配信を開いた受信者の数。<br/> </td> 
  </tr> 
  <tr> 
   <td> ユニーク登録解除数 <br/> </td> 
   <td> 購読解除リンクをクリックした受信者の数。<br/> </td> 
  </tr> 
  <tr> 
   <td> 登録解除率 <br/> </td> 
   <td> 配信されたメッセージに対する、一意の購読解除の数。<br/> </td> 
  </tr> 
  <tr> 
   <td> 登録解除 <br/> </td> 
   <td> 購読解除リンクのクリック数。<br/> </td> 
  </tr> 
 </tbody> 
</table>

<!--
### Push notification metrics {#push-notification-metrics}

<table> 
 <thead> 
  <tr> 
   <th> Metric<br/> </th> 
   <th> Definition<br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Bounces + Errors<br/> </td> 
   <td> Total of errors cumulated during delivery in relation to the total number of sent messages, e.g. errors from MCPNS or provider.<br/> </td> 
  </tr> 
  <tr> 
   <td> Bounce + Error rate<br/> </td> 
   <td> Percentage of push notifications that bounced compared to push notifications sent.<br/> </td> 
  </tr> 
  <tr> 
   <td> Click<br/> </td> 
   <td> Number of times a push notification has been delivered to the device and clicked on by the user. The user either wanted to view the notification, which will then be moved to Push Open tracking, or dismiss it.<br/> </td> 
  </tr> 
  <tr> 
   <td> Click through rate<br/> </td> 
   <td> Percentage of users who interacted with the push notification.<br/> </td> 
  </tr> 
  <tr> 
   <td> Delivered<br/> </td> 
   <td> Number of push notifications successfully sent, in relation to the total number of sent push notifications.<br/> </td> 
  </tr> 
  <tr> 
   <td> Delivered rate<br/> </td> 
   <td> Percentage of push notifications successfully sent.<br/> </td> 
  </tr> 
  <tr> 
   <td> Impressions<br/> </td> 
   <td> Number of times a push notification has been delivered to the device and left untouched in the notification center. In most cases, impressions number should be similar to the delivered number. This ensures that the device got the message and relayed that information back to the server.<br/> </td> 
  </tr> 
  <tr> 
   <td> Processed/sent<br/> </td> 
   <td> Total number of push notifications sent.<br/> </td> 
  </tr> 
  <tr> 
   <td> Open<br/> </td> 
   <td> Total number of push notifications delivered to the device and clicked on by users thus opening the app. This is similar to the Push Click except a Push Open will not be triggered if the notification was dismissed.<br/> </td> 
  </tr> 
  <tr> 
   <td> Open rate<br/> </td> 
   <td> Percentage of opened push notifications.<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique clicks<br/> </td> 
   <td> Number of times a unique user interacts with the push notification, e.g. clicks on the notification or button.<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique impressions<br/> </td> 
   <td> Number of impressions by recipient.<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique Opens<br/> </td> 
   <td> Number of recipients who opened the delivery.<br/> </td> 
  </tr> 
 </tbody> 
</table>

### In-App metrics {#in-app-metrics}

<table> 
 <thead> 
  <tr> 
   <th> Metric<br/> </th> 
   <th> Definition<br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Delivered<br/> </td> 
   <td> Total number of In-App messages delivered to the device by the service provider.<br/> </td> 
  </tr> 
  <tr> 
   <td> Impressions<br/> </td> 
   <td> Total of In-App messages seen by recipients depending on whether trigger criterion was met.<br/> </td> 
  </tr> 
  <tr> 
   <td> In-App clicks <br/> </td> 
   <td> Total number of recipients who clicked on Button 1 or Button 2.<br/> </td> 
  </tr> 
  <tr> 
   <td> In-App click through rate<br/> </td> 
   <td> Percentage of users who clicked on Button 1 or Button 2 compared to users who saw the message.<br/> </td> 
  </tr> 
  <tr> 
   <td> In-App dismissal<br/> </td> 
   <td> Total number of messages that recipients dismissed either by clicking the close button or auto-dismiss.<br/> </td> 
  </tr> 
  <tr> 
   <td> In-App dismissal rate<br/> </td> 
   <td> Percentage of In-App messages that recipients dismissed.<br/> </td> 
  </tr> 
  <tr> 
   <td> Processed/sent<br/> </td> 
   <td> Total number of In-App messages sent from Adobe Campaign as part of the delivery sent process.<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique impressions<br/> </td> 
   <td> Number of impressions by a unique recipient.<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique In-App clicks<br/> </td> 
   <td> Number of times recipients clicked on Button 1 or Button 2.<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique In-App dismissals<br/> </td> 
   <td> Number of time recipients dismissed an In-App message.<br/> </td> 
  </tr> 
 </tbody> 
</table>
-->

## セグメント {#segments}

次の表に、レポートで使用されるセグメントとその定義のリストを示します。

<table> 
 <thead> 
  <tr> 
   <th> セグメント <br/> </th> 
   <th> 定義<br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 年齢：ブーマー 1<br/> </td> 
   <td> 1946 年から 1954 年に生まれた受信者。<br/> </td> 
  </tr> 
  <tr> 
   <td> 年齢：ブーマー 2<br/> </td> 
   <td> 1955 年から 1965 年に生まれた受信者。<br/> </td> 
  </tr> 
  <tr> 
   <td> 年齢：18 ～ 25<br/> </td> 
   <td> 18 歳から 25 歳までの受信者。<br/> </td> 
  </tr> 
  <tr> 
   <td> 年齢：26 ～ 30<br/> </td> 
   <td> 26 歳から 30 歳までの受信者。<br/> </td> 
  </tr> 
  <tr> 
   <td> 年齢：31 ～ 40<br/> </td> 
   <td> 31 歳から 40 歳までの受信者。<br/> </td> 
  </tr> 
  <tr> 
   <td> 年齢：41 ～ 50<br/> </td> 
   <td> 41 歳から 50 歳までの受信者。<br/> </td> 
  </tr> 
  <tr> 
   <td> 年齢：X<br/> 世代 </td> 
   <td> 1966 年から 1976 年までに生まれた受信者。<br/> </td> 
  </tr> 
  <tr> 
   <td> 年齢：Y 世代（ミレニアル世代） <br/> </td> 
   <td> 1977 年から 1994 年までに生まれた受信者。<br/> </td> 
  </tr> 
  <tr> 
   <td> 年齢：Z<br/> 世代 </td> 
   <td> 1995 年から現在までに生まれた受信者。<br/> </td> 
  </tr> 
  <tr> 
   <td> 年齢：50<br/> 以上 </td> 
   <td> 年齢が 50.<br/> を超える受信者 </td> 
  </tr> 
  <tr> 
   <td> 年齢：25<br/> 未満 </td> 
   <td> 年齢が 25.<br/> 未満の受信者 </td> 
  </tr> 
  <tr> 
   <td> 年齢：30<br/> 未満 </td> 
   <td> 年齢が 30.<br/> 未満の受信者 </td> 
  </tr> 
  <tr> 
   <td> 年齢：40<br/> 未満 </td> 
   <td> 年齢が 40.<br/> 未満の受信者 </td> 
  </tr> 
  <tr> 
   <td> 年齢：50<br/> 未満 </td> 
   <td> 年齢が 50.<br/> 未満の受信者 </td> 
  </tr> 
  <tr> 
   <td> 年齢：サイレントジェネレーション <br/> </td> 
   <td> 1945 年以前に生まれた受信者。<br/> </td> 
  </tr> 
  <tr> 
   <td> すべての訪問 <br/> </td> 
   <td> すべての受信者 <br/> </td> 
  </tr>
 </tbody> 
</table>
