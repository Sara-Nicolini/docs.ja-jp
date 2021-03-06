---
title: "高度なフィルター | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8d81590f-e036-4f96-824a-4a187f462764
caps.latest.revision: 23
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 23
---
# 高度なフィルター
このサンプルでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ルーティング サービスを示します。ルーティング サービスは、コンテンツ ベースのルーターをアプリケーションに簡単に追加できるようにする [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] コンポーネントです。このサンプルでは、標準の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 電卓のサンプルを改良し、ルーティング サービスを使用して通信するようにします。そして、メッセージ フィルターとメッセージ フィルター テーブルを使用してコンテンツ ベースのルーティング ロジックを定義する方法を説明します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\AdvancedFilters`  
  
## サンプルの詳細  
 次の表は、ルーティング サービスのメッセージ フィルター テーブルに追加されるメッセージ フィルターを示しています。  
  
|フィルター|規則|優先順位|  
|-----------|--------|----------|  
|If \(has header\)|Rounding|2|  
|If \(showed up on Ep2\)|Regular|1|  
|If \(showed up with Address2\)|Rounding|1|  
|If \(RoundRobin1\)|Regular|0|  
|If \(RoundRobin2\)|Rounding|0|  
  
 メッセージ フィルターとメッセージ フィルター テーブルは、コードまたはアプリケーション構成ファイルで作成および構成できます。このサンプルのメッセージ フィルターとメッセージ フィルター テーブルは、コードで定義されたものが RoutingService\\routing.cs ファイルに、アプリケーション構成ファイルで定義されたものが RoutingService\\App.config ファイルにあります。以降では、このサンプルのメッセージ フィルターとメッセージ フィルター テーブルをコードで作成する方法を説明します。  
  
 まず最初に、<xref:System.ServiceModel.Dispatcher.XPathMessageFilter> でカスタム ヘッダーを探します。<xref:System.ServiceModel.WSHttpBinding> の結果のエンベロープ バージョンでは SOAP 1.2 が使用されるため、SOAP 1.2 名前空間を使用するように XPath ステートメントを定義します。<xref:System.ServiceModel.Dispatcher.XPathMessageFilter> の既定の名前空間マネージャーでは SOAP 1.2 名前空間のプレフィックス \/s12 が既に定義されているため、このプレフィックスを使用できます。一方、クライアントが実際のヘッダー値を定義するために使用するカスタムの名前空間は含まれていないため、そのプレフィックスを定義する必要があります。このヘッダーを持つすべてのメッセージがこのフィルターに一致します。  
  
```  
XPathMessageContext namespaceManager = new XPathMessageContext();  
namespaceManager.AddNamespace("custom", "http://my.custom.namespace/");  
  
XPathMessageFilter xpathFilter = new XPathMessageFilter("/s12:Envelope/s12:Header/custom:RoundingCalculator = 1", namespaceManager);  
  
```  
  
 2 番目のフィルターは、`calculatorEndpoint` で受信されたメッセージに一致する <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> です。エンドポイント名は、サービス エンドポイント オブジェクトの作成時に定義されます。  
  
```  
EndpointNameMessageFilter endpointNameFilter = new EndpointNameMessageFilter("calculatorEndpoint");  
  
```  
  
 3 番目のフィルターは、<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> です。このフィルターは、指定したアドレス プレフィックス \(アドレスの前半部分\) に一致するアドレスを持つエンドポイントで受信されたメッセージに一致します。この例のアドレス プレフィックスは "http:\/\/localhost\/routingservice\/router\/rounding\/" として定義されています。この場合、"http:\/\/localhost\/routingservice\/router\/rounding\/\*" 宛ての受信メッセージがこのフィルターに一致します。この例では、丸め処理を行う電卓のエンドポイントのアドレスが "http:\/\/localhost\/routingservice\/router\/rounding\/calculator" なので、このエンドポイントで受信されたメッセージがこのフィルターに一致することになります。  
  
```  
PrefixEndpointAddressMessageFilter prefixAddressFilter = new PrefixEndpointAddressMessageFilter(new EndpointAddress("http://localhost/routingservice/router/rounding/"));  
  
```  
  
 最後の 2 種類のメッセージ フィルターは、カスタムの <xref:System.ServiceModel.Dispatcher.MessageFilter> です。この例では、"RoundRobin" メッセージ フィルターが使用されています。このメッセージ フィルターは、付属の RoutingService\\RoundRobinMessageFilter.cs ファイルに作成されています。これらのフィルターを同じグループに設定すると、両方のフィルターが同時に `true` を返さないように、メッセージに一致したという報告と一致しないという報告を交互に行うようになります。  
  
```  
RoundRobinMessageFilter roundRobinFilter1 = new RoundRobinMessageFilter("group1");  
  
RoundRobinMessageFilter roundRobinFilter2 = new RoundRobinMessageFilter("group1");  
  
```  
  
 次に、これらすべてのメッセージ フィルターを <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> に追加します。その際に、メッセージ フィルター テーブルでフィルターが実行される順番を左右する優先度を指定します。優先度の高いフィルターが先に実行され、優先度の低いフィルターは後に実行されます。したがって、優先度が 2 のフィルターは優先度が 1 のフィルターより先に実行されます。優先度が指定されていない場合の既定の優先度は 0 です。メッセージ フィルター テーブルは、特定の優先度のフィルターをすべて実行してから次の優先度に移ります。特定の優先度で一致が検出された場合、それより低い優先度のフィルターでの検出は省略されます。  
  
> [!NOTE]
>  ここではメッセージ フィルターの優先度の使い方を説明していますが、一般的には、優先度を設定しなくても正しく機能するようにフィルターを設計および構成するのがパフォーマンスの観点からも設計の観点からも理想的です。  
  
 最初に追加するフィルターは、優先度が 2 に設定された XPath フィルターです。これが、最初に実行されるメッセージ フィルターです。このフィルターによってカスタム ヘッダーが検出されると、他のフィルターの結果に関係なく、メッセージは丸め処理を行う電卓のエンドポイントにルーティングされます。  
  
 優先度 1 では 2 つのフィルターを追加します。これらのフィルターは、メッセージが優先度 2 の XPath フィルターに一致しなかった場合にのみ実行されます。この 2 つのフィルターは、受信したメッセージの宛先を特定する 2 とおりの方法を示しており、それぞれが、2 つのエンドポイントの一方でメッセージが受信されたかどうかを確認します。したがって、両方が同時に `true` を返すことはないため、同じ優先度で実行できます。  
  
 最後に、優先度 0 \(最も低い優先度\) で RoundRobin メッセージ フィルターが実行されます。これらのフィルターは同じグループ名で構成されているため、一度に 1 つのフィルターのみが一致します。カスタム ヘッダーを持つメッセージと特定の仮想エンドポイント宛てのメッセージはすべて既にルーティングされているため、RoundRobin メッセージ フィルターによって処理されるメッセージは、カスタム ヘッダーを持たない、既定のルーターのエンドポイント宛てのメッセージだけです。これらのメッセージは呼び出しのたびに切り替えられるため、操作の半分は通常の電卓のエンドポイントに送られ、もう半分は丸め処理を行う電卓のエンドポイントに送られます。  
  
#### このサンプルを使用するには  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を使用して AdvancedFilters.sln を開きます。  
  
2.  **ソリューション エクスプローラー**を開くには、**\[表示\]** メニューの **\[ソリューション エクスプローラー\]** をクリックします。  
  
3.  [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] で F5 キーを押すか、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
    1.  F5 キーを押したときに必要なプロジェクトが自動的に起動されるようにする場合は、ソリューションを右クリックし、**\[プロパティ\]** をクリックします。左ペインの **\[共通プロパティ\]** で **\[スタートアップ プロジェクト\]** をクリックします。**\[マルチ スタートアップ プロジェクト\]** をクリックし、すべてのプロジェクトに**開始**アクションを設定します。  
  
    2.  Ctrl キーと Shift キーを押しながら B キーを押してプロジェクトをビルドする場合は、次のアプリケーションを開始する必要があります。  
  
        1.  電卓クライアント \(.\/CalculatorClient\/bin\/client.exe\)  
  
        2.  電卓サービス \(.\/CalculatorService\/bin\/service.exe\)  
  
        3.  丸め処理を行う電卓サービス \(.\/RoundingCalcService\/bin\/service.exe\)  
  
        4.  ルーティング サービス \(.\/RoutingService\/bin\/RoutingService.exe\)  
  
4.  電卓クライアントのコンソール ウィンドウで、Enter キーを押してクライアントを起動します。選択可能な送信先エンドポイントの一覧が返されます。  
  
5.  対応する文字を入力して送信先エンドポイントを選択し、Enter キーを押します。  
  
6.  次に、カスタム ヘッダーを追加するかどうかを確認するメッセージが表示されます。追加する場合は Y \(Yes\) キーを、追加しない場合は N \(No\) キーを押して、Enter キーを押します。  
  
7.  選択に応じて異なる出力が表示されます。  
  
    1.  メッセージにカスタム ヘッダーを追加した場合は、次の出力が返されます。  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.1  
  
        ```  
  
    2.  カスタム ヘッダーを使用せずに丸め処理を行う電卓のエンドポイントを選択した場合は、次の出力が返されます。  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.1  
  
        ```  
  
    3.  カスタム ヘッダーを使用せずに通常の電卓のエンドポイントを選択した場合は、次の出力が返されます。  
  
        ```Output  
        Add(100,15.99) = 115.99  
        Subtract(145,76.54) = 6846  
        Multiply(9,81.25) = 731.25  
        Divide(22,7) = 3.14285714285714  
  
        ```  
  
    4.  カスタム ヘッダーを使用せずに既定のルーターのエンドポイントを選択した場合は、次の出力が返されます。  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.46  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.14285714285714  
  
        ```  
  
8.  また、電卓サービスと丸め処理を行う電卓サービスは、呼び出された操作のログをそれぞれのコンソール ウィンドウに出力します。  
  
9. 終了するには、クライアント コンソール ウィンドウで「`quit`」と入力するか、Enter キーを押します。  
  
10. サービスを終了するには、サービス コンソール ウィンドウで Enter キーを押します。  
  
## コードまたは App.config で構成可能  
 サンプルは、提供された時点では、App.config ファイルを使用してルーターの動作を定義するように構成されています。RoutingService\\App.config ファイルの名前を別の名前に変更して認識されないようにし、RoutingService\\routing.cs の `ConfigureRouterViaCode()` に対するメソッド呼び出しのコメントを解除することもできます。どちらの方法でも、ルーターの動作は同じになります。  
  
### シナリオ  
 このサンプルでは、1 つのエンドポイントを介して複数の種類または実装のサービスを公開することを可能にするコンテンツ ベースのルーターとして機能するルーターを示します。  
  
### 実際のシナリオ  
 Contoso では、すべてのサービスを仮想化して 1 つのエンドポイントのみを公開し、そのエンドポイントを通じて複数の異なる種類のサービスへのアクセスを提供したいと考えています。この場合は、ルーティング サービスのコンテンツ ベースのルーティング機能を使用して受信要求の送信先を決定します。  
  
## 参照  
 [AppFabric のホストおよび永続化のサンプル](http://go.microsoft.com/fwlink/?LinkId=193961)