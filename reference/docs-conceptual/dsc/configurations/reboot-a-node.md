---
ms.date: 01/17/2019
keywords: dsc,powershell,設定,安裝
title: 重新啟動節點
description: 有許多組態設定可能會要求電腦重新開機，以完成設定變更。 此文章說明如何管理設定中的重新開機。
ms.openlocfilehash: d2b0f77c34ebcb006821da1f4f8d7c4b046f7a95
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645117"
---
# <a name="reboot-a-node"></a><span data-ttu-id="7b5c2-105">重新啟動節點</span><span class="sxs-lookup"><span data-stu-id="7b5c2-105">Reboot a Node</span></span>

> [!NOTE]
> <span data-ttu-id="7b5c2-106">本主題討論如何重新啟動節點。</span><span class="sxs-lookup"><span data-stu-id="7b5c2-106">This topic talks about how to reboot a Node.</span></span> <span data-ttu-id="7b5c2-107">必須正確設定 **ActionAfterReboot** 和 **RebootNodeIfNeeded** LCM 設定，才能成功重新開機。</span><span class="sxs-lookup"><span data-stu-id="7b5c2-107">In order for the reboot to be successful the **ActionAfterReboot** and **RebootNodeIfNeeded** LCM settings need to be configured properly.</span></span> <span data-ttu-id="7b5c2-108">若要查看本機設定管理員設定，請參閱[設定本機設定管理員](../managing-nodes/metaConfig.md)或[設定本機設定管理員 (v4)](../managing-nodes/metaConfig4.md)。</span><span class="sxs-lookup"><span data-stu-id="7b5c2-108">To read about Local Configuration Manager settings, see [Configure the Local Configuration Manager](../managing-nodes/metaConfig.md), or [Configure the Local Configuration Manager (v4)](../managing-nodes/metaConfig4.md).</span></span>

<span data-ttu-id="7b5c2-109">使用 `$global:DSCMachineStatus` 旗標即可從資源內重新啟動節點。</span><span class="sxs-lookup"><span data-stu-id="7b5c2-109">Nodes can be rebooted from within a resource, by using the `$global:DSCMachineStatus` flag.</span></span> <span data-ttu-id="7b5c2-110">在 `Set-TargetResource` 函式中將此旗標設為 `1`，會強制 LCM 在目前資源的 **Set** 方法之後，直接重新啟動節點。</span><span class="sxs-lookup"><span data-stu-id="7b5c2-110">Setting this flag to `1` in the `Set-TargetResource` function forces the LCM to reboot the Node directly after the **Set** method of the current resource.</span></span> <span data-ttu-id="7b5c2-111">使用此旗標， **ComputerManagementDsc** 資源模組中的 [PendingReboot](https://github.com/PowerShell/ComputerManagementDsc) 資源會偵測 DSC 外部是否有擱置的重新開機。</span><span class="sxs-lookup"><span data-stu-id="7b5c2-111">Using this flag, the **PendingReboot** resource in the [ComputerManagementDsc](https://github.com/PowerShell/ComputerManagementDsc) DSC Resource module detects if a reboot is pending outside of DSC.</span></span>

<span data-ttu-id="7b5c2-112">您的[設定](configurations.md)會執行需要重新啟動節點的步驟。</span><span class="sxs-lookup"><span data-stu-id="7b5c2-112">Your [configurations](configurations.md) may perform steps that require the Node to reboot.</span></span> <span data-ttu-id="7b5c2-113">這可能包括下列項目：</span><span class="sxs-lookup"><span data-stu-id="7b5c2-113">This could include things such as:</span></span>

- <span data-ttu-id="7b5c2-114">Windows 更新</span><span class="sxs-lookup"><span data-stu-id="7b5c2-114">Windows updates</span></span>
- <span data-ttu-id="7b5c2-115">軟體安裝</span><span class="sxs-lookup"><span data-stu-id="7b5c2-115">Software install</span></span>
- <span data-ttu-id="7b5c2-116">檔案重新命名</span><span class="sxs-lookup"><span data-stu-id="7b5c2-116">File renames</span></span>
- <span data-ttu-id="7b5c2-117">電腦重新命名</span><span class="sxs-lookup"><span data-stu-id="7b5c2-117">Computer rename</span></span>

<span data-ttu-id="7b5c2-118">**PendingReboot** 資源會檢查特定的電腦位置來判斷重新啟動是否暫止。</span><span class="sxs-lookup"><span data-stu-id="7b5c2-118">The **PendingReboot** resource checks specific computer locations to determine if a reboot is pending.</span></span> <span data-ttu-id="7b5c2-119">如果節點要求在 DSC 外重新啟動，則 **PendingReboot** 資源會將 `$global:DSCMachineStatus` 旗標設定為 `1` 來強制重新啟動並解決暫止狀況。</span><span class="sxs-lookup"><span data-stu-id="7b5c2-119">If the Node requires a reboot outside of DSC, the **PendingReboot** resource sets the `$global:DSCMachineStatus` flag to `1` forcing a reboot and resolving the pending condition.</span></span>

> [!NOTE]
> <span data-ttu-id="7b5c2-120">任何 DSC 資源皆可在 `Set-TargetResource` 函式中設定此旗標，指示 LCM 重新啟動節點。</span><span class="sxs-lookup"><span data-stu-id="7b5c2-120">Any DSC resource can instruct the LCM to reboot the node by setting this flag in the `Set-TargetResource` function.</span></span> <span data-ttu-id="7b5c2-121">如需詳細資訊，請參閱[使用 MOF 撰寫自訂的 DSC 資源](../resources/authoringResourceMOF.md)。</span><span class="sxs-lookup"><span data-stu-id="7b5c2-121">For more information, see [Writing a custom DSC resource with MOF](../resources/authoringResourceMOF.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="7b5c2-122">語法</span><span class="sxs-lookup"><span data-stu-id="7b5c2-122">Syntax</span></span>

```
PendingReboot [String] #ResourceName
{
    Name = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [SkipCcmClientSDK = [bool]]
    [SkipComponentBasedServicing = [bool]]
    [SkipPendingComputerRename = [bool]]
    [SkipPendingFileRename = [bool]]
    [SkipWindowsUpdate = [bool]]
}
```

## <a name="properties"></a><span data-ttu-id="7b5c2-123">屬性</span><span class="sxs-lookup"><span data-stu-id="7b5c2-123">Properties</span></span>

| <span data-ttu-id="7b5c2-124">屬性</span><span class="sxs-lookup"><span data-stu-id="7b5c2-124">Property</span></span> | <span data-ttu-id="7b5c2-125">描述</span><span class="sxs-lookup"><span data-stu-id="7b5c2-125">Description</span></span> |
| --- | --- |
| <span data-ttu-id="7b5c2-126">Name</span><span class="sxs-lookup"><span data-stu-id="7b5c2-126">Name</span></span>| <span data-ttu-id="7b5c2-127">在設定內，資源每個執行個體的必要參數都必須為唯一。</span><span class="sxs-lookup"><span data-stu-id="7b5c2-127">Required parameter that must be unique per instance of the resource within a configuration.</span></span>|
| <span data-ttu-id="7b5c2-128">SkipComponentBasedServicing</span><span class="sxs-lookup"><span data-stu-id="7b5c2-128">SkipComponentBasedServicing</span></span> | <span data-ttu-id="7b5c2-129">以元件為基礎服務元件所觸發的略過重新啟動。</span><span class="sxs-lookup"><span data-stu-id="7b5c2-129">Skip reboots triggered by the Component-Based Servicing component.</span></span> |
| <span data-ttu-id="7b5c2-130">SkipWindowsUpdate</span><span class="sxs-lookup"><span data-stu-id="7b5c2-130">SkipWindowsUpdate</span></span> | <span data-ttu-id="7b5c2-131">Windows Update 所觸發的略過重新啟動。</span><span class="sxs-lookup"><span data-stu-id="7b5c2-131">Skip reboots triggered by Windows Update.</span></span>|
| <span data-ttu-id="7b5c2-132">SkipPendingFileRename</span><span class="sxs-lookup"><span data-stu-id="7b5c2-132">SkipPendingFileRename</span></span> | <span data-ttu-id="7b5c2-133">略過暫止檔案重新命名重新啟動。</span><span class="sxs-lookup"><span data-stu-id="7b5c2-133">Skip pending file rename reboots.</span></span> |
| <span data-ttu-id="7b5c2-134">SkipCcmClientSDK</span><span class="sxs-lookup"><span data-stu-id="7b5c2-134">SkipCcmClientSDK</span></span> | <span data-ttu-id="7b5c2-135">ConfigMgr 用戶端所觸發的略過重新啟動。</span><span class="sxs-lookup"><span data-stu-id="7b5c2-135">Skip reboots triggered by the ConfigMgr client.</span></span> |
| <span data-ttu-id="7b5c2-136">SkipComputerRename</span><span class="sxs-lookup"><span data-stu-id="7b5c2-136">SkipComputerRename</span></span> | <span data-ttu-id="7b5c2-137">電腦重新命名所觸發的略過重新啟動。</span><span class="sxs-lookup"><span data-stu-id="7b5c2-137">Skip reboots triggered by Computer renames.</span></span> |
| <span data-ttu-id="7b5c2-138">PSDSCRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="7b5c2-138">PSDSCRunAsCredential</span></span> | <span data-ttu-id="7b5c2-139">v5 支援。</span><span class="sxs-lookup"><span data-stu-id="7b5c2-139">Supported in v5.</span></span> <span data-ttu-id="7b5c2-140">以指定的使用者身分執行資源。</span><span class="sxs-lookup"><span data-stu-id="7b5c2-140">Executes the resource as the specified user.</span></span> |
| <span data-ttu-id="7b5c2-141">DependsOn</span><span class="sxs-lookup"><span data-stu-id="7b5c2-141">DependsOn</span></span> | <span data-ttu-id="7b5c2-142">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="7b5c2-142">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="7b5c2-143">例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 **ResourceName** ，而它的類型是 **ResourceType** ，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="7b5c2-143">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType** , the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> <span data-ttu-id="7b5c2-144">如需詳細資訊，請參閱[使用 DependsOn](resource-depends-on.md)</span><span class="sxs-lookup"><span data-stu-id="7b5c2-144">For more information, see [Using DependsOn](resource-depends-on.md)</span></span>|

## <a name="example"></a><span data-ttu-id="7b5c2-145">範例</span><span class="sxs-lookup"><span data-stu-id="7b5c2-145">Example</span></span>

<span data-ttu-id="7b5c2-146">下列範例會使用 [xExchange](https://github.com/PowerShell/xExchange) 資源來安裝 Microsoft Exchange。</span><span class="sxs-lookup"><span data-stu-id="7b5c2-146">The following example installs Microsoft Exchange using the [xExchange](https://github.com/PowerShell/xExchange) resource.</span></span> <span data-ttu-id="7b5c2-147">在整個安裝過程中，都使用 **PendingReboot** 資源來重新啟動節點。</span><span class="sxs-lookup"><span data-stu-id="7b5c2-147">Throughout the install, the **PendingReboot** resource is used to reboot the Node.</span></span>

> [!NOTE]
> <span data-ttu-id="7b5c2-148">這個範例需要有權將 Exchange 伺服器新增至樹系的帳戶認證。</span><span class="sxs-lookup"><span data-stu-id="7b5c2-148">This example requires the credential of an account that has rights to add an Exchange server to the forest.</span></span> <span data-ttu-id="7b5c2-149">如需在 DSC 中使用認證的詳細資訊，請參閱[處理 DSC 的認證](../configurations/configDataCredentials.md)</span><span class="sxs-lookup"><span data-stu-id="7b5c2-149">For more information on using credentials in DSC, see [Handling Credentials in DSC](../configurations/configDataCredentials.md)</span></span>

```powershell
$ConfigurationData = @{
    AllNodes = @(
        @{
            NodeName                    = '*'
            PSDSCAllowPlainTextPassword = $true
        },
        @{
            NodeName = 'DSCPULL-1'
        }
    )
}

Configuration Example
{
    param
    (
        [Parameter(Mandatory = $true)]
        [System.Management.Automation.PSCredential]
        $ExchangeAdminCredential
    )

    Import-DscResource -Module xExchange
    Import-DscResource -Module ComputerManagementDsc

    Node $AllNodes.NodeName
    {
        # Copy the Exchange setup files locally
        File ExchangeBinaries
        {
            Ensure          = 'Present'
            Type            = 'Directory'
            Recurse         = $true
            SourcePath      = '\\rras-1\Binaries\E15CU6'
            DestinationPath = 'C:\Binaries\E15CU6'
        }

        # Check if a reboot is needed before installing Exchange
        PendingReboot BeforeExchangeInstall
        {
            Name       = 'BeforeExchangeInstall'
            DependsOn  = '[File]ExchangeBinaries'
        }

        # Do the Exchange install
        xExchInstall InstallExchange
        {
            Path       = 'C:\Binaries\E15CU6\Setup.exe'
            Arguments  = '/mode:Install /role:Mailbox /Iacceptexchangeserverlicenseterms'
            Credential = $ExchangeAdminCredential
            DependsOn  = '[PendingReboot]BeforeExchangeInstall'
        }

        # See if a reboot is required after installing Exchange
        PendingReboot AfterExchangeInstall
        {
            Name      = 'AfterExchangeInstall'
            DependsOn = '[xExchInstall]InstallExchange'
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="7b5c2-150">這個範例假設您已設定本機設定管理員允許重新啟動，並在重新啟動後繼續設定。</span><span class="sxs-lookup"><span data-stu-id="7b5c2-150">This example assumes that you have configured your Local Configuration Manager to allow reboots and continue the configuration after a reboot.</span></span>

## <a name="where-to-download"></a><span data-ttu-id="7b5c2-151">下載位置</span><span class="sxs-lookup"><span data-stu-id="7b5c2-151">Where to Download</span></span>

<span data-ttu-id="7b5c2-152">您可在下列位置下載本主題中使用的資源，或使用 PowerShell 資源庫。</span><span class="sxs-lookup"><span data-stu-id="7b5c2-152">You can download the resources used in this topic at the following locations, or by using the PowerShell gallery.</span></span>

- [<span data-ttu-id="7b5c2-153">ComputerManagementDsc</span><span class="sxs-lookup"><span data-stu-id="7b5c2-153">ComputerManagementDsc</span></span>](https://github.com/PowerShell/ComputerManagementDsc)
- [<span data-ttu-id="7b5c2-154">xExchange</span><span class="sxs-lookup"><span data-stu-id="7b5c2-154">xExchange</span></span>](https://github.com/PowerShell/xExchange)
