---
description: '詳細については、次を参照してください: EContextType 列挙型'
title: EContextType 列挙型
ms.date: 03/30/2017
api_name:
- EContextType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EContextType
helpviewer_keywords:
- EContextType enumeration [.NET Framework hosting]
ms.assetid: 92b926a9-b87e-408a-9036-df7b752c9492
topic_type:
- apiref
ms.openlocfilehash: b7d6ddb385386bb0616a01ef6fcc432f2c925d51
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785533"
---
# <a name="econtexttype-enumeration"></a>EContextType 列挙型

現在実行中のスレッドのセキュリティコンテキストを記述します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum {  
    eCurrentContext    = 0x00,  
    eRestrictedContext = 0x01  
} EContextType;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`eCurrentContext`|共通言語ランタイム (CLR) が [IHostSecurityManager:: GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md) メソッドを呼び出す時点での現在のスレッドのコンテキスト、または [IHostSecurityManager:: SetSecurityContext](ihostsecuritymanager-setsecuritycontext-method.md) メソッドの呼び出しで CLR によって要求されたコンテキストを示します。|  
|`eRestrictedContext`|ホストが低い特権 (ガベージコレクター、クラスまたはモジュールコンストラクターなど) を持つコンテキストを示します。|  
  
## <a name="remarks"></a>解説  

 CLR は、 `EContextType` メソッドとメソッドの呼び出しで、値の1つをパラメーター値として提供し `IHostSecurityManager::GetSecurityContext` `IHostSecurityManager::SetSecurityContext` ます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IHostSecurityContext インターフェイス](ihostsecuritycontext-interface.md)
- [IHostSecurityManager インターフェイス](ihostsecuritymanager-interface.md)
- [ホスティングの列挙型](hosting-enumerations.md)
