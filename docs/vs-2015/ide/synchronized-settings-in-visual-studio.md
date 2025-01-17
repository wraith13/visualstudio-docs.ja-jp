---
title: 同期された設定
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: a3d2ea29-be5d-4012-9820-44b06adbb7dd
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ed6e544378089222cb69c491b0cd473544e05220
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67825662"
---
# <a name="synchronized-settings-in-visual-studio"></a>Visual Studio での同期された設定
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

複数のコンピューターで同じ個人アカウントを使用して Visual Studio にサインインした場合、既定ではすべてのコンピューターで設定が同期されます。

## <a name="synchronized-settings"></a>同期された設定
 既定では、次の設定が同期されます。

- 開発設定 (Visual Studio を初めて実行するときに設定を選択する必要がありますが、選択内容はいつでも変更できます)。 詳細については、「[Visual Studio での開発設定のカスタマイズ](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。

- **[ツール &#124; オプション]** ページの次のオプション。

  - **[環境]** 、 **[全般]** オプション ページの **[テーマ]** およびメニュー バー枠の設定

  - **[環境]** 、 **[フォントおよび色]** オプション ページのすべての設定

  - **[環境]** 、 **[キーボード]** オプション ページのすべてのキーボード ショートカット

  - **[環境]、[タブ]、および [ウィンドウ]** オプション ページのすべての設定

  - **[環境]** 、 **[スタートアップ]** オプション ページのすべての設定

  - **[テキスト エディター]** オプション ページのすべての設定

- [XAML デザイナー] オプション ページのすべての設定

- ユーザー定義のコマンド エイリアス。 コマンド エイリアスを定義する方法の詳細については、「[Visual Studio コマンドの定義済みのエイリアス](../ide/reference/visual-studio-command-aliases.md)」を参照してください。

- **[ウィンドウ &#124; ウィンドウ レイアウトの管理]** ページのユーザー定義のウィンドウ レイアウト

## <a name="turning-synchronized-settings-off-for-a-particular-computer"></a>特定のコンピューター上の同期された設定の無効化
 Visual Studio の同期された設定は、既定でオンになっています。 あるコンピューター上の同期された設定をオフにするには、 **[ツール &#124; オプション &#124; 環境 &#124; 同期された設定]** ページに移動して、チェック ボックスをオフにします。  たとえば、コンピューター A 上の Visual Studio の設定を同期しないようにすると、コンピューター A で行った設定変更がコンピューター B やコンピューター C に表示されなくなります。コンピューター B および C は、引き続き相互に同期しますが、コンピューター A とは同期しなくなります。

## <a name="synchronizing-settings-across-visual-studio-family-products-and-editions"></a>Visual Studio ファミリ製品およびエディション間での設定の同期
 Express エディションや Community エディションを含む Visual Studio 2015 の任意のエディション間で、設定を同期できます。 Blend などの Visual Studio ファミリ製品の間でも設定が同期されます。 ただし、各ファミリ製品には Visual Studio で共有されない独自の設定が含まれる場合があります。 たとえば、コンピューター A 上の Blend に固有の設定は、コンピューター B 上の Blend で共有されますが、コンピューター A または B 上の Visual Studio では共有されません。

> [!WARNING]
> Visual Studio 2013 と Visual Studio 2015 の間では、設定は同期されません。 Visual Studio 2015 を初めて開くと、Visual Studio 2013 の設定が移行されますが、その後で設定を Visual Studio 2013 に再度移行することはできません。

## <a name="see-also"></a>関連項目
 [IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)
