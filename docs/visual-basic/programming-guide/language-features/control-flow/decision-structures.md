---
title: 条件判断構造 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- If statement [Visual Basic], decision structures
- If statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], decision structures
- decision structures [Visual Basic]
- conditional statements [Visual Basic], decision structures
ms.assetid: 2e2e0895-4483-442a-b17c-26aead751ec2
ms.openlocfilehash: f0df649c4be50e9cadd51258c89137b68b4ffe22
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963199"
---
# <a name="decision-structures-visual-basic"></a>条件判断構造 (Visual Basic)
Visual Basic を使用すると、テストの結果に応じて、条件をテストしたり、さまざまな操作を実行したりできます。 true または false の場合、さまざまな値の式、または一連のステートメントを実行するときに生成された例外のさまざまな条件をテストできます。  
  
 次の図は、条件が true であるかどうかをテストし、true であるか false であるかに応じて異なるアクションを実行するデシジョン構造を示しています。  
  
 ![If...Then...Else 構築。](./media/decision-structures/if-then-else-construction.gif)  
  
## <a name="ifthenelse-construction"></a>If...Then...Else 構造  
 `If...Then...Else`構造を使用すると、1つ以上の条件をテストし、各条件に応じて1つ以上のステートメントを実行できます。 条件をテストし、次の方法でアクションを実行することができます。  
  
- 条件がの場合に1つ以上のステートメントを実行する`True`  
  
- 条件がの場合に1つ以上のステートメントを実行する`False`  
  
- 条件が`True`の場合はステートメントを実行し、それ以外の場合は`False`  
  
- 前の条件がの場合に追加条件をテストする`False`  
  
 これらすべての可能性を提供する制御構造が、[If...Then...Else ステートメント](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)です。 1つのテストと1つのステートメントを実行するだけの場合は、単一行バージョンを使用できます。 より複雑な条件とアクションのセットがある場合は、複数行のバージョンを使用できます。  
  
## <a name="selectcase-construction"></a>Select...Case 構造  
 この`Select...Case`構築により、式を1回評価し、さまざまな値に基づいてさまざまなステートメントのセットを実行できます。 詳細については、[Select...Case ステートメント](../../../../visual-basic/language-reference/statements/select-case-statement.md)を参照してください。  
  
## <a name="trycatchfinally-construction"></a>Try...Catch...Finally 構造  
 `Try...Catch...Finally`構造を使用すると、ステートメントのいずれかによって例外が発生した場合にコントロールを保持する環境で、一連のステートメントを実行できます。 例外ごとに異なるアクションを実行できます。 必要に応じて、実行するコードのブロックを指定して、 `Try...Catch...Finally`何が発生したかにかかわらず、構築全体を終了する必要があります。 詳細については、[Try...Catch...Finally ステートメント](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)を参照してください。  
  
> [!NOTE]
> 多くの制御構造では、キーワードをクリックすると、構造内のすべてのキーワードが強調表示されます。 たとえば、 `If...Then...Else`構築をクリック`If`すると、、 `Then` `ElseIf`、、 `Else`、および`If` `End If`のすべてのインスタンスが構築されます。 次または前の強調表示されたキーワードに移動するには、CTRL + SHIFT + ↓キーを押すか、CTRL + SHIFT + 上方向キーを押します。  
  
## <a name="see-also"></a>関連項目

- [制御フロー](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [ループ構造](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [その他の制御構造](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [入れ子になった制御構造](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [If 演算子](../../../../visual-basic/language-reference/operators/if-operator.md)
