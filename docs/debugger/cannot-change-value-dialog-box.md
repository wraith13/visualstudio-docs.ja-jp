---
title: ダイアログ ボックスの値を変更することはできません |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Cannot Change Value dialog box
- variables [debugger], editing
ms.assetid: 19e930c2-5fbf-4c83-aae8-a1dc3f8fcae8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2f8f9dafe8ada8914591426dea9abc867de2236f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62564152"
---
# <a name="cannot-change-value-dialog-box"></a>[値を変更できません] ダイアログ ボックス
## <a name="error"></a>Error
 `The value of this variable cannot be changed` &#124;`The name` *名前* `does not exist in the current context` &#124; *さまざまな他のメッセージ*

 このメッセージ ボックスが表示されるのは、デバッガー ウィンドウ ([自動変数]、[ウォッチ]、または [ローカル] の各ウィンドウ)、または [クイック ウォッチ] ダイアログ ボックスで変数の内容を不正な値に変更しようとした場合です。 たとえば、整数値を文字列に設定しようとすると、このメッセージ ボックスが表示されます。

## <a name="solution"></a>ソリューション
 デバッグ用ウィンドウや [クイック ウォッチ] ダイアログ ボックスに入力した内容が、設定する変数に対して有効な値を表していることを確認します。

## <a name="see-also"></a>関連項目

- [デバッガー内の式](../debugger/expressions-in-the-debugger.md)