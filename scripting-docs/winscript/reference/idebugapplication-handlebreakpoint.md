---
title: IDebugApplication::HandleBreakPoint |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.HandleBreakPoint
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::HandleBreakPoint
ms.assetid: 97219bdf-a39a-4e69-81ac-4ca2afe77ce5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5e3444e6eedde9576216552e41abb0e97aafa2d7
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63412388"
---
# <a name="idebugapplicationhandlebreakpoint"></a>IDebugApplication::HandleBreakPoint
現在のスレッドをブロックして、デバッガー IDE にブレークポイントの通知を送信します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT HandleBreakPoint(  
   BREAKREASON         br,  
   BREAKRESUMEACTION*  pbra  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `br`  
 [in]中断の理由です。  
  
 `pbra`  
 [out]デバッガーは、アプリケーションを再開したときに実行するアクション。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>Remarks  
 言語エンジンは、ブレークポイントをヒットするスレッドのコンテキストでこのメソッドを呼び出します。 このメソッドは、現在のスレッドをブロックし、デバッガー IDE にブレークポイント通知を送信します。 デバッガーは、アプリケーションを再開するとき、`pbra`パラメーターを実行するには、どのようなアクションを指定します。  
  
> [!NOTE]
> 言語エンジンは、フレームまたは、ブレークポイント中の式を評価スタックの列挙などのタスクを実行するスレッドによって呼び出される可能性があります。  
  
 このメソッドにより`IApplicationDebugger::onHandleBreakPoint`呼び出されます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugApplication インターフェイス](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onHandleBreakPoint](../../winscript/reference/iapplicationdebugger-onhandlebreakpoint.md)   
 [BREAKREASON 列挙型](../../winscript/reference/breakreason-enumeration.md)   
 [BREAKRESUMEACTION 列挙型](../../winscript/reference/breakresumeaction-enumeration.md)