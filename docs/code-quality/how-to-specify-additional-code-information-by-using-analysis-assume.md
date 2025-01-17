---
title: _Analysis_assume を使用して、コード分析のヒント
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _Analysis_assume
helpviewer_keywords:
- _Analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 1d3c80f0780dcd577356de69944dcc76cca7133c
ms.sourcegitcommit: ab06cde69d862440b4277bcd9bf02e7b50593a1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/13/2019
ms.locfileid: "67132116"
---
# <a name="how-to-specify-additional-code-information-by-using-analysisassume"></a>方法: _Analysis_assume を使用して追加のコード情報を指定する

C/C++ コード分析のプロセスを支援し、警告を減らすは、コード分析ツールへのヒントを指定できます。 追加情報を提供するには、次の関数を使用します。

`_Analysis_assume(`  `expr`  `)`

`expr` -任意の式は true と評価されると見なされます。

コード分析ツールでは、関数が表示され、式が変更されるまで、たとえば、変数への代入によってが true の時点で、式で表される条件のことを前提としています。

> [!NOTE]
> `_Analysis_assume` コードの最適化には影響しません。 コード分析ツールでは、外部`_Analysis_assume`操作なしとして定義されます。

## <a name="example"></a>例

次のコードでは`_Analysis_assume`コード分析の警告を解決する[C6388](../code-quality/c6388.md):

```cpp
#include<windows.h>
#include<codeanalysis\sourceannotations.h>

using namespace vc_attributes;

//requires pc to be null
void f([Pre(Null=Yes)] char* pc);

// calls free and sets ch to null
void FreeAndNull(char** ch);

void test()
{
    char pc = (char)malloc(5);
    FreeAndNull(&pc);
    __analysis_assume(pc == NULL);
    f(pc);
}
```

## <a name="see-also"></a>関連項目

- [__assume](/cpp/intrinsics/assume)
