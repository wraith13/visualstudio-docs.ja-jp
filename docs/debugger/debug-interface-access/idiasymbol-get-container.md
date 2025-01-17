---
title: Idiasymbol::get_container |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_container method
ms.assetid: 24e832eb-80b3-484c-a41b-11477ec9de99
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 23b8d43931b880ff61ec9871f9f5984b98833c28
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2019
ms.locfileid: "64787893"
---
# <a name="idiasymbolgetcontainer"></a>IDiaSymbol::get_container
この関数は、この記号の親/コンテナーを表すシンボルへのポインターを取得します。

## <a name="syntax"></a>構文

```C++
HRESULT get_container(
   IDiaSymbol **pRetVal
);
```

#### <a name="parameters"></a>パラメーター
 `pRetVal`

[out]ポインターを返します、`IDiaSymbol`このシンボルのコンテナーに関する情報を格納します。

## <a name="return-value"></a>戻り値
 成功した場合、S_OK を返します。それ以外の場合、S_FALSE またはエラー コードを返します。

> [!NOTE]
> S_FALSE の戻り値は、プロパティがシンボルを使用できないことを意味します。

## <a name="requirements"></a>必要条件

|必要条件|説明|
|-----------------|-----------------|
|ヘッダー:|Dia2.h|
|バージョン:|DIA SDK バージョン 8.0|

## <a name="see-also"></a>関連項目
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)