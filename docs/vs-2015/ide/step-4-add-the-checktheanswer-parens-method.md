---
title: '手順 4: CheckTheAnswer() メソッドの追加 |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: c66f3831-b4a0-40bc-a109-8f46f4db35ed
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a9806bad150a5d03a942c7dfb36753f91d10536e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442574"
---
# <a name="step-4-add-the-checktheanswer-method"></a>手順 4: CheckTheAnswer() メソッドを追加する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このチュートリアルの第 4 部では、計算問題に対する解答が正しいかどうかを判断するメソッド、`CheckTheAnswer()` を記述します。 このトピックは、コーディングの基本概念に関するチュートリアル シリーズの一部です。 チュートリアルの概要については、「[チュートリアル 2:クイズの作成](../ide/tutorial-2-create-a-timed-math-quiz.md)です。  
  
> [!NOTE]
> Visual Basic を使用している場合、このメソッドは値を返すため、通常の `Function` キーワードではなく、`Sub` キーワードを使用することに注意してください。 これは単に、Sub は値を返さないため、値を返す Function を使用しているだけです。  
  
### <a name="to-verify-whether-the-answers-are-correct"></a>解答が正しいかどうかを確認するには  
  
1. `CheckTheAnswer()` メソッドを追加します。  
  
     このメソッドが呼び出されると、addend1 と addend2 の値を加算し、その結果を sum `NumericUpDown` コントロールの値と比較します。 値が等しい場合、メソッドは `true` を返します。 それ以外の場合、メソッドは `false` の値を返します。 コードは次のようになります。  
  
     [!code-csharp[VbExpressTutorial3Step4#8](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step4/cs/form1.cs#8)]
     [!code-vb[VbExpressTutorial3Step4#8](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step4/vb/form1.vb#8)]  
  
     次に、新しい `CheckTheAnswer()` メソッドを呼び出すタイマーの Tick イベント ハンドラーのメソッドのコードを更新して解答を確認します。  
  
2. 次のコードを `if else` ステートメントに追加します。  
  
     [!code-csharp[VbExpressTutorial3Step4#10](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step4/cs/form1.cs#10)]
     [!code-vb[VbExpressTutorial3Step4#10](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step4/vb/form1.vb#10)]  
  
     解答が正しい場合、`CheckTheAnswer()` は `true` を返します。 イベント ハンドラーはタイマーを停止し、クリアしたことを示すメッセージを表示し、**[Start]** ボタンが再び使用できるようになります。 それ以外の場合は、クイズが続行されます。  
  
3. プログラムを保存し、実行して、クイズを起動し、加算問題の正しい解答を提供します。  
  
    > [!NOTE]
    > 解答を入力する場合、解答を入力する前に既定値を選択するか、手動でゼロを削除する必要があります。 この動作については、このチュートリアルで後ほど修正します。  
  
     正しい解答を入力すると、メッセージ ボックスが開き、**[Start]** が使用できるようになり、タイマーが停止します。  
  
### <a name="to-continue-or-review"></a>続行または確認するには  
  
- チュートリアルの次の手順に進むには、「[手順 5:追加 NumericUpDown コントロールの Enter イベント ハンドラー](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)します。  
  
- チュートリアルの前の手順に戻るには、「[手順 3:カウント ダウン タイマーの追加](../ide/step-3-add-a-countdown-timer.md)します。
