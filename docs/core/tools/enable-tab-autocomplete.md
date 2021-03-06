---
title: タブ補完を有効にする
description: この記事では、PowerShell、Bash、zsh、fish 向けの .NET CLI のタブ補完を有効にする方法を説明します。
author: adegeo
ms.author: adegeo
ms.topic: how-to
ms.date: 11/03/2019
ms.openlocfilehash: b5b63166faa1762d9fa82a93aa70aebb33167630
ms.sourcegitcommit: 65af0f0ad316858882845391d60ef7e303b756e8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/05/2021
ms.locfileid: "99585560"
---
# <a name="how-to-enable-tab-completion-for-the-net-cli"></a>.NET CLI のタブ補完を有効にする方法

**この記事の対象:** ✔️ .NET Core 2.1 SDK 以降のバージョン

この記事では、4 つのシェル、PowerShell、Bash、zsh、fish のタブ補完を構成する方法について説明します。 他のシェルについては、タブ補完を構成する方法に関するシェルのドキュメントを参照してください。

セットアップが完了したら、シェルに `dotnet` コマンドを入力した後、TAB キーを押すと、.NET CLI のタブ補完がトリガーされます。 現在のコマンド ラインが `dotnet complete` コマンドに送信され、結果がシェルによって処理されます。 何かを `dotnet complete` コマンドに直接送信することで、タブ補完を有効にせずに結果をテストすることができます。 次に例を示します。

```console
> dotnet complete "dotnet a"
add
clean
--diagnostics
migrate
pack
```

そのコマンドが機能しない場合は、.NET Core 2.0 SDK 以降がインストールされていることを確認します。 インストールされているにもかかわらず、そのコマンドが機能しない場合は、`dotnet` コマンドが .NET Core 2.0 SDK 以降のバージョンに解決されることを確認します。 `dotnet --version` コマンドを使用して、現在のパスの解決先となっている `dotnet` のバージョンを確認します。 詳細については、「[使用する .NET のバージョンを選択する](../versions/selection.md)」を参照してください。

### <a name="examples"></a>使用例

タブ補完で提供されることの例をいくつか次に示します。

入力                                | 結果                                                                     | 理由
:------------------------------------|:----------------------------------------------------------------------------|:--------------------------------
`dotnet a⇥`                          | `dotnet add`                                                                 | アルファベット順では、`add` が最初のサブコマンドのため。
`dotnet add p⇥`                      | `dotnet add --help`                                                          | タブ補完が部分文字列と一致しており、アルファベット順では `--help` が先になるため。
`dotnet add p⇥⇥`                    | `dotnet add package`                                                          | Tab キーを 2 回押すと、次の修正候補が表示されるため。
`dotnet add package Microsoft⇥`      | `dotnet add package Microsoft.ApplicationInsights.Web`                      | 結果はアルファベット順に返されるため。
`dotnet remove reference ⇥`          | `dotnet remove reference ..\..\src\OmniSharp.DotNet\OmniSharp.DotNet.csproj` | タブ補完がプロジェクト ファイルに対応しているため。

## <a name="powershell"></a>PowerShell

.NET CLI の **PowerShell** にタブ補完を追加するには、変数 `$PROFILE` に格納されているプロファイルを作成または編集します。 詳細については、[プロファイルの作成方法](/powershell/module/microsoft.powershell.core/about/about_profiles#how-to-create-a-profile)と[プロファイルと実行ポリシー](/powershell/module/microsoft.powershell.core/about/about_profiles#profiles-and-execution-policy)のトピックを参照してください。

自分のプロファイルに次のコードを追加します。

```powershell
# PowerShell parameter completion shim for the dotnet CLI
Register-ArgumentCompleter -Native -CommandName dotnet -ScriptBlock {
     param($commandName, $wordToComplete, $cursorPosition)
         dotnet complete --position $cursorPosition "$wordToComplete" | ForEach-Object {
            [System.Management.Automation.CompletionResult]::new($_, $_, 'ParameterValue', $_)
         }
 }
```

## <a name="bash"></a>Bash

.NET CLI の **bash** シェルにタブ補完を追加するには、次のコードを `.bashrc` ファイルに追加します。

```bash
# bash parameter completion for the dotnet CLI

_dotnet_bash_complete()
{
  local word=${COMP_WORDS[COMP_CWORD]}

  local completions
  completions="$(dotnet complete --position "${COMP_POINT}" "${COMP_LINE}" 2>/dev/null)"
  if [ $? -ne 0 ]; then
    completions=""
  fi

  COMPREPLY=( $(compgen -W "$completions" -- "$word") )
}

complete -f -F _dotnet_bash_complete dotnet
```

## <a name="zsh"></a>zsh

.NET CLI の **zsh** シェルにタブ補完を追加するには、次のコードを `.zshrc` ファイルに追加します。

```zsh
# zsh parameter completion for the dotnet CLI

_dotnet_zsh_complete()
{
  local completions=("$(dotnet complete "$words")")

  reply=( "${(ps:\n:)completions}" )
}

compctl -K _dotnet_zsh_complete dotnet
```

## <a name="fish"></a>fish

.NET CLI の **fish** シェルにタブ補完を追加するには、次のコードを `config.fish` ファイルに追加します。

```fish
complete -f -c dotnet -a "(dotnet complete)"
```
