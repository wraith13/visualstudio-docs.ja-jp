---
title: アクティビティ デザイナーの並列 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Parallel.UI
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 627a99fec632871b815904abd798c0e4bbfd6505
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62971343"
---
# <a name="parallel-activity-designer"></a>Parallel アクティビティ デザイナー
<xref:System.Activities.Statements.Parallel> アクティビティは、一連の子アクティビティを同時に実行するアクティビティです。  
  
## <a name="the-parallel-activity"></a>Parallel アクティビティ  
 <xref:System.Activities.Statements.Parallel> アクティビティは、子アクティビティを <xref:System.Activities.Statements.Parallel.Branches%2A> コレクションに格納します。 一部の子アクティビティがアイドル状態になる可能性がある場合は、<xref:System.Activities.Statements.Parallel> アクティビティの代わりに <xref:System.Activities.Statements.Sequence> アクティビティを使用してください。  
  
 <xref:System.Activities.Statements.Parallel> アクティビティには、ユーザーによって指定された <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> 式を保持する [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] プロパティがあります。 このプロパティは、各分岐の完了後に、<xref:System.Activities.Statements.Parallel> アクティビティによって評価されます。 評価されると、 **True**、<xref:System.Activities.Statements.Parallel>アクティビティが他の分岐を実行せずに完了します。 場合、<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>に評価されない**True**、<xref:System.Activities.Statements.Parallel>アクティビティのすべての子アクティビティが完了したときに完了します。  
  
### <a name="using-the-parallel-activity-designer"></a>Parallel アクティビティ デザイナーの使用  
 **並列**アクティビティ デザイナーが記載されて、**制御フロー**のカテゴリ、**ツールボックス**をクリックしてアクセスする、**ツールボックス** タブの左側にある、 [!INCLUDE[wfd2](../includes/wfd2-md.md)] (または、選択**ツールバー**から、**ビュー**メニューのまたは CTRL + ALT + X)。  
  
 **並列**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**ドロップ、[!INCLUDE[wfd2](../includes/wfd2-md.md)]サーフェス任意の場所のアクティビティ デザイナー通常配置しているなどを内部**シーケンス**アクティビティ デザイナー。 ドロップすると、 [!INCLUDE[wfd2](../includes/wfd2-md.md)]、作成、<xref:System.Activities.Statements.Parallel>を既定で含む、アクティビティ、<xref:System.Activities.Activity.DisplayName%2A>の**並列**  
  
 活動を追加する、 <xref:System.Activities.Statements.Parallel.Branches%2A> 、parallel アクティビティのコレクションから他のアクティビティ デザイナーをドラッグして、**ツールボックス**内の三角形にドロップし、**並列**アクティビティ デザイナー。 分岐に含まれるアクティビティのそばに三角形が配置されます。 この手順を繰り返すことによって、さらにアクティビティを追加できます。 ドラッグ アンド ドロップし内で、アクティビティの順序を変更できます、**並列**アクティビティ デザイナー。  
  
### <a name="parallel-activity-properties-in-the-workflow-designer"></a>ワークフロー デザイナーでの Parallel アクティビティのプロパティ  
 次の表に、Parallel アクティビティのプロパティと、デザイナーでのその使用方法を示します。  
  
|プロパティ名|必須|使用方法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|ヘッダーのアクティビティ デザイナーの表示名を指定します。 既定値は**並列**します。 値を必要に応じて編集、**プロパティ**グリッドまたは直接アクティビティ デザイナーのヘッダー。|  
|<xref:System.Activities.Statements.Parallel.Branches%2A>|True|実行される子アクティビティのコレクションが格納されます。|  
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|False|分岐の完了後に評価されます。 評価されると、 **True**、スケジュールされた保留分岐は取り消されます。 このプロパティが設定されていないかに評価される場合**False**、すべての子アクティビティが完了したときに、アクティビティが完了します。 既定値は**null**します。|  
  
## <a name="see-also"></a>関連項目  
 [シーケンス](../workflow-designer/sequence-activity-designer.md)   
 [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)   
 [制御フロー](../workflow-designer/control-flow-activity-designers.md)