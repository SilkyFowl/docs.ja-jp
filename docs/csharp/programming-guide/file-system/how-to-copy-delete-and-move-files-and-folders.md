---
title: ファイルおよびフォルダーをコピー、削除、および移動する方法 - C# プログラミング ガイド
description: File、Directory、FileInfo、および DirectoryInfo クラスを使用して、ファイルとフォルダーをコピー、削除、および移動する方法について説明します。
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
ms.openlocfilehash: 24595c9f5c75b70afb0ff079b6b93e35502f7fb5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202514"
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a>ファイルおよびフォルダーをコピー、削除、および移動する方法 (C# プログラミング ガイド)

次の例では、<xref:System.IO?displayProperty=nameWithType> 名前空間から <xref:System.IO.File?displayProperty=nameWithType>、<xref:System.IO.Directory?displayProperty=nameWithType>、<xref:System.IO.FileInfo?displayProperty=nameWithType>、および <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> クラスを使用して、同期的な方法でファイルとフォルダーをコピー、移動および削除する方法を示します。 これらの例では、進行状況バーやその他のユーザー インターフェイスは表示されません。 標準の進行状況ダイアログ ボックスを表示する場合は、「[ファイル操作の [進行状況] ダイアログ ボックスを表示する方法](how-to-provide-a-progress-dialog-box-for-file-operations.md)」を参照してください。  
  
 複数のファイルを操作するときに進行状況を計算できるイベントを提供するには、<xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> を使用します。 プラットフォーム呼び出しを使用して、Windows シェルで関連するファイル関連メソッドを呼び出す方法もあります。 これらのファイル操作を非同期に実行する方法については、「[非同期ファイル I/O](../../../standard/io/asynchronous-file-i-o.md)」を参照してください。  
  
## <a name="example"></a>例  

 次の例では、ファイルとディレクトリをコピーする方法を示します。  
  
 [!code-csharp[csFilesandFolders#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#7)]  
  
## <a name="example"></a>例  

 次の例では、ファイルとディレクトリを移動する方法を示します。  
  
 [!code-csharp[csFilesandFolders#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#8)]  
  
## <a name="example"></a>例  

 次の例では、ファイルとディレクトリを削除する方法を示します。  
  
 [!code-csharp[csFilesandFolders#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#9)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.IO?displayProperty=nameWithType>
- [C# プログラミング ガイド](../index.md)
- [ファイル システムとレジストリ (C# プログラミング ガイド)](index.md)
- [ファイル操作の [進行状況] ダイアログ ボックスを表示する方法](how-to-provide-a-progress-dialog-box-for-file-operations.md)
- [ファイルおよびストリーム入出力](../../../standard/io/index.md)
- [共通 I/O タスク](../../../standard/io/common-i-o-tasks.md)
