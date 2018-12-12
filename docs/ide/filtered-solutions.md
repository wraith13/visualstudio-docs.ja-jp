---
title: プロジェクトのサブセットを読み込む
ms.date: 12/04/2018
ms.topic: conceptual
ms.prod: visual-studio-dev16
ms.technology: vs-ide-general
helpviewer_keywords:
- filtered solution
- solution filtering
author: gewarren
ms.author: stsu
manager: douge
ms.openlocfilehash: 655644e936bdfb1382e70d746f589b8fcfabf488
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2018
ms.locfileid: "52897223"
---
# <a name="filtered-solutions-in-visual-studio"></a>Visual Studio のフィルター処理済みソリューション

**Visual Studio 2019 Preview 1 の新機能**

大規模な開発チームでは、多くのプロジェクトがある 1 つの大規模なソリューションを使用して、共同作業することがよくあります。 しかし、個々の開発者は通常、これらのプロジェクトの小さなサブセットで作業します。 大規模なソリューションを開くときのパフォーマンスを向上させるため、Visual Studio 2019 Preview 1 では、*ソリューション フィルタリング*が導入されました。 ソリューション フィルタリングにより、選択したプロジェクトのみが読み込まれたソリューションを開くことができます。 ソリューションにプロジェクトのサブセットを読み込むことで、ソリューションの読み込み時間とテストの実行時間を短縮し、より焦点を絞ったレビューが可能になります。

次の機能が使用できます。

- どのプロジェクトも読み込まずにソリューションを開くことで、よりすばやくコードに到達できます。 ソリューションを開いてから、ロードするプロジェクトを選択することができます。

- Visual Studio では前のセッションで読み込まれたプロジェクトを記憶しているため、ソリューションを再度開くと、これらのプロジェクトだけが読み込まれます。

- ソリューション フィルター ファイルを作成して、1 つ以上のプロジェクトの読み込み構成を保存したり、他のチーム メンバーと構成を共有することができます。

## <a name="open-a-filtered-solution"></a>フィルター処理されたソリューションを開く

一部のプロジェクトだけが読み込まれたソリューションを開くには、次の手順を実行します。

1. メニュー バーから、**[ファイル]** > **[開く]** > **[プロジェクト/ソリューション]** を選択します。

2. **[新しいプロジェクト]** ダイアログで、ソリューションを選択してから、**[プロジェクトを読み込まない]** を選択します。

   ![[プロジェクトを読み込まない] がオンになった Visual Studio の [プロジェクトを開く] ダイアログ](media/filtered-solutions/do-not-load-projects.png)

3. **[開く]** をクリックします。

   すべてのプロジェクトがアンロードされたソリューションが開きます。

4. **ソリューション エクスプローラー**で、読み込むプロジェクトを選択し (複数のプロジェクトを選択する場合は、**Ctrl** キーを押しながらながらクリック)、そのプロジェクトを右クリックして、**[プロジェクトの再読み込み]** を選択します。

   ![Visual Studio ソリューション エクスプローラーで複数のプロジェクトを再読み込みする](media/filtered-solutions/reload-project.png)

   Visual Studio では、次回そのソリューションをローカルで開いたときに読み込まれるプロジェクトが記憶されます。

## <a name="toggle-unloaded-project-visibility"></a>アンロードされたプロジェクトの表示を切り替える

**ソリューション エクスプローラー**で次のいずれかの選択肢を使用して、ソリューション内のすべてのプロジェクトを表示するか、読み込まれたプロジェクトのみを表示するかを選択できます。

- ソリューションを右クリックして、**[アンロードされたプロジェクトを表示]** または **[アンロードされたプロジェクトを非表示]** を選択します。

- アンロードされたプロジェクトの表示を切り替えるには、**[すべてのファイルを表示]** ボタンを選択します。

   ![Visual Studio ソリューション エクスプローラーの [すべてのファイルを表示] ボタン](media/filtered-solutions/show-all-files.PNG)

## <a name="solution-filter-files"></a>ソリューション フィルター ファイル

プロジェクトの読み込み構成を共有またはソース管理にコミットする場合は、ソリューション フィルター ファイル (拡張子は *.slnf*) を作成することができます。 ソリューション フィルター ファイルを開くと、指定されたプロジェクトが読み込まれ、アンロードされたプロジェクトがすべて非表示になったソリューションが Visual Studio で開かれます。 アンロードされたプロジェクトを表示するように[切り替える](#toggle-unloaded-project-visibility)ことができます。

ソリューション フィルター ファイルは、**ソリューション エクスプローラー**でソリューションの横のアイコンにじょうごグリフが追加されることで、通常のソリューション ファイルと視覚的に区別されます。 フィルターの名前と、読み込まれたプロジェクトの数も、ソリューション名の横に表示されます。

![Visual Studio ソリューション エクスプローラーで開かれたソリューション フィルター ファイル](media/filtered-solutions/solution-filter.PNG)

> [!NOTE]
> ソリューション フィルター ファイルを作成した後に新しいプロジェクトが元のソリューションに追加される場合、それらはアンロードされたプロジェクトとして**ソリューション エクスプローラー**に表示されます。

### <a name="create-a-solution-filter-file"></a>ソリューション フィルター ファイルを作成する

1. **ソリューション エクスプローラー**で、ソリューションを右クリックし、**[ソリューション フィルターとして保存]** を選択します。

   ![Visual Studio ソリューション エクスプローラーの [ソリューション フィルターとして保存] メニュー](media/filtered-solutions/save-as-solution-filter.png)

2. ソリューション フィルター ファイルの場所と名前を選択します。

ソリューション フィルター ファイルを作成すると、そのファイルは簡単にアクセスできるように **最近使ったプロジェクトおよびソリューション** リストに追加されます。

![Visual Studio の最近開いた項目](media/filtered-solutions/open-recent.png)

## <a name="see-also"></a>関連項目

- [ソリューション エクスプローラーでファイルの入れ子をカスタマイズする](file-nesting-solution-explorer.md)
- [Visual Studio のパフォーマンスの最適化](optimize-visual-studio-performance.md)