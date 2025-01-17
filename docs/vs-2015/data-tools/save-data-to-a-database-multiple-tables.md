---
title: データをデータベースに保存 (複数テーブル) |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- updating datasets, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], updating
ms.assetid: 7ebe03da-ce8c-4cbc-bac0-a2fde4ae4d07
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 132aa0f37cc63e6afe2eff61a6d0f6dec5b200b5
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65692446"
---
# <a name="save-data-to-a-database-multiple-tables"></a>データベースへのデータの保存 (複数テーブル)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

アプリケーション開発における最も一般的なシナリオの 1 つに、Windows アプリケーションのフォームにデータを表示して編集し、更新したデータをデータベースに返送する操作があります。 このチュートリアルでは、2 つの関連するテーブルのデータを表示するフォームを作成し、レコードを編集して変更内容をデータベースに保存する方法を示します。 この例では、Northwind サンプル データベースの `Customers` テーブルと `Orders` テーブルを使用します。  
  
 アプリケーション内のデータをデータベースに保存するには、TableAdapter の `Update` メソッドを呼び出します。 テーブルをドラッグすると、**データソース**ウィンドウからフォーム、データを保存するために必要なコードには、自動的に追加されます。フォームに追加される追加のテーブルには、このコードを手動で追加が必要です。 ここでは、複数のテーブルから更新を保存するコードを追加する手順を示します。  
  
> [!NOTE]
> アクティブな設定または使用しているエディションによって、ヘルプの説明から、ダイアログ ボックスとメニュー コマンドが表示が異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「 [Visual Studio での開発設定のカスタマイズ](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
- 新しいを作成する**Windows アプリケーション**プロジェクト。  
  
- 使用してアプリケーションでのデータ ソースの構成の作成と、[データ ソース構成ウィザード](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f)します。  
  
- 内の項目のコントロールの設定、[データ ソース ウィンドウ](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)します。 詳細については、次を参照してください。[設定、データ ソース ウィンドウからドラッグするときに作成されるコントロール](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)します。  
  
- **[データ ソース]** ウィンドウからフォームに項目をドラッグして、データ バインド コントロールを作成します。  
  
- データセット内の各テーブル内のいくつかのレコードを変更します。  
  
- データセット内の更新されたデータをデータベースに返送するコードを変更します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを完了するための要件は次のとおりです。  
  
- Northwind サンプル データベースにアクセスします。
  
## <a name="create-the-windows-application"></a>Windows アプリケーションを作成します。  
 作成するには、まず、 **Windows アプリケーション**します。 この手順で、省略可能ですが、プロジェクトに名前を割り当てるが名前を付けますが、後で保存することを計画していますので。  
  
#### <a name="to-create-the-new-windows-application-project"></a>新しい Windows アプリケーション プロジェクトを作成するには  
  
1. **ファイル**] メニューの [新しいプロジェクトを作成します。  
  
2. プロジェクトに `UpdateMultipleTablesWalkthrough` という名前を付けます。  
  
3. 選択**Windows アプリケーション**、し、 **OK**します。 詳細については、次を参照してください。[クライアント アプリケーション](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68)します。  
  
     **UpdateMultipleTablesWalkthrough** プロジェクトが作成されて、**ソリューション エクスプローラー**に追加されます。  
  
## <a name="create-the-data-source"></a>データ ソースを作成します。  
 この手順では、**データ ソース構成ウィザード**を使用して、Northwind データベースからデータ ソースを作成します。 接続を作成するには、Northwind サンプル データベースへのアクセス権を持っている必要があります。
  
#### <a name="to-create-the-data-source"></a>データ ソースを作成するには  
  
1. **データ**メニューの **データ ソースの**します。  
  
2. **データソース**ウィンドウで、**新しいデータ ソースの追加**を開始する、**データ ソース構成ウィザード**します。  
  
3. **データ ソースの種類を選択**画面で、**データベース**、し、**次**します。  
  
4. **データ接続の選択**画面は、次のいずれか。  
  
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
  
#### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>[データ ソース] ウィンドウの項目にドロップ タイプを設定するには  
  
1. **データソース**ウィンドウで、展開、**顧客**ノード。  
  
2. **顧客**ノードの **詳細**のコントロールを変更するコントロール リストから、**顧客**個々 のコントロールをテーブル。 詳細については、次を参照してください。[設定、データ ソース ウィンドウからドラッグするときに作成されるコントロール](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)します。  
  
## <a name="create-the-data-bound-form"></a>データ バインド フォームを作成します。  
 **[データ ソース]** ウィンドウからフォームに項目をドラッグして、データ バインド コントロールを作成します。  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>フォームにデータ バインド コントロールを作成するには  
  
1. **[データ ソース]** ウィンドウから **Form1** にメインの **[Customers]** ノードをドラッグします。  
  
     説明のラベルが付いたデータ バインド コントロールとレコード間を移動するためのツール ストリップ (<xref:System.Windows.Forms.BindingNavigator>) がフォームに表示されます。 [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)、CustomersTableAdapter、<xref:System.Windows.Forms.BindingSource>、<xref:System.Windows.Forms.BindingNavigator> がコンポーネント トレイに表示されます。  
  
2. **[データ ソース]** ウィンドウから **Form1** に関連する **[Orders]** ノードをドラッグします。  
  
    > [!NOTE]
    > 関連する **[Orders]** ノードは **[Fax]** 列の下にあり、**[Customers]** ノードの子ノードです。  
  
     レコード間をナビゲートするための <xref:System.Windows.Forms.DataGridView> コントロールとツール ストリップ (<xref:System.Windows.Forms.BindingNavigator>) がフォームに表示されます。 OrdersTableAdapter と<xref:System.Windows.Forms.BindingSource>コンポーネント トレイに表示されます。  
  
## <a name="addcode-to-update-the-database"></a>データベースを更新する Addcode  
 **Customers** TableAdapter および **Orders** TableAdapter の `Update` メソッドを呼び出して、データベースを更新できます。 既定では、イベント ハンドラーを**保存**のボタン、<xref:System.Windows.Forms.BindingNavigator>データベースに更新を送信するためのフォームのコードに追加されます。 この手順は、正しい順序で更新プログラムを送信するコードを変更します。これにより、参照整合性エラーが発生する可能性がなくなります。 また、Update 呼び出しを try-catch ブロックにラップして、エラー処理も実装します。 アプリケーションの要件に適合するようにコードを変更できます。  
  
> [!NOTE]
> わかりやすくするため、このチュートリアルでは、トランザクションは使用しません。ただし、2 つを更新する、またはその他の関連テーブルには、トランザクション内ですべての更新ロジックが含まれます。 トランザクションは、すべての変更がコミットされるまでデータベースに関連するすべての変更が成功したことを保証するプロセスです。 詳細については、次を参照してください。[トランザクションと同時実行](https://msdn.microsoft.com/library/f46570de-9e50-4fe6-8710-a8c31fa8569b)します。  
  
#### <a name="to-add-update-logic-to-the-application"></a>アプリケーションに更新ロジックを追加するには  
  
1. 選択、**保存**のボタンでは、<xref:System.Windows.Forms.BindingNavigator>します。コード エディターが開きます、`bindingNavigatorSaveItem_Click`イベント ハンドラー。  
  
2. イベント ハンドラーのコードを、関連する TableAdapter の `Update` メソッドを呼び出すコードに置き換えます。 次のコードは、最初に、各 <xref:System.Data.DataRowState> (<xref:System.Data.DataRowState>、<xref:System.Data.DataRowState>、および <xref:System.Data.DataRowState>) の更新済み情報を保持する 3 つの一時的なデータ テーブルを作成します。 更新プログラムは、正しい順序で実行されます。 コードは、次のようになります。  
  
     [!code-csharp[VbRaddataSaving#10](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form4.cs#10)]
     [!code-vb[VbRaddataSaving#10](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form4.vb#10)]  
  
## <a name="test-the-application"></a>アプリケーションをテストする  
  
#### <a name="to-test-the-application"></a>アプリケーションをテストするには  
  
1. 選択**F5**します。  
  
2. 各テーブルの 1 つ以上のレコードのデータを変更します。  
  
3. **[保存]** ボタンを選択します。  
  
4. データベースの値をチェックし、変更が保存されたことを確認します。  
  
## <a name="next-steps"></a>次の手順  
 アプリケーションの要件によっては、Windows アプリケーションでデータ バインド フォームを作成後に実行する場合があります。 このチュートリアルで行うことができる拡張には次のものがあります。  
  
- フォームに検索機能を追加します。 詳細については、「[方法 :パラメーター化クエリを Windows フォーム アプリケーションを追加する](https://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416)します。  
  
- データ ソースを編集し、データベース オブジェクトの追加または削除を行います。 詳細については、「[方法 :データセットを編集する](https://msdn.microsoft.com/library/f2dade5f-9c7a-4ddb-96a8-e0a39e50bfd3)します。  
  
## <a name="see-also"></a>関連項目  
 [データをデータベースに保存する](../data-tools/save-data-back-to-the-database.md)
