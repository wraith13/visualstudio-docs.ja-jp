---
title: 型のメンバーの作成と構成 (クラス デザイナー) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdetails.method
- vs.classdetails.property
- vs.classdetails.parameter
- vs.classdetails.event
- vs.classdetails.field
helpviewer_keywords:
- Class Designer [Visual Studio], member creation
- type members, modifying in Class Designer
- parameters [ASP.NET Web Services], adding to methods
- type members, configuring
- type members
- members
- type members, creating
- members, creating
- Class Designer [Visual Studio], type members
- read-only information, displaying
- members, configuring
- methods [Visual Studio], adding parameters
- Class Details window
- Class Details window, member creation
ms.assetid: 42af8738-3738-4ca7-82ff-edf573a68f96
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 93d001af54a84bdb2cd2ec00f3e8fb80174c6436
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65701209"
---
# <a name="creating-and-configuring-type-members-class-designer"></a>型のメンバーの作成と構成 (クラス デザイナー)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

これらのメンバーをクラス ダイアグラムの型に追加して、メンバーを **[クラスの詳細]** ウィンドウで構成することができます。  
  
|**Type**|**含めることのできるメンバー**|  
|--------------|--------------------------------|  
|クラス|メソッド、プロパティ (C# と Visual Basic の場合)、フィールド、イベント (C# と Visual Basic の場合)、コンストラクター (メソッド)、デストラクター (メソッド)、定数|  
|Enum|member|  
|Interface|メソッド、プロパティ、イベント (C# と Visual Basic の場合)|  
|抽象クラス|メソッド、プロパティ (C# と Visual Basic の場合)、フィールド、イベント (C# と Visual Basic の場合)、コンストラクター (メソッド)、デストラクター (メソッド)、定数|  
|構造体 (C# の構造体)|メソッド、プロパティ (C# と Visual Basic の場合)、フィールド、イベント (C# と Visual Basic の場合)、コンストラクター (メソッド)、定数|  
|Delegate|パラメーター|  
|モジュール (VB の場合のみ)|メソッド、プロパティ、フィールド、イベント、コンストラクター、定数|  
  
> [!NOTE]
> 自動実装するプロパティを使用すると、このプロパティの get アクセサーと set アクセサーで追加のロジックが必要ない場合に、プロパティ宣言がより簡単になります (C# の場合のみ)。 完全署名を表示するには、**[クラス ダイアグラム]** メニューの **[メンバー形式の変更]** を選択し、**[完全署名の表示]** を選択します。 自動実装するプロパティの詳細については、「[自動実装するプロパティ](https://msdn.microsoft.com/library/aa55fa97-ccec-431f-b5e9-5ac789fd32b7)」を参照してください。  
  
## <a name="common-tasks"></a>よく使う機能  
  
|タスク|関連する参照先|  
|----------|------------------------|  
|**作業の開始:** 作成して、型のメンバーを構成する前に、クラスの詳細 ウィンドウを開く必要があります。|-   [[クラスの詳細] ウィンドウを開くには](../ide/creating-and-configuring-type-members-class-designer.md#OpenClassDetails)<br />-   [クラスの詳細の使用上の注意](../ide/creating-and-configuring-type-members-class-designer.md#ClassDetailsUsageNotes)<br />-   [読み取り専用の情報の表示](../ide/creating-and-configuring-type-members-class-designer.md#ReadOnlyInfo)<br />-   [クラス ダイアグラムおよびクラスの詳細情報のウィンドウでのキーボードとマウスのショートカット (クラス デザイナー)](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md)|  
|**型のメンバーの作成および変更:** 新しいメンバーを作成、メンバーの変更、およびクラスの詳細ウィンドウを使用してメソッドにパラメーターを追加することができます。|-   [メンバーの作成](../ide/creating-and-configuring-type-members-class-designer.md#CreateMembers)<br />-   [型のメンバーの変更](../ide/creating-and-configuring-type-members-class-designer.md#ModifyTypeMembers)<br />-   [メソッドへのパラメーターの追加](../ide/creating-and-configuring-type-members-class-designer.md#AddMethodParams)|  
  
## <a name="OpenClassDetails"></a> [クラスの詳細] ウィンドウを開くには  
 既定では、クラスの詳細 ウィンドウが表示されます自動的に新しいクラス ダイアグラムを開くと (を参照してください[方法。(クラス デザイナー) のプロジェクトにクラス ダイアグラムを追加する](../ide/how-to-add-class-diagrams-to-projects-class-designer.md))。 また、次の方法で明示的に開くこともできます。  
  
#### <a name="to-open-the-class-details-window"></a>[クラスの詳細] ウィンドウを開くには  
  
1. ダイアグラム内の任意のクラスを右クリックしてコンテキスト メニューを表示します。  
  
2. コンテキスト メニューの **[クラスの詳細情報]** をクリックします。  
  
   または  
  
- [表示] メニューの **[その他のウィンドウ]** をポイントし、**[クラスの詳細情報]** をクリックします。  
  
## <a name="CreateMembers"></a> メンバーの作成  
 次のいずれかのツールを使用して、メンバーを作成できます。  
  
- クラス デザイナー  
  
- [クラスの詳細] ウィンドウ ツール バー  
  
- [クラスの詳細] ウィンドウ  
  
> [!NOTE]
> このセクションの手順に従って、コンストラクターとデストラクターを作成することもできます。 コンストラクターとデストラクターは特殊なメソッドであるため、クラス ダイアグラムの図形の **[メソッド]** コンパートメントと [クラスの詳細] ウィンドウ グリッドの **[メソッド]** セクションに表示されることに注意してください。  
  
> [!NOTE]
> デリゲートに追加できるエンティティはパラメーターだけです。 「[クラスの詳細] ウィンドウ ツール バーを使用してメンバーを作成するには」の手順は、この処理には有効ではありません。  
  
#### <a name="to-create-a-member-using-class-designer"></a>クラス デザイナーを使用してメンバーを作成するには  
  
1. メンバーを追加する型を右クリックして **[追加]** をポイントし、追加するメンバーの型を選択します。  
  
     新しいメンバー シグネチャが作成され、型に追加されます。 **クラス デザイナー**、**[クラスの詳細]** ウィンドウ、または **[プロパティ]** ウィンドウで変更できる既定の名前が与えられます。  
  
2. オプションとして、型など、メンバーに関するその他の詳細を指定します。  
  
#### <a name="to-create-a-member-using-the-class-details-window-toolbar"></a>[クラスの詳細] ウィンドウ ツール バーを使用してメンバーを作成するには  
  
1. ダイアグラム領域で、メンバーを追加する型を選択します。  
  
     型がフォーカスを取得し、その内容が [クラスの詳細] ウィンドウに表示されます。  
  
2. [クラスの詳細] ウィンドウ ツール バーで、上部のアイコンをクリックし、ドロップダウン リストの **[新しい \<メンバー>]** をクリックします。  
  
     カーソルが追加するメンバーの種類の列の**名前**フィールドに移動します。 たとえば、**[新しいプロパティ]** をクリックすると、[クラスの詳細] ウィンドウの **[プロパティ]** セクションの新しい行にカーソルが移動します。  
  
3. 作成するメンバーの名前を入力し、Enter キーを押します (または、Tab キーの押下などによりフォーカスを移動します)。  
  
     新しいメンバー シグネチャが作成され、型に追加されます。 これで、メンバーのコードへの追加が完了し、**クラス デザイナー**、[クラスの詳細] ウィンドウ、および [プロパティ] ウィンドウに表示されます。  
  
4. オプションとして、型など、メンバーに関するその他の詳細を指定します。  
  
#### <a name="to-create-a-member-using-the-class-details-window"></a>[クラスの詳細] ウィンドウを使用してメンバーを作成するには  
  
1. ダイアグラム領域で、メンバーを追加する型を選択します。  
  
     型がフォーカスを取得し、その内容が [クラスの詳細] ウィンドウに表示されます。  
  
2. [クラスの詳細] ウィンドウの、追加するメンバーの種類を含むセクションで、**[\<メンバーの追加>]** をクリックします。 たとえば、フィールドを追加する場合は **[\<フィールドの追加>]** をクリックします。  
  
3. 作成するメンバーの名前を入力し、Enter キーを押します。  
  
     新しいメンバー シグネチャが作成され、型に追加されます。 これで、メンバーのコードへの追加が完了し、**クラス デザイナー**、[クラスの詳細] ウィンドウ、および [プロパティ] ウィンドウに表示されます。  
  
4. オプションとして、型など、メンバーに関するその他の詳細を指定します。  
  
     **注:** キーボード ショートカットを使用してメンバーを作成することもできます。 詳細については、「[クラス ダイアグラムおよびクラスの詳細情報のウィンドウでのキーボードとマウスのショートカット (クラス デザイナー)](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md)」を参照してください。  
  
## <a name="ModifyTypeMembers"></a> 型のメンバーの変更  
 クラス デザイナーを使用して、ダイアグラムに表示される型のメンバーを変更できます。 読み取り専用でない、クラス ダイアグラムに表示される任意の型のメンバーを変更できます。 (「[読み取り専用の情報の表示 (クラス デザイナー)](https://msdn.microsoft.com/33e2d3a9-1668-4d10-ae56-fa09b3156e0a)」を参照してください。)型のメンバーは、デザイン サーフェイス、プロパティ ウィンドウ、および [クラスの詳細] ウィンドウで埋め込み先編集を使用して変更します。  
  
 [クラスの詳細] ウィンドウに表示されるすべてのメンバーは、クラス ダイアグラムの型のメンバーを表します。 メソッド、プロパティ、フィールド、およびイベントという 4 種類のメンバーがあります。  
  
 すべてのメンバー行は、メンバーを種類別にグループ化する見出しの下に表示されます。 たとえば、すべてのプロパティは、グリッドのノードとして縮小または展開できる見出し **[プロパティ]** の下に表示されます。  
  
 各メンバー行には、次の要素が表示されます。  
  
- **メンバー アイコン**  
  
     各種メンバーは、独自のアイコンで表されます。 メンバー アイコンをマウスでポイントすると、メンバーのシグネチャが表示されます。 メンバー アイコンまたはメンバー アイコンの左の空白をクリックすると、その行が選択されます。  
  
- **メンバー名**  
  
     メンバー行の **[名前]** 列には、メンバーの名前が表示されます。 この名前は、[プロパティ] ウィンドウの **[名前]** プロパティにも表示されます。 このセルを使用して、読み書き可能アクセス許可を持つ任意のメンバーの名前を変更します。  
  
     **[名前]** 列が狭すぎて名前全体を表示できない場合は、メンバー名をマウスでポイントするとメンバーの名前が表示されます。  
  
- **メンバーの型**  
  
     **[メンバーの型]** セルでは、IntelliSense を使用します。IntelliSense では、現在のプロジェクトまたは参照先プロジェクトで使用できるすべての型の一覧から選択できます。  
  
- **メンバー修飾子**  
  
     `Public` (`public`)、`Private` (`private`)、`Friend` (`internal`) `Protected` (`protected`)、`Protected``Friend` (`protected``internal`)、`Default` のいずれかにメンバーの可視性修飾子を変更します。  
  
- **\<メンバーの追加>**  
  
     [クラスの詳細] ウィンドウの最後の行には、**[名前]** セルに **\<メンバーの追加>** というテキストが表示されます。 このセルをクリックすると、新しいメンバーを作成できます。 詳細については、「[メンバーの作成](../ide/creating-and-configuring-type-members-class-designer.md#CreateMembers)」を参照してください。  
  
- **[プロパティ] ウィンドウでのメンバーのプロパティ**  
  
     [クラスの詳細] ウィンドウには、[プロパティ] ウィンドウに表示されるメンバーのプロパティのサブセットが表示されます。 ある場所のプロパティを変更すると、プロパティの値がグローバルに更新されます。 つまり、他の場所でのその値の表示も更新されます。  
  
- **まとめ**  
  
     **[概要]** セルでは、メンバーに関する情報の概要が公開されます。 **[概要]** セルの省略記号をクリックすると、メンバーの **[概要]**、**[リターン]**、および **[コメント]** に関する情報を表示または編集できます。  
  
- **[非表示]**  
  
     **[非表示]** チェック ボックスがオンの場合は、メンバーが型に表示されません。  
  
#### <a name="to-modify-a-type-member"></a>型のメンバーを変更するには  
  
1. クラス デザイナーを使用して型を選択します。  
  
2. [クラスの詳細] ウィンドウが表示されていない場合、クラス デザイナー ツール バーの **[クラスの詳細ウィンドウ]** をクリックします。  
  
3. [クラスの詳細] ウィンドウのグリッドでフィールドの値を編集します。 各編集の後に Enter キーを押すか、Tab キーを押すなどして、編集したフィールドからフォーカスを移動します。 編集内容は、コードに即時に反映されます。  
  
    > [!NOTE]
    > メンバーの名前だけを変更する場合でも、埋め込み先での編集を使用して変更できます。  
  
## <a name="AddMethodParams"></a> メソッドへのパラメーターの追加  
 [クラスの詳細] ウィンドウを使用して、メソッドにパラメーターを追加します。 パラメーターは、必須の場合または省略可能に構成できます。 パラメーターの **省略可能な既定値** プロパティに値を指定すると、デザイナーで省略可能なパラメーターとしてコードが生成されます。  
  
 パラメーター行には次の項目が含まれます。  
  
- **Name**  
  
   パラメーター行の **[名前]** 列には、パラメーターの名前が表示されます。 この名前は、[プロパティ] ウィンドウの **[名前]** プロパティにも表示されます。 このセルを使用して、読み書き可能アクセス許可を持つ任意のパラメーターの名前を変更できます。  
  
   **[名前]** 列が狭すぎて名前全体を表示できない場合は、パラメーター名をポイントするとパラメーターの名前が表示されます。  
  
- **Type**  
  
   **[パラメーターの型]** セルでは、IntelliSense を使用します。IntelliSense では、現在のプロジェクトまたは参照先プロジェクトで使用できるすべての型の一覧から選択できます。  
  
- **修飾子**  
  
   パラメーター行の **[修飾子]** セルは、パラメーターの新しい修飾子を受け入れ、表示します。 新しいパラメーター修飾子を入力するには、ドロップダウン リスト ボックスを使用して、**[None]**、**[ref]**、**[out]**、または **[params]** (C# の場合)、または **[ByVal]**、**[ByRef]**、または **[ParamArray]** (VB の場合) から選択します。  
  
- **まとめ**  
  
   パラメーター行の **[概要]** セルでは、コード エディターにパラメーターを入力するときに IntelliSense に表示されるコードのコメントを入力できます。  
  
- **\<パラメーターの追加>**  
  
   メンバーの最後のパラメーター行には、**[名前]** セルに **<パラメーターの追加\>** というテキストが表示されます。 このセルをクリックして、新しいパラメーターを作成できます。 詳細については、「[メソッドにパラメーターを追加するには](../ide/creating-and-configuring-type-members-class-designer.md#HowToAddParameterToMethod)」を参照してください。  
  
  **[プロパティ] ウィンドウでのパラメーターのプロパティ**  
  
  [プロパティ] ウィンドウには、クラスの詳細ウィンドウに表示される同じパラメーターのプロパティが表示されます。**[名前]**、**[型]**、**[修飾子]**、**[概要]**、**[省略可能な既定値]**) が表示されます。 ある場所でプロパティを変更すると、プロパティの値がグローバルに更新され、他の場所でのその値の表示も更新されます。  
  
> [!NOTE]
> パラメーターをデリゲートに追加するには、「[メンバーの作成](../ide/creating-and-configuring-type-members-class-designer.md#CreateMembers)」を参照してください。  
  
> [!NOTE]
>    デストラクターはメソッドですが、パラメーターを持つことはできません。  
  
### <a name="HowToAddParameterToMethod"></a> メソッドにパラメーターを追加するには  
  
1. ダイアグラム領域で、パラメーターを追加するメソッドを含む型をクリックします。  
  
     型がフォーカスを取得し、その内容が [クラスの詳細] ウィンドウに表示されます。  
  
2. [クラスの詳細] ウィンドウで、パラメーターを追加するメソッドの行を展開します。  
  
     インデントを設定したパラメーター行が表示され、かっこのペアと **[\<パラメーターの追加>]** という語だけが表示されます。  
  
3. **[\<パラメーターの追加>]** をクリックし、新しいパラメーターの名前を入力し、**Enter** キーを押します。  
  
     新しいパラメーターがメソッドおよびメソッドのコードに追加されます。 このパラメーターは [クラスの詳細] ウィンドウと [プロパティ] ウィンドウに表示されます。  
  
4. オプションとして、型など、パラメーターに関するその他の詳細を指定します。  
  
### <a name="to-add-an-optional-parameter-to-a-method"></a>メソッドに省略可能なパラメーターを追加するには  
  
1. ダイアグラム領域で、省略可能なパラメーターを追加するメソッドを含む型をクリックします。  
  
     型がフォーカスを取得し、その内容が [クラスの詳細] ウィンドウに表示されます。  
  
2. [クラスの詳細] ウィンドウで、省略可能なパラメーターを追加するメソッドの行を展開します。  
  
     インデントを設定したパラメーター行が表示され、かっこのペアと **[\<パラメーターの追加>]** という語だけが表示されます。  
  
3. **[\<パラメーターの追加>]** をクリックし、新しいパラメーターの名前を入力し、**Enter** キーを押します。  
  
     新しいパラメーターがメソッドおよびメソッドのコードに追加されます。 このパラメーターは [クラスの詳細] ウィンドウと [プロパティ] ウィンドウに表示されます。  
  
4. プロパティ ウィンドウで、**省略可能な既定値** プロパティの値を入力します。 パラメーターの "省略可能な既定値" プロパティを設定すると、そのパラメーターは省略可能になります。  
  
    > [!NOTE]
    > 省略可能なパラメーターは、パラメーター リストの最後のパラメーターにする必要があります。  
  
## <a name="ClassDetailsUsageNotes"></a> クラスの詳細の使用上の注意  
 [クラスの詳細] ウィンドウを使用する場合は、次のヒントに注意してください。  
  
 **編集できるセルと編集できないセル**  
  
 [クラスの詳細] ウィンドウのすべてのセルは、次のいくつかの例外を除いて編集できます。  
  
- たとえば、参照アセンブリに存在する場合などは、型全体が読み取り専用です (「[読み取り専用の情報の表示 (クラス デザイナー)](https://msdn.microsoft.com/33e2d3a9-1668-4d10-ae56-fa09b3156e0a)」を参照してください)。クラス デザイナーで図形を選択すると、[クラスの詳細] ウィンドウにその詳細が読み取り専用状態で表示されます。  
  
- インデクサーの場合、名前は読み取り専用でその他 (型、修飾子、概要) は編集できます。  
  
- [クラスの詳細] ウィンドウでは、すべてのジェネリックが読み取り専用パラメーターを持ちます。 ジェネリック パラメーターを変更するには、そのソース コードを編集します。  
  
- ジェネリック型で定義されている型パラメーターの名前は読み取り専用です。  
  
- 型のコードが壊れている (解析できない) 場合は、[クラスの詳細] ウィンドウに型の内容が読み取り専用として表示されます。  
  
  **[クラスの詳細] ウィンドウとソース コード**  
  
- [クラスの詳細] ウィンドウ (またはクラス デザイナー) で図形を右クリックし、[コードの表示] をクリックすることにより、ソース コードを表示できます。 ソース コード ファイルが開き、選択した要素にスクロールします。  
  
- ソース コードの変更は、クラス デザイナーおよび [クラスの詳細] ウィンドウのシグネチャ情報の表示に即時に反映されます。 その時点で [クラスの詳細] ウィンドウが閉じている場合は、次にこのウィンドウを開いたときに新しい情報が表示されます。  
  
- 型のコードが壊れている (解析できない) 場合は、[クラスの詳細] ウィンドウに型の内容が読み取り専用として表示されます。  
  
  **[クラスの詳細] ウィンドウのクリップボード機能**  
  
  [クラスの詳細] ウィンドウからフィールドまたは行をコピーするか切り取り、別の型に貼り付けることができます。 行は、読み取り専用でない場合にだけ切り取ることができます。 行を貼り付けるときに、[クラスの詳細] ウィンドウでは、競合を回避するために新しい名前 (コピーした行の名前から派生した名前) が割り当てられます。  
  
## <a name="ReadOnlyInfo"></a> 読み取り専用の情報の表示  
 クラス デザイナーと [クラスの詳細] ウィンドウには、次の項目の型 (および型のメンバー) を表示できます。  
  
- クラス ダイアグラムを含むプロジェクト  
  
- クラス ダイアグラムを含むプロジェクトから参照されるプロジェクト  
  
- クラス ダイアグラムを含むプロジェクトから参照されるアセンブリ  
  
  後の 2 つでは、参照されるエンティティ (型またはメンバー) は、そのエンティティを表すクラス ダイアグラムで読み取り専用になります。  
  
  プロジェクト全体またはプロジェクトの一部 (個々のファイルなど) が読み取り専用の場合があります。 プロジェクトまたはそのいずれかのファイルが読み取り専用である最も一般的なケースは、ソース コード管理の対象である (およびチェックアウトされていない) 場合、外部アセンブリに存在する場合、またはオペレーティング システムがファイルを読み取り専用と見なす場合です。  
  
  **ソース コード管理**  
  
  クラス ダイアグラムはプロジェクトにファイルとして保存されるため、クラス デザイナーまたは [クラスの詳細] ウィンドウで行う変更を保存するにはプロジェクトをチェックアウトする必要があります。  
  
  **読み取り専用プロジェクト**  
  
  プロジェクトは、ソース コード管理以外の理由で読み取り専用の場合があります。 プロジェクトを閉じると、プロジェクト ファイルを上書きするか、変更を破棄する (保存しない) か、または閉じる操作をキャンセルするかを確認するダイアログ ボックスが表示されます。 上書きを選択した場合は、プロジェクト ファイルが上書きされ、読み書き可能になります。 新しいクラス ダイアグラム ファイルが追加されます。  
  
  **読み取り専用の型**  
  
  ソース コード ファイルが読み取り専用である型を含むプロジェクトの保存を試みた場合は、**[読み取り専用のファイルを保存]** ダイアログ ボックスが表示され、新しい名前または新しい場所でファイルを保存するか、読み取り専用ファイルを上書きするかの選択肢が提示されます。 ファイルを上書きした場合、新しいコピーは読み取り専用でなくなります。  
  
  コード ファイルに構文エラーが含まれる場合、そのファイル内のコードを表示している図形は、構文エラーが修正されるまで一時的に読み取り専用になります。 この状態の図形は、"ソース コード ファイルに解析エラーが含まれています" というツールヒントを表示する赤いテキストと赤いアイコンで示されます。  
  
  別のプロジェクト ノードの下または参照されるアセンブリ ノードの下に存在する参照される型 (.NET Framework 型など) は、クラス デザイナーのデザイン サーフェイスに読み取り専用として示されます。 開いたプロジェクトに存在するローカル型は読み書き可能であり、その図形は、クラス デザイナーのデザイン サーフェイスで読み書き可能として示されます。  
  
  インデクサーは、コードと [クラスの詳細] ウィンドウで読み書き可能ですが、インデクサー名は読み取り専用です。  
  
  [クラス デザイナー] ウィンドウまたは [クラスの詳細] ウィンドウを使用して部分メソッドを編集することはできません。部分メソッドの編集には、コード エディターを使用する必要があります。  
  
  [クラス デザイナー] ウィンドウまたは [クラスの詳細] ウィンドウを使用してネイティブ C++ コードを編集することはできません。ネイティブ C++ コードの編集には、コード エディターを使用する必要があります。  
  
## <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[型およびリレーションシップの表示 (クラス デザイナー)](../ide/viewing-types-and-relationships-class-designer.md)|既存の型、メンバー、および関係は、クラス ダイアグラムで表示できます。|  
|[クラスおよび型のリファクタリング (クラス デザイナー)](../ide/refactoring-classes-and-types-class-designer.md)|リファクタリングを使用すると、型および型のメンバーの名前を簡単に変更できます。 また、クラス間でメンバーを移動し、クラスを部分クラスに分割し、インターフェイスを実装することができます。|