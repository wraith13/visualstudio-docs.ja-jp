---
title: CA2216:破棄可能な型はファイナライザーを宣言する必要があります |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DisposableTypesShouldDeclareFinalizer
- CA2216
helpviewer_keywords:
- CA2216
- DisposableTypesShouldDeclareFinalizer
ms.assetid: 0cabcc5e-b526-452b-8c2a-0cbe3b93c0ef
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8a033dbb152542e528b32e26f35a7d63dba30891
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65681164"
---
# <a name="ca2216-disposable-types-should-declare-finalizer"></a>CA2216:破棄可能な型はファイナライザーを宣言しなければなりません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DisposableTypesShouldDeclareFinalizer|
|CheckId|CA2216|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 実装する型<xref:System.IDisposable?displayProperty=fullName>、およびアンマネージ リソースの使用を提案するフィールドを持つ、による記述では、ファイナライザーを実装しません<xref:System.Object.Finalize%2A?displayProperty=fullName>します。

## <a name="rule-description"></a>規則の説明
 破棄可能な型には、次の種類のフィールドが含まれている場合は、この規則違反が報告されます。

- <xref:System.IntPtr?displayProperty=fullName>

- <xref:System.UIntPtr?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、実装を呼び出すファイナライザー、<xref:System.IDisposable.Dispose%2A>メソッド。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 型が実装していない場合、この規則による警告を抑制するのには安全では<xref:System.IDisposable>アンマネージ リソースを解放するためにします。

## <a name="example"></a>例
 次の例では、この規則に違反する型を示します。

 [!code-csharp[FxCop.Usage.DisposeNoFinalize#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DisposeNoFinalize/cs/FxCop.Usage.DisposeNoFinalize.cs#1)]

## <a name="related-rules"></a>関連規則
 [CA 2115:GC を呼び出します。KeepAlive ネイティブ リソースを使用する場合](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

 [CA 1816:GC を呼び出します。SuppressFinalize 正しく](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

 [CA 1049:ネイティブ リソースを所有する型は、破棄可能でなければなりません](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)

## <a name="see-also"></a>関連項目
 <xref:System.IDisposable?displayProperty=fullName> <xref:System.IntPtr?displayProperty=fullName>
 <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>
 <xref:System.UIntPtr?displayProperty=fullName>
 <xref:System.Object.Finalize%2A?displayProperty=fullName>
 [Dispose パターン](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
