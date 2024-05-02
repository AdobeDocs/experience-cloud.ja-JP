---
title: API アクセスの設定
description: Campaign StandardAPI へのアクセスを設定する方法について説明します。
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="限定提供（LA）" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Campaign Standard移行済みユーザーに制限"
exl-id: efbbd0cd-9c56-4ad0-8bcb-efba4b63c28b
source-git-commit: 3e7af8a9ba41ab54738fff2f69388595041a8574
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 31%

---

# API アクセスのセットアップ {#setting-up-api-access}

Adobe Campaign Standardの API アクセスは、以下の手順でセットアップします。 これらの各手順について詳しくは、こちらを参照してください [Adobe Developer ドキュメント](https://developer.adobe.com/developer-console/docs/guides/#!AdobeDocs/adobeio-auth/master/AuthenticationOverview/ServiceAccountIntegration.md).

>[!IMPORTANT]
>
>で証明書を管理するには [Adobe Developer](https://developer.adobe.com/)。次が揃っていることを確認します **システム管理者** 組織またはに対する権限 [開発者アカウント](https://helpx.adobe.com/jp/enterprise/using/manage-developers.html) Admin Consoleで。

1. **電子証明書があることを確認するか**、必要に応じて作成します。証明書に記載されている公開鍵と秘密鍵は、以降の手順で必要になります。
1. **Adobe Campaign サービスへの新しい統合の作成** 。対象： [Adobe Developer](https://developer.adobe.com/) そして、設定します。 次に、資格情報を生成します（API キー、クライアントシークレットなど）。
1. 生成済みの資格情報から **JSON Web トークン（JWT）を作成**&#x200B;し、それに秘密鍵で署名します。JWT では、Adobeがユーザーの ID が正しいことを確認し API へのアクセス権をユーザーに付与するのに必要なすべての ID およびセキュリティ情報をエンコードします。

   >[!IMPORTANT]
   >
   >JWT（JSON web トークン）は、現在非推奨（廃止予定）の段階で、OAuth に置き換えられています。この移行は、Campaign の今後のリリースで段階的に実行されます。 サービスアカウント（JWT）資格情報は非推奨（廃止予定）としてマークされ、2025 年 1 月 27 日（PT）まで引き続き機能します。 したがって、2025 年 1 月 27 日（PT）より前に、新しい OAuth サーバー間資格情報を使用するようにアプリケーションまたは統合を移行する必要があります。 OAuth 認証をお勧めします。 JWT 認証から OAuth 認証に移行するすべての要素は、次のページにあります。
   >* [移行](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/)
   >* [実装](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/)
   >* [非推奨（廃止予定）の JWT に関するよくある質問](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/faqs/)

1. **JWT をアクセストークンと交換する** POSTリクエストを通じて行います。 このアクセストークンを API リクエストの各ヘッダーで使用する必要があります。

サービス間のセキュアな Adobe I/O API セッションを確立するには、アドビサービスへのすべてのリクエストで、以下の情報を Authorization ヘッダーに含める必要があります。

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

* **&lt;organization>**：これは個人の組織 ID で、インスタンスごとに 1 つの組織 ID がAdobeから提供されます。

   * &lt;organization> ：実稼動インスタンス、
   * &lt;organization-mkt-stage>：ステージインスタンス。

  組織 ID の値を取得するには、管理者またはアドビの技術担当者にお問い合わせください。また、新しい統合を作成する際に、ライセンスリストでAdobe I/Oに取得することもできます（ <a href="https://developer.adobe.com/developer-console/docs/guides/authentication/">Adobe Developer ドキュメント</a>）に設定します。

* **&lt;access_token>**:POSTリクエストを通じて JSON web トークンを交換する際に取得した個人用アクセストークンです。

* **&lt;API_KEY>**：個人用 API キーです。Adobe Campaign サービスへの新しい統合を作成した後、Adobe I/Oで提供されます。

  ![代替テキスト](assets/tenant.png)

## トラブルシューティング

AdobeIO 統合中に、次のエラーが表示される場合。

```
{ 
"code": 502, 
"message": "Oops. Something went wrong. Check your URI and try again." 
}
```


CNAME パラメーターが正しく作成されているかどうかを確認するには、管理者またはAdobeの技術担当者に問い合わせてください。
