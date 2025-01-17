---
title: データセットと TableAdapters を別々のプロジェクトに分離する
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, separating Datasets and TableAdapters
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: cb70705d29ad636329803656aeaa1a27ddf237d5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63402764"
---
# <a name="separate-datasets-and-tableadapters-into-different-projects"></a>データセットと TableAdapters を別々のプロジェクトに分離する
型指定されたデータセットが強化されているように、 [Tableadapter](create-and-configure-tableadapters.md)および個別のプロジェクトにデータセット クラスを生成することができます。 これにより、アプリケーション層を分離して、n 層データ アプリケーションをすばやく生成できるようになります。

次の手順を使用してプロセスを説明する、**データセット デザイナー**は生成された TableAdapter コードを含むプロジェクトから別のプロジェクトにデータセット コードを生成します。

## <a name="separate-datasets-and-tableadapters"></a>別のデータセットと tableadapters の分離
TableAdapter コードからデータセット コードを分離する場合は、データセット コードを含むプロジェクトを現在のソリューション内になければなりません。 このプロジェクトが現在のソリューションにない場合で使用できない、 **DataSet プロジェクト**の一覧で、**プロパティ**ウィンドウ。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-separate-the-dataset-into-a-different-project"></a>データセットを別のプロジェクトに分離するには

1. データセット (*.xsd* ファイル) を含むソリューションを開きます。

    > [!NOTE]
    > ソリューションに、データセット コードを分離するプロジェクトが含まれていない場合は、プロジェクトを作成または既存のプロジェクトをソリューションに追加します。

2. **ソリューション エクスプローラー**で型指定されたデータセット ファイル (*.xsd* ファイル) をダブルクリックして、**データセット デザイナー**でデータセットを開きます。

3. 空の領域を選択して、**データセット デザイナー**します。

4. **プロパティ**ウィンドウで、検索、 **DataSet プロジェクト**ノード。

5. **DataSet プロジェクト**一覧で、データセット コードを生成するプロジェクトの名前を選択します。

     データセット コードを生成するプロジェクトを選択した後、**データセット ファイル**プロパティには、既定のファイル名が設定されます。 必要な場合は、この名前を変更できます。 さらに、データセット コードを特定のディレクトリに生成する場合は、**[プロジェクト フォルダー]** プロパティをフォルダーの名前に設定できます。

    > [!NOTE]
    > データセットと Tableadapter を分離する場合 (設定して、 **DataSet プロジェクト**プロパティ)、プロジェクト内の既存のデータセット部分クラスが自動的に移動しません。 既存のデータセット部分クラスは、データセット プロジェクトに手動で移動する必要があります。

6. データセットを保存します。

     選択したプロジェクトにデータセット コードが生成された、 **DataSet プロジェクト**プロパティ、および**TableAdapter**現在のプロジェクトにコードが生成されます。

既定では、データセットと TableAdapter コードを分離したら、結果はプロジェクトごとに別個のクラス ファイルが。 元のプロジェクトにという名前のファイル*DatasetName.Designer.vb* (または*DatasetName.Designer.cs*) TableAdapter コードを格納しています。 指定されているプロジェクト、 **Dataset プロジェクト**プロパティという名前のファイルは、 *DatasetName.DataSet.Designer.vb* (または*DatasetName.DataSet.Designer.cs*) します。データセット コードが含まれています。

> [!NOTE]
> 生成されたクラス ファイルを表示するには、データセットまたは TableAdapter プロジェクトを選択します。 次に、**ソリューション エクスプ ローラー**、 **すべてのファイル**します。

## <a name="see-also"></a>関連項目

- [n 層データ アプリケーションの概要](../data-tools/n-tier-data-applications-overview.md)
- [チュートリアル: n 層データ アプリケーションを作成する](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [階層更新](../data-tools/hierarchical-update.md)
- [Visual Studio でのデータへのアクセス](../data-tools/accessing-data-in-visual-studio.md)
- [ADO.NET](/dotnet/framework/data/adonet/index)