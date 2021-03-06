---
description: '詳細情報: -recurse'
title: -recurse
ms.date: 03/13/2018
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
ms.openlocfilehash: 2c0f1788c3811e24e2d51ff30e4cb2842aa0bd7a
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475878"
---
# <a name="-recurse"></a>-recurse

指定したディレクトリまたはプロジェクト ディレクトリのすべての子ディレクトリ内のソース コード ファイルをコンパイルします。  
  
## <a name="syntax"></a>構文  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a>引数  

 `dir`  
 任意。 検索を開始するディレクトリ。 指定しない場合は、プロジェクト ディレクトリから検索が開始されます。  
  
 `file`  
 必須です。 検索するファイル。 ワイルドカード文字を使用できます。  
  
## <a name="remarks"></a>Remarks  

 `-recurse` を使わなくても、ファイル名にワイルドカードを使用することで、プロジェクト ディレクトリ内の一致するすべてのファイルをコンパイルできます。 出力ファイル名が指定されていない場合、コンパイラで最初に処理される入力ファイルに基づいて、出力ファイル名が決定されます。 これは通常、コンパイルされるファイルの一覧をアルファベット順に表示したときの先頭のファイルです。 このため、出力ファイルは `-out` オプションを使用して指定することをお勧めします。  
  
> [!NOTE]
> `-recurse` オプションは、Visual Studio 開発環境からは利用できません。これはコマンド ラインからコンパイルするときにのみ使用できます。  
  
## <a name="example"></a>例  

 次のコマンドでは、現在のディレクトリにあるすべての Visual Basic ファイルをコンパイルします。  
  
```console
vbc *.vb  
```  
  
 次のコマンドでは、`Test\ABC` ディレクトリとそれより下にあるすべてのディレクトリ内のすべての Visual Basic ファイルをコンパイルし、`Test.ABC.dll` を生成します。  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](index.md)
- [-out (Visual Basic)](out.md)
- [コンパイル コマンド ラインのサンプル](sample-compilation-command-lines.md)
