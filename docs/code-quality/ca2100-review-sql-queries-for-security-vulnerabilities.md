---
title: CA2100:SQL クエリのセキュリティ脆弱性を確認
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- Review SQL queries for security vulnerabilities
- ReviewSqlQueriesForSecurityVulnerabilities
- CA2100
helpviewer_keywords:
- CA2100
- ReviewSqlQueriesForSecurityVulnerabilities
ms.assetid: 79670604-c02a-448d-9c0e-7ea0120bc5fe
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: b3ba92e154e3091f6ec483ba469c3fe60f50ec61
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "66744811"
---
# <a name="ca2100-review-sql-queries-for-security-vulnerabilities"></a>CA2100:SQL クエリのセキュリティ脆弱性を確認

|||
|-|-|
|TypeName|ReviewSqlQueriesForSecurityVulnerabilities|
|CheckId|CA2100|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因

メソッドの設定、<xref:System.Data.IDbCommand.CommandText%2A?displayProperty=fullName>プロパティ、メソッドに文字列の引数から構築された文字列を使用しています。

## <a name="rule-description"></a>規則の説明

この規則では、文字列引数にユーザー入力が含まれていることが想定されています。 ユーザー入力から構築された SQL コマンド文字列には、SQL 注入攻撃に対する脆弱性があります。 SQL インジェクション攻撃では、悪意のあるユーザーは、破損または基になるデータベースへの不正アクセスを確保するために、クエリのデザインを変更する入力を提供します。 標準的な方法は、単一引用符またはアポストロフィ、SQL リテラル文字列の区切り記号; の挿入2 つのダッシュは、SQL コメント; ことを示しますセミコロンでは、新しいコマンドが続くことを示します。 攻撃のリスクを軽減する効果の順序で表示されている場合、ユーザー入力は、次のいずれかを使用して、クエリの一部である必要があります。

- ストアド プロシージャを使用します。

- パラメーター化されたコマンド文字列を使用します。

- コマンド文字列をビルドする前に、型とコンテンツの両方のユーザー入力を検証します。

次の .NET 型の実装、<xref:System.Data.IDbCommand.CommandText%2A>プロパティまたは文字列引数を使用して、プロパティを設定するコンス トラクターを提供します。

- <xref:System.Data.Odbc.OdbcCommand?displayProperty=fullName> および <xref:System.Data.Odbc.OdbcDataAdapter?displayProperty=fullName>

- <xref:System.Data.OleDb.OleDbCommand?displayProperty=fullName> および <xref:System.Data.OleDb.OleDbDataAdapter?displayProperty=fullName>

- <xref:System.Data.OracleClient.OracleCommand?displayProperty=fullName> および <xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=fullName>

- <xref:System.Data.SqlClient.SqlCommand?displayProperty=fullName> および <xref:System.Data.SqlClient.SqlDataAdapter?displayProperty=fullName>

明示的または暗黙的に型の ToString メソッドを使用する場合に、この規則が違反したことに注意してください。 クエリ文字列を作成します。 次に例を示します。

```csharp
int x = 10;
string query = "SELECT TOP " + x.ToString() + " FROM Table";
```

悪意のあるユーザーは、ToString() メソッドをオーバーライドできるため、規則に違反します。

ルールもが破ら ToString を暗黙的に使用するとします。

```csharp
int x = 10;
string query = String.Format("SELECT TOP {0} FROM Table", x);
```

## <a name="how-to-fix-violations"></a>違反の修正方法

この規則違反を修正するには、パラメーター化クエリを使用します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

コマンド テキストでユーザー入力が含まれない場合は、この規則による警告を抑制するのには安全です。

## <a name="example"></a>例

次の例では、メソッド、 `UnsafeQuery`、ルールと、メソッドに違反する`SaferQuery`、パラメーター化されたコマンド文字列を使用して、ルールを満たします。

[!code-vb[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/VisualBasic/ca2100-review-sql-queries-for-security-vulnerabilities_1.vb)]
[!code-csharp[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CSharp/ca2100-review-sql-queries-for-security-vulnerabilities_1.cs)]
[!code-cpp[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CPP/ca2100-review-sql-queries-for-security-vulnerabilities_1.cpp)]

## <a name="see-also"></a>関連項目

- [セキュリティの概要](/dotnet/framework/data/adonet/security-overview)