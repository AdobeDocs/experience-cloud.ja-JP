---
title: API を使用したプロファイルの作成
description: API を使用してプロファイルを作成する方法について説明します。
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="限定提供（LA）" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Campaign Standard移行済みユーザーに制限"
exl-id: 69e8d034-6bdd-4b82-bcd7-1ef4be0a59b3
source-git-commit: 14d8cf78192bcad7b89cc70827f5672bd6e07f4a
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 0%

---

# API を使用したプロファイルの作成 {#creating-profiles-api}

プロファイルの作成は、プロファイルリソースに対する **POST** リクエストで実行されます。

>[!CAUTION]
>
>作成したプロファイルに <b>orgUnit</b> を関連付ける場合は、このフィールドでプロファイルリソースを拡張し、拡張機能の公開後に <b>ProfileAndServicesExt</b> エンドポイントでPOSTリクエストを実行する必要があります。
>
>プロファイルのリソース拡張機能について詳しくは、<a href="https://helpx.adobe.com/jp/campaign/standard/administration/using/organizational-units.html#partitioning-profiles">Campaign ドキュメント </a> を参照してください。

<br/>

***リクエストのサンプル***

「john.doe@mail.com」というメールを使用してプロファイルを作成するPOSTリクエストのサンプル。

```
-X POST https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>' \
-i
-d '{"email":"john.doe@mail.com"}'
```

「john.doe@mail.com」のメールアドレスを持つ、新しく作成されたプロファイルを返します。

```
{
    "PKey": "<PKEY>",
    "firstName": "John",
    "lastName":"Doe",
    "birthDate": "1980-10-24",
    "email": "john.doe@mail.com",
    ...
}
```
