---
title: -nostdlib (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
ms.openlocfilehash: 819505df2e7d5f93302f9ed601de856e36ed7124
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005416"
---
# <a name="-nostdlib-visual-basic"></a>-nostdlib (Visual Basic)
コンパイラが標準ライブラリを自動的に参照しないようにします。  
  
## <a name="syntax"></a>構文  
  
```console  
-nostdlib  
```  
  
## <a name="remarks"></a>コメント  
 @No__t-0 オプションを指定すると、System .dll アセンブリへの自動参照が削除され、コンパイラによって Vbc.exe ファイルが読み取られなくなります。 Vbc.exe ファイルと同じディレクトリにある Vbc.exe ファイルは、一般的に使用される .NET Framework アセンブリを参照し、`System` と `Microsoft.VisualBasic` の名前空間をインポートします。  
  
> [!NOTE]
> Mscorlib.dll および Microsoft の .dll アセンブリは常に参照されます。  
  
> [!NOTE]
> @No__t-0 オプションは、Visual Studio 開発環境内からは使用できません。これは、コマンドラインからコンパイルする場合にのみ使用できます。  
  
## <a name="example"></a>例  
 次のコードは、標準ライブラリを参照せずに `T2.vb` をコンパイルします。 @No__t-1 オブジェクトを削除するには、`_MYTYPE` の条件付きコンパイル定数を文字列 "Empty" に設定する必要があります。  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a>関連項目

- [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [My で利用可能なオブジェクトのカスタマイズ](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
