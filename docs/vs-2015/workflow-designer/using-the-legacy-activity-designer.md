---
title: 従来のアクティビティ デザイナーの使用 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- activities, configuring
- custom activities
- Activity Designer
- child activities, adding
- activities, adding child
- activities, creating custom
ms.assetid: 2fea8a05-6e58-423d-94bf-a822b15ffb80
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5755c6a3b4ece5b40c7799d83bdf33966d5c2b3e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62855776"
---
# <a name="using-the-legacy-activity-designer"></a>従来のアクティビティ デザイナーの使用
このトピックでは、従来の [!INCLUDE[wfd1](../includes/wfd1-md.md)]でアクティビティ デザイナーを使用する方法について説明します。 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] または [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] を対象とする場合は、従来のデザイナーを使用します。  
  
 アクティビティ デザイナーを使用すると、独自のカスタム アクティビティを作成できます。  
  
## <a name="creating-a-custom-activity"></a>カスタム アクティビティの作成  
 アクティビティ デザイナを使ってカスタム アクティビティを作成するには、次の手順に従います。  
  
1. **プロジェクト** メニューのをクリックして**アクティビティの追加**します。  
  
2. 選択、**アクティビティ**または**アクティビティ (コード分離付き)** テンプレート。  
  
   1. 使用して、**アクティビティ**アクティビティ定義と同じコード ファイル内のユーザー コード アクティビティを作成するテンプレート。  
  
   2. 使用して、**アクティビティ (コード分離付き)** アクティビティ定義がワークフロー マークアップや別のコード ファイル内のユーザー コードとして表現されるアクティビティを作成するテンプレート。  
  
3. アクティビティ名を入力または既定の名前をクリックして**追加**します。  
  
   型の新しいプロジェクトを作成して、カスタム アクティビティのセットを作成することも**Workflow Activity Library**します。 このプロジェクトの種類の詳細については、次を参照してください。[方法。ワークフロー アクティビティ ライブラリ (レガシ) 作成](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md)です。  
  
## <a name="configuring-an-activity"></a>アクティビティの構成  
 アクティビティ デザイナがアクティブであるときに、プロパティ ブラウザを使用すると、次の表にリストされているプロパティを構成できます。  
  
|プロパティ|コメント|  
|--------------|--------------|  
|**Name**|アクティビティの名前。|  
|**基本クラス**|アクティビティの派生元の基本クラス。 既定の基本クラスは[SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020)します。 **プロパティ**ウィンドウで、をクリックして、**ベース クラス**楕円 **[...]** で別の基本クラスを選択する、[参照し、.NET の種類 ダイアログ ボックス (レガシ) を選択](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md)します。|  
|**説明**|アクティビティに関するユーザー定義の説明。|  
|**有効**|設定**True**既定では、アクティビティの実行と検証を有効にします。 設定**False**アクティビティの実行と検証を無効にします。 アクティビティの実行と検証については、次を参照してください。[ワークフロー アクティビティの開発](http://go.microsoft.com/fwlink?LinkID=65024)します。|  
  
## <a name="adding-child-activities"></a>子アクティビティの追加  
 子アクティビティを、ツールボックスから設計中のアクティビティまでドラッグすることができます。 その後、プロパティ ブラウザを使ってそれぞれの子アクティビティを構成できます。  
  
## <a name="see-also"></a>関連項目  
 [ワークフロー アクティビティの開発](http://go.microsoft.com/fwlink?LinkID=65024)   
 [カスタム アクティビティの作成](http://go.microsoft.com/fwlink?LinkID=65021)   
 [従来のワークフロー アクティビティ](../workflow-designer/legacy-workflow-activities.md)   
 [カスタム アクティビティのサンプル](http://go.microsoft.com/fwlink?LinkID=65022)   
 [方法: ワークフロー アクティビティ ライブラリ (レガシ) を作成します。](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md)   
 [従来のワークフロー デザイナーの使用](../workflow-designer/using-the-legacy-workflow-designer.md)