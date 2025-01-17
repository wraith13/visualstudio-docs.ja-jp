---
title: ビルド アクション
description: この記事では、C# プロジェクトで使用できるさまざまなビルド アクションについて説明します。
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.openlocfilehash: 54e341b4e5961623f41963bb90c2e5d60b110cf4
ms.sourcegitcommit: 7fbfb2a1d43ce72545096c635df2b04496b0be71
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2019
ms.locfileid: "67691195"
---
# <a name="build-actions"></a>ビルド アクション

Visual Studio for Mac プロジェクト内のすべてのファイルに、ビルド アクションがあります。 これで、ビルド時にファイルに発生する内容を制御します。 下の画像のように、任意のファイルを右クリックして **[ビルド アクション]** に移動することで、この動作を設定できます。

![ソリューション エクスプローラーで [コンパイル] ビルド アクションを選択する](media/projects-and-solutions-image1.png)

C# プロジェクトの一般的ビルド アクションには次のようなものがあります。

* **なし** - このファイルはいかなる形でもビルドに含まれません。IDE から簡単にアクセスできるようにプロジェクトに含まれています。
* **コンパイル** - このファイルはソース ファイルとして C# コンパイラに渡されます。
* **EmbeddedResource** - このファイルはアセンブリに埋め込むリソースとして C# コンパイラに渡されます。 `System.Reflection` 名前空間の [Assembly.GetManifestResourceStream](https://docs.microsoft.com/dotnet/api/system.reflection.assembly.getmanifestresourcestream) を使用すると、アセンブリからファイルを読み取ることができます。
* **コンテンツ** - ASP.NET プロジェクトの場合、展開時、このファイルはサイトの一部として追加されます。 Xamarin.iOS プロジェクトと Xamarin.Mac プロジェクトの場合、アプリ バンドルに含まれます。

ソリューション エクスプローラーでは複数のファイルを選択でき、ビルド アクションを一度に複数のファイルに設定できます。

また、特定のプロジェクトのビルド アクションがあります。 Xamarin.iOS プロジェクトには、**BundleResource** ビルド アクションがあります。このアクションでは、アプリ バンドルの一環としてファイルを追加します。 Xamarin.Android 固有のビルド アクションに関する詳細は、[ビルド プロセス](/xamarin/android/deploy-test/building-apps/build-process#Build_Actions) ガイドでご覧いただけます。

## <a name="see-also"></a>関連項目

- [ビルド アクション (Windows 上の Visual Studio)](/visualstudio/ide/build-actions)