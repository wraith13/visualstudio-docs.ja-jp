---
title: CA1412:ComSource インターフェイスを IDispatch として設定します
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MarkComSourceInterfacesAsIDispatch
- CA1412
helpviewer_keywords:
- CA1412
- MarkComSourceInterfacesAsIDispatch
ms.assetid: 131a7563-0410-443c-a8f5-52104250cfb4
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e0a7214ce37aa48d69b9261d686960fa0a4c308c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546350"
---
# <a name="ca1412-mark-comsource-interfaces-as-idispatch"></a>CA1412:ComSource インターフェイスを IDispatch として設定します

|||
|-|-|
|TypeName|MarkComSourceInterfacesAsIDispatch|
|CheckId|CA1412|
|カテゴリ|Microsoft.Interoperability|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因

型が付いて、<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>属性と少なくとも 1 つの指定したインターフェイスでマークされていない、<xref:System.Runtime.InteropServices.InterfaceTypeAttribute>属性に設定、`InterfaceIsDispatch`値。

## <a name="rule-description"></a>規則の説明

<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> クラスは、コンポーネント オブジェクト モデル (COM) クライアントに公開するイベント インターフェイスを識別するために使用されます。 これらのインターフェイスとして公開する必要があります`InterfaceIsIDispatch`イベント通知を受信する Visual Basic 6 COM クライアントを有効にします。 インターフェイスが設定されていない場合、既定で、<xref:System.Runtime.InteropServices.InterfaceTypeAttribute>属性、デュアル インターフェイスとして公開されます。

## <a name="how-to-fix-violations"></a>違反の修正方法

この規則違反を修正するのには、追加または変更、<xref:System.Runtime.InteropServices.InterfaceTypeAttribute>属性で指定されたすべてのインターフェイスの InterfaceIsIDispatch にその値が設定されるように、<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>属性。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

この規則による警告は抑制しないでください。

## <a name="example"></a>例

次の例では、規則に違反する場所、インターフェイスの 1 つのクラスを示します。

[!code-csharp[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/CSharp/ca1412-mark-comsource-interfaces-as-idispatch_1.cs)]
[!code-vb[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/VisualBasic/ca1412-mark-comsource-interfaces-as-idispatch_1.vb)]

## <a name="related-rules"></a>関連するルール

[CA 1408:AutoDual ClassInterfaceType を使用します。](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>関連項目

- [アンマネージ コードとの相互運用](/dotnet/framework/interop/index)