---
ms.openlocfilehash: d61a3b3dd855d783d7bff7cb74e5b84969e60860
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2020
ms.locfileid: "91608050"
---
### <a name="aspnet-incorrect-multipart-handling-may-result-in-lost-form-data"></a>ASP.NET 正しくないマルチパート処理により、フォーム データが失われる場合がある。

#### <a name="details"></a>説明

.NET Framework 4.7.2 以前のバージョンをターゲットとするアプリケーションでは、ASP.NET でマルチパート境界の値が正しく解析されないために、要求の実行中にフォーム データが使用できなくなる場合があります。 .NET Framework 4.8 以降のバージョンをターゲットとするアプリケーションではマルチパート データが正しく解析されるため、要求の実行中にフォーム値を使用することができます。

#### <a name="suggestion"></a>提案される解決策

.NET Framework 4.8 以降で実行されているアプリケーションで、Framework 4.8 以降をターゲットとする場合は、<code>targetFrameworkVersion</code> 要素を使用して、区切り記号を削除するように既定の動作を変更します。 以前のフレームワークのバージョンをターゲットとするか、<code>targetFrameworkVersion</code> を使用しない場合、一部の値の末尾の区切り記号が引き続き返されます。この動作は、<code>appSetting</code> で明示的に制御することもできます。<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:UseLegacyMultiValueHeaderHandling&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| 名前    | [値]       |
|:--------|:------------|
| スコープ   |不明|
|バージョン|4.8|
|種類|ランタイム|

#### <a name="affected-apis"></a>影響を受ける API

- <xref:System.Web.HttpRequest.Form?displayProperty=nameWithType>
- <xref:System.Web.HttpRequest.Files?displayProperty=nameWithType>
- <xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Web.HttpRequest.Form`
- `P:System.Web.HttpRequest.Files`
- `P:System.Web.HttpRequest.ContentEncoding`

-->
