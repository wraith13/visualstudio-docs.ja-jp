---
title: CA1601:電源状態の変更を妨げるタイマーを使用しません |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
helpviewer_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
ms.assetid: b8028c92-0696-4c54-9773-0028f29bda9a
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 228c95a8f0c3e1b9b1643e529e78f52f1e059bc5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "68189248"
---
# <a name="ca1601-do-not-use-timers-that-prevent-power-state-changes"></a>CA1601:電源の状態の変更を妨げるタイマーを使用しません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotUseTimersThatPreventPowerStateChanges|
|CheckId|CA1601|
|Category|Microsoft.Mobility|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 タイマーが、設定を 1 秒あたりの 1 つ以上の時間間隔。

## <a name="rule-description"></a>規則の説明
 ポーリング 1 よりも頻繁に発生するタイマーを使用したり秒ごとに 1 回よりもより多くの場合、1 秒あたりの時間。 定期的な動作の頻度が高くなると、CPU のビジー状態が続き、ディスプレイとハード ディスクをオフにする省電力アイドル タイマーに影響を与えます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 1 秒あたりの 1 つ未満の時間が発生するタイマーの間隔を設定します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 1 秒あたりの 1 つ以上の時間のタイマーを発生させることが必要ですし、モビリティに関する考慮事項を無視しても場合にのみ、このルールを抑制する必要があります。
