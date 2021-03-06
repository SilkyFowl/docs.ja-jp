---
description: '詳細情報: 方法: 時間ベースのキャッシュ ポリシーをカスタマイズする'
title: '方法: 時間ベースのキャッシュ ポリシーをカスタマイズする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time-based cache policies
- customizing time-based cache policies
- cache [.NET Framework], time-based policies
ms.assetid: 8d84f936-2376-4356-9264-03162e0f9279
ms.openlocfilehash: bb00faa5c2cd3170a0f56b74032867d489c1fb8a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747453"
---
# <a name="how-to-customize-a-time-based-cache-policy"></a>方法: 時間ベースのキャッシュ ポリシーをカスタマイズする

時間ベースのキャッシュ ポリシーを作成する場合、最大有効期間、最小鮮度、最大期限延長、またはキャッシュ同期日付の値を指定することで、キャッシュの動作をカスタマイズできます。 <xref:System.Net.Cache.HttpRequestCachePolicy> オブジェクトは、これらの値の有効な組み合わせを指定できるようにする複数のコンストラクターを提供します。

## <a name="to-create-a-time-based-cache-policy-that-uses-a-cache-synchronization-date"></a>キャッシュ同期日付を使用する時間ベースのキャッシュ ポリシーを作成するには

<xref:System.Net.Cache.HttpRequestCachePolicy> コンストラクターに <xref:System.DateTime> オブジェクトを渡して、キャッシュ同期日付を使用する時間ベースのキャッシュ ポリシーを作成します。

```csharp
public static HttpRequestCachePolicy CreateLastSyncPolicy(DateTime when)
{
    var policy = new HttpRequestCachePolicy(when);
    Console.WriteLine("When: {0}", when);
    Console.WriteLine(policy.ToString());
    return policy;
}
```

```vb
Public Shared Function CreateLastSyncPolicy([when] As DateTime) As HttpRequestCachePolicy
    Dim policy As New HttpRequestCachePolicy([when])
    Console.WriteLine("When: {0}", [when])
    Console.WriteLine(policy.ToString())
    Return policy
End Function
```

次のように出力されます。

```output
When: 1/14/2004 8:07:30 AM
Level:Default CacheSyncDate:1/14/2004 8:07:30 AM
```

## <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness"></a>最小鮮度に基づく時間ベースのキャッシュ ポリシーを作成するには

`cacheAgeControl` パラメーター値として <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> を指定し、<xref:System.Net.Cache.HttpRequestCachePolicy> コンストラクターに <xref:System.TimeSpan> オブジェクトを渡して、最小鮮度に基づく時間ベースのキャッシュ ポリシーを作成します。

```csharp
public static HttpRequestCachePolicy CreateMinFreshPolicy(TimeSpan span)
{
    var policy = new HttpRequestCachePolicy(HttpCacheAgeControl.MinFresh, span);
    Console.WriteLine(policy.ToString());
    return policy;
}
```

```vb
Public Shared Function CreateMinFreshPolicy(span As TimeSpan) As HttpRequestCachePolicy
    Dim policy As New HttpRequestCachePolicy(HttpCacheAgeControl.MinFresh, span)
    Console.WriteLine(policy.ToString())
    Return policy
End Function
```

呼び出しと出力例を以下に示します。

```csharp
CreateMinFreshPolicy(new TimeSpan(1,0,0));
```

出力は次のようになります。

```output
Level:Default MinFresh:3600
```

## <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness-and-maximum-age"></a>最小鮮度と最大有効期間に基づく時間ベースのキャッシュ ポリシーを作成するには

`cacheAgeControl` パラメーター値として <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> を指定し、<xref:System.Net.Cache.HttpRequestCachePolicy> コンストラクターに 2 つの <xref:System.TimeSpan> オブジェクト (1 つはリソースの最大有効期間を指定し、もう 1 つはキャッシュから返されたオブジェクトで許可される最小鮮度を指定する) を渡して、最小鮮度と最大有効期間に基づく時間ベースのキャッシュ ポリシーを作成します。

```csharp
public static HttpRequestCachePolicy CreateFreshAndAgePolicy(TimeSpan freshMinimum, TimeSpan ageMaximum)
{
    var policy = new HttpRequestCachePolicy(HttpCacheAgeControl.MaxAgeAndMinFresh, ageMaximum, freshMinimum);
    Console.WriteLine(policy.ToString());
    return policy;
}
```

```vb
Public Shared Function CreateFreshAndAgePolicy(freshMinimum As TimeSpan, ageMaximum As TimeSpan) As HttpRequestCachePolicy
    Dim policy As New HttpRequestCachePolicy(HttpCacheAgeControl.MaxAgeAndMinFresh, ageMaximum, freshMinimum)
    Console.WriteLine(policy.ToString())
    Return policy
End Function
```

呼び出しと出力例を以下に示します。
  
```csharp
CreateFreshAndAgePolicy(new TimeSpan(5,0,0), new TimeSpan(10,0,0));  
```  

出力は次のようになります。
  
```output
Level:Default MaxAge:36000 MinFresh:18000  
```  
  
## <a name="see-also"></a>関連項目

- [ネットワーク アプリケーションのキャッシュ管理](cache-management-for-network-applications.md)
- [キャッシュ ポリシー](cache-policy.md)
- [場所ベースのキャッシュ ポリシー](location-based-cache-policies.md)
- [時間ベースのキャッシュ ポリシー](time-based-cache-policies.md)
- [\<requestCaching> 要素 (ネットワーク設定)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
