---
title: '軽減策: アプリ ドメイン全体でのオブジェクトの逆シリアル化'
ms.date: 03/30/2017
ms.assetid: 30c2d66c-04a8-41a5-ad31-646b937f61b5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: de2456a1365a1fb48b3e9f126e090b8da77728cc
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894122"
---
# <a name="mitigation-deserialization-of-objects-across-app-domains"></a>軽減策: アプリ ドメイン全体でのオブジェクトの逆シリアル化
場合によっては、アプリが異なるアプリケーション ベースを持つ複数のアプリ ドメインを使用すると、アプリ ドメイン間で論理呼び出しコンテキストのオブジェクトを逆シリアル化しようとして、例外がスローされます。  
  
## <a name="diagnosing-the-issue"></a>問題の診断  
 問題は、次の条件の順序で発生します。  
  
1. アプリケーションが異なるアプリケーション ベースを持つ複数のアプリ ドメインを使用します。  
  
2. 一部の型は、<xref:System.Runtime.Remoting.Messaging.LogicalCallContext> や <xref:System.Runtime.Remoting.Messaging.LogicalCallContext.SetData%2A?displayProperty=nameWithType> などのメソッドを呼び出して <xref:System.Runtime.Remoting.Messaging.CallContext.LogicalSetData%2A?displayProperty=nameWithType> に明示的に追加されます。 これらの型は、シリアル化可能としてマークされず、グローバル アセンブリ キャッシュに格納されません。  
  
3. 後で、既定以外のアプリ ドメインで実行されているコードは、構成ファイルから値を読み取るか、XML を使用してオブジェクトを逆シリアル化しようとします。  
  
4. 構成ファイルから読み取るか、オブジェクトを逆シリアル化するために、<xref:System.Xml.XmlReader> オブジェクトは構成システムにアクセスしようとします。  
  
5. 構成システムがまだ初期化されていないときは、初期化を完了する必要があります。 これは特に、ランタイムが次のように構成システムの固定のパスを作成する必要があることを意味します。  
  
    1. これは既定以外のアプリ ドメインの証拠を検索します。  
  
    2. 既定のアプリ ドメインに基づいて既定以外のアプリ ドメインの証拠を計算しようとします。  
  
    3. 既定のアプリ ドメインの証拠を取得するための呼び出しは、既定以外のアプリ ドメインから既定のアプリ ドメインへのアプリ ドメイン間の呼び出しをトリガーします。  
  
    4. .NET Framework のアプリ ドメイン間コントラクトの一部として、論理呼び出しコンテキストの内容も、アプリ ドメインの境界を越えてマーシャリングされる必要があります。  
  
6. 論理呼び出しコンテキストに含まれる型が既定のアプリ ドメインで解決できないため、例外がスローされます。  
  
## <a name="mitigation"></a>軽減策  
 この問題を回避するには、次を実行します  
  
1. 例外がスローされたときにコール スタックで `get_Evidence` の呼び出しを検索します。 この例外は、<xref:System.IO.FileNotFoundException> や <xref:System.Runtime.Serialization.SerializationException> などの例外の大きなサブセットであることもあります。  
  
2. オブジェクトが論理呼び出しコンテキストに追加されないアプリ内の場所を特定して、次のコードを追加します。  
  
    ```csharp
    System.Configuration.ConfigurationManager.GetSection("system.xml/xmlReader");  
    ```
  
## <a name="see-also"></a>関連項目

- [ランタイムの変更点](runtime-changes-in-the-net-framework-4-5-1.md)
