---
title: データの並べ替え (C#)
ms.date: 07/20/2015
ms.assetid: d93fa055-2f19-46d2-9898-e2aed628f1c9
ms.openlocfilehash: 28cf4025d0b9bca841695c9873a0ff7972726b98
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591043"
---
# <a name="sorting-data-c"></a>データの並べ替え (C#)
並べ替え操作では、1 つ以上の属性に基づいてシーケンスの要素を並べ替えます。 並べ替えの第 1 条件で、要素に対して一回目の並べ替えが実行されます。 第 2 条件を指定すると、第 1 条件で並べ替えられた各グループ内の要素を並べ替えることができます。  
  
 次の図は、文字のシーケンスに対してアルファベット順の並べ替え操作を実行した結果を示しています。 
  
 ![アルファベット順の並べ替え操作を示している図。](./media/sorting-data/alphabetical-sort-operation.png)  
  
 次のセクションでは、データの並べ替えを実行する標準クエリ演算子のメソッドの一覧を示します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド名|説明|C# のクエリ式の構文|詳細情報|  
|-----------------|-----------------|---------------------------------|----------------------|  
|OrderBy|値を昇順に並べ替えます。|`orderby`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|OrderByDescending|値を降順に並べ替えます。|`orderby … descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|ThenBy|2 番目の並べ替えを昇順で実行します。|`orderby …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|ThenByDescending|2 番目の並べ替えを降順で実行します。|`orderby …, … descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|Reverse|コレクションの要素の順序を反転させます。|適用不可。|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>クエリ式の構文例  
  
### <a name="primary-sort-examples"></a>1 番目の並べ替えの例  
  
#### <a name="primary-ascending-sort"></a>1 番目の並べ替え (昇順)  
 次の例は、LINQ クエリで `orderby` 句を使用して、配列内の文字列を文字列長に従って昇順に並べ替える方法を示しています。  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Length  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
    quick  
    brown  
    jumps  
*/  
```  
  
#### <a name="primary-descending-sort"></a>1 番目の並べ替え (降順)  
 次の例は、LINQ クエリで `orderby descending` 句を使用して、文字列を最初の文字に従って降順に並べ替える方法を示しています。  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Substring(0, 1) descending  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    quick  
    jumps  
    fox  
    brown  
*/  
```  
  
### <a name="secondary-sort-examples"></a>2 番目の並べ替えの例  
  
#### <a name="secondary-ascending-sort"></a>2 番目の並べ替え (昇順)  
 次の例は、LINQ クエリで `orderby` 句を使用して、配列内の文字列に対して 1 番目および 2 番目の並べ替えを実行する方法を示しています。 文字列は、最初に文字列長を基準として、次に文字列の最初の文字を基準として、どちらも昇順に並べ替えられます。  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Length, word.Substring(0, 1)  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    fox  
    the  
    brown  
    jumps  
    quick  
*/  
```  
  
#### <a name="secondary-descending-sort"></a>2 番目の並べ替え (降順)  
 次の例は、LINQ クエリで `orderby descending` 句を使用して、1 番目の並べ替えを昇順で実行し、2 番目の並べ替えを降順で実行する方法を示しています。 各文字列は、最初に文字列長を基準として、次に文字列の最初の文字を基準として並べ替えられます。  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Length, word.Substring(0, 1) descending  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
    quick  
    jumps  
    brown  
*/  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Linq>
- [標準クエリ演算子の概要 (C#)](./standard-query-operators-overview.md)
- [orderby 句](../../../language-reference/keywords/orderby-clause.md)
- [方法: Join 句の結果の順序指定](../../linq-query-expressions/how-to-order-the-results-of-a-join-clause.md)
- [方法: 任意の単語またはフィールドを基準にテキスト データの並べ替えまたはフィルター処理を実行する (LINQ) (C#)](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
