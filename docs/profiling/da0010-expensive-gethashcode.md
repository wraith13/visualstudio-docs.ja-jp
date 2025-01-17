---
title: DA0010:GetHashCode の負荷が高くなっています | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAExpensiveGetHashCode
- vs.performance.DA0010
- vs.performance.rules.DA0010
- vs.performance.10
ms.assetid: 3987e21a-5b4f-45e4-8a33-6b3f0a472c08
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2a1ddeb2b12d592c93bb0e5b88ba76c1b01c3c3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62936554"
---
# <a name="da0010-expensive-gethashcode"></a>DA0010:GetHashCode の負荷が高くなっています

|||
|-|-|
|規則 ID|DA0010|
|カテゴリ|.NET Framework の使用|
|プロファイル方法|サンプリング<br /><br /> .NET メモリ|
|メッセージ|GetHashCode 関数の負荷を抑える必要があります。メモリを割り当てることはできません。 可能な場合は、ハッシュ コード関数の複雑さを軽減してください。|
|メッセージの種類|警告|

## <a name="cause"></a>原因
 型の GetHashCode メソッドの呼び出しがプロファイリング データの大きな割合を占めているか、またはそのメソッドがメモリを割り当てています。

## <a name="rule-description"></a>規則の説明
 ハッシュは、大きなコレクションの中から特定の項目を簡単に見つけるための手法です。 ハッシュ テーブルは非常に大きくなることがあり、高いアクセス率に対応しなければなりません。そのため、ハッシュ テーブルは効率的にする必要があります。 この要件が意味するところは、.NET Framework の GetHashCode メソッドでメモリを割り当ててはいけないということです。 メモリを割り当てるとガベージ コレクターの負荷が増し、割り当て要求の結果としてガベージ コレクションを実行しなければならなくなると、メソッドに遅延が発生する可能性があります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 メソッドの複雑さを軽減してください。