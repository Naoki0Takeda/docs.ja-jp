---
title: ASP.NET キャッシュ統合
ms.date: 03/30/2017
ms.assetid: f581923a-8a72-42fc-bd6a-46de2aaeecc1
ms.openlocfilehash: 56f686b83deb576f1245a9d4b9df2df433ea1e2f
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045786"
---
# <a name="aspnet-caching-integration"></a>ASP.NET キャッシュ統合

このサンプルでは、WCF WEB HTTP プログラミング モデルで ASP.NET 出力キャッシュを利用する方法を示します。 ここでは、ASP.NET 出力キャッシュ統合機能について集中的に説明します。

## <a name="demonstrates"></a>使用例

ASP.NET 出力キャッシュとの統合

> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780)にアクセスして、すべての[!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (wcf) とサンプルをダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetCachingIntegration`

## <a name="discussion"></a>説明

このサンプルでは<xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> 、を使用して、Windows Communication Foundation (WCF) サービスで ASP.NET 出力キャッシュを使用します。 <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> は、サービス操作に適用される属性で、特定の操作からの応答に適用する構成ファイル内のキャッシュ プロファイルの名前を指定します。

サンプルサービスプロジェクトの Service.cs ファイルでは、 `GetCustomer` <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>操作と`GetCustomers`操作の両方が、キャッシュプロファイル名 "CacheFor60Seconds" を提供するに設定されています。 サービスプロジェクトの web.config ファイルでは、<`caching``system.web`> の < > 要素の下にキャッシュプロファイル "CacheFor60Seconds" が用意されています。 このキャッシュプロファイルでは、 `duration`属性の値は "60" なので、このプロファイルに関連付けられている応答は ASP.NET 出力キャッシュに60秒間キャッシュされます。 また、このキャッシュプロファイル`varmByParam`では、属性が "format" に設定されているため、 `format`クエリ文字列パラメーターの値が異なる要求の応答が個別にキャッシュされます。 最後に、キャッシュプロファイルの`varyByHeader`属性が "Accept" に設定されているため、accept ヘッダー値が異なる要求の応答は個別にキャッシュされます。

Client プロジェクトの Program.cs では、<xref:System.Net.HttpWebRequest> を使用してこのようなクライアントを作成する方法を示します。 これは、WCF サービスにアクセスする 1 つの方法にすぎません。 また、WCF チャネルファクトリや<xref:System.Net.WebClient>などの他の .NET Framework クラスを使用してサービスにアクセスすることもできます。 SDK のその他のサンプル ([基本的な HTTP サービス](../../../../docs/framework/wcf/samples/basic-http-service.md)サンプルなど) は、これらのクラスを使用して WCF サービスと通信する方法を示しています。

## <a name="to-run-the-sample"></a>サンプルを実行するには

このサンプルは、3 つのプロジェクトで構成されます。

- **[サービス]** :ASP.NET でホストされる WCF HTTP サービスを含む Web アプリケーションプロジェクト。

- **クライアント**:サービスを呼び出すコンソール アプリケーション プロジェクト。

- **共通**:クライアントとサービスによって使用される顧客の種類を含む共有ライブラリ。

クライアント コンソール アプリケーションが実行されると、クライアントはサービスに要求を発行し、応答からの適切な情報をコンソール ウィンドウに書き込みます。

#### <a name="to-run-the-sample"></a>サンプルを実行するには

1. ASP.NET キャッシュ統合サンプルのソリューションを開きます。

2. Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。

3. **ソリューションエクスプローラー**ウィンドウがまだ開いていない場合は、Ctrl + W + S キーを押します。

4. **[ソリューションエクスプローラー]** ウィンドウで、**サービス**プロジェクトを右クリックし、 **[新しいインスタンスを開始]** を選択します。 これで、サービスをホストする ASP.NET 開発サーバーが起動します。

5. **[ソリューションエクスプローラー]** ウィンドウで、**クライアント**プロジェクトを右クリックし、 **[新しいインスタンスを開始]** を選択します。

6. クライアント コンソール ウィンドウが表示されて、実行中のサービスの URI および実行中のサービスの HTML ヘルプ ページの URI が示されます。 ブラウザーでヘルプ ページの URI を入力することで、いつでも HTML ヘルプ ページを表示することができます。

7. サンプルが実行されると、クライアントは現在のアクティビティのステータスを書き込みます。

8. クライアント コンソール アプリケーションを終了するには、任意のキーを押します。

9. サービスのデバッグを停止するには、Shift キーを押しながら F5 キーを押します。

10. Windows 通知領域で、ASP.NET development server アイコンを右クリックし、 **[停止]** を選択します。
