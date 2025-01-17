---
title: CA2006:SafeHandle を使用して、ネイティブ リソースをカプセル化する |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2006
- UseSafeHandleToEncapsulateNativeResources
helpviewer_keywords:
- UseSafeHandleToEncapsulateNativeResources
- CA2006
ms.assetid: a71950bd-bcc1-463d-b1f2-5233bc451456
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: dcf385263eba5a6012097f43b49e7a75166bad42
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "68154403"
---
# <a name="ca2006-use-safehandle-to-encapsulate-native-resources"></a>CA2006:SafeHandle を使用して、ネイティブ リソースを要約します
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseSafeHandleToEncapsulateNativeResources|
|CheckId|CA2006|
|Category|Microsoft.Reliability|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 マネージ コードが<xref:System.IntPtr>ネイティブ リソースにアクセスします。

## <a name="rule-description"></a>規則の説明
 使用`IntPtr`マネージ コードで潜在的なセキュリティと信頼性に問題がある可能性があります。 すべての使用`IntPtr`決定を確認する必要があるかどうかの使用、 <xref:System.Runtime.InteropServices.SafeHandle> 、その場所に同様のテクノロジが必要です。 問題が発生する場合、`IntPtr`メモリ、ファイル ハンドル、またはマネージ コードが独自と見なされること、ソケットなどのいくつかのネイティブ リソースを表します。 マネージ コードがリソースを所有している場合は、それに関連付けられているネイティブ リソースも解放ように障害には、リソース リークが発生するために必要があります。

 このようなシナリオでは、セキュリティや信頼性の問題も存在するマルチ スレッド アクセスが許可されている場合、`IntPtr`で表されるリソースを解放する方法と、`IntPtr`提供されます。 これらの問題、`IntPtr`でリソースの解放中に、別のスレッドで同時に、リソースの使用がされている値。 競合状態の 1 つのスレッドが読み取りまたは間違ったリソースに関連付けられているデータを書き込む場所がある可能性があります。 たとえば、次の型としての OS ハンドルに格納、`IntPtr`と、ユーザーの両方を呼び出す**閉じる**と他のメソッドと同期の仕掛けなしを同時に、そのハンドルを使用して、コードがハンドルのリサイクル問題があります。

 このハンドルのリサイクル問題には、データが破損したり、多くの場合、セキュリティの脆弱性可能性があります。 `SafeHandle` その兄弟クラス<xref:System.Runtime.InteropServices.CriticalHandle>このようなスレッド処理の問題を回避するために、リソースへのネイティブ ハンドルをカプセル化するためのメカニズムを提供します。 また、使用することができます`SafeHandle`とその兄弟クラス`CriticalHandle`他のスレッド問題については、たとえば、ネイティブ メソッドの呼び出し経由でネイティブのハンドルのコピーが含まれている管理対象のオブジェクトの有効期間を慎重に制御します。 このような状況への呼び出しを削除することが多くの場合、`GC.KeepAlive`します。 使用する場合に発生するパフォーマンス オーバーヘッド ユーザー`SafeHandle`とほど、 `CriticalHandle`、慎重に設計を頻繁に削減できます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 変換`IntPtr`の使用状況を`SafeHandle`ネイティブ リソースへのアクセスを安全に管理します。 参照してください、<xref:System.Runtime.InteropServices.SafeHandle>例については、リファレンス トピック。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この警告を抑制する必要があります。

## <a name="see-also"></a>関連項目
 <xref:System.IDisposable>
