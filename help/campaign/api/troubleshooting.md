---
title: API のトラブルシューティング
description: Campaign StandardAPI に関するよくある問題の詳細を説明します
role: Data Engineer
level: Experienced
badge: label="限定提供（LA）" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Campaign Standard移行済みユーザーに制限"
source-git-commit: 84b72258789ba61016deb813e93bdca0ea142712
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# API のトラブルシューティング {#troubleshooting}

* **enterprise.io コンソールに移動すると、次のAdobeが表示されます。「Adobe I/Oコンソールは、Enterprise アカウントの一部のメンバーのみが使用できます。 アクセス権が必要と思われる場合は、システム管理者にお問い合わせください。」**

API キーを作成できるのは、管理者である組織用のみです。 このメッセージが表示された場合、API キーを作成して組織の管理者の 1 人に依頼するとします。

* **error.io にリクエストを行うと、{&quot;Adobe_code&quot;:&quot;403023&quot;,&quot;message&quot;:&quot;プロファイルが無効です&quot;} と表示される**

つまり、特定の Campaign 製品の IMS プロビジョニングに問題があります。IMS チームがそれを修正する必要があります。

詳細を確認するには、IMS API をトークンで呼び出して、IMS プロファイルがどのように見えるかを確認できます。リクエストをルーティングするには、organization_id がAdobe用に URL に入力したものと同じである prodCtx が必要です。
ない場合、IMS プロビジョニングを修正する必要があります。

```
-X GET https://mc.adobe.io/{ORGANIZATION}/campaign/profileAndServices/profile \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

このメソッドは次のエラーを返します。

```
{"error_code":"403023","message":"Profile is not valid"}
```

このリクエストの IMS プロファイルを確認します。

```
-X GET https://ims-na1.adobelogin.com/ims/profile/v1 \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

応答の ORGANIZATION_ID 値は、最初のGETリクエストで同じである必要があります。

```
{
  "countryCode": "FR",
  "mrktPermEmail": null,
  "projectedProductContext": [
    {
    "prodCtx": {
      "statusCode": "ACTIVE",
      "ident": "ZQ9FRQK7BF09YXAESFY9DDQP1G",
      "modDts": 1448307260000,
      "organization_id": "actest",
      "owningEntity": "6096892F54B5819E0A4C98A2@AdobeOrg",
      "serviceCode": "dma_tartan",
      "label": "Adobe Marketing Cloud",
      "serviceLevel": "standard",
      "createDts": 1421181343000,
      "deal_id": " "
      }
    }
  ]
}
```

* **message.io にリクエストを行うと、&lbrace;&quot;code&quot;:500, &quot;Adobe&quot;:&quot;エラーが発生します。 エラーが発生しました。 URI を確認して、もう一度やり直してください。」**

Adobe.io は無効な URI を宣言します：おそらく、要求している URI が無効です。 Adobe.io で Campaign サービスを選択すると、使用可能な organization_ids のリストを含むピッカーが表示されます。 選択したものが URL に入力したものであることを確認する必要があります。

* **error.io にリクエストを行うと、{&quot;Adobe_code&quot;:&quot;401013&quot;,&quot;message&quot;:&quot;Oauth トークンが無効です&quot;} と表示される**

トークンが無効であるか（トークンの生成に使用された IMS 呼び出しが正しくありません）、トークンの有効期限が切れています。

* **作成後にプロファイルが表示されません**

インスタンスの設定に応じて、作成したプロファイルは **orgUnit** に関連付ける必要があります。 作成にこのフィールドを追加する方法については、[ この節 ](creating-profiles-api.md) を参照してください。

<!-- * (error duplicate key : quand tu crées un profile qui existe déjà , il faut faire un patch pour updater le profile plutôt qu'un POST)

With Curl
List all profiles

Create a profile

Update the mobilePhone attribute of a profile

API Calls on Service

GET the list of services

-->

<!--

How to find and use a filter?
Error codes:

* PAtch sur Age = message d'erreur :
500
Cannot update the 'age' property that is read-only
'age' property is not valid for the 'profile' resource.
-->

<!--
How to filter a list of subscribed profiles with available profile filters ? by date (by les filtres dispo sur la ressource) ?

Pattern classique :

recupérer la liste des subscriptions filtrées d'un profile
1) get sur profile
2) recup PKey
3) get sur PKey
4) get sur href des subscriptions

Comment savoir quel filtre appliquer ?

1) get sur metadata de profile
2) retourne description de la collection subscription
3) get sur la valeur du champ resTarget
4) get sur le href dans filters
5) retourne les filtres applicables sur l'url des data.

-->
