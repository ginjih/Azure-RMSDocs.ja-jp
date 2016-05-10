---
# required metadata

title: シナリオ – 社外秘の電子メールを送信する | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 950799e9-2289-48c7-b95a-f54a8ead520a

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# シナリオ – 社外秘の電子メールを送信する
このシナリオおよびサポート ユーザー ドキュメントでは、Azure Rights Management を使用して、組織内の各ユーザーが、組織の部外者が読み取ることのできない安全な方法で電子メールによる通信を送信できるようにします。 たとえば、別の組織の誰かまたは個人用の電子メール アカウントに電子メール メッセージを転送するとします。 電子メールと添付ファイルは、Azure Rights Management とユーザーが電子メール クライアントから選択するテンプレートによって保護されます。

このシナリオを実現する最も簡単な方法は、組み込まれている既定のテンプレートを使用して、組織内のすべてのユーザーへのアクセスを自動的に制限することですが、 必要に応じて、ユーザーのサブセットに対するアクセスを制限するなどのカスタム テンプレートを作成したり、その他の制限 (読み取り専用や有効期限など) を設定したり、電子メール クライアントの [進む] ボタンを無効にしたりすることで、制限を強化することができます。

> [!IMPORTANT]
> このシナリオでは、構成するカスタム テンプレートから**転送**権限を削除し、電子メール クライアントの [進む] ボタンを無効にすることができますが、この構成ではユーザーが権限のある他のユーザーと共有することは妨げられません。 受信者は、電子メール (および添付ファイル) を保存し、他の共有メカニズムを使用してその情報を共有することが可能です。
> 
> たとえば、Bob は、Marketing グループにファイルの保存とコンテンツの編集のカスタム権限を適用し、転送権限を含めないカスタム テンプレートを使用して、Alice に電子メールを送信します。 Alice は他のユーザーに電子メールを転送できませんが、電子メール メッセージと添付ファイルを USB ドライブまたはファイル サーバー共有に保存できます。これらのファイルへのアクセス権がある Marketing グループのメンバーは、ファイルを読み取り、編集することができます。 Marketing グループ以外のユーザーは、コンテンツを開くことができません。

この手順は、次の一連の状況に適してします。

-   組織内では各ユーザーが他のユーザーと情報を共有できるようにし、組織外のユーザーとは情報を共有できないようにする必要がある。

-   共有する情報を電子メール メッセージまたは添付ファイルに含めることができる。

-   ユーザーは電子メール クライアントからテンプレートを手動で選択する必要がある。

## デプロイの手順
![](../media/AzRMS_AdminBanner.png)

ユーザー ドキュメントを参照する前に、次の要件を満たしていることを確認してください。

## このシナリオの要件
このシナリオの手順を実行するには、次の要件を満たしている必要があります。

|要件|詳細情報が必要な場合|
|---------------|--------------------------------|
|Office 365 または Azure Active Directory のアカウントとグループを準備した|[Azure Rights Management の準備を行う](https://technet.microsoft.com/library/jj585029.aspx)|
|Azure Rights Management テナント キーは、マイクロソフトによって管理されています。BYOK は使用しません|[Azure Rights Management テナント キーを計画して実装する](https://technet.microsoft.com/library/dn440580.aspx)|
|Rights Management がアクティブ化されている|[Rights Management をアクティブにする](https://technet.microsoft.com/library/jj658941.aspx)|
|次のいずれかです。<br /><br />Azure Rights Management の Exchange Online が有効になっている<br /><br />RMS コネクタがインストールされ、Exchange On-Premises に構成されている|Exchange Online の場合: 「[Azure Rights Management 用にアプリケーションを構成する](https://technet.microsoft.com/library/jj585031.aspx)」トピックの「**Exchange Online: IRM 構成**」セクションを参照してください。<br /><br />Exchange On-Premises の場合: 「[Azure Rights Management コネクタをデプロイする](https://technet.microsoft.com/library/dn375964.aspx)」|
|既定の Azure Rights Management テンプレート **&lt; 組織 &gt; - 社外秘** をアーカイブしていない。 または、より厳しい制限を設定する、あるいは組織内のユーザーのサブセットのみが保護された電子メールを読み取ることができるようにする必要があるため、この目的でカスタム テンプレートを構成した。|[Azure Rights Management のカスタム テンプレートを構成する](https://technet.microsoft.com/library/dn642472.aspx)<br /><br />ヒント: より制限の厳しい使用ポリシーを組織内のすべてのユーザーに対して設定する必要がある場合、最初から新しいテンプレートを作成するのではなく、既定のテンプレートをコピーして編集します。<br /><br />このシナリオの電子メール クライアントでは、更新されたテンプレートはすぐには最新の情報に更新されません。 詳細については、構成テンプレートに関する記事「Azure Rights Management のカスタム テンプレートを構成する」の「 [ユーザー用のテンプレートの更新](https://technet.microsoft.com/library/dn642472.aspx) 」を参照してください。|
|保護された電子メールを送信するユーザーが Outlook 2013、Outlook 2016、または Outlook Web Access を持っている。<br /><br />電子メールを受信するユーザーが Azure Rights Management をサポートする電子メール クライアントを持っている。|Outlook 2010 を使用できますが、[Windows 用の Rights Management 共有アプリケーションをインストール](https://technet.microsoft.com/library/dn339003.aspx) し、それに従ってユーザーの手順を調整する必要があります。<br /><br />Azure Rights Management をサポートする電子メールの一覧については、「[Azure Rights Management の要件](https://technet.microsoft.com/library/dn655136.aspx)」の 「[クライアント デバイスの機能](https://technet.microsoft.com/library/dn655136.aspx)」の表の「**電子メール**」列を参照してください。|

## ユーザー ドキュメントの手順
次のテンプレートを使用して、ユーザーの手順をコピーしてエンド ユーザーの通信欄に貼り付け、環境に合わせて次の変更を行います。

1.  *&lt;組織名&gt;* のすべてのインスタンスを組織の名前に置き換えます。

2.  *&lt;組織名 - 社外秘&gt;* のすべてのインスタンスを既定のテンプレートまたはカスタム テンプレートの名前に置き換えます。

3.  組織のテンプレート名が表示されるように、スクリーン ショットを置き換えます。

4.  *&lt;連絡先の詳細&gt;* を、Web サイト リンク、電子メール アドレス、電話番号など、ユーザーがヘルプ デスクに連絡を取るための方法を示す手順に置き換えます。

5.  **その他の推奨の変更:**

    -   1 つの電子メール クライアントのみに手順を制限することが現実的な場合は、わかりやすくするためこれを行うことを検討し、その他の一連の手順を削除します。

    -   推奨される既定のテンプレートではなく、カスタム テンプレートを使用する場合は、それに応じて内容を変更します。

        -   具体的なタイトルを付けます。

        -   手順 1. で選択するユーザーまたはグループを指定します。

        -   手順 2. でカスタム テンプレートの名前を指定します。

        -   受信者に対する制限を説明する最後の段落を変更します。

6.  必要に応じて手順に変更を加え、変更した手順をユーザーに送信します。

7.  一部のクライアントは Rights Management をサポートしないため、場合によっては、保護された電子メール メッセージの受信者にガイダンスと推奨事項を示す必要があります。 この情報は、組織で使用しているデバイスと電子メール アプリケーション、およびユーザーの基本設定に応じて異なります。 たとえば、iOS ユーザーには、保護された電子メールを読む場合にはネイティブ iOS メール クライアントではなく、iPad および iPhone 用 Outlook を使用することを推奨します。

    電子メール クライアントの詳細については、「[Azure Rights Management の要件](https://technet.microsoft.com/library/dn655136.aspx)」の 「[クライアント デバイスの機能](https://technet.microsoft.com/library/dn655136.aspx)」の表の「**電子メール**」列を参照してください。

ドキュメントの例では、カスタマイズ後、これらの手順がユーザーにどのように表示されるかを示します。

![](../media/AzRMS_UsersBanner.png)

### Outlook を使用して社外秘情報を含む電子メールを送信する方法

1.  Outlook で新しい電子メール メッセージを作成し、必要な添付ファイルを追加し、*&lt; 組織名&gt;* からユーザーまたはグループを選択します。

2.  **[オプション]** タブの **[アクセス許可]** をクリックし、**[&lt;組織名 - 社外秘&gt;]** を選択します。

    ![](../media/AzRMS_OutlookTemplate.PNG)

3.  メッセージを送信します。

### Outlook Web アプリを使用して社外秘情報を含む電子メールを送信する方法

1.  Outlook Web アプリで新しい電子メール メッセージを作成し、必要な添付ファイルを追加し、アドレス帳から *&lt; 組織名&gt;* ユーザーまたはグループを選択します。

2.  **[…]** をクリックし、**[アクセス権の設定]** をクリックし、**[&lt;組織名 - 社外秘&gt;]** を選択します。

    ![](../media/AzRMS_OWATemplate.png)

3.  メッセージを送信します。

**[宛先]**、**[CC]**、または **[BCC]** 行上のだれかがこの電子メールを受け取ると、受信者は、メッセージを読む取ることができるようになる前に、*&lt;組織名&gt;* のユーザーであることを確認する認証を要求される場合があります。 それ以外の場合には、ユーザーは既に認証されているため、認証を求められることはありません。

ユーザーは受信した電子メールを他のユーザーに転送できますが、転送された電子メールを読むことができるのは *&lt;組織名&gt;* のユーザーのみです。 Office ドキュメントを添付した場合、その添付ファイルを別の場所に別の名前で保存しても、同様に保護されます。 ただし、正常に認証されたユーザーは、その電子メールまたは添付ファイルの内容をコピーして貼り付けたり、印刷したりすることができます。 このような操作を防止し、より制限の厳しい保護を必要とする場合は、ヘルプ デスクに問い合わせてください。

**サポートが必要な場合は、**

-   ヘルプ デスクに問い合わせる

    -   *&lt;連絡先の詳細&gt;*

### カスタマイズされたユーザー ドキュメントの例
![](../media/AzRMS_ExampleBanner.png)

#### Outlook を使用して社外秘情報を含む電子メールを送信する方法

1.  Outlook で新しい電子メール メッセージを作成し、必要な添付ファイルを追加し、アドレス帳から VanArsdel ユーザーまたはグループを選択します。

2.  **[オプション]** タブの **[アクセス許可]** をクリックし、**[VanArsdel, Ltd - 社外秘]** を選択します。

    ![](../media/AzRMS_OutlookTemplate.PNG)

3.  メッセージを送信します。

#### Outlook Web アプリを使用して社外秘情報を含む電子メールを送信する方法

1.  Outlook Web アプリで新しい電子メール メッセージを作成し、必要な添付ファイルを追加し、アドレス帳から VanArsdel ユーザーまたはグループを選択します。

2.  **[…]** をクリックし、**[アクセス権の設定]** をクリックし、**[VanArsdel, Ltd - 社外秘]** を選択します。

    ![](../media/AzRMS_OWATemplate.png)

3.  メッセージを送信します。

**[宛先]**、**[CC]**、または **[BCC]** 行上のだれかがこの電子メールを受け取ると、受信者は、メッセージを読む取ることができるようになる前に、VanArsdel, Ltd のユーザーであることを確認する認証を要求される場合があります。 それ以外の場合には、ユーザーは既に認証されているため、認証を求められることはありません。

ユーザーは受信した電子メールを他のユーザーに転送できますが、転送された電子メールを読むことができるのは VanArsdel のユーザーのみです。 Office ドキュメントを添付した場合、その添付ファイルを別の場所に別の名前で保存しても、同様に保護されます。 ただし、正常に認証されたユーザーは、その電子メールまたは添付ファイルの内容をコピーして貼り付けたり、印刷したりすることができます。 このような操作を防止し、より制限の厳しい保護を必要とする場合は、ヘルプ デスクに問い合わせてください。

**サポートが必要な場合は、**

-   ヘルプ デスクに問い合わせる

    -   電子メール: helpdesk@vanarsdelltd.com



<!--HONumber=Apr16_HO4-->

