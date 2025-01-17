---
title: エディターの他の言語のサポートの追加
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax colorization
- IntelliSense
- IDE, navigation
- documents [Visual Studio], navigation
- TextMate bundle
- TextMate language grammar
- language support
ms.assetid: d78c43ee-4ef2-42e5-984e-d137de4e7e92
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7ae0b2f606b4fe04ad390712f48ac1e06ff9bb86
ms.sourcegitcommit: 283f2dbce044a18e9f6ac6398f6fc78e074ec1ed
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/16/2019
ms.locfileid: "65805326"
---
# <a name="add-visual-studio-editor-support-for-other-languages"></a>Visual Studio エディターの他の言語のサポートの追加

Visual Studio エディターでさまざまなコンピューター言語の読み取りと移動をサポートする方法、および Visual Studio エディターで他の言語のサポートを追加する方法について説明します。

## <a name="syntax-colorization-statement-completion-and-navigate-to-support"></a>構文の色づけ、ステートメント入力候補、および移動のサポート

構文の色づけ、ステートメント入力候補 (IntelliSense とも呼ばれる)、および_移動_などの Visual Studio エディターの機能を使用することで、コードの記述、読み取り、編集がより簡単になります。 次のスクリーン ショットは、Visual Studio での Perl スクリプトの編集例を示しています。 構文は自動的に色づけされます。 たとえば、コードの注釈は緑、コードは黒、パスは赤、ステートメントは青に色づけされます。 Visual Studio エディターでは、サポートされる言語に自動的に構文の色づけが適用されます。 さらに、既知の言語キーワードまたはオブジェクトの入力を始めると、ステートメント入力候補に使用可能なステートメントとオブジェクトの一覧が表示されます。 ステートメント入力候補を使用すれば、コードをよりすばやく簡単に記述することができます。

![Perl スクリプトの構文の色づけ](../ide/media/vside_perledit.png)

現在、Visual Studio では、[TextMate 文法](https://manual.macromates.com/en/language_grammars)を使用する以下の言語に対する構文の色づけおよび基本的なステートメント入力候補がサポートされます。 表に好みの言語がない場合でもご安心ください。言語は追加することができます。

|||||||
|-|-|-|-|-|-|
|Bat|F#|Java|Markdown|Rust|Visual Basic|
|Clojure|移動|JavaDoc|Objective-C|ShaderLab|C#|
|CMake|Groovy|JSON|Perl|ShellScript|Visual C++|
|CoffeeScript|HTML|LESS|Python|SQL|VBNet|
|CSS|INI|LUA|R|Swift|XML|
|Docker|Jade|Make|Ruby|TypeScript|YAML|

構文の色づけと基本的なステートメント入力候補に加え、Visual Studio には[移動](https://blogs.msdn.microsoft.com/benwilli/2015/04/09/visual-studio-tip-3-use-navigate-to/)という機能もあります。 この機能を使用すれば、コード ファイル、ファイル パスおよびコード シンボルをすばやく検索することができます。 Visual Studio では、次の言語の移動がサポートされます。

- C#

- C++

- TypeScript

- JavaScript

- Visual Basic

- 移動

- Java

- PHP

特定の言語のサポートがまだインストールされていない場合でも、これらのファイルの種類にはすべて前述の機能があります。 一部の言語の特別なサポートをインストールすると、IntelliSense や電球などのようなその他の高度な言語機能など、追加の言語サポートが提供される場合があります。

## <a name="add-support-for-non-supported-languages"></a>サポートされていない言語のサポートの追加

Visual Studio では、[TextMate 文法](https://manual.macromates.com/en/language_grammars)を使用して、エディターの言語サポートが提供されます。 現在、Visual Studio エディターで好みのプログラミング言語がサポートされていない場合は、まず、Web を検索します。その言語に対応する TextMate バンドルが既に存在している可能性があります。 それでも見つからない場合は、言語の文法とスニペットに対応する TextMate バンドル モデルを作成して、自分でサポートを追加することができます。

次のフォルダーに Visual Studio の新しい TextMate 文法を追加します。

*%userprofile%\\.vs\Extensions*

自分の状況に当てはまる場合は、この基本パスの下に以下のフォルダーを追加します。

|フォルダー名|説明|
|-----------------|-----------------|
|\\*\<言語名>*|言語のフォルダーです。 *\<言語名>* を該当する言語の名前に置き換えます。 たとえば、*\Matlab* などに置き換えます。|
|*\Syntaxes*|文法のフォルダーです。 *Matlab.json* などの、言語に対応する文法の *.json* ファイルが含まれています。|
|*\Snippets*|スニペットのフォルダーです。 言語のスニペットが含まれています。|

Windows では、*%userprofile%* はパス (*c:\Users\\\<ユーザー名>*) に解決されます。 システム上に *Extensions* フォルダーが存在しない場合は、作成する必要があります。 フォルダーが既に存在する場合は、表示されません。

> [!TIP]
> エディターでファイルを開いている場合、TextMate 文法を追加した後に構文の強調表示を参照するには、ファイルをいったん閉じてから、再び開く必要があります。

TextMate 文法の作成方法の詳細については、「[TextMate - Introduction to Language Grammars (TextMate - 言語の文法の概要)](https://developmentality.wordpress.com/2011/02/08/textmate-introduction-to-language-grammars/)」 と「[Notes on how to create a Language Grammar and Custom Theme for a Textmate Bundle (Textmate バンドルの言語の文法とカスタム テーマを作成する方法に関する注意事項)](https://benparizek.com/notebook/notes-on-how-to-create-a-language-grammar-and-custom-theme-for-a-textmate-bundle)」 を参照してください。

## <a name="see-also"></a>関連項目

- [言語サーバー プロトコルの拡張機能の追加](../extensibility/adding-an-lsp-extension.md)
- [チュートリアル: コード スニペットを作成する](../ide/walkthrough-creating-a-code-snippet.md)
- [チュートリアル: 入力候補の表示](../extensibility/walkthrough-displaying-statement-completion.md)
