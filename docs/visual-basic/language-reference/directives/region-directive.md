---
description: '詳細情報: #Region ディレクティブ'
title: '#Region ディレクティブ'
ms.date: 07/20/2015
f1_keywords:
- vb.Region
- vb.#Region
helpviewer_keywords:
- Visual Basic compiler, compiler directives
- '#region directive'
- region directive (#region)
- '#Region keyword [Visual Basic]'
ms.assetid: 90a6a104-3cbf-47d0-bdc4-b585d0921b87
ms.openlocfilehash: 4ba1645cfc51a69d39e6a60b5ea236dd65883e1c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797225"
---
# <a name="region-directive"></a>#Region ディレクティブ

Visual Basic ファイルのコードのセクションを折りたたんで非表示にします。  
  
## <a name="syntax"></a>構文  

```vb
#Region "identifier_string"  
#End Region  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`identifier_string`|必須です。 領域が折りたたまれたときにその領域のタイトルとして機能する文字列です。 既定では、領域は折りたたまれています。|  
|`#End Region`|`#Region` ブロックを終了します。|  
  
## <a name="remarks"></a>Remarks  

 Visual Studio Code エディターのアウトライン機能を使うときに展開または折りたたみの対象となるコード ブロックを指定するには、`#Region` ディレクティブを使用します。 類似した領域をグループ化するために、他の領域内に領域を配置する ("*入れ子にする*") ことができます。  
  
## <a name="example"></a>例  

 `#Region` ディレクティブの使用例を次に示します。  
  
 [!code-vb[VbVbalrConditionalComp#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#4)]  
  
## <a name="see-also"></a>関連項目

- [#If...Then...#Else ディレクティブ](if-then-else-directives.md)
- [アウトライン](/visualstudio/ide/outlining)
- [方法: コードのセクションを折りたたんで非表示にする](../../programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)
