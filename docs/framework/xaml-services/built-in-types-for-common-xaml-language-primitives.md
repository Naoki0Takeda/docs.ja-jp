---
title: 共通の XAML 言語プリミティブの組み込み型
ms.date: 03/30/2017
helpviewer_keywords:
- XAML language primitives [XAML Services]
- XAML [XAML Services], built-in types
- x:String [XAML Services]
- x:TimeSpan [XAML Services]
- x:Byte [XAML Services]
- x:Double [XAML Services]
- XAML [XAML Services], types
- x:Uri [XAML Services]
- XAML built-in types [XAML Services]
- x:Int64 [XAML Services]
- x:Single [XAML Services]
- x:Int32 [XAML Services]
ms.assetid: 11de2f08-5b95-4989-b5ec-5178eb968184
ms.openlocfilehash: 85fd0c04a40b9de64979e4da1459dbf8953a93bf
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053877"
---
# <a name="built-in-types-for-common-xaml-language-primitives"></a>共通の XAML 言語プリミティブの組み込み型
XAML 2009 では、いくつかのデータ型に対する XAML 言語をサポートします。これらのデータ型は、共通言語ランタイム (CLR: Common Language Runtime) およびその他のプログラミング言語でよく使用されているプリミティブです。 XAML 2009 でサポートされるようになったのは、 `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`、および `x:Array`の各プリミティブです。  
  
<a name="previous_techniques_for_language_primitives_in_xaml_markup"></a>   
## <a name="previous-techniques-for-language-primitives-in-xaml-markup"></a>XAML マークアップの言語プリミティブにおける以前の技術  
 以前の WPF バージョンの XAML では、.NET Framework の CLR プリミティブ定義クラスを含むアセンブリと名前空間をマッピングすることによって、CLR 言語プリミティブを参照していました。 これらの大半は mscorlib アセンブリおよび <xref:System> 名前空間に含まれています。 たとえば、 <xref:System.Int32>を使用するには、次のマッピングを宣言します (使用例については、その後に示します)。  
  
```xaml  
<Application xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"   
xmlns:sys="clr-namespace:System;assembly=mscorlib">  
  <Application.Resources>  
    <sys:Int32 x:Key="intMeaning">42</sys:Int32>  
  </Application.Resources>  
</Application>  
```  
  
<a name="xaml_2009_language_primitives"></a>   
## <a name="xaml-2009-language-primitives"></a>XAML 2009 言語プリミティブ  
 慣例により、XAML の言語プリミティブとその他すべての XAML 言語要素は、 `x:` プレフィックスを含めて示されます。 XAML 言語要素は、実際のマークアップで一般的にこのように使用されます。 WPF の XAML の概念ドキュメントや XAML 仕様書でも、この規則に従っています。  
  
### <a name="xobject"></a>x:Object  
 CLR バッキングの場合は、 `x:Object` プリミティブは <xref:System.Object>に対応しています。  
  
 このプリミティブは通常はアプリケーション マークアップでは使用されず、XAML 型システムで割り当てできるかどうかを確認する場合などに便利です。  
  
### <a name="xboolean"></a>x:Boolean  
 CLR バッキングの場合は、 `x:Boolean` プリミティブは <xref:System.Boolean>に対応しています。  
  
 XAML は、 `x:Boolean` の値の大文字と小文字を区別しないで解析します。 `x:Bool` は、承諾済みのプリミティブではありません。 Xaml 言語仕様の定義については、「 [ \[5.2.17 and 5.4.11\] ](https://go.microsoft.com/fwlink/?LinkId=114525)」を参照してください。  
  
### <a name="xchar"></a>x:Char  
 CLR バッキングの場合は、 `x:Char` プリミティブは <xref:System.Char>に対応しています。  
  
 文字列型および char 型は、XML レベルでファイルの全体的なエンコーディングと相互作用しています。 Xaml 言語仕様の定義については、「 [ \[5.2.7 and 5.4.1\] ](https://go.microsoft.com/fwlink/?LinkId=114525)」を参照してください。  
  
### <a name="xstring"></a>x:String  
 CLR バッキングの場合は、 `x:String` プリミティブは <xref:System.String>に対応しています。  
  
 文字列型および char 型は、XML レベルでファイルの全体的なエンコーディングと相互作用しています。 Xaml 言語仕様の定義については、「 [ \[5.2.6\] ](https://go.microsoft.com/fwlink/?LinkId=114525)」を参照してください。  
  
### <a name="xdecimal"></a>x:Decimal  
 CLR バッキングの場合は、 `x:Decimal` プリミティブは <xref:System.Decimal>に対応しています。  
  
 XAML の解析は、本質的に `en-US` カルチャにおいて行われます。 `en-US` カルチャでは、開発環境または、XAML が実行時に読み込まれる最終的なクライアント ターゲットのカルチャ設定に関係なく、小数コンポーネントの正しい区切り記号は常にピリオド (`.`) です。  
  
 Xaml 言語仕様の定義については、「 [ \[5.2.14 and 5.4.8\] ](https://go.microsoft.com/fwlink/?LinkId=114525)」を参照してください。  
  
### <a name="xsingle"></a>x:Single  
 CLR バッキングの場合は、 `x:Single` プリミティブは <xref:System.Single>に対応しています。  
  
 数値に加え、 `x:Single` のテキスト構文はトークン `Infinity`、 `-Infinity`、および `NaN`も許可しています。 これらのトークンは、大文字と小文字を区別します。  
  
 `x:Single` は、テキスト構文の最初の文字が `e` または `E`の場合は、指数表記形式の値をサポートします。  
  
 Xaml 言語仕様の定義については、「 [ \[5.2.8 and 5.4.2\] ](https://go.microsoft.com/fwlink/?LinkId=114525)」を参照してください。  
  
### <a name="xdouble"></a>x:Double  
 CLR バッキングの場合は、 `x:Double` プリミティブは <xref:System.Double>に対応しています。  
  
 数値に加え、 `x:Double` のテキスト構文は、 `Infinity`、 `-Infinity`、および `NaN`の各トークンも許可しています。 これらのトークンは、大文字と小文字を区別します。  
  
 `x:Double` は指数表記形式の値をサポートしています。 `e` または `E` という文字を使用して指数部分を示すことができます。  
  
 Xaml 言語仕様の定義については、「 [ \[5.2.9 and 5.4.3\] ](https://go.microsoft.com/fwlink/?LinkId=114525)」を参照してください。  
  
### <a name="xint16"></a>x:Int16  
 CLR バッキングの場合は、 `x:Int16` プリミティブは <xref:System.Int16> に対応し、 `x:Int16` は符号付きとして処理されます。 XAML では、テキスト構文に正 (`+`) 符号がない場合でも、暗黙的に正符号値を示しています。  
  
 Xaml 言語仕様の定義については、「 [ \[5.2.11 and 5.4.5\] ](https://go.microsoft.com/fwlink/?LinkId=114525)」を参照してください。  
  
### <a name="xint32"></a>x:Int32  
 CLR バッキングの場合は、 `x:Int32` プリミティブは <xref:System.Int32>に対応しています。 `x:Int32` は符号付きとして処理されます。 XAML では、テキスト構文に正 (`+`) 符号がない場合でも、暗黙的に正符号値を示しています。  
  
 Xaml 言語仕様の定義については、「 [ \[5.2.12」および「5.4.6」\]セクション](https://go.microsoft.com/fwlink/?LinkId=114525)を参照してください。  
  
### <a name="xint64"></a>x:Int64  
 CLR バッキングの場合は、 `x:Int64` プリミティブは <xref:System.Int64>に対応しています。 `x:Int64` は符号付きとして処理されます。 XAML では、テキスト構文に正 (`+`) 符号がない場合でも、暗黙的に正符号値を示しています。  
  
 Xaml 言語仕様の定義については、「 [ \[5.2.13 and 5.4.7\] ](https://go.microsoft.com/fwlink/?LinkId=114525)」を参照してください。  
  
### <a name="xtimespan"></a>x:TimeSpan  
 CLR バッキングの場合は、 `x:TimeSpan` プリミティブは <xref:System.TimeSpan>に対応しています。  
  
 XAML の時刻-日付形式での解析は、本質的に `en-US` カルチャにおいて行われます。  
  
 Xaml 言語仕様の定義については、「 [ \[5.2.16 and 5.4.10\] ](https://go.microsoft.com/fwlink/?LinkId=114525)」を参照してください。  
  
### <a name="xuri"></a>x:Uri  
 CLR バッキングの場合は、 `x:Uri` プリミティブは <xref:System.Uri>に対応しています。  
  
 プロトコルのチェックは、 `x:Uri`の XAML 定義の一部ではありません。  
  
 Xaml 言語仕様の定義については、「 [ \[5.2.15 and 5.4.9\] ](https://go.microsoft.com/fwlink/?LinkId=114525)」を参照してください。  
  
### <a name="xbyte"></a>x:Byte  
 CLR バッキングの場合は、 `x:Byte` プリミティブは <xref:System.Byte>に対応しています。 は<xref:System.Byte> 、  /  符号なしとして`x:Byte`扱われます。  
  
 Xaml 言語仕様の定義については、「 [ \[5.2.10 and 5.4.4\] ](https://go.microsoft.com/fwlink/?LinkId=114525)」を参照してください。  
  
### <a name="xarray"></a>x:Array  
 CLR バッキングの場合は、 `x:Array` プリミティブは <xref:System.Array>に対応しています。  
  
 マークアップ拡張構文を使用して配列を XAML 2006 で定義することもできますが、XAML 2009 構文は言語によって定義されたプリミティブであり、マークアップ拡張機能にアクセスする必要がありません。 XAML 2006 のサポートの詳細については、「 [x:Array のマークアップ拡張機能](x-array-markup-extension.md)」を参照してください。  
  
 Xaml 言語仕様の定義については、「 [ \[5.2.18\] ](https://go.microsoft.com/fwlink/?LinkId=114525)」を参照してください。  
  
<a name="wpf_support"></a>   
## <a name="wpf-support"></a>WPF のサポート  
 WPF では XAML 2009 の機能を使用できますが、マークアップ コンパイルされていない XAML に限定されます。 WPF 向けにマークアップ コンパイルされた XAML、および XAML の BAML 形式は、現在、XAML 2009 のキーワードと機能をサポートしていません。  
  
 WPF と共に XAML 2009 の機能を使用できるシナリオとして、Loose XAML を作成し、その XAML を <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>を使用して WPF ランタイムとオブジェクト グラフに読み込む場合があります。 WPF <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> およびその <xref:System.Windows.Markup.XamlReader.Load%2A> は、XAML 2009 言語キーワードおよび機能を有効なオブジェクト グラフ表現に処理することができます。
