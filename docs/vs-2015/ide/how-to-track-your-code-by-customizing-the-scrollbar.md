---
title: '方法: Scrollbar のカスタマイズによるコードの追跡 |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: a9ebe7ec-4b6f-4ba2-a79e-80fab3db485b
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: da6745b3980b6ef5b0200c91d4abf245daadfa71
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "68186240"
---
# <a name="how-to-track-your-code-by-customizing-the-scrollbar"></a>方法: ScrollBar をカスタマイズしてコードを追跡する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

長いコード ファイルで作業していると、すべてを頭に入れておくことは困難です。 コード ウィンドウのスクロール バーをカスタマイズして、コード全体を見渡せるようにすることができます。  
  
### <a name="to-show-annotations-on-the-scroll-bar"></a>スクロール バーにコメントを表示するには  
  
1. コードの変更、ブレークポイント、エラー、およびブックマークを表示するようにスクロール バーを設定できます。  
  
     **スクロール バー**のオプション ページを開きます ( **[ツール]、[オプション]、[テキスト エディター]、[すべての言語]** または特定の言語を選択、または [クイック起動] ウィンドウに「**スクロール バー**」と入力)。  
  
2. **[垂直スクロール バーへのコメントの表示]** を選択し、表示するコメントを選択します ( **[マーク]** オプションには、ブレークポイントとブックマークが含まれています)。  
  
3. 試してみましょう。大きなコード ファイルを開き、ファイル内の複数の場所で出現するコードを置き換えます。 スクロール バーに置き換えた結果が表示されるため、置き換えるべきでないものを置き換えた場合は変更を取り消すことができます。  
  
     次の図は、文字列を検索した後のスクロール バーです。 文字列のすべてのインスタンスが表示されています。  
  
     ![文字列の検索後のスクロール バー。](../ide/media/enhancedscrollbarsearch.png "EnhancedScrollbarSearch")  
  
     次の図は、文字列のすべてのインスタンスを置き換えた後のスクロール バーです。 この操作で問題が発生したことがわかります。  
  
     ![文字列の置換でエラーが発生した後のスクロール バー](../ide/media/enhancedscrollbarreplace.png "EnhancedScrollbarReplace")  
  
### <a name="to-set-the-display-mode-for-the-scroll-bar"></a>スクロール バーの表示モードを設定するには  
  
1. スクロール バーには、バー モード (既定) とマップ モードの 2 つのモードがあります。 バー モードでは、コメントのインジケーターだけがスクロール バーに表示されます。 マップ モードでは、スクロール バーにコード行が表示されます。 コード行の幅を選択でき、コード行の上にポインターを置いたときに基になるコードを表示するかどうかを選択できます。 スクロール バー上のある位置をクリックすると、カーソルがコード内のその位置に移動します。 折りたたまれた部分は他と異なる影付きで表示され、ダブルクリックすると展開されます。  
  
     **スクロール バー**のオプション ページで、 **[垂直スクロール バーでのバー モードの使用]** または **[垂直スクロール バーでのマップ モードの使用]** を選択します。 **[ソースの概要]** ドロップダウンで幅を選択できます。  
  
     マップ モードが有効で、幅が [中] に設定されているときの検索例を示します。  
  
     ![マップ モードのスクロール バー](../ide/media/enhancedscrollbar.png "EnhancedScrollbar")  
  
2. マップ モードで、スクロール バーの上下にポインターを移動したときのコードのプレビューを有効にするには、 **[プレビュー ツール ヒントの表示]** オプションを選択します。 次のように表示されます。  
  
     ![ツールヒント付きのスクロール バー](../ide/media/enhancedscrollbarsearchtooltip.png "EnhancedScrollbarSearchTooltip")  
  
     マップ モードのスクロール動作とプレビュー ツール ヒントはそのままで、ソース コードの概要を表示しない場合は、 **[ソースの概要]** を **[オフ]** に設定できます。
