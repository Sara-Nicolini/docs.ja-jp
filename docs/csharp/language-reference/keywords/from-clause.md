---
title: "from 句 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- from_CSharpKeyword
- from
dev_langs:
- CSharp
helpviewer_keywords:
- from clause [C#]
- from keyword [C#]
ms.assetid: 1aefd18c-1314-47f8-99ec-9bcefb09e699
caps.latest.revision: 27
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: f0165144acfa8d0928015e8222179f7e69f19644
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="from-clause-c-reference"></a>from 句 (C# リファレンス)
クエリ式は、`from` 句で始める必要があります。 また、クエリ式にはサブクエリを含めることができます。サブクエリも `from` 句で始めます。 `from` 句は次を指定します。  
  
-   クエリまたはサブクエリを実行するデータ ソース。  
  
-   ソース シーケンスの各要素を表す、ローカルの*範囲変数*。  
  
 範囲変数とデータ ソースの両方は厳密に型指定されます。 `from` 句で参照されるデータ ソースには、<xref:System.Collections.IEnumerable> 型、<xref:System.Collections.Generic.IEnumerable%601> 型、あるいは <xref:System.Linq.IQueryable%601> のような派生型が含まれている必要があります。  
  
 次の例では、`numbers` はデータ ソースであり、`num` は範囲変数です。 [var](../../../csharp/language-reference/keywords/var.md) キーワードが使用されていても、両方の変数が厳密に型指定されていることに注目してください。  
  
 [!code-cs[cscsrefQueryKeywords#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/from-clause_1.cs)]  
  
## <a name="the-range-variable"></a>範囲変数  
 データ ソースが <xref:System.Collections.Generic.IEnumerable%601> を実装するとき、コンパイラは範囲変数の型を推測します。 たとえば、ソースの型が `IEnumerable<Customer>` の場合、範囲変数は `Customer` ではないかと推測されます。 ソースが <xref:System.Collections.ArrayList> のような非ジェネリック `IEnumerable` 型のときにのみ、型を明示的に指定する必要があります。 詳細については、「[How to: Query an ArrayList with LINQ](http://msdn.microsoft.com/library/c318b79a-fa4d-4de3-b62d-c1162beb267e)」(方法: LINQ を使用して ArrayList を照会する) を参照してください。  
  
 前述の例では、`num` は型 `int` として推測されます。 範囲変数は厳密に型指定されるため、範囲変数の上でメソッドを呼び出したり、他の操作で範囲変数を使用したりできます。 たとえば、`select num` を記述する代わりに、`select num.ToString()` を記述し、クエリ式が整数ではなく文字列のシーケンスを返すようにできます。 あるいは、式でシーケンス 14、11、13、12、10 を返すように `select n + 10` を記述できます。 詳細については、「[select 句](../../../csharp/language-reference/keywords/select-clause.md)」をご覧ください。  
  
 範囲変数は [foreach](../../../csharp/language-reference/keywords/foreach-in.md) ステートメントの繰り返し変数に似ていますが、1 つだけ非常に重要な違いがあります。範囲変数がソースのデータを格納することは決してありません。 これは構文上の利便性のためです。クエリの実行時に何が起こるのかクエリで表現できます。 詳細については、「[LINQ クエリの概要 (C#)](../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)」を参照してください。  
  
## <a name="compound-from-clauses"></a>複合 from 句  
 ソース シーケンスの各要素がそれ自体シーケンスになったり、それ自体にシーケンスが含まれたりすることがあります。 たとえば、データ ソースが `IEnumerable<Student>` になることがあります。この場合、シーケンスの各学生オブジェクト参照にテストの点数の一覧が含まれます。 各 `Student` 要素内の内部一覧にアクセスするには、複合 `from` 句を利用できます。 この手法は、[foreach](../../../csharp/language-reference/keywords/foreach-in.md) ステートメントを入れ子にして使う場合に似ています。 [where](../../../csharp/language-reference/keywords/partial-method.md) 句または [orderby](../../../csharp/language-reference/keywords/orderby-clause.md) 句をいずれかの `from` 句に追加し、結果を絞り込むことができます。 次は、`Student` オブジェクトのシーケンスの例です。テストの点数を表す整数の内部 `List` がそれぞれに含まれています。 内部一覧にアクセスするには、複合 `from` 句を利用できます。 必要に応じて、2 つの `from` 句の間に句を挿入できます。  
  
 [!code-cs[cscsrefQueryKeywords#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/from-clause_2.cs)]  
  
## <a name="using-multiple-from-clauses-to-perform-joins"></a>複数の from 句を使用して結合を実行する  
 複合 `from` 句を使用し、単一データ ソースの内部コレクションにアクセスします。 ただし、個別データ ソースから補足クエリを生成する複数の `from` 句をクエリに含めることもできます。 この手法では、[join 句](../../../csharp/language-reference/keywords/join-clause.md)で不可能な特定の結合操作を実行できます。  
  
 2 つの `from` 句を使用し、2 つのデータ ソースの完全なクロス結合を作る様子を示したのが次の例です。  
  
 [!code-cs[cscsrefQueryKeywords#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/from-clause_3.cs)]  
  
 複数の `from` 句を使用する結合操作の詳細については、「[方法 : カスタム結合操作を実行する](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-custom-join-operations.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [クエリ キーワード (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md)   
 [LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md)

