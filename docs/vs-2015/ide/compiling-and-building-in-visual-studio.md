---
title: コードのコンパイルとビルド
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- builds [Visual Studio], about building in Visual Studio
- custom build steps, types of builds
ms.assetid: c7958821-285f-4e28-9e7a-b5d8b40336a1
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b534e46f4cdef87641207ec13419d4c59d04ed3f
ms.sourcegitcommit: b56dc6fadc6c924beed36bb4c2ccc16cf6bcfa1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/02/2019
ms.locfileid: "68740073"
---
# <a name="compiling-and-building-in-visual-studio"></a>Visual Studio でのコンパイルとビルド
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

開発サイクル中、何度も Visual Studio を使用して、アプリケーションをビルドし、アセンブリや実行可能プログラムを作成できます。 コードを何度もビルドすることによって、無効な構文、キーワードのスペルミス、型の不一致などのコンパイル時エラーを早い段階で特定できます。 また、コードのデバッグ バージョンを何度もビルドして実行することにより、ロジック エラーやセマンティック エラーなどの実行時エラーを検出して修正できます。

 プロジェクトまたはソリューションの開発を完了し、十分にデバッグしたら、そのプロジェクトまたはソリューションのコンポーネントをリリース ビルドでコンパイルできます。 既定では、リリース ビルドはデバッグ バージョンよりサイズが小さく実行が高速になるように設計および最適化されます。 詳細については、「[チュートリアル:アプリケーションをビルドする](../ide/walkthrough-building-an-application.md)」を参照してください。

## <a name="choosing-a-build-method"></a>ビルド方法の選択
 アプリケーションは、IDE の既定のビルド オプション、コマンド プロンプト、または Team Foundation ビルドを使用してビルドできます。 これらの各オプションでは基になるテクノロジとして MSBuild が使用されており、それぞれの方法には次の表に示すような利点があります。

|ビルド方法|利点|詳細情報|
|------------------|--------------|--------------------------|
|IDE の使用|-   ビルドをより簡単に作成し、すぐに実行できます。<br />-   C++ および C# のプロジェクトについては、マルチプロセッサ ビルドを実行できます。<br />-   ビルド システムの一部をカスタマイズできます。|[Visual Studio でのプロジェクトとソリューションのビルドおよびクリーン](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)|
|MSBuild コマンド ラインの実行|-   Visual Studio をインストールせずにプロジェクトをビルドできます。<br />-   すべての種類のプロジェクトについて、マルチ プロセッサ ビルドを実行できます。<br />-   ビルド システムのほとんどの部分をカスタマイズできます。|[MSBuild](../msbuild/msbuild.md)|
|Team Foundation ビルドの使用|-   ビルド プロセスを自動化できます。 たとえば、1 つまたは複数のプロジェクトを夜間にビルドすることも、コードのチェックインごとにビルドすることもできます。 また、開発用コンピューターではなく、共有ビルド サーバーでプロジェクトをビルドできます。<br />-   ビルドするコード、実行するテスト、およびその他のオプションを簡単に指定できます。<br />-   ビルド ワークフローを変更し、必要に応じてビルド アクティビティを作成することで、大幅にカスタマイズされたタスクを実行できます。|[アプリケーションのビルド](/azure/devops/pipelines/index)|

## <a name="building-from-the-ide"></a>IDE でのビルド
 プロジェクトを作成すると、既定のビルド構成が定義され、ビルドのコンテキストを用意するために、既定のソリューション ビルド構成が割り当てられます。 ソリューション構成によって、ソリューション内のプロジェクトをビルドおよび配置する方法が定義されます。 プロジェクト構成とは、プラットフォームおよびビルドの種類 (リリース Win32 など) に固有の一連のプロジェクト プロパティです。 これらの既定の構成を編集して、独自の構成を作成することもできます。 詳細については、「[プロジェクトデザイナーの概要](https://msdn.microsoft.com/898dd854-c98d-430c-ba1b-a913ce3c73d7)」および[「NIB 方法:プロジェクトのプロパティと構成設定](https://msdn.microsoft.com/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)を変更します。

 IDE 内で、次の追加タスクを実行することもできます。

- [ビルド出力ディレクトリを変更する](../ide/how-to-change-the-build-output-directory.md)。

- [正しくビルドするために、別のプロジェクトからの出力に依存するプロジェクトを特定する](../ide/how-to-create-and-remove-project-dependencies.md)。

- [ビルド ログまたはビルドの出力ウィンドウに含まれる情報の量を変更する](../ide/how-to-view-save-and-configure-build-log-files.md)。

- [Visual C#、Visual C++、または Visual Basic で特定のコンパイラの警告を非表示にする](../ide/how-to-suppress-compiler-warnings.md)。

- [ビルドに対してカスタムのコンパイル前アクションまたはコンパイル後アクションを指定する](../ide/specifying-custom-build-events-in-visual-studio.md)。

- 並行ビルドを使用してビルド パフォーマンスを改善する。 詳細については、「[複数のプロジェクトの並行ビルド](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)」またはブログ投稿「[Tuning C++ build parallelism](http://blogs.msdn.com/b/msbuild/archive/2010/03/08/tuning-c-build-parallelism-in-vs2010.aspx)」 (C++ での並列ビルドの調整) を参照してください。

## <a name="see-also"></a>関連項目
 [チュートリアル: アプリケーション](../ide/walkthrough-building-an-application.md)の構築[ビルド構成](../ide/understanding-build-configurations.md)についてビルド[プラットフォームの概要](../ide/understanding-build-platforms.md) [Web サイトプロジェクト](https://msdn.microsoft.com/library/a9cbb88c-8fff-4c67-848b-98fbfd823193) [のビルド (コンパイル) 方法:プロジェクトの依存関係を作成および削除する](../ide/how-to-create-and-remove-project-dependencies.md)
