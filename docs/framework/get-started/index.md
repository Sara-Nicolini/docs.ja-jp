---
title: ".NET Framework の概要"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework, getting started
- getting started [.NET Framework]
ms.assetid: c693fd34-88fe-4d90-b332-19eeadf3b7e7
caps.latest.revision: 35
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 21c6a1485f3d0c38bde065d6ecc7b07d5e424c1d
ms.openlocfilehash: 327aad36a560a772e9ddb4d8d721c2545f800151
ms.contentlocale: ja-jp
ms.lasthandoff: 08/05/2017

---

# <a name="get-started-with-the-net-framework"></a>.NET Framework の概要

.NET Framework は、.NET Framework を対象としたアプリを管理するランタイム実行環境です。 これは、メモリ管理やその他のシステム サービスを提供する共通言語ランタイムと、プログラマがアプリ開発のすべての主要領域で堅牢性と信頼性の高いコードを利用できるようにするための広範なクラス ライブラリから構成されています。

<a name="Introducing"></a>
## <a name="what-is-the-net-framework"></a>.NET Framework とは

.NET Framework は、実行中のアプリにさまざまなサービスを提供するマネージ実行環境です。 これは、実行中のアプリを処理する実行エンジンである共通言語ランタイム (CLR) と、開発者が独自のアプリから呼び出すことができる検証済みの再利用可能なコード ライブラリである .NET Framework クラス ライブラリから構成されています。 .NET Framework は実行中のアプリに次のようなサービスを提供します。

- メモリ管理 多くのプログラミング言語では、プログラマがメモリの割り当てと解放およびオブジェクトの有効期間の処理を行う必要があります。 .NET Framework アプリでは、CLR がアプリに代わってこのサービスを提供します。

- 共通型システム。 従来のプログラミング言語では、コンパイラによって基本型が定義されており、このために言語間の相互運用性が複雑になります。 .NET Framework では、基本型は .NET Framework の型システムによって定義され、.NET Framework を対象とするすべての言語に共通です。

- 広範なクラス ライブラリ。 プログラマは、低レベルの共通プログラミング操作を処理するためのコードを大量に記述する代わりに、簡単にアクセスできる .NET Framework クラス ライブラリの型とメンバーのライブラリを使用します。

- 開発フレームワークとテクノロジ。 .NET Framework には、Web アプリ向けの ASP.NET、データ アクセス向けの ADO.NET、サービス指向アプリ向けの Windows Communication Foundation などの特定領域のアプリ開発のためのライブラリが用意されています。

- 言語の相互運用性。 .NET Framework を対象とする言語コンパイラは、共通中間言語 (CIL) と呼ばれる中間コードを生成し、このコードが共通言語ランタイムによって実行時にコンパイルされます。 この機能を使用すると、1 つの言語で記述されたルーチンが他の言語でもアクセスでき、プログラマは優先言語でのアプリの作成に集中できます。

- バージョンの互換性。 まれなケースを除き、特定のバージョンの .NET Framework を使用して開発されたアプリは、後続バージョンでも変更の必要なく実行されます。

- side-by-side 実行。 .NET Framework では、同じコンピューターに複数バージョンの共通言語ランタイムが共存でき、バージョン競合の解決に役立ちます。 これは、複数バージョンのアプリも共存でき、アプリがビルドされた .NET Framework のバージョンでアプリを実行できることを意味します。 side-by-side 実行は、.NET Framework の 1.0/1.1、2.0/3.0/3.5、および 4/4.5.x/4.6.x/4.7 のバージョン グループに適用されます。

- 複数バージョン対応。 開発者は、[.NET Standard](~/docs/standard/net-standard.md) を対象にすることで、Windows 7、Windows 8、Windows 8.1、Windows 10、Windows Phone、Xbox 360 などの複数の .NET Framework プラットフォームで機能するアセンブリを作成できます。

<a name="ForUsers"></a>
## <a name="the-net-framework-for-users"></a>ユーザーにとっての .NET Framework

.NET Framework アプリを開発しなくても、使用するユーザーは、.NET Framework やその操作に関する知識を持つ必要はありません。 ほとんどの場合、.NET Framework は、ユーザーにとって完全に透過的に機能します。

Windows オペレーティング システムを使用している場合は、.NET Framework がコンピューターに既にインストールされている場合があります。 また、.NET Framework を必要とするアプリをインストールすると、アプリのセットアップ プログラムにより、コンピューターに特定バージョンの .NET Framework がインストールされることがあります。 場合によっては、.NET Framework のインストールを求めるダイアログ ボックスが表示されることがあります。 アプリを実行しようとしたときにこのダイアログ ボックスが表示される場合や、コンピューターからインターネットにアクセスできる場合は、必要なバージョンの .NET Framework をインストールするための Web ページにアクセスすることができます。

通常は、コンピューターにインストールされている .NET Framework のバージョンはアンインストールしないでください。 これには、次の 2 つの理由があります。

- 使用するアプリが特定のバージョンの .NET Framework に依存している場合、そのバージョンが削除されるとアプリの互換性に影響する可能性があります。

- .NET Framework のバージョンの中には、前のバージョンのインプレース更新であるものがあります。 たとえば、[!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] はバージョン 2.0 のインプレース更新で、.NET Framework 4.7 はバージョン 4、4.5、4.5.1、4.5.2、4.6、4.6.1、および 4.6.2 のインプレース更新です。 詳細については、「[.NET Framework のバージョンおよび依存関係](../../../docs/framework/migration-guide/versions-and-dependencies.md)」を参照してください。

.NET Framework を削除する場合は、必ずコントロール パネルの [**プログラムと機能**] を使用してアンインストールしてください。 .NET Framework のバージョンを手動で削除しないでください。

1 台のコンピューターで複数バージョンの .NET Framework が同時に共存できることに注意してください。 これは、後続バージョンをインストールするために前のバージョンをアンインストールする必要がないことを意味します。

<a name="ForDevelopers"></a> 
## <a name="the-net-framework-for-developers"></a>開発者にとっての .NET Framework

開発者は、アプリを作成するために .NET Framework をサポートする任意のプログラミング言語を選択できます。 .NET Framework は言語への依存性がなく、相互運用性があるので、開発に使用した言語に関係なく、他の .NET Framework アプリおよびコンポーネントと対話できます。

.NET Framework アプリまたはコンポーネントを開発するには、次の操作を行います。

1. オペレーティング システムにプレインストールされていない場合は、アプリが対象とする .NET Framework のバージョンをインストールします。 最新の製品バージョンである .NET Framework 4.7 は Windows 10 Creators Update にプレインストールされていますが、以前のバージョンの Windows オペレーティング システムでも使用できます。 .NET Framework システム要件については、「[.NET Framework システム要件](../../../docs/framework/get-started/system-requirements.md)」を参照してください。 その他のバージョンの .NET Framework のインストールの詳細については、[インストール ガイド](../../../docs/framework/install/guide-for-developers.md)に関するページを参照してください。 .NET Framework の追加パッケージは、アウト オブ バンドでリリースされます。これは、通常のリリース サイクルや定期的なリリース サイクルではなく、ローリング方式でリリースされるということを意味します。 これらのパッケージの詳細については、「[.NET Framework および特別なリリース](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)」を参照してください。

2. .NET Framework でサポートされている、アプリ開発に使用する言語を選択します。 Microsoft の Visual Basic、C#、Visual F#、および C++/CLI を含む多くの言語から選択できます  (.NET Framework のアプリを開発できるプログラミング言語は、[共通言語基盤 (CLI) 仕様](http://go.microsoft.com/fwlink/?LinkId=199862)に準拠します)。

3. アプリの作成に使用する、選択したプログラミング言語をサポートする開発環境を選択してインストールします。 [Visual Studio](http://go.microsoft.com/fwlink/?LinkId=325532) は、.NET Framework アプリ用の Microsoft 統合開発環境 (IDE) です。 これには、いくつかエディションがあります。

.NET Framework を対象にしたアプリの開発の詳細については、「[.NET Framework の開発ガイド](../../../docs/framework/development-guide.md)」を参照してください。

## <a name="related-topics"></a>関連トピック

| タイトル | 説明 |
| ----- |------------ |
| [概要](../../../docs/framework/get-started/overview.md) | .NET Framework を対象としたアプリを作成する開発者向けの詳細情報を提供します。 |
| [インストール ガイド](../../../docs/framework/install/index.md) | .NET Framework のインストールに関する情報を提供します。 |  
| [NET Framework および特別なリリース](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md) | .NET Framework のアウト オブ バンド リリースと、これらをアプリ内で使用する方法について説明します。 |
| [システム要件](../../../docs/framework/get-started/system-requirements.md) | .NET Framework を実行するためのハードウェアおよびソフトウェアの要件を示します。 |
| [.NET Core とオープン ソース](../../../docs/framework/get-started/net-core-and-open-source.md) | .NET Core と .NET Framework の関係性、およびオープン ソースの .NET Core プロジェクトにアクセスする方法について説明します。 |
| [.NET Core ドキュメント](https://docs.microsoft.com/dotnet/) | .NET Core の概念と API リファレンス ドキュメントを提供します。 |

## <a name="see-also"></a>関連項目

[.NET Framework ガイド](../../../docs/framework/index.md)   
[新機能](../../../docs/framework/whats-new/index.md)   
[.NET API ブラウザー](/dotnet/api/)   
[開発ガイド](../../../docs/framework/development-guide.md)

