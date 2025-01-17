---
title: 従来のワークフロー デザイナーの使用 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- Visual Studio 2005 Extensions for Windows Workflow Foundation, about
ms.assetid: 7af53077-afd7-465f-9c1d-b387e9d4f216
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 899f0b81055f67c323c2efb60a07280368dad321
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62855843"
---
# <a name="using-the-legacy-workflow-designer"></a>従来のワークフロー デザイナーの使用
[!INCLUDE[wfd2](../includes/wfd2-md.md)] が備えている従来の[!INCLUDE[vs2010](../includes/vs2010-md.md)]を使用すると、[!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] または [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] を対象とすることができます。  
  
 どちらかを選択してアクセスした、 **.NET Framework 3.0**オプションまたは **.NET Framework 3.5**オプションで、ドロップダウン リストの上部にある、**新しいプロジェクト**ウィンドウ。 既定のオプションに[!INCLUDE[vs2010](../includes/vs2010-md.md)]は **.NET Framework 4**作成に使用される[!INCLUDE[wf](../includes/wf-md.md)]を対象とするアプリケーション、[!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)]します。  
  
 [!INCLUDE[wfd2](../includes/wfd2-md.md)] では、使い慣れた [!INCLUDE[wf](../includes/wf-md.md)] ユーザー インターフェイスを使用して [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] アプリケーションをグラフィカルに作成できます。 [!INCLUDE[wf](../includes/wf-md.md)] アプリケーションは、アクティビティと呼ばれるワークフロー プロセス ステップで構成されます。 ワークフローを作成するから、それぞれのアクティビティ デザイナーをドラッグしてデザイン サーフェイスにアクティビティを作成**ツールボックス**デザイン サーフェイスにします。  
  
 次の表に、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] for Windows Workflow Foundation の主な機能を示します。  
  
|機能|説明|  
|-------------|-----------------|  
|アクティビティのドラッグ アンド ドロップ|アクティビティをドラッグして、**ツールボックス**ワークフローを作成するデザイン サーフェイスにします。|  
|プロパティ ブラウザー|標準**プロパティ**ウィンドウ[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]アクティビティのプロパティを構成するために使用します。|  
|ズーム|双眼鏡**拡大レベル**アイコンは、デザイン画面の右側にある垂直スクロール バーの下にあります。 ワークフローのグラフィック表示を拡大または縮小するには、双眼鏡をクリックしてズーム倍率を選択します。使用することも、**パン**アイコン拡大鏡のカーソル オプションに拡大/縮小します。|  
|パン|**パン**アイコン、4 つの方向を指す 4 つの交差矢印が描かれた円は、双眼鏡ズーム アイコンのすぐ下、デザイン画面の右側にある垂直スクロール バーの下にあります。 パン アイコンをクリックすると、次のようなカーソル オプションがポップアップ メニューに表示されます。<br /><br /> -**ズームイン**｡ ｢ 虫葭カーソルでは、デザイン画面をクリックしてズーム インすることができます。<br />-**ズーム アウト**｡ ｢ 虫葭カーソルでは、デザイン画面をクリックしてズーム アウトすることができます。<br />-**ナビゲーション ツール**手形カーソルでは、「つかんで」、ワークフロー デザイン サーフェイスでのビューを移動することができます。<br />-**既定**矢印カーソルでは、既定の矢印カーソルに、他のカーソルから切り替えることができます。|  
|自動スクロール|ワークフローが大きいために、デザイン サーフェイスの表示領域外にアクティビティを配置する必要が生じる場合があります。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] のデザイン サーフェスでは、アクティビティを配置したい方向に最も近い側の端にアクティビティをドラッグすることができます。 デザイン サーフェイスの表示が、その方向に自動的にスクロールされます。|  
|スマート タグ|構成が完了していないアクティビティ、または構成が有効でないアクティビティは、感嘆符アイコン付きで表示されます。 このアイコンをクリックして表示されるドロップダウン リストで、アクティビティに存在する、必要な構成を確認できます。 使用することができますし、**プロパティ**アクティビティを適切に構成するウィンドウ。 アクティビティのすべてのプロパティが正しく構成されれば、感嘆符アイコンは表示されなくなります。|  
  
## <a name="in-this-section"></a>このセクションの内容  
 [Visual Studio ワークフローのウィンドウ (レガシ)](../workflow-designer/visual-studio-workflow-windows-legacy.md)  
  
 [従来のワークフロー プロジェクトの作成](../workflow-designer/creating-legacy-workflow-projects.md)  
  
 [シーケンシャル ワークフロー ビュー (レガシ)](../workflow-designer/sequential-workflow-views-legacy.md)  
  
 [従来のワークフロー アクティビティ](../workflow-designer/legacy-workflow-activities.md)  
  
 [ワークフロー内でのテーマの使用 (レガシ)](../workflow-designer/using-themes-in-workflows-legacy.md)  
  
 [従来のステート マシン ワークフロー デザイナーの使用](../workflow-designer/using-the-legacy-state-machine-workflow-designer.md)  
  
 [従来のアクティビティ デザイナーの使用](../workflow-designer/using-the-legacy-activity-designer.md)  
  
 [従来の Designer for Windows Workflow Foundation UI ヘルプ](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)  
  
## <a name="see-also"></a>関連項目  
 [ワークフローの開発](http://go.microsoft.com/fwlink?LinkID=65010)