---
title: デバッグを行うときの呼び出し履歴に対するメソッドのマップ
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.progression.debugwithcodemaps
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- call stacks, code maps
- Call Stack window, mapping calls
- debugging [Visual Studio], diagramming the call stack
- call stacks, mapping
- Call Stack window, visualizing
- debugging code visually
- debugging [Visual Studio], mapping the call stack
- call stacks, visualizing
- debugging, code maps
- Call Stack window, tracing calls visually
- Call Stack window, show on code map
- debugging [Visual Studio], tracing the call stack visually
- debugging [Visual Studio], visualizing the call stack
ms.assetid: d6a72e5e-f88d-46fc-94a3-1789d34805ef
caps.latest.revision: 43
author: MikeJo5000
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b55c677f4ba241260f1ebebc024a150dcd23eb19
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432166"
---
# <a name="map-methods-on-the-call-stack-while-debugging-in-visual-studio"></a>Visual Studio でデバッグを行うときの呼び出し履歴に対するメソッドのマップ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

デバッグ中に呼び出し履歴を視覚的にトレースするためのコード マップを作成します。 コメントをマップに追加することでバグの発見に重点を置いてコードの動作を追跡できます。

 ![呼び出し履歴コード マップを使用したデバッグ](../debugger/media/debuggermap-overview.png "DebuggerMap_Overview")

 要件:

- [Visual Studio Enterprise](https://www.visualstudio.com/downloads/download-visual-studio-vs)

- デバッグできるコード (Visual C# .NET、Visual Basic .NET、C++、JavaScript、X++ など) です。

  参照トピック[ビデオ:コード マップ デバッガーの統合 (チャネル 9) で視覚的にデバッグ](http://go.microsoft.com/fwlink/?LinkId=293418)•[呼び出し履歴でマップ](#MapStack)•[コードに関するメモを作成](#MakeNotes)•[マップを更新し、[次へ] のコール スタック](#UpdateMap)•[マップに関連するコードを追加](#AddRelatedCode)•[マップを使用してバグの検索](#FindBugs)• [Q & A](#QA)

  コマンドとコード マップを使用する場合に使用できる操作の詳細については、[参照およびコード マップの再配置](../modeling/browse-and-rearrange-code-maps.md)を参照してください。

## <a name="MapStack"></a>呼び出し履歴でマップを作成する

1. デバッグを開始します。 (キーボード:**F5 キーを押して**)

2. アプリが中断モードになるか、関数にステップ イン、選択**コード マップ**します。 (キーボード:**Ctrl キーを押し** + **Shift** + **`**)

     ![呼び出し履歴のマッピングを開始するコード マップを選択](../debugger/media/debuggermap-choosecodemap.png "DebuggerMap_ChooseCodeMap")

     現在の呼び出し履歴は新しいコード マップ上にオレンジ色で表示されます。

     ![参照呼び出し履歴コード マップに](../debugger/media/debuggermap-seeundocallstack.png "DebuggerMap_SeeUndoCallStack")

     デバッグを継続している間、マップは自動的に更新されます。 参照してください[次の呼び出し履歴でマップを更新](#UpdateMap)します。

## <a name="MakeNotes"></a>コードに関するコメントを追加する
 コードの動作を追跡するためのコメントを追加します。 コメントで新しい行を追加するキーを押して**shift + return**します。

 ![呼び出し履歴コード マップにコメントを追加](../debugger/media/debuggermap-addcomment.png "DebuggerMap_AddComment")

## <a name="UpdateMap"></a>次の呼び出し履歴でマップを更新する
 アプリを次のブレークポイントまで実行するか、関数にステップ インします。 マップに新しい呼び出し履歴が追加されます。

 ![[次へ] のコール スタックで更新プログラムのコード マップ](../debugger/media/debuggermap-addclearcallstack.png "DebuggerMap_AddClearCallStack")

## <a name="AddRelatedCode"></a>関連するコードをマップに追加する
 マップを作成できたところで、次の作業に進みます。 Visual C# .NET または Visual Basic .NET で作業している場合は、フィールド、プロパティ、およびその他のメソッドなどの項目を追加して、コードの動作を追跡します。

 メソッドのコード定義を表示するには、そのメソッドをダブルクリックするか、そのメソッドのショートカット メニューを使用します。 (キーボード:マップとキーを押してでメソッドを選択**F12**)

 ![コード マップ上のメソッドのコード定義に移動して](../debugger/media/debuggermap-gotocodedefinition.png "DebuggerMap_GoToCodeDefinition")

 マップで追跡する項目を追加します。

 ![呼び出し履歴コード マップ上のメソッドでフィールドを表示する](../debugger/media/debuggermap-showfields.png "DebuggerMap_ShowFields")

> [!NOTE]
> 既定では、マップに項目を追加すると、クラス、名前空間、アセンブリなどの親グループのノードも追加されます。 便利ですが、おくと、マップ単純な機能を使用してこの機能をオフに、**親を含める**マップのツールバー、またはキーを押してボタン**CTRL**項目を追加するとします。

 ![呼び出し履歴コード マップのメソッドに関連するフィールドを](../debugger/media/debuggermap-showedfields.png "DebuggerMap_ShowedFields")

 ここでは、同じフィールドを使用するメソッドを簡単に表示できます。 追加された最新の項目は緑色で表示されます。

 コードのさらに多くの項目を表示するには、マップの作成を続けます。

 ![フィールドを使用するメソッドを参照してください呼び出し履歴コード マップ](../debugger/media/debuggermap-findallreferences.png "DebuggerMap_FindAllReferences。")

 ![呼び出し履歴コード マップ上のフィールドを使用するメソッド](../debugger/media/debuggermap-foundallreferences.png "DebuggerMap_FoundAllReferences")

## <a name="FindBugs"></a>マップを使用してバグを見つける
 コードの視覚化はバグをよりすばやく見つけるために役立ちます。 たとえば、描画プログラムのバグを調査しているとします。 直線を描画して元に戻そうとしても、別の直線を描画するまで何も起こりません。

 そのため、`clear`、`undo`、および `Repaint` メソッドにブレークポイントを設定し、デバッグを開始して、次のようなマップを作成します。

 ![別の呼び出し履歴コード マップを追加](../debugger/media/debuggermap-addpaintobjectcallstack.png "DebuggerMap_AddPaintObjectCallStack")

 マップ上のすべてのユーザー ジェスチャーが、`Repaint` を除いて、`undo` を呼び出していることがわかります。 この動作が原因で `undo` がすぐに実行されない可能性があります。

 バグを修正してプログラムの実行を続けると、マップに `undo` から `Repaint` への新しい呼び出しが追加されます。

 ![コード マップに新しいメソッドの呼び出しごとにスタックに追加](../debugger/media/debuggermap-addnewcallforrepaint.png "DebuggerMap_AddNewCallForRepaint")

## <a name="QA"></a> Q & A

- **すべての呼び出しは、マップに表示されます。その理由を教えてください。**

   既定では、ユーザー自身のコードだけがマップに表示されます。 外部コードを表示するで有効にする、**呼び出し履歴**ウィンドウ。

   ![呼び出し履歴 ウィンドウを使用して外部コードの表示](../debugger/media/debuggermap-callstackmenu.png "DebuggerMap_CallStackMenu")

   オフにするか**マイ コードのみを有効にする**Visual studio のデバッグ オプション。

   ![[オプション] ダイアログを使用して外部コードの表示](../debugger/media/debuggermap-debugoptions.png "DebuggerMap_DebugOptions")

- **マップを変更するコードに影響しますか。**

   マップを変更してもコードは何も影響を受けません。 マップでの名前変更、移動、削除は自由に行うことができます。

- **このメッセージは何を意味します。「ダイアグラムは以前のバージョンのコードでベース可能性がありますか。」**

   マップを最後に更新してからコードが変更されている可能性があります。 たとえば、マップ上の呼び出しがコードに存在しなくなった可能性があります。 メッセージを閉じてから、マップを再び更新する前にソリューションをリビルドしてみます。

- **マップのレイアウトを制御する方法は?**

   開く、**レイアウト**マップのツールバー メニュー。

  - 既定のレイアウトを変更します。

  - オフにする、マップを自動的に再配置を停止する**デバッグ時に自動レイアウト**します。

  - 項目を追加するときに、できるだけ少なくのマップを再配置、オフにする。**インクリメンタル レイアウト**します。

- **マップを他のユーザーと共有できますか。**

   マップをエクスポートし、Microsoft Outlook があれば、他のユーザーに送信できます。または、マップを独自のソリューションに保存し、Team Foundation バージョン管理にチェックインできます。

   ![他のユーザーと共有呼び出し履歴コード マップ](../debugger/media/debuggermap-sharewithothers.png "DebuggerMap_ShareWithOthers")

- **新しい呼び出し履歴を自動的に追加することから、マップを停止するにはどうすればよいですか。**

   選択![ボタン&#45;Show コール スタックは、自動的にコード マップに](../debugger/media/debuggermap-automaticupdateicon.gif "DebuggerMap_AutomaticUpdateIcon")マップのツールバー。 マップを現在の呼び出し履歴を手動で追加するには、キーを押して**Ctrl** + **Shift** + **`** します。

   マップでは引き続き、デバッグ中にマップ上の既存の呼び出し履歴が強調表示されます。

- **項目のアイコンと矢印の意味**

   項目に関する詳細を取得するには、その項目の上にマウス ポインターを移動し、アイテムのヒントを確認します。 検索することも、**凡例**に各アイコンの意味について説明します。

   ![呼び出し履歴のコード マップ上のアイコンの意味](../debugger/media/debuggermap-showlegend.png "DebuggerMap_ShowLegend")

  参照トピック[呼び出し履歴でマップ](#MapStack)•[コードに関するメモ](#MakeNotes)•[次の呼び出し履歴でマップを更新](#UpdateMap)•[マップに関連するコードを追加](#AddRelatedCode)•[バグを見つけるマップの使用](#FindBugs)

## <a name="see-also"></a>関連項目
 [ソリューション間の依存関係をマップする](../modeling/map-dependencies-across-your-solutions.md)[コード マップをアプリケーションのデバッグ](../modeling/use-code-maps-to-debug-your-applications.md)[検索潜在的な問題のコードを使用してマップ アナライザー](../modeling/find-potential-problems-using-code-map-analyzers.md) [参照およびコード マップの再配置](../modeling/browse-and-rearrange-code-maps.md)
