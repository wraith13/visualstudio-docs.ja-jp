---
title: Ijsdebugdatatarget::getthreadcontext メソッド |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.GetThreadContext
apilocation:
- jscript9diag.dll
ms.assetid: faf2a689-6c49-4a7d-b5a6-2b323e2257a7
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d7904ef81eb900c6466069267101f30d89e362a1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62582834"
---
# <a name="ijsdebugdatatargetgetthreadcontext-method"></a>IJsDebugDataTarget::GetThreadContext メソッド
指定したスレッドのコンテキストを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetThreadContext(  
   DWORD threadId,  
   ULONG32 contextFlags,  
   ULONG32 contextSize,  
   void *pContext  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `threadId`  
 [入力] ターゲット プロセスで実行中のスレッド。  
  
 `contextFlags`  
 [入力] コンテキスト フラグを指定します。 これは CONTEXT の ContextFlags フィールドと同じです (詳細については「winnt.h」で「CONTEXT_ALL」を参照)。  
  
 `contextSize`  
 [入力] pContext で指定したバッファーのサイズ。  
  
 `pContext`  
 [出力] pContext で指定したバッファーでプラットフォーム固有の CONTEXT 構造体を受け取ります。  
  
## <a name="return-value"></a>戻り値  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** jscript9diag.h です  
  
## <a name="see-also"></a>関連項目  
 [IJsDebugDataTarget インターフェイス](../../winscript/reference/ijsdebugdatatarget-interface.md)