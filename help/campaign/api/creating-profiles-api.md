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
source-git-commit: 3f4400f24b75e8e435610afbe49e9d9444dbf563
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 0%

---

# API を使用したプロファイルの作成 {#creating-profiles-api}

プロファイルの作成は、次を使用して実行します **POST** プロファイルリソースに対するリクエスト。

>[!CAUTION]
>
>を関連付ける <b>orgUnit</b> POST作成したプロファイルには、このフィールドでプロファイルリソースを拡張し、拡張機能を公開した後、 <b>ProfileAndServicesExt</b> エンドポイント。
>
>プロファイルのリソース拡張機能について詳しくは、 <a href="https://helpx.adobe.com/campaign/standard/administration/using/organizational-units.html#partitioning-profiles">Campaign ドキュメント</a>.

<br/>

***サンプルリクエスト***

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
