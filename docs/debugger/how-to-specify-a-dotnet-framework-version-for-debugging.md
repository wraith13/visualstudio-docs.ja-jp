﻿---
title: デバッグで .NET Framework のバージョンの指定 |Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- .NET Framework, specifying version for debugging
- debugging [Visual Studio], specifying .NET Framework version
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: bfe17100fcdcb0d475a7467233caa51ba7895225
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747472"
---
# <a name="how-to-specify-a-net-framework-version-for-debugging-c-visual-basic-f"></a>方法: デバッグで .NET Framework のバージョンを指定 (C#、Visual Basic、 F#)

Visual Studio デバッガーでは、Microsoft .NET Framework の旧バージョンと現在のバージョンのデバッグをサポートします。 Visual Studio からアプリケーションを起動する場合、デバッガーはデバッグ中のアプリケーションの .NET Framework の正しいバージョンを常に特定できます。 ただし場合は、アプリケーションは既に実行してデバッグを開始を使用して**にアタッチ**デバッガーは常にできないことがあります、.NET Framework の以前のバージョンを識別します。 この場合、次のようなエラー メッセージが出力されます。

``` cmd
The debugger has made an incorrect assumption about the .NET Framework version your application is going to use.
```

このエラーが表示される場所のまれなケースで、デバッガーに使用するバージョンを示すためにレジストリ キーを設定できます。

### <a name="to-specify-a-net-framework-version-for-debugging"></a>デバッグで .NET Framework のバージョンを指定するには

1. コンピューターにインストールされている .NET Framework のバージョンを確認するには、Windows\Microsoft.NET\Framework ディレクトリを探します。 バージョン番号は次のようになります。

    `V1.1.4322`

    正しいバージョン番号を確認し、メモしておきます。

2. **レジストリ エディター** (regedit) を起動します。

3. **レジストリ エディター**で、[HKEY_LOCAL_MACHINE] フォルダーを開きます。

4. 次に移動します。HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine\\{449EC4CC-30D2-4032-9256-EE18EB41B62B}

    このキーが存在しない場合、HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine を右クリックし、 **[新しいキー]** をクリックします。 新しいキーの名前`{449EC4CC-30D2-4032-9256-EE18EB41B62B}`します。

5. {449EC4CC-30D2-4032-9256-EE18EB41B62B} に移動し、 **[名前]** 列を確認して、CLRVersionForDebugging キーを探します。

   1. このキーが存在しない場合、{449EC4CC-30D2-4032-9256-EE18EB41B62B} を右クリックし、 **[新規] - [文字列値]** をクリックします。 新しい文字列値を右クリックし、をクリックして**の名前を変更**、および種類`CLRVersionForDebugging`します。

6. **[CLRVersionForDebugging]** をダブルクリックします。

7. **[文字列の編集]** ボックスの **[値]** ボックスに、.NET Framework のバージョン番号を入力します。 例:V1.1.4322

8. **[OK]** をクリックします。

9. **レジストリ エディター**を閉じます。

     それでもデバッグの開始時にエラー メッセージが表示される場合は、レジストリに正しいバージョン番号が入力されていることを確認します。 また、Visual Studio でサポートされている .NET Framework のバージョンを使用していることを確認します。 デバッガーは、現在のバージョンおよび以前のバージョンの .NET Framework と互換性がありますが、将来のバージョンとの上位互換性はない可能性があります。

## <a name="see-also"></a>関連項目
- [デバッガーの設定と準備](../debugger/debugger-settings-and-preparation.md)
