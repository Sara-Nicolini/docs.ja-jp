---
title: "依存関係プロパティのメタデータ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "API, メタデータ"
  - "依存関係プロパティ, メタデータ"
  - "メタデータ, 依存関係プロパティ"
  - "オーバーライド (メタデータを)"
ms.assetid: d01ed009-b722-41bf-b82f-fe1a8cdc50dd
caps.latest.revision: 24
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 23
---
# 依存関係プロパティのメタデータ
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] プロパティ システムには、リフレクションや一般的な [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 特性から得られる以上の詳細なプロパティ情報を提供するメタデータ報告システムが含まれています。  [依存関係プロパティ](GTMT)のメタデータは、[依存関係プロパティ](GTMT)を定義するクラスで個別に割り当てることも、[依存関係プロパティ](GTMT)を別のクラスに追加する際に変更することもできます。また、[依存関係プロパティ](GTMT)をその定義元の基本クラスから継承するすべての派生クラスで明確にオーバーライドすることもできます。  
  
   
  
<a name="prerequisites"></a>   
## 必要条件  
 このトピックでは、ユーザーが [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] クラスの既存の依存関係プロパティの使用という観点から依存関係プロパティを理解し、「[依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)」トピックを通読していることを前提としています。  このトピックの例に従うには、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] について理解し、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションの作成方法に精通している必要があります。  
  
<a name="dp_metadata_contents"></a>   
## 依存関係プロパティのメタデータの使用方法  
 依存関係プロパティのメタデータは、依存プロパティの特性を照会して調べることができるオブジェクトとして存在します。  また、プロパティ システムは、特定の依存関係プロパティを処理する際に、このメタデータに頻繁にアクセスします。  依存関係プロパティのメタデータ オブジェクトには、次のような情報が格納されます。  
  
-   依存関係プロパティの既定値 \(ローカル値、スタイル、継承などによってその他の依存関係プロパティ値が指定されない場合\)。  依存関係プロパティの値を割り当てる際の、既定値と、プロパティ システムで使用される優先順位の関係に関する詳細な説明については、「[依存関係プロパティ値の優先順位](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md)」を参照してください。  
  
-   所有者型に基づく強制または変更通知の動作に影響を与えるコールバック実装への参照。  多くの場合、これらのコールバックは非パブリックなアクセス レベルで定義されます。したがって、参照が、許可されたアクセス スコープ内にない限り、一般にメタデータから実際の参照を取得することはできません。  依存関係プロパティのコールバックの詳細については、「[依存関係プロパティのコールバックと検証](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md)」を参照してください。  
  
-   対象の依存関係プロパティが [WPF フレームワーク レベル](GTMT)のプロパティと見なされる場合、[WPF フレームワーク レベル](GTMT)の依存関係プロパティ特性がメタデータに含まれる可能性があります。これは、[WPF フレームワーク レベル](GTMT)のレイアウト エンジンやプロパティ継承ロジックなどのサービスの情報および状態を報告します。  この内容に関する依存関係プロパティのメタデータの詳細については、「[フレームワーク プロパティ メタデータ](../../../../docs/framework/wpf/advanced/framework-property-metadata.md)」を参照してください。  
  
<a name="APIs"></a>   
## メタデータ API  
 プロパティ システムで使用されるほとんどのメタデータ情報を報告する型は <xref:System.Windows.PropertyMetadata> クラスです。  メタデータ インスタンスは、依存関係プロパティをプロパティ システムに登録する際に必要に応じて指定されます。それ自体を所有者として追加する追加の型、または基本クラスの依存関係プロパティ定義から継承したメタデータをオーバーライドする追加の型に再度指定することもできます   \(プロパティ登録でメタデータが指定されない場合は、そのクラスの既定値を使用して既定の <xref:System.Windows.PropertyMetadata> が作成されます\)。<xref:System.Windows.DependencyObject> インスタンスの依存関係プロパティからメタデータを取得するさまざまな <xref:System.Windows.DependencyProperty.GetMetadata%2A> オーバーロードを呼び出すと、登録されているメタデータが <xref:System.Windows.PropertyMetadata> として返されます。  
  
 <xref:System.Windows.PropertyMetadata> クラスは、[WPF フレームワーク レベル](GTMT) クラスなどのアーキテクチャ区分に対してより具体的なメタデータを提供するために派生されます。  <xref:System.Windows.UIPropertyMetadata> は、アニメーション報告を追加し、<xref:System.Windows.FrameworkPropertyMetadata> は、前のセクションで説明した [WPF フレームワーク レベル](GTMT) プロパティを提供します。  依存関係プロパティを登録すると、これらの <xref:System.Windows.PropertyMetadata> 派生クラスにその依存関係プロパティを登録できるようになります。  メタデータを検査すると、基本 <xref:System.Windows.PropertyMetadata> 型が派生クラスにキャストされる場合があります。これにより、より具体的な情報プロパティを検査することができます。  
  
> [!NOTE]
>  このドキュメントでは、<xref:System.Windows.FrameworkPropertyMetadata> で指定できるプロパティ特性を "フラグ" と呼ぶことがあります。  依存関係プロパティの登録やメタデータのオーバーライドで使用するメタデータ インスタンスを新しく作成する場合、フラグ列挙体である <xref:System.Windows.FrameworkPropertyMetadataOptions> を使用してこれらの値を指定し、この列挙体の値 \(連結された値である可能性があります\) を <xref:System.Windows.FrameworkPropertyMetadata> コンストラクターに渡します。  ただし、メタデータが構築されると、これらのオプション特性は、構築元の列挙値ではなく、一連のブール型プロパティとして <xref:System.Windows.FrameworkPropertyMetadata> 内で公開されます。  これらのブール型プロパティを使用すると、目的の情報を取得するためにフラグ列挙値に対してマスクを適用することなく、各条件をチェックすることができます。  コンストラクターは、コンストラクター シグネチャを適切な長さに保つために、連結された <xref:System.Windows.FrameworkPropertyMetadataOptions> を使用します。一方、実際に構築されたメタデータは、より直感的な方法でメタデータを照会できるようにするために、プロパティを個別に公開します。  
  
<a name="override_or_subclass"></a>   
## メタデータをオーバーライドする場合、クラスを派生する場合  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プロパティ システムには、依存関係プロパティを完全に再実装することなく、依存関係プロパティの一部の特性を変更するための機能が用意されています。  これは、特定の型に存在する依存関係プロパティについて、そのプロパティ メタデータの別のインスタンスを構築することで実現されます。  既存の依存関係プロパティの大部分は仮想プロパティではありません。したがって、厳密には、継承クラスでの依存関係プロパティの "再実装" は、既存のメンバーをシャドウすることによってのみ実現されます。  
  
 型の依存関係プロパティに対して有効にしようとしているシナリオが、既存の依存関係プロパティの特性の変更では実現できない場合、派生クラスを作成し、その派生クラスでカスタム依存関係プロパティを宣言することが必要になる場合があります。  カスタム依存関係プロパティは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] で定義されている依存関係プロパティとまったく同じように動作します。  カスタム依存関係プロパティの詳細については、「[カスタム依存関係プロパティ](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)」を参照してください。  
  
 オーバーライドすることができない依存関係プロパティの代表的な特性の 1 つは、依存関係プロパティの値型です。  目的の動作にほぼ合致する依存関係プロパティを継承していても、その依存関係プロパティに別の型が必要な場合には、カスタム依存関係プロパティを実装し、型変換またはカスタム クラスのその他の実装を通じてプロパティをリンクする必要があります。  また、既存の <xref:System.Windows.ValidateValueCallback> を置換することはできません。このコールバックが、そのメタデータ内ではなく、登録フィールド自体に存在するためです。  
  
<a name="scenarios"></a>   
## 既存のメタデータを変更するシナリオ  
 既存の依存関係プロパティのメタデータを使用している場合、依存関係プロパティのメタデータを変更する一般的なシナリオの 1 つは、既定値を変更することです。  プロパティ システム コールバックの変更または追加は、より高度なシナリオです。  依存関係プロパティ間の異なる相互関係が派生クラスの実装に含まれている場合は、プロパティ システム コールバックの変更または追加が必要になることがあります。  コードと宣言的な使用方法の両方をサポートするプログラミング モデルを使用する条件の 1 つとして、プロパティを任意の順序で設定できる必要があります。  したがって、依存関係プロパティはすべて、コンテキストを使用せずにジャスト イン タイムで設定する必要があります。また、設定順序 \(コンストラクター内の順序など\) に依存することもできません。  この内容に関するプロパティ システムの詳細については、「[依存関係プロパティのコールバックと検証](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md)」を参照してください。  検証コールバックは、メタデータの一部ではなく、依存関係プロパティ識別子の一部であることに注意してください。  したがって、検証コールバックは、メタデータのオーバーライドでは変更できません。  
  
 既存の依存関係プロパティに対して、[WPF フレームワーク レベル](GTMT)のプロパティのメタデータ オプションの変更が必要になる場合があります。  これらのオプションは、[WPF フレームワーク レベル](GTMT)のプロパティに関する特定の既知の条件を、レイアウト システムなどの他の [WPF フレームワーク レベル](GTMT)のプロセスに伝達します。  通常、これらのオプションを設定するのは、新しい依存関係プロパティを登録するときだけです。ただし、<xref:System.Windows.DependencyProperty.OverrideMetadata%2A> 呼び出しまたは <xref:System.Windows.DependencyProperty.AddOwner%2A> 呼び出しの一部として [WPF フレームワーク レベル](GTMT)のプロパティのメタデータを変更することもできます。  使用する具体的な値および詳細については、「[フレームワーク プロパティ メタデータ](../../../../docs/framework/wpf/advanced/framework-property-metadata.md)」を参照してください。  新しく登録した依存関係プロパティに対してこれらのオプションを設定する方法の詳細については、「[カスタム依存関係プロパティ](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)」を参照してください。  
  
<a name="dp_override_metadata"></a>   
### メタデータのオーバーライド  
 メタデータのオーバーライドの主な目的は、型に存在する依存関係プロパティに適用される、メタデータから派生したさまざまな動作を変更できるようにすることです。  この理由については、「[メタデータ](#dp_metadata_contents)」セクションで詳しく説明します。  コード例を含む詳細については、「[依存関係プロパティのメタデータをオーバーライドする](../../../../docs/framework/wpf/advanced/how-to-override-metadata-for-a-dependency-property.md)」を参照してください。  
  
 プロパティのメタデータは、登録 \(<xref:System.Windows.DependencyProperty.Register%2A>\) の呼び出し時に依存関係プロパティに対して指定できます。  ただし、多くの場合、その依存関係プロパティを継承するクラスに対して、型固有のメタデータを提供する必要があります。  これを行うには、<xref:System.Windows.DependencyProperty.OverrideMetadata%2A> メソッドを呼び出します。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] の例では、<xref:System.Windows.UIElement.Focusable%2A> 依存関係プロパティを最初に登録する型は <xref:System.Windows.FrameworkElement> クラスです。  ただし、<xref:System.Windows.Controls.Control> クラスは、この依存関係プロパティのメタデータをオーバーライドし、それ自体の初期既定値を `false` から `true` に変更して提供します。オーバーライドしない場合は、元の <xref:System.Windows.UIElement.Focusable%2A> 実装を再利用します。  
  
 メタデータをオーバーライドすると、さまざまなメタデータ特性がマージされるか置き換えられます。  
  
-   <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> はマージされます。  新しい <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> を追加すると、そのコールバックがメタデータに格納されます。  オーバーライド時に <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> を指定しないと、<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> の値が昇格され、メタデータでそれを指定した最も近い先祖からの参照となります。  
  
-   <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> の実際のプロパティ システム動作では、階層内のすべてのメタデータ所有者用の実装が維持されてテーブルに追加されます。プロパティ システムによる実行順序としては、派生回数の最も多いクラスのコールバックが最初に呼び出されます。  
  
-   <xref:System.Windows.PropertyMetadata.DefaultValue%2A> は置き換えられます。  オーバーライド時に <xref:System.Windows.PropertyMetadata.DefaultValue%2A> を指定しないと、<xref:System.Windows.PropertyMetadata.DefaultValue%2A> の値は、メタデータでそれを指定した最も近い先祖によって決まります。  
  
-   <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> 実装は置き換えられます。  新しい <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> を追加すると、そのコールバックがメタデータに格納されます。  オーバーライド時に <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> を指定しないと、<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> の値が昇格され、メタデータでそれを指定した最も近い先祖からの参照となります。  
  
-   プロパティ システム動作では、直接のメタデータ内の <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> だけが呼び出されます。  階層内の他の <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> 実装への参照は行われません。  
  
 この動作は <xref:System.Windows.PropertyMetadata.Merge%2A> によって実装され、派生メタデータ クラス上でオーバーライドできます。  
  
#### 添付プロパティのメタデータのオーバーライド  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、[添付プロパティ](GTMT)は依存関係プロパティとして実装されます。  このことは、添付プロパティもプロパティ メタデータを持ち、これを個々のクラスでオーバーライドできることを意味します。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の添付プロパティのスコープでは、通常、任意の <xref:System.Windows.DependencyObject> に、添付プロパティを設定できます。  したがって、クラスのインスタンスで設定されている場合、<xref:System.Windows.DependencyObject> 派生クラスは添付プロパティのメタデータをオーバーライドできます。  オーバーライドできるのは、既定値、コールバック、または [WPF フレームワーク レベル](GTMT)の特性報告プロパティです。  添付プロパティがクラスのインスタンスで設定されている場合、そのオーバーライド プロパティ メタデータ特性が適用されます。  たとえば、プロパティが他では特に指定されていないときには、オーバーライド値がクラスのインスタンス上の添付プロパティの値として報告されるように、既定値をオーバーライドできます。  
  
> [!NOTE]
>  <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A> プロパティは、添付プロパティに関係しません。  
  
<a name="dp_add_owner"></a>   
### 既存の依存関係プロパティの所有者としてのクラスの追加  
 クラスは、<xref:System.Windows.DependencyProperty.AddOwner%2A> メソッドを使用することで、それ自体を登録済みの依存関係プロパティの所有者として追加できます。  これにより、当初は別の型に対して登録された依存関係プロパティをクラスで使用できるようになります。  通常、追加するクラスは、所有者としてその依存関係プロパティを最初に登録した型の派生クラスではありません。  これにより、元の所有者クラスと追加するクラスが同一のクラス階層内にない場合でも、クラスとその派生クラスで[依存関係プロパティ](GTMT)の実装を "継承" することが事実上可能になります。  また、追加するクラスとすべての派生クラスでは、型固有のメタデータを元の依存関係プロパティに提供することができます。  
  
 追加するクラスは、プロパティ システムのユーティリティ メソッドを介してそれ自体を所有者として追加するだけでなく、追加のパブリック メンバーをそれ自体で宣言する必要があります。これは、[依存関係プロパティ](GTMT)を完全な形でプロパティ システムに登録し、コードとマークアップの両方に対して公開するためです。  既存の依存関係プロパティを追加するクラスは、その依存関係プロパティのオブジェクト モデルを公開する限り、新しいカスタム依存関係プロパティを定義するクラスと同様の役割を負います。  これらのメンバーの中で最初に公開するのは、依存関係プロパティの識別子フィールドです。  このフィールドは、<xref:System.Windows.DependencyProperty.AddOwner%2A> 呼び出しの戻り値に割り当てられる、<xref:System.Windows.DependencyProperty> 型の `public static readonly` フィールドである必要があります。  2 番目に定義するメンバーは、[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] の "ラッパー" プロパティです。  ラッパーを使用すると、コード内での依存関係プロパティの操作がずっと簡単になります \(<xref:System.Windows.DependencyObject.SetValue%2A> を毎回呼び出す必要がなくなり、ラッパー内で 1 回呼び出すだけで済むようになります\)。  このラッパーの実装方法は、カスタム[依存関係プロパティ](GTMT)を登録する場合の実装方法とまったく同じです。  [依存関係プロパティ](GTMT)の実装の詳細については、「[カスタム依存関係プロパティ](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)」および「[依存関係プロパティの所有者の種類を追加する](../../../../docs/framework/wpf/advanced/how-to-add-an-owner-type-for-a-dependency-property.md)」を参照してください。  
  
#### AddOwner および添付プロパティ  
 所有者クラスで添付プロパティとして定義されている依存関係プロパティに対して、<xref:System.Windows.DependencyProperty.AddOwner%2A> を呼び出すことができます。  通常、これは、以前の添付プロパティを非添付の依存関係プロパティとして公開する目的で行います。  次に、<xref:System.Windows.DependencyProperty.AddOwner%2A> の戻り値を、依存関係プロパティの識別子として使用される `public static readonly` フィールドとして公開し、プロパティがメンバー テーブルに表示され、クラス内で非添付プロパティを使用できるように、適切な "ラッパー" プロパティを定義します。  
  
## 参照  
 <xref:System.Windows.PropertyMetadata>   
 <xref:System.Windows.DependencyObject>   
 <xref:System.Windows.DependencyProperty>   
 <xref:System.Windows.DependencyProperty.GetMetadata%2A>   
 [依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)   
 [フレームワーク プロパティ メタデータ](../../../../docs/framework/wpf/advanced/framework-property-metadata.md)