---
title: "RefType 結果を返すクエリの実行方法 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "ESQL"
  - "jsharp"
ms.assetid: 7dbbfbcd-93f5-4546-9dbf-e5fa290b69fa
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# RefType 結果を返すクエリの実行方法
このトピックでは、<xref:System.Data.EntityClient.EntityCommand> オブジェクトを使用して概念モデルに対してコマンドを実行する方法と、<xref:System.Data.EntityClient.EntityDataReader> を使用して <xref:System.Data.Metadata.Edm.RefType> の結果を取得する方法を示します。  
  
### この例のコードを実行するには  
  
1.  [AdventureWorks Sales Model](http://msdn.microsoft.com/ja-jp/f16cd988-673f-4376-b034-129ca93c7832) をプロジェクトに追加して、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] を使用するようにプロジェクトを構成します。  詳細については、「[How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/ja-jp/dadb058a-c5d9-4c5c-8b01-28044112231d)」を参照してください。  
  
2.  アプリケーションのコード ページで、次の `using` ステートメント \(Visual Basic の場合は `Imports`\) を追加します。  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## 使用例  
 この例は、<xref:System.Data.Metadata.Edm.RefType> の結果を返すクエリを実行します。  次のクエリを引数として `ExectueRefTypeQuery` 関数に渡すと、関数はエンティティへの参照を返します。  
  
 [!code-csharp[DP EntityServices Concepts#REF2](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#ref2)]
 [!code-sql[DP EntityServices Concepts#REF2](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#ref2)]  
  
 パラメーター化されたクエリを渡す場合は、次のように、<xref:System.Data.EntityClient.EntityCommand> オブジェクトの <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> プロパティに <xref:System.Data.EntityClient.EntityParameter> オブジェクトを追加します。  
  
 [!code-csharp[DP EntityServices Concepts#REF3](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#ref3)]
 [!code-sql[DP EntityServices Concepts#REF3](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#ref3)]  
  
 [!code-csharp[DP EntityServices Concepts#eSQLRefTypes](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#esqlreftypes)]
 [!code-vb[DP EntityServices Concepts#eSQLRefTypes](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#esqlreftypes)]  
  
## 参照  
 [Entity SQL リファレンス](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)   
 [Entity Framework 用の EntityClient プロバイダー](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)