---
title: CA1309:順序を示す StringComparison を使用します
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UseOrdinalStringComparison
- CA1309
helpviewer_keywords:
- UseOrdinalStringComparison
- CA1309
ms.assetid: 19be0854-cb6e-4efd-a4c8-a5c1fc6f7a71
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2c528266c54bbb2f3f0d9420461d700a46b09bd5
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922281"
---
# <a name="ca1309-use-ordinal-stringcomparison"></a>CA1309:順序を示す StringComparison を使用します

|||
|-|-|
|TypeName|UseOrdinalStringComparison|
|CheckId|CA1309|
|Category|Microsoft のグローバリゼーション|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因

非言語的な文字列比較操作では、 <xref:System.StringComparison>パラメーターは**序数**または**stringcomparison.ordinalignorecase**に設定されません。

## <a name="rule-description"></a>規則の説明
多くの<xref:System.String.Compare%2A?displayProperty=fullName>文字列操作 (最も重要な<xref:System.String.Equals%2A?displayProperty=fullName>メソッドとメソッド) は、列挙値を<xref:System.StringComparison?displayProperty=fullName>パラメーターとして受け取るオーバーロードを提供するようになりました。

Stringcomparison.ordinalignorecase または**stringcomparison.** のいずれかを指定すると、文字列比較は非言語化になります。 つまり、比較の決定が行われると、自然言語に固有の機能は無視されます。 自然言語機能を無視すると、決定は単純なバイト比較に基づいて行われます。これは、カルチャによってパラメーター化された大文字と小文字の区別や同等のテーブルではありません 結果として、パラメーターを**Stringcomparison. Ordinal**または**stringcomparison.ordinalignorecase**のいずれかに明示的に設定すると、コードの速度が向上し、正確性が向上し、信頼性も高くなります。

## <a name="how-to-fix-violations"></a>違反の修正方法
この規則違反を修正するには、文字列比較メソッドをパラメーターとして<xref:System.StringComparison?displayProperty=fullName>列挙型を受け入れるオーバーロードに変更し、 **Ordinal**または**stringcomparison.ordinalignorecase**を指定します。 たとえば、`String.Compare(str1, str2)` を `String.Compare(str1, str2, StringComparison.Ordinal)` に変更します。

## <a name="when-to-suppress-warnings"></a>警告を非表示にする場合
ライブラリまたはアプリケーションが限定されたローカルユーザーを対象としている場合、または現在のカルチャのセマンティクスを使用する必要がある場合は、この規則からの警告を抑制することが安全です。

## <a name="see-also"></a>関連項目

- [グローバリゼーションに関する警告](../code-quality/globalization-warnings.md)
- [CA1307StringComparison の指定](../code-quality/ca1307-specify-stringcomparison.md)