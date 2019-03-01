---
title: クラスの mip::AuthDelegate::OAuth2Challenge
description: Mip::authdelegate クラスの Microsoft Information Protection (MIP) SDK について説明します。
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: 64a485c30dc6fdb8154c85c3afbd548bbc78ce9a
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2019
ms.locfileid: "56259410"
---
# <a name="class-mipauthdelegateoauth2challenge"></a>クラスの mip::AuthDelegate::OAuth2Challenge 
oauth2 トークンを生成するために呼び出し元アプリケーションに必要なすべての情報を含むクラスです。
  
## <a name="summary"></a>まとめ
 メンバー                        | 説明                                
--------------------------------|---------------------------------------------
パブリック OAuth2Challenge (const std::string & 機関、const std::string & リソース、const std::string & スコープ)  |  新しい[OAuth2Challenge](class_mip_authdelegate_oauth2challenge.md)オブジェクト。
public const std::string& GetAuthority() const  |  機関の文字列を取得します。
public const std::string& GetResource() const  |  リソース文字列を取得します。
public const std::string& GetScope() const  |  スコープ文字列を取得します。
  
## <a name="members"></a>メンバー
  
### <a name="oauth2challenge-function"></a>OAuth2Challenge 関数
新しい[OAuth2Challenge](class_mip_authdelegate_oauth2challenge.md)オブジェクト。

パラメーター:  
* **機関**: に対して生成されるトークンが必要な権限。 


* **リソース**: トークンに設定されているリソース。 


* **スコープ**: トークンに設定されているスコープです。


  
### <a name="getauthority-function"></a>GetAuthority 関数
機関の文字列を取得します。

  
**返します**:機関の文字列。
  
### <a name="getresource-function"></a>GetResource 関数
リソース文字列を取得します。

  
**返します**:リソース文字列。
  
### <a name="getscope-function"></a>GetScope 関数
スコープ文字列を取得します。

  
**返します**:スコープの文字列。