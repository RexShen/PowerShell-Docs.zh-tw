---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,設定
ms.openlocfilehash: a8947844df0da167961c64e1e09d5075960c95de
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="generate-powershell-cmdlets-based-on-odata-endpoint"></a><span data-ttu-id="2e8fa-102">根據 OData 端點產生 PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2e8fa-102">Generate PowerShell Cmdlets based on OData Endpoint</span></span>
<a name="generate-windows-powershell-cmdlets-based-on-an-odata-endpoint"></a><span data-ttu-id="2e8fa-103">根據 OData 端點產生 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2e8fa-103">Generate Windows PowerShell cmdlets based on an OData endpoint</span></span>
--------------------------------------------------------------

<span data-ttu-id="2e8fa-104">**Export-ODataEndpointProxy** 是 Cmdlet，它會根據指定的 OData 端點所公開的功能產生一組 Windows PowerShell Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2e8fa-104">**Export-ODataEndpointProxy** is a cmdlet that generates a set of Windows PowerShell cmdlets based on the functionality exposed by a given OData endpoint.</span></span>

<span data-ttu-id="2e8fa-105">下例示範如何使用這個新的 Cmdlet：</span><span class="sxs-lookup"><span data-stu-id="2e8fa-105">The following example shows how to use this new cmdlet:</span></span>

<span data-ttu-id="2e8fa-106">\# Export-ODataEndpointProxy 基本使用案例</span><span class="sxs-lookup"><span data-stu-id="2e8fa-106">\# Basic use case of Export-ODataEndpointProxy</span></span>

```powershell
Export-ODataEndpointProxy -Uri 'http://services.odata.org/v3/(S(snyobsk1hhutkb2yulwldgf1))/odata/odata.svc' -OutputModule C:\Users\user\Generated.psd1

ipmo 'C:\Users\user\Generated.psd1'
# Cmdlets are created based on the following heuristics
# New-<EntityType> -<Key> [-<Other Attributes>]
#
# Get-<EntityType> [-<Key> -Top –Skip –Filter -OrderBy]
# # If there is a complex key, the keys will actually be -<Key1> -<Key2>…
# # Note this rule applies to any other instances of the key
#
# Set-<EntityType> -<Key> [-<Other Attributes>]
#
# Remove-<EntityType> -<Key>
#
# Invoke-<EntityType><Action> [-<Key> -<Other Parameters>]
#
#
# Cmdlets from associations (Note: Get and Remove get additional parameter sets)
# Get-<EntityType> -<AssociatedEntity>
# New-<EntityType> -<AssociatedEntity> -<Key>
# Remove-<EntityType> -<AssociatedEntity> -<Key>
#
#
# Note: Every cmdlet has the –ConnectionURI parameter for explicitly setting the URI of the endpoint. This normally uses the same address that you gave the Export-ODataEndpointProxy cmdlet, but can be overridden in this fashion for the sake of similar endpoints.
#
```

<span data-ttu-id="2e8fa-107">這項功能仍有部分主要使用案例仍在開發中，包括但不限於：</span><span class="sxs-lookup"><span data-stu-id="2e8fa-107">There are still parts of key use cases in development for this functionality, including, but not limited to:</span></span>
-   <span data-ttu-id="2e8fa-108">關聯</span><span class="sxs-lookup"><span data-stu-id="2e8fa-108">Associations</span></span>
-   <span data-ttu-id="2e8fa-109">傳遞資料流</span><span class="sxs-lookup"><span data-stu-id="2e8fa-109">Passing streams</span></span>

<a name="generate-windows-powershell-cmdlets-based-on-an-odata-endpoint-with-odatautils"></a><span data-ttu-id="2e8fa-110">根據具有 ODataUtils 的 OData 端點產生 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2e8fa-110">Generate Windows PowerShell cmdlets based on an OData endpoint with ODataUtils</span></span>
------------------------------------------------------------------------------
<span data-ttu-id="2e8fa-111">ODataUtils 模組可以從支援 OData 的 REST 端點產生 Windows PowerShell Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2e8fa-111">The ODataUtils module allows generation of Windows PowerShell cmdlets from REST endpoints that support OData.</span></span> <span data-ttu-id="2e8fa-112">下列的累加增強功能位在 Microsoft.PowerShell.ODataUtils Windows PowerShell 模組中。</span><span class="sxs-lookup"><span data-stu-id="2e8fa-112">The following incremental enhancements are in the Microsoft.PowerShell.ODataUtils Windows PowerShell module.</span></span>
-   <span data-ttu-id="2e8fa-113">從伺服器端端點到用戶端的通道其他資訊。</span><span class="sxs-lookup"><span data-stu-id="2e8fa-113">Channel additional information from server-side endpoint to client side.</span></span>
-   <span data-ttu-id="2e8fa-114">用戶端的分頁支援</span><span class="sxs-lookup"><span data-stu-id="2e8fa-114">Client-side paging support</span></span>
-   <span data-ttu-id="2e8fa-115">使用 -Select 參數進行伺服器端篩選</span><span class="sxs-lookup"><span data-stu-id="2e8fa-115">Server-side filtering by using the -Select parameter</span></span>
-   <span data-ttu-id="2e8fa-116">Web 要求標頭的支援</span><span class="sxs-lookup"><span data-stu-id="2e8fa-116">Support for web request headers</span></span>

<span data-ttu-id="2e8fa-117">Export-ODataEndPointProxy Cmdlet 產生的 Proxy Cmdlet 提供伺服器端 OData 端點資訊資料流 (新的 Windows PowerShell 5.0 功能) 的其他資訊 (用戶端 Proxy 產生期間所使用的 $metadata 中未提及)。</span><span class="sxs-lookup"><span data-stu-id="2e8fa-117">The proxy cmdlets generated by the Export-ODataEndPointProxy cmdlet provide additional information (not mentioned in the $metadata used during the client-side proxy generation) from the server side OData endpoint on the Information stream (a new Windows PowerShell 5.0 feature).</span></span> <span data-ttu-id="2e8fa-118">下例為取得這項資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="2e8fa-118">Here is an example of how to get that information.</span></span>
```powershell
Import-Module Microsoft.PowerShell.ODataUtils -Force
$generatedProxyModuleDir = Join-Path -Path $env:SystemDrive -ChildPath 'ODataDemoProxy'
$uri = "http://services.odata.org/V3/(S(fhleiief23wrm5a5nhf542q5))/OData/OData.svc/"
Export-ODataEndpointProxy -Uri $uri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -AllowClobber
Import-Module $generatedProxyModuleDir -Force

# In the below command, we are retrieving top 1 product.
# By specifying -IncludeTotalResponseCount parameter,
# we are getting the total count of all the Product records
# available on the server side. This information
# is surfaced on the client side through the Information stream.
$product = Get-Product -Top 1 -AllowUnsecureConnection -AllowAdditionalData -IncludeTotalResponseCount -InformationVariable infoStream
# The Information stream contains the additional
# information sent from the server side.
$additionalInfo = $infoStream.GetEnumerator() | % MessageData
# 'Odata.Count' indicates the total product records
# available on the server side Odata endpoint.
$additionalInfo['odata.count']
```

<span data-ttu-id="2e8fa-119">您可以使用用戶端的分頁支援，從批次的伺服器端取得記錄。</span><span class="sxs-lookup"><span data-stu-id="2e8fa-119">You can get the records from the server side in batches by using client-side paging support.</span></span> <span data-ttu-id="2e8fa-120">當您必須透過網路從伺服器取得大量資料時，這非常有用。</span><span class="sxs-lookup"><span data-stu-id="2e8fa-120">This is useful when you must get a large amount of data from the server over the network.</span></span>
```powershell
$skipCount = 0
$batchSize = 3
# Client-Side Paging Support: The records from the server side
# are retrieved in batches of $batchSize
while($skipCount -le $additionalInfo['odata.count'])
{
Get-Product -AllowUnsecureConnection -AllowAdditionalData -Top $batchSize -Skip $skipCount
$skipCount += $batchSize
}
```

<span data-ttu-id="2e8fa-121">產生的 Proxy Cmdlet 支援 –Select 參數，這可用為篩選條件，只接收用戶端需要的記錄屬性。</span><span class="sxs-lookup"><span data-stu-id="2e8fa-121">The generated proxy cmdlets support the –Select parameter which you can use as a filter to receive only the record properties that the client needs.</span></span> <span data-ttu-id="2e8fa-122">因為篩選發生在伺服器端，所以這會減少透過網路傳送的資料量。</span><span class="sxs-lookup"><span data-stu-id="2e8fa-122">This reduces the amount of data that is transferred over the network, because the filtering occurs on the server side.</span></span>
```powershell
# In the below example only the Name property of the
# Product record is retrieved from the server side.
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

<span data-ttu-id="2e8fa-123">Export-ODataEndpointProxy Cmdlet 和它產生的 Proxy Cmdlet，現在支援標頭參數 (提供值當做雜湊表)，可用來傳輸伺服器端 OData 端點所預期的任何其他資訊。</span><span class="sxs-lookup"><span data-stu-id="2e8fa-123">The Export-ODataEndpointProxy cmdlet, and the proxy cmdlets generated by it, now support the Headers parameter (supply values as a hash table), which you can use to channel any additional information that is expected by the server-side OData endpoint.</span></span> <span data-ttu-id="2e8fa-124">在下列範例中，您可以透過期待驗證訂閱金鑰的服務標頭傳輸訂閱金鑰。</span><span class="sxs-lookup"><span data-stu-id="2e8fa-124">In the following example, you can channel a Subscription key through Headers for services that are expecting a Subscription key for authentication.</span></span>
```powershell
# As an example, in the below command 'XXXX' is the authentication used by the
# Export-ODataEndpointProxy cmdlet to interact with the server-side
# OData endpoint accessed through $endPointUri.

Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```