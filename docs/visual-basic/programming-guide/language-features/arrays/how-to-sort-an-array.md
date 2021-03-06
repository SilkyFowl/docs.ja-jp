---
description: '詳細情報: Visual Basic で配列を並べ替える'
title: '方法: 配列を並べ替える'
ms.date: 07/20/2015
f1_keywords:
- Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
ms.openlocfilehash: ea030b63dbbb5f5ea1d6160757afe2e9b58f7c21
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100462764"
---
# <a name="how-to-sort-an-array-in-visual-basic"></a>Visual Basic で配列を並べ替える

この記事では、Visual Basic で文字列の配列を並べ替える方法の例を示します。

## <a name="example"></a>例

この例では、`zooAnimals` という名前の `String` オブジェクトの配列を宣言し、値を設定して、アルファベット順に並べ替えます。
  
```vb
Private Sub SortAnimals()
    Dim zooAnimals(2) As String
    zooAnimals(0) = "lion"
    zooAnimals(1) = "turtle"
    zooAnimals(2) = "ostrich"
    Array.Sort(zooAnimals)
End Sub
```

## <a name="robust-programming"></a>信頼性の高いプログラミング

次の条件を満たす場合は、例外が発生する可能性があります。

- 配列が空である (<xref:System.ArgumentNullException> クラス)。
- 多次元配列である (<xref:System.RankException> クラス)。
- 配列の 1 つ以上の要素で <xref:System.IComparable> インターフェイス (<xref:System.InvalidOperationException> クラス) が実装されていない。

## <a name="see-also"></a>関連項目

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- [配列](index.md)
- [配列のトラブルシューティング](troubleshooting-arrays.md)
- [コレクション](../../concepts/collections.md)
- [For Each...Next ステートメント](../../../language-reference/statements/for-each-next-statement.md)
