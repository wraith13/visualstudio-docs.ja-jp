---
title: CA2241:書式設定メソッドに正しい引数を提供
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2241
- Provide correct arguments to formatting methods
- ProvideCorrectArgumentsToFormattingMethods
helpviewer_keywords:
- ProvideCorrectArgumentsToFormattingMethods
- CA2241
ms.assetid: 83639bc4-4c91-4a07-a40e-dc5e49a84494
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 3bdb8ef315c9702cc10352368aba7202a8f29f7f
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920003"
---
# <a name="ca2241-provide-correct-arguments-to-formatting-methods"></a>CA2241:書式設定メソッドに正しい引数を提供

|||
|-|-|
|TypeName|ProvideCorrectArgumentsToFormattingMethods|
|CheckId|CA2241|
|Category|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
、、などのメソッドに渡された文字列引数に、各オブジェクト引数に対応する書式項目が含まれていません。また、その逆も同様です。`format` <xref:System.Console.Write%2A> <xref:System.Console.WriteLine%2A> <xref:System.String.Format%2A?displayProperty=fullName>

## <a name="rule-description"></a>規則の説明
<xref:System.Console.WriteLine%2A> <xref:System.Object?displayProperty=fullName> 、<xref:System.String.Format%2A> 、などのメソッドへの引数は、書式指定文字列の後に複数のインスタンスが続く形式で構成されます。 <xref:System.Console.Write%2A> 書式指定文字列は、{index [, alignment] [: formatString]} という形式のテキストと埋め込み書式項目で構成されます。 ' index ' は、どのオブジェクトを書式設定するかを示す、0から始まる整数です。 オブジェクトの書式指定文字列に対応するインデックスがない場合、オブジェクトは無視されます。 ' Index ' によって指定されたオブジェクトが存在<xref:System.FormatException?displayProperty=fullName>しない場合は、実行時にがスローされます。

## <a name="how-to-fix-violations"></a>違反の修正方法
この規則違反を修正するには、各オブジェクト引数に書式項目を指定し、各書式指定項目にオブジェクト引数を指定します。

## <a name="when-to-suppress-warnings"></a>警告を非表示にする場合
この規則による警告は抑制しないでください。

## <a name="example"></a>例
次の例は、規則の2つの違反を示しています。

[!code-vb[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/VisualBasic/ca2241-provide-correct-arguments-to-formatting-methods_1.vb)]
[!code-csharp[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/CSharp/ca2241-provide-correct-arguments-to-formatting-methods_1.cs)]