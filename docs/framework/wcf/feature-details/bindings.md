---
title: "Windows Communication Foundation バインディング | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "バインディング [WCF]"
  - "WCF [WCF], バインディング"
  - "Windows Communication Foundation [WCF], バインディング"
ms.assetid: 83639133-89f7-43f0-b4ef-8d9e57c08d25
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# Windows Communication Foundation バインディング
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] では、アプリケーション ソフトウェアを作成する方法と、アプリケーション ソフトウェアが他のソフトウェアと通信する方法は分離されています。バインディングを使用して、クライアントとサービスが相互に通信するために必要なトランスポート、エンコーディング、およびプロトコルの詳細を指定します。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、バインディングを使用してエンドポイントの基になるネットワーク上の表現を生成します。このため、バインディングの詳細の大半について通信している双方が合意する必要があります。これを実現する最も簡単な方法は、サービスのクライアントがサービスのエンドポイントと同じバインディングを使用することです。その方法[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/ja-jp/bd8b277b-932f-472f-a42a-b02bb5257dfb)」を参照してください。  
  
 バインディングは、バインド要素のコレクションで構成されます。各要素は、エンドポイントがクライアントと通信する方法の一部分を記述します。バインディングには、1 つ以上のトランスポート バインド要素、1 つ以上のメッセージ エンコーディング バインド要素 \(既定では、トランスポート バインド要素によって提供されます\)、および任意の数の他のプロトコル バインド要素が含まれている必要があります。このように、ランタイムをビルドするプロセスでは、各バインド要素からランタイムにコードを提供できます。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] には、一般的なバインド要素を含むさまざまなバインディングが用意されています。これらのバインディングは、既定の設定で使用することも、ユーザーの要件に応じて既定値を変更することもできます。これらのシステム指定のバインディングには、バインド要素およびその設定を直接制御できるプロパティが含まれます。また、バインディングの各バージョンに独自の名前を付けることで、複数のバージョンを同時に使用することもできます。詳細については、「[システムが提供するバインディングの構成](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)」を参照してください。  
  
 システム指定のバインディングに用意されていないバインド要素のコレクションが必要になった場合には、その必要なバインド要素のコレクションで構成されるカスタム バインディングを作成できます。このようなカスタム バインディングは簡単に作成でき、新しいクラスも必要ありませんが、バインド要素およびその設定を制御するためのプロパティは提供されません。バインド要素へのアクセスと設定の変更は、バインド要素を含むコレクションを通じて行います。詳細については、「[カスタム バインディング](../../../../docs/framework/wcf/extending/custom-bindings.md)」を参照してください。  
  
## このセクションの内容  
 [システムが提供するバインディングの構成](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 一般的なシナリオをサポートするために [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に用意されたバインディングを使用および変更する方法について説明します。  
  
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/ja-jp/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 サービスおよびクライアントで使用する [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] バインディングをコードで強制的に定義する方法と、構成を使用して宣言によって定義する方法について説明します。  
  
 [カスタム バインディング](../../../../docs/framework/wcf/extending/custom-bindings.md)  
 <xref:System.ServiceModel.Channels.CustomBinding> の概要と使用する状況について説明します。  
  
## 関連項目  
 <xref:System.ServiceModel.Channels.Binding>  
  
 <xref:System.ServiceModel.Channels.BindingElement>  
  
 <xref:System.ServiceModel.Channels.CustomBinding>  
  
## 関連項目  
 [バインディングの拡張](../../../../docs/framework/wcf/extending/extending-bindings.md)