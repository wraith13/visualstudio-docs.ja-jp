---
title: CA2114:メソッド セキュリティは型のスーパーセットでなければなりません
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MethodSecurityShouldBeASupersetOfType
- CA2114
helpviewer_keywords:
- CA2114
- MethodSecurityShouldBeASupersetOfType
ms.assetid: 663f7aa4-8be5-4bd5-be92-4e9444f07077
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d83da42a029d746899bfaccf5d62f8856a040611
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921114"
---
# <a name="ca2114-method-security-should-be-a-superset-of-type"></a>CA2114:メソッド セキュリティは型のスーパーセットでなければなりません

|||
|-|-|
|TypeName|MethodSecurityShouldBeASupersetOfType|
|CheckId|CA2114|
|Category|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
型には宣言セキュリティがあり、そのメソッドの1つには同じセキュリティアクションの宣言セキュリティがあり、セキュリティアクションは[リンク確認要求](/dotnet/framework/misc/link-demands)ではなく、型によってチェックされるアクセス許可は、メソッドによってチェックされるアクセス許可のサブセットではありません。

## <a name="rule-description"></a>規則の説明
メソッドは、同じアクションに対して、メソッドレベルと型レベルの宣言セキュリティの両方を持つことはできません。 2つのチェックは結合されません。メソッドレベルの要求だけが適用されます。 たとえば、型がアクセス`X`許可を要求し、そのメソッドの1つがアクセス許可`Y`を要求する場合、コードに`X`はメソッドを実行するアクセス許可が必要ありません。

## <a name="how-to-fix-violations"></a>違反の修正方法
コードを確認して、両方のアクションが必要であることを確認します。 両方のアクションが必要な場合は、メソッドレベルのアクションに、型レベルで指定されたセキュリティが含まれていることを確認してください。 たとえば、 `X`型がアクセス許可を要求し、そのメソッドがアクセス許可`Y`を要求する必要がある場合、 `Y`メソッドはとを明示的に要求`X`する必要があります。

## <a name="when-to-suppress-warnings"></a>警告を非表示にする場合
メソッドが型によって指定されたセキュリティを必要としない場合は、この規則による警告を抑制しても安全です。 ただし、これは通常のシナリオではなく、慎重な設計レビューが必要であることを示している可能性があります。

## <a name="example-1"></a>例 1

次の例では、環境のアクセス許可を使用して、この規則に違反する危険性を示します。 この例では、アプリケーションコードは、型に必要なアクセス許可を拒否する前に、セキュリティで保護された型のインスタンスを作成します。 実際の脅威のシナリオでは、アプリケーションでオブジェクトのインスタンスを取得する別の方法が必要になります。

次の例では、ライブラリは、型に対する書き込みアクセス許可と、メソッドに対する読み取りアクセス許可を要求します。

[!code-csharp[FxCop.Security.MethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_1.cs)]

## <a name="example-2"></a>例 2

次のアプリケーションコードは、型レベルのセキュリティ要件を満たしていない場合でも、メソッドを呼び出すことによって、ライブラリの脆弱性を示しています。

[!code-csharp[FxCop.Security.TestMethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_2.cs)]

この例を実行すると、次の出力が生成されます。

```txt
[All permissions] Personal information: 6/16/1964 12:00:00 AM
[No write permission (demanded by type)] Personal information: 6/16/1964 12:00:00 AM
[No read permission (demanded by method)] Could not access personal information: Request failed.
```

## <a name="see-also"></a>関連項目

- [安全なコーディングのガイドライン](/dotnet/standard/security/secure-coding-guidelines)
- [リンク確認要求](/dotnet/framework/misc/link-demands)
- [データとモデリング](/dotnet/framework/data/index)