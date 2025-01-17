﻿---
title: '方法: ビルドからプロジェクトを除外する |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 17a837ca-5db9-46cd-b5a7-b14ad1d2c47d
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6a0b46a4aaa780357faa38a9ee4b01d04b1a0ba1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "68178861"
---
# <a name="how-to-exclude-projects-from-a-build"></a>方法: ビルドからプロジェクトを除外する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ソリューションをビルドするために、含まれるすべてのプロジェクトをビルドする必要はありません。 たとえば、ビルドを中断するプロジェクトを除外できます。 その後、問題の調査と対処を行ってからプロジェクトをビルドすることができます。  
  
 次の方法を実行することでプロジェクトを除外できます。  
  
- アクティブなソリューション構成からプロジェクトを一時的に削除する。  
  
- 対象プロジェクトを含まないソリューション構成を作成する。  
  
  詳しくは、「[ビルド構成について](../ide/understanding-build-configurations.md)」をご覧ください。  
  
### <a name="to-temporarily-remove-a-project-from-the-active-solution-configuration"></a>アクティブなソリューション構成からプロジェクトを一時的に削除するには  
  
1. メニュー バーで **[ビルド]** 、 **[構成マネージャー]** の順に選択します。  
  
2. **[プロジェクトのコンテキスト]** テーブルで、ビルドから除外するプロジェクトを見つけます。  
  
3. プロジェクトの **[ビルド]** 列で、チェック ボックスをオフにします。  
  
4. **[閉じる]** を選択し、ソリューションをリビルドします。  
  
### <a name="to-create-a-solution-configuration-that-excludes-a-project"></a>プロジェクトを除外するソリューション構成を作成するには  
  
1. メニュー バーで **[ビルド]** 、 **[構成マネージャー]** の順に選択します。  
  
2. **[アクティブ ソリューション構成]** 一覧の **[\<新規作成>]** を選択します。  
  
3. **[名前]** ボックスに、ソリューション構成の名前を入力します。  
  
4. **[設定のコピー元]** ボックスの一覧で、新しい構成のベースにするソリューション構成 ( **[デバッグ]** など) を選択し、 **[OK]** を選択します。  
  
5. **[構成マネージャー]** ダイアログ ボックスで、除外するプロジェクトの **[ビルド]** 列のチェック ボックスをオフにし、 **[閉じる]** を選択します。  
  
6. **[標準]** ツール バーで、 **[ソリューション構成]** ボックスのアクティブな構成が、新しいソリューション構成であることを確認します。  
  
7. メニュー バーから、 **[ビルド]** 、 **[ソリューションのリビルド]** の順に選びます。  
  
## <a name="see-also"></a>関連項目
 [ビルド構成について](../ide/understanding-build-configurations.md)   
 [方法: 作成し、構成の編集](../ide/how-to-create-and-edit-configurations.md)   
 [方法: 複数の構成を同時にビルドする](../ide/how-to-build-multiple-configurations-simultaneously.md)
