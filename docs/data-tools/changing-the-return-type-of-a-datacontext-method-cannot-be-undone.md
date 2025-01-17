---
title: DataContext メソッドの戻り値の型を変更すると、元に戻せなくなります
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 76b161fc-5075-4192-8d94-f15b02e199e9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 7aee87e353cb3b69b70e78508c20a9a9c1ed5102
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/09/2019
ms.locfileid: "65460687"
---
# <a name="changing-the-return-type-of-a-datacontext-method-cannot-be-undone"></a>DataContext メソッドの戻り値の型を変更すると、元に戻せなくなります

DataContext メソッドの戻り値の型を変更すると、元に戻せなくなります。 自動生成された型に戻すには、項目を**サーバー エクスプローラー**または**データベース エクスプローラー**から O/R デザイナーにもう一度ドラッグする必要があります。 戻り値の型を変更してもよろしいですか?

<xref:System.Data.Linq.DataContext> メソッドの戻り値の型は、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]で項目をドロップする場所によって異なります。 既存のエンティティ クラスに項目を直接ドロップすると、そのエンティティ クラスを戻り値の型とする <xref:System.Data.Linq.DataContext> メソッドが作成されます。 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]の空の領域に項目をドロップすると、自動生成された型を返す <xref:System.Data.Linq.DataContext> メソッドが作成されます。 <xref:System.Data.Linq.DataContext> メソッドをメソッド ペインに追加した後に、その戻り値の型を変更できます。 <xref:System.Data.Linq.DataContext> メソッドの戻り値の型を確認または変更するには、**[プロパティ]** ウィンドウでそのメソッドを選択し、**[Return Type]** プロパティをクリックします。

## <a name="to-change-the-return-type-of-a-datacontext"></a>DataContext の戻り値の型を変更するには

- **[はい]** をクリックします。

## <a name="to-exit-the-message-box-and-leave-the-return-type-unchanged"></a>メッセージ ボックスを終了し、現在の戻り値の型を維持するには

- **[いいえ]** をクリックします。

## <a name="to-revert-to-the-original-return-type-after-changing-the-return-type"></a>戻り値の型を変更した後で、元の戻り値の型に戻すには

1. <xref:System.Data.Linq.DataContext> で [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] メソッドを選択し、削除します。

2. **サーバー エクスプローラー/データベース エクスプローラー**で項目を探し、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] にドラッグします。

    元の既定の戻り値の型で <xref:System.Data.Linq.DataContext> メソッドが作成されます。

## <a name="see-also"></a>関連項目

- [Visual Studio の LINQ to SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)