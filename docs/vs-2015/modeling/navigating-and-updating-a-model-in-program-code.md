---
title: プログラムコードでのモデルの移動と更新 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
ms.assetid: 1427ae91-be8a-4ce7-85df-00038faa2cbb
caps.latest.revision: 28
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4a923eaa04018aae8df48049c729216abc30e401
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2019
ms.locfileid: "68871850"
---
# <a name="navigating-and-updating-a-model-in-program-code"></a>プログラム コードにおけるモデル内の移動およびモデルの更新
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

モデル要素を作成および削除したり、それらのプロパティを設定したり、要素間のリンクを作成および削除したりするコードを記述できます。 すべての変更は、トランザクション内で行う必要があります。 図に要素が表示されている場合、図はトランザクションの終了時に自動的に "固定" されます。

## <a name="in-this-topic"></a>このトピックの内容
 [DSL 定義の例](#example)

 [モデル内の移動](#navigation)

 [クラス情報へのアクセス](#metadata)

 [トランザクション内で変更を実行する](#transaction)

 [モデル要素の作成](#elements)

 [リレーションシップリンクの作成](#links)

 [要素の削除](#deleteelements)

 [リレーションシップリンクの削除](#deletelinks)

 [リレーションシップのリンクの並べ替え](#reorder)

 [固定](#locks)

 [コピーと貼り付け](#copy)

 [ダイアグラムの移動と更新](#diagrams)

 [図形と要素間の移動](#views)

 [図形とコネクタのプロパティ](#shapeProperties)

 [DocView と Docview](#docdata)

 図形、コネクタ、図、およびモデル要素との関係については、別のトピックで説明します。 詳細については、「[方法 :図](../misc/how-to-navigate-and-update-a-diagram.md)に移動し、更新します。

## <a name="example"></a>DSL 定義の例
 これは、このトピックの例で使用する DslDefinition. dsl の主要な部分です。

 ![DSL 定義図&#45;ファミリツリーモデル](../modeling/media/familyt-person.png "FamilyT_Person")

 このモデルは、この DSL のインスタンスです。

 ![Tudor ファミリツリーモデル](../modeling/media/tudor-familytreemodel.png "Tudor_FamilyTreeModel")

### <a name="references-and-namespaces"></a>参照と名前空間
 このトピックのコードを実行するには、次を参照する必要があります。

 `Microsoft.VisualStudio.Modeling.Sdk.11.0.dll`

 コードでは、次の名前空間を使用します。

 `using Microsoft.VisualStudio.Modeling;`

 さらに、DSL が定義されているものとは別のプロジェクトにコードを記述する場合は、Dsl プロジェクトによってビルドされたアセンブリをインポートする必要があります。

## <a name="navigation"></a>モデル内の移動

### <a name="properties"></a>プロパティ
 DSL 定義で定義したドメインプロパティは、プログラムコードでアクセスできるプロパティになります。

 `Person henry = ...;`

 `if (henry.BirthDate < 1500) ...`

 `if (henry.Name.EndsWith("VIII")) ...`

 プロパティを設定する場合は、[トランザクション](#transaction)内で行う必要があります。

 `henry.Name = "Henry VIII";`

 DSL 定義の場合、プロパティの**種類**が**計算**されますが、設定することはできません。 詳細については、[計算とストレージのカスタム プロパティ](../modeling/calculated-and-custom-storage-properties.md)を参照してください。

### <a name="relationships"></a>リレーションシップ
 DSL 定義で定義したドメインリレーションシップは、プロパティのペアになります。1つはリレーションシップの端にあるクラスです。 DslDefinition ダイアグラムには、プロパティの名前がリレーションシップの各側のロールのラベルとして表示されます。 ロールの多重度に応じて、プロパティの型は、リレーションシップのもう一方の端のクラス、またはそのクラスのコレクションのいずれかになります。

 `foreach (Person child in henry.Children) { ... }`

 `FamilyTreeModel ftree = henry.FamilyTreeModel;`

 リレーションシップの反対側のプロパティは、常に相互に関係しています。 リンクが作成または削除されると、両方の要素のロールプロパティが更新されます。 次の式 (の`System.Linq`拡張機能を使用) は、この例の ParentsHaveChildren リレーションシップに対して常に true です。

 `(Person p) => p.Children.All(child => child.Parents.Contains(p))`

 `&& p.Parents.All(parent => parent.Children.Contains(p));`

 **Elementlinks**。 リレーションシップは、ドメインリレーションシップ型のインスタンスである*リンク*と呼ばれるモデル要素によっても表されます。 リンクには、常に1つのソース要素と1つのターゲット要素があります。 ソース要素とターゲット要素は同じにすることができます。

 リンクとそのプロパティにアクセスできます。

 `ParentsHaveChildren link = ParentsHaveChildren.GetLink(henry, edward);`

 `// This is now true:`

 `link == null || link.Parent == henry && link.Child == edward`

 既定では、リレーションシップの1つ以上のインスタンスがモデル要素のペアをリンクすることはできません。 しかし、DSL 定義`Allow Duplicates`の場合、リレーションシップに対してフラグが true に設定されていると、複数のリンクが存在し、を使用`GetLinks`する必要があります。

 `foreach (ParentsHaveChildren link in ParentsHaveChildren.GetLinks(henry, edward)) { ... }`

 リンクにアクセスするための他の方法もあります。 例:

 `foreach (ParentsHaveChildren link in     ParentsHaveChildren.GetLinksToChildren(henry)) { ... }`

 **非表示のロール。** DSL 定義では、特定のロールに対して **"プロパティが生成**されました" が**false**の場合、そのロールに対応するプロパティは生成されません。 ただし、リレーションシップのメソッドを使用してリンクにアクセスし、リンクを走査することはできます。

 `foreach (Person p in ParentsHaveChildren.GetChildren(henry)) { ... }`

 最もよく使用される例は<xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> 、モデル要素を図に表示する図形にリンクするリレーションシップです。

 `PresentationViewsSubject.GetPresentation(henry)[0] as PersonShape`

### <a name="the-element-directory"></a>要素ディレクトリ
 要素ディレクトリを使用して、ストア内のすべての要素にアクセスできます。

 `store.ElementDirectory.AllElements`

 要素を検索するためのメソッドもあります。次に例を示します。

 `store.ElementDirectory.FindElements(Person.DomainClassId);`

 `store.ElementDirectory.GetElement(elementId);`

## <a name="metadata"></a>クラス情報へのアクセス
 DSL 定義のクラス、リレーションシップ、およびその他の側面に関する情報を取得できます。 例:

 `DomainClassInfo personClass = henry.GetDomainClass();`

 `DomainPropertyInfo birthProperty =`

 `personClass.FindDomainProperty("BirthDate")`

 `DomainRelationshipInfo relationship =`

 `link.GetDomainRelationship();`

 `DomainRoleInfo sourceRole = relationship.DomainRole[0];`

 モデル要素の先祖クラスは次のとおりです。

- ModelElement-すべての要素とリレーションシップは ModelElements です。

- ElementLink-すべてのリレーションシップは Elementlink です

## <a name="transaction"></a>トランザクション内で変更を実行する
 プログラムコードによってストア内の何かが変更されるたびに、トランザクション内で実行する必要があります。 これは、すべてのモデル要素、リレーションシップ、図形、図、およびそれらのプロパティに適用されます。 詳細については、「 <xref:Microsoft.VisualStudio.Modeling.Transaction> 」を参照してください。

 トランザクションを管理する最も便利な方法は、ステートメント`using` `try...catch`でステートメントを使用することです。

```
Store store; ...
try
{
  using (Transaction transaction =
    store.TransactionManager.BeginTransaction("update model"))
    // Outermost transaction must always have a name.
  {
    // Make several changes in Store:
    Person p = new Person(store);
    p.FamilyTreeModel = familyTree;
    p.Name = "Edward VI";
    // end of changes to Store

    transaction.Commit(); // Don't forget this!
  } // transaction disposed here
}
catch (Exception ex)
{
  // If an exception occurs, the Store will be
  // rolled back to its previous state.
}
```

 1つのトランザクション内で任意の数の変更を行うことができます。 アクティブなトランザクション内で新しいトランザクションを開くことができます。

 変更を永続的なものにするに`Commit`は、トランザクションが破棄される前にトランザクションを実行する必要があります。 トランザクション内でキャッチされない例外が発生した場合、ストアは変更前の状態にリセットされます。

## <a name="elements"></a>モデル要素の作成
 次の例では、既存のモデルに要素を追加します。

```
FamilyTreeModel familyTree = ...; // The root of the model.
using (Transaction t =
    familyTree.Store.TransactionManager
    .BeginTransaction("update model"))
{
  // Create a new model element
  // in the same partition as the model root:
  Person edward = new Person(familyTree.Partition);
  // Set its embedding relationship:
  edward.FamilyTreeModel = familyTree;
          // same as: familyTree.People.Add(edward);
  // Set its properties:
  edward.Name = "Edward VII";
  t.Commit(); // Don't forget this!
}
```

 次の例は、要素の作成に関する重要なポイントを示しています。

- ストアの特定のパーティションに新しい要素を作成します。 モデル要素とリレーションシップについては、図形ではありませんが、通常は既定のパーティションです。

- 埋め込みリレーションシップのターゲットにします。 この例の DslDefinition では、各ユーザーは、埋め込みリレーションシップ FamilyTreeHasPeople のターゲットである必要があります。 これを実現するには、Person オブジェクトの FamilyTreeModel role プロパティを設定するか、FamilyTreeModel オブジェクトの People ロールプロパティに Person を追加します。

- 新しい要素のプロパティを設定します。特に、dsldefinition では true に設定されている`IsName`プロパティです。 このフラグは、自身の所有者内で要素を一意に識別するために機能するプロパティをマークします。 この例では、Name プロパティにそのフラグが指定されています。

- この DSL の DSL 定義がストアに読み込まれている必要があります。 メニューコマンドなどの拡張機能を作成する場合は、通常、これが既に true になっています。 それ以外の場合は、明示的にモデルをストアに読み込むか、 [Modelbus](/previous-versions/ee904639(v=vs.140))を使用してそれを読み込むことができます。 詳細については、「[方法 :プログラムコード](../modeling/how-to-open-a-model-from-file-in-program-code.md)でファイルからモデルを開きます。

  この方法で要素を作成すると、図形が自動的に作成されます (DSL に図がある場合)。 既定の図形、色、およびその他の機能を使用して、自動的に割り当てられた場所に表示されます。 関連付けられた図形を表示する場所と方法を制御する場合は、「[要素とその形状を作成](#merge)する」を参照してください。

## <a name="links"></a>リレーションシップリンクの作成
 DSL 定義の例では、2つのリレーションシップが定義されています。 各リレーションシップは、リレーションシップの各 end でクラスの*ロールプロパティ*を定義します。

 リレーションシップのインスタンスを作成するには、次の3つの方法があります。 これら3つのメソッドは、それぞれ同じ効果を持ちます。

- ソースロールプレーヤーのプロパティを設定します。 例:

  - `familyTree.People.Add(edward);`

  - `edward.Parents.Add(henry);`

- ターゲットロールプレーヤーのプロパティを設定します。 例:

  - `edward.familyTreeModel = familyTree;`

       このロールの多重度は`1..1`であるため、値を割り当てます。

  - `henry.Children.Add(edward);`

       このロールの多重度は`0..*`であるため、コレクションにを追加します。

- リレーションシップのインスタンスを明示的に構築します。 例:

  - `FamilyTreeHasPeople edwardLink = new FamilyTreeHasPeople(familyTreeModel, edward);`

  - `ParentsHaveChildren edwardHenryLink = new ParentsHaveChildren(henry, edward);`

  最後のメソッドは、リレーションシップ自体にプロパティを設定する場合に便利です。

  この方法で要素を作成すると、図のコネクタが自動的に作成されますが、既定の図形、色、およびその他の機能があります。 関連付けられているコネクタの作成方法を制御するには、「[要素とその図形の作成](#merge)」を参照してください。

## <a name="deleteelements"></a>要素の削除
 を呼び出し`Delete()`て要素を削除します。

 `henry.Delete();`

 この操作では、次の項目も削除されます。

- 要素との間のリレーションシップリンク。 たとえば、 `edward.Parents`にはが含ま`henry`れなくなります。

- `PropagatesDelete`フラグが true になっているロールの要素。 たとえば、要素を表示する図形は削除されます。

  既定では、すべての埋め`PropagatesDelete`込みリレーションシップはターゲットロールで true に設定されています。 を削除して`familyTree` `familyTree.Delete()` `Persons`も、は削除されませんが、すべてを削除することになります。 `henry` 詳細については、「[削除動作のカスタマイズ](../modeling/customizing-deletion-behavior.md)」を参照してください。

  既定では`PropagatesDelete` 、参照リレーションシップのロールに対しては true ではありません。

  オブジェクトを削除すると、削除規則によって特定の伝達が省略される可能性があります。 これは、ある要素を別の要素に置換する場合に便利です。 削除を反映しない1つまたは複数のロールの GUID を指定します。 GUID は、リレーションシップクラスから取得できます。

  `henry.Delete(ParentsHaveChildren.SourceDomainRoleId);`

  (この特定の例は`PropagatesDelete` `false` 、 `ParentsHaveChildren`リレーションシップのロールを対象としているため、効果はありません)。

  場合によっては、要素または伝達によって削除される要素に、ロックが存在しても削除できません。 を使用`element.CanDelete()`すると、要素を削除できるかどうかを確認できます。

## <a name="deletelinks"></a>リレーションシップリンクの削除
 リレーションシップリンクを削除するには、ロールプロパティから要素を削除します。

 `henry.Children.Remove(edward); // or:`

 `edward.Parents.Remove(henry);  // or:`

 また、リンクを明示的に削除することもできます。

 `edwardHenryLink.Delete();`

 これら3つのメソッドはすべて同じ効果を持ちます。 これらのうちの1つのみを使用する必要があります。

 ロールの複数要素の接続性が 0 ..1 または 1 ..1 の場合は`null`、、または別の値に設定できます。

 `edward.FamilyTreeModel = null;`もしくは

 `edward.FamilyTreeModel = anotherFamilyTree;`

## <a name="reorder"></a>リレーションシップのリンクを並べ替える
 特定のモデル要素をソースまたはターゲットとする特定のリレーションシップのリンクには、特定のシーケンスがあります。 これらは、追加された順序で表示されます。 たとえば、次のステートメントでは、常に同じ順序で子が生成されます。

 `foreach (Person child in henry.Children) ...`

 リンクの順序は次のように変更できます。

 `ParentsHaveChildren link = GetLink(henry,edward);`

 `ParentsHaveChildren nextLink = GetLink(henry, elizabeth);`

 `DomainRoleInfo role =`

 `link.GetDomainRelationship().DomainRoles[0];`

 `link.MoveBefore(role, nextLink);`

## <a name="locks"></a>固定
 ロックによって変更が禁止されている可能性があります。 ロックは、個々の要素、パーティション、およびストアで設定できます。 これらのレベルのいずれかが、変更の種類を妨げるロックを持っている場合は、例外がスローされることがあります。 ロックが設定されているかどうかは、要素を使用して検出できます。GetLocks ()。これは、名前空間<xref:Microsoft.VisualStudio.Modeling.Immutability>で定義されている拡張メソッドです。

 詳細については、「[ロックポリシーを定義して読み取り専用セグメントを作成する](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)」を参照してください。

## <a name="copy"></a>コピーと貼り付け
 要素または要素のグループをに<xref:System.Windows.Forms.IDataObject>コピーできます。

```
Person person = personShape.ModelElement as Person;
Person adopter = adopterShape.ModelElement as Person;
IDataObject data = new DataObject();
personShape.Diagram.ElementOperations
      .Copy(data, person.Children.ToList<ModelElement>());
```

 要素は、シリアル化された要素グループとして格納されます。

 IDataObject の要素をモデルにマージできます。

```
using (Transaction t = targetDiagram.Store.
        TransactionManager.BeginTransaction("paste"))
{
  adopterShape.Diagram.ElementOperations.Merge(adopter, data);
}
```

 `Merge ()`は、 `PresentationElement`またはの`ModelElement`いずれかを受け入れることができます。 をに指定した場合は、3番目のパラメーターとしてターゲットダイアグラム上の位置を指定することもできます。`PresentationElement`

## <a name="diagrams"></a>ダイアグラムの移動と更新
 DSL では、Person や Song などの概念を表すドメインモデル要素は、図に表示される内容を表す shape 要素とは別のものです。 ドメインモデル要素は、概念の重要なプロパティと関係を格納します。 図形要素には、オブジェクトのビューのサイズ、位置、および色、およびそのコンポーネントパーツのレイアウトが格納されます。

### <a name="presentation-elements"></a>プレゼンテーション要素
 ![基本図形と要素の種類のクラス図](../modeling/media/dslshapesandelements.png "DSLshapesAndElements")

 DSL 定義では、指定した各要素によって、次のいずれかの標準クラスから派生したクラスが作成されます。

|要素の種類|基底クラス|
|---------------------|----------------|
|ドメインクラス|<xref:Microsoft.VisualStudio.Modeling.ModelElement>|
|ドメインリレーションシップ|<xref:Microsoft.VisualStudio.Modeling.ElementLink>|
|形式|<xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>|
|コネクタ|<xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>|
|図|<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>|

 図の要素は、通常、モデル要素を表します。 通常は (常にではあり<xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>ません)、はドメインクラスの<xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>インスタンスを表し、はドメインリレーションシップのインスタンスを表します。 リレーションシップ<xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject>は、ノードまたはリンク図形を、それが表すモデル要素にリンクします。

 すべてのノードまたはリンク図形は、1つの図に属します。 バイナリリンク図形は、2つのノード図形を接続します。

 図形は、2つのセットに子図形を持つことができます。 `NestedChildShapes`セット内の図形は、その親の境界ボックスに限定されます。 `RelativeChildShapes`リスト内の図形は、親の境界の外側または一部に表示できます (ラベルやポートなど)。 図には`RelativeChildShapes` `Parent`、とがありません。

### <a name="views"></a>図形と要素間の移動
 ドメインモデル要素と図形要素は、 <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject>リレーションシップによって関連付けられます。

```csharp
// using Microsoft.VisualStudio.Modeling;
// using Microsoft.VisualStudio.Modeling.Diagrams;
// using System.Linq;
Person henry = ...;
PersonShape henryShape =
  PresentationViewsSubject.GetPresentation(henry)
    .FirstOrDefault() as PersonShape;
```

 同じリレーションシップによって、ダイアグラム上のコネクタへのリレーションシップがリンクされます。

```
Descendants link = Descendants.GetLink(henry, edward);
DescendantConnector dc =
   PresentationViewsSubject.GetPresentation(link)
     .FirstOrDefault() as DescendantConnector;
// dc.FromShape == henryShape && dc.ToShape == edwardShape
```

 このリレーションシップは、モデルのルートを図にリンクします。

```
FamilyTreeDiagram diagram =
   PresentationViewsSubject.GetPresentation(familyTree)
      .FirstOrDefault() as FamilyTreeDiagram;
```

 図形によって表されるモデル要素を取得するには、次のように使用します。

 `henryShape.ModelElement as Person`

 `diagram.ModelElement as FamilyTreeModel`

### <a name="navigating-around-the-diagram"></a>図の周りを移動する
 一般に、図の図形とコネクタの間を移動することはお勧めしません。 図の外観を操作する必要がある場合にのみ、モデル内のリレーションシップを移動し、図形とコネクタ間を移動することをお勧めします。 これらのメソッドは、コネクタを各端の図形にリンクします。

 `personShape.FromRoleLinkShapes, personShape.ToRoleLinkShapes`

 `connector.FromShape, connector.ToShape`

 多くの図形は複合です。親図形と子の1つ以上のレイヤーで構成されます。 別の図形に相対的に配置された図形は、*子*と呼ばれます。 親図形が移動すると、子が移動します。

 *相対子*は、親図形の境界ボックスの外側に表示できます。 *入れ子になっ*た子は、親の境界内に厳密に出現します。

 図の最上位の図形を取得するには、次のように使用します。

 `Diagram.NestedChildShapes`

 図形とコネクタの先祖クラスは次のとおりです。

 <xref:Microsoft.VisualStudio.Modeling.ModelElement>

 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationElement>

 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>

 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>

 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>

 ------- *YourShape*

 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.LinkShape>

 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>

 --------- *YourConnector*

### <a name="shapeProperties"></a>図形とコネクタのプロパティ
 ほとんどの場合、図形に対して明示的な変更を行う必要はありません。 モデル要素を変更すると、"修正" ルールによって図形とコネクタが更新されます。 詳細については、「[変更に対する応答と反映](../modeling/responding-to-and-propagating-changes.md)」を参照してください。

 ただし、モデル要素に依存しないプロパティの図形に対して明示的な変更を加えると便利です。 たとえば、次のプロパティを変更できます。

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Size%2A>-図形の高さと幅を決定します。

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Location%2A>-親のシェイプまたは図に対する相対位置

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.StyleSet%2A>-図形またはコネクタの描画に使用されるペンとブラシのセット

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Hide%2A>-図形を非表示にします

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Show%2A>-図形を表示します。`Hide()`

### <a name="merge"></a>要素とその図形の作成
 要素を作成し、埋め込みリレーションシップのツリーにリンクすると、図形が自動的に作成され、関連付けられます。 これは、トランザクションの終了時に実行される "fixup" 規則によって行われます。 ただし、図形は自動的に割り当てられた場所に表示され、その図形、色、およびその他の機能には既定値が設定されます。 図形の作成方法を制御するには、merge 関数を使用します。 まず、追加する要素を ElementGroup に追加してから、そのグループをダイアグラムにマージする必要があります。

 このメソッドは次のとおりです。

- プロパティが要素名として割り当てられている場合は、名前を設定します。

- DSL 定義で指定したすべての要素マージディレクティブを監視します。

  この例では、ユーザーが図をダブルクリックしたときに、マウスの位置に図形を作成します。 このサンプル`FillColor`の DSL 定義では、の`ExampleShape`プロパティが公開されています。

```

using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
partial class MyDiagram
{
  public override void OnDoubleClick(DiagramPointEventArgs e)
  {
    base.OnDoubleClick(e);

    using (Transaction t = this.Store.TransactionManager
        .BeginTransaction("double click"))
    {
      ExampleElement element = new ExampleElement(this.Store);
      ElementGroup group = new ElementGroup(element);

      { // To use a shape of a default size and color, omit this block.
        ExampleShape shape = new ExampleShape(this.Partition);
        shape.ModelElement = element;
        shape.AbsoluteBounds = new RectangleD(0, 0, 1.5, 1.0);
        shape.FillColor = System.Drawing.Color.Azure;
        group.Add(shape);
      }

      this.ElementOperations.MergeElementGroupPrototype(
        this,
        group.CreatePrototype(),
        PointD.ToPointF(e.MousePosition));
      t.Commit();
    }
  }
}

```

 複数の図形を指定する場合は、を使用して`AbsoluteBounds`それらの相対位置を設定します。

 この方法を使用して、コネクタの色やその他の公開プロパティを設定することもできます。

### <a name="use-transactions"></a>トランザクションの使用
 図形、コネクタ、および図は、 <xref:Microsoft.VisualStudio.Modeling.ModelElement>ストア内ののサブタイプであり、ライブです。 したがって、トランザクション内でのみ変更を加える必要があります。 詳細については、「[方法 :トランザクションを使用してモデル](../modeling/how-to-use-transactions-to-update-the-model.md)を更新します。

## <a name="docdata"></a>ドキュメントビューとドキュメントデータ
 ![標準の図の種類のクラス図](../modeling/media/dsldiagramsanddocs.png "DSLDiagramsandDocs")

## <a name="store-partitions"></a>パーティションの格納
 モデルが読み込まれると、付随する図が同時に読み込まれます。 通常、モデルは DefaultPartition ストアに読み込まれ、図のコンテンツは別のパーティションに読み込まれます。 通常、各パーティションの内容が読み込まれ、別のファイルに保存されます。

## <a name="see-also"></a>関連項目
 <xref:Microsoft.VisualStudio.Modeling.ModelElement>[ドメイン固有言語での検証](../modeling/validation-in-a-domain-specific-language.md)[ドメイン固有言語からのコードの生成](../modeling/generating-code-from-a-domain-specific-language.md)[方法:トランザクションを使用してモデル](../modeling/how-to-use-transactions-to-update-the-model.md)を更新する[Visual Studio modelbus を使用し](../modeling/integrating-models-by-using-visual-studio-modelbus.md)てモデルを統合し、[変更を反映](../modeling/responding-to-and-propagating-changes.md)する
