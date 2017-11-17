---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,設定"
ms.openlocfilehash: ce60b240045acf538edae1a08007971e538588ca
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2017
---
# <a name="test-dscconfiguration-cmdlet-supports-reference-configurations"></a><span data-ttu-id="9f3af-102">Test-DscConfiguration Cmdlet 支援參考設定</span><span class="sxs-lookup"><span data-stu-id="9f3af-102">Test-DscConfiguration cmdlet supports Reference Configurations</span></span>

<span data-ttu-id="9f3af-103">Test-DscConfiguration Cmdlet 已更新，允許進行一個或多個目標節點所需設定狀態的測試 (藉由比較指定的參考設定文件來完成測試)。</span><span class="sxs-lookup"><span data-stu-id="9f3af-103">The Test-DscConfiguration cmdlet has been updated to allow testing of desired configuration state of one or more target nodes by specifying a reference configuration document to compare against.</span></span>

<span data-ttu-id="9f3af-104">下列的新參數集，只在指定的路徑中將 DSC 設定用於測試，並永遠不會將個別設定套用在指定的目標節點上。</span><span class="sxs-lookup"><span data-stu-id="9f3af-104">The following new parameter sets use DSC configurations in the path specified to only test and never apply each configuration on the specified target node(s).</span></span> <span data-ttu-id="9f3af-105">就像 Start-DscConfiguration 與其他 DSC Cmdlets 一樣，每個 MOF 的名稱將用於判斷在哪個目標節點上測試設定。</span><span class="sxs-lookup"><span data-stu-id="9f3af-105">As with Start-DscConfiguration and other DSC cmdlets, the name of each MOF is used to determine which target node to test the configuration on.</span></span> 

```powershell
Test-DscConfiguration   [-Path] <string> 
                        [[-ComputerName] <string[]>] 
                        [-Credential <pscredential>] 
                        [-ThrottleLimit <int>] 
                        [-AsJob] 
                        [<CommonParameters>]

Test-DscConfiguration   [-Path] <string> 
                        -CimSession <CimSession[]> 
                        [-ThrottleLimit <int>] 
                        [-AsJob] 
                        [<CommonParameters>]
```

<span data-ttu-id="9f3af-106">下列新的參數集只將單一 DSC 設定用於測試，且永遠不會將設定套用在指定的目標節點上。</span><span class="sxs-lookup"><span data-stu-id="9f3af-106">The following new parameter sets use a single DSC configuration to only test and never apply the configuration on the specified target node(s).</span></span> 

```powershell
Test-DscConfiguration   -ReferenceConfiguration <string> 
                        [[-ComputerName] <string[]>]
                        [-Credential <pscredential>] 
                        [-ThrottleLimit <int>] 
                        [-AsJob] 
                        [<CommonParameters>]

Test-DscConfiguration   -ReferenceConfiguration <string> 
                        -CimSession <CimSession[]> 
                        [-ThrottleLimit <int>] 
                        [-AsJob] 
                        [<CommonParameters>]
```

