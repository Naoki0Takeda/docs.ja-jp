---
title: XAML での WPF と WF の統合
ms.date: 03/30/2017
ms.assetid: a4f53b48-fc90-4315-bca0-ba009562f488
ms.openlocfilehash: 547049488a1bf97d5f5ef03a71278b8f653293a2
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045323"
---
# <a name="wpf-and-wf-integration-in-xaml"></a>XAML での WPF と WF の統合
このサンプルでは、1つの XAML ドキュメントで Windows Presentation Foundation (WPF) および Windows Workflow Foundation (WF) 機能を使用するアプリケーションを作成する方法を示します。 これを実現するために、このサンプルでは Windows Workflow Foundation (WF) と XAML 拡張機能を使用します。

## <a name="sample-details"></a>サンプルの詳細
 ShowWindow.xaml ファイルは、シーケンスのアクティビティによって操作される 2 つの文字列変数 <xref:System.Activities.Statements.Sequence> および `ShowWindow` を持つ `WriteLine` アクティビティに逆シリアル化します。 <xref:System.Activities.Statements.WriteLine> アクティビティは、<xref:System.Activities.Statements.WriteLine.Text%2A> プロパティに割り当てる式をコンソール ウィンドウに出力します。 アクティビティ`ShowWindow`は、実行ロジックの一部として WPF ウィンドウを表示します。 このウィンドウの <xref:System.Activities.ActivityContext.DataContext%2A> には、シーケンスで宣言された変数が含まれます。 `ShowWindow` アクティビティで宣言されたウィンドウのコントロールは、データ バインドを使用してこれらの変数を操作します。 最後に、このウィンドウにはボタン コントロールが含まれます。 このボタンの `Click` イベントは、<xref:System.Activities.ActivityDelegate> アクティビティを含む `MarkupExtension` という名前の `CloseWindow` によって処理されます。 `MarkUpExtension` は、`x:Name` によって識別されるオブジェクトおよび格納先ウィンドウの <xref:System.Activities.ActivityContext.DataContext%2A> を、コンテキストとして提供する、含まれているアクティビティを呼び出します。 したがって、`CloseWindow.InArgument<Window>` は、ウィンドウの名前を参照する式を使用してバインドできます。

 アクティビティ`ShowWindow`は、WPF ウィンドウ<xref:System.Activities.AsyncCodeActivity%601>を表示するためにクラスから派生し、ウィンドウが閉じたときに完了します。 `Window` プロパティは、アクティビティの実行ごとにウィンドウを必要に応じて作成できるようにする `Func<Window>` 型です。 `Window` プロパティは、<xref:System.Xaml.XamlDeferringLoader> を使用してこの遅延評価モデルを有効にします。 `FuncFactoryDeferringLoader` を使用すると、`XamlReader` をシリアル化中にキャプチャしてアクティビティの実行中に読み取ることができます。

 アクティビティが適切に記述されていれば、スケジューラ スレッドはブロックされません。 ただし、`ShowWindow` アクティビティは、表示しているウィンドウが閉じられるまで完了できません。 `ShowWindow` アクティビティは、<xref:System.Activities.AsyncCodeActivity> から派生して <xref:System.Activities.WorkflowInvoker.BeginInvoke%2A> メソッドを <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> メソッドで呼び出し、ウィンドウをモーダルで表示することによってこの動作を実現します。 デリゲートは、WPF <xref:System.ServiceModel.InstanceContext.SynchronizationContext%2A> を介して呼び出されます。 `ShowWindow` アクティビティは、<xref:System.Activities.ActivityContext.DataContext%2A> プロパティを `Window.DataContext` プロパティに割り当てて、データ バインド コントロールがスコープ内の変数にアクセスできるようにします。

 このサンプルにおける最後の重要な点は、<xref:System.Workflow.ComponentModel.Serialization.MarkupExtension> という `DelegateActivityExtension` です。 このマークアップ拡張機能の `ProvideValue` メソッドは、埋め込みアクティビティを呼び出すデリゲートを返します。 このアクティビティは、WPF データコンテキストとスコープ内の任意`x:Name`の値を含む環境で実行されます。 `GenericInvoke` メソッドで、この環境は <xref:System.Activities.Hosting.SymbolResolver> 拡張機能を介してアクティビティに提供されます。 この拡張機能は、マークアップ拡張機能のデリゲートが呼び出されるたびに埋め込みアクティビティを呼び出すために使用される <xref:System.Activities.WorkflowInvoker> に追加されます。

> [!NOTE]
> 既定のデザイナーでは ShowWindow アクティビティはサポートされません。したがって、ShowWindow.Xaml ファイルはデザイナーでは正しく表示されません。

#### <a name="to-use-this-sample"></a>このサンプルを使用するには

1. Visual Studio 2010 を使用して、WPFWFIntegration ソリューションファイルを開きます。

2. ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。

3. ソリューションを実行するには、F5 キーを押します。

4. 姓と名をダイアログ ボックスに入力します。

5. ダイアログ ボックスを閉じると、コンソールに名前がエコーされます。

> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780)にアクセスして、すべての[!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (wcf) とサンプルをダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\WPFWFIntegration`
