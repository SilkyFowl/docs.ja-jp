---
description: '詳細情報: 承認されていないセキュリティ呼び出し'
title: 承認されていないセキュリティ呼び出し
ms.date: 03/30/2017
ms.assetid: cb6acdcd-7336-42e1-9ae8-ac891336cd58
ms.openlocfilehash: 80dc161f2be5a678e80860410f1b6adbde7bfb71
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803413"
---
# <a name="security-calls-not-authorized"></a>承認されていないセキュリティ呼び出し

カウンター名 : 承認されていないセキュリティ呼び出し。  
  
## <a name="description"></a>説明  

 このカウンターは <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> メソッドで `false` が返された場合にインクリメントされます。 受信メッセージが有効なユーザーから適切な保護を適用して送信されたものであり、その一方でそのユーザーが特定のタスクの実行を許可されていないことを示します。
