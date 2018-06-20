---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
ms.openlocfilehash: f929ce4684bb53c3039238ecd465f1c0e432f741
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225669"
---
# <a name="deliver-a-configuration-document-without-applying"></a><span data-ttu-id="1d97a-102">傳遞設定文件，但不套用它</span><span class="sxs-lookup"><span data-stu-id="1d97a-102">Deliver a configuration document without applying</span></span>

<span data-ttu-id="1d97a-103">[Publish-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) Cmdlet 將設定 MOF 檔案複製到目標節點，但不會套用此設定。</span><span class="sxs-lookup"><span data-stu-id="1d97a-103">The [Publish-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) cmdlet copies a configuration MOF file to a target node, but does not apply the configuration.</span></span>
<span data-ttu-id="1d97a-104">直到下個一致性階段，或當您執行 [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx) Cmdlet 時才會套用此設定。</span><span class="sxs-lookup"><span data-stu-id="1d97a-104">This configuration is applied during the next consistency pass, or when you run the [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx) cmdlet.</span></span>
