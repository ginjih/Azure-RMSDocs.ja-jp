---
# required metadata

title: リリース ノート | Azure RMS
description:
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 84a93d5b-37e9-4d9c-9b7c-ad00963a68d7

# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

﻿
# リリース ノート

このトピックには、RMS SDK 2.1 のこのリリースおよびそれ以前のリリースに関する重要な情報が含まれています。

## 2015 年 12 月の更新の新しい点

-   以下を含む一部の領域のパフォーマンスが向上しました。

    ライセンス専用のサーバーを使用する場合は、プライマリのライセンス サーバーから発行します。

    ネットワーク接続がない場合に RMS SDK 2.1 が失敗するまでの時間が短縮されています。

-   エラー メッセージやトラブルシューティングを向上させる多くの更新があります。
-   [サポートされているプラットフォーム](supported-platforms.md)一覧も更新されました。

## 2015 年 5 月の更新

-   **サービス アプリケーションとクラウド ベースの RMS** – [**IPC\_CREDENTIAL\_SYMMETRIC\_KEY**](/rights-management/sdk/2.1/api/win/ipc_credential#msipc_ipc_credential_symmetric_key) に 3 つの情報 (対称キー、**AppPrincipalId**、**TenantBposId**) が必要です。 この点についてのトピックが更新され、この情報取得の処理に関するガイダンスが用意されました。 この更新については、「[クラウド ベース RMS でのサービス アプリケーション使用の有効化](how-to-use-file-api-with-aadrm-cloud.md)」を参照してください。

## 2015 年 4 月の更新

-   一連の新しい API で**ドキュメント追跡** が可能になりました。 詳細については、「[Tracking Content](tracking-content.md)」 (コンテンツの追跡) を参照してください。
-   **暗号化の種類** – 暗号化パッケージの選択の API レベルでの制御をサポートします。 詳細については、「[Working with encryption](working-with-encryption.md)」 (暗号化の処理) を参照してください。

    **注**  API の **IPC\_LI\_DEPRECATED\_ENCRYPTION\_ALGORITHMS** フラグは非公開となりました。 今後、このフラグを参照しても、アプリケーションでコンパイルされませんが、既にビルドされたアプリケーションではこのフラグを API コード内でプライベートに評価するため、引き続き機能します。 フラグを変更するだけでも、古い非推奨の暗号化アルゴリズムのフラグの機能を利用できます。 詳細については、「[Working with encryption](working-with-encryption.md)」 (暗号化の処理) を参照してください。

     

-   **サーバー モード アプリケーション**は **IPC\_API\_MODE\_SERVER** の [**API モード値**](/rights-management/sdk/2.1/api/win/api%20mode%20values#msipc_api_mode_values_IPC_API_MODE_SERVER) を使用し、アプリケーション マニフェストは不要になりました。 運用 RMS サーバーに対してアプリケーションをテストすることができ、運用環境に切り替えるときに運用のライセンスを取得する必要はありません。 サーバー モード アプリケーションの詳細については、「[アプリケーションの種類](application-types.md)」を参照してください。
-   **ログ**は、ファイルと Event Tracing for Windows メソッドの両方で実装されました。
-   **Windows 7 SP1 または Windows Server 2008 R2 コンピューター**を実行している場合は、「開発者向けの重要な注意事項」の下の記述を参照してください。

## 2015 年 1 月の更新

-   **保護されたファイル (pfile) のサポート対象サイズの増加** – 1 GB より大きいサイズの pfile がサポートされるようになりました。 pfile の詳細については、「[Support File Formats](supported-file-formats.md)」 (サポート されるファイル形式) を参照してください。
-   **ログの強化による診断の向上** – 確認する必要があるメッセージが**エラー**または**警告**のログ レベルで表示されます。 表示されている例外など、他のすべてのメッセージは**情報**としてログに記録されます。

    詳細情報が失われないようにするために、この方法を選択しました。 これにより、重要なメッセージだけが警告レベルで表示されるようになりました。

-   **会社テンプレートの取得** – ユーザーからのレポートやフィードバックに基づき、テンプレート取得コードが大幅に修正されました。
-   強化されたローカライズの整合性

## 2014 年 10 月の更新

-   SDK のファイル API のコンポーネントの既定の動作が更新されました。 詳細については、「 [ファイル API の構成](file-api-configuration.md)」を参照してください。
-   新機能の電子メール通知については、開発者向け注意事項のトピック「[電子メール通知の有効化](how-to-enable-email-notification.md)」を参照してください。

## 2014 年 7 月の更新

SDK のファイル API のコンポーネントが拡張され、次の機能が提供されるようになりました。

-   使用する保護機能を識別します。
-   ファイル レベルの粒度で RMS 保護を提供します。

    このリリースで追加された関数:

    **注**  ここに記載されている以外に、ファイル API の拡張機能として、サポートされるデータ型と構造体が追加されました。 このリリースで更新されているすべてのトピックに、"**暫定的なものであり、変更される可能性があります**" と記載されています。

     

    -   [**IpcfOpenFileOnHandle**]()
    -   [**IpcfOpenFileOnILockBytes**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfopenfileonilockbytes)
    -   [**IpcfGetFileProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfgetfileproperty)
    -   [**IpcfLogicalFileRangeToRawFileRange**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcflogicalfilerangetorawfilerange)
    -   [**IpcfReadFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfreadfile)
    -   [**IpcfSetEndOfFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfsetendoffile)
    -   [**IpcfWriteFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfwritefile)

## 2014 年 4 月の更新

-   **ファイル API のメモリ使用率** (特に大規模な PFile の場合) が大幅に改善されました。
-   **コンテンツ ID** は、**IPC\_LI\_CONTENT\_ID** プロパティを使用して書き込み可能になりました。 詳細については、「[**License property types**](/rights-management/sdk/2.1/api/win/License%20property%20types#msipc_license_property_types_IPC_LI_APP_SPECIFIC_DATA)」 (ライセンスのプロパティの種類) を参照してください。
-   **運用マニフェストの要件** – RMS 対応のアプリケーション/サービスをサーバー モードで実行する場合には、マニフェストは不要になりました。 詳細については、「[Application types](application-types.md)」 (アプリケーションの種類) を参照してください。
-   **ドキュメントの更新**

    **再構成** – 「[How-to use](how-to-use-msipc.md)」 (使用方法) の説明を用意し、環境の設定とアプリケーションのテスト手順の順序を明確にしています。

    **ベスト プラクティスのテスト** – Azure RMS でテストする前にオンプレミス サーバーを使用する場合のガイダンスを追加しました。 詳細については、「[クラウド ベース RMS でのサービス アプリケーション使用の有効化](how-to-use-file-api-with-aadrm-cloud.md)」を参照してください。

## 開発者向けの重要な注意事項

-   **あらゆるファイルの種類のネイティブ サポート**

    Rights Management サービス SDK 2.1 のこのリリースでは、あらゆるファイルの種類 (拡張子) のネイティブ サポートを追加できます。 たとえば、拡張子 &lt;ext&gt; (Office 以外および pdf) では、その拡張子の管理者の構成が "NATIVE" の場合、\*.p&lt;ext&gt; が使用されます。

    サポートされているファイルの種類の詳細については、「[ファイル API の構成](file-api-configuration.md)」を参照してください。

-   **Windows 7 SP1 および Windows Server 2008 R2 SP1 コンピューター**に更新プログラム [KB2533623](https://support.microsoft.com/en-us/kb/2533623) が適用されていない場合、office ファイルを保護する際に "パラメーターが正しくありません。 エラー コード 0x80070057" というエラーが発生することがあります。 このエラーが表示された場合は、更新プログラムをインストールしてやり直してください。 それでも問題が解決しない場合は、RMS SDK ベータ フィードバック (<rmcstbeta@microsoft.com>) にお問い合わせください。

    **注**  2015 年 4 月のリリース時点で、この更新プログラムのインストール プロセスにチェックが追加されました。

     

-   **ファイル API の統合**

    Active Directory Rights Management サービスのファイル API は、ファイル API の追加により次の利点と機能を提供します。

    機密データを自動化された方法で保護することが可能であり、さまざまなファイル形式で使用される Information Rights Management (IRM) の実装の詳細を知る必要はありません。

    Microsoft Office ファイル、Portable Document Format (PDF) ファイル、および他の一部のファイルの種類は、ネイティブ保護を使用して保護することができます。 ネイティブ保護で保護できるファイルの種類の一覧については、「[ファイル API の構成](file-api-configuration.md)」を参照してください。

    システム ファイルと Office ファイルを除く、すべてのファイルは、RMS 保護されたファイル形式 (PFile) を使用して保護できます。

-   **問題**: ライセンスを最初から作成する場合は、所有権を明示的に許可する必要があります。

    **ソリューション**: ライセンスを最初から作成する場合は、アプリケーションで [**IpcCreateLicenseFromScratch**](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensefromscratch) を使用して、ライセンス所有者に**所有者**権限を明示的に追加する必要があります。 詳細については、「[Add explicit owner rights](add-explicit-owner-rights.md)」 (所有権を明示的に追加する) を参照してください。

-   **問題**: アプリケーションがハンドルを使用して、同じウィンドウに対して [**IpcProtectWindow**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcprotectwindow) または [**IpcUnprotectWindow**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcunprotectwindow) を 2 回呼び出した場合、RMS SDK 2.1 は **HRESULT** にエラーを返します。

    **ソリューション**: この問題に対する具体的なガイダンスについては、[**IpcProtectWindow**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcprotectwindow) および [**IpcUnprotectWindow**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcunprotectwindow) の「解説」を参照してください。

-   **問題**: 複数のアーキテクチャをビルドする場合は、このガイダンスに従う必要があります。

    **ソリューション**: Ipcsecproc\*isv.dll を異なるアーキテクチャに使用する場合 (たとえば、64 ビット コンピューターに 64 ビット SDK がインストールされていて、Ipcsecproc\*isv.dll を必要とする 32 ビット コンピューターに 32 ビット SDK をインストールしなければならない場合)、32 ビット SDK を別のコンピューターにインストールし、%PROGRAMFILES%\\Microsoft Information Protection And Control フォルダー (既定の場所または SDK のインストール先として選択した任意の場所) から Ipcsecproc\*isv.dll ファイルをコピーする必要があります。

## よく寄せられる質問

**Q**: LCID パラメーターを受け取る関数では、既定の言語の動作はどうなるでしょうか。

**A**: 既定のロケールには 0 を使用します。 この場合、AD RMS Client 2.1 では、名前と説明を次の順序でを検索し、使用可能な最初の値を取得します。

1 – ユーザーが指定した LCID。
2 – システム ロケール LCID。
3 – Rights Management サーバー (RMS) テンプレートで指定された、使用可能な最初の言語。
名前と説明を取得できない場合、エラーが返されます。 名前と説明は、1 つの LCID に 1 つだけ存在できます。

## 関連項目

* [概要](ad-rms-overview.md)
* [明示的な所有者権限の追加](add-explicit-owner-rights.md)
* [ファイル API の構成](file-api-configuration.md)
* [**IpcfGetSerializedLicenseFromFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfgetserializedlicensefromfile)
* [**IpcfEncryptFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfile)
* [**IpcfDecryptFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfdecryptfile)
* [**IpcfIsFileEncrypted**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfisfileencrypted)
* [**IpcCreateLicenseFromScratch**](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensefromscratch)
* [**IpcProtectWindow**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcprotectwindow)
* [**IpcUnprotectWindow**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcunprotectwindow)
 

 





<!--HONumber=Apr16_HO3-->

