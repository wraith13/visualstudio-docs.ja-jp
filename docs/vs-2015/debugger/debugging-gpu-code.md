---
title: GPU コードのデバッグ |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c7e77a5a-cb57-4b11-9187-ecc89acc8775
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bb5342dc2b5da3d1192aadbbea186b5b21f179f3
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65691546"
---
# <a name="debugging-gpu-code"></a>GPU コードのデバッグ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

グラフィックス処理装置 (GPU) で実行されている C++ コードをデバッグできます。 Visual Studio での GPU デバッグのサポートには、競合の検出、プロセスの開始、プロセスへのアタッチ、デバッグ ウィンドウへの統合が含まれます。  
  
## <a name="supported-platforms"></a>サポートされているプラットフォーム  
 デバッグは [!INCLUDE[win7](../includes/win7-md.md)]、[!INCLUDE[win8](../includes/win8-md.md)]、[!INCLUDE[winsvr08_r2](../includes/winsvr08-r2-md.md)]、[!INCLUDE[winserver8](../includes/winserver8-md.md)] でサポートされています。 ソフトウェア エミュレーターでデバッグするには、[!INCLUDE[win8](../includes/win8-md.md)] または [!INCLUDE[winserver8](../includes/winserver8-md.md)] が必要です。 ハードウェアでデバッグするには、使用するグラフィックス カードのドライバーをインストールする必要があります。 ハードウェア ベンダーによってはデバッガーの一部の機能が実装されていない場合があります。 制限については、ベンダーのドキュメントを参照してください。  
  
> [!NOTE]
> Visual Studio での GPU デバッグをサポートする独立系ハードウェア ベンダーは、VSD3DDebug インターフェイスを実装し、独自のドライバーを対象とする DLL を作成する必要があります。  
  
## <a name="configuring-gpu-debugging"></a>GPU デバッグの構成  
 デバッガーは同じアプリの実行中に CPU コードと GPU コードの両方で中断することはできません。 既定では、デバッガーは CPU コードで中断されます。 GPU コードをデバッグするには、次の 2 つの手順のいずれかを使用します。  
  
- **[標準]** ツール バーの **[デバッグの種類]** リストで **[GPU のみ]** を選択します。  
  
- **ソリューション エクスプローラー**で、プロジェクトのショートカット メニューの **[プロパティ]** を選びます。 **[プロパティ ページ]** ダイアログ ボックスで **[デバッグ]** をクリックし、**[デバッガーの種類]** リストで **[GPU のみ]** を選択します。  
  
## <a name="launching-and-attaching-to-applications"></a>アプリケーションの起動とアプリケーションへのアタッチ  
 Visual Studio のデバッグ コマンドを使用して GPU デバッグを開始および停止できます。 詳細については、「[デバッガーでのコード間の移動](../debugger/navigating-through-code-with-the-debugger.md)」を参照してください。 また、実行中のプロセスに GPU デバッガーをアタッチできます。ただし、そのプロセスが GPU コードを実行している場合に限ります。 詳細については、次を参照してください。[実行中のプロセスにアタッチ](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)します。  
  
## <a name="run-current-tile-to-cursor-and-run-to-cursor"></a>[現在の Tile をカーソル行の前まで実行] と [カーソル行の前まで実行]  
 GPU でデバッグするとき、カーソル位置まで実行するには 2 つの選択肢があります。 いずれの選択肢のコマンドもコード エディターのショートカット メニューで使用できます。  
  
1. **[カーソル行の前まで実行]** コマンドは、カーソル位置に達するまでアプリを実行してから中断します。 これは、現在のスレッドがカーソル位置まで実行されるという意味ではありません。カーソル位置に達した最初のスレッドが中断されるということです。 参照してください[デバッガーでコード間の移動](../debugger/navigating-through-code-with-the-debugger.md)  
  
2. **[現在の Tile をカーソル行の前まで実行]** コマンドは、現在の Tile 内のすべてのスレッドがカーソル位置に達するまでアプリを実行してから中断します。  
  
## <a name="debugging-windows"></a>デバッグ ウィンドウ  
 特定のデバッグ ウィンドウを使用することで、GPU スレッドを調べたり、スレッドにフラグを設定したり、スレッドを凍結したりできます。 詳細については次を参照してください:  
  
- [[並列スタック] ウィンドウの使用](../debugger/using-the-parallel-stacks-window.md)  
  
- [[タスク] ウィンドウの使用](../debugger/using-the-tasks-window.md)  
  
- [方法: [並列ウォッチ] ウィンドウを使用する](../debugger/how-to-use-the-parallel-watch-window.md)  
  
- [スレッドとプロセス](../debugger/debug-threads-and-processes.md)([デバッグの場所] ツールバー)  
  
- [方法: [GPU スレッド] ウィンドウを使用する](../debugger/how-to-use-the-gpu-threads-window.md)  
  
## <a name="data-synchronization-exceptions"></a>データ同期の例外  
 デバッガーは実行中に複数のデータ同期条件を検出できます。 条件を検出すると、デバッガーは中断状態になります。 **[中断]** または **[続行]** の 2 つの選択肢があります。 **[例外]** ダイアログ ボックスを使用して、デバッガーがこれらの条件を検出するかどうか、どの条件で実行を中断するかを構成できます。 詳細については、次を参照してください。[デバッガーでの例外を管理する](../debugger/managing-exceptions-with-the-debugger.md)します。 使用することも、**オプション** ダイアログ ボックスに書き込まれたデータのデータの値が変更されない場合に、デバッガーが例外を無視する必要がありますを指定します。 詳細については、[[全般]、デバッグ、オプションダイアログ ボックス](../debugger/general-debugging-options-dialog-box.md)を参照してください。  
  
## <a name="troubleshooting"></a>トラブルシューティング  
  
### <a name="specifying-an-accelerator"></a>アクセラレータの指定  
 GPU コード内のブレークポイントがヒットするのは、コードが [accelerator::direct3d_ref](https://msdn.microsoft.com/library/a514b1a7-3b3f-4011-be6c-f7b0d9a42663) (REF) アクセラレータで実行されている場合のみです。 コード内でアクセラレータを指定していない場合は、REF アクセラレータがプロジェクトのプロパティの **[デバッグ アクセラレータの種類]** で自動的に選択されます。 コード内でアクセラレータを明示的に選択している場合、REF アクセラレータはデバッグ中に使用されません。GPU ハードウェアがデバッグをサポートしていない限り、ブレークポイントがヒットすることはありません。 この問題を解決するには、デバッグ中に REF アクセラレータを使用するようにコードを記述します。 詳細については、プロジェクトのプロパティを参照してくださいと[アクセラレータおよび accelerator_view オブジェクトを使用して](https://msdn.microsoft.com/library/18f0dc66-8236-4420-9f46-1a14f2c3fba1)と[のプロジェクト設定、C++デバッグ構成](../debugger/project-settings-for-a-cpp-debug-configuration.md)します。  
  
### <a name="conditional-breakpoints"></a>条件付きブレークポイント  
 GPU コード内の条件付きブレークポイントはサポートされていますが、すべての式をデバイス上で評価できるとは限りません。 式はデバイスで評価できないと、デバッガーで評価されます。 デバッガーでの処理はデバイスでの処理よりも遅くなる可能性があります。  
  
### <a name="error-there-is-a-configuration-issue-with-the-selected-debugging-accelerator-type"></a>エラー :選択されたデバッグ アクセラレータの種類と構成の問題があります。  
 プロジェクトの設定とデバッグ中の PC の設定との間に矛盾があると、このエラーが発生します。 詳細については、次を参照してください。 [C++ デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)します。  
  
### <a name="error-the-debug-driver-for-the-selected-debugging-accelerator-type-is-not-installed-on-the-target-machine"></a>エラー :ターゲット コンピューターでは、選択されたデバッグ アクセラレータの種類に対応するデバッグ ドライバーがインストールされていません。  
 リモート PC でデバッグしている場合に、このエラーが発生します。 デバッガーは、ドライバーがリモート PC にインストールされているかどうかを実行時まで判別できません。 ドライバーはグラフィックス カードの製造元から入手できます。  
  
### <a name="error-timeout-detection-and-recovery-tdr-must-be-disabled-at-the-remote-site"></a>エラー :リモート サイトでは、タイムアウト検出と復旧 (TDR) を無効にする必要があります。  
 Windows のタイムアウト検出と復旧 (TDR) で設定されている既定の時間間隔より、C++ AMP の計算が長くかかっている可能性があります。 その場合、計算は取り消され、データは失われます。 詳細については、「[Handling TDRs in C++ AMP](http://go.microsoft.com/fwlink/p/?LinkId=249154)」 (C++ AMP での TDR の処理) を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: C++ AMP アプリケーションのデバッグ](https://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5)   
 [C++ デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Visual Studio で GPU デバッグを開始する](http://go.microsoft.com/fwlink/p/?LinkId=255381)
