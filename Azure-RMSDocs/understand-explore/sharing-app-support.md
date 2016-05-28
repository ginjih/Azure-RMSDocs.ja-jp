---
# required metadata

title: Windows およびモバイル プラットフォーム用の RMS 共有アプリケーション | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 1da6e372-2b3f-4af7-80f7-6b9073dff7f5

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Windows およびモバイル プラットフォーム用の RMS 共有アプリケーション
RMS 共有アプリケーションは、無料でダウンロードできるアプリケーションであり、Office 2010 のサポートには必須で、Windows コンピューター、Mac コンピューター、モバイル デバイスにも推奨されます。 利点の 1 つとして、[!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] をネイティブでサポートしないアプリケーションやファイルの一般的な保護を適用できることが挙げられます。つまり、すべてのファイルを保護できます。 各種の保護レベルの詳細については、「[Rights Management 共有アプリケーション管理者ガイド](../rms-client/sharing-app-admin-guide-technical.md#levels-of-protection-native-and-generic)」の「[保護のレベル – ネイティブと汎用](../rms-client/sharing-app-admin-guide.md)」セクションを参照してください。

ユーザーが RMS 共有アプリケーションを使用してファイルを保護すると、ユーザーが保護したドキュメントを追跡したり、必要に応じてそれらへのアクセスを取り消したりすることもできます。 これを行うには、 [ドキュメント追跡サイト](http://go.microsoft.com/fwlink/?LinkId=529562)を使用します。

Windows コンピューターの場合、RMS 共有アプリケーションは、ユーザーが既に使用しているアプリケーションに既に統合されていて機能を拡張しています。

-   Word、Excel、PowerPoint、および Outlook 用の Office アドインのインストール。 このアドオンにより、**[Share Protected]** (保護ファイルの共有) ボタンがリボンに表示され、このボタンをクリックすると、電子メールで送信されるファイルの保護の設定に最もよく使用される、使いやすいダイアログ ボックスが開きます。 また、このボタンを利用するとドキュメント追跡サイトに簡単にアクセスできます。

-   エクスプローラーの新しい右クリック オプション。 このオプションにより、**[Protect in-place]** (保護済み) オプションが表示され、このボタンをクリックすると、ディスクに保存されているファイルの保護の設定に最もよく使用される、使いやすいダイアログ ボックスが開きます。

-   [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] によって保護されているファイルを開くためのビューアー。 このビューアーは、保護されたファイルを開くことができるアプリケーションが他にインストールされていない場合に自動的に起動します。

-   Office 2010 のバックエンド構成により、このスイートの Word、Excel、PowerPoint、および Outlook が [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] とシームレスに連携できるようになります。

Windows 用の RMS 共有アプリケーションは、 [Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970)ページを使用して 1 つのコンピューターにダウンロードしてインストールできますが、サイレント インストールおよびカスタム構成のためのエンタープライズ デプロイもサポートされています。 詳細については、次のリソースを参照してください。

-   [保護のレベル – ネイティブと汎用](../rms-client/sharing-app-admin-guide.md)

-   [Rights Management 共有アプリケーション ユーザー ガイド](../rms-client/sharing-app-user-guide.md)

モバイル デバイス用の RMS 共有アプリケーションは、iPad、iPhone、Android、Windows Phone、Windows RT などの最も一般的に使用されているモバイル デバイスをサポートします。 ユーザーは、関連するストアからこのアプリをダウンロードできます。 [Microsoft Rights Management ページ](http://go.microsoft.com/fwlink/?LinkId=303970)には、それらのリンクがあります。

**Microsoft Intune がある場合**: RMS 共有アプリには Microsoft Intune アプリ ソフトウェア開発キットが含まれているため、次のオプションを使用できます。

-   Intune で登録されている iOS および Android デバイス用のアプリをデプロイおよび管理する。

-   Intune で登録されていない Android デバイス用のアプリを管理する。


## 次のステップ
「[アプリケーションで Azure Rights Management をサポートする方法](applications-support.md)」を参照して、他のアプリケーションおよびサービスで Azure Rights Management をサポートする方法について確認してください。



<!--HONumber=Apr16_HO3-->

