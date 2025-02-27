---
title: 方法:インストールされている NET Framework セキュリティ更新プログラムおよび修正プログラムを確認する
description: コンピューターにインストールされている NET Framework セキュリティ更新プログラムおよび修正プログラムを確認する方法について説明します。
ms.date: 11/27/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- updates, determining for .NET Framework
- .NET Framework, determining updates
ms.assetid: 53c7b5f7-d47a-402a-b194-7244a696a88b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1c69d4bb370087dddafbfed41cbfb1fef229677c
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318973"
---
# <a name="how-to-determine-which-net-framework-security-updates-and-hotfixes-are-installed"></a>方法:インストールされている NET Framework セキュリティ更新プログラムおよび修正プログラムを確認する

この記事では、コンピューターにインストールされている NET Framework セキュリティ更新プログラムおよび修正プログラムを確認する方法について説明します。

> [!NOTE]
> この記事で紹介する手法にはすべて、管理特権が与えられたアカウントが必要になります。

## <a name="to-find-installed-updates-using-the-registry"></a>レジストリを利用し、インストールされている更新プログラムを見つける

コンピューターにインストールされている .NET Framework のバージョンごとのインストール済みのセキュリティ更新プログラムおよび修正プログラムは、Windows レジストリに一覧表示されます。 レジストリ エディター (*regedit.exe*) プログラムを使用して、この情報を表示することができます。

1. プログラム **regedit.exe** を開きます。 Windows 8 以降のバージョンでは、 **[スタート]** ![Windows キー ロゴのスクリーンショット](./media/how-to-determine-which-net-framework-updates-are-installed/windows-keyboard-logo.png "Windowskeyboardlogo") を右クリックし、 **[実行]** を選択します。 **[開く]** ボックスに「**regedit**」と入力し、 **[OK]** を選択します。

2. レジストリ エディターで、次のサブキーを開きます。

     `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates`

     インストールされている更新プログラムは、適用された .NET Framework バージョンを識別するサブキーの下に一覧表示されています。 各更新プログラムは、サポート技術情報の (KB) 番号で識別されます。

レジストリ エディターでは、各バージョンの .NET Framework バージョンとインストールされている更新プログラムが別々のサブキーに格納されます。 インストールされているバージョン番号の詳細については、「[方法: インストールされている .NET Framework バージョンを確認する](how-to-determine-which-versions-are-installed.md)」を参照してください。

## <a name="to-find-installed-updates-by-querying-the-registry-in-code"></a>コードでレジストリにクエリを実行し、インストールされている更新プログラムを見つける

次の例では、コンピューターにインストールされている .NET Framework セキュリティ更新プログラムおよび修正プログラムをプログラミングによって判断します。

[!code-csharp[ListUpdates](../../../samples/snippets/csharp/VS_Snippets_CLR/listupdates/cs/program.cs)]
[!code-vb[ListUpdates](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listupdates/vb/program.vb)]

この例では次のような出力が生成されます。

```console
Microsoft .NET Framework 4 Client Profile
  KB2468871
  KB2468871v2
  KB2478063
  KB2533523
  KB2544514
  KB2600211
  KB2600217
Microsoft .NET Framework 4 Extended
  KB2468871
  KB2468871v2
  KB2478063
  KB2533523
  KB2544514
  KB2600211
  KB2600217
```

## <a name="to-find-installed-updates-by-querying-the-registry-in-powershell"></a>PowerShell でレジストリにクエリを実行し、インストールされている更新プログラムを見つける

次の例では、PowerShell を利用し、コンピューターにインストールされている .NET Framework セキュリティ更新プログラムおよび修正プログラムを判断する方法を示します。

```powershell
$DotNetVersions = Get-ChildItem HKLM:\SOFTWARE\WOW6432Node\Microsoft\Updates | Where-Object {$_.name -like
 "*.NET Framework*"}

ForEach($Version in $DotNetVersions){
    
   $Updates = Get-ChildItem $Version.PSPath
    $Version.PSChildName
    ForEach ($Update in $Updates){
       $Update.PSChildName
       }
}
```

この例では次のような出力が生成されます。

```console
Microsoft .NET Framework 4 Client Profile
KB2468871
KB2468871v2
KB2478063
KB2533523
KB2544514
KB2600211
KB2600217
Microsoft .NET Framework 4 Extended
KB2468871
KB2468871v2
KB2478063
KB2533523
KB2544514
KB2600211
KB2600217
```

## <a name="see-also"></a>関連項目

- [方法: インストールされている .NET Framework バージョンを確認する](how-to-determine-which-versions-are-installed.md)
- [開発者向けの .NET Framework のインストール](../install/guide-for-developers.md)
- [バージョンおよび依存関係](versions-and-dependencies.md)
