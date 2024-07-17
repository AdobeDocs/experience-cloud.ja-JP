---
title: トランザクションメッセージの管理
description: API を使用してトランザクションメッセージを管理する方法を説明します。
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
hidefromtoc: true
hide: true
role: Data Engineer
level: Experienced
badge: label="限定提供（LA）" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Campaign Standard移行済みユーザーに制限"
exl-id: 00d39438-a232-49f1-ae5e-1e98c73397e3
source-git-commit: 14d8cf78192bcad7b89cc70827f5672bd6e07f4a
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 1%

---

# トランザクションメッセージの管理 {#managing-transactional-messages}

トランザクションイベントを作成して公開したら、このイベントのトリガーを web サイトに統合する必要があります。

例えば、クライアントの 1 人が Web サイトを離れてから買い物かごの商品を購入するたびに、「買い物かごの放棄」イベントをトリガーしたいとします。 これを行うには、web 開発者は、REST トランザクションメッセージ API を使用する必要があります。

1. POSTメソッドに従ってリクエストを送信します。このメソッドは [ トランザクションイベントの送信 ](#sending-a-transactional-event) をトリガーにします。
1. POSTリクエストへの応答にはプライマリキーが含まれており、GETリクエストを通じて 1 つまたは複数のリクエストを送信できます。 これにより、[ イベントステータス ](#transactional-event-status) を取得できるようになります。

## トランザクションイベントの送信 {#sending-a-transactional-event}

トランザクションイベントは、次の URL 構造を持つPOSTリクエストを介して送信されます。

```
POST https://mc.adobe.io/<ORGANIZATION>/campaign/<transactionalAPI>/<eventID>
```

* **&lt;ORGANIZATION>**：個人の組織 ID。 この[節](must-read.md)を参照してください。

* **&lt;transactionalAPI>**：トランザクションメッセージ API のエンドポイント。

  トランザクションメッセージ API エンドポイントの名前は、インスタンス設定によって異なります。 これは、値「mc」に続いて個人の組織 ID に対応します。 Geometrixx会社の例で、組織 ID として「geometrixx」を使用するとします。 その場合、POSTリクエストは次のようになります。

  `POST https://mc.adobe.io/geometrixx/campaign/mcgeometrixx/<eventID>`

  なお、トランザクションメッセージ API エンドポイントは、API プレビュー中にも表示されます。

* **&lt;eventID>**：送信するイベントのタイプ。 この ID は、イベント設定の作成時に生成されます

### POSTリクエストヘッダー

リクエストには、「Content-Type: application/json」ヘッダーが含まれている必要があります。

文字セット（例：**utf-8**）を追加する必要があります。 この値は、使用している REST アプリケーションによって異なることに注意してください。

```
-X POST \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>' \
-H 'Content-Type: application/json;charset=utf-8' \
-H 'Content-Length:79' \
```

### POSTリクエスト本文

イベントデータは JSON POST本文内に含まれます。 イベントの構造は定義によって異なります。 リソース定義画面の「API プレビュー」ボタンに、リクエストサンプルが表示されます。

イベントにリンクされたトランザクションメッセージの送信を管理するために、次のオプションのパラメーターをイベントコンテンツに追加できます。

* **有効期限** （任意）：この日付以降、トランザクションイベントの送信はキャンセルされます。
* **スケジュール済み** （オプション）：この日付から、トランザクションイベントが処理され、トランザクションメッセージが送信されます。

>[!NOTE]
>
>「expiration」パラメーターと「scheduled」パラメーターの値は、ISO 8601 形式に従います。 ISO 8601 では、大文字「T」を使用して日付と時刻を区切るように指定されています。 ただし、読みやすくするために、入力または出力から削除できます。

### POSTリクエストへの応答

POSTレスポンスは、作成時のトランザクションイベントのステータスを返します。 現在のステータス（イベントデータ、イベントステータスなど）を取得するには、GETリクエストでPOSTレスポンスから返されるプライマリキーを使用します。

`GET https://mc.adobe.io/<ORGANIZATION>/campaign/<transactionalAPI>/<eventID>/`

<br/>

***リクエストのサンプル***

イベントを送信するためのPOSTリクエスト。

```
-X POST https://mc.adobe.io/<ORGANIZATION>/campaign/mcAdobe/EVTcartAbandonment \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>' \
-H 'Content-Type: application/json;charset=utf-8' \
-H 'Content-Length:79'

{
  "email":"test@example.com",
  "scheduled":"2017-12-01 08:00:00.768Z",
  "expiration":"2017-12-31 08:00:00.768Z",
  "ctx":
  {
    "cartAmount": "$ 125",
    "lastProduct": "Leather motorbike jacket",
    "firstName": "Jack"
  }
}
```

POSTリクエストへの応答。

```
{
  "PKey":"<PKEY>",
  "ctx":
  {
    "cartAmount": "",
    "lastProduct": "",
    "firstName": ""
  }
  "email":"",
  "scheduled":"2017-12-01 08:00:00.768Z",
  "expiration":"2017-12-31 08:00:00.768Z",
  "href": "mcAdobe/EVTcartAbandonment/<PKEY>",
  "serverUrl":" https://myserver.com ",
  "status":"pending",
  "type":""
}
```

### トランザクションイベントのステータス {#transactional-event-status}

応答で、「ステータス」フィールドを使用すると、イベントが処理されたかどうかを知ることができます。

* **pending**：イベントは保留中です。イベントがトリガーされると、このステータスになります。
* **処理中**：イベントは配信待ちです。イベントがメッセージに変換され、メッセージが送信されます。
* **paused**：イベントプロセスが一時停止されています。 処理は行われなくなりましたが、Adobe Campaign データベースのキューに保持されます。
* **processed**：イベントは処理され、メッセージは正常に送信されました。
* **無視**：配信でイベントが無視されました（通常、アドレスが強制隔離されている場合）。
* **deliveryFailed**: イベントの処理中に配信エラーが発生しました。
* **routingFailed**：ルーティングフェーズが失敗しました。これは、指定されたイベントのタイプが見つからない場合などに発生する可能性があります。
* **tooOld**：処理可能になる前にイベントの有効期限が切れました。これは、様々な理由で発生する可能性があります。例えば、送信が数回失敗した場合（イベントが最新ではなくなる結果となる）、オーバーロードされた後にサーバーがイベントを処理できなくなった場合などです。
* **targetingFailed**: Campaign Standardは、メッセージのターゲティングに使用されているリンクをエンリッチメントできませんでした。
