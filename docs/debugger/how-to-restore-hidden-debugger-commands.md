---
title: '方法: 非表示のデバッガー コマンドを復元 |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, restoring commands
- debugging [Visual Studio], restoring commands
- commands, debugger
ms.assetid: 76ac9b77-f536-43b5-a9fc-984854b1c566
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7766f83eef6205ce445ed892ffaf5861a0dcabbb
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63387538"
---
# <a name="how-to-restore-hidden-debugger-commands"></a>方法: 非表示のデバッガー コマンドを復元する
Visual Studio をセット アップするときに、既定の IDE 設定で主要なプログラム言語を選択するように指示されます。 言語によっては、既定の IDE 設定で一部のデバッガー コマンドが非表示のことがあります。

 既定の IDE 設定で非表示のデバッガー機能を使用するには、次の手順でコマンドをメニューに表示します。

### <a name="to-restore-hidden-debugger-commands"></a>非表示のデバッガー コマンドを復元するには

1. プロジェクトが開いている状態で、**[ツール]** メニューの **[ユーザー設定]** をクリックします。

2. **[ユーザー設定]** ダイアログ ボックスの **[コマンド]** タブをクリックします。

3. **メニュー バー**のドロップダウンで、復元されたコマンドを含める **[デバッグ]** メニューを選択します。

4. **[コマンドの追加]** をクリックします。

5. **[コマンドの追加]** ボックスで、追加するコマンドを選択して、**[OK]** をクリックします。

6. 前の手順を繰り返して、ブレークポイントを追加します。

7. メニューにコマンドを追加し終わったら、**[閉じる]** をクリックします。

    > [!WARNING]
    > メニュー項目によっては、デバッガーが特殊なモード (実行モードまたは中断モード) のときにのみ表示されます。 そのため、この手順でコマンドを追加しても、すぐに表示されないことがあります。

## <a name="restoring-commands-not-available-from-the-customize-dialog-box"></a>[ユーザー設定] ダイアログ ボックスから使用できないコマンドを復元する
 コマンドによっては、特に階層メニューに含まれる場合、**[ユーザー設定]** ダイアログ ボックスから復元できないことがあります。 このようなコマンドを復元するには、IDE 設定の新しいコレクションをインポートする必要があります。

#### <a name="to-import-new-ide-settings"></a>新しい IDE 設定をインポートするには

1. **[ツール]** メニューの **[設定のインポートとエクスポート]** を選択します。

2. **[設定のインポートとエクスポート ウィザードへようこそ]** ページの **[選択された環境設定をインポート]** をクリックし、**[次へ]** をクリックします。

3. **[現在の設定の保存]** ページでご利用の既存の設定を保存するかどうかを選択し、**[次へ]** をクリックします。

4. **[インポートする設定コレクションの選択]** ページの **[既定の設定]** フォルダーで、使用するコマンドが含まれる開発設定のコレクションを選択します。 選択するコレクションがわからない場合、**[全般的な開発設定]** または **[Visual C++ 開発設定]** を確認してください。ほとんどのデバッガー コマンドを表示されます。

5. **[次へ]** をクリックします。

6. **[インポートする設定の選択]** ページの **[オプション]** で、**[デバッグ]** がオンになっていることを確認します。 この設定をインポートしないのであれば、他のチェック ボックスはオフにします。

7. **[完了]** をクリックします。

8. **[インポートの完了]** ページの **[詳細]** で、ご利用の設定のリセットに関するエラーを確認します。

9. **[閉じる]** をクリックします。

## <a name="see-also"></a>関連項目
- [デバッガーのセキュリティ](../debugger/debugger-security.md)
- [デバッガーでのはじめに](../debugger/debugger-feature-tour.md)