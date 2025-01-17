---
title: CA1034:入れ子にされた型を参照可能にすることはできません
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
helpviewer_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
ms.assetid: e9789a2c-2540-42a1-8705-ae7104011194
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: a086ad80bd13fb18f866769db34d72cae3e67496
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922860"
---
# <a name="ca1034-nested-types-should-not-be-visible"></a>CA1034:入れ子にされた型を参照可能にすることはできません

|||
|-|-|
|TypeName|NestedTypesShouldNotBeVisible|
|CheckId|CA1034|
|Category|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因

外部から参照できる型に、外部から参照できる型宣言が含まれています。 入れ子になった列挙型とプロテクト型は、この規則から除外されます。

## <a name="rule-description"></a>規則の説明
入れ子になった型は、別の型のスコープ内で宣言された型です。 入れ子になった型は、含んでいる型のプライベート実装の詳細をカプセル化する場合に便利です。 このような用途なので、入れ子にされた型は外部から参照できないようにします。

論理グループまたは名前の競合を避けるために、外部から参照できる入れ子になった型を使用しないでください。代わりに、名前空間を使用します。

入れ子になった型には、メンバーアクセシビリティの概念が含まれており、プログラマによってはわかりにくくなります。

保護された型は、高度なカスタマイズシナリオでサブクラスおよび入れ子にされた型で使用できます。

## <a name="how-to-fix-violations"></a>違反の修正方法
入れ子になった型を外部から参照できるようにしない場合は、型のアクセシビリティを変更します。 それ以外の場合は、入れ子になった型を親から削除します。 入れ子になった型を分類することが目的である場合は、代わりに名前空間を使用して階層を作成します。

## <a name="when-to-suppress-warnings"></a>警告を非表示にする場合
この規則による警告は抑制しないでください。

## <a name="example"></a>例
次の例は、規則に違反する型を示しています。

[!code-cpp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CPP/ca1034-nested-types-should-not-be-visible_1.cpp)]
[!code-csharp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CSharp/ca1034-nested-types-should-not-be-visible_1.cs)]
[!code-vb[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/VisualBasic/ca1034-nested-types-should-not-be-visible_1.vb)]