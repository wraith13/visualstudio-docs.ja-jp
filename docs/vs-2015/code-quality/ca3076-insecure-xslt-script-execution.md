---
title: CA3076:安全ではない XSLT スクリプトの実行 |Microsoft Docs
ms.date: 11/15/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 53cb7a46-c564-488f-bc51-0e210a7853c9
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0a6b1efa5b5ee84092531a67421d03583afc3578
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65680718"
---
# <a name="ca3076-insecure-xslt-script-execution"></a>CA3076:安全ではない XSLT スクリプトの実行
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|InsecureXSLTScriptExecution|
|CheckId|CA3076|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 .NET アプリケーションで [XSLT (Extensible Stylesheet Language Transformation)](https://support.microsoft.com/kb/313997) を安全ではない方法で実行すると、攻撃者に機密情報を漏えいする可能性のある、 [信頼されていない URI 参照がプロセッサにより解決される](https://msdn.microsoft.com/ba3e4d4f-1ee7-4226-a51a-78a1f1b5bd8a) おそれがあります。そのことは、サービス拒否攻撃やクロスサイト攻撃につながります。

## <a name="rule-description"></a>規則の説明
 [XSLT](https://msdn.microsoft.com/6377ce5f-3c45-42a6-b7a9-ec8da588b60c) は、XML データを変換するための W3C (World Wide Web Consortium) 規格です。 通常 XSLT は、XML データを他の形式 (HTML、固定長のテキスト、コンマ区切りのテキスト、または別の XML 形式など) に変換するために、スタイル シートを書き込むのに使用します。 既定では禁止になっていますが、プロジェクトに応じて有効にもできます。

 攻撃にさらされないように、このルールはたびにトリガー、XslCompiledTransform します。<xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> インスタンスを安全でない組み合わせを受け取る<xref:System.Xml.Xsl.XsltSettings>と<xref:System.Xml.XmlResolver>、悪意のあるスクリプトの処理をことができます。

## <a name="how-to-fix-violations"></a>違反の修正方法

- 安全ではない XsltSettings 引数を xsltsettings に置き換えます。<xref:System.Xml.Xsl.XsltSettings.Default%2A> または、インスタンスが、ドキュメントの関数とスクリプトの実行を無効な。

- <xref:System.Xml.XmlResolver> 引数を null または <xref:System.Xml.XmlSecureResolver> インスタンスに置き換えます。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 入力が信頼できるソースからのものとわかっているのでない限り、この警告からのルールを抑制しないでください。

## <a name="pseudo-code-examples"></a>疑似コードの例

### <a name="violation"></a>違反

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
         void TestMethod()
        {
             XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
             var settings = XsltSettings.TrustedXslt;
             var resolver = new XmlUrlResolver();
             xslCompiledTransform.Load("testStylesheet", settings, resolver); // warn
        }
    }
} 
```

### <a name="solution"></a>ソリューション

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
        void TestMethod()
        {
            XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
            var settings = XsltSettings.Default;
            var resolver = new XmlUrlResolver();
            xslCompiledTransform.Load("testStylesheet", settings, resolver);
        }
    }
}
```

### <a name="violation"></a>違反

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
        private static void TestMethod(XsltSettings settings)
        {
            try
            {
                XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
                var resolver = new XmlUrlResolver();
                xslCompiledTransform.Load("testStylesheet", settings, resolver); // warn
            }
            catch { throw; }
            finally { }
        }
    }
}
```

### <a name="solution"></a>ソリューション

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
        private static void TestMethod(XsltSettings settings)
        {
            try
            {
                XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
                settings.EnableDocumentFunction = false;
                settings.EnableScript = false;
                var resolver = new XmlUrlResolver();
                xslCompiledTransform.Load("testStylesheet", settings, resolver);
            }
            catch { throw; }
            finally { }
        }
    }
}
```
