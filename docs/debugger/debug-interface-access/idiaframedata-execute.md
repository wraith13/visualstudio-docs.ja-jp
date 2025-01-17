---
title: Idiaframedata::execute |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::execute method
ms.assetid: 7a6c7d03-1ff1-4059-bd54-5f407eeebc26
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 78440c703ece2aa54e54594d57156dbb17848915
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62832660"
---
# <a name="idiaframedataexecute"></a>IDiaFrameData::execute
スタック アンワインドを実行し、スタック ウォーク フレーム インターフェイスで結果を返します。

## <a name="syntax"></a>構文

```C++
HRESULT execute ( 
   IDiaStackWalkFrame* frame
);
```

#### <a name="parameters"></a>パラメーター
 `frame`

[in][IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)フレーム レジスタの状態を保持するオブジェクト。

## <a name="return-value"></a>戻り値
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。 次の表では、このメソッドの戻り値を示します。

|[値]|説明|
|-----------|-----------------|
|E_DIA_INPROLOG|プロローグ コードの中にスタック フレームを実行することはできません。|
|E_DIA_SYNTAX|フレームのプログラムで発生したエラーを解析します。|
|E_DIA_FRAME_ACCESS|アクセスのレジスタまたはメモリをできません。|
|E_DIA_VALUE|(たとえば、0 による除算)、値の計算のエラーです。|

## <a name="remarks"></a>Remarks
 このメソッドは、スタックをアンワインドするデバッグ中に呼び出されます。 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)オブジェクトがレジスタに更新プログラムを受信しで使用されるメソッドを提供するクライアント アプリケーションによって実装される、`execute`メソッド。

## <a name="see-also"></a>関連項目
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)