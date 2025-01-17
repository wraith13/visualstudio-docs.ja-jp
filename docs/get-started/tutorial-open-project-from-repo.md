---
title: 'チュートリアル: リポジトリからプロジェクトを開く'
description: Visual Studio を使って Git または Azure DevOps リポジトリのプロジェクトを開く方法について説明します。
ms.custom: get-started
ms.date: 03/30/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b1796ca10226e4aa5d0242bea89cc01f8452cf9e
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/30/2019
ms.locfileid: "66402087"
---
# <a name="tutorial-open-a-project-from-a-repo"></a>チュートリアル: リポジトリからプロジェクトを開く

このチュートリアルでは、最初に Visual Studio を使ってリポジトリに接続した後、そこからプロジェクトを開きます。

::: moniker range="vs-2017"

Visual Studio をまだインストールしていない場合は、[Visual Studio のダウンロード](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ページに移動し、無料試用版をインストールしてください。

::: moniker-end

::: moniker range="vs-2019"

Visual Studio をまだインストールしていない場合は、[Visual Studio のダウンロード](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ページに移動し、無料試用版をインストールしてください。

::: moniker-end

## <a name="open-a-project-from-a-github-repo"></a>GitHub リポジトリからプロジェクトを開く

::: moniker range="vs-2017"

1. Visual Studio 2017 を開きます。

1. 上部のメニュー バーで、 **[ファイル]** > **[開く]** > **[ソース管理から開く]** の順に選択します。

   **[チーム エクスプローラー - 接続]** ページが開きます。

    ![Visual Studio IDE 内の [チーム エクスプローラー] ウィンドウ](./media/open-proj-repo-team-explorer.png)

1. **[ローカル Git リポジトリ]** セクションで、 **[複製]** を選択します。

    ![[ローカル Git リポジトリ] セクションから [複製] を選択する](./media/open-proj-repo-local-git-repo-clone.png)

1. "***複製する Git リポジトリの URL を入力してください***" と表示されているボックスに、リポジトリの URL を入力または貼り付けてから、**Enter** キーを押します。 (GitHub にサインインするよう求められた場合は、サインインします。)

   Visual Studio でリポジトリが複製されると、チーム エクスプローラーが閉じてソリューション エクスプローラーが開きます。 "*ソリューションの一覧を表示するには、上記のソリューションおよびフォルダーをクリックします*" というメッセージが表示されます。 **[ソリューションおよびフォルダー]** を選択します。

   ![ソリューション エクスプローラーから "ソリューションおよびフォルダー" を選択する](./media/open-proj-repo-github-solutions-folders.png)

1. 使用可能なソリューション ファイルがある場合は、それが "ソリューションおよびフォルダー" スライド アウト メニューに表示されます。 それを選択すると、Visual Studio でソリューションが開きます。

   ![ソリューション エクスプローラーのドロップダウン リストから開きたいものを選択する](./media/open-proj-repo-github-solutions-folders-picker.png)

   リポジトリ内にソリューション ファイル (具体的には、.sln ファイル) がない場合は、スライド アウト メニューに "ソリューションが見つかりません" と表示されます。 ただし、フォルダーのメニューから任意のファイルをダブルクリックして、それを Visual Studio コード エディターで開くことができます。

### <a name="review-your-work"></a>作業内容の確認

次のアニメーションを見て、前のセクションで完了した作業を確認します。

   ![Visual Studio を使って GitHub リポジトリのプロジェクトを開くアニメーション](./media/open-project-from-github.gif)

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio 2019 を開きます。

1. スタート ウィンドウで、 **[コードを複製またはチェックアウトする]** を選択します。

   ![[新しいプロジェクトの作成] ウィンドウを表示する](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. リポジトリの場所を入力し、 **[複製]** を選択します。

   ![[コードを複製またはチェックアウトする] ウィンドウを表示する](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Visual Studio でリポジトリからプロジェクトが開かれます。

1. 使用可能なソリューション ファイルがある場合は、それが "ソリューションおよびフォルダー" スライド アウト メニューに表示されます。 それを選択すると、Visual Studio でソリューションが開きます。

   ![ソリューション エクスプローラーのドロップダウン リストから開きたいものを選択する](./media/open-proj-repo-github-solutions-folders-picker.png)

   リポジトリ内にソリューション ファイル (具体的には、.sln ファイル) がない場合は、スライド アウト メニューに "ソリューションが見つかりません" と表示されます。 ただし、フォルダーのメニューから任意のファイルをダブルクリックして、それを Visual Studio コード エディターで開くことができます。

::: moniker-end

## <a name="open-a-project-from-an-azure-devops-repo"></a>Azure DevOps リポジトリからプロジェクトを開く

::: moniker range="vs-2017"

1. Visual Studio 2017 を開きます。

1. 上部のメニュー バーで、 **[ファイル]** > **[開く]** > **[ソース管理から開く]** の順に選択します。

   **[チーム エクスプローラー - 接続]** ページが開きます。

    ![Visual Studio IDE 内の [チーム エクスプローラー] ウィンドウ](./media/open-proj-repo-team-explorer.png)

1. Azure DevOps リポジトリに接続するには、次の 2 つの方法があります。

      - **[ホストされるサービスのプロバイダー]** セクションで、 **[接続...]** を選択します。

        ![Visual Studio IDE 内のチーム エクスプローラー ウィンドウの [ホストされるサービスのプロバイダー] セクション](./media/open-proj-repo-azure-devops.png)

      - **[接続の管理]** ドロップダウン リストで、 **[プロジェクトに接続...]** を選択します。

        ![Visual Studio IDE 内のチーム エクスプローラー ウィンドウの [接続の管理] セクション](./media/open-proj-repo-azuredevops-manage-connections.png)

1. **[プロジェクトに接続]** ダイアログ ボックスで、接続するリポジトリを選択してから、 **[複製]** を選択します。

      ![Visual Studio から生成される "プロジェクトに接続" ダイアログ ボックス](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > リスト ボックスに表示される内容は、自分がアクセスできる Azure DevOps リポジトリによって異なります。

1. Visual Studio でリポジトリが複製されると、チーム エクスプローラーが閉じてソリューション エクスプローラーが開きます。 "*ソリューションの一覧を表示するには、上記のソリューションおよびフォルダーをクリックします*" というメッセージが表示されます。 **[ソリューションおよびフォルダー]** を選択します。

      ![Visual Studio のチーム エクスプローラーからの "ソリューションおよびフォルダー" 通知](./media/open-proj-repo-solutions-folders.png)

   ソリューション ファイル (具体的には、.sln ファイル) が "ソリューションおよびフォルダー" スライド アウト メニューに表示されます。 それを選択すると、Visual Studio でソリューションが開きます。

   リポジトリ内にソリューション ファイルがない場合は、スライド アウト メニューに "ソリューションが見つかりません" と表示されます。 ただし、フォルダーのメニューから任意のファイルをダブルクリックして、それを Visual Studio コード エディターで開くことができます。

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio 2019 を開きます。

1. スタート ウィンドウで、 **[コードを複製またはチェックアウトする]** を選択します。

   ![[新しいプロジェクトの作成] ウィンドウを表示する](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. **[リポジトリを参照する]** セクションで、 **[Azure DevOps]** を選択します。

   ![[コードを複製またはチェックアウトする] ウィンドウを表示する](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   サインイン ウィンドウが表示される場合は、アカウントにサインインします。

1. **[プロジェクトに接続]** ダイアログ ボックスで、接続するリポジトリを選択してから、 **[複製]** を選択します。

      ![Visual Studio から生成される "プロジェクトに接続" ダイアログ ボックス](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > リスト ボックスに表示される内容は、自分がアクセスできる Azure DevOps リポジトリによって異なります。

   複製が完了すると、Visual Studio で **[チーム エクスプローラー]** が開いて通知が表示されます。

     ![複製が完了した後の Visual Studio の [チーム エクスプローラー] ウィンドウ](./media/vs-2019/clone-complete-azure-devops.png)

1. フォルダーやファイルを表示するには、 **[フォルダー ビューの表示]** リンクを選択します。

     ![複製が完了した後の Visual Studio の [チーム エクスプローラー] ウィンドウの [ソリューション] セクション](./media/vs-2019/show-folder-view-azure-devops.png)

     Visual Studio で **[ソリューション エクスプローラー]** が開きます。

1. **[ソリューションおよびフォルダー]** リンクを選択し、ソリューション ファイル (具体的には .sln ファイル) を検索して開きます。

      ![Visual Studio のチーム エクスプローラーからの "ソリューションおよびフォルダー" 通知](./media/open-proj-repo-solutions-folders.png)

   リポジトリにソリューション ファイルがない場合は、"ソリューションが見つかりません" というメッセージが表示されます。 ただし、フォルダーのメニューから任意のファイルをダブルクリックして、それを Visual Studio コード エディターで開くことができます。

::: moniker-end

## <a name="next-steps"></a>次の手順

Visual Studio を使ってコードを書く準備が整ったら、次の言語固有のチュートリアルのいずれかを開始します。

- [Visual Studio のチュートリアル | **C#** ](./csharp/index.yml)
- [Visual Studio のチュートリアル | **Visual Basic**](./visual-basic/index.yml)
- [Visual Studio のチュートリアル | **C++** ](/cpp/get-started/tutorial-console-cpp)
- [Visual Studio のチュートリアル | **Python**](/visualstudio/python/)
- [Visual Studio のチュートリアル | **JavaScript**、**TypeScript**、**Node.js**](/visualstudio/javascript/)

## <a name="see-also"></a>関連項目

- [Azure DevOps Services:Azure Repos と Visual Studio の概要](/azure/devops/repos/git/gitquickstart/)
- [Microsoft Learn:Azure DevOps の概要](/learn/modules/get-started-with-devops/)