---
title: アップデーターが情報の取得中にエラーを表示する
description: 「更新プログラム情報の取得中にエラーが発生しました」というエラーが発生した場合の修正方法に関する手順です。 Visual Studio 2019 for Mac で
author: asb3993
ms.author: amburns
ms.date: 04/13/2019
ms.technology: vs-ide-install
ms.assetid: 31AF914A-C66B-4CD3-9429-39695E0E94AE
ms.openlocfilehash: ef0d1f7516c410475f467ecaadecbb0aeaac71a3
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67825726"
---
# <a name="troubleshooting-updater-has-errors-retrieving-information"></a>トラブルシューティング:アップデーターが情報の取得中にエラーを表示する

[Visual Studio for Mac を更新](update.md)しようとしたときに、まれに、「更新プログラム情報の取得中にエラーが発生しました」というエラー メッセージが表示されることがあります。 これが発生した場合は、修正するために次の手順を試してください。

- インターネット接続を確認します。 接続の切断は、このエラーの最も一般的な原因です。
  - コンポーネントのダウンロードが失敗した場合は、コンポーネント名の横にある再試行ボタンをクリックして、もう一度ダウンロードをやり直すことができます。
- IDE を再起動します。
- このエラー メッセージが表示され続ける場合は、マシン上にまだ **.dmg** があるなら、インストーラーを使って更新してみることもできます。または、[visualstudio.com](https://visualstudio.microsoft.com/vs/mac/) からこれをダウンロードできます。
  - インストーラーにより、マシン上にあるインストール済みのコンポーネントがすべて更新されます。
  - インストーラーを再実行することで、以前にインストールしていなかった足りないコンポーネントをインストールすることもできます。
- `~/Library/Caches/VisualStudio/7.0/TempDownload/index.xml` にあるファイルを削除することによって、キャッシュされたダウンロードをクリアすることもできます。
