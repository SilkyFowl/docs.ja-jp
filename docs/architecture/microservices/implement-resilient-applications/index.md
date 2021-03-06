---
title: 回復性があるアプリケーションを実装する
description: マイクロサービスのアーキテクチャで中核となる概念である、回復性について説明します。 一時的な障害が発生したときのために、それらを適切に処理する方法を知っておく必要があります。
ms.date: 01/30/2020
ms.openlocfilehash: 3ed4474eaa1225e80f05db86965e4ba53b5d2301
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100429326"
---
# <a name="implement-resilient-applications"></a>回復性があるアプリケーションを実装する

*マイクロサービスおよびクラウド ベースのアプリケーションは、最終的に確実に発生する部分的な障害を受け入れる必要があります。そのような部分的な障害に対する回復性があるようにアプリケーションを設計する必要があります。*

回復性は、障害から回復し、引き続き機能する能力です。 これは、障害を回避することではなく、障害が発生するという事実を受け入れ、ダウンタイムまたはデータの損失を回避するようにそれらに対応することです。 回復性の目的は、障害発生後にアプリケーションを完全に機能する状態に戻すことです。

マイクロサービスベースのアプリケーションの設計および展開は難しい作業です。 しかし、何らかの障害が確実に発生する環境で、アプリケーションの稼働を維持する必要もあります。 そのため、アプリケーションは、回復性を持っている必要があります。 ネットワークの停止、クラウド内のノードまたは VM のクラッシュなどの部分的な障害に対処するように設計する必要があります。 クラスタ内でマイクロサービス (コンテナー) を別のノードに移動するだけでも、アプリケーション内での断続的な短いエラーが発生する可能性があります。

アプリケーションの多くの個々のコンポーネントにも、正常性監視機能を組み込むも必要があります。 この章のガイドラインに従うと、複雑で、クラウド ベースの展開で発生する一時的なダウンタイムや定期的な障害があってもスムーズに動作するアプリケーションを作成できます。

>[!IMPORTANT]
> eShopOnContainer では、リリース 3.0.0 まで、[型指定されたクライアント](./use-httpclientfactory-to-implement-resilient-http-requests.md)を使用した回復性の実装に [Polly ライブラリ](https://thepollyproject.azurewebsites.net/)を使用していました。
>
> リリース 3.0.0 以降では、再試行をコード内で処理するのではなく、Kubernetes クラスター内で透過的で構成可能な方法で処理される [Linkerd のメッシュ](https://linkerd.io/)を使用した HTTP 呼び出しの回復性が実装されています。
>
> Polly ライブラリは、(特にサービスの起動時の) データベース接続に回復性を追加するためにまだ使用されています。

>[!WARNING]
> このセクションのすべてのコード サンプルは、Linkerd の使用前に有効であり、現在の実際のコードを反映するようには更新されていません。 つまり、このセクションのコンテキストで道理にかなうものです。

>[!div class="step-by-step"]
>[前へ](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
>[次へ](handle-partial-failure.md)
