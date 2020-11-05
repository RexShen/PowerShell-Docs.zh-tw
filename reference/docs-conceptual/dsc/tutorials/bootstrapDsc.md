---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 使用 DSC 在初始開機時設定虛擬機器
description: 此文章說明如何使用 DSC 在初始開機時設定虛擬機器
ms.openlocfilehash: 9fa8c4a21486aaef87e1c0a3097e5983a378d98d
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656197"
---
# <a name="configure-a-virtual-machines-at-initial-boot-up-by-using-dsc"></a><span data-ttu-id="66a7a-104">使用 DSC 在初始開機時設定虛擬機器</span><span class="sxs-lookup"><span data-stu-id="66a7a-104">Configure a virtual machines at initial boot-up by using DSC</span></span>

> [!IMPORTANT]
> <span data-ttu-id="66a7a-105">適用於：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="66a7a-105">Applies To: Windows PowerShell 5.0</span></span>

## <a name="requirements"></a><span data-ttu-id="66a7a-106">規格需求</span><span class="sxs-lookup"><span data-stu-id="66a7a-106">Requirements</span></span>

> [!NOTE]
> <span data-ttu-id="66a7a-107">本主題所述的 **DSCAutomationHostEnabled** 登錄機碼無法在 PowerShell 4.0 中使用。</span><span class="sxs-lookup"><span data-stu-id="66a7a-107">The **DSCAutomationHostEnabled** registry key described in this topic is not available in PowerShell 4.0.</span></span> <span data-ttu-id="66a7a-108">如需如何在 PowerShell 4.0 初始開機時設定新的虛擬機器，請參閱 [Want to Automatically Configure Your Machines Using DSC at Initial Boot-up?](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/) (想要使用 DSC 在初始開機時自動設定您的電腦嗎？)</span><span class="sxs-lookup"><span data-stu-id="66a7a-108">For information on how to configure new virtual machines at initial boot-up in PowerShell 4.0, see [Want to Automatically Configure Your Machines Using DSC at Initial Boot-up?](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)</span></span>

<span data-ttu-id="66a7a-109">若要執行這些範例，您需要︰</span><span class="sxs-lookup"><span data-stu-id="66a7a-109">To run these examples, you will need:</span></span>

- <span data-ttu-id="66a7a-110">可開機使用的 VHD。</span><span class="sxs-lookup"><span data-stu-id="66a7a-110">A bootable VHD to work with.</span></span> <span data-ttu-id="66a7a-111">您可以從 [TechNet 評估中心](https://www.microsoft.com/evalcenter/evaluate-windows-server-2016)下載評估版 Windows Server 2016 的 ISO。</span><span class="sxs-lookup"><span data-stu-id="66a7a-111">You can download an ISO with an evaluation copy of Windows Server 2016 at [TechNet Evaluation Center](https://www.microsoft.com/evalcenter/evaluate-windows-server-2016).</span></span>
  <span data-ttu-id="66a7a-112">您可以在 [Creating Bootable Virtual Hard Disks](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10)) (建立可開機的虛擬硬碟) 中尋找如何從 ISO 建立 VHD 的指示。</span><span class="sxs-lookup"><span data-stu-id="66a7a-112">You can find instructions on how to create a VHD from an ISO image at [Creating Bootable Virtual Hard Disks](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10)).</span></span>
- <span data-ttu-id="66a7a-113">已啟用 HYPER-V 的主機電腦。</span><span class="sxs-lookup"><span data-stu-id="66a7a-113">A host computer that has Hyper-V enabled.</span></span> <span data-ttu-id="66a7a-114">如需資訊，請參閱 [HYPER-V 概觀](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11))。</span><span class="sxs-lookup"><span data-stu-id="66a7a-114">For information, see [Hyper-V overview](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11)).</span></span>

  <span data-ttu-id="66a7a-115">藉由使用 DSC，您可以在初始開機時自動安裝軟體及設定電腦。</span><span class="sxs-lookup"><span data-stu-id="66a7a-115">By using DSC, you can automate software installation and configuration for a computer at initial boot-up.</span></span> <span data-ttu-id="66a7a-116">您可以將設定 MOF 文件或 metaconfiguration 插入可開機的媒體 (例如 VHD)，於初始開機程序期間加以執行。</span><span class="sxs-lookup"><span data-stu-id="66a7a-116">You do this by either injecting a configuration MOF document or a metaconfiguration into bootable media (such as a VHD) so that they are run during the initial boot-up process.</span></span> <span data-ttu-id="66a7a-117">此行為是由 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System` 下方的 [DSCAutomationHostEnabled 登錄機碼](DSCAutomationHostEnabled.md) 登錄機碼所設定的。</span><span class="sxs-lookup"><span data-stu-id="66a7a-117">This behavior is specified by the [DSCAutomationHostEnabled registry key](DSCAutomationHostEnabled.md) registry key under `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`.</span></span>
  <span data-ttu-id="66a7a-118">此機碼的值預設為 2，表示允許 DSC 在開機時執行。</span><span class="sxs-lookup"><span data-stu-id="66a7a-118">By default, the value of this key is 2, which allows DSC to run at boot time.</span></span>

  <span data-ttu-id="66a7a-119">若您不想在開機時執行 DSC，請將 [DSCAutomationHostEnabled 登錄機碼](DSCAutomationHostEnabled.md) 登錄機碼設為 0。</span><span class="sxs-lookup"><span data-stu-id="66a7a-119">If you do not want DSC to run at boot time, set the value of the [DSCAutomationHostEnabled registry key](DSCAutomationHostEnabled.md) registry key to 0.</span></span>

- <span data-ttu-id="66a7a-120">將設定 MOF 文件插入 VHD</span><span class="sxs-lookup"><span data-stu-id="66a7a-120">Inject a configuration MOF document into a VHD</span></span>
- <span data-ttu-id="66a7a-121">將 DSC metaconfiguration 插入 VHD</span><span class="sxs-lookup"><span data-stu-id="66a7a-121">Inject a DSC metaconfiguration into a VHD</span></span>
- <span data-ttu-id="66a7a-122">開機時停用 DSC</span><span class="sxs-lookup"><span data-stu-id="66a7a-122">Disable DSC at boot time</span></span>

> [!NOTE]
> <span data-ttu-id="66a7a-123">您可以同時將 `Pending.mof` 和 `MetaConfig.mof` 插入到同一部電腦。</span><span class="sxs-lookup"><span data-stu-id="66a7a-123">You can inject both `Pending.mof` and `MetaConfig.mof` into a computer at the same time.</span></span>
> <span data-ttu-id="66a7a-124">當這兩個檔案同時存在時，`MetaConfig.mof` 中所指定的設定會優先執行。</span><span class="sxs-lookup"><span data-stu-id="66a7a-124">If both files are present, the settings specified in `MetaConfig.mof` take precedence.</span></span>

## <a name="inject-a-configuration-mof-document-into-a-vhd"></a><span data-ttu-id="66a7a-125">將設定 MOF 文件插入 VHD</span><span class="sxs-lookup"><span data-stu-id="66a7a-125">Inject a configuration MOF document into a VHD</span></span>

<span data-ttu-id="66a7a-126">若要制定初始開機時的組態，可以將預先編譯的設定 MOF 文件用為 `Pending.mof` 檔案插入 VHD。</span><span class="sxs-lookup"><span data-stu-id="66a7a-126">To enact a configuration at initial boot-up, you can inject a compiled configuration MOF document into the VHD as its `Pending.mof` file.</span></span> <span data-ttu-id="66a7a-127">若 **DSCAutomationHostEnabled** 登錄機碼設定為 2 (預設值)，當電腦第一次開機時，DSC 會套用 `Pending.mof` 所定義的組態。</span><span class="sxs-lookup"><span data-stu-id="66a7a-127">If the **DSCAutomationHostEnabled** registry key is set to 2 (the default value), DSC will apply the configuration defined by `Pending.mof` when the computer boots up for the first time.</span></span>

<span data-ttu-id="66a7a-128">此範例中，我們會使用下列組態在新的電腦上安裝 IIS：</span><span class="sxs-lookup"><span data-stu-id="66a7a-128">For this example, we will use the following configuration, which will install IIS on the new computer:</span></span>

```powershell
Configuration SampleIISInstall
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    node ('localhost')
    {
        WindowsFeature IIS
        {
            Ensure = 'Present'
            Name   = 'Web-Server'
        }
    }
}
```

### <a name="to-inject-the-configuration-mof-document-on-the-vhd"></a><span data-ttu-id="66a7a-129">將設定 MOF 文件插入 VHD</span><span class="sxs-lookup"><span data-stu-id="66a7a-129">To inject the configuration MOF document on the VHD</span></span>

1. <span data-ttu-id="66a7a-130">呼叫 [掛接 VHD](/powershell/module/hyper-v/mount-vhd) Cmdlet，以掛接組態所要插入的 VHD。</span><span class="sxs-lookup"><span data-stu-id="66a7a-130">Mount the VHD into which you want to inject the configuration by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="66a7a-131">例如：</span><span class="sxs-lookup"><span data-stu-id="66a7a-131">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

1. <span data-ttu-id="66a7a-132">在執行 PowerShell 5.0 或更新版本的電腦上，將上述組態 ( **SampleIISInstall** ) 另存為 PowerShell 指令碼 (.ps1) 檔案。</span><span class="sxs-lookup"><span data-stu-id="66a7a-132">On a computer running PowerShell 5.0 or later, save the above configuration ( **SampleIISInstall** ) as a PowerShell script (.ps1) file.</span></span>

1. <span data-ttu-id="66a7a-133">在 PowerShell 主控台中，瀏覽至用以儲存.ps1 檔案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="66a7a-133">In a PowerShell console, navigate to the folder where you saved the .ps1 file.</span></span>

1. <span data-ttu-id="66a7a-134">執行下列 PowerShell 命令編譯 MOF 文件 (如需如何編譯 DSC 組態的資訊，請參閱 [DSC 組態](../configurations/configurations.md)：</span><span class="sxs-lookup"><span data-stu-id="66a7a-134">Run the following PowerShell commands to compile the MOF document (for information about compiling DSC configurations, see [DSC Configurations](../configurations/configurations.md):</span></span>

   ```powershell
   . .\SampleIISInstall.ps1
   SampleIISInstall
   ```

1. <span data-ttu-id="66a7a-135">這會在名為 `SampleIISInstall` 的新資料夾中建立 `localhost.mof` 檔案。</span><span class="sxs-lookup"><span data-stu-id="66a7a-135">This will create a `localhost.mof` file in a new folder named `SampleIISInstall`.</span></span> <span data-ttu-id="66a7a-136">使用 `Pending.mof`Move-Item[ Cmdlet 將該檔案重新命名為 ](/powershell/module/microsoft.powershell.management/move-item)，再將其移至 VHD 上正確的位置。</span><span class="sxs-lookup"><span data-stu-id="66a7a-136">Rename and move that file into the proper location on the VHD as `Pending.mof` by using the [Move-Item](/powershell/module/microsoft.powershell.management/move-item) cmdlet.</span></span> <span data-ttu-id="66a7a-137">例如：</span><span class="sxs-lookup"><span data-stu-id="66a7a-137">For example:</span></span>

   ```powershell
   Move-Item -Path C:\DSCTest\SampleIISInstall\localhost.mof -Destination E:\Windows\System32\Configuration\Pending.mof
   ```

1. <span data-ttu-id="66a7a-138">呼叫 [DISMOUNT-VHD](/powershell/module/hyper-v/dismount-vhd) Cmdlet 可卸載 VHD。</span><span class="sxs-lookup"><span data-stu-id="66a7a-138">Dismount the VHD by calling the [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet.</span></span>
   <span data-ttu-id="66a7a-139">例如：</span><span class="sxs-lookup"><span data-stu-id="66a7a-139">For example:</span></span>

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

1. <span data-ttu-id="66a7a-140">使用安裝有 DSC MOF 文件的 VHD 建立 VM。</span><span class="sxs-lookup"><span data-stu-id="66a7a-140">Create a VM by using the VHD where you installed the DSC MOF document.</span></span>

<span data-ttu-id="66a7a-141">在初始開機和安裝作業系統之後，便會安裝 IIS。</span><span class="sxs-lookup"><span data-stu-id="66a7a-141">After initial boot-up and operating system installation, IIS will be installed.</span></span> <span data-ttu-id="66a7a-142">您可以呼叫 [Get-windowsfeature](/powershell/module/servermanager/get-windowsfeature) Cmdlet 加以驗證。</span><span class="sxs-lookup"><span data-stu-id="66a7a-142">You can verify this by calling the [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet.</span></span>

## <a name="inject-a-dsc-metaconfiguration-into-a-vhd"></a><span data-ttu-id="66a7a-143">將 DSC metaconfiguration 插入 VHD</span><span class="sxs-lookup"><span data-stu-id="66a7a-143">Inject a DSC metaconfiguration into a VHD</span></span>

<span data-ttu-id="66a7a-144">您也可以將中繼設定作為 VHD 的 `MetaConfig.mof` 檔案插入 VHD，將電腦設定成在初始開機時提取設定 (請參閱[設定本機設定管理員 (LCM)](../managing-nodes/metaConfig.md))。</span><span class="sxs-lookup"><span data-stu-id="66a7a-144">You can also configure a computer to pull a configuration at initial boot-up by injecting a metaconfiguration (see [Configuring the Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md)) into the VHD as its `MetaConfig.mof` file.</span></span> <span data-ttu-id="66a7a-145">若 **DSCAutomationHostEnabled** 登錄機碼已設定為 2 (預設值)，則在電腦第一次開機時，DSC 會將 `MetaConfig.mof` 所定義的中繼設定套用到 LCM。</span><span class="sxs-lookup"><span data-stu-id="66a7a-145">If the **DSCAutomationHostEnabled** registry key is set to 2 (the default value), DSC will apply the metaconfiguration defined by `MetaConfig.mof` to the LCM when the computer boots up for the first time.</span></span> <span data-ttu-id="66a7a-146">若中繼設定指定 LCM 應從提取伺服器提取設定，電腦就會嘗試在初始開機時從該提取伺服器提取設定。</span><span class="sxs-lookup"><span data-stu-id="66a7a-146">If the metaconfiguration specifies that the LCM should pull configurations from a pull server, the computer will attempt to pull a configuration from that pull server at initial boot-up.</span></span> <span data-ttu-id="66a7a-147">如需設定 DSC 提取伺服器的資訊，請參閱[設定 DSC Web 提取伺服器](../pull-server/pullServer.md)。</span><span class="sxs-lookup"><span data-stu-id="66a7a-147">For information about setting up a DSC pull server, see [Setting up a DSC web pull server](../pull-server/pullServer.md).</span></span>

<span data-ttu-id="66a7a-148">在此範例中，我們將會同時使用上一節所述的組態 ( **SampleIISInstall** ) 及下列中繼設定：</span><span class="sxs-lookup"><span data-stu-id="66a7a-148">For this example, we will use both the configuration described in the previous section ( **SampleIISInstall** ), and the following metaconfiguration:</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientBootstrap
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('SampleIISInstall')
        }
    }
}
```

### <a name="to-inject-the-metaconfiguration-mof-document-on-the-vhd"></a><span data-ttu-id="66a7a-149">將中繼設定 MOF 文件插入 VHD</span><span class="sxs-lookup"><span data-stu-id="66a7a-149">To inject the metaconfiguration MOF document on the VHD</span></span>

1. <span data-ttu-id="66a7a-150">呼叫 [Mount-VHD](/powershell/module/hyper-v/mount-vhd) Cmdlet，掛接您要插入中繼設定的 VHD。</span><span class="sxs-lookup"><span data-stu-id="66a7a-150">Mount the VHD into which you want to inject the metaconfiguration by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="66a7a-151">例如：</span><span class="sxs-lookup"><span data-stu-id="66a7a-151">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

1. <span data-ttu-id="66a7a-152">[設定 DSC Web 提取伺服器](../pull-server/pullServer.md)，並將 **SampleIISInistall** 設定儲存到適當的資料夾。</span><span class="sxs-lookup"><span data-stu-id="66a7a-152">[Set up a DSC web pull server](../pull-server/pullServer.md), and save the **SampleIISInstall** configuration to the appropriate folder.</span></span>

1. <span data-ttu-id="66a7a-153">在執行 PowerShell 5.0 或更新版本的電腦上，將上述繼設定 ( **PullClientBootstrap** ) 另存為 PowerShell 指令碼 (.ps1) 檔案。</span><span class="sxs-lookup"><span data-stu-id="66a7a-153">On a computer running PowerShell 5.0 or later, save the above metaconfiguration ( **PullClientBootstrap** ) as a PowerShell script (.ps1) file.</span></span>

1. <span data-ttu-id="66a7a-154">在 PowerShell 主控台中，瀏覽至用以儲存.ps1 檔案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="66a7a-154">In a PowerShell console, navigate to the folder where you saved the .ps1 file.</span></span>

1. <span data-ttu-id="66a7a-155">執行下列 PowerShell 命令以編譯中繼設定 MOF 文件 (如需編譯 DSC 設定的相關資訊，請參閱 [DSC 設定](../configurations/configurations.md)：</span><span class="sxs-lookup"><span data-stu-id="66a7a-155">Run the following PowerShell commands to compile the metaconfiguration MOF document (for information about compiling DSC configurations, see [DSC Configurations](../configurations/configurations.md):</span></span>

   ```powershell
   . .\PullClientBootstrap.ps1
   PullClientBootstrap
   ```

1. <span data-ttu-id="66a7a-156">這會在名為 `PullClientBootstrap` 的新資料夾中建立 `localhost.meta.mof` 檔案。</span><span class="sxs-lookup"><span data-stu-id="66a7a-156">This will create a `localhost.meta.mof` file in a new folder named `PullClientBootstrap`.</span></span> <span data-ttu-id="66a7a-157">使用 `MetaConfig.mof`Move-Item[ Cmdlet 將該檔案重新命名為 ](/powershell/module/microsoft.powershell.management/move-item)，再將其移至 VHD 上正確的位置。</span><span class="sxs-lookup"><span data-stu-id="66a7a-157">Rename and move that file into the proper location on the VHD as `MetaConfig.mof` by using the [Move-Item](/powershell/module/microsoft.powershell.management/move-item) cmdlet.</span></span>

   ```powershell
   Move-Item -Path C:\DSCTest\PullClientBootstrap\localhost.meta.mof -Destination E:\Windows\System32\Configuration\MetaConfig.mof
   ```

1. <span data-ttu-id="66a7a-158">呼叫 [DISMOUNT-VHD](/powershell/module/hyper-v/dismount-vhd) Cmdlet 可卸載 VHD。</span><span class="sxs-lookup"><span data-stu-id="66a7a-158">Dismount the VHD by calling the [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet.</span></span>
   <span data-ttu-id="66a7a-159">例如：</span><span class="sxs-lookup"><span data-stu-id="66a7a-159">For example:</span></span>

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

1. <span data-ttu-id="66a7a-160">使用安裝有 DSC MOF 文件的 VHD 建立 VM。</span><span class="sxs-lookup"><span data-stu-id="66a7a-160">Create a VM by using the VHD where you installed the DSC MOF document.</span></span>

<span data-ttu-id="66a7a-161">初始開機並安裝作業系統之後，DSC 會從提取伺服器提取設定，然後安裝 IIS。</span><span class="sxs-lookup"><span data-stu-id="66a7a-161">After initial boot-up and operating system installation, DSC will pull the configuration from the pull server, and IIS will be installed.</span></span> <span data-ttu-id="66a7a-162">您可以呼叫 [Get-windowsfeature](/powershell/module/servermanager/get-windowsfeature) Cmdlet 加以驗證。</span><span class="sxs-lookup"><span data-stu-id="66a7a-162">You can verify this by calling the [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet.</span></span>

## <a name="disable-dsc-at-boot-time"></a><span data-ttu-id="66a7a-163">開機時停用 DSC</span><span class="sxs-lookup"><span data-stu-id="66a7a-163">Disable DSC at boot time</span></span>

<span data-ttu-id="66a7a-164">根據預設，`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\DSCAutomationHostEnabled`</span><span class="sxs-lookup"><span data-stu-id="66a7a-164">By default, the value of the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\DSCAutomationHostEnabled`</span></span>
<span data-ttu-id="66a7a-165">機碼的值會設定為 2，其會允許 DSC 設定在電腦處於擱置或目前狀態時執行。</span><span class="sxs-lookup"><span data-stu-id="66a7a-165">key is set to 2, which allows a DSC configuration to run if the computer is in pending or current state.</span></span> <span data-ttu-id="66a7a-166">對於不想在初始開機時執行的組態，您必須將此機碼值設為 0：</span><span class="sxs-lookup"><span data-stu-id="66a7a-166">If you do not want a configuration to run at initial boot-up, you need so set the value of this key to 0:</span></span>

1. <span data-ttu-id="66a7a-167">呼叫 [Mount-VHD](/powershell/module/hyper-v/mount-vhd) Cmdlet，以掛接 VHD。</span><span class="sxs-lookup"><span data-stu-id="66a7a-167">Mount the VHD by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="66a7a-168">例如：</span><span class="sxs-lookup"><span data-stu-id="66a7a-168">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

1. <span data-ttu-id="66a7a-169">呼叫 `reg load`，以從 VHD 載入登錄 `HKLM\Software` 子機碼。</span><span class="sxs-lookup"><span data-stu-id="66a7a-169">Load the registry `HKLM\Software` subkey from the VHD by calling `reg load`.</span></span>

   ```powershell
   reg load HKLM\Vhd E:\Windows\System32\Config\Software`
   ```

1. <span data-ttu-id="66a7a-170">使用 PowerShell 登錄提供者瀏覽至 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`。</span><span class="sxs-lookup"><span data-stu-id="66a7a-170">Navigate to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System` by using the PowerShell Registry provider.</span></span>

   ```powershell
   Set-Location HKLM:\Software\Microsoft\Windows\CurrentVersion\Policies\System`
   ```

1. <span data-ttu-id="66a7a-171">將 `DSCAutomationHostEnabled` 的值變更為 0。</span><span class="sxs-lookup"><span data-stu-id="66a7a-171">Change the value of `DSCAutomationHostEnabled` to 0.</span></span>

   ```powershell
   Set-ItemProperty -Path . -Name DSCAutomationHostEnabled -Value 0
   ```

5. <span data-ttu-id="66a7a-172">執行下列命令，以卸載此機碼︰</span><span class="sxs-lookup"><span data-stu-id="66a7a-172">Unload the registry by running the following commands:</span></span>

   ```powershell
   [gc]::Collect()
   reg unload HKLM\Vhd
   ```

## <a name="see-also"></a><span data-ttu-id="66a7a-173">另請參閱</span><span class="sxs-lookup"><span data-stu-id="66a7a-173">See Also</span></span>

[<span data-ttu-id="66a7a-174">DSC 設定</span><span class="sxs-lookup"><span data-stu-id="66a7a-174">DSC Configurations</span></span>](../configurations/configurations.md)

[<span data-ttu-id="66a7a-175">DSCAutomationHostEnabled 登錄機碼</span><span class="sxs-lookup"><span data-stu-id="66a7a-175">DSCAutomationHostEnabled registry key</span></span>](DSCAutomationHostEnabled.md)

[<span data-ttu-id="66a7a-176">設定本機設定管理員 (LCM)</span><span class="sxs-lookup"><span data-stu-id="66a7a-176">Configuring the Local Configuration Manager (LCM)</span></span>](../managing-nodes/metaConfig.md)

[<span data-ttu-id="66a7a-177">設定 DSC Web 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="66a7a-177">Setting up a DSC web pull server</span></span>](../pull-server/pullServer.md)
