---
title: XML ツール
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
f1_keywords:
- vb.xmldesigner
helpviewer_keywords:
- XML [Visual Studio], resources
- Enterprise Templates, XML and
- discovery files, XML
- server controls, XML and
- Web server controls, XML
- XSL
- XML [Visual Studio], data sources
- XML schemas
- XML [Visual Studio], SGML relationship to
- CSS, style sheets for XML
- XML [Visual Studio], .NET Framework classes
- data [Visual Studio], XML
- classes [Visual Studio], XML
- style sheets, for XML
- Web services
- SGML, XML
- XML [Visual Studio]
- datasets [Visual Basic], XML Schemas
- XSD schemas
- XSL, style sheets
- XMLDataDocument class
ms.assetid: 1fd5de47-2d61-4180-9539-c2c4bf9ab768
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 906f08c0020eb288c1bcd318327be18dc8d08ca5
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65695315"
---
# <a name="xml-tools-in-visual-studio"></a>Visual Studio の XML ツール
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

拡張マークアップ言語 (XML) * は、データを記述する形式を提供するマークアップ言語です。 これにより、コンテンツの宣言がより正確になり、複数のプラットフォームをまたいだ検索結果がよりわかりやすくなります。 さらに、XML では、データと表示形式とを切り離すことができます。 たとえば、HTML では、ブラウザーでの太字や斜体によるデータの表示をタグで指定します。XML では、市の名前、気温、気圧などのデータを記述する目的でのみタグを使用します。 XML では、拡張スタイルシート言語 (XSL) やカスケード スタイル シート (CSS) などのスタイル シートを使用して、ブラウザーにデータを表示します。 XML では、データが表示形式と処理から切り離されます。 このため、適用するスタイル シートやアプリケーションを変えることによって、データの表示や処理を思いどおりに行うことができます。

 XML は SGML のサブセットで、Web を通じて送信するために最適化されています。 これは W3C (World Wide Web Consortium) が定義したものです。 この標準化によって、アプリケーションや販売元から独立している統一形式の構造化データを作成できます。

 XML は、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] および [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] の多くの機能の中核となっています。 次のトピック一覧に、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] および [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] で提供される XML 関連のツールと機能を示します。

 詳細については、次を参照してください。、 [XML Developer Center](http://go.microsoft.com/fwlink/?LinkID=100176)、XML 開発者向けの最新のドキュメント、技術情報については、ダウンロード、ニュースグループ、およびその他のリソースを提供します。

## <a name="in-this-section"></a>このセクションの内容
 [XML データを扱う](../xml-tools/working-with-xml-data.md)での方法で XML の役割の処理について説明します[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]します。

 [XSLT のデバッグ](../xml-tools/debugging-xslt.md)Visual Studio デバッガーを使用して、XSLT のデバッグに関するトピックへのリンクを提供します。

## <a name="reference"></a>参照
 [Microsoft.VisualStudio.XmlEditor](http://go.microsoft.com/fwlink/?LinkID=165699)公開、 [XML エディター](http://go.microsoft.com/fwlink/?LinkId=228249)解析ツリーを[System.Xml.Linq](http://go.microsoft.com/fwlink/?LinkId=228250)の任意の XML ドキュメント。

 [XML 標準のリファレンス](https://msdn.microsoft.com/79c78508-c9d0-423a-a00f-672e855de401)XML、ドキュメント型定義 (DTD)、XML スキーマ定義言語 (XSD)、および XSLT などの XML テクノロジに関する情報を提供します。

 <xref:System.Xml?displayProperty=fullName> クラスとその他の要素を構成するについて説明します、<xref:System.Xml>名前空間と、各項目をより詳細な情報へのリンクを提供します。

 <xref:System.Xml.Serialization?displayProperty=fullName> クラスとその他の要素を構成するについて説明します、<xref:System.Xml.Serialization>名前空間の各項目に関する詳細情報へのリンクを提供します。

## <a name="related-sections"></a>関連項目
 [XML ドキュメント オブジェクト モデル (DOM)](https://msdn.microsoft.com/library/b5e52844-4820-47c0-a61d-de2da33e9f54)方法について説明しますが、どの<xref:System.Xml.XmlDocument>とその関連クラスは、W3C ドキュメント オブジェクト モデル (Core) Level 1 およびレベル 2 の名前空間サポート仕様に準拠します。

 [XmlReader による XML の読み取り](https://msdn.microsoft.com/3029834c-a27e-4331-b7aa-711924062182)方法について説明しますが、どのように<xref:System.Xml.XmlReader>XML ストリームを介した XML データに限定、前方参照専用、読み取り専用アクセスを提供します。

 [XmlWriter による XML の書き込み](https://msdn.microsoft.com/ea41f72c-e1d3-4e0a-ab0f-f0eb1c27ab86)方法について説明します、<xref:System.Xml.XmlWriter>限定で提供し、W3C 標準に準拠した XML ドキュメントを作成する XML ストリームを生成する方法を前方参照専用、します。

 [XSLT 変換](https://msdn.microsoft.com/library/202f8820-224c-494f-b61e-cd127eac6e03)方法について説明しますが、どの<xref:System.Xml.Xsl.XslCompiledTransform>クラスは、XSLT 1.0 勧告を実装します。

 [XPath データ モデルを使用して XML データを処理](https://msdn.microsoft.com/library/536c6fce-1453-4654-9c72-bca54d47e081)方法について説明します、<xref:System.Xml.XPath.XPathNavigator>クラスに格納された XML データを処理できる、<xref:System.Xml.XPath.XPathDocument>または<xref:System.Xml.XmlDocument>オブジェクト。 <xref:System.Xml.XPath.XPathNavigator> クラスは XQuery 1.0 および XPath 2.0 のデータ モデルに基づいており、XML データの操作と編集に使用できます。

 [XML スキーマ オブジェクト モデル (SOM)](https://msdn.microsoft.com/library/a897a599-ffd1-43f9-8807-e58c8a7194cd)作成および提供することで、XML スキーマを操作するために使用されるクラスについて説明します、<xref:System.Xml.Schema.XmlSchema>クラスを読み込み、スキーマを編集します。
