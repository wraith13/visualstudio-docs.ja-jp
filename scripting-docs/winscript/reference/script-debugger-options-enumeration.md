---
title: SCRIPT_DEBUGGER_OPTIONS 列挙型 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SCRIPT_DEBUGGER_OPTIONS Enumeration
ms.assetid: aef41ec0-6f65-48e8-a69e-44b4e4fb929f
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 404d3939e0a328beb5e2413d25885fddf8478ead
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443629"
---
# <a name="scriptdebuggeroptions-enumeration"></a>SCRIPT_DEBUGGER_OPTIONS 列挙型
オプションや、アタッチされたデバッガーに適用する機能のセットを示します。 使用される[IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md)と[IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)  
  
> [!IMPORTANT]
> これらの定数は、PDM v10.0 によって以降に実装されます。 activdbg100.h にあります。  
  
## <a name="syntax"></a>構文  
  
```cpp
typedef SCRIPT_DEBUGGER_OPTIONS  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|[値]|説明|  
|------------|-----------|-----------------|  
|SDO_NONE|0x00000000|オプションは設定されません。|  
|SDO_ENABLE_FIRST_CHANCE_EXCEPTIONS|0x00000001|スクリプトのランタイムが例外がスローされたときに、BREAKREASON_ERROR イベントを発生させることを示します。 このオプションをデバッガーによって設定またはを使用してユーザー コードで設定が`Debug.enableFirstChanceExceptions(<true&#124;false>)`します。|  
|SDO_ENABLE_WEB_WORKER_SUPPORT|0x00000002|アタッチされたデバッガーが web ワーカーをサポートしていることを示します。|  
  
## <a name="see-also"></a>関連項目  
 [アクティブ スクリプト デバッガーの定数、列挙型、および構造体](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)