---
audience: user
user-guide-title: Adobe Experience Rollouts
user-guide-description: Adobe Experience Rolloutsを使用して、アプリケーション全体で機能フラグ、制御ロールアウト、ターゲットリリースを管理する方法について説明します。
source-git-commit: c654ca1507abcefcff84cef9f99830042939805d
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 6%

---


# Adobe Experience Rollouts {#experience-rollouts}

+ [概要](home.md)
+ はじめに {#get-started}
   + [エクスペリエンスのロールアウトの概要](getting-started/introduction.md)
   + [エクスペリエンスのロールアウトを使用する理由](getting-started/why-use-experience-rollouts.md)
   + [エクスペリエンスのロールアウトモード](getting-started/experience-rollouts-modes.md)
+ 概念 {#concepts}
   + [機能フラグとは](concepts/what-is-a-feature-flag.md)
   + [機能を有効または無効にする機能フラグ](concepts/feature-flags-to-enable-disable-features.md)
   + [複数の機能を制御する機能グループ](concepts/feature-groups-to-control-multiple-features.md)
   + [リリース管理について](concepts/concept-of-release-management.md)
   + [エクスペリエンスのロールアウトでのリリース管理](concepts/release-management.md)
   + [段階的な展開](concepts/gradual-rollout.md)
+ ガイド {#guides}
   + コンソールの概要 {#console}
      + [Experience Rollouts コンソールにログインします](guides/console/log-in-to-the-console.md)
      + [サンドボックスの選択](guides/console/environments-overview.md)
      + [利用申請](guides/console/request-access.md)
   + アプリケーション {#applications}
      + [アプリケーションの管理](guides/applications/manage-applications.md)
      + [アプリケーションのオンボーディング](guides/applications/onboard-your-application.md)
   + エクスペリエンスのロールアウトの統合 {#integrate}
      + [アプリにエクスペリエンスのロールアウトを統合する](guides/integrate/integrating-in-your-app.md)
      + [スタートアップガイド](guides/integrate/startup-guide.md)
      + [デスクトップアプリケーション](guides/integrate/desktop-applications.md)
      + [モバイルアプリ](guides/integrate/mobile-applications.md)
      + [web アプリケーション](guides/integrate/web-applications.md)
      + [Web サービス](guides/integrate/web-services.md)
      + [SDK](guides/integrate/sdks.md)
      + [統合ステップ](guides/integrate/integration-steps.md)
      + [Adobe Developer ConsoleでAPI アプリケーションを購読する](guides/integrate/subscribe-to-api-application.md)
   + 機能フラグ {#feature-flags}
      + [機能と機能グループ](guides/feature-flags/features-feature-groups-releases.md)
      + [最初の機能フラグを作成](guides/feature-flags/create-your-first-feature-flag.md)
      + [徐々にロールアウトする機能を設定する](guides/feature-flags/set-feature-gradual-rollout.md)
      + [機能グループの作成](guides/feature-flags/create-a-feature-group.md)
      + [機能グループを設定し](guides/feature-flags/set-feature-group-gradual-rollout.md)
      + [機能フラグによるA/B テスト](guides/feature-flags/a-b-testing.md)
      + [リリース管理に関するFAQ](guides/feature-flags/release-management-faqs.md)
      + [Analytics](guides/feature-flags/analytics.md)
      + [スケジュール](guides/feature-flags/schedule.md)
   + オーディエンス基準 {#audience}
      + [機能フラグと機能グループのオーディエンス](guides/audience/audience-in-feature-flags-and-feature-groups.md)
      + [オーディエンスルールでのコンテキストの使用](guides/audience/using-context-in-audience-rules.md)
      + [複雑なオーディエンスルール](guides/audience/complex-rules.md)
      + [オーディエンスルールでの企業組織データの使用](guides/audience/using-enterprise-org-data.md)
      + [オーディエンス条件に割合ルールを追加](guides/audience/adding-percentage-rules.md)
      + [クライアント IP コンテキスト変数を使用したオーディエンスルール](guides/audience/clientip-rule.md)
   + 環境をまたいだワークフロー {#cross-environment}
      + [環境横断的な概念](guides/cross-environment/cross-environment-concept.md)
      + [環境をアプリケーションに関連付ける](guides/cross-environment/associate-environments.md)
      + [環境をまたいで機能フラグを表示](guides/cross-environment/view-feature-flags-across-environments.md)
      + [機能フラグの読み込み](guides/cross-environment/import-feature-flags.md)
   + サポート {#support}
      + [トラブルシューティング](guides/support/troubleshooting.md)
      + [サポートを受ける](guides/support/get-support.md)
      + [サポートに連絡](guides/support/contact-support.md)
   + SDK リリース {#sdk-releases}
      + Java SDK {#java-sdk}
         + [Java SDK統合ガイド](guides/sdk-releases/java/java-sdk-integration-guide.md)
         + [Java SDK リリースノート](guides/sdk-releases/java/java-sdk-release-notes.md)
      + Node.js SDK {#nodejs-sdk}
         + [Node.js SDK統合ガイド](guides/sdk-releases/nodejs/nodejs-sdk-integration-guide.md)
         + [Node.js SDK リリースノート](guides/sdk-releases/nodejs/nodejs-sdk-release-notes.md)
      + [SDK ベンチマーク](guides/sdk-releases/java-sdk-benchmarking.md)
+ 機能API {#feature-api}
   + [GET Feature API V3](feature-api/get-feature-api-v3.md)
   + [GET Feature API V2](feature-api/get-feature-api-v2.md)
+ 管理API {#management-api}
   + [機能管理APIの概要](management-api/feature-management-apis-overview.md)
   + [機能フラグ管理API](management-api/feature-flags-management-api.md)
   + [機能グループ管理API](management-api/feature-group-management-api.md)
   + [リリース管理API](management-api/release-management-apis.md)
   + [アプリケーションのクライアント IDを取得](management-api/get-client-id.md)
   + [必要なオーディエンス条件を取得](management-api/get-audience-criteria.md)
   + [管理パッチ API](management-api/management-patch-api.md)
