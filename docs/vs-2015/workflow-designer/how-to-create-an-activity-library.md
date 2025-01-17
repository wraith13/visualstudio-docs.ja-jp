---
title: '方法: アクティビティ ライブラリを作成 |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 1eeebe74-7303-4345-8a83-fe37a26bc84b
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9463e46a7341a7da5c4aa79ae477d6aa0ff0c6cc
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686655"
---
# <a name="how-to-create-an-activity-library"></a>方法: アクティビティ ライブラリを作成する
カスタム アクティビティは、ワークフローで特定のビジネス プロセスをモデル化するために使用されます。 [!INCLUDE[vs2010](../includes/vs2010-md.md)] のアクティビティ ライブラリ テンプレートでは、[!INCLUDE[wfd1](../includes/wfd1-md.md)]を使用して、こうしたカスタム アクティビティを視覚的に作成できます。  
  
### <a name="to-create-a-workflow-activity-library"></a>ワークフロー アクティビティ ライブラリを作成するには  
  
1. [!INCLUDE[vs2010](../includes/vs2010-md.md)] を起動します。  
  
2. **ファイル**メニューで、**新規**、し、**プロジェクト**.  
  
     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
3. **プロジェクトの種類**ペインで、**ワークフロー**いずれかから、 **Visual c#** プロジェクトまたは**Visual Basic**に応じてグループ化、優先する言語。  
  
4. **テンプレート**ペインで、**アクティビティ ライブラリ**します。  
  
5. **名前**ボックスに、簡単に特定できるようにする、プロジェクトのわかりやすい名前を入力します。  
  
6. **場所** ボックスに入力してプロジェクトを保存するディレクトリに**参照**それに移動します。  
  
7. **ソリューション**ボックスに、ソリューションでは、わかりやすい名前を入力し、をクリックして**OK**します。  
  
    > [!NOTE]
    > 既存のソリューションのワークフロー コンソール アプリケーションを追加する場合は、そのソリューションを開きます[!INCLUDE[vs2010](../includes/vs2010-md.md)]でソリューションを右クリックして**ソリューション エクスプ ローラー**、選択および**追加**、し**新しいプロジェクト.** 開く、**新しいプロジェクト** ダイアログ ボックス。 上記の手順を実行します。  
  
8. プロジェクト テンプレートによって、XAML でアクティビティ定義が作成されます。 [!INCLUDE[wfd1](../includes/wfd1-md.md)] で、カスタム アクティビティ用のキャンバスが開かれて表示されます。  
  
9. アクティビティをドラッグして、**ツールボックス**に含めるカスタム アクティビティ デザイン サーフェイスにします。  
  
    > [!CAUTION]
    > カスタム アクティビティの本体に含めることができる子アクティビティは 1 つのみです。ただし、その子アクティビティは、<xref:System.Activities.Statements.Sequence> アクティビティや <xref:System.Activities.Statements.Flowchart> アクティビティなどの複合アクティビティにすることができます。  
  
## <a name="see-also"></a>関連項目  
 [方法: アクティビティを作成します。](https://msdn.microsoft.com/library/c09b1e99-21b5-4d96-9c04-ec31db3f4436)   
 [ワークフロー プロジェクトの作成](../workflow-designer/creating-a-workflow-project.md)