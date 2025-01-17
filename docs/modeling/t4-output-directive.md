---
title: T4 出力ディレクティブ
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dfbe77f5b6e2bbda6a51d392c4dd16b079100e81
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62856245"
---
# <a name="t4-output-directive"></a>T4 出力ディレクティブ

Visual Studio のテキスト テンプレートで、`output`ディレクティブを使用して、ファイル名拡張子と変換後のファイルのエンコードを定義します。

 たとえば、Visual Studio プロジェクトに **MyTemplate.tt** という名前のテンプレート ファイルが含まれていて、次のディレクティブが含まれているとします。

 `<#@output extension=".cs"#>`

 Visual Studio は **MyTemplate.cs** という名前のファイルを生成します。

 `output` ディレクティブは、ランタイム (前処理済み) のテキスト テンプレートには必要ありません。 その代わりに、アプリケーションは `TextTransform()` を呼び出して、生成済みの文字列を取得します。 詳細については、次を参照してください。 [T4 テキスト テンプレートを使用した実行時テキスト生成](../modeling/run-time-text-generation-with-t4-text-templates.md)

## <a name="using-the-output-directive"></a>出力ディレクティブの使用

```
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>
```

 各テキスト テンプレートには複数の `output` ディレクティブを含めてはいけません。

## <a name="extension-attribute"></a>extension 属性
 生成されたテキスト出力ファイルのファイル名の拡張子を指定します。

 既定値は **.cs** です。

 例: `<#@ output extension=".txt" #>`

 `<#@ output extension=".htm" #>`

 `<#@ output extension=".cs" #>`

 `<#@ output extension=".vb" #>`

 許容される値:任意の有効なファイル名の拡張子。

## <a name="encoding-attribute"></a>エンコーディング属性
 出力ファイルが生成されるときに使用するエンコードを指定します。 次に例を示します。

 `<#@ output encoding="utf-8"#>`

 既定値は、テキスト テンプレート ファイルが使用するエンコードです。

 許容される値: `us-ascii`

 `utf-16BE`

 `utf-16`

 `utf-8`

 `utf-7`

 `utf-32`

 `0` (システムの既定値)

 一般に、<xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName> が返す任意のエンコードの WebName 文字列または CodePage 数値を使用できます。