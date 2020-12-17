---
author: sdwheeler
ms.author: sewhee
ms.date: 11/18/2020
ms.topic: include
ms.prod: powershell
ms.openlocfilehash: 700021715729254f5704abca16c0e18f598efaec
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2020
ms.locfileid: "96913267"
---
> [!IMPORTANT]
> <span data-ttu-id="7781a-101">從 2020 年 4 月起，PowerShell 資源庫已不再支援傳輸層安全性 (TLS) 1.0 和 1.1 版。</span><span class="sxs-lookup"><span data-stu-id="7781a-101">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="7781a-102">如果您不是使用 TLS 1.2 或更高版本，您在嘗試存取 PowerShell 資源庫時將會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="7781a-102">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="7781a-103">使用下列命令來確保您使用的是 TLS 1.2：</span><span class="sxs-lookup"><span data-stu-id="7781a-103">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> ```powershell
> [Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
> ```
>
> <span data-ttu-id="7781a-104">如需詳細資訊，請參閱 PowerShell 部落格中的[公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="7781a-104">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>
