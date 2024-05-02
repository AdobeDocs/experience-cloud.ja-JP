---
title: プロファイルの更新
description: API でプロファイルを更新する方法の詳細情報
role: Data Engineer
level: Experienced
badge: label="限定提供（LA）" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Campaign Standard移行済みユーザーに制限"
exl-id: fa3796ee-a00c-4d70-bf3d-e8d2099f1116
source-git-commit: 3f4400f24b75e8e435610afbe49e9d9444dbf563
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 1%

---

# API を使用したプロファイルの更新{#updating-profiles-api}

プロファイルの更新は、で実行します。 **PATCH** リクエスト。

`https://mc.adobe.io/<ORGANIZATION>/campaign/<apiName>/<resourceName>/<PKEY>`

1. 最初のステップは次のとおりです。 **プロファイルの取得**.

1. 2 番目のリクエストで、次を実行します **PATCHリクエスト** プロファイルで、ペイロードに入力済みの情報を含める。

1. PATCHリクエストがプロファイルを更新したかどうかを確認するには、最終的なGETリクエストを実行します。

<br/>

***サンプルリクエスト***

プロファイルを取得するサンプルGETリクエスト。

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/<PKEY>\
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

リクエストに対する応答。

```
{
    "content": [
        {
            "PKey": "<PKEY>",
            "firstName": "Amy",
            "lastName":"Dakota",
            "birthDate": "1980-10-24",
            ...
        }
    ]
}
```

「phone」属性を更新するPATCHリクエスト。

```
-X PATCH https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/<PKEY> \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>' \
-d '{"phone":"3301020304"}'
```

更新されたプロファイルを取得する PKEY と URL を返します。

```
{
    "PKey": "<PKEY>",
    "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/@2v1dr3ZKJveMDhAdh0MPnh9hNQQ93qb7AW6BNVVKknjwXvTZRBAgUqz1SNcB4ZndgjqOofx3BwBZYBftlmObISoM3rs"
}
```
