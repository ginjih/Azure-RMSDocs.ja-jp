---
title: アプリケーションのテスト | Azure RMS
description: アプリケーションのテストを設定する方法
keywords: ''
author: bryanla
ms.author: bryanla
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: conceptual
ms.service: information-protection
ms.assetid: E480D8D6-F070-43D1-B2B0-6921459C3437
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 323816b04f59d8a18015157052f097531b34cf03
ms.sourcegitcommit: bd2b31dd97c8ae08c28b0f5688517110a726e3a1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54071779"
---
# <a name="testing-your-application"></a>アプリケーションのテスト

ここでは、アプリケーションのテストを準備する方法を説明します。

## <a name="instructions"></a>手順

Azure RMS または Windows Server で実行される RMS サーバーのいずれかからテストすることができます。  Azure RMS でテストを開始し、RMS Server を使用してテストを行います (展開で必要な場合)。

- Azure RMS でテストする方法については、「[方法: ADAL 認証の使用](how-to-use-adal-authentication.md)」を参照してください。
- RMS サーバーでテストする方法については、「[方法: RMS サーバーをインストールし、構成する](how-to-install-and-configure-an-rms-server.md)」を参照してください。
- 開発者向けランタイムをインストールするには:

   Rights Management Service Client 2.1 がアプリケーションのテストを実行するコンピューターにインストールされている必要があります。
   - 開発コンピューター以外のコンピューターでアプリケーションをテストする場合は、[AD RMS クライアント ダウンロード ページ](https://www.microsoft.com/download/details.aspx?id=38396)からそのコンピューターに RMS クライアント 2.1 をインストールします。
   - 開発用のコンピューターには、既に Rights Management サービス SDK 2.1 がインストールされている必要があります。

   RMS SDK 2.1 のインストールについては、「[SDK のインストール](install-the-rms-sdk.md)」を参照してください。

## <a name="remarks"></a>解説

これは、包括的なガイドではありません。 RMS クライアント 2.1 の構成方法については、「[RMS クライアント 2.1 のデプロイに関する注意事項](https://technet.microsoft.com/library/jj159267(WS.10).aspx)」を参照してください。

## <a name="related-topics"></a>関連項目

* [RMS サーバーをインストールして構成する方法](how-to-install-and-configure-an-rms-server.md)
* [方法: ADAL 認証の使用](how-to-use-adal-authentication.md)
* [SDK のインストール](install-the-rms-sdk.md)
* [RMS クライアント 2.1 のデプロイに関する注意事項](https://technet.microsoft.com/library/jj159267(WS.10).aspx)

