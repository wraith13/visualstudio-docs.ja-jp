---
title: CA1810:参照型の静的フィールドをインラインで初期化します
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
helpviewer_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
ms.assetid: e9693118-a914-4efb-9550-ec659d8d97d2
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8838de46c6b14f698194f343aebec30402452970
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921527"
---
# <a name="ca1810-initialize-reference-type-static-fields-inline"></a>CA1810:参照型の静的フィールドをインラインで初期化します

|||
|-|-|
|TypeName|InitializeReferenceTypeStaticFieldsInline|
|CheckId|CA1810|
|カテゴリ|Microsoft.Performance|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
参照型は、明示的な静的コンストラクターを宣言します。

## <a name="rule-description"></a>規則の説明
型で明示的な静的コンストラクターを宣言すると、Just-In-Time (JIT) コンパイラが、静的コンストラクターが呼び出されたことを確認するために、型の静的メソッドと静的インスタンス コンストラクターに個別にチェックを追加します。 静的初期化は、静的メンバーにアクセスするか、型のインスタンスが作成されるときにトリガーされます。 ただし、静的な初期化は、型の変数を宣言しても使用しない場合にはトリガーされません。これは、初期化がグローバル状態を変更した場合に重要になる可能性があります。

すべての静的データがインラインで初期化され、明示的な静的コンストラクターが宣言されていない場合、 `beforefieldinit` Microsoft 中間言語 (msil) コンパイラは、静的データを初期化するフラグと暗黙的な静的コンストラクターを msil 型に追加します。カスタム. JIT コンパイラが`beforefieldinit`フラグを検出すると、ほとんどの場合、静的コンストラクターチェックは追加されません。 静的フィールドにアクセスする前に、静的メソッドまたはインスタンスコンストラクターが呼び出される前に静的初期化が行われることは保証されていません。 静的な初期化は、型の変数が宣言された後でいつでも発生する可能性があることに注意してください。

静的コンストラクターのチェックによってパフォーマンスが低下することがあります。 静的コンストラクターは、静的フィールドの初期化にのみ使用されることがよくあります。その場合は、静的フィールドに最初にアクセスする前に静的初期化が行われるようにする必要があります。 `beforefieldinit`動作は、これらおよびその他のほとんどの型に適しています。 これは、静的な初期化がグローバル状態に影響し、次のいずれかに該当する場合にのみ不適切です。

- グローバルな状態への影響は高価であり、型が使用されていない場合は必要ありません。

- グローバル状態の効果には、型の静的フィールドにアクセスせずにアクセスできます。

## <a name="how-to-fix-violations"></a>違反の修正方法
この規則違反を修正するには、静的データが宣言されたとき、および静的コンストラクターを削除するときに、静的データをすべて初期化します。

## <a name="when-to-suppress-warnings"></a>警告を非表示にする場合
パフォーマンスが問題にならない場合は、このルールの警告を抑制しても安全です。または、静的な初期化によって発生するグローバル状態の変更がコストがかかる場合や、型の静的メソッドが呼び出される前に発生することを保証する必要がある場合、または型のインスタンスが作成される場合は、。

## <a name="example"></a>例

次の例は、規則`StaticConstructor` `NoStaticConstructor`に違反する型 () を示しています。この型は、規則に適合するように静的コンストラクターをインライン初期化で置き換えます。

[!code-csharp[FxCop.Performance.RefTypeStaticCtor#1](../code-quality/codesnippet/CSharp/ca1810-initialize-reference-type-static-fields-inline_1.cs)]
[!code-vb[FxCop.Performance.RefTypeStaticCtor#1](../code-quality/codesnippet/VisualBasic/ca1810-initialize-reference-type-static-fields-inline_1.vb)]

クラスの MSIL 定義に`beforefieldinit`フラグが追加されていることに注意してください。 `NoStaticConstructor`

```
.class public auto ansi StaticConstructor
extends [mscorlib]System.Object
{
} // end of class StaticConstructor

.class public auto ansi beforefieldinit NoStaticConstructor
extends [mscorlib]System.Object
{
} // end of class NoStaticConstructor
```

## <a name="related-rules"></a>関連するルール

- [CA2207値型の静的フィールドをインラインで初期化する](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)