---
title: VSIX パッケージの署名 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9fabe2931310b97f0c0864ea77ceef024f0e57cd
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63447204"
---
# <a name="signing-vsix-packages"></a>VSIX パッケージの署名
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

拡張機能アセンブリは、Visual Studio で実行できますが、これを行うことをお勧めする前に署名する必要はありません。  
  
 拡張機能をセキュリティで保護し、改ざんされていないことを確認する場合は、VSIX パッケージにデジタル署名を追加できます。 VSIX が署名されたときに、VSIX インストーラー署名があること、さらに、署名自体に関する詳細情報を示すメッセージが表示されます。 VSIX の内容が変更された、VSIX が再度署名されていない場合は、署名が無効である、VSIX インストーラーが表示されます。 インストールは停止されませんが、ユーザーに警告が表示されます。  
  
> [!IMPORTANT]
> 2015 以降では、VSIX パッケージの SHA256 暗号化以外のものを使用して署名が無効な署名を持つものとして識別されます。 VSIX のインストールはブロックされませんが、ユーザーに警告が表示されます。  
  
## <a name="signing-a-vsix-with-vsixsigntool"></a>VSIXSignTool で VSIX の署名  
 署名ツールから使用可能な SHA256 暗号化が[VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility)で nuget.org で[VsixSignTool](http://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool)します。  
  
#### <a name="to-use-the-vsixsigntool"></a>VSIXSignTool を使用するには  
  
1. プロジェクトに、VSIX を追加します。  
  
2. ソリューション エクスプ ローラーでプロジェクト ノードを右クリックして選択**追加&#124;NuGet パッケージの管理**します。  詳細については、NuGet、NuGet を追加するパッケージを参照してください[NuGet の概要](http://docs.nuget.org/)と[ダイアログによる NuGet パッケージの管理](http://docs.nuget.org/Consume/Package-Manager-Dialog)します。  
  
3. VSIXSignTool VisualStudioExtensibility から検索し、NuGet パッケージをインストールします。  
  
4. プロジェクトのローカル パッケージの場所から、VSIXSignTool を実行できます。 署名のシナリオでは、ツールのコマンドラインのヘルプを参照してください (VSIXSignTool.exe/?)。  
  
   パスワード保護されている証明書ファイルで署名する例。  
  
   VSIXSignTool.exe サインオン/f \<certfile >/p\<パスワード > \<VSIXfile >  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio 拡張機能の配布](../extensibility/shipping-visual-studio-extensions.md)
