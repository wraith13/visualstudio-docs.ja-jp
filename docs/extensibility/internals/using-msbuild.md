---
title: MSBuild の使用 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, compiling with MSBuild
- MSBuild, extensibility
- packages, compiling with MSBuild
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab089a7a37acb377a043ec2c3a4db2c6538e6312
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344711"
---
# <a name="using-msbuild"></a>MSBuild の使用
MSBuild では、ビルド、ビルド タスク、および構成をビルドするプロジェクト アイテムを完全に記述するプロジェクト ファイルを作成するために適切に定義された、拡張性の高い XML 形式を提供します。

## <a name="general-msbuild-considerations"></a>MSBuild の一般的な考慮事項
 MSBuild プロジェクト ファイル、たとえば、 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] .csproj および[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]、.vbproj ファイルには、ビルド時に使用されますが、デザイン時に使用されるデータを含めることができますもデータが含まれています。 などの MSBuild のプリミティブを使用して、ビルド時のデータが格納された[Item 要素 (MSBuild)](../../msbuild/item-element-msbuild.md)と[Property 要素 (MSBuild)](../../msbuild/property-element-msbuild.md)します。 プロジェクトの種類との関連プロジェクト サブタイプに固有のデータである、デザイン時のデータは、自由形式の XML 用に予約に格納されます。

 MSBuild では、構成オブジェクトのネイティブ サポートはありませんが、構成に固有のデータを指定するための条件付き属性は提供します。 例:

```xml
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>
```

 条件付き属性の詳細については、次を参照してください。[条件構造](../../msbuild/msbuild-conditional-constructs.md)します。

### <a name="extending-msbuild-for-your-project-type"></a>種類のプロジェクトの MSBuild の拡張
 MSBuild のインターフェイスと Api は、の将来のバージョンで変更される可能性は[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。 そのため、変更からシールドを提供するために、マネージ パッケージ フレームワーク (MPF) クラスを使用することをお勧めします。

 Managed Package Framework (MPFProj) プロジェクトを作成して、新しいプロジェクト システムを管理するためのヘルパー クラスを提供します。 コードとコンパイル」の手順に従って、ソースを検索できる[- Visual Studio 2013 のプロジェクトの MPF](https://github.com/tunnelvisionlabs/MPFProj10)します。

 プロジェクトに固有の MPF クラスは次のとおりです。

|クラス|実装|
|-----------|--------------------|
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|

 `Microsoft.VisualStudio.Package.ProjectElement` クラスは、MSBuild 項目用のラッパーです。

#### <a name="single-file-generators-vs-msbuild-tasks"></a>単一ファイル ジェネレーターの vs します。MSBuild タスク
 単一ファイル ジェネレーターは、デザイン時のみにアクセスできるが、デザイン時およびビルド時に MSBuild タスクを使用できます。 最大限の柔軟性の変換し、コードを生成する MSBuild タスクを使用してそのため。 詳細については、次を参照してください。[カスタム ツール](../../extensibility/internals/custom-tools.md)します。

## <a name="see-also"></a>関連項目
- [MSBuild リファレンス](../../msbuild/msbuild-reference.md)
- [MSBuild](../../msbuild/msbuild.md)
- [カスタム ツール](../../extensibility/internals/custom-tools.md)