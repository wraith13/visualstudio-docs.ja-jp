---
title: '[オプション]、[テキスト エディター]、[C/C++]、[詳細]'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C\C++.Advanced
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Advanced
- VS.ToolsOptionsPages.Text_Editor.C/C++.Advanced
helpviewer_keywords:
- Text Editor Options dialog box, advanced
ms.assetid: 67c82ae5-fddd-49df-baec-8e7498b156f3
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 6c5399411998f4a03468f2dedccfd660eaf8de11
ms.sourcegitcommit: 85d66dc9fea3fa49018263064876b15aeb6f9584
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68461822"
---
# <a name="options-text-editor-cc-advanced"></a>[オプション]、[テキスト エディター]、[C/C++]、[詳細]

これらのオプションを変更することによって、C または C++ でプログラミングを行うときに、IntelliSense に関連する動作と参照データベースを変更できます。

このページにアクセスするには、左ウィンドウ枠の **[オプション]** ダイアログ ボックスで、 **[テキスト エディター]** 、 **[C/C++]** の順に展開して、 **[詳細]** を選択します。

> [!NOTE]
> 次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。 これらの要素は、使用している Visual Studio のエディションや独自の設定によって決まります。 「[Visual Studio IDE のカスタマイズ](../../ide/personalizing-the-visual-studio-ide.md)」を参照してください。

## <a name="browsingnavigation"></a>参照/ナビゲーション

ソリューションの規模が大きすぎるため、データベース アクティビティにより許容できない量のシステム リソースが消費されるというまれなケースを除いて、これらのオプションを選択しないでください。

**データベースの無効化**

コード参照データベース (SDF) のすべての使用、その他のすべての参照/ナビゲーション オプション、および #include のオートコンプリートを除く IntelliSense のすべての機能は無効になります。

**データベース更新の無効化**

データベースは読み取り専用で開かれ、ファイルの編集時に更新は実行されません。 ほとんどの機能は引き続き動作します。 ただし、編集が加えられると、データは古くなり、正しくない結果が取得されます。

**データベース自動更新の無効化**

コード参照データベースは、ソース ファイルが変更されるときに自動的に更新されなくなります。 ただし、**ソリューション エクスプローラー**を開き、プロジェクトのショートカット メニューを開いてから **[ソリューションの再スキャン]** を選択すると、期限切れのすべてのファイルがチェックされ、データベースが更新されます。

**暗黙的なファイルの無効化**

コード参照データベースは、プロジェクトで指定されていないファイルのデータを収集しません。 プロジェクトには、明示的に指定されているソース ファイルとヘッダー ファイルが含まれています。 暗黙的なファイルは、明示的なファイル (たとえば、afxwin.h、windows.h、および atlbase.h) に含まれています。 通常、システムでは、これらのファイルが検出され、さまざまな参照機能 (移動など) のためにインデックスが付けられます。 このオプションを選択した場合は、これらのファイルにインデックスが付けられず、一部の機能が使用できなくなります。 また、このオプションを選択した場合は、"暗黙的なクリーンアップの無効化" と "外部依存関係の無効化" が暗黙的に選択されます。

**暗黙的なクリーンアップの無効化**

コード参照データベースは、参照されなくなった暗黙的なファイルをクリーンアップしません。 このオプションは、暗黙的なファイルが使用されなくなったときにデータベースから削除されないようにします。 たとえば、mapi.h を参照する `#include` ディレクティブをソース ファイルの 1 つに追加すると、mapi.h が検出されてインデックス付けされます。 次に、#include を削除すると、ファイルが他の場所で参照されなくなり、このオプションを選択しない限り、このファイルに関する情報が最終的に削除されます ( **[ソリューションの再スキャンの間隔]** オプションを参照してください)。このオプションは、ソリューションを明示的に再スキャンする場合には無視されます。

**外部依存関係フォルダーの無効化**

各プロジェクトの外部依存関係フォルダーは作成または更新されません。 **ソリューション エクスプローラー**では、各プロジェクトに外部依存関係フォルダーが含まれます。このフォルダーには、そのプロジェクトのすべての暗黙的なファイルが含まれます。 このオプションを選択した場合は、外部依存関係フォルダーが表示されません。

**データベースの再作成**

次回にソリューションを読み込んだときにコード参照データベースをゼロから再作成します。 このオプションを選択した場合は、次回にソリューションを読み込んだときに SDF データベース ファイルが削除されるため、データベースが再作成され、すべてのファイルにインデックスが付けられます。

**ソリューションの再スキャンの間隔**

'ソリューションの再スキャン' ジョブは、指定した間隔でスケジュールされます。 有効な値は 0 ～ 5000 分です。 既定値は 60 分です。 ソリューションの再スキャン中にファイルのタイムスタンプがチェックされ、ファイルが IDE の外部で変更されたかどうかが判断されます (IDE で行われた変更が自動的に追跡され、ファイルが更新されます)。暗黙的に含まれたファイルがチェックされ、これらのファイルすべてがまだ参照されているかどうかが判断されます。

## <a name="diagnostic-logging"></a>診断ログ

これらのオプションは、Microsoft から問題を診断するために詳細な情報を収集するように求められた場合に提供されます。 ログ情報はユーザーにとって便利ではなく、無効にしておくことをお勧めします。

**ログの有効化**

診断ログを出力ウィンドウに出力します。

**ログ レベル**

ログの詳細レベルを 0 ～ 5 の数値で設定します。

**ログ フィルター**

ビットマスクを使用して、表示されるイベントの種類をフィルター処理します。

次の任意のオプションの合計で設定します。

- 0 - なし

- 1 - General

- 2 - Idle

- 4 - WorkItem

- 8 - IntelliSense

- 16 - ACPerf

- 32 - ClassView

## <a name="fallback-location"></a>フォールバック位置

フォールバック位置は、プライマリの場所 (ソリューションと同じディレクトリ) が使用されないときに SDF および IntelliSense サポート ファイル (たとえば、iPCH) が置かれる場所です。 ユーザーにソリューション ディレクトリへの書き込みアクセス許可がない場合、またはソリューション ディレクトリが低速のデバイス上にある場合、この状況が発生することがあります。 既定のフォールバック位置は、ユーザーの一時ディレクトリにあります。

**常にフォールバック位置を使用**

コード参照データベースと IntelliSense ファイルが .sln ファイルの横に保存されるのでなく、"フォールバック位置" として指定したフォルダーに常に保存される必要があることを示します。 IDE では、ソリューション ディレクトリの横に SDF ファイルまたは iPCH ファイルが配置されることはなく、常にフォールバック位置が使用されます。

**フォールバック位置の使用を警告しない**

'フォールバック位置' が使用されている場合は、通知またはプロンプトが表示されません。 通常、IDE では、フォールバック位置を使用する必要があったかどうが通知されます。 このオプションは、その警告をオフにします。

**フォールバック位置**

この値は、コード参照データベースまたは IntelliSense ファイルの第 2 の格納場所として使用されます。 既定では、一時ディレクトリがフォールバック位置です。 IDE では、ソリューションへの完全パスのハッシュに加えて、ソリューション名を含む指定のパス (または、一時ディレクトリ) の下にサブディレクトリが作成されます。これにより、ソリューション名が同一になる問題を回避します。

## <a name="intellisense"></a>IntelliSense

**自動クイック ヒント**

ポインターをテキストの上に移動すると、クイック ツールヒントが表示されます。

**IntelliSense の無効化**

すべての IntelliSense 機能を無効にします。 IDE では、IntelliSense 要求にサービスを提供するために VCPkgSrv.exe プロセスを作成しないので、IntelliSense 機能 (QuickInfo、メンバー一覧、オートコンプリート、パラメーター ヘルプ) は機能しません。 また、セマンティクスの色づけと参照の強調表示は無効になります。 このオプションは、データベースのみに依存する参照機能 (ナビゲーション バー、ClassView、[プロパティ] ウィンドウなど) を無効にしません。

**自動更新の無効化**

IntelliSense の更新は、IntelliSense の実際の要求時まで遅延されます。 この遅延により、ファイルでの最初の IntelliSense 操作の実行時間が長くなる可能性がありますが、非常に低速またはリソースが限られているコンピューターでこのオプションを設定すると便利な場合があります。 また、このオプションを選択した場合は、"エラー レポートの無効化" オプションと "波線の無効化" オプションを暗黙的に選択します。

**エラー レポートの無効化**

波線と [エラー一覧] ウィンドウによる IntelliSense エラーのレポートを無効にします。 エラー レポートに関連付けられているバックグラウンドの解析も無効にします。 また、このオプションを選択した場合は、"波線の無効化" オプションを暗黙的に選択します。

**波線の無効化**

IntelliSense エラーの波線を無効にします。 赤い "波線" はエディター ウィンドウに表示されませんが、エラーは [エラー一覧] ウィンドウに表示されます。

**変換単位の最大キャッシュの自動調整**

IntelliSense 要求で同時に維持されるアクティブな変換単位の最大数です。 有効な値は 2 ～ 15 です。 この数値は、(Visual Studio の特定のインスタンスに対して) 実行される VCPkgSrv.exe プロセスの最大数に直接関連しています。 既定値は 2 ですが、使用可能なメモリがある場合は、この値を大きくすると、IntelliSense でパフォーマンスがわずかに向上する可能性があります。

変換単位の詳細については、「[変換フェーズ](/cpp/preprocessor/phases-of-translation)」を参照してください。

**#include のオートコンプリートの無効化**

`#include` ステートメントのオートコンプリートを無効にします。

**#include のオートコンプリートにスラッシュを使用**

"/" 使用すると `#include` ステートメントのオートコンプリートがトリガーされます。 既定の区切り記号は円記号 '\' です。 コンパイラでは、どちらの記号も使用できるため、このオプションを使用して、コード ベースが使用する記号を指定します。

**アグレッシブ メンバー一覧を無効にする**

型または変数の名前を入力するときに、メンバー一覧が表示されません。 この一覧は、 **[メンバー一覧のコミット文字]** オプションで定義されているコミット文字の 1 つを入力した後にのみ表示されます。

**メンバー一覧のキーワードを無効にする**

メンバー一覧の提案には、`void`、`class`、`switch` などの言語キーワードは表示されません。

**メンバー一覧のコード スニペットを無効にする**

コード スニペットはメンバー一覧の提案に表示されません。

**メンバー一覧のフィルター モード**

照合アルゴリズムの型を設定します。 **[ファジー]** では、スペル チェック機能に類似したアルゴリズムを使用して、類似しているが同一ではない一致を検出するため、最も可能性の高い一致が検出されます。 **[スマート フィルター処理]** では、単語の先頭でない場合でも、部分文字列と照合されます。 **[プレフィックス]** では、単語の先頭から始まる同一の部分文字列に対してのみ照合されます。

**セマンティクスの色づけを無効にする**

言語キーワード、文字列、およびコメントを除き、すべてのコードの色付けをオフにします。

**メンバー一覧のコミット文字**

現在強調表示されているメンバー一覧の提案をコミットする文字を指定します。 この一覧の文字を追加または削除できます。

**スマート メンバー一覧コミット**

単語を完全に入力した後、Enter キーを押すと行が追加されます。

**メンバー リスト Dot-To-Arrow の有効化**

メンバー リストに該当する場合に、ドット ('.') を矢印 ('->') に置換します。

## <a name="references"></a>関連項目

**解決の無効化**

'すべての参照の検索' は IntelliSense を使用して各候補を検証する代わりに未加工のテキスト検索結果を既定で表示します。 すべての検索操作でより正確な結果を表示する場合は、このチェック ボックスをオフにできます。 検索単位ベースでフィルター処理するには、結果一覧のショートカット メニューを開き、[結果の解決] をクリックします。

**未確認の項目を非表示**

'すべての参照の検索' の結果で未確認の項目を非表示にします。 "解決の無効化" オプションを設定解除した場合は、このオプションを使用して結果で未確認の項目を非表示にします。

**参照の強調表示を無効にする**

既定では、いくつかのテキストを選択すると、現在のドキュメントで同じテキストのすべてのインスタンスが自動的に強調表示されます。 この機能を無効にするには、 **[参照の強調表示を無効にする]** を **[True]** に設定します。

## <a name="text-editor"></a>[テキスト エディター]

**波かっこによる囲みの有効化**

有効にすると、テキスト エディターに '{' を入力すれば選んだテキストが中かっこで囲まれます。

**かっこによる囲みの有効化**

有効にすると、テキスト エディターに '(' を入力すれば選んだテキストがかっこで囲まれます。

## <a name="see-also"></a>関連項目

- [言語固有のエディター オプションの設定](../../ide/reference/setting-language-specific-editor-options.md)
