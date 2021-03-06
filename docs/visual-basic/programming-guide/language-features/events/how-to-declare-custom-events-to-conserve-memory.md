---
description: '詳細情報: 方法:カスタム イベントを宣言してメモリを節約する (Visual Basic)'
title: '方法: カスタム イベントを宣言してメモリを節約する'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
ms.openlocfilehash: 7371ec3df41ad0efd4598e0902f6937881d1e1a2
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100460086"
---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a>方法: カスタム イベントを宣言してメモリを節約する (Visual Basic)

場合によっては、アプリのメモリ使用量を抑えなければならないことがあります。 カスタム イベントを使用すると、アプリケーションが使用するメモリを、処理するイベントのものだけに制限できます。  
  
 既定では、クラスでイベントを宣言すると、メモリがそのイベント情報を格納するフィールドにコンパイラにより割り当てられます。 使用されないイベントがクラスに多数含まれている場合、これらによって不必要にメモリが占有されることになります。  
  
 Visual Basic に備わっている既定のイベント実装ではなく、カスタム イベントを使用することで、メモリ使用量を細かく管理できます。  
  
## <a name="example"></a>例  

 次の例のクラスでは、`Events` フィールドに格納される <xref:System.ComponentModel.EventHandlerList> のインスタンス 1 つを使用して、使用中のイベントに関する情報を格納しています。 <xref:System.ComponentModel.EventHandlerList> クラスは、デリゲートの保持向けに最適化された list クラスです。  
  
 このクラスのイベントはすべて、`Events` フィールドを使用して、各イベントを処理しているメソッドを追跡します。  
  
 [!code-vb[VbVbalrEvents#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#22)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.ComponentModel.EventHandlerList>
- [イベント](index.md)
- [方法: カスタム イベントを宣言してブロックを回避する](how-to-declare-custom-events-to-avoid-blocking.md)
