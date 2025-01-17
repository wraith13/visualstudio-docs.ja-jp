---
title: 'チュートリアル: データ ソースを定義する構成ファイルの使用 |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- configuration files [Visual Studio ALM], defining data sources
- unit tests, walkthrough
- data sources, defining with configuration files
ms.assetid: 95fa5214-b12e-4e1f-84e5-cc4c2d86b0d7
caps.latest.revision: 34
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f078d8a15cbef4c2f17b154af13a997b77da8766
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65695057"
---
# <a name="walkthrough-using-a-configuration-file-to-define-a-data-source"></a>チュートリアル: データ ソースを定義するための構成ファイルの使用
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このチュートリアルでは、単体テスト用に app.config ファイルで定義されたデータ ソースを使用する方法について説明します。 ここでは、<xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> クラスで使用できるデータ ソースを定義する app.config ファイルの作成方法を学習します。 このチュートリアルでは、次のタスクについて説明します。  
  
- app.Config ファイルを作成する。  
  
- カスタム構成セクションを定義する。  
  
- 接続文字列を定義する。  
  
- データ ソースを定義する。  
  
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> クラスを使用してデータ ソースにアクセスする。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを完了するための要件を次に示します。  
  
- Visual Studio Enterprise  
  
- 少なくとも 1 つのテスト メソッドにデータを提供する Microsoft Access または Microsoft Excel  
  
- テスト プロジェクトを含む Visual Studio ソリューション  
  
## <a name="create-the-appconfig-file"></a>App.config ファイルを作成する  
  
#### <a name="to-add-an-appconfig-file-to-the-project"></a>app.config ファイルをプロジェクトに追加するには  
  
1. テスト プロジェクトに既に app.config ファイルが存在する場合は、「[カスタム構成セクションの定義](#DefineCustomConfigurationSection)」に進みます。  
  
2. **ソリューション エクスプローラー**で、テスト プロジェクトを右クリックして **[追加]** をポイントし、**[新しい項目]** をクリックします。  
  
     **[新しい項目の追加]** ウィンドウが開きます。  
  
3. **[アプリケーション構成ファイル]** テンプレートを選択し、**[追加]** をクリックします。  
  
## <a name="DefineCustomConfigurationSection"></a> カスタム構成セクションを定義する  
 app.config ファイルを確認します。 少なくとも XML 宣言とルート要素が含まれています。  
  
#### <a name="to-add-the-custom-configuration-section-to-the-appconfig-file"></a>app.config ファイルにカスタム構成セクションを追加するには  
  
1. app.config のルート要素は `configuration` 要素である必要があります。 `configuration` 要素内に `configSections` 要素を作成します。 `configSections` は、app.config ファイル内で最初の要素である必要があります。  
  
2. `configSections` 要素内に、`section` 要素を作成します。  
  
3. `section` 要素に、`name` という属性を追加し、その属性に `microsoft.visualstudio.testtools` という値を割り当てます。 `type` という別の属性を追加し、その属性に `Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a` という値を割り当てます。  
  
   `section` 要素は次のようになります。  
  
```  
<section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"/>  
```  
  
> [!NOTE]
> アセンブリ名は、使用している Microsoft Visual Studio .NET Framework のビルドと一致する必要があります。 Visual Studio .NET Framework 3.5 を使用している場合は、Version を 9.0.0.0 に設定します。 Visual Studio .NET Framework 2.0 を使用している場合は、Version を 8.0.0.0 に設定します。  
  
## <a name="define-connection-strings"></a>接続文字列を定義する  
 接続文字列は、データ ソースにアクセスするためのプロバイダー固有の情報を定義します。 構成ファイルで定義された接続文字列は、アプリケーション全体で再利用可能なデータ プロバイダー情報を提供します。 このセクションでは、カスタム構成セクションで定義されているデータ ソースによって使用される 2 つの接続文字列を作成します。  
  
#### <a name="to-define-connection-strings"></a>接続文字列を定義するには  
  
1. `configSections` 要素の後に、`connectionStrings` 要素を作成します。  
  
2. `connectionStrings` 要素内に、`add` 要素を 2 つ作成します。  
  
3. 1 つ目の `add` 要素には、Microsoft Access データベースに接続するための次の属性と値を作成します。  
  
|属性|値|  
|---------------|------------|  
|`name`|`"MyJetConn"`|  
|`connectionString`|`"Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;"`|  
|`providerName`|`"System.Data.OleDb"`|  
  
 2 つ目の `add` 要素には、Microsoft Excel スプレッドシートに接続するための次の属性と値を作成します。  
  
|||  
|-|-|  
|`name`|`"MyExcelConn"`|  
|`connectionString`|`"Dsn=Excel Files;dbq=data.xlsx;defaultdir=.; driverid=790;maxbuffersize=2048;pagetimeout=5"`|  
|`providerName`|`"System.Data.Odbc"`|  
  
 `connectionStrings` 要素は次のようになります。  
  
```  
<connectionStrings>  
    <add name="MyJetConn" connectionString="Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;" providerName="System.Data.OleDb" />  
    <add name="MyExcelConn" connectionString="Dsn=Excel Files;dbq=data.xlsx;defaultdir=.; driverid=790;maxbuffersize=2048;pagetimeout=5" providerName="System.Data.Odbc" />  
</connectionStrings>  
```  
  
## <a name="define-data-sources"></a>データ ソースを定義する  
 データ ソース セクションには、テスト エンジンがデータ ソースからデータを取得するために使用する 4 つの属性が含まれます。  
  
- `name` は、使用するデータ ソースを指定するために <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> で使用される ID を定義します。  
  
- `connectionString` は、前の「接続文字列を定義する」セクションで作成した接続文字列を識別します。  
  
- `dataTableName` は、テストで使用するデータを保持するテーブルまたはシートを定義します。  
  
- `dataAccessMethod` は、データ ソース内のデータ値にアクセスする方法を定義します。  
  
  ここでは、単体テストで使用する 2 つのデータ ソースを定義します。  
  
#### <a name="to-define-data-sources"></a>データ ソースを定義するには  
  
1. `connectionStrings` 要素の後に、`microsoft.visualstudio.testtools` 要素を作成します。 この部分は、「カスタム構成セクションを定義する」セクションで作成されています。  
  
2. `microsoft.visualstudio.testtools` 要素内に、`dataSources` 要素を作成します。  
  
3. `dataSources` 要素内に、`add` 要素を 2 つ作成します。  
  
4. 1 つ目の `add` 要素には、Microsoft Access データ ソース用の次の属性と値を作成します。  
  
|属性|値|  
|---------------|------------|  
|`name`|`"MyJetDataSource"`|  
|`connectionString`|`"MyJetConn"`|  
|`dataTableName`|`"MyDataTable"`|  
|`dataAccessMethod`|`"Sequential"`|  
  
 2 つ目の `add` 要素には、Microsoft Excel データ ソース用の次の属性と値を作成します。  
  
|||  
|-|-|  
|`Name`|`"MyExcelDataSource"`|  
|`connectionString`|`"MyExcelConn"`|  
|`dataTableName`|`"Sheet1$"`|  
|`dataAccessMethod`|`"Sequential"`|  
  
 `microsoft.visualstudio.testtools` 要素は次のようになります。  
  
```  
<microsoft.visualstudio.testtools>  
    <dataSources>  
        <add name="MyJetDataSource" connectionString="MyJetConn" dataTableName="MyDataTable" dataAccessMethod="Sequential"/>  
        <add name="MyExcelDataSource" connectionString="MyExcelConn" dataTableName="Sheet1$" dataAccessMethod="Sequential"/>  
    </dataSources>  
</microsoft.visualstudio.testtools>  
```  
  
 最終的な app.config ファイルは次のようになります。  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
    <configSections>  
        <section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"/>   
    </configSections>  
    <connectionStrings>  
        <add name="MyJetConn" connectionString="Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;" providerName="System.Data.OleDb" />  
        <add name="MyExcelConn" connectionString="Dsn=Excel Files;dbq=data.xlsx;defaultdir=.; driverid=790;maxbuffersize=2048;pagetimeout=5" providerName="System.Data.Odbc" />  
    </connectionStrings>  
    <microsoft.visualstudio.testtools>  
        <dataSources>  
            <add name="MyJetDataSource" connectionString="MyJetConn" dataTableName="MyDataTable" dataAccessMethod="Sequential"/>  
            <add name="MyExcelDataSource" connectionString="MyExcelConn" dataTableName="Sheet1$" dataAccessMethod="Sequential"/>  
        </dataSources>  
    </microsoft.visualstudio.testtools>  
</configuration>  
```  
  
## <a name="create-a-unit-test-using-data-sources-defined-in-appconfig"></a>app.config で定義したデータ ソースを使用して単体テストを作成する  
 app.config ファイルの定義が完了したところで、app.config ファイルで定義されているデータ ソース内にあるデータを使用する単体テストを作成します。 このセクションでは、次のタスクを実行します。  
  
- app.config ファイルにあるデータ ソースを作成する。  
  
- 各データ ソースの値を比較する 2 つのテスト メソッド内のデータ ソースを使用する。  
  
#### <a name="to-create-a-microsoft-access-data-source"></a>Microsoft Access データ ソースを作成するには  
  
1. `testdatasource.accdb` という名前の Microsoft Access データベースを作成します。  
  
2. `testdatasource.accdb` にテーブルを作成し、`MyDataTable` という名前を付けます。  
  
3. `Number` データ型を使用して、`MyDataTable` に `Arg1` と `Arg2` という名前の 2 つのフィールドを作成します。  
  
4. 5 つのエンティティを `MyDataTable` に追加します。`Arg1` と `Arg2` の値は、それぞれ(10,50)、(3,2)、(6,0)、(0,8)、(12312,1000) となるようにします。  
  
5. データベースを保存して閉じます。  
  
6. データベースの場所を指すように接続文字列を変更します。 データベースの場所を反映するように `Data Source` の値を変更します。  
  
#### <a name="to-create-a-microsoft-excel-data-source"></a>Microsoft Excel データ ソースを作成するには  
  
1. `data.xlsx` という名前の Microsoft Excel スプレッドシートを作成します。  
  
2. `Sheet1` という名前のシートが `data.xlsx` にまだ存在しない場合は作成します。  
  
3. `Sheet1` に 2 つの列ヘッダーを作成し、`Val1` と `Val2` という名前を付けます。  
  
4. 5 つのエンティティを `Sheet1` に追加します。`Val1` と `Val2` の値は、それぞれ(1,1)、(2,2)、(3,3)、(4,4)、(5,0) となるようにします。  
  
5. スプレッドシートを保存して閉じます。  
  
6. スプレッドシートの場所を指すように接続文字列を変更します。 スプレッドシートの場所を反映するように `dbq` の値を変更します。  
  
#### <a name="to-create-a-unit-test-using-the-appconfig-data-sources"></a>app.config のデータ ソースを使用して単体テストを作成するには  
  
1. 単体テストをテスト プロジェクトに追加します。  
  
     詳細については、「[既存コードに対する単体テストの作成と実行](https://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173)」を参照してください。  
  
2. 自動生成された単体テストの内容を次のコードに置き換えます。  
  
    ```  
    using System;  
    using Microsoft.VisualStudio.TestTools.UnitTesting;  
  
    namespace TestProject1  
    {  
         [TestClass]  
        public class UnitTest1  
        {  
            private TestContext context;  
  
            public TestContext TestContext  
            {  
                get { return context; }  
                set { context = value; }  
            }  
  
            [TestMethod()]  
            [DeploymentItem("MyTestProject\\testdatasource.accdb")]  
            [DataSource("MyJetDataSource")]  
            public void MyTestMethod()  
            {  
                int a = Int32.Parse(context.DataRow["Arg1"].ToString());  
                int b = Int32.Parse(context.DataRow["Arg2"].ToString());  
                Assert.AreNotEqual(a, b, "A value was equal.");  
            }  
  
            [TestMethod()]  
            [DeploymentItem("MyTestProject\\data.xlsx")]  
            [DataSource("MyExcelDataSource")]  
            public void MyTestMethod2()  
            {  
                Assert.AreEqual(context.DataRow["Val1"], context.DataRow["Val2"]);  
            }  
        }  
    }  
    ```  
  
3. DataSource 属性を確認します。 app.config ファイルの設定名に注意してください。  
  
4. ソリューションをビルドして、MyTestMethod テストと MyTestMethod2 テストを実行します。  
  
> [!IMPORTANT]
> データ ソースなどの項目を、配置ディレクトリのテストからアクセスできるように配置します。  
  
## <a name="see-also"></a>関連項目  
 [コードの単体テスト](../test/unit-test-your-code.md)   
 [既存コードに対する単体テストの作成と実行](https://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173)   
 [アプリケーションのテスト](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)   
 [方法: データ ドリブン単体テストを作成する](../test/how-to-create-a-data-driven-unit-test.md)
