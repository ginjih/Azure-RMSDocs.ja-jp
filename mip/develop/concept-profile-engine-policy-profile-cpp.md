---
title: 概念 - ポリシー API プロファイル オブジェクト
description: この記事は、アプリケーションの初期化中に作成される、ポリシー プロファイル オブジェクトに関する概念を理解するのに役立ちます。
author: msmbaldwin
ms.service: information-protection
ms.topic: conceptual
ms.date: 07/30/2019
ms.author: mbaldwin
ms.openlocfilehash: bdc72bc3da8added696733cb271116764d0fd0c7
ms.sourcegitcommit: f54920bf017902616589aca30baf6b64216b6913
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/22/2020
ms.locfileid: "81764055"
---
# <a name="microsoft-information-protection-sdk---policy-api-profile-concepts"></a>Microsoft Information Protection SDK - ポリシー API プロファイルの概念

ポリシー API の操作を実行する前に、`mip::Profile` を読み込む必要があります。

次の 2 つの例では、状態ストレージに対するローカル ストレージ、およびメモリ内のみを使用する profileSettings オブジェクト作成する方法を示します。 

## <a name="load-a-profile"></a>プロファイルの読み込み

これで `MipContext` と `ProfileObserver` を定義したので、それらを使用して `mip::PolicyProfile` をインスタンス化します。 オブジェクトを`mip::PolicyProfile`作成する[`mip::PolicyProfile::Settings`](reference/class_mip_PolicyProfile_settings.md)に`mip::MipContext`は、とが必要です。

### <a name="profilesettings-parameters"></a>Profile::Settings パラメーター

コンストラクター `PolicyProfile::Settings`は、次に示す4つのパラメーターを受け取ります。

- `const std::shared_ptr<MipContext>`: アプリケーション`mip::MipContext`情報や状態パスなどを格納するために初期化されたオブジェクト。
- `mip::CacheStorageType`: 状態をメモリ内、ディスク上、またはディスク上に格納し、暗号化する方法を定義します。 詳細については、「[キャッシュストレージの概念](concept-cache-storage.md)」を参照してください。
- `std::shared_ptr<mip::PolicyProfile::Observer> observer`: プロファイル`Observer`の実装への共有ポインター ( [`PolicyProfile`](reference/class_mip_policyprofile_observer.md)、 [`ProtectionProfile`](reference/class_mip_protectionprofile_observer.md)、および[`FileProfile`](reference/class_mip_fileprofile_observer.md))。

次の 2 つの例では、状態ストレージに対するローカル ストレージ、およびメモリ内のみを使用する profileSettings オブジェクト作成する方法を示します。 

#### <a name="store-state-in-memory-only"></a>メモリ内の状態のみを格納

```cpp
mip::ApplicationInfo appInfo {clientId, "APP NAME", "1.2.3" };

mMipContext = mip::MipContext::Create(appInfo,
                "mip_app_data",
                mip::LogLevel::Trace,
                nullptr /*loggerDelegateOverride*/,
                nullptr /*telemetryOverride*/);

PolicyProfile::Settings profileSettings(
    mipContext,                                   // mipContext object
    mip::CacheStorageType::InMemory,              // use in memory storage
    std::make_shared<PolicyProfileObserverImpl>()); // new protection profile observer
```

#### <a name="readwrite-profile-settings-from-storage-path-on-disk"></a>ディスク上のストレージ パスからのプロファイル設定の読み取り/書き込み

```cpp
mip::ApplicationInfo appInfo {clientId, "APP NAME", "1.2.3" };

mMipContext = mip::MipContext::Create(appInfo,
                "mip_app_data",
                mip::LogLevel::Trace,
                nullptr /*loggerDelegateOverride*/,
                nullptr /*telemetryOverride*/);

PolicyProfile::Settings profileSettings(
    mipContext,                                    // mipContext object
    mip::CacheStorageType::OnDisk,                 // use on disk storage
    std::make_shared<PolicyProfileObserverImpl>());  // new protection profile observer
```

次に、promise/future パターンを使用して `Profile` を読み込みます。

```cpp
auto profilePromise = std::make_shared<std::promise<std::shared_ptr<Profile>>>();
auto profileFuture = profilePromise->get_future();
Profile::LoadAsync(profileSettings, profilePromise);
```

プロファイルが正常に読み込まれたら、`mip::Profile::Observer::OnLoadSuccess` の実装である `ProfileObserver::OnLoadSuccess` が通知されます。 この場合は `mip::Profile` である、結果のオブジェクトおよびコンテキストは、オブザーバー関数にパラメーターとして渡されます。

この*コンテキスト*は、非同期操作を処理するために作成した `std::promise` へのポインターです。 この関数は、最初のパラメーター用に渡した Profile オブジェクトに Promise の値を単純に設定します。 メイン関数で `Future.get()` を使用する場合、結果は呼び出しスレッドの新しいオブジェクトに格納できます。

```cpp
//get the future value and store in profile.
auto profile = profileFuture.get();
```

### <a name="putting-it-together"></a>まとめ

オブザーバーおよび認証委任を完全に実装したので、プロファイルを完全に読み込めるようになりました。 以下のコードの切り取りでは、すべての必要なハンドラーが既に含まれていると想定しています。

```cpp
int main()
{
    const string userName = "MyTestUser@consoto.com";
    const string password = "P@ssw0rd!";
    const string clientId = "MyClientId";

    mip::ApplicationInfo appInfo {clientId, "APP NAME", "1.2.3" };
 
    auto mipContext = mip::MipContext::Create(appInfo,
                        "mip_app_data",
                        mip::LogLevel::Trace,
                        nullptr /*loggerDelegateOverride*/,
                        nullptr /*telemetryOverride*/);

    PolicyProfile::Settings profileSettings(
        mipContext,                                    // mipContext object
        mip::CacheStorageType::OnDisk,                 // use on disk storage
        std::make_shared<PolicyProfileObserverImpl>());  // new protection profile observer

    auto profilePromise = std::make_shared<promise<shared_ptr<PolicyProfile>>>();
    auto profileFuture = profilePromise->get_future();
    Profile::LoadAsync(profileSettings, profilePromise);
    auto profile = profileFuture.get();
}
```

最終結果は、プロファイルの読み込みが成功し、それが `profile` と呼ばれるオブジェクトに格納されます。

## <a name="next-steps"></a>次の手順

これでプロファイルが追加されました。次の手順では、エンジンをプロファイルに追加します。

[ポリシー エンジンの概念](concept-profile-engine-policy-engine-cpp.md)
