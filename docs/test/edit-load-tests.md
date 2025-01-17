---
title: ロード テストの編集
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Load Test Editor
- load tests, Load Test Editor
ms.assetid: ba16ed02-137e-40bf-a4cb-45d87d922d37
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 130f7296985aa5c5e6115cd3e61b00efd90f25c7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62784054"
---
# <a name="edit-load-tests"></a>ロード テストを編集する

ロード テストでは、Web のパフォーマンス テストまたは単体テストを実行し、たくさんのユーザーが 1 台のサーバーに同時にアクセスする状況をシミュレーションします。 ロード テストにより、アプリケーションのストレスおよびパフォーマンスのデータを利用できるようになります。 ロード テストは、ユーザーのロードやネットワークの種類など、さまざまなロード条件をエミュレートするように構成できます。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

ロード テストは、*シナリオ*、*カウンター セット*、*実行設定*によって定義されます。 次の図では、[シナリオ](../test/edit-load-test-scenarios.md)、[カウンター セット](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)、[実行設定](../test/load-test-run-settings-properties.md)の違いを確認できます。

![ロード テストのアーキテクチャ](../test/media/load_test_editor.png)

## <a name="software-requirements"></a>ソフトウェア要件

Web パフォーマンスとロード テスト プロジェクトは、Visual Studio Enterprise Edition でのみ利用できます。

## <a name="edit-load-test-scenario-settings"></a>ロード テスト シナリオ設定を編集する

シナリオは、ユーザー グループがサーバー アプリケーションと対話する状況をモデル化するために使用されます。 シナリオは、ロード パターン、テスト ミックス モデル、テスト ミックス、ブラウザー ミックス、およびネットワーク ミックスで構成されます。 ロード テストには複数のシナリオを指定でき、個々のシナリオには複数の Web パフォーマンス テストおよび単体テストを含めることができます。 同様の設定をグループ化することによって、シナリオでは同様の性質を持つテストを一緒にグループ化したり、実行したりできます。

詳細については、「[ロード テスト シナリオの編集](../test/edit-load-test-scenarios.md)」と「[ロード テスト シナリオのプロパティ](../test/load-test-scenario-properties.md)」を参照してください。

## <a name="configure-and-manage-performance-counter-sets"></a>パフォーマンス カウンター セットを構成し、管理する

ロード テストでは、テクノロジ単位で整理された名前付きカウンター セットが提供されます。これらのカウンター セットは、パフォーマンス カウンター データを分析する際に役立ちます。 カウンター セットには、ロード テスト、IIS、ASP.NET、SQL などがあります。 **新しいロード テスト ウィザード**でロード テストを作成すると、ロード テストに含めるように指定したコンピューターに対して、定義済みの重要なカウンターの初期セットが構成されます。 カウンターは、**ロード テスト エディター**で管理します。

詳しくは、「[ロード テストでのコンピューターのカウンター セットとしきい値規則を指定する](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)」をご覧ください。

## <a name="configure-and-manage-load-test-run-settings"></a>ロード テストの実行設定を構成し、管理する

実行設定とは、ロード テストの実行方法に影響を与えるプロパティです。 実行設定は、**[プロパティ]** ウィンドウでカテゴリ別に整理されています。

詳細については、「[ロード テストの実行設定の構成](../test/configure-load-test-run-settings.md)」と「[ロード テストの実行設定のプロパティ](../test/load-test-run-settings-properties.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [ロード テストの結果の分析](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [しきい値規則違反の分析](../test/analyze-threshold-rule-violations-in-load-tests.md)