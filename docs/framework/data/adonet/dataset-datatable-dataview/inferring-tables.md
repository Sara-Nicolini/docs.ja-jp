---
title: "テーブルの推論 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# テーブルの推論
XML ドキュメントから <xref:System.Data.DataSet> のスキーマを推論するときには、ADO.NET では、テーブルを表す XML 要素を最初に決定します。  次に示すいくつかの XML 構造は、**DataSet** スキーマのテーブルとして推論されます。  
  
-   属性を持つ要素  
  
-   子要素を持つ要素  
  
-   繰り返し出現する要素  
  
## 属性を持つ要素  
 要素に属性が指定されている場合は、それらの要素はテーブルとして推論されます。  たとえば、次のような XML があるとします。  
  
```  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 推論プロセスにより、"Element1" という名前のテーブルが生成されます。  
  
 **DataSet:** DocumentElement  
  
 **Table:** Element1  
  
|attr1|Element1\_Text|  
|-----------|--------------------|  
|value1||  
|value2|Text1|  
  
## 子要素を持つ要素  
 子要素を持つ要素は、テーブルとして推論されます。  たとえば、次のような XML があるとします。  
  
```  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 推論プロセスにより、"Element1" という名前のテーブルが生成されます。  
  
 **DataSet:** DocumentElement  
  
 **Table:** Element1  
  
|ChildElement1|  
|-------------------|  
|Text1|  
  
 ドキュメント \(ルート\) 要素に属性または子要素があり、それらが列として推論される場合には、そのドキュメント要素はテーブルとして推論されます。  ドキュメント要素の属性や子要素が列として推論されない場合には、そのドキュメント要素は **DataSet** として推論されます。  たとえば、次のような XML があるとします。  
  
```  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 推論プロセスにより、"DocumentElement" という名前のテーブルが生成されます。  
  
 **DataSet:** NewDataSet  
  
 **Table:** DocumentElement  
  
|Element1|Element2|  
|--------------|--------------|  
|Text1|Text2|  
  
 または、次のような XML があるとします。  
  
```  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 推論プロセスにより、"Element1" という名前のテーブルを含む "DocumentElement" という名前の **DataSet** が生成されます。  
  
 **DataSet:** DocumentElement  
  
 **Table:** Element1  
  
|attr1|attr2|  
|-----------|-----------|  
|value1|value2|  
  
## 繰り返し出現する要素  
 繰り返し出現する要素は、単一のテーブルとして推論されます。  たとえば、次のような XML があるとします。  
  
```  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 推論プロセスにより、"Element1" という名前のテーブルが生成されます。  
  
 **DataSet:** DocumentElement  
  
 **Table:** Element1  
  
|Element1\_Text|  
|--------------------|  
|Text1|  
|Text2|  
  
## 参照  
 [XML からの DataSet リレーショナル構造の推論](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)   
 [XML からの DataSet の読み込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)   
 [XML の DataSet スキーマ情報の読み込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)   
 [DataSet での XML の使用](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)   
 [DataSets、DataTables、および DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)