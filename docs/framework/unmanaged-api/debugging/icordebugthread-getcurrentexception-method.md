---
description: '詳細については、次のページを参照してください: いい Thread:: GetCurrentException メソッド'
title: ICorDebugThread::GetCurrentException メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetCurrentException
helpviewer_keywords:
- ICorDebugThread::GetCurrentException method [.NET Framework debugging]
- GetCurrentException method [.NET Framework debugging]
ms.assetid: 331ed465-a195-4359-8584-b82c6098b29b
topic_type:
- apiref
ms.openlocfilehash: cb241995520f26ca0e35f2b9e3b3187c2a2906a2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659167"
---
# <a name="icordebugthreadgetcurrentexception-method"></a>ICorDebugThread::GetCurrentException メソッド

現在マネージコードによってスローされている例外を表す、ICorDebugValue オブジェクトへのインターフェイスポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetCurrentException (  
    [out] ICorDebugValue **ppExceptionObject  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `ppExceptionObject`  
 入出力 `ICorDebugValue` 現在マネージコードによってスローされている例外を表すオブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>解説  

 例外オブジェクトは、ブロックの末尾まで例外がスローされた時点から存在し `catch` ます。 関数の評価は、テキストの評価メソッドによって実行され、セットアップ時に例外オブジェクトをクリアし、完了時に復元します。  
  
 例外は入れ子にすることができます (たとえば、フィルターまたは関数評価で例外がスローされた場合)。そのため、1つのスレッドで複数の未処理の例外が発生する可能性があります。 `GetCurrentException` 最新の例外を返します。  
  
 例外オブジェクトと型は、例外が発生したときに変更される可能性があります。 たとえば、型 x の例外がスローされた後、共通言語ランタイム (CLR) がメモリ不足になり、メモリ不足の例外に昇格することがあります。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
