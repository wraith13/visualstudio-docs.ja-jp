---
title: データベースへのデータの保存 (複数テーブル)
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- updating datasets, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], updating
ms.assetid: 7ebe03da-ce8c-4cbc-bac0-a2fde4ae4d07
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 9e4a30c3aa85969a4cbf712f2f4018c24169ff6d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62565895"
---
# <a name="save-data-to-a-database-multiple-tables"></a>データベースへのデータの保存 (複数テーブル)

アプリケーション開発における最も一般的なシナリオの 1 つに、Windows アプリケーションのフォームにデータを表示して編集し、更新したデータをデータベースに返送する操作があります。 このチュートリアルでは、2 つの関連するテーブルのデータを表示するフォームを作成し、レコードを編集して変更内容をデータベースに保存する方法を示します。 この例では、Northwind サンプル データベースの `Customers` テーブルと `Orders` テーブルを使用します。

アプリケーション内のデータをデータベースに保存するには、TableAdapter の `Update` メソッドを呼び出します。 テーブルをドラッグすると、**データソース**ウィンドウからフォーム、データを保存するために必要なコードには、自動的に追加されます。 フォームに追加される追加のテーブルには、このコードを手動で追加が必要です。 ここでは、複数のテーブルから更新を保存するコードを追加する手順を示します。

このチュートリアルでは、以下のタスクを行います。

- 使用してアプリケーションでのデータ ソースの構成の作成と、[データ ソース構成ウィザード](../data-tools/media/data-source-configuration-wizard.png)します。

- 内の項目のコントロールの設定、[データ ソース ウィンドウ](add-new-data-sources.md#data-sources-window)します。 詳細については、次を参照してください。[設定、データ ソース ウィンドウからドラッグするときに作成されるコントロール](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)します。

- **[データ ソース]** ウィンドウからフォームに項目をドラッグして、データ バインド コントロールを作成します。

- データセット内の各テーブル内のいくつかのレコードを変更します。

- データセット内の更新されたデータをデータベースに返送するコードを変更します。

## <a name="prerequisites"></a>必須コンポーネント

このチュートリアルでは、SQL Server Express LocalDB と、Northwind サンプル データベースを使用します。

1. SQL Server Express LocalDB をお持ちでない場合は、インストールのいずれかから、 [SQL Server Express のダウンロード ページ](https://www.microsoft.com/sql-server/sql-server-editions-express)、または、 **Visual Studio インストーラー**します。 **Visual Studio インストーラー**の一部として SQL Server Express LocalDB をインストールすることができます、**データ ストレージと処理**ワークロード、または個々 のコンポーネントとして。

2. 次の手順に従って、Northwind サンプル データベースをインストールします。

    1. Visual Studio で開く、 **SQL Server オブジェクト エクスプ ローラー**ウィンドウ。 (SQL Server オブジェクト エクスプ ローラーがの一部としてインストールされている、**データ ストレージと処理**Visual Studio インストーラーにワークロード)。展開、 **SQL Server**ノード。 LocalDB インスタンスを右クリックし、選択**新しいクエリ**します。

       クエリ エディター ウィンドウが開きます。

    2. コピー、 [Northwind Transact SQL スクリプト](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)をクリップボードにします。 この T-SQL スクリプトでは、最初から、Northwind データベースを作成し、データを設定します。

    3. T-SQL スクリプトをクエリ エディターに貼り付けて選択し、 **Execute**ボタンをクリックします。

       しばらくすると、クエリの実行が完了し、Northwind データベースを作成します。

## <a name="create-the-windows-forms-application"></a>Windows フォーム アプリケーションを作成します。

新規作成**Windows フォーム アプリ**のいずれかのプロジェクトC#または Visual Basic です。 プロジェクトに **UpdateMultipleTablesWalkthrough** という名前を付けます。

## <a name="create-the-data-source"></a>データ ソースを作成します。

この手順では、**データ ソース構成ウィザード**を使用して、Northwind データベースからデータ ソースを作成します。 接続を作成するには、Northwind サンプル データベースへのアクセス権を持っている必要があります。 Northwind サンプル データベースの設定の詳細については、次を参照してください。[方法。サンプル データベースをインストール](../data-tools/installing-database-systems-tools-and-samples.md)します。

1. **データ**メニューの  **データ ソースの**します。

   **[データ ソース]** ウィンドウが開きます。

2. **[データ ソース]** ウィンドウで、**[新しいデータ ソースの追加]** をクリックして**データ ソース構成ウィザード**を起動します。

3. **データ ソースの種類を選択**画面で、**データベース**、し、**次**します。

4. **データ接続の選択**画面で、次のいずれかの操作を行います。

    - Northwind サンプル データベースへのデータ接続がドロップダウン リストに表示されている場合は選択します。

         - または -

    - **[新しい接続]** を選択して **[接続の追加] または [接続の変更]** ダイアログ ボックスを開きます。

5. データベースにパスワードが必要な場合は、機密データを含めるしを選択するオプションを選択**次**します。

6. **接続文字列をアプリケーション構成ファイルに保存**を選択します**次**します。

7. **データベース オブジェクトの選択**画面で、展開、**テーブル**ノード。

8. 選択、**顧客**と**注文**テーブル、および選択し**完了**します。

     自分のプロジェクトに **NorthwindDataSet** が追加され、**[データ ソース]** ウィンドウにテーブルが表示されます。

## <a name="set-the-controls-to-be-created"></a>作成されるコントロールを設定します。

このチュートリアルでのデータ、`Customers`テーブルは、**詳細**レイアウトの個々 のコントロールにデータが表示されます。 データ、`Orders`テーブルは、**グリッド**に表示されるレイアウトを<xref:System.Windows.Forms.DataGridView>コントロール。

### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>[データ ソース] ウィンドウの項目にドロップ タイプを設定するには

1. **データソース**ウィンドウで、展開、**顧客**ノード。

2. **顧客**ノードの **詳細**のコントロールを変更するコントロール リストから、**顧客**個々 のコントロールをテーブル。 詳細については、次を参照してください。[設定、データ ソース ウィンドウからドラッグするときに作成されるコントロール](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)します。

## <a name="create-the-data-bound-form"></a>データ バインド フォームを作成します。

**[データ ソース]** ウィンドウからフォームに項目をドラッグして、データ バインド コントロールを作成します。

1. **[データ ソース]** ウィンドウから **Form1** にメインの **[Customers]** ノードをドラッグします。

     説明のラベルが付いたデータ バインド コントロールとレコード間を移動するためのツール ストリップ (<xref:System.Windows.Forms.BindingNavigator>) がフォームに表示されます。 A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)、 `CustomersTableAdapter`、 <xref:System.Windows.Forms.BindingSource>、および<xref:System.Windows.Forms.BindingNavigator>コンポーネント トレイに表示されます。

2. **[データ ソース]** ウィンドウから **Form1** に関連する **[Orders]** ノードをドラッグします。

    > [!NOTE]
    > 関連する **[Orders]** ノードは **[Fax]** 列の下にあり、**[Customers]** ノードの子ノードです。

     レコード間をナビゲートするための <xref:System.Windows.Forms.DataGridView> コントロールとツール ストリップ (<xref:System.Windows.Forms.BindingNavigator>) がフォームに表示されます。 `OrdersTableAdapter`と<xref:System.Windows.Forms.BindingSource>コンポーネント トレイに表示されます。

## <a name="add-code-to-update-the-database"></a>データベースを更新するコードを追加します。

**Customers** TableAdapter および **Orders** TableAdapter の `Update` メソッドを呼び出して、データベースを更新できます。 既定では、イベント ハンドラーを**保存**のボタン、<xref:System.Windows.Forms.BindingNavigator>データベースに更新を送信するためのフォームのコードに追加されます。 この手順は、正しい順序で更新プログラムを送信するコードを変更します。これにより、参照整合性エラーが発生する可能性がなくなります。 また、Update 呼び出しを try-catch ブロックにラップして、エラー処理も実装します。 アプリケーションの要件に適合するようにコードを変更できます。

> [!NOTE]
> わかりやすくするため、このチュートリアルでは、トランザクションは使用しません。 ただし、2 つを更新する、またはその他の関連テーブルには、トランザクション内ですべての更新ロジックが含まれます。 トランザクションは、すべての変更がコミットされるまでデータベースに関連するすべての変更が成功したことを保証するプロセスです。 詳細については、次を参照してください。[トランザクションと同時実行](/dotnet/framework/data/adonet/transactions-and-concurrency)します。

### <a name="to-add-update-logic-to-the-application"></a>アプリケーションに更新ロジックを追加するには

1. 選択、**保存**のボタンでは、<xref:System.Windows.Forms.BindingNavigator>します。 コード エディターが開きます、`bindingNavigatorSaveItem_Click`イベント ハンドラー。

2. イベント ハンドラーのコードを、関連する TableAdapter の `Update` メソッドを呼び出すコードに置き換えます。 次のコードは、最初に、各 <xref:System.Data.DataRowState> (<xref:System.Data.DataRowState.Deleted>、<xref:System.Data.DataRowState.Added>、および <xref:System.Data.DataRowState.Modified>) の更新済み情報を保持する 3 つの一時的なデータ テーブルを作成します。 更新プログラムは、正しい順序で実行されます。 コードは、次のようになります。

     [!code-vb[VbRaddataSaving#10](../data-tools/codesnippet/VisualBasic/save-data-to-a-database-multiple-tables_1.vb)]
     [!code-csharp[VbRaddataSaving#10](../data-tools/codesnippet/CSharp/save-data-to-a-database-multiple-tables_1.cs)]

## <a name="test-the-application"></a>アプリケーションをテストする

1. **F5**キーを押します。

2. 各テーブルの 1 つ以上のレコードのデータを変更します。

3. **[保存]** ボタンを選択します。

4. データベースの値をチェックし、変更が保存されたことを確認します。

## <a name="see-also"></a>関連項目

- [データをデータベースに保存する](../data-tools/save-data-back-to-the-database.md)