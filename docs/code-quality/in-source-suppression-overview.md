---
title: コード分析の警告を表示しない
ms.date: 12/01/2018
ms.topic: conceptual
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: 60fcb13c978d614d40964bd8d6da21e8cf41f00f
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551082"
---
# <a name="suppress-code-analysis-warnings"></a>コード分析の警告を表示しない

多くの場合、警告が適用されないことを示すと便利です。 これは、コードがレビューされたことと、警告を抑制できることをチームメンバーに示します。 ソース内抑制 (ISS) では、 <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>属性を使用して警告を抑制します。 属性は、警告を生成したコードセグメントの近くに配置できます。 <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>属性を入力してソースファイルに追加することも、**エラー一覧**の警告のショートカットメニューを使用して自動的に追加することもできます。

<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>属性は、コンパイル時に CODE_ANALYSIS コンパイルシンボルが定義されている場合にのみ、マネージコードアセンブリの IL メタデータに含まれる条件付き属性です。

/Cli C++では、マクロ\_CA\_の [メッセージを表示し\_ない] または [ca\_グローバル SUPPRESS_MESSAGE] をヘッダーファイルで使用して、属性を追加します。

> [!NOTE]
> ソース内の抑制メタデータが誤って配布されるのを防ぐために、リリースビルドでは、ソース内の抑制を使用しないでください。 また、ソース内抑制の処理コストが原因で、アプリケーションのパフォーマンスが低下する可能性があります。

> [!NOTE]
> プロジェクトを Visual Studio 2017 または Visual Studio 2019 に移行すると、コード分析の警告が多数発生する可能性があります。 警告を修正する準備ができていない場合は、[実行コード分析の**分析** > ]**を選択し、[アクティブな問題を抑制**する] を選択して、すべての警告を抑制できます。
>
> ![Visual Studio でコード分析を実行し、問題を抑制する](media/suppress-active-issues.png)

## <a name="suppressmessage-attribute"></a>SuppressMessage 属性

**エラー一覧**でコード分析の警告のコンテキストまたは右クリックメニューから [**抑制**] を選択すると、 <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>属性がコードまたはプロジェクトのグローバル抑制ファイルのいずれかに追加されます。

属性<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>の形式は次のとおりです。

```vb
<Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")>
```

```csharp
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]
```

```cpp
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")
```

属性のプロパティは次のとおりです。

- [**カテゴリ]** -ルールが定義されているカテゴリ。 コード分析規則のカテゴリの詳細については、「[マネージコードの警告](../code-quality/code-analysis-for-managed-code-warnings.md)」を参照してください。

- **Checkid** -ルールの識別子。 サポートには、規則識別子の短い名前と長い名前の両方が含まれます。 短い名前は CAXXXX です。長い名前は CAXXXX: FriendlyTypeName です。

- **理由**-メッセージを抑制する理由を文書化するために使用されるテキストです。

- **MessageId** -各メッセージの問題の一意の識別子。

- **スコープ**-警告が抑制されている対象。 ターゲットが指定されていない場合は、属性のターゲットに設定されます。 サポートされる[スコープ](xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope)は次のとおりです。

  - `module`

  - `resource`

  - `type`

  - `member`

  - `namespace`-このスコープでは、名前空間自体に対する警告が抑制されます。 名前空間内の型に対する警告は抑制されません。

  - `namespaceanddescendants`-(Visual Studio 2019 の新) このスコープでは、名前空間とそのすべての子孫シンボルで警告が抑制されます。 この`namespaceanddescendants`値は、レガシ分析では無視されます。

- **Target** -警告が抑制されるターゲットを指定するために使用される識別子。 完全修飾項目名が含まれている必要があります。

## <a name="suppressmessage-usage"></a>SuppressMessage の使用法

コード分析の警告は、 <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>属性が適用されるレベルでは抑制されます。 たとえば、属性は、アセンブリ、モジュール、型、メンバー、またはパラメーターレベルで適用できます。 この目的は、違反が発生したコードに対して抑制情報を密に結合することです。

抑制の一般的な形式には、ルールカテゴリとルール識別子が含まれます。このルールには、ユーザーが判読できる規則名の表現が含まれています。 例:

`[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

ソース内の抑制メタデータを最小限に抑えるためにパフォーマンス上の厳密な理由がある場合は、規則名を省略できます。 ルールカテゴリとそのルール ID が一緒に、十分に一意なルール識別子が構成されます。 例:

`[SuppressMessage("Microsoft.Design", "CA1039")]`

保守容易性のために、規則名を省略することは推奨されません。

## <a name="suppress-selective-violations-within-a-method-body"></a>メソッド本体内の選択的違反を抑制する

抑制属性はメソッドに適用できますが、メソッド本体内に埋め込むことはできません。 これは、 <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>属性をメソッドに追加した場合に、特定の規則のすべての違反が抑制されることを意味します。

場合によっては、将来のコードがコード分析ルールから自動的に除外されるように、違反の特定のインスタンスを抑制することが必要になることがあります。 特定のコード分析規則を使用すると、 `MessageId` <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>属性のプロパティを使用してこれを行うことができます。 一般に、特定のシンボル (ローカル変数またはパラメーター) に対する違反に関する従来の`MessageId`ルールでは、プロパティが尊重されます。 [CA1500: VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500-variable-names-should-not-match-field-names.md)は、このようなルールの一例です。 ただし、実行可能コード (非シンボル) での違反に関する従来の規則で`MessageId`は、プロパティは考慮されません。 また、.NET Compiler Platform ("roslyn") アナライザーでは、プロパティ`MessageId`は考慮されません。

規則の特定のシンボル違反を抑制するには、 `MessageId` <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>属性のプロパティのシンボル名を指定します。 次の例は、2つの CA1500 の違反を含むコードを`name`示しています。 `age`変数の場合は[VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500-variable-names-should-not-match-field-names.md)&mdash;、変数の場合は1です。 `age`シンボルの違反のみが抑制されます。

```vb
Public Class Animal
    Dim age As Integer
    Dim name As String

    <CodeAnalysis.SuppressMessage("Microsoft.Maintainability", "CA1500:VariableNamesShouldNotMatchFieldNames", MessageId:="age")>
    Sub PrintInfo()
        Dim age As Integer = 5
        Dim name As String = "Charlie"

        Console.WriteLine("Age {0}, Name {1}", age, name)
    End Sub

End Class
```

```csharp
public class Animal
{
    int age;
    string name;

    [System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Maintainability", "CA1500:VariableNamesShouldNotMatchFieldNames", MessageId = "age")]
    private void PrintInfo()
    {
        int age = 5;
        string name = "Charlie";

        Console.WriteLine($"Age {age}, Name {name}");
    }
}
```

## <a name="generated-code"></a>生成されたコード

マネージコードコンパイラと一部のサードパーティツールでは、コードの迅速な開発を容易にするコードが生成されます。 ソースファイルに表示されるコンパイラで生成されたコードは`GeneratedCodeAttribute` 、通常、属性でマークされます。

生成されたコードのコード分析の警告とエラーを非表示にするかどうかを選択できます。 このような警告やエラーを抑制する方法の詳細[については、「」を参照してください。生成されたコード](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md)の警告を非表示にします。

> [!NOTE]
> コード分析は`GeneratedCodeAttribute` 、アセンブリ全体または単一のパラメーターのいずれかに適用されるときに無視されます。

## <a name="global-level-suppressions"></a>グローバルレベルの抑制

マネージコード分析ツールは、 `SuppressMessage`アセンブリ、モジュール、型、メンバー、またはパラメーターレベルで適用される属性を調べます。 また、リソースと名前空間に対する違反も発生します。 これらの違反はグローバルレベルで適用される必要があり、スコープが設定され、対象となります。 たとえば、次のメッセージでは、名前空間違反が抑制されます。

`[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> スコープで`namespace`警告を非表示にすると、名前空間自体に対して警告が抑制されます。 名前空間内の型に対して警告が抑制されることはありません。

明示的なスコープを指定することで、任意の抑制を表現できます。 これらの抑制はグローバルレベルで有効である必要があります。 型を修飾することによって、メンバーレベルの抑制を指定することはできません。

明示的に指定されたユーザーソースにマップされないコンパイラで生成されたコードを参照するメッセージを抑制する唯一の方法は、グローバルレベルの抑制です。 たとえば、次のコードは、コンパイラによって生成されたコンストラクターに対する違反を抑制します。

`[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> `Target`常に、完全修飾された項目名を含みます。

## <a name="global-suppression-file"></a>グローバル抑制ファイル

グローバル抑制ファイルは、グローバルレベルの抑制またはターゲットを指定しない抑制のいずれかである抑制を保持します。 たとえば、アセンブリレベルの違反の抑制は、このファイルに格納されます。 また、一部の ASP.NET 抑制は、フォームの分離コードではプロジェクトレベルの設定が使用できないため、このファイルに格納されます。 グローバル抑制ファイルが作成され、プロジェクトに追加されます。その際、[**エラー一覧**] ウィンドウで [**抑制**] コマンドの [**プロジェクトの抑制ファイルを**使用する] オプションを初めて選択します。

## <a name="see-also"></a>関連項目

- <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope>
- <xref:System.Diagnostics.CodeAnalysis>
- [コードアナライザーを使用する](../code-quality/use-roslyn-analyzers.md)
