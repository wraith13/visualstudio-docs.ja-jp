﻿---
title: SetCurrentThread コマンド | Microsoft ドキュメント
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.setcurrentthread
helpviewer_keywords:
- Set Current Thread command
- Debug.SetCurrentThread command
ms.assetid: 9917ed1d-6c30-4d94-b2f0-69acce74f1b2
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 107303082202cb1dbb162ef9dfb845c2f6564df4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "68163332"
---
# <a name="set-current-thread-command"></a>SetCurrentThread コマンド
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

指定したスレッドを現在のスレッドとして設定します。  
  
## <a name="syntax"></a>構文  
  
```  
Debug.SetCurrentThread index  
```  
  
## <a name="arguments"></a>引数  
 `index`  
 必須です。 スレッドをそのインデックスで選択します。  
  
## <a name="example"></a>例  
  
```  
>Debug.SetCurrentThread 1  
```  
  
## <a name="see-also"></a>関連項目
 [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [[検索/コマンド] ボックス](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
