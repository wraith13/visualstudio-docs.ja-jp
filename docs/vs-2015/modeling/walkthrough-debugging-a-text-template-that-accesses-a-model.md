---
title: 'チュートリアル: モデルにアクセスするテキスト テンプレートのデバッグ |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: af46a7fe-6b98-4d3d-b816-0bbf8e81e220
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 26ff566c9d9ff833a92668d06c818245ed55d066
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65700571"
---
# <a name="walkthrough-debugging-a-text-template-that-accesses-a-model"></a>チュートリアル: モデルにアクセスするテキスト テンプレートのデバッグ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

変更またはドメイン固有言語ソリューションでテキスト テンプレートを追加するときに、エンジンのソース コードに、または、生成されたコードをコンパイル時にテンプレートを変換するときにエラーが発生する可能性があります。 次のチュートリアルでは、テキスト テンプレートをデバッグすることの一部を示します。  
  
> [!NOTE]
> を一般に、テンプレート文字列の詳細についてを参照してください[コードの生成と T4 テキスト テンプレート](../modeling/code-generation-and-t4-text-templates.md)します。 テキスト テンプレートのデバッグの詳細については、次を参照してください。[チュートリアル。テキスト テンプレートのデバッグ](https://msdn.microsoft.com/library/5c3fd3b7-c110-4e86-a22f-d5756be6b94f)します。  
  
## <a name="creating-a-domain-specific-language-solution"></a>ドメイン固有言語ソリューションを作成します。  
 この手順では、次の特性を持つドメイン固有言語ソリューションを作成します。  
  
- 名前:DebuggingTestLanguage  
  
- ソリューション テンプレート:最小言語  
  
- ファイル拡張子: .ddd  
  
- 会社名:Fabrikam Fiber Web サイト  
  
  ドメイン固有言語ソリューションを作成する方法の詳細については、次を参照してください。[方法。ドメイン固有言語ソリューションを作成する](../modeling/how-to-create-a-domain-specific-language-solution.md)」を参照してください。  
  
## <a name="creating-a-text-template"></a>テキスト テンプレートの作成  
 テキスト テンプレートをソリューションに追加します。  
  
#### <a name="to-create-a-text-template"></a>テキスト テンプレートを作成するには  
  
1. ソリューションをビルドし、デバッガーで実行を開始します。 (上、**ビルド** メニューのをクリックして**ソリューションのリビルド**、し、**デバッグ** メニューのをクリックして**デバッグの開始**)。Visual Studio の新しいインスタンスは、デバッグ プロジェクトを開きます。  
  
2. という名前のテキスト ファイルを追加`DebugTest.tt`デバッグ プロジェクトへです。  
  
3. 必ず、**カスタム ツール**DebugTest.tt のプロパティに設定されて`TextTemplatingFileGenerator`。  
  
## <a name="debugging-directives-that-access-a-model-from-a-text-template"></a>テキスト テンプレートから、モデルにアクセスするデバッグ ディレクティブ  
 ステートメントとテキスト テンプレート内の式からモデルにアクセスすることができます、生成済みディレクティブ プロセッサを呼び出す必要があります。 生成されたディレクティブ プロセッサを呼び出すことクラスは、モデルを使用できるように、テキスト テンプレート コード プロパティとして。 詳細については、[テキスト テンプレートからへのアクセス モデル](../modeling/accessing-models-from-text-templates.md)を参照してください。  
  
 次の手順では、正しくないのディレクティブ名と正しくないプロパティ名をデバッグします。  
  
#### <a name="to-debug-an-incorrect-directive-name"></a>正しくないのディレクティブ名をデバッグするには  
  
1. DebugTest.tt でコードを次のコードに置き換えます。  
  
    > [!NOTE]
    > コードには、エラーが含まれています。 これをデバッグするために、エラーが導入されました。  
  
    ```csharp  
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ modelRoot processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
  
    Model: <#= this.ExampleModel #>  
    <#  
    foreach (ExampleElement element in this.ExampleModel.Elements)   
    {   
    #>   
        Element: <#= element.Name #>  
    <#   
    }  
    #>  
    ```  
  
    ```vb  
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ modelRoot processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
  
    Model: <#= Me.ExampleModel #>  
    <#  
    For Each element as ExampleElement in Me.ExampleModel.Elements  
    #>   
        Element: <#= element.Name #>  
    <#   
    Next  
    #>  
    ```  
  
2. **ソリューション エクスプ ローラー**DebugTest.tt を右クリックし、クリックして**カスタム ツールの実行**します。  
  
     **エラー一覧**ウィンドウには、このエラーが表示されます。  
  
     **'DebuggingTestLanguageDirectiveProcessor' という名前のプロセッサがディレクティブ 'modelRoot' をサポートしていません。変換は実行されません。**  
  
     この場合は、ディレクティブの呼び出しには、正しくないのディレクティブ名が含まれています。 指定した`modelRoot`ディレクティブの名前が正しいディレクティブ名が`DebuggingTestLanguage`します。  
  
3. エラーをダブルクリックして、**エラー一覧**コードに移動するウィンドウ。  
  
4. ディレクティブ名を変更して、コードを修正する`DebuggingTestLanguage`します。  
  
     変更が強調表示されます。  
  
    ```csharp  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
    ```  
  
    ```vb  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
    ```  
  
5. **ソリューション エクスプ ローラー**DebugTest.tt を右クリックし、クリックして**カスタム ツールの実行**します。  
  
     これで、システムでは、テキスト テンプレート変換し、対応する出力ファイルを生成します。 内のエラーが表示されませんが、**エラー一覧**ウィンドウ。  
  
#### <a name="to-debug-an-incorrect-property-name"></a>間違ったプロパティ名をデバッグするには  
  
1. DebugTest.tt でコードを次のコードに置き換えます。  
  
    > [!NOTE]
    > コードには、エラーが含まれています。 これをデバッグするために、エラーが導入されました。  
  
    ```csharp  
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
  
    Model: <#= this.ExampleModel #>  
    <#  
    foreach (ExampleElement element in this.ExampleModel.Elements)   
    {   
    #>   
        Element: <#= element.Name #>  
    <#   
    }  
    #>  
    ```  
  
    ```vb  
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
  
    Model: <#= Me.ExampleModel #>  
    <#  
    For Each element as ExampleElement in Me.ExampleModel.Elements  
    #>   
        Element: <#= element.Name #>  
    <#   
    Next  
    #>  
    ```  
  
2. **ソリューション エクスプ ローラー**DebugTest.tt を右クリックし、クリックして**カスタム ツールの実行**します。  
  
     **エラー一覧**ウィンドウが表示され、これらのエラーのいずれかが表示されます。  
  
     (C#)  
  
     **変換をコンパイルします。Microsoft.VisualStudio.TextTemplating\<GUID >。GeneratedTextTransformation' 'ExampleModel' の定義が含まれていません**  
  
     (Visual Basic)  
  
     **変換をコンパイルします。'ExampleModel' のメンバーでない ' Microsoft.VisualStudio.TextTemplating\<GUID >。GeneratedTextTransformation'。**  
  
     ここでは、テキスト テンプレート コードには、正しくないプロパティ名が含まれています。 指定した`ExampleModel`名には、プロパティの名前が、適切なプロパティとして`LibraryModel`します。 適切なプロパティの名前を検索する、次のコードに示すように、パラメーターを提供します。  
  
    ```  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
    ```  
  
3. コードにジャンプする [エラー一覧] ウィンドウでエラーをダブルクリックします。  
  
4. プロパティ名を変更して、コードを修正する`LibraryModel`テキスト テンプレート コードでします。  
  
     変更が強調表示されます。  
  
    ```csharp  
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
  
    Model: <#= this.LibraryModel #>  
    <#  
    foreach (ExampleElement element in this.LibraryModel.Elements)   
    {   
    #>   
        Element: <#= element.Name #>  
    <#   
    }  
    #>  
    ```  
  
    ```vb  
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
  
    Model: <#= Me.LibraryModel #>  
    <#  
    For Each element as ExampleElement in Me.LibraryModel.Elements  
    #>   
        Element: <#= element.Name #>  
    <#   
    Next  
    #>  
    ```  
  
5. **ソリューション エクスプ ローラー**DebugTest.tt を右クリックし、クリックして**カスタム ツールの実行**します。  
  
     これで、システムでは、テキスト テンプレート変換し、対応する出力ファイルを生成します。 内のエラーが表示されませんが、**エラー一覧**ウィンドウ。
