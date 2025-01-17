---
title: CA2123:オーバーライドのリンク確認要求は基本同一である必要があります |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2123
- OverrideLinkDemandsShouldBeIdenticalToBase
helpviewer_keywords:
- OverrideLinkDemandsShouldBeIdenticalToBase
- CA2123
ms.assetid: 4538ecd5-fc6f-4480-ab00-90b2ce4730db
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 338d61db9c24972b7fef656498abd43f8ea0b976
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687223"
---
# <a name="ca2123-override-link-demands-should-be-identical-to-base"></a>CA2123:オーバーライドのリンク要求はベースと同一でなければなりません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverrideLinkDemandsShouldBeIdenticalToBase|
|CheckId|CA2123|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 パブリック型の public または protected のメソッドのメソッドをオーバーライドまたはインターフェイスを実装し、同じではありません[リンク確認要求](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)インターフェイスまたは仮想メソッドとします。

## <a name="rule-description"></a>規則の説明
 この規則は、メソッドをその基本メソッド (別の型のインターフェイスまたは仮想メソッド) とマッチングし、それぞれについてリンク確認要求を比較します。 メソッドまたは基本メソッドのいずれかがリンク確認要求し、もう一方にない場合は、違反が報告されます。

 この規則に違反すると、悪意のある呼び出し元は、保護されていないメソッドを呼び出すことによって単なるリンク確認要求をバイパスできます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、メソッドをオーバーライドまたは実装する同じリンク確認要求を適用します。 それができない場合は、完全な要求を持つメソッドをマークまたは属性をすべて削除します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、このルールのさまざまな違反を示します。

 [!code-csharp[FxCop.Security.OverridesAndSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.OverridesAndSecurity/cs/FxCop.Security.OverridesAndSecurity.cs#1)]

## <a name="see-also"></a>関連項目
 [安全なコーディングのガイドライン](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)[リンク確認要求](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)
