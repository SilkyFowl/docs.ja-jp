---
description: '詳細情報: 方法:スカラー値のユーザー定義関数を使用する'
title: '方法: スカラー値のユーザー定義関数を使用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 714e252f-c053-4bbb-b1f3-924111cd4d97
ms.openlocfilehash: e606dd3f840b8f082928217c6118b48d8d4a2e5c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785811"
---
# <a name="how-to-use-scalar-valued-user-defined-functions"></a>方法: スカラー値のユーザー定義関数を使用する

<xref:System.Data.Linq.Mapping.FunctionAttribute> 属性を使用することによって、クラスで定義されているクライアント メソッドを、ユーザー定義関数に対応付けることができます。 メソッドの本体は、メソッド呼び出しの目的を反映する式を構築し、変換および実行のためにその式を <xref:System.Data.Linq.DataContext> に渡します。  
  
> [!NOTE]
> 直接実行は、関数がクエリの外部で呼び出される場合のみ発生します。 詳細については、[ユーザー定義関数をインラインで呼び出す](how-to-call-user-defined-functions-inline.md)」を参照してください。  
  
## <a name="example"></a>例  

 次の SQL コードは、スカラー値のユーザー定義関数 `ReverseCustName()` を示しています。  
  
```sql  
CREATE FUNCTION ReverseCustName(@string varchar(100))  
RETURNS varchar(100)  
AS  
BEGIN  
    DECLARE @custName varchar(100)  
    -- Implementation left as exercise for users.  
    RETURN @custName  
END  
```  
  
 このコードで、次のようなクライアント メソッドを対応付けます。  
  
 [!code-csharp[DLinqUDFS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#3)]
 [!code-vb[DLinqUDFS#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#3)]  
  
## <a name="see-also"></a>関連項目

- [ユーザー定義関数](user-defined-functions.md)
