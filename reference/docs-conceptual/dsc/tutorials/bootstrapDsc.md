---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 使用 DSC 在初始開機時設定虛擬機器
ms.openlocfilehash: 48f5e30bed0b97b80724fbf95ec604ede9f2ea5d
ms.sourcegitcommit: c4906f4c9fa4ef1a16dcd6dd00ff960d19446d71
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2020
ms.locfileid: "89236283"
---
# <a name="configure-a-virtual-machines-at-initial-boot-up-by-using-dsc"></a><span data-ttu-id="7ee78-103">使用 DSC 在初始開機時設定虛擬機器</span><span class="sxs-lookup"><span data-stu-id="7ee78-103">Configure a virtual machines at initial boot-up by using DSC</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7ee78-104">適用於：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="7ee78-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="requirements"></a><span data-ttu-id="7ee78-105">需求</span><span class="sxs-lookup"><span data-stu-id="7ee78-105">Requirements</span></span>

> [!NOTE]
> <span data-ttu-id="7ee78-106">本主題所述的 **DSCAutomationHostEnabled** 登錄機碼無法在 PowerShell 4.0 中使用。</span><span class="sxs-lookup"><span data-stu-id="7ee78-106">The **DSCAutomationHostEnabled** registry key described in this topic is not available in PowerShell 4.0.</span></span>
> <span data-ttu-id="7ee78-107">如需如何在 PowerShell 4.0 初始開機時設定新的虛擬機器，請參閱 [Want to Automatically Configure Your Machines Using DSC at Initial Boot-up?](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/) (想要使用 DSC 在初始開機時自動設定您的電腦嗎？)</span><span class="sxs-lookup"><span data-stu-id="7ee78-107">For information on how to configure new virtual machines at initial boot-up in PowerShell 4.0, see [Want to Automatically Configure Your Machines Using DSC at Initial Boot-up?](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)</span></span>

<span data-ttu-id="7ee78-108">若要執行這些範例，您需要︰</span><span class="sxs-lookup"><span data-stu-id="7ee78-108">To run these examples, you will need:</span></span>

- <span data-ttu-id="7ee78-109">可開機使用的 VHD。</span><span class="sxs-lookup"><span data-stu-id="7ee78-109">A bootable VHD to work with.</span></span> <span data-ttu-id="7ee78-110">您可以從 [TechNet 評估中心](https://www.microsoft.com/evalcenter/evaluate-windows-server-2016)下載評估版 Windows Server 2016 的 ISO。</span><span class="sxs-lookup"><span data-stu-id="7ee78-110">You can download an ISO with an evaluation copy of Windows Server 2016 at [TechNet Evaluation Center](https://www.microsoft.com/evalcenter/evaluate-windows-server-2016).</span></span>
  <span data-ttu-id="7ee78-111">您可以在 [Creating Bootable Virtual Hard Disks](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10)) (建立可開機的虛擬硬碟) 中尋找如何從 ISO 建立 VHD 的指示。</span><span class="sxs-lookup"><span data-stu-id="7ee78-111">You can find instructions on how to create a VHD from an ISO image at [Creating Bootable Virtual Hard Disks](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10)).</span></span>
- <span data-ttu-id="7ee78-112">已啟用 HYPER-V 的主機電腦。</span><span class="sxs-lookup"><span data-stu-id="7ee78-112">A host computer that has Hyper-V enabled.</span></span> <span data-ttu-id="7ee78-113">如需資訊，請參閱 [HYPER-V 概觀](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11))。</span><span class="sxs-lookup"><span data-stu-id="7ee78-113">For information, see [Hyper-V overview](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11)).</span></span>

  <span data-ttu-id="7ee78-114">藉由使用 DSC，您可以在初始開機時自動安裝軟體及設定電腦。</span><span class="sxs-lookup"><span data-stu-id="7ee78-114">By using DSC, you can automate software installation and configuration for a computer at initial boot-up.</span></span>
  <span data-ttu-id="7ee78-115">您可以將設定 MOF 文件或 metaconfiguration 插入可開機的媒體 (例如 VHD)，於初始開機程序期間加以執行。</span><span class="sxs-lookup"><span data-stu-id="7ee78-115">You do this by either injecting a configuration MOF document or a metaconfiguration into bootable media (such as a VHD) so that they are run during the initial boot-up process.</span></span>
  <span data-ttu-id="7ee78-116">此行為是由 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System` 下方的 [DSCAutomationHostEnabled 登錄機碼](DSCAutomationHostEnabled.md) 登錄機碼所設定的。</span><span class="sxs-lookup"><span data-stu-id="7ee78-116">This behavior is specified by the [DSCAutomationHostEnabled registry key](DSCAutomationHostEnabled.md) registry key under `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`.</span></span>
  <span data-ttu-id="7ee78-117">此機碼的值預設為 2，表示允許 DSC 在開機時執行。</span><span class="sxs-lookup"><span data-stu-id="7ee78-117">By default, the value of this key is 2, which allows DSC to run at boot time.</span></span>

  <span data-ttu-id="7ee78-118">若您不想在開機時執行 DSC，請將 [DSCAutomationHostEnabled 登錄機碼](DSCAutomationHostEnabled.md) 登錄機碼設為 0。</span><span class="sxs-lookup"><span data-stu-id="7ee78-118">If you do not want DSC to run at boot time, set the value of the [DSCAutomationHostEnabled registry key](DSCAutomationHostEnabled.md) registry key to 0.</span></span>

- <span data-ttu-id="7ee78-119">將設定 MOF 文件插入 VHD</span><span class="sxs-lookup"><span data-stu-id="7ee78-119">Inject a configuration MOF document into a VHD</span></span>
- <span data-ttu-id="7ee78-120">將 DSC metaconfiguration 插入 VHD</span><span class="sxs-lookup"><span data-stu-id="7ee78-120">Inject a DSC metaconfiguration into a VHD</span></span>
- <span data-ttu-id="7ee78-121">開機時停用 DSC</span><span class="sxs-lookup"><span data-stu-id="7ee78-121">Disable DSC at boot time</span></span>

> [!NOTE]
> <span data-ttu-id="7ee78-122">您可以同時將 `Pending.mof` 和 `MetaConfig.mof` 插入到同一部電腦。</span><span class="sxs-lookup"><span data-stu-id="7ee78-122">You can inject both `Pending.mof` and `MetaConfig.mof` into a computer at the same time.</span></span>
> <span data-ttu-id="7ee78-123">當這兩個檔案同時存在時，`MetaConfig.mof` 中所指定的設定會優先執行。</span><span class="sxs-lookup"><span data-stu-id="7ee78-123">If both files are present, the settings specified in `MetaConfig.mof` take precedence.</span></span>

## <a name="inject-a-configuration-mof-document-into-a-vhd"></a><span data-ttu-id="7ee78-124">將設定 MOF 文件插入 VHD</span><span class="sxs-lookup"><span data-stu-id="7ee78-124">Inject a configuration MOF document into a VHD</span></span>

<span data-ttu-id="7ee78-125">若要制定初始開機時的組態，可以將預先編譯的設定 MOF 文件用為 `Pending.mof` 檔案插入 VHD。</span><span class="sxs-lookup"><span data-stu-id="7ee78-125">To enact a configuration at initial boot-up, you can inject a compiled configuration MOF document into the VHD as its `Pending.mof` file.</span></span>
<span data-ttu-id="7ee78-126">若 **DSCAutomationHostEnabled** 登錄機碼設定為 2 (預設值)，當電腦第一次開機時，DSC 會套用 `Pending.mof` 所定義的組態。</span><span class="sxs-lookup"><span data-stu-id="7ee78-126">If the **DSCAutomationHostEnabled** registry key is set to 2 (the default value), DSC will apply the configuration defined by `Pending.mof` when the computer boots up for the first time.</span></span>

<span data-ttu-id="7ee78-127">此範例中，我們會使用下列組態在新的電腦上安裝 IIS：</span><span class="sxs-lookup"><span data-stu-id="7ee78-127">For this example, we will use the following configuration, which will install IIS on the new computer:</span></span>

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

### <a name="to-inject-the-configuration-mof-document-on-the-vhd"></a><span data-ttu-id="7ee78-128">將設定 MOF 文件插入 VHD</span><span class="sxs-lookup"><span data-stu-id="7ee78-128">To inject the configuration MOF document on the VHD</span></span>

1. <span data-ttu-id="7ee78-129">呼叫 [掛接 VHD](/powershell/module/hyper-v/mount-vhd) Cmdlet，以掛接組態所要插入的 VHD。</span><span class="sxs-lookup"><span data-stu-id="7ee78-129">Mount the VHD into which you want to inject the configuration by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="7ee78-130">例如：</span><span class="sxs-lookup"><span data-stu-id="7ee78-130">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. <span data-ttu-id="7ee78-131">在執行 PowerShell 5.0 或更新版本的電腦上，將上述組態 (**SampleIISInstall**) 另存為 PowerShell 指令碼 (.ps1) 檔案。</span><span class="sxs-lookup"><span data-stu-id="7ee78-131">On a computer running PowerShell 5.0 or later, save the above configuration (**SampleIISInstall**) as a PowerShell script (.ps1) file.</span></span>

3. <span data-ttu-id="7ee78-132">在 PowerShell 主控台中，瀏覽至用以儲存.ps1 檔案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="7ee78-132">In a PowerShell console, navigate to the folder where you saved the .ps1 file.</span></span>

4. <span data-ttu-id="7ee78-133">執行下列 PowerShell 命令編譯 MOF 文件 (如需如何編譯 DSC 組態的資訊，請參閱 [DSC 組態](../configurations/configurations.md)：</span><span class="sxs-lookup"><span data-stu-id="7ee78-133">Run the following PowerShell commands to compile the MOF document (for information about compiling DSC configurations, see [DSC Configurations](../configurations/configurations.md):</span></span>

   ```powershell
   . .\SampleIISInstall.ps1
   SampleIISInstall
   ```

5. <span data-ttu-id="7ee78-134">這會在名為 `SampleIISInstall` 的新資料夾中建立 `localhost.mof` 檔案。</span><span class="sxs-lookup"><span data-stu-id="7ee78-134">This will create a `localhost.mof` file in a new folder named `SampleIISInstall`.</span></span>
   <span data-ttu-id="7ee78-135">使用 `Pending.mof`Move-Item[ Cmdlet 將該檔案重新命名為 ](/powershell/module/microsoft.powershell.management/move-item)，再將其移至 VHD 上正確的位置。</span><span class="sxs-lookup"><span data-stu-id="7ee78-135">Rename and move that file into the proper location on the VHD as `Pending.mof` by using the [Move-Item](/powershell/module/microsoft.powershell.management/move-item) cmdlet.</span></span> <span data-ttu-id="7ee78-136">例如：</span><span class="sxs-lookup"><span data-stu-id="7ee78-136">For example:</span></span>

   ```powershell
       Move-Item -Path C:\DSCTest\SampleIISInstall\localhost.mof -Destination E:\Windows\System32\Configuration\Pending.mof
   ```

6. <span data-ttu-id="7ee78-137">呼叫 [DISMOUNT-VHD](/powershell/module/hyper-v/dismount-vhd) Cmdlet 可卸載 VHD。</span><span class="sxs-lookup"><span data-stu-id="7ee78-137">Dismount the VHD by calling the [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet.</span></span> <span data-ttu-id="7ee78-138">例如：</span><span class="sxs-lookup"><span data-stu-id="7ee78-138">For example:</span></span>

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

7. <span data-ttu-id="7ee78-139">使用安裝有 DSC MOF 文件的 VHD 建立 VM。</span><span class="sxs-lookup"><span data-stu-id="7ee78-139">Create a VM by using the VHD where you installed the DSC MOF document.</span></span>

<span data-ttu-id="7ee78-140">在初始開機和安裝作業系統之後，便會安裝 IIS。</span><span class="sxs-lookup"><span data-stu-id="7ee78-140">After initial boot-up and operating system installation, IIS will be installed.</span></span>
<span data-ttu-id="7ee78-141">您可以呼叫 [Get-windowsfeature](/powershell/module/servermanager/get-windowsfeature) Cmdlet 加以驗證。</span><span class="sxs-lookup"><span data-stu-id="7ee78-141">You can verify this by calling the [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet.</span></span>

## <a name="inject-a-dsc-metaconfiguration-into-a-vhd"></a><span data-ttu-id="7ee78-142">將 DSC metaconfiguration 插入 VHD</span><span class="sxs-lookup"><span data-stu-id="7ee78-142">Inject a DSC metaconfiguration into a VHD</span></span>

<span data-ttu-id="7ee78-143">您也可以將中繼設定作為 VHD 的 `MetaConfig.mof` 檔案插入 VHD，將電腦設定成在初始開機時提取設定 (請參閱[設定本機設定管理員 (LCM)](../managing-nodes/metaConfig.md))。</span><span class="sxs-lookup"><span data-stu-id="7ee78-143">You can also configure a computer to pull a configuration at initial boot-up by injecting a metaconfiguration (see [Configuring the Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md)) into the VHD as its `MetaConfig.mof` file.</span></span>
<span data-ttu-id="7ee78-144">若 **DSCAutomationHostEnabled** 登錄機碼設為 2 (預設值)，則電腦第一次開機時，DSC 將會套用 `MetaConfig.mof` 所定義的中繼設定。</span><span class="sxs-lookup"><span data-stu-id="7ee78-144">If the **DSCAutomationHostEnabled** registry key is set to 2 (the default value),  DSC will apply the metaconfiguration defined by `MetaConfig.mof` to the LCM when the computer boots up for the first time.</span></span>
<span data-ttu-id="7ee78-145">若中繼設定指定 LCM 應從提取伺服器提取設定，電腦就會嘗試在初始開機時從該提取伺服器提取設定。</span><span class="sxs-lookup"><span data-stu-id="7ee78-145">If the metaconfiguration specifies that the LCM should pull configurations from a pull server, the computer will attempt to pull a configuration from that pull server at initial boot-up.</span></span>
<span data-ttu-id="7ee78-146">如需設定 DSC 提取伺服器的資訊，請參閱[設定 DSC Web 提取伺服器](../pull-server/pullServer.md)。</span><span class="sxs-lookup"><span data-stu-id="7ee78-146">For information about setting up a DSC pull server, see [Setting up a DSC web pull server](../pull-server/pullServer.md).</span></span>

<span data-ttu-id="7ee78-147">在此範例中，我們將會同時使用上一節所述的組態 (**SampleIISInstall**) 及下列中繼設定：</span><span class="sxs-lookup"><span data-stu-id="7ee78-147">For this example, we will use both the configuration described in the previous section (**SampleIISInstall**), and the following metaconfiguration:</span></span>

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

### <a name="to-inject-the-metaconfiguration-mof-document-on-the-vhd"></a><span data-ttu-id="7ee78-148">將中繼設定 MOF 文件插入 VHD</span><span class="sxs-lookup"><span data-stu-id="7ee78-148">To inject the metaconfiguration MOF document on the VHD</span></span>

1. <span data-ttu-id="7ee78-149">呼叫 [Mount-VHD](/powershell/module/hyper-v/mount-vhd) Cmdlet，掛接您要插入中繼設定的 VHD。</span><span class="sxs-lookup"><span data-stu-id="7ee78-149">Mount the VHD into which you want to inject the metaconfiguration by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="7ee78-150">例如：</span><span class="sxs-lookup"><span data-stu-id="7ee78-150">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. <span data-ttu-id="7ee78-151">[設定 DSC Web 提取伺服器](../pull-server/pullServer.md)，並將 **SampleIISInistall** 設定儲存到適當的資料夾。</span><span class="sxs-lookup"><span data-stu-id="7ee78-151">[Set up a DSC web pull server](../pull-server/pullServer.md), and save the **SampleIISInstall** configuration to the appropriate folder.</span></span>

3. <span data-ttu-id="7ee78-152">在執行 PowerShell 5.0 或更新版本的電腦上，將上述繼設定 (**PullClientBootstrap**) 另存為 PowerShell 指令碼 (.ps1) 檔案。</span><span class="sxs-lookup"><span data-stu-id="7ee78-152">On a computer running PowerShell 5.0 or later, save the above metaconfiguration (**PullClientBootstrap**) as a PowerShell script (.ps1) file.</span></span>

4. <span data-ttu-id="7ee78-153">在 PowerShell 主控台中，瀏覽至用以儲存.ps1 檔案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="7ee78-153">In a PowerShell console, navigate to the folder where you saved the .ps1 file.</span></span>

5. <span data-ttu-id="7ee78-154">執行下列 PowerShell 命令編譯中繼設定 MOF 文件 (如需如何編譯 DSC 組態的資訊，請參閱 [DSC 組態](../configurations/configurations.md)：</span><span class="sxs-lookup"><span data-stu-id="7ee78-154">Run the following PowerShell commands to compile the  metaconfiguration MOF document (for information about compiling DSC configurations, see [DSC Configurations](../configurations/configurations.md):</span></span>

   ```powershell
   . .\PullClientBootstrap.ps1
   PullClientBootstrap
   ```

6. <span data-ttu-id="7ee78-155">這會在名為 `PullClientBootstrap` 的新資料夾中建立 `localhost.meta.mof` 檔案。</span><span class="sxs-lookup"><span data-stu-id="7ee78-155">This will create a `localhost.meta.mof` file in a new folder named `PullClientBootstrap`.</span></span>
   <span data-ttu-id="7ee78-156">使用 `MetaConfig.mof`Move-Item[ Cmdlet 將該檔案重新命名為 ](/powershell/module/microsoft.powershell.management/move-item)，再將其移至 VHD 上正確的位置。</span><span class="sxs-lookup"><span data-stu-id="7ee78-156">Rename and move that file into the proper location on the VHD as `MetaConfig.mof` by using the [Move-Item](/powershell/module/microsoft.powershell.management/move-item) cmdlet.</span></span>

   ```powershell
   Move-Item -Path C:\DSCTest\PullClientBootstrap\localhost.meta.mof -Destination E:\Windows\System32\Configuration\MetaConfig.mof
   ```

7. <span data-ttu-id="7ee78-157">呼叫 [DISMOUNT-VHD](/powershell/module/hyper-v/dismount-vhd) Cmdlet 可卸載 VHD。</span><span class="sxs-lookup"><span data-stu-id="7ee78-157">Dismount the VHD by calling the [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet.</span></span> <span data-ttu-id="7ee78-158">例如：</span><span class="sxs-lookup"><span data-stu-id="7ee78-158">For example:</span></span>

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

8. <span data-ttu-id="7ee78-159">使用安裝有 DSC MOF 文件的 VHD 建立 VM。</span><span class="sxs-lookup"><span data-stu-id="7ee78-159">Create a VM by using the VHD where you installed the DSC MOF document.</span></span>

<span data-ttu-id="7ee78-160">初始開機並安裝作業系統之後，DSC 會從提取伺服器提取設定，然後安裝 IIS。</span><span class="sxs-lookup"><span data-stu-id="7ee78-160">After initial boot-up and operating system installation, DSC will pull the configuration from the pull server, and IIS will be installed.</span></span>
<span data-ttu-id="7ee78-161">您可以呼叫 [Get-windowsfeature](/powershell/module/servermanager/get-windowsfeature) Cmdlet 加以驗證。</span><span class="sxs-lookup"><span data-stu-id="7ee78-161">You can verify this by calling the [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet.</span></span>

## <a name="disable-dsc-at-boot-time"></a><span data-ttu-id="7ee78-162">開機時停用 DSC</span><span class="sxs-lookup"><span data-stu-id="7ee78-162">Disable DSC at boot time</span></span>

<span data-ttu-id="7ee78-163">預設會將 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\DSCAutomationHostEnabled` 機碼的值設為 2，讓 DSC 設定可以在電腦處於擱置或目前狀態時執行。</span><span class="sxs-lookup"><span data-stu-id="7ee78-163">By default, the value of the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\DSCAutomationHostEnabled` key is set to 2, which allows a DSC configuration to run if the computer is in pending or current state.</span></span> <span data-ttu-id="7ee78-164">對於不想在初始開機時執行的組態，您必須將此機碼值設為 0：</span><span class="sxs-lookup"><span data-stu-id="7ee78-164">If you do not want a configuration to run at initial boot-up, you need so set the value of this key to 0:</span></span>

1. <span data-ttu-id="7ee78-165">呼叫 [Mount-VHD](/powershell/module/hyper-v/mount-vhd) Cmdlet，以掛接 VHD。</span><span class="sxs-lookup"><span data-stu-id="7ee78-165">Mount the VHD by calling the [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet.</span></span> <span data-ttu-id="7ee78-166">例如：</span><span class="sxs-lookup"><span data-stu-id="7ee78-166">For example:</span></span>

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. <span data-ttu-id="7ee78-167">呼叫 `reg load`，以從 VHD 載入登錄 `HKLM\Software` 子機碼。</span><span class="sxs-lookup"><span data-stu-id="7ee78-167">Load the registry `HKLM\Software` subkey from the VHD by calling `reg load`.</span></span>

   ```powershell
   reg load HKLM\Vhd E:\Windows\System32\Config\Software`
   ```

3. <span data-ttu-id="7ee78-168">使用 PowerShell 登錄提供者瀏覽至 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`。</span><span class="sxs-lookup"><span data-stu-id="7ee78-168">Navigate to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System` by using the PowerShell Registry provider.</span></span>

   ```powershell
   Set-Location HKLM:\Software\Microsoft\Windows\CurrentVersion\Policies\System`
   ```

4. <span data-ttu-id="7ee78-169">將 `DSCAutomationHostEnabled` 的值變更為 0。</span><span class="sxs-lookup"><span data-stu-id="7ee78-169">Change the value of `DSCAutomationHostEnabled` to 0.</span></span>

   ```powershell
   Set-ItemProperty -Path . -Name DSCAutomationHostEnabled -Value 0
   ```

5. <span data-ttu-id="7ee78-170">執行下列命令，以卸載此機碼︰</span><span class="sxs-lookup"><span data-stu-id="7ee78-170">Unload the registry by running the following commands:</span></span>

   ```powershell
   [gc]::Collect()
   reg unload HKLM\Vhd
   ```

## <a name="see-also"></a><span data-ttu-id="7ee78-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ee78-171">See Also</span></span>

[<span data-ttu-id="7ee78-172">DSC 設定</span><span class="sxs-lookup"><span data-stu-id="7ee78-172">DSC Configurations</span></span>](../configurations/configurations.md)

[<span data-ttu-id="7ee78-173">DSCAutomationHostEnabled 登錄機碼</span><span class="sxs-lookup"><span data-stu-id="7ee78-173">DSCAutomationHostEnabled registry key</span></span>](DSCAutomationHostEnabled.md)

[<span data-ttu-id="7ee78-174">設定本機設定管理員 (LCM)</span><span class="sxs-lookup"><span data-stu-id="7ee78-174">Configuring the Local Configuration Manager (LCM)</span></span>](../managing-nodes/metaConfig.md)

[<span data-ttu-id="7ee78-175">設定 DSC Web 提取伺服器</span><span class="sxs-lookup"><span data-stu-id="7ee78-175">Setting up a DSC web pull server</span></span>](../pull-server/pullServer.md)
