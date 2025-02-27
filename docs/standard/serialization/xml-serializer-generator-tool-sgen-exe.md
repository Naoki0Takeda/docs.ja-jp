---
title: XML シリアライザー ジェネレーター ツール (Sgen.exe)
ms.date: 03/30/2017
ms.assetid: cc1d1f1c-fb26-4be9-885a-3fe84c81cec6
ms.openlocfilehash: 492337973f71b10dc061353b7083f596b402ae29
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/27/2019
ms.locfileid: "71392713"
---
# <a name="xml-serializer-generator-tool-sgenexe"></a>XML シリアライザー ジェネレーター ツール (Sgen.exe)
XML シリアライザー ジェネレーターは、指定された型のオブジェクトをシリアル化または逆シリアル化するとき、<xref:System.Xml.Serialization.XmlSerializer> の起動パフォーマンスを向上させるために、指定されたアセンブリの型に対して XML シリアル化アセンブリを作成します。  
  
## <a name="syntax"></a>構文  
  
```console  
sgen [options]  
```  
  
## <a name="parameters"></a>パラメーター  
  
|オプション|説明|  
|------------|-----------------|  
|**/a @ no__t-1 ssemno__t:** _filename_|アセンブリ、または *filename* によって指定される実行可能ファイルに含まれるすべての型に対して、シリアル化コードを生成します。 指定できるファイル名は 1 つのみです。 この引数を複数指定した場合は、最後のファイル名が使用されます。|  
|**/c @ no__t-1ompiler @ no__t:** _options_|オプションを C# コンパイラに渡すように指定します。 csc.exe のすべてのオプションがサポートされ、コンパイラに渡されます。 このオプションを使用して、アセンブリに署名してキー ファイルを指定するように指定できます。|  
|**/d @ no__t-1ebug @ no__t-2**|デバッガーで使用できるイメージを生成します。|  
|**/f @ no__t-1orce @ no__t-2**|同じ名前の既存のアセンブリに上書きします。 既定値は **false** です。|  
|**/help または /?**|このツールのコマンド構文とオプションを表示します。|  
|**/k @ no__t-1eep @ no__t-2**|生成されたソース ファイルとその他の一時ファイルをシリアル化アセンブリにコンパイルした後、元のファイルを削除しません。 このオプションを使用して、ツールが特定の型に対してシリアル化コードを生成するかどうかを指定できます。|  
|**/n @ no__t-1ologo @ no__t-2**|Microsoft の著作権情報を表示しません。|  
|**/o @ no__t-1ut @ no__t:** _path_|生成されたアセンブリの保存先のディレクトリを指定します。 **注:** 生成されたアセンブリの名前は、入力アセンブリの名前と "xmlSerializers.dll" で構成されます。|  
|**/p @ no__t-1roxytypes @ no__t**|XML Web サービス プロキシ型に対してのみシリアル化コードを生成します。|  
|**/r @ no__t-1eference @ no__t:** _assemblyfiles_|XML シリアル化が必要な型によって参照されるアセンブリを指定します。 コンマで区切られた複数のアセンブリ ファイルを受け入れます。|  
|**/s @ no__t-1ilent @ no__t**|成功メッセージを表示しません。|  
|**/t @ no__t-1 種類 @ no__t:** _type_|指定された型に対してのみ、シリアル化コードを生成します。|  
|**/v @ no__t-1erbose @ no__t-2**|デバッグに関する詳細出力を表示します。 <xref:System.Xml.Serialization.XmlSerializer> でシリアル化できない対象アセンブリの型を一覧表示します。|  
|**/?**|このツールのコマンド構文とオプションを表示します。|  
  
## <a name="remarks"></a>コメント  
 XML シリアライザー ジェネレーターを使用しない場合、<xref:System.Xml.Serialization.XmlSerializer> はアプリケーションを実行するたびに、各型に対してシリアル化コードとシリアル化アセンブリを生成します。 XML シリアル化の起動時のパフォーマンスを向上させるには、Sgen ツールを使用して、これらのアセンブリを事前に生成します。 生成したアセンブリは、アプリケーションで配置できます。  
  
 XML シリアライザー ジェネレーターは、サーバーとの通信に XML Web サービス プロキシを使用するクライアントのパフォーマンスも向上させますが、これは型が初めて読み込まれるとき、シリアル化プロセスによってパフォーマンスが低下しないためです。  
  
 これらの生成されたアセンブリは、Web サービスのサーバー側では使用できません。 このツールは、Web サービス クライアントと手動シリアル化シナリオに対してのみ使用できます。  
  
 シリアル化する型を含むアセンブリの名前が MyType.dll の場合、関連するシリアル化アセンブリの名前は MyType.XmlSerializers.dll となります。  
  
## <a name="examples"></a>使用例  
 次のコマンドは、Data.dll という名前のアセンブリに含まれるすべての型をシリアル化するために、Data.XmlSerializers.dll という名前のアセンブリを作成します。  
  
```console  
sgen Data.dll   
```  
  
 Data.XmlSerializers.dll アセンブリは、Data.dll の型をシリアル化および逆シリアル化する必要のあるコードから参照できます。  
  
## <a name="see-also"></a>関連項目

- [ツール](../../../docs/framework/tools/index.md)
- [Visual Studio 用開発者コマンド プロンプト](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
