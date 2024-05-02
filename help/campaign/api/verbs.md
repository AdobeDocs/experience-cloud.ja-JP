---
title: GET/POST/PATCH/DELETE動詞
description: Campaign StandardAPI で使用される動詞の詳細を説明します。
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="限定提供（LA）" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Campaign Standard移行済みユーザーに制限"
exl-id: de97a194-d497-4665-906e-53178fd3b119
source-git-commit: 3f4400f24b75e8e435610afbe49e9d9444dbf563
workflow-type: tm+mt
source-wordcount: '139'
ht-degree: 0%

---

# GET/POST/PATCH/DELETE動詞 {#verbs}

リソースに対して操作を実行するために使用できる動詞は次のとおりです。

* `GET`:1 つの要素または要素のコレクションを取得します
* `POST`：パラメーターを持つリソースを作成します。
* `PATCH`：パラメーターでリソースを更新します。
* `DELETE`：リソースを削除します。

<!-- ajouter codes retour -->

<br/>

***サンプルリクエスト***

* プロファイルコレクションに対するサンプルGETリクエスト。


  ```
  $curl  
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```

  プロファイルの配列を返します。


  ```
  {
      "content": [
          {
              "PKey": "<PKEY>",
              "firstName": "Olivia",
              "lastName": "Varney",
              "birthDate": "1977-09-°4",
              "email": "o.varney@mail.com",
          },
          {
              "PKey": "<PKEY>",
              "firstName": "John",
              "lastName": "Doe",
              "birthDate": "1985-08-17",
              "email": "johndoe@mail.com",
          }
      ],
  }
  ```

* 特定のプロファイルに対するサンプルGETリクエスト。


  ```
  $curl  
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/<PKEY> \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```

  リクエストされたプロファイルを返します。


  ```
  {
      "PKey": "<PKEY>",
      "firstName": "John",
      "lastName": "Doe",
      "birthDate": "1985-08-17",
      "email": "johndoe@mail.com",
      ...
  }
  ```

* プロファイルを作成するためのサンプルPOSTリクエスト。


  ```
  -X POST https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>' \
  -d '{"lastName":"Doe"}'
  ```

  デフォルトフィールドを含むプロファイルが返されます。

  ```
  {
      "PKey": "<PKEY>",
      "firstName": "John",
      "lastName": "Doe",
      "birthDate": "1985-08-17",
      "email": "johndoe@mail.com",
  }
  ```

* プロファイルを更新するサンプルPATCHリクエスト。

  ```
  -X PATCH https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/<PKEY> \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>' \
  -d '{"firstName":"Mark"',"lastName":"Smith"}'
  ```

  更新されたプロファイルを取得する PKEY と URL を返します。

  ```
  {
      "PKey": "<PKEY>",
      "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/<PKEY>"
  }
  ```

* プロファイルを削除するサンプルDELETEリクエスト。

  ```
  -X DELETE https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/<PKEY> \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```

  このリクエストは、プロファイルが削除されたことを確認する 200 応答を返します。
