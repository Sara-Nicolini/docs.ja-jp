---
title: "入れ子になったグループの作成"
description: "入れ子になったグループを作成する方法。"
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: e9f00708-362e-4d13-98c5-d77549347ba0
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 361ac1f224c6eef292fcf8434c7e465c9448b19c
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="create-a-nested-group"></a>入れ子になったグループの作成

LINQ クエリ式で入れ子になったグループを作成する方法を次の例に示します。 学年レベルに基づいて作成した各グループを、さらに個人の名前に基づくグループに分割します。  
  
## <a name="example"></a>例

 > [!NOTE]
 > この例には、「[オブジェクトのコレクションの照会](query-a-collection-of-objects.md)」のサンプル コードで定義されているオブジェクトへの参照が含まれています。 

 [!code-cs[csProgGuideLINQ#24](../../../samples/snippets/csharp/concepts/linq/how-to-create-a-nested-group_1.cs)]  
  
 入れ子になったグループの内部要素に対して反復処理を実行するために、入れ子になった `foreach` ループが 3 つ必要であることに注意してください。  
  
## <a name="see-also"></a>関連項目  
 [LINQ クエリ式](index.md)

