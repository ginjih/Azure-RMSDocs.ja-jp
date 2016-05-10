---
# required metadata

title: シナリオ - SharePoint に保存されているドキュメントを管理する | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 1b6244c7-5ab9-4881-bc8f-6fa960390d89

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# シナリオ - SharePoint に保存されているドキュメントを管理する
このシナリオおよびサポート ユーザー ドキュメントでは、Azure Rights Management を使用して、SharePoint に保存されている Office ドキュメントが自分の管理下にあることを確認します。この場合、保護されたライブラリを使用します。 たとえばドキュメントは、偶発的またはユーザーの故意による漏えいから自動的に保護され、ドキュメントがダウンロードや同期された後でも、コンテンツへのアクセスをブロックすることができます。 保護するファイルの例としては、組織内での共同作業用の設計文書や企画、その他の成果物などがあります。 SharePoint で保護されたライブラリを構成すると、SharePoint 内の Office ファイルは Azure Rights Management によって保護されます。

この手順は、次の一連の状況に適しています。

-   従業員は、SharePoint ライブラリ内の Office ドキュメントを使って共有したり、共同作業したりします。

-   管理者がライブラリ レベルで設定したアクセス許可を、従業員が設定したり変更したりする必要はありません。

-   従業員は、組織外のユーザーとこれらのドキュメントを共有する必要はありません。

## デプロイの手順
![](../media/AzRMS_AdminBanner.png)

ユーザー ドキュメントを参照する前に、次の要件を満たしていることを確認し、サポートされる手順に従ってください。

## このシナリオの要件
このシナリオを実現するには、次の内容が必要になります。

|要件|詳細情報が必要な場合|
|---------------|--------------------------------|
|Office 365 または Azure Active Directory のアカウントとグループを準備した|[Azure Rights Management の準備を行う](https://technet.microsoft.com/library/jj585029.aspx)|
|Rights Management がアクティブ化されている|[Rights Management をアクティブにする](https://technet.microsoft.com/library/jj658941.aspx)|
|SharePoint サーバーを使用する場合:RMS コネクタをデプロイし、SharePoint 用に構成する|[Azure Rights Management コネクタをデプロイする](https://technet.microsoft.com/library/dn375964.aspx)|
|保護する SharePoint サイトのアクセス許可を構成する|[リスト、ライブラリ、フォルダー、ドキュメント、またはリスト アイテムのアクセス許可を管理する](https://support.office.com/en-ca/article/Manage-permissions-for-a-list-library-folder-document-or-list-item-9d13e7df-a770-4646-91ab-e3c117fcef45)<br /><br />[Information Rights Management をリストまたはライブラリに適用する](http://office.microsoft.com/sharepoint-help/apply-information-rights-management-to-a-list-or-library-HA102891460.aspx)|
|SharePoint を IRM と保護されたライブラリ用に構成する|[SharePoint 管理センターにおける Information Rights Management (IRM) の設定](https://support.office.com/en-us/article/Set-up-Information-Rights-Management-IRM-in-SharePoint-admin-center-239ce6eb-4e81-42db-bf86-a01362fed65c)<br /><br />[Information Rights Management をリストまたはライブラリに適用する](http://office.microsoft.com/sharepoint-help/apply-information-rights-management-to-a-list-or-library-HA102891460.aspx)|

### IRM 設定用の SharePoint ライブラリを構成するには

1.  IRM サービスを使用するように SharePoint を構成したら、Azure RMS で保護する SharePoint ライブラリに移動します。 サイトの **[設定]** &gt; **[Information Rights Management (IRM)]** ページで、**[ダウンロード時にこのライブラリへのアクセス許可を制限する]** を選択し、管理者用のポリシーのタイトルとユーザー用のポリシーの説明を指定して、**[オプションの表示]** をクリックします。

2.  次の項目を選択します。

    -   **IRM をサポートしないドキュメントのアップロードをユーザーに許可しない**

    -   省略可能: **[グループの保護を許可します。既定のグループ]** を選択し、SharePoint の外部で、このライブラリに保存されているドキュメントでの共同作業が必要になる可能性のある追加のグループの名前を指定します。 たとえば、営業グループにサイトの編集が許可されており、このグループのだれかがドキュメントをダウンロードしてディスクに保存し、営業グループに属していない共同作業者にメールで送信するとします。 共同作業者がここで指定したグループに属している場合、その共同作業者はサイト用に構成された同じアクセス許可を自動的に継承し、ドキュメントを編集できます。

        このオプションを使用しない場合は、SharePoint ライブラリにアクセスできるユーザーだけがこれらのドキュメントで共同作業できます。そのためには、SharePoint から直接ドキュメントをダウンロードする必要があります。 多くの場合、この制限が適切です。

## ユーザー ドキュメントの手順
保護されたライブラリには、ユーザーが取るべき手順は特にないため、このシナリオではユーザーに説明する必要のある手順はありません。 SharePoint の管理者がサイトに設定したアクセス許可に従って、ドキュメントはダウンロード時に自動的に保護されます。 ただし、ユーザーが次に行うべき操作を把握できるように、この変更についてユーザーに通知し、どのライブラリが保護されているのか、それによってドキュメント使用がどのように制限されるのかをヘルプ デスクに伝えておく必要があります。 たとえば、現在の制限によって、モバイル デバイスではドキュメントを閲覧できるが、編集はできないといった場合があります。 グループの保護を構成した場合は、SharePoint の外部でドキュメントにアクセスし、編集できるグループをユーザーに伝えておく必要があります。

次のテンプレートを使用して、お知らせをコピーしてエンド ユーザーの通信欄に貼り付け、環境に合わせて次の変更を行います。

1.  *&lt;SharePoint ライブラリの名前&gt;* の各インスタンスは、Azure Rights Management 用に構成した SharePoint ライブラリの名前とリンクに置き換えます。 複数の保護されているライブラリ用の通信の場合は、それに応じて手順を変更します。

2.  **[グループの保護を許可します。既定のグループ]** オプションを構成した場合は、*&lt;グループ名&gt;* を構成済みのグループの名前に置き換えて、&lt;(SharePoint ライブラリを使用せずに) ファイルで共同作業するためのアクセス許可がこのグループに付与されている理由&gt; に理由を指定します。 このオプションを構成しなかった場合は、この文を削除します。

3.  *&lt;連絡先の詳細&gt;* を、Web サイト リンク、電子メール アドレス、電話番号など、ユーザーがヘルプ デスクに連絡を取るための方法を示す手順に置き換えます。

4.  必要に応じてお知らせに変更を加え、変更したお知らせをユーザーに送信します。

ドキュメントの例では、カスタマイズ後、このお知らせがユーザーにどのように表示されるかを示します。

![](../media/AzRMS_UsersBanner.png)

### IT からのお知らせ: &lt;SharePoint ライブラリの名前&gt; サイトの変更
**&lt;SharePoint ライブラリの名前&gt;** の SharePoint サイトは、コラボレーションの安全性向上のため構成が変更されました。 現在、このサイトのこれらのドキュメントは、ローカルに保存した場合でも他の人にメールで送信した場合でも、開くことができるのは &lt;グループ名&gt; のメンバーのみです。 例外として、ドキュメントをダウンロードした後に、&lt;グループ名&gt; のメンバーとドキュメントを共有できます。そのため、&lt;(SharePoint ライブラリを使用せずに) ファイルで共同作業するためのアクセス許可がこのグループに付与されている理由&gt;。 ファイルを編集するときに、ドキュメントの上部に黄色の情報バナーが表示されます。これにより、ドキュメントが保護されていることと、ファイルにアクセスできるユーザーがわかります。

この変更は、会社の機密データを、見るべきでないユーザーから保護するのに役立ちます。 モバイル デバイスを使用してこのような保護されたドキュメントにアクセスする場合、ドキュメントを閲覧することはできますが、編集するにはデスクトップ デバイスを使う必要があります。

ドキュメントで安全なコラボレーションがサポートされていない場合は、&lt;SharePoint サイトの名前&gt; サイトにドキュメントをアップロードすることはできません。

**サポートが必要な場合は、**

-   ヘルプ デスクに問い合わせる: &lt;連絡先の詳細&gt;

### ユーザー ドキュメントの例
![](../media/AzRMS_ExampleBanner.png)

#### IT からのお知らせ：売上の予測とレポート サイトへの変更
**売上予測とレポート**の SharePoint サイトは、コラボレーションの安全性向上のため構成が変更されました。 現在、このサイトのこれらのドキュメントは、ローカルに保存した場合でも他の人にメールで送信した場合でも、開くことができるのは営業/マーケティング チームのメンバーのみです。 例外として、ドキュメントをダウンロードした後に財務チームのメンバーと共有することができます。これで財務チームのメンバーは毎月の予測数値を抽出できます。 ファイルを編集するときに、ドキュメントの上部に黄色の情報バナーが表示されます。これにより、ドキュメントが保護されていることと、ファイルにアクセスできるユーザーがわかります。

この変更は、会社の機密データを、見るべきでないユーザーから保護するのに役立ちます。 モバイル デバイスを使用してこのような保護されたドキュメントにアクセスする場合、ドキュメントを閲覧することはできますが、編集するにはデスクトップ デバイスを使う必要があります。

ドキュメントで安全なコラボレーションがサポートされていない場合は、"売上の予測とレポート" サイトにドキュメントをアップロードすることはできません。

**サポートが必要な場合は、**

-   ヘルプ デスク helpdesk@vanarsdelltd.com にお問い合わせください。



<!--HONumber=Apr16_HO4-->

