---
title: ReceiveAndSendReply テンプレート デザイナー |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9de3e8446250829d431dcbf33b14effd607ab545
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62802403"
---
# <a name="receiveandsendreply-template-designer"></a>ReceiveAndSendReply テンプレート デザイナー
**ReceiveAndSendReply**のペアを作成するテンプレートが使用される事前構成済み<xref:System.ServiceModel.Activities.Receive>と<xref:System.ServiceModel.Activities.SendReply>内のアクティビティを<xref:System.Activities.Statements.Sequence>要求/応答メッセージ交換の一部として関連付けられるアクティビティサーバー上のパターン。  

## <a name="the-receiveandsendreply-template"></a>ReceiveAndSendReply テンプレート  
 追加**ReceiveAndSendReply**テンプレートは次の 3 つ作成されるほか、<xref:System.ServiceModel.Activities.Receive>と<xref:System.ServiceModel.Activities.SendReply>でアクティビティを<xref:System.Activities.Statements.Sequence>アクティビティ。  

1. <xref:System.ServiceModel.Activities.Receive.OperationName%2A> アクティビティの <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> プロパティと <xref:System.ServiceModel.Activities.Receive> プロパティを構成する。  

2. <xref:System.ServiceModel.Activities.SendReply.Request%2A> アクティビティの <xref:System.ServiceModel.Activities.Receive> プロパティを <xref:System.ServiceModel.Activities.Send> アクティビティにバインドする。  

3. 親アクティビティに、変数として <xref:System.ServiceModel.Activities.CorrelationHandle> を作成する。  

### <a name="using-the-receiveandsendreply-template-designer"></a>ReceiveAndSendReply テンプレート デザイナーの使用  
 **ReceiveAndSendReply**アクティビティ デザイナーが記載されて、**メッセージング**のカテゴリ、**ツールボックス**をクリックしてアクセスする、**ツールボックス** ] タブの [ [!INCLUDE[wfd2](../includes/wfd2-md.md)] (または、選択**ツールバー**から、**ビュー**メニューのまたは CTRL + ALT + X)。  

 **ReceiveAndSendReply**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**ドロップ、[!INCLUDE[wfd2](../includes/wfd2-md.md)]サーフェス場所でアクティビティを通常配置しています。 これを作成、<xref:System.ServiceModel.Activities.Receive>アクティビティで構成できる、**送信**アクティビティ デザイナーと、相関<xref:System.ServiceModel.Activities.SendReply>SendReplyToReceive デザイナーで構成できます。  

 [!INCLUDE[crabout](../includes/crabout-md.md)] 使用して、**受信**を構成するデザイナー、<xref:System.ServiceModel.Activities.Receive>アクティビティを参照してください、[受信](../workflow-designer/receive-activity-designer.md)トピック。  

 [!INCLUDE[crabout](../includes/crabout-md.md)] 使用して、 **SendReplyToReceive**を構成するデザイナー、<xref:System.ServiceModel.Activities.SendReply>アクティビティでは、次のセクションを参照してください。  

### <a name="properties-of-sendreply"></a>SendReply のプロパティ  
 次の表に、<xref:System.ServiceModel.Activities.SendReply> のプロパティと、デザイナーでのその使用方法を示します。 これらのプロパティは、プロパティ グリッドで編集できます。また、その一部は[!INCLUDE[wfd2](../includes/wfd2-md.md)]のデザイナー画面で編集できます。  

|                               プロパティ名                                | 必須 |                                                                                                                                                                                                                                                                                                                                                      使用方法                                                                                                                                                                                                                                                                                                                                                       |
|----------------------------------------------------------------------------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|              <xref:System.Activities.Activity.DisplayName%2A>              |  False   |                                                                                                                                                                                            <xref:System.ServiceModel.Activities.SendReply> アクティビティの省略可能な表示名。 既定値は SendReplyToReceive です。<br /><br /> 既定値以外の <xref:System.Activities.Activity.DisplayName%2A> の使用は必須ではありませんが、使用することをお勧めします。                                                                                                                                                                                             |
|         <xref:System.ServiceModel.Activities.SendReply.Request%2A>         |   True   | この <xref:System.ServiceModel.Activities.Receive> アクティビティと関連付けられる <xref:System.ServiceModel.Activities.SendReply> アクティビティへの参照。 このプロパティがある必要がありますいない**null**します。 <xref:System.ServiceModel.Activities.Receive> アクティビティと <xref:System.ServiceModel.Activities.SendReply> アクティビティは、要求/応答メッセージ パターンをモデル化するためにサーバーで一緒に使用されます。 このプロパティでは、関連付ける <xref:System.ServiceModel.Activities.Send> アクティビティを指定します。 このプロパティは、<xref:System.ServiceModel.Activities.Send> アクティビティの作成元である <xref:System.ServiceModel.Activities.SendReply> アクティビティに自動的にバインドされるため、デザイナーでは編集できません。 |
|         <xref:System.ServiceModel.Activities.SendReply.Content%2A>         |  False   |                       受信するメッセージまたはパラメーターの内容を指定します。 <xref:System.ServiceModel.Activities.ReceiveMessageContent> アクティビティまたは <xref:System.ServiceModel.Activities.ReceiveParametersContent> アクティビティを指定できます。 このプロパティの横にある省略記号ボタンをクリックして編集、**コンテンツ**フィールドにプロパティ グリッドまたはをクリックすると、**を定義する.** ボタンの横にある、**コンテンツ**のラベルを**受信**アクティビティ デザイナー画面。 両方を表示、**コンテンツ定義**ダイアログ。 [!INCLUDE[crabout](../includes/crabout-md.md)] このボックスを使用して、表示する方法、[コンテンツ定義 ダイアログ ボックス](../workflow-designer/content-definition-dialog-box.md)トピック。                       |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> |  False   |            ワークフロー内のこの <xref:System.ServiceModel.Activities.CorrelationInitializer> アクティビティを構成する複数の <xref:System.ServiceModel.Activities.CorrelationHandle> オブジェクトを初期化する <xref:System.ServiceModel.Activities.Receive> オブジェクトのコレクションを指定します。 横にある省略記号ボタンをクリックして、<xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A>プロパティを開く [プロパティ] グリッドで、 **[関連付け初期化子**] ダイアログ ボックス。 [!INCLUDE[crabout](../includes/crabout-md.md)] このボックスを使用して参照してください、[関連付け初期化子の追加 ダイアログ ボックス](../workflow-designer/add-correlationinitializers-dialog-box.md)トピック。            |
|         <xref:System.ServiceModel.Activities.SendReply.Action%2A>          |  False   |                                                                                                                                                                                                                                              メッセージのアクション ヘッダーを指定します。 これを明示的に設定しない場合は、次の既定値が設定されます。<br /><br /> <strong>https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}</strong>                                                                                                                                                                                                                                              |
|    <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A>    |  False   |                                                                                                                                                                                                                                                                                          応答メッセージを送信する前にワークフロー サービス インスタンスを永続化するかどうかを指定します。 既定値は **false** です。                                                                                                                                                                                                                                                                                           |

## <a name="see-also"></a>関連項目  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [受信](../workflow-designer/receive-activity-designer.md)   
 [送信](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)