---
title: 'クラス ProtectionProfile:: Settings'
description: 'Microsoft Information Protection (MIP) SDK の protectionprofile:: settings クラスを文書にします。'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 04/16/2020
ms.openlocfilehash: f0b9ef139762621205f69d46094a6729f3ec19d9
ms.sourcegitcommit: f54920bf017902616589aca30baf6b64216b6913
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/22/2020
ms.locfileid: "81763889"
---
# <a name="class-protectionprofilesettings"></a>クラス ProtectionProfile:: Settings 
作成時および有効期間全体にわたって ProtectionProfile によって使用される設定。
  
## <a name="summary"></a>まとめ
 メンバー                        | 説明                                
--------------------------------|---------------------------------------------
パブリック設定 (const std:: shared_ptr\<mipContext\>& MipContext、cacheStorageType cachestoragetype、const std:: shared_ptr\<conのデリゲート\>& con delegate、const Std:: shared_ptr\<protectionprofile:: observer\>& オブザーバー)  |  非同期操作に使用されるオブザーバーを指定する ProtectionProfile::Settings コンストラクター。
パブリック設定 (const std:: shared_ptr\<mipContext\>& MipContext、cachestoragetype cachestoragetype、const std:: shared_ptr\<con delegate\>& conのデリゲート)  |  同期操作に使用される、ProtectionProfile::Settings コンストラクター。
パブリック CacheStorageType GetCacheStorageType () const  |  キャッシュをメモリまたはディスクのどちらに格納するかを取得します。
public std:: shared_ptr\<con、delegate\> getconの delegate () const  |  サービスに接続するために使用する同意委任を取得します。
public std:: shared_ptr\<protectionprofile:: Observer\> GetObserver () const  |  ProtectionProfile に関連するイベントの通知を受信するオブザーバーを取得します。
public std:: shared_ptr\<MipContext\> GetMipContext () const  |  すべてのプロファイルで共有状態を表す mipmap コンテキストを取得します。
public std:: shared_ptr\<httpdelegate\> GetHttpDelegate () const  |  アプリケーションによって提供される HTTP 委任が取得されます (提供される場合)。
public void SetHttpDelegate (const std:: shared_ptr\<httpdelegate\>& httpdelegate)  |  クライアント自体のスタックで既定の HTTP スタックをオーバーライドします。
public std:: shared_ptr\<TaskDispatcherDelegate\> GetTaskDispatcherDelegate () const  |  アプリケーションによって提供される TaskDispatcher デリゲート (存在する場合) を取得します。
public void SetTaskDispatcherDelegate (const std:: shared_ptr\<taskDispatcherDelegate\>& TaskDispatcherDelegate)  |  クライアント独自のを使用して、既定の asynchonous タスクのディスパッチ処理をオーバーライドします。
public void SetSessionId(const std::string& sessionId)  |  セッション ID を設定します。
public const std::string& GetSessionId() const  |  セッション ID を取得します。
public void SetCanCacheLicenses (bool canCacheLicenses)  |  エンドユーザーライセンス (Eul) がローカルにキャッシュされるかどうかを構成します。
public bool CanCacheLicenses () const  |  エンドユーザーライセンス (Eul) がローカルにキャッシュされているかどうかを取得します。
public void setcustomsettings (const std:: vector\<std::p air\<std:: string, std:: string\> \>& customsettings)  |  機能のゲーティングとテストに使用するカスタム設定を設定します。
public const std:: vector\<std::p air\<std:: string、std:: string\> \>& GetCustomSettings () const  |  機能のゲーティングとテストに使用するカスタム設定を取得します。
  
## <a name="members"></a>メンバー
  
### <a name="settings-function"></a>Settings 関数
非同期操作に使用されるオブザーバーを指定する ProtectionProfile::Settings コンストラクター。

パラメーター:  
* **mipContext**: グローバルコンテキスト設定 


* **Cachestoragetype**: キャッシュされた状態をメモリまたはディスクに格納します。 


* **Conのデリゲート**: 外部リソースにアクセスするためのユーザーアクセス許可を取得するために使用されるデリゲート 


* **オブザーバー**: protectionprofile に関連するイベントの通知を受信するオブザーバーインスタンス


* **applicationInfo**: 保護 SDK を利用しているアプリケーションに関する情報


  
### <a name="settings-function"></a>Settings 関数
同期操作に使用される、ProtectionProfile::Settings コンストラクター。

パラメーター:  
* **mipContext**: グローバルコンテキスト設定 


* **Cachestoragetype**: キャッシュされた状態をメモリまたはディスクに格納します。 


* **Conのデリゲート**: 外部リソースにアクセスするためのユーザーアクセス許可を取得するために使用されるデリゲート 


* **applicationInfo**: 保護 SDK を利用しているアプリケーションに関する情報


  
### <a name="getcachestoragetype-function"></a>GetCacheStorageType 関数
キャッシュをメモリまたはディスクのどちらに格納するかを取得します。

  
**戻り値**: 使用されているストレージの種類
  
### <a name="getconsentdelegate-function"></a>Getconのデリゲート関数
サービスに接続するために使用する同意委任を取得します。

  
**戻り値**: サービスに接続するために使用する同意委任
  
### <a name="getobserver-function"></a>GetObserver 関数
ProtectionProfile に関連するイベントの通知を受信するオブザーバーを取得します。

  
**戻り値**: protectionprofile に関連するイベントの通知を受け取るオブザーバー
  
### <a name="getmipcontext-function"></a>GetMipContext 関数
すべてのプロファイルで共有状態を表す mipmap コンテキストを取得します。

  
**戻り値**: mipmap コンテキスト
  
### <a name="gethttpdelegate-function"></a>GetHttpDelegate 関数
アプリケーションによって提供される HTTP 委任が取得されます (提供される場合)。

  
**戻り値**: HTTP 操作に使用される HTTP 委任
  
### <a name="sethttpdelegate-function"></a>SetHttpDelegate 関数
クライアント自体のスタックで既定の HTTP スタックをオーバーライドします。

パラメーター:  
* **Httpdelegate**: クライアントアプリケーションによって実装される HTTP コールバックインターフェイス


  
### <a name="gettaskdispatcherdelegate-function"></a>GetTaskDispatcherDelegate 関数
アプリケーションによって提供される TaskDispatcher デリゲート (存在する場合) を取得します。

  
は、非同期タスクの実行に使用される taskdispatcher デリゲートを**返し**ます。
  
### <a name="settaskdispatcherdelegate-function"></a>SetTaskDispatcherDelegate 関数
クライアント独自のを使用して、既定の asynchonous タスクのディスパッチ処理をオーバーライドします。

パラメーター:  
* **taskDispatcherDelegate**: クライアントアプリケーションによって実装されたタスクのディスパッチコールバックインターフェイス


タスクはプロファイルオブジェクトを参照することができるため、結果としてその破棄が妨げられます。 taskdispatcher キューは共有しないでください。
  
### <a name="setsessionid-function"></a>SetSessionId 関数
セッション ID を設定します。

パラメーター:  
* **sessionId**: ログ/テレメトリを関連付けるために使用されるセッション ID


  
### <a name="getsessionid-function"></a>GetSessionId 関数
セッション ID を取得します。

  
**戻り値**: ログ/テレメトリを関連付けるために使用されるセッション ID
  
### <a name="setcancachelicenses-function"></a>SetCanCacheLicenses 関数
エンドユーザーライセンス (Eul) がローカルにキャッシュされるかどうかを構成します。

パラメーター:  
* **canCacheLicenses**: エンジンが保護されたコンテンツを開くときにライセンスをキャッシュする必要があるかどうか


True の場合、保護されたコンテンツを開くと、関連付けられているライセンスがローカルにキャッシュされます。 False の場合、保護されたコンテンツを開くと、常に RMS サービスからライセンスを取得するための HTTP 操作が実行されます。
  
### <a name="cancachelicenses-function"></a>CanCacheLicenses 関数
エンドユーザーライセンス (Eul) がローカルにキャッシュされているかどうかを取得します。

  
**戻り値**: ライセンスキャッシュの構成
  
### <a name="setcustomsettings-function"></a>SetCustomSettings 関数
機能のゲーティングとテストに使用するカスタム設定を設定します。

パラメーター:  
* **Customsettings**: 名前と値のペアの一覧。


  
### <a name="getcustomsettings-function"></a>GetCustomSettings 関数
機能のゲーティングとテストに使用するカスタム設定を取得します。

  
**戻り値**: 名前と値のペアのリスト。