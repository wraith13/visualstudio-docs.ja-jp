---
title: IDiaStackWalkFrame |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame interface
ms.assetid: 42d82845-d6f6-4846-9ecd-9dd169216077
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 343c56e3d3175c26900b0cfb4cdc3d816a324404
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62831820"
---
# <a name="idiastackwalkframe"></a>IDiaStackWalkFrame
呼び出しの間のスタック コンテキストを維持、 [idiaframedata::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)メソッド。

## <a name="syntax"></a>構文

```
IDiaStackWalkFrame : IUnknown
```

## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド
 次の表は、メソッドの`IDiaStackWalkFrame`します。

|メソッド|説明|
|------------|-----------------|
|[IDiaStackWalkFrame::get_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-get-registervalue.md)|レジスタの値を取得します。|
|[IDiaStackWalkFrame::put_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-put-registervalue.md)|レジスタの値を設定します。|
|[IDiaStackWalkFrame::readMemory](../../debugger/debug-interface-access/idiastackwalkframe-readmemory.md)|イメージからは、メモリを読み取ります。|
|[IDiaStackWalkFrame::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddress.md)|最も近い関数のリターン アドレスの指定したスタック フレームを検索します。|
|[IDiaStackWalkFrame::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddressstart.md)|指定したアドレスに近いのリターン アドレスの指定したスタック フレームを検索します。|

## <a name="remarks"></a>Remarks
 このインターフェイスに読み取りおよびレジスタの書き込みだけでなくメモリへのアクセス、および戻り値のアドレスの検索プログラムの実行中に使用されます。

## <a name="notes-for-callers"></a>呼び出し元のノート
 クライアント アプリケーションを選択し、このインターフェイスを実装するインターフェイスのインスタンスを渡す、 [idiaframedata::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)メソッド。 このインターフェイスの同じインスタンスが繰り返しの呼び出しごとに、レジスタの状態を維持するために使用される、`execute`メソッド。 `execute`メソッドは、戻り値のアドレスを決定するこのインターフェイスを使用することもできます。

## <a name="requirements"></a>必要条件
 ヘッダー:Dia2.h

 ライブラリ: diaguids.lib

 DLL: msdia80.dll

## <a name="see-also"></a>関連項目
- [インターフェイス (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)