---
title: Azure と .NET を使用して作業を開始する
description: Azure と .NET について知っておくべき基本的事項について説明します。
ms.date: 03/15/2020
ms.openlocfilehash: 64defed4433647c2a0dcce91493d9ec77d21b541
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607883"
---
# <a name="introduction-to-azure-and-net"></a><span data-ttu-id="dc022-103">Azure と .NET の概要</span><span class="sxs-lookup"><span data-stu-id="dc022-103">Introduction to Azure and .NET</span></span>

<span data-ttu-id="dc022-104">このドキュメントでは、Azure サービスを使用してアプリの開発を開始するために、.NET 開発者が使い慣れている必要のある主要な概念とサービスの概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="dc022-104">This document provides an overview of key concepts and services .NET developers should be familiar with to get started developing apps using Azure services.</span></span>

## <a name="key-concepts"></a><span data-ttu-id="dc022-105">主要概念</span><span class="sxs-lookup"><span data-stu-id="dc022-105">Key Concepts</span></span>

<span data-ttu-id="dc022-106">**Azure アカウント**: Azure アカウントは、Azure サービス ([Azure portal](https://portal.azure.com) や [Cloud Shell](https://shell.azure.com) など) にサインインする際に使用する資格情報です。</span><span class="sxs-lookup"><span data-stu-id="dc022-106">**Azure account**: Your Azure account is the credential you use to sign into Azure services, such as the [Azure Portal](https://portal.azure.com) or [Cloud Shell](https://shell.azure.com).</span></span> <span data-ttu-id="dc022-107">Azure アカウントがない場合は、[アカウントを無料で作成](https://azure.microsoft.com/free/dotnet/)できます。</span><span class="sxs-lookup"><span data-stu-id="dc022-107">If you don't have an Azure account, you can [create one for free](https://azure.microsoft.com/free/dotnet/).</span></span>

<span data-ttu-id="dc022-108">**Azure サブスクリプション**: サブスクリプションとは、Azure リソースを作成する際の料金プランです。</span><span class="sxs-lookup"><span data-stu-id="dc022-108">**Azure subscription**: A subscription is the billing plan within which Azure resources are created.</span></span> <span data-ttu-id="dc022-109">サブスクリプションには、個人用サブスクリプションと会社が管理するエンタープライズ サブスクリプションがあります。</span><span class="sxs-lookup"><span data-stu-id="dc022-109">Subscriptions can be individual subscriptions or enterprise subscriptions managed by your company.</span></span> <span data-ttu-id="dc022-110">Azure アカウントは複数のサブスクリプションに関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="dc022-110">Your Azure account can be associated with multiple subscriptions.</span></span> <span data-ttu-id="dc022-111">この場合、リソースの作成時に適切なサブスクリプションを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc022-111">In this case, make sure you're selecting the correct subscription when creating resources.</span></span> <span data-ttu-id="dc022-112">詳細については、「[アカウント、サブスクリプション、課金の概要](https://docs.microsoft.com/azure/guides/developer/azure-developer-guide#understanding-accounts-subscriptions-and-billing)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="dc022-112">For more information, see [Understanding accounts, subscriptions and billing](https://docs.microsoft.com/azure/guides/developer/azure-developer-guide#understanding-accounts-subscriptions-and-billing).</span></span>

> [!TIP]
> <span data-ttu-id="dc022-113">Visual Studio サブスクリプションをお持ちの場合は、[月単位の Azure クレジットをアクティブにする](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/)ことができます。</span><span class="sxs-lookup"><span data-stu-id="dc022-113">If you have a Visual Studio subscription, [you have monthly Azure credits waiting to be activated](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/).</span></span>

<span data-ttu-id="dc022-114">**リソース グループ**: リソース グループを使用すると、管理のために Azure リソースをグループにまとめることができます。</span><span class="sxs-lookup"><span data-stu-id="dc022-114">**Resource group**: Resource groups are a way to organize your Azure resources into groups for management.</span></span> <span data-ttu-id="dc022-115">コンピューター上のフォルダーにファイルを保存するのと同様に、Azure で作成されたリソースは、リソース グループに保存されます。</span><span class="sxs-lookup"><span data-stu-id="dc022-115">Resources created in Azure will be stored in a resource group, similar to saving a file in a folder on a computer.</span></span>

<span data-ttu-id="dc022-116">**ホスティング**: Azure でコードを実行するには、ユーザー指定のコードの実行をサポートするサービスでホストされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc022-116">**Hosting**: To run code in Azure, it needs to be hosted in a service that supports executing user-provided code.</span></span>

<span data-ttu-id="dc022-117">**マネージド サービス**: Azure には、ユーザーがデータや情報を Azure に提供するためのサービスが用意されており、Azure の実装によって適切なアクションが実行されます。</span><span class="sxs-lookup"><span data-stu-id="dc022-117">**Managed services**: Azure provides some services where you provide data or information to Azure, and Azure's implementation takes the appropriate action.</span></span> <span data-ttu-id="dc022-118">一例として Azure Blob Storage があります。このサービスでは、ユーザーがファイルを提供すると、Azure によってそれらの読み取り、書き込み、永続化が処理されます。</span><span class="sxs-lookup"><span data-stu-id="dc022-118">One example is Azure Blob Storage, where you provide files and Azure handles reading, writing, and persisting them.</span></span>

## <a name="choosing-a-hosting-option"></a><span data-ttu-id="dc022-119">ホスティング オプションの選択</span><span class="sxs-lookup"><span data-stu-id="dc022-119">Choosing a hosting option</span></span>

<span data-ttu-id="dc022-120">Azure でのホスティングは、3 つのカテゴリに分けることができます。</span><span class="sxs-lookup"><span data-stu-id="dc022-120">Hosting in Azure can be divided into three categories.</span></span>

* <span data-ttu-id="dc022-121">**サービスとしてのインフラストラクチャ (IaaS)**: IaaS を使用して、関連付けられているネットワークおよびストレージ コンポーネントと共に、必要な仮想マシンをプロビジョニングします。</span><span class="sxs-lookup"><span data-stu-id="dc022-121">**Infrastructure-as-a-Service (IaaS)**: With IaaS, you provision the virtual machines you need along with associated network and storage components.</span></span> <span data-ttu-id="dc022-122">その後、必要なソフトウェアとアプリケーションをそれらの VM にデプロイします。</span><span class="sxs-lookup"><span data-stu-id="dc022-122">You then deploy whatever software and applications you want onto those VMs.</span></span> <span data-ttu-id="dc022-123">このモデルは従来のオンプレミス環境に最も近いものですが、Microsoft がインフラストラクチャを管理する点が異なります。</span><span class="sxs-lookup"><span data-stu-id="dc022-123">This model is the closest to a traditional on-premises environment except that Microsoft manages the infrastructure.</span></span> <span data-ttu-id="dc022-124">オペレーティング システム、カスタム ソフトウェア、セキュリティ更新プログラムなど、個々の VM は引き続きユーザーが管理します。</span><span class="sxs-lookup"><span data-stu-id="dc022-124">You still manage the individual VMs, including the operating system, custom software, and security updates.</span></span>

* <span data-ttu-id="dc022-125">**サービスとしてのプラットフォーム (PaaS)**: PaaS は、管理されたホスティング環境を提供します。この環境では、VM やネットワーク リソースを管理せずにアプリケーションをデプロイできます。</span><span class="sxs-lookup"><span data-stu-id="dc022-125">**Platform-as-a-Service (PaaS)**: PaaS provides a managed hosting environment where you deploy your application without needing to manage VMs or networking resources.</span></span> <span data-ttu-id="dc022-126">たとえば、個々の VM を作成するのではなく、インスタンス数を指定すると、サービスによって、必要なリソースがプロビジョニング、構成、および管理されます。</span><span class="sxs-lookup"><span data-stu-id="dc022-126">For example, instead of creating individual VMs, you specify an instance count, and the service will provision, configure, and manage the necessary resources.</span></span> <span data-ttu-id="dc022-127">Azure App Service は PaaS サービスの例です。</span><span class="sxs-lookup"><span data-stu-id="dc022-127">Azure App Service is an example of a PaaS service.</span></span>
  
* <span data-ttu-id="dc022-128">**サービスとしての関数 (FaaS)**: 一般に "サーバーレス コンピューティング" と呼ばれる FaaS は、PaaS よりもさらに先を行き、ホスティング環境に関する懸念を取り除きます。</span><span class="sxs-lookup"><span data-stu-id="dc022-128">**Functions-as-a-Service (FaaS)**: Commonly referred to as serverless computing, FaaS goes even further than PaaS in abstracting the concerns of the hosting environment.</span></span> <span data-ttu-id="dc022-129">コンピューティング インスタンスを作成し、それらのインスタンスにコードをデプロイするのではなく、コードをデプロイすると、サービスによってコードが自動的に実行されます。</span><span class="sxs-lookup"><span data-stu-id="dc022-129">Instead of creating compute instances and then deploying code to those instances, you deploy your code and the service automatically runs it.</span></span> <span data-ttu-id="dc022-130">コンピューティング リソースを管理する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="dc022-130">You don't need to administer the compute resources.</span></span> <span data-ttu-id="dc022-131">プラットフォームによって、トラフィックを処理するために必要なレベルに、コードがシームレスにスケールアップまたはスケールダウンされ、コードの実行時間にのみ課金されます。</span><span class="sxs-lookup"><span data-stu-id="dc022-131">The platform seamlessly scales your code up or down to whatever level necessary to handle the traffic, and you pay only when your code is running.</span></span> <span data-ttu-id="dc022-132">Azure Functions は FaaS サービスの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="dc022-132">Azure Functions is a FaaS service.</span></span>

<span data-ttu-id="dc022-133">一般に、アプリケーションで FaaS モデルや PaaS モデルが重視されるようになると、クラウドでの実行によって得られるメリットが増えます。</span><span class="sxs-lookup"><span data-stu-id="dc022-133">Generally, the more your application favors FaaS and PaaS models, the more benefits you'll see from running in the cloud.</span></span> <span data-ttu-id="dc022-134">Azure における 3 つの一般的なホスティングの選択肢とそれらを選ぶ状況の概要を次に示します。</span><span class="sxs-lookup"><span data-stu-id="dc022-134">Below is a summary of three common hosting choices in Azure and when to choose them.</span></span>

* <span data-ttu-id="dc022-135">[Azure App Service](https://docs.microsoft.com/azure/app-service/app-service-value-prop-what-is): Web アプリケーションまたはサービスをホストする場合は、まず App Service を検討します。</span><span class="sxs-lookup"><span data-stu-id="dc022-135">[Azure App Service](https://docs.microsoft.com/azure/app-service/app-service-value-prop-what-is): If you're looking to host a web application or service, look at App Service first.</span></span> <span data-ttu-id="dc022-136">App Service と ASP.NET、WCF、ASP.NET Core の各アプリを使った作業を開始する場合は、「[Azure に ASP.NET Core Web アプリを作成する](https://docs.microsoft.com/azure/app-service/app-service-web-get-started-dotnet)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="dc022-136">To get started with App Service and ASP.NET, WCF, and ASP.NET Core apps, see [Create an ASP.NET Core web app in Azure](https://docs.microsoft.com/azure/app-service/app-service-web-get-started-dotnet).</span></span>

* <span data-ttu-id="dc022-137">[Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview): Azure Functions はイベント ドリブン ワークフローに最適です。</span><span class="sxs-lookup"><span data-stu-id="dc022-137">[Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview): Azure Functions is great for event-driven workflows.</span></span> <span data-ttu-id="dc022-138">例として、Webhook への応答、キューまたは Blob Storage 内の項目の処理、タイマーなどがあります。</span><span class="sxs-lookup"><span data-stu-id="dc022-138">Examples include responding to webhooks, processing items in queues or blob storage, and timers.</span></span> <span data-ttu-id="dc022-139">Azure Functions を使った作業を開始する場合は、「[Visual Studio を使用して初めての関数を作成する](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="dc022-139">To get started with Azure Functions, see [Create your first function using Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).</span></span>

* <span data-ttu-id="dc022-140">[Azure Virtual Machines](https://docs.microsoft.com/azure/virtual-machines/): 特定の依存関係のため、App Service では既存のアプリケーションのホスティングのニーズが満たされない場合は、Virtual Machines が最も簡単な出発点となります。</span><span class="sxs-lookup"><span data-stu-id="dc022-140">[Azure Virtual Machines](https://docs.microsoft.com/azure/virtual-machines/): If App Service doesn't meet your needs for hosting an existing application due to specific dependencies, Virtual Machines will be the easiest place to start.</span></span> <span data-ttu-id="dc022-141">Virtual Machines と ASP.NET または WCF を使った作業を開始する場合は、「[Deploy an ASP.NET app to an Azure virtual machine (ASP.NET アプリを Azure 仮想マシンにデプロイする)](https://tutorials.visualstudio.com/aspnet-vm/intro)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="dc022-141">To get started with Virtual Machines and ASP.NET or WCF, see [Deploy an ASP.NET app to an Azure virtual machine](https://tutorials.visualstudio.com/aspnet-vm/intro).</span></span>

> [!TIP]
> <span data-ttu-id="dc022-142">サービスの選択の詳細については、「[アプリケーションの Azure コンピューティング サービスの選択」を](https://docs.microsoft.com/azure/architecture/guide/technology-choices/compute-decision-tree)参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc022-142">For more information on choosing a service, see [Choose an Azure compute service for your application](https://docs.microsoft.com/azure/architecture/guide/technology-choices/compute-decision-tree).</span></span>

## <a name="choose-a-data-storage-service"></a><span data-ttu-id="dc022-143">データ ストレージ サービスの選択</span><span class="sxs-lookup"><span data-stu-id="dc022-143">Choose a data storage service</span></span>

<span data-ttu-id="dc022-144">Azure には、ニーズに応じてデータを格納するための複数のサービスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="dc022-144">Azure offers several services for storing your data depending on your needs.</span></span> <span data-ttu-id="dc022-145">.NET 開発者向けの最も一般的なデータ サービスを次に示します。</span><span class="sxs-lookup"><span data-stu-id="dc022-145">The most common data services for .NET developers are:</span></span>

* <span data-ttu-id="dc022-146">[Azure SQL Database](https://docs.microsoft.com/azure/sql-database/): SQL Server を既に使用しているアプリケーションをクラウドに移行する場合は、Azure SQL Database が自然な出発点です。</span><span class="sxs-lookup"><span data-stu-id="dc022-146">[Azure SQL Database](https://docs.microsoft.com/azure/sql-database/): If you're looking to migrate an application that is already using SQL Server to the cloud, Azure SQL Database is a natural place to start.</span></span> <span data-ttu-id="dc022-147">作業を開始するには、「[チュートリアル: SQL Database を使用して Azure に ASP.NET アプリを作成する](https://docs.microsoft.com/azure/app-service/app-service-web-tutorial-dotnet-sqldatabase)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="dc022-147">To get started, see [Tutorial: Build an ASP.NET app in Azure with SQL Database](https://docs.microsoft.com/azure/app-service/app-service-web-tutorial-dotnet-sqldatabase).</span></span>

* <span data-ttu-id="dc022-148">[Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/): Azure Cosmos DB は、クラウド向けに設計された最新のデータベースです。</span><span class="sxs-lookup"><span data-stu-id="dc022-148">[Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/): Azure Cosmos DB is a modern database designed for the cloud.</span></span> <span data-ttu-id="dc022-149">特定のデータベース依存関係がまだない新しいアプリケーションを開始する場合は、Azure Cosmos DB を検討してください。</span><span class="sxs-lookup"><span data-stu-id="dc022-149">When starting a new application that doesn't yet have a specific database dependency, you should look at Azure Cosmos DB.</span></span> <span data-ttu-id="dc022-150">Cosmos DB は、自動スケール、予測可能なパフォーマンス、高速応答時間、スキーマレスなデータのクエリを実行できることが重要である、新しい Web、モバイル、ゲーム、IoT の各アプリケーションに適しています。</span><span class="sxs-lookup"><span data-stu-id="dc022-150">Cosmos DB is a good choice for new web, mobile, gaming, and IoT applications where automatic scale, predictable performance, fast response times, and the ability to query schema-free data are important.</span></span> <span data-ttu-id="dc022-151">作業を開始するには、「[クイック スタート: SQL API と Azure Portal を使って Azure Cosmos DB による .NET Web アプリを作る](https://docs.microsoft.com/azure/cosmos-db/create-sql-api-dotnet)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="dc022-151">To get started, see [Quickstart: Build a .NET web app with Azure Cosmos DB using the SQL API and the Azure portal](https://docs.microsoft.com/azure/cosmos-db/create-sql-api-dotnet).</span></span>

* <span data-ttu-id="dc022-152">[Azure Blob Storage](https://docs.microsoft.com/azure/storage/): Azure Blob Storage は、画像、ファイル、ストリームなどの大きなバイナリ オブジェクトの格納と取得に最適化されています。</span><span class="sxs-lookup"><span data-stu-id="dc022-152">[Azure Blob Storage](https://docs.microsoft.com/azure/storage/): Azure Blob Storage is optimized for storing and retrieving large binary objects, such as images, files, and streams.</span></span> <span data-ttu-id="dc022-153">オブジェクト ストアにより、大量の非構造化データの管理が可能になります。</span><span class="sxs-lookup"><span data-stu-id="dc022-153">Object stores enable the management of extremely large amounts of unstructured data.</span></span> <span data-ttu-id="dc022-154">作業を開始するには、「[Quickstart: Use .NET to create a blob in object storage (クイック スタート: .NET を使用してオブジェクト ストレージに BLOB を作成する)](https://docs.microsoft.com/azure/storage/blobs/storage-quickstart-blobs-dotnet)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="dc022-154">To get started, see [Quickstart: Use .NET to create a blob in object storage](https://docs.microsoft.com/azure/storage/blobs/storage-quickstart-blobs-dotnet).</span></span>

> [!TIP]
> <span data-ttu-id="dc022-155">詳細については、「[適切なデータ ストアの選択](https://docs.microsoft.com/azure/architecture/guide/technology-choices/data-store-overview)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="dc022-155">For more information, see [Choose the right data store](https://docs.microsoft.com/azure/architecture/guide/technology-choices/data-store-overview).</span></span>

## <a name="connect-to-azure-services"></a><span data-ttu-id="dc022-156">Azure サービスに接続する</span><span class="sxs-lookup"><span data-stu-id="dc022-156">Connect to Azure services</span></span>

<span data-ttu-id="dc022-157">Visual Studio を使用する場合は、特定の Azure サービスのサポートをプロジェクトに追加できます。</span><span class="sxs-lookup"><span data-stu-id="dc022-157">If you use Visual Studio, you can add support for certain Azure services to your projects.</span></span> <span data-ttu-id="dc022-158">Visual Studio の **[接続済みサービス]** ダイアログを使用すると、必要な参照、接続コード、および構成設定をプロジェクトに簡単に追加できます。</span><span class="sxs-lookup"><span data-stu-id="dc022-158">The **Connected Services** dialog in Visual Studio provides an easy way to add all the required references, connection code, and configuration settings to your projects.</span></span> <span data-ttu-id="dc022-159">よく使用される一部の Azure サービス ([Storage](/azure/vs-azure-tools-connected-services-storage)、[Azure Active Directory](/azure/active-directory/develop/vs-active-directory-add-connected-service) 認証、[Azure Key Vault](/azure/key-vault/vs-key-vault-add-connected-service)、([Computer Vision](/azure/cognitive-services/computer-vision/vs-computer-vision-connected-service) を含む) [Cognitive Services](/azure/cognitive-services/) など) は、すぐ使えるようにサポートされています。</span><span class="sxs-lookup"><span data-stu-id="dc022-159">Some commonly used Azure services are supported out of the box, such as [Storage](/azure/vs-azure-tools-connected-services-storage), [Azure Active Directory](/azure/active-directory/develop/vs-active-directory-add-connected-service) authentication, [Azure Key Vault](/azure/key-vault/vs-key-vault-add-connected-service), and [Cognitive Services](/azure/cognitive-services/) such as [Computer Vision](/azure/cognitive-services/computer-vision/vs-computer-vision-connected-service).</span></span> <span data-ttu-id="dc022-160">サード パーティのサービスを含むその他のサービスは、拡張機能として [Visual Studio Marketplace](https://marketplace.visualstudio.com/search?term=connected%20service&target=VS&category=Tools&vsVersion=&subCategory=All&sortBy=Relevance) で入手できます。</span><span class="sxs-lookup"><span data-stu-id="dc022-160">More services, including third-party services, are available as extensions in the [Visual Studio Marketplace](https://marketplace.visualstudio.com/search?term=connected%20service&target=VS&category=Tools&vsVersion=&subCategory=All&sortBy=Relevance).</span></span>

## <a name="diagnosing-problems-in-the-cloud"></a><span data-ttu-id="dc022-161">クラウドでの問題の診断</span><span class="sxs-lookup"><span data-stu-id="dc022-161">Diagnosing problems in the Cloud</span></span>
<span data-ttu-id="dc022-162">アプリケーションを Azure にデプロイした後、開発環境では動作していても、Azure では動作しない状況に遭遇することがあります。</span><span class="sxs-lookup"><span data-stu-id="dc022-162">Once you deploy your application to Azure, you may run into cases where it worked in development but doesn't in Azure.</span></span> <span data-ttu-id="dc022-163">問題を診断するときは、まず次の 2 つを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="dc022-163">Below are two good places to start when diagnosing issues:</span></span>

* <span data-ttu-id="dc022-164">**Visual Studio からのリモート デバッグ**: (このドキュメントで説明するサービスを含め) ほとんどの Azure コンピューティング サービスでは、Visual Studio を使用したリモート デバッグとログの取得がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="dc022-164">**Remote debug from Visual Studio**: Most Azure compute services (including the services discussed in this document) support remote debugging with Visual Studio and acquiring logs.</span></span> <span data-ttu-id="dc022-165">アプリケーションで Visual Studio の機能を調べるには、Visual Studio のクイック起動ツール バー (右上隅) に「Cloud Explorer」と入力して、Cloud Explorer ツール ウィンドウを開き、ツリーで目的のアプリケーションを見つけます。</span><span class="sxs-lookup"><span data-stu-id="dc022-165">To explore Visual Studio's capabilities with your application, open the Cloud Explorer tool window by typing 'Cloud Explorer' into Visual Studio's quick launch toolbar (in the upper-right corner), and then locate your application in the tree.</span></span> <span data-ttu-id="dc022-166">詳細については、[Visual Studio を使用した Azure App Service の Web アプリのトラブルシューティング](https://docs.microsoft.com/azure/app-service/web-sites-dotnet-troubleshoot-visual-studio#remotedebug)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="dc022-166">For details, see [Troubleshoot a web app in Azure App Service using Visual Studio](https://docs.microsoft.com/azure/app-service/web-sites-dotnet-troubleshoot-visual-studio#remotedebug).</span></span>

* <span data-ttu-id="dc022-167">**Application Insights**: [Application Insights](https://docs.microsoft.com/azure/application-insights/) は、診断データ、テレメトリ、パフォーマンス データをアプリケーションから自動的に取り込む、完全なアプリケーション パフォーマンス監視 (APM) ソリューションです。</span><span class="sxs-lookup"><span data-stu-id="dc022-167">**Application Insights**: [Application Insights](https://docs.microsoft.com/azure/application-insights/) is a complete application performance monitoring (APM) solution that captures diagnostic data, telemetry, and performance data from applications automatically.</span></span> <span data-ttu-id="dc022-168">アプリの診断データの収集を開始するには、「[ASP.NET Web アプリケーションの監視を開始する](https://docs.microsoft.com/azure/application-insights/quick-monitor-portal)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="dc022-168">To get started collecting diagnostic data for your app, see [Start monitoring your ASP.NET Web Application](https://docs.microsoft.com/azure/application-insights/quick-monitor-portal).</span></span>

## <a name="next-steps"></a><span data-ttu-id="dc022-169">次の手順</span><span class="sxs-lookup"><span data-stu-id="dc022-169">Next steps</span></span>

* [<span data-ttu-id="dc022-170">Azure に最初の ASP.NET Core Web アプリをデプロイする</span><span class="sxs-lookup"><span data-stu-id="dc022-170">Deploy your first ASP.NET Core web app to Azure</span></span>](https://docs.microsoft.com/azure/app-service/app-service-web-get-started-dotnet)
* [<span data-ttu-id="dc022-171">NET 用 Azure SDK での認証について</span><span class="sxs-lookup"><span data-stu-id="dc022-171">Learn about authentication in Azure SDK for .NET</span></span>](./sdk/authentication.md)
* [<span data-ttu-id="dc022-172">クラウド アプリのエラーを診断する</span><span class="sxs-lookup"><span data-stu-id="dc022-172">Diagnose errors in your cloud apps</span></span>](https://blogs.msdn.microsoft.com/webdev/2018/02/07/diagnosing-errors-on-your-cloud-apps)
* <span data-ttu-id="dc022-173">[.NET 開発者向けの Azure クイック スタート ガイド](https://www.microsoft.com/net/download/thank-you/azure-quick-start-ebook) (無料の電子書籍) をダウンロードする</span><span class="sxs-lookup"><span data-stu-id="dc022-173">Download the free e-book [Azure Quick Start Guide for .NET Developers](https://www.microsoft.com/net/download/thank-you/azure-quick-start-ebook)</span></span>