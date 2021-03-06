---
title: '方法: ローカルのプロセス間通信で匿名パイプを使用する'
description: .Net でローカル コンピューターのプロセス間通信で匿名パイプを使用する方法について学習します。 匿名パイプに必要なオーバーヘッドは、名前付きパイプより少ないです。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- anonymous pipes [.NET]
- parent-child communication [.NET]
- pipes [.NET]
- one-way communication [.NET]
- local computer communication [.NET], pipes
ms.assetid: e7773c77-c646-4a01-8a96-a003d59fc4c9
ms.openlocfilehash: 389451d1c6c313ac4a10652c7aa614a5e4e7bf1c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734557"
---
# <a name="how-to-use-anonymous-pipes-for-local-interprocess-communication"></a>方法: ローカルのプロセス間通信で匿名パイプを使用する

匿名パイプは、ローカル コンピューターでのプロセス間通信を実現します。 名前付きパイプと比較して提供する機能は少なくなりますが、オーバーヘッドも小さくなります。 匿名パイプを使用して、ローカル コンピューター上で容易にプロセス間通信を実行できます。 匿名パイプを使用してネットワーク経由の通信を行うことはできません。  
  
 匿名パイプを実装するには、<xref:System.IO.Pipes.AnonymousPipeServerStream> クラスと <xref:System.IO.Pipes.AnonymousPipeClientStream> クラスを使用します。  
  
## <a name="example"></a>例  

 次に、匿名パイプを使用して、親プロセスから子プロセスに文字列を送信する方法の例を示します。 この例では、<xref:System.IO.Pipes.AnonymousPipeServerStream> の <xref:System.IO.Pipes.PipeDirection> 値を使用して、親プロセス内に <xref:System.IO.Pipes.PipeDirection.Out> オブジェクトを作成しています。 次に、親プロセスは、クライアント ハンドルを使用して子プロセスを作成し、<xref:System.IO.Pipes.AnonymousPipeClientStream> オブジェクトを作成します。 子プロセスには、<xref:System.IO.Pipes.PipeDirection> の <xref:System.IO.Pipes.PipeDirection.In> 値が指定されています。  
  
 次に、親プロセスはユーザー指定の文字列を子プロセスに送信します。 この文字列は、子プロセスのコンソールに表示されます。  
  
 サーバー プロセスの例を次に示します。  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/vb/program.vb#01)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]
  
## <a name="example"></a>例  

 クライアント プロセスの例を次に示します。 サーバー プロセスはクライアント プロセスを開始し、開始したプロセスをクライアント ハンドルに渡します。 クライアント コードから生成される実行可能ファイルの名前は `pipeClient.exe` とします。サーバー プロセスを実行する前に、このファイルをサーバーの実行可能ファイルと同じディレクトリにコピーします。  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/vb/program.vb#01)]  
  
## <a name="see-also"></a>関連項目

- [パイプ](pipe-operations.md)
- [方法: ネットワークのプロセス間通信で名前付きパイプを使用する](how-to-use-named-pipes-for-network-interprocess-communication.md)
