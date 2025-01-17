---
title: ロード テスト シナリオのプロパティ
ms.date: 10/19/2016
ms.topic: reference
helpviewer_keywords:
- load tests, properties
- load tests, scenarios
ms.assetid: 4414a638-1fa2-40ad-b1f4-b99f90b62e62
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 86ed8346a27a02eb7e04c1f7a9fa361b0e03431a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62785957"
---
# <a name="load-test-scenario-properties"></a>ロード テスト シナリオのプロパティ

ロード テスト要件を満たすために Visual Studio で、ロード テスト シナリオ プロパティ設定を変更します。 この記事では、さまざまなロード テスト シナリオのプロパティをカテゴリごとに一覧表示します。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="general"></a>全般

|プロパティ|定義|
|-|----------------|
|**Name**|シナリオの名前です。|

## <a name="mix"></a>ミックス

|プロパティ|定義|
|-|----------------|
|**ブラウザー ミックス**|ロード テスト用の Web ブラウザー ミックスを指定します。 さまざまな Web ブラウザーの種類とその負荷の配分を指定できます。<br /><br />省略記号ボタン **(…)** を選択し、**[ブラウザー ミックスの編集]** ダイアログを開き、**[追加]** と **[削除]** を使用してロード テストでの Web ブラウザーの種類を選択します。<br /><br />詳細については、[Web ブラウザーの種類の指定](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)に関するページを参照してください。|
|**ネットワーク ミックス**|ロード テスト用のネットワーク ミックスを指定します。 対象とするネットワークの種類とその負荷の配分を指定できます。<br /><br />省略記号ボタン **(…)** を選択し、**[ネットワーク ミックスの編集]** ダイアログ ボックスを開き、**[追加]** と **[削除]** を使用してロード テストでのネットワークの種類を選択します。<br /><br />詳細については、[仮想ネットワークの種類の指定](../test/specify-virtual-network-types-in-a-load-test-scenario.md)に関するページを参照してください。|
|**テスト ミックス**|ロード テスト用の Web パフォーマンス テストと単体テストのテスト ミックスを指定します。 対象とするテストとその負荷の配分を指定できます。<br /><br />省略記号ボタン **(…)** を選択し、**[テスト ミックスの編集]** ダイアログ ボックスを開き、**[追加]** と **[削除]** を使用してロード テストでのテストを選択します。<br /><br />詳細については、[ロード テスト シナリオのテスト ミックスの編集](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)に関するページを参照してください。|
|**テスト ミックスの種類**|ロード テストに使用するテスト ミックス モデルを指定します。<br /><br />省略記号ボタン **(…)** を選択し、**[テスト ミックスの編集]** ダイアログ ボックスを開き、**[テスト ミックス モデル]** のドロップダウンを使用してロード テストでのテスト ミックス モデルを選択します。<br /><br />詳細については、[テキスト ミックス モデルの編集](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)に関するページを参照してください。|

## <a name="options"></a>オプション

|プロパティ|定義|
|-|----------------|
|**使用するエージェント**|リモートでロード テストを実行する場合は、シナリオに使用するエージェントを指定します。 たとえば、特定のエージェントのセットを指定することで、パフォーマンスの傾向を分析する際の一貫性を維持することができます。 エージェントを地理的に分散して、実行するスクリプトとエージェントの場所の間に親和性を持たせることもできます。<br /><br />エージェントは、"**Agent1, Agent2, Agent3**" のように、コンマで区切る必要があります。 プロパティが空白の場合、シナリオでは、使用できるすべてのエージェントが使用されます。<br /><br />詳細については、「[方法 :使用するテスト エージェントを指定する](../test/how-to-specify-test-agents-to-use-in-load-test-scenarios.md)」を参照してください。|
|**遅延のペースに分布を適用**|ユーザー ペース配分のテスト ミックス モデルに一般的な分布の遅延を適用するかどうかを指定するブール値。 このプロパティは、**[テスト ミックスの種類]** プロパティが **[ユーザーのペース]** に設定されている場合にのみ適用されます。<br /><br />詳細については、「[方法 :遅延のペースに分布を適用する](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md)」を参照してください。|
|**IP 切り替え**|IP 切り替えを使用するかどうかを指定するために使用するブール値。<br /><br />IP 切り替えを使用すると、テスト エージェントで IP アドレスの範囲を使用してサーバーに要求を送信できます。 これにより、異なるクライアント コンピューターからの呼び出しをシミュレートできます。 IP 切り替えは、負荷分散されている Web ファームに対してテストする場合に重要です。 ほとんどの負荷分散機能では、クライアントと特定の Web サーバーとの間の関係を確立するのに、クライアントの IP アドレスを使用します。 すべての要求が単一のクライアントから送信されているように見える場合、負荷分散機能は負荷の分散を実行しません。 Web ファームで適切な負荷分散を得るには、要求が一定の範囲の IP アドレスから送信されることが重要です。<br /><br />IP 切り替えは、テスト エージェントでのみ使用できます。|
|**テスト イテレーションの最大数**|シナリオで実行するテストの最大数を指定するために使用する数値。 値がゼロの場合、最大数は指定されません。<br /><br />詳細については、「[ロード テスト シナリオにおけるテスト イテレーションの構成](../test/configure-test-iterations-in-a-load-test-scenario.md)」を参照してください。|
|**新しいユーザーのパーセンテージ**|新しいユーザーまたはシナリオの初めてのビジターのパーセンテージを指定する数値。<br /><br />詳細については、「[方法 :Web キャッシュ データを使用する仮想ユーザーの割合を指定する](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md)」を参照してください。|
|**待ち動作のプロファイル**|シナリオが **[記録された待ち時間を中央値とする正規分布を使用する]** を使用するかどうか、または待ち動作のプロファイルが **[オン]** か **[オフ]** かを指定します。<br /><br />詳細については、「[待ち時間を編集してロード テスト シナリオにおける Web サイトでの対話操作の遅延をシミュレートする](../test/edit-think-times-in-load-test-scenarios.md)」を参照してください。|

## <a name="timing"></a>[タイミング]

|プロパティ|定義|
|-|----------------|
|**開始時刻の遅延**|ロード テストを開始した後シナリオの開始を遅らせる時間 (時間、分、秒) を指定する時刻値。 **[ウォームアップ時に無効化]** プロパティの値が **[True]** に設定されている場合、待機時間はウォームアップ期間の終了後に適用されます。<br /><br />詳細については、「[シナリオの開始遅延の設定](../test/configure-scenario-start-delays.md)」を参照してください。|
|**ウォームアップ時に無効化**|ロード テストの実行設定で指定された **[ウォームアップ継続時間]** プロパティの時刻値の間に、シナリオを実行するかどうかを指定するために使用するブール値。<br /><br />ロード テストの実行設定プロパティの詳細については、「[ロード テストの実行設定のプロパティ](../test/load-test-run-settings-properties.md)」を参照してください。<br /><br />詳細については、「[シナリオの開始遅延の設定](../test/configure-scenario-start-delays.md)」を参照してください。|
|**テスト イテレーション間の待ち時間**|テスト イテレーション間の待ち時間を指定するために使用する数値 (秒)。<br /><br />詳細については、「[待ち時間を編集してロード テスト シナリオにおける Web サイトでの対話操作の遅延をシミュレートする](../test/edit-think-times-in-load-test-scenarios.md)」を参照してください。|

## <a name="see-also"></a>関連項目

- [ロード テスト シナリオの編集](../test/edit-load-test-scenarios.md)