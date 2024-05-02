---
title: ページネーション
description: ページネーション操作の実行方法を説明します。
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="限定提供（LA）" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Campaign Standard移行済みユーザーに制限"
exl-id: d6ebce3c-1e84-4b3b-a68d-90df4680af64
source-git-commit: 3f4400f24b75e8e435610afbe49e9d9444dbf563
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 1%

---

# ページネーション

デフォルトでは、25 個のリソースが 1 つのリストに読み込まれます。

この **_lineCount** パラメーターを使用すると、応答にリストされるリソースの数を制限できます。  その後、を使用できます **次へ** ノード：次の結果を表示します。

>[!NOTE]
>
>で返された URL 値を常に使用します **次へ** ページネーションリクエストを実行するノード。
>
>この **_lineStart** リクエストは計算され、 **次へ** ノード。

<br/>

***サンプルリクエスト***

プロファイルリソースの 1 件のレコードを表示するサンプルGETリクエスト。

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile?_lineCount=1 \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

リクエストへの応答（を含む） **次へ** ページネーションを実行するノード。

```
{
    "content": [
        {
            "PKey": "<PKEY>",
            "firstName": "John",
            "lastName":"Doe",
            "birthDate": "1980-10-24",
            ...
        }
    ],
    "next": {
        "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/email?_lineCount=10&_
        lineStart=@Qy2MRJCS67PFf8soTf4BzF7BXsq1Gbkp_e5lLj1TbE7HJKqc"
    }
    ...
}
```

デフォルトでは、 **次へ** 大量のデータを含むテーブルを操作する場合、ノードは使用できません。 ページネーションを実行するには、 **_forcePagination=true** パラメーターを呼び出し URL に追加します。

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile?_forcePagination=true \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

>[!NOTE]
>
>テーブルの大きさが基準となるレコードの数は、Campaign Standardで定義されます **XtkBigTableThreshold** オプション。 デフォルト値は 100,000 レコードです。
