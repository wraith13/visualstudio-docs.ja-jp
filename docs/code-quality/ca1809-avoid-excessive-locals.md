---
title: CA1809:ローカルを使用しすぎないでください
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1809
- AvoidExcessiveLocals
helpviewer_keywords:
- AvoidExcessiveLocals
- CA1809
ms.assetid: 5c81ea43-cb49-448f-980f-a1dd9764043c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d1c2f76258be3b0be6409bffd002fd916883ab2
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921536"
---
# <a name="ca1809-avoid-excessive-locals"></a>CA1809:ローカルを使用しすぎないでください

|||
|-|-|
|TypeName|AvoidExcessiveLocals|
|CheckId|CA1809|
|Category|Microsoft.Performance|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
メンバーに64個を超えるローカル変数が含まれており、その一部がコンパイラによって生成される可能性があります。

## <a name="rule-description"></a>規則の説明
一般的なパフォーマンスの最適化では、メモリ内ではなくプロセッサレジスタに値を格納します。これは、値の*登録*と呼ばれます。 共通言語ランタイムは、enregistration 用に最大64のローカル変数を考慮します。 Enregistered ではない変数はスタックに配置され、操作の前にレジスタに移動する必要があります。 すべてのローカル変数が enregistered を取得できるようにするには、ローカル変数の数を64に制限します。

## <a name="how-to-fix-violations"></a>違反の修正方法
この規則違反を修正するには、64を超えるローカル変数を使用するように実装をリファクターします。

## <a name="when-to-suppress-warnings"></a>警告を非表示にする場合
パフォーマンスが問題にならない場合は、このルールからの警告を抑制するか、ルールを無効にしても安全です。

## <a name="related-rules"></a>関連するルール
[CA1804未使用のローカルの削除](../code-quality/ca1804-remove-unused-locals.md)