---
title: WS-AtomicTransaction 構成ユーティリティ (wsatConfig.exe)
ms.date: 03/30/2017
ms.assetid: 1c56cf98-3963-46d5-a4e1-482deae58c58
ms.openlocfilehash: 5333c9c5caad502ce925fe4a45a039c553812ba6
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320200"
---
# <a name="ws-atomictransaction-configuration-utility-wsatconfigexe"></a>WS-AtomicTransaction 構成ユーティリティ (wsatConfig.exe)
WS-AtomicTransaction 構成ユーティリティは、基本的な WS-AtomicTransaction サポート設定を構成するために使用されます。  
  
## <a name="syntax"></a>構文  
  
```  
wsatConfig [Options]  
```  
  
## <a name="remarks"></a>Remarks  
 このコマンド ライン ツールを使用して、基本的な WS-AtomicTransaction 設定をローカル マシンでのみ構成できます。 ローカルコンピューターとリモートコンピューターの両方で設定を構成する必要がある場合は、「 [ws-atomictransaction のサポートを構成](./feature-details/configuring-ws-atomic-transaction-support.md)する」の説明に従って、MMC スナップインを使用する必要があります。  
  
 コマンド ライン ツールは、Windows SDK の次のインストール場所にあります。  
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\wsatConfig.exe  
  
 [!INCLUDE[wxp](../../../includes/wxp-md.md)] または [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] を実行している場合は、更新プログラムをダウンロードしてから、WsatConfig.exe を実行する必要があります。 この更新プログラムの詳細については、「 [update For コマース Server 2007 (KB912817)](https://go.microsoft.com/fwlink/?LinkId=95340) 」および「 [Windows XP Com + 修正プログラムロールアップパッケージ13の可用性](https://go.microsoft.com/fwlink/?LinkId=95341)」を参照してください。  
  
 次の表は、WS-AtomicTransaction 構成ユーティリティ (wsatConfig.exe) で使用できるオプションを示します。  
  
> [!NOTE]
> 選択したポートに SSL 証明書を設定すると、そのポートに関連付けられたオリジナルの SSL 証明書が上書きされます。  
  
|オプション|説明|  
|-------------|-----------------|  
|-accounts: \<account、>|WS-AtomicTransaction に追加できるアカウントをコンマで区切って指定します。 これらのアカウントの有効性の確認は行われません。|  
|-accountsCerts: \<thumb >&#124;"Issuer\SubjectName", >|WS-AtomicTransaction に追加できる証明書をコンマで区切って指定します。 証明書は、サムプリントまたは Issuer\SubjectName ペアで示されます。 空の場合は、サブジェクト名に {EMPTY} を使用します。|  
|-endpointCert: < マシン&#124;\< thumb >&#124;"Issuer\SubjectName" >|コンピューターの証明書を使用するか、サムプリントまたは Issuer\SubjectName ペアで指定される別のローカル エンドポイントの証明書を使用します。 空の場合は、サブジェクト名に {EMPTY} を使用します。|  
|-maxTimeout: \<sec >|最大タイムアウトを秒単位で指定します。 有効な値は 0 ~ 3600 です。|  
|-network: @no__t 0enable&#124;disable >|WS-AtomicTransaction ネットワーク サポートを有効または無効にします。|  
|-port: @no__t 0portNum >|WS-AtomicTransaction の HTTPS ポートを設定します。<br /><br /> このツールを実行する前にファイアウォールが既に有効な場合、ポートは例外の一覧に自動的に登録されます。 このツールを実行する前にファイアウォールが無効な場合は、ファイアウォールに関する追加の構成はありません。<br /><br /> WS-AT の構成後にファイアウォールを有効にする場合は、このツールを再度実行し、このパラメーターを使用してポート番号を指定する必要があります。 WS-AT の構成後にファイアウォールを無効にする場合は、入力を追加しないで WS-AT の動作を続行します。|  
|-timeout: \< 秒 >|既定のタイムアウトを秒単位で指定します。 有効な値は 1 ～ 3600 の範囲です。|  
|-traceActivity: @no__t 0enable&#124;disable >|アクティビティ イベントのトレースを有効または無効にします。|  
|-traceLevel: \<Off&#124;エラー&#124;重大&#124;警告&#124;情報&#124; &#124;すべて >}|トレース レベルを指定します。|  
|-tracePII: \<enable&#124;disable >|個人を特定できる情報のトレースを有効または無効にします。|  
|-traceProp: @no__t 0enable&#124;disable >|伝達イベントのトレースを有効または無効にします。|  
|-restart|MSDTC を再起動して変更を直ちに反映します。 これが指定されていない場合、変更は、MSDTC が再起動されたときに有効になります。|  
|-show|現在の WS-AtomicTransaction プロトコル設定を表示します。|  
|-virtualServer: \<virtualServer >|DTC リソース クラスター名を指定します。|  
  
## <a name="see-also"></a>関連項目

- [WS-AtomicTransaction の使用](./feature-details/using-ws-atomictransaction.md)
- [WS-AtomicTransaction サポートの構成](./feature-details/configuring-ws-atomic-transaction-support.md)
