---
title: ワークフロー デザイナー - Rethrow アクティビティ デザイナー
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 558ff5a36d172b8cd1fef0b811d1eaa920b90c6d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63009276"
---
# <a name="rethrow-activity-designer"></a>Rethrow アクティビティ デザイナー

**を再スロー**作成および構成するアクティビティ デザイナーが使用される、<xref:System.Activities.Statements.Rethrow>アクティビティ。

## <a name="the-rethrow-activity"></a>Rethrow アクティビティ

<xref:System.Activities.Statements.Rethrow> アクティビティでは、以前にスローされた例外をスローします。 このアクティビティは、<xref:System.Activities.Statements.Catch> アクティビティの <xref:System.Activities.Statements.TryCatch> ハンドラーでのみ使用できます。

### <a name="use-the-rethrow-activity-designer"></a>ReThrow アクティビティ デザイナーを使用します。

アクセス、**を再スロー**内のアクティビティ デザイナー、**エラー処理**のカテゴリ、**ツールボックス**します。 **を再スロー**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**どこにも、アクティビティを通常配置など内に、ワークフロー デザイナー画面にドロップし、<xref:System.Activities.Statements.Sequence>します。 アクティビティ デザイナーをドロップを作成、 <xref:System.Activities.Statements.Rethrow> 、既定値は、アクティビティ**DisplayName** Throw の。 <xref:System.Activities.Activity.DisplayName%2A>のヘッダーに値を編集できる、**を再スロー**アクティビティ デザイナー、または、 **DisplayName**プロパティ グリッドのボックスです。

### <a name="the-rethrow-properties"></a>Rethrow のプロパティ

次の表は、<xref:System.Activities.Statements.Rethrow>プロパティ、デザイナーでの使用方法について説明します。

|プロパティ名|必須|使用方法|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Rethrow> アクティビティの表示名を指定します (省略可能)。 既定値は Rethrow です。|

## <a name="see-also"></a>関連項目

- [コレクション](../workflow-designer/collection-activity-designers.md)
- [Throw](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)