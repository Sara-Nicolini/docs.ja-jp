---
title: "XML entity references are not supported | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc31180"
  - "bc31180"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC31180"
ms.assetid: 2a393327-d8e2-4187-85b1-642b4f53b4ae
caps.latest.revision: 6
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 6
---
# XML entity references are not supported
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

XML 1.0 仕様で定義されていないエンティティ参照 \(たとえば `©`\) が XML リテラルの値として組み込まれています。  XML リテラルでサポートされている XML エンティティ参照は、`&`、`"`、`<`、`>`、`'` だけです。  
  
 **エラー ID:** BC31180  
  
### このエラーを解決するには  
  
-   サポートされていないエンティティ参照を削除します。  
  
## 参照  
 [XML Literals and the XML 1.0 Specification](../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)   
 [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md)   
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)