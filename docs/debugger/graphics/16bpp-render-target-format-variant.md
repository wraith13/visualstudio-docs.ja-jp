---
title: 16 bpp レンダリング ターゲット フォーマット バリアント |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 24b22ad9-5ad0-4161-809a-9b518eb924bf
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94775b717a3095d54d3fa52e3d2a5325dc3d21c5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62896424"
---
# <a name="16-bpp-render-target-format-variant"></a>16 bpp レンダリング ターゲット フォーマット バリアント
すべてのレンダー ターゲットおよびバック バッファーに対して、ピクセル形式を DXGI_FORMAT_B5G6R5_UNORM に設定します。

## <a name="interpretation"></a>解釈
 レンダー ターゲットまたはバック バッファーは、通常、B8G8R8A8_UNORM などの 32 ビット/ピクセル (1 ピクセルあたり 32 ビット) の形式を使用します。 32 bpp 形式は、大量のメモリ帯域幅を使用できます。 B5G6R5_UNORM 形式は、32 bpp 形式の半分のサイズである 16 bpp 形式であるためには、それを使用とメモリ帯域幅が削減色の忠実性を犠牲に負荷を軽減できます。

 このバリアントによりパフォーマンスが大幅に向上する場合は、おそらくアプリケーションで使用しているメモリ帯域幅が多すぎることを示しています。 プロファイルされたフレームがある、かなりアルファブレンディングまたはアルファ ブレンドの場合に特に大幅なパフォーマンスの向上が得られます。

16 bpp レンダリング ターゲット フォーマットでは、アプリケーションに、次の条件がある場合、メモリ使用量の帯域外を軽減できます。
- 信頼性の高い色の再現は必要ありません。
- アルファ チャネルは必要ありません。
- Ofent は (これは、削減色の忠実性 縞模様の成果物に影響を受けやすい) 滑らかなグラデーションがありません。

メモリ帯域幅を減らすには、その他の方法は次のとおりです。
- アルファブレンディングまたはアルファ ブレンドの量を削減します。
- フレーム バッファーのサイズを削減します。
- テクスチャのリソースのサイズを削減します。
- テクスチャのリソースの圧縮を削減します。

これらの方法のいずれかを最適化することとイメージの品質を保持することは背反するため、通常と同じように両者のバランスを考慮する必要があります。

スワップ チェーンの一部であるアプリケーションには、16 bpp をサポートしていないバック バッファー形式 (DXGI_FORMAT_B5G6R5_UNORM) があります。 これらのスワップ チェーンを使用して作成された`D3D11CreateDeviceAndSwapChain`または`IDXGIFactory::CreateSwapChain`します。 この制限を回避するには、次の手順を実行します。
1. 使用して B5G6R5_UNORM 形式のレンダー ターゲットを作成する`CreateTexture2D`し、そのターゲットにレンダリングします。
2. ソース テクスチャとしてレンダー ターゲット フルスクリーン クアッドを描画して、スワップ チェーンのもっと上にレンダー ターゲットをコピーします。
3. スワップ チェーンで Present を呼び出します。

   この戦略では、レンダー ターゲットをスワップ チェーン バックバッファーにコピーすることによって使用されるよりも多くの帯域幅を保存、レンダリングのパフォーマンスが向上します。

   並べて表示されるレンダリング手法を使用する GPU アーキテクチャでは、16 bpp フレーム バッファーの形式を使用して大幅なパフォーマンス上の利点を確認できます。 この機能強化は、フレームバッファーのより大きい領域が各タイルのフレームのローカル バッファー キャッシュ内に収まるのでです。 タイル型のレンダリング アーキテクチャは、携帯電話機やタブレット コンピューターの GPU で使用されています。これらの市場以外で使用されることはほとんどありません。

## <a name="remarks"></a>Remarks
 レンダー ターゲット形式は、レンダー ターゲットを作成する `ID3D11Device::CreateTexture2D` への呼び出しのたびに、DXGI_FORMAT_B5G6R5_UNORM にリセットされます。 具体的には、pDesc で渡される D3D11_TEXTURE2D_DESC オブジェクトがレンダー ターゲットを記述するときに、この形式はオーバーライドされます。つまり、

- BindFlags メンバーは、D3D11_BIND_REDNER_TARGET フラグを設定します。

- BindFlags メンバーは D3D11_BIND_DEPTH_STENCIL フラグを解除します。

- Usage メンバーは D3D11_USAGE_DEFAULT に設定されます。

## <a name="restrictions-and-limitations"></a>制約と制限
 B5G6R5 形式ではアルファ チャネルを持たないため、アルファ コンテンツはこのバリアントでは保存されません。 アプリケーションのレンダリングで、レンダー ターゲットのアルファ チャネルが必要な場合、B5G6R5 形式に切り替えることはできません。

## <a name="example"></a>例
 **16 bpp Render Target Format**を使用して作成したレンダー ターゲットのバリアントを再現できる`CreateTexture2D`このようなコードを使用しています。

```cpp
D3D11_TEXTURE2D_DESC target_description;

target_description.BindFlags = D3D11_BIND_RENDER_TARGET;
target_description.Format = DXGI_FORMAT_B5G6R5_UNORM;
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);
```
