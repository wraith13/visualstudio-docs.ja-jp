---
title: CA1308:文字列を大文字に標準化します
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1308
- NormalizeStringsToUppercase
helpviewer_keywords:
- NormalizeStringsToUppercase
- CA1308
ms.assetid: 7e9a7457-3f93-4938-ac6f-1389fba8d9cc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 06fe8d4fbd4def14bfb8a24f4f211a121c809930
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922240"
---
# <a name="ca1308-normalize-strings-to-uppercase"></a>CA1308:文字列を大文字に標準化します

|||
|-|-|
|TypeName|NormalizeStringsToUppercase|
|CheckId|CA1308|
|Category|Microsoft のグローバリゼーション|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
操作は、文字列を小文字に正規化します。

## <a name="rule-description"></a>規則の説明
文字列は大文字に正規化する必要があります。 小文字に変換された小さな文字グループは、ラウンドトリップを行うことができません。 ラウンドトリップを行うには、あるロケールから文字データを表す別のロケールに文字を変換し、変換された文字から元の文字を正確に取得することを意味します。

## <a name="how-to-fix-violations"></a>違反の修正方法
文字列を小文字に変換する操作を変更して、文字列を大文字に変換します。 たとえば、`String.ToLower(CultureInfo.InvariantCulture)` を `String.ToUpper(CultureInfo.InvariantCulture)` に変更します。

## <a name="when-to-suppress-warnings"></a>警告を非表示にする場合
結果に基づいてセキュリティを決定しない場合 (たとえば、UI に表示する場合)、警告メッセージを抑制するのは安全です。

## <a name="see-also"></a>関連項目
[グローバリゼーションに関する警告](../code-quality/globalization-warnings.md)