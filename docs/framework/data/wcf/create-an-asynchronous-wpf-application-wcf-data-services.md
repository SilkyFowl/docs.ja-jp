---
description: '詳細情報: 方法:非同期 Windows Presentation Framework アプリケーションを作成する (WCF Data Services)'
title: '方法: 非同期 Windows Presentation Framework アプリケーションを作成する (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, asynchronous operations
ms.assetid: 834614df-1427-4839-b0be-90f68e5afffd
ms.openlocfilehash: 8bc8045854ed0b73c06276e2c81e7e03a0ecc8d6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99766187"
---
# <a name="how-to-create-an-asynchronous-windows-presentation-framework-application-wcf-data-services"></a>方法: 非同期 Windows Presentation Framework アプリケーションを作成する (WCF Data Services)

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

WCF Data Services では、データ サービスから取得したデータを Windows Presentation Framework (WPF) アプリケーションの UI 要素にバインドできます。 詳細については、「[コントロールへのデータのバインド](binding-data-to-controls-wcf-data-services.md)」を参照してください。データ サービスに対して非同期で複数の操作を実行することもできます。この場合、アプリケーションは、データ サービス要求に対する応答を待機している間も引き続き応答できます。 データ サービスに非同期でアクセスするには、Silverlight 用のアプリケーションが必要です。 詳細については、「[非同期操作](asynchronous-operations-wcf-data-services.md)」をご覧ください。  
  
 このトピックでは、データ サービスに非同期でアクセスして、結果を WPF アプリケーションの要素にバインドする方法について説明します。 このトピックの例では、Northwind サンプル データ サービスおよび自動生成されたクライアント データ サービス クラスを使用します。 このサービスとクライアント データ クラスは、「[WCF Data Services クイックスタート](quickstart-wcf-data-services.md)」を完了すると作成されます。  
  
## <a name="example"></a>例  

 次の XAML は、WPF アプリケーションのウィンドウを定義します。  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingAsyncXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerordersasync.xaml#wpfdatabindingasyncxaml)]  
  
## <a name="example"></a>例  

 次の XAML ファイルの分離コード ページは、データ サービスを使用して非同期クエリを実行し、結果を WPF ウィンドウの要素にバインドします。  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBindingAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerordersasync.xaml.cs#wpfdatabindingasync)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerordersasync.xaml.vb#wpfdatabindingasync)]  
  
## <a name="see-also"></a>関連項目

- [WCF Data Services クライアント ライブラリ](wcf-data-services-client-library.md)
