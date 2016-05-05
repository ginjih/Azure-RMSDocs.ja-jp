---
# required metadata

title: 概要 | Azure RMS
description: AD RMS および Azure RMS は、デジタル情報を権限のない使用から保護するために役立つ情報保護テクノロジです。
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: a1da2517-c50f-4e02-bec7-92836bbd4007

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
# 概要


Microsoft Rights Management サービス (AD RMS および Azure RMS) は、デジタル情報を権限のない使用から保護するために役立つ情報保護テクノロジです。 コンテンツの所有者は、権限を有効にしたアプリケーションを通じて、そのコンテンツを開く、変更する、印刷する、転送する、などの操作を実行できるユーザーを定義することができます。

Microsoft Rights Management SDK 4.2 は、複数のプラットフォームで使用できる、クライアント コンピューターおよびデバイス向けに ”権限が有効になった” アプリケーションからの情報へのアクセスおよび使用を保護するために設計されている Software Developer Kit (SDK) またはフレームワークです。 これらのプラットフォーム用の SDK によって、デジタル コンテンツの保護と使用、テンプレートの取得、サーバーからのポリシーの取得、およびその他の関連する権限関連タスクの実行を行うための単純な API がアプリケーション開発者に提供されます。

現在サポートされているプラットフォームの詳細については、[Microsoft Rights Management SDK](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md) の開発者ドキュメント ポータルを参照してください。

考えられるシナリオの一部を次に示します。

-   機密情報を含む電子メール メッセージが印刷または転送されないようにすることを望む法律事務所。
-   パスワードを使用することなく、描画のアクセスを研究部門内の小規模のユーザー グループに制限することを希望する CAD/CAM ソフトウェアの開発者。
-   1 つのライセンスを使用して、イメージの低解像度のコピーは無料で表示できるが、高解像度のコピーを表示する場合は支払いを求めるようにすることを望む、グラフィック デザインのモバイル アプリ所有者。
-   ドキュメントがモバイル デバイスにダウンロードされたときに、ユーザーの ID に基づいて、ドキュメントの表示、印刷、または編集の権限を有効にすることを望むオンライン ドキュメント ライブラリの所有者。
-   表示と編集の権限を特定のユーザーに制限する社内の Web サイトに従業員の機密情報を公開することを望む企業。

MS RMS SDK 4.2 は、使用許諾契約書を確認して承諾することでダウンロードできるようになり、サードパーティ製ソフトウェアと一緒に自由に配布できるため、クライアントは環境内の AD RMS サーバーを使用してデプロイすることで、権利保護されたコンテンツにアクセスできるようになります。 詳細については、「[作業開始](get-started.md)」を参照してください。

## SDK の概要


MS RMS SDK 4.2 には、次のような便利な新機能があります。

-   **再設計された API** – MS RMS SDK 4.2 API は可能な限りわかりやすくなるように再設計されているため、開発者は最低限の労力で API のシンプルかつ透過的な暗号化および暗号化解除を利用できます。
-   **AD RMS および Azure RMS のハイブリッド サポート** – 1 つの RMS 対応アプリで、AD RMS サーバー (AD RMS のモバイル デバイス拡張機能を使用) と Azure RMS サービスの両方からのコンテンツを使用および保護できます。 MS RMS SDK 4.2 は、IT 管理者が構成できる関連エンドポイントを透過的に検出します。
-   **独自の認証ライブラリの使用** – ユーザーは、アプリ開発者として MS RMS SDK 4.2 で使用する認証ライブラリを選択できます。 MS RMS SDK 4.2 によって、認証ライブラリが [Azure AD 認証ライブラリ](https://msdn.microsoft.com/en-us/library/jj573266.aspx)かユーザーの組織のカスタム ライブラリかによって認証スタックが分離されるため、ユーザーはニーズに最も適したライブラリを選択することができます。
-   **独自のユーザー インターフェイスの使用** - MS RMS SDK 4.2 では、カスタマイズしたユーザー インターフェイスを実装できるようになりました。 保護されたコンテンツを使用しているときのコンテンツの保護およびテンプレートの選択からアクセス許可の変更まで、MS RMS SDK 4.2 によってアプリの組み込み UI を強制されることはありません。 ただし、希望する場合は、 [GitHub アカウント](https://github.com/AzureAD/)からすべてのプラットフォームに対して Microsoft RMS の UI ライブラリを使用できます。
-   **保護されたコンテンツへのオフライン アクセス** – MS RMS SDK 4.2 は、インターネット接続がない場合でも、保護されているコンテンツへのアクセスをユーザーに許可します。 MS RMS SDK 4.2 では保護されているコンテンツの使用ポリシーが安全にキャッシュされるため、ユーザーは RMS で保護されたデータにオフラインでアクセスできます。

[作業開始](get-started.md)ガイドを使用して、保護されている情報のデバイス アプリ プロジェクトを開始してください。

## 関連項目

* [Microsoft Rights Management SDK](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md)
* [作業開始](get-started.md)
* [Azure AD 認証ライブラリ](https://msdn.microsoft.com/en-us/library/jj573266.aspx)
* [GitHub アカウント](https://github.com/AzureAD/)
 

 





<!--HONumber=Apr16_HO3-->

