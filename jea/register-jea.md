---
ms.date: 06/12/2017
keywords: jea,powershell,安全性
title: 登錄 JEA 設定
ms.openlocfilehash: 160aa95283da57a10aad5fdd4043adb1354a5db5
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002901"
---
# <a name="registering-jea-configurations"></a><span data-ttu-id="892bf-103">登錄 JEA 設定</span><span class="sxs-lookup"><span data-stu-id="892bf-103">Registering JEA Configurations</span></span>

> <span data-ttu-id="892bf-104">適用對象：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="892bf-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="892bf-105">在您建立[角色功能](role-capabilities.md)和[工作階段設定檔](session-configurations.md)之後，使用 JEA 前所需進行的最後步驟，便是註冊 JEA 端點。</span><span class="sxs-lookup"><span data-stu-id="892bf-105">Once you have your [role capabilities](role-capabilities.md) and [session configuration file](session-configurations.md) created, the last step before you can use JEA is to register the JEA endpoint.</span></span>
<span data-ttu-id="892bf-106">向系統註冊 JEA 端點，將能使該端點可供使用者和自動化引擎使用。</span><span class="sxs-lookup"><span data-stu-id="892bf-106">Registering the JEA endpoint with the system makes the endpoint available for use by users and automation engines.</span></span>

## <a name="single-machine-configuration"></a><span data-ttu-id="892bf-107">單一電腦設定</span><span class="sxs-lookup"><span data-stu-id="892bf-107">Single machine configuration</span></span>

<span data-ttu-id="892bf-108">針對小型環境，您可以藉由使用 [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration) Cmdlet 登錄工作階段設定檔來部署 JEA。</span><span class="sxs-lookup"><span data-stu-id="892bf-108">For small environments, you can deploy JEA by registering the session configuration file using the [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.</span></span>

<span data-ttu-id="892bf-109">開始之前，請確定符合下列先決條件：</span><span class="sxs-lookup"><span data-stu-id="892bf-109">Before you begin, ensure that the following prerequisites have been met:</span></span>
- <span data-ttu-id="892bf-110">建立一或多個角色並放置在有效 PowerShell 模組的 'RoleCapabilities' 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="892bf-110">One or more roles has been created and placed in the 'RoleCapabilities' folder of a valid PowerShell module.</span></span>
- <span data-ttu-id="892bf-111">建立並測試工作階段設定檔。</span><span class="sxs-lookup"><span data-stu-id="892bf-111">A session configuration file has been created and tested.</span></span>
- <span data-ttu-id="892bf-112">登錄 JEA 設定的使用者在系統上具有系統管理員權限。</span><span class="sxs-lookup"><span data-stu-id="892bf-112">The user registering the JEA configuration has administrator rights on the system(s).</span></span>

<span data-ttu-id="892bf-113">您也必須選取 JEA 端點的名稱。</span><span class="sxs-lookup"><span data-stu-id="892bf-113">You also need to select a name for your JEA endpoint.</span></span>
<span data-ttu-id="892bf-114">當使用者想要使用 JEA 連線到系統時，便會需要 JEA 端點的名稱。</span><span class="sxs-lookup"><span data-stu-id="892bf-114">The name of the JEA endpoint is required when users want to connect to the system using JEA.</span></span>
<span data-ttu-id="892bf-115">您可以使用 [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) Cmdlet 來檢查系統上的現有端點名稱。</span><span class="sxs-lookup"><span data-stu-id="892bf-115">You can use the [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet to check the names of existing endpoints on the system.</span></span>
<span data-ttu-id="892bf-116">開頭為 'microsoft' 的端點通常都與 Windows 一起出貨。</span><span class="sxs-lookup"><span data-stu-id="892bf-116">Endpoints that start with 'microsoft' are typically shipped with Windows.</span></span>
<span data-ttu-id="892bf-117">'microsoft.powershell' 端點是在連線到遠端 PowerShell 端點時使用的預設端點。</span><span class="sxs-lookup"><span data-stu-id="892bf-117">The 'microsoft.powershell' endpoint is the default endpoint used when connecting to a remote PowerShell endpoint.</span></span>

```powershell
PS C:\> Get-PSSessionConfiguration | Select-Object Name

Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

<span data-ttu-id="892bf-118">當您決定好 JEA 端點的適當名稱時，請執行下列命令來登錄端點。</span><span class="sxs-lookup"><span data-stu-id="892bf-118">When you have determined an appropriate name for your JEA endpoint, run the following command to register the endpoint.</span></span>

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="892bf-119">上述命令會重新啟動系統上的 WinRM 服務。</span><span class="sxs-lookup"><span data-stu-id="892bf-119">The above command restarts the WinRM service on the system.</span></span>
> <span data-ttu-id="892bf-120">這會終止所有 PowerShell 遠端工作階段，以及任何進行中的 DSC 設定。</span><span class="sxs-lookup"><span data-stu-id="892bf-120">This terminates all PowerShell remoting sessions as well as any ongoing DSC configurations.</span></span>
> <span data-ttu-id="892bf-121">建議您讓任何實際執行電腦離線，然後才執行命令，以避免中斷營運。</span><span class="sxs-lookup"><span data-stu-id="892bf-121">It is recommended that you take any production machines offline before running the command to avoid disrupting business operations.</span></span>

<span data-ttu-id="892bf-122">如果登錄成功，您便可以[使用 JEA](using-jea.md)。</span><span class="sxs-lookup"><span data-stu-id="892bf-122">If registration is successful, you are ready to [use JEA](using-jea.md).</span></span>
<span data-ttu-id="892bf-123">您可以隨時刪除工作階段設定檔；在註冊之後，便不會再度使用它。</span><span class="sxs-lookup"><span data-stu-id="892bf-123">You may delete the session configuration file at any time; it is not used after registration of the end point.</span></span>

## <a name="multi-machine-configuration-with-dsc"></a><span data-ttu-id="892bf-124">DSC 的多電腦設定</span><span class="sxs-lookup"><span data-stu-id="892bf-124">Multi-machine configuration with DSC</span></span>

<span data-ttu-id="892bf-125">如果您要在多部電腦上部署 JEA，最簡單的部署模型是使用 JEA [期望狀態設定](https://msdn.microsoft.com/powershell/dsc/overview)資源快速且一致地在每部機器上部署 JEA。</span><span class="sxs-lookup"><span data-stu-id="892bf-125">If you are deploying JEA on multiple machines, the simplest deployment model is to use the JEA [Desired State Configuration](https://msdn.microsoft.com/powershell/dsc/overview) resource to quickly and consistently deploy JEA on each machine.</span></span>

<span data-ttu-id="892bf-126">若要搭配 DSC 部署 JEA，您必須確定符合下列先決條件︰</span><span class="sxs-lookup"><span data-stu-id="892bf-126">To deploy JEA with DSC, you need to ensure the following prerequisites are met:</span></span>
- <span data-ttu-id="892bf-127">已撰寫一或多個角色功能並新增至有效的 PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="892bf-127">One or more role capabilities have been authored and added to a valid PowerShell module.</span></span>
- <span data-ttu-id="892bf-128">包含角色的 PowerShell 模組儲存在每一部機器可存取的 (唯讀) 檔案共用上。</span><span class="sxs-lookup"><span data-stu-id="892bf-128">The PowerShell module containing the roles is stored on a (read-only) file share accessible by each machine.</span></span>
- <span data-ttu-id="892bf-129">已確定工作階段設定的設定。</span><span class="sxs-lookup"><span data-stu-id="892bf-129">Settings for the session configuration have been determined.</span></span> <span data-ttu-id="892bf-130">使用 JEA DSC 資源時，您不需要建立工作階段設定檔。</span><span class="sxs-lookup"><span data-stu-id="892bf-130">You do not need to create a session configuration file when using the JEA DSC resource.</span></span>
- <span data-ttu-id="892bf-131">您有可讓您在每部電腦上執行系統管理動作的認證，或是能夠存取用來管理電腦的 DSC 提取伺服器。</span><span class="sxs-lookup"><span data-stu-id="892bf-131">You have credentials that allow you to perform administrative actions on each machine, or have access to a DSC pull server used to manage the machines.</span></span>
- <span data-ttu-id="892bf-132">您已下載 [JEA DSC 資源](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)</span><span class="sxs-lookup"><span data-stu-id="892bf-132">You have downloaded the [JEA DSC resource](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)</span></span>

<span data-ttu-id="892bf-133">在目標電腦 (或提取伺服器上，如果您有使用的話)，建立 JEA 端點的 DSC 設定。</span><span class="sxs-lookup"><span data-stu-id="892bf-133">On a target machine (or pull server, if you are using one), create a DSC configuration for your JEA endpoint.</span></span>
<span data-ttu-id="892bf-134">在此設定中，您會使用 JustEnoughAdministration DSC 資源來設定工作階段設定檔和 File 資源，以便從檔案共用複製角色功能。</span><span class="sxs-lookup"><span data-stu-id="892bf-134">In this configuration, you use the JustEnoughAdministration DSC resource to set up the session configuration file and the File resource to copy over the role capabilities from the file share.</span></span>

<span data-ttu-id="892bf-135">下列屬性可以使用 DSC 資源來設定︰</span><span class="sxs-lookup"><span data-stu-id="892bf-135">The following properties are configurable using the DSC resource:</span></span>
- <span data-ttu-id="892bf-136">角色定義</span><span class="sxs-lookup"><span data-stu-id="892bf-136">Role Definitions</span></span>
- <span data-ttu-id="892bf-137">虛擬帳戶群組</span><span class="sxs-lookup"><span data-stu-id="892bf-137">Virtual Account groups</span></span>
- <span data-ttu-id="892bf-138">群組受管理的服務帳戶名稱</span><span class="sxs-lookup"><span data-stu-id="892bf-138">Group Managed Service Account name</span></span>
- <span data-ttu-id="892bf-139">文字記錄目錄</span><span class="sxs-lookup"><span data-stu-id="892bf-139">Transcript directory</span></span>
- <span data-ttu-id="892bf-140">使用者磁碟機</span><span class="sxs-lookup"><span data-stu-id="892bf-140">User drive</span></span>
- <span data-ttu-id="892bf-141">條件式存取原則</span><span class="sxs-lookup"><span data-stu-id="892bf-141">Conditional access rules</span></span>
- <span data-ttu-id="892bf-142">JEA 工作階段的啟動指令碼</span><span class="sxs-lookup"><span data-stu-id="892bf-142">Startup scripts for the JEA session</span></span>

<span data-ttu-id="892bf-143">DSC 設定中的這些屬性，每個的語法都與 PowerShell 工作階段設定檔一致。</span><span class="sxs-lookup"><span data-stu-id="892bf-143">The syntax for each of these properties in a DSC configuration is consistent with the PowerShell session configuration file.</span></span>

<span data-ttu-id="892bf-144">以下是一般伺服器維護模組的範例 DSC 設定。</span><span class="sxs-lookup"><span data-stu-id="892bf-144">Below is a sample DSC configuration for a general server maintenance module.</span></span>

<span data-ttu-id="892bf-145">它假設在 'RoleCapabilities' 子資料夾中包含角色功能的有效 PowerShell 模組位於 '\\\\我的檔案期用\\JEA' 檔案共用上。</span><span class="sxs-lookup"><span data-stu-id="892bf-145">It assumes that a valid PowerShell module containing role capabilities in a 'RoleCapabilities' subfolder is located on the '\\\\myfileshare\\JEA' file share.</span></span>


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

<span data-ttu-id="892bf-146">這個設定便可以藉由[直接叫用本機設定管理員](https://msdn.microsoft.com/powershell/dsc/metaconfig)或更新[提取伺服器設定](https://msdn.microsoft.com/powershell/dsc/pullserver)，以套用在系統上。</span><span class="sxs-lookup"><span data-stu-id="892bf-146">This configuration can then be applied on a system by [directly invoking the Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig) or updating the [pull server configuration](https://msdn.microsoft.com/powershell/dsc/pullserver).</span></span>

<span data-ttu-id="892bf-147">DSC 資源也可讓您取代預設的 Microsoft.PowerShell 遠端端點。</span><span class="sxs-lookup"><span data-stu-id="892bf-147">The DSC resource also allows you to replace the default Microsoft.PowerShell remoting endpoint.</span></span>
<span data-ttu-id="892bf-148">如果您這麼做，資源會自動登錄名為 "Microsoft.PowerShell.Restricted" 的備份無限制端點，它具有預設 WinRM ACL (允許遠端管理使用者與本機系統管理員群組成員存取它)。</span><span class="sxs-lookup"><span data-stu-id="892bf-148">If you do this, the resource automatically registers a backup unconstrainted endpoint named "Microsoft.PowerShell.Restricted" which has the default WinRM ACL (allowing Remote Management Users and local Administrators group members to access it).</span></span>

## <a name="unregistering-jea-configurations"></a><span data-ttu-id="892bf-149">取消登錄 JEA 設定</span><span class="sxs-lookup"><span data-stu-id="892bf-149">Unregistering JEA configurations</span></span>

<span data-ttu-id="892bf-150">若要移除系統上的 JEA 端點，請使用 [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="892bf-150">To remove a JEA endpoint on a system, use the [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet.</span></span>
<span data-ttu-id="892bf-151">取消登錄 JEA 端點會使新使用者無法在系統上建立新的 JEA 工作階段。</span><span class="sxs-lookup"><span data-stu-id="892bf-151">Unregistering a JEA endpoint prevents new users from creating new JEA sessions on the system.</span></span>
<span data-ttu-id="892bf-152">它也可讓您藉由使用相同的端點名稱重新登錄已更新的工作階段設定檔來更新 JEA 設定。</span><span class="sxs-lookup"><span data-stu-id="892bf-152">It also allows you to update a JEA configuration by re-registering an updated session configuration file using the same endpoint name.</span></span>

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="892bf-153">取消登錄 JEA 端點會導致 WinRM 服務重新啟動。</span><span class="sxs-lookup"><span data-stu-id="892bf-153">Unregistering a JEA endpoint causes the WinRM service to restart.</span></span>
> <span data-ttu-id="892bf-154">這會中斷大部分正在進行中的遠端管理作業，包括其他的 PowerShell 工作階段、WMI 引動過程，以及某些管理工具。</span><span class="sxs-lookup"><span data-stu-id="892bf-154">This interrupts most remote management operations in progress, including other PowerShell sessions, WMI invocations, and some management tools.</span></span>
> <span data-ttu-id="892bf-155">只在計劃的維護期間取消登錄 PowerShell 端點。</span><span class="sxs-lookup"><span data-stu-id="892bf-155">Only unregister PowerShell endpoints during planned maintenance windows.</span></span>

## <a name="next-steps"></a><span data-ttu-id="892bf-156">接下來的步驟</span><span class="sxs-lookup"><span data-stu-id="892bf-156">Next steps</span></span>

- [<span data-ttu-id="892bf-157">測試 JEA 端點</span><span class="sxs-lookup"><span data-stu-id="892bf-157">Test the JEA endpoint</span></span>](using-jea.md)
