---
description: '詳細情報: 方法:Visual Basic でファイルのコピーを同じディレクトリに作成する'
title: '方法: ファイルのコピーを同じディレクトリに作成する'
ms.date: 07/20/2015
f1_keywords:
- File.Copy
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: b2fdda86-e666-42c2-9706-9527e9fa68ff
ms.openlocfilehash: 27fecc22a9317dd45e663aa37884c6c1f1e36349
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797615"
---
# <a name="how-to-create-a-copy-of-a-file-in-the-same-directory-in-visual-basic"></a>方法 : Visual Basic でファイルのコピーを同じディレクトリに作成する

ファイルをコピーするには、`My.Computer.FileSystem.CopyFile` メソッドを使用します。 このパラメーターでは、既存のファイルの上書き、ファイルの名前変更、操作の進行状況の表示、ユーザーによる操作のキャンセルが可能になります。  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder"></a>ファイルのコピーを同じフォルダーに作成するには  
  
- ターゲット ファイルと場所を指定し、`CopyFile` メソッドを使用します。 次の例では、`test2.txt` という `test.txt` のコピーを作成します。  
  
     [!code-vb[VbVbcnMyFileSystem#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#51)]  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder-overwriting-existing-files"></a>同じフォルダーにファイルのコピーを、既存のファイルを上書きして作成するには  
  
- ターゲット ファイルと場所を指定し、`overwrite` を `True` に設定して、`CopyFile` メソッドを使用します。 次の例では、`test2.txt` という `test.txt` のコピーを、既存のファイルをその名前で上書きして作成します。  
  
     [!code-vb[VbVbcnMyFileSystem#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#52)]  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  

 次の条件を満たす場合は、例外がスローされる可能性があります。  
  
- 次のいずれかの理由で、パスが正しくない。長さが 0 の文字列である、空白だけが含まれている、使用できない文字が含まれている、デバイス パスである (先頭が \\\\.\\) (<xref:System.ArgumentException>)。  
  
- システムが絶対パスを取得できなかった (<xref:System.ArgumentException>)。  
  
- パスが `Nothing` であるため、有効でない (<xref:System.ArgumentNullException>)  
  
- ソース ファイルが正しくない、または存在しない (<xref:System.IO.FileNotFoundException>)。  
  
- 結合したパスが、既存のディレクトリを指している (<xref:System.IO.IOException>)。  
  
- リンク先ファイルが存在し、`overwrite` が `False` に設定されている (<xref:System.IO.IOException>)。  
  
- ファイルにアクセスする十分なアクセス許可がユーザーにない (<xref:System.IO.IOException>)。  
  
- 同じ名前がターゲット フォルダー内のファイルで使用されている (<xref:System.IO.IOException>)。  
  
- パス内のファイル名またはフォルダー名にコロン (:) が含まれている、または形式が無効である (<xref:System.NotSupportedException>)。  
  
- `ShowUI` が `True` に設定され、`onUserCancel` が `ThrowException`に設定され、ユーザーが操作をキャンセルしている (<xref:System.OperationCanceledException>)。  
  
- `ShowUI` が `True` に設定され、`onUserCancel` が `ThrowException` に設定され、未指定の I/O エラーが発生する (<xref:System.OperationCanceledException>)。  
  
- パスがシステムで定義されている最大長を超えている (<xref:System.IO.PathTooLongException>)。  
  
- ユーザーに必要なアクセス許可がない (<xref:System.UnauthorizedAccessException>)。  
  
- ユーザーがパスを参照するのに必要なアクセス許可がない (<xref:System.Security.SecurityException>)  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- [方法: 特定のパターンを持つファイルをディレクトリにコピーする](how-to-copy-files-with-a-specific-pattern-to-a-directory.md)
- [方法: ファイルのコピーを別のディレクトリに作成する](how-to-create-a-copy-of-a-file-in-a-different-directory.md)
- [方法: ディレクトリを別のディレクトリにコピーする](how-to-copy-a-directory-to-another-directory.md)
- [方法: ファイルの名前を変更する](how-to-rename-a-file.md)
