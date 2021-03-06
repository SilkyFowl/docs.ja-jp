---
description: '詳細情報: 序数が有効ではありません。'
title: 序数が有効ではありません。
ms.date: 07/20/2015
f1_keywords:
- vbrID452
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
ms.openlocfilehash: 7c58675a08d3821cd05ba0109e5ce0107c68e497
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795522"
---
# <a name="ordinal-is-not-valid"></a>序数が有効ではありません。

ダイナミック リンク ライブラリ (DLL) への呼び出しが、`#num` 構文を使用して、プロシージャ名の代わりに数値を使用するように指定されています。 このエラーには、次のような原因が考えられます。  
  
- `#num` 式を序数に変換しようとして失敗しました。  
  
- 指定された `#num` が、DLL 内の関数を指定していません。  
  
- タイプ ライブラリに無効な宣言が含まれているため、無効な序数が内部で使用されています。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. 式が有効な数値を表していること、または名前によってプロシージャを呼び出していることを確認します。  
  
2. `#num` が DLL 内の有効な関数を識別することを確認します。  
  
3. コードをコメント アウトすることで、問題の原因となっているプロシージャ呼び出しを分離します。 プロシージャの `Declare` ステートメントを記述し、その問題をタイプ ライブラリのベンダーに報告します。  
  
## <a name="see-also"></a>関連項目

- [Declare ステートメント](../statements/declare-statement.md)
