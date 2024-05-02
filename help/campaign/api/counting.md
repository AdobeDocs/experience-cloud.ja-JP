---
title: カウント
description: カウント操作の実行方法を説明します。
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="限定提供（LA）" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Campaign Standard移行済みユーザーに制限"
exl-id: d6354249-3b0d-4532-951f-b0fae953f7e1
source-git-commit: 3f4400f24b75e8e435610afbe49e9d9444dbf563
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 2%

---

# カウント

Adobe Campaign REST API は、リクエスト内のレコード数をカウントできます。 これを行うには、で返された URL を使用します **count** ノード。

<br/>

***サンプルリクエスト***

を持つすべてのサービスをカウントするには **messageType** 値は「sms」と同じ、を使用してGETリクエストを実行します。 **byChannel** フィルター。

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/byChannel?channel=sms \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

フィルターに対応するサービスを返します。

```
{
    "content": [
        {
            ...
            "messageType": "sms",
            "mode": "newsletter",
            "name": "SVC6",
            ...
        },
        ...
    ],
    "count": {
        "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/byChannel/_count?channel=sms&_lineStart=@iKTZ2q3IiSEDqZ5Nw1vdoGnQCqF-8DAUJRaVwR9obqqTxhMy"
    },
    "serverSidePagination": true
}
```

でGETリクエストを実行します。 **count** ノードの URL を使用して結果の数を取得します。

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/byChannel/_count?channel=sms&_lineStart=@iKTZ2q3IiSEDqZ5Nw1vdoGnQCqF-8DAUJRaVwR9obqqTxhMy \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

レコード数を返します。

```
{
    "count": 26
}
```
