---
title: '方法: 階層リンク ナビゲーションを使用して、|Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 4a688056-37dc-406a-9071-be2141e192fe
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 64f84d33a814937df74002ffeb2fe7453694377e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444145"
---
# <a name="how-to-use-breadcrumb-navigation"></a>方法: 階層リンク ナビゲーションを使用する
[!INCLUDE[wfd1](../includes/wfd1-md.md)]に表示されるアクティビティのセットを変更する主な方法は、次の 3 つです。  
  
1. ダブルクリックして、子アクティビティにドリル ダウンする。  
  
2. 階層リンク バーのボタンをクリックして、先祖アクティビティに移動する。  
  
3. アクティビティを直接展開するか、折りたたむ。  
  
### <a name="using-breadcrumb-navigation"></a>階層リンク バーの使用  
  
1. [!INCLUDE[wfd2](../includes/wfd2-md.md)]のアクティビティをダブルクリックして、クリックしたアクティビティのルート アクティビティを変更します。 クリックしたアクティビティはルートで完全に展開され、その先祖が階層リンク バーに表示されます。 これは、アクティビティのドリル インまたはドリル アウトと呼ばれることがあります。  
  
2. 現在のルート アクティビティの先祖に移動するには、階層リンク バーのアクティビティをクリックします。  
  
### <a name="expanding-or-collapsing-an-activity-in-place"></a>アクティビティの直接の展開または折りたたみ  
  
1. アクティビティのシェブロンをクリックすると、その場でアクティビティが展開されるか、折りたたまれます。  
  
2. ボタンのクリックによって展開の状態が変更されると、展開の新しい状態が XAML に保存されます。  
  
    > [!WARNING]
    > アクティビティには、その場で展開できないものもあります。 アクティビティをその場で展開できない状況は 2 つ考えられます。親アクティビティがその子アクティビティに対して、その場での展開を許可していない場合 (たとえば、フローチャート内のアクティビティをその場で展開できない) と、アクティビティ デザイナー自体でその場での展開が禁止されている場合です。 [!INCLUDE[wfd2](../includes/wfd2-md.md)]に含まれるアクティビティ デザイナーでは、その場での展開は禁止されていませんが、一部のカスタム アクティビティは、この理由で展開できない場合があります。  
  
### <a name="expanding-all-or-collapsing-all-activities"></a>すべてのアクティビティの展開または折りたたみ  
  
1. 使用して、**すべて展開**と**すべて折りたたみ**展開または折りたたみの現在の階層リンク ルートの下のアクティビティをすべてのユーザー インターフェイス内のボタン。 "すべて展開" および "すべて折りたたみ" はグローバル状態であることに注意してください。 つまり、階層リンク ナビゲーション、すべての展開を使用して、ルート アクティビティを変更するか"折りたたみ"状態のすべてがクリックするまで永続化する**復元**します。  
  
2. クリックすることができますが、すべての展開を適用するか、またはすべての状態を折りたたむ後、**復元**各アクティビティに以前に適用される状態に戻すに表示されるボタン。  
  
    > [!WARNING]
    > アクティビティがなど<xref:System.Activities.Statements.Flowchart>が選択の場で展開、機能に関連付けられている、**すべて展開**と**すべて折りたたむ**ボタンが無効になって、**フローチャート**デザイナー。 [!INCLUDE[crabout](../includes/crabout-md.md)] **フローチャート**デザイナーを参照してください、[フローチャート](../workflow-designer/flowchart-activity-designer.md)トピック。  
  
    > [!WARNING]
    > [すべて展開] 特別な効果があります**スイッチ**と**TryCatch**アクティビティ デザイナー。 クリックすると**すべて展開**、すべての switch ケースおよびすべての try、catch、finally ブロックが表示されます。 クリックすると**復元**または**すべて折りたたむ**その内容を表示する個々 のケース/ブロックをクリックすることができます、既定の状態にこれらのデザイナーを返します。