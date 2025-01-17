---
title: SAL 注釈を使って C/C++ のコード障害を減らす方法
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- annotations
- SAL annotations
- code analysis, annotation
ms.assetid: a16e47d0-6f3e-4ed6-8883-459b2874e9a4
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: e968879e10456137033f53d57f7351de5522fe46
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923778"
---
# <a name="using-sal-annotations-to-reduce-cc-code-defects"></a>SAL 注釈を使って C/C++ のコード障害を減らす方法
SAL は、Microsoft ソースコード注釈言語です。 ソースコードの注釈を使用すると、コードの意図を明確にすることができます。 これらの注釈を使用すると、自動化された静的分析ツールでコードをより正確に分析することができ、誤検知や誤否定も大幅に減少します。

ドキュメントのこのセクションの記事では、SAL の側面について説明し、SAL 構文のリファレンスを提供し、その使用例を示します。

- [SAL について](../code-quality/understanding-sal.md)

     主要な SAL 注釈を示す情報と例を提供します。

- [関数パラメーターおよび戻り値の注釈設定](../code-quality/annotating-function-parameters-and-return-values.md)

     関数と関数のパラメーターの SAL 注釈を一覧表示します。

- [関数の動作に注釈を付ける](../code-quality/annotating-function-behavior.md)

     関数と関数の動作に関する SAL 注釈の一覧を示します。

- [構造体とクラスに注釈を付ける](../code-quality/annotating-structs-and-classes.md)

     構造体とクラスの SAL 注釈の一覧を示します。

- [ロック動作に注釈を付ける](../code-quality/annotating-locking-behavior.md)

     SAL 注釈をロックメカニズムと共に使用する方法について説明します。

- [注釈を適用するタイミングと場所の指定](../code-quality/specifying-when-and-where-an-annotation-applies.md)

     他の SAL 注釈の条件またはスコープ (配置) を指定する SAL 注釈を一覧表示します。

- [組み込み関数](../code-quality/intrinsic-functions.md)

     組み込みの SAL 注釈を一覧表示します。

- [ベスト プラクティスと例](../code-quality/best-practices-and-examples-sal.md)

     SAL 注釈の使用方法を示す例を示します。 また、一般的な落とし穴についても説明します。

## <a name="related-resources"></a>関連資料
[コード分析チームのブログ](http://go.microsoft.com/fwlink/?LinkId=251197)

## <a name="see-also"></a>関連項目
[Windows ドライバーの SAL 2.0 注釈](http://go.microsoft.com/fwlink/?LinkId=250979)