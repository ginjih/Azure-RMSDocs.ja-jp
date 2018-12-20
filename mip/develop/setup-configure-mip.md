---
title: Microsoft Information Protection (MIP) SDK のセットアップと構成
description: Microsoft Information Protection SDK でビルドされたアプリケーションを使用するには、セットアップと構成の前提条件を提供します。
author: BryanLa
ms.service: information-protection
ms.topic: quickstart
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 2790c64095a6fca4a33f70aeada68fa0c6668020
ms.sourcegitcommit: bdce88088f7a575938db3848dce33e7ae24fdc26
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2018
ms.locfileid: "52386731"
---
# <a name="microsoft-information-protection-mip-sdk-setup-and-configuration"></a>Microsoft Information Protection (MIP) SDK のセットアップと構成 

クイック スタートとチュートリアルの記事では、MIP SDK ライブラリと API を使用するアプリケーションのビルドを中心に説明しています。 この記事では、SDK を使用するための準備として、Office 365 サブスクリプションとクライアント ワークステーションをセットアップして構成する方法を示します。

MIP SDK は、次のプラットフォームで使用できます。  

[!INCLUDE [MIP SDK platform support](../include/mip-sdk-platform-support.md)]

## <a name="prerequisites"></a>前提条件

開始する前に、次のトピックを確認してください。

- [Office 365 セキュリティとコンプライアンス センターとは](https://docs.microsoft.com/office365/securitycompliance/security-and-compliance)
- [Azure Information Protection とは](/azure/information-protection/understand-explore/what-is-information-protection)
- [Azure Information Protection での保護のしくみ](/azure/information-protection/understand-explore/what-is-information-protection#how-data-is-protected)

> [!IMPORTANT]
> **ユーザーのプライバシーを保証するためには、ユーザーに自動ログ記録を有効にする前に同意を求める必要があります。** 次の例では、Microsoft はログ記録の通知を使用する標準的なメッセージを示します。
>
> *エラーとパフォーマンス ログの記録を有効にすると、エラーとパフォーマンス データの Microsoft への送信に同意することになります。Microsoft はインターネット経由でエラーとパフォーマンス データ (以下 "データ") を収集します。Microsoft は、Microsoft 製品およびサービスの品質、セキュリティ、および整合性を向上するためにこのデータを使用します。たとえば、ユーザーが使用している機能、その機能の反応速度、デバイスのパフォーマンス、ユーザー インターフェイスの操作、製品の使用時に発生した問題など、パフォーマンスと信頼性を分析しています。データには、ユーザーが現在実行しているソフトウェアや IP アドレスなど、ソフトウェアの構成に関する情報も含まれます。*

## <a name="sign-up-for-an-office-365-subscription"></a>Office 365 サブスクリプションへのサインアップ

多くの SDK サンプルでは、Office 365 サブスクリプションへのアクセスが必要です。 次のサブスクリプションの種類のいずれかにサインアップしていることを確認します (まだ確認していない場合)。

| 名前 | サインアップ |
|------|---------|
| Office 365 Enterprise E3 評価版 (30 日間の無料評価版) | https://go.microsoft.com/fwlink/p/?LinkID=403802 |
| Office 365 Enterprise E3 または E5 | https://products.office.com/business/office-365-enterprise-e3-business-software |
| Enterprise Mobility and Security E3 または E5 | https://www.microsoft.com/cloud-platform/enterprise-mobility-security |
| Azure Information Protection Premium P1 または P2 | https://azure.microsoft.com/pricing/details/information-protection/ |
| Microsoft 365 E3、E5、または F1 | https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans | 

## <a name="configure-sensitivity-labels"></a>機密ラベルの構成

Azure Information Protection を使用している場合は、Office 365 セキュリティ/コンプライアンス センターにラベルを移行する必要があります。 プロセスの詳細については、「[How to migrate Azure Information Protection labels to the Office 365 Security & Compliance Center](/azure/information-protection/configure-policy-migrate-labels)」 (Azure Information Protection ラベルを Office 365 セキュリティとコンプライアンス センターに移行する方法) を参照してください。 

## <a name="configure-your-client-workstation"></a>クライアント ワークステーションの構成

次に、クライアント コンピューターがセットアップされ、正しく構成されていることを確認するため、次の手順を完了します。

1. Windows 10 ワークステーションを使用している場合:

   - Windows Update を使用して、ご使用のコンピューターを Windows 10 Fall Creators Update (バージョン 1709) 以降に更新します。 現在のバージョンを確認するには、次の手順を実行します。
     - 左下にある Windows アイコンをクリックします。
     - 「PC 情報」と入力し、Enter キーを押します。
     - **[Windows の仕様]** まで下にスクロールして、**[バージョン]** の下を確認します。

   - ご使用のワークステーションで [開発者モード] が有効になっていることを確認します。
     - 左下にある Windows アイコンをクリックします。
     - 「開発者向けの機能の使用」と入力して Enter キーを押すと、**[Use Developer Features]\(開発者向けの機能の使用\)** 項目が表示されます。
     - **[設定]** ダイアログの **[開発者向け]** タブの [Use Developer Features]\(開発者向けの機能の使用\) の下で、**[開発者モード]** オプションを選択します。
     - **[設定]** ダイアログを閉じます。

2. 次のワークロードとオプション コンポーネントを使用して、[Visual Studio 2017](https://visualstudio.microsoft.com/downloads/) をインストールします。
   - **ユニバーサル Windows プラットフォーム開発** Windows ワークロード、および次のオプション コンポーネント:
     - **C++ ユニバーサル Windows プラットフォーム ツール**
     - **Windows 10 SDK 10.0.16299.0 SDK** 以降 (既定で含まれていない場合)
   - **C++ によるデスクトップ開発** Windows ワークロード、および次のオプション コンポーネント:
     - **Windows 10 SDK 10.0.16299.0 SDK** 以降 (既定で含まれていない場合) 

     [![Visual Studio のセットアップ](media/setup-mip-client/visual-studio-install.png)](media/setup-mip-client/visual-studio-install.png#lightbox)

3. [ADAL.PS PowerShell モジュール](https://www.powershellgallery.com/packages/ADAL.PS/3.19.4.2)をインストールします。 

   - モジュールをインストールするには管理者権限が必要なため、最初に次のいずれかを行う必要があります。

     - 管理者権限を持つアカウントを使用してコンピューターにサインインする。
     - 管理者特権を使用して Windows PowerShell セッションを実行する (管理者として実行)。

   - `install-module -name adal.ps` コマンドレットを実行します。

     ```powershell
     PS C:\WINDOWS\system32> install-module -name adal.ps

     Untrusted repository
     You are installing the modules from an untrusted repository. If you trust this repository, change its
     InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
     'PSGallery'?
     [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): A

     PS C:\WINDOWS\system32>
     ```

4. GitHub から SDK サンプルをダウンロードします。 

   - [GitHub プロファイル](https://github.com/join)をまだお持ちでない場合は、まずそれを作成します。
   - 次に、[Software Freedom Conservancy の Git クライアント ツール (Git Bash)](https://git-scm.com/download/) の最新バージョンをインストールします。
   - Git Bash を使用して、関心のあるサンプルをダウンロードします。
     - 次のクエリを使用して、リポジトリを表示します。 https://github.com/Azure-Samples?utf8=%E2%9C%93&q=MipSdk 
     - Git Bash で、`git clone https://github.com/azure-samples/<repo-name>` を使用して各サンプル リポジトリをダウンロードします。

5. SDK バイナリ ファイルとヘッダー ファイルをダウンロードします。

   すべてのプラットフォームの SDK バイナリとヘッダーを含む .zip ファイルは、 https://aka.ms/mipsdkbinaries にあります。 .zip には、複数の追加の .zip ファイル (プラットフォームと API ごとに 1 つ) が含まれています。 ファイルは次のように命名されます。`mip_sdk_<API>_<OS>_1.0.0.0.zip (or .tar.gz)`: ここで、\<API\> = `file`、`protection`、または `upe` で、\<OS\> = プラットフォームです。

   たとえば、Debian での保護 API のバイナリとヘッダーの .zip は次のようになります。`mip_sdk_protection_debian9_1.0.0.0.tar.gz`

   各 .zip や tarball には、次の 3 つのディレクトリが含まれています。

   - **Bins:** 各プラットフォーム アーキテクチャのコンパイル済みバイナリ (該当する場合)
   - **Include:** Microsoft Information Protection SDK ヘッダー ファイル
   - **Samples:** サンプル アプリケーションのソース コード

   Visual Studio の開発を行っている場合は、NuGet パッケージ マネージャー コンソールを使用して SDK をインストールすることもできます。

    ```console
    Install-Package Microsoft.InformationProtection.File
    Install-Package Microsoft.InformationProtection.Policy
    Install-Package Microsoft.InformationProtection.Protection
    ```  
    
6. SDK バイナリのパス (ダイナミック リンク ライブラリ (.dll)) を PATH 環境変数に追加します。 PATH 変数は、実行時にクライアント アプリケーションによって依存 DLL が見つかるようにします。
   - 左下にある Windows アイコンをクリックします。
   - 「パス」と入力して Enter キーを押すと、**[Edit the system environment variables]\(システム環境変数の編集\)** 項目が表示されます。
   - **[システムのプロパティ]** ダイアログで、**[環境変数]** をクリックします。
   - **[環境変数]** ダイアログで、**[User variables for \<user\>]\(<ユーザー> のユーザー変数\)** の下で **[パス]** 変数行をクリックして、**[編集]** をクリックします。
   - **[環境変数の編集]** ダイアログで、新しい編集可能な行を作成する **[新規]** をクリックします。 `file\bins\debug\amd64`、`protection\bins\debug\amd64`、`upe\bins\debug\amd64` の各サブディレクトリへの完全なパスを使用して、それぞれに新しい行を追加します。 SDK ディレクトリは `<API>\bins\<target>\<platform>` の形式で格納されます。
     - \<API\> = `file`、`protection`、`upe`
     - \<target\> = `debug`、`release`
     - \<platform\> = `amd64` (別名: x64)、`x86` など
   
   - **パス**変数の更新が完了したら、**[OK]** をクリックします。 **[環境変数]** ダイアログに戻ったら、**[OK]** をクリックします。

## <a name="register-a-client-application-with-azure-active-directory"></a>Azure Active Directory へのクライアント アプリケーションの登録

Office 365 サブスクリプションのプロビジョニング プロセスの一環として、関連付けられた Azure AD テナントが作成されます。 Azure AD テナントでは、Office 365 *ユーザー アカウント*と*アプリケーション アカウント*の ID とアクセス管理を提供します。 セキュリティで保護された API (MIP API など) へのアクセスを必要とするアプリケーションでは、アプリケーション アカウントが必要です。

実行時の認証と承認では、アカウントの ID 情報から派生した*セキュリティ プリンシパル*によってアカウントが表されます。 アプリケーション アカウントを表すセキュリティ プリンシパルは、[*サービス プリンシパル*](/azure/active-directory/develop/developer-glossary#service-principal-object)と呼ばれます。 

クイック スタートおよび MIP SDK のサンプルで使用するために Azure AD でアプリケーション アカウントを登録するには、次の手順を実行します。

  > [!IMPORTANT] 
  > アカウント作成のために Azure AD テナントの管理にアクセスするには、[サブスクリプションで "所有者" ロール](/azure/billing/billing-add-change-azure-subscription-administrator)のメンバーであるユーザー アカウントを使用して、Azure portal にサインインする必要があります。 テナントの構成によっては、[アプリケーションを登録する](https://ms.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/RegisteredApps)には、"グローバル管理者" ディレクトリ ロールのメンバーである必要もあります。
  > 制限付きのアカウントを使用してテストすることをお勧めします。 アカウントには、必要な SCC エンドポイントにアクセスするための適切な権限のみがあることを確認します。 コマンドラインを通じて渡されたクリア テキスト パスワードは、ログ システムによって収集することができます。

1. [アプリケーションを Azure Active Directory と統合し、アプリケーションを追加するのセクション](/azure/active-directory/develop/quickstart-v1-integrate-apps-with-azure-ad#adding-an-application)の手順に従います。 テスト目的のため、ガイドの手順を進めるときに、指定されたプロパティに次の値を使用します。 
    - **アプリケーションの種類**: [ネイティブ] を選択します。これは、SDK でデモンストレーションされるアプリケーションは、ネイティブにインストールされたコンソール アプリケーションだからです。 ネイティブ アプリケーションは、アプリケーションの資格情報を安全な方法で格納/使用できないため、OAuth2 では "パブリック" クライアントと見なされます。 独自の資格情報を使用して登録される Web アプリケーションなどの "機密性の高い" サーバー ベース アプリケーションとは異なります。 
    - **リダイレクト URI**: SDK は単純なコンソール クライアント アプリケーションを使用しているため、`<app-name>://authorize` の形式で URI を使用します。

2. 完了すると、新しいアプリケーションを登録するため、**[登録されているアプリ]** ページに戻ります。 **[アプリケーション ID]** フィールド内の GUID をコピーして保存します。これはクイック スタートで必要になります。 

3. 次に、**[設定]** をクリックして、クライアントがアクセスする必要がある API とアクセス許可を追加します。 **[設定]** ページで、**[必要なアクセス許可]** をクリックします。

4. 次に、実行時にアプリケーションで要求される MIP API とアクセス許可を追加します。
   - **[必要なアクセス許可]** ページで **[追加]** をクリックします。 
   - **[API アクセスの追加]** ページで **[API の選択]** をクリックします。
   - **[API の選択]** ページで、**[Microsoft Rights Management Services]** API をクリックして、**[選択]** をクリックします。
   - **[アクセスを有効にする]** ページで、API の指定できるアクセス許可に対して、**[ユーザー用の保護されたコンテンツを作成してアクセスする]** をクリックして、**[選択]**、**[完了]** の順にクリックします。

5. 手順 4 を繰り返しますが、今回は **[API の選択]** ページで API を検索する必要があります。
   - **[API の選択]** ページの検索ボックスに「**Microsoft Information Protection 同期サービス**」と入力し、その API をクリックし、**[選択]** をクリックします。
   - **[アクセスを有効にする]** ページで、API の指定できるアクセス許可に対して、**[Read all unified policies a user has access to]\(ユーザーがアクセスするすべての統一されたポリシーを読み取る\)** をクリックし、**[選択]**、**[完了]** の順にクリックします。

6. **[必要なアクセス許可]** ページに戻ったら、**[アクセス許可の付与]**、**[はい]** の順にクリックします。 この手順により、指定されたアクセス許可で API にアクセスするための事前の同意が、この登録を使用してアプリケーションに与えられます。 グローバル管理者としてサインインした場合は、アプリケーションを実行しているテナント内のすべてのユーザーに対して同意が記録されます。それ以外の場合は、自分のユーザー アカウントにのみ同意が適用されます。 

完了すると、アプリケーションの登録と API のアクセス許可は、次の例のようになるはずです。

   [![Azure AD アプリの登録](media/setup-mip-client/aad-app-registration.png)](media/setup-mip-client/aad-app-registration.png#lightbox)


登録に API とアクセス許可を追加する方法の詳細については、[アプリケーションを更新し、Web API にアクセスするようにクライアント アプリケーションを構成するのセクション](/azure/active-directory/develop/quickstart-v1-integrate-apps-with-azure-ad#updating-an-application)を参照してください。 ここでは、クライアント アプリケーションで必要な API とアクセス許可の追加に関する情報が見つかります。  

## <a name="request-an-information-protection-integration-agreement-ipia"></a>Information Protection Integration Agreement (IPIA) を申請する

MIP で開発されたアプリケーションをリリースすることができます、前にの適用し、Microsoft との正式な取り決めを完了する必要があります。

1. 次の情報を記載した電子メールを [IPIA@microsoft.com](mailto:IPIA@microsoft.com?subject=Requesting%20IPIA%20for%20<company-name>) に送信して、IPIA を入手します。

   **件名:** *会社名* の IPIA 申し込み

   電子メールの本文に、次の情報を含めます。
   - アプリケーションと製品名
   - 要求者の氏名
   - 要求者の電子メール アドレス

2. IPIA 申請が受信されると、(Word 文書形式の) フォームがお客様に送信されます。 IPIA の使用条件を確認し、次の情報をフォームに入力して [IPIA@microsoft.com](mailto:IPIA@microsoft.com?subject=IPIA%20Response%20for%20<company-name>) に返送します。

   - 会社の正式名称
   - 法人の都道府県または国
   - 会社の URL
   - 連絡先の電子メール アドレス
   - (省略可能) 会社の追加住所
   - 会社のアプリケーションの名前
   - アプリケーションの簡単な説明
   - *Azure テナント ID*
   - アプリケーションの*アプリ ID*
   - 緊急時の会社の連絡先、電子メール アドレス、および電話番号

3. フォームが受信されると、デジタル署名を行うための最終的な IPIA リンクがお客様に送信されます。 お客様の署名後、適切な Microsoft 担当者が署名することで、契約が締結されます。

### <a name="already-have-a-signed-ipia"></a>既に署名済みの IPIA がある場合

署名済みの IPIA が既に存在し、リリースするアプリケーション用に新しい *アプリ ID* を追加する場合は、電子メールに次の情報を記載して [IPIA@microsoft.com](mailto:IPIA@microsoft.com?subject=Updating%20IPIA%20for%20<company-name>) に送信します。

- 会社のアプリケーションの名前
- アプリケーションの簡単な説明
- Azure テナント ID (以前と同じ場合でも記載)
- アプリケーションのアプリ ID
- 緊急時の会社の連絡先、電子メール アドレス、および電話番号

電子メールの送信時には、受領の確認には最大で 72 時間かかることをご了承ください。

## <a name="next-steps"></a>次の手順

- MIP SDK はほぼ完全に非同期に設計されているため、クイック スタート セクションを開始する前に、必ず [MIP SDK のオブザーバー](concept-async-observers.md)のページをお読みください。
- SDK を使用した実践的な体験をする準備ができたら、「[Quickstart: Client application initialization (C++)](quick-app-initialization-cpp.md)」 (クイック スタート: クライアント アプリケーションの初期化 (C++)) を開始します。

