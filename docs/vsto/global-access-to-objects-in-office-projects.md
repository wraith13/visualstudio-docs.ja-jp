---
title: Office プロジェクト内のオブジェクトへのグローバル アクセス
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ThisDocument_Shutdown
- ThisDocument_Startup
- Globals class, object global access
- worksheets [Office development in Visual Studio], global access
- documents [Office development in Visual Studio], global access
- event handlers [Office development in Visual Studio]
- ThisWorkbook_Startup
- application-level addins [Office development in Visual Studio]
- addins [Office development in Visual Studio], events
- workbooks [Office development in Visual Studio], global access
- ThisWorkbook_Shutdown
- document-level customizations [Office development in Visual Studio]
- Startup event
- Shutdown event
- projects [Office development in Visual Studio], global access
- Office documents [Office development in Visual Studio, global access
- ThisAddin_Startup
- events [Office development in Visual Studio]
- ThisAddIn_Shutdown
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7266e7fa26574332bcb343b552eea2b707a8672b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63427946"
---
# <a name="global-access-to-objects-in-office-projects"></a>Office プロジェクト内のオブジェクトへのグローバル アクセス
  Office プロジェクトを作成すると、Visual Studio は自動的に `Globals` という名前のクラスをプロジェクトに生成します。 `Globals` クラスを使用して、プロジェクト内の任意のコードから実行時に異なる複数のプロジェクト項目にアクセスすることができます。

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="how-to-use-the-globals-class"></a>Globals クラスを使用する方法
 `Globals` はプロジェクト内の特定の項目への参照を保持する静的クラスです。 `Globals` クラスを使用することで、実行時にプロジェクト内の任意のコードから次の項目へとアクセスすることができます。

- Excel ブックまたはテンプレート プロジェクトの `ThisWorkbook` および `Sheet`*n* クラス。 これらのオブジェクトは、 `Globals.ThisWorkbook` および `Sheet`*n* プロパティを使用してアクセスすることができます。

- Word 文書またはテンプレート プロジェクトの `ThisDocument` クラス。 このオブジェクトには、 `Globals.ThisDocument` プロパティを使用してアクセスすることができます。

- `ThisAddIn` VSTO アドイン プロジェクト内のクラス。 このオブジェクトには、 `Globals.ThisAddIn` プロパティを使用してアクセスすることができます。

- リボン デザイナーを使用してカスタマイズした、プロジェクト内のすべてのリボン。 リボンには、 `Globals.Ribbons` プロパティを使用してアクセスすることができます。 詳細については、次を参照してください。[実行時にリボンをアクセス](../vsto/accessing-the-ribbon-at-run-time.md)します。

- Outlook VSTO アドイン プロジェクトのすべての Outlook フォーム領域。 フォーム領域には、 `Globals.FormRegions` プロパティを使用してアクセスすることができます。 詳細については、次を参照してください。[実行時にフォーム領域へのアクセス](../vsto/accessing-a-form-region-at-run-time.md)します。

- [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] または [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]をターゲットとするプロジェクトで実行時にリボン コントロールおよびホスト項目を作成できるようにするファクトリ オブジェクト。 このオブジェクトには、 `Globals.Factory` プロパティを使用してアクセスすることができます。 このオブジェクトは、次のいずれかのインターフェイスを実装するクラスのインスタンスです。

  - <xref:Microsoft.Office.Tools.Factory>

  - <xref:Microsoft.Office.Tools.Excel.Factory>

  - <xref:Microsoft.Office.Tools.Outlook.Factory>

  - <xref:Microsoft.Office.Tools.Word.Factory>

  たとえば、 `Globals.Sheet1` プロパティを使用すると、Excel のドキュメントレベルのプロジェクトの操作ウィンドウでユーザーがボタンをクリックした場合に <xref:Microsoft.Office.Tools.Excel.NamedRange> の `Sheet1` コントロールにテキストを挿入することができます。

  [!code-vb[Trin_VstcoreProgramming#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#1)]
  [!code-csharp[Trin_VstcoreProgramming#1](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs#1)]

## <a name="initialize-the-globals-class"></a>Globals クラスを初期化します。
 使用を試みるコード、`Globals`クラスのドキュメントまたは VSTO アドインが初期化される前に、実行時の例外をスロー可能性があります。 たとえば、クラス レベルの変数の宣言が `Globals` を使用することで失敗する場合があります。これは、宣言されたオブジェクトがインスタンス化される前に、 `Globals` クラスがすべてのホスト項目への参照を使用して初期化されない可能性があるためです。

> [!NOTE]
> `Globals` クラスは設計時に初期化されることはありませんが、コントロールのインスタンスがデザイナーによって作成されます。 つまりのプロパティを使用するユーザー コントロールを作成する場合、`Globals`クラスから、ユーザー コントロール クラス内でオンにしてください、プロパティが返すかどうか**null**返されたオブジェクトを使用する前にします。

## <a name="see-also"></a>関連項目
- [実行時にリボンへのアクセスします。](../vsto/accessing-the-ribbon-at-run-time.md)
- [実行時にフォーム領域へのアクセスします。](../vsto/accessing-a-form-region-at-run-time.md)
- [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)
- [Document ホスト項目](../vsto/document-host-item.md)
- [Workbook ホスト項目](../vsto/workbook-host-item.md)
- [Worksheet ホスト項目](../vsto/worksheet-host-item.md)
- [Office ソリューションにおけるコードの記述](../vsto/writing-code-in-office-solutions.md)
