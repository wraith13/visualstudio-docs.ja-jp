---
title: VSIX 言語パック スキーマ 2.0 リファレンス |Microsoft Docs
ms.date: 10/26/2017
ms.topic: conceptual
helpviewer_keywords:
- language pack
- localize vsix
- localize package
- localize extension
ms.assetid: 2a2932bc-cdbe-4d32-91fa-a3e0474f9098
ms.author: dagriffe
author: dgriffen
manager: jillfra
ms.workload:
- dagriffe
ms.openlocfilehash: acea36031b98693e1d618986720d9932f76a0a63
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62953102"
---
# <a name="vsix-language-pack-schema-20-reference"></a>VSIX 言語パック スキーマ 2.0 リファレンス

VSIX 言語パックのスキーマは、VSIX パッケージのローカライズされたインストール情報を提供します。 このスキーマのバージョン 2.0 では、要素のローカリゼーションの追加をサポートします。

## <a name="language-pack-schema"></a>言語パックのスキーマ

言語パックのファイルのルート要素は`<PackageLanguagePackManifest>`の属性を持つ`Version`、言語パックの形式のバージョンであります。 この記事で説明を設定して、マニフェストで指定されている言語パックの形式のバージョン 2.0、`Version`属性値を`Version="2.0.0"`します。 ルート要素には、正確に 1 つの子が含まれています。`<Metadata>`要素。

### <a name="packagelanguagepackmanifest-element"></a>PackageLanguagePackManifest 要素

内で、`<PackageLanguagePackManifest>`要素の次の要素が存在する必要があります。

|Title|説明|
|-----------|-----------------|
|`<Metadata>`| ローカライズされたパッケージのすべてのメタデータのコンテナー要素

### <a name="metadata-element"></a>メタデータ要素

内で、`<Metadata>`要素は、次の要素があることができます。

|Title|説明|
|-----------|-----------------|
|`<DisplayName>`|拡張機能のインストールのローカライズされた名前|
|`<Description>`|ローカライズされた拡張機能のインストールの説明|
|`<License>`| ローカライズされた拡張機能のライセンス版へのパス|
|`<MoreInfo>`| 拡張機能のローカライズされた情報へのリンク|
|`<ReleaseNotes>`| パスまたはリリース ノートのローカライズ版へのリンク|
|`<Icon>`| 拡張機能アイコンのローカライズ版へのパス|

### <a name="sample-manifest"></a>サンプル マニフェスト

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageLanguagePackManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <DisplayName>Arbol de Familia</LocalizedName>
    <Description> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</Description>
    <MoreInfo> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
</PackageLanguagePackManifest>
```

## <a name="see-also"></a>関連項目

|Title|説明|
|-----------|-----------------|
|[VSIX パッケージのローカライズ](../extensibility/localizing-vsix-packages.md)|VSIX パッケージのローカライズされたインストールのサポートを提供する方法を示しています。|
|[VSIX 拡張機能スキーマ 2.0 リファレンス](../extensibility/vsix-extension-schema-2-0-reference.md)|VSIX マニフェストの内容を記述する、 *.vsix*展開ファイル。 配置ファイルを使用して Visual Studio 拡張機能をインストールすることができます、**拡張機能と更新** ダイアログ ボックス。|
|[Visual Studio 拡張機能の検索と使用](../ide/finding-and-using-visual-studio-extensions.md)|使用する方法を示しています、**拡張機能と更新**をインストール、削除、アクティブ化、および拡張機能を非アクティブ化 ダイアログ ボックス。|