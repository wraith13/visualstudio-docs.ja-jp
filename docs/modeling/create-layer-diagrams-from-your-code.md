﻿---
title: コードからの依存関係図の作成
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b9822dda92a096e3c497d468865d3ed9fd56e16d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62421187"
---
# <a name="create-dependency-diagrams-from-your-code"></a>コードからの依存関係図の作成

ソフトウェア システムの高レベルの論理アーキテクチャを視覚化するには、Visual Studio で*依存関係図*を作成します。 コードがこの設計と一致していることを確認するために、依存関係図を使用してコードを検証します。 Visual C＃ および Visual Basic プロジェクトの依存関係図を作成することができます。 Visual C＃ および Visual Basic プロジェクトの依存関係図を作成することができます[アーキテクチャおよびモデリングツールのエディションサポート](../modeling/what-s-new-for-design-in-visual-studio.md#edition-support-for-architecture-and-modeling-tools) を参照してください。

![依存関係図を作成します。](../modeling/media/layerdiagramvisualizecode.png)

依存関係図では、Visual Studio のソリューション項目と呼ばれる抽象的な論理グループに編成できます。*レイヤー*します。 レイヤーを使用して、これらの成果物が実行する主要タスク、またはシステムの主要コンポーネントを示すことができます。 各レイヤーには、より詳細なタスクを示す別のレイヤーを含めることができます。 意図的または既存を指定することも*依存関係*レイヤー間。 矢印で表されるこれらの依存関係は、どのレイヤーが、他のレイヤーが表す機能を使用できるか、または現在使用しているかを示します。 コードのアーキテクチャ コントロールを保持するには、目的の依存関係を図で示し、図と照らし合わせてコードを検証します。

[ビデオ:リアルタイムでアーキテクチャ依存関係を検証します。](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)

## <a name="CreateDiagram"></a> 依存関係図を作成します。

依存関係図を作成する前に、ソリューションにモデリング プロジェクトを確認します。

> [!IMPORTANT]
> しない追加、ドラッグ、または別のモデリング プロジェクトまたはソリューション内の別の場所には、モデリング プロジェクトから既存の依存関係図をコピーします。 これで、図を変更しても、元の図からの参照が保持されます。 また、これによってレイヤー検証が正しく機能しないため、要素が欠落したり、図を開こうとすると他のエラーが発生するなど、別の問題が生じる可能性があります。
>
> 代わりに、新しい依存関係図をモデリング プロジェクトに追加します。 元の図から新しい図へ要素をコピーします。 モデリング プロジェクトと新しい依存関係図の両方を保存します。

### <a name="add-a-new-dependency-diagram-to-a-modeling-project"></a>新しい依存関係図をモデリング プロジェクトに追加します。

> [!NOTE]
> Visual Studio で .NET Core プロジェクトでは、依存関係図はサポートされていません。

1. **アーキテクチャ**] メニューの [選択**新しい依存関係図**します。

2. **テンプレート**、選択**依存関係図**します。

3. 図に名前を付けます。

4. **モデリング プロジェクトに追加**を参照し、ソリューション内の既存のモデリング プロジェクトを選択します。

     - または -

     選択**新しいモデリング プロジェクトを作成する**新しいモデリング プロジェクトをソリューションに追加します。

    > [!NOTE]
    > 依存関係図はモデリング プロジェクト内に存在する必要があります。 ただし、ソリューション内のどの場所にある項目にもリンクできます。

5. モデリング プロジェクトと依存関係図の両方を保存してください。

## <a name="drag-and-drop-or-copy-and-paste-from-a-code-map"></a>ドラッグし削除、またはコピーして貼り付けるには、コード マップから

1. 使用して、ソリューションのコード マップを生成、**アーキテクチャ**メニュー。

2. 製品コードの依存関係を適用する場合は、ソリューション フォルダーと テスト アセット"を削除するコード マップのフィルターを適用することを検討してください。

3. 生成されたコード マップに"External"のノードを削除、名前空間の依存関係を適用するかどうかに応じて、外部のアセンブリを表示するようを展開し、コード マップから省略可能なアセンブリを削除します。

4. ソリューションを使用して、新しい依存関係図を作成、**アーキテクチャ**メニュー

5. コード マップ上のすべてのノードを選択します （_Ctrl_ + _A_を使用するか、_Shift_キーを押してクリック、ドラッグ、リリースする前にラバーバンドを選択します）。

6. ドラッグ アンド ドロップ、または、コピーや貼り付け、新しい依存関係検証ダイアグラムを選択した要素。

7. これは、現在のアプリのアーキテクチャを示します。 対象を決定するアーキテクチャと依存関係図を適宜変更します。

![コード マップから生成された依存関係図](media/dependency-validation-01.png)

## <a name="CreateLayers"></a> 成果物からレイヤーを作成します。
 レイヤーは、プロジェクト、コード ファイル、名前空間、クラス、メソッドなど、Visual Studio ソリューションの項目から生成できます。 これにより、レイヤーと項目の間のリンクが自動的に作成され、レイヤー検証プロセスに含まれます。

 Word 文書や PowerPoint プレゼンテーションなどの検証をサポートしない項目にレイヤーをリンクすることもできます。こうすると、仕様や計画にレイヤーを関連付けることができます。 複数のアプリが共有するプロジェクトのファイルにレイヤーをリンクすることもできます。ただし、これらのレイヤーは検証プロセスには含まれず、"レイヤー 1"、"レイヤー 2" などの汎用名で表示されます。

 リンクされた項目が検証をサポートしているかを確認するには、開きます**レイヤー エクスプ ローラー**を調べ、**検証をサポート**アイテムのプロパティ。 参照してください[成果物へのリンクを管理する](#Managing)します。

|**To**|**次の手順します。**|
|-|-|
|1 つの成果物を表すレイヤーを生成する|<ol><li>これらのソースから依存関係図に項目をドラッグします。<br /><br /> <ul><li>**ソリューション エクスプローラー**<br /><br />         ファイルやプロジェクトなどをドラッグできます。</li><li>コード マップ<br /><br />         参照してください[ソリューション間の依存関係をマップする](../modeling/map-dependencies-across-your-solutions.md)と[コード マップをアプリケーションのデバッグ](../modeling/use-code-maps-to-debug-your-applications.md)します。</li><li>**クラス ビュー**または**オブジェクト ブラウザー**</li></ul><br />     レイヤーが図に表示され、成果物にリンクされます。</li><li>レイヤーの名前を、関連するコードや成果物の役割を表す名前に変更します。</li></ol> **重要:** 依存関係図にバイナリ ファイルをドラッグすることも、モデリング プロジェクトへの参照は自動的に追加されません。 検証するバイナリ ファイルを手動でモデリング プロジェクトに追加する必要があります。 **バイナリ ファイルをモデリング プロジェクトに追加するには** <ol><li>**ソリューション エクスプ ローラー**、モデリング プロジェクトのショートカット メニューを開き、選択し、**既存項目の追加**します。</li><li>**既存項目の追加**ダイアログ ボックスで、バイナリ ファイルを参照、選択して、および選択**OK**します。     バイナリ ファイルがモデリング プロジェクトに表示されます。</li><li>**ソリューション エクスプ ローラー**、バイナリ ファイルを追加し、キーを押します**F4**を開く、**プロパティ**ウィンドウ。</li><li>各バイナリ ファイルでは、設定、**ビルド アクション**プロパティを**検証**です。</li></ol>|
|選択したすべての成果物を表す 1 つのレイヤーを生成する|すべての成果物を同時に依存関係図にドラッグします。<br /><br /> レイヤーが図に表示され、すべての成果物にリンクされます。|
|選択した各成果物を表すレイヤーを生成する|長押しし、 **SHIFT**キーながらすべてのアイテム、依存関係図を同時にドラッグします。 **注:** 使用する場合、 **SHIFT**キー範囲の項目を選択するには、成果物を選択した後、キーをリリースします。 成果物を図にドラッグするときは、キーを再び押して、押したままにします。 <br /><br /> 各成果物を表すレイヤーが図に表示され、各成果物にリンクされます。|
|成果物をレイヤーに追加する|成果物をレイヤーにドラッグします。|
|リンクされない新しいレイヤーを生成する|**ツールボックス**、展開、**依存関係図**セクションで、し、ドラッグ、**レイヤー**依存関係図にします。<br /><br /> 複数のレイヤーを追加するには、ツールをダブルクリックします。 完了したら、選択、**ポインター**ツールまたはキーを押して、 **ESC**キー。<br /><br /> または<br /><br /> 依存関係図のショートカット メニューを開き、選択**追加**を選び、**レイヤー**します。|
|入れ子になったレイヤーを生成する|既存のレイヤーを別のレイヤー上へドラッグします。<br /><br /> または<br /><br /> レイヤーのショートカット メニューを開き、選択**追加**を選び、**レイヤー**します。|
|複数の既存レイヤーを含む新しいレイヤーを生成する|レイヤーを選択、選択内容のショートカット メニューを開き、選択し、**グループ**します。|
|レイヤーの色を変更する|設定の**色**プロパティを使用する色。|
|レイヤーに関連付けられている成果物を、指定した名前空間に所属させることができないように指定する|レイヤーの名前空間を入力**禁止された名前空間**プロパティ。 セミコロンで区切ります (**;**) 名前空間を分離します。|
|レイヤーに関連付けられている成果物が、指定した名前空間に依存できないように指定する|レイヤーの名前空間を入力**Namespace 依存関係の禁止**プロパティ。 セミコロンで区切ります (**;**) 名前空間を分離します。|
|レイヤーに関連付けられている成果物を、指定した名前空間のいずれかに必ず所属させるように指定する|レイヤーの名前空間を入力**名前空間のために必要な**プロパティ。 セミコロンで区切ります (**;**) 名前空間を分離します。|

 レイヤーの数字は、レイヤーにリンクされている成果物の数を示します。 ただし、この数値を読み取るときには、次の点に注意してください。

- 1 つのレイヤーが他の成果物を含む 1 つの成果物にリンクされているが、他の成果物に直接リンクされていない場合、その数字にはリンクされた成果物のみが含まれます。 ただし、レイヤー検証時の分析にはそれらの他の成果物も含まれます。

     たとえば、1 つのレイヤーが 1 つの名前空間にリンクされている場合、その名前空間に複数のクラスが含まれていても、リンクされた成果物の数は 1 です。 レイヤーに名前空間の各クラスへのリンクもある場合、その数字にはリンクされたクラスが含まれます。

- 1 つのレイヤーに成果物にリンクされた他のレイヤーが含まれている場合は、そのコンテナー レイヤーの数字にそれらの成果物が含まれていなくても、コンテナー レイヤーはそれらの成果物にリンクされます。

## <a name="Managing"></a> レイヤーと成果物の間のリンクを管理します。

1. 依存関係図、レイヤーのショートカット メニューを開きし、**ビュー リンク**します。

     **レイヤー エクスプ ローラー**選択したレイヤーの成果物のリンクが表示されます。

2. これらのリンクを管理するには、次の操作を行います。

|**To**|**レイヤー エクスプ ローラーで**|
|-|-|
|レイヤーと成果物のリンクを削除する|成果物のリンクのショートカット メニューを開き、選択し、**削除**します。|
|リンクを別のレイヤーに移動する|成果物のリンクを図上の既存のレイヤーにドラッグします。<br /><br /> または<br /><br /> 1.成果物のリンクのショートカット メニューを開き、選択し、**切り取り**します。<br />2.依存関係図、レイヤーのショートカット メニューを開きし、**貼り付け**します。|
|リンクを別のレイヤーにコピーする|1.成果物のリンクのショートカット メニューを開き、選択し、**コピー**します。<br />2.依存関係図、レイヤーのショートカット メニューを開きし、**貼り付け**します。|
|既存の成果物のリンクから新しいレイヤーを生成する|成果物のリンクを図上の空白領域にドラッグします。|
|リンクされた成果物が依存関係図に対する検証をサポートしていることを確認します。|見て、**検証をサポート**成果物のリンクの列。|

## <a name="Discovering"></a> 既存の依存関係をリバース エンジニア リング
 依存関係が存在するのは、あるレイヤーに関連付けられている成果物が、別のレイヤーに関連付けられている成果物を参照している場合です。 たとえば、あるレイヤー内のクラスが、別のレイヤー内のクラスを保持する変数を宣言する場合などです。 図のレイヤーにリンクされている成果物の既存の依存関係はリバース エンジニアリングできます。

> [!NOTE]
> 成果物の種類によっては、依存関係をリバース エンジニアリングできないものもあります。 たとえば、テキスト ファイルにリンクされているレイヤーから、またはそのレイヤーに対して依存関係をリバース エンジニアリングすることはできません。 アイテムがあるリバース エンジニア リングできる依存関係を表示する 1 つまたは複数のレイヤーのショートカット メニューを開きし、**ビュー リンク**します。 **レイヤー エクスプ ローラー**、確認、**検証をサポート**列。 依存関係にこの列が表示対象の成果物のリバース エンジニア リングがされません**False**します。

- 1 つまたは複数のレイヤーを選択で、選択したレイヤーのショートカット メニューを開きを**依存関係の生成**します。

  通常は、不要な依存関係がいくつか見つかります。 これらの依存関係を編集して、目的の設計に準拠するようアラインできます。

## <a name="EditDependencies"></a> レイヤーと意図した設計を表示する依存関係を編集します。
 システムまたは必要とされるアーキテクチャをする予定の変更を記述するには、依存関係図を編集します。

|**To**|**これらの手順に従います**|
|-|-|
|依存関係の方向を変更または制限する|設定の**方向**プロパティ。|
|新しい依存関係を生成する|使用して、**依存関係**と**双方向の依存関係**ツール。<br /><br /> 複数の依存関係を描画するには、ツールをダブルクリックします。 完了したら、選択、**ポインター**ツールまたはキーを押して、 **ESC**キー。|
|レイヤーに関連付けられている成果物が、指定した名前空間に依存できないように指定する|レイヤーの名前空間を入力**Namespace 依存関係の禁止**プロパティ。 セミコロンで区切ります (**;**) 名前空間を分離します。|
|レイヤーに関連付けられている成果物を、指定した名前空間に所属させることができないように指定する|レイヤーの名前空間を入力**禁止された名前空間**プロパティ。 セミコロンで区切ります (**;**) 名前空間を分離します。|
|レイヤーに関連付けられている成果物を、指定した名前空間のいずれかに必ず所属させるように指定する|レイヤーの名前空間を入力**名前空間のために必要な**プロパティ。 セミコロンで区切ります (**;**) 名前空間を分離します。|

## <a name="EditLayout"></a> 図上の要素を表示する方法を変更します。
 プロパティを編集して、レイヤーのサイズ、形状、色、位置、または依存関係の色を変更できます。

## <a name="Codemaps"></a> パターンとコード マップ上の依存関係を検出します。
 依存関係図を作成するときに作成することも**コード マップ**します。 これらの図を利用することで、コードを検証するときに、パターンと依存関係を見つけやすくなります。 ソリューション エクスプローラー、クラス ビュー、またはオブジェクト ブラウザーを使用して、アセンブリ、名前空間、およびクラスを調べることができます。これらは、通常は既存のレイヤーに対応しています。 コード マップについての詳細は、次を参照してください。

- [ソリューション間の依存関係をマップする](../modeling/map-dependencies-across-your-solutions.md)

- [コード マップを使用してアプリケーションをデバッグする](../modeling/use-code-maps-to-debug-your-applications.md)

- [コード マップ アナライザーを使用して潜在的な問題を検索する](../modeling/find-potential-problems-using-code-map-analyzers.md)

## <a name="see-also"></a>関連項目

- [アーキテクチャ ツールとモデリング ツールのエディションのサポート](../modeling/what-s-new-for-design-in-visual-studio.md#edition-support-for-architecture-and-modeling-tools)
- [ビデオ:リアルタイムでアーキテクチャ依存関係を検証します。](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)
- [依存関係図:リファレンス](../modeling/layer-diagrams-reference.md)
- [依存関係図:ガイドライン](../modeling/layer-diagrams-guidelines.md)
- [依存関係図を使用したコードの検証](../modeling/validate-code-with-layer-diagrams.md)
- [コードの視覚化](../modeling/visualize-code.md)
