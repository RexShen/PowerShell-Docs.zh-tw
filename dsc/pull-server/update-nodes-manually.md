---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 從提取伺服器更新節點
ms.openlocfilehash: 4333a5bf82ef45f22a062942ebe93409433623f5
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400614"
---
# <a name="update-nodes-from-a-pull-server"></a><span data-ttu-id="e500f-103">從提取伺服器更新節點</span><span class="sxs-lookup"><span data-stu-id="e500f-103">Update Nodes from a Pull Server</span></span>

<span data-ttu-id="e500f-104">下列各節假設您有已設定提取伺服器。</span><span class="sxs-lookup"><span data-stu-id="e500f-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="e500f-105">如果您還沒有設定提取伺服器，您可以使用下列指南：</span><span class="sxs-lookup"><span data-stu-id="e500f-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="e500f-106">設定 DSC SMB 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="e500f-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="e500f-107">設定 DSC HTTP 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="e500f-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="e500f-108">若要下載組態中，資源，並甚至報告其狀態，可以設定每個目標節點。</span><span class="sxs-lookup"><span data-stu-id="e500f-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="e500f-109">本文將說明如何上傳資源，讓它們可被下載，並設定用戶端會自動下載的資源。</span><span class="sxs-lookup"><span data-stu-id="e500f-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="e500f-110">當節點會收到指派的組態，透過**提取**或是**推送**(v5)，便會自動下載從 LCM 中指定的位置組態所需的任何資源。</span><span class="sxs-lookup"><span data-stu-id="e500f-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="using-the-update-dscconfiguration-cmdlet"></a><span data-ttu-id="e500f-111">使用 Update-dscconfiguration cmdlet</span><span class="sxs-lookup"><span data-stu-id="e500f-111">Using the Update-DSCConfiguration cmdlet</span></span>

<span data-ttu-id="e500f-112">從 PowerShell 5.0 [Update-dscconfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) cmdlet，此 cmdlet 會強制更新從提取伺服器設定 LCM 中其組態的節點。</span><span class="sxs-lookup"><span data-stu-id="e500f-112">Beginning in PowerShell 5.0, the [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) cmdlet, forces a Node to update its configuration from the Pull Server configured in the LCM.</span></span>

```powershell
Update-DSCConfiguration -ComputerName "Server01"
```

## <a name="using-invoke-cimmethod"></a><span data-ttu-id="e500f-113">使用叫用 CIMMethod</span><span class="sxs-lookup"><span data-stu-id="e500f-113">Using Invoke-CIMMethod</span></span>

<span data-ttu-id="e500f-114">在 PowerShell 4.0 中，您可以手動強制提取用戶端更新其組態中使用[Invoke-cimmethod](/powershell/module/cimcmdlets/invoke-cimmethod)。</span><span class="sxs-lookup"><span data-stu-id="e500f-114">In PowerShell 4.0, you can still manually force a Pull Client to update its Configuration using [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod).</span></span> <span data-ttu-id="e500f-115">下列範例會使用指定的認證建立 CIM 工作階段、 叫用適當的 CIM 方法，並移除工作階段。</span><span class="sxs-lookup"><span data-stu-id="e500f-115">The following example creates a CIM session with specified credentials, invokes the appropriate CIM method, and removes the session.</span></span>

```powershell
$cimSession = New-CimSession -ComputerName "Server01" -Credential $(Get-Credential)
Invoke-CimMethod -CimSession $cimSession -Namespace 'root/microsoft/windows/desiredstateconfiguration' -Class 'MSFT_DscLocalConfigurationManager' -MethodName 'PerformRequiredConfigurationChecks' -Arguments @{ 'Flags' = [uint32]1 } -Verbose
$cimSession | Remove-CimSession
```

## <a name="see-also"></a><span data-ttu-id="e500f-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e500f-116">See Also</span></span>

[<span data-ttu-id="e500f-117">PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="e500f-117">PerformRequiredConfigurationChecks</span></span>](/powershell/dsc/msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks)
