---
description: '詳細について: ICorDebugProcess2:: ClearUnmanagedBreakpoint メソッド'
title: ICorDebugProcess2::ClearUnmanagedBreakpoint メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.ClearUnmanagedBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::ClearUnmanagedBreakpoint
helpviewer_keywords:
- ClearUnmanagedBreakpoint method [.NET Framework debugging]
- ICorDebugProcess2::ClearUnmanagedBreakpoint method [.NET Framework debugging]
ms.assetid: 12ed0fff-7f0e-4d7a-bb70-b3376371f36c
topic_type:
- apiref
ms.openlocfilehash: fba31a479e9bac525109e14c02995e78918d4c17
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746634"
---
# <a name="icordebugprocess2clearunmanagedbreakpoint-method"></a>ICorDebugProcess2::ClearUnmanagedBreakpoint メソッド

指定したアドレスに、以前に設定したブレークポイントを削除します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ClearUnmanagedBreakpoint (  
    [in] CORDB_ADDRESS   address  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `address`  
 から `CORDB_ADDRESS` ブレークポイントが設定されたアドレスを示す値です。  
  
## <a name="remarks"></a>解説  

 指定されたブレークポイントは、以前の [ICorDebugProcess2:: SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md)の呼び出しによって以前に設定されていた可能性があります。  
  
 メソッドは、 `ClearUnmanagedBreakpoint` デバッグ中のプロセスの実行中に呼び出すことができます。  
  
 `ClearUnmanagedBreakpoint`デバッガーがマネージ専用モードでアタッチされている場合、または指定されたアドレスにブレークポイントが存在しない場合、メソッドはエラーコードを返します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
