---
title: シグナルアクティビティのトリガー
description: API を使用してシグナルアクティビティをトリガーにする方法を説明します。
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="限定提供（LA）" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Campaign Standard移行済みユーザーに制限"
source-git-commit: 84b72258789ba61016deb813e93bdca0ea142712
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 2%

---

# シグナルアクティビティのトリガー {#triggering-a-signal-activity}

Adobe Campaign Standardのワークフローでは、次の 1 つ以上の操作が可能です **外部シグナル** アクティビティ。 これらのアクティビティは、トリガーされるのを待つ「リスナー」です。

Campaign Standardトリガー API では、 **外部シグナル** ワークフローを呼び出すアクティビティ。 API 呼び出しには、ワークフローのイベント変数に取り込まれるパラメーター（ターゲットにするオーディエンス名、読み込むファイル名、メッセージコンテンツの一部など）を含めることができます。 これにより、Campaign の自動化を外部システムと簡単に統合できます。

>[!NOTE]
>
>外部シグナルアクティビティは、10 分以上の頻度でトリガーすることはできず、宛先ワークフローが既に実行されている必要があります。

ワークフローをトリガーするには、次の手順に従います。

1. 実行 **GET** 外部シグナルアクティビティのトリガー URL を取得するリクエストがワークフローに送信されます。

   `GET https://mc.adobe.io/<ORGANIZATION>/campaign/workflow/execution/<workflowID>`

1. 実行 **POST** 返された URL に対して、シグナル アクティビティをトリガーするリクエスト。次のパラメーターを使用します **「ソース」** パラメーターがペイロードにあります。 この属性は必須で、トリガーするリクエストソースを指定できます。

ワークフローをパラメーター付きで呼び出す場合は、次を使用してペイロードに追加します **&quot;パラメーター&quot;** 属性。 構文は、パラメーターの名前と値で構成されます（次のタイプがサポートされています。 **string**, **数値**, **ブール型** および **日付/時刻**）に設定します。

```
  -X POST <TRIGGER_URL>
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>' \
  -H 'Content-Type: application/json;charset=utf-8' \
  -H 'Content-Length:79' \
  -i
  -d {
  -d    "source":"<SOURCE>",
  -d    "parameters":{
  -d      "<PARAMETER_NAME":"<PARAMETER_VALUE>",
  -d      "<PARAMETER_NAME":"<PARAMETER_VALUE>",
  -d      "<PARAMETER_NAME":"<PARAMETER_VALUE>",  
  -d      "<PARAMETER_NAME":"<PARAMETER_VALUE>"
  -d    }
  -d }
```

>[!NOTE]
>
>ペイロードにパラメーターを追加する場合、その **名前** および **タイプ** 値は、「外部シグナル」アクティビティで宣言された情報と一致します。 さらに、ペイロードサイズは 64Ko を超えないようにする必要があります。

<br/>

***サンプルリクエスト***

ワークフローでGETリクエストを実行します。

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/workflow/execution/<workflowID> \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

ワークフローシグナル アクティビティと、関連するトリガー URL を返します。

```
{
"PKey": "<PKEY>",
"activities": {
  "activity": {
    "signal1": {
      ...
      "trigger": {
        "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/workflow/execution/<PKEY>/activities/activity/<PKEY>/trigger/"
        },
        ...
      }
    }
  }
}
```

シグナルアクティビティをトリガーするには、「source」を持つトリガー url でPOSTリクエストを実行します。 パラメーターを使用してワークフローを呼び出す場合は、「parameters」属性を追加します。

```
-X POST https://mc.adobe.io/<ORGANIZATION>/campaign/workflow/execution/<PKEY>/activities/activity/<PKEY>/trigger \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>' \
-i
-d '{
-d "source":"API",
-d "parameters":{
-d    "audience":"audience",
-d    "email":"anna.varney@mail.com",
-d    "template":"05",
-d    "contentURL":"http://www.adobe.com",
-d    "test":"true",
-d    "segmentCode":"my segment",
-d    "attribute":"2019-04-03 08:17:19.100Z"}
-d  }'
```

<!-- + réponse -->

パラメーターの 1 つが外部シグナル アクティビティで宣言されていない場合、POSTリクエストは次のエラーを返し、どのパラメーターが欠落しているかを示します。

```
RST-360011 An error has occurred - please contact your administrator.
'contentURL' parameter isn't defined in signal activity.
XTK-170006 Unable to parse expression 'HandleTrigger(@name, $(source), $({parameters}))'.
RST-360000 Error while assessing 'HandleTrigger(@name, $(source), $({parameters}))' expression ('xtk:workflow:execution/activities/signal/trigger' resource)
```
