---
title: エスケープ シーケンスを使用して、テンプレートからテンプレートを生成するには
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, generating templates from templates
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7872b9bf55ad5d712ac01edf10c4b9df2a82feea
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/28/2019
ms.locfileid: "66263684"
---
# <a name="how-to-generate-templates-from-templates-by-using-escape-sequences"></a>方法: エスケープ シーケンスを使用してテンプレートからテンプレートを生成する
別のテキスト テンプレートを作成するテキスト出力として生成されたテキスト テンプレートを作成することができます。 これを行うには、テキスト テンプレートのタグを区切るためにエスケープ シーケンスを使用する必要があります。 エスケープ シーケンスを使用しない場合、生成されたテキスト テンプレートが定義済みの意味になります。 テキスト テンプレートでのエスケープ シーケンスの使用の詳細については、次を参照してください。[テキスト テンプレートでのエスケープ シーケンスの使用](../modeling/using-escape-sequences-in-text-templates.md)

### <a name="to-generate-a-text-template-from-within-a-text-template"></a>テキスト テンプレート内でテキスト テンプレートを生成するには

- 別のテキスト テンプレート ファイル内で、ディレクティブ、ステートメント、式、クラス機能といった必要なマークアップ タグをテキスト テンプレート内で作成するためにエスケープ文字として、バックスラッシュ (\\) を使用します。

    ```
    \<#@ directive \#>
    \<# statement \#>
    \<#= expression \#>
    \<#+ classfeature \#>
    ```

## <a name="example"></a>例
 次の例では、エスケープ文字を使用して、テキスト テンプレートからテキスト テンプレートを生成します。 `output` ディレクティブは、変換先ファイルのテキスト テンプレート ファイルの種類 (.tt) を設定します。

```csharp
\<#@ output extension=".tt" \#>
\<#@ assembly name="System.Xml.dll" \#>
\<#@ import namespace="System.Xml" \#>
\<#
XmlDocument xDoc = new XmlDocument();
//System.Diagnostics.Debugger.Break();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes != null)
    {
       foreach (XmlAttribute attr in attributes)
       {\#>
           \<#= attr.Name \#>
       \<#}
     }
\#>
```

 生成されたテキスト出力は、テキスト テンプレートです。

```
<#@ output extension=".tt" #>
<#@ assembly name="System.Xml.dll" #>
<#@ import namespace="System.Xml" #>
<#
XmlDocument xDoc = new XmlDocument();
//System.Diagnostics.Debugger.Break();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes != null)
    {
       foreach (XmlAttribute attr in attributes)
       {#>
           <#= attr.Name #>
       <#}
     }
#>
```