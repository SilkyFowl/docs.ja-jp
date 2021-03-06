---
description: '詳細情報: 方法:16 進数文字列を数値に変換する (Visual Basic)'
title: '方法: 16 進文字列を数値に変換する'
ms.date: 01/31/2018
helpviewer_keywords:
- numbers [Visual Basic], hexadecimals
- hexadecimals [Visual Basic], decimals
- examples [Visual Basic], string conversion
- decimals [Visual Basic], hexadecimals
- string conversion [Visual Basic], hexadecimal to numbers
ms.assetid: 76675807-eadb-4c08-bd50-e6c6ff4b8ced
ms.openlocfilehash: cf1648b5f85f189f203f56cf569041e4f2db5ac3
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100425544"
---
# <a name="how-to-convert-hexadecimal-strings-to-numbers-visual-basic"></a>方法: 16 進数文字列を数値に変換する (Visual Basic)

この例では、<xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> メソッドを使用して、16 進数文字列を整数に変換します。

## <a name="to-convert-a-hexadecimal-string-to-a-number"></a>16 進数文字列を数値に変換するには

- <xref:System.Convert.ToInt32(System.String,System.Int32)> メソッドを使用して、base 16 で表された数値を整数に変換します。

  <xref:System.Convert.ToInt32(System.String,System.Int32)> メソッドの最初の引数は、変換する文字列です。 2 番目の引数は、数値をどの基数で表すかを示しています。16 進数は base 16 です。

  [!code-vb[VbVbalrStrings#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#62)]

- 16 進数文字列には次の制限があります。

  - `&h` プレフィックスを含めることはできません。
  - `_` 桁区切り記号を含めることはできません。

  このプレフィックスまたは桁区切り記号が存在する場合、<xref:System.Convert.ToInt32(System.String,System.Int32)> メソッドの呼び出しは <xref:System.FormatException> をスローします。

## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.Conversion.Hex%2A>
- <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>
