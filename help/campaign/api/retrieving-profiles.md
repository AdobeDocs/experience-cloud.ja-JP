---
title: プロファイルの取得
description: API を使用してプロファイルを取得する方法の詳細を説明します
role: Data Engineer
level: Experienced
badge: label="限定提供（LA）" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Campaign Standard移行済みユーザーに制限"
source-git-commit: 84b72258789ba61016deb813e93bdca0ea142712
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 4%

---

# API を使用したプロファイルの取得 {#retrieving-profiles}

プロファイルの取得は、 **GET** リクエスト。

その後、フィルター、順序、ページネーションを使用して、検索を絞り込むことができます。 詳しくは、次を参照してください [その他の操作](sorting.md) セクション。

さらに、Campaign StandardAPI では、「メール」、「名」、「姓」または任意のカスタムフィールドのいずれか 1 つに基づいてプロファイルを検索できます。 詳しくは、[この節](#searching-field)を参照してください。

<br/>

***サンプルリクエスト***

* すべてのプロファイルを取得するサンプルGETリクエスト。

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile \
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
              "firstName": "John",
              "lastName":"Doe",
              "birthDate": "1980-10-24",
              ...
          },
          ...
  }
  ```

* 最初の 10 個のメール値を取得するサンプルGETリクエスト。

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/email?_lineCount=10 \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```

  リクエストに対する応答。 「next」ノードは、次の 10 件のメール値へのアクセスを許可する URL を返します。

  ```
  {
  "content": [
      "amy.dakota@mail.com",
      "kristen.smith@mail.com",
      "omalley@mail.com",
      "xander.harrys@mail.com",
      "jane.summer@mail.com",
      "gloria.boston@mail.com",
      "edward.snow@mail.com",
      "dorian.simons@mail.com",
      "peter.paolini@mail.com",
      "mingam+test08@adobe.com"
  ],
  "next": {
      "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/email?_lineCount=10&_
      lineStart=@Qy2MRJCS67PFf8soTf4BzF7BXsq1Gbkp_e5lLj1TbE7HJKqc"
  }
  }
  ```

## フィールドに基づくプロファイルの検索 {#searching-field}

この **[!UICONTROL filterType]** パラメーターを使用すると、「電子メール」、「名」、「姓」またはプロファイルリソースの拡張時に詳細フィルタリングで追加したカスタムフィールドのうち、いずれかのフィールドに基づいてプロファイルを取得できます。

>[!NOTE]
>
>検索では大文字と小文字が区別され、プレフィックスに対してのみ実行されます。 例えば、姓の最後の文字を使用してプロファイルを検索することはできません。

***サンプルリクエスト***

* 名に基づいてプロファイルをフィルタリングするリクエストのサンプル。

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/byText?text=John&filterType=firstName \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```

* 姓に基づいてプロファイルをフィルタリングするサンプルリクエスト。

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/byText?text=Miller&filterType=lastName \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```

* メールに基づいてプロファイルをフィルタリングするリクエストのサンプル。

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/byText?text=John%40gmail.com&filterType=email \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```

* 「Hobby」カスタムフィールドに基づいてプロファイルをフィルタリングするリクエストのサンプル。

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServicesExt/profile/byText?cusHobby=Dancing&filterType=Hobby \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```
