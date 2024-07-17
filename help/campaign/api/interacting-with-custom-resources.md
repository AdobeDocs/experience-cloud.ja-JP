---
title: カスタムリソースとのやり取り
description: API を使用したカスタムリソース管理の詳細情報/
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="限定提供（LA）" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Campaign Standard移行済みユーザーに制限"
exl-id: 19bfeecb-da60-479c-a929-0cfb72ef59e3
source-git-commit: 14d8cf78192bcad7b89cc70827f5672bd6e07f4a
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# カスタムリソースとのやり取り {#interacting-with-custom-resources}

**/customResources** エンドポイントを使用すると、Campaign のカスタムリソースを REST で公開できます。 この API に基づいて、カスタムエンティティと外部エンドポイントの統合を使用できます。

/customResources エンドポイントの動作は、/profileAndServices エンドポイントとまったく同じです。

この API 内で公開されるカスタムリソースは次のとおりです。

* /profileAndServicesExt で公開されないすべてのエンティティ
* プロファイルにリンクされていないすべてのエンティティ。これらのエンティティについては、その子と孫。
* デフォルトでは、何にもリンクされていないすべてのエンティティ、およびその子と孫です。

>[!NOTE]
>/profileAndServicesExt 以下で使用可能なカスタムリソースは、/customResources API では公開されません。


次に、カスタムリソースからメタデータを取得する例を示します。

```
GET /customResources/resourceType/<customResourceName>
```

作成、更新、削除を行うには、GET、POST、PATCH、DELETEを使用します。

```
POST /customResources/<customResourceName>
```
