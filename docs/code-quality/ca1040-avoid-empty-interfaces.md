---
title: CA1040:空のインターフェイスは使用しません
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1040
- AvoidEmptyInterfaces
helpviewer_keywords:
- AvoidEmptyInterfaces
- CA1040
ms.assetid: 120a741b-5fd1-4836-8453-7857e0cd0380
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 491923cb46100e9239b889024ade00022318b6cd
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547695"
---
# <a name="ca1040-avoid-empty-interfaces"></a>CA1040:空のインターフェイスは使用しません

|||
|-|-|
|TypeName|AvoidEmptyInterfaces|
|CheckId|CA1040|
|Category|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因

インターフェイスがメンバーを宣言していないか、2つ以上のインターフェイスを実装していません。

既定では、この規則は外部から参照できるインターフェイスだけを参照しますが、これは[構成可能](#configurability)です。

## <a name="rule-description"></a>規則の説明

インターフェイスには、動作や使用のコントラクトを実現するメンバーが定義されます。 インターフェイスで示される機能は、継承の階層構造内に型が存在するかどうかにかかわらず、どの型からも適用できます。 型ではインターフェイスのメンバーに実装することで、インターフェイスが実装されます。 空のインターフェイスでは、メンバーは定義されません。 そのため、実装できるコントラクトは定義されていません。

型に実装する必要がある空のインターフェイスが設計に含まれている場合は、通常、インターフェイスをマーカーとして使用するか、型のグループを識別する方法を使用します。 この id が実行時に発生する場合は、カスタム属性を使用することをお勧めします。 対象の型を特定するには、属性の有無、または属性のプロパティを使用します。 コンパイル時に id が発生する必要がある場合は、空のインターフェイスを使用できます。

## <a name="how-to-fix-violations"></a>違反の修正方法

インターフェイスを削除するか、またはそのインターフェイスにメンバーを追加します。 空のインターフェイスを使用して一連の型にラベルを付ける場合は、インターフェイスをカスタム属性に置き換えます。

## <a name="when-to-suppress-warnings"></a>警告を非表示にする場合

コンパイル時に型のセットを識別するためにインターフェイスを使用する場合は、この規則からの警告を抑制することが安全です。

## <a name="configurability"></a>かつ

この規則を[FxCop アナライザー](install-fxcop-analyzers.md) (レガシ分析ではなく) から実行している場合は、ユーザー補助に基づいて、この規則を実行するコードベースの部分を構成できます。 たとえば、パブリックでない API サーフェイスに対してのみルールを実行するように指定するには、プロジェクトの editorconfig ファイルに次のキーと値のペアを追加します。

```ini
dotnet_code_quality.ca1040.api_surface = private, internal
```

このオプションは、この規則、すべての規則、またはこのカテゴリのすべての規則 (デザイン) に対してのみ構成できます。 詳細については、「 [FxCop アナライザーの構成](configure-fxcop-analyzers.md)」を参照してください。

## <a name="example"></a>例

次の例は、空のインターフェイスを示しています。

[!code-csharp[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/CSharp/ca1040-avoid-empty-interfaces_1.cs)]
[!code-cpp[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/CPP/ca1040-avoid-empty-interfaces_1.cpp)]
[!code-vb[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/VisualBasic/ca1040-avoid-empty-interfaces_1.vb)]