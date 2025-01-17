---
title: '方法: プログラム コード内のファイルからモデルを開く'
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f89c62863aadf4e1f8902799b502c07b9dea528d
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67821912"
---
# <a name="how-to-open-a-model-from-file-in-program-code"></a>方法: プログラム コード内のファイルからモデルを開く

任意のアプリケーションで DSL モデルを開くことができます。

Visual Studio 拡張機能では、この目的の ModelBus を使用できます。 ModelBus はモデルまたはモデルでは、要素を参照して、移動された場合、モデルを検索するための標準的なメカニズムを提供します。 詳細については、次を参照してください。 [Visual Studio modelbus によるモデルの統合](../modeling/integrating-models-by-using-visual-studio-modelbus.md)します。

## <a name="target-framework"></a>[対象とする Framework]

設定、**ターゲット フレームワーク**アプリケーション プロジェクトを .NET Framework 4 またはそれ以降の。

1. DSL モデルを読み取るアプリケーションの Visual Studio プロジェクトを開きます。

2. **ソリューション エクスプ ローラー**プロジェクトを右クリックし、クリックして**プロパティ**します。

3. プロジェクトのプロパティ ウィンドウでの**アプリケーション**タブで、設定、**ターゲット フレームワーク**フィールドを **.NET Framework 4** (またはそれ以降)。

> [!NOTE]
> ターゲット フレームワークがすることはできません **.NET Framework 4 Client Profile**します。

## <a name="references"></a>リファレンス

Visual Studio アプリケーション プロジェクトにこれらの参照を追加します。

- `Microsoft.VisualStudio.Modeling.Sdk.11.0`

  - 表示されない場合、 **.NET**  タブで、**参照の追加**ダイアログ ボックスで、をクリックして、**参照**タブに移動して`%Program Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Common\Assemblies\`します。

- DSL アセンブリ、DSL プロジェクト bin フォルダーの下で検索されます。 その名前の形式では通常です。*Yourcompany ' と*.*プロジェクト*`.Dsl.dll`します。

## <a name="important-classes-in-the-dsl"></a>DSL で重要なクラス

DSL を読み取るコードを記述する前に、一部の DSL によって生成されたクラスの名前を知っておくべきです。 DSL ソリューションで開く、 **Dsl**プロジェクトし、ファイルの場所、 **GeneratedCode**フォルダー。 または、プロジェクトで DSL のアセンブリをダブルクリック**参照**、DSL の名前空間を開くと**オブジェクト ブラウザー**します。

これらは、クラスを識別する必要があります。

- *YourDslRootClass* -これは、内のルート クラスの名前、`DslDefinition.dsl`します。

- *YourDslName* `SerializationHelper` -でこのクラスが定義されている`SerializationHelper.cs`DSL プロジェクト。

- *YourDslName* `DomainModel` -でこのクラスが定義されている`DomainModel.cs`DSL プロジェクト。

## <a name="read-from-a-file"></a>ファイルのデータを読み取ります。

次の例は、重要なクラスの次のように DSL を読み取るために設計されました。

- FamilyTreeModel

- FamilyTreeSerializationHelper

- FamilyTreeDomainModel

この DSL で他のドメイン クラスには、ユーザーです。

```csharp
using System;
using Microsoft.VisualStudio.Modeling;
using Company.FamilyTree; // Your DSL namespace

namespace StandaloneReadDslConsole
{ class Program
  { static void Main(string[] args)
    {
      // The path of a DSL model file:
      string dslModel = @"C:\FamilyTrees\Tudor.ftree";
      // Set up the Store to read your type of model:
      Store store = new Store(
        typeof(Company.FamilyTree.FamilyTreeDomainModel));
      // The Model type generated by the DSL:
      FamilyTreeModel familyTree;
      // All Store changes must be in a Transaction:
      using (Transaction t =
        store.TransactionManager.BeginTransaction("Load model"))
      {
        familyTree =
           FamilyTreeSerializationHelper.Instance.
              LoadModel(store, dslModel, null, null, null);
        t.Commit(); // Don't forget this!
      }
      // Now we can read the model:
      foreach (Person p in familyTree.People)
      {
        Console.WriteLine(p.Name);
        foreach (Person child in p.Children)
        {
          Console.WriteLine("    " + child.Name);
        }
} } } }
```

## <a name="save-to-a-file"></a>ファイルに保存します。

前のコードを次の追加は、モデルに変更を加えるし、ファイルに保存されます。

```csharp
using (Transaction t =
  store.TransactionManager.BeginTransaction("update model"))
{
  // Create a new model element:
  Person p = new Person(store);
  // Set its embedding relationship:
  p.FamilyTreeModel = familyTree;
  // - same as: familyTree.People.Add(p);
  // Set its properties:
  p.Name = "Edward VI";
  t.Commit(); // Don't forget this!
}
// Save the model:
try
{
  SerializationResult result = new SerializationResult();
  FamilyTreeSerializationHelper.Instance
    .SaveModel(result, familyTree, @"C:\FamilyTrees\Tudor-upd.ftree");
  // Report any error:
  if (result.Failed)
  {
    foreach (SerializationMessage message in result)
    {
      Console.WriteLine(message);
    }
  }
}
catch (System.IO.IOException ex)
{ ... }
```
