---
description: 詳細については、「ISymUnmanagedVariable インターフェイス」を参照してください。
title: ISymUnmanagedVariable インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable
helpviewer_keywords:
- ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: 704c69ba-77bc-40d7-8c0c-400061686321
topic_type:
- apiref
ms.openlocfilehash: 15b6c7018f92ad4c82abb9e5b4e52bf428b3f54b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762696"
---
# <a name="isymunmanagedvariable-interface"></a>ISymUnmanagedVariable インターフェイス

パラメーター、ローカル変数、またはフィールドなどの変数を表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetAddressField1 メソッド](isymunmanagedvariable-getaddressfield1-method.md)|この変数の最初のアドレスフィールドを取得します。 その意味は、アドレスの種類によって異なります。|  
|[GetAddressField2 メソッド](isymunmanagedvariable-getaddressfield2-method.md)|この変数の2番目のアドレスフィールドを取得します。 その意味は、アドレスの種類によって異なります。|  
|[GetAddressField3 メソッド](isymunmanagedvariable-getaddressfield3-method.md)|この変数の3番目のアドレスフィールドを取得します。 その意味は、アドレスの種類によって異なります。|  
|[GetAddressKind メソッド](isymunmanagedvariable-getaddresskind-method.md)|この変数のアドレスの種類を取得します。|  
|[GetAttributes メソッド](isymunmanagedvariable-getattributes-method.md)|この変数の属性フラグを取得します。|  
|[GetEndOffset メソッド](isymunmanagedvariable-getendoffset-method.md)|親内のこの変数の終了オフセットを取得します。|  
|[GetName メソッド](isymunmanagedvariable-getname-method.md)|この変数の名前を取得します。|  
|[GetSignature メソッド](isymunmanagedvariable-getsignature-method.md)|この変数のシグネチャを取得します。|  
|[GetStartOffSet メソッド](isymunmanagedvariable-getstartoffset-method.md)|親内のこの変数の開始オフセットを取得します。|  
  
## <a name="requirements"></a>要件  

 **ヘッダー:** CorSym .idl、CorSym .h  
  
## <a name="see-also"></a>関連項目

- [シンボル ストア診断インターフェイス](diagnostics-symbol-store-interfaces.md)
