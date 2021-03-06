---
description: '詳細情報: <namedPipeTransport>'
title: <namedPipeTransport>
ms.date: 03/30/2017
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
ms.openlocfilehash: 68714404492be92ce789dbde95a39199f5de16d4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99684101"
---
# \<namedPipeTransport>

チャネルがカスタム バインドに含まれているときに名前付きパイプを使用してメッセージを転送するトランスポートを定義します。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedPipeTransport>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<namedPipeTransport channelInitializationTimeout="TimeSpan"
                    connectionBufferSize="Integer"
                    hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"
                    manualAddressing="Boolean"
                    maxBufferPoolSize="Integer"
                    maxBufferSize="Integer"
                    maxOutputDelay="TimeSpan"
                    maxPendingAccepts="Integer"
                    maxPendingConnections="Integer"
                    maxReceivedMessageSize="Integer"
                    transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">
  <connectionPoolSettings groupName="String"
                          idleTimeout="TimeSpan"
                          maxOutboundConnectionsPerEndpoint="Integer" />
</namedPipeTransport>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  

以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  

なし。  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|ChannelInitializationTimeout|接続が切断されるまでのチャネルの初期化ステータスの最大時間を決定する <xref:System.TimeSpan> を取得または設定します。|  
|ConnectionBufferSize|クライアントまたサービスからネットワークでシリアル化されたメッセージのチャンクを転送するために使用されるバッファーのサイズを取得または設定します。|  
|hostNameComparisonMode|URI で一致する場合にサービスに到達するためにホスト名を使用するかどうかを示す値を取得または設定します。|  
|manualAddressing|メッセージの手動アドレス指定が必要かどうかを示す値を取得または設定します。|  
|maxBufferPoolSize|トランスポートが使用するバッファー プールの最大サイズ (バイト単位) を取得または設定します。|  
|maxBufferSize|使用するバッファーの最大サイズを取得または設定します。 ストリーム メッセージの場合、この値は少なくともメッセージ ヘッダーで使用できる最大サイズにする必要があります。これは、バッファー モードで読み取られます。|  
|maxOutputDelay|メッセージのチャンクまたは完全なメッセージを、送信前にメモリ内のバッファーに残したままにできる最長期間を取得または設定します。|  
|maxPendingAccepts|サービスへの受信接続を処理するためにサービスがリスナーで待機できるチャネルの最大数を取得または設定します。|  
|maxPendingConnections|サービスでディスパッチを待機している最大接続数を取得または設定します。|  
|maxReceivedMessageSize|受信できるメッセージの最大サイズをバイト単位で取得または設定します。|  
|transferMode|接続指向のトランスポートでメッセージをバッファーするか、ストリーム配信するかを示す値を取得または設定します。|  
|[\<namedPipeTransport> の \<connectionPoolSettings>](connectionpoolsettings.md)|名前付きパイプ バインディングの追加の接続プール設定を指定します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|カスタム バインドのすべてのバインド機能を定義します。|  
  
## <a name="remarks"></a>解説  

このトランスポートは、"net.pipe://hostname/path" の形式の URI を使用します。 他の URI コンポーネントは省略可能です。  
  
`namedPipeTransport` 要素は、名前付きパイプ トランスポート プロトコルを実装するカスタム バインディングを作成する場合の開始点となります。 このトランスポートは、コンピューター上での WCF (Windows Communication Foundation) 間の通信に使用されます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.NamedPipeTransportElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [トランスポート](../../../wcf/feature-details/transports.md)
- [トランスポートの選択](../../../wcf/feature-details/choosing-a-transport.md)
- [バインド](../../../wcf/bindings.md)
- [バインディングの拡張](../../../wcf/extending/extending-bindings.md)
- [カスタムバインド](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
