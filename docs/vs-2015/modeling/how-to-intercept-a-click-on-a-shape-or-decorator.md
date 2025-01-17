---
title: '方法: シェイプまたはデコレーターに対するクリックして |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
ms.assetid: e2bc3124-c0c0-4104-9779-a5bf565d7f51
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 865cd15416fbc901b6c5e58e1d83385f64f6a5a8
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441073"
---
# <a name="how-to-intercept-a-click-on-a-shape-or-decorator"></a>方法: シェイプまたはデコレーターに対するクリック操作を受け取る
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

次の手順では、図形または、アイコン デコレーターに対するクリックする方法を説明します。 数回のクリックをインターセプトできるをダブルクリックしたにドラッグ、およびその他のジェスチャをし応答要素。  
  
## <a name="to-intercept-clicks-on-shapes"></a>図形のクリックをインターセプトするには  
 生成されたコード ファイルから別のコード ファイルで、Dsl プロジェクトでは、shape クラスの部分クラス定義を作成します。 オーバーライド`OnDoubleClick()`または名前の先頭にある他の方法の 1 つ`On...`します。 例:  
  
```  
public partial class MyShape // change  
  {  
    public override void OnDoubleClick(DiagramPointEventArgs e)  
    {  
      base.OnDoubleClick(e);  
      System.Windows.Forms.MessageBox.Show("Click");  
      e.Handled = true;  
  }  }  
```  
  
> [!NOTE]
> 設定`e.Handled`に`true`図形または図に渡されるイベントの場合を除き、します。  
  
## <a name="to-intercept-clicks-on-decorators"></a>デコレーターの数回のクリックをインターセプトするには  
 イメージのデコレーターは、OnDoubleClick メソッドを持つ ImageField クラスのインスタンスで実行されます。 ImageField サブクラスを作成する場合、数回のクリックをインターセプトすることができます。 フィールドは InitializeShapeFields メソッドで設定されます。 そのため、通常 ImageField ではなく、サブクラスのインスタンスを作成するには、そのメソッドを変更する必要があります。 InitializeShapeFields メソッドは、shape クラスの生成されたコード内に示します。 シェイプ クラスを上書きするには、設定した場合、`Generates Double Derived`プロパティを次の手順で説明します。  
  
 InitializeShapeFields はインスタンス メソッドが、1 回だけクラスごとに呼び出されます。 そのため、ダイアグラム内の各図形の 1 つインスタンスではなく、各クラスの各フィールドに対して ClickableImageField の 1 つだけのインスタンスが存在します。 ユーザーをダブルクリックすると、インスタンスは、例のコードに示すよう先のインスタンスにヒットしたを識別する必要があります。  
  
#### <a name="to-intercept-a-click-on-an-icon-decorator"></a>アイコン、デコレーターに対するクリックするには  
  
1. 開くか、DSL ソリューションを作成します。  
  
2. 選択またはアイコン デコレータでは、図形を作成し、ドメイン クラスにマップします。  
  
3. コード ファイル内のファイルとは別に、`GeneratedCode`フォルダー、ImageField の新しいサブクラスを作成します。  
  
    ```  
    using Microsoft.VisualStudio.Modeling;  
    using Microsoft.VisualStudio.Modeling.Design;  
    using Microsoft.VisualStudio.Modeling.Diagrams;  
    using System.Collections.Generic;  
    using System.Linq;  
  
    namespace Fabrikam.MyDsl { // Change to your namespace  
    internal class ClickableImageField : ImageField  
    {  
      // You can also override OnClick and so on.  
      public override void OnDoubleClick(DiagramPointEventArgs e)  
      {  
        base.OnDoubleClick(e);  
        // Work out which instance was hit.  
        MyShape shapeHit = e.HitDiagramItem.Shape as MyShape;  
        if (shapeHit != null)  
        {  
          MyDomainClass element =   
              shapeHit.ModelElement as MyDomainClass;  
          System.Windows.Forms.MessageBox.Show(  
             "Double click on shape for " + element.Name);  
          // If we do not set Handled, the event will  
          // be passed to the containing shape:  
          e.Handled = true;  
        }  
      }  
  
       public ClickableImageField(string fieldName)  
         : base(fieldName)  
       { }  
    }  
    ```  
  
     処理済みイベントが含まれている図形に渡されるしたくない場合は true に設定してください。  
  
4. 次の部分クラス定義を追加することで、図形渡してで InitializeShapeFields メソッドをオーバーライドします。  
  
    ```  
    public partial class MyShape // change  
    {  
     protected override void InitializeShapeFields  
          (IList<ShapeField> shapeFields)  
     {  
      base.InitializeShapeFields(shapeFields);  
      // You can see the above method in MyShapeBase   
      // in the generated Shapes.cs  
      // It has already added fields for the Icons.  
      // So you will have to retrieve them and replace with your own.  
      ShapeField unwantedField = shapeFields.First  
          (field => field.Name == "IconDecorator1");  
      shapeFields.Remove(unwantedField);  
  
      // Now replicate the generated code from the base class   
      // in Shape.cs, but with your own image constructor.  
      ImageField field2 = new ClickableImageField("IconDecorator1");        
      field2.DefaultImage = ImageHelper.GetImage(  
        MyDslDomainModel.SingletonResourceManager  
        .GetObject("MyShapeIconDecorator1DefaultImage"));  
          shapeFields.Add(field2);  
    }  
    ```  
  
1. ソリューションをビルドして実行します。  
  
2. 図形のインスタンス上のアイコンをダブルクリックします。 テスト メッセージが表示されます。  
  
## <a name="intercepting-clicks-and-drags-on-compartmentshape-lists"></a>インターセプトをクリックしておよびドラッグ CompartmentShape リスト  
 次の例では、順序にドラッグしてコンパートメント シェイプで項目を変更することができます。 このコードを実行します。  
  
1. 使用して、新しい DSL ソリューションを作成、**クラス ダイアグラム**ソリューション テンプレート。  
  
    コンパートメント シェイプを含む独自のソリューションを操作することもできます。 このコードでは、シェイプによって表されるモデル要素と、コンパートメント リスト項目で表される要素間に埋め込みリレーションシップがあることを前提としています。  
  
2. 設定、 **Double Derived の生成**コンパートメント シェイプのプロパティ。  
  
3. 内のファイルに次のコードを追加、 **Dsl**プロジェクト。  
  
4. 独自の DSL を一致するようにこのコードではドメイン クラスとシェイプの名前を調整します。  
  
   要約すると、コードの次のように動作します。 この例で`ClassShape`コンパートメント シェイプの名前を指定します。  
  
- マウス イベント ハンドラーのセットは、作成時に、各コンパートメント インスタンスにアタッチされます。  
  
- `ClassShape.MouseDown`イベントは、現在の項目を格納します。  
  
- 移動したときに、マウス、現在のアイテムから MouseAction のインスタンスが作成されたカーソルを設定し、解放されるまでマウスをキャプチャします。  
  
     項目のテキストを選択するなど、他のマウス操作で干渉を避けるため、マウスが、元の項目を左になるまで、MouseAction は作成されません。  
  
     MouseAction を作成する代わりには、MouseUp リッスンするように単純になります。 ただし、これは正しく機能しません、コンパートメントの外側にドラッグした後、マウスを離した場合。 MouseAction はマウスがリリースされた場所に関係なく、適切なアクションを実行できません。  
  
- マウスがリリースされると、MouseAction.MouseUp はモデル要素間のリンクの順序を並べ替えます。  
  
- ロールの順序の変更には、表示を更新する規則が適用されます。 この動作が既に定義されているし、コードを追加する必要はありません。  
  
```csharp  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Design;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
using System.Collections.Generic;  
using System.Linq;  
  
// This sample allows users to re-order items in a compartment shape by dragging.  
  
// This example is built on the "Class Diagrams" solution template of VMSDK (DSL Tools).  
// You will need to change the following domain class names to your own:  
// ClassShape = a compartment shape  
// ClassModelElement = the domain class displayed using a ClassShape  
// This code assumes that the embedding relationships   
// displayed in the compartments don't use inheritance   
// (don't have base or derived domain relationships).  
  
namespace Company.CompartmentDrag  
{  
 /// <summary>  
 /// Manage the mouse while dragging a compartment item.  
 /// </summary>  
 public class CompartmentDragMouseAction : MouseAction  
 {  
  private ModelElement sourceChild;  
  private ClassShape sourceShape;  
  private RectangleD sourceCompartmentBounds;  
  
  public CompartmentDragMouseAction(ModelElement sourceChildElement, ClassShape sourceParentShape, RectangleD bounds)  
   : base (sourceParentShape.Diagram)  
  {  
   sourceChild = sourceChildElement;  
   sourceShape = sourceParentShape;  
   sourceCompartmentBounds = bounds; // For cursor.  
  }  
  
  /// <summary>  
  /// Call back to the source shape to drop the dragged item.  
  /// </summary>  
  /// <param name="e"></param>  
  protected override void OnMouseUp(DiagramMouseEventArgs e)  
  {  
   base.OnMouseUp(e);  
   sourceShape.DoMouseUp(sourceChild, e);  
   this.Cancel(e.DiagramClientView);  
   e.Handled = true;  
  }  
  
  /// <summary>  
  /// Ideally, this shouldn't happen. This action should only be active  
  /// while the mouse is still pressed. However, it can happen if you  
  /// move the mouse rapidly out of the source shape, let go, and then   
  /// click somewhere else in the source shape.  
  /// </summary>  
  /// <param name="e"></param>  
  protected override void OnMouseDown(DiagramMouseEventArgs e)  
  {  
   base.OnMouseDown(e);  
   this.Cancel(e.DiagramClientView);  
   e.Handled = false;  
  }  
  
  /// <summary>  
  /// Display an appropriate cursor while the drag is in progress:  
  /// Up-down arrow if we are inside the original compartment.  
  /// No entry if we are elsewhere.  
  /// </summary>  
  /// <param name="currentCursor"></param>  
  /// <param name="diagramClientView"></param>  
  /// <param name="mousePosition"></param>  
  /// <returns></returns>  
  public override System.Windows.Forms.Cursor GetCursor(System.Windows.Forms.Cursor currentCursor, DiagramClientView diagramClientView, PointD mousePosition)  
  {  
   // If the cursor is inside the original compartment, show up-down cursor.  
   return sourceCompartmentBounds.Contains(mousePosition)   
    ? System.Windows.Forms.Cursors.SizeNS // Up-down arrow.  
    : System.Windows.Forms.Cursors.No;  
  }  
 }  
  
 /// <summary>  
 /// Override some methods of the compartment shape.  
 /// *** GenerateDoubleDerived must be set for this shape in DslDefinition.dsl. ****  
 /// </summary>  
 public partial class ClassShape  
 {  
  /// <summary>  
  /// Model element that is being dragged.  
  /// </summary>  
  private static ClassModelElement dragStartElement = null;  
  /// <summary>  
  /// Absolute bounds of the compartment, used to set the cursor.  
  /// </summary>  
  private static RectangleD compartmentBounds;  
  
  /// <summary>  
  /// Attach mouse listeners to the compartments for the shape.  
  /// This is called once per compartment shape.  
  /// The base method creates the compartments for this shape.  
  /// </summary>  
  public override void EnsureCompartments()  
  {  
   base.EnsureCompartments();  
   foreach (Compartment compartment in this.NestedChildShapes.OfType<Compartment>())  
   {  
    compartment.MouseDown += new DiagramMouseEventHandler(compartment_MouseDown);  
    compartment.MouseUp += new DiagramMouseEventHandler(compartment_MouseUp);  
    compartment.MouseMove += new DiagramMouseEventHandler(compartment_MouseMove);  
   }  
  }  
  
  /// <summary>  
  /// Remember which item the mouse was dragged from.  
  /// We don't create an Action immediately, as this would inhibit the  
  /// inline text editing feature. Instead, we just remember the details  
  /// and will create an Action when/if the mouse moves off this list item.  
  /// </summary>  
  /// <param name="sender"></param>  
  /// <param name="e"></param>  
  void compartment_MouseDown(object sender, DiagramMouseEventArgs e)  
  {  
   dragStartElement = e.HitDiagramItem.RepresentedElements  
     .OfType<ClassModelElement>().FirstOrDefault();  
   compartmentBounds = e.HitDiagramItem.Shape.AbsoluteBoundingBox;  
  }  
  
  /// <summary>  
  /// When the mouse moves away from the initial list item,  
  /// but still inside the compartment, create an Action   
  /// to supervise the cursor and handle subsequent mouse events.  
  /// Transfer the details of the initial mouse position to the Action.  
  /// </summary>  
  /// <param name="sender"></param>  
  /// <param name="e"></param>  
  void compartment_MouseMove(object sender, DiagramMouseEventArgs e)  
  {  
   if (dragStartElement != null)  
   {  
    if (dragStartElement != e.HitDiagramItem.RepresentedElements.OfType<ClassModelElement>().FirstOrDefault())  
    {  
     e.DiagramClientView.ActiveMouseAction = new CompartmentDragMouseAction(dragStartElement, this, compartmentBounds);  
     dragStartElement = null;  
    }  
   }  
  }  
  
  /// <summary>  
  /// User has released the mouse button.   
  /// </summary>  
  /// <param name="sender"></param>  
  /// <param name="e"></param>  
  void compartment_MouseUp(object sender, DiagramMouseEventArgs e)  
  {  
    dragStartElement = null;  
  }  
  
  /// <summary>  
  /// Forget the source item if mouse up occurs outside the  
  /// compartment.  
  /// </summary>  
  /// <param name="e"></param>  
  public override void OnMouseUp(DiagramMouseEventArgs e)  
  {  
   base.OnMouseUp(e);  
   dragStartElement = null;  
  }  
  
  /// <summary>  
  /// Called by the Action when the user releases the mouse.  
  /// If we are still on the same compartment but in a different list item,  
  /// move the starting item to the position of the current one.  
  /// </summary>  
  /// <param name="dragFrom"></param>  
  /// <param name="e"></param>  
  public void DoMouseUp(ModelElement dragFrom, DiagramMouseEventArgs e)  
  {  
   // Original or "from" item:  
   ClassModelElement dragFromElement = dragFrom as ClassModelElement;  
   // Current or "to" item:  
   ClassModelElement dragToElement = e.HitDiagramItem.RepresentedElements.OfType<ClassModelElement>().FirstOrDefault();  
   if (dragFromElement != null && dragToElement != null)  
   {  
    // Find the common parent model element, and the relationship links:  
    ElementLink parentToLink = GetEmbeddingLink(dragToElement);  
    ElementLink parentFromLink = GetEmbeddingLink(dragFromElement);  
    if (parentToLink != parentFromLink && parentFromLink != null && parentToLink != null)  
    {  
     // Get the static relationship and role (= end of relationship):  
     DomainRelationshipInfo relationshipFrom = parentFromLink.GetDomainRelationship();  
     DomainRoleInfo parentFromRole = relationshipFrom.DomainRoles[0];  
     // Get the node in which the element is embedded, usually the element displayed in the shape:  
     ModelElement parentFrom = parentFromLink.LinkedElements[0];  
  
     // Same again for the target:  
     DomainRelationshipInfo relationshipTo = parentToLink.GetDomainRelationship();  
     DomainRoleInfo parentToRole = relationshipTo.DomainRoles[0];  
     ModelElement parentTo = parentToLink.LinkedElements[0];  
  
     // Mouse went down and up in same parent and same compartment:  
     if (parentTo == parentFrom && relationshipTo == relationshipFrom)  
     {  
      // Find index of target position:  
      int newIndex = 0;  
      var elementLinks = parentToRole.GetElementLinks(parentTo);  
      foreach (ElementLink link in elementLinks)  
      {  
       if (link == parentToLink) { break; }  
       newIndex++;  
      }  
  
      if (newIndex < elementLinks.Count)  
      {  
       using (Transaction t = parentFrom.Store.TransactionManager.BeginTransaction("Move list item"))  
       {  
        parentFromLink.MoveToIndex(parentFromRole, newIndex);  
        t.Commit();  
       }  
      }  
     }  
    }  
   }  
  }  
  
  /// <summary>  
  /// Get the embedding link to this element.  
  /// Assumes there is no inheritance between embedding relationships.  
  /// (If there is, you need to make sure you've got the relationship  
  /// that is represented in the shape compartment.)  
  /// </summary>  
  /// <param name="child"></param>  
  /// <returns></returns>  
  ElementLink GetEmbeddingLink(ClassModelElement child)  
  {  
   foreach (DomainRoleInfo role in child.GetDomainClass().AllEmbeddedByDomainRoles)  
   {  
    foreach (ElementLink link in role.OppositeDomainRole.GetElementLinks(child))  
    {  
     // Just the assume the first embedding link is the only one.  
     // Not a valid assumption if one relationship is derived from another.  
     return link;  
    }  
   }  
   return null;  
  }  
 }  
}  
  
```  
  
## <a name="see-also"></a>関連項目  
 [対応および変更の反映](../modeling/responding-to-and-propagating-changes.md)   
 [デコレーターのプロパティ](../modeling/properties-of-decorators.md)
