---
title: '方法: 定義およびワークフロー デザイナーでアクティビティ デリゲートの使用 |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
caps.latest.revision: 3
author: steved0x
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 37adb6cf6462887010b1c06c7d5af4a539203b15
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62974580"
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>方法: ワークフロー デザイナーでアクティビティ デリゲートを定義および使用する
[!INCLUDE[net_v45](../includes/net-v45-md.md)] には、すぐに使用できる <xref:System.Activities.Statements.InvokeDelegate> アクティビティの新しいデザイナーが用意されています。 このデザイナーを使用すると、<xref:System.Activities.ActivityDelegate> や <xref:System.Activities.ActivityAction> など、<xref:System.Activities.ActivityFunc%601> から派生するアクティビティにデリゲートを割り当てることができます。  
  
### <a name="define-an-activity-delegate"></a>アクティビティ デリゲートの定義  
  
1. [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]、**ファイル**、**新規**、**プロジェクト**します。 選択、**ワークフロー** 、左側のノードと**ワークフロー コンソール アプリケーション**右側のテンプレート。 (必要な) 場合、プロジェクトの名前を指定し、をクリックして**Ok**します。  
  
2. プロジェクトを右クリックして**ソリューション エクスプ ローラー**選択**追加**、**新しい項目.**. 選択、**ワークフロー** 、左側のノードと**アクティビティ**右側のテンプレート。 新しいアクティビティの名前**MyForEach.xaml**クリック**Ok**します。 ワークフロー デザイナーでアクティビティが開かれます。  
  
3. ワークフロー デザイナーで、クリックして、**引数**タブ。  
  
4. クリックして**引数の作成**です。 新しい引数を名前**項目**します。  
  
5. **引数の型**列で、 **[T] の配列**します。  
  
6. 型ブラウザーで次のように選択します。**オブジェクト**します。 **[OK]** をクリックします。  
  
7. クリックして**引数の作成**もう一度です。 新しい引数を名前**本文**します。 **方向**選択、新しい引数は列**プロパティ**します。  
  
8. 引数の型の列で、選択**型を参照しています.**  
  
9. 型ブラウザーで、入力**ActivityAction**で、**型名**フィールド。 選択**ActivityAction\<T >** ツリー ビュー。 選択**オブジェクト**タイプを割り当てるために表示されるドロップダウン リストで**ActivityAction\<オブジェクト >** 引数にします。  
  
10. ドラッグ、<xref:System.Activities.Statements.While>からのアクティビティ、**制御フロー**デザイナー画面に、ツールボックスのセクション。  
  
11. 選択、<xref:System.Activities.Statements.While>アクティビティ、および選択、**変数**タブ。  
  
12. 選択**変数作成**です。 新しい変数の名前**インデックス**します。  
  
13. **変数の型**列で、 **Int32**します。 ままに、**スコープ**として**中**、および**既定**列は空白です。  
  
14. 設定、**条件**のプロパティ、<xref:System.Activities.Statements.While>アクティビティを**インデックス < Items.Length;** します。  
  
15. ドラッグ、<xref:System.Activities.Statements.InvokeDelegate>からのアクティビティ、**プリミティブ**、ツールボックスのセクション、**本文**の<xref:System.Activities.Statements.While>アクティビティ。  
  
16. 選択**本文**デリゲートのドロップダウンから。  
  
17. **プロパティ**のグリッド、<xref:System.Activities.Statements.InvokeDelegate>アクティビティ、クリックして、 **.** ボタン、**デリゲート引数**プロパティ。  
  
18. **値**という名前の引数の列**引数**、入力**Items [Index]** します。 クリックして**Ok**を閉じる、 **DelegateArguments**ダイアログ。  
  
19. <xref:System.Activities.Statements.Assign> アクティビティを <xref:System.Activities.Statements.InvokeDelegate> アクティビティの下の水平線にドラッグします。 <xref:System.Activities.Statements.Assign>アクティビティが作成され、および<xref:System.Activities.Statements.Sequence>で 2 つのアクティビティを格納するアクティビティが自動的に作成されます、**本文**のセクション、 **MyForEach**アクティビティ。 以降、シーケンスが必要な**本文**セクションがのみ 1 つのアクティビティを含めることができます。 新しい <xref:System.Activities.Statements.Sequence> アクティビティの自動作成は [!INCLUDE[net_v45](../includes/net-v45-md.md)] の新機能です。  
  
20. 設定、**に**のプロパティ、<xref:System.Activities.Statements.Assign>アクティビティを**インデックス**します。 設定、**値**のプロパティ、**割り当てる**アクティビティを**インデックス + 1**します。  
  
    カスタム**MyForEach**アクティビティを通じて渡される各値に対して 1 回、任意のアクティビティを呼び出すようになりましたが、**項目**アクティビティの入力として、コレクション内の値のコレクション。  
  
### <a name="use-the-custom-activity-in-a-workflow"></a>ワーク フローでのカスタム アクティビティの使用  
  
1. キーを押してプロジェクトをビルド**Ctrl + Shift + B**します。  
  
2. **ソリューション エクスプ ローラー**オープン**Workflow1.xaml**デザイナー。  
  
3. ドラッグ、 **MyForEach**アクティビティをツールボックスからデザイナー画面にします。 アクティビティは、プロジェクトと同じ名前のツールボックスのセクションにあります。  
  
4. 設定、**項目**のプロパティ、 **MyForEach**アクティビティを**new object[] {1,"abc"}** します。  
  
5. ドラッグ、<xref:System.Activities.Statements.WriteLine>からのアクティビティ、**プリミティブ**、ツールボックスのセクション、 **Delegate:body**のセクション、 **MyForEach**アクティビティ。  
  
6. 設定、**テキスト**のプロパティ、<xref:System.Activities.Statements.WriteLine>アクティビティを**Argument.ToString()** します。  
  
   ワーク フローの実行時に、コンソールには次のように表示されます。  
  
   **1**   
   **abc**