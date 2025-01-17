---
title: CA1806:メソッドの結果を無視しない
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1806
- DoNotIgnoreMethodResults
helpviewer_keywords:
- CA1806
- DoNotIgnoreMethodResults
ms.assetid: fd805687-0817-481e-804e-b62cfb3b1076
author: gewarren
ms.author: gewarren
dev_langs:
- CPP
- CSharp
- VB
manager: jillfra
ms.openlocfilehash: 2e68fb6b4c40c165a09ae2631a2ad0a64bf52fbc
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921553"
---
# <a name="ca1806-do-not-ignore-method-results"></a>CA1806:メソッドの結果を無視しない

|||
|-|-|
|TypeName|DoNotIgnoreMethodResults|
|CheckId|CA1806|
|Category|Microsoft.Usage|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因

この警告には、次のようないくつかの原因が考えられます。

- 新しいオブジェクトが作成されましたが、使用されませんでした。

- 新しい文字列を作成して返すメソッドが呼び出され、新しい文字列が使用されることはありません。

- 使用されていない HRESULT またはエラーコードを返す COM メソッドまたは P/Invoke メソッド。 規則の説明

不要なオブジェクトの作成と、使用されていないオブジェクトの関連するガベージコレクションにより、パフォーマンスが低下します。

文字列は不変であり、ToUpper などのメソッドは、呼び出し元のメソッド内の文字列のインスタンスを変更するのではなく、文字列の新しいインスタンスを返します。

HRESULT またはエラーコードを無視すると、エラー状態やリソース不足の状態で予期しない動作が発生する可能性があります。

## <a name="how-to-fix-violations"></a>違反の修正方法
メソッド A が使用されていない B オブジェクトの新しいインスタンスを作成する場合は、インスタンスを引数として別のメソッドに渡すか、インスタンスを変数に代入します。 オブジェクトの作成が不要な場合は、それを削除します。-または-

メソッド A がメソッド B を呼び出しますが、メソッド B が返す新しい文字列インスタンスを使用しない場合。 インスタンスを引数として別のメソッドに渡し、インスタンスを変数に代入します。 不要な場合は、呼び出しを削除します。

 \- または -

メソッド A がメソッド B を呼び出しても、メソッドが返す HRESULT またはエラーコードを使用しない場合。 条件付きステートメントで結果を使用するか、変数に結果を代入するか、または別のメソッドに引数として渡します。

## <a name="when-to-suppress-warnings"></a>警告を非表示にする場合
オブジェクトを作成する操作によって何らかの目的がある場合を除き、この規則による警告を抑制しないでください。

## <a name="example"></a>例
次の例は、文字列 Trim の呼び出し結果を無視するクラスを示しています。

[!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_1.cs)]
[!code-vb[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_1.vb)]
[!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_1.cpp)]

## <a name="example"></a>例
次の例では、前の違反を修正しました。この結果は、呼び出された変数に代入して戻します。

[!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_2.cs)]
[!code-vb[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_2.vb)]
[!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_2.cpp)]

## <a name="example"></a>例
次の例は、作成したオブジェクトを使用しないメソッドを示しています。

> [!NOTE]
> Visual Basic でこの違反を再現することはできません。

[!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_3.cpp)]
[!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_3.cs)]

## <a name="example"></a>例
次の例では、オブジェクトの不要な作成を削除することによって、以前の違反を修正します。

[!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_4.cs)]
[!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_4.cpp)]

<!-- Examples don't exist for the below... -->
<!--
## Example
The following example shows a method that ignores the error code that the native method GetShortPathName returns.

## Example
The following example fixes the previous violation by checking the error code and throwing an exception when the call fails.
-->