---
title: マーク ビュー | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.marks
helpviewer_keywords:
- profiling tools, Marks view
- profiling tools reports, Marks view
ms.assetid: b2773344-8081-4116-85a1-58f770448f6a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: badb2266e47fcbf0bb20c5fd6fd2f7f25a167997
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62830916"
---
# <a name="marks-view"></a>マーク ビュー
[マーク] ビューには、アプリケーションに挿入されたサンプリングおよび ETW イベントが表示されます。

 レポートにあらかじめ設定されている既定のマークは、プログラムの開始と終了を示します。

 自動的に生成されるマークの Windows カウンター データもこのビューに表示されます。 詳細については、「[方法 :Windows カウンター データを収集する](../profiling/how-to-collect-windows-counter-data.md)」を参照してください。

 2 つのマークに対してフィルターを作成するには、マークを選択し、右クリックして、**[マークにフィルターを追加]** または **[タイムスタンプにフィルターを追加]** をクリックします。

 次の表に、[マーク] ビューで使用できる列の定義を示します。

 **マーク ID**: プロファイリング マークの一意識別子です。

 **マーク名**: イベントの名前です。

 **タイムスタンプ**: プロファイリングを開始してからイベントが記録されるまでの時間です。

 Windows パフォーマンス カウンター データ: Windows パフォーマンス カウンター データが収集される場合は、その値がカウンターの名前の付いた列に表示されます。

## <a name="see-also"></a>関連項目
- [パフォーマンス レポートの概要](../profiling/performance-report-overview.md)
- [方法: Windows カウンター データを収集する](../profiling/how-to-collect-windows-counter-data.md)
- [&#91;NIB&#93; [データ収集コントロール] ウィンドウ](https://msdn.microsoft.com/98d740d8-459f-4605-bf04-fb17aafaaa8f)