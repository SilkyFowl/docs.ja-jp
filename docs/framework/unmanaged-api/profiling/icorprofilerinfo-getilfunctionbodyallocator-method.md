---
description: '詳細について: ICorProfilerInfo:: GetILFunctionBodyAllocator メソッド'
title: ICorProfilerInfo::GetILFunctionBodyAllocator メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetILFunctionBodyAllocator
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetILFunctionBodyAllocator
helpviewer_keywords:
- GetILFunctionBodyAllocator method [.NET Framework profiling]
- ICorProfilerInfo::GetILFunctionBodyAllocator method [.NET Framework profiling]
ms.assetid: 5da1bf3d-dddf-4892-b266-578ee54d570b
topic_type:
- apiref
ms.openlocfilehash: 25d059d784fe64231d4d2ff3d23b4820443873cf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647428"
---
# <a name="icorprofilerinfogetilfunctionbodyallocator-method"></a>ICorProfilerInfo::GetILFunctionBodyAllocator メソッド

Microsoft 中間言語 (MSIL) コードでメソッドの本体を交換するために使用されるメモリを割り当てるメソッドを提供するインターフェイスを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetILFunctionBodyAllocator(  
    [in]  ModuleID      moduleId,  
    [out] IMethodMalloc **ppMalloc);  
```  
  
## <a name="parameters"></a>パラメーター  

 `moduleId`  
 からメソッドが存在するモジュールの ID。  
  
 `ppMalloc`  
 入出力メモリを割り当てるメソッドを提供する [Imethodmalloc](imethodmalloc-interface.md) インターフェイスへのポインター。  
  
## <a name="remarks"></a>解説  

 MSIL コードのメソッド本体は、読み込まれたモジュールに対して相対的な相対仮想アドレス (RVA) として配置されている必要があります。これは、モジュールが 4 GB 以内に続くことを意味します。 ツールがメソッドの本体を簡単に交換できるようにするために、メソッドは、 `GetILFunctionBodyAllocator` その範囲内でメモリが割り当てられるようにします。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo インターフェイス](icorprofilerinfo-interface.md)
