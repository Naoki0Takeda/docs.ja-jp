---
title: Delegate ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Delegate
helpviewer_keywords:
- delegate keyword [Visual Basic]
- Delegate statement [Visual Basic]
ms.assetid: f799c518-0817-40cc-ad0b-4da846fdba57
ms.openlocfilehash: 4a8260da4d2224551de71fd54f734007c7fa214f
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583456"
---
# <a name="delegate-statement"></a>Delegate ステートメント
デリゲートを宣言するために使用されます。 デリゲートは、型の `Shared` メソッドまたはオブジェクトのインスタンスメソッドを参照する参照型です。 パラメーターと戻り値の型が一致するプロシージャを使用すると、このデリゲートクラスのインスタンスを作成できます。 このプロシージャは、後でデリゲートインスタンスを使用して呼び出すことができます。  
  
## <a name="syntax"></a>構文  
  
```vb  
[ <attrlist> ] [ accessmodifier ] _  
[ Shadows ] Delegate [ Sub | Function ] name [( Of typeparamlist )] [([ parameterlist ])] [ As type ]  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`attrlist`|省略可能です。 このデリゲートに適用される属性のリスト。 複数の属性を指定するときは、コンマで区切ります。 [属性リスト](../../../visual-basic/language-reference/statements/attribute-list.md)は山かっこ ("`<`" と "`>`") で囲む必要があります。|  
|`accessmodifier`|省略可能です。 デリゲートにアクセスできるコードを指定します。 次のいずれかの値を指定します。<br /><br /> - [パブリック](../../../visual-basic/language-reference/modifiers/public.md)です。 デリゲートを宣言する要素にアクセスできるすべてのコードは、それにアクセスできます。<br />-   [保護さ](../../../visual-basic/language-reference/modifiers/protected.md)れています。 デリゲートのクラスまたは派生クラス内のコードだけがアクセスできます。<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)。 同じアセンブリ内のコードだけが、デリゲートにアクセスできます。<br />- [プライベート](../../../visual-basic/language-reference/modifiers/private.md)です。 デリゲートを宣言する要素内のコードだけがアクセスできます。<br /><br /> デリゲートのクラス、派生クラス、または同じアセンブリ内の[Protected Friend](../../language-reference/modifiers/protected-friend.md)のみのコード - 、デリゲートにアクセスできます。 <br />デリゲートのクラス内または同じアセンブリ内の派生クラス内の[プライベートに保護された](../../language-reference/modifiers/private-protected.md)コードのみを - 、デリゲートにアクセスできます。 |  
|`Shadows`|省略可能です。 このデリゲートが、基底クラスで同じ名前を持つプログラミング要素、またはオーバーロードされた要素のセットを直しして非表示にすることを示します。 宣言された要素は、他の任意の種類の要素でシャドウできます。<br /><br /> シャドウされた要素は、その要素をシャドウする派生クラスからは使用できません。ただし、シャドウする要素がアクセスできない要素の場合は例外です。 たとえば、`Private` 要素が基本クラス要素をシャドウする場合、`Private` 要素にアクセスするためのアクセス許可を持たないコードは、代わりに基本クラス要素にアクセスします。|  
|`Sub`|省略可能ですが、`Sub` または `Function` のいずれかが表示されている必要があります。 このプロシージャを、値を返さないデリゲート `Sub` プロシージャとして宣言します。|  
|`Function`|省略可能ですが、`Sub` または `Function` のいずれかが表示されている必要があります。 このプロシージャを、値を返すデリゲート `Function` プロシージャとして宣言します。|  
|`name`|必須です。 デリゲート型の名前。標準の変数の名前付け規則に従います。|  
|`typeparamlist`|省略可能です。 このデリゲートの型パラメーターのリスト。 複数の型パラメーターは、コンマで区切ります。 必要に応じて、`In` および `Out` ジェネリック修飾子を使用して、各型パラメーターをバリアントとして宣言できます。 [型リスト](../../../visual-basic/language-reference/statements/type-list.md)をかっこで囲み、`Of` キーワードと共に導入する必要があります。|  
|`parameterlist`|省略可能です。 呼び出されたときにプロシージャに渡されるパラメーターのリスト。 [パラメーターリスト](../../../visual-basic/language-reference/statements/parameter-list.md)はかっこで囲む必要があります。|  
|`type`|@No__t_0 プロシージャを指定する場合は必須です。 戻り値のデータ型。|  
  
## <a name="remarks"></a>Remarks  
 @No__t_0 ステートメントは、デリゲートクラスのパラメーターと戻り値の型を定義します。 パラメーターと戻り値の型が一致するプロシージャを使用すると、このデリゲートクラスのインスタンスを作成できます。 デリゲートの `Invoke` メソッドを呼び出すことによって、後でデリゲートインスタンスを使用してプロシージャを呼び出すことができます。  
  
 デリゲートは、名前空間、モジュール、クラス、または構造体レベルで宣言できますが、プロシージャ内では宣言できません。  
  
 各デリゲート クラスでは、オブジェクト メソッドの仕様を渡すコンストラクターを定義します。 デリゲート コンス トラクターに渡す引数は、メソッドへの参照、またはラムダ式である必要があります。  
  
 メソッドへの参照を指定するには、次の構文を使用します。  
  
 `AddressOf` [`expression`.]`methodname`  
  
 コンパイル時の `expression` の型は、シグネチャがデリゲート クラスのシグネチャと同じで、指定された名前のメソッドを持つクラスまたはインターフェイスである必要があります。 `methodname` は、共有メソッドまたはインスタンス メソッドのいずれかにできます。 クラスの既定メソッドに対してデリゲートを作成する場合も、`methodname` は省略できません。  
  
 ラムダ式を指定するには、次の構文を使用します。  
  
 `Function` ([`parm` As `type`, `parm2` As `type2`, ...]) `expression`  
  
 関数のシグネチャは、デリゲート型のシグネチャと一致している必要があります。 ラムダ式について詳しくは、「[ラムダ式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)」をご覧ください。  
  
 デリゲートの詳細については、「[デリゲート](../../../visual-basic/programming-guide/language-features/delegates/index.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例では、`Delegate` ステートメントを使用して、2つの数値を操作するデリゲートを宣言し、数値を返します。 @No__t_0 メソッドは、この型のデリゲートのインスタンスを受け取り、それを使用して数値のペアを操作します。  
  
 [!code-vb[VbVbalrDelegates#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#14)]  
  
## <a name="see-also"></a>関連項目

- [AddressOf 演算子](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Of](../../../visual-basic/language-reference/statements/of-clause.md)
- [デリゲート](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [方法 : ジェネリック クラスを使用する](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [共変性と反変性](../../programming-guide/concepts/covariance-contravariance/index.md)
- [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
