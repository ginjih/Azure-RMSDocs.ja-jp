---
title: RecommendLabelAction クラス
description: 'Microsoft Information Protection (MIP) SDK の recommendlabelaction:: undefined クラスを文書にします。'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 04/16/2020
ms.openlocfilehash: 3990d6de9d78002d9c240e621f96351cd337aabb
ms.sourcegitcommit: f54920bf017902616589aca30baf6b64216b6913
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/22/2020
ms.locfileid: "81764543"
---
# <a name="class-recommendlabelaction"></a>RecommendLabelAction クラス 
このアクションの目的は、ユーザーにラベルを提案することです。 ユーザーが推奨ラベルを無視した後にこの呼び出しを抑制する場合、実行状態のサポートされるアクションを使用して行う必要があります。
  
## <a name="summary"></a>まとめ
 メンバー                        | 説明                                
--------------------------------|---------------------------------------------
public const std:: shared_ptr\<Label\>& getlabel () const  |  推奨されるラベルを取得します。
public const std:: vector\<std:: String\>& GetClassificationIds () const  |  一致し、このラベルが表示される原因となった分類 Id を取得します。
  
## <a name="members"></a>メンバー
  
### <a name="getlabel-function"></a>GetLabel 関数
推奨されるラベルを取得します。

  
は、ラベルを**返し**ます。
  
### <a name="getclassificationids-function"></a>GetClassificationIds 関数
一致し、このラベルが表示される原因となった分類 Id を取得します。

  
は、Const std:: vector<std:: string>& 、このラベルが表示される原因となった分類 Id の一覧を**返し**ます。