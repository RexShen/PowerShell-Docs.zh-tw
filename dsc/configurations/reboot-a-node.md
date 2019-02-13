---
ms.date: 1/17/2019
keywords: dsc,powershell,設定,安裝
title: 重新啟動節點
ms.openlocfilehash: 33ecd98aa62c3dc94a8ff2213fd3e68bf0c05cb7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55676833"
---
# <a name="reboot-a-node"></a><span data-ttu-id="10b75-103">重新啟動節點</span><span class="sxs-lookup"><span data-stu-id="10b75-103">Reboot a Node</span></span>

> [!NOTE]
> <span data-ttu-id="10b75-104">本主題討論如何重新啟動節點。</span><span class="sxs-lookup"><span data-stu-id="10b75-104">This topic talks about how to reboot a Node.</span></span> <span data-ttu-id="10b75-105">為了讓重新開機，才能成功**ActionAfterReboot**並**RebootNodeIfNeeded**必須正確設定的 LCM 設定。</span><span class="sxs-lookup"><span data-stu-id="10b75-105">In order for the reboot to be successful the **ActionAfterReboot** and **RebootNodeIfNeeded** LCM settings need to be configured properly.</span></span>
> <span data-ttu-id="10b75-106">若要深入了解本機設定管理員設定，請參閱[設定本機設定管理員](../managing-nodes/metaConfig.md)，或[設定本機設定管理員 (v4)](../managing-nodes/metaConfig4.md)。</span><span class="sxs-lookup"><span data-stu-id="10b75-106">To read about Local Configuration Manager settings, see [Configure the Local Configuration Manager](../managing-nodes/metaConfig.md), or [Configure the Local Configuration Manager (v4)](../managing-nodes/metaConfig4.md).</span></span>

<span data-ttu-id="10b75-107">節點可重新啟動從資源中，使用`$global:DSCMachineStatus`旗標。</span><span class="sxs-lookup"><span data-stu-id="10b75-107">Nodes can be rebooted from within a resource, by using the `$global:DSCMachineStatus` flag.</span></span> <span data-ttu-id="10b75-108">若要設定這個旗標`1`中`Set-TargetResource`函式會強制重新啟動之後直接的節點 LCM**設定**方法目前的資源。</span><span class="sxs-lookup"><span data-stu-id="10b75-108">Setting this flag to `1` in the `Set-TargetResource` function forces the LCM to reboot the Node directly after the **Set** method of the current resource.</span></span> <span data-ttu-id="10b75-109">使用此旗標， **xPendingReboot**重新開機是否擱置中偵測到的資源之外 DSC。</span><span class="sxs-lookup"><span data-stu-id="10b75-109">Using this flag, the **xPendingReboot** resource detects if a reboot is pending outside of DSC.</span></span>

<span data-ttu-id="10b75-110">您[組態](configurations.md)可能會執行需要重新啟動節點的步驟。</span><span class="sxs-lookup"><span data-stu-id="10b75-110">Your [configurations](configurations.md) may perform steps that require the Node to reboot.</span></span> <span data-ttu-id="10b75-111">例如，這可能包括項目：</span><span class="sxs-lookup"><span data-stu-id="10b75-111">This could include things such as:</span></span>

- <span data-ttu-id="10b75-112">Windows: 更新</span><span class="sxs-lookup"><span data-stu-id="10b75-112">Windows updates</span></span>
- <span data-ttu-id="10b75-113">軟體安裝</span><span class="sxs-lookup"><span data-stu-id="10b75-113">Software install</span></span>
- <span data-ttu-id="10b75-114">檔案重新命名</span><span class="sxs-lookup"><span data-stu-id="10b75-114">File renames</span></span>
- <span data-ttu-id="10b75-115">電腦重新命名</span><span class="sxs-lookup"><span data-stu-id="10b75-115">Computer rename</span></span>

<span data-ttu-id="10b75-116">**XPendingReboot**資源檢查特定電腦的位置，以判斷是否暫止重新開機。</span><span class="sxs-lookup"><span data-stu-id="10b75-116">The **xPendingReboot** resource checks specific computer locations to determine if a reboot is pending.</span></span> <span data-ttu-id="10b75-117">如果節點要求 DSC，之外重新開機**xPendingReboot**的資源集`$global:DSCMachineStatus`旗標設為`1`強制重新開機，並解決問題的暫止。</span><span class="sxs-lookup"><span data-stu-id="10b75-117">If the Node requires a reboot outside of DSC, the **xPendingReboot** resource sets the `$global:DSCMachineStatus` flag to `1` forcing a reboot and resolving the pending condition.</span></span>

> [!NOTE]
> <span data-ttu-id="10b75-118">任何 DSC 資源可以指示來設定這個旗標，重新啟動節點 LCM`Set-TargetResource`函式。</span><span class="sxs-lookup"><span data-stu-id="10b75-118">Any DSC resource can instruct the LCM to reboot the node by setting this flag in the `Set-TargetResource` function.</span></span> <span data-ttu-id="10b75-119">如需詳細資訊，請參閱 <<c0> [ 撰寫自訂 DSC 資源與 MOF](../resources/authoringResourceMOF.md)。</span><span class="sxs-lookup"><span data-stu-id="10b75-119">For more information, see [Writing a custom DSC resource with MOF](../resources/authoringResourceMOF.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="10b75-120">語法</span><span class="sxs-lookup"><span data-stu-id="10b75-120">Syntax</span></span>

```
xPendingReboot [String] #ResourceName
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

## <a name="properties"></a><span data-ttu-id="10b75-121">Properties</span><span class="sxs-lookup"><span data-stu-id="10b75-121">Properties</span></span>

| <span data-ttu-id="10b75-122">屬性</span><span class="sxs-lookup"><span data-stu-id="10b75-122">Property</span></span> | <span data-ttu-id="10b75-123">描述</span><span class="sxs-lookup"><span data-stu-id="10b75-123">Description</span></span> |
| --- | --- |
| <span data-ttu-id="10b75-124">名稱</span><span class="sxs-lookup"><span data-stu-id="10b75-124">Name</span></span>| <span data-ttu-id="10b75-125">必須是唯一的每個執行個體設定中之資源的必要的參數。</span><span class="sxs-lookup"><span data-stu-id="10b75-125">Required parameter that must be unique per instance of the resource within a configuration.</span></span>|
| <span data-ttu-id="10b75-126">SkipComponentBasedServicing</span><span class="sxs-lookup"><span data-stu-id="10b75-126">SkipComponentBasedServicing</span></span> | <span data-ttu-id="10b75-127">元件為基礎的服務元件所觸發的略過重新開機。</span><span class="sxs-lookup"><span data-stu-id="10b75-127">Skip reboots triggered by the Component-Based Servicing component.</span></span> |
| <span data-ttu-id="10b75-128">SkipWindowsUpdate</span><span class="sxs-lookup"><span data-stu-id="10b75-128">SkipWindowsUpdate</span></span> | <span data-ttu-id="10b75-129">由 Windows Update 所觸發的略過重新開機。</span><span class="sxs-lookup"><span data-stu-id="10b75-129">Skip reboots triggered by Windows Update.</span></span>|
| <span data-ttu-id="10b75-130">SkipPendingFileRename</span><span class="sxs-lookup"><span data-stu-id="10b75-130">SkipPendingFileRename</span></span> | <span data-ttu-id="10b75-131">略過暫止檔案重新命名重新開機。</span><span class="sxs-lookup"><span data-stu-id="10b75-131">Skip pending file rename reboots.</span></span> |
| <span data-ttu-id="10b75-132">SkipCcmClientSDK</span><span class="sxs-lookup"><span data-stu-id="10b75-132">SkipCcmClientSDK</span></span> | <span data-ttu-id="10b75-133">由 ConfigMgr 用戶端所觸發的略過重新開機。</span><span class="sxs-lookup"><span data-stu-id="10b75-133">Skip reboots triggered by the ConfigMgr client.</span></span> |
| <span data-ttu-id="10b75-134">SkipComputerRename</span><span class="sxs-lookup"><span data-stu-id="10b75-134">SkipComputerRename</span></span> | <span data-ttu-id="10b75-135">略過重新觸發開機的電腦重新命名。</span><span class="sxs-lookup"><span data-stu-id="10b75-135">Skip reboots triggerd by Computer renames.</span></span> |
| <span data-ttu-id="10b75-136">PSDSCRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="10b75-136">PSDSCRunAsCredential</span></span> | <span data-ttu-id="10b75-137">支援 v5。</span><span class="sxs-lookup"><span data-stu-id="10b75-137">Supported in v5.</span></span> <span data-ttu-id="10b75-138">指定的使用者身分執行的資源。</span><span class="sxs-lookup"><span data-stu-id="10b75-138">Executes the resource as the specified user.</span></span> |
| <span data-ttu-id="10b75-139">DependsOn</span><span class="sxs-lookup"><span data-stu-id="10b75-139">DependsOn</span></span> | <span data-ttu-id="10b75-140">表示必須先執行另一個資源的設定，再設定這個資源。</span><span class="sxs-lookup"><span data-stu-id="10b75-140">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="10b75-141">例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 **ResourceName**，而它的類型是 **ResourceType**，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="10b75-141">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> <span data-ttu-id="10b75-142">如需詳細資訊，請參閱[使用 DependsOn](resource-depends-on.md)</span><span class="sxs-lookup"><span data-stu-id="10b75-142">For more information, see [Using DependsOn](resource-depends-on.md)</span></span>|

## <a name="example"></a><span data-ttu-id="10b75-143">範例</span><span class="sxs-lookup"><span data-stu-id="10b75-143">Example</span></span>

<span data-ttu-id="10b75-144">下列範例會安裝使用 Microsoft Exchange [xExchange](https://github.com/PowerShell/xExchange)資源。</span><span class="sxs-lookup"><span data-stu-id="10b75-144">The following example installs Microsoft Exchange using the [xExchange](https://github.com/PowerShell/xExchange) resource.</span></span>
<span data-ttu-id="10b75-145">在安裝中，整個**xPendingReboot**資源用來重新啟動節點。</span><span class="sxs-lookup"><span data-stu-id="10b75-145">Throughout the install, the **xPendingReboot** resource is used to reboot the Node.</span></span>

> [!NOTE]
> <span data-ttu-id="10b75-146">這個範例需要可將 Exchange server 新增至樹系的權限的帳戶的認證。</span><span class="sxs-lookup"><span data-stu-id="10b75-146">This example requires the credential of an account that has rights to add an Exchange server to the forest.</span></span> <span data-ttu-id="10b75-147">如需有關如何在 DSC 中使用認證的詳細資訊，請參閱[處理 DSC 的認證](../configurations/configDataCredentials.md)</span><span class="sxs-lookup"><span data-stu-id="10b75-147">For more information on using credentials in DSC, see [Handling Credentials in DSC](../configurations/configDataCredentials.md)</span></span>

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
    Import-DscResource -Module xPendingReboot

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
        xPendingReboot BeforeExchangeInstall
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
            DependsOn  = '[xPendingReboot]BeforeExchangeInstall'
        }

        # See if a reboot is required after installing Exchange
        xPendingReboot AfterExchangeInstall
        {
            Name      = 'AfterExchangeInstall'
            DependsOn = '[xExchInstall]InstallExchange'
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="10b75-148">這個範例假設您已設定您的本機設定管理員，來允許重新開機，並繼續在重新開機後的設定。</span><span class="sxs-lookup"><span data-stu-id="10b75-148">This example assumes that you have configured your Local Configuration Manager to allow reboots and continue the configuration after a reboot.</span></span>

## <a name="where-to-download"></a><span data-ttu-id="10b75-149">若要下載的位置</span><span class="sxs-lookup"><span data-stu-id="10b75-149">Where to Download</span></span>

<span data-ttu-id="10b75-150">您可以下載本主題的下列位置，或使用 「 PowerShell 資源庫中使用的資源。</span><span class="sxs-lookup"><span data-stu-id="10b75-150">You can download the resources used in this topic at the following locations, or by using the PowerShell gallery.</span></span>

- [<span data-ttu-id="10b75-151">xPendingReboot</span><span class="sxs-lookup"><span data-stu-id="10b75-151">xPendingReboot</span></span>](https://github.com/PowerShell/xPendingReboot)
- [<span data-ttu-id="10b75-152">xExchange</span><span class="sxs-lookup"><span data-stu-id="10b75-152">xExchange</span></span>](https://github.com/PowerShell/xExchange)
