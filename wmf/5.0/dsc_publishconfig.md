---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,設定
ms.openlocfilehash: 136e16ae74e54f3bc9d0623178257df1e9104aac
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="deliver-a-configuration-document-without-applying"></a><span data-ttu-id="48e5c-102">傳遞設定文件，但不套用它</span><span class="sxs-lookup"><span data-stu-id="48e5c-102">Deliver a configuration document without applying</span></span>

<span data-ttu-id="48e5c-103">[Publish-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) Cmdlet 將設定 MOF 檔案複製到目標節點，但不會套用此設定。</span><span class="sxs-lookup"><span data-stu-id="48e5c-103">The [Publish-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) cmdlet copies a configuration MOF file to a target node, but does not apply the configuration.</span></span>
<span data-ttu-id="48e5c-104">直到下個一致性階段，或當您執行 [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx) Cmdlet 時才會套用此設定。</span><span class="sxs-lookup"><span data-stu-id="48e5c-104">This configuration is applied during the next consistency pass, or when you run the [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx) cmdlet.</span></span>