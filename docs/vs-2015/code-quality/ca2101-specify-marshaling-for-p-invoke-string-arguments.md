---
title: CA2101:P/invoke 文字列引数に対してマーシャ リングを指定します |。Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyMarshalingForPInvokeStringArguments
- CA2101
helpviewer_keywords:
- CA2101
- SpecifyMarshalingForPInvokeStringArguments
ms.assetid: 9d1abfc3-d320-41e0-9f6e-60cefe6ffe1b
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 11916609f2efa9c0b6e208548ba51795bd276015
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "68154390"
---
# <a name="ca2101-specify-marshaling-for-pinvoke-string-arguments"></a>CA2101:P/Invoke 文字列引数に対してマーシャリングを指定します
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SpecifyMarshalingForPInvokeStringArguments|
|CheckId|CA2101|
|Category|Microsoft.Globalization|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 プラットフォーム呼び出しメンバーにより部分的に信頼された呼び出し元は、文字列パラメーターを持つし、文字列が明示的にマーシャ リングされません。

## <a name="rule-description"></a>規則の説明
 Unicode から ANSI に変換することが特定の ANSI コード ページですべての Unicode 文字を表現できることができます。 *最適マッピング*の文字を表現できない文字に置き換えることによってこの問題を解決しようとしています。 選択されている文字は制御できないため、この機能の使用にはセキュリティの脆弱性を潜在的な可能性があります。 たとえば、悪意のあるコードをなど、ファイル システムの特殊文字に変換されます、特定のコード ページではない文字を含む Unicode 文字列に意図的に作成 '… ' または '/'。 特殊文字のセキュリティ チェックは、文字列が ANSI に変換される前に頻繁に発生することにも注意してください。

 最適マッピングでは、非管理対象の変換では、バイトを WChar の既定値です。 最適マッピングを明示的に無効にした場合を除き、コードはこの問題のため、悪用可能なセキュリティの脆弱性を含む可能性があります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、文字列データ型を明示的にマーシャ リングします。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、この規則に違反し、違反を修正する方法を示しますメソッドを示します。

 [!code-csharp[FxCop.Security.PinvokeAnsiUnicode#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PinvokeAnsiUnicode/cs/FxCop.Security.PinvokeAnsiUnicode.cs#1)]
