---
title: DSL 定義への拡張機能の追加 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 07e133be-92ab-4936-a02b-45d2012bd0a6
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bd45a2345e6e5b28b74cb27fac226514c3f92a04
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "68159079"
---
# <a name="adding-extensions-to-dsl-definitions"></a>DSL 定義への拡張機能の追加
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DSL 定義の拡張機能では、ドメイン固有言語 (DSL) の拡張機能のパッケージを作成できます。 Visual Studio Integration Extension (VSIX) に含まれている、DSL の拡張機能は、DSL と同じ方法でユーザーのコンピューターにインストールできます。 追加の機能を動的に有効になっている、実行時に無効になっています。 Dsl を拡張機能を明示的に設計する必要はありません、拡張機能後で、またはサード パーティによる拡張の DSL を変更することがなく設計します。  
  
 追加の機能を次に含めることができます。  
  
- モデルとプレゼンテーション要素のプロパティ  
  
- シェイプとコネクタのデコレーター  
  
- クラス、リレーションシップ、図形とコネクタ  
  
- 検証制約  
  
- ツールボックス項目とタブ  
  
  拡張の DSL のユーザーが作成し、追加の機能のインスタンスを含むモデルを保存し、これらは、適切な拡張機能がインストールされている他のユーザーで読み取ることができます。 拡張機能をインストールしていないユーザーは、追加の機能を使用できませんが、更新、追加の機能を失うことがなく、モデルを保存します。  
  
  サンプル コードとこの機能の詳細については、次を参照してください。、 [Visual Studio Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=186128) Web サイト。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=186128)
