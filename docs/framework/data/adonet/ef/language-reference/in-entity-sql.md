---
title: "IN (Entity SQL) | Microsoft Docs"
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
ms.assetid: 51662950-ee01-4857-b7b9-311dd8515966
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# IN (Entity SQL)
コレクション内に一致する値があるかどうかを調べます。  
  
## 構文  
  
```  
  
value [ NOT ] IN expression  
```  
  
## 引数  
 `value`  
 照合する値を返す任意の有効な式。  
  
 \[ NOT \]  
 IN の `Boolean` 型の結果を否定することを指定します。  
  
 `expression`  
 一致の判定対象のコレクションを返す任意の有効な式。 すべての式は、`value` と同じ型であるか、共通の基本型または派生型である必要があります。  
  
## 戻り値  
 コレクションに値が見つかった場合は `true`、値が null またはコレクションが null の場合は null、それ以外の場合は `false` が返されます。 NOT IN を使用すると、IN の結果が否定されます。  
  
## 使用例  
 次の Entity SQL クエリでは、IN 演算子を使用して、コレクション内に一致する値があるかどうかを調べます。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1.  「[StructuralType 結果を返すクエリの実行方法](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。  
  
2.  次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。  
  
 [!code-csharp[DP EntityServices Concepts 2#IN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#in)]  
  
## 参照  
 [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)