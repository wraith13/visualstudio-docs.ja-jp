---
title: ASP.NET Core アプリケーションの構築
description: この記事では、インストールや新しいプロジェクトの作成など、Visual Studio for Mac で ASP.NET の使用を始める方法について説明します。
author: sayedihashimi
ms.author: sayedha
ms.date: 05/30/2019
ms.assetid: 771C2F8E-46BC-4280-AFE8-ED9D5C7790CE
ms.openlocfilehash: 345111144e0e209d91d34e53fefcd7d1207d9a8a
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2019
ms.locfileid: "68872892"
---
# <a name="building-aspnet-core-applications-in-visual-studio-for-mac"></a>Visual Studio for Mac での ASP.NET Core アプリケーションのビルド

ASP.NET Core は、Web アプリとサービス、IoT アプリ、モバイル バックエンドなど、最新のクラウド ベースのインターネットに接続されているアプリケーションをビルドするためのオープンソースおよびクロスプラットフォーム フレームワークです。 ASP.NET Core アプリは、[.NET Core](https://www.microsoft.com/net/core/platform) ランタイムまたは .NET Framework ランタイムで実行できます。 クラウドに展開されているか、またはオンプレミスで実行されるアプリに対して、最適化された開発フレームワークを提供するように構築されています。 これは、オーバーヘッドが最小限であるモジュラー コンポーネントで構成されています。 Windows、Mac、Linux 上で、ASP.NET Core アプリ クロスプラットフォームを開発して実行することができます。 ASP.NET Core は [GitHub](https://github.com/aspnet/home) でオープン ソースとして公開されています。

このラボでは、Visual Studio for Mac で ASP.NET Core アプリケーションを作成し、探索します。

## <a name="objectives"></a>目的

> [!div class="checklist"]
> * ASP.NET Core Web アプリを作成する
> * ASP.NET Core のホスト、構成、およびミドルウェア モデルを探索する
> * ASP.NET Core Web アプリをデバッグする

## <a name="prerequisites"></a>必須コンポーネント

- [Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac)

## <a name="intended-audience"></a>対象読者

このラボは C# を使い慣れている開発者を対象としていますが、豊富な経験は必要ありません。

## <a name="task-1-creating-a-new-aspnet-core-application"></a>タスク 1:新しい ASP.NET Core アプリケーションの作成

1. **Visual Studio for Mac** を起動します。

2. **[ファイル]、[新しいソリューション]** の順に選択します。

3. **[.NET Core] > [アプリ]** カテゴリを選択し、 **[ASP.NET Core Web アプリ (C#)]** テンプレートを選択します。 **[次へ]** をクリックします。

    ![](media/netcore-image1.png)

4. **"CoreLab"** の名前を入力し、 **[作成]** を選択してプロジェクトを作成します。 完了までに少し時間がかかります。

    ![](media/netcore-image2.png)

## <a name="task-2-touring-the-solution"></a>タスク 2:ソリューションの探索

1. 既定のテンプレートでは、**CoreLab** という名前の 1 つの ASP.NET Core プロジェクトを含むソリューションがビルドされます。 プロジェクト ノードを展開すると、その内容が表示されます。

    ![](media/netcore-image3.png)

2. このプロジェクトでは、Model-View-Controller (MVC) パラダイムに従って、データ (モデル)、プレゼンテーション (ビュー)、機能 (コントローラー) の間で明確な責任区分が指定されます。 **Controllers** フォルダーから **HomeController.cs** ファイルを開きます。

    ![](media/netcore-image4.png)

3. **HomeController** クラスでは (規則により)、 **/Home** で始まるすべての着信要求が処理されます。 **Index** メソッドでは、ディレクトリのルート (`http://site.com/Home` など) への要求が処理されます。その他のメソッドでは、規則に基づいて名前付きのパスへの要求が処理されます (`http://site.com/Home/About` への要求を処理する **About()** など)。 もちろん、これらはすべて構成可能です。 1 つの重要点として、**HomeController** は新しいプロジェクトの既定のコントローラーであるため、サイトのルート (`http://site.com`) への要求は、`http://site.com/Home` または `http://site.com/Home/Index` への要求と同様に、**HomeController** の **Index()** への要求を経由します。

    ![](media/netcore-image5.png)

4. プロジェクトには **Views** フォルダーもあり、ここには各コントローラーにマップされるその他のフォルダー (および **Shared** ビューのフォルダー) が含まれます。 たとえば、 **/Home/About** パスのビュー CSHTML ファイル (HTML を拡張したもの) は、**Views/Home/About.cshtml** にあります。 そのファイルを開きます。

    ![](media/netcore-image6.png)

5. この CSHTML ファイルでは Razor 構文を使用して、標準タグとインライン C# の組み合わせに基づいて HTML をレンダリングします。 この詳細については、[オンライン ドキュメント](https://docs.microsoft.com/aspnet/web-pages/overview/getting-started/introducing-razor-syntax-c)を参照してください。

    ![](media/netcore-image7.png)

6. ソリューションには、Web サイトのルートである **wwwroot** フォルダーも含まれます。 CSS、イメージ、JavaScript ライブラリなどの静的サイト コンテンツを、サイトの展開時に指定するパスに直接配置することができます。

    ![](media/netcore-image8.png)

7. また、プロジェクトとそのパッケージ、およびアプリケーションを実行時に管理するために機能するさまざまな構成ファイルがあります。 たとえば、既定のアプリケーション[構成](https://docs.microsoft.com/aspnet/core/fundamentals/configuration)は **appsettings.json** に格納されます。 ただし、**開発**環境用の **appsettings.Development.json** ファイルを提供するなどして、環境ごとにこれらの設定の一部/すべてをオーバーライドすることができます。

    ![](media/netcore-image9.png)

## <a name="task-3-understanding-how-the-application-is-hosted"></a>タスク 3:アプリケーションをホストする方法の理解

1. **ソリューション エクスプローラー**で、**Program.cs** を開きます。 これは、アプリケーションを実行するブートストラップです。

    ![](media/netcore-image10.png)

2. ここに示すコードは 2 行だけですが、重要です。 では、詳しく見てみましょう。 最初に、新しい **WebHostBuilder** が作成されます。 ASP.NET Core アプリには、実行するホストが必要です。 ホストでは、機能とサービスのコレクションを公開する **IWebHost** インターフェイスと、**Start** メソッドを実装する必要があります。 ホストは通常、**WebHost** インスタンスをビルドして返す、**WebHostBuilder** のインスタンスを使用して作成されます。 **WebHost** は、要求を処理するサーバーを参照します。

    ![](media/netcore-image11.png)

3. **WebHostBuilder** では、アプリのサーバーをブートストラップするホストが作成されますが、あなたは、**IServer** を実装するサーバーを指定する必要があります。 既定で、これは **libuv** (クロスプラットフォームの非同期 I/O ライブラリ) に基づくクロスプラットフォームの ASP.NET Core 用 Web サーバーである **[Kestrel](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel)** です。

    ![](media/netcore-image12.png)

4. 次に、サーバーのコンテンツ ルートが設定されます。 これにより、MVC ビュー ファイルなどのコンテンツ ファイルを検索する場所が指定されます。 既定のコンテンツ ルートは、アプリケーションの実行元となるフォルダーです。

    ![](media/netcore-image13.png)

5. アプリがインターネット インフォメーション サービス (IIS) Web サーバーと連携する必要がある場合は、ホストのビルドの一部として **UseIISIntegration** メソッドを呼び出す必要があります。 **UseKestrel** とは異なり、このメソッドによってサーバーは構成されません。 ASP.NET Core で IIS を使用する場合は、**UseKestrel** と **UseIISIntegration** の両方を指定する必要があります。 **Kestrel** は、プロキシの内側で実行するよう設計されており、インターネットに直接接続して展開することはできません。 **UseIISIntegration** では、リバース プロキシ サーバーとして IIS が指定されますが、これは IIS を備えたマシンで実行される場合にのみ該当します。 Windows にアプリケーションを展開する場合は、そのままにしておきます。 それ以外では害はありません。

    ![](media/netcore-image14.png)

6. 設定の読み込みをアプリケーションのブートストラップから分離する方法は、よりクリーンなのでお勧めします。 この処理を簡単に行うには、設定およびその他のスタートアップ タスク (HTTP パイプラインへのミドルウェアの挿入など) の読み込みに **Startup** クラスが呼び出されることを指定するために、**UseStartup** が呼び出されます。 必要に応じて呼び出しごとに前の設定が上書きされることを想定して、複数の **UseStartup** 呼び出しが存在する場合があります。

    ![](media/netcore-image15.png)

7. **IWebHost** を作成する最後の手順として、**Build** を呼び出します。

    ![](media/netcore-image16.png)

8. **IWebHost** クラスは、非ブロッキング **Start** を実装するために必要ですが、ASP.NET Core プロジェクトには、**Start** をブロッキング コードでラップする **Run** という拡張メソッドが含まれます。そのため、メソッドが終了するのを手動で防ぐ必要はありません。

    ![](media/netcore-image17.png)

## <a name="task-4-running-and-debugging-the-application"></a>タスク 4: アプリケーションの実行とデバッグ

1. **ソリューション エクスプローラー**で、**CoreLab** プロジェクトのノードを右クリックし、 **[オプション]** を選択します。

    ![](media/netcore-image18.png)

2. **[プロジェクト オプション]** ダイアログには、アプリケーションをビルドして実行する方法を調整するのに必要なすべての項目が含まれます。 左側のパネルで、 **[実行] > [構成] > [既定値]** を選択します。

3. **[外部コンソールで実行する]** をオンにし、 **[コンソール出力を一時停止する]** をオフにします。 通常、自己ホスト型アプリケーションではそのコンソールは表示されませんが、代わりにその結果が **[出力]** パッドにログ記録されます。 このラボの目的のため、別のウィンドウにも表示します。これは、通常の開発時に実行する必要はありません。

4. **[OK]** をクリックします。

    ![](media/netcore-image19.png)

5. **F5** キーを押してアプリケーションをビルドし、実行します。 または、 **[実行] > [デバッグの開始]** を選択します。

6. Visual Studio for Mac で、2 つのウィンドウが起動します。 1 つ目は、自己ホスト型サーバー アプリケーションのビューを提供するコンソール ウィンドウです。

    ![](media/netcore-image20.png)

7. 2 つ目は、サイトをテストするための標準的なブラウザー ウィンドウです。 ブラウザーによって認識される限り、このアプリケーションはどこでもホストできます。 **[バージョン情報]** をクリックして、そのページに移動します。

    ![](media/netcore-image21.png)

8. [バージョン情報] ページには、コントローラーで設定されているいくつかのテキストが表示されます。

    ![](media/netcore-image22.png)

9. 両方のウィンドウを開いたままにし、Visual Studio for Mac に戻ります。 **Controllers/HomeController.cs** を開きます (まだ開いていない場合)。

    ![](media/netcore-image23.png)

10. **About** メソッドの最初の行にブレークポイントを設定します。 そのためには、余白をクリックするか、または行にカーソルを設定して **F9** キーを押します。 この行では、**Views/Home/About.cshtml** の CSHTML ページでレンダリングされる **ViewData** コレクションのデータがいくつか設定されます。

    ![](media/netcore-image24.png)

11. ブラウザーに戻り、[バージョン情報] ページを更新します。 これにより、Visual Studio for Mac のブレークポイントがトリガーされます。

12. **ViewData** メンバーにマウスを移動し、そのデータを表示します。 その子メンバーを展開して、入れ子になったデータを表示することもできます。

    ![](media/netcore-image25.png)

13. アプリケーションのブレークポイントを、追加する際に使用したものと同じメソッドを使用して削除します。

14. **Views/Home/About.cshtml** を開きます。

15. テキストの **"additional"** を **"changed"** に変更して、ファイルを保存します。

    ![](media/netcore-image26.png)

16. **[続行]** ボタンを押して、実行を続行します。

    ![](media/netcore-image27.png)

17. ブラウザー ウィンドウに戻り、更新されたテキストを表示します この変更は、いつでも行うことができ、デバッガー ブレークポイントを必要とするとは限りません。 変更すぐに反映されない場合は、ブラウザーを更新してください。

    ![](media/netcore-image28.png)

18. テスト ブラウザー ウィンドウとアプリケーション コンソールを閉じます。 これにより、デバッグも停止されます。

## <a name="task-5-application-startup-configuration"></a>タスク 5: アプリケーションのスタートアップ構成

1. **ソリューション エクスプローラー**で、**Startup.cs** を開きます。 バックグラウンドで NuGet パッケージが復元され、Roslyn コンパイラによってプロジェクトの依存関係の全体像が構築されていると、最初にいくつかの赤色の波線が表示される場合があります。

    ![](media/netcore-image29.png)

2. **Startup** メソッドを見つけます。 このセクションでは、アプリケーションの初期構成が定義され、内容がぎっしり詰まっています。 詳しく見てみましょう。

    ![](media/netcore-image30.png)

3. このメソッドでは、まず **ConfigurationBuilder** が初期化され、その基本パスが設定されます。

    ![](media/netcore-image31.png)

4. 次に、必要な **appsettings.json** ファイルが読み込まれます。

    ![](media/netcore-image32.png)

5. その後、環境固有の **appsettings.json** ファイルの読み込みが試行されます。これにより、既存の設定がオーバーライドされます。 たとえば、その特定の環境に使用される、指定の **appsettings.Development.json** ファイルです。 ASP.NET Core での構成の詳細については、[ドキュメント](https://docs.microsoft.com/aspnet/core/fundamentals/configuration)を参照してください。

    ![](media/netcore-image34.png)

6. 最後に、環境変数が構成ビルダーに追加され、利用するために構成が構築され設定されます。

    ![](media/netcore-image35.png)

## <a name="task-6-inserting-application-middleware"></a>タスク 6: アプリケーション ミドルウェアの挿入

1. **Startup** クラスで **Configure** メソッドを見つけます。 この位置で、ミドルウェアが、HTTP パイプラインに挿入し、サーバーへのすべての要求を処理するために使用できるよう構成されます。 このメソッドが呼び出されるのは 1 回だけですが、メソッドの内容 (**UseStaticFiles** など) は要求ごとに実行される場合があります。

    ![](media/netcore-image36.png)

2. パイプラインの一部として実行されるその他のミドルウェアを追加することもできます。 すべての送信応答に **X-Test** ヘッダーが自動的に追加されるよう、**app.UseStaticFiles** の後に次のコードを追加します。 IntelliSense は、入力時にコードを完成させるのに役立ちます。

    ```csharp
    app.Use(async (context, next) =>
    {
        context.Response.Headers.Add("X-Test", new[] { "Test value" });
        await next();
    });
    ```

3. **F5** キーを押し、プロジェクトをビルドして実行します。

4. ブラウザーを使用して、ヘッダーが追加されたことを確認できます。 次の手順は Safari の場合ですが、[Chrome](https://stackoverflow.com/questions/4423061/view-http-headers-in-google-chrome) または [Firefox](https://stackoverflow.com/questions/33974595/in-firefox-how-do-i-see-http-request-headers-where-in-web-console) でも同様の処理を行えます。

5. ブラウザーにサイトが読み込まれたら、 **[Safari] > [環境設定]** を選択します。

6. **[詳細]** タブで、 **[メニューバーに "開発" メニューを表示]** をオンにし、ダイアログを閉じます。

    ![](media/netcore-image37.png)

7. **[開発] > [ページのリソースを表示]** を選択します。

8. 新しく開かれた開発者ツールでトラフィックとコンテンツを追跡して分析できるように、ブラウザー ウィンドウを更新します。

9. サーバーによってレンダリングされる localhost HTML ページは、既定で選択された項目になります。

    ![](media/netcore-image38.png)

10. **詳細サイドバー**を展開します。

    ![](media/netcore-image39.png)

11. サイドバーの一番下までスクロールして、先ほどコードに追加した応答ヘッダーを確認します。

    ![](media/netcore-image40.png)

12. 確認できたら、ブラウザー ウィンドウとコンソールを閉じます。

## <a name="summary"></a>まとめ

このラボでは、Visual Studio for Mac で ASP.NET Core アプリの開発を開始する方法を学習しました。 より完全なムービー データベース アプリケーションの開発の詳細については、「[Get started with ASP.NET Core MVC](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/start-mvc)」(ASP.NET Core MVC の概要) チュートリアルを参照してください。
