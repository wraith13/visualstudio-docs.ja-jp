---
title: Modeling SDK の API リファレンス
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
ms.assetid: 590c9a69-4e22-4841-bb23-f32e80ec1e76
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6a290227b120958b5bb3407393dcff33b247b20d
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2019
ms.locfileid: "68872020"
---
# <a name="api-reference-for-modeling-sdk-for-visual-studio"></a>Modeling SDK for Visual Studio の API リファレンス
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio の視覚化およびモデリング SDK には、ドメイン固有言語 (DSL) と UML ツールがビルドされるプラットフォームが用意されています。

> [!NOTE]
> UML モデリング API の詳細については、「 [Uml モデリング機能拡張の Api リファレンス](../modeling/api-reference-for-uml-modeling-extensibility.md)」を参照してください。 テキスト変換の詳細については、「 [T4 テキスト変換のカスタマイズ](../modeling/customizing-t4-text-transformation.md)」を参照してください。

 このセクションには、"Microsoft.VisualStudio.Modeling"で始まる名前を持つ名前空間のリファレンスが含まれています。

|名前空間|Content|
|---------------|-------------|
|<xref:Microsoft.VisualStudio.Modeling?displayProperty=fullName>|ModelElement、DSL で定義するすべてのドメイン クラスの基本クラスであるなどのクラス。|
|<xref:Microsoft.VisualStudio.Modeling.Design?displayProperty=fullName>|DSL 定義の一部を形成するクラス。|
|<xref:Microsoft.VisualStudio.Modeling.Diagnostics?displayProperty=fullName>|モデル ストア ビューアーとパフォーマンス測定ツールです。|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams?displayProperty=fullName>|ShapeElement、DSL で定義するすべての図形の基本クラスであるなどのクラス。|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement?displayProperty=fullName>|メソッドのジェスチャと選択します。|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition?displayProperty=fullName>|DSL 定義のデザイナーの API です。|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.Design?displayProperty=fullName>|DSL 定義のデザイナーの内部クラス。|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement?displayProperty=fullName>|コマンド、ジェスチャ、および検証を使用して DSL デザイナーを拡張できる属性。|
|<xref:Microsoft.VisualStudio.Modeling.Extensibility?displayProperty=fullName>|DSL の拡張機能を実装する ModelElement の拡張メソッド。|
|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement?displayProperty=fullName>|拡張属性|
|<xref:Microsoft.VisualStudio.Modeling.Immutability?displayProperty=fullName>|読み取り専用にモデルの部分を作成できます。|
|[VisualStudio の統合](/previous-versions/ee904412(v=vs.140))|役立つ Modelbus API では、さまざまなモデルを統合します。|
|[VisualStudio を選択します。](/previous-versions/ee904394(v=vs.140))|ユーザー モデルおよび Modelbus 参照を作成する要素に移動できるように、ダイアログ ボックス。|
|`Microsoft.VisualStudio.Modeling.Integration.Picker.Hosting`|選択サービス。|
|[VisualStudio を作成します。](/previous-versions/ee869435(v=vs.140))|の[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]modelbus アダプターフレームワーク。|
|[VisualStudio を選択してください。](/previous-versions/ee886769(v=vs.140))|ユーザーがモデルと Modelbus 参照を作成する要素に移動できるピッカー ダイアログ ボックス。|
|<xref:Microsoft.VisualStudio.Modeling.Shell?displayProperty=fullName>|Dsl と[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]の間のインターフェイス。|
|<xref:Microsoft.VisualStudio.Modeling.Shell.ExtensionEnablement?displayProperty=fullName>|ショートカット (コンテキスト) メニューのコマンドを定義できます。|
|<xref:Microsoft.VisualStudio.Modeling.Validation?displayProperty=fullName>|検証制約を定義できます。|

## <a name="see-also"></a>関連項目

- [UML モデリング機能拡張の API リファレンス](../modeling/api-reference-for-uml-modeling-extensibility.md)
- [T4 テキスト変換のカスタマイズ](../modeling/customizing-t4-text-transformation.md)
