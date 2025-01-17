---
title: 方法:ロード テストの結果リポジトリを選択する
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.dialog.connectstringmissing
- vs.test.load.dialog.databaseconnectstring
helpviewer_keywords:
- load tests, results repository
- results, load test
- load test results, repository
- Load Test Results Repository
- SQL, Load Test Results Store
ms.assetid: fa0c4dd9-612f-4a57-b8eb-458f129d9cda
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 602327d49733077e3c180c0e192027be6374afe6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62950029"
---
# <a name="how-to-select-a-load-test-results-repository"></a>方法:ロード テストの結果リポジトリを選択する

結果ストアはローカルの結果ストアに限定されていません。 多くの場合、ロード テストは複数のリモート エージェント コンピューターで実行されます。 エージェントをコントローラーと共に使用すると、単一のコンピューターを使用した場合と比較して、よりシミュレートされたロードを生成できます。 詳細については、「[テスト コントローラーとテスト エージェント](configure-test-agents-and-controllers-for-load-tests.md)」を参照してください。

エージェントまたはローカル コンピューターからのテスト結果は、ロード テストの結果ストアを作成した SQL サーバーのいずれかに保存できます。 いずれの場合も、**[テスト コントローラーの管理]** ウィンドウを使用して、ロード テストの結果を保存する場所を指定する必要があります。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="identify-a-results-store-for-load-test-data"></a>ロード テスト データの結果ストアを指定する

1. **ソリューション エクスプローラー**でロード テスト ファイルを開きます。

2. **[ロード テスト]** ツール バーで、**[テスト コントローラーの管理]** を選択します。 **[テスト コントローラーの管理]** ダイアログ ボックスが表示されます。 エージェントをリモートで使用している場合は、コントローラーを選択する必要があります。

     ![ロード テストの結果ストアの接続プロパティ](../test/media/loadtestconnectionproperties.png) ロード テストの結果ストアの接続プロパティ

3. **[ロード テストの結果ストア]** で、**(...)** をクリックし、**[接続のプロパティ]** ダイアログ ボックスを表示します。

4. **[サーバー名]** で、`LoadTest` スクリプトを実行したサーバーの名前を入力します。

    > [!TIP]
    > ロード テスト ストアにローカル コンピューターの SQL Express を使用している場合は、「\<コンピューター名>\sqlexpress (例: **MyComputer\sqlexpress**)」と入力します。

5. **[サーバーにログオンする]** で、**[Windows 認証を使用]** を選択します。 ユーザー名とパスワードを指定することもできますが、その場合は、**[パスワードの保存]** を選択する必要があります。

6. **[データベースへの接続]** で、**[データベース名の選択または入力]** を選択します。 ドロップダウン リスト ボックスの **[LoadTest]** を選択します。

7. **[OK]** をクリックします。 **[接続の確認]** を選択して接続をテストできます。

8. **[テスト コントローラーの管理]** ダイアログ ボックスの **[閉じる]** をクリックします。

## <a name="see-also"></a>関連項目

- [ロード テストの結果リポジトリ内のロード テスト結果の管理](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [テスト コントローラーとテスト エージェント](configure-test-agents-and-controllers-for-load-tests.md)