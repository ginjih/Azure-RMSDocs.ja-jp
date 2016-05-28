---
# required metadata

title: Rights Management 共有アプリケーションをダウンロードしてインストールする | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 2bf09690-9dba-43b7-9e0a-0110915d4081

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Rights Management 共有アプリケーションをダウンロードしてインストールする
RMS 共有アプリケーションをインストールするのにローカル管理者である必要はありません。 ただし、ローカル管理者ではなく、かつ Office 2010 を使用している場合は、いくつか制限があります。 詳細については、このページの「[ローカル管理者ではなく、かつ Office 2010 を使用している場合](#if-you-are-not-a-local-administrator-and-use-office-2010)」を参照してください。

## Rights Management 共有アプリケーションをダウンロードしてインストールするには

1.  Microsoft Web サイトの [Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970) ページに移動します。

2.  [ **コンピューター** ] セクションで、 **Windows 用 RMS アプリケーション** のアイコンをクリックして、Microsoft Rights Management 共有アプリケーションをインストールする **Setup.exe** ファイルを保存します。

3.  ダウンロードされた Setup.exe ファイルをダブルクリックします。 続行を確認するメッセージが表示されたら、[ **はい**] をクリックします。

4.  [ **Microsoft RMS のセットアップ** ] ページで、[ **次へ**] をクリックし、インストールが完了するまで待機します。

    > [!NOTE]
    > RMS 共有アプリケーションには、Microsoft .NET Framework のバージョン 4.0 以上が必要です。 これがインストールされているかどうかがセットアップで確認され、インストールされていない場合は、インストールするためのリンクを含むメッセージが表示されます。

5.  インストールが完了したら、[ **再起動** ] をクリックして、コンピューターを再起動し、インストールを完了します。 または、[ **閉じる** ] をクリックして、後でコンピューターを再起動し、インストールを完了します。

これで、ファイルの保護を開始したり、他のユーザーが保護しているファイルを読み取ったりする準備ができました。

## ローカル管理者ではなく、かつ Office 2010 を使用している場合
コンピューターへのサインイン時にローカルの管理者権限を持っておらず、かつセットアップ時に Office 2010 がインストールされていることが検出される場合、この構成では一部のシナリオがうまくいかないことを示す警告メッセージが表示されます。 シナリオは次のとおりです。

-   組織が RMS のオンプレミス バージョンではなく Azure RMS を使用している場合

    -   Office の Information Rights Management (IRM) の機能は利用できません。 たとえば、メールの **[転送不可]** オプションや、Word と Excel の **[ファイル]** メニューから設定できる **[アクセスの制限]** アクセス許可は利用できません。 リボンの [保護ファイルの共有] オプションやエクスプローラーの右クリック オプションを使用できます。

-   組織が Azure RMS ではなく RMS のオンプレミス バージョンを使用している場合

    -   Azure RMS を使用している他の組織の人間から送信された、保護されたドキュメントを読み取ることはできません。

ローカル管理者でなくとも、Office 365 または Office 2013 を使用している場合は、このメッセージが表示されません。これらのシナリオはサポートされています。

このような既知の制限はありますが、インストールを続行できます。 また、インストールを中止することもできます。その場合、手順 3. で Setup.exe を実行するときに **[管理者として実行]** オプションを使用して再実行するか、管理者にインストールしてもらうように依頼できます。 管理者は、インストールが自動的に行われるように[このインストールをスクリプト化](sharing-app-admin-guide.md#automatic-deployment-for-the-microsoft-rights-management-sharing-application)できます。

## 例とその他の説明
Rights Management 共有アプリケーションの使用方法の例と操作手順については、Rights Management 共有アプリケーション ユーザー ガイドの次のセクションをご覧ください。

-   [RMS 共有アプリケーションの使用例](sharing-app-user-guide.md#examples-for-using-the-rms-sharing-application)

-   [作業内容](sharing-app-user-guide.md##what-do-you-want-to-do-)

## 参照
[Rights Management 共有アプリケーション ユーザー ガイド](sharing-app-user-guide.md)



<!--HONumber=Apr16_HO3-->

