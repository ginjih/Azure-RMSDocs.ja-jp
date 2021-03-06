---
title: 概念 - ファイル API プロファイル オブジェクト
description: この記事は、アプリケーションの初期化中に作成される、ファイル プロファイル オブジェクトに関する概念を理解するのに役立ちます。
author: msmbaldwin
ms.service: information-protection
ms.topic: conceptual
ms.date: 07/30/2019
ms.author: mbaldwin
ms.openlocfilehash: c48f3f3a45e77698bda2870babaa2564968fc47e
ms.sourcegitcommit: f54920bf017902616589aca30baf6b64216b6913
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/22/2020
ms.locfileid: "81764083"
---
# <a name="microsoft-information-protection-sdk---file-api-profile-concepts"></a>Microsoft Information Protection SDK - ファイル API プロファイルの概念

プロファイルは、MIP SDK のすべての操作のルート クラスです。 ファイル API 機能のいずれかを使用する前に、`FileProfile` を作成する必要があり、今後の操作はすべて、プロファイルまたはプロファイルに*追加された*その他のオブジェクトによって実行されます。

プロファイルをインスタンス化しようとする前に、満たす必要があるいくつかのコード条件があります。

- `MipContext`が作成され、 `mip::FileProfile`オブジェクトにアクセスできるオブジェクトに格納されています。
- `ConsentDelegateImpl` は、`mip::ConsentDelegate` を実装します。
- アプリケーションが [Azure Active Directory に登録されており](/azure/active-directory/develop/quickstart-v1-integrate-apps-with-azure-ad.md)、クライアント ID がアプリケーションまたは構成ファイルにハードコードされています。
- `mip::FileProfile::Observer` を継承しているクラスは適切に実装されています。

## <a name="load-a-profile"></a>プロファイルの読み込み

`ProfileObserver`を使用すると`ConsentDelegateImpl`、が定義`mip::FileProfile`され、をインスタンス化できるようになりました。 `mip::FileProfile`オブジェクトを作成するに`mip::MipContext`は、[] [`mip::FileProfile::Settings`](reference/class_mip_fileprofile_settings.md)で、 `FileProfile`およびに関するすべての設定情報を格納する必要があります。

### <a name="fileprofilesettings-parameters"></a>FileProfile::Settings パラメーター

`FileProfile::Settings` コンストラクターでは、以下に一覧された 5 つのパラメーターを受け取ります。

- `std::shared_ptr<MipContext>`: アプリケーション`mip::MipContext`情報や状態パスなどを格納するために初期化されたオブジェクト。
- `mip::CacheStorageType`: 状態をメモリ内、ディスク上、またはディスク上に格納し、暗号化する方法を定義します。
- `std::shared_ptr<mip::ConsentDelegate>`: クラス[`mip::ConsentDelegate`](reference/class_mip_consentdelegate.md)の共有ポインター。
- `std::shared_ptr<mip::FileProfile::Observer> observer`: プロファイル`Observer`の実装への共有ポインター ( [`PolicyProfile`](reference/class_mip_policyprofile_observer.md)、 [`ProtectionProfile`](reference/class_mip_protectionprofile_observer.md)、および[`FileProfile`](reference/class_mip_fileprofile_observer.md))。

次の例では、状態ストレージに対するローカル ストレージ、およびメモリ内のみを使用する `profileSettings` オブジェクトを作成する方法を示します。 

#### <a name="store-state-in-memory-only"></a>メモリ内の状態のみを格納

```cpp
mip::ApplicationInfo appInfo {clientId, "APP NAME", "1.2.3" };

mMipContext = mip::MipContext::Create(appInfo,
                "mip_app_data",
                mip::LogLevel::Trace,
                nullptr /*loggerDelegateOverride*/,
                nullptr /*telemetryOverride*/);

FileProfile::Settings profileSettings(
    mipContext,                                   // mipContext object
    mip::CacheStorageType::InMemory,              // use in memory storage
    std::make_shared<ConsentDelegateImpl>(),      // new consent delegate
    std::make_shared<FileProfileObserverImpl>()); // new protection profile observer
```

#### <a name="readwrite-profile-settings-from-storage-path-on-disk"></a>ディスク上のストレージ パスからのプロファイル設定の読み取り/書き込み

次のコードの切り取りでは、`FileProfile` に `./mip_app_data` でアプリの状態データをすべて格納するように指示します。

```cpp
mip::ApplicationInfo appInfo {clientId, "APP NAME", "1.2.3" };

mMipContext = mip::MipContext::Create(appInfo,
                "mip_app_data",
                mip::LogLevel::Trace,
                nullptr /*loggerDelegateOverride*/,
                nullptr /*telemetryOverride*/);

FileProfile::Settings profileSettings(
    mipContext,                                    // mipContext object
    mip::CacheStorageType::OnDisk,                 // use on disk storage    
    std::make_shared<ConsentDelegateImpl>(),       // new consent delegate
    std::make_shared<FileProfileObserverImpl>());  // new protection profile observer
```

#### <a name="load-the-profile"></a>プロファイルの読み込み

上記いずれかの方法の詳細を使用して、promise/future パターンを使用して `FileProfile` を読み込みます。

```cpp
auto profilePromise = std::make_shared<std::promise<std::shared_ptr<FileProfile>>>();
auto profileFuture = profilePromise->get_future();
FileProfile::LoadAsync(profileSettings, profilePromise);
```

プロファイルを読み込み、その操作が成功した場合、`mip::FileProfile::Observer::OnLoadSuccess` の実装の `ProfileObserver::OnLoadSuccess` が呼び出されます。 結果のオブジェクトまたは例外のポインターやコンテキストが、関数にパラメーターとして渡されます。 このコンテキストは、非同期操作を処理するために作成した `std::promise` へのポインターです。 関数では最初のパラメーターに渡した FileProfile オブジェクトへの promise の値を設定するだけです。 メイン関数で `Future.get()` を使用する場合、結果は新しいオブジェクトに格納できます。

```cpp
//get the future value and store in profile. 
auto profile = profileFuture.get();
```

### <a name="putting-it-together"></a>まとめ

オブザーバーおよび認証委任を完全に実装したので、プロファイルを完全に読み込めるようになりました。 以下のコードの切り取りでは、すべての必要なハンドラーが既に含まれていると想定しています。

```cpp
int main()
{
    const string userName = "MyTestUser@contoso.com";
    const string password = "P@ssw0rd!";
    const string clientId = "MyClientId";

    mip::ApplicationInfo appInfo {clientId, "APP NAME", "1.2.3" };

    auto mipContext = mip::MipContext::Create(appInfo,
                        "mip_app_data",
                        mip::LogLevel::Trace,
                        nullptr /*loggerDelegateOverride*/,
                        nullptr /*telemetryOverride*/);

    FileProfile::Settings profileSettings(
        mipContext,                                    // mipContext object
        mip::CacheStorageType::OnDisk,                 // use on disk storage        
        std::make_shared<ConsentDelegateImpl>(),       // new consent delegate
        std::make_shared<FileProfileObserverImpl>());  // new file profile observer

        auto profilePromise = std::make_shared<promise<shared_ptr<FileProfile>>>();
        auto profileFuture = profilePromise->get_future();
        FileProfile::LoadAsync(profileSettings, profilePromise);
        auto profile = profileFuture.get();
}
```

最終結果は、プロファイルの読み込みが成功し、それが `profile` と呼ばれるオブジェクトに格納されます。

## <a name="next-steps"></a>次の手順

これでプロファイルが追加されました。次の手順では、エンジンをプロファイルに追加します。 

- [ファイル エンジンの概念](concept-profile-engine-file-engine-cpp.md)
