﻿---
title: Idiasymbol::get_intro |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_intro method
ms.assetid: 101afe4a-4c57-45de-87b4-330394c6de10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 153daa1f43ba4945a5eb32aea82c5d58ff57c5f6
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2019
ms.locfileid: "62836801"
---
# <a name="idiasymbolgetintro"></a>IDiaSymbol::get_intro
関数が紹介の仮想関数であるかどうかを指定するフラグを取得します。

## <a name="syntax"></a>構文

```C++
HRESULT get_intro ( 
    BOOL* pRetVal
);
```

#### <a name="parameters"></a>パラメーター
`pRetVal`

[out]返します`TRUE`関数が仮想; 入門場合を返しますそれ以外の場合、`FALSE`します。

## <a name="return-value"></a>戻り値
成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`またはエラー コード。

> [!NOTE]
> 戻り値`S_FALSE`プロパティが、シンボルの使用可能なことを意味します。

## <a name="example"></a>例

```C++
class A {
    virtual int f1();
}
class B : public A {
    int f1();
}
```

両方`A::f1`と`B::f1`は仮想関数ですが`A::f1`は、仮想メソッドの概要。

## <a name="requirements"></a>必要条件

|必要条件|説明|
|-----------------|-----------------|
|ヘッダー:|Dia2.h|
|バージョン:|DIA SDK v7.0|

## <a name="see-also"></a>関連項目
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
