---
title: CA1716:識別子はキーワードと同一にすることはできません
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
helpviewer_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9a51ac9509cf891c05166d46e4b72b862c0dc723
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547072"
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716:識別子はキーワードと同一にすることはできません

|||
|-|-|
|TypeName|IdentifiersShouldNotMatchKeywords|
|CheckId|CA1716|
|Category|Microsoft.Naming|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因

名前空間、型、または仮想メンバーまたはインターフェイスメンバーの名前は、プログラミング言語の予約されたキーワードと一致します。

既定では、この規則は外部から参照できる名前空間、型、およびメンバーのみを参照しますが、これは[構成可能](#configurability)です。

## <a name="rule-description"></a>規則の説明

名前空間、型、および仮想およびインターフェイスのメンバーの識別子は、共通言語ランタイムを対象とする言語で定義されているキーワードと一致させることはできません。 使用されている言語とキーワードによっては、ライブラリを使用するのが困難になることがあります。

このルールでは、次の言語のキーワードについて確認します。

- Visual Basic
- C#
- C++/CLI

Visual Basic キーワードには大文字と小文字を区別しない比較が使用され、その他の言語では大文字と小文字を区別する比較が使用されます。

## <a name="how-to-fix-violations"></a>違反の修正方法

キーワードの一覧に表示されない名前を選択してください。

## <a name="when-to-suppress-warnings"></a>警告を非表示にする場合

識別子が API のユーザーと混同しないこと、およびライブラリが .NET で使用可能なすべての言語で使用可能であることが確信できる場合は、この規則からの警告を抑制することができます。

## <a name="configurability"></a>かつ

この規則を[FxCop アナライザー](install-fxcop-analyzers.md) (レガシ分析ではなく) から実行している場合は、ユーザー補助に基づいて、この規則を実行するコードベースの部分を構成できます。 たとえば、パブリックでない API サーフェイスに対してのみルールを実行するように指定するには、プロジェクトの editorconfig ファイルに次のキーと値のペアを追加します。

```ini
dotnet_code_quality.ca1716.api_surface = private, internal
```

このオプションは、この規則、すべての規則、またはこのカテゴリのすべての規則 (名前付け) に対してのみ構成できます。 詳細については、「 [FxCop アナライザーの構成](configure-fxcop-analyzers.md)」を参照してください。