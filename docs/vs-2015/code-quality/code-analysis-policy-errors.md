---
title: コード分析ポリシー エラー |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.policyfailures
helpviewer_keywords:
- policy errors, code analysis
ms.assetid: d1f221cd-68c0-4277-9397-b76ad0dbae77
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 9b61d7d9718e9557ef153474718542f889ad7629
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62576742"
---
# <a name="code-analysis-policy-errors"></a>コード分析ポリシー エラー
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

以下のエラーは、チェックインにおいてコード分析ポリシーに適合しない場合に発生します。  
  
 **1 つまたは複数のプロジェクトのコード分析の設定は、コード分析ポリシーと互換性がないです。**  
  
 1 つ以上のコード プロジェクトについて、チーム プロジェクトのソース管理にチェックインするというコード分析の要件が満たされていません。 このエラーは、次に示す 1 つ以上の条件によって発生します。  
  
1. ソリューション内のすべてのプロジェクトで、ビルドに対してコード分析が有効になっていない。  
  
2. ローカル、規則セットの Visual Studio でプロジェクトがある、緩い**アクション**設定に設定されている規則を設定など、チーム プロジェクトの規則よりも**アクション**=**エラー**サーバーがその**アクション**に設定**警告**または**None**規則セットの Visual Studio で実行されている)。  
  
3. Visual Studio で指定された規則セットに、チーム プロジェクトのコード分析チェックイン ポリシーで指定された規則セットのすべての規則が含まれていない。  
  
   **コード分析ポリシーに失敗しました。プロジェクトでエラーがある{0}か、ビルドが最新ではありません。**  
  
   ビルドにエラーがあるか、エラーが修正された後にコード分析が実行されませんでした。  
  
   **チェックインに失敗しました。コード分析ポリシーでは、確認すること Visual Studio でソリューションを開いている必要があります。**  
  
   コード分析ポリシーには、チェックインするファイルがすべて現在開いているソリューションに含まれていなければならないと規定されています。 このエラーを修正するには、チェックインするファイルが含まれるソリューションを開きます。  
  
   **保留中のチェックインのすべてのファイルは、現在開いているソリューション内では。**  
  
   コード分析ポリシーには、チェックインするファイルがすべて現在開いているソリューションに含まれていなければならないと規定されています。 このエラーは、ソリューションは開いているものの [保留中のチェックイン] ビューに表示されているファイルの中に現在開いているソリューションに属していないものがある場合に発生します。 このエラーを修正するには、チェックインするファイルが含まれるソリューションを開きます。  
  
   **バージョン '{0}' が正しくありません。ポリシーで指定した厳密な名前が '{1}'。**  
  
   このエラーは、.NET プロジェクトで発生します。 コード分析ポリシーで必要な規則の .dll がローカル コンピューターに存在しますが、バージョンまたは公開キーが一致しません。 ポリシーの作成者は、このエラーを修正するに .dll を更新する必要があります*C:\Program files \microsoft Visual Studio 8\Team \static Analysis Tools\FxCop\Rules\\* ディレクトリがコンピューターにします。  
  
   **'{0}' ポリシーで指定されたアセンブリが存在しません。**  
  
   このエラーは、.NET プロジェクトで発生します。 コード分析ポリシーで必要な規則に対応する dll が、クライアント コンピューターにインストールされていません。 ポリシーの作成者は、このエラーを修正するで dll を更新する必要があります*C:\Program files \microsoft Visual Studio 8\Team \static Analysis Tools\FxCop\Rules\\* ディレクトリがコンピューターにします。  
  
   **プロジェクト{0}規則の設定がコード分析ポリシーに一致していません。**  
  
   このエラーは、.NET プロジェクトで発生します。 マネージド コード規則の設定が、ポリシーで要求されている厳密さを満たしていません。 このエラーを修正するには、クライアント設定をサーバー側のポリシー要件と同等以上に厳密にします。  
  
   **コード分析は、アクティブな構成では無効です。構成に切り替える{0}プロジェクトをビルドおよび{1}チェックインする前にします。**  
  
   [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] では、アクティブ構成ではコード分析は有効ではありませんが、有効になっているコード分析が少なくとも 1 つあります。  
  
   **プロジェクト内のマネージ バイナリのコード分析を有効にする必要があります{0}プロパティおよびチェックインする前にビルドします。**  
  
   このエラーは、[!INCLUDE[vcprvc](../includes/vcprvc-md.md)] .NET アプリケーションで発生します。 ポリシーでは、マネージド コード分析の実行を要求していますが、クライアント上の現在のプロジェクトでは有効になっていません。  
  
   **プロジェクトでコード分析を有効にする必要があります{0}プロパティおよびチェックインする前にビルドします。**  
  
   このエラーは、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] プロジェクトおよび Web プロジェクトで発生します。 ポリシーでは、マネージド コード分析の実行を要求していますが、クライアント上の現在のプロジェクトでは有効になっていません。  
  
   **プロジェクトで C/C++ コード分析を有効にする必要があります{0}プロパティおよびチェックインする前にビルドします。**  
  
   このエラーは、アンマネージ プロジェクトで発生します。 コード分析ポリシーでは、C/C++ のコード分析の実行を要求していますが、クライアント上の現在のプロジェクトでは有効になっていません。  
  
## <a name="see-also"></a>関連項目  
 [コード分析のアプリケーション エラー](../code-quality/code-analysis-application-errors.md)
