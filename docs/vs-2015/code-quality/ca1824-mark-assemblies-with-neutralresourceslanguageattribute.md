---
title: CA1824:アセンブリを NeutralResourcesLanguageAttribute にマーク |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1824
- MarkAssembliesWithNeutralResourcesLanguage
helpviewer_keywords:
- MarkAssembliesWithNeutralResourcesLanguage
- CA1824
ms.assetid: 10e97f8a-aa6e-47aa-b253-1e5d3a295d82
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 795d48b96392057a3f96cf3a67f3c49de8aee9b9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203088"
---
# <a name="ca1824-mark-assemblies-with-neutralresourceslanguageattribute"></a>CA1824:アセンブリを NeutralResourcesLanguageAttribute に設定します
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkAssembliesWithNeutralResourcesLanguage|
|CheckId|CA1824|
|Category|Microsoft.Performance|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 アセンブリに含まれる、 **ResX**-ベースのリソースがありません、<xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName>を適用します。

## <a name="rule-description"></a>規則の説明
 **NeutralResourcesLanguage**属性の通知、 **ResourceManager**のアセンブリのニュートラル カルチャのリソースを表示するために使用された言語です。 ニュートラル リソース言語と同じカルチャのリソースを探すとき、 **ResourceManager**メイン アセンブリに配置されているリソースを自動的に使用されます。 これを現在のスレッドの現在のユーザー インターフェイス カルチャを持つサテライト アセンブリを検索する代わりにします。 これにより、読み込んだ最初のリソースに対する検索のパフォーマンスが向上し、ワーキング セットを縮小できます。

## <a name="fixing-violations"></a>違反の修正
 この規則違反を修正するには、アセンブリに属性を追加し、ニュートラル カルチャのリソースの言語を指定します。

## <a name="specifying-the-language"></a>言語を指定します。

#### <a name="to-specify-the-language-of-the-resource-of-the-neutral-culture"></a>ニュートラル カルチャのリソースの言語を指定するには

1. **ソリューション エクスプ ローラー**、プロジェクトを右クリックし、クリックして**プロパティ**します。

2. 左側のナビゲーション バーから選択**アプリケーション**、 をクリックし、**アセンブリ情報**します。

3. **アセンブリ情報** ダイアログ ボックスから言語を選択、**ニュートラル言語**ドロップダウン リスト。

4. **[OK]** をクリックします。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告を抑制することはできます。 ただし、起動時のパフォーマンスが低下する可能性があります。
