---
title: API を使用したサービスの作成
description: API を使用してサービスを作成する方法を学ぶ
role: Data Engineer
level: Experienced
badge: label="限定提供（LA）" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Campaign Standard移行済みユーザーに制限"
exl-id: 91bbce9e-a618-4be2-840b-c7d021271f4e
source-git-commit: 14d8cf78192bcad7b89cc70827f5672bd6e07f4a
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 0%

---

# API を使用したサービスの作成{#creating-a-service-api}

サービスの作成は、サービス リソースの **POST** リクエストで実行されます。

特定の属性でサービスを作成する場合は、それらをペイロードに追加します。 それ以外の場合は、新しいサービスがデフォルトのサービスで作成されます。

<br/>

***リクエストのサンプル***

特定の属性を持つサービスを作成するためのサンプルPOSTリクエスト。

```
-X POST https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/ \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
-i
-d {
-d "label": "My newsletter",
-d "messageType": "email",
-d "name": "email_newsletter",
-d "start": "2019-10-06"
-d }
```

更新された属性を含む新しく作成されたサービスが返されます。

```
{
    "PKey": "<PKEY>",
    "builtIn": false,
    "created": "2019-09-26 12:00:37.005Z",
    "href": "https://mc.adobe.io/<ORGANIZATION>/profileAndServices/service/@NLscZuVHxdVu9rPftvrMWFfR1zRIxQGswSOmGLrK09JTF_iWhB0JCUHEndA_vvy__k9mzOYa5NVkcWDcrK8qGh0wygahX9kRcD44kiWWSEceShn3",
    "label": "My newsletter",
    ...
}
```
