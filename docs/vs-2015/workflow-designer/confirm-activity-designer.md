---
title: Confirm アクティビティ デザイナー |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Confirm.UI
ms.assetid: c753b67b-b0e7-462a-bb4e-ba8db04a078d
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 29635044eb4cca558d631ab959b1b4f5480dbdbe
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977380"
---
# <a name="confirm-activity-designer"></a>Confirm アクティビティ デザイナー
**確認**作成および構成するアクティビティ デザイナーが使用される、<xref:System.Activities.Statements.Confirm>アクティビティ。  
  
## <a name="the-confirm-activity"></a>Confirm アクティビティ  
 <xref:System.Activities.Statements.Confirm> アクティビティは、<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> に含まれているアクティビティの <xref:System.Activities.Statements.CompensableActivity> を明示的に呼び出します。 <xref:System.Activities.Statements.Confirm> アクティビティが <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> の <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> 内、<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> 内、および <xref:System.Activities.Statements.CompensableActivity> 内のいずれでも使用されていない場合は、<xref:System.Activities.Statements.Confirm.Target%2A> プロパティを指定する必要があります。  
  
 <xref:System.Activities.Statements.CompensationToken> で指定された <xref:System.Activities.Statements.Compensate.Target%2A> は、<xref:System.Activities.Statements.CompensableActivity> の <xref:System.Activities.Statements.CompensableActivity.Body%2A> が正常に完了した後に <xref:System.Activities.Statements.CompensableActivity> を明示的に確認または補正する手段を提供します。  
  
### <a name="using-the-confirm-activity-designer"></a>Confirm アクティビティ デザイナーの使用  
 **確認**アクティビティ デザイナーが記載されて、**トランザクション**のカテゴリ、**ツールボックス**をクリックしてアクセスする、**ツールボックス** タブの左側にある、 [!INCLUDE[wfd2](../includes/wfd2-md.md)] (または、選択**ツールバー**から、**ビュー**メニューまたは CTRL + ALT + X)。  
  
 **確認**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**ドロップ、[!INCLUDE[wfd2](../includes/wfd2-md.md)]サーフェス任意の場所、アクティビティを通常配置など内、<xref:System.Activities.Statements.Sequence>します。 この操作により、Confirm という既定の <xref:System.Activities.Statements.Confirm> を持つ <xref:System.Activities.Activity.DisplayName%2A> アクティビティが作成されます。 <xref:System.Activities.Activity.DisplayName%2A>値を指定できますいずれかのヘッダーで編集、**確認**アクティビティ デザイナーまたは、 **DisplayName**プロパティ グリッドのボックスです。  
  
### <a name="the-confirm-properties"></a>Confirm のプロパティ  
 次の表に、<xref:System.Activities.Statements.Confirm> のプロパティと、デザイナーでのその使用方法を示します。 <xref:System.Activities.Activity.DisplayName%2A> プロパティはプロパティ グリッドまたは[!INCLUDE[wfd2](../includes/wfd2-md.md)]画面で編集できますが、<xref:System.Activities.Statements.Confirm.Target%2A> プロパティはプロパティ グリッドで編集する必要があります。  
  
|プロパティ名|必須|使用方法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.CancellationScope> アクティビティの表示名を指定します (省略可能)。 既定値は Confirm です。|  
|<xref:System.Activities.Statements.Confirm.Target%2A>|True|この <xref:System.Activities.InArgument%601> アクティビティの <xref:System.Activities.Statements.CompensationToken> を含む <xref:System.Activities.Statements.Confirm> を指定します。|  
  
## <a name="see-also"></a>関連項目  
 [トランザクション](../workflow-designer/transaction-activity-designers.md)   
 [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [補正](../workflow-designer/compensate-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)