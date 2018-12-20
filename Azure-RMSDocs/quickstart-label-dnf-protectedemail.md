---
title: クイック スタート - ラベルを構成して、ユーザーが機密情報を含む電子メールを簡単に保護できるようにする - AIP
description: 転送不可の保護を自動的に適用することで、ユーザーの電子メールを保護するラベルを構成します。
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/14/2018
ms.topic: quickstart
ms.service: information-protection
ms.openlocfilehash: 217fbdc45967b5677f554410bca2ac1da58552d2
ms.sourcegitcommit: d06594550e7ff94b4098a2aa379ef2b19bc6123d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/07/2018
ms.locfileid: "53023500"
---
# <a name="quickstart-configure-a-label-for-users-to-easily-protect-emails-that-contain-sensitive-information"></a>クイック スタート: ラベルを構成して、ユーザーが機密情報を含む電子メールを簡単に保護できるようにする

このクイック スタートでは、転送不可の保護設定を自動的に適用するように既存のラベルを構成します。

現在の Azure Information Protection ポリシーには、この構成を持つ次の 2 つのラベルが既に含まれています。

- **社外秘 \ 受信者のみ**

- **非常に機密性の高い社外秘 \ 受信者のみ**

ただし、ポリシーが古い場合や、組織のポリシーの作成時に保護がアクティブ化されなかった場合、これらのラベルは含まれません。 

この構成は 5 分で完了します。

## <a name="prerequisites"></a>必要条件

このクイック スタートを完了するには、次の要件があります。

1. Azure Information Protection プラン 1 またはプラン 2 を含むサブスクリプション。
    
    このようないずれかのサブスクリプションがない場合は、組織用の[無料](https://portal.office.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7)アカウントを作成できます。

2. Azure portal に [Azure Information Protection] ブレードを追加し、保護サービスがアクティブになっていることを確認した。

    これらのアクションに関するヘルプが必要な場合は、「[クイック スタート: Azure portal で作業を開始する](quickstart-viewpolicy.md)」をご覧ください。

3. 構成する既存の Azure Information Protection ラベル。 
    
    既定のいずれかのラベルまたは作成済みのラベルを使用できます。 新しいラベルの作成に関するヘルプが必要な場合は、「[クイック スタート: 特定のユーザー向けの新しい Azure Information Protection ラベルを作成する](quickstart-label-specificusers.md)」をご覧ください。

4. 新しいラベルをテストする場合: ユーザーのコンピューターに Azure Information Protection クライアントをインストールする必要があります。 
    
    ラベルをご自分で試してみるには、[Microsoft ダウンロード センター](https://www.microsoft.com/en-us/download/details.aspx?id=53018)に移動し、Azure Information Protection ページから **AzInfoProtection.exe** をダウンロードしてクライアントをインストールできます。

5. 新しいラベルをテストする場合: Windows (Windows 7 Service Pack 1 以降) を搭載しているコンピューター。また、このコンピューターで、次のいずれかのカテゴリから Office アプリにサインインしている必要があります。
    
    - Office 365 と Office 2016 アプリ (バージョン 1805、ビルド 9330.2078 以降)。 このオプションを使用するには、Azure Rights Management のライセンスがアカウントに割り当てられている必要があります。 このライセンスは、Azure Information Protection サブスクリプションに含まれています。
    
    - Office 365 ProPlus と 2016 アプリまたは 2013 アプリ (クリック実行または Windows インストーラー ベースのインストール)。
    
    - Office Professional Plus 2016。
    
    - Office Professional Plus 2013 Service Pack 1。
    
    - Office Professional Plus 2010 Service Pack 2。

Azure Information Protection を使用するための必要条件の完全な一覧については、「[Azure Information Protection の要件](requirements.md)」をご覧ください。

## <a name="configure-an-existing-label-to-apply-the-do-not-forward-protection"></a>転送不可の保護を適用するように既存のラベルを構成する

1. 新しいブラウザー ウィンドウを開き、全体管理者として [Azure portal](https://portal.azure.com) にサインインします。次に、**[Azure Information Protection]** に移動します。 
    
    たとえば、ハブ メニューで **[すべてのサービス]** をクリックし、[フィルター] ボックスに「**Information**」と入力します。 "**Azure Information Protection**" を選択します。
    
    グローバル管理者でない場合は、別のロールのためにリンク「[Azure Portal にサインインする](configure-policy.md#signing-in-to-the-azure-portal)」を使用します。

2. **[分類]** > **[ラベル]** メニュー オプションから: **[Azure Information Protection - ラベル]** ブレードで、保護を適用するように構成するラベルを選択します。 

3. **[ラベル]** ブレードで、**[Set permissions for documents and emails containing this label]** (このラベルを含むドキュメントと電子メールにアクセス許可を設定する) を見つけます。 **[保護]** を選択し、**[保護]** を選択します。
    
    ![Azure Information Protection ラベルの保護を構成する](./media/info-protect-protection-bar-configured.png)。

4. **[保護]** ブレードで、**[Azure (cloud key)]\(Azure (クラウド キー)\)** が選択されていることを確認します。
    
5. **[ユーザー定義のアクセス許可の設定 (プレビュー)]** を選択します。

6. **[Outlook で [転送不可] を適用する]** オプションが選択されていることを確認します。

7. 選択されている場合は、**[Word、Excel、PowerPoint、エクスプローラーでは、カスタム アクセス許可を指定するようユーザーに促す]** オプションをオフにします。

8. **[保護]** ブレードで **[OK]** をクリックしてから、**[ラベル]** ブレードで **[保存]** をクリックします。

これで、Outlook でのみ表示し、転送不可の保護を電子メールに適用するようにラベルが構成されました。

## <a name="test-your-new-label"></a>新しいラベルをテストする

[Office 365 Message Encryption の新機能](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e)向けに Exchange Online が構成されている場合、構成済みのラベルは Outlook でのみ表示され、組織外の受信者に送信される電子メールに適しています。

1. コンピューターで Outlook を開き、新しい電子メール メッセージを作成します。 Outlook が既に開いている場合は再起動して、ポリシーの更新を適用します。

2. 受信者、電子メール メッセージのテキストを指定し、作成したラベルを適用します。 
    
    電子メール メッセージはラベル名に従って分類され、転送不可の制限を使用して保護されます。

3. 電子メールを送信します。 

その結果、受信者はメールの転送、印刷、メールからのコピー、添付ファイルの保存を行ったり、メールを別の名前で保存したりすることはできません。 任意のユーザーが任意のデバイスで、保護された電子メール メッセージを読むことができます。

## <a name="clean-up-resources"></a>リソースをクリーンアップする

この構成を保持しない場合や、保護を適用しないようなラベルを返さない場合は、次の手順を実行します。

1. **[分類]** > **[ラベル]** メニュー オプションから: **[Azure Information Protection - ラベル]** ブレードで、構成済みのラベルを選択します。 

3. **[ラベル]** ブレードで、**[このラベルを含むドキュメントやメールに対するアクセス許可の設定]** を見つけ、**[未構成]** を選択して **[保存]** を選択します。

## <a name="next-steps"></a>次の手順

このクイック スタートには、ラベルをすばやく構成するための最低限のオプションが含まれています。ラベルを使用すると、ユーザーは電子メールを簡単に保護できます。 ただし、構成の制限が厳しすぎる場合や、制限が不十分な場合は、以下に示す他の構成例をご覧ください。

- [[転送不可] よりも制限の緩いアクセス許可をサポートする保護された電子メールのラベル](configure-policy-protection.md#example-4-label-for-protected-email-that-supports-less-restrictive-permissions-than-do-not-forward)

- [コンテンツを暗号化するが、アクセスできるユーザーは制限しないラベル](configure-policy-protection.md#example-5-label-that-encrypts-content-but-doesnt-restrict-who-can-access-it)

保護を適用するラベルを構成するための詳しい手順については、「[Rights Management による保護でラベルを構成する方法](configure-policy-protection.md)」をご覧ください。 