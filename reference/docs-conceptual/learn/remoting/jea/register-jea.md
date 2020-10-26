---
ms.date: 07/10/2019
keywords: jea,powershell,安全性
title: 登錄 JEA 設定
description: 向系統註冊 JEA 端點，將能使該端點可供使用者和自動化引擎使用。
ms.openlocfilehash: 6e7f8cdc1e7a666bddaa42034d70fcbcf55c1972
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2020
ms.locfileid: "92499904"
---
# <a name="registering-jea-configurations"></a><span data-ttu-id="0fca8-104">登錄 JEA 設定</span><span class="sxs-lookup"><span data-stu-id="0fca8-104">Registering JEA Configurations</span></span>

<span data-ttu-id="0fca8-105">在您建立[角色功能](role-capabilities.md)和[工作階段設定檔](session-configurations.md)之後，最後一個步驟即是登錄 JEA 端點。</span><span class="sxs-lookup"><span data-stu-id="0fca8-105">Once you have your [role capabilities](role-capabilities.md) and [session configuration file](session-configurations.md) created, the last step is to register the JEA endpoint.</span></span> <span data-ttu-id="0fca8-106">向系統註冊 JEA 端點，將能使該端點可供使用者和自動化引擎使用。</span><span class="sxs-lookup"><span data-stu-id="0fca8-106">Registering the JEA endpoint with the system makes the endpoint available for use by users and automation engines.</span></span>

## <a name="single-machine-configuration"></a><span data-ttu-id="0fca8-107">單一電腦設定</span><span class="sxs-lookup"><span data-stu-id="0fca8-107">Single machine configuration</span></span>

<span data-ttu-id="0fca8-108">針對小型環境，您可以藉由使用 [Register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration) Cmdlet 登錄工作階段設定檔來部署 JEA。</span><span class="sxs-lookup"><span data-stu-id="0fca8-108">For small environments, you can deploy JEA by registering the session configuration file using the [Register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.</span></span>

<span data-ttu-id="0fca8-109">開始之前，請確定符合下列先決條件：</span><span class="sxs-lookup"><span data-stu-id="0fca8-109">Before you begin, ensure that the following prerequisites have been met:</span></span>

- <span data-ttu-id="0fca8-110">已建立一或多個角色並放置在 PowerShell 模組的 **RoleCapabilities** 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="0fca8-110">One or more roles has been created and placed in the **RoleCapabilities** folder of a PowerShell module.</span></span>
- <span data-ttu-id="0fca8-111">建立並測試工作階段設定檔。</span><span class="sxs-lookup"><span data-stu-id="0fca8-111">A session configuration file has been created and tested.</span></span>
- <span data-ttu-id="0fca8-112">登錄 JEA 設定的使用者在系統上具有系統管理員權限。</span><span class="sxs-lookup"><span data-stu-id="0fca8-112">The user registering the JEA configuration has administrator rights on the system.</span></span>
- <span data-ttu-id="0fca8-113">您已選取您的 JEA 端點名稱。</span><span class="sxs-lookup"><span data-stu-id="0fca8-113">You've selected a name for your JEA endpoint.</span></span>

<span data-ttu-id="0fca8-114">當使用者使用 JEA 連線到系統時，便會需要 JEA 端點的名稱。</span><span class="sxs-lookup"><span data-stu-id="0fca8-114">The name of the JEA endpoint is required when users connect to the system using JEA.</span></span> <span data-ttu-id="0fca8-115">[Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) Cmdlet 會列出系統上的端點名稱。</span><span class="sxs-lookup"><span data-stu-id="0fca8-115">The [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet lists the names of the endpoints on a system.</span></span> <span data-ttu-id="0fca8-116">開頭為 `microsoft` 的端點通常隨附於 Windows。</span><span class="sxs-lookup"><span data-stu-id="0fca8-116">Endpoints that start with `microsoft` are typically shipped with Windows.</span></span> <span data-ttu-id="0fca8-117">`microsoft.powershell` 端點是在連線到遠端 PowerShell 端點時使用的預設端點。</span><span class="sxs-lookup"><span data-stu-id="0fca8-117">The `microsoft.powershell` endpoint is the default endpoint used when connecting to a remote PowerShell endpoint.</span></span>

```powershell
Get-PSSessionConfiguration | Select-Object Name
```

```Output
Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

<span data-ttu-id="0fca8-118">執行下列命令以登錄端點。</span><span class="sxs-lookup"><span data-stu-id="0fca8-118">Run the following command to register the endpoint.</span></span>

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="0fca8-119">上一個命令會重新啟動系統上的 WinRM 服務。</span><span class="sxs-lookup"><span data-stu-id="0fca8-119">The previous command restarts the WinRM service on the system.</span></span> <span data-ttu-id="0fca8-120">這會終止所有 PowerShell 遠端工作階段，以及任何正在進行的 DSC 設定。</span><span class="sxs-lookup"><span data-stu-id="0fca8-120">This terminates all PowerShell remoting sessions and any ongoing DSC configurations.</span></span> <span data-ttu-id="0fca8-121">建議您先將實際執行電腦離線再執行命令，以免中斷營運。</span><span class="sxs-lookup"><span data-stu-id="0fca8-121">We recommended you take production machines offline before running the command to avoid disrupting business operations.</span></span>

<span data-ttu-id="0fca8-122">登錄之後，即可[使用 JEA](using-jea.md)。</span><span class="sxs-lookup"><span data-stu-id="0fca8-122">After registration, you're ready to [use JEA](using-jea.md).</span></span> <span data-ttu-id="0fca8-123">您可以隨時刪除工作階段設定檔。</span><span class="sxs-lookup"><span data-stu-id="0fca8-123">You may delete the session configuration file at any time.</span></span> <span data-ttu-id="0fca8-124">端點登錄後即不再使用設定檔。</span><span class="sxs-lookup"><span data-stu-id="0fca8-124">The configuration file isn't used after registration of the endpoint.</span></span>

## <a name="multi-machine-configuration-with-dsc"></a><span data-ttu-id="0fca8-125">DSC 的多電腦設定</span><span class="sxs-lookup"><span data-stu-id="0fca8-125">Multi-machine configuration with DSC</span></span>

<span data-ttu-id="0fca8-126">在多部電腦上部署 JEA 時，最簡單的部署模型是使用 JEA [Desired State Configuration (DSC)](../../../dsc/overview/overview.md) 資源快速且一致地在每部機器上部署 JEA。</span><span class="sxs-lookup"><span data-stu-id="0fca8-126">When deploying JEA on multiple machines, the simplest deployment model uses the JEA [Desired State Configuration (DSC)](../../../dsc/overview/overview.md) resource to quickly and consistently deploy JEA on each machine.</span></span>

<span data-ttu-id="0fca8-127">若要搭配 DSC 部署 JEA，請務必符合下列先決條件︰</span><span class="sxs-lookup"><span data-stu-id="0fca8-127">To deploy JEA with DSC, ensure the following prerequisites are met:</span></span>

- <span data-ttu-id="0fca8-128">已撰寫一或多個角色功能並新增至 PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="0fca8-128">One or more role capabilities have been authored and added to a PowerShell module.</span></span>
- <span data-ttu-id="0fca8-129">包含角色的 PowerShell 模組儲存在每一部機器可存取的 (唯讀) 檔案共用上。</span><span class="sxs-lookup"><span data-stu-id="0fca8-129">The PowerShell module containing the roles is stored on a (read-only) file share accessible by each machine.</span></span>
- <span data-ttu-id="0fca8-130">已確定工作階段設定的設定。</span><span class="sxs-lookup"><span data-stu-id="0fca8-130">Settings for the session configuration have been determined.</span></span> <span data-ttu-id="0fca8-131">使用 JEA DSC 資源時，您不需要建立工作階段設定檔。</span><span class="sxs-lookup"><span data-stu-id="0fca8-131">You don't need to create a session configuration file when using the JEA DSC resource.</span></span>
- <span data-ttu-id="0fca8-132">您的認證可在每部電腦上執行系統管理動作，或存取用來管理電腦的 DSC 提取伺服器。</span><span class="sxs-lookup"><span data-stu-id="0fca8-132">You have credentials that allow administrative actions on each machine or access to the DSC pull server used to manage the machines.</span></span>
- <span data-ttu-id="0fca8-133">您已下載 [JEA DSC 資源](https://github.com/powershell/JEA/tree/master/DSC%20Resource)。</span><span class="sxs-lookup"><span data-stu-id="0fca8-133">You've downloaded the [JEA DSC resource](https://github.com/powershell/JEA/tree/master/DSC%20Resource).</span></span>

<span data-ttu-id="0fca8-134">在目標電腦或提取伺服器上建立 JEA 端點的 DSC 設定。</span><span class="sxs-lookup"><span data-stu-id="0fca8-134">Create a DSC configuration for your JEA endpoint on a target machine or pull server.</span></span> <span data-ttu-id="0fca8-135">在此設定中， **JustEnoughAdministration** DSC 資源會定義工作階段設定檔，而 **File** 資源則會從檔案共用複製角色功能。</span><span class="sxs-lookup"><span data-stu-id="0fca8-135">In this configuration, the **JustEnoughAdministration** DSC resource defines the session configuration file and the **File** resource copies the role capabilities from the file share.</span></span>

<span data-ttu-id="0fca8-136">下列屬性可以使用 DSC 資源來設定︰</span><span class="sxs-lookup"><span data-stu-id="0fca8-136">The following properties are configurable using the DSC resource:</span></span>

- <span data-ttu-id="0fca8-137">角色定義</span><span class="sxs-lookup"><span data-stu-id="0fca8-137">Role Definitions</span></span>
- <span data-ttu-id="0fca8-138">虛擬帳戶群組</span><span class="sxs-lookup"><span data-stu-id="0fca8-138">Virtual account groups</span></span>
- <span data-ttu-id="0fca8-139">群組受控服務帳戶名稱</span><span class="sxs-lookup"><span data-stu-id="0fca8-139">Group-managed service account name</span></span>
- <span data-ttu-id="0fca8-140">文字記錄目錄</span><span class="sxs-lookup"><span data-stu-id="0fca8-140">Transcript directory</span></span>
- <span data-ttu-id="0fca8-141">使用者磁碟機</span><span class="sxs-lookup"><span data-stu-id="0fca8-141">User drive</span></span>
- <span data-ttu-id="0fca8-142">條件式存取原則</span><span class="sxs-lookup"><span data-stu-id="0fca8-142">Conditional access rules</span></span>
- <span data-ttu-id="0fca8-143">JEA 工作階段的啟動指令碼</span><span class="sxs-lookup"><span data-stu-id="0fca8-143">Startup scripts for the JEA session</span></span>

<span data-ttu-id="0fca8-144">DSC 設定中的這些屬性，每個的語法都與 PowerShell 工作階段設定檔一致。</span><span class="sxs-lookup"><span data-stu-id="0fca8-144">The syntax for each of these properties in a DSC configuration is consistent with the PowerShell session configuration file.</span></span>

<span data-ttu-id="0fca8-145">以下是一般伺服器維護模組的範例 DSC 設定。</span><span class="sxs-lookup"><span data-stu-id="0fca8-145">Below is a sample DSC configuration for a general server maintenance module.</span></span> <span data-ttu-id="0fca8-146">假設包含角色功能的有效 PowerShell 模組位於 `\\myfileshare\JEA` 檔案共用上。</span><span class="sxs-lookup"><span data-stu-id="0fca8-146">It assumes that a valid PowerShell module containing role capabilities is located on the `\\myfileshare\JEA` file share.</span></span>

```powershell
Configuration JEAMaintenance
{
    Import-DscResource -Module JustEnoughAdministration, PSDesiredStateConfiguration

    File MaintenanceModule
    {
        SourcePath = "\\myfileshare\JEA\ContosoMaintenance"
        DestinationPath = "C:\Program Files\WindowsPowerShell\Modules\ContosoMaintenance"
        Checksum = "SHA-256"
        Ensure = "Present"
        Type = "Directory"
        Recurse = $true
    }

    JeaEndpoint JEAMaintenanceEndpoint
    {
        EndpointName = "JEAMaintenance"
        RoleDefinitions = "@{ 'CONTOSO\JEAMaintenanceAuditors' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit' }; 'CONTOSO\JEAMaintenanceAdmins' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit', 'GeneralServerMaintenance-Admin' } }"
        TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
        DependsOn = '[File]MaintenanceModule'
    }
}
```

<span data-ttu-id="0fca8-147">接著，這個設定便可透過直接叫用[本機設定管理員](/powershell/scripting/dsc/managing-nodes/metaConfig)或更新[提取伺服器設定](/powershell/scripting/dsc/pull-server/pullServer)來套用在系統上。</span><span class="sxs-lookup"><span data-stu-id="0fca8-147">Next, the configuration is applied on a system by directly invoking the [Local Configuration Manager](/powershell/scripting/dsc/managing-nodes/metaConfig) or updating the [pull server configuration](/powershell/scripting/dsc/pull-server/pullServer).</span></span>

<span data-ttu-id="0fca8-148">DSC 資源也可讓您取代預設的 **Microsoft.PowerShell** 端點。</span><span class="sxs-lookup"><span data-stu-id="0fca8-148">The DSC resource also allows you to replace the default **Microsoft.PowerShell** endpoint.</span></span> <span data-ttu-id="0fca8-149">取代後，此資源會自動登錄名為 **Microsoft.PowerShell.Restricted** 的備份端點。</span><span class="sxs-lookup"><span data-stu-id="0fca8-149">When replaced, the resource automatically registers a backup endpoint named **Microsoft.PowerShell.Restricted** .</span></span> <span data-ttu-id="0fca8-150">備份端點都具有預設的 WinRM ACL，允許 Remote Management Users 與本機 Administrators 群組成員存取它。</span><span class="sxs-lookup"><span data-stu-id="0fca8-150">The backup endpoint has the default WinRM ACL that allows Remote Management Users and local Administrators group members to access it.</span></span>

## <a name="unregistering-jea-configurations"></a><span data-ttu-id="0fca8-151">取消登錄 JEA 設定</span><span class="sxs-lookup"><span data-stu-id="0fca8-151">Unregistering JEA configurations</span></span>

<span data-ttu-id="0fca8-152">[Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) Cmdlet 會移除 JEA 端點。</span><span class="sxs-lookup"><span data-stu-id="0fca8-152">The [Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet removes a JEA endpoint.</span></span> <span data-ttu-id="0fca8-153">取消登錄 JEA 端點會使新使用者無法在系統上建立新的 JEA 工作階段。</span><span class="sxs-lookup"><span data-stu-id="0fca8-153">Unregistering a JEA endpoint prevents new users from creating new JEA sessions on the system.</span></span> <span data-ttu-id="0fca8-154">它也可讓您藉由使用相同的端點名稱重新登錄已更新的工作階段設定檔來更新 JEA 設定。</span><span class="sxs-lookup"><span data-stu-id="0fca8-154">It also allows you to update a JEA configuration by re-registering an updated session configuration file using the same endpoint name.</span></span>

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="0fca8-155">取消登錄 JEA 端點會導致 WinRM 服務重新啟動。</span><span class="sxs-lookup"><span data-stu-id="0fca8-155">Unregistering a JEA endpoint causes the WinRM service to restart.</span></span> <span data-ttu-id="0fca8-156">這會中斷大部分正在進行中的遠端管理作業，包括其他的 PowerShell 工作階段、WMI 引動過程，以及某些管理工具。</span><span class="sxs-lookup"><span data-stu-id="0fca8-156">This interrupts most remote management operations in progress, including other PowerShell sessions, WMI invocations, and some management tools.</span></span> <span data-ttu-id="0fca8-157">只在計劃的維護期間取消登錄 PowerShell 端點。</span><span class="sxs-lookup"><span data-stu-id="0fca8-157">Only unregister PowerShell endpoints during planned maintenance windows.</span></span>

## <a name="next-steps"></a><span data-ttu-id="0fca8-158">下一步</span><span class="sxs-lookup"><span data-stu-id="0fca8-158">Next steps</span></span>

[<span data-ttu-id="0fca8-159">測試 JEA 端點</span><span class="sxs-lookup"><span data-stu-id="0fca8-159">Test the JEA endpoint</span></span>](using-jea.md)
