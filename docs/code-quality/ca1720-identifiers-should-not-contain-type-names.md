---
title: CA1720:識別子には型名を含めないでください
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1720
- IdentifiersShouldNotContainTypeNames
helpviewer_keywords:
- IdentifiersShouldNotContainTypeNames
- CA1720
ms.assetid: c95ee48f-f23a-45f0-ac9e-a3c1ecfabdea
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a35bec2395ccec649443df71e87904c71bf635d8
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547097"
---
# <a name="ca1720-identifiers-should-not-contain-type-names"></a>CA1720:識別子には型名を含めないでください

|||
|-|-|
|TypeName|IdentifiersShouldNotContainTypeNames|
|CheckId|CA1720|
|Category|Microsoft.Naming|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因

メンバー内のパラメーターの名前にデータ型の名前が含まれています。

\- または -

メンバーの名前には、言語固有のデータ型名が含まれています。

既定では、この規則は外部から参照できるメンバーだけを参照しますが、これは[構成可能](#configurability)です。

## <a name="rule-description"></a>規則の説明

パラメーターとメンバーの名前は、開発ツールによって提供されると予想される型を記述するよりも、その意味を伝えるために使用する方が適切です。 メンバーの名前については、データ型名を使用する必要がある場合は、言語固有の名前ではなく、言語に依存しない名前を使用します。 たとえば、 C#型名`int`の代わりに、言語に依存しないデータ型名を`Int32`使用します。

パラメーターまたはメンバーの名前に含まれる各個別トークンは、大文字と小文字を区別せずに、次の言語固有のデータ型名に対してチェックされます。

- Bool
- WChar
- Int8
- UInt8
- Short
- UShort
- Int
- UInt
- 整数型
- UInteger
- Long
- ULong
- 符号なし
- 符号付き
- Float
- Float32
- Float64

さらに、パラメーターの名前は、大文字と小文字を区別せずに、次の言語に依存しないデータ型名に対してもチェックされます。

- Object
- Obj
- ブール型
- Char
- String
- SByte
- Byte
- UByte
- Int16
- UInt16
- Int32
- UInt32
- Int64
- UInt64
- IntPtr
- ポインター
- ポインター
- UInptr
- UPtr
- UPointer
- Single
- 倍精度浮動小数点型
- Decimal (10 進数型)
- GUID

## <a name="how-to-fix-violations"></a>違反の修正方法

**パラメーターに対してが発生した場合:**

パラメーターの名前に含まれるデータ型識別子を、その意味またはより汎用的な用語 (' value ' など) により適切に記述された用語で置き換えます。

**メンバーに対して起動される場合:**

メンバー名に含まれる言語固有のデータ型識別子を、その意味、言語に依存しないもの、または一般的な用語 (' value ' など) をより詳細に記述した用語で置き換えます。

## <a name="when-to-suppress-warnings"></a>警告を非表示にする場合

型ベースのパラメーターとメンバー名をときどき使用することが適切な場合があります。 ただし、新しい開発では、この規則による警告を抑制する必要がある既知のシナリオはありません。 以前に出荷されたライブラリについては、このルールからの警告を抑制することが必要になる場合があります。

## <a name="configurability"></a>かつ

この規則を[FxCop アナライザー](install-fxcop-analyzers.md) (レガシ分析ではなく) から実行している場合は、ユーザー補助に基づいて、この規則を実行するコードベースの部分を構成できます。 たとえば、パブリックでない API サーフェイスに対してのみルールを実行するように指定するには、プロジェクトの editorconfig ファイルに次のキーと値のペアを追加します。

```ini
dotnet_code_quality.ca1720.api_surface = private, internal
```

このオプションは、この規則、すべての規則、またはこのカテゴリのすべての規則 (名前付け) に対してのみ構成できます。 詳細については、「 [FxCop アナライザーの構成](configure-fxcop-analyzers.md)」を参照してください。

## <a name="related-rules"></a>関連するルール

- [CA1709識別子は正しく使用する必要があります](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708識別子の大文字と小文字の区別が異なる場合](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
- [CA1707識別子にアンダースコアを含めることはできません](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)
- [CA1719パラメーター名はメンバー名と同一にすることはできません](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)