---
title: Visual Studio Test Professional のワークロードとコンポーネント ID
titleSuffix: ''
description: Visual Studio のワークロードとコンポーネント ID を使用して、あらゆる側面からテストを行う担当者向けの統合テスト ツールを提供します
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.date: 05/22/2019
ms.topic: reference
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.assetid: 70c03438-8434-4921-ada0-c172519af431
ms.prod: visual-studio-windows
ms.technology: vs-installation
monikerRange: vs-2017
ms.openlocfilehash: cbda03d7a302de04af3f66537afeefc2073d158f
ms.sourcegitcommit: cd21b38eefdea2cdefb53e68e7a30b868e78dd6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/22/2019
ms.locfileid: "66037348"
---
# <a name="visual-studio-test-professional-component-directory"></a>Visual Studio Test Professional のコンポーネント ディレクトリ

このページの表では、コマンド ラインを使用して Visual Studio をインストールするか、VSIX マニフェストで依存関係として指定するために使用できる ID の一覧を示します。 Visual Studio の更新プログラムがリリースされる際には、さらにコンポーネントが追加される予定です。

また、このページに関して以下の点に注意してください。

* 各ワークロードに個別のセクションがあり、ワークロード ID と、そのワークロードで利用できるコンポーネントの表が示されています。
* 既定では、ワークロードをインストールすると**必須**コンポーネントがインストールされます。
* 選択した場合は、**推奨**コンポーネントと**オプション** コンポーネントもインストールできます。
* どのワークロードにも関連付けられていない追加のコンポーネントの一覧を示したセクションも追加しました。

VSIX マニフェストで依存関係を設定するときは、コンポーネント ID のみを指定する必要があります。 このページの表を使用して、コンポーネントの最小の依存関係を確認してください。 シナリオによって、1 つのワークロードの 1 つのコンポーネントだけを指定する場合もあれば、 1 つのワークロードの複数のコンポーネントを指定したり、複数のワークロードの複数のコンポーネントを指定したりする場合もあります。 詳細については、「[方法: Migrate Extensibility Projects to Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)」 (方法: 機能拡張プロジェクトを Visual Studio 2017 に移行する) を参照してください。

これらの ID の使用方法の詳細については、「[Use Command-Line Parameters to Install Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)」(コマンドライン パラメーターを使用して Visual Studio 2017 をインストールする) をご覧ください。 その他の製品のワークロードとコンポーネント ID の一覧については、「[Visual Studio 2017 Workload and Component IDs](workload-and-component-ids.md)」(Visual Studio 2017 のワークロード ID とコンポーネント ID) をご覧ください。

## <a name="test-professional"></a>Test Professional

**ID:** Microsoft.VisualStudio.Workload.TestProfessional

**説明:** Test Professional はあらゆる側面からテストを行う担当者向けの統合テスト ツールを提供し、テスト ライフサイクル全体にわたるテストのニーズに応えます。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | name | Version | 依存関係の種類
--- | --- | --- | ---
Microsoft.VisualStudio.Component.TestTools.FeedbackClient | Microsoft Feedback Client | 15.6.27406.0 | 必須
Microsoft.VisualStudio.Component.TestTools.MicrosoftTestManager | Microsoft Test Manager | 15.6.27406.0 | 必須

## <a name="unaffiliated-components"></a>関連付けられていないコンポーネント

以下のコンポーネントはどのワークロードにも含まれていませんが、個別のコンポーネントとして選択できます。

コンポーネント ID | name | Version
--- | --- | ---
N/A | N/A | N/A

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>関連項目

* [Visual Studio のワークロードとコンポーネント ID](workload-and-component-ids.md)
* [Visual Studio 管理者ガイド](visual-studio-administrator-guide.md)
* [コマンド ライン パラメーターを使用して Visual Studio をインストールする](use-command-line-parameters-to-install-visual-studio.md)
  * [コマンド ライン パラメーターの例](command-line-parameter-examples.md)
* [Visual Studio のオフライン インストールを作成する](create-an-offline-installation-of-visual-studio.md)
