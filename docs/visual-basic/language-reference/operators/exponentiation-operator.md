---
title: ^ 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.^
helpviewer_keywords:
- raising numbers to powers
- ^ operator [Visual Basic], exponentiation
- square operator [Visual Basic]
- ^ operator [Visual Basic]
- exponentiation operator [Visual Basic]
- exponent
- numbers [Visual Basic], rasing
- powers
- arithmetic operators [Visual Basic], exponentiation
ms.assetid: d89a1ca8-83da-4784-a87b-a9d7dceb3f62
ms.openlocfilehash: 8cdfbec917608211e19c39eb37bd12dbc7c4d33f
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592220"
---
# <a name="-operator-visual-basic"></a>^ 演算子 (Visual Basic)

数値を別の数値のべき乗で累乗します。

## <a name="syntax"></a>構文

```vb
number ^ exponent
```

## <a name="parts"></a>指定項目

`number`\
必須。 任意の数式。

`exponent`\
必須。 任意の数式。

## <a name="result"></a>結果

結果は、`exponent` の累乗に0を @no__t、常に `Double` の値として生成されます。

## <a name="supported-types"></a>サポートされている型

`Double`。 異なる型のオペランドは `Double` に変換されます。

## <a name="remarks"></a>コメント

Visual Basic は、常に[Double データ型](../../../visual-basic/language-reference/data-types/double-data-type.md)の指数演算を実行します。

@No__t-0 の値には、小数、負、またはその両方を指定できます。

1つの式で複数の指数演算が実行された場合、@no__t 0 演算子は左から右に検出されたときに評価されます。

> [!NOTE]
> @No__t-0 演算子は*オーバーロード*できます。つまり、クラスまたは構造体がそのクラスまたは構造体の型を持つ場合に、クラスまたは構造体がその動作を再定義できます。 コードでこのようなクラスまたは構造体に対してこの演算子を使用する場合は、再定義された動作を理解していることを確認してください。 詳細については、「 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。

## <a name="example"></a>例

次の例では、`^` 演算子を使用して指数の指数部に数値を累乗します。 結果は、2番目のオペランドの累乗になります。

[!code-vb[VbVbalrOperators#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#20)]

前の例では、次の結果が生成されます。

`exp1` は 4 (2 乗) に設定されます。

`exp2` は 19683 (3 キューブ、その値キューブ) に設定されます。

`exp3` は-125 (-5 キューブ) に設定されます。

`exp4` は 625 (-5 ~ 4 乗) に設定されます。

`exp5` は 2 (キューブルートは 8) に設定されます。

`exp6` は0.5 に設定されます (1.0 が8のルートで割った値)。

前の例の式では、かっこの重要性に注意してください。 演算子の*優先順位*により、Visual Basic は、単項 `–` 演算子でも、通常は `^` 演算子を実行します。 @No__t-0 および `exp6` がかっこなしで計算された場合、次の結果が生成されます。

`exp4 = -5 ^ 4` は– (5 ~ 4 乗) として計算されます。この場合、-625 となります。

`exp6 = 8 ^ -1.0 / 3.0` は、(8 から-1 の累乗または 0.125) を3.0 で割った値として計算され、0.041666666666666666666666666666667 になります。

## <a name="see-also"></a>関連項目

- [^= 演算子](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [算術演算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic の算術演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
