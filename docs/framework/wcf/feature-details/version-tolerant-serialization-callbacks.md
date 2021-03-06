---
title: "バージョン トレラントなシリアル化コールバック | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "OnDeserializedAttribute [WCF]"
  - "OnDeserializingAttribute [WCF]"
  - "OnSerializedAttribute [WCF]"
  - "OnSerializingAttribute [WCF]"
  - "シリアル化 [WCF], 既定値の設定"
ms.assetid: aa4a3a6f-05ec-4efd-bdbf-2181e13e6468
caps.latest.revision: 17
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 17
---
# バージョン トレラントなシリアル化コールバック
データ コントラクトのプログラミング モデルでは、<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> クラスと <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> クラスがサポートする、複数のバージョンに対応するシリアル化コールバック メソッドが完全にサポートされます。  
  
## 複数のバージョンに対応する属性  
 4 つのコールバック属性があります。各属性は、さまざまなタイミングでシリアル化エンジンまたは逆シリアル化エンジンが呼び出すメソッドに適用できます。次の表では、各属性を使用するタイミングについて説明します。  
  
|属性|対応するメソッドが呼び出されるタイミング|  
|--------|--------------------------|  
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|型をシリアル化する前に呼び出されます。|  
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|型をシリアル化した後に呼び出されます。|  
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|型を逆シリアル化する前に呼び出されます。|  
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|型を逆シリアル化した後に呼び出されます。|  
  
 メソッドは、<xref:System.Runtime.Serialization.StreamingContext> パラメーターを受け入れる必要があります。  
  
 これらのメソッドは、主にバージョン管理と初期化に使用するためのものです。逆シリアル化時にコンストラクターは呼び出されません。このため、データ メンバーのデータが受信ストリームにない場合、たとえば、データの送信元が、一部のデータ メンバーが不足している前のバージョンの型である場合、そのデータ メンバーを目的の既定値に適切に初期化できないことがあります。これを修正するには、次の例で示すように、<xref:System.Runtime.Serialization.OnDeserializingAttribute> でマークされたコールバック メソッドを使用します。  
  
 上記の各コールバック属性でマークできるのは、型ごとに 1 つのメソッドだけです。  
  
### 例  
 [!code-csharp[C_DataContract#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#9)]
 [!code-vb[C_DataContract#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#9)]  
  
## 参照  
 <xref:System.Runtime.Serialization.OnSerializingAttribute>   
 <xref:System.Runtime.Serialization.OnSerializedAttribute>   
 <xref:System.Runtime.Serialization.OnDeserializingAttribute>   
 <xref:System.Runtime.Serialization.OnDeserializedAttribute>   
 <xref:System.Runtime.Serialization.StreamingContext>   
 [バージョン トレラントなシリアル化](../../../../docs/framework/serialization/version-tolerant-serialization.md)