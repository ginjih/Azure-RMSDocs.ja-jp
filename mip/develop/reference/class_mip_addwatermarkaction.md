---
title: AddWatermarkAction クラス
description: 'Microsoft Information Protection (MIP) SDK の addwatermarkaction:: undefined クラスを文書にします。'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 04/16/2020
ms.openlocfilehash: fe2cc80e5abb225a5e83c1b10c1c5f9f99401628
ms.sourcegitcommit: f54920bf017902616589aca30baf6b64216b6913
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/22/2020
ms.locfileid: "81763739"
---
# <a name="class-addwatermarkaction"></a>AddWatermarkAction クラス 
ウォーターマークの追加を指定するアクション クラス。
  
## <a name="summary"></a>まとめ
 メンバー                        | 説明                                
--------------------------------|---------------------------------------------
public const std::string& GetUIElementName()  |  ウォーターマーク要素を示すために使用される API。
public WatermarkLayout GetLayout() const  |  ウォーターマーク レイアウトを取得するために使用される API。
public const std::string& GetText() const  |  ウォーターマークに移動されるテキストを取得します。
public const std::string& GetFontName() const  |  ウォーターマークの表示に使用されるフォント名を取得します。
public int GetFontSize() const  |  ウォーターマークの表示に使用されるフォント サイズを取得します。
public const std::string& GetFontColor() const  |  ウォーターマークの表示に使用されるフォントの色を取得します。
  
## <a name="members"></a>メンバー
  
### <a name="getuielementname-function"></a>GetUIElementName 関数
ウォーターマーク要素を示すために使用される API。

  
**戻り値**: ウォーターマークを保持する UI 要素に使用する必要のある名前。 ウォーターマークを削除する必要がある場合は、RemoveWatermarkingAction でも同じ名前が返されます。
  
### <a name="getlayout-function"></a>GetLayout 関数
ウォーターマーク レイアウトを取得するために使用される API。

  
**戻り値**: WatermarkLayout: 列挙型 HORIZONTAL|DIAGONAL の形式のウォーターマーク レイアウト。 ,
  
### <a name="gettext-function"></a>GetText 関数
ウォーターマークに移動されるテキストを取得します。

  
**戻り値**: コンテンツ ヘッダーのテキスト。
  
### <a name="getfontname-function"></a>GetFontName 関数
ウォーターマークの表示に使用されるフォント名を取得します。

  
**戻り値**: フォント名。 ポリシーで何も設定されていない場合、規定値は Calibri です。
  
### <a name="getfontsize-function"></a>GetFontSize 関数
ウォーターマークの表示に使用されるフォント サイズを取得します。

  
**戻り値**: 整数値としてのフォント サイズ。
  
### <a name="getfontcolor-function"></a>GetFontColor 関数
ウォーターマークの表示に使用されるフォントの色を取得します。

  
**戻り値**: 文字列としてのフォントの色 (例: "#000000")。