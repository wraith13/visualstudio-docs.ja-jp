---
title: CA2136:メンバーには、透過性注釈の競合があってはならない
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2127
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2136
helpviewer_keywords:
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2127
ms.assetid: ff5a1d18-7c52-4da5-8990-60be83a8ea81
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1dcef8fbfd61b8cd8c946f76d6fcb93dc46f1654
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920631"
---
# <a name="ca2136-members-should-not-have-conflicting-transparency-annotations"></a>CA2136:メンバーには、透過性注釈の競合があってはならない

|||
|-|-|
|TypeName|TransparencyAnnotationsShouldNotConflict|
|CheckId|CA2136|
|Category|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
この規則は、型のメンバーが、メンバーの<xref:System.Security>コンテナーのセキュリティ属性とは異なる透過性を持つセキュリティ属性でマークされている場合に適用されます。

## <a name="rule-description"></a>規則の説明
透過性属性は、大きいスコープのコード要素から小さいスコープの要素に適用されます。 大きいスコープのコード要素の透過性属性は、最初の要素に含まれているコード要素の透過性属性よりも優先されます。 たとえば、 <xref:System.Security.SecurityCriticalAttribute>属性でマークされたクラスには、 <xref:System.Security.SecuritySafeCriticalAttribute>属性でマークされたメソッドを含めることはできません。

## <a name="how-to-fix-violations"></a>違反の修正方法
この違反を修正するには、スコープが低いコード要素からセキュリティ属性を削除するか、属性を、含んでいるコード要素と同じになるように変更します。

## <a name="when-to-suppress-warnings"></a>警告を非表示にする場合
この規則からの警告を抑制しないでください。

## <a name="example"></a>例
次の例では、メソッドが<xref:System.Security.SecuritySafeCriticalAttribute>属性でマークされ、 <xref:System.Security.SecurityCriticalAttribute>属性でマークされたクラスのメンバーになっています。 セキュリティセーフ属性を削除する必要があります。

[!code-csharp[FxCop.Security.CA2136.TransparencyAnnotationsShouldNotConflict#1](../code-quality/codesnippet/CSharp/ca2136-members-should-not-have-conflicting-transparency-annotations_1.cs)]