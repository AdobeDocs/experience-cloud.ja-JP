---
title: 購読の取得
description: API を使用して購読を取得する方法を説明します
role: Data Engineer
level: Experienced
badge: label="限定提供（LA）" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Campaign Standard移行済みユーザーに制限"
exl-id: 6d935074-3196-45c5-97cd-ccb7c80bbba8
source-git-commit: 14d8cf78192bcad7b89cc70827f5672bd6e07f4a
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---

# API を使用した購読の取得 {#retrieving-subscriptions-api}

## サービスを購読しているプロファイルの取得

これは、2 段階の手順です。

1. 目的のサービスの購読 URL を取得します。
1. 購読 URL でGETリクエストを実行します。 サービスの購読のリストと、関連する各プロファイルを返します。

>[!CAUTION]
>
>REST API は「href」プロパティを返します。このプロパティには、使用する URL が含まれています。 <b> 応答に含まれる URL を常に使用して、後続の API リクエストを実行します </b>。

<br/>

***リクエストのサンプル***

GETリクエストを実行して、サービスを取得します。

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY> \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

これは、サービスの購読 URL を返します。

```
  {
    ...
    "messageType": "email",
    "name": "SVC1",
    "subscriptions": {
                "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY>/subscriptions/"
    },
    ...
  },
```

購読 URL でGETリクエストを実行します。

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY>/subscriptions \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

サービスの購読のリストが、関連する各プロファイルと共に表示されます。

```
  {
    ...
    "service": ...,
    "serviceName": "SVC3",
    "subscriber": {
        "PKey": "<PKEY>",
        "email": "",
        "firstName": "John",
        "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/<PKEY>",
        "lastName": "Doe",
    },
  }
```

## プロファイルが購読しているサービスの取得

これは、2 段階の手順です。

1. 特定のプロファイルの購読 URL を取得します。
1. URL でGETリクエストを実行します。 プロファイルの購読のリストと、関連する各サービスを返します。

<br/>

***リクエストのサンプル***

GETリクエストを実行して、プロファイルを取得します。

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/<PKEY> \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

プロファイルの購読 URL を返します。

```
  {
    ...
    "postalAddress":...,
    "preferredLanguage": "none",
    "subscriptions": {
      "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/<PKEY>/subscriptions/"
    },
    ...
  }
```

購読 URL でGETリクエストを実行します。

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/<PKEY>/subscriptions \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

プロファイルが購読しているサービスのリストを返します。

```
  {
    ...
    "PKey": "<PKEY>",
    "created": "2017-03-03 10:54:00.363Z",
    "service": {
      "PKey": "<PKEY>",
      "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY>",
      "label": "Sport Newsletter",
      "name": "SVC1",
      "title": "Sport Newsletter (SVC1)"
    },
    ...
  }
```
