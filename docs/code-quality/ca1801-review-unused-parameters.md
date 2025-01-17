---
title: CA1801:使用されていないパラメーターの確認
ms.date: 06/24/2019
ms.topic: reference
f1_keywords:
- AvoidUnusedParameters
- CA1801
- ReviewUnusedParameters
helpviewer_keywords:
- CA1801
- ReviewUnusedParameters
ms.assetid: 5d73545c-e153-4b7c-a7b2-be6bf5aca5be
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f9a0714082e0fce744fe74eaa4e4aefee5a41867
ms.sourcegitcommit: 01c3c9dcade5d913bde2c7efa8c931a7b04e6cd0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2019
ms.locfileid: "67365376"
---
# <a name="ca1801-review-unused-parameters"></a>CA1801:使用されていないパラメーターの確認

|||
|-|-|
|TypeName|ReviewUnusedParameters|
|CheckId|CA1801|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|なし - メンバーが行った変更に関係なく、アセンブリの外部に表示されない場合<br /><br /> なし - の本体にあるパラメーターを使用するメンバーを変更する場合<br /><br /> あり - パラメーターを削除して、アセンブリの外側に表示される場合。|

## <a name="cause"></a>原因

メソッド シグネチャには、メソッドの本体で使用されていないパラメーターが含まれています。

このルールでは、次のようなメソッドはチェックしません。

- デリゲートによって参照されるメソッド。

- イベント ハンドラーとして使用されるメソッド。

- 宣言されたメソッド、 `abstract` (`MustOverride` Visual basic) 修飾子。

- 宣言されたメソッド、 `virtual` (`Overridable` Visual basic) 修飾子。

- 宣言されたメソッド、 `override` (`Overrides` Visual basic) 修飾子。

- 宣言されたメソッド、 `extern` (`Declare` Visual Basic でのステートメント) 修飾子。

## <a name="rule-description"></a>規則の説明

それらにアクセスする障害が回避の正確性が存在しないかどうかを確認するメソッドの本体で使用されていない非仮想メソッドのパラメーターを確認します。 使用されていないパラメーターには、メンテナンスとパフォーマンスのコストが発生します。

この規則違反は、メソッドの実装に関するバグをポイントできます。 たとえば、パラメーターがメソッドの本体で使用されているがする必要があります。 パラメーターに旧バージョンと互換性のために存在する場合は、この規則の警告を抑制します。

## <a name="how-to-fix-violations"></a>違反の修正方法

このルールの違反を修正するには、未使用のパラメーター (重大な変更) を削除またはメソッドの本体 (互換性に影響しない変更) で、パラメーターを使用します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

このルールから警告を抑制しても安全です。

- 以前にリリース済みのコード修正が重大な変更になります。

- `this`のカスタム拡張メソッドのパラメーター<xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=nameWithType>します。 内の関数、<xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>にアクセスする必要がないクラスが静的では、`this`メソッドの本体でのパラメーター。

## <a name="example"></a>例

次の例では、2 つの方法を示します。 1 つのメソッドには、ルールに違反しているし、他のメソッドは、ルールを満たします。

[!code-csharp[FxCop.Usage.ReviewUnusedParameters#1](../code-quality/codesnippet/CSharp/ca1801-review-unused-parameters_1.cs)]

## <a name="related-rules"></a>関連するルール

[CA1811:呼び出されていないプライベート コードを避ける](../code-quality/ca1811-avoid-uncalled-private-code.md)

[CA1812:インスタンス化されていない内部クラスを回避します。](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

[CA 1804:使用されていないローカルを削除します](../code-quality/ca1804-remove-unused-locals.md)