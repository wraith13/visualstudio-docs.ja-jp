---
title: CA1308:文字列を大文字に正規化 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1308
- NormalizeStringsToUppercase
helpviewer_keywords:
- NormalizeStringsToUppercase
- CA1308
ms.assetid: 7e9a7457-3f93-4938-ac6f-1389fba8d9cc
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8385839ce7029ef0676225fd443582ba750b618b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200385"
---
# <a name="ca1308-normalize-strings-to-uppercase"></a>CA1308:文字列を大文字に標準化します
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|NormalizeStringsToUppercase|
|CheckId|CA1308|
|Category|Microsoft.Globalization|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 操作は、小文字の文字列を正規化します。

## <a name="rule-description"></a>規則の説明
 文字列は大文字に正規化する必要があります。 少数の文字を小文字に変換されますが、ラウンド トリップを行うことはできません。 ラウンド トリップを行うには、文字変換 1 つのロケールから、文字データを異なる方法で表す別のロケールに正確にするための手段は、変換後の文字から、元の文字を取得します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 文字列を変換できるように、文字列を小文字に変換する操作を変更する代わりに大文字にします。 たとえば、`String.ToLower(CultureInfo.InvariantCulture)` を `String.ToUpper(CultureInfo.InvariantCulture)` に変更します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 (たとえば、UI に表示している場合) の結果に基づいてセキュリティに関する決定を行わない場合に警告メッセージを安全になります。

## <a name="see-also"></a>関連項目
 [グローバリゼーションに関する警告](../code-quality/globalization-warnings.md)
