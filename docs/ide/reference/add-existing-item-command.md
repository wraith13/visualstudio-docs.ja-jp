---
title: AddExistingSolutionItem コマンド
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- project.addexistingitem
helpviewer_keywords:
- File.AddExistingItem command
- Add Existing Item command
ms.assetid: 41f56131-d4c7-4f81-83b7-bdac713ea870
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d91e84a817b7b68f56c053d11d69facf753c6efc
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2019
ms.locfileid: "68919386"
---
# <a name="add-existing-item-command"></a>AddExistingSolutionItem コマンド
既存のファイルを現在のソリューションに追加して、そのファイルを開きます。

## <a name="syntax"></a>構文

```cmd
File.AddExistingItem filename [/e:editorname]
```

## <a name="arguments"></a>引数
`filename`\
必須です。 現在のソリューションに追加する項目の完全なパスとファイル名 (拡張子付き)。 ファイル パスまたはファイル名にスペースが含まれている場合は、パス全体を引用符で囲みます。

## <a name="switches"></a>スイッチ
/e: `editorname`\
任意。 ファイルを開くために使用するエディターの名前です。 引数は指定されていても、エディター名がない場合、 **[プログラムから開く]** ダイアログ ボックスが表示されます。

/e:`editorname` 引数の構文では、 **[プログラムから開く] ダイアログ ボックス**に表示されるエディター名 (引用符で囲まれている) が使用されます。 たとえば、ソース コード エディターでスタイル シートを開く場合、/e:`editorname` 引数に対して次のように入力します。

```cmd
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>解説
オート コンプリートでは、入力された正しいパスとファイル名の検索を試みます。

## <a name="example"></a>例
この例では、Form1.frm というファイルを現在のソリューションに追加します。

```cmd
>File.AddExistingItem "C:\public\solution files\Form1.frm"
```

## <a name="see-also"></a>関連項目

- [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)
- [コマンド ウィンドウ](../../ide/reference/command-window.md)
- [検索コマンド ボックス](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
