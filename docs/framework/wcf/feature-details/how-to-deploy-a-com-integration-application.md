---
description: '詳細については、「方法: COM + 統合アプリケーションを展開する」を参照してください。'
title: '方法: COM+ 統合アプリケーションを展開する'
ms.date: 03/30/2017
ms.assetid: 2e5a0510-db3c-4988-a09c-696285836650
ms.openlocfilehash: 4bf9e72a631c97f3b791ecd01abb5cb74365772d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734387"
---
# <a name="how-to-deploy-a-com-integration-application"></a>方法: COM+ 統合アプリケーションを展開する

COM+ 統合アプリケーションを作成した後、これを別のコンピューターに展開する必要が生じる場合があります。 ここでは、COM+ 統合アプリケーションをコンピューター間で移動する方法を説明します。  
  
### <a name="moving-a-com-hosted-integration-app"></a>COM+ ホスト統合アプリケーションの移動  
  
1. 両方のコンピューターに WCF がインストールされていることを確認します。  
  
2. コンピューター A からアプリケーションをエクスポートします。  
  
3. コンピューター B にアプリケーションをインポートします。  
  
4. アプリケーション ルート ディレクトリを設定します。 通常これは %PROGRAMFILES%/ComPlus Applications/{AppGUID} になります。  
  
5. コンピューター A のアプリケーション ルート ディレクトリにある Application.config ファイルおよび Application.manifest ファイルを、コンピューター B のアプリケーション ルート ディレクトリにコピーします。  
  
6. コンピューター B の Application.config ファイルのサービス エンドポイント アドレスを編集して、コンピューター B が識別されるようにします。 たとえば、`http://machineA/MyService` を `http://machineB/MyService` に変更します。  
  
### <a name="moving-a-web-hosted-integration-application"></a>Web ホスト統合アプリケーションの移動  
  
1. 両方のコンピューターに WCF がインストールされていることを確認します。  
  
2. コンピューター A からアプリケーションをエクスポートします。  
  
3. コンピューター B にアプリケーションをインポートします。  
  
4. コンピューター B で IIS vroot を作成します。  
  
5. コンピューター A の vroot にある .svc ファイル (componentName.svc) と Web.config ファイルを、コンピューター B で新しく作成した vroot にコピーします。  
  
## <a name="see-also"></a>関連項目

- [COM + アプリケーションとの統合の概要](integrating-with-com-plus-applications-overview.md)
- [方法: COM+ サービス設定を構成する](how-to-configure-com-service-settings.md)
- [方法: COM+ サービス モデル構成ツールを使用する](how-to-use-the-com-service-model-configuration-tool.md)
