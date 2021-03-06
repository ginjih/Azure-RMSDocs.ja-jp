---
title: クラス PolicyHandler
description: 'Microsoft Information Protection (MIP) SDK の policyhandler:: undefined クラスについて説明します。'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 04/16/2020
ms.openlocfilehash: c46b72f3a040204b4485da14f00f38ca69fa8222
ms.sourcegitcommit: f54920bf017902616589aca30baf6b64216b6913
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/22/2020
ms.locfileid: "81760958"
---
# <a name="class-policyhandler"></a>クラス PolicyHandler 
このクラスは、ファイル上のすべてのポリシー ハンドラー関数にインターフェイスを提供します。
  
## <a name="summary"></a>まとめ
 メンバー                        | 説明                                
--------------------------------|---------------------------------------------
public std:: shared_ptr\<contentlabel\> GetSensitivityLabel (const executionstate& 状態)  |  既存のコンテンツから機密ラベルを取得します。
public std:: vector\<std:: shared_ptr\<Action\> \> computeactions (const executionstate& state)  |  指定された状態に基づいてハンドラー内でルールを実行し、実行するアクションの一覧を返します。
public void NotifyCommittedActions(const ExecutionState& state)  |  計算されたアクションが適用され、データがディスクにコミットされると呼び出されます。
  
## <a name="members"></a>メンバー
  
### <a name="getsensitivitylabel-function"></a>GetSensitivityLabel 関数
既存のコンテンツから機密ラベルを取得します。

パラメーター:  
* **state**: コンテンツの現在の状態。 



  
**戻り値**: 現在、コンテンツに適用されているラベル。 ラベルが付いていない場合は、空を返します。
  
### <a name="computeactions-function"></a>ComputeActions 関数
指定された状態に基づいてハンドラー内でルールを実行し、実行するアクションの一覧を返します。

パラメーター:  
* **state**: ルールが実行されているコンテンツの現在の実行状態。 



  
**戻り値**: コンテンツに適用する必要のあるアクションの一覧。
  
### <a name="notifycommittedactions-function"></a>NotifyCommittedActions 関数
計算されたアクションが適用され、データがディスクにコミットされると呼び出されます。

パラメーター:  
* **状態**: アクションがコミットされた後のコンテンツの現在の実行状態。 


: この呼び出しは、監査イベントを送信します。