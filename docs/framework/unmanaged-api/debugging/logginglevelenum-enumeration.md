---
description: 詳細については、「ログイン Levelenum 列挙型」を参照してください。
title: LoggingLevelEnum 列挙型
ms.date: 03/30/2017
api_name:
- LoggingLevelEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- LoggingLevelEnum
helpviewer_keywords:
- LoggingLevelEnum enumeration [.NET Framework debugging]
ms.assetid: 09daac08-005a-46b2-beab-408d0820c5e5
topic_type:
- apiref
ms.openlocfilehash: 7c9676fef83ea44f45a25350a2b3d325c1c22f98
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800613"
---
# <a name="logginglevelenum-enumeration"></a>LoggingLevelEnum 列挙型

マネージド スレッドがイベントを記録する際にイベント ログに書き込まれる説明メッセージの重大度レベルを示します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum LoggingLevelEnum {  
    LTraceLevel0 = 0,  
    LTraceLevel1,  
    LTraceLevel2,  
    LTraceLevel3,  
    LTraceLevel4,  
    LStatusLevel0 = 20,  
    LStatusLevel1,  
    LStatusLevel2,  
    LStatusLevel3,  
    LStatusLevel4,  
    LWarningLevel = 40,  
    LErrorLevel = 50,  
    LPanicLevel = 100  
} LoggingLevelEnum;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`LTraceLevel0`|メッセージはトレースレベル0です。|  
|`LTraceLevel1`|メッセージはトレースレベル1です。|  
|`LTraceLevel2`|メッセージはトレースレベル2です。|  
|`LTraceLevel3`|メッセージはトレースレベル3です。|  
|`LTraceLevel4`|メッセージはトレースレベル4です。|  
|`LStatusLevel0`|メッセージはステータスレベル0です。|  
|`LStatusLevel1`|メッセージはステータスレベル1です。|  
|`LStatusLevel2`|メッセージはステータスレベル2です。|  
|`LStatusLevel3`|メッセージはステータスレベル3です。|  
|`LStatusLevel4`|メッセージはステータスレベル4です。|  
|`LWarningLevel`|メッセージは警告レベルです。|  
|`LErrorLevel`|メッセージはエラーレベルです。|  
|`LPanicLevel`|メッセージはパニックレベルです。|  
  
## <a name="remarks"></a>解説  

 共通言語ランタイム (CLR: common language runtime) は、コンポーネントのマネージ [コールバック:: LogMessage](icordebugmanagedcallback-logmessage-method.md) メソッドを呼び出して、マネージスレッドがイベントを記録したことをデバッガーに通知します。 CLR は、マネージスレッドによって `LoggingLevelEnum` イベントログに書き込まれたメッセージの重大度レベルを示すために、列挙体の値を渡します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Diagnostics.EventLog>
- [列挙体のデバッグ](debugging-enumerations.md)
