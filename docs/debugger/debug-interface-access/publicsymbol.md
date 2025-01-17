﻿---
title: PublicSymbol |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- data symbols [C++]
- PublicSymbol symbol
- global functions [C++], as public symbols
ms.assetid: f8d33007-302d-4549-9dad-47fb33ea60b7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c2c042d75ad74cc42d94596d60008dc43704e612
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62854887"
---
# <a name="publicsymbol"></a>PublicSymbol
(最小値、各グローバル関数とデータ シンボル) にある各パブリック シンボルが指定された .exe ファイルが作成されたときに、`SymTagPublicSymbol`タグ。

## <a name="properties"></a>プロパティ
 次の表では、この記号の型の有効なプロパティを示します。

|プロパティ|データの種類|説明|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|場所のオフセットの部分詳細については、次を参照してください。、 [LocationType 列挙型](../../debugger/debug-interface-access/locationtype.md)します。|
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|場所のセクションの一部詳細については、次を参照してください。、 [LocationType 列挙型](../../debugger/debug-interface-access/locationtype.md)します。|
|[IDiaSymbol::get_code](../../debugger/debug-interface-access/idiasymbol-get-code.md)|`BOOL`|`TRUE` シンボルの場所がコード内にある場合は。|
|[IDiaSymbol::get_function](../../debugger/debug-interface-access/idiasymbol-get-function.md)|`BOOL`|`TRUE` シンボルが関数の場合は。|
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|このシンボル (バイト単位) の長さ。|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|グローバル スコープの記号。|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|構文の親のシンボルの ID。|
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|パブリック シンボルがある静的な場所です。詳細については、次を参照してください。[シンボルの場所](../../debugger/debug-interface-access/symbol-locations.md)します。|
|[IDiaSymbol::get_managed](../../debugger/debug-interface-access/idiasymbol-get-managed.md)|`BOOL`|`TRUE` シンボルの場所がマネージ コードの場合は。|
|[IDiaSymbol::get_msil](../../debugger/debug-interface-access/idiasymbol-get-msil.md)|`BOOL`|`TRUE` シンボルの場所が Microsoft Intermediate Language (MSIL) コード内にある場合。|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|シンボルの完全修飾名。|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|シンボルのインデックス ID。|
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|そのブロック内でシンボルの相対的な位置。|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|返します`SymTagPublicSymbol`(の 1 つ、 [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md)値)。|
|[IDiaSymbol::get_undecoratedName](../../debugger/debug-interface-access/idiasymbol-get-undecoratedname.md)|`BSTR`|装飾されていないシンボルの名前。|
|[IDiaSymbol::get_undecoratedNameEx](../../debugger/debug-interface-access/idiasymbol-get-undecoratednameex.md)|`BSTR`|一部またはすべての非装飾のシンボル名にします。|

## <a name="see-also"></a>関連項目
- [シンボル型の構文階層](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [LocationType 列挙型](../../debugger/debug-interface-access/locationtype.md)
- [シンボルの場所](../../debugger/debug-interface-access/symbol-locations.md)
