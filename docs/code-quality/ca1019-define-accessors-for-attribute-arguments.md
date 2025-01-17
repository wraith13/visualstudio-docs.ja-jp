---
title: CA1019:属性引数にアクセサーを定義します
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
helpviewer_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
ms.assetid: 197f2378-3c43-427e-80de-9ec25006c05c
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8422427997db291aa24bc8a8bacfdc59abe35998
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923075"
---
# <a name="ca1019-define-accessors-for-attribute-arguments"></a>CA1019:属性引数にアクセサーを定義します

|||
|-|-|
|TypeName|DefineAccessorsForAttributeArguments|
|CheckId|CA1019|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
コンストラクターでは、属性は対応するプロパティを持たない引数を定義します。

## <a name="rule-description"></a>規則の説明
属性では、対象に適用するときに必ず指定する必須の引数を定義できます。 この引数は、コンストラクターに位置指定パラメーターで属性を指定できるようになるため、位置指定引数とも呼ばれます。 必須のすべての引数について、対応する読み取り専用のプロパティも属性で規定する必要があります。これは、引数値を実行時に取得できるようにするためです。 このルールでは、各コンストラクターパラメーターに対応するプロパティが定義されていることを確認します。

また、属性ではオプションの引数も定義できます。これは名前付き引数とも呼ばれます。 この引数は、名前でコンストラクターに属性を指定するときに使用されます。また、対応する読み取り/書き込みプロパティが必要です。

必須および省略可能な引数については、対応するプロパティとコンストラクターパラメーターで同じ名前を使用する必要がありますが、大文字と小文字は区別されません。 プロパティは Pascal 形式の大文字と小文字を使用し、パラメーターは camel 形式を使用します。

## <a name="how-to-fix-violations"></a>違反の修正方法
この規則違反を修正するには、1つも含まれていない各コンストラクターパラメーターに読み取り専用プロパティを追加します。

## <a name="when-to-suppress-warnings"></a>警告を非表示にする場合
必須の引数の値を取得可能にしない場合は、この規則からの警告を非表示にします。

## <a name="custom-attributes-example"></a>カスタム属性の例

次の例は、必須 (位置指定) パラメーターを定義する2つの属性を示しています。 属性の最初の実装が正しく定義されていません。 2番目の実装は正しい方法です。

[!code-csharp[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_1.cs)]
[!code-vb[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/VisualBasic/ca1019-define-accessors-for-attribute-arguments_1.vb)]

## <a name="positional-and-named-arguments"></a>位置指定引数と名前付き引数

位置指定引数と名前付き引数を使用すると、ライブラリのコンシューマーに対して、属性に必須の引数と省略可能な引数を明確にすることができます。

次の例は、位置指定引数と名前付き引数の両方を持つ属性の実装を示しています。

[!code-csharp[FxCop.Design.AttributeAccessorsNamed#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_2.cs)]

次の例は、カスタム属性を2つのプロパティに適用する方法を示しています。

[!code-csharp[FxCop.Design.AttributeAccessorsNamedApplied#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_3.cs)]

## <a name="related-rules"></a>関連するルール
[CA1813:封印されていない属性を避ける](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>関連項目
[属性](/dotnet/standard/design-guidelines/attributes)