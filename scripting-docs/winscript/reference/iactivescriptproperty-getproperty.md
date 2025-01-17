---
title: IActiveScriptProperty::GetProperty |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProperty.GetProperty
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetProperty method, IActiveScriptProperty interface
ms.assetid: a43383db-b148-4d76-83bd-4f0e899b7cb1
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e10d72e289fc2dc31464ce4505cea5c03e8d7f9d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992791"
---
# <a name="iactivescriptpropertygetproperty"></a>IActiveScriptProperty::GetProperty
パラメーターで指定されているプロパティを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetProperty(  
// The property value:  
    uint dwProperty,    
// Not used:  
    IntPtr pvarIndex,    
// The value of the property:   
    out object pvarValue,    
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwProperty`  
 取得するプロパティの値。  
  
 `pvarIndex`  
 使用しません。  
  
 `pvarValue`  
 プロパティの値。  
  
 値が許可されている`dwProperty`は次の表で説明します。  
  
|定数|[値]|説明|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|浮動小数点のポイント モードではなく整数モードで分割するスクリプト エンジンを強制します。|  
|SCRIPTPROP_STRINGCOMPAREINSTANCE|0x00003001|置き換えられるスクリプト エンジンの文字列比較関数を使用します。|  
|SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION|0x70000002|グローバル オブジェクトに貢献するその他のスクリプト エンジンが存在するスクリプト エンジンに通知します。|  
|SCRIPTPROP_INVOKEVERSIONING|0x00004000|力、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]スクリプト エンジンをサポートする言語機能のセットを選択します。 既定でサポートされる言語機能のセット、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]スクリプト エンジンがバージョン 5.7 のされていた言語機能セットと同じですが、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]スクリプト エンジンです。|  
  
## <a name="return-value"></a>戻り値  
 次のいずれかの値を返します。  
  
|戻り値|説明|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引数が有効ではありません。|  
|`E_UNEXPECTED`|呼び出しが予期されていませんでした (たとえば、スクリプト エンジンがされていないされて読み込まれるまたは初期化) します。|  
  
## <a name="remarks"></a>Remarks  
 ホストは、SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION プロパティを使用して、グローバル オブジェクトに貢献するその他のスクリプト エンジンが存在するスクリプト エンジンに通知することができます。 たとえば、Internet Explorer に通知できます、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]のみ表示するページを含むエンジン[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]スクリプト。 したがって、のみ、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]エンジンは、グローバル オブジェクトのウィンドウに新しいプロパティを追加することができ、同じ操作を実行する Visual Basic Scripting Edition (VBScript) エンジンはありません。 エンジンは、このフラグは無視してかまいませんまたはグローバル オブジェクトに追加される新しいメンバーの管理を最適化するために使用できます。  
  
 ホストは SCRIPTPROP_INVOKEVERSIONING プロパティを使用して、ある言語機能のセットを選択サポートされているときに、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]スクリプト エンジンが起動します。 このプロパティが 1 (SCRIPTLANGUAGEVERSION_5_7) に設定されている場合、利用可能な言語機能は、のバージョン 5.7 に表示されていたものと同じ、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]スクリプト エンジンです。 2 (SCRIPTLANGUAGEVERSION_5_8) に設定されている場合、バージョン 5.7 バージョン 5.8 で追加された機能だけでなくで登場するものは、利用可能な言語機能。 既定でこのプロパティは、ホストが別の既定の動作をサポートしていない限りバージョン 5.7 に含まれる言語機能セットと同じです (SCRIPTLANGUAGEVERSION_DEFAULT) を 0 に設定されます。 たとえばが Internet Explorer 8、 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 5.8 バージョンでサポートされる言語機能[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]既定で Internet Explorer 8 のドキュメント モードは、「Internet Explorer 8 標準」モードとスクリプト エンジン。  
  
## <a name="see-also"></a>関連項目  
 [ドキュメントの互換性の定義](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/compatibility/cc288325(v=vs.85))   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [バージョン情報](../../javascript/reference/javascript-version-information.md)