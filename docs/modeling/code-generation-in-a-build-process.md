---
title: ビルド処理でのコード生成
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- text templates, build tasks
- text templates, transforming by using msbuild
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: b3d61a5bcd530afb951f98f84f1f4e38e36f96d6
ms.sourcegitcommit: 9cfd3ef6c65f671a26322320818212a1ed5955fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/26/2019
ms.locfileid: "68533300"
---
# <a name="code-generation-in-a-build-process"></a>ビルドプロセスでのコード生成

[テキスト変換](../modeling/code-generation-and-t4-text-templates.md)は、Visual Studio ソリューションの[ビルド プロセス](/azure/devops/pipelines/index)の一部として呼び出すことができます。 テキスト変換に特化したビルド タスクがあります。 T4 ビルド タスクはデザイン時テキスト テンプレートを実行し、また、実行時 (前処理済み) テキスト テンプレートをコンパイルします。

使用するビルド エンジンに応じて、ビルド タスクができることには違いがあります。 Visual Studio でソリューションをビルドする時に、[hostspecific ="true"](../modeling/t4-template-directive.md)属性が設定されていると、テキスト テンプレートは Visual Studio API (EnvDTE) にアクセスできます。 しかし、ソリューションをコマンド ラインからビルドする時、あるいは Visual Studio を通してサーバー ビルドを開始する時は異なります。 このような場合、ビルドは MSBuild によって実行され、別の T4 ホストが使用されます。 これは、MSBuild を使用してテキストテンプレートを作成する場合と同じ方法でプロジェクトファイル名のようなものにアクセスできないことを意味します。 ただし、[ビルド パラメーターを使用してテキスト テンプレートとディレクティブ プロセッサに環境情報を渡す](#parameters)ことができます。

## <a name="buildserver"></a>コンピューターを構成する

開発用コンピューターでビルドタスクを有効にするには、モデリング SDK for Visual Studio をインストールします。

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

[ビルド サーバー](/azure/devops/pipelines/agents/agents)を Visual Studio がインストールされていないコンピューター上で、実行している場合、開発用コンピューターからビルド コンピューターに次のファイルをコピーします。 '*' を、最新のバージョン番号に置き換えてください。

- $(ProgramFiles)\MSBuild\Microsoft\VisualStudio\v*.0\TextTemplating

  - Microsoft.VisualStudio.TextTemplating.Sdk.Host.*.0.dll

  - Microsoft.TextTemplating.Build.Tasks.dll

  - Microsoft.TextTemplating.targets

- $(ProgramFiles)\Microsoft Visual Studio *.0\VSSDK\VisualStudioIntegration\Common\Assemblies\v4.0

  - Microsoft.VisualStudio.TextTemplating.*.0.dll

  - Microsoft.VisualStudio.TextTemplating.Interfaces.*.0.dll (複数のファイル)

  - Microsoft.VisualStudio.TextTemplating.VSHost.*.0.dll

- $(ProgramFiles)\Microsoft Visual Studio *.0\Common7\IDE\PublicAssemblies\

  - Microsoft.VisualStudio.TextTemplating.Modeling.*.0.dll
  
> [!TIP]
> ビルドサーバーで textcodebuild ターゲットを実行しているときに、Microsoft codeanalysis メソッドのを`MissingMethodException`取得した場合は、roslyn アセンブリが、ビルド実行可能ファイルと同じディレクトリにある*roslyn*という名前のディレクトリにあることを確認してください (たとえば、*msbuild.exe*)。

## <a name="edit-the-project-file"></a>プロジェクト ファイルを編集する

プロジェクトファイルを編集して、MSBuild の一部の機能を構成します。たとえば、テキスト変換ターゲットをインポートします。

**ソリューションエクスプローラー**で、プロジェクトの右クリックメニューから **[アンロード]** を選択します。 これにより XML エディターで .csproj または .vbproj ファイルを編集できるようになります。 編集が完了したら、**再読み込み**を選択します。

## <a name="import-the-text-transformation-targets"></a>テキスト変換ターゲットをインポートする

.vbproj ファイルまたは .csproj ファイルで、次のような行を探します。

`<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`

\- または -

`<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />`

この行の後に、テキスト テンプレートのインポートを挿入します。

```xml
<!-- Optionally make the import portable across VS versions -->
  <PropertyGroup>
    <!-- Get the Visual Studio version: -->
    <VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">16.0</VisualStudioVersion>
    <!-- Keep the next element all on one line: -->
    <VSToolsPath Condition="'$(VSToolsPath)' == ''">$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)</VSToolsPath>
  </PropertyGroup>

<!-- This is the important line: -->
  <Import Project="$(VSToolsPath)\TextTemplating\Microsoft.TextTemplating.targets" />
```

## <a name="transform-templates-in-a-build"></a>ビルド内のテンプレートの変換

プロジェクト ファイルに挿入して変換タスクを制御できるプロパティがいくつかあります。

- すべてのビルドの開始時に変換タスクを実行します。

    ```xml
    <PropertyGroup>
        <TransformOnBuild>true</TransformOnBuild>
    </PropertyGroup>
    ```

- ファイルがチェックアウトされていないためなど、読み取り専用のファイルを上書きします。

    ```xml
    <PropertyGroup>
        <OverwriteReadOnlyOutputFiles>true</OverwriteReadOnlyOutputFiles>
    </PropertyGroup>
    ```

- 毎回、すべてのテンプレートを変換します。

    ```xml
    <PropertyGroup>
        <TransformOutOfDateOnly>false</TransformOutOfDateOnly>
    </PropertyGroup>
    ```

     既定では、次の値より古い場合、T4 MSBuild タスクによって出力ファイルが再生成されます。
     
     - そのテンプレートファイル
     - 含まれているすべてのファイル
     - 以前にテンプレートまたは使用するディレクティブプロセッサによって読み取られたファイル
     
     これは、Visual Studio の **[すべてのテンプレートの変換]** コマンドで使用されるよりも強力な依存関係テストであり、テンプレートと出力ファイルの日付のみを比較します。

プロジェクトでテキスト変換だけを実行するには、TransformAll タスクを呼び出します。

`msbuild myProject.csproj /t:TransformAll`

特定のテキスト テンプレートを変換するには、次のように実行します。

`msbuild myProject.csproj /t:Transform /p:TransformFile="Template1.tt"`

TransformFile ではワイルドカードを使用できます。

`msbuild dsl.csproj /t:Transform /p:TransformFile="GeneratedCode\**\*.tt"`

## <a name="source-control"></a>ソース管理

ソース管理システムと連携するような専用の機能は組み込まれていません。 ただし、たとえば、独自の拡張機能を追加して、生成されたファイルをチェックアウトしてチェックインすることもできます。 既定では、テキスト変換タスクは、読み取り専用としてマークされているファイルの上書きを回避します。 このようなファイルが検出されると、Visual Studio エラー一覧にエラーが記録され、タスクは失敗します。

読み取り専用ファイルを上書きするには、次のプロパティを挿入します。

`<OverwriteReadOnlyOutputFiles>true</OverwriteReadOnlyOutputFiles>`

後処理の手順をカスタマイズしない限り、ファイルが上書きされたときにエラー一覧に警告が記録されます。

## <a name="customize-the-build-process"></a>ビルドプロセスをカスタマイズする

テキスト変換は、ビルド処理で他のタスクよりも前に実行されます。 `$(BeforeTransform)` プロパティと `$(AfterTransform)` プロパティを設定して、変換の前後に呼び出すタスクを定義できます。

```xml
<PropertyGroup>
    <BeforeTransform>CustomPreTransform</BeforeTransform>
    <AfterTransform>CustomPostTransform</AfterTransform>
  </PropertyGroup>
  <Target Name="CustomPreTransform">
    <Message Text="In CustomPreTransform..." Importance="High" />
  </Target>
  <Target Name="CustomPostTransform">
    <Message Text="In CustomPostTransform..." Importance="High" />
  </Target>
```

`AfterTransform` では、ファイルのリストを参照できます。

- GeneratedFiles: 処理中に出力されたファイルのリスト。 既存の読み取り専用ファイルを上書きしたファイルの`%(GeneratedFiles.ReadOnlyFileOverwritten)`場合、は true になります。 これらのファイルは、ソース管理からチェックアウトできます。

- NonGeneratedFiles: 上書きされなかった読み取り専用ファイルのリスト。

たとえば、GeneratedFiles をチェックアウトするタスクを定義します。

## <a name="outputfilepath-and-outputfilename"></a>OutputFilePath と OutputFileName

これらのプロパティを使用するのは MSBuild だけです。 Visual Studio のコード生成には影響しません。 これらは生成された出力ファイルを別のフォルダーまたはファイルにリダイレクトします。 対象となるフォルダーが既に存在する必要があります。

```xml
<ItemGroup>
  <None Include="MyTemplate.tt">
    <Generator>TextTemplatingFileGenerator</Generator>
    <OutputFilePath>MyFolder</OutputFilePath>
    <LastGenOutput>MyTemplate.cs</LastGenOutput>
  </None>
</ItemGroup>
```

リダイレクト先として便利な`$(IntermediateOutputPath)`フォルダーはです。

出力ファイル名を指定した場合は、テンプレートの output ディレクティブで指定されている拡張子よりも優先されます。

```xml
<ItemGroup>
  <None Include="MyTemplate.tt">
    <Generator>TextTemplatingFileGenerator</Generator>
    <OutputFileName>MyOutputFileName.cs</OutputFileName>
    <LastGenOutput>MyTemplate.cs</LastGenOutput>
  </None>
</ItemGroup>
```

OutputFileName または OutputFilePath を指定することは、Visual Studio 内で **すべて変換**する (1 つのファイルジェネレーター) を使用してテンプレートを変換する場合には推奨されません。 変換のトリガー方法によっては、ファイルパスが異なる場合があります。 これは混乱する可能性があります。

## <a name="add-reference-and-include-paths"></a>参照パスとインクルードパスの追加

ホストには、テンプレートで参照されているアセンブリを検索する既定のパス セットがあります。 このパス セットを追加するには、次のように指定します。

```xml
<ItemGroup>
    <T4ReferencePath Include="$(VsIdePath)PublicAssemblies\" />
    <!-- Add more T4ReferencePath items here -->
</ItemGroup>
```

インクルード ファイルを検索するフォルダーを設定するには、セミコロン区切りのリストを指定します。 通常は、既存のフォルダー リストに追加します。

```xml
<PropertyGroup>
    <IncludeFolders>
$(IncludeFolders);$(MSBuildProjectDirectory)\Include;AnotherFolder;And\Another</IncludeFolders>
</PropertyGroup>
```

## <a name="parameters"></a>ビルドコンテキストデータをテンプレートに渡す

プロジェクト ファイルにパラメーターと値を設定できます。 たとえば、[ビルド](../msbuild/msbuild-properties.md)プロパティと[環境変数](../msbuild/how-to-use-environment-variables-in-a-build.md)を渡すことができます。

```xml
<ItemGroup>
  <T4ParameterValues Include="ProjectFolder">
    <Value>$(ProjectDir)</Value>
    <Visible>false</Visible>
  </T4ParameterValues>
</ItemGroup>
```

テキスト テンプレートでは、template ディレクティブで `hostspecific` を設定します。 [パラメーター](../modeling/t4-parameter-directive.md)ディレクティブを使用して、値を取得します。

```
<#@template language="c#" hostspecific="true"#>
<#@ parameter type="System.String" name="ProjectFolder" #>
The project folder is: <#= ProjectFolder #>
```

ディレクティブ プロセッサでは、[ITextTemplatingEngineHost.ResolveParameterValue](/previous-versions/visualstudio/visual-studio-2012/bb126369\(v\=vs.110\))を呼び出すことができます。

```csharp
string value = Host.ResolveParameterValue("-", "-", "parameterName");
```

```vb
Dim value = Host.ResolveParameterValue("-", "-", "parameterName")
```

> [!NOTE]
> `ResolveParameterValue` は、MSBuild を使用する場合に限り、`T4ParameterValues` からデータを取得します。 Visual Studio を使用してテンプレートを変換すると、パラメーターには既定値が設定されます。

## <a name="msbuild"></a> assembly および include ディレクティブで、プロジェクトのプロパティを使用する

Visual Studio のマクロ **$ (solutiondir)** などは、MSBuild では動作しません。 その代わりに、プロジェクト プロパティを使用できます。

*.csproj*または *.vbproj* ファイルを編集して、プロジェクト プロパティを定義します。 次の例は、**myLibFolder**という名前のプロパティを定義します。

```xml
<!-- Define a project property, myLibFolder: -->
<PropertyGroup>
    <myLibFolder>$(MSBuildProjectDirectory)\..\libs</myLibFolder>
</PropertyGroup>

<!-- Tell the MSBuild T4 task to make the property available: -->
<ItemGroup>
    <T4ParameterValues Include="myLibFolder">
      <Value>$(myLibFolder)</Value>
    </T4ParameterValues>
  </ItemGroup>
```

これで、assembly ディレクティブおよび include ディレクティブでプロジェクト プロパティを使用できます。

```
<#@ assembly name="$(myLibFolder)\MyLib.dll" #>
<#@ include file="$(myLibFolder)\MyIncludeFile.t4" #>
```

これらのディレクティブは、MSBuild ホストおよび Visual Studio ホストの両方で T4parameterValues から値を取得します。

## <a name="q--a"></a>Q & A

**ビルドサーバーでテンプレートを変換する理由コードをチェックインする前に、Visual Studio で既にテンプレートを変換しました。**

インクルードファイルまたはテンプレートによって読み取られた別のファイルを更新すると、Visual Studio はファイルを自動的に変換しません。 ビルドの一部としてテンプレートを変換するなら、すべてが最新の状態です。

**テキスト テンプレート変換には、その他のオプションがありますか。**

- [Texttransform ユーティリティ](../modeling/generating-files-with-the-texttransform-utility.md)は、コマンドスクリプトで使用できます。 ほとんどの場合、MSBuild を使用する方が簡単です。

- [Visual Studio 拡張機能でテキスト変換を呼び出し](../modeling/invoking-text-transformation-in-a-vs-extension.md)ます。

- [デザイン時テキスト テンプレート](../modeling/design-time-code-generation-by-using-t4-text-templates.md)は、Visual Studio によって変換されます。

- [実行時テキスト テンプレート](../modeling/run-time-text-generation-with-t4-text-templates.md)は、アプリケーションでの実行時に変換されます。

## <a name="see-also"></a>関連項目

::: moniker range="vs-2017"

- *% ProgramFiles (x86)% \ Microsoft Visual Studio\2017\Enterprise\msbuild\Microsoft\VisualStudio\v15.0\TextTemplating\Microsoft.TextTemplating.targets*の T4 MSbuild テンプレートには、適切なガイダンスがあります。

::: moniker-end

::: moniker range=">=vs-2019"

- *% ProgramFiles (x86)% \ Microsoft Visual Studio\2019\Enterprise\msbuild\Microsoft\VisualStudio\v16.0\TextTemplating\Microsoft.TextTemplating.targets*の T4 MSbuild テンプレートには、適切なガイダンスがあります。

::: moniker-end

- [T4 テキストテンプレートを作成する](../modeling/writing-a-t4-text-template.md)
