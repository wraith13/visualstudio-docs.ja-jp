---
title: Visual Studio のアンインストール
titleSuffix: ''
description: Visual Studio をアンインストールする方法について、ステップ バイ ステップで説明します。
ms.date: 07/31/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- uninstall
- uninstall Visual Studio
ms.assetid: 0e445255-b796-426d-ad93-a4d8e36da2c5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 9e9212bc5dda2ea69f685077eb2cbe86470d4064
ms.sourcegitcommit: 5694c5236fa32ba7f5bc1236a853f725ec7557e9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/31/2019
ms.locfileid: "68681349"
---
# <a name="uninstall-visual-studio"></a>Visual Studio のアンインストール

このページでは、開発者向け生産性向上ツールの統合スイートである、Visual Studio のアンインストールについて説明します。

> [!NOTE]
> このトピックは、Windows 上の Visual Studio に適用されます。 Visual Studio for Mac については、[Visual Studio for Mac のアンインストール](/visualstudio/mac/uninstall)に関するページを参照してください。

::: moniker range="vs-2017"

1. コンピューター上で Visual Studio インストーラーを見つけます。

     たとえば、Windows 10 Anniversary Update 以降を実行しているコンピューター上では、 **[スタート]** を選択し、**Visual Studio インストーラー**として一覧表示される **V** の文字までスクロールします。

     ![Visual Studio インストーラー](media/vs2017-locate-the-visual-studio-installer.PNG "Microsoft Visual Studio インストーラーの検索")

   > [!NOTE]
   > 一部のコンピューターでは、Visual Studio インストーラーが **Microsoft Visual Studio インストーラー**として **"M"** の項に表示される場合があります。<br/><br/> Visual Studio インストーラーは `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe` にもあります。

1. インストーラーで、インストールした Visual Studio のエディションを探します。 次に、 **[その他]** を選択した後、 **[アンインストール]** を選択します。

     ![Visual Studio 2017 のアンインストール](media/uninstall-visual-studio.png "Visual Studio 2017 のアンインストール")

1. **[OK]** をクリックして選択を確定します。

後で気が変わり、Visual Studio 2017 を再インストールする場合は、もう一度 Visual Studio インストーラーを起動し、選択画面で **[インストール]** を選びます。

## <a name="uninstall-visual-studio-installer"></a>Visual Studio インストーラーをアンインストールする

Visual Studio 2017 のすべてのインストールと Visual Studio インストーラーを自分のマシンから完全に削除するには、[アプリと機能] からアンインストールします。

1. Windows 10 では、[検索するテキストをここに入力] ボックスに「**アプリと機能**」と入力します。
1. **Microsoft Visual Studio 2017** (または **Visual Studio 2017**) を検索します。
1. **[アンインストール]** を選択します。
1. 次に、**Microsoft Visual Studio インストーラー**を見つけます。
1. **[アンインストール]** を選択します。

::: moniker-end

::: moniker range="vs-2019"

1. コンピューター上で Visual Studio インストーラーを見つけます。

     たとえば、Windows 10 を実行しているコンピューター上で、 **[スタート]** を選択し、**Visual Studio インストーラー**としてリスト表示される **V** の文字までスクロールします。

     ![Visual Studio インストーラーを開く](media/vs-2019/vs-installer-windows-start.png "Visual Studio インストーラーを開く")

     > [!NOTE]
     > また、Visual Studio インストーラーは次の場所にもあります。
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    続行する前に、インストーラーの更新が必要な場合があります。 その場合は、画面の指示に従います。

1. インストーラーで、インストールした Visual Studio のエディションを探します。 次に、 **[その他]** を選択した後、 **[アンインストール]** を選択します。

     ![Visual Studio 2019 のアンインストール](media/vs-2019/vs-installer-uninstall.png "Visual Studio 2019 のアンインストール")

1. **[OK]** をクリックして選択を確定します。

     ![Visual Studio のアンインストールの確認](media/vs-2019/uninstall-visualstudio-confirm.png "Visual Studio 2019 のアンインストールの確認")

後で気が変わって Visual Studio 2019 を再インストールする場合は、再度 Visual Studio インストーラーを起動し、 **[使用可能]** タブを選択し、インストールする Visual Studio のエディションを選択してから、 **[インストール]** を選択します。

## <a name="uninstall-visual-studio-installer"></a>Visual Studio インストーラーをアンインストールする

Visual Studio 2019 のすべてのインストールと Visual Studio インストーラーを自分のマシンから削除するには、[アプリと機能] からアンインストールします。

1. Windows 10 では、[検索するテキストをここに入力] ボックスに「**アプリと機能**」と入力します。
1. **Visual Studio 2019** を見つけます。
1. **[アンインストール]** を選択します。
1. 次に、**Microsoft Visual Studio インストーラー**を見つけます。
1. **[アンインストール]** を選択します。

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>関連項目

* [Visual Studio の変更](modify-visual-studio.md)
* [Visual Studio の更新](update-visual-studio.md)
* [Visual Studio for Mac のアンインストール](/visualstudio/mac/uninstall)
