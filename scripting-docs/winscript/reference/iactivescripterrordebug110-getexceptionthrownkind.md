---
title: IActiveScriptErrorDebug110::GetExceptionThrownKind |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptErrorDebug110::QueryIsFirstChance
ms.assetid: ecc16e54-93e4-4322-ae13-afa7cd860032
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a58add60560f22681f18225d844814e3547b671f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436068"
---
# <a name="iactivescripterrordebug110getexceptionthrownkind"></a>IActiveScriptErrorDebug110::GetExceptionThrownKind
スローされた例外の種類を示す値を返します。  
  
> [!IMPORTANT]
> [IActiveScriptErrorDebug110 インターフェイス](../../winscript/reference/iactivescripterrordebug110-interface.md)PDM version 11.0 以降によって実装されます。 activdbg100.h にあります。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetExceptionThrownKind(  
   SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND*  pExceptionKind  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pExceptionKind`  
 [out]によって表される (たとえば、初回るまたはハンドルされない)、スローされる例外の種類、 [SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND 列挙型](../../winscript/reference/script-error-debug-exception-thrown-kind-enumeration.md)列挙値。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptErrorDebug110 インターフェイス](../../winscript/reference/iactivescripterrordebug110-interface.md)