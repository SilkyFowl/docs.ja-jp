---
title: 使用する .NET のバージョンを選択する
description: .NET によってプログラムのランタイムのバージョンが自動的に検出されて選択されるしくみについて説明します。 さらに、この記事では、特定のバージョンを強制的に使用する方法についても説明します。
author: adegeo
ms.author: adegeo
ms.date: 02/05/2021
ms.openlocfilehash: 2fe30041cbf85de644d9ba17330884961fcf7504
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791999"
---
# <a name="select-the-net-version-to-use"></a>使用する .NET のバージョンを選択する

この記事では、.NET ツール、SDK、ランタイムによって使用されるバージョン選択ポリシーについて説明します。 これらのポリシーでは、指定バージョンを使用してアプリケーションを実行することと、開発者のコンピューターとエンド ユーザーのコンピューターの両方を簡単にアップグレードすることを両立させています。 これらのポリシーによって次のアクションが実行されます。

- セキュリティと信頼性の更新プログラムを含む、.NET の簡単で効率的な展開。
- ターゲット ランタイムとは関係なく、最新のツールとコマンドを使用する。

バージョンが次のように選択されます。

- SDK コマンドを実行すると、[SDK はインストールされている最新のバージョンを使用します](#the-sdk-uses-the-latest-installed-version)。
- アセンブリをビルドすると、[ターゲット フレームワーク モニカーによってビルド時間 API が定義されます](#target-framework-monikers-define-build-time-apis)。
- .NET アプリケーションを実行すると、[ターゲット フレームワークに依存するアプリがロールフォワードされます](#framework-dependent-apps-roll-forward)。
- 自己完結型アプリケーションを公開するとき、[自己完結型の展開には選択されたランタイムが含まれます](#self-contained-deployments-include-the-selected-runtime)。

このドキュメントの残りの部分では、これら 4 つのシナリオについて説明します。

## <a name="the-sdk-uses-the-latest-installed-version"></a>SDK はインストールされている最新バージョンを使用する

SDK コマンドには `dotnet new` または `dotnet run` が含まれています。 .NET CLI の場合、どの `dotnet` コマンドについても SDK バージョンを選択する必要があります。 以下のような場合でも、既定でマシンにインストールされている最新の SDK が使用されます。

- プロジェクトのターゲットが、以前のバージョンの .NET ランタイムである。
- .NET SDK の最新バージョンがプレビュー バージョンである。

以前のバージョンの .NET ランタイムをターゲットにしていても、SDK の最新の機能と機能改善を利用できます。 すべてのプロジェクトに同じ SDK ツールを使用し、異なるプロジェクトで .NET の複数のランタイム バージョンをターゲットにできます。

まれに、以前のバージョンの SDK を使用する必要がある場合があります。 そのバージョンは [*global.json* ファイル](../tools/global-json.md)で指定します。 "最新版を使用する" というポリシーは、インストールされている最新版より以前のバージョンの .NET SDK を指定するには *global.json* を使用することを意味します。

*global.json* はファイル階層のどこにでも配置できます。 CLI はプロジェクト ディレクトリから上方を検索し、最初の *global.json* を見つけます。 ファイル システム内のその場所によって、特定の *global.json* が適用されるプロジェクトを制御します。 .NET CLI は、現在の作業ディレクトリからパスを上方に移動し、*global.json* ファイルを繰り返し検索します。 見つかった最初の *global.json* ファイルによって、使用されるバージョンが指定されます。 その SDK バージョンがインストールされている場合、そのバージョンが使用されます。 *global.json* で指定された SDK が見つからない場合、.NET CLI では、[照合ルール](../tools/global-json.md#matching-rules)を使用して、互換性のある SDK を選択します。何も見つからない場合は失敗します。

次の例は *global.json* 構文を示しています。

``` json
{
  "sdk": {
    "version": "3.0.0"
  }
}
```

SDK バージョンを選択するためのプロセス:

1. `dotnet` は、現在の作業ディレクトリからパスを上方に逆移動し、*global.json* ファイルを繰り返し検索します。
1. `dotnet` は見つかった最初の *global.json* に指定されている SDK を使用します。
1. *global.json* が見つからない場合、`dotnet` はインストールされている最新の SDK を使用します。

SDK バージョンの選択に関する詳細は、*global.json* に関する記事の「[照合ルール](../tools/global-json.md#matching-rules)」にあります。

## <a name="target-framework-monikers-define-build-time-apis"></a>ターゲット フレームワーク モニカーによりビルド時間 API を定義する

**ターゲット フレームワーク モニカー** (TFM) に定義されている API に対してプロジェクトをビルドします。 [ターゲット フレームワーク](../../standard/frameworks.md)はプロジェクト ファイルで指定します。 次の例のように、プロジェクト ファイルに `TargetFramework` 要素を設定します。

``` xml
<TargetFramework>netcoreapp3.0</TargetFramework>
```

複数の TFM に対してプロジェクトをビルドできます。 複数のターゲット フレームワークを設定することはライブラリで一般的ですが、アプリケーションでも可能です。 `TargetFrameworks` プロパティ (`TargetFramework` の複数形) を指定します。 次の例のように、ターゲット フレームワークはセミコロンで区切られます。

``` xml
<TargetFrameworks>netcoreapp3.0;net47</TargetFrameworks>
```

特定の SDK でサポートされる一連のフレームワークは決まっており、同梱のランタイムのターゲット フレームワークが上限となります。 たとえば、.NET Core 3.1 SDK には .NET Core 3.1 ランタイムが含まれますが、これは `netcoreapp3.0` ターゲット フレームワークの実装です。 .NET Core 3.1 SDK では、`netcoreapp2.1`、`netcoreapp2.2`、`netcoreapp3.0` はサポートされますが、`net5.0` (以降) はサポートされません。 `net5.0` 用のビルドには、.NET 5.0 SDK をインストールします。

.NET Standard ターゲット フレームワークの上限も、SDK に付属するランタイムのターゲット フレームワークになります。 .NET 5.0 SDK の上限は `netstandard2.1` になります。 詳細については、「[.NET Standard](../../standard/net-standard.md)」をご覧ください。

## <a name="framework-dependent-apps-roll-forward"></a>フレームワーク依存のアプリをロールフォワードする

[`dotnet myapp.dll`](../tools/dotnet.md#description) が存在する [**フレームワークに依存するデプロイ**](../deploying/index.md#publish-framework-dependent)で [`dotnet run`](../tools/dotnet-run.md) を使用する、または `myapp.exe` が存在する [**フレームワークに依存する実行可能ファイル**](../deploying/index.md#publish-framework-dependent)を使用して、ソースからアプリケーションを実行した場合、`dotnet` 実行可能ファイルがアプリケーションの **ホスト** になります。

このホストがコンピューターにインストールされている最新版のパッチを選択します。 たとえば、プロジェクト ファイルに `netcoreapp3.0` を指定したとき、`3.0.2` がインストールされている最新の .NET ランタイムであれば、`3.0.2` ランタイムが使用されます。

許容される `3.0.*` バージョンが見つからない場合、新しい `3.*` バージョンが使用されます。 たとえば、`netcoreapp3.0` を指定したとき、`3.1.0` だけがインストールされている場合、アプリケーションは `3.1.0` ランタイムを利用して実行されます。 この動作は "マイナー バージョン ロールフォワード" と呼ばれます。 下位バージョンも考慮されません。 許容されるランタイムがインストールされていないとき、アプリケーションは実行されません。

以下にこの動作を示す使用例をいくつか示します (ターゲットが 3.0 の場合):

- ✔️ 3.0 が指定されています。 インストールされている最も高いパッチ バージョンは 3.0.3 です。 3.0.3 が使用されます。
- ❌ 3.0 が指定されています。 3\.0.* バージョンはインストールされていません。 2.1.1 がインストールされる最も高いランタイムです。 エラー メッセージが表示されます。
- ✔️ 3.0 が指定されています。 3\.0.* バージョンはインストールされていません。 インストールされている最も高いランタイム バージョンは 3.1.0 です。 3.1.0 が使用されます。
- ❌ 2.0 が指定されています。 2\.x バージョンはインストールされていません。 インストールされている最も高いランタイムは 3.0.0 です。 エラー メッセージが表示されます。

マイナー バージョン ロールフォワードには、エンド ユーザーに影響を与える可能性がある副作用が 1 つあります。 次のシナリオについて検討してください。

1. アプリケーションで 3.0 が必要であると指定されます。
2. 実行すると、バージョン 3.0.* はインストールされませんが、3.1.0 がインストールされます。 バージョン 3.1.0 が使用されます。
3. 後で、ユーザーが 3.0.3 をインストールし、もう一度アプリケーションを実行すると、3.0.3 が使用されるようになります。

バイナリ データをシリアル化するなどのシナリオでは特に、3.0.3 と 3.1.0 の動作が異なることがあります。

## <a name="self-contained-deployments-include-the-selected-runtime"></a>自己完結型の展開に選択したランタイムが含まれる

[**自己完結型ディストリビューション**](../deploying/index.md#publish-self-contained)としてアプリケーションを公開できます。 この手法を使用すると、.NET のランタイムとライブラリがアプリケーションと共にバンドルされます。 自己完結型の展開には、ランタイム環境に対する依存性がありません。 ランタイム バージョンは実行時ではなく、公開時に選択されます。

公開プロセスでは、特定のランタイム ファミリの最新版パッチが選択されます。 たとえば、`dotnet publish` では、.NET Core 3.0 ランタイム ファミリの最新版パッチが .NET Core 3.0.3 であればそれが選択されます。 ターゲット フレームワーク (インストールされているセキュリティ パッチを含む) がアプリケーションと共にパッケージ化されます。

アプリケーションに指定されている最小バージョンで十分ではない場合、エラーとなります。 `dotnet publish` は (特定の major.minor バージョン ファミリ内の) 最新ランタイム パッチ バージョンにバインドします。 `dotnet publish` は `dotnet run` のロールフォワード セマンティクスをサポートしません。 パッチや自己完結型の展開の詳細については、.NET アプリケーション展開の[ランタイム パッチ選択](../deploying/runtime-patch-selection.md)に関する記事を参照してください。

自己完結型の展開では、特定のパッチ バージョンが必要になることがあります。 次の例のように、プロジェクト ファイルで最小ランタイム パッチ バージョンを (上位または下位のバージョンに) オーバーライドできます。

``` xml
<RuntimeFrameworkVersion>3.0.3</RuntimeFrameworkVersion>
```

`RuntimeFrameworkVersion` 要素は既定のバージョン ポリシーをオーバーライドします。 自己完結型の展開の場合、`RuntimeFrameworkVersion` によって *厳密な* ランタイム フレームワーク バージョンが指定されます。 フレームワーク依存アプリケーションの場合、`RuntimeFrameworkVersion` によって *最小限* 必要なランタイム フレームワーク バージョンが指定されます。

## <a name="see-also"></a>関連項目

- [.NET をダウンロードしてインストールする](../install/index.yml)。
- [.NET ランタイムと SDK を削除する方法](../install/remove-runtime-sdk-versions.md)。
