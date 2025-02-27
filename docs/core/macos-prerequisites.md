---
title: Mac における .NET Core の前提条件
description: macOS コンピューターで .NET Core アプリケーションを開発、展開、および実行するために必要なサポート対象 macOS のバージョンと .NET Core の依存関係。
author: thraka
ms.author: adegeo
ms.custom: updateeachvsrelease
ms.date: 10/11/2019
ms.openlocfilehash: 2d4fc0b37be08988440325db8b507124c36bf053
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318320"
---
# <a name="prerequisites-for-net-core-on-macos"></a>macOS における .NET Core の前提条件

この記事では、macOS コンピューターで .NET Core アプリケーションを開発、展開、および実行するために必要なサポート対象 macOS のバージョンと .NET Core の依存関係を示します。 後述のサポート対象 OS のバージョンと依存関係は、Mac で .NET Core アプリを開発する 3 つの方法 ([好きなエディターでコマンド ラインを使用](tutorials/using-with-xplat-cli.md)、[Visual Studio Code を使用](https://code.visualstudio.com/)、および [Visual Studio for Mac を使用](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)) に適用されます。

## <a name="downloads-and-dependencies"></a>ダウンロードと依存関係

<!-- markdownlint-disable MD025 -->

# <a name="net-core-30tabnetcore30"></a>[.NET Core 3.0](#tab/netcore30)

.NET Core 3.0 は、**macOS High Sierra (バージョン 10.13)** 以降のバージョンでサポートされています。 **x64** CPU アーキテクチャが必要です。

[.NET Core 3.0 のダウンロード](https://dotnet.microsoft.com/download/dotnet-core/3.0) ページから .NET Core SDK をダウンロードしてインストールします。 .NET Core 3.0 でサポートされているオペレーティング システム、ディストリビューション、バージョン、サポートされていない OS バージョン、ライフサイクル ポリシー リンクの完全なリストについては、[.NET Core 3.0 がサポートされる OS バージョン](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)に関するページを参照してください。

既知の問題の一覧については、「[.NET Core の既知の問題](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-known-issues.md)」をご覧ください。

# <a name="net-core-22tabnetcore22"></a>[.NET Core 2.2](#tab/netcore22)

.NET Core 2.2 は、**macOS Sierra (バージョン 10.12)** 以降のバージョンでサポートされています。 **x64** CPU アーキテクチャが必要です。

[.NET Core 2.2 のダウンロード](https://dotnet.microsoft.com/download/dotnet-core/2.2) ページから .NET Core SDK をダウンロードしてインストールします。 .NET Core 2.2 でサポートされているオペレーティング システム、ディストリビューション、バージョン、サポートされていない OS バージョン、ライフサイクル ポリシー リンクの完全なリストについては、[.NET Core 2.2 がサポートされる OS バージョン](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)に関するページを参照してください。

既知の問題の一覧については、「[.NET Core の既知の問題](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-known-issues.md)」をご覧ください。

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

.NET Core 2.1 は、**macOS Sierra (バージョン 10.12)** 以降のバージョンでサポートされています。 **x64** CPU アーキテクチャが必要です。

[.NET Core 2.1 のダウンロード](https://dotnet.microsoft.com/download/dotnet-core/2.1) ページから .NET Core SDK をダウンロードしてインストールします。 .NET Core 2.1 でサポートされているオペレーティング システム、ディストリビューション、バージョン、サポートされていない OS バージョン、ライフサイクル ポリシー リンクの完全なリストについては、[.NET Core 2.1 がサポートされる OS バージョン](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)に関するページを参照してください。

既知の問題の一覧については、「[.NET Core の既知の問題](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-known-issues.md)」をご覧ください。

---

## <a name="libgdiplus"></a>libgdiplus

*System.Drawing.Common* アセンブリを使用する .NET Core アプリケーションでは、libgdiplus をインストールする必要があります。

libgdiplus を取得する簡単な方法は、macOS の [Homebrew ("brew")](https://brew.sh/) パッケージ マネージャーを使用することです。 *brew* をインストールしたら、端末 (コマンド) プロンプトで次のコマンドを実行して libgdiplus をインストールします。

```console
brew update
brew install libgdiplus
```

## <a name="visual-studio-for-mac"></a>Visual Studio for Mac

.NET Core SDK を使用して .NET Core アプリケーションを開発する場合は、好きなエディターを使用できます。 ただし、Mac 上の統合開発環境で .NET Core アプリケーションを開発する場合には、[Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) を使用できます。
