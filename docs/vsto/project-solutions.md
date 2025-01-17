---
title: プロジェクトソリューション
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [Office development in Visual Studio], Project
- Office solutions [Office development in Visual Studio], Project
- Project [Office development in Visual Studio]
- templates [Office development in Visual Studio], Project
- Office projects [Office development in Visual Studio], Project
- solutions [Office development in Visual Studio], Project
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f2158918aa6c2487719043abd797eb9d5e8f3f2e
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551386"
---
# <a name="project-solutions"></a>プロジェクトソリューション
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] には、Microsoft Office Project の VSTO アドインを作成するために使用できるプロジェクト テンプレートが用意されています。 VSTO アドインを使用すると、Project の自動化、Project 機能の拡張、Project ユーザー インターフェイス (UI) のカスタマイズが可能です。

 VSTO アドインの詳細については、「vsto アドインの[プログラミングの概要](../vsto/getting-started-programming-vsto-add-ins.md)」と「 [Vsto アドインのアーキテクチャ](../vsto/architecture-of-vsto-add-ins.md)」を参照してください。Microsoft Office を使用したプログラミングの初心者の場合は、「 [Visual Studio &#40;&#41;での Office 開発の概要](../vsto/getting-started-office-development-in-visual-studio.md)」を参照してください。

 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="automate-project-by-using-the-project-object-model"></a>Project オブジェクトモデルを使用してプロジェクトを自動化する
 Project オブジェクト モデルでは、Project の自動化に使用できる型が多数公開されています。 これらの型により、プロジェクト内のタスクをプログラムによって作成したり変更したりするなど、一般的なタスクを行うコードを記述できます。

 VSTO アドインから project オブジェクトモデルにアクセスするには、プロジェクトの`Application` `ThisAddIn`クラスのフィールドを使用します。 この`Application`フィールドは、 `Microsoft.Office.Interop.MsProject.Application` Project の現在のインスタンスを表すオブジェクトを返します。 詳細については、「[プログラム VSTO アドイン](../vsto/programming-vsto-add-ins.md)」を参照してください。

 Project オブジェクト モデルを呼び出すときには、Project のプライマリ相互運用機能アセンブリに用意された型を使用します。 プライマリ相互運用機能アセンブリは、VSTO アドインのマネージド コードと Project の COM オブジェクト モデルとの仲介役を果たします。 Project プライマリ相互運用機能アセンブリ内の型は、すべて `Microsoft.Office.Interop.MSProject` 名前空間に定義されています。 プライマリ相互運用機能アセンブリの詳細については、「 [ &#40;office&#41;ソリューション開発の概要 VSTO](../vsto/office-solutions-development-overview-vsto.md)と[office プライマリ相互運用機能アセンブリ](../vsto/office-primary-interop-assemblies.md)」を参照してください。

## <a name="use-the-project-object-model-documentation"></a>プロジェクトオブジェクトモデルのドキュメントを使用する
 Project オブジェクト モデルの詳細については、Project の VBA オブジェクト モデルのリファレンスを参照してください。 VBA オブジェクト モデルのリファレンスでは、Visual Basic for Applications (VBA) コードに公開される Project オブジェクト モデルについて説明しています。 詳細については、「 [Project 2010 オブジェクトモデルのリファレンス](http://go.microsoft.com/fwlink/?LinkId=199771)」を参照してください。

 VBA オブジェクト モデルのリファレンス内のオブジェクトとメンバーはすべて、Project プライマリ相互運用機能アセンブリ (PIA) の型とメンバーに対応します。 たとえば、VBA オブジェクト モデルのリファレンスで、暦オブジェクトの対応する、 `Microsoft.Office.Interop.MSProject.Calendar` Project PIA の型。 VBA オブジェクトモデルのリファレンスでは、ほとんどのプロパティ、メソッド、およびイベントのコード例が提供されていますが、この参照のC# vba コードを、で作成した Project VSTO アドインプロジェクトで使用する場合は、Visual Basic または Visual に変換する必要があります。Visual Studio を使用する。

> [!NOTE]
> 現在のところ、Project プライマリ相互運用機能アセンブリに関するリファレンス ドキュメントは提供されていません。

### <a name="infrastructure-types-in-the-project-primary-interop-assembly"></a>Project プライマリ相互運用機能アセンブリのインフラストラクチャの種類
 Project PIA を使用するコードを作成すると、VBA リファレンスには記載されていない型が多数あることに気付きます。 そうした追加の型は、Project の COM ベースのオブジェクト モデルに含まれるオブジェクトをマネージド コードに変換する場合に役立ちますが、コード内で直接使用することを目的としたものではありません。

 詳細については、「 [Office プライマリ相互運用機能アセンブリのクラスとインターフェイスの概要](http://go.microsoft.com/fwlink/?LinkId=189592)」を参照してください。

## <a name="customize-the-user-interface-of-project"></a>Project のユーザーインターフェイスのカスタマイズ
 Project の UI は次の方法でカスタマイズできます。

|タスク|詳細情報|
|----------|--------------------------|
|Project のリボンにカスタム タブを追加する。|[リボンの概要](../vsto/ribbon-overview.md)|

 プロジェクトおよびその他の Microsoft Office アプリケーションの UI をカスタマイズする方法の詳細については、「 [OFFICE ui のカスタマイズ](../vsto/office-ui-customization.md)」を参照してください。

## <a name="see-also"></a>関連項目
- [チュートリアル: Project 用の最初の VSTO アドインを作成する](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)
- [VSTO アドインのプログラミングの概要](../vsto/getting-started-programming-vsto-add-ins.md)
- [Office ソリューションの開発&#40;の概要 VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [VSTO アドインのアーキテクチャ](../vsto/architecture-of-vsto-add-ins.md)
- [方法: Visual Studio での Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [プログラム VSTO アドイン](../vsto/programming-vsto-add-ins.md)
- [Office ソリューションにおけるコードの記述](../vsto/writing-code-in-office-solutions.md)
- [Office プライマリ相互運用機能アセンブリ](../vsto/office-primary-interop-assemblies.md)
- [Office UI のカスタマイズ](../vsto/office-ui-customization.md)
- [Office 開発における project 2010 および Project Server 2010](http://go.microsoft.com/fwlink/?LinkId=199016)
