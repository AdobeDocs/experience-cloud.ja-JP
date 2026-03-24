---
title: Node.js SDK リリースノート
description: Experience Rollouts Node.js SDKのリリースノートには、公開済みのすべてのバージョンの新機能、改善点、バグ修正の変更ログが含まれています。
source-git-commit: 9bfe0e55e89c1d7fbd77cde63831a6a186820e24
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 1%

---


# Node.js SDK リリースノート {#nodejs-sdk-release-notes}

このページでは、Experience Rollouts Node.js SDKのリリース履歴を示します。 統合の設定については、[Node.js SDK統合ガイド ](nodejs-sdk-integration-guide.md)を参照してください。

## バージョン 1.0.10 {#v1-0-10}

**バグ修正とソケットの改善**

* スケジュールされたキャッシュの更新中に`ESOCKETTIMEDOUT`個の例外がスローされる問題を修正しました。 `createInstance()`の`featureRequestHttpParams`および`ingestAnalyticsHttpParams`から`maxSockets` パラメーターを削除しました。
* キャッシュ可能なクライアントが、HTTP 304 （未変更）応答の後にキャッシュ不可と誤ってマークされるバグを修正しました。
* `isReleaseBitEnabled()`が削除されました。このメソッドはサポートされなくなりました。
* ログ出力が改善され、診断が向上しました。
* 公開されたnpm パッケージには、テストフォルダーとカバレッジフォルダーは含まれなくなりました。

## バージョン 1.0.5 {#v1-0-5}

**安定性の向上**

キャッシュの更新処理とSDKの初期化エッジケースに関する一般的な修正。

## バージョン 1.0.3 {#v1-0-3}

**最初の安定リリース**

認証済み、匿名、およびデフォルトのフルロールアウト機能フラグ取得をサポートするNode.js SDKの最初の実稼動リリース。

## 関連トピック {#see-also}

* [Node.js SDK統合ガイド](nodejs-sdk-integration-guide.md)
* [Java SDK リリースノート](../../sdk-releases/java/java-sdk-release-notes.md)
* [SDK](../../integrate/sdks.md)
