---
title: 数値演算ノード
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: adc225cc-1cf5-4f7c-9b00-e7ac8450b6b9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 43809923b730800cfa71185b136743f3098239e1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62844243"
---
# <a name="math-nodes"></a>数値演算ノード

シェーダー デザイナーでは、代数演算、論理演算、三角関数演算などの数値演算が演算ノードによって実行されます。

> [!NOTE]
> シェーダー デザイナーで演算ノードを使用する際には、型の上位変換が特に顕著に見られます。 型の上位変換が入力パラメーターに及ぼす影響については、「[シェーダー デザイナー ノード](../designers/shader-designer-nodes.md)」の「入力の上位変換」を参照してください。

## <a name="math-node-reference"></a>数値演算ノードの参照

|ノード|説明|プロパティ|
|----------|-------------|----------------|
|**Abs**|指定された入力の要素ごとの絶対値を計算します。<br /><br /> 入力 `X` の要素ごとに、結果のすべての要素が正の値になるように負の値が正の値に変換されます。<br /><br /> **入力:**<br /><br /> `X`: `float`、`float2`、`float3`、または `float4`<br /> 絶対値を決定する値。<br /><br /> `Output:`<br /><br /> `Output`: 入力 `X` と同じ<br /> 要素ごとの絶対値。|なし|
|**[追加]**|指定された入力の要素ごとの合計を計算します。<br /><br /> 結果の要素ごとに、入力 `X` と入力 `Y` の対応する要素が合計されます。<br /><br /> **入力:**<br /><br /> `X`: `float`、`float2`、`float3`、または `float4`<br /> 合計する値のいずれか。<br /><br /> `Y`: 入力 `X` と同じ<br /> 合計する値のいずれか。<br /><br /> **出力:**<br /><br /> `Output`: 入力 `X` と同じ<br /> 要素ごとの合計。|なし|
|**Ceil**|指定された入力の要素ごとの切り上げを計算します。<br /><br /> 各値は、その値以上の最も近い整数に切り上げられます。<br /><br /> **入力:**<br /><br /> `X`: `float`、`float2`、`float3`、または `float4`<br /> 切り上げを計算する値。<br /><br /> **出力:**<br /><br /> `Output`: 入力 `X` と同じ<br /> 要素ごとの切り上げ。|なし|
|**Clamp**|指定された入力の各要素を定義済みの範囲にクランプします。<br /><br /> 結果の要素ごとに、定義済みの範囲に満たない値が範囲内の最小値に変更され、定義済みの範囲を超える値が範囲内の最大値に変更されます。範囲内の値は変更されません。<br /><br /> **入力:**<br /><br /> `X`: `float`、`float2`、`float3`、または `float4`<br /> クランプする値。<br /><br /> **出力:**<br /><br /> `Output`: 入力 `X` と同じ<br /> 要素ごとのクランプされた値。|**最大**<br /> 範囲内の最大有効値。<br /><br /> **最小**<br /> 範囲内の最小有効値。|
|**Cos**|指定された入力の要素ごとのコサイン (ラジアン) を計算します。<br /><br /> 結果の要素ごとに、対応する要素のコサイン (ラジアン) が計算されます。 結果の要素の値の範囲は [-1, 1] です。<br /><br /> **入力:**<br /><br /> `X`: `float`、`float2`、`float3`、または `float4`<br /> コサイン (ラジアン) を計算する値。<br /><br /> **出力:**<br /><br /> `Output`: 入力 `X` と同じ<br /> 要素ごとのコサイン。|なし|
|**Cross**|指定された 3 要素のベクターのクロス積を計算します。<br /><br /> クロス積を使用して、2 つのベクターで定義される表面の法線を計算できます。<br /><br /> **入力:**<br /><br /> `X`: `float3`<br /> クロス積の左側のベクター。<br /><br /> `Y`: `float3`<br /> クロス積の右側のベクター。<br /><br /> **出力:**<br /><br /> `Output`: `float3`<br /> クロス積。|なし|
|**Distance**|指定したポイント間の距離を計算します。<br /><br /> 正のスカラー値が返されます。<br /><br /> **入力:**<br /><br /> `X`: `float`、`float2`、`float3`、または `float4`<br /> 相互間の距離を特定するポイントのいずれか。<br /><br /> `Y`: 入力 `X` と同じ<br /> 相互間の距離を特定するポイントのいずれか。<br /><br /> **出力:**<br /><br /> `Output`: 入力 `X` と同じ<br /> 距離。|なし|
|**Divide**|指定された入力の要素ごとの商を計算します。<br /><br /> 結果の要素ごとに、入力 `X` の対応する要素が入力 `Y` の対応する要素で除算されます。<br /><br /> **入力:**<br /><br /> `X`: `float`、`float2`、`float3`、または `float4`<br /> 除算される値。<br /><br /> `Y`: 入力 `X` と同じ<br /> 除数の値。<br /><br /> **出力:**<br /><br /> `Output`: 入力 `X` と同じ<br /> 要素ごとの商。|なし|
|**Dot**|指定されたベクターのドット積を計算します。<br /><br /> スカラー値が返されます。 ドット積を使用して、2 つのベクター間の角度を特定できます。<br /><br /> **入力:**<br /><br /> `X`: `float`、`float2`、`float3`、または `float4`<br /> 項のいずれか。<br /><br /> `Y`: 入力 `X` と同じ<br /> 項のいずれか。<br /><br /> **出力:**<br /><br /> `Output`: `float`<br /> ドット積。|なし|
|**Floor**|指定された入力の要素ごとの切り下げを計算します。<br /><br /> 結果の要素ごとに、入力の対応する要素以下の最も近い整数に値が切り下げられます。 結果のすべての要素が整数になります。<br /><br /> **入力:**<br /><br /> `X`: `float`、`float2`、`float3`、または `float4`<br /> 切り下げを計算する値。<br /><br /> **出力:**<br /><br /> `Output`: 入力 `X` と同じ<br /> 要素ごとの切り下げ。|なし|
|**Fmod**|指定された入力の要素ごとの剰余を計算します。<br /><br /> 結果の要素ごとに、入力 `Y` の対応する要素の整数倍の値 m が入力 `X` の対応する要素から除算され、その剰余が返されます。 倍数 m には、剰余が入力 `Y` の対応する要素より小さくなり、符号が入力 `X` の対応する要素と同じになる値が選択されます。 たとえば、fmod(-3.14, 1.5) は -0.14 を返します。<br /><br /> **入力:**<br /><br /> `X`: `float`、`float2`、`float3`、または `float4`<br /> 除算される値。<br /><br /> `Y`: 入力 `X` と同じ<br /> 除数の値。<br /><br /> **出力:**<br /><br /> `Output`: 入力 `X` と同じ<br /> 要素ごとの剰余。|なし|
|**Frac**|指定された入力の要素ごとの整数部分を削除します。<br /><br /> 結果の要素ごとに、入力の対応する要素の整数部分が削除されます。小数部分と符号は変更されません。 この小数値の範囲は [0, 1) です。 たとえば、値 -3.14 は値 -0.14 になります。<br /><br /> **入力:**<br /><br /> `X`: `float`、`float2`、`float3`、または `float4`<br /> 小数部分を計算する値。<br /><br /> **出力:**<br /><br /> `Output`: 入力 `X` と同じ<br /> 要素ごとの小数部分。|なし|
|**Lerp**|線形補間。 指定された入力の要素ごとの加重平均を計算します。<br /><br /> 結果の要素ごとの、入力 `X` と入力 `Y` の対応する要素の加重平均。 重みは `Percent` (スカラー) で指定され、すべての要素に均一に適用されます。 この演算を使用して、ポイント、色、属性などの値を補間できます。<br /><br /> **入力:**<br /><br /> `X`: `float`、`float2`、`float3`、または `float4`<br /> 開始値。 `Percent` がゼロの場合、結果は入力と同じです。<br /><br /> `Y`: 入力 `X` と同じ<br /> 終了値。 `Percent` が 1 の場合、結果は入力と同じです。<br /><br /> `Percent`: `float`<br /> 入力 `X` から入力 `Y` までの距離に対する割合として表されるスカラーの重み。<br /><br /> **出力:**<br /><br /> `Output`: 入力 `X` と同じ<br /> 指定された入力に対して共線的である値。|なし|
|**Multiply Add**|指定された入力の要素ごとの積和演算を実行します。<br /><br /> 結果の要素ごとに、入力 `M` と入力 `A` の対応する要素の積が、入力 `B` の対応する要素に加算されます。 この演算は、直線のポイントとスロープの数式や、スケールの後にバイアスを適用する数式など、一般的な数式で使用されます。<br /><br /> **入力:**<br /><br /> `M`: `float`、`float2`、`float3`、または `float4`<br /> 積和演算する値のいずれか。<br /><br /> `A`: 入力 `M` と同じ<br /> 積和演算する値のいずれか。<br /><br /> `B`: 入力 `M` と同じ<br /> 他の 2 つの入力の積に加算する値。<br /><br /> **出力:**<br /><br /> `Output`: 入力 `M` と同じ<br /> 要素ごとの積和演算の結果。|なし|
|**Max**|指定された入力の要素ごとの最大値を計算します。<br /><br /> 結果の要素ごとに、入力の対応する要素の大きい方の値が取得されます。<br /><br /> **入力:**<br /><br /> `X`: `float`、`float2`、`float3`、または `float4`<br /> 最大値を計算する値のいずれか。<br /><br /> `Y`: 入力 `X` と同じ<br /> 最大値を計算する値のいずれか。<br /><br /> **出力:**<br /><br /> `Output`: 入力 `X` と同じ<br /> 要素ごとの最大値。|なし|
|**Min**|指定された入力の要素ごとの最小値を計算します。<br /><br /> 結果の要素ごとに、入力の対応する要素の小さい方の値が取得されます。<br /><br /> **入力:**<br /><br /> `X`: `float`、`float2`、`float3`、または `float4`<br /> 最小値を計算する値のいずれか。<br /><br /> `Y`: 入力 `X` と同じ<br /> 最小値を計算する値のいずれか。<br /><br /> **出力:**<br /><br /> `Output`: 入力 `X` と同じ<br /> 要素ごとの最小値。|なし|
|**Multiply**|指定された入力の要素ごとの積を計算します。<br /><br /> 結果の要素ごとに、入力 `X` と入力 `Y` の対応する要素が乗算されます。<br /><br /> **入力:**<br /><br /> `X`: `float`、`float2`、`float3`、または `float4`<br /> 積和演算する値のいずれか。<br /><br /> `Y`: 入力 `X` と同じ<br /> 積和演算する値のいずれか。<br /><br /> **出力:**<br /><br /> `Output`: 入力 `X` と同じ<br /> 要素ごとの積。|なし|
|**Normalize**|指定されたベクターを正規化します。<br /><br /> 正規化されたベクターは、元のベクターの向きを保持しますが、大きさは保持しません。 正規化されたベクターを使用すると、ベクターの大きさは重要でない場合の計算が簡単になります。<br /><br /> **入力:**<br /><br /> `X`: `float2`、`float3`、または `float4`<br /> 正規化するベクトル。<br /><br /> **出力:**<br /><br /> `Output`: 入力 `X` と同じ<br /> 正規化後のベクトル。|なし|
|**One Minus**|1 と指定された入力の差を要素ごとに計算します。<br /><br /> 結果の要素ごとに、入力の対応する要素が 1 から減算されます。<br /><br /> **入力:**<br /><br /> `X`: `float`、`float2`、`float3`、または `float4`<br /> 1 から減算される値。<br /><br /> **出力:**<br /><br /> `Output`: 入力 `X` と同じ<br /> 1 と指定された入力との、要素ごとの差。|なし|
|**Power**|指定された入力の要素ごとの指数演算 (累乗近似) を実行します。<br /><br /> 結果の要素ごとに、入力 `X` の対応する要素が入力 `Y` の対応する要素で累乗されます。<br /><br /> **入力:**<br /><br /> `X`: `float`、`float2`、`float3`、または `float4`<br /> 底の値。<br /><br /> `Y`: 入力 `X` と同じ<br /> 指数の値。<br /><br /> **出力:**<br /><br /> `Output`: 入力 `X` と同じ<br /> 要素ごとの指数演算。|なし|
|**Saturate**|指定された入力の各要素を [0, 1] の範囲にクランプします。<br /><br /> この範囲は、パーセンテージなどの相対単位を表すために計算で使用できます。 結果の要素ごとに、入力の対応する要素の 0 未満の値が 0 に変更され、1 を超える値が 1 に変更されます。範囲内の値は変更されません。<br /><br /> **入力:**<br /><br /> `X`: `float`、`float2`、`float3`、または `float4`<br /> 飽和させる値。<br /><br /> **出力:**<br /><br /> `Output`: 入力 `X` と同じ<br /> 要素ごとの飽和させられた値。|なし|
|**Sin**|指定された入力の要素ごとのサイン (ラジアン) を計算します。<br /><br /> 結果の要素ごとに、対応する要素のサイン (ラジアン) が計算されます。 結果の要素の値の範囲は、[-1, 1] です。<br /><br /> **入力:**<br /><br /> `X`: `float`、`float2`、`float3`、または `float4`<br /> サイン (ラジアン) を計算する値。<br /><br /> **出力:**<br /><br /> `Output`: 入力 `X` と同じ<br /> 要素ごとのサイン。|なし|
|**Sqrt**|指定された入力の要素ごとの平方根を計算します。<br /><br /> 結果の要素ごとに、対応する要素の平方根が計算されます。<br /><br /> **入力:**<br /><br /> `X`: `float`、`float2`、`float3`、または `float4`<br /> 平方根を計算する値。<br /><br /> **出力:**<br /><br /> `Output`: 入力 `X` と同じ<br /> 要素ごとの平方根。|なし|
|**Subtract**|指定された入力の要素ごとの差を計算します。<br /><br /> 結果の要素ごとに、入力 `Y` の対応する要素が入力 `X` の対応する要素から減算されます。 この演算を使用して、1 つ目の入力から 2 つ目の入力までのベクターを計算できます。<br /><br /> **入力:**<br /><br /> `X`: `float`、`float2`、`float3`、または `float4`<br /> 減算元の値。<br /><br /> `Y`: 入力 `X` と同じ<br /> 入力 `X` から減算する値。<br /><br /> **出力:**<br /><br /> `Output`: 入力 `X` と同じ<br /> 要素ごとの差。|なし|
|**Transform 3D Vector**|指定された 3D ベクターを別の空間に変換します。<br /><br /> この演算を使用すると、ポイントまたはベクターを共通の空間に移して、重要な計算の実行に使用することができます。<br /><br /> **入力:**<br /><br /> `Vector`: `float3`<br /> 変換するベクトル。<br /><br /> **出力:**<br /><br /> `Output`: `float3`<br /> 変換されたベクトル。|**システムから**<br /> ベクターのネイティブ空間です。<br /><br /> **システムへ**<br /> ベクターを変換する空間です。|