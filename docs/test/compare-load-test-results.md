---
title: ロード テスト結果の比較
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, reporting
- load tests, results
ms.assetid: 31874114-459a-45d5-9f8b-2ea503627db8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: dcd7a3a6e3aca3320cfc016d9e3b5db4aa0991ba
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62786342"
---
# <a name="report-load-tests-results-for-test-comparisons-or-trend-analysis"></a>テストの比較または傾向分析のためにロード テストの結果レポートを作成する

複数のテスト結果に基づいて、Microsoft Excel のロード テスト レポートを生成することができます。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

次の 2 種類のロード テスト レポートを作成できます。

- 比較の実行 &mdash; このレポートは実際には 2 つのレポートに分かれており、表と横棒グラフを使用した比較データが横に並べて表示されます。

- 傾向 &mdash; 複数のレポートに基づく傾向分析を生成できます。 結果は折れ線グラフで表示されます。

どちらのレポートも、関係者とパフォーマンス データを共有し、システム全体のパフォーマンスおよび正常性が改善しているか悪化しているかを伝えるために使用できます。

レポート定義はロード テスト データベースに格納されます。 レポートが保存されるとき、レポートの定義がこのデータベースに保存され、後で再利用できます。

さらに、関係者がデータベースに接続しなくてもレポートを表示できるように、スプレッドシート ファイルを関係者と共有することができます。

> [!NOTE]
> ロード テストにコメントを追加すると、Excel レポートに表示されます。

## <a name="tasks"></a>[タスク]

|[タスク]|関連するトピック|
|-|-|
|**パフォーマンス レポートおよびストレス レポートの作成:** Microsoft Excel を使用して、ロード テストおよび Web パフォーマンス テストのレポートを作成できます。|- [方法:Microsoft Excel を使用してロード テスト パフォーマンス レポートを作成する](../test/how-to-create-load-test-performance-reports-using-microsoft-excel.md)|
|**Microsoft Word を使用したパフォーマンス レポートおよびストレス レポートの手動での作成:** Microsoft Word 文書に概要、表、グラフ データをコピーして貼り付けることによって、ロード テストおよび Web パフォーマンス テストについてのレポートを手動で作成できます。|- [方法:Microsoft Word を使用してロード テスト パフォーマンス レポートを手動で作成する](../test/how-to-manually-create-a-load-test-performance-report-using-microsoft-word.md)|

## <a name="see-also"></a>関連項目

- [ロード テストの結果の分析](../test/analyze-load-test-results-using-the-load-test-analyzer.md)