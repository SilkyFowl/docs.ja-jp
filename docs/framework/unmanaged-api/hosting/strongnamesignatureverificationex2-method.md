---
description: '詳細情報: StrongNameSignatureVerificationEx2 メソッド'
title: StrongNameSignatureVerificationEx2 メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName2.StrongNameSignatureVerificationEx2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StrongNameSignatureVerificationEx2
helpviewer_keywords:
- StrongNameSignatureVerificationEx2 method, ICLRStrongName2 interface [.NET Framework hosting]
- ICLRStrongName2::StrongNameSignatureVerificationEx2 method [.NET Framework hosting]
ms.assetid: dfd4133f-a074-4db3-a7ee-4f250fe9ad3a
topic_type:
- apiref
ms.openlocfilehash: d79491744ce1a930693d2901544ad80bf8049544
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679278"
---
# <a name="strongnamesignatureverificationex2-method"></a>StrongNameSignatureVerificationEx2 メソッド

厳密に名前が付けられたアセンブリの署名を検証し、ECMA キーから実際のキーへのマッピングを提供します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,    [in]  BYTE      *pbEcmaPublicKey,  
    [in]  DWORD     cbEcmaPublicKey,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `wszFilePath`  
 から検証するアセンブリの移植可能な実行可能ファイル (.exe または .dll) のパス。  
  
 `fForceVerification`  
 [入力] `true` レジストリ設定を上書きする必要がある場合でも、検証を実行するにはそれ以外の場合は `false` 。  
  
 `pbEcmaPublicKey`  
 からECMA 公開キーから、検証に使用される実際のキーへのマッピングへのポインター。  
  
 `cbEcmaPublicKey`  
 から実際の ECMA 公開キーの長さ。  
  
 `pfWasVerified`  
 [出力] `true` 厳密な名前の署名が検証された場合は。それ以外の場合は `false` 。 `false`レジストリ設定によって検証が成功した場合も、このパラメーターはに設定されます。  
  
## <a name="return-value"></a>戻り値  

 `S_OK` 検証が成功した場合は、それ以外の場合は、失敗を示す HRESULT 値 (「リストの [一般的な Hresult 値](/windows/win32/seccrypto/common-hresult-values) 」を参照してください)。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** メタホスト .h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [StrongNameSignatureVerification メソッド](iclrstrongname-strongnamesignatureverification-method.md)
- [StrongNameSignatureVerificationEx メソッド](iclrstrongname-strongnamesignatureverificationex-method.md)
- [ICLRStrongName インターフェイス](iclrstrongname-interface.md)
