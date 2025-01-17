---
title: TableAdapter の機能を拡張 |Microsoft Docs
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
- data [Visual Studio], TableAdapters
- data [Visual Studio], extending TableAdapters
- TableAdapters, adding functionality
ms.assetid: 418249c8-c7f3-47ef-a94c-744cb6fe6aaf
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7e14acedeab457df10cc011a94f96d7202972eea
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697893"
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>TableAdapter の機能を拡張する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

TableAdapter の機能を拡張するには、TableAdapter の部分クラス ファイルにコードを追加します。  
  
 TableAdapter に変更されたときに TableAdapter を定義するコードが再生成、**データセット デザイナー**、またはウィザードが、TableAdapter の構成を変更します。 コードが、TableAdapter の再生成中に削除されないようにするには、TableAdapter の部分クラス ファイルにコードを追加します。  
  
 部分クラスは、特定のクラスを複数の物理ファイルに分割するためのコードを使用します。 詳細については、次を参照してください。[部分](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448)または[partial (型)](https://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334)します。  
  
## <a name="locate-tableadapters-in-code"></a>コード内で Tableadapter を検索します。  
 Tableadapter は設計されています中に、**データセット デザイナー**、生成された TableAdapter クラスの入れ子になったクラスでない<xref:System.Data.DataSet>します。 Tableadapter は、TableAdapter の関連付けられているデータセットの名前に基づいて、名前空間に配置されます。 たとえば、アプリケーションには、という名前のデータセットが含まれている場合`HRDataSet`、Tableadapter に配置されます、`HRDataSetTableAdapters`名前空間。 (名前付け規則がこのパターンに従います。*DatasetName* + `TableAdapters`)。  
  
 次の例では、という名前の TableAdapter`CustomersTableAdapter`のプロジェクトでは、`NorthwindDataSet`します。  
  
#### <a name="to-create-a-partial-class-for-a-tableadapter"></a>TableAdapter の部分クラスを作成するには  
  
1. 移動して、プロジェクトに新しいクラスを追加、**プロジェクト**メニュー**クラスの追加**します。  
  
2. クラスに `CustomersTableAdapterExtended` という名前を付けます。  
  
3. **[追加]** を選びます。  
  
4. 正しい名前空間と、プロジェクトの名前を部分クラスとしては、次のようにコードを置き換えます。  
  
     [!code-csharp[VbRaddataTableAdapters#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/CustomersTableAdapterExtended.cs#2)]
     [!code-vb[VbRaddataTableAdapters#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/CustomersTableAdapterExtended.vb#2)]  
  
## <a name="see-also"></a>関連項目  
 [TableAdapters を使用してデータセットを入力する](../data-tools/fill-datasets-by-using-tableadapters.md)
