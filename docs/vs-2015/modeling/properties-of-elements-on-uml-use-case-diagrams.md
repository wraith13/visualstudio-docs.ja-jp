---
title: ユース ケース図の UML 要素のプロパティ |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.usecasediagram.artifact.properties
- vs.teamarch.usecasediagram.shapes.properties
helpviewer_keywords:
- use case diagrams, properties
ms.assetid: 2728fb26-a275-4fce-8a2c-5a78af6bee04
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b52afab80bc22c03dc5ff980b937cad53869f5db
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444401"
---
# <a name="properties-of-elements-on-uml-use-case-diagrams"></a>UML ユース ケース図の要素のプロパティ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML ユース ケース図では、図の各要素にプロパティが存在します。 要素のプロパティを表示するには、図、または要素を右クリックして**UML モデル エクスプ ローラー**し**プロパティ**します。 プロパティが表示されます、**プロパティ**ウィンドウ。  
  
> [!NOTE]
> このトピックでは、UML ユース ケース図の要素のプロパティについて説明します。 UML アクティビティ図を読み取る方法の詳細については、次を参照してください。 [UML ユース ケース図。Reference](../modeling/uml-use-case-diagrams-reference.md)」(UML クラス図: リファレンス) を参照してください。 UML アクティビティ図を描画する方法の詳細については、次を参照してください。 [UML ユース ケース図。ガイドライン](../modeling/uml-use-case-diagrams-guidelines.md)します。  
  
## <a name="properties-of-elements"></a>要素のプロパティ  
  
|プロパティ|既定値|要素|説明|  
|--------------|-------------|-------------|-----------------|  
|**Name**|既定名|すべて|要素を指定します。|  
|**修飾名**|パッケージ:名前|すべて|要素を一意に識別します。 要素を格納するパッケージの修飾名が先頭につきます。|  
|**作業項目**|関連付けなし|すべて|この要素に関連付けられている作業項目の数。 作業項目に関連付けるを参照してください。[モデル要素をリンクし、作業項目](../modeling/link-model-elements-and-work-items.md)します。|  
|**説明**|(なし)|すべて|ここに、要素に関する一般的なメモを作成できます。|  
|**色**|(既定値)|すべて|シェイプの色。 他のプロパティとは異なり、これは図形が表示する要素のプロパティではありません。|  
|**イメージのパス**|(なし)|アクター|既定のアクター アイコンの代わりに使われるイメージのファイル パス。 このアイコンは、Visual Studio プロジェクト内のリソース ファイルである必要があります。|  
|**件名**|(なし)|ユース ケース|ユース ケースを所有するサブシステムまたは他の型。<br /><br /> 図のサブシステムにユース ケースを配置することで、設定できます。|  
|**可視性**|Public|ユース ケース、アクター、サブシステム|**パブリック**- グローバルに参照できます。<br /><br /> **パッケージ**- パッケージ内で参照できます。|  
|**IsAbstract**|False|ユース ケース、アクター、サブシステム|True の場合、型をインスタンス化することはできません。型は他の定義による特殊化のベースとして使われることを意図しています。|  
|**直接インスタンス化します。**|True|サブシステム|サブシステムは、設計の成果物としてのみ存在します。 実行時には、そのパートのみ存在します。|  
|**ハイパーリンク**|(なし)|成果物|成果物からのリンクが設定された図またはドキュメントの URL またはファイル パス。|  
  
 関連付けのプロパティの一覧では、次を参照してください。 [uml の関連付けのプロパティにクラス ダイアグラム](../modeling/properties-of-associations-on-uml-class-diagrams.md)します。  
  
## <a name="see-also"></a>関連項目  
 [UML ユース ケース図: 参照](../modeling/uml-use-case-diagrams-reference.md)   
 [UML ユース ケース図: ガイドライン](../modeling/uml-use-case-diagrams-guidelines.md)
