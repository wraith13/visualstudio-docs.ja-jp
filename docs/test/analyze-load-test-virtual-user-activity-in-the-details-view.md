---
title: ロード テストの仮想ユーザー アクティビティの分析
ms.date: 10/03/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.activitychart
helpviewer_keywords:
- virtual user activity chart
- load test, virtual user activity chart
ms.assetid: 63f4bd42-3cfb-4eee-af68-e8334976539e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a03096e92f2a5da98da2d1850f505c65eb5b6e27
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2019
ms.locfileid: "68918618"
---
# <a name="analyzing-load-test-virtual-user-activity-in-the-details-view-of-the-load-test-analyzer"></a>ロード テスト アナライザーの詳細ビューでのロード テストの仮想ユーザー アクティビティの分析

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**仮想ユーザー アクティビティ チャート**

![仮想ユーザー アクティビティ チャート](../test/media/virtual_actchart.png)

**詳細**ビューには、ロード テスト中に各仮想ユーザーが実行していた操作を視覚的に分析するための**仮想ユーザー アクティビティ チャート**が表示されます。 **仮想ユーザー アクティビティ チャート**で、ユーザー アクティビティのパターンとロード パターンを表示して、失敗したテストや時間のかかったテストを関連付け、他の仮想ユーザー アクティビティによる要求を確認できます。 **仮想ユーザー アクティビティ チャート**は、CPU 使用率のスパイク、1 秒あたりの要求数のドロップ、スパイクとドロップの間に実行されていたテストまたはページを調べるのに役立ちます。

> [!NOTE]
> **仮想ユーザー アクティビティ詳細チャート**を使用するロード テストを実行する前に、ロード パフォーマンス テスト エディターを使用して、 **[タイミングの詳細ストレージ]** プロパティが **[AllIndividualDetails]** に設定されていることを確認する必要があります。

**[詳細の凡例] パネル**

![詳細な凡例パネル](../test/media/ltest_detailslegend.png)

**[詳細の凡例]** パネルは、仮想ユーザー アクティビティ チャートに表示されます。 [詳細の凡例] パネルを使用すると、数種類の基準に基づいてテスト、ページ、およびトランザクションを除外できます。 たとえば、ビューから特定のテストを削除したり、成功したすべてのテストを削除したりできます。特定のエラーで失敗したテストを削除することもできます。 ログがないテストをすべて削除することもできます。

失敗したテストを強調表示すると、失敗したテストがすべて赤で表示されます。 テスト ログのあるテストを強調表示することもできます。 ログのあるテストは緑で表示されます。

**[フィルター結果] パネル**

![結果パネルのフィルター処理](../test/media/ltest_filterresults.png)

[フィルター結果] パネルは、**仮想ユーザー アクティビティ チャート**に表示されます。 [フィルター結果] パネルでは、次のように結果がフィルターされます。

- **[ログのある結果のみを表示]** 関連付けられたテスト ログがあるテスト結果のみが表示されます。

- **[成功した結果の表示]** 成功した結果が表示されます。

- **[エラーのある結果の表示]** デバッグに役立つエラーのある結果が表示されます。

## <a name="tasks"></a>タスク

|タスク|関連するトピック|
|-|-|
|**ロード テストの実行:** ロード テストを作成し、仮想ユーザー アクティビティ データを収集するように構成したら、テストを実行して完了し、**仮想ユーザー アクティビティ チャート**を表示できるようにします。||
|**仮想ユーザー アクティビティ データを含むロード テスト結果の表示:** ロード テストの作成、構成、実行が完了したら、**仮想ユーザー アクティビティ チャート**を使用して仮想ユーザー アクティビティ データを表示できます。|-   [ロード テストの結果の分析](../test/analyze-load-test-results-using-the-load-test-analyzer.md)<br />-   [方法:ロード テスト中に仮想ユーザーが行っている操作を分析する](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md)|
|**ロード テスト時のパフォーマンスの問題の特定:** **仮想ユーザー アクティビティ チャート** を使用して、ロード テストにおけるパフォーマンスの問題を特定できます。|-   [チュートリアル:仮想ユーザー アクティビティ チャートを使用した問題の特定](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)|

## <a name="see-also"></a>関連項目

- [ロード テストの結果の分析](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [テーブル ビューでのロード テスト結果とエラーの分析](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)