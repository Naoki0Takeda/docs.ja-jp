---
title: <smtp> 要素 (ネットワーク設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp
- http://schemas.microsoft.com/.NetConfiguration/v2.0#smtp
helpviewer_keywords:
- <smtp> element
- smtp element
ms.assetid: 220b0329-e384-4e0c-86b4-0945ad17efd9
ms.openlocfilehash: 2105a6dd25a7f6e5e4c1ce286be7f60beae1dca0
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697609"
---
# <a name="smtp-element-network-settings"></a>\<smtp > 要素 (ネットワーク設定)
電子メールの送信に使用する配信形式、配信方法、差出人アドレスを構成します。  
  
[ **\<configuration>** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **@no__t 47 >** ](system-net-element-network-settings.md)  
&nbsp; @ no__t @ no__t-2 @ no__t-3[ **\<mailSettings >** ](mailsettings-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t @ no__t @ no__t-5 **\< smtp >** のようになります。  
  
## <a name="syntax"></a>構文  
  
```xml  
<smtp  
  deliveryFormat="format"  
  deliveryMethod="method"  
  from="from address">
    <specifiedPickupDirectory>...</specifiedPickupDirectory>  
    <network>...</network>  
</smtp>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`deliveryFormat`|送信電子メールの配信形式を指定します。 指定できる値は SevenBit および International です。|  
|`deliveryMethod`|電子メールの配信方法を指定します。 使用可能な値は、Network、ピックアップディレクトリ Fromiis、および指定された指定された Updirectory です。|  
|`from`|送信メールの差出人アドレスを指定します。|  
  
### <a name="child-elements"></a>子要素  
  
|属性|説明|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|SMTP (Simple Mail Transport Protocol) サーバー用のローカル ディレクトリを設定します。|  
|`network`|外部 SMTP サーバー用のネットワーク オプションを設定します。|  
  
### <a name="parent-elements"></a>親要素  
  
|**要素**|**[説明]**|  
|-----------------|---------------------|  
|[\<mailSettings> 要素 (ネットワーク設定)](mailsettings-element-network-settings.md)|電子メールの送信オプションを設定します。|  
  
## <a name="example"></a>例  
 次の例では、既定のネットワーク資格情報を使用して電子メールを送信するための適切な SMTP パラメーターを指定しています。  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="Network" deliveryFormat="SevenBit"  from="ben@contoso.com">  
        <network  
          host="localhost"  
          port="25"  
          defaultCredentials="true"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpDeliveryFormat>
- <xref:System.Net.Mail.SmtpDeliveryMethod>
- [ネットワーク設定スキーマ](index.md)
