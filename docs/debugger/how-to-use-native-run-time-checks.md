---
title: '方法: ネイティブ ランタイム チェックの使用 |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- c.runtime.errorchecks
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- /RTC compiler option [C++], /O compiler option
- run-time checks, native
- stack, pointer corruption
- stack pointers, corruption
- /O compiler option, /RTC option
- run-time errors, error checks
- O compiler option, /RTC option
- debugger, runtime errors
- variables [debugger], loss of data
- runtime_checks pragma
- variables [debugger], catching dependencies on uninitialized local variables
- run-time errors, debugging
- debugger, native run-time checks
- optimized build option
- RTC compiler option, /O compiler option
- native run-time checks
- run-time checks
- debugging arrays
- stack pointers
- arrays [Visual Studio], debugging
ms.assetid: dc7b2f1e-5ff6-42e0-89b3-dc9dead83ee1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 4ccf0fea80ddfcc7db0921512391f5063a8f2dad
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62846971"
---
# <a name="how-to-use-native-run-time-checks"></a>方法: ネイティブ ランタイム チェックを使用する
Visual C++ では、ネイティブ [runtime_checks](/cpp/preprocessor/runtime-checks) を使用して、次のような一般的なランタイム エラーをキャッチできます。

- スタック ポインターの破損

- ローカル配列のオーバーラン

- スタックの破損

- 初期化されていないローカル変数への依存性

- 短い変数への代入によるデータの消失

  最適化された ( **/RTC** ) ビルドで **/O**を使用すると、コンパイラ エラーが発生します。 `runtime_checks` プラグマを最適化されたビルドに使用しても効果はありません。

  ランタイム チェックが有効になっている状態のプログラムをデバッグすると、既定の動作では、ランタイム エラーの発生時にプログラムが停止し、デバッガーが起動されます。 この既定の動作は、任意のランタイム チェックで変更できます。 詳細については、次を参照してください。[デバッガーでの例外を管理する](../debugger/managing-exceptions-with-the-debugger.md)します。

  次の手順で、デバッグ ビルドでネイティブ ランタイム チェックを有効にする方法と、ネイティブ ランタイム チェックの動作を変更する方法を説明します。

  このセクションのその他のトピックでは、次の内容について説明します。

- [C ランタイム ライブラリによるネイティブ ランタイム チェックのカスタマイズ](../debugger/native-run-time-checks-customization.md)

- [C ランタイム ライブラリなしのランタイム チェックの使用方法](../debugger/using-run-time-checks-without-the-c-run-time-library.md)

### <a name="to-enable-native-run-time-checks-in-a-debug-build"></a>デバッグ ビルドでネイティブ ランタイム チェックを有効にするには

- **/RTC** オプションを使用して、C ランタイム ライブラリのデバッグ バージョン (/MDd など) とリンクします。

### <a name="to-modify-native-run-time-check-behavior"></a>ネイティブ ランタイム チェックの動作を変更するには

- `runtime_checks` プラグマを使用します。

## <a name="see-also"></a>関連項目
- [Visual Studio でのデバッグ](../debugger/index.md)
- [デバッガーでのはじめに](../debugger/debugger-feature-tour.md)
- [runtime_checks](/cpp/preprocessor/runtime-checks)
- [ランタイム エラー チェック](/cpp/c-runtime-library/run-time-error-checking)