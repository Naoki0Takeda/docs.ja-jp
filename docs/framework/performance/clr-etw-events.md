---
title: CLR ETW イベント
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: ef2b31c3-7426-43e7-9924-92339b96556d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6798a83973f94f07a2a215d5208aa55f0f9ae929
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046740"
---
# <a name="clr-etw-events"></a>CLR ETW イベント
このセクションのトピックでは、Windows イベント トレーシング (ETW) イベントについて説明します。 各イベントは、キーワードとレベルに関連付けられています。詳細については、「[CLR ETW キーワードおよびレベル](clr-etw-keywords-and-levels.md)」トピックを参照してください。 CLR には、イベントのプロバイダーが 2 つあります。  
  
- ランタイム プロバイダー。有効になっているキーワードに応じてイベントを発生させます (キーワードとはイベントのカテゴリです)。 CLR ランタイム プロバイダーの GUID は e13c0d23-ccbc-4e12-931b-d9cc2eee27e4 です。  
  
- ランダウン プロバイダー。特殊な用途があります。 CLR ランダウン プロバイダーの GUID は a669021c-c450-4609-a035-5af59af4df18 です。  
  
 プロバイダーの詳細については、「[CLR ETW プロバイダー](clr-etw-providers.md)」を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [ランタイム情報イベント](runtime-information-etw-events.md)  
 SKU、バージョン番号、アクティブ化の方法、起動時に使用されたコマンド ライン パラメーター、GUID (該当する場合) などのランタイムに関する情報をキャプチャします。  
  
 [Exception Thrown_V1 イベント](exception-thrown-v1-etw-event.md)  
 スローされる例外に関する情報をキャプチャします。  
  
 [競合イベント](contention-etw-events.md)  
 ランタイムが使用するモニター ロックまたはネイティブ ロックの競合に関する情報をキャプチャします。  
  
 [スレッド プール イベント](thread-pool-etw-events.md)  
 ワーカー スレッド プールと I/O スレッド プールに関する情報をキャプチャします。  
  
 [ローダー イベント](loader-etw-events.md)  
 アプリケーションのドメイン、アセンブリ、およびモジュールのロードとアンロードに関連する情報をキャプチャします。  
  
 [メソッド イベント](method-etw-events.md)  
 CLR メソッド シンボルの解決に関する情報をキャプチャします。  
  
 [ガベージ コレクション イベント](garbage-collection-etw-events.md)  
 診断とデバッグに役立つガベージ コレクションに関する情報をキャプチャします。  
  
 [JIT トレース イベント](jit-tracing-etw-events.md)  
 Just-In-Time (JIT) インライン展開と末尾呼び出しに関する情報をキャプチャします。  
  
 [相互運用イベント](interop-etw-events.md)  
 Microsoft intermediate language (MSIL) のスタブ生成とキャッシュに関する情報をキャプチャします。  
  
 [ARM のイベント](application-domain-resource-monitoring-arm-etw-events.md)  
 アプリケーション ドメインの状態に関する詳細な診断情報をキャプチャします。  
  
 [セキュリティ イベント](security-etw-events.md)  
 厳密な名前と Authenticode の検証に関する情報をキャプチャします。  
  
 [スタック イベント](stack-etw-event.md)  
 イベントが発生した後に、他のイベントでスタック トレースの生成に使用された情報をキャプチャします。  
  
## <a name="see-also"></a>関連項目

- [ETW によるデバッグとパフォーマンスチューニングの向上](https://go.microsoft.com/fwlink/?LinkId=179696)
- [Windows パフォーマンスブログ](https://go.microsoft.com/fwlink/?LinkId=179509)
- [.NET Framework のログ記録の制御](controlling-logging.md)
- [CLR ETW プロバイダー](clr-etw-providers.md)
- [CLR ETW キーワードおよびレベル](clr-etw-keywords-and-levels.md)
- [共通言語ランタイムの ETW イベント](etw-events-in-the-common-language-runtime.md)
