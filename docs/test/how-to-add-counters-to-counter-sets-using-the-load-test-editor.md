---
title: ロード テスト用のカウンター セットにカウンターを追加する
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- counters, counter sets
- counter sets
- load tests, counter sets
ms.assetid: e17d0e71-f982-4fc1-a2df-a1065d37473d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 004eff423874a07e2b49713eaed16eb1bf8be609
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979453"
---
# <a name="how-to-add-counters-to-counter-sets-using-the-load-test-editor"></a>方法: ロード テスト エディターを使用してカウンターをカウンター セットに追加する

**ロード テスト ウィザード**を使用してロード テストを作成する場合、初期のカウンター セットを追加します。 これらによって、定義済みのカウンター セットがロード テスト用に提供されます。 詳しくは、「[ロード テストでのコンピューターのカウンター セットとしきい値規則を指定する](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)」をご覧ください。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> ロード テストを複数のリモート コンピューターに分散する場合、コントローラーとエージェント カウンターが、コントローラーとエージェント カウンター セットに割り当てられます。 ロード テストでリモート コンピューターを使用する方法の詳細については、「[テスト コントローラーとテスト エージェント](configure-test-agents-and-controllers-for-load-tests.md)」を参照してください。

カウンターは、**ロード テスト エディター**で管理します。 テストに既に追加されているカウンター セットは、ロード テストの **[カウンター セット]** ノードに表示されます。 ロード テストを作成すると、既存のカウンター セットに新しいカウンターを追加できます。

## <a name="to-add-counters-to-a-counter-set"></a>カウンターをカウンター セットに追加するには

1. ロード テストを開きます。

2. **[カウンター セット]** ノードを展開します。 ロード テストに追加されているすべてのカウンター セットが表示されます。

    > [!NOTE]
    > ロード テスト階層ツリーには、**[実行設定]** ノードもあります。 このノードには、すべてのコンピューターとそれらに割り当てられているカウンター セットを示す **[カウンター セットの割り当て]** ノードが含まれています。

3. 既存のカウンター セットを右クリックし、**[カウンターの追加]** を選択します。

     **[パフォーマンス カウンターの選択]** ダイアログ ボックスが表示されます。

4. **[コンピューター]** ドロップダウン コンボ ボックスに、マップ先のコンピューター名を入力します。 または、ドロップダウン リストからいずれかのコンピューターを選択します。

    > [!NOTE]
    > カウンター セットは、パフォーマンス データの収集前にコンピューターにマップする必要があるため、パフォーマンス データを収集するコンピューターを指定する必要があります。

5. **[パフォーマンス カテゴリ]** を選択して、パフォーマンス データ カウンターのカテゴリを絞り込みます。 2 つのデータの列が表示されるので、そこからパフォーマンス カウンターを選択します。

    > [!NOTE]
    > カウンター カテゴリによっては、インスタンスの選択も必要になります。 たとえば、SQL カウンターを選択した場合は、ターゲット コンピューターに SQL インスタンスが複数インストールされている可能性があるので、SQL インスタンスを選択する必要があります。

6. カスタム カウンター セットに追加するカウンターおよびインスタンスを選択します。

     \- または

     使用できるカウンターをすべて選択する場合は、**[すべてのカウンター]** オプション ボタンをクリックします。

7. **[OK]** をクリックします。

    > [!NOTE]
    > カウンターをカウンター セットに追加することもできます。追加するには、既存のカウンターまたはカウンター カテゴリを選択し、[コピー] を選択して、他のカウンター セット ノードに貼り付けます。 コピーされたカウンターで不要になったものは削除できます。

## <a name="see-also"></a>関連項目

- [ロード テストでのコンピューターのカウンター セットとしきい値規則の指定](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [ロード テストの実行設定の構成](../test/configure-load-test-run-settings.md)