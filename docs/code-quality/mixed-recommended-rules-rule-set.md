---
title: "\"混合推奨規則\" 規則セット"
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4401417aba2055e7b2189db6bf33503668c2a658
ms.sourcegitcommit: b83fefa8177c5554cbe2c59c4d102cbc534f7cc6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/19/2019
ms.locfileid: "69585319"
---
# <a name="mixed-recommended-rules-rule-set"></a>"混合推奨規則" 規則セット

Microsoft の混合推奨規則は、潜在的なセキュリティホール、アプリケーションのクラッシュC++ 、その他の重要なロジックや設計エラーなど、共通言語ランタイムをサポートするプロジェクトの中で最も一般的で重大な問題に焦点を当てています。 この規則セットには、"[混合最小規則](mixed-minimum-rules-rule-set.md)" 規則セット内のすべての規則が含まれます。

共通言語ランタイムをサポートするC++プロジェクト用に作成したカスタム規則セットに、この規則セットを含めます。

|ルール|説明|
|----------|-----------------|
|[C6001](../code-quality/c6001.md)|初期化されていないメモリの使用|
|[C6011](../code-quality/c6011.md)|Null ポインターの逆参照|
|[C6029](../code-quality/c6029.md)|未確認の値の使用|
|[C6031](../code-quality/c6031.md)|戻り値は無視されます|
|[C6053](../code-quality/c6053.md)|呼び出しの 0 での終了|
|[C6054](../code-quality/c6054.md)|ゼロの終了がありません|
|[C6059](../code-quality/c6059.md)|不適切な連結|
|[C6063](../code-quality/c6063.md)|Format 関数への文字列引数がない|
|[C6064](../code-quality/c6064.md)|Format 関数への整数引数がない|
|[C6066](../code-quality/c6066.md)|Format 関数へのポインター引数がない|
|[C6067](../code-quality/c6067.md)|Format 関数への文字列ポインター引数がない|
|[C6101](../code-quality/c6101.md)|初期化されていないメモリを返す|
|[C6200](../code-quality/c6200.md)|インデックスがバッファーの最大値を超過|
|[C6201](../code-quality/c6201.md)|インデックスがスタック バッファーの最大値を超過|
|[C6214](../code-quality/c6214.md)|HRESULT から BOOL へのキャストが無効です|
|[C6215](../code-quality/c6215.md)|BOOL から HRESULT へのキャストが無効です|
|[C6216](../code-quality/c6216.md)|無効なコンパイラ挿入キャスト BOOL から HRESULT|
|[C6217](../code-quality/c6217.md)|NOT での無効な HRESULT テスト|
|[C6220](../code-quality/c6220.md)|-1 との無効な HRESULT 比較|
|[C6226](../code-quality/c6226.md)|-1 への無効な HRESULT 割り当て|
|[C6230](../code-quality/c6230.md)|ブール値としての HRESULT 使用は無効です|
|[C6235](../code-quality/c6235.md)|論理 Or を使用した0でない定数|
|[C6236](../code-quality/c6236.md)|論理 Or (0 以外の定数を含む)|
|[C6237](../code-quality/c6237.md)|0と論理 And で失われた副作用|
|[C6242](../code-quality/c6242.md)|ローカルアンワインド強制|
|[C6248](../code-quality/c6248.md)|Null DACL の作成|
|[C6250](../code-quality/c6250.md)|未リリースのアドレス記述子|
|[C6255](../code-quality/c6255.md)|Alloca の保護されていない使用|
|[C6258](../code-quality/c6258.md)|Terminate スレッドの使用|
|[C6259](../code-quality/c6259.md)|ビットごとの Or 限定スイッチでの配信不能コード|
|[C6260](../code-quality/c6260.md)|バイト演算の使用|
|[C6262](../code-quality/c6262.md)|過剰なスタック使用|
|[C6263](../code-quality/c6263.md)|ループでの Alloca の使用|
|[C6268](../code-quality/c6268.md)|キャストにかっこがありません|
|[C6269](../code-quality/c6269.md)|ポインターの逆参照は無視されます|
|[C6270](../code-quality/c6270.md)|Format 関数への Float 引数がない|
|[C6271](../code-quality/c6271.md)|Format 関数への余分な引数|
|[C6272](../code-quality/c6272.md)|Format 関数への Float でない引数|
|[C6273](../code-quality/c6273.md)|Format 関数への整数でない引数|
|[C6274](../code-quality/c6274.md)|Format 関数への文字でない引数|
|[C6276](../code-quality/c6276.md)|無効な文字列のキャスト|
|[C6277](../code-quality/c6277.md)|無効な CreateProcess 呼び出し|
|[C6278](../code-quality/c6278.md)|配列-新しいスカラーと削除の不一致|
|[C6279](../code-quality/c6279.md)|スカラーの新しい配列-Delete の不一致|
|[C6280](../code-quality/c6280.md)|メモリ割り当て-解放の不一致|
|[C6281](../code-quality/c6281.md)|ビットごとの関係の優先順位|
|[C6282](../code-quality/c6282.md)|割り当てがテストに置き換わる|
|[C6283](../code-quality/c6283.md)|プリミティブ配列-新しいスカラー/Delete の不一致|
|[C6284](../code-quality/c6284.md)|Format 関数への無効なオブジェクト引数|
|[C6285](../code-quality/c6285.md)|定数の論理 Or|
|[C6286](../code-quality/c6286.md)|0以外の論理 Or による副作用の損失|
|[C6287](../code-quality/c6287.md)|冗長なテスト|
|[C6288](../code-quality/c6288.md)|論理 And に対する相互包括は False|
|[C6289](../code-quality/c6289.md)|論理 Or での相互排他は True|
|[C6290](../code-quality/c6290.md)|論理 Not とビットごとの And の優先順位|
|[C6291](../code-quality/c6291.md)|論理 Not とビットごとの Or の優先順位|
|[C6292](../code-quality/c6292.md)|ループ数が最大値を上限としています|
|[C6293](../code-quality/c6293.md)|ループの数が最小値より下|
|[C6294](../code-quality/c6294.md)|ループ本体は実行されませんでした|
|[C6295](../code-quality/c6295.md)|無限ループ|
|[C6296](../code-quality/c6296.md)|ループは一度だけ実行されます|
|[C6297](../code-quality/c6297.md)|シフトの結果が大きなサイズにキャストされる|
|[C6299](../code-quality/c6299.md)|ビットフィールドとブール値の比較|
|[C6302](../code-quality/c6302.md)|Format 関数への無効な文字列引数|
|[C6303](../code-quality/c6303.md)|Format 関数への無効なワイド文字列引数|
|[C6305](../code-quality/c6305.md)|サイズと数の使用の不一致|
|[C6306](../code-quality/c6306.md)|不適切な変数引数の関数呼び出し|
|[C6308](../code-quality/c6308.md)|Realloc リーク|
|[C6310](../code-quality/c6310.md)|無効な例外フィルター定数|
|[C6312](../code-quality/c6312.md)|例外の実行ループの続行|
|[C6314](../code-quality/c6314.md)|ビットごとの or の優先順位|
|[C6317](../code-quality/c6317.md)|非補数|
|[C6318](../code-quality/c6318.md)|例外の検索を続行します|
|[C6319](../code-quality/c6319.md)|コンマで無視|
|[C6324](../code-quality/c6324.md)|文字列比較ではなく文字列のコピー|
|[C6328](../code-quality/c6328.md)|引数の型の不一致の可能性|
|[C6331](../code-quality/c6331.md)|VirtualFree 無効なフラグ|
|[C6332](../code-quality/c6332.md)|VirtualFree 無効なパラメーター|
|[C6333](../code-quality/c6333.md)|VirtualFree のサイズが無効です|
|[C6335](../code-quality/c6335.md)|処理ハンドルのリーク|
|[C6381](../code-quality/c6381.md)|シャットダウン情報がありません|
|[C6383](../code-quality/c6383.md)|要素数のバイト数のバッファーオーバーラン|
|[C6384](../code-quality/c6384.md)|ポインターのサイズの除算|
|[C6385](../code-quality/c6385.md)|読み取りのオーバーラン|
|[C6386](../code-quality/c6386.md)|書き込みのオーバーラン|
|[C6387](../code-quality/c6387.md)|無効なパラメーター値|
|[C6388](../code-quality/c6388.md)|無効なパラメーター値|
|[C6500](../code-quality/c6500.md)|無効な属性プロパティ|
|[C6501](../code-quality/c6501.md)|属性プロパティ値の競合|
|[C6503](../code-quality/c6503.md)|参照は Null にはできない|
|[C6504](../code-quality/c6504.md)|非ポインターでの Null|
|[C6505](../code-quality/c6505.md)|Void での MustCheck|
|[C6506](../code-quality/c6506.md)|非ポインターまたは配列でのバッファー サイズ|
|[C6508](../code-quality/c6508.md)|定数での書き込みアクセス|
|[C6509](../code-quality/c6509.md)|前提条件で使用される Return|
|[C6510](../code-quality/c6510.md)|非ポインターでの Null 終了|
|[C6511](../code-quality/c6511.md)|MustCheck は Yes または No でなければならない|
|[C6513](../code-quality/c6513.md)|バッファー サイズのない要素サイズ|
|[C6514](../code-quality/c6514.md)|バッファー サイズが配列サイズを超過|
|[C6515](../code-quality/c6515.md)|非ポインターでのバッファー サイズ|
|[C6516](../code-quality/c6516.md)|属性にプロパティがない|
|[C6517](../code-quality/c6517.md)|読み取り可能でないバッファーでの有効なサイズ|
|[C6518](../code-quality/c6518.md)|書き込み可能でないバッファーでの書き込み可能サイズ|
|[C6522](../code-quality/c6522.md)|無効なサイズの文字列型|
|[C6525](../code-quality/c6525.md)|無効なサイズの到達不能な場所の文字列|
|[C6527](../code-quality/c6527.md)|無効な注釈:' 必要な Srelease ' プロパティは、void 型の値では使用できません|
|[C6530](../code-quality/c6530.md)|認識されない書式指定文字列スタイル|
|[C6540](../code-quality/c6540.md)|この関数で属性注釈を使用すると、既存の __declspec 注釈がすべて無効となります|
|[C6551](../code-quality/c6551.md)|無効なサイズ指定です: 式が解析可能ではありません|
|[C6552](../code-quality/c6552.md)|無効な Deref= または Notref= です: 式が解析可能ではありません|
|[C6701](../code-quality/c6701.md)|値が有効な Yes/No/Maybe 値ではありません|
|[C6702](../code-quality/c6702.md)|値が文字列値ではありません|
|[C6703](../code-quality/c6703.md)|値が数値ではありません|
|[C6704](../code-quality/c6704.md)|予期しない注釈式エラーです|
|[C6705](../code-quality/c6705.md)|想定した注釈の引数の数が、実際の注釈の引数の数と一致しません|
|[C6706](../code-quality/c6706.md)|注釈に対する、予期しない注釈エラーです|
|[C6995](../code-quality/c6995.md)|XML ログファイルを保存できませんでした|
|[C26100](../code-quality/c26100.md)|競合状態|
|[C26101](../code-quality/c26101.md)|インタロック操作を適切に使用することが失敗する|
|[C26110](../code-quality/c26110.md)|呼び出し元がロックを保持することに失敗した|
|[C26111](../code-quality/c26111.md)|呼び出し元がロックの解放に失敗した|
|[C26112](../code-quality/c26112.md)|呼び出し元はロックを保持できません|
|[C26115](../code-quality/c26115.md)|ロックの解放に失敗する|
|[C26116](../code-quality/c26116.md)|ロックの取得または保持の失敗|
|[C26117](../code-quality/c26117.md)|保持されていないロックの解放|
|[C26140](../code-quality/c26140.md)|コンカレンシー SAL 注釈のエラーです|
|[C28020](../code-quality/c28020.md)|この呼び出しでは式が true ではありません|
|[C28021](../code-quality/c28021.md)|注釈が付けられているパラメーターはポインターである必要があります|
|[C28022](../code-quality/c28022.md)|この関数の関数クラスは、定義に使用された typedef の関数クラスと一致しません。|
|[C28023](../code-quality/c28023.md)|割り当てられる、または渡される関数\_に\_は、少なくとも1つのクラスの関数クラス\_の注釈が必要です。|
|[C28024](../code-quality/c28024.md)|割り当てられている関数ポインターには、function クラスで注釈が付けられています。関数クラスは、関数クラスのリストに含まれていません。|
|[C28039](../code-quality/c28039.md)|実際のパラメーターの型は、型と完全に一致している必要があります|
|[C28112](../code-quality/c28112.md)|インタロック関数を介してアクセスされる変数には、常にインタロックされた関数を介してアクセスする必要があります。|
|[C28113](../code-quality/c28113.md)|インタロック関数を使用したローカル変数へのアクセス|
|[C28125](../code-quality/c28125.md)|関数は try/except ブロック内から呼び出す必要があります|
|[C28137](../code-quality/c28137.md)|変数引数は、(リテラル) 定数である必要があります|
|[C28138](../code-quality/c28138.md)|定数引数は、変数である必要があります|
|[C28159](../code-quality/c28159.md)|代わりに別の関数を使用することを検討してください。|
|[C28160](../code-quality/c28160.md)|エラーの注釈|
|[C28163](../code-quality/c28163.md)|Try/except ブロック内から関数を呼び出すことはできません|
|[C28164](../code-quality/c28164.md)|引数が、ポインターへのポインターではなく、オブジェクトへのポインターを必要とする関数に渡されています|
|[C28182](../code-quality/c28182.md)|Null ポインターの逆参照 このポインターは、もう 1 つのポインターと同じ Null 値を持ちます。|
|[C28183](../code-quality/c28183.md)|引数には、1つの値を指定できます。また、は、ポインターで見つかった値のコピーです。|
|[C28193](../code-quality/c28193.md)|変数は、検査する必要がある値を保持します。|
|[C28196](../code-quality/c28196.md)|要件が満たされていません。 (式は true に評価されません)|
|[C28202](../code-quality/c28202.md)|静的でないメンバーへの参照が正しくありません|
|[C28203](../code-quality/c28203.md)|クラス メンバーへのあいまいな参照です。|
|[C28205](../code-quality/c28205.md)|\_無効\_な\_コンテキストで\_の成功または失敗時の\_使用|
|[C28206](../code-quality/c28206.md)|左側のオペランドは構造体をポイントするため、'-> ' を使用します|
|[C28207](../code-quality/c28207.md)|左側のオペランドは構造体であるため、'.' を使用します|
|[C28209](../code-quality/c28209.md)|シンボルの宣言に競合する宣言があります。|
|[C28210](../code-quality/c28210.md)|__on_failure コンテキストの注釈を明示的なプリ コンテキストに含めることはできません|
|[C28211](../code-quality/c28211.md)|SAL_context には静的コンテキスト名が必要です|
|[C28212](../code-quality/c28212.md)|注釈にはポインター式が必要です|
|[C28213](../code-quality/c28213.md)|以前\_の宣言\_を\_変更せずに参照するには、宣言注釈を使用\_する注釈を使用する必要があります。|
|[C28214](../code-quality/c28214.md)|属性パラメーター名は、p1...p9 である必要があります|
|[C28215](../code-quality/c28215.md)|typefix は、既に typefix のあるパラメーターには適用できません|
|[C28216](../code-quality/c28216.md)|checkReturn 注釈は、特定の関数パラメーターの事後条件にのみ適用されます。|
|[C28217](../code-quality/c28217.md)|関数について、注釈へのパラメーター数がファイルで検出されたものと一致しません|
|[C28218](../code-quality/c28218.md)|関数パラメーターの場合、注釈のパラメーターがファイルで見つかったものと一致しません|
|[C28219](../code-quality/c28219.md)|注釈 (注釈のパラメーター) には列挙型のメンバーが必要です|
|[C28220](../code-quality/c28220.md)|注釈 (注釈のパラメーター) には整数式が必要です|
|[C28221](../code-quality/c28221.md)|注釈のパラメーターには文字列式が必要です|
|[C28222](../code-quality/c28222.md)|注釈には __yes、\__no、または \__maybe が必要です|
|[C28223](../code-quality/c28223.md)|注釈に必要なトークン/識別子、パラメーターがありません|
|[C28224](../code-quality/c28224.md)|注釈にはパラメーターが必要です|
|[C28225](../code-quality/c28225.md)|注釈に正しい数の必須パラメーターがありません|
|[C28226](../code-quality/c28226.md)|注釈は、PrimOp (現在の宣言内) になることもできません|
|[C28227](../code-quality/c28227.md)|注釈は、PrimOp (前の宣言を参照) になることもできません|
|[C28228](../code-quality/c28228.md)|注釈パラメーター: 注釈内で型を使用することはできません|
|[C28229](../code-quality/c28229.md)|注釈はパラメーターをサポートしません|
|[C28230](../code-quality/c28230.md)|パラメーターの型にはメンバーがありません。|
|[C28231](../code-quality/c28231.md)|注釈は配列でのみ有効です|
|[C28232](../code-quality/c28232.md)|pre、post、または deref は注釈に適用されません|
|[C28233](../code-quality/c28233.md)|pre、post、または deref はブロックに適用されます|
|[C28234](../code-quality/c28234.md)|_at 式は現在の関数に適用されません|
|[C28235](../code-quality/c28235.md)|関数は注釈として独立できません|
|[C28236](../code-quality/c28236.md)|注釈は式内で使用できません|
|[C28237](../code-quality/c28237.md)|パラメーターの注釈は、もうサポートされていません|
|[C28238](../code-quality/c28238.md)|パラメーターの注釈には、複数の値、stringValue、および longValue が含まれています。 paramn=xxx を使用してください|
|[C28239](../code-quality/c28239.md)|パラメーターの注釈には、両方の値、stringValue、または longValue、さらに paramn=xxx が含まれます。 paramn=xxx のみを使用してください|
|[C28240](../code-quality/c28240.md)|パラメーターの注釈は、param2 を含みますが param1 は含みません|
|[C28241](../code-quality/c28241.md)|パラメーターの関数の注釈は認識されません|
|[C28243](../code-quality/c28243.md)|パラメーターの関数の注釈には、注釈が付けられた実際の型に許可された数よりも多くの逆参照が必要です|
|[C28244](../code-quality/c28244.md)|関数の注釈に解析不可能なパラメーター/外部注釈が含まれています|
|[C28245](../code-quality/c28245.md)|関数に対する注釈は、非メンバー関数上で 'this' に注釈を付けます。|
|[C28246](../code-quality/c28246.md)|関数に対するパラメーターの注釈が、パラメーターの型に一致しません|
|[C28250](../code-quality/c28250.md)|関数に対する一貫性のない注釈: 前のインスタンスにはエラーが含まれます。|
|[C28251](../code-quality/c28251.md)|関数に対する一貫性のない注釈: 前のインスタンスにはエラーが含まれます。|
|[C28252](../code-quality/c28252.md)|関数に対する一貫性のない注釈: パラメーターは、このインスタンスについて他の注釈を含みます。|
|[C28253](../code-quality/c28253.md)|関数に対する一貫性のない注釈: パラメーターは、このインスタンスについて他の注釈を含みます。|
|[C28254](../code-quality/c28254.md)|dynamic_cast<>() は、注釈ではサポートされません|
|[C28262](../code-quality/c28262.md)|注釈での構文エラーが関数の注釈で見つかりました|
|[C28263](../code-quality/c28263.md)|条件付き注釈での構文エラーが、組み込みの注釈で見つかりました|
|[C28267](../code-quality/c28267.md)|注釈での構文エラーが、関数の注釈で見つかりました。|
|[C28272](../code-quality/c28272.md)|検査中の関数とパラメーターに対する注釈に関数宣言との一貫性がありません|
|[C28273](../code-quality/c28273.md)|関数について、手がかりには関数宣言との一貫性がありません。|
|[C28275](../code-quality/c28275.md)|マクロ\_\_値へのパラメーターがnullです\_|
|[C28279](../code-quality/c28279.md)|シンボルについて、'begin' はありましたが、対応する 'end' がありません|
|[C28280](../code-quality/c28280.md)|シンボルについて、'end' はありましたが、対応する 'begin' がありません|
|[C28282](../code-quality/c28282.md)|書式指定文字列は、前提条件の中に存在する必要があります|
|[C28285](../code-quality/c28285.md)|関数について、パラメーターに構文エラーがあります|
|[C28286](../code-quality/c28286.md)|関数について、構文エラーが最後の近くにあります|
|[C28287](../code-quality/c28287.md)|関数について、\_At\_() 注釈 (認識されないパラメーター名) に構文エラーがあります|
|[C28288](../code-quality/c28288.md)|関数について、\_At\_() 注釈 (無効のパラメーター名) に構文エラーがあります|
|[C28289](../code-quality/c28289.md)|関数の場合:ReadableTo または WritableTo に、パラメーターとして制限仕様がありませんでした|
|[C28290](../code-quality/c28290.md)|関数の注釈は、実際のパラメーターの数より多い外部参照を含みます|
|[C28291](../code-quality/c28291.md)|deref レベル 0 での post null/notnull は、関数に対して意味がありません。|
|[C28300](../code-quality/c28300.md)|演算子に対する互換性のない型の、式のオペランドです|
|[C28301](../code-quality/c28301.md)|関数の最初の宣言に対して注釈がありません。|
|[C28302](../code-quality/c28302.md)|余分な \_Deref\_ 演算子が注釈に見つかりました。|
|[C28303](../code-quality/c28303.md)|あいまいな \_Deref\_ 演算子が注釈に見つかりました。|
|[C28304](../code-quality/c28304.md)|不適切に設定された \_Notref\_ 演算子がトークンに適用されました。|
|[C28305](../code-quality/c28305.md)|トークンの解析中にエラーが発生しました。|
|[C28306](../code-quality/c28306.md)|パラメーターの注釈は obsolescent|
|[C28307](../code-quality/c28307.md)|パラメーターの注釈は obsolescent|
|[C28350](../code-quality/c28350.md)|注釈には、条件付きで適用できない状況の説明が表示されます。|
|[C28351](../code-quality/c28351.md)|注釈には、動的な値 (変数) が使用できない条件が記述されています。|
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|破棄可能なフィールドを所有する型は、破棄可能でなければなりません|
|[CA1009](../code-quality/ca1009-declare-event-handlers-correctly.md)|イベント ハンドラーを正しく宣言します|
|[CA1016](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|アセンブリに AssemblyVersionAttribute を設定します|
|[CA1033](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md)|インターフェイス メソッドは、子型によって呼び出し可能でなければなりません|
|[CA1049](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|ネイティブ リソースを所有する型は、破棄可能でなければなりません|
|[CA1060](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|P/Invoke を NativeMethods クラスに移動します|
|[CA1061](../code-quality/ca1061-do-not-hide-base-class-methods.md)|基底クラス メソッドを非表示にしません|
|[CA1063](../code-quality/ca1063-implement-idisposable-correctly.md)|IDisposable を正しく実装します|
|[CA1065](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|予期しない場所に例外を発生させません|
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|重複するアクセラレータを使用しません|
|[CA1400](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|P/Invoke エントリ ポイントは存在しなければなりません|
|[CA1401](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|P/Invoke は参照可能であることはできません|
|[CA1403](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|Auto 配置の型を COM 参照可能にすることはできません|
|[CA1404](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|P/Invoke の直後に GetLastError を呼び出します|
|[CA1405](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|COM 参照可能な型の基本型は COM 参照可能でなければなりません|
|[CA1410](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|COM 登録メソッドは一致しなければなりません|
|[CA1415](../code-quality/ca1415-declare-p-invokes-correctly.md)|P/Invoke を正しく宣言します|
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|空のファイナライザーを削除します|
|[CA1900](../code-quality/ca1900-value-type-fields-should-be-portable.md)|値型フィールドはポータブルでなければなりません|
|[CA1901](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|P/Invoke 宣言はポータブルでなければなりません|
|[CA2002](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|弱い ID を伴うオブジェクト上でロックしません|
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|SQL クエリのセキュリティ脆弱性を確認|
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|P/Invoke 文字列引数に対してマーシャリングを指定します|
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|値型での宣言セキュリティを確認します|
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|ポインターは参照可能にすることはできません|
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|セキュリティで保護された型はフィールドを公開してはなりません|
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|メソッド セキュリティは型のスーパーセットでなければなりません|
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|APTCA メソッドは APTCA メソッドのみを呼び出すことができます|
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|APTCA 型は APTCA 基本型のみを拡張することができます|
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|リンク要求を含むメソッドを間接的に公開しません|
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|オーバーライドのリンク要求はベースと同一でなければなりません|
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|脆弱性のある finally 句を外側の try でラップします|
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|型のリンク要求には継承要求が必要です|
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|セキュリティ上重要な型は型等価性に参加してはならない|
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|既定のコンストラクターは、基本型の既定コンストラクターと同程度以上、重要であることが必要|
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|デリゲートは透過性の整合がとれたメソッドにバインドする必要がある|
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|メソッドは、基本メソッドをオーバーライドしている場合、透過性の整合性を保つ必要がある|
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|透過的メソッドは、検証可能な IL のみを含まなければならない|
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|透過的メソッドは、SuppressUnmanagedCodeSecurity 属性を持つメソッドを呼び出してはならない|
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|透過的コードは、セキュリティ上重要な項目を参照してはならない|
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|透過的メソッドは Linkdemand を満たしてはならない|
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|型は、基本型およびインターフェイスと同程度以上、重要でなければならない|
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|透過コードは、セキュリティ アサートを使用してはならない|
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|透過的メソッドは、ネイティブ コード内に呼び出しを行ってはならない|
|[CA2200](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|スタック詳細を保持するために再度スローします|
|[CA2202](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|オブジェクトを複数回破棄しない|
|[CA2207](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|値型のスタティック フィールドのインラインを初期化します|
|[CA2212](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|サービス コンポーネントを WebMethod に設定しません|
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|破棄可能なフィールドは破棄されなければなりません|
|[CA2214](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md)|コンストラクターのオーバーライド可能なメソッドを呼び出しません|
|[CA2216](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|破棄可能な型はファイナライザーを宣言しなければなりません|
|[CA2220](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|ファイナライザーは基底クラスのファイナライザーを呼び出さなければなりません|
|[CA2229](../code-quality/ca2229-implement-serialization-constructors.md)|シリアル化コンストラクターを実装します|
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|ValueType.Equals のオーバーライドで、演算子 equals をオーバーロードします|
|[CA2232](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|Windows フォームのエントリ ポイントを STAThread に設定します|
|[CA2235](../code-quality/ca2235-mark-all-non-serializable-fields.md)|すべてのシリアル化不可能なフィールドを設定します|
|[CA2236](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|ISerializable 型で基底クラス メソッドを呼び出します|
|[CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|ISerializable 型を SerializableAttribute に設定します|
|[CA2238](../code-quality/ca2238-implement-serialization-methods-correctly.md)|シリアル化メソッドを正しく実装します|
|[CA2240](../code-quality/ca2240-implement-iserializable-correctly.md)|ISerializable を正しく実装します|
|[CA2241](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|書式設定メソッドに正しい引数を提供|
|[CA2242](../code-quality/ca2242-test-for-nan-correctly.md)|NaN に対して正しくテストします|