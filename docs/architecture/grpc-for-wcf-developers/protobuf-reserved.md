---
title: Protobuf の予約済みフィールド-WCF 開発者向け gRPC
description: バージョン間の互換性のために予約されているフィールドについて説明します。
ms.date: 12/15/2020
ms.openlocfilehash: d82043d619c5b3b81091ae4ea381e4778c1cf6ba
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938521"
---
# <a name="protobuf-reserved-fields"></a>Protobuf 予約フィールド

プロトコルバッファー (Protobuf) での下位互換性の保証は、常に同じデータ項目を表すフィールド番号に依存します。 新しいバージョンのサービスでメッセージからフィールドが削除された場合、そのフィールド番号は再利用しないでください。 キーワードを使用して、この動作を強制でき `reserved` ます。

前に `displayName` 定義したメッセージからフィールドとフィールドを削除した場合は `marketId` `Stock` 、次の例のようにフィールド番号を予約する必要があります。

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

キーワードは、 `reserved` 今後追加される可能性のあるフィールドのプレースホルダーとして使用することもできます。 キーワードを使用して、連続するフィールド番号を範囲として表すことができ `to` ます。

```protobuf
syntax "proto3";

message Info {

    reserved 2, 9 to 11, 15;
    // ...
}
```

>[!div class="step-by-step"]
>[前へ](protobuf-repeated.md)
>[次へ](protobuf-any-oneof.md)
