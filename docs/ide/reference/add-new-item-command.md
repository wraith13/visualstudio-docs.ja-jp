---
title: AddNewSolutionItem コマンド
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- project.addnewitem
helpviewer_keywords:
- Add New Item command
- File.AddNewItem command
ms.assetid: 63b7df32-db83-463b-bbe7-7ff011fe5298
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6a73bd7008e0058fe984fcb708c92c2bd983d427
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2019
ms.locfileid: "68919366"
---
# <a name="add-new-item-command"></a>AddNewSolutionItem コマンド
新規ソリューションのアイテム (.htm、.css、.txt、フレームセットなど) を現在のソリューションに追加して、そのソリューションを開きます。

## <a name="syntax"></a>構文

```cmd
File.AddNewItem [filename] [/t:templatename] [/e:editorname]
```

## <a name="arguments"></a>引数
`filename`\
任意。 ソリューションに追加する項目のパスとファイル名。

## <a name="switches"></a>スイッチ
/t: `templatename`\
任意。 作成するファイルの種類を指定します。 テンプレート名が指定されていない場合は、既定でテキスト ファイルが作成されます。

/t:`templatename` 引数の構文は、 **[新しいソリューション項目の追加]** ダイアログ ボックスの情報をミラー化します。 ファイルの種類が後に続く完全なカテゴリを入力する必要があります。その場合、カテゴリ名とファイルの種類を円記号 (`\`) で区切り、引用符で文字列全体を囲みます。

たとえば、新しいテキスト ファイルを作成する場合は、/t:`templatename` 引数に対して次のように入力します。

```cmd
/t:"General\Style Sheet"
```

/e: `editorname`\
任意。 ファイルが開かれるエディターの名前。 引数は指定されていても、エディター名がない場合、 **[プログラムから開く]** ダイアログ ボックスが表示されます。

/e:`editorname` 引数の構文では、 **[プログラムから開く] ダイアログ ボックス**に表示されるエディター名 (引用符で囲まれている) が使用されます。

たとえば、ソース コード エディターでスタイル シートを開く場合、/e:`editorname` 引数に対して次のように入力します。

```cmd
/e:"Source Code (text) Editor"
```

## <a name="example"></a>例
この例では、現在のソリューションに、MyHTMLpg という新しいソリューション項目を追加します。

```cmd
>File.AddNewItem MyHTMLpg /t:"General\HTML Page"
```

## <a name="see-also"></a>関連項目

- [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)
- [コマンド ウィンドウ](../../ide/reference/command-window.md)
- [検索コマンド ボックス](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
