---
title: カスタムリソース
description: API を使用したカスタムリソース管理の詳細情報/
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="限定提供（LA）" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Campaign Standard移行済みユーザーに制限"
source-git-commit: 84b72258789ba61016deb813e93bdca0ea142712
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 2%

---

# カスタムリソース {#custom-resources}

Adobe Campaignには事前定義済みのデータモデルが付属しており、データは様々なリソースを使用して定義されます。 リソースを拡張することで提供されるデータモデルをエンリッチメントし、独自のカスタムフィールドや、購入テーブルや製品テーブルなどのカスタムテーブルを追加できます。

カスタムリソースには、API を使用して次のメソッドを使用します： **/profileAndServicesExt** エンドポイント、およびカスタムリソース名。

`https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServicesExt/<resourceName>/`

>[!NOTE]
>
>標準ではないリソースの場合は、常に次を使用します <b>&quot;cus&quot;</b> リソースの名前の前にプレフィックスを付けます。

カスタムリソースがプロファイルテーブルにリンクされている限り、カスタムリソースを使用してあらゆる操作を実行できます。 例えば、次のテーブル構造について考えてみましょう。

![代替テキスト](assets/cusresources.png)

この場合、のすべてのリソースは **トランザクション**, **TransactionDetails** および **製品** テーブルは、 **Profile** テーブル。

<br/>

***サンプルリクエスト***

拡張された profileAndServicesExt リソースにアクセスするためのサンプルGETリクエスト。

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServicesExt/\
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>' \
```

リンクされたすべてのカスタムリソースのリストを返します。 その後、リソースの URL を使用して、このドキュメントで説明している API タスクを実行できます。

```
{
"apiName": "resourceType",
"cusProduct": {
        "content": ...,
        "data": "/profileAndServicesExt/cusProduct/",
        "help": "Product",
        "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServicesExt/cusProduct/metadata",
        "name": "cusProduct",
        "type": "collection"
    },
"cusTransaction": {
        "content": ...,
        "data": "/profileAndServicesExt/cusTransaction/",
        "help": "Product",
        "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServicesExt/cusTransaction/metadata",
        "name": "cusProduct",
        "type": "collection"
    },
    ...
}
```
