---
description: '詳細情報: StrongNameSignatureGenerationEx 関数'
title: StrongNameSignatureGenerationEx 関数
ms.date: 03/30/2017
api_name:
- StrongNameSignatureGenerationEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureGenerationEx
helpviewer_keywords:
- StrongNameSignatureGenerationEx function [.NET Framework strong naming]
ms.assetid: 9a75469e-aa49-4e32-ad48-3bafd5202f09
topic_type:
- apiref
ms.openlocfilehash: e4d35cf51df6047d3a89d4146ceb8bf62e3f1b8b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798876"
---
# <a name="strongnamesignaturegenerationex-function"></a>StrongNameSignatureGenerationEx 関数

指定したフラグに従って、指定したアセンブリの厳密な名前の署名を生成します。  
  
 この関数は非推奨とされます。 代わりに [ICLRStrongName:: StrongNameSignatureGenerationEx](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md) メソッドを使用してください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
BOOLEAN StrongNameSignatureGenerationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob,  
    [in]  DWORD     dwFlags  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `wszFilePath`  
 から厳密な名前の署名が生成されるアセンブリのマニフェストを含むファイルへのパス。  
  
 `wszKeyContainer`  
 から公開キーと秘密キーのペアを格納するキーコンテナーの名前。  
  
 `pbKeyBlob`が null の場合、では、 `wszKeyContainer` 暗号化サービスプロバイダー (CSP) 内の有効なコンテナーを指定する必要があります。 この場合、コンテナーに格納されているキーペアがファイルの署名に使用されます。  
  
 `pbKeyBlob`が null でない場合、キーペアは、バイナリラージオブジェクト (BLOB) に格納されていると見なされます。  
  
 `pbKeyBlob`  
 から公開/秘密キーのペアへのポインター。 このペアは、Win32 関数によって作成される形式です `CryptExportKey` 。 `pbKeyBlob`が null の場合、によって指定されたキーコンテナーには、キーのペアが含まれていると `wszKeyContainer` 見なされます。  
  
 `cbKeyBlob`  
 からのサイズ (バイト単位) `pbKeyBlob` 。  
  
 `ppbSignatureBlob`  
 入出力共通言語ランタイムが署名を返す場所へのポインター。 `ppbSignatureBlob`が null の場合、ランタイムはによって指定されたファイルに署名を格納し `wszFilePath` ます。  
  
 `ppbSignatureBlob`が null でない場合は、共通言語ランタイムによって、署名を返す領域が割り当てられます。 呼び出し元は、 [StrongNameFreeBuffer](strongnamefreebuffer-function.md) 関数を使用してこの領域を解放する必要があります。  
  
 `pcbSignatureBlob`  
 入出力返されたシグネチャのサイズ (バイト単位)。  
  
 `dwFlags`  
 から次の値の1つまたは複数です。  
  
- `SN_SIGN_ALL_FILES` (0x00000001)-リンクされたモジュールのすべてのハッシュを再計算します。  
  
- `SN_TEST_SIGN` (0x00000002)-アセンブリに対してテストを行います。  
  
## <a name="return-value"></a>戻り値  

 `true` 正常に完了した場合は。それ以外の場合は `false` 。  
  
## <a name="remarks"></a>解説  

 `wszFilePath`署名を作成せずに署名のサイズを計算するには、に null を指定します。  
  
 署名は、ファイルに直接格納するか、呼び出し元に返すことができます。  
  
 が指定されていて `SN_SIGN_ALL_FILES` も、公開キーが含まれていない場合 ( `pbKeyBlob` との両方が null の場合 `wszFilePath` )、リンクされたモジュールのハッシュは再計算されますが、アセンブリは再署名されません。  
  
 が指定されている場合 `SN_TEST_SIGN` 、共通言語ランタイムヘッダーは、アセンブリが厳密な名前で署名されていることを示すために変更されません。  
  
 関数が `StrongNameSignatureGenerationEx` 正常に完了しない場合は、 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 関数を呼び出して、最後に生成されたエラーを取得します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** StrongName  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [StrongNameSignatureGenerationEx メソッド](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [StrongNameSignatureGeneration メソッド](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [ICLRStrongName インターフェイス](../hosting/iclrstrongname-interface.md)
