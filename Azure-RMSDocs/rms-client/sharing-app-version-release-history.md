---
# required metadata

title: Rights Management 共有アプリケーション&colon; バージョン リリース履歴 | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 6751bd90-959f-4eba-91ed-6588ac983762

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Rights Management 共有アプリケーション: バージョン リリース履歴
Rights Management チームは、Rights Management 共有アプリケーションの修正プログラムと新機能を定期的に更新しています。 次の情報を使用して、リリースの新機能や変更内容をご確認ください。 最新のリリースは一番上に表示されます。

2015 年 1 月 1 日より前のバージョンは表示されません。

> [!NOTE]
> RMS 共有アプリケーションに関するフィードバックまたはご質問については、 [AskIPTeam](mailto:AskIPTeam@microsoft.com?subject=RMS%20sharing%20app:%20Feedback%20or%20question)まで電子メール メッセージをお送りください。

## バージョン 1.0.2004.0
**リリース日**: 2015 年 12 月 11 日

**修正内容**:

-   ファイルの所有者と "**共同所有者**" アクセス許可レベルが付与されているユーザーのみがファイルの保護を解除できます。 以前は、ファイルの所有者と "**共同作成者**" および "**共同所有者**" アクセス許可レベルが付与されているユーザーのみがファイルの保護を解除できました。

-   RMS で保護された読み取り専用 **.ptif** ファイルを生成するための、**.tif** ファイル (および .tiff ファイル) のネイティブ保護。

-   エラー メッセージの改善 (正確さと明確さ)。

-   コンテンツの暗号化と暗号化解除に関するパフォーマンスの向上。

**新機能**:

-   管理者以外によるインストールのサポート。これにより、標準ユーザーは RMS 共有アプリケーションをインストールできます。

    Office 2010 を実行している標準ユーザーの場合は、いくつか制限があります。 詳細については、「[Rights Management 共有アプリケーションをダウンロードしてインストールする](install-sharing-app.md)」の「[ローカル管理者ではなく、かつ Office 2010 を使用している場合](install-sharing-app.md#if-you-are-not-a-local-administrator-and-use-office-2010)」セクションを参照してください。

## バージョン 1.0.1908.0
**リリース日**: 2015 年 9 月 16 日

**修正内容**:

-   Azure RMS 用の多要素認証 (MFA) をサポートするようになりました。それにより、最新の認証を利用するアプリケーションの Microsoft サインイン アシスタントへの依存関係が削除されました。

    詳細については、「[Azure Rights Management の要件](../get-started/requirements-azure-rms.md)」の「[多要素認証 (MFA) と Azure RMS](../get-started/requirements-azure-ad.md#multi-factor-authentication-mfa-and-azure-rms)」セクションを参照してください。

## バージョン 1.0.1784.0
**リリース日**: 2015 年 7 月 30 日

**修正内容**:

-   権限ポリシー テンプレートの既定の更新間隔が 7 日から 1 日に短縮されました。

-   少数の回帰とマイナー バグ。

## バージョン 1.0.1770.0
**リリース日**: 2015 年 4 月 25 日

**修正内容**:

-   所有者と共同所有者のみが保護を削除できるようになりました。 共同作成者は保護を削除できません。

-   ネットワーク共有上のファイルを保護できるようになりました。

**新機能**:

-   ドキュメントの追跡と取り消しをサポートします。 詳細については、「[RMS 共有アプリケーションを使用してドキュメントを追跡および取り消す](sharing-app-track-revoke.md)」を参照してください。

-   **[保護ファイルの共有]**を選んだ場合のテンプレートのサポート:

    -   テンプレートを選べるようになりました。

    -   スライダーの代わりに、テンプレートとカスタム アクセス許可を含むリスト ボックスが表示されます。

    -   **[すべてのデバイスで使用を許可する]** と **[使用制限を強制する]**のオプションが表示されなくなりました。 代わりに、ファイルの種類によって **[一般保護]** が自動的に選択されます。

    詳細については、「[Rights Management 共有アプリケーションのダイアログ ボックス オプション](sharing-app-dialog-box.md)」を参照してください。

## バージョン 1.0.1667.0
**リリース日**: 2015 年 1 月 19 日

**修正内容**:

-   RMS 共有アプリの PPDF ビューアーで中国語のフォントをサポートするようになりました。

-   エラー処理とメッセージングが向上しました。

-   新しいバージョンのアプリがダウンロード可能になったときの自動更新通知に関する問題が修正されました。

**新機能**:

-   **組織内の複数の電子メール ドメインのサポート**: AD RMS を使用している組織のユーザーが複数の電子メール ドメインを持つ場合、この更新プログラムによって、このユーザーは、他のドメイン内にある自分の組織のユーザーによって保護されているコンテンツを使用できます。 詳細については、「[Rights Management 共有アプリケーション管理者ガイド](sharing-app-admin-guide.md)」の「[AD RMS のみ: 組織内での複数の電子メール ドメインのサポート](sharing-app-admin-guide.md#ad-rms-only-support-for-multiple-email-domains-within-your-organization)」セクションを参照してください。



<!--HONumber=Apr16_HO3-->

