---
title: CA1010:コレクションは、ジェネリック インターフェイスを実装する必要があります |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
helpviewer_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
ms.assetid: c7d7126f-fa70-40be-8f93-3243e1760dc5
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 930e80530b10449c0a2e0d740d97e20f4b0cc5b5
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704279"
---
# <a name="ca1010-collections-should-implement-generic-interface"></a>CA1010:コレクションは、ジェネリック インターフェイスを実装しなければなりません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CollectionsShouldImplementGenericInterface|
|CheckId|CA1010|
|Category|Microsoft.Design|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 外部から参照の型を実装して、<xref:System.Collections.IEnumerable?displayProperty=fullName>インターフェイスしますが、実装されません、<xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>インターフェイス、および含んでいるアセンブリのターゲット[!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)]します。 この規則を実装する型<xref:System.Collections.IDictionary?displayProperty=fullName>します。

## <a name="rule-description"></a>規則の説明
 コレクションの操作性を拡充するために、ジェネリック コレクション インターフェイスの 1 つを実装します。 次などのジェネリック コレクション型を設定するコレクションを使用できます。

- <xref:System.Collections.Generic.List%601?displayProperty=fullName>

- <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>

- <xref:System.Collections.Generic.Stack%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、次のジェネリック コレクション インターフェイスの 1 つを実装します。

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>

- <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>

- <xref:System.Collections.Generic.IList%601?displayProperty=fullName>

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告を抑制しても安全です。ただし、コレクションより限定的な使用があります。

## <a name="example-violation"></a>例の違反

### <a name="description"></a>説明
 次の例では、非ジェネリックから派生したクラス (参照型)`CollectionBase`クラスは、この規則に違反します。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Design.CollectionsGenericViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CollectionsGenericViolation/cs/FxCop.Design.CollectionsGenericViolation.cs#1)]

### <a name="comments"></a>コメント
 この規則違反を修正するのにする必要がありますジェネリック インターフェイスを実装するかを既になど両方、ジェネリックと非ジェネリック インターフェイスを実装する型に基本クラスを変更、`Collection<T>`クラス。

## <a name="fix-by-base-class-change"></a>基本クラスの変更を修正します。

### <a name="description"></a>説明
 次の例から、非ジェネリック コレクションの基本クラスを変更することで、違反を修正する`CollectionBase`クラスをジェネリック`Collection<T>`(`Collection(Of T)`で[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) クラス。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Design.CollectionsGenericBase#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CollectionsGenericBase/cs/FxCop.Design.CollectionsGenericBase.cs#1)]

### <a name="comments"></a>コメント
 リリース済みのクラスの基本クラスを変更すると、既存のコンシューマーに重大な変更と見なされます。

## <a name="fix-by-interface-implementation"></a>インターフェイスの実装を修正します。

### <a name="description"></a>説明
 次の例では、これらのジェネリック インターフェイスを実装することで、違反を修正する: `IEnumerable<T>`、 `ICollection<T>`、および`IList<T>`(`IEnumerable(Of T)`、 `ICollection(Of T)`、および`IList(Of T)`で[!INCLUDE[vbprvb](../includes/vbprvb-md.md)])。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Design.CollectionsGenericInterface#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CollectionsGenericInterface/cs/FxCop.Design.CollectionsGenericInterface.cs#1)]

## <a name="related-rules"></a>関連規則
 [CA1005:ジェネリック型で過剰なパラメーターを回避します。](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA 1000:ジェネリック型で静的メンバーを宣言しません](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA 1002:ジェネリック リストを公開しません](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA 1006:ジェネリック型メンバー シグネチャ内で入れ子にしません](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA 1004:ジェネリック メソッドは、型パラメーターを指定する必要があります。](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA 1003:汎用イベント ハンドラーのインスタンスを使用して、](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA 1007:適切な場所にジェネリックを使用します。](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>関連項目
 [ジェネリック](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
