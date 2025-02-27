---
title: 弱いイベント パターン
ms.date: 03/30/2017
helpviewer_keywords:
- weak event pattern implementation [WPF]
- event handlers [WPF], weak event pattern
- IWeakEventListener interface [WPF]
ms.assetid: e7c62920-4812-4811-94d8-050a65c856f6
ms.openlocfilehash: f4cbb22a3cdd7b966c36f6c8246b13b5c58e056d
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991786"
---
# <a name="weak-event-patterns"></a>弱いイベント パターン
アプリケーションでは、イベントソースにアタッチされているハンドラーが、ハンドラーをソースにアタッチしたリスナーオブジェクトと連携して破棄されない可能性があります。 このような状況では、メモリリークが発生する可能性があります。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]では、特定のイベントに専用のマネージャークラスを提供し、そのイベントのリスナーにインターフェイスを実装することによって、この問題に対処するために使用できるデザインパターンが導入されています。 この設計パターンは、*弱いイベントパターン*と呼ばれます。  
  
## <a name="why-implement-the-weak-event-pattern"></a>弱いイベントパターンを実装する理由  
 イベントをリッスンすると、メモリリークが発生する可能性があります。 イベントをリッスンする一般的な方法は、ソースのイベントにハンドラーを関連付ける言語固有の構文を使用することです。 たとえば、でC#は、という構文が`source.SomeEvent += new SomeEventHandler(MyEventHandler)`使用されます。  
  
 この手法では、イベントソースからイベントリスナーへの強い参照が作成されます。 通常、リスナーのイベントハンドラーをアタッチすると、リスナーには、ソースのオブジェクトの有効期間の影響を受けるオブジェクトの有効期間が設定されます (イベントハンドラーが明示的に削除されていない場合)。 ただし、特定の状況では、リスナーのオブジェクトの有効期間を、ソースの有効期間ではなく、アプリケーションのビジュアルツリーに現在属しているかどうかなど、他の要因によって制御する必要がある場合があります。 ソースオブジェクトの有効期間がリスナーのオブジェクトの有効期間を超えた場合、通常のイベントパターンはメモリリークにつながります。リスナーは意図した時間より長く維持されます。  
  
 弱いイベントパターンは、このメモリリークの問題を解決するように設計されています。 弱いイベントパターンは、リスナーがイベントに登録する必要がある場合に使用できますが、登録解除のタイミングをリスナーが明示的に認識していません。 弱いイベントパターンは、ソースのオブジェクトの有効期間がリスナーの有効なオブジェクトの有効期間を超えた場合にも使用できます。 (この場合、*役に立ち*ます)。弱いイベントパターンを使用すると、リスナーは、リスナーのオブジェクトの有効期間特性に一切影響を与えずに、イベントの登録と受信を行うことができます。 実際には、ソースからの暗黙的な参照では、リスナーがガベージコレクションの対象であるかどうかは判断されません。 参照は弱い参照であるため、弱いイベントパターンと関連する Api の名前が付けられます。 リスナーは、ガベージコレクションを実行したり、破棄したりすることができます。また、破棄されたオブジェクトへの非収集ハンドラー参照を保持せずに、ソースを継続できます。  
  
## <a name="who-should-implement-the-weak-event-pattern"></a>弱いイベントパターンを実装する必要があるのはだれですか。  
 弱いイベントパターンの実装は、主にコントロールの作成者を対象としています。 コントロールの作成者は、コントロールの動作とコンテインメント、およびコントロールが挿入されるアプリケーションに与える影響について、ほとんどの責任を担います。 これには、コントロールオブジェクトの有効期間の動作が含まれます。特に、説明されているメモリリークの問題を処理します。  
  
 特定のシナリオでは、弱いイベントパターンの適用が本質的に適しています。 このようなシナリオの1つに、データバインディングがあります。 データバインディングでは、ソースオブジェクトがバインディングのターゲットであるリスナーオブジェクトと完全に独立していることが一般的です。 データバインディングの[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]多くの側面には、イベントの実装方法に弱いイベントパターンが既に適用されています。  
  
## <a name="how-to-implement-the-weak-event-pattern"></a>弱いイベントパターンを実装する方法  
 弱いイベントパターンを実装するには、3つの方法があります。 次の表に、3つの方法を示し、それぞれを使用する必要がある場合のガイダンスを示します。  
  
|方法|実装する場合|  
|--------------|-----------------------|  
|既存の weak イベントマネージャークラスを使用する|サブスクライブするイベントに対応<xref:System.Windows.WeakEventManager>するが存在する場合は、既存の弱いイベントマネージャーを使用します。 WPF に含まれる弱いイベントマネージャーの一覧については、 <xref:System.Windows.WeakEventManager>クラスの継承階層を参照してください。 含まれている弱いイベントマネージャーには制限があるため、他の方法のいずれかを選択する必要がある場合があります。|  
|汎用の弱いイベントマネージャークラスを使用する|<xref:System.Windows.WeakEventManager%602> 既存<xref:System.Windows.WeakEventManager>のが使用できない場合に汎用を使用します。簡単に実装でき、効率について心配する必要はありません。 ジェネリック<xref:System.Windows.WeakEventManager%602>は、既存またはカスタムの弱いイベントマネージャーよりも効率が悪くなります。 たとえば、ジェネリッククラスは、イベントの名前を指定してイベントを検出するために、より多くのリフレクションを行います。 また、ジェネリック<xref:System.Windows.WeakEventManager%602>を使用してイベントを登録するコードは、既存のまたはカスタム<xref:System.Windows.WeakEventManager>を使用する場合よりも詳細です。|  
|カスタムの weak イベントマネージャークラスを作成する|<xref:System.Windows.WeakEventManager> 既存<xref:System.Windows.WeakEventManager>のが使用できないときに、最適な効率を実現するには、カスタムを作成します。 カスタム<xref:System.Windows.WeakEventManager>を使用してイベントをサブスクライブする方が効率的ですが、最初により多くのコードを記述するコストが発生します。|  
|サードパーティの弱いイベントマネージャーを使用する|NuGet には[いくつかの弱いイベントマネージャー](https://www.nuget.org/packages?q=weak+event+manager&prerel=false)があり、多くの WPF フレームワークでもパターンがサポートされています (例については、[疎結合イベントサブスクリプションに関する Prism のドキュメント](https://github.com/PrismLibrary/Prism-Documentation/blob/master/docs/wpf/Communication.md#subscribing-to-events)を参照してください)。|

 以下のセクションでは、弱いイベントパターンを実装する方法について説明します。  この説明のために、サブスクライブするイベントには次の特性があります。  
  
- イベント名が`SomeEvent`です。  
  
- イベントは`EventSource`クラスによって発生します。  
  
- イベントハンドラーの型`SomeEventEventHandler`は、(または`EventHandler<SomeEventEventArgs>`) です。  
  
- イベントは、型`SomeEventEventArgs`のパラメーターをイベントハンドラーに渡します。  
  
### <a name="using-an-existing-weak-event-manager-class"></a>既存の Weak イベントマネージャークラスを使用する  
  
1. 既存の弱いイベントマネージャーを検索します。  
  
     WPF に含まれる弱いイベントマネージャーの一覧については、 <xref:System.Windows.WeakEventManager>クラスの継承階層を参照してください。  
  
2. 通常のイベントフックアップではなく、新しい弱いイベントマネージャーを使用します。  
  
     たとえば、コードで次のパターンを使用してイベントをサブスクライブしているとします。  
  
    ```csharp  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     次のパターンに変更します。  
  
    ```csharp  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     同様に、コードで次のパターンを使用してイベントのサブスクリプションを解除します。  
  
    ```csharp  
    source.SomeEvent -= new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     次のパターンに変更します。  
  
    ```csharp  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
### <a name="using-the-generic-weak-event-manager-class"></a>汎用弱いイベントマネージャークラスの使用  
  
1. 通常のイベント<xref:System.Windows.WeakEventManager%602>フックの代わりに、ジェネリッククラスを使用します。  
  
     を使用<xref:System.Windows.WeakEventManager%602>してイベントリスナーを登録する場合は、次の<xref:System.EventArgs>コードに示すように、イベントソースと型<xref:System.Windows.WeakEventManager%602.AddHandler%2A>をクラスの型パラメーターとして渡し、を呼び出します。  
  
    ```csharp  
    WeakEventManager<EventSource, SomeEventEventArgs>.AddHandler(source, "SomeEvent", source_SomeEvent);  
    ```  
  
### <a name="creating-a-custom-weak-event-manager-class"></a>カスタムの弱いイベントマネージャークラスを作成する  
  
1. 次のクラステンプレートをプロジェクトにコピーします。  
  
     このクラスは、 <xref:System.Windows.WeakEventManager>クラスから継承されます。  
  
     [!code-csharp[WeakEvents#WeakEventManagerTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/WeakEvents/CSharp/WeakEventManagerTemplate.cs#weakeventmanagertemplate)]  
  
2. `SomeEventWeakEventManager`名前を実際の名前に置き換えます。  
  
3. 前に説明した3つの名前を、対応するイベントの名前に置き換えます。 (`SomeEvent`、 `EventSource`、および`SomeEventEventArgs`)  
  
4. 弱いイベントマネージャークラスの可視性 (公開/内部/プライベート) を、それが管理するイベントと同じ可視性に設定します。  
  
5. 通常のイベントフックアップではなく、新しい弱いイベントマネージャーを使用します。  
  
     たとえば、コードで次のパターンを使用してイベントをサブスクライブしているとします。  
  
    ```csharp  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     次のパターンに変更します。  
  
    ```csharp  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     同様に、コードで次のパターンを使用してイベントのサブスクリプションを解除します。  
  
    ```csharp  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     次のパターンに変更します。  
  
    ```csharp  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.WeakEventManager>
- <xref:System.Windows.IWeakEventListener>
- [ルーティング イベントの概要](routed-events-overview.md)
- [データ バインディングの概要](../data/data-binding-overview.md)
