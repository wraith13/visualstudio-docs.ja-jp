---
title: CA2242:NaN に対して正しくテスト |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TestForNaNCorrectly
- CA2242
helpviewer_keywords:
- CA2242
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 17a98ce3d213c5d9ae85bb5132a0a44e50112037
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142350"
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242:NaN に対して正しくテストします
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TestForNaNCorrectly|
|CheckId|CA2242|
|Category|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 式に対して値をテストする<xref:System.Single.NaN?displayProperty=fullName>または<xref:System.Double.NaN?displayProperty=fullName>します。

## <a name="rule-description"></a>規則の説明
 <xref:System.Double.NaN?displayProperty=fullName>、not 非数を表す場合、算術演算が定義されていない場合に発生します。 値の間で等しいかどうかをテストする任意の式と<xref:System.Double.NaN?displayProperty=fullName>は常に返します`false`します。 値の間の不等性をテストする任意の式と<xref:System.Double.NaN?displayProperty=fullName>は常に返します`true`します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正し、値を表すかどうかを正確に判断する<xref:System.Double.NaN?displayProperty=fullName>を使用して、<xref:System.Single.IsNaN%2A?displayProperty=fullName>または<xref:System.Double.IsNaN%2A?displayProperty=fullName>値をテストします。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、対応する値を正しくテストする 2 つの式<xref:System.Double.NaN?displayProperty=fullName>と正しく使用する式<xref:System.Double.IsNaN%2A?displayProperty=fullName>値をテストします。

 [!code-csharp[FxCop.Usage.TestForNaN#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/cs/FxCop.Usage.TestForNaN.cs#1)]
 [!code-vb[FxCop.Usage.TestForNaN#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/vb/FxCop.Usage.TestForNaN.vb#1)]
