---
title: レイヤー モデル拡張機能の展開 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, deploying extensions
- layer models, deploying extensions
ms.assetid: 00a4675b-d20e-487e-8fd5-be2b1e0ba238
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a58adf1be92655a6ca7846e8c1d7ea41515b7109
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63422663"
---
# <a name="deploy-a-layer-model-extension"></a>レイヤー モデル拡張機能の配置
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio の他のユーザーは、Visual Studio を使って作成されたレイヤー モデリング拡張機能をインストールできます。  
  
## <a name="installing-your-extension"></a>拡張機能のインストール  
 拡張機能をコンパイルすると VSIX ファイルが作成され、これを他のコンピューターにインストールできます。 また、このファイルを開発用コンピューターにインストールし、Visual Studio のメイン インスタンスで拡張機能を使用できるようにすることもできます。  
  
#### <a name="to-install-the-extension"></a>拡張機能をインストールするには  
  
1. 含むプロジェクトで**source.vsix.manifest**オープン**bin\\\\*** ファイル エクスプ ローラーでします。  
  
2. コピー、  **\*.vsix**ファイルを拡張機能をインストールするコンピューターにします。  
  
3. ターゲット コンピューターの Windows エクスプローラーで *.vsix をダブルクリックします。  
  
    VSIX インストーラーが起動します。  
  
#### <a name="to-uninstall-the-extension"></a>拡張機能をアンインストールするには  
  
1. Visual Studio での**ツール** メニューのをクリックして**拡張機能と更新**します。  
  
2. 拡張機能の名前をクリックし、クリックして**アンインストール**します。  
  
## <a name="installing-an-extension-on-a-team-foundation-build-server"></a>Team Foundation ビルド サーバーへの拡張機能のインストール  
 通常、[!INCLUDE[esprbuild](../includes/esprbuild-md.md)] サーバーには Visual Studio はインストールされていないので、VSIX をダブルクリックしてインストールすることはできません。 [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] のインストールには VSIX 拡張機能を実行できるコンポーネントがいくつか含まれますが、拡張機能のインストールは手動で行う必要があります。  
  
#### <a name="to-install-your-layer-extension-on-a-includeesprbuildincludesesprbuild-mdmd-server"></a>レイヤー拡張機能を [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] サーバーにインストールするには  
  
1. コピー、 **.vsix** 、開発用コンピューターからファイルを[!INCLUDE[esprbuild](../includes/esprbuild-md.md)]コンピューター。  
  
     VSIX ファイルを次のいずれかの場所に置きます。  
  
    - すべてのユーザーおよびサービスを対象にインストールする場合:  
  
         %ProgramFiles%\Microsoft Visual Studio [バージョン]\Common7\IDE\Extensions\Microsoft  
  
    - [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] を実行するネットワーク サービスだけを対象にインストールする場合:  
  
         %WinDir%\ServiceProfiles\NetworkService\AppData\Local\Microsoft\VisualStudio\\[version]\Extensions\Microsoft  
  
    - [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] が特定のユーザーとして対話モードで実行されるように構成されており、そのユーザーだけを対象にインストールする場合:  
  
         %LocalAppData%\Microsoft\VisualStudio\\[version]\Extensions\Microsoft  
  
        > [!NOTE]
        > %Localappdata% は通常*DriveName*: ユーザー*UserName*AppDataLocal します。  
  
2. 各 VSIX ファイルを同じ場所のフォルダーに展開します。  
  
    1. ファイル名拡張子が変更 **.vsix**に **.zip**します。  
  
    2. .zip ファイルの内容をフォルダーに抽出します。  
  
    3. .zip ファイルを削除します。  
  
3. [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] を再起動します。
