---
title: '方法: ドメイン固有言語デザイナーを拡張 |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: fa807f1b-2780-491e-925b-abbfd31b2bfa
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8c02dbf550ca1621a17d2b674a522e1e4f4bcc1c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546942"
---
# <a name="how-to-extend-the-domain-specific-language-designer"></a>方法: ドメイン固有言語デザイナーを拡張する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DSL 定義を編集するために使用するデザイナーには、拡張機能を行うことができます。 行うことができます メニューのコマンドの追加のハンドラーがドラッグし、ジェスチャ、および特定の種類の値またはリレーションシップを変更するときにトリガーされるルールをダブルクリックを追加する拡張機能の種類。 拡張機能は、として、Visual Studio Integration Extension (VSIX) パッケージ化および他のユーザーに配布できます。  
  
 サンプル コードとこの機能の詳細については、Visual Studio を参照してください。 [Visualization and Modeling SDK (VMSDK) Web サイト](http://go.microsoft.com/fwlink/?LinkID=186128)します。  
  
## <a name="setting-up-the-solution"></a>ソリューションのセットアップ  
 プロジェクトをエクスポートする、拡張機能のコードを含むプロジェクトと VSIX プロジェクトを設定します。 ソリューションは、同じ VSIX に採用されている他のプロジェクトを含めることができます。  
  
#### <a name="to-create-a-dsl-designer-extension-solution"></a>DSL デザイナーの拡張機能ソリューションを作成するには  
  
1. クラス ライブラリ プロジェクト テンプレートを使用して新しいプロジェクトを作成します。 **新しいプロジェクト**ダイアログ ボックスで、をクリックして**Visual c#** しをクリックして、中央のウィンドウで、**クラス ライブラリ**します。  
  
     このプロジェクトには、拡張機能のコードが含まれます。  
  
2. VSIX プロジェクト テンプレートを使用して新しいプロジェクトを作成します。 **新しいプロジェクト** ダイアログ ボックスで、展開**Visual c#**、 をクリックして**拡張**、中央のウィンドウを選択し、 **VSIX プロジェクト**します。  
  
     選択**ソリューションに追加**します。  
  
     Source.extension.vsixmanifest は、VSIX マニフェスト エディターで開きます。  
  
3. コンテンツのフィールドの上をクリックして**コンテンツの追加**します。  
  
4. **コンテンツの追加**ダイアログ ボックスで、セット**コンテンツの種類を選択します。** に**MEF コンポーネント**、設定と**プロジェクト**クラス ライブラリ プロジェクトにします。  
  
5. をクリックして**エディションの**ことを確認し、 **Visual Studio Enterprise**がチェックされます。  
  
6. VSIX プロジェクトがソリューションのスタートアップ プロジェクトであることを確認します。  
  
7. クラス ライブラリ プロジェクトでは、次のアセンブリへの参照を追加します。  
  
     Microsoft.VisualStudio.CoreUtility  
  
     Microsoft.VisualStudio.Modeling.Sdk.11.0  
  
     Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0  
  
     Microsoft.VisualStudio.Modeling.Sdk.DslDefinition.11.0  
  
     Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0  
  
     System.ComponentModel.Composition  
  
     System.Drawing  
  
     System.Drawing.Design  
  
     System.Windows.Forms  
  
## <a name="testing-and-deployment"></a>テストと展開  
 このトピックでは、拡張機能のいずれかをテストするには、ビルドし、ソリューションを実行します。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] の実験用のインスタンスが開きます。 このインスタンスでは、DSL ソリューションを開きます。 DslDefinition ダイアグラムを編集します。 拡張機能の動作を確認できます。  
  
 主に、拡張機能を展開する[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]、他のコンピューターに次の手順に従います。  
  
1. VSIX プロジェクトの箱で、VSIX のインストール ファイルを見つける\\*\*\\\*.vsix  
  
2. 対象のコンピュータにこのファイルをコピーし、Windows エクスプ ローラー (またはファイル エクスプ ローラー) でそれをダブルクリックします。  
  
    [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]拡張機能がインストールされていることを確認する拡張機能マネージャーを開きます。  
  
   拡張機能をアンインストールするには、次の手順を実行します。  
  
3. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]の**ツール** メニューのをクリックして**拡張機能マネージャー**です。  
  
4. 拡張機能を選択して削除します。  
  
## <a name="adding-a-shortcut-menu-command"></a>ショートカット メニュー コマンドの追加  
 DSL デザイナー画面または DSL エクスプ ローラー ウィンドウに表示されるショートカット メニューのコマンドを作成するには、次のようなクラスを記述します。  
  
 クラスを実装する必要があります`ICommandExtension`は属性が必要と`DslDefinitionModelCommandExtension`します。  
  
```  
using System.Collections.Generic;  
using System.ComponentModel.Composition;  
using System.Linq;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;  
using Microsoft.VisualStudio.Modeling.DslDefinition;  
using Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement;  
using Microsoft.VisualStudio.Modeling.DslDesigner;  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
  
namespace Fabrikam.SimpleDslDesignerExtension  
{  
  /// <summary>  
  /// Command extending the DslDesigner.  
  /// </summary>  
  [DslDefinitionModelCommandExtension]   
  public class MyDslDesignerCommand : ICommandExtension  
  {  
    /// <summary>  
    /// Selection Context for this command  
    /// </summary>  
    [Import]  
    IVsSelectionContext SelectionContext { get; set; }  
  
    /// <summary>  
    /// Is the command visible and active?  
    /// This is called when the user right-clicks.  
    /// </summary>  
    public void QueryStatus(IMenuCommand command)  
    {  
      command.Visible = true;  
      // Is there any selected DomainClasses in the Dsl explorer?  
      command.Enabled =   
        SelectionContext.AtLeastOneSelected<DomainClass>();  
  
      // Is there any selected ClassShape on the design surface?  
      command.Enabled |=   
        (SelectionContext.GetCurrentSelection<ClassShape>()  
                .Count() > 0);  
    }  
    /// <summary>  
    /// Executes the command   
    /// </summary>  
    /// <param name="command">Command initiating this action</param>  
    public void Execute(IMenuCommand command)  
    {  
      ...  
    }  
    /// <summary>  
    /// Label for the command  
    /// </summary>  
    public string Text  
    {  
      get { return "My Command"; }  
    }  
  }  
}  
```  
  
## <a name="handling-mouse-gestures"></a>マウス ジェスチャの処理  
 コードは、メニュー コマンドのコードに似ています。  
  
```  
[DslDefinitionModelGestureExtension]  
 class MouseGesturesExtensions : IGestureExtension  
 {  
  /// <summary>  
  /// Double-clicking on a shape representing a Domain model element displays this model element in a dialog box  
  /// </summary>  
  /// <param name="targetElement">Shape element on which the user has clicked</param>  
  /// <param name="diagramPointEventArgs">event args for this double-click</param>  
  public void OnDoubleClick(ShapeElement targetElement,  
       DiagramPointEventArgs diagramPointEventArgs)  
  {  
   ModelElement modelElement = PresentationElementHelper.  
        GetDslDefinitionModelElement(targetElement);  
   if (modelElement != null)  
   {  
    MessageBox.Show(string.Format(  
      "Double clicked on {0}", modelElement.ToString()),   
      "Model element double-clicked");  
   }  
  }  
  
  /// <summary>  
  /// Tells if the DslDesigner can consume the to-be-dropped information  
  /// </summary>  
  /// <param name="targetMergeElement">Shape on which we try to drop</param>  
  /// <param name="diagramDragEventArgs">Drop event</param>  
  /// <returns><c>true</c> if we can consume the to be dropped data, and <c>false</c> otherwise</returns>  
  public bool CanDragDrop(ShapeElement targetMergeElement,  
        DiagramDragEventArgs diagramDragEventArgs)  
  {  
   if (diagramDragEventArgs.Data.GetDataPresent(DataFormats.FileDrop))  
   {  
    diagramDragEventArgs.Effect = DragDropEffects.Copy;  
    return true;  
   }  
   return false;  
  }  
  
  /// <summary>  
  /// Processes the drop by displaying the dropped text  
  /// </summary>  
  /// <param name="targetMergeElement">Shape on which we dropped</param>  
  /// <param name="diagramDragEventArgs">Drop event</param>  
  public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)  
  {  
   if (diagramDragEventArgs.Data.GetDataPresent(DataFormats.FileDrop))  
   {  
    string[] droppedFiles =   
      diagramDragEventArgs.Data.  
               GetData(DataFormats.FileDrop) as string[];  
    MessageBox.Show(string.Format("Dropped text {0}",  
        string.Join("\r\n", droppedFiles)), "Dropped Text");  
   }  
  }  
 }  
```  
  
## <a name="responding-to-value-changes"></a>値の変更に応答してください。  
 このハンドラーでは、正常に動作するドメイン モデルが必要です。 単純なドメイン モデルを提供しています。  
  
```  
using System.Diagnostics;  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.DslDefinition;  
namespace Fabrikam.SimpleDslDesignerExtension  
{  
  /// <summary>  
  /// Rule firing when the type of a domain model property is changed. The change is displayed  
  /// in the debugger (Output window of the Visual Studio instance debugging this extension)  
  /// </summary>  
  [RuleOn(typeof(PropertyHasType))]  
  public class DomainPropertyTypeChangedRule : RolePlayerChangeRule  
  {  
    /// <summary>  
    /// Method called when the Type of a Domain Property   
    /// is changed by the user in a DslDefinition  
    /// </summary>  
    /// <param name="e"></param>  
    public override void RolePlayerChanged(RolePlayerChangedEventArgs e)  
    {  
      // We are only interested in the type  
      if (e.DomainRole.Id == PropertyHasType.TypeDomainRoleId)  
      {  
        PropertyHasType relationship =   
           e.ElementLink as PropertyHasType;  
        DomainType newType = e.NewRolePlayer as DomainType;  
        DomainType oldType = e.OldRolePlayer as DomainType;  
        DomainProperty property = relationship.Property;  
  
         // We write about the Type change in the debugguer  
        Debug.WriteLine(string.Format("The type of the Domain property '{0}' of domain class '{1}' changed from '{2}' to '{3}'",  
          property.Name,  
          property.Class.Name,  
          oldType.GetFullName(false),  
          newType.GetFullName(false))  
} }  }  );  
```  
  
 次のコードでは、単純なモデルを実装します。 プレース ホルダーを置き換えるには、新しい GUID を作成します。  
  
```  
using System;  
using System.ComponentModel.Composition;  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.DslDefinition;  
namespace Fabrikam.SimpleDslDesignerExtension  
{  
    /// <summary>  
    /// Simplest possible domain model   
    /// needed only for extension rules.   
    /// </summary>  
    [DomainObjectId(SimpleDomainModelExtension.DomainModelId)]  
    public class SimpleDomainModelExtension : DomainModel  
    {  
        // Id of this domain model extension   
        // Please replace this with a new GUID:  
        public const string DomainModelId =   
                  "00000000-0000-0000-0000-000000000000";  
  
        /// <summary>  
        /// Constructor for the domain model extension  
        /// </summary>  
        /// <param name="store">Store in which the domain model will be loaded</param>  
        public SimpleDomainModelExtension(Store store)  
            : base(store, new Guid(SimpleDomainModelExtension.DomainModelId))  
        {  
  
        }  
  
        /// <summary>  
        /// Rules brought by this domain model extension  
        /// </summary>  
        /// <returns></returns>  
        protected override System.Type[] GetCustomDomainModelTypes()  
        {  
            return new Type[] {  
                     typeof(DomainPropertyTypeChangedRule)  
                              };  
        }  
    }  
  
    /// <summary>  
    /// Provider for the DomainModelExtension  
    /// </summary>  
    [Export(typeof(DomainModelExtensionProvider))]    [ProvidesExtensionToDomainModel(typeof(DslDefinitionModelDomainModel))]  
    public class SimpleDomainModelExtensionProvider   
          : DomainModelExtensionProvider  
    {  
        /// <summary>  
        /// Extension model type  
        /// </summary>  
        public override Type DomainModelType  
        {  
            get  
            {  
                return typeof(SimpleDomainModelExtension);  
            }  
        }  
  
    }  
}  
```
