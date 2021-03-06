---
title: "重要なトレース | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 40a1770e-3b09-4142-b0dd-f9ef73642074
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# 重要なトレース
ここでは、[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] によって出力される主要なトレースの一部を示します。  
  
## 重要なトレース  
  
|トレース|説明|  
|----------|--------|  
|Message Log トレース|このトレースは、`System.ServiceModel.MessageLogging` トレース ソースが有効な場合に、メッセージ ログ機能によって [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] メッセージがログに記録されるときに出力されます。このトレースをクリックすると、メッセージが表示されます。メッセージには、構成可能なログ ポイントが 4 つ \(`ServiceLevelSendRequest`、`TransportSend`、`TransportReceive`、`ServiceLevelReceiveRequest`\) あり、これらは、メッセージ ログ トレースの Message Source 属性にも示されます。|  
|Message Received トレース|このトレースは、`System.ServiceModel` トレース ソースが Information レベルか Verbose レベルで有効な場合に、[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] メッセージが受信されるときに出力されます。このトレースはアクティビティのグラフ ビューでメッセージの相関矢印を表示するために必要です。|  
|Message Sent トレース|このトレースは、`System.ServiceModel` トレース ソースが Information レベルか Verbose レベルで有効な場合に、[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] メッセージが送信されるときに出力されます。このトレースはアクティビティのグラフ ビューでメッセージの相関矢印を表示するために必要です。|  
|Get ChannelEndpointElement|このトレースは、情報レベルで Construct チャネル ファクトリに出力されます。このトレースには、クライアントが対話しているエンドポイントの説明 \(リモート アドレス、バインディング、コントラクト名など\) が表示されます。|  
|Get ServiceElement|このトレースは、情報レベルで Construct サービス ホストに出力されます。サービス コントラクトとバインディングの説明が提供されます。|  
|SocketConnection Create|このトレースは、クライアントによって実行される最初の "プロセス" アクションおよびサービスの "バイトを受信" アクティビティで出力されます。ローカルとリモートの IP アドレスを提供します。情報レベルで出力されます。|