---
title: 名前付けに関する警告
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.namingrules
helpviewer_keywords:
- managed code analysis warnings, naming warnings
- naming warnings
- warnings, naming
ms.assetid: f97223ce-1d39-4134-81c9-fff2c75d979b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 90bdc70a2de900d43831994aff72e25031241cc3
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "66715306"
---
# <a name="naming-warnings"></a>名前付けに関する警告

名前付けの警告は、.NET デザイン ガイドラインの名前付け規則への準拠をサポートします。

## <a name="in-this-section"></a>このセクションの内容

|ルール|説明|
|----------|-----------------|
|[CA1700:列挙値 'Reserved' という名前しない操作を行います](../code-quality/ca1700-do-not-name-enum-values-reserved.md)|この規則では、"reserved" を含む名前の列挙体のメンバーは、現在使用されていなくても、将来的なバージョンでは名前を変更するか削除されるプレースホルダーと想定しています。 メンバーの名前変更や削除は、互換性に影響する変更点です。|
|[CA1713:Before または after プレフィックス イベントのないです。](../code-quality/ca1713-events-should-not-have-before-or-after-prefix.md)|イベント名が "Before" または "After" で始まっています。 特定のシーケンスで発生する関連イベントに名前を付ける場合、現在時制または過去時制を使用して、アクション シーケンスの相対的な位置を示します。|
|[CA1714:フラグ列挙型が複数形の名前](../code-quality/ca1714-flags-enums-should-have-plural-names.md)|パブリック列挙体に System.FlagsAttribute 属性と、その名前が"s"で終わっていません。 FlagsAttribute でマークされている型は、属性が 1 つ以上の値を指定できることを示しているために、複数形の名前があります。|
|[CA 1704:識別子は正しく入力されなければなりません](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)|外部から参照できる識別子の名前に Microsoft スペル チェック ライブラリで認識されない語が 1 つ以上含まれています。|
|[CA1708:識別子は、ケース以外で相違させる必要があります。](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)|名前空間、型、メンバー、およびパラメーターの各識別子は、大文字/小文字以外のみでは区別できません。共通言語ランタイムを対象とする言語は、大文字と小文字を区別する必要はないためです。|
|[CA1715:識別子は正しいプレフィックスをいなければなりません](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)|外部から参照できるインターフェイスの名前の先頭が大文字の"I"でありません。  外部から参照できる型またはメソッドのジェネリック型パラメーターの名前は、大文字の"T"は開始されません。|
|[CA 1720:識別子は型名を含めることはできません。](../code-quality/ca1720-identifiers-should-not-contain-type-names.md)|外部から参照できるメンバーのパラメーター名にデータ型の名前が含まれているか、外部から参照できるメンバーの名前に言語固有のデータ型の名前が含まれています。|
|[CA1722:識別子には、不適切なプレフィックスはありません。](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)|規則では、特定のプログラミング要素にのみ、固有のプレフィックスで始まる名前を付けることができます。|
|[CA1711:識別子には、不適切なサフィックスはありません。](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)|規則では、特定の基本型を拡張する型、特定のインターフェイスを実装する型、またはそのような型から派生した型の名前にのみ、固有の予約済みサフィックスを末尾に付けます。 その他の型名では、予約済みのサフィックスを使用しないでください。|
|[CA1717:FlagsAttribute 列挙のみが複数形の名前](../code-quality/ca1717-only-flagsattribute-enums-should-have-plural-names.md)|名前付け規則では、列挙体の複数形の名前は同時に複数の列挙値を指定できることを意味します。|
|[CA1725:パラメーター名は基本宣言と一致する必要があります。](../code-quality/ca1725-parameter-names-should-match-base-declaration.md)|オーバーライド階層のパラメーターに対する一貫性のある名前付けによって、メソッド オーバーライドの有用性が高まります。 派生メソッドのパラメーター名が基本宣言のパラメーター名と異なる場合、メソッドが基本メソッドのオーバーライドであるか、またはメソッドの新しいオーバーライドであるかについて混乱が生じる可能性があります。|
|[CA1719:パラメーター名は、メンバー名と一致する必要があります。](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)|パラメーター名、パラメーターの意味を伝えるし、メンバー名は、メンバーの意味を伝える必要があります。 この 2 つの名前が一致するデザインは、まれにしか見られません。 パラメーターにメンバーと同じ名前を付けるとわかりづらくなり、ライブラリの操作が難しくなります。|
|[CA1701:リソース文字列の複合語では、大文字と小文字が正しく区別する必要があります。](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)|リソース文字列内の各単語は、大文字と小文字に基づいてトークンに分割されます。 Microsoft スペル チェック ライブラリは、隣接する 2 つのトークンの組み合わせを個別にチェックします。 それらが認識されると、その語はこの規則への違反となります。|
|[CA 1703:リソース文字列を正しく入力されなければなりません](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)|リソース文字列に Microsoft スペル チェック ライブラリで認識されない語が 1 つ以上含まれています。|
|[CA1724:型名が名前空間と一致する必要があります。](../code-quality/ca1724-type-names-should-not-match-namespaces.md)|型名は、.NET 名前空間の名前と一致する必要があります。 この規則違反は、ライブラリの使いやすさを減らすことができます。|
|[CA 1707:識別子はアンダー スコアを含めることはできません。](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)|名前付け規則では、識別子名にアンダースコア (_) 文字を含めることができません。 この規則により、名前空間、型、メンバー、およびパラメーターがチェックされます。|
|[CA1721:プロパティ名は、get メソッドと一致する必要があります。](../code-quality/ca1721-property-names-should-not-match-get-methods.md)|パブリック メンバーまたはプロテクト メンバーの名前が、"Get" から始まっているか、パブリック プロパティまたはプロテクト プロパティの名前と一致します。 "Get" メソッドとプロパティには、それぞれの機能を明確に区別する名前を指定しなければなりません。|
|[CA1716:識別子は、キーワードと一致する必要があります。](../code-quality/ca1716-identifiers-should-not-match-keywords.md)|名前空間の名前または型の名前が、プログラミング言語で、予約済みのキーワードと一致します。 名前空間と型の識別子は、共通言語ランタイムを対象にする言語で定義されているキーワードと一致しないようにします。|
|[CA 1726: 適切な。用語を使用します](../code-quality/ca1726-use-preferred-terms.md)|外部から参照可能な識別子の名前に含まれている用語に対応する、別の推奨される用語があります。 あるいは、名前に "Flag" または "Flags" という語が含まれています。|
|[CA 1709:識別子では、大文字と小文字が正しく区別する必要があります。](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)|慣例により、パラメーター名は camel 形式の大文字小文字の区別、および名前空間、型を使用して、メンバー名は pascal 形式を使用して大文字小文字の区別します。|
|[CA1702:複合語では、大文字と小文字が正しく区別する必要があります。](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)|識別子の名前に複数の語が含まれており、大文字と小文字が正しく使い分けられていない複合語が 1 つ以上あります。|
|[CA 1712:列挙型の値を型名のプレフィックスにしません](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)|列挙型メンバーの名前は、開発ツールが提供する型情報が予想されるため、型名でが付きますされません。|
|[CA1710:識別子は、正しいサフィックスをいなければなりません](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)|慣例により、特定の基本型を拡張するか、特定のインターフェイス、またはこれらの型から派生した型を実装する型の名前には、基本データ型またはインターフェイスに関連付けられているサフィックスを持ちます。|