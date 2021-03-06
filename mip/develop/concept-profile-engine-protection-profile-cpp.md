---
title: 概念 - 保護 API プロファイル オブジェクト
description: この記事は、アプリケーションの初期化中に作成される、保護プロファイル オブジェクトの概念を理解するのに役立ちます。
author: msmbaldwin
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: mbaldwin
ms.openlocfilehash: 7d6dded96c3d87cdbf925f85c675c10a68f182fb
ms.sourcegitcommit: f54920bf017902616589aca30baf6b64216b6913
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/22/2020
ms.locfileid: "81764034"
---
# <a name="microsoft-information-protection-sdk---protection-api-profile-concepts"></a>Microsoft Information Protection SDK - 保護 API プロファイルの概念

次の 2 つの例では、状態ストレージに対するローカル ストレージ、およびメモリ内のみを使用する profileSettings オブジェクト作成する方法を示します。 

## <a name="load-a-profile"></a>プロファイルの読み込み

`ProtectionProfileObserverImpl`が定義されたので、それを使用し`mip::ProtectionProfile`てインスタンス化します。 オブジェクトを`mip::ProtectionProfile`作成する[`mip::ProtectionProfile::Settings`](reference/class_mip_ProtectionProfile_settings.md)には、が必要です。

### <a name="protectionprofilesettings-parameters"></a>ProtectionProfile::Settings Parameters

- `std::shared_ptr<MipContext>`: アプリケーション`mip::MipContext`情報や状態パスなどを格納するために初期化されたオブジェクト。
- `mip::CacheStorageType`: 状態をメモリ内、ディスク上、またはディスク上に格納し、暗号化する方法を定義します。
- `std::shared_ptr<mip::ConsentDelegate>`: クラス[`mip::ConsentDelegate`](reference/class_mip_consentdelegate.md)の共有ポインター。
- `std::shared_ptr<mip::ProtectionProfile::Observer> observer`: プロファイル`Observer`の実装への共有ポインター ( [`PolicyProfile`](reference/class_mip_policyprofile_observer.md)、 [`ProtectionProfile`](reference/class_mip_protectionprofile_observer.md)、および[`FileProfile`](reference/class_mip_fileprofile_observer.md))。

次の 2 つの例では、状態ストレージに対するローカル ストレージ、およびメモリ内のみを使用する profileSettings オブジェクト作成する方法を示します。 

#### <a name="store-state-in-memory-only"></a>メモリ内の状態のみを格納

```cpp
mip::ApplicationInfo appInfo {clientId, "APP NAME", "1.2.3" };

mMipContext = mip::MipContext::Create(appInfo,
                "mip_app_data",
                mip::LogLevel::Trace,
                nullptr /*loggerDelegateOverride*/,
                nullptr /*telemetryOverride*/);

ProtectionProfile::Settings profileSettings(
    mipContext,                                        // mipContext object
    mip::CacheStorageType::InMemory,                   // use in memory storage    
    std::make_shared<ConsentDelegateImpl>(),           // new consent delegate
    std::make_shared<ProtectionProfileObserverImpl>()); // new protection profile observer
```

#### <a name="readwrite-profile-settings-from-storage-path-on-disk"></a>ディスク上のストレージ パスからのプロファイル設定の読み取り/書き込み

```cpp
mip::ApplicationInfo appInfo {clientId, "APP NAME", "1.2.3" };

mMipContext = mip::MipContext::Create(appInfo,
                "mip_app_data",
                mip::LogLevel::Trace,
                nullptr /*loggerDelegateOverride*/,
                nullptr /*telemetryOverride*/);

ProtectionProfile::Settings profileSettings(
    mipContext,                                         // mipContext object
    mip::CacheStorageType::OnDisk,                      // use on disk storage    
    std::make_shared<ConsentDelegateImpl>(),            // new consent delegate
    std::make_shared<ProtectionProfileObserverImpl>()); // new protection profile
```

次に、promise/future パターンを使用して `ProtectionProfile` を読み込みます。

```cpp
auto profilePromise = std::make_shared<std::promise<std::shared_ptr<ProtectionProfile>>>();
auto profileFuture = profilePromise->get_future();
ProtectionProfile::LoadAsync(profileSettings, profilePromise);
```

プロファイルを読み込み、その操作が成功した場合、`mip::ProtectionProfile::Observer::OnLoadSuccess` の実装の `ProtectionProfileObserverImpl::OnLoadSuccess` が呼び出されます。 結果のオブジェクトまたは例外のポインターやコンテキストが、関数にパラメーターとして渡されます。 このコンテキストは、非同期操作を処理するために作成した `std::promise` へのポインターです。 この関数は、単純に約束の値を ProtectionProfile オブジェクト (コンテキスト) に設定します。 メイン関数で `Future.get()` を使用する場合、結果は新しいオブジェクトに格納できます。

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

    ProtectionProfile::Settings profileSettings(
        mipContext,                                    // mipContext object
        mip::CacheStorageType::OnDisk,                 // use on disk storage        
        std::make_shared<ConsentDelegateImpl>(),       // new consent delegate
        std::make_shared<ProfileObserver>());          // new protection profile observer

    auto profilePromise = std::make_shared<promise<shared_ptr<ProtectionProfile>>>();
    auto profileFuture = profilePromise->get_future();
    ProtectionProfile::LoadAsync(profileSettings, profilePromise);
    auto profile = profileFuture.get();
}
```

最終結果は、プロファイルの読み込みが成功し、それが `profile` と呼ばれるオブジェクトに格納されます。

## <a name="next-steps"></a>次の手順

これでプロファイルが追加されました。次の手順では、エンジンをプロファイルに追加します。

[保護エンジンの概念](concept-profile-engine-protection-engine-cpp.md)
