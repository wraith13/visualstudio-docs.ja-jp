﻿---
title: '方法: グレースケール テクスチャ シェーダーを作成する |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 79181d81-44af-445e-9a18-03483dd70260
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b43e7806ebf6d67300fdee7be165c7cd745c4acb
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431717"
---
# <a name="how-to-create-a-grayscale-texture-shader"></a>方法: グレースケール テクスチャ シェーダーを作成する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このドキュメントでは、シェーダー デザイナーと DGSL (Directed Graph Shader Language) を使用してグレースケール テクスチャ シェーダーを作成する方法を説明します。 このシェーダーは、テクスチャ サンプルの RGB 色の値を変更し、その値を未変更のアルファ値と併用して最終的な色を設定します。  
  
## <a name="creating-a-grayscale-texture-shader"></a>グレースケール テクスチャ シェーダーの作成  
 テクスチャ サンプルの色の値を変更してから最終的な出力の色に記述することで、グレースケール テクスチャ シェーダーを実装できます。  
  
 開始する前に、**[プロパティ]** ウィンドウと**ツールボックス**が表示されていることを確認します。  
  
#### <a name="to-create-a-grayscale-texture-shader"></a>グレースケール テクスチャ シェーダーを作成するには  
  
1. 「[方法:基本的なテクスチャ シェーダーを作成](../designers/how-to-create-a-basic-texture-shader.md)です。  
  
2. **[テクスチャ サンプル]** ノードの **[RGB]** ターミナルを **[最終的な色]** ノードの **[RGB]** ターミナルから接続解除します。 **[選択]** モードで、**[テクスチャ サンプル]** ノードの **[RGB]** ターミナルを選択し、**[リンクの解除]** を選択します。 これにより、次の手順で追加するノードのための領域を確保できます。  
  
3. グラフに **[彩度を下げる]** ノードを追加します。 **ツールボックス**の **[フィルター]** で **[彩度を下げる]** を選択し、デザイン サーフェイスに移動します。  
  
4. **[彩度を下げる]** ノードを使用して、グレースケールの値を計算します。 **[選択]** モードで、**[テクスチャ サンプル]** ノードの **[RGB]** ターミナルを **[彩度を下げる]** ノードの **[RGB]** ターミナルに移動します。  
  
   > [!NOTE]
   > 既定では、**[彩度を下げる]** ノードは、入力色の彩度を全体的に下げ、グレースケール変換に標準的な輝度の重みを使用します。 **[輝度]** プロパティの値を変更するか、入力色の彩度を一部だけ下げて、**[彩度を下げる]** ノードの動作を変更できます。 入力色の彩度を部分的に下げるには、**[彩度を下げる]** ノードの **[パーセント]** ターミナルに範囲 [0,1) のスカラー値を提供します。  
  
5. グレースケールの色の値を最終的な色に接続します。 **[彩度を下げる]** ノードの **[出力]** ターミナルを **[最終的な色]** ノードの **[RGB]** ターミナルに移動します。  
  
   次の図は、完成したシェーダー グラフと、立体に適用されるシェーダーのプレビューを示します。  
  
> [!NOTE]
> この図では、平面がプレビューの図形として使用され、テクスチャはシェーダーの効果がわかりやすくなるように指定されています。  
  
 ![シェーダー グラフとその効果のプレビュー](../designers/media/digit-grayscale-effect.png "Digit-Grayscale-Effect")  
  
 シェーダーによっては、特定の図形を使用すると、より適切にプレビューできる可能性があります。 シェーダー デザイナーでのシェーダーのプレビューの詳細については、「[シェーダー デザイナー](../designers/shader-designer.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目
 [方法: シェーダーを 3-D モデルに適用します。](../designers/how-to-apply-a-shader-to-a-3-d-model.md)   
 [方法: シェーダーをエクスポートします。](../designers/how-to-export-a-shader.md)   
 [イメージ エディター](../designers/image-editor.md)   
 [シェーダー デザイナー](../designers/shader-designer.md)   
 [シェーダー デザイナー ノード](../designers/shader-designer-nodes.md)
