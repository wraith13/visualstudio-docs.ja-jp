---
title: DA0029:サポートされていない CLR バージョンです | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.29
- vs.performance.rules.DA0029
helpviewer_keywords:
- vs.performance.29
- vs.performance.DA0029
- vs.performance.rules.DA0029
ms.assetid: 76247259-c6f3-44c4-b3f9-d8dac16b5e0d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a3855b8975684b088b2838a866db36e6ec19e665
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62936293"
---
# <a name="da0029-unsupported-clr-version"></a>DA0029:サポートされていない CLR バージョンです

|||
|-|-|
|規則 ID|DA0029|
|カテゴリ|プロファイリング ツールの使用|
|プロファイル方法|コマンド ラインからのプロファイリング|
|メッセージ|収集時に、サポートされていない CLR バージョンが検出されました。 マネージド シンボルが正しく解決されない可能性があります。|
|規則の種類|情報。|

## <a name="cause"></a>原因
 プロファイリング ツールでサポートされていない [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)] を使用するアプリケーションをプロファイリングしようとしています。

## <a name="rule-description"></a>規則の説明
 アプリケーションで実行されているマネージド コードのシンボルをプロファイリング ツールが解決できないため、この警告が発生します。 プロファイリング ツールは、[!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)] を実行しているアプリケーションのマネージド コード シンボルを解決できません。

## <a name="how-to-fix-violations"></a>違反の修正方法
 なし。