---
title: 既存のプロジェクト項目テンプレートの更新
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- item templates, updating
- Visual Studio templates, updating
- project templates, updating
- updating templates [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 57e457224d47e278df169b931c6e9cf6b8ae25e1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62974697"
---
# <a name="how-to-update-existing-templates"></a>方法:既存のテンプレートを更新する

テンプレートを作成し、複数のファイルを *.zip* ファイルに圧縮した後で、テンプレートを変更できます。 それには、テンプレートのファイルを手動で変更するか、テンプレートに基づいてプロジェクトから新しいテンプレートをエクスポートします。

## <a name="use-the-export-template-wizard"></a>[テンプレートのエクスポート] ウィザードを使用する

Visual Studio の**テンプレートのエクスポート ウィザード**を使って、既存のテンプレートを更新することができます。

1. メニュー バーから **[ファイル]** > **[新規作成]** > **[プロジェクト]** の順に選択します。

1. 更新するテンプレートを選択して、新しいプロジェクトを作成する手順を続行します。

1. Visual Studio でプロジェクトを変更します。 たとえば、出力の種類を変更するか、または新しいファイルをプロジェクトに追加します。

1. **[プロジェクト]** メニューの **[テンプレートのエクスポート]** を選択します。

    **テンプレートのエクスポート ウィザード**が開きます。

1. ウィザードの指示に従って、テンプレートを *.zip* ファイルとしてエクスポートします。

1. (省略可能) テンプレートが選択肢として表示されるようにするには、その *.zip* ファイルを次のディレクトリに置きます: *%USERPROFILE%\Documents\Visual Studio \<version\>\Templates\ProjectTemplates* **テンプレートのエクスポート ウィザード**で **[テンプレートを自動的に Visual Studio にインポート]** オプションを選ばなかった場合、このステップを実行する必要があります。

1. 古いテンプレートの *.zip* ファイルを削除します。

## <a name="manually-update-an-existing-template"></a>既存のテンプレートを手動で更新する

圧縮された *.zip* ファイル内のファイルを変更することで、**テンプレートのエクスポート ウィザード**を使わずに既存のテンプレートを更新できます。

### <a name="to-manually-update-an-existing-template"></a>既存のテンプレートを手動で更新するには

1. テンプレートを含む *.zip* ファイルを探します。 ユーザー プロジェクト テンプレートは、*%USERPROFILE%\Documents\Visual Studio \<バージョン\>\Templates\ProjectTemplates* にあります。

1. *.zip* ファイルを展開します。

1. 現在のテンプレート ファイルを変更または削除するか、テンプレートに新しいファイルを追加します。

1. *.vstemplate* XML ファイルを開いたり、変更したり、保存したりして、更新された動作または新しいファイルを処理します。

    *.vstemplate* スキーマの詳細については、[「Visual Studio テンプレート スキーマ参照 (機能拡張)](../extensibility/visual-studio-template-schema-reference.md)」を参照してください。 ソース ファイルでパラメーター化できる内容の詳細については、「[テンプレート パラメーター](../ide/template-parameters.md)」を参照してください。

1. テンプレートでファイルを選び、右クリック メニューまたはコンテキスト メニューから、**[送る]** > **[圧縮 (zip 形式) フォルダー]** の順に選択します。

    選択したファイルは *.zip* ファイルに圧縮されます。

1. 新しい *.zip* ファイルを古い *.zip* ファイルと同じディレクトリに配置します。

1. 抽出したテンプレート ファイルと古いテンプレート *.zip* ファイルを削除します。

## <a name="see-also"></a>関連項目

- [テンプレートのカスタマイズ](../ide/customizing-project-and-item-templates.md)
- [プロジェクト テンプレートと項目テンプレートを作成する](../ide/creating-project-and-item-templates.md)
- [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)
- [テンプレート パラメーター](../ide/template-parameters.md)