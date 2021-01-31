---
ms.openlocfilehash: cfe06de07950d287d59f3812a6b31e76d73775e1
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/27/2021
ms.locfileid: "98898757"
---
> [!IMPORTANT]
> <span data-ttu-id="095a0-101">WCF Data Services は非推奨になっており、Microsoft ダウンロード センターからダウンロードできなくなりました。</span><span class="sxs-lookup"><span data-stu-id="095a0-101">WCF Data Services has been deprecated and is no longer available for download on the Microsoft Download Centre.</span></span>
> <span data-ttu-id="095a0-102">WCF Data Services では以前のバージョンの Microsoft OData (V1-V3) プロトコルのみがサポートされていました。また、アクティブな開発の対象ではなくなっています。</span><span class="sxs-lookup"><span data-stu-id="095a0-102">WCF Data Services supported earlier versions of the Microsoft OData (V1-V3) protocol only and has not been under active development.</span></span> <span data-ttu-id="095a0-103">OData V1-V3 は OData V4 に置き換えられました。これは、OASIS によって公開され ISO によって承認された業界標準です。</span><span class="sxs-lookup"><span data-stu-id="095a0-103">OData V1-V3 has been superseded by OData V4, which is an industry standard published by OASIS and ratified by ISO.</span></span> <span data-ttu-id="095a0-104">OData V4 は、[Microsoft.OData.Core](https://www.nuget.org/packages/Microsoft.OData.Core/) で入手できる OData V4 準拠のコア ライブラリ全体でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="095a0-104">OData V4 is supported through the OData V4 compliant core libraries available at [Microsoft.OData.Core](https://www.nuget.org/packages/Microsoft.OData.Core/).</span></span> <span data-ttu-id="095a0-105">サポート ドキュメントは [OData.Net](https://odata.github.io/odata.net) で入手でき、OData V4 のサービス ライブラリは [Microsoft.AspNetCore.OData](https://www.nuget.org/packages/Microsoft.AspNetCore.OData) で入手できます。</span><span class="sxs-lookup"><span data-stu-id="095a0-105">Support documentation is available at [OData.Net](https://odata.github.io/odata.net), and the OData V4 service libraries are available at [Microsoft.AspNetCore.OData](https://www.nuget.org/packages/Microsoft.AspNetCore.OData).</span></span>
>
> <span data-ttu-id="095a0-106">[RESTier](https://github.com/OData/RESTier) は WCF Data Services の後継です。</span><span class="sxs-lookup"><span data-stu-id="095a0-106">[RESTier](https://github.com/OData/RESTier) is the successor to WCF Data Services.</span></span> <span data-ttu-id="095a0-107">RESTier は、標準化された、クエリ可能な、HTTP ベースの REST インターフェイスを数分でブートストラップするのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="095a0-107">RESTier helps you bootstrap a standardized, queryable, HTTP-based REST interface in minutes.</span></span>
> <span data-ttu-id="095a0-108">RESTier では、以前の WCF Data Services と同様に、シンプルでわかりやすい方法でクエリを整形し、データベースに到達する前と後に送信をインターセプトできます。</span><span class="sxs-lookup"><span data-stu-id="095a0-108">Like WCF Data Services before it, Restier provides simple and straightforward ways to shape queries and intercept submissions before and after they hit the database.</span></span> <span data-ttu-id="095a0-109">また、Web API + OData と同様に、既に使い慣れている手法を使用して独自のカスタム クエリとアクションを追加する柔軟性も備えています。</span><span class="sxs-lookup"><span data-stu-id="095a0-109">And like Web API + OData, you still have the flexibility to add your own custom queries and actions with techniques you're already familiar with.</span></span>