---
title: Nothing (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Nothing
- vb.Nothing
helpviewer_keywords:
- Nothing keyword [Visual Basic]
- Nothing keyword [Visual Basic], syntax
ms.assetid: 06176e2d-bbf7-4a37-afaa-a86ad21ee99f
ms.openlocfilehash: 12c88db49dc7723fc269195e7d174bfa822c64d3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963757"
---
# <a name="nothing-visual-basic"></a>Nothing (Visual Basic)
任意のデータ型の既定値を表します。 参照型の場合、既定値は`null`参照です。 値型の場合、既定値は、値型が null 値を許容するかどうかによって異なります。  
  
> [!NOTE]
> Null 非許容の値型の`Nothing`場合、Visual Basic の`null`はC#とでは異なります。 Visual Basic で、null 非許容の値型の変数をに`Nothing`設定すると、変数は宣言された型の既定値に設定されます。 でC#は、null 非許容の値型の変数をに`null`割り当てた場合、コンパイル時エラーが発生します。  
  
## <a name="remarks"></a>Remarks  
 `Nothing`データ型の既定値を表します。 既定値は、変数が値型であるか、参照型であるかによって異なります。  
  
 *値型*の変数には、その値が直接含まれています。 値型には、すべての数値`Boolean`データ`Char`型`Date`、、、、すべての構造体、およびすべての列挙が含まれます。 *参照型*の変数は、メモリ内のオブジェクトのインスタンスへの参照を格納します。 参照型には、クラス、配列、デリゲート、および文字列が含まれます。 詳細については、「 [値型と参照型](../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)」を参照してください。  
  
 変数が値型の場合、の`Nothing`動作は、変数が null 許容型かどうかによって異なります。 Null 許容値型を表すには、 `?`型名に修飾子を追加します。 Null `Nothing`許容変数に割り当てると、値が`null`に設定されます。 詳細と例については、「 [Null 許容値型](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)」を参照してください。  
  
 変数が null 値が許容されない値型である場合`Nothing` 、に割り当てると、宣言された型の既定値に設定されます。 その型に変数メンバーが含まれている場合は、すべてが既定値に設定されます。 次の例では、スカラー型について説明します。  
  
 [!code-vb[VbVbalrKeywords#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class2.vb#7)]  
  
 変数が参照型の場合、変数にを`Nothing`割り当てると、変数の型の`null`参照に設定されます。 `null`参照に設定されている変数は、どのオブジェクトにも関連付けられていません。 次に例を示します。  
  
 [!code-vb[VbVbalrKeywords#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class3.vb#8)]  
  
 参照 (または null 許容値型) 変数が`null`であるかどうかを確認する場合は、または`<> Nothing`を使用`= Nothing`しないでください。 常に`Is Nothing`また`IsNot Nothing`はを使用します。  
  
 Visual Basic 内の文字列の場合、空の`Nothing`文字列はと等しくなります。 したがって`"" = Nothing` 、は true になります。  
  
 次の例は、演算子`Is`と`IsNot`演算子を使用する比較を示しています。  
  
 [!code-vb[VbVbalrKeywords#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class4.vb#9)]  
  
 `As`句を使用せずに変数を宣言し、に設定`Nothing`すると、 `Object`変数の型はになります。 たとえば、の`Dim something = Nothing`ようになります。 この場合`Option Strict` 、がオンになっていて、がオフ`Option Infer`になっていると、コンパイル時エラーが発生します。  
  
 をオブジェクト変数`Nothing`に割り当てると、オブジェクトインスタンスを参照しなくなります。 変数が以前にインスタンスを参照していた場合、 `Nothing`に設定すると、インスタンス自体は終了しません。 インスタンスが終了し、そのインスタンスに関連付けられているメモリおよびシステムリソースが解放されるのは、ガベージコレクター (GC) によってアクティブな参照が残っていないことが検出された後のみです。  
  
 `Nothing`は、初期<xref:System.DBNull>化されていない variant または存在しないデータベース列を表すオブジェクトとは異なります。  
  
## <a name="see-also"></a>関連項目

- [Dim ステートメント](../../visual-basic/language-reference/statements/dim-statement.md)
- [オブジェクトの有効期間:オブジェクトの作成方法と破棄方法](../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [Visual Basic の有効期間](../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Is 演算子](../../visual-basic/language-reference/operators/is-operator.md)
- [IsNot 演算子](../../visual-basic/language-reference/operators/isnot-operator.md)
- [null 許容値型](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
