---
title: プロファイラーのコマンド ライン:サービスのタイミングの詳細を取得するためのインストルメント化
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6116e1df-ed3e-4b0d-ac7f-22f7d7ac00ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e9271974857da4fffa7d053afdb2b160fb72ede4
ms.sourcegitcommit: 91c7f1b525e0c22d938bc4080ba4ceac2483474f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2019
ms.locfileid: "67033043"
---
# <a name="collect-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line"></a>プロファイラーのコマンド ラインからインストルメンテーション メソッドを使用した、サービスの詳細なタイミング データの収集
このセクションでは、コマンド ラインからインストルメンテーション メソッドを使用して、Windows サービスの詳細なパフォーマンス データを収集する手順とオプションについて説明します。

## <a name="common-tasks"></a>一般的なタスク

|タスク|関連するコンテンツ|
|----------|---------------------|
|**.NET サービスをプロファイリングする**|-   [方法: .NET サービスをインストルメントし、詳細なタイミング データを収集する](../profiling/how-to-instrument-a-dotnet-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)|
|**階層の相互作用データを追加する**|-   [階層相互作用データを収集する](../profiling/adding-tier-interaction-data-from-the-command-line.md)|
|**C/C++ サービスをプロファイリングする**|-   [方法: ネイティブ サービスをインストルメントし、詳細なタイミング データを収集する](../profiling/how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)|

## <a name="related-tasks"></a>関連するタスク

### <a name="profile-windows-services"></a>Windows サービスのプロファイリング

|タスク|関連するコンテンツ|
|----------|---------------------|
|**サンプリング メソッドを使用したプロファイリング**|-   [サンプリングを使用したアプリケーション統計情報の収集](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|
|**.NET のメモリ割り当てとガベージ コレクションのプロファイリング**|-   [.NET メモリ データの収集](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|
|**リソースの競合とスレッド アクティビティのプロファイリング**|-   [コンカレンシー データの収集](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|

### <a name="profile-by-using-the-instrumentation-method"></a>インストルメンテーション方式を使用したプロファイリング

|タスク|関連するコンテンツ|
|----------|---------------------|
|**スタンドアロン (クライアント) アプリケーションのプロファイリング**|-   [インストルメンテーションを使用した詳細なタイミング データの収集](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|
|**ASP.NET Web アプリケーションのプロファイリング**|-   [インストルメンテーションを使用した詳細なタイミング データの収集](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md)|

### <a name="analyze-instrumentation-data-views-and-reports"></a>インストルメンテーション データ ビューとレポートの分析
- [インストルメンテーション メソッドのデータ ビュー](../profiling/instrumentation-method-data-views.md)
