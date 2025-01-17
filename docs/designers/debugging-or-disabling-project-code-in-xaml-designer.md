---
title: XAML デザイナーでプロジェクト コードをデバッグまたは無効化する
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ac600581-8fc8-49e3-abdf-1569a3483d74
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4f588395284891bab61a575f088931e2fc244bce
ms.sourcegitcommit: 90c3187d804ad7544367829d07ed4b47d3f8a72d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2019
ms.locfileid: "68822105"
---
# <a name="debug-or-disable-project-code-in-xaml-designer"></a>XAML デザイナーでプロジェクト コードをデバッグまたは無効化する

ハンドルされない例外が XAML デザイナーで起こる原因の多くは、プロジェクト コードがアクセスしようとするプロパティまたはメソッドが、デザイナーでアプリケーションを実行するときに、返す値や動作方法が変わることにあります。 Visual Studio の別のインスタンスでプロジェクト コードをデバッグしてこれらの例外を解決するか、デザイナーでプロジェクトのコードを無効にして、一時的に例外を回避することができます。

プロジェクト コードには次のものが含まれます。

- カスタム コントロールおよびユーザー コントロール

- クラス ライブラリ

- 値コンバーター

- プロジェクト コードから生成されるデザイン時のデータに対するバインド

プロジェクト コードが無効になると、Visual Studio によってプレースホルダーが表示されます。 たとえば、データが使用できなくなったバインドのプロパティ名などのプレースホルダーや、実行されなくなったコントロールのプレースホルダーが表示されます。

![[ハンドルされていない例外] ダイアログ](../designers/media/xaml_unhandledexception.png)

## <a name="to-determine-if-project-code-is-causing-an-exception"></a>プロジェクト コードが例外の原因かどうかを判断するには

1. ハンドルされない例外のダイアログで、 **[ここをクリックして、デザイナーを再読み込み]** リンクを選びます。

2. メニュー バーで、 **[デバッグ]**  >  **[デバッグ開始]** の順に選択して、アプリケーションを実行します。

     アプリケーションがビルドされ、正常に実行される場合は、デザイナーで実行されているプロジェクト コードによってデザイン時例外が発生する可能性があります。

## <a name="to-debug-project-code-running-in-the-designer"></a>デザイナーで実行されているプロジェクト コードをデバッグするには

1. ハンドルされない例外のダイアログで、 **[ここをクリックしてプロジェクト コードの実行を無効にし、デザイナーを再読み込み]** リンクを選びます。

2. Windows タスク マネージャーで、 **[タスクの終了]** ボタンを選び、現在実行している Visual Studio XAML デザイナーのすべてのインスタンスを閉じます。

     ![TaskManager の XAML デザイナー インスタンス](../designers/media/xaml_taskmanager.png)

3. Visual Studio で、デバッグするコードまたはコントロールを含む XAML ページを開きます。

4. Visual Studio の新しいインスタンスを開き、プロジェクトの 2 番目のインスタンスを開きます。

5. プロジェクト コードにブレークポイントを設定します。

6. Visual Studio の新しいインスタンスのメニュー バーで、 **[デバッグ]**  >  **[プロセスにアタッチ]** の順に選択します。

7. **[プロセスにアタッチ]** ダイアログの **[選択可能なプロセス]** 一覧で、 **XDesProc.exe**を選び、 **[アタッチ]** ボタンを選びます。

     ![XAML デザイナー プロセス](../designers/media/xaml_attach.png)

     これは、Visual Studio の最初のインスタンスの XAML デザイナーの手順です。

8. Visual Studio の最初のインスタンスのメニュー バーで、 **[デバッグ]** 、 **[デバッグ開始]** の順に選択します。

     デザイナーで実行しているコードにステップ インできます。

## <a name="to-disable-project-code-in-the-designer"></a>デザイナーでプロジェクト コードを無効にするには

- ハンドルされない例外のダイアログで、 **[ここをクリックしてプロジェクト コードの実行を無効にし、デザイナーを再読み込み]** リンクを選びます。

- あるいは、**XAML デザイナー**のツール バーで、 **[プロジェクト コードを無効にする]** ボタンを選びます。

     ![[プロジェクト コードの無効化] ボタン](../designers/media/xaml_disablecode.png)

     もう一度ボタンを切り替えて、プロジェクト コードを再び有効にできます。

    > [!NOTE]
    > ARM または X64 プロセッサがターゲットのプロジェクトの場合、Visual Studio は、デザイナーでプロジェクト コードを実行できないため、デザイナーで **[プロジェクト コードを無効にする]** ボタンは無効です。

- どちらかのオプションを実行するとデザイナーは再度読み込み、関連付けられているプロジェクトのすべてのコードを無効にします。

    > [!NOTE]
    > プロジェクト コードを無効にすると、デザイン時データが失われることがあります。 別の方法は、デザイナーで実行されているコードをデバッグすることです。

## <a name="control-display-options"></a>コントロールの表示オプション

> [!NOTE]
> **コントロールの表示オプション**は、Windows 10 Fall Creators Update (ビルド 16299) 以降を対象とするユニバーサル Windows プラットフォーム アプリケーションでのみ使用できます。 **コントロールの表示オプション**機能は、Visual Studio 2017 バージョン 15.9 以降で使用できます。

XAML デザイナーでは、Windows SDK からのプラットフォーム コントロールのみを表示するようにコントロールの表示オプションを変更できます。 これにより、XAML デザイナーの信頼性が向上する可能性があります。

コントロールの表示オプションを変更するには、デザイナー ウィンドウの左下のアイコンをクリックし、 **[コントロールの表示オプション]** の下でオプションを選択します。

![コントロールの表示オプション](../designers/media/control_display_options.png)

**[プラットフォーム コントロールのみを表示]** を選択すると、SDK からのすべてのカスタム コントロールや顧客ユーザー コントロールなどが完全にレンダリングされなくなります。 代わりに、これらはコントロールの位置とサイズを示すフォールバック コントロールで置き換えられます。

## <a name="see-also"></a>関連項目

- [Visual Studio および Blend for Visual Studio での XAML の設計](../designers/designing-xaml-in-visual-studio.md)
