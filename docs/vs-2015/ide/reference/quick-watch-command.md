﻿---
title: QuickWatch コマンド | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.quickwatch
helpviewer_keywords:
- Quick Watch command
- Debug.Quickwatch command
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c9ac805ebea19604343d561bf553448fff2ca575
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65701744"
---
# <a name="quick-watch-command"></a>QuickWatch コマンド
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

選択または指定したテキストが [[クイック ウォッチ] ダイアログ ボックス](https://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867)の [式] フィールドに表示されます。 このダイアログ ボックスを利用し、デバッガーが認識する変数または式の現在値やレジスタのコンテンツの現在値を計算できます。 さらに、非定数の変数の値やレジストリのコンテンツの値を変更できます。  
  
## <a name="syntax"></a>構文  
  
```  
Debug.QuickWatchq [text]  
```  
  
## <a name="arguments"></a>引数  
 `text`  
 任意。 **[クイック ウォッチ]** ダイアログ ボックスに追加するテキスト。  
  
## <a name="remarks"></a>解説  
 `text` を省略した場合、カーソルで現在選択されているテキストや単語がウォッチ ウィンドウに追加されます。  
  
## <a name="example"></a>例  
  
```  
>Debug.QuickWatch  
```  
  
## <a name="see-also"></a>関連項目
 [方法: [クイック ウォッチ] ダイアログ ボックスを使用する](https://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867)   
 [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [[検索/コマンド] ボックス](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
