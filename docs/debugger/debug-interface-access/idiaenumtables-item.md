---
title: Idiaenumtables::item |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Item method
ms.assetid: d65ab262-10c6-48ce-95a3-b5e4cb2c85af
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 03931580f774c29a67771d2251b51825242535c9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62829378"
---
# <a name="idiaenumtablesitem"></a>IDiaEnumTables::Item
インデックスまたは名前を使用してテーブルを取得します。

## <a name="syntax"></a>構文

```C++
HRESULT Item ( 
   VARIANT     index,
   IDiaTable** table
);
```

#### <a name="parameters"></a>パラメーター
 `index`

[in]インデックスまたは名前、 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)を取得します。 0 の範囲の場合は、整数のバリアントを使用すると、必要があります`count`-1 の場合、`count`によって返されるは、 [idiaenumtables::get_count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)メソッド。

 `table`

[out]返します、 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)目的のテーブルを表すオブジェクト。

## <a name="return-value"></a>戻り値
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。

## <a name="remarks"></a>Remarks
 文字列のバリアントが指定されている場合、文字列は、特定のテーブルを名前します。 名前は、テーブル名のいずれかで定義されている[定数 (Debug Interface Access SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)します。

## <a name="example"></a>例

```C++
VARIANT var;
var.vt = VT_BSTR;
var.bstrVal = SysAllocString(DiaTable_Symbols );
IDiaTable* pTable;
pEnumTables->Item( var, &pTable );
```

## <a name="see-also"></a>関連項目
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
- [IDiaEnumTables::get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)
- [定数 (Debug Interface Access SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)