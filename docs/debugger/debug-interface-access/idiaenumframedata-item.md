---
title: Idiaenumframedata::item |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Item method
ms.assetid: 2761a72d-1868-4f5b-a32e-c2a1d9358c91
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a8d083cea518032c121a5cb9e9213abbbd7eaaf8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62829860"
---
# <a name="idiaenumframedataitem"></a>IDiaEnumFrameData::Item
インデックスを使用して、フレーム データ要素を取得します。

## <a name="syntax"></a>構文

```C++
HRESULT Item ( 
   DWORD           index,
   IDiaFrameData** section
);
```

#### <a name="parameters"></a>パラメーター
 インデックス

[in]インデックス、 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)を取得するオブジェクト。 インデックスは 0 ~ の範囲内で、 `count`-1 の場合、`count`によって返される、 [idiaenumframedata::get_count](../../debugger/debug-interface-access/idiaenumframedata-get-count.md)メソッド。

 section

[out]返します、 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)目的のフレームのデータ要素を表すオブジェクト。

## <a name="return-value"></a>戻り値
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。

## <a name="see-also"></a>関連項目
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)