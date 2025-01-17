---
title: プロファイラーのコマンド ライン:動的な ASP.NET アプリのインストルメント化、タイミング データの取得
ms.date: 11/04/2016
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 656cceea8cfc76d9c4865b5a2a792993e3f90f15
ms.sourcegitcommit: 91c7f1b525e0c22d938bc4080ba4ceac2483474f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2019
ms.locfileid: "67032006"
---
# <a name="how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line"></a>方法: プロファイラーのコマンド ラインを使用して動的にコンパイルされた ASP.NET Web アプリケーションをインストルメント化し、詳細なタイミング データを収集する

この記事では、コマンドライン ツールの Visual Studio プロファイル ツールを利用し、インストルメンテーション プロファイル方法で、動的にコンパイルされた [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] アプリケーションの詳細なタイミング データを収集する方法について説明します。

> [!NOTE]
> プロファイル ツールへのパスを取得するには、[コマンド ライン ツールへのパスの指定](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)に関する記事をご覧ください。 64 ビット コンピューター上では、64 ビット バージョンのツールと 32 ビット バージョンのツールの両方を使用できます。 プロファイラー コマンド ライン ツールを使用するには、コマンド プロンプト ウィンドウの PATH 環境変数にツールのパスを追加するか、コマンド自体にそれを追加します。

[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web アプリケーションからパフォーマンス データを収集するには、ターゲット アプリケーションの *web.config* ファイルを変更し、動的にコンパイルされたアプリケーション ファイルをインストルメント化する [VSInstr.exe](../profiling/vsinstr.md) ツールを有効にします。 [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) ツールを使用し、Web サーバーで適切な環境変数を設定してプロファイルを有効にし、コンピューターを再起動します。

プロファイラーを起動し、ターゲット アプリケーションを実行します。 プロファイラーをアプリケーションにアタッチしている間はデータ収集を一時停止し、完了後に再開できます。 プロファイルが完了したら、アプリケーションを閉じ、インターネット インフォメーション サービス (IIS) のワーカー プロセスを閉じ、プロファイラーをシャットダウンします。 プロファイル作業を完了したら、*web.config* ファイルと Web サーバーを元の状態に復元します。

## <a name="configure-the-aspnet-web-application-and-the-web-server"></a>ASP.NET Web アプリケーションと Web サーバーを構成する

1. ターゲット アプリケーションの *web.config* ファイルを変更します。 「[方法:Web.config ファイルを変更して、動的にコンパイルされた ASP.NET Web アプリケーションをインストルメント化およびプロファイルする](../profiling/how-to-modify-web-config-files-to-instrument-dynamically-compiled-aspnet-apps.md)」をご覧ください。

2. コマンド プロンプト ウィンドウを開きます。

3. プロファイル環境変数を初期化します。 型:

     **VSPerfClrEnv /globaltraceon**

    - **/globaltraceon** は、インストルメンテーション メソッドを使用したプロファイルを有効にします。

4. コンピューターを再起動します。

## <a name="run-the-profiling-session"></a>プロファイル セッションの実行

1. コマンド プロンプト ウィンドウを開きます。

2. プロファイラーを起動します。 型:

     **VSPerfCmd**  [/start](../profiling/start.md) **:trace**  [/output](../profiling/output.md) **:** `OutputFile` [`Options`]

   - **/start:trace** オプションによってプロファイラーが初期化されます。

   - **/start** を使用するには、 **/output:** `OutputFile` オプションを指定する必要があります。 `OutputFile` には、プロファイル データ (.*vsp*) ファイルの名前と場所を指定します。

     **/start:trace** オプションを使用する場合は、次のうちいずれのオプションでも指定できます。

     > [!NOTE]
     > **/user** オプションと **/crosssession** オプションは、通常、ASP.NET アプリケーションで必要です。

     | オプション | 説明 |
     | - | - |
     | [/user](../profiling/user-vsperfcmd.md) **:** [`Domain` **\\** ]`UserName` | ASP.NET ワーカー プロセスを所有するアカウントのドメインおよびユーザー名を指定します。 このオプションは、ログオンしているユーザーとは別のユーザーがプロセスを実行している場合に指定する必要があります。 プロセスの所有者は、Windows タスク マネージャーの **[プロセス]** タブの **[ユーザー名]** 列に表示されます。 |
     | [/crosssession](../profiling/crosssession.md) | 他のログオン セッションにおけるプロセスのプロファイリングを有効にします。 このオプションは、ASP.NET アプリケーションが別のセッションで実行されている場合に必要です。 セッション ID は、Windows タスク マネージャーの **[プロセス]** タブの **[セッション ID]** 列に表示されます。 **/crosssession** の省略形として、 **/CS** を指定することができます。 |
     | [/globaloff](../profiling/globalon-and-globaloff.md) | データ コレクションを一時停止した状態でプロファイラーを起動します。 プロファイリングを再開するには、[/globalon](../profiling/globalon-and-globaloff.md) を使用します。 |
     | [/counter](../profiling/counter.md) **:** `Config` | `Config` で指定されたプロセッサのパフォーマンス カウンターから情報を収集します。 カウンター情報は、プロファイル イベントが発生するたびに、収集されたデータに追加されます。 |
     | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | プロファイリング実行中に収集する Windows パフォーマンス カウンターを指定します。 |
     | [/automark](../profiling/automark.md) **:** `Interval` | **/wincounter** との組み合わせでのみ使用します。 Windows パフォーマンス カウンター コレクション イベントの間隔をミリ秒単位で指定します。 既定値は 500 ミリ秒です。 |
     | [/events](../profiling/events-vsperfcmd.md) **:** `Config` | プロファイリング実行中に収集する ETW (Event Tracing for Windows) イベントを指定します。 ETW イベントは独立した (.*etl*) ファイルに収集されます。 |

3. 一般的な方法で [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web アプリケーションを起動します。

## <a name="control-data-collection"></a>データ収集の制御

ターゲット アプリケーションの実行中に、*VSPerfCmd.exe* のオプションを使用して、プロファイラーのデータ ファイルへのデータ書き込みを開始および停止することにより、データ収集を制御できます。 データ コレクションを制御することにより、アプリケーションの起動や終了など、プログラム実行の特定の部分についてのデータ コレクションを行うことができます。

- 次に示すオプションの組み合わせにより、データ収集を開始および停止します。 個別のコマンド ラインで各オプションを指定します。 データ収集のオンとオフは複数回切り替えることができます。

    |オプション|説明|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|すべてのプロセスのデータ収集を開始 ( **/globalon**) または停止 ( **/globaloff**) します。|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|プロセス ID (`PID`) で指定されたプロセスのデータ収集を開始 ( **/processon**) または停止 ( **/processoff**) します。|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|スレッド ID (`TID`) で指定されたスレッドのデータ収集を開始 ( **/threadon**) または停止 ( **/threadoff**) します。|

- **VSPerfCmd.exe**[/mark](../profiling/mark.md) オプションを使用して、データ ファイルにプロファイル マークを挿入することもできます。 **/mark** コマンドは、識別子、タイム スタンプ、およびオプションのユーザー定義文字列を追加します。 マークは、プロファイラー レポートおよびデータ ビューでデータをフィルター処理するために使用できます。

## <a name="end-the-profiling-session"></a>プロファイル セッションの終了

プロファイル セッションを終了するには、ターゲット [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web アプリケーションを閉じ、IIS をリセットしてプロファイルされたプロセスを停止し、プロファイラーをシャットダウンします。

1. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web アプリケーションを終了します。

2. インターネット インフォメーション サービス (IIS) をリセットし、[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ワーカー プロセスを閉じます。 種類:

     **IISReset /stop**

3. プロファイラーをシャットダウンします。 型:

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)

4. IIS を再起動します。 型:

     **IISReset /start**

## <a name="restore-the-application-and-computer-configuration"></a>アプリケーションとコンピューターの構成を復元する

すべてのプロファイルを完了したら、*web.config* ファイルを置換し、プロファイル環境変数を消去し、コンピューターを再起動してアプリケーションとサーバーをプロファイル前の状態に復元します。

1. *web.config* ファイルを元のファイルのコピーで置き換えます。

2. プロファイル環境変数を削除します。 型:

     **VSPerfCmd /globaloff**

3. コンピューターを再起動します。

## <a name="see-also"></a>関連項目

[ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)
[インストルメンテーション メソッドのデータ ビュー](../profiling/instrumentation-method-data-views.md)