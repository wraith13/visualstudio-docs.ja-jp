---
title: -Log (devenv.exe)
ms.date: 12/12/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b2e11cb36176aec94528019cdd19bb5fa86c92b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946805"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)

すべてのアクティビティをトラブルシューティング用のログ ファイルに記録します。 このファイルは、`devenv /log` を少なくとも 1 回呼び出した後に表示されます。 ログ ファイルは既定で次の場所にあります。

**%APPDATA%\\Microsoft\\VisualStudio\\**\<Version\>**\\ActivityLog.xml**

ここで、<\<バージョン\>> は Visual Studio のバージョンです。 ただし、別のパスとファイル名を指定することもできます。

## <a name="syntax"></a>構文

```shell
devenv /Log NameOfLogFile
```

## <a name="arguments"></a>引数

- *NameOfLogFile*

  必須です。 保存先のログ ファイルの完全なパスと名前。

## <a name="remarks"></a>解説

このスイッチは、その他すべてのスイッチの後、コマンド ラインの末尾に指定する必要があります。

ログは、`/Log` スイッチを指定して開いた Visual Studio のすべてのインスタンスのみを対象として記録されます。

## <a name="example"></a>例

この例では、ユーザーのホーム ディレクトリにある `MyVSLog.xml` ファイルにログが記録されます。

```shell
devenv /log "%USERPROFILE%\MyVSLog.xml"
```

## <a name="see-also"></a>関連項目

- [Devenv コマンドライン スイッチ](../../ide/reference/devenv-command-line-switches.md)