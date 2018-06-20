---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
ms.openlocfilehash: 6d37fbc5091d69925d60349f3acbdecc92da1b95
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
ms.locfileid: "34220337"
---
# <a name="on-demand-pull-of-dsc-configurations"></a><span data-ttu-id="1650b-102">DSC 設定的依需求 PULL</span><span class="sxs-lookup"><span data-stu-id="1650b-102">On-demand PULL of DSC Configurations</span></span>

<span data-ttu-id="1650b-103">新的 Update-DscConfiguration Cmdlet 觸發在中繼設定中定義的提取伺服器提取。</span><span class="sxs-lookup"><span data-stu-id="1650b-103">The new Update-DscConfiguration cmdlet triggers a pull from the pull server(s) defined in the meta-configuration.</span></span> <span data-ttu-id="1650b-104">此行為通常稱為「現在提取」。</span><span class="sxs-lookup"><span data-stu-id="1650b-104">The behavior is often referred to as 'Pull Now'.</span></span>


<span data-ttu-id="1650b-105">一旦觸發，提取行為會和在一般的頻率期間觸發時完全相同︰</span><span class="sxs-lookup"><span data-stu-id="1650b-105">Once triggered, the pull behaves exactly the same as it would have when triggered during the regular frequency:</span></span>

1. <span data-ttu-id="1650b-106">目前設定的總和檢查碼會和在提取伺服器上設定的總和檢查碼比較。</span><span class="sxs-lookup"><span data-stu-id="1650b-106">The checksum for current configuration is compared to the checksum for the configuration on the pull server.</span></span>
2. <span data-ttu-id="1650b-107">如果兩者相同，它不套用設定就能順利完成。</span><span class="sxs-lookup"><span data-stu-id="1650b-107">If they are the same, it completes successfully without applying the configuration.</span></span>
3. <span data-ttu-id="1650b-108">如果兩者不同，就會從提取伺服器提取設定，並將其套用。</span><span class="sxs-lookup"><span data-stu-id="1650b-108">If they are different, the configuration is pulled down from the pull server and applied.</span></span>

<span data-ttu-id="1650b-109">**注意︰** 如果中繼設定 RefreshMode = 'Push' 時，此 Cmdlet 會傳回錯誤，因此目標節點處在 'Push' 模式時此 Cmdlet 一律不會執行任何動作。</span><span class="sxs-lookup"><span data-stu-id="1650b-109">**Note:** If the Meta-Configuration RefreshMode = 'Push' an error is returned by this cmdlet so this cmdlet will always do nothing when a target node is in 'Push' Mode.</span></span>

```powershell
Update-DscConfiguration     [[-ComputerName] <string[]>]
                            [-Wait]
                            [-Force]
                            [-JobName <string>]
                            [-Credential<pscredential>]
                            [-ThrottleLimit <int>]
                            [-WhatIf]
                            [-Confirm]
                            [<CommonParameters>]

Update-DscConfiguration     -CimSession <CimSession[]>
                            [-Wait]
                            [-Force]
                            [-JobName <string>]
                            [-ThrottleLimit <int>]
                            [-WhatIf]
                            [-Confirm]
                            [<CommonParameters>]
```
