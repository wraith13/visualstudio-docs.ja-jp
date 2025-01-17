---
title: Visio ソリューション
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], Visio
- solutions [Office development in Visual Studio], Visio
- Visio [Office development in Visual Studio]
- templates [Office development in Visual Studio], Visio
- projects [Office development in Visual Studio], Visio
- Office solutions [Office development in Visual Studio], Visio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 69d795fe9e4243bbce51e1e137bb6704492bae32
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551278"
---
# <a name="visio-solutions"></a>Visio ソリューション
  Visual Studio には、Microsoft Office Visio の VSTO アドインを作成するために使用できるプロジェクト テンプレートが用意されています。 VSTO アドインを使用して、Visio の自動化、Visio 機能の拡張、または Visio ユーザー インターフェイス (UI) のカスタマイズが可能です。

 VSTO アドインの詳細については、「vsto アドインの[プログラミングの概要](../vsto/getting-started-programming-vsto-add-ins.md)」と「 [Vsto アドインのアーキテクチャ](../vsto/architecture-of-vsto-add-ins.md)」を参照してください。Microsoft Office を使用したプログラミングの初心者の場合は、「 [Visual Studio &#40;&#41;での Office 開発の概要](../vsto/getting-started-office-development-in-visual-studio.md)」を参照してください。

 **適用対象:** このトピックの情報は、Visio 2010 の VSTO アドインのプロジェクトに適用されます。 詳細については、「[Office アプリケーションおよびプロジェクトの種類別の使用可能な機能](../vsto/features-available-by-office-application-and-project-type.md)」を参照してください。

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="automate-visio-by-using-the-visio-object-model"></a>Visio オブジェクトモデルを使用して Visio を自動化する
 Visio オブジェクト モデルでは、組織図、フローチャート、プロジェクト タイムライン、ネットワーク ダイアグラム、事務所スペースなどのダイアグラムを Visio で自動的に作成するために使用できる多数のクラスが公開されています。 この API を使用して、次のような一般的なタスクを実行するコードを作成できます。

- 図形やテキストを作成し、ダイアグラムに配置する。

- ビジネス ロジックやユーザー入力に基づいて図形の動作を管理する。

- ダイアグラムの視覚エフェクト (パン、ズームなど) を制御する。

- アプリケーション UI をカスタマイズする。

- 外部データを Visio にインポートし、図形にリンクしてページ上にグラフィカルに表示する。

  Visio のオブジェクトモデルを使用して visio[図面](../vsto/working-with-visio-documents.md)を操作し、 [visio 図形](../vsto/working-with-visio-shapes.md)を操作するためのステップバイステップの手順とコード例を確認できます。

  VSTO アドインから Visio オブジェクト モデルにアクセスするには、プロジェクト内の `Application` クラスの `ThisAddIn` フィールドを使用します。 `Application` フィールドは、Visio の現在のインスタンスを表す `Microsoft.Office.Interop.Visio.Application` オブジェクトを返します。 詳細については、「[プログラム VSTO アドイン](../vsto/programming-vsto-add-ins.md)」を参照してください。

  Visio オブジェクト モデルを呼び出すときは、Visio のプライマリ相互運用機能アセンブリ (PIA) に用意された型を使用します。 PIA は、VSTO アドインのマネージド コードと Visio の COM オブジェクト モデルとの橋渡し役として機能します。 Visio PIA のすべての型は、`Microsoft.Office.Interop.Visio` 名前空間で定義されます。 プライマリ相互運用機能アセンブリの詳細については、「 [ &#40;office&#41;ソリューション開発の概要 VSTO](../vsto/office-solutions-development-overview-vsto.md)と[office プライマリ相互運用機能アセンブリ](../vsto/office-primary-interop-assemblies.md)」を参照してください。

## <a name="visio-object-model-overview"></a>Visio オブジェクトモデルの概要
 Visio オブジェクトモデルの概要については、visio オブジェクトモデルのリファレンスと Sdk へのリンクを含む、visio オブジェクトモデルの[概要](../vsto/visio-object-model-overview.md)に関するページを参照してください。

## <a name="customize-the-user-interface-of-visio"></a>Visio のユーザーインターフェイスのカスタマイズ
 Visio の UI には、次のようなカスタマイズ オプションがあります。

|タスク|詳細情報|
|----------|--------------------------|
|リボンをカスタマイズします。|[リボンの概要](../vsto/ribbon-overview.md)|

 Visio の UI をカスタマイズする方法の詳細については、 [Visio.UIObject](/office/vba/api/Visio.UIObject) クラスの VBA リファレンス ドキュメントを参照してください。

## <a name="see-also"></a>関連項目
- [VSTO アドインのプログラミングの概要](../vsto/getting-started-programming-vsto-add-ins.md)
- [Office ソリューションの開発&#40;の概要 VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [VSTO アドインのアーキテクチャ](../vsto/architecture-of-vsto-add-ins.md)
- [方法: Visual Studio での Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [プログラム VSTO アドイン](../vsto/programming-vsto-add-ins.md)
- [Office ソリューションにおけるコードの記述](../vsto/writing-code-in-office-solutions.md)
- [Office プライマリ相互運用機能アセンブリ](../vsto/office-primary-interop-assemblies.md)
- [Office UI のカスタマイズ](../vsto/office-ui-customization.md)
- [Visio オブジェクトモデルの概要](../vsto/visio-object-model-overview.md)
- [Office 開発における Visio 2010](http://go.microsoft.com/fwlink/?LinkId=199017)
