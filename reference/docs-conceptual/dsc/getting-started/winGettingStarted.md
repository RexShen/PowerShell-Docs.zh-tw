---
ms.date: 08/15/2019
keywords: dsc,powershell,設定,安裝
title: 開始使用適用於 Windows 的 Desired State Configuration (DSC)
ms.openlocfilehash: 00e1cf545b19f054b4b1ff468c9f6ad94e5cef55
ms.sourcegitcommit: c4906f4c9fa4ef1a16dcd6dd00ff960d19446d71
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2020
ms.locfileid: "89236317"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-windows"></a><span data-ttu-id="3ad79-103">開始使用適用於 Windows 的 Desired State Configuration (DSC)</span><span class="sxs-lookup"><span data-stu-id="3ad79-103">Get started with Desired State Configuration (DSC) for Windows</span></span>

<span data-ttu-id="3ad79-104">此主題說明如何開始使用適用於 Windows 的 PowerShell Desired State Configuration (DSC)。</span><span class="sxs-lookup"><span data-stu-id="3ad79-104">This topic explains how to get started using PowerShell Desired State Configuration (DSC) for Windows.</span></span>
<span data-ttu-id="3ad79-105">如需 DSC 的一般資訊，請參閱[開始使用 Windows PowerShell 預期狀態設定](../overview/overview.md)。</span><span class="sxs-lookup"><span data-stu-id="3ad79-105">For general information about DSC, see [Get Started with Windows PowerShell Desired State Configuration](../overview/overview.md).</span></span>

## <a name="supported-windows-operation-system-versions"></a><span data-ttu-id="3ad79-106">支援的 Windows 作業系統版本</span><span class="sxs-lookup"><span data-stu-id="3ad79-106">Supported Windows operation system versions</span></span>

<span data-ttu-id="3ad79-107">下面是支援的版本：</span><span class="sxs-lookup"><span data-stu-id="3ad79-107">The following versions are supported:</span></span>

- <span data-ttu-id="3ad79-108">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="3ad79-108">Windows Server 2019</span></span>
- <span data-ttu-id="3ad79-109">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="3ad79-109">Windows Server 2016</span></span>
- <span data-ttu-id="3ad79-110">Windows Server 2012R2</span><span class="sxs-lookup"><span data-stu-id="3ad79-110">Windows Server 2012R2</span></span>
- <span data-ttu-id="3ad79-111">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="3ad79-111">Windows Server 2012</span></span>
- <span data-ttu-id="3ad79-112">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="3ad79-112">Windows Server 2008 R2 SP1</span></span>
- <span data-ttu-id="3ad79-113">Windows 10</span><span class="sxs-lookup"><span data-stu-id="3ad79-113">Windows 10</span></span>
- <span data-ttu-id="3ad79-114">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="3ad79-114">Windows 8.1</span></span>
- <span data-ttu-id="3ad79-115">Windows 7</span><span class="sxs-lookup"><span data-stu-id="3ad79-115">Windows 7</span></span>

<span data-ttu-id="3ad79-116">[Microsoft Hyper-V Server](/windows-server/virtualization/hyper-v/hyper-v-server-2016) 獨立產品 SKU 不包含 Desired State Configuration 的實作，因此無法由 PowerShell DSC 或 Azure 自動化狀態設定管理。</span><span class="sxs-lookup"><span data-stu-id="3ad79-116">The [Microsoft Hyper-V Server](/windows-server/virtualization/hyper-v/hyper-v-server-2016) standalone product sku doesn't contain an implementation of Desired State Configuration so it cannot be managed by PowerShell DSC or Azure Automation State Configuration.</span></span>

## <a name="installing-dsc"></a><span data-ttu-id="3ad79-117">安裝 DSC</span><span class="sxs-lookup"><span data-stu-id="3ad79-117">Installing DSC</span></span>

<span data-ttu-id="3ad79-118">PowerShell Desired State Configuration 包含在 Windows 中，而且透過 Windows Management Framework 來更新。</span><span class="sxs-lookup"><span data-stu-id="3ad79-118">PowerShell Desired State Configuration is included in Windows and updated through Windows Management Framework.</span></span> <span data-ttu-id="3ad79-119">最新版本是 [Windows Management Framework 5.1](https://www.microsoft.com/download/details.aspx?id=54616) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="3ad79-119">The latest version is [Windows Management Framework 5.1](https://www.microsoft.com/download/details.aspx?id=54616).</span></span>

> [!NOTE]
> <span data-ttu-id="3ad79-120">您不需要啟用 Windows Server 功能 'DSC-Service'，即可使用 DSC 來管理電腦。</span><span class="sxs-lookup"><span data-stu-id="3ad79-120">You do not need to enable the Windows Server feature 'DSC-Service' to manage a machine using DSC.</span></span>
> <span data-ttu-id="3ad79-121">只有在建置 Windows 提取伺服器執行個體時，才需要該功能。</span><span class="sxs-lookup"><span data-stu-id="3ad79-121">That feature is only needed when building a Windows Pull Server instance.</span></span>

## <a name="using-dsc-for-windows"></a><span data-ttu-id="3ad79-122">使用適用於 Windows 的 DSC</span><span class="sxs-lookup"><span data-stu-id="3ad79-122">Using DSC for Windows</span></span>

<span data-ttu-id="3ad79-123">下列各節說明如何在 Windows 電腦上建立並執行 DSC 設定。</span><span class="sxs-lookup"><span data-stu-id="3ad79-123">The following sections explain how to create and run DSC configurations on Windows computers.</span></span>

### <a name="creating-a-configuration-mof-document"></a><span data-ttu-id="3ad79-124">建立設定 MOF 文件</span><span class="sxs-lookup"><span data-stu-id="3ad79-124">Creating a configuration MOF document</span></span>

<span data-ttu-id="3ad79-125">Windows PowerShell `Configuration` 關鍵字可用來建立設定。</span><span class="sxs-lookup"><span data-stu-id="3ad79-125">The Windows PowerShell `Configuration` keyword is used to create a configuration.</span></span>
<span data-ttu-id="3ad79-126">下列步驟說明如何使用 Windows PowerShell 建立設定文件。</span><span class="sxs-lookup"><span data-stu-id="3ad79-126">The following steps describe the creation of a configuration document using Windows PowerShell.</span></span>

#### <a name="define-a-configuration-and-generate-the-configuration-document"></a><span data-ttu-id="3ad79-127">定義設定，然後產生設定文件：</span><span class="sxs-lookup"><span data-stu-id="3ad79-127">Define a configuration and generate the configuration document:</span></span>

```powershell
Configuration EnvironmentVariable_Path
{
    param ()

    Import-DscResource -ModuleName 'PSDscResources'

    Node localhost
    {
        Environment CreatePathEnvironmentVariable
        {
            Name = 'TestPathEnvironmentVariable'
            Value = 'TestValue'
            Ensure = 'Present'
            Path = $true
            Target = @('Process', 'Machine')
        }
    }
}

EnvironmentVariable_Path -OutputPath:"C:\EnvironmentVariable_Path"
```

#### <a name="install-a-module-containing-dsc-resources"></a><span data-ttu-id="3ad79-128">安裝包含 DSC 資源的模組</span><span class="sxs-lookup"><span data-stu-id="3ad79-128">Install a module containing DSC resources</span></span>

<span data-ttu-id="3ad79-129">Windows PowerShell Desired State Configuration 包含內有 DSC 資源的內建模組。</span><span class="sxs-lookup"><span data-stu-id="3ad79-129">Windows PowerShell Desired State Configuration includes built-in modules containing DSC resources.</span></span>
<span data-ttu-id="3ad79-130">您也可以使用 PowerShellGet Cmdlet，從外部來源 (例如，PowerShell 資源庫) 載入模組。</span><span class="sxs-lookup"><span data-stu-id="3ad79-130">You can also load modules from external sources such as the PowerShell Gallery, using the PowerShellGet cmdlets.</span></span>

```PowerShell
Install-Module 'PSDscResources' -Verbose
```

#### <a name="apply-the-configuration-to-the-machine"></a><span data-ttu-id="3ad79-131">將設定套用至機器</span><span class="sxs-lookup"><span data-stu-id="3ad79-131">Apply the configuration to the machine</span></span>

> [!NOTE]
> <span data-ttu-id="3ad79-132">若要允許 DSC 執行，就必須將 Windows 設定成即使在您執行 `localhost` 設定時，也接收 PowerShell 遠端命令。</span><span class="sxs-lookup"><span data-stu-id="3ad79-132">To allow DSC to run, Windows needs to be configured to receive PowerShell remote commands even when you're running a `localhost` configuration.</span></span> <span data-ttu-id="3ad79-133">若要輕鬆正確地設定您的環境，只要在已提高權限的 PowerShell 終端機中執行 `Set-WsManQuickConfig -Force` 即可。</span><span class="sxs-lookup"><span data-stu-id="3ad79-133">To easily configure your environment correctly, just run `Set-WsManQuickConfig -Force` in an elevated PowerShell Terminal.</span></span>

<span data-ttu-id="3ad79-134">您可以使用 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) Cmdlet 將設定文件 (MOF 檔案) 套用至機器。</span><span class="sxs-lookup"><span data-stu-id="3ad79-134">Configuration documents (MOF files) can be applied to the machineusing the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

```powershell
Start-DscConfiguration -Path 'C:\EnvironmentVariable_Path' -Wait -Verbose
```

#### <a name="get-the-current-state-of-the-configuration"></a><span data-ttu-id="3ad79-135">取得設定的目前狀態</span><span class="sxs-lookup"><span data-stu-id="3ad79-135">Get the current state of the configuration</span></span>

<span data-ttu-id="3ad79-136">[Get-DscConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) Cmdlet 會查詢機器的目前狀態，並傳回設定的目前值。</span><span class="sxs-lookup"><span data-stu-id="3ad79-136">The [Get-DscConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet queries the current status of the machine and returns the current values for the configuration.</span></span>

```powershell
Get-DscConfiguration
```

<span data-ttu-id="3ad79-137">[Get-DscLocalConfigurationManager](/powershell/module/psdesiredstateconfiguration/get-dscLocalConfigurationManager) Cmdlet 會傳回套用至電腦的目前中繼設定。</span><span class="sxs-lookup"><span data-stu-id="3ad79-137">The [Get-DscLocalConfigurationManager](/powershell/module/psdesiredstateconfiguration/get-dscLocalConfigurationManager) cmdlet returns the current meta-configuration applied to the machine.</span></span>

```powershell
Get-DscLocalConfigurationManager
```

#### <a name="remove-the-current-configuration-from-a-machine"></a><span data-ttu-id="3ad79-138">將目前設定從電腦移除</span><span class="sxs-lookup"><span data-stu-id="3ad79-138">Remove the current configuration from a machine</span></span>

<span data-ttu-id="3ad79-139">[Remove-DscConfigurationDocument](/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument)</span><span class="sxs-lookup"><span data-stu-id="3ad79-139">The [Remove-DscConfigurationDocument](/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument)</span></span>

```powershell
Remove-DscConfigurationDocument -Stage Current -Verbose
```

#### <a name="configure-settings-in-local-configuration-manager"></a><span data-ttu-id="3ad79-140">設定本機 Configuration Manager 中的設定</span><span class="sxs-lookup"><span data-stu-id="3ad79-140">Configure settings in Local Configuration Manager</span></span>

<span data-ttu-id="3ad79-141">使用 [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) Cmdlet，將中繼設定 MOF 檔案套用至電腦。</span><span class="sxs-lookup"><span data-stu-id="3ad79-141">Apply a Meta Configuration MOF file to the machine using the [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet.</span></span>
<span data-ttu-id="3ad79-142">需要中繼設定 MOF 路徑。</span><span class="sxs-lookup"><span data-stu-id="3ad79-142">Requires the path to the Meta Configuration MOF.</span></span>

```powershell
Set-DSCLocalConfigurationManager -Path 'c:\metaconfig\localhost.meta.mof' -Verbose
```

## <a name="windows-powershell-desired-state-configuration-log-files"></a><span data-ttu-id="3ad79-143">Windows PowerShell Desired State Configuration 記錄檔</span><span class="sxs-lookup"><span data-stu-id="3ad79-143">Windows PowerShell Desired State Configuration log files</span></span>

<span data-ttu-id="3ad79-144">DSC 的記錄會寫入在路徑 `Microsoft-Windows-Dsc/Operational` 中的 Windows 事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="3ad79-144">Logs for DSC are written to Windows Event Log in the path `Microsoft-Windows-Dsc/Operational`.</span></span>
<span data-ttu-id="3ad79-145">您可以遵循 [DSC 事件記錄檔在哪裡](/powershell/scripting/dsc/troubleshooting/troubleshooting#where-are-dsc-event-logs)中的步驟，啟用用於偵錯工具的其他記錄檔。</span><span class="sxs-lookup"><span data-stu-id="3ad79-145">Additional logs for debugging purposes can be enabled following the steps in [Where Are DSC Event Logs](/powershell/scripting/dsc/troubleshooting/troubleshooting#where-are-dsc-event-logs).</span></span>
