---
title: CA1059:メンバーは特定の具象型を公開できません
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1059
- MembersShouldNotExposeCertainConcreteTypes
helpviewer_keywords:
- MembersShouldNotExposeCertainConcreteTypes
- CA1059
ms.assetid: 59f61f52-8d6c-49cb-aefb-191910523a3c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3f24881d04599677c5d45c93fc940286f115d593
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922514"
---
# <a name="ca1059-members-should-not-expose-certain-concrete-types"></a>CA1059:メンバーは特定の具象型を公開できません

|||
|-|-|
|TypeName|MembersShouldNotExposeCertainConcreteTypes|
|CheckId|CA1059|
|Category|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
外部から参照できるメンバーは、特定の具象型であるか、そのパラメーターまたは戻り値のいずれかによって特定の具象型を公開します。 現在、このルールは次の具象型の露出を報告します。

- から<xref:System.Xml.XmlNode?displayProperty=fullName>派生した型。

## <a name="rule-description"></a>規則の説明
具象型は、完全な実装を含む型であるため、インスタンス化できます。 メンバーを広範囲に使用できるようにするには、具象型を提案されたインターフェイスに置き換えます。 これにより、インターフェイスを実装する任意の型をメンバーが受け入れることができるようになります。また、インターフェイスを実装する型が想定される場所で使用することもできます。

次の表に、対象となる具象型とその推奨される置換の一覧を示します。

|具象型|Replacement|
|-------------------|-----------------|
|<xref:System.Xml.XPath.XPathDocument>|<xref:System.Xml.XPath.IXPathNavigable?displayProperty=fullName>。<br /><br /> インターフェイスを使用すると、XML データソースの特定の実装からメンバーを分離できます。|

## <a name="how-to-fix-violations"></a>違反の修正方法
この規則違反を修正するには、具象型を提案されたインターフェイスに変更します。

## <a name="when-to-suppress-warnings"></a>警告を非表示にする場合
具象型によって提供される特定の機能が必要な場合は、この規則からのメッセージを抑制することが安全です。

## <a name="related-rules"></a>関連するルール
[CA1011基本型をパラメーターとして渡すことを検討してください](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)