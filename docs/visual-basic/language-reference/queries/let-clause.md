---
title: Let 句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryLet
helpviewer_keywords:
- queries [Visual Basic], Let
- Let clause [Visual Basic]
- Let statement [Visual Basic]
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
ms.openlocfilehash: 88166a040823cfefe623f672e556c364d652a7fc
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004732"
---
# <a name="let-clause-visual-basic"></a>Let 句 (Visual Basic)
値を計算し、クエリ内の新しい変数に代入します。  
  
## <a name="syntax"></a>構文  
  
```vb  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a>指定項目  
  
|項目|定義|  
|---|---|  
|`variable`|必須。 指定された式の結果を参照するために使用できるエイリアス。|  
|`expression`|必須。 評価され、指定された変数に割り当てられる式。|  
  
## <a name="remarks"></a>コメント  
 @No__t-0 句を使用すると、各クエリ結果の値を計算し、別名を使用してその値を参照できます。 別名は、`Where` 句などの他の句で使用できます。 @No__t-0 句を使用すると、クエリに含まれる式の句の別名を指定し、expression 句が使用されるたびに別名を置き換えることができるので、読みやすいクエリステートメントを作成できます。  
  
 @No__t-2 句には、任意の数の @no__t 0 と @no__t の割り当てを含めることができます。 各割り当てはコンマ (,) で区切ります。  
  
## <a name="example"></a>例  
 次のコード例では、`Let` 句を使用して、製品に対して 10% の割引を計算します。  
  
 [!code-vb[VbSimpleQuerySamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#16)]  
  
## <a name="see-also"></a>関連項目

- [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [クエリ](../../../visual-basic/language-reference/queries/index.md)
- [Select 句](../../../visual-basic/language-reference/queries/select-clause.md)
- [From 句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Where 句](../../../visual-basic/language-reference/queries/where-clause.md)
