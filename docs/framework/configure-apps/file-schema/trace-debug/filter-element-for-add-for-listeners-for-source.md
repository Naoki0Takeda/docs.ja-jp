---
title: <source> の <listeners> の <add> の <filter> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#filter
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- <filter> element for <add> for <listeners> for <source>
- filter element for <add> for <listeners> for <source>
ms.assetid: 15808b80-4579-4c25-b385-178cfdf154ba
ms.openlocfilehash: ec288685f47c8a35e2371c31d359b604a4967196
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697168"
---
# <a name="filter-element-for-add-for-listeners-for-source"></a>\<source @no__t の >-2listeners @no__t の \< add > の > 要素
トレース ソースの `Listeners` コレクション内のリスナーにフィルターを追加します。  
  
[ **\<configuration>** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **\<system. diagnostics >** ](system-diagnostics-element.md)  
&nbsp; @ no__t-1 @ no__t no__t-3[ **\<sources >** ](sources-element.md)  
&nbsp; @ no__t-1 @ no__t @ no__t @ no__t-5[ **\<source >** になります。](source-element.md)  
&nbsp; @ no__t-1 @ no__t @ no__t @ no__t-5 @ no__t-6 @ no__t-7[ **&nbsp;0listeners** (&) >](listeners-element-for-source.md)  
&nbsp; @ no__t-1 @ no__t @ no__t @ no__t @ no__t-6 @ no__t-7 @ no__t-8 @ no__t-9[ **&nbsp;2add > を追加**します。](add-element-for-listeners-for-source.md)  
&nbsp; @ no__t @ no__t @ no__t @ no__t @ no__t @ no__t @ no__t-7 @ no__t-6 @ no__t-9 @ no__t-10 @-11 **&nbsp;3filter > を選択**して、フィルターを適用します。  
  
## <a name="syntax"></a>構文  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`type`|必須の属性です。<br /><br /> フィルターの種類を指定します。この型は、<xref:System.Diagnostics.TraceFilter> クラスから継承する必要があります。 型の名前空間で修飾された名前を使用できます。これは、型の @no__t 0 のプロパティに対応します。または、<xref:System.Type.AssemblyQualifiedName%2A> プロパティに対応するアセンブリ情報を含む完全修飾型名を使用することもできます。 完全修飾型名の詳細については、「[完全修飾型名の指定](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)」を参照してください。|  
|`initializeData`|省略可能な属性です。<br /><br /> 指定されたフィルタークラスのコンストラクターに渡される文字列。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`system.diagnostics`|メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。|  
|`sources`|トレース メッセージを開始するトレース ソースを保持します。|  
|`source`|トレース メッセージを開始するトレース ソースを指定します。|  
|`listeners`|メッセージを収集、格納、およびルーティングするリスナーを格納します。 リスナーは、適切なターゲットにトレース出力を送信します。|  
|`add`|トレース ソースの `Listeners` コレクションにリスナーを追加します。|  
  
## <a name="remarks"></a>コメント  
 @No__t-0 要素は、 [\<sharedListeners >](sharedlisteners-element.md)で定義されているリスナーの名前だけでなく、リスナーの種類を指定するトレースソースリスナーの `<add>` 要素に含まれている必要があります。 リスナーが[@no__t 1sharedListeners >](sharedlisteners-element.md)で定義されている場合は、そのリスナーのフィルターをその要素で定義する必要があります。  
  
 この要素は、コンピューターの構成ファイル (machine.config) とアプリケーション構成ファイルで使用できます。  
  
## <a name="example"></a>例  
 次の例では、`<filter>` 要素を使用して、トレース @no__t ソースの `Listeners` コレクションのリスナー `console` にフィルターを追加し、フィルターイベントレベルを `Error` に指定する方法を示します。  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="myTraceSource" switchName="SourceSwitch"   
        switchType="System.Diagnostics.SourceSwitch"  >  
        <listeners>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener" >  
            <filter type="System.Diagnostics.EventTypeFilter"   
              initializeData="Error" />  
          </add>  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="SourceSwitch" value="Warning" />  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [トレースおよびデバッグ設定のスキーマ](index.md)
