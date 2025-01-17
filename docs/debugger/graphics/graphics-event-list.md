﻿---
title: グラフィックス イベント一覧 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics.eventlist
ms.assetid: a1252e19-b27d-4dc7-a16b-fdac894c1f0e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 710cc8cae2b1974529be1eded6c5148eedd1211e
ms.sourcegitcommit: 283f2dbce044a18e9f6ac6398f6fc78e074ec1ed
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/16/2019
ms.locfileid: "65805313"
---
# <a name="graphics-event-list"></a>グラフィックス イベント一覧
Visual Studio Graphics Analyzer でグラフィックス イベント一覧を使用して、ゲームまたはアプリのフレームのレンダリング中に記録された Direct3D イベントを調査できます。

 イベント一覧を次に示します。

 ![名前に"Index"を持つイベントの一覧。](media/gfx_diag_demo_event_list_orientation.png "gfx_diag_demo_event_list_orientation")

## <a name="using-the-event-list"></a>イベント一覧の使用
 イベント一覧でイベントを選択すると、他のグラフィックス分析ツールで表示されている情報に反映されます。イベント一覧を他のツールと連携して使用すると、レンダリングの問題を詳しく調べて、その原因を特定することができます。 イベント一覧と他のグラフィックス分析ツールを合わせて使用し、レンダリングの問題を解決するための方法については、[サンプル](graphics-diagnostics-examples.md)に関するページを参照してください。

 数千個のイベントが含まれている可能性がある複雑なフレームに対処するには、イベント一覧の機能を効果的に使用することが重要です。 イベント一覧を効果的に使用するには、最適に機能するビューを選択し、検索を使用してイベント一覧をフィルターして、リンクに従って、イベントに関連付けられている Direct3D オブジェクトの詳細を調べてから、矢印ボタンを使用して描画呼び出し間をすばやくナビゲートします。

### <a name="color-coded-events-in-direct3d-12"></a>Direct3D 12 の色分けされたイベント
 Direct3D 12 は、異なるハードウェア機能に対応する複数のキューを公開します。 Direct3D 12 の特定のグラフィックス イベントに関連付けられたキューを識別しやすくするため、イベント一覧に表示されるイベントは、Direct3D 12 アプリのキャプチャ時に処理していたキューに応じて色分けされます。

|Direct3D 12 キュー|色|
|-----------------------|-----------|
|レンダリング キュー|緑|
|計算キュー|黄|
|コピー キュー|オレンジ|

 Direct3D 11 は複数のキューを公開していないため、Direct3D 11 アプリのキャプチャ時にイベント一覧のイベントが色分けされることはありません。

### <a name="event-list-views"></a>イベント一覧ビュー
 イベント一覧は、2 つの異なるビューをサポートしています。これらのビューは、ワークフローと環境設定をサポートするためにさまざまな方法でグラフィックス イベントを体系化しています。 最初のビューは、 *GPU 作業ビュー*イベントとその関連付けられた状態を階層的に整理します。 2 つ目のビューは *タイムライン ビュー* で、これはイベントを時系列の単純なリストに体系化します。

 **GPU 作業**ビューが表示されます、キャプチャしたイベントと、階層内の状態。 階層の最上位は、描画呼び出し、クリア、現在、ビューの処理などのイベントで構成されます。 イベント一覧では、描画呼び出しを展開して、描画呼び出しが行われたタイミングでのデバイスの状態を表示できます。また、それぞれの状態をさらに展開して、値を設定したイベントを表示できます。 このレベルでは、前のフレームで特別な状態が設定されていたかどうか、または最後の描画呼び出し以降に複数回設定されていたかどうかも確認できます。

 **タイムライン**ビューには、時系列でキャプチャされた各イベントが表示されます。 イベント一覧をこのように体系化する方法は、Visual Studio の前のバージョンと同じです。

##### <a name="to-change-the-event-list-view-mode"></a>イベント一覧ビューのモードを変更するには

- **グラフィックス イベント一覧**、イベントの一覧の上のウィンドウの検索、**ビュー**ドロップダウンいずれかを選択、**タイムライン**ビューまたは**のGPUの処理**ビュー。

### <a name="filtering-events"></a>イベントのフィルタリング
 **[グラフィックス イベント一覧]** ウィンドウの右上にある [検索] ボックスを使用してイベント一覧をフィルタリングし、特定のキーワードが含まれている名前のイベントのみを検索することができます。 前の図に示されているように、「 `Vertex`」などの 1 つのキーワードを指定することも、「 `Draw;Primitive`」のようにセミコロンで区切って複数のキーワードを指定することもできます。複数のキーワードを指定すると、名前に `Draw` または `Primitive` のいずれかが含まれているイベントが該当します。 検索では、空白の有無も区別されます。たとえば、「 `VSSet` 」と「 `VS Set` 」は異なる検索であるため、検索する語には注意が必要です。

### <a name="moving-between-draw-calls"></a>描画呼び出し間の移動
 `Draw` 呼び出しを調べることは非常に重要であるため、 **[グラフィックス イベント一覧]** ウィンドウの左上にある **[次の描画呼び出しに移動します]** ボタンと **[前の描画呼び出しに移動します]** ボタンを使用して描画呼び出しを検索し、それらの間をすばやく移動することができます。

### <a name="links-to-graphics-objects"></a>グラフィックス オブジェクトへのリンク
 特定のグラフィックス イベントについて理解するために、Direct3D の現在の状態やイベントで参照されている Direct3D オブジェクトに関して追加情報が必要になることがあります。 多数のイベントがこの情報に対するリンクを提供しており、このリンクに従って詳細を調べることができます。

## <a name="kinds-of-events-and-event-markers"></a>イベントおよびイベント マーカーの種類
 イベント一覧に表示されるイベントは 4 つのカテゴリ、つまり general (一般) イベント、draw (描画) イベント、user-defined (ユーザー定義) イベント グループ、および user-defined (ユーザー定義) イベント マーカーに分類されます。 一般イベント以外のイベントは、自身が属しているカテゴリを示すアイコンと共にまとめて表示されます。

|アイコン|イベントの説明|
|----------|-----------------------|
|(アイコンなし)|一般イベント<br /> ユーザー定義イベント、ユーザー定義イベント グループ、または描画イベント以外のすべてのイベント。|
|![描画イベント アイコン](media/vsg_eventlist_icon_draw.png "vsg_eventlist_icon_draw")|描画イベント<br /> キャプチャしたフレームの間に	発生した描画イベントをマークします。|
|![ユーザー&#45;イベント マーカーのアイコンが定義されている](media/vsg_eventlist_icon_user.png "vsg_eventlist_icon_user")|ユーザー定義イベント グループ<br /> アプリケーションで定義されているとおりに、関連するイベントをグループ化します。|
|![ユーザー&#45;イベント マーカーのアイコンが定義されている](media/vsg_eventlist_icon_user.png "vsg_eventlist_icon_user")|ユーザー定義イベント マーカー<br /> アプリケーションで定義されているとおりに、特定の場所をマークします。|

## <a name="marking-user-defined-events-in-your-app"></a>アプリのユーザー定義イベントのマーク付け
 ユーザー定義イベントは、ユーザーのアプリケーションに特有のものです。 これを使用して、アプリケーション内で発生する重要なイベントを、グラフィックス イベント一覧のイベントに関連付けることができます。 たとえば、ユーザー定義イベント グループを作成して、関連するイベント (ユーザー インターフェイスをレンダリングするイベントなど) をグループまたは階層にまとめることができます。このようにすると、イベント一覧を簡単に参照したり、特定の種類のオブジェクトが描画されたときにマーカーを作成して、イベント一覧の中でグラフィックス イベントを簡単に見つけたりすることができます。

 アプリケーションでグループおよびマーカーを作成するには、Direct3D が他の Direct3D デバッギング ツールで使用できるように提供している API と同じものを使用します。 これらの API は Direct3D のバージョン間で変わることがありますが、基本的な機能は同じです。

### <a name="user-defined-events-in-direct3d-12"></a>Direct3D 12 のユーザー定義イベント
 Direct3D 12 でグループやマーカーを作成するには、このセクションで説明する API を使用します。 次の表は、コマンド キュー内のイベントをマークするか、またはコマンド一覧内のイベントをマークするかに応じて使用できる API をまとめたものです。

|API の説明|[ID3D12CommandQueue](/windows/desktop/api/d3d12/nn-d3d12-id3d12commandqueue)|[ID3D12GraphicsCommandList](/windows/desktop/api/d3d12/nn-d3d12-id3d12graphicscommandlist)|
|---------------------| - | - |
|ユーザー定義のイベントの可用性を確認する|[PIXGetStatus](/previous-versions//dn788637(v=vs.85))|[PIXGetStatus](/previous-versions//dn788637(v=vs.85))|
|イベント グループを作成する|[PIXBeginEvent](/windows/desktop/api/d3d12/nf-d3d12-id3d12commandqueue-beginevent)|[PIXBeginEvent](/windows/desktop/api/d3d12/nf-d3d12-id3d12graphicscommandlist-beginevent)|
|イベント グループを終了する|[PIXEndEvent](/windows/desktop/api/d3d12/nf-d3d12-id3d12commandqueue-endevent)|[PIXEndEvent](/windows/desktop/api/d3d12/nf-d3d12-id3d12graphicscommandlist-endevent)|
|イベント マーカーを作成する|[PIXSetMarker](/windows/desktop/api/d3d12/nf-d3d12-id3d12commandqueue-setmarker)|[PIXSetMarker](/windows/desktop/api/d3d12/nf-d3d12-id3d12graphicscommandlist-setmarker)|

### <a name="user-defined-events-in-direct3d-11-and-earlier"></a>Direct3D 11 またはそれより前のバージョンのユーザー定義イベント
 Direct3D 11 またはそれより前のバージョンでグループやマーカーを作成するには、このセクションで説明する API を使用します。 次の表は、Direct3D 11 またはそれより前のさまざまなバージョンで使用できる API をまとめたものです。

|API の説明|[ID3D11DeviceContext2](/windows/desktop/api/d3d11_2/nn-d3d11_2-id3d11devicecontext2) (Direct3D 11.2)|[ID3DUserDefinedAnnotation](http://go.microsoft.com/fwlink/p/?LinkID=250967) (Direct3D 11.1)|D3DPerf_ API ファミリー (Direct3D 11.0 以前)|
|---------------------| - | - | - |
|イベント グループを作成する|`BeginEventInt`|`BeginEvent`|`D3DPerf_BeginEvent`|
|イベント グループを終了する|`EndEventInt`|`EndEvent`|`D3DPerf_EndEvent`|
|イベント マーカーを作成する|`SetMarkerInt`|`SetMarker`|`D3DPerf_SetMarker`|

 ご利用の Direct3D のバージョンがサポートしている API のいずれかを使用することができます。たとえば、ターゲットが Direct3D 11.1 API の場合は、 `SetMarker` または `D3DPerf_SetMarker` を使用してイベント マーカーを作成できますが、 `SetMarkerInt` は Direct3D 11.2 でしか使用できないため、使用できません。また、Direct3D の複数のバージョンをサポートしているものを同じアプリケーション内に混在させることもできます。

<!-- VERSIONLESS -->
<a name="resource-history"></a>
## <a name="resource-history"></a>リソース履歴
Visual Studio 2017 およびそれ以降を含む、**リソース履歴**ウィンドウ。  [ウォッチ] アイコンを選択する![ウォッチ アイコン](media/gfx_watch.png)内のエントリの横にある、**イベント一覧**ウィンドウが表示されます、**リソース履歴**次に示すウィンドウ。

![リソース履歴](media/gfx_diag_resource_history.png)

このウィンドウを使用すると、イベントの一覧で選択した項目の履歴を表示できます。  上部にあるドロップダウン リストには、履歴を表示するには、他の項目の選択ができます。  ウィンドウの上半分が含まれています、**フレーム セットアップ イベント**します。  これらはイベントには、*作成*カテゴリを入力し、呼び出しが通常を初期化し、リソースを作成します。  含むウィンドウの下部にある、**フレーム イベント**セクション。  これらは通常の読み取りであり、リソースの使用状況の中に発生するイベントを書き込みます。

| Column | 説明 |
|-----------| - |
| **Type** | 通常、エントリの種類を表示*作成*、*読み取り*と*書き込み*します。 |
| **表示** | その時点で、リソースのサムネイルを示しています。  その時点で、リソースの詳細ビューを開くためのサムネイルをダブルクリックします。 |
| **Event** | 発生したメソッドの呼び出しを示しています。 イベントを生成します。  [ウォッチ] アイコンを選択して、個々 のアイテムで、追加の履歴を表示できます![ウォッチ アイコン](media/gfx_watch.png)適切な行にします。  またなどの青のテキストの描画される項目`m_commandList`上記のスクリーン ショットでは、詳細については選択できます。 |

<!-- /VERSIONLESS -->

## <a name="see-also"></a>関連項目
- [チュートリアル: デバイス状態によるオブジェクトの不足](walkthrough-missing-objects-due-to-device-state.md)
