---
title: T4 テキスト テンプレートを使用した実行時テキスト生成 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Preprocessed Text Template project item
- TextTemplatingFilePreprocessor custom tool
- text templates, TransformText() method
- text templates, generating files at run time
ms.assetid: 79b4b3c6-a9a7-4446-b6fd-e2388fc6b05f
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 586ad1d68ce1d0310b30b8bdac8aa2fb55acdeb5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63411876"
---
# <a name="run-time-text-generation-with-t4-text-templates"></a>T4 テキスト テンプレートを使用した実行時テキスト生成
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

使用して、実行時に、アプリケーションでのテキスト文字列を生成できます[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]ランタイム テキスト テンプレート。 アプリケーションが実行されるコンピューターを持っていなくて[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]します。 実行時テンプレートとも呼ばれる「ランタイム テキスト テンプレート」のため、コンパイル時に、テンプレートからランタイムに実行されるコードが生成されます。  
  
 各テンプレートは、生成される文字列として現れるテキストと、プログラム コードのフラグメントの組み合わせです。 プログラムのフラグメントは、文字列の変数部分の値の指定と、条件と繰り返し部分を制御します。  
  
 たとえば、次のテンプレートは、HTML レポートを作成するアプリケーションで使用され得るものです。  
  
```  
<#@ template language="C#" #>  
<html><body>  
<h1>Sales for Previous Month</h2>  
<table>  
    <# for (int i = 1; i <= 10; i++)  
       { #>  
         <tr><td>Test name <#= i #> </td>  
             <td>Test value <#= i * i #> </td> </tr>  
    <# } #>  
 </table>  
This report is Company Confidential.  
</body></html>  
```  
  
 テンプレートが、変数部分がプログラム コードにより置き換えらた HTML ページとなっていることに注目してください。 静的な HTML ページのプロトタイプを記述することで、このようなページのデザインを始めることができます。 様々なコンテントを生成するブログラム コードによりテーブルとその他の可変部分を次々と置き換えることができます。  
  
 アプリケーションでテンプレートを使用することにより、例えば、長い一連のステートメントを記述するよりも、出力の最終形式をみて容易に作成することができます。 出力の形式を変更が、簡単かつ確実になります。  
  
## <a name="creating-a-run-time-text-template-in-any-application"></a>任意のアプリケーションでの ランタイム テキスト テンプレートの作成  
  
#### <a name="to-create-a-run-time-text-template"></a>ランタイム テキスト テンプレートを作成するには  
  
1. ソリューション エクスプ ローラーで、プロジェクトのショートカット メニューの 選択**追加**、**新しい項目の**します。  
  
2. **新しい項目の追加** ダイアログ ボックスで、**ランタイム テキスト テンプレート** を選択します。 (で[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]下を見て**共通 Items\General**)。  
  
3. テンプレート ファイルの名前を入力します。  
  
    > [!NOTE]
    > テンプレート ファイルの名前は、生成されたコード内のクラス名として使用されます。 そのため、スペースまたは句読点を含めることはできません。  
  
4. **[追加]** をクリックします。  
  
     拡張子 **.tt** を持つ新しいファイルが作成されます。 その **カスタム ツール** プロパティには **TextTemplatingFilePreprocessor** が設定されています。 次の行が含まれています。  
  
    ```  
    <#@ template language="C#" #>  
    <#@ assembly name="System.Core" #>  
    <#@ import namespace="System.Linq" #>  
    <#@ import namespace="System.Text" #>  
    <#@ import namespace="System.Collections.Generic" #>  
    ```  
  
## <a name="converting-an-existing-file-to-a-run-time-template"></a>既存のファイルのランタイム テンプレートへの変換  
 テンプレートを作成する優れた方法は、既存の出力の例を変換することです。 たとえば、アプリケーションが HTML ファイルを生成する場合ならば、プレーンな HTML ファイルの作成から開始します。 正しく動作しいて、その外観が正しいことを確認してください。 含める、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]プロジェクト、テンプレートに変換します。  
  
#### <a name="to-convert-an-existing-text-file-to-a-run-time-template"></a>既存のテキスト ファイルをランタイム テンプレートに変換するには  
  
1. ファイルを含める、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]プロジェクト。 ソリューション エクスプ ローラーで、プロジェクトのショートカット メニューの 選択**追加**、**既存項目の**します。  
  
2. ファイルの設定 **カスタム ツール** プロパティを **TextTemplatingFilePreprocessor** にします。 ソリューション エクスプ ローラーで、ファイルのショートカット メニューの **プロパティ** を選択します。  
  
    > [!NOTE]
    > プロパティが既に設定されている場合は、**TextTemplatingFilePreprocessor** ではなく **TextTemplatingFileGenerator** であることを確認します。 拡張子 **.tt** のファイルをインクルードする場合に起こりえます。  
  
3. ファイル名の拡張子を **.tt** に変更します。 この手順は省略可能ですが、不適切なエディターでファイルを開いてしまうことを防ぎます。  
  
4. ファイル名の主要部分から、スペースや句読点を削除します。 たとえば"My Web Page.tt"は適切ではないですが、"MyWebPage.tt"は適切です。 ファイル名は、生成されたコード内のクラス名として使用されます。  
  
5. ファイルの先頭に次の行を挿入します。 Visual Basic プロジェクトで作業している場合は、"C#" が "VB" に置き換えられます。  
  
     `<#@ template language="C#" #>`  
  
## <a name="the-content-of-the-run-time-template"></a>ランタイム テンプレートの内容  
  
### <a name="template-directive"></a>テンプレート ディレクティブ  
 ファイルが作成された時のように、テンプレートの最初の行は次のようにしてください。  
  
 `<#@ template language="C#" #>`  
  
 language パラメーターは、プロジェクトの言語によって異なります。  
  
### <a name="plain-content"></a>プレーン コンテンツ  
 アプリケーションが生成したいテキストを含む **.tt** ファイルを編集します。 例えば:  
  
```  
<html><body>  
<h1>Sales for January</h2>  
<!-- table to be inserted here -->  
This report is Company Confidential.  
</body></html>  
```  
  
### <a name="embedded-program-code"></a>埋め込まれたプログラム コード  
 プログラム コードは`<#`と`#>`の間に挿入します。 例えば:  
  
```csharp  
<table>  
    <# for (int i = 1; i <= 10; i++)  
       { #>  
         <tr><td>Test name <#= i #> </td>  
             <td>Test value <#= i * i #> </td> </tr>  
    <# } #>  
 </table>  
```  
  
```vb  
<table>  
<#  
    For i As Integer = 1 To 10  
#>  
    <tr><td>Test name <#= i #> </td>  
      <td>Test value <#= i*i #> </td></tr>  
<#  
    Next  
#>  
</table>  
  
```  
  
 ステートメントは、`<# ... #>`の間に挿入され、式は`<#= ... #>`の間に挿入されていることにことに注意してください。 詳細については、次を参照してください。 [T4 テキスト テンプレートの作成](../modeling/writing-a-t4-text-template.md)  
  
## <a name="using-the-template"></a>テンプレートの使用  
  
### <a name="the-code-built-from-the-template"></a>テンプレートから作成されるコード  
 保存するたびに、 **.tt**ファイル、子会社 **.cs**または **.vb**ファイルが生成されます。 ソリューション エクスプ ローラーでこのファイルを表示するには展開、 **.tt**ファイル ノード。 Visual Basic プロジェクトですることがクリックした後、ノードを展開**すべてのファイル**ソリューション エクスプ ローラーのツールバー。  
  
 この関連会社のファイルと呼ばれるメソッドを含む部分クラスが含まれている通知`TransformText()`します。 このメソッドは、アプリケーションから呼び出すことができます。  
  
### <a name="generating-text-at-run-time"></a>実行時のテキストの生成  
 アプリケーション コードでは、このような呼び出しを使用して、テンプレートのコンテンツを生成できます。  
  
```csharp  
MyWebPage page = new MyWebPage();  
String pageContent = page.TransformText();  
System.IO.File.WriteAllText("outputPage.html", pageContent);  
  
```  
  
```vb  
Dim page = New My.Templates.MyWebPage  
Dim pageContent = page.TransformText()  
System.IO.File.WriteAllText("outputPage.html", pageContent)  
  
```  
  
 生成されるクラスを特定の名前空間に配置するには、テキスト テンプレート ファイルの **カスタム ツールの Namespace** プロパティを設定します。  
  
### <a name="debugging-runtime-text-templates"></a>ランタイム テキスト テンプレートのデバッグ  
 通常のコードと同じ方法でランタイム テキスト テンプレートをデバッグしテストします。  
  
 テキスト テンプレートでは、ブレークポイントを設定できます。 Visual Studio からデバッグ モードでアプリケーションを開始する場合は、コードをステップ実行し、通常の方法でウォッチ式を評価できます。  
  
### <a name="passing-parameters-in-the-constructor"></a>コンストラクターでのパラメーターの引き渡し  
 通常、テンプレートでは、アプリケーションの他の部分から一部のデータをインポートする必要があります。 これを簡単にするために、テンプレートによって作成されるコードは、部分クラスになっています。 プロジェクトの別のファイルで、同じクラスの別の部分を作成できます。 そのファイルには、パラメーター、プロパティ、およびテンプレートでは、埋め込まれているコードと、アプリケーションの残りの部分の両方にアクセスできる関数を持つコンス トラクターを含めることができます。  
  
 たとえば、**MyWebPageCode.cs** という別のファイルを作成し、  
  
```csharp  
partial class MyWebPage  
{  
    private MyData m_data;  
    public MyWebPage(MyData data) { this.m_data = data; }}  
```  
  
 **MyWebPage.tt** というテンプレート ファイルで次のように記述し、  
  
```csharp  
<h2>Sales figures</h2>  
<table>  
<# foreach (MyDataItem item in m_data.Items)   
   // m_data is declared in MyWebPageCode.cs  
   { #>  
      <tr><td> <#= item.Name #> </td>  
          <td> <#= item.Value #> </td></tr>  
<# } // end of foreach  
#>  
</table>  
```  
  
 アプリケーションでこのテンプレートを使用します。  
  
```csharp  
MyData data = ...;  
MyWebPage page = new MyWebPage(data);  
String pageContent = page.TransformText();  
System.IO.File.WriteAllText("outputPage.html", pageContent);  
```  
  
#### <a name="constructor-parameters-in-visual-basic"></a>Visual Basic でのコンストラクターのパラメーター  
 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]、別のファイル**MyWebPageCode.vb**が含まれています。  
  
```vb  
Namespace My.Templates  
  Partial Public Class MyWebPage  
    Private m_data As MyData  
    Public Sub New(ByVal data As MyData)  
      m_data = data  
    End Sub  
  End Class  
End Namespace  
```  
  
 テンプレート ファイルには次の内容を記述し、  
  
```vb  
<#@ template language="VB" #>  
<html><body>  
<h1>Sales for January</h2>  
<table>  
<#  
    For Each item In m_data.Items  
#>  
    <tr><td>Test name <#= item.Name #> </td>  
      <td>Test value <#= item.Value #> </td></tr>  
<#  
    Next  
#>  
</table>  
This report is Company Confidential.  
</body></html>  
  
```  
  
 テンプレート コンス トラクターでパラメーターを渡すことによって呼び出されます。  
  
```vb  
Dim data = New My.Templates.MyData  
    ' Add data values here ....  
Dim page = New My.Templates.MyWebPage(data)  
Dim pageContent = page.TransformText()  
System.IO.File.WriteAllText("outputPage.html", pageContent)  
  
```  
  
#### <a name="passing-data-in-template-properties"></a>テンプレートのプロパティでデータを渡す  
 データ テンプレートを渡すことの代替方法では、部分クラス定義内のテンプレート クラスにパブリック プロパティを追加します。 `TransformText()` を呼び出す前に、アプリケーションでプロパティを設定します。  
  
 部分定義で、テンプレート クラスにフィールドを追加することもできます。 これは、結果、連続的に、テンプレート実行の間でデータを渡すことができます。  
  
### <a name="use-partial-classes-for-code"></a>部分クラスを使用するコード  
 多くの開発者は、テンプレート内で大量のコードを作成することを回避することを好みます。 代わりに、テンプレート ファイルと同じ名前を持つ部分クラスでメソッドを定義します。 テンプレートからこれらのメソッドを呼び出します。 この方法で、テンプレートではより明確にどのようなターゲット出力文字列のようになります。 結果の外観に関する議論を、表示するデータを作成するロジックから分離できます。  
  
### <a name="assemblies-and-references"></a>アセンブリと参照  
 場合は、テンプレート コードなど、.NET またはその他のアセンブリの参照を**System.Xml.dll**、プロジェクトに追加する必要があります**参照**通常の方法でします。  
  
 `using`ステートメントといった方法で名前空間をインポートする場合は、`import`ディレクティブで行います。  
  
```  
<#@ import namespace="System.Xml" #>  
```  
  
 これらのディレクティブは、`<#@template`ディレクティブ直後のファイルの先頭に配置する必要があります。  
  
### <a name="shared-content"></a>共有コンテンツ  
 複数のテンプレート間で共有されるテキストがあれば、別のファイルに配置およびを表示する各ファイルに含めることできます。  
  
```  
<#@include file="CommonHeader.txt" #>  
```  
  
 含まれるコンテンツは、プログラム コードやプレーン テキストでのあらゆる組み合わせを含めることができ、それには、その他の include ディレクティブおよび他のディレクティブを含ませることができます。  
  
 include ディレクティブは、テンプレート ファイルまたはインクルード ファイルのテキスト内の任意の場所で使用できます。  
  
### <a name="inheritance-between-run-time-text-templates"></a>ランタイム テキスト テンプレート間の継承  
 抽象クラスになりうる基底クラス テンプレートを記述することで、実行時テンプレート間でコンテンツを共有することができます。 `<@#template#>` ディレクティブの `inherits` パラメーターを使用して、別のランタイム テンプレート クラスを参照します。  
  
#### <a name="inheritance-pattern-fragments-in-base-methods"></a>継承パターン:基本メソッドのフラグメント  
 次の例で使用されるパターンでは、次の点に注意してください。  
  
- 基底クラス`SharedFragments`は、クラス機能ブロック`<#+ ... #>`内でメソッドを定義します。  
  
- 基底クラスには、フリー テキストは含まれません。 代わりに、すべてのテキスト ブロックは、クラスの機能のメソッド内で発生します。  
  
- 派生クラスは、`SharedFragments`で定義されているメソッドを呼び出します。  
  
- アプリケーションは、派生クラスの `TextTransform()` メソッドを呼び出します。基底クラス`SharedFragments`を変換しません。  
  
- 基本と派生クラスの両方が実行時テキスト テンプレート: これは、**カスタム ツール**プロパティに設定されて**TextTemplatingFilePreprocessor**します。  
  
  **SharedFragments.tt:**  
  
```csharp  
<#@ template language="C#" #>  
<#+  
protected void SharedText(int n)  
{  
#>  
   Shared Text <#= n #>  
<#+  
}  
// Insert more methods here if required.  
#>  
  
```  
  
 **MyTextTemplate1.tt:**  
  
```csharp  
<#@ template language="C#" inherits="SharedFragments" #>  
begin 1  
   <# SharedText(2); #>  
end 1  
  
```  
  
 **MyProgram.cs:**  
  
```csharp  
...   
MyTextTemplate1 t1  = new MyTextTemplate1();  
string result = t1.TransformText();  
Console.WriteLine(result);  
```  
  
 **結果の出力:**  
  
```  
begin 1  
    Shared Text 2  
end 1  
```  
  
#### <a name="inheritance-pattern-text-in-base-body"></a>継承パターン:基本の本文内のテキスト  
 テンプレートの継承を使用する別の方法は、基底テンプレートの中で大きなテキスト定義することです。 派生テンプレートは、ベースのコンテンツに適合したデータと テキスト フラグメントを提供します。  
  
 **AbstractBaseTemplate1.tt:**  
  
```csharp  
<#@ template language="C#" #>  
  
Here is the description for this derived template:  
  <#= this.Description #>  
  
Here is the fragment specific to this derived template:  
<#   
  this.PushIndent("  ");  
  SpecificFragment(42);   
  this.PopIndent();  
#>  
End of common template.  
<#+   
  // State set by derived class before calling TextTransform:  
  protected string Description = "";  
  // 'abstract' method to be defined in derived classes:  
  protected virtual void SpecificFragment(int n) { }  
#>  
  
```  
  
 **DerivedTemplate1.tt:**  
  
```csharp  
<#@ template language="C#" inherits="AbstractBaseTemplate1" #>  
<#   
  // Set the base template properties:  
  base.Description = "Description for this derived class";   
  
  // Run the base template:  
  base.TransformText();  
  
#>  
End material for DerivedTemplate1.  
  
<#+  
// Provide a fragment specific to this derived template:  
  
protected override void SpecificFragment(int n)  
{  
#>  
   Specific to DerivedTemplate1 : <#= n #>  
<#+  
}  
#>  
  
```  
  
 **アプリケーション コード:**  
  
```csharp  
...   
DerivedTemplate1 t1 = new DerivedTemplate1();  
string result = t1.TransformText();  
Console.WriteLine(result);  
```  
  
 **結果の出力:**  
  
```  
Here is the description for this derived template:  
  Description for this derived class  
  
Here is the fragment specific to this derived template:  
     Specific to DerivedTemplate1 : 42  
End of common template.  
End material for DerivedTemplate1.  
```  
  
## <a name="related-topics"></a>関連トピック  
 デザイン時テンプレート:アプリケーションの一部になるコードを生成するテンプレートを使用する場合を参照してください[T4 テキスト テンプレートを使用したデザイン時コード生成](../modeling/design-time-code-generation-by-using-t4-text-templates.md)します。  
  
 実行時テンプレートは、コンパイル時にテンプレートおよびその内容を決定する、任意のアプリケーションで使用できます。 作成する場合は、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]拡張機能を実行時に、「テンプレートからテキストを生成する[VS 拡張機能でテキスト変換を呼び出す](../modeling/invoking-text-transformation-in-a-vs-extension.md)します。  
  
## <a name="see-also"></a>関連項目  
 [コードの生成と T4 テキスト テンプレート](../modeling/code-generation-and-t4-text-templates.md)   
 [T4 テキスト テンプレートの作成](../modeling/writing-a-t4-text-template.md)   
 [T4 の理解。Oleg Sych では、前処理されたテキスト テンプレート](https://github.com/olegsych/T4Toolbox)
