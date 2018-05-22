---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 用來從提取伺服器查詢節點資訊的 DSC 函式。
ms.openlocfilehash: 069fc79a79fbd5f75bcce27f7f0bd95af0d7b1ad
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="dsc-function-to-query-node-information-from-pull-server"></a><span data-ttu-id="b6951-103">用來從提取伺服器查詢節點資訊的 DSC 函式。</span><span class="sxs-lookup"><span data-stu-id="b6951-103">DSC function to query node information from pull server.</span></span>

```powershell
function QueryNodeInformation
{
Param (
       [string] $Uri =
"http://localhost:7070/PSDSCComplianceServer.svc/Status",
       [string] $ContentType = "application/json"
     )

  Write-Host "Querying node information from pull server URI  = $Uri" -ForegroundColor Green

  Write-Host "Querying node status in content type  = $ContentType " -ForegroundColor Green

   $response = Invoke-WebRequest -Uri $Uri -Method Get -ContentType $ContentType -UseDefaultCredentials -Headers
    @{Accept = $ContentType}

   if($response.StatusCode -ne 200)
 {
     Write-Host "node information was not retrieved." -ForegroundColor Red
 }

 $jsonResponse = ConvertFrom-Json $response.Content

  return $jsonResponse
}
```

<span data-ttu-id="b6951-104">將 `Uri` 參數取代為提取伺服器的 URI。</span><span class="sxs-lookup"><span data-stu-id="b6951-104">Replace the `Uri` parameter with the URI for your pull server.</span></span> <span data-ttu-id="b6951-105">如果您希望節點資訊為 XML 格式，請將 `ContentType` 設定為 `application/xml`。</span><span class="sxs-lookup"><span data-stu-id="b6951-105">If you want the node information in XML format, set `ContentType` to `application/xml`.</span></span>

<span data-ttu-id="b6951-106">若要從 `$json` 參數擷取節點資訊，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="b6951-106">To retrieve the node information from the `$json` parameter, use the following:</span></span>

```powershell
$json = QueryNodeInformation –Uri http://localhost:7070/PSDSCComplianceServer.svc/Status

$json.value | Format-Table TargetName, ConfigurationId, ServerChecksum, NodeCompliant, LastComplianceTime, StatusCode
```