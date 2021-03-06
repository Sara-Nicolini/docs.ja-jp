---
title: "dotnet store コマンド"
description: "'dotnet store' コマンドは、指定したアセンブリをランタイム パッケージ ストアに格納します。"
author: bleroy
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.translationtype: HT
ms.sourcegitcommit: a19ab54a6cc44bd7acd1e40a4ca94da52bf14297
ms.openlocfilehash: fcf1eeba0709e05cff124bc3ae7bb93f4ca57128
ms.contentlocale: ja-jp
ms.lasthandoff: 08/14/2017

---
# <a name="dotnet-store"></a>dotnet store

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

## <a name="name"></a>名前

`dotnet store` - 指定したアセンブリを[ランタイム パッケージ ストア](../deploying/runtime-store.md)に格納します。

## <a name="synopsis"></a>構文

`dotnet store -m|--manifest -f|--framework -r|--runtime  [--framework-version] [-h|--help] [--output] [--skip-optimization] [--skip-symbols] [-v|--verbosity] [--working-dir]`

## <a name="description"></a>説明

`dotnet store` - 指定したアセンブリを[ランタイム パッケージ ストア](../deploying/runtime-store.md)に格納します。 既定では、アセンブリは、ターゲット ランタイムとフレームワークに合わせて最適化されます。 詳細については、[「ランタイム パッケージ ストア」](../deploying/runtime-store.md) を参照してください。

## <a name="required-options"></a>必須オプション

`-f|--framework <FRAMEWORK>`

[ターゲット フレームワーク](../../standard/frameworks.md)を指定します。

`-m|--manifest <PATH_TO_MANIFEST_FILE>`

"*パッケージ ストア マニフェスト ファイル*" は、格納するパッケージの一覧を含む XML ファイルです。 マニフェスト ファイルの形式は、*csproj* 形式と互換性があります。 そのため、必要なパッケージを参照する *csproj* プロジェクト ファイルを `-m|--manifest` オプションと使用することで、ランタイム パッケージ ストアにアセンブリを格納することができます。 複数のマニフェスト ファイルを指定するには、ファイルごとにオプションとパスを繰り返します: `--manifest packages1.csproj --manifest packages2.csproj`

`-r|--runtime <RUNTIME_IDENTIFIER>`

ターゲットとするランタイム識別子。

## <a name="optional-options"></a>省略可能なオプション

`--framework-version <FRAMEWORK_VERSION>`

.NET Core SDK のバージョンを指定します。 このオプションでは、`-f|--framework` オプションで指定したフレームワーク以降の特定のフレームワーク バージョンを選択することができます。

`-h|--help`

ヘルプ情報を表示します。

`-o|--output <OUTPUT_DIRECTORY>`

ランタイム パッケージ ストアへのパスを指定します。 指定しない場合、ユーザー プロファイル .NET Core インストール ディレクトリのサブディレクトリ *store* が既定値となります。

`--skip-optimization`

最適化フェーズをスキップします。

`--skip-symbols`

シンボルの生成をスキップします。 現時点では、Windows と Linux 上でのみシンボルを生成することができます。

`-v|--verbosity <LEVEL>`

コマンドの詳細レベルを設定します。 指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。

`-w|--working-dir <INTERMEDIATE_WORKING_DIRECTORY>`

コマンドで使用される作業ディレクトリです。 指定しない場合、現在のディレクトリの *obj* サブディレクトリが使用されます。

## <a name="examples"></a>例

.NET Core 2.0.0 の *packages.csproj* プロジェクト ファイルで指定されたパッケージを格納します。

`dotnet store --manifest packages.csproj --framework-version 2.0.0`

*packages.csproj* で指定されたパッケージを最適化なしで格納します。

`dotnet store --manifest packages.csproj --skip-optimization`

## <a name="see-also"></a>関連項目

[ランタイム パッケージ ストア](../deploying/runtime-store.md)   

