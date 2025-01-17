---
title: ワークフロー デザイナーの場合はアクティビティ デザイナー
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 762199906bbb84701c044b5fa9f3f3b8c6fdfdae
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62949202"
---
# <a name="if-activity-designer"></a>If アクティビティ デザイナー

<xref:System.Activities.Statements.If> アクティビティでは、条件を評価し、その評価の結果に応じてアクティビティを実行します。 このアクティビティは、手順型モデルのプログラミング スタイルを使用する場合に最も役立ちます。 <xref:System.Activities.Statements.If> アクティビティは、<xref:System.Activities.Statements.Sequence> アクティビティや <xref:System.Activities.Statements.Parallel> アクティビティなどの内部に入れ子にすることができます。 <xref:System.Activities.Statements.Flowchart> アクティビティを使用している場合は、代わりに、<xref:System.Activities.Statements.FlowDecision> アクティビティの使用を検討してください。

## <a name="if-properties-in-the-workflow-designer"></a>ワークフロー デザイナーでの If のプロパティ

次の表に、最も役に立つ <xref:System.Activities.Statements.If> アクティビティのプロパティと、デザイナーでのその使用方法を示します。

|プロパティ名|必須|使用法|
|-|--------------|-|
|<xref:System.Activities.Statements.If.Condition%2A>|True|実行する子アクティビティを決定する条件。 設定する、 <xref:System.Activities.Statements.If.Condition%2A>、Visual Basic の式を入力、**条件**ボックスに、**場合**アクティビティ デザイナーまたはプロパティ グリッドでします。|
|<xref:System.Activities.Statements.If.Else%2A>|False|場合に実行されるアクティビティ、<xref:System.Activities.Statements.If.Condition%2A>は**false**します。 によって実行されるアクティビティを追加する、<xref:System.Activities.Statements.If.Else%2A>分岐からアクティビティ、**ツールボックス**に、 **Else**ボックスに、**場合**アクティビティ デザイナーのヒント テキスト"ここにアクティビティをドロップ"。|
|<xref:System.Activities.Statements.If.Then%2A>|False|場合に実行されるアクティビティ、<xref:System.Activities.Statements.If.Condition%2A>は**true**します。 によって実行されるアクティビティを追加する、<xref:System.Activities.Statements.If.Then%2A>分岐からアクティビティ、**ツールボックス**に、**し**ボックスに、**場合**アクティビティ デザイナーのヒント テキスト"ここにアクティビティをドロップ"。|

## <a name="see-also"></a>関連項目

- [Sequence](../workflow-designer/sequence-activity-designer.md)
- [Parallel](../workflow-designer/parallel-activity-designer.md)
- [制御フロー](../workflow-designer/control-flow-activity-designers.md)