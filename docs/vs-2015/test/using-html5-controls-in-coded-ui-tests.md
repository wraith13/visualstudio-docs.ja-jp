---
title: コード化された UI テストでの HTML5 コントロールの使用 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 2000b214-ae92-4334-b549-aa0eb4f45fe1
caps.latest.revision: 19
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8b08853937be3f11913f88293633b02f3636898c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439727"
---
# <a name="using-html5-controls-in-coded-ui-tests"></a>コード化された UI テストでの HTML5 コントロールの使用
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

コード化された UI テストには、Internet Explorer 9 と Internet Explorer 10 に含まれる HTML5 コントロールの一部のサポートが含まれます。  
  
 **必要条件**  
  
- Visual Studio Enterprise  
  
> [!WARNING]
> Internet Explorer 10 以前のバージョンでは、Internet Explorer プロセスより高い特権レベルでコード化された UI テストを実行できました。 Internet Explorer 10 でコード化された UI テストを実行するときは、コード化された UI テストと Internet Explorer のプロセスを同じ特権レベルで実行する必要があります。 これは、Internet Explorer 10 のよりセキュリティ レベルの高い AppContainer 機能によるものです。  
  
> [!WARNING]
> Internet Explorer 10 でコード化された UI テストを作成した場合、そのテストは Internet Explorer 9 または Internet Explorer 8 を使用して実行できないことがあります。 これは、Internet Explorer 10 には、オーディオ、ビデオ、ProgressBar、スライダーなどの HTML5 コントロールが含まれているためです。 これらの HTML5 コントロールは、Internet Explorer 9 または Internet Explorer 8 で認識されません。 同様に、Internet Explorer 9 を使用するコード化された UI テストには、Internet Explorer 8 で認識されない HTML5 コントロールが含まれる場合があります。  
  
## <a name="supported-html5-controls"></a>サポートされている HTML5 コントロール  
 コード化された UI テストには、次の HTML5 コントロールの記録、再生、検証のサポートが含まれます。  
  
- [オーディオ コントロール](#audio-control)  
  
- [ビデオ コントロール](#video-control)  
  
- [スライダー](#slider)  
  
- [ProgressBar](#progressbar)  
  
### <a name="audio-control"></a>オーディオ コントロール  
 **オーディオ コントロール:** HTML5 オーディオ コントロールに対するアクションが正しく記録され再生されます。  
  
 ![HTML5 オーディオ コントロール](../test/media/codedui-html5-audio.png)  
  
|アクション|記録中|生成されたコード|  
|------------|---------------|--------------------|  
|**オーディオの再生**<br /><br /> コントロールから直接、またはコントロールのコンテキスト メニューから|\<name> オーディオを 00:00:00 の時点から再生|HtmlAudio.Play(TimeSpan)|  
|**オーディオの特定の時点にシーク**|\<name> オーディオの 00:01:48 の時点にシーク|HtmlAudio.Seek(TimeSpan)|  
|**オーディオの一時停止**<br /><br /> コントロールから直接、またはコントロールのコンテキスト メニューから|\<name> オーディオの 00:01:53 の時点で一時停止|HtmlAudio.Pause(TimeSpan)|  
|**オーディオのミュート**<br /><br /> コントロールから直接、またはコントロールのコンテキスト メニューから|\<name> オーディオをミュート|HtmlAudio.Mute()|  
|**オーディオのミュートの解除**<br /><br /> コントロールから直接、またはコントロールのコンテキスト メニューから|\<name> オーディオのミュートを解除|HtmlAudio.Unmute()|  
|**オーディオの音量の変更**|\<name> オーディオのボリュームを 79% に設定|HtmlAudio.SetVolume(float)|  
  
 HtmlAudio には次のプロパティがあり、それらのすべてでアサーションを追加することができます。  
  
```  
string AutoPlay  
string Controls  
string CurrentSrc  
string CurrentTime  
string CurrentTimeAsString  
string Duration  
string DurationAsString  
string Ended  
string Loop  
string Muted  
string Paused  
string PlaybackRate  
string ReadyState  
string Seeking  
string Src  
string Volume  
```  
  
 **検索プロパティ:**`HtmlAudio` の検索プロパティは、`Id`、`Name`、`Title` です。  
  
 **フィルター プロパティ:**`HtmlAudio` のフィルター プロパティは、`Src`、`Class`、`ControlDefinition`、`TagInstance` です。  
  
> [!NOTE]
> Seek および Pause の時間は大きな意味を持つことがあります。 再生中、コード化された UI テストは、オーディオを一時停止する前に、`(TimeSpan)` に指定された時間まで待機します。 特殊な状況において、Pause コマンドが実行される前に指定された時間が経過したとき、例外がスローされます。  
  
### <a name="video-control"></a>ビデオ コントロール  
 **ビデオ コントロール:** HTML5 ビデオ コントロールに対するアクションが正しく記録され再生されます。  
  
 ![HTML5 ビデオ コントロール](../test/media/codedui-html5-video.png)  
  
|アクション|記録中|生成されたコード|  
|------------|---------------|--------------------|  
|**ビデオの再生**<br /><br /> コントロールから直接、またはコントロールのコンテキスト メニューから|\<name> ビデオを 00:00:00 の時点から再生|HtmlVideo.Play(TimeSpan)|  
|**ビデオの特定の時点にシーク**|\<name> ビデオの 00:01:48 の時点にシーク|HtmlVideo.Seek(TimeSpan)|  
|**ビデオの一時停止**<br /><br /> コントロールから直接、またはコントロールのコンテキスト メニューから|\<name> ビデオの 00:01:53 の時点で一時停止|HtmlVideo.Pause(TimeSpan)|  
|**ビデオのミュート**<br /><br /> コントロールから直接、またはコントロールのコンテキスト メニューから|\<name> ビデオをミュート|HtmlVideo.Mute()|  
|**ビデオのミュートの解除**<br /><br /> コントロールから直接、またはコントロールのコンテキスト メニューから|\<name> ビデオのミュートを解除|HtmlVideo.Unmute()|  
|**ビデオの音量の変更**|\<name> ビデオのボリュームを 79% に設定||  
  
 HtmlVideo には、HtmlAudio のすべてのプロパティが用意されています。 さらに、次の 3 つのプロパティも使用できます。 それらのすべてでアサーションを追加することができます。  
  
```  
string Poster  
string VideoHeight  
string VideoWidth  
  
```  
  
 **検索プロパティ:**`HtmlVideo` の検索プロパティは、`Id`、`Name`、`Title` です。  
  
 **フィルター プロパティ:**`HtmlVideo` のフィルター プロパティは、`Src`、`Poster`、`Class`、`ControlDefinition`、`TagInstance` です。  
  
> [!NOTE]
> -30s または +30s のラベルを使用してビデオを巻き戻したり早送りしたりする場合、集計後の適切なタイミングにシークされます。  
  
### <a name="slider"></a>スライダー  
 **スライダー コントロール:** HTML5 スライダー コントロールに対するアクションを正しく記録および再生します。  
  
 ![HTML5 スライダー コントロール](../test/media/codedui-html5-slider.png)  
  
|アクション|記録中|生成されたコード|  
|------------|---------------|--------------------|  
|**スライダーにおける位置の設定**|\<name> スライダー内の \<x> に位置を設定|HtmlSlider.ValueAsNumber=\<x>|  
  
 HtmlSlider には次のプロパティがあり、それらのすべてでアサーションを追加することができます。  
  
```  
string Disabled  
string Max  
string Min  
string Required  
string Step  
string ValueAsNumber  
```  
  
### <a name="progressbar"></a>ProgressBar  
 **ProgressBar コントロール:** ProgressBar は、非対話型コントロールです。 このコントロールの `Value` プロパティと `Max` プロパティでアサーションを追加できます。  
  
 ![HTML5 ProgressBar コントロール](../test/media/codedui-html5-progressbar.png)  
  
## <a name="see-also"></a>関連項目

- [HTML 要素](https://www.w3schools.com/HTML/html_elements.asp)   
- [UI オートメーションを使用してコードをテストする](../test/use-ui-automation-to-test-your-code.md)   
- [コード化された UI テストを作成する](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
- [コード化された UI テストをカスタマイズする](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeCUITModify)   
- [コード化された UI テストと操作の記録でサポートされている構成とプラットフォーム](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
