---
title: UI オートメーションによる Calendar コントロール型のサポート
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Calendar control type
- Calendar control type
- control types, Calendar
ms.assetid: e91a7393-a7f9-4838-a1a6-857438b24bc9
ms.openlocfilehash: 0096ce3703a04feece49eea2580d49b7d947ecb3
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "71041928"
---
# <a name="ui-automation-support-for-the-calendar-control-type"></a>UI オートメーションによる Calendar コントロール型のサポート
> [!NOTE]
> このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 の最新情報[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]については[、「Windows Automation API:UI オートメーション](https://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 このトピックでは、Calendar コントロール型に対する [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] のサポートについて説明します。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]でのコントロール型とは、コントロールが <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> プロパティを使用するために満たす必要がある一連の条件のことです。 条件には、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリー構造、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] プロパティの値、コントロール パターン、および [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] イベントに関する特定のガイドラインが含まれます。  
  
 Calendar コントロールでは、簡単に日付を指定したり、他の日付を選択したりできます。  
  
 以下の各セクションで、Calendar コントロール型に必要な [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリー構造、プロパティ、コントロール パターン、およびイベントを定義します。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] の各要件は、 [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]、 [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]、 [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]のいずれの場合でも、すべてのカレンダー コントロールに当てはまります。  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>必須の UI オートメーション ツリー構造  
 次の表では、カレンダー コントロールに関連した [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリーのコントロール ビューとコンテンツ ビューを示し、それぞれのビューに含めることができる内容について説明します。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ツリーの詳細については、[UI Automation Tree Overview](ui-automation-tree-overview.md)をご覧ください。  
  
|コントロール ビュー|コンテンツ ビュー|  
|------------------|------------------|  
|予定表<br /><br /> <ul><li>DataGrid<br /><br /> <ul><li>Header (0 または 1)</li><li>HeaderItem (0 または 7、数量は列に表示される日数によって異なる)</li><li>ListItem (数量は表示される日数によって異なる)</li><li>Button (0 または 2、カレンダー ビューのページ移動用)</li></ul></li></ul>|予定表<br /><br /> -ListItem (数量は表示される日数によって異なります)|  
  
 Calendar コントロールは、ユーザー インターフェイスのさまざまな形式で表すことができます。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリーのコントロール ビューに含まれることが保証されるコントロールは、データ グリッド、ヘッダー、ヘッダー項目、およびリスト項目のコントロールだけです。  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>必須の UI オートメーション プロパティ  
 次の表に、カレンダー コントロールに特に関連する値または定義を持つ [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] プロパティを示します。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]プロパティの詳細については、「[クライアントの UI オートメーションのプロパティ](ui-automation-properties-for-clients.md)」を参照してください。  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] プロパティ|[値]|メモ|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|「ノート」をご覧ください。|このプロパティの値は、アプリケーションのすべてのコントロールで一意である必要があります。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|「ノート」をご覧ください。|コントロール全体を格納する最も外側の四角形。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|「ノート」をご覧ください。|四角形領域が存在する場合にサポートされます。 四角形領域内にクリック不可能な点が存在し、特別なヒット テストを実行する場合は、オーバーライドしてクリック可能な点を提供します。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|予定表|この値は、すべての [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] フレームワークで同じです。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|カレンダー コントロールは、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリーのコンテンツ ビューに常に含まれます。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|カレンダー コントロールは、常に [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリーのコントロール ビューに含まれます。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|「ノート」をご覧ください。|コントロールがキーボード フォーカスを受け取ることができる場合は、このプロパティをサポートする必要があります。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|「ノート」をご覧ください。|ドキュメント コントロールのラベル。 通常は、ドキュメントのタイトルが使用されます。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"カレンダー"|Calendar コントロール型に対応するローカライズされた文字列。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|「ノート」をご覧ください。|通常、カレンダー コントロールの名前は、今日の日付から取得されます。|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>必須の UI オートメーション コントロール パターン  
 次の表に、すべてのカレンダー コントロールでサポートされなければならない [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] コントロール パターンを示します。 コントロール パターンについて詳しくは、「 [UI Automation Control Patterns Overview](ui-automation-control-patterns-overview.md)」をご覧ください。  
  
|コントロール パターン/パターン プロパティ|サポート|メモ|  
|---------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider>|[はい]|1 か月の中に含まれる日付が空間的に移動できる項目になるため、カレンダー コントロールは必ず Grid パターンをサポートします。|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|依存|ほとんどのカレンダー コントロールはページごとのビューのフリッピングをサポートしています。 ページ移動をサポートするために、Scroll パターンを使用することをお勧めします。|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|依存|ほとんどのカレンダー コントロールは、特定の日付、月、または年を、サブ要素の選択内容の形で保存します。 複数選択が可能なカレンダーもあれば、1 つしか選択できないカレンダーもあります。|  
|<xref:System.Windows.Automation.Provider.ITableProvider>|[はい]|カレンダー コントロールには曜日のサブツリー内に常にヘッダーがあるため、Table パターンがサポートされる必要があります。|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|いいえ|カレンダー コントロールでは値を直接設定できないため、このコントロールに Value コントロール パターンは必要ありません。 特定の日付がコントロールに関連付けられている場合は、Selection コントロール パターンによって情報を提供する必要があります。|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>必須の UI オートメーション イベント  
 次の表に、すべてのカレンダー コントロールでサポートされなければならない [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] イベントを示します。 イベントについて詳しくは、「 [UI Automation Events Overview](ui-automation-events-overview.md)」をご覧ください。  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] イベント|サポート|メモ|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|必要|なし|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> プロパティ変更イベント。|必須|なし|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> プロパティ変更イベント。|必須|なし|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> プロパティ変更イベント。|必須|なし|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent>|必須|なし|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|必須|なし|  
|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty> プロパティ変更イベント。|依存|なし|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> プロパティ変更イベント。|依存|コントロールで Scroll コントロール パターンをサポートする場合は、このイベントをサポートする必要があります。|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> プロパティ変更イベント。|依存|コントロールで Scroll コントロール パターンをサポートする場合は、このイベントをサポートする必要があります。|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> プロパティ変更イベント。|依存|コントロールで Scroll コントロール パターンをサポートする場合は、このイベントをサポートする必要があります。|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> プロパティ変更イベント。|依存|コントロールで Scroll コントロール パターンをサポートする場合は、このイベントをサポートする必要があります。|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> プロパティ変更イベント。|依存|コントロールで Scroll コントロール パターンをサポートする場合は、このイベントをサポートする必要があります。|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> プロパティ変更イベント。|依存|コントロールで Scroll コントロール パターンをサポートする場合は、このイベントをサポートする必要があります。|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|必須|なし|  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Automation.ControlType.Calendar>
- [UI オートメーション コントロール型の概要](ui-automation-control-types-overview.md)
- [UI オートメーションの概要](ui-automation-overview.md)
