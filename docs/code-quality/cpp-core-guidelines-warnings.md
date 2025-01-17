---
title: C++ Core Guidelines の警告
ms.date: 08/10/2017
ms.topic: conceptual
ms.assetid: 7c83814a-f21d-4323-ad5f-13bac40d3e38
author: mblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 002a82143ca30e87a8e83f3e7e4b7217ab677f11
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62822501"
---
# <a name="using-the-c-core-guidelines-checkers"></a>C++ Core ガイドライン チェッカーの使用

C++ Core ガイドラインは、ガイドライン、ルール、および C++ 専門家とデザイナーで作成された C++ のコーディングについてのベスト プラクティスの移植可能なセットです。 Visual Studio では、c++ のコード分析ツールの一部としてこれらのルールのサブセットがサポートされています。 Core ガイドラインのチェッカーが Visual Studio 2017 と Visual Studio 2019、既定でインストールされ[Visual Studio 2015 用の NuGet パッケージとして利用可能な](#vs2015_corecheck)します。

## <a name="the-c-core-guidelines-project"></a>C++ Core ガイドラインのプロジェクト

Bjarne Stroustrup と他のユーザーによって作成された、C++ Core Guidelines は、安全で効果的に最新の C++ を使用するためのガイドです。 ガイドラインは、静的な型の安全性とリソースの安全性を強調します。 排除または言語のエラーを起こしやすい部分を最小化する方法を特定され、信頼性の高い方法でパフォーマンスが向上と、コードを簡素化する方法をお勧めします。 次のガイドラインは、標準の C++ Foundation によって管理されます。 詳細については、ドキュメントを参照してください。 [C++ Core Guidelines](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)、C++ Core Guidelines のドキュメントのプロジェクト ファイルにアクセスして[GitHub](https://github.com/isocpp/CppCoreGuidelines)します。

## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>C++ Core Check のガイドラインにコード分析を有効にします。

選択してプロジェクトでコード分析を有効にすることができます、**ビルドに対するコード分析を有効にする**でチェック ボックスをオン、**コード分析**のセクション、**プロパティ ページ**のダイアログ ボックスプロジェクト。

![コード分析の全般設定のプロパティ ページ](../code-quality/media/cppcorecheck_codeanalysis_general.png)

C++ Core Check の規則は、コード分析が有効になっているときに実行される既定の規則セットの拡張機能です。 C++ Core Check の規則では、開発中であるため、いくつかのルールが準備されていますを実行し、いくつか、すべてのコードで使用する準備ができていない可能性がありますが、できない可能性がありますでも有益を実行します。 ルールは 2 つのグループに分けられます: リリースおよび試験段階。 プロジェクトのプロパティでリリースされたまたは試験用の規則を実行するかどうかを選択できます。

![コード分析の拡張機能設定のプロパティ ページ](../code-quality/media/cppcorecheck_codeanalysis_extensions.png)

有効または、C++ Core Check の規則セットを無効にする、開く、**プロパティ ページ**プロジェクトのダイアログ。 **構成プロパティ**、展開**コード分析**、**拡張**します。 横にドロップダウン リストで制御**を有効にする C++ Core の Check (リリース)** または**を有効にする C++ Core の Check (試験段階)**、選択**はい**または**いいえ**します。 選択**OK**または**適用**変更を保存します。

## <a name="examples"></a>使用例

C++ Core Check の規則を検索する問題のいくつかの例を次に示します。

```cpp
// CoreCheckExample.cpp
// Add CppCoreCheck package and enable code analysis in build for warnings.

int main()
{
    int arr[10];           // warning C26494
    int* p = arr;          // warning C26485

    [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1
    {
        int* q = p + 1;    // warning C26481 (suppressed)
        p = q++;           // warning C26481 (suppressed)
    }

    return 0;
}
```

この例では、C++ Core Check の規則を検索する警告のいくつかを示します。

- C26494 は、規則 Type.5 です。常にオブジェクトを初期化します。

- C26485 は、規則 Bounds.3 です。配列とポインター減退がありません。

- C26481 は、規則 Bounds.1 です。ポインターの算術演算を使用しないでください。 代わりに、`span` を使用してください。

C++ Core Check のコード分析ルールセットはインストールされている、このコードをコンパイルすると、最初の 2 つの警告は、出力が、3 つ目の抑制を有効になっている場合。 コード例からのビルド出力を次に示します。

```Output
1>------ Build started: Project: CoreCheckExample, Configuration: Debug Win32 ------
1>  CoreCheckExample.cpp
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.exe
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.pdb (Full PDB)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(6): warning C26494: Variable 'arr' is uninitialized. Always initialize an object. (type.5: http://go.microsoft.com/fwlink/p/?LinkID=620421)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(7): warning C26485: Expression 'arr': No array to pointer decay. (bounds.3: http://go.microsoft.com/fwlink/p/?LinkID=620415)
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

安全なコードを記述するため、C++ Core Guidelines は。 ただし、場所、ルール、またはプロファイルを適用しないインスタンスがある場合を簡単に、コード内で直接非表示になります。 使用することができます、`gsl::suppress`を検出して、次のコード ブロックの規則の違反をレポートから C++ Core Check を保持する属性。 特定のルールを抑制する個々 のステートメントをマークすることができます。 記述することで、全体の bounds プロファイルを抑制することができますも`[[gsl::suppress(bounds)]]`含めず、特定のルールの数。

## <a name="supported-rule-sets"></a>規則セットのサポート

ように、新しいルールを追加する、C++ Core ガイドライン チェッカーの既存のコードを生成する警告の数は増やすことができます。 有効にするのにルールの種類をフィルター処理するのに定義済みの規則のセットを使用することができます。 Visual Studio 2017 バージョン 15.3 の時点では、サポートされている規則セット。

- **所有者ポインターの規則**適用[所有者に関連するリソース管理を確認します\<T >、C++ Core Guidelines から](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management)します。

- **Const ルール**適用[、C++ Core guidelines の定数に関連したチェック](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con-constants-and-immutability)します。

- **生のポインターの規則**適用[リソース管理に関連する生のポインター、C++ Core guidelines のチェック](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management)します。

- **一意のポインターの規則**適用[、C++ Core guidelines のユニーク ポインター セマンティクスを持つ型に関連するリソース管理を確認します](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management)します。

- **範囲の規則**適用、 [、C++ Core Guidelines のプロファイルの境界](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile)します。

- **入力規則**適用、 [、C++ Core Guidelines のプロファイルを入力](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prosafety-type-safety-profile)します。

警告を 1 つだけ、またはグループの数を制限することができます。 **ネイティブ最小**と**ネイティブ推奨**ルール セットには、その他の PREfast のチェックだけでなく C++ Core Check の規則が含まれます。 確認には、使用可能なルール セット、プロジェクトのプロパティ ダイアログを開き、次のように選択します**コード Analysis\General**、にあるボックスを開き、**規則セット**コンボ ボックス、および選択**複数の規則セットの選択**。 Visual Studio でのルール セットの使用に関する詳細については、次を参照してください。[ルール セットのコード分析規則のグループを使用して](using-rule-sets-to-group-code-analysis-rules.md)します。

## <a name="macros"></a>[マクロ]

全体のカテゴリには、コードの警告を抑制するが簡単にするマクロを定義するヘッダー ファイルには、C++ Core ガイドライン チェッカーできます。

```cpp
ALL_CPPCORECHECK_WARNINGS
CPPCORECHECK_TYPE_WARNINGS
CPPCORECHECK_RAW_POINTER_WARNINGS
CPPCORECHECK_CONST_WARNINGS
CPPCORECHECK_OWNER_POINTER_WARNINGS
CPPCORECHECK_UNIQUE_POINTER_WARNINGS
CPPCORECHECK_BOUNDS_WARNINGS
```

これらのマクロは、ルール セットに対応し、警告番号のスペースで区切られたリストに展開します。 適切なプラグマ コンストラクトを使用して、プロジェクトにとって重要である有効な規則のセットまたはコードのセクションを構成できます。 次の例では、コード分析は定数の修飾子が見つからない場合の警告のみ。

```cpp
#include <CppCoreCheck\Warnings.h>
#pragma warning(disable: ALL_CPPCORECHECK_WARNINGS)
#pragma warning(default: CPPCORECHECK_CONST_WARNINGS)
```

## <a name="attributes"></a>属性

Microsoft Visual C コンパイラでは、属性を非表示、GSL の制限付きサポートには。 式および関数内でのブロックのステートメントで警告を抑制するために使用します。

```cpp
// Suppress only warnings from the 'r.11' rule in expression.
[[gsl::suppress(r.11)]] new int;

// Suppress all warnings from the 'r' rule group (resource management) in block.
[[gsl::suppress(r)]]
{
    new int;
}

// Suppress only one specific warning number.
// For declarations, you may need to use the surrounding block.
// Macros are not expanded inside of attributes.
// Use plain numbers instead of macros from the warnings.h.
[[gsl::suppress(26400)]]
{
    int *p = new int;
}
```

## <a name="suppressing-analysis-by-using-command-line-options"></a>分析コマンド ライン オプションを使用して非表示にします。

#Pragmas の代わりには、ファイルのプロパティ ページで、プロジェクトまたはファイルを 1 つの警告を抑制するのにコマンド ライン オプションを使用することができます。 たとえば、警告を無効にするファイルの 26400。

1. ファイルを右クリックして**ソリューション エクスプ ローラー**

2. 選択**プロパティ |C または C++ |コマンド ライン**

3. **追加オプション**ウィンドウで、追加`/wd26400`します。

コマンド ライン オプションを使用するには、ファイルのすべてのコード分析を指定することで一時的に無効に`/analyze-`します。 警告が生成されます*D9025 オーバーライド '/analyze' を '/analyze -'*、これは通知後でコード分析を再び有効にします。

## <a name="corecheck_per_file"></a> 特定のプロジェクト ファイルでは、C++ Core ガイドライン チェッカーの有効化

重点を置いてコード分析をまだ活用、Visual Studio IDE に役立つ場合があります。 大規模なプロジェクトのビルド時間を節約して、結果をフィルター処理を容易に使用できるシナリオの例を次に示します。

1. コマンド シェルで次のように設定します。、`esp.extension`と`esp.annotationbuildlevel`環境変数。
2. これらの変数を継承するように、コマンド シェルから、Visual Studio を開きます。
3. プロジェクトを読み込むし、そのプロパティを開きます。
4. コード分析を有効にする、適切なルール セットの選択が、コード分析の拡張機能を有効にしません。
5. C++ Core ガイドライン チェッカーの使用の分析のプロパティを表示するファイルに移動します。
6. 選択**C/c++ \Command ライン オプション**追加 `/analyze:plugin EspXEngine.dll`
7. プリコンパイル済みヘッダーの使用を無効にする (**C/c++ \Precompiled ヘッダー**)。 これは、機能は、拡張機能のエンジンがプリコンパイル済みヘッダーからの内部情報を読み取ろうと可能性があり、後者が既定のプロジェクト オプションでコンパイルである場合に互換性がないため、必要です。
8. プロジェクトをリビルドします。 共通の PREFast のチェックは、すべてのファイルを実行する必要があります。 C++ Core ガイドライン チェッカーが既定で有効でないためする必要があります、それを使用するように構成ファイルでのみ実行します。

## <a name="how-to-use-the-c-core-guidelines-checker-outside-of-visual-studio"></a>Visual Studio の外部では、C++ Core ガイドライン チェッカーの使用方法
自動ビルドで、C++ Core Guidelines のチェックを使用することができます。

### <a name="msbuild"></a>MSBuild

ネイティブ コード分析チェック (PREfast) はカスタム ターゲット ファイルで MSBuild 環境に統合されます。 プロジェクトのプロパティを使用して、それを有効にし、C++ Core ガイドライン チェッカー (これは、PREfast に基づきます) を追加できます。

```xml
<PropertyGroup>
  <EnableCppCoreCheck>true</EnableCppCoreCheck>
  <CodeAnalysisRuleSet>CppCoreCheckRules.ruleset</CodeAnalysisRuleSet>¬¬
  <RunCodeAnalysis>true</RunCodeAnalysis>
</PropertyGroup>
```

Microsoft.Cpp.targets ファイルをインポートする前にこれらのプロパティを追加することを確認します。 特定のルール セットを選択またはカスタム規則セットを作成またはその他の PREfast のチェックが含まれる既定の規則セットを使用できます。

同じアプローチを使用して、指定したファイルにのみ、C++ Core チェックを行うことができます[前に説明した](#corecheck_per_file)、MSBuild ファイルを使用します。 使用して、環境変数を設定することができます、`BuildMacro`項目。

```xml
<ItemGroup>
    <BuildMacro Include="Esp_AnnotationBuildLevel">
      <EnvironmentVariable>true</EnvironmentVariable>
      <Value>Ignore</Value>
    </BuildMacro>
    <BuildMacro Include="Esp_Extensions">
      <EnvironmentVariable>true</EnvironmentVariable>
      <ValueCppCoreCheck.dll</Value>
    </BuildMacro>
</ItemGroup>
```

プロジェクト ファイルを変更しない場合は、コマンドラインでプロパティを渡すことができます。

```cmd
msbuild /p:EnableCppCoreCheck=true /p:RunCodeAnalysis=true /p:CodeAnalysisRuleSet=CppCoreCheckRules.ruleset ...
```

### <a name="non-msbuild-projects"></a>非 MSBuild プロジェクト
MSBuild に依存しないビルド システムを使用する場合は、チェックを実行することができますが、(これは、今後サポートされるには保証されません)、コード分析エンジンの構成の一部の内部について理解する必要があります。

いくつかの環境変数を設定して、コンパイラは適切なコマンド ライン オプションを使用する必要があります。 コンパイラの特定のパスを検索するには、ディレクトリなどが含まれますがあるないように、「Native Tools コマンド プロンプト」環境で機能することをお勧めします。

1. **環境変数**
   - `set esp.extensions=cppcorecheck.dll` これは、C++ Core Guidelines のモジュールを読み込むエンジンを指示します。
   - `set esp.annotationbuildlevel=ignore` これには、SAL 注釈を処理するロジックが無効にします。 注釈は、C++ Core ガイドライン チェッカーのコード分析に影響はありませんが、処理時間がかかります (場合によって多くの時間に)。 この設定は、省略可、ただし強くお勧めします。
   - `set caexcludepath=%include%` 標準ヘッダーでは発生する警告を無効にすることを強くお勧めします。 プロジェクトの一般的なヘッダーへのパスなど、ここでは、複数のパスを追加できます。
2. **コマンド ライン オプション**
   - `/analyze`  コード分析を有効 (も使用を検討して/analyze: のみと/analyze: quiet)。
   - `/analyze:plugin EspXEngine.dll` このオプションは、PREfast にコード分析の拡張機能のエンジンを読み込みます。 このエンジンでは、C++ Core ガイドライン チェッカーを読み込みます。

## <a name="use-the-guideline-support-library"></a>ガイドライン サポート ライブラリを使用します。

ガイドライン サポート ライブラリは、Core Guidelines をフォローするように設計されています。 GSL より安全な代替手段でエラーが発生しやすい構成要素を置き換えますできる定義が含まれます。 などに置き換えることができます、`T*, length`パラメーターのペア、`span<T>`型。 GSL [ http://www.nuget.org/packages/Microsoft.Gsl](http://www.nuget.org/packages/Microsoft.Gsl)します。 ライブラリは、オープン ソースはので、ソースを表示、コメントの作成、または投稿することができます。 プロジェクトに掲載する[ https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL)します。

## <a name="vs2015_corecheck"></a> Visual Studio 2015 のプロジェクトで、C++ Core Check のガイドラインを使用します。

Visual Studio 2015 を使用する場合、C++ Core Check コード分析規則セットは既定ではインストールされていません。 Visual Studio 2015 での C++ Core Check コード分析ツールを有効にする前に、追加の手順を実行する必要があります。 マイクロソフトでは、Nuget パッケージを使用して、Visual Studio 2015 プロジェクトのサポートを提供します。 パッケージの名前は Microsoft.CppCoreCheck とで使用可能になる[ http://www.nuget.org/packages/Microsoft.CppCoreCheck](http://www.nuget.org/packages/Microsoft.CppCoreCheck)します。 このパッケージには少なくとも Visual Studio 2015 Update 1 でインストールが必要になります。

パッケージには、依存関係をヘッダーのみのガイドライン サポート ライブラリ (GSL) として別のパッケージもインストールされます。 GitHub の「使用可能な、GSL も[ https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL)します。

コード分析の規則が読み込まれるため、Visual Studio 2015 内でチェックする C++ プロジェクトごとに、Microsoft.CppCoreCheck NuGet パッケージをインストールする必要があります。

### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project-in-visual-studio-2015"></a>Visual Studio 2015 でプロジェクトに Microsoft.CppCoreCheck パッケージを追加するには

1. **ソリューション エクスプ ローラー**、右クリックすると、パッケージを追加するソリューションで、プロジェクトのコンテキスト メニューを開きます。 選択**NuGet パッケージの管理**を開く、 **NuGet パッケージ マネージャー**します。

2. **NuGet パッケージ マネージャー**ウィンドウで、Microsoft.CppCoreCheck を検索します。

    ![Nuget パッケージ マネージャー ウィンドウは、CppCoreCheck パッケージを示しています。](../code-quality/media/cppcorecheck_nuget_window.png)

3. Microsoft.CppCoreCheck パッケージを選択し、選択、**インストール**をプロジェクトに規則を追加するボタンをクリックします。

   NuGet パッケージでは、プロジェクトでコード分析を有効にしたときに呼び出されるプロジェクトに追加の MSBuild .targets ファイルを追加します。 この .targets ファイルでは、Visual Studio コード分析ツールに追加の拡張機能として、C++ Core Check の規則を追加します。 パッケージがインストールされている場合は、有効または無効、リリースと実験用のルールにプロパティ ページ ダイアログを使用できます。
