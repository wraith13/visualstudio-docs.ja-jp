﻿---
title: '方法: クラス デザイナーを使用して型を作成する |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.Clr.ClrAttributesDialog
helpviewer_keywords:
- custom attributes, applying
- class diagrams, creating types
- classes [Visual Studio], creating with Class Designer
- Class Designer [Visual Studio], creating classes
- types [Visual Studio], class diagrams
- attributes [Visual Studio], applying custom
ms.assetid: 94458c31-28bc-40e2-9737-85868788a0e5
caps.latest.revision: 45
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3a20a9ecf08c82589fd915fdd4bd60c6144e9d1c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201824"
---
# <a name="how-to-create-types-by-using-class-designer"></a>方法: クラス デザイナーを使用して型を作成する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual C# .NET プロジェクトおよび Visual Basic .NET プロジェクトの新しい型を設計するには、これらをクラス ダイアグラム上で作成します。 既存の型を表示する場合は、「[方法:既存の型 (クラス デザイナー) を表示](../ide/how-to-view-existing-types-class-designer.md)します。  
  
- [新しい型を作成する](#CreateType)  
  
- [カスタム属性を型に適用する](#CustAttributeType)  
  
- [カスタム属性を型のメンバーに適用する](#CustAttributeMember)  
  
## <a name="CreateType"></a> 新しい型を作成する  
  
1. クラス デザイナーのツールボックスから、いずれかをクラス ダイアグラムにドラッグします。  
  
    - **[クラス]** または **[抽象クラス]**  
  
    - **Enum**  
  
    - **Interface**  
  
    - **[構造体]** (VB) または **[構造体]** (C#)  
  
    - **Delegate**  
  
    - **[モジュール]** (VB のみ)  
  
2. 型の名前を付けます。 それからアクセス レベルを選択します。  
  
3. 型の初期コードを追加するファイルを選択します。  
  
    - 新しいクラス ファイルを作成して、そのファイルを現在のプロジェクトに追加するには、 **[新しいファイルの作成]** をクリックし、ファイル名を入力します。  
  
    - 既存のファイルにコードを追加するには、 **[存在するファイルに追加]** をクリックします。  
  
         ソリューションに複数のアプリでコードを共有しているプロジェクトがある場合、対応するクラス ファイルが同じアプリ プロジェクトまたは共有プロジェクトにある場合にのみ、アプリケーション プロジェクトで新しい型をクラス ダイアグラムに追加できます。  
  
4. 次に、型を定義するために他の項目を追加します。  
  
    |||  
    |-|-|  
    |**対象**|**[追加]**|  
    |クラス、抽象クラス、構造体|型を定義するメソッド、プロパティ、フィールド、イベント、コンストラクター (メソッド)、デストラクター (メソッド)、および定数|  
    |列挙体|列挙型を構成するフィールド値|  
    |インターフェイス|インターフェイスを構成するメソッド、プロパティ、イベント|  
    |Delegate|デリゲートを定義するパラメーター|  
    |Module|モジュールを定義するメソッド、プロパティ、フィールド、イベント、コンストラクター (メソッド)、および定数|  
  
     「[メンバーの作成](../ide/creating-and-configuring-type-members-class-designer.md#CreateMembers)」をご覧ください。  
  
## <a name="CustAttributeType"></a> カスタム属性を型に適用する  
  
1. クラス ダイアグラムで型の図形をクリックします。  
  
2. [プロパティ] ウィンドウで、型の **[カスタム属性]** プロパティの横の省略記号 (...) ボタンをクリックします。  
  
3. 1 つ以上のカスタム属性を 1 行あたり 1 つ追加します。 角かっこで閉じません。  
  
     終了後、カスタム属性が型に適用されます。  
  
## <a name="CustAttributeMember"></a> カスタム属性を型のメンバーに適用する  
  
1. クラス ダイアグラムの型の図形でメンバーの名前をクリックするか、[クラスの詳細] ウィンドウでその行をクリックします。  
  
2. [プロパティ] ウィンドウで、メンバーの **[カスタム属性]** プロパティを探します。  
  
3. 1 つ以上のカスタム属性を 1 行あたり 1 つ追加します。 角かっこで閉じません。  
  
     終了後、カスタム属性が型に適用されます。  
  
## <a name="see-also"></a>関連項目
 [方法: 型 (クラス デザイナー) の間の継承を作成します。](../ide/how-to-create-inheritance-between-types-class-designer.md)   
 [方法: 型 (クラス デザイナー) の間の関連付けを作成します。](../ide/how-to-create-associations-between-types-class-designer.md)   
 [型のメンバーの作成と構成 (クラス デザイナー)](../ide/creating-and-configuring-type-members-class-designer.md)   
 [クラス ダイアグラムの使用 (クラス デザイナー)](../ide/working-with-class-diagrams-class-designer.md)   
 [クラスおよび型のデザイン (クラス デザイナー)](../ide/designing-classes-and-types-class-designer.md)
