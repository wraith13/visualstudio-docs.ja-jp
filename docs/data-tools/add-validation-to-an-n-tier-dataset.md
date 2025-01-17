---
title: n 層データセットに検証を追加する
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, validating
- validation [Visual Basic], n-tier data applications
- validating n-tier data applications
ms.assetid: 34ce4db6-09bb-4b46-b435-b2514aac52d3
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: abdc719a7884e331b93313122631972cc0cfa42a
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2019
ms.locfileid: "68925683"
---
# <a name="add-validation-to-an-n-tier-dataset"></a>n 層データセットに検証を追加する
n 層ソリューションに分離されたデータセットへの検証の追加は、単一ファイルのデータセット (1 つのプロジェクト内のデータセット) に検証を追加するのと基本的には同じです。 データで検証を実行する位置として推奨されるのは、データ テーブルの <xref:System.Data.DataTable.ColumnChanging> イベントや <xref:System.Data.DataTable.RowChanging> イベントの発生時です。

データセットは、データセット内のデータテーブルの列および行に変化するイベントにユーザーコードを追加できる部分クラスを作成するための機能を提供します。 N 層ソリューションのデータセットにコードを追加する方法の詳細については、「 [n 層アプリケーションのデータセットにコードを追加する](../data-tools/add-code-to-datasets-in-n-tier-applications.md)」および「 [n 層アプリケーションの tableadapter にコードを追加](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)する」を参照してください。 部分クラスの詳細については[、「方法:クラスを部分クラス (クラスデザイナー)](../ide/class-designer/how-to-split-a-class-into-partial-classes.md)または部分クラス[とメソッド](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)に分割します。

> [!NOTE]
> データセットを Tableadapter から分離する ( **DataSet プロジェクト**プロパティを設定する) と、プロジェクト内の既存の部分データセットクラスは自動的には移動されません。 既存の部分データセットクラスは、データセットプロジェクトに手動で移動する必要があります。

> [!NOTE]
> C# では、<xref:System.Data.DataTable.ColumnChanging> イベントおよび <xref:System.Data.DataTable.RowChanging> イベントのイベント ハンドラーはデータセット デザイナーにより自動作成されません。 イベントハンドラーを手動で作成し、基になるイベントにイベントハンドラーをフックする必要があります。 次の手順では、Visual Basic とC#の両方で必要なイベントハンドラーを作成する方法について説明します。

## <a name="validate-changes-to-individual-columns"></a>個々の列に対する変更を検証する
個々の列の値は、<xref:System.Data.DataTable.ColumnChanging> イベントを処理することにより検証します。 イベント<xref:System.Data.DataTable.ColumnChanging>は、列の値が変更されたときに発生します。 データセットデザイナーの目的の列を<xref:System.Data.DataTable.ColumnChanging>ダブルクリックして、イベントのイベントハンドラーを作成します。

最初に列をダブルクリックすると、デザイナーにより <xref:System.Data.DataTable.ColumnChanging> イベントのイベント ハンドラーが生成されます。 特定の列をテストするステートメントも作成されます。`If...Then` たとえば、Northwind Orders テーブルの **[締切日]** 列をダブルクリックすると、次のコードが生成されます。

```vb
Private Sub OrdersDataTable_ColumnChanging(ByVal sender As System.Object, ByVal e As System.Data.DataColumnChangeEventArgs) Handles Me.ColumnChanging
    If (e.Column.ColumnName = Me.RequiredDateColumn.ColumnName) Then
        ' Add validation code here.
    End If
End Sub
```

> [!NOTE]
> C# プロジェクトでは、データセットの部分クラスとデータセットの個々のテーブルのみがデータセット デザイナーにより作成されます。 C# では、Visual Basic と同様に <xref:System.Data.DataTable.ColumnChanging> イベントおよび <xref:System.Data.DataTable.RowChanging> イベントのイベント ハンドラーはデータセット デザイナーにより自動作成されません。 プロジェクトC#では、イベントを処理し、基になるイベントにメソッドをフックするメソッドを手動で構築する必要があります。 次の手順では、必要なイベント ハンドラーを Visual Basic と C# の両方で作成する方法について説明します。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-add-validation-during-changes-to-individual-column-values"></a>個々の列値の変更時に検証を追加するには

1. **ソリューションエクスプローラー**で *.xsd*ファイルをダブルクリックして、データセットを開きます。 詳細については、「[チュートリアル:データセットデザイナー](walkthrough-creating-a-dataset-with-the-dataset-designer.md)にデータセットを作成します。

2. 検証する列をダブルクリックします。 この操作によって <xref:System.Data.DataTable.ColumnChanging> イベント ハンドラーが作成されます。

    > [!NOTE]
    > データセット デザイナーでは、C# イベントのイベント ハンドラーは自動作成されません。 でC#イベントを処理するために必要なコードは、次のセクションに含まれています。 `SampleColumnChangingEvent`が作成され、 <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.EndInit%2A>メソッドでイベントにフックされます。

3. アプリケーションの要件を満たすデータが `e.ProposedValue` に含まれていることを検証するコードを追加します。 指定された値が受け入れられない場合、エラーがあることを表すように該当する列を設定します。

     次のコード例では、 **Quantity**列に0より大きい値が含まれていることを検証します。 **Quantity**が0以下の場合、列はエラーに設定されます。 Quantity `Else`が0よりも大きい場合、句によってエラーがクリアされます。 列変更イベント ハンドラー内のコードは、次のようになります。

    ```vb
    If (e.Column.ColumnName = Me.QuantityColumn.ColumnName) Then
        If CType(e.ProposedValue, Short) <= 0 Then
            e.Row.SetColumnError(e.Column, "Quantity must be greater than 0")
        Else
            e.Row.SetColumnError(e.Column, "")
        End If
    End If
    ```

    ```csharp
    // Add this code to the DataTable partial class.

    public override void EndInit()
    {
        base.EndInit();
        // Hook up the ColumnChanging event
        // to call the SampleColumnChangingEvent method.
        ColumnChanging += SampleColumnChangingEvent;
    }

    public void SampleColumnChangingEvent(object sender, System.Data.DataColumnChangeEventArgs e)
    {
        if (e.Column.ColumnName == QuantityColumn.ColumnName)
        {
            if ((short)e.ProposedValue <= 0)
            {
                e.Row.SetColumnError("Quantity", "Quantity must be greater than 0");
            }
            else
            {
                e.Row.SetColumnError("Quantity", "");
            }
        }
    }
    ```

## <a name="validate-changes-to-whole-rows"></a>行全体に対する変更を検証する
行全体の値は、<xref:System.Data.DataTable.RowChanging> イベントを処理することにより検証します。 <xref:System.Data.DataTable.RowChanging> イベントは、すべての列の値がコミットされたときに発生します。 ある列の値が別の列の値に依存している場合は、<xref:System.Data.DataTable.RowChanging> イベントで検証を行う必要があります。 たとえば、Northwind の Orders テーブルの OrderDate と RequiredDate について考えます。

注文が入力されると、RequiredDate が OrderDate と同じか、それより前の日付の注文が入力されていないかを検証します。 この例では、RequiredDate 列と OrderDate 列の両方を比較する必要があるため、個々の列の変更を検証しても意味がありません。

データセットデザイナーのテーブルのタイトルバー <xref:System.Data.DataTable.RowChanging>にあるテーブル名をダブルクリックして、イベントのイベントハンドラーを作成します。

#### <a name="to-add-validation-during-changes-to-whole-rows"></a>行全体の変更時に検証を追加するには

1. **ソリューションエクスプローラー**で *.xsd*ファイルをダブルクリックして、データセットを開きます。 詳細については、「[チュートリアル:データセットデザイナー](walkthrough-creating-a-dataset-with-the-dataset-designer.md)にデータセットを作成します。

2. デザイナーでデータ テーブルのタイトル バーをダブルクリックします。

     `RowChanging` イベント ハンドラーを使用して部分クラスが作成され、コード エディターが開きます。

    > [!NOTE]
    > C# プロジェクトでは、<xref:System.Data.DataTable.RowChanging> イベントのイベント ハンドラーはデータセット デザイナーにより自動作成されません。 <xref:System.Data.DataTable.RowChanging>イベントを処理し、コードを実行してから、テーブルの初期化メソッドでイベントをフックするメソッドを作成する必要があります。

3. 部分クラスの宣言内にユーザー コードを追加します。

4. 次のコードは、 <xref:System.Data.DataTable.RowChanging>イベント中に検証するユーザーコードを追加する場所を示しています。 このC#例には、イベントハンドラーメソッドを`OrdersRowChanging`イベントにフックするコードも含まれています。

    ```vb
    Partial Class OrdersDataTable
        Private Sub OrdersDataTable_OrdersRowChanging(ByVal sender As System.Object, ByVal e As OrdersRowChangeEvent) Handles Me.OrdersRowChanging
            ' Add logic to validate columns here.
            If e.Row.RequiredDate <= e.Row.OrderDate Then
                ' Set the RowError if validation fails.
                e.Row.RowError = "Required Date cannot be on or before the OrderDate"
            Else
                ' Clear the RowError when validation passes.
                e.Row.RowError = ""
            End If
        End Sub
    End Class
    ```

    ```csharp
    partial class OrdersDataTable
    {
        public override void EndInit()
        {
            base.EndInit();
            // Hook up the event to the
            // RowChangingEvent method.
            OrdersRowChanging += RowChangingEvent;
        }

        public void RowChangingEvent(object sender, OrdersRowChangeEvent e)
        {
            // Perform the validation logic.
            if (e.Row.RequiredDate <= e.Row.OrderDate)
            {
                // Set the row to an error when validation fails.
                e.Row.RowError = "Required Date cannot be on or before the OrderDate";
            }
            else
            {
                // Clear the RowError if validation passes.
                e.Row.RowError = "";
            }
        }
    }
    ```

## <a name="see-also"></a>関連項目

- [n 層データ アプリケーションの概要](../data-tools/n-tier-data-applications-overview.md)
- [チュートリアル: n 層データ アプリケーションの作成](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [データセットのデータの検証](../data-tools/validate-data-in-datasets.md)