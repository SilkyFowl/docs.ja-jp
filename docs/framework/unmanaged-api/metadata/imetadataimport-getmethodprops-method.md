---
description: '詳細について: IMetaDataImport:: GetMethodProps メソッド'
title: IMetaDataImport::GetMethodProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMethodProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMethodProps
helpviewer_keywords:
- GetMethodProps method [.NET Framework metadata]
- IMetaDataImport::GetMethodProps method [.NET Framework metadata]
ms.assetid: e0667ef7-1d31-4c89-a2d3-d426f023f8d2
topic_type:
- apiref
ms.openlocfilehash: 5fb344d72378a806e0e71820b55a90998e497916
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783881"
---
# <a name="imetadataimportgetmethodprops-method"></a>IMetaDataImport::GetMethodProps メソッド

指定した MethodDef トークンによって参照されるメソッドに関連付けられているメタデータを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetMethodProps (  
    [in]  mdMethodDef         mb,  
    [out] mdTypeDef           *pClass,  
    [out] LPWSTR              szMethod,  
    [in]  ULONG               cchMethod,  
    [out] ULONG               *pchMethod,  
    [out] DWORD               *pdwAttr,  
    [out] PCCOR_SIGNATURE     *ppvSigBlob,  
    [out] ULONG               *pcbSigBlob,  
    [out] ULONG               *pulCodeRVA,  
    [out] DWORD               *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `mb`  
 からメタデータを返すメソッドを表す MethodDef トークン。  
  
 `pClass`  
 入出力メソッドを実装する型を表す TypeDef トークンへのポインター。  
  
 `szMethod`  
 入出力メソッドの名前を持つバッファーへのポインター。  
  
 `cchMethod`  
 から要求されたのサイズ `szMethod` 。  
  
 `pchMethod`  
 入出力のワイド文字のサイズへのポインター `szMethod` 。切り捨ての場合は、メソッド名の実際のワイド文字数。  
  
 `pdwAttr`  
 入出力メソッドに関連付けられているフラグへのポインター。  
  
 `ppvSigBlob`  
 入出力メソッドのバイナリメタデータシグネチャへのポインター。  
  
 `pcbSigBlob`  
 入出力のサイズ (バイト単位) へのポインター `ppvSigBlob` 。  
  
 `pulCodeRVA`  
 入出力メソッドの相対仮想アドレスへのポインター。  
  
 `pdwImplFlags`  
 入出力メソッドの実装フラグへのポインター。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Cor  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IMetaDataImport インターフェイス](imetadataimport-interface.md)
- [IMetaDataImport2 インターフェイス](imetadataimport2-interface.md)
