---
description: '詳細について: ICorDebugSymbolProvider2:: Getフレーム Props メソッド'
title: ICorDebugSymbolProvider2::GetFrameProps メソッド
ms.date: 03/30/2017
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
ms.openlocfilehash: c0286e423f8f395568ad4df94fac38a7ef91c6bd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659557"
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a>ICorDebugSymbolProvider2::GetFrameProps メソッド

メソッドのメソッド開始位置を示す相対仮想アドレスと、指定されたコード相対仮想アドレスを持つ親フレームを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `codeRva`  
 [in] コード相対仮想アドレス。  
  
 `pCodeStartRva`  
 [out] メソッドの開始相対仮想アドレスへのポインター。  
  
 `pParentFrameStartRva`  
 [out] フレームの開始相対仮想アドレスへのポインター。  
  
## <a name="remarks"></a>解説  
  
> [!NOTE]
> このメソッドは .NET ネイティブでのみ使用できます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugSymbolProvider2 インターフェイス](icordebugsymbolprovider2-interface.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
