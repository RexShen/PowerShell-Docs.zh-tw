---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,設定"
ms.openlocfilehash: e921a5ead21f52b7e0d9efd9335c44b99d7d6802
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="deliver-a-configuration-document-without-applying"></a><span data-ttu-id="e3466-102">傳遞設定文件，但不套用它</span><span class="sxs-lookup"><span data-stu-id="e3466-102">Deliver a configuration document without applying</span></span>

<span data-ttu-id="e3466-103">[Publish-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) Cmdlet 將設定 MOF 檔案複製到目標節點，但不會套用此設定。</span><span class="sxs-lookup"><span data-stu-id="e3466-103">The [Publish-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) cmdlet copies a configuration MOF file to a target node, but does not apply the configuration.</span></span> <span data-ttu-id="e3466-104">直到下個一致性階段，或當您執行 [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx) Cmdlet 時才會套用此設定。</span><span class="sxs-lookup"><span data-stu-id="e3466-104">This configuration is applied during the next consistency pass, or when you run the [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx) cmdlet.</span></span>

