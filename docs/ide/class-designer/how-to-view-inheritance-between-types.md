---
title: '方法: 型の間の継承を表示する (クラス デザイナー)'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.AssociationTypeNotFoundError
helpviewer_keywords:
- types [Visual Studio], inheritance
- types [Visual Studio], base
- types [Visual Studio], derived
ms.assetid: ea3f0ada-f53b-4fb1-9fb5-908286f5ec3e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d1a15765bff6d391afc7395be03172bf5d5fc32
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62975100"
---
# <a name="how-to-view-inheritance-between-types-in-class-designer"></a>方法: クラス デザイナーで型の間の継承を表示する

基本型とその派生型の間に継承関係がある場合は、**クラス デザイナー**のクラス ダイアグラムでそのことがわかります。 2 つの型の間に継承関係が存在しない場合に継承関係を作成するときは、[方法:型間の継承の作成](how-to-create-inheritance-between-types.md)に関するページを参照してください。

## <a name="to-find-the-base-type"></a>基本型を特定するには

1. クラス ダイアグラムで、基底クラスまたは基本インターフェイスを表示する型をクリックします。

2. **[クラス ダイアグラム]** メニューで、**[基底クラスの表示]** または **[基底インターフェイスの表示]** を選択します。

     該当する型の基底クラスまたは基本インターフェイスがダイアグラムに表示され、選択されます。 2 つの図形間に非表示の継承線がある場合、それも表示されます。

また、基本型を表示する型を右クリックして、**[基底クラスの表示]** または **[基底インターフェイスの表示]** を選択することもできます。

## <a name="to-find-the-derived-types"></a>派生型を特定するには

1. クラス ダイアグラムで、派生クラスまたは派生インターフェイスを表示する型をクリックします。

2. **[クラス ダイアグラム]** メニューで、**[派生クラスの表示]** または **[派生インターフェイスの表示]** を選択します。

     該当する型の派生クラスまたは派生インターフェイスがダイアグラムに表示されます。 図形間に非表示の継承線がある場合、それも表示されます。

また、派生型を表示する型を右クリックして、**[派生クラスの表示]** または **[派生インターフェイスの表示]** を選択することもできます。

## <a name="see-also"></a>関連項目

- [方法: 型の間の関連付けを作成する](how-to-create-associations-between-types.md)
- [型およびリレーションシップの表示](designing-and-viewing-classes-and-types.md)