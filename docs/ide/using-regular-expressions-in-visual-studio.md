---
title: '[正規表現を使用する]'
ms.date: 03/26/2018
ms.topic: conceptual
f1_keywords:
- vsregularexpressionhelp
- vs.regularexpressionhelp
- vs.wildcardsbuilder
- vs.netregularexpressionhelp
- vs.wildcards
helpviewer_keywords:
- regular expressions [Visual Studio]
- regular expressions
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c4e461fd69e048e406fbe062ff297da9baab3696
ms.sourcegitcommit: 8562a337cc9f674c756a4a0b2c7e288ebd61b51e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345751"
---
# <a name="use-regular-expressions-in-visual-studio"></a>Visual Studio での正規表現の使用

Visual Studio は、テキストの検索と置換をするときに、[.NET Framework の正規表現](/dotnet/standard/base-types/regular-expressions)を使います。

## <a name="regular-expression-examples"></a>正規表現の例

次の表では、正規表現の文字、演算子、コンストラクト、およびパターンの例をいくつか示します。 詳細なリファレンスについては、[正規表現言語](/dotnet/standard/base-types/regular-expression-language-quick-reference)に関する記事をご覧ください。

|目的|正規表現|例|
|-------------|----------------|-------------|
|(改行を除く) 任意の 1 文字に一致します。 詳細については、「[任意の文字](/dotnet/standard/base-types/character-classes-in-regular-expressions#any-character-)」を参照してください。|.|`a.o` は、"around" の "aro" および "about" の "abo" には一致しますが、"across" の "acro" には一致しません。|
|直前の正規表現の 0 回以上の繰り返しに一致します (一致する文字列の長さを最大限にします)。 詳しくは、「[0 回以上の繰り返しに一致](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-zero-or-more-times-)」をご覧ください。|*|`a*r` は、"rack" の中の "r"、"ark" の中の "ar"、"aardvark" の中の "aar" に一致します。|
|0 回以上の任意の文字に一致します (ワイルドカード \*)|.*|`c.*e` は、"racket" の中の "cke"、"comment" の中の "comme"、"code" の中の "code" に一致します。|
|直前の正規表現の 1 回以上の繰り返しに一致します (一致する文字列の長さを最大限にします)。 詳しくは、「[1 回以上の繰り返しに一致](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-one-or-more-times-)」をご覧ください。|+|`e.+d` は、"feeder" の中の "eed" に一致しますが、"ed" には一致しません。|
|1 回以上の任意の文字に一致します (ワイルドカード ?)|.+|`e.+e` は、"feeder" の中の "eede" に一致しますが、"ee" には一致しません。|
|直前の正規表現の 0 回以上の繰り返しに一致します (一致する文字列の長さを最小限にします)。 詳しくは、「[0 回以上の繰り返しに一致 (最短一致)](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-zero-or-more-times-lazy-match-)」をご覧ください。|*?|`e.*?e` は、"feeder" の中の "ee" に一致しますが、"eede" には一致しません。|
|直前の正規表現の 1 回以上の繰り返しを検索します (一致する文字列の長さを最小限にします)。 詳しくは、「[1 回以上の繰り返しに一致 (最短一致)](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-one-or-more-times-lazy-match-)」をご覧ください。|+?|`e.+?e` は、"enterprise" 中の "ente" および "erprise" には一致しますが、単語全体 "enterprise" には一致しません。|
|一致文字列を、[行頭または文字列の先頭](/dotnet/standard/base-types/anchors-in-regular-expressions#start-of-string-or-line-)に固定します|^|`^car` は、単語 "car" が行の先頭に登場する場合のみ、その単語に一致します。|
|一致文字列を、[行末](/dotnet/standard/base-types/anchors-in-regular-expressions#end-of-string-or-line-)に固定します|\r?$|`end\r?$` は、"end" が行末に登場する場合のみ、その単語に一致します。|
|一致文字列を、ファイルの末尾に固定します。|$|`end$` は、"end" がファイルの末尾に登場する場合のみ、その単語に一致します。|
|セット内の任意の 1 文字と一致します。|[abc]|`b[abc]` は、"ba"、"bb"、および "bc" に一致します。|
|範囲内の任意の文字に一致します|[a-f]|`be[n-t]` は、"between" の中の "bet"、"beneath" の中の "ben"、および "beside" の中の "bes" には一致しますが、"below" の中の "bel" には一致しません。|
|かっこで囲まれた表現を 1 つのまとまりとして扱い、その表現に対して暗黙的に番号を付けます。|()|`([a-z])X\1` は、"aXa" および "bXb" に一致しますが、"aXb" には一致しません。 "\1"は、最初の表現グループ "[a-z]" を指します。 詳しくは、「[キャプチャ グループと置換パターン](#capture-groups-and-replacement-patterns)」をご覧ください。 |
|一致を否定します。|(?!abc)|`real(?!ity)` は、"realty" や "really" の中の "real" に一致しますが、"reality" の中の "real" には一致しません。 また、"realityreal" の中の 2 番目の "real" に一致します (一方、最初の "real" には一致しません)。|
|指定された一連の文字の中に含まれていない任意の文字と一致します。 詳細については、「[文字グループの否定](/dotnet/standard/base-types/character-classes-in-regular-expressions#negative-character-group-)」を参照してください。|[^abc]|`be[^n-t]` は、"before" の中の "bef"、"behind" の中の "beh"、および "below" の中の "bel" に一致しますが、"beneath" の中の "ben" には一致しません。|
|記号の前にある表現、または後にある表現のいずれかに一致します|&#124;|`(sponge\|mud) bath` は "sponge bath" および "mud bath" に一致します。|
|円記号の後の[文字をエスケープ処理](/dotnet/standard/base-types/character-escapes-in-regular-expressions)します| \\ |`\^` は、^ 文字に一致します。|
|直前の文字またはグループが登場する回数を指定します。 詳しくは、「[n 回の繰り返しに一致](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-exactly-n-times-n)」をご覧ください。|{n}、ここで "n" は登場する回数です|`x(ab){2}x` は "xababx" に一致し、`x(ab){2,3}x` は "xababx" および "xabababx" に一致しますが、"xababababx" には一致しません。|
|[Unicode カテゴリに含まれるテキストに一致します](/dotnet/standard/base-types/character-classes-in-regular-expressions#unicode-category-or-unicode-block-p)。 Unicode 文字クラスについて詳しくは、Unicode Standard 5.2 の「[Character Properties (文字プロパティ)](http://www.unicode.org/versions/Unicode5.2.0/ch04.pdf)」をご覧ください。|\p{X}、ここで "X" は Unicode 番号です。|`\p{Lu}` は "Thomas Doe" の中の "T" および "D" に一致します。|
|[ワード境界に一致します](/dotnet/standard/base-types/anchors-in-regular-expressions#word-boundary-b)|\b (文字クラス `\b` の外部にあるときはワード境界を指定し、文字クラス `\b` の内部にあるときはバックスペースを指定します)。|`\bin` は、"inside" の中の "in" と一致しますが、"pinto" には一致しません。|
|改行 (つまり、キャリッジ リターンとそれに続く新しい行) に一致します|\r?\n|`End\r?\nBegin` は、"End" が行の最後の文字列で、"Begin" が次の行の先頭の文字列である場合のみ、単語 "End" と "Begin" に一致します。|
|[単語に使用される任意の文字](/dotnet/standard/base-types/character-classes-in-regular-expressions#word-character-w)と一致します|\w|`a\wd` は、"add" および "a1d" に一致しますが、"a d" には一致しません。|
|任意の[空白文字](/dotnet/standard/base-types/character-classes-in-regular-expressions#whitespace-character-s)と一致します|\s|`Public\sInterface` は、語句 "Public Interface" に一致します。|
|任意の [10 進数字](/dotnet/standard/base-types/character-classes-in-regular-expressions#decimal-digit-character-d)と一致します|\d|`\d` は、"3456" の中の "3"、"23" の中の "2"、および "1" の中の "1" に一致します。|
|Unicode 文字に一致します。|\uXXXX、ここで XXXX は、Unicode 文字の値を指定します。|`\u0065` は、^ 文字に一致します。|
|識別子に一致します|\b[\_\w-[0-9]][\_\w]*\b|"type1" に一致しますが、"&type1" や "#define" には一致しません。|
|引用符の内側にある文字列と一致します|((\\".+?\\")&#124;('.+?'))|単一引用符または二重引用符の内部にある任意の文字列に一致します。|
|16 進数に一致します|\b0[xX]([0-9a-fA-F]+\)\b|"0xc67f" と一致しますが、"0xc67g" とは一致しません。|
|整数と小数に一致します|\b[0-9]*\\.\*[0-9]+\b|"1.333" に一致します。|

> [!TIP]
> Windows オペレーティング システムでは、ほとんどの行は、"\r\n" (キャリッジ リターンと、それに続く新しい行) で終わります。 これらの文字は表示されませんが、エディターの中に存在し、.NET の正規表現のサービスに渡されます。

## <a name="capture-groups-and-replacement-patterns"></a>キャプチャ グループと置換パターン

キャプチャ グループは、正規表現の部分式を示し、入力文字列の部分文字列をキャプチャします。 キャプチャされたグループは、正規表現自体の内部 (たとえば、繰り返される単語を探す)、または置換パターン内で使用できます。 詳細については、「[正規表現でのグループ化構成体](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions)」を参照してください。

番号付きキャプチャ グループを作成するには、正規表現パターンにおいて部分式をかっこで囲みます。 キャプチャには、正規表現の左かっこの位置に基づいて、左から右に自動的に番号が付けられます。 キャプチャされたグループにアクセスするには:

- **正規表現内**: `\number` を使用してください。 たとえば、正規表現 `(\w+)\s\1` 内の `\1` は、最初のキャプチャ グループ `(\w+)` を参照します。

- **置換パターン内**: `$number` を使用してください。 たとえば、グループ化された正規表現 `(\d)([a-z])` では、2 つのグループが定義されています。1 番目のグループには 1 つの 10 進数字が含まれ、2 番目のグループには **a** から **z** の 1 つの文字が含まれます。 この式では、**1a 3c 2b 4d** という文字列の中で、4 つの一致が見つかります。 置換文字列 `z$1` は最初のグループのみ (`$1`) を参照し、この文字列を **z1 z2 z3 z4** に変換します。

次の図では、正規表現 `(\w+)\s\1` と置換文字列 `$1` を示します。 正規表現と置換パターンの両方で、番号 1 が自動的に付けられた最初のキャプチャ グループが参照されます。 Visual Studio の **[クイック置換]** ダイアログ ボックスで **[すべて置換]** を選択すると、繰り返されている単語がテキストから削除されます。

![Visual Studio の番号付きキャプチャ グループが示されている [クイック置換]](media/numbered-capture-group.png)

> [!TIP]
> **[クイック置換]** ダイアログ ボックスで **[正規表現を使用する]** ボタンが選択されていることを確認します。

### <a name="named-capture-groups"></a>名前付きキャプチャ グループ

キャプチャ グループの自動番号付けに頼るのではなく、自分で名前を指定できます。 名前付きキャプチャ グループの構文は、`(?<name>subexpression)` です。

名前付きキャプチャ グループは、番号付きキャプチャ グループと同じように、正規表現自体内または置換パターン内で使用できます。 名前付きキャプチャ グループにアクセスするには:

- **正規表現内**: `\k<name>` を使用してください。 たとえば、正規表現 `(?<repeated>\w+)\s\k<repeated>` 内の `\k<repeated>` は、名前が `repeated` で部分式が `\w+` であるキャプチャ グループを参照します。

- **置換パターン内**: `${name}` を使用してください。 たとえば、`${repeated}` のようにします。

たとえば、次の図では、正規表現 `(?<repeated>\w+)\s\k<repeated>` と置換文字列 `${repeated}` を示します。 正規表現と置換パターンの両方で、`repeated` という名前のキャプチャ グループが参照されます。 Visual Studio の **[クイック置換]** ダイアログ ボックスで **[すべて置換]** を選択すると、繰り返されている単語がテキストから削除されます。

![Visual Studio の名前付きキャプチャ グループが示されている [クイック置換]](media/named-capture-group.png)

> [!TIP]
> **[クイック置換]** ダイアログ ボックスで **[正規表現を使用する]** ボタンが選択されていることを確認します。

名前付きキャプチャ グループについて詳しくは、「[一致した名前付き部分式](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions#named-matched-subexpressions)」をご覧ください。 置換パターンで使われる正規表現について詳しくは、「[正規表現での置換](/dotnet/standard/base-types/substitutions-in-regular-expressions)」をご覧ください。

## <a name="see-also"></a>関連項目

- [正規表現言語](/dotnet/standard/base-types/regular-expression-language-quick-reference)
- [テキストの検索と置換](../ide/finding-and-replacing-text.md)
