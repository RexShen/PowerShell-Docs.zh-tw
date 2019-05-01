---
ms.date: 12/12/2018
keywords: dsc, powershell, 資源, 資源庫, 安裝, 設定
title: 安裝額外的 DSC 資源
ms.openlocfilehash: ecaf176230ccd934b57b1c27d72ff83e6ba906e9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080068"
---
# <a name="install-additional-dsc-resources"></a><span data-ttu-id="9769e-103">安裝額外的 DSC 資源</span><span class="sxs-lookup"><span data-stu-id="9769e-103">Install Additional DSC Resources</span></span>

<span data-ttu-id="9769e-104">PowerShell 包含幾個適用於 Desired State Configuration (DSC) 的立即可用資源。</span><span class="sxs-lookup"><span data-stu-id="9769e-104">PowerShell includes several Out-of-the-box resources for Desired State Configuration (DSC).</span></span> <span data-ttu-id="9769e-105">**PSDesiredStateConfiguration** 模組包含所有 OOB DSC 資源，可供您的特定 PowerShell 執行個體使用。</span><span class="sxs-lookup"><span data-stu-id="9769e-105">The **PSDesiredStateConfiguration** module contains all of the OOB DSC resources available on your specific instance of PowerShell.</span></span>

<span data-ttu-id="9769e-106">這是 PowerShell 4.0 中包含的 OOB 資源清單和資源功能描述。</span><span class="sxs-lookup"><span data-stu-id="9769e-106">This is a list of the OOB resources included in PowerShell 4.0 and a description of the resource's capabilities.</span></span>

> [!NOTE]
> <span data-ttu-id="9769e-107">此清單並不完整，因為 OOB 資源的數量會隨著 PowerShell 的每個版本而增加。</span><span class="sxs-lookup"><span data-stu-id="9769e-107">This is an incomplete list, as the number of OOB resources has grown with each version of PowerShell.</span></span>

|<span data-ttu-id="9769e-108">資源</span><span class="sxs-lookup"><span data-stu-id="9769e-108">Resource</span></span>  |<span data-ttu-id="9769e-109">描述</span><span class="sxs-lookup"><span data-stu-id="9769e-109">Description</span></span>  |
|---------|---------|
|<span data-ttu-id="9769e-110">**檔案**</span><span class="sxs-lookup"><span data-stu-id="9769e-110">**File**</span></span>|<span data-ttu-id="9769e-111">控制檔案和目錄的狀態。</span><span class="sxs-lookup"><span data-stu-id="9769e-111">Controls the state of files and directories.</span></span> <span data-ttu-id="9769e-112">在**來源**變更時將檔案從**來源**複製到**目的地**，並藉由比較日期、總和檢查碼和雜湊更新檔案。</span><span class="sxs-lookup"><span data-stu-id="9769e-112">Copies files from a **Source** to a **Destination** and updates them when the **Source** changes by comparing dates, checksums, and hashes.</span></span>|
|<span data-ttu-id="9769e-113">**封存**</span><span class="sxs-lookup"><span data-stu-id="9769e-113">**Archive**</span></span>|<span data-ttu-id="9769e-114">將封存和指定位置解除封裝。</span><span class="sxs-lookup"><span data-stu-id="9769e-114">Unpacks archives and a specified location.</span></span> <span data-ttu-id="9769e-115">驗證封存具有指定的**總和檢查碼**。</span><span class="sxs-lookup"><span data-stu-id="9769e-115">Validates the archives with a specified **Checksum**.</span></span>|
|<span data-ttu-id="9769e-116">**環境**</span><span class="sxs-lookup"><span data-stu-id="9769e-116">**Environment**</span></span>|<span data-ttu-id="9769e-117">管理環境變數。</span><span class="sxs-lookup"><span data-stu-id="9769e-117">Manages environment variables.</span></span>|
|<span data-ttu-id="9769e-118">**群組**</span><span class="sxs-lookup"><span data-stu-id="9769e-118">**Group**</span></span>|<span data-ttu-id="9769e-119">管理本機群組並控制群組成員資格。</span><span class="sxs-lookup"><span data-stu-id="9769e-119">Manages local groups and controls group membership.</span></span>|
|<span data-ttu-id="9769e-120">**Log**</span><span class="sxs-lookup"><span data-stu-id="9769e-120">**Log**</span></span>|<span data-ttu-id="9769e-121">將訊息寫入至 `Microsoft-Windows-Desired State Configuration/Analytic` 事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="9769e-121">Writes messages to the `Microsoft-Windows-Desired State Configuration/Analytic` event log.</span></span>|
|<span data-ttu-id="9769e-122">**套件**</span><span class="sxs-lookup"><span data-stu-id="9769e-122">**Package**</span></span>|<span data-ttu-id="9769e-123">使用**引數**、**LogPath**、**ReturnCode** 和其他設定安裝套件或解除安裝套件。</span><span class="sxs-lookup"><span data-stu-id="9769e-123">Installs or uninstalls packages using **Arguments**, **LogPath**, **ReturnCode**, other settings.</span></span>|
|<span data-ttu-id="9769e-124">**Registry**</span><span class="sxs-lookup"><span data-stu-id="9769e-124">**Registry**</span></span>|<span data-ttu-id="9769e-125">管理登錄機碼和值。</span><span class="sxs-lookup"><span data-stu-id="9769e-125">Manages registry keys and values.</span></span>|
|<span data-ttu-id="9769e-126">**Script**</span><span class="sxs-lookup"><span data-stu-id="9769e-126">**Script**</span></span>|<span data-ttu-id="9769e-127">可讓您設計自己的[取得-測試-設定](../resources/get-test-set.md)指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="9769e-127">Allows you to design your own [get-test-set](../resources/get-test-set.md) script blocks.</span></span>|
|<span data-ttu-id="9769e-128">**Service**</span><span class="sxs-lookup"><span data-stu-id="9769e-128">**Service**</span></span>|<span data-ttu-id="9769e-129">設定 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="9769e-129">Configures Windows services.</span></span>|
|<span data-ttu-id="9769e-130">**User**</span><span class="sxs-lookup"><span data-stu-id="9769e-130">**User**</span></span> |<span data-ttu-id="9769e-131">管理本機使用者和屬性。</span><span class="sxs-lookup"><span data-stu-id="9769e-131">Manages local users and attributes.</span></span>|
|<span data-ttu-id="9769e-132">**WindowsFeature**</span><span class="sxs-lookup"><span data-stu-id="9769e-132">**WindowsFeature**</span></span>|<span data-ttu-id="9769e-133">管理角色和功能。</span><span class="sxs-lookup"><span data-stu-id="9769e-133">Manages roles and features.</span></span>|
|<span data-ttu-id="9769e-134">**WindowsProcess**</span><span class="sxs-lookup"><span data-stu-id="9769e-134">**WindowsProcess**</span></span>|<span data-ttu-id="9769e-135">設定 Windows 處理序。</span><span class="sxs-lookup"><span data-stu-id="9769e-135">Configures Windows processes.</span></span>|

<span data-ttu-id="9769e-136">OOB 資源是適合一般作業的良好起點。</span><span class="sxs-lookup"><span data-stu-id="9769e-136">The OOB resources allow a good starting point for common operations.</span></span> <span data-ttu-id="9769e-137">如果 OOB 資源不能滿足您的需求，您可以撰寫自己的[自訂資源](../resources/authoringResource.md)。</span><span class="sxs-lookup"><span data-stu-id="9769e-137">If the OOB resources do not meet your needs, you can write your own [Custom Resource](../resources/authoringResource.md).</span></span> <span data-ttu-id="9769e-138">在撰寫自訂資源來解決問題之前，您應該先瀏覽由 Microsoft 和 PowerShell 社群建立的大量 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="9769e-138">Before you write a custom resource to solve your problem, you should look through the vast number of DSC resources that have already been created by both Microsoft and the PowerShell community.</span></span>

<span data-ttu-id="9769e-139">您可以在 [PowerShell 資源庫](https://www.powershellgallery.com/)和 [GitHub](https://github.com/) 中找到 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="9769e-139">You can find DSC resources in both the [PowerShell Gallery](https://www.powershellgallery.com/) and [GitHub](https://github.com/).</span></span> <span data-ttu-id="9769e-140">您也可以直接從 PowerShell 主控台中使用 [PowerShellGet](/powershell/module/powershellget/) 來安裝 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="9769e-140">You can also install DSC resources directly from the PowerShell console using [PowerShellGet](/powershell/module/powershellget/).</span></span>

## <a name="installing-powershellget"></a><span data-ttu-id="9769e-141">安裝 PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="9769e-141">Installing PowerShellGet</span></span>

<span data-ttu-id="9769e-142">若要判斷您是否已有 **PowerShellGet**，或是要取得安裝協助，請參閱下列指南：[安裝 PowerShellGet](/powershell/gallery/installing-psget)。</span><span class="sxs-lookup"><span data-stu-id="9769e-142">To determine if you already have **PowerShell** get, or to get help installing it, see the following guide: [Installing PowerShellGet](/powershell/gallery/installing-psget).</span></span>

## <a name="finding-dsc-resources-using-powershellget"></a><span data-ttu-id="9769e-143">使用 PowerShellGet 尋找 DSC 資源</span><span class="sxs-lookup"><span data-stu-id="9769e-143">Finding DSC resources using PowerShellGet</span></span>

<span data-ttu-id="9769e-144">一旦在系統上安裝 **PowerShellGet** 之後，您就可以尋找並安裝於 [PowerShell 資源庫](https://www.powershellgallery.com/)中裝載的 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="9769e-144">Once **PowerShellGet** is installed on your system, you can find and install DSC resources hosted in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>

<span data-ttu-id="9769e-145">首先，使用 [Find-DSCResource](/powershell/module/powershellget/find-dscresource) Cmdlet 尋找 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="9769e-145">First, use the [Find-DSCResource](/powershell/module/powershellget/find-dscresource) cmdlet to find DSC resources.</span></span> <span data-ttu-id="9769e-146">當您第一次執行 `Find-DSCResource` 時，您會看到以下安裝「NuGet 提供者」的提示。</span><span class="sxs-lookup"><span data-stu-id="9769e-146">When you run `Find-DSCResource` for the first time, you see the following prompt to install the "NuGet provider".</span></span>

```
PS> Find-DSCResource

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The
NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\xAdministrator\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider
 by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to
install and import the NuGet provider now?
[Y] Yes  [N] No  [?] Help (default is "Y"):
```

<span data-ttu-id="9769e-147">按下 'y' 後隨即會安裝 "NuGet" 提供者，您會看到可從 PowerShell 資源庫安裝的 DSC 資源清單。</span><span class="sxs-lookup"><span data-stu-id="9769e-147">After pressing 'y', the "NuGet" provider is installed, you see a list of DSC resources that you can install from the PowerShell Gallery.</span></span>

> [!NOTE]
> <span data-ttu-id="9769e-148">因為清單非常大，故在此不顯示。</span><span class="sxs-lookup"><span data-stu-id="9769e-148">List is not shown because it is very large.</span></span>

<span data-ttu-id="9769e-149">您也可以使用萬用字元指定 `-Name` 參數，或不含萬用字元的 `-Filter` 參數來縮小搜尋範圍。</span><span class="sxs-lookup"><span data-stu-id="9769e-149">You can also specify the `-Name` parameter using wildcards, or `-Filter` parameter without wildcards to narrow down your search.</span></span> <span data-ttu-id="9769e-150">此範例會使用萬用字元嘗試尋找 "TimeZone" (時區) 的 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="9769e-150">This example attempts to find a "TimeZone" DSC resource using the wildcards.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9769e-151">`Find-DSCResource` Cmdlet 目前有錯誤 (Bug)，無法在 `-Name` 和 `-Filter` 參數中使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="9769e-151">Currently there is a bug in the `Find-DSCResource` cmdlet that prevents using wildcards in both the `-Name` and `-Filter` parameters.</span></span> <span data-ttu-id="9769e-152">下列第二個範例示範使用 `Where-Object` 的因應措施。</span><span class="sxs-lookup"><span data-stu-id="9769e-152">The second example below shows a workaround using `Where-Object`.</span></span>

```
PS> Find-DSCResource -Name *Time*

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Carbon_EnvironmentVariable          2.6.0      Carbon                              PSGallery
Carbon_FirewallRule                 2.6.0      Carbon                              PSGallery
Carbon_Group                        2.6.0      Carbon                              PSGallery
Carbon_IniFile                      2.6.0      Carbon                              PSGallery
Carbon_Permission                   2.6.0      Carbon                              PSGallery
Carbon_Privilege                    2.6.0      Carbon                              PSGallery
Carbon_ScheduledTask                2.6.0      Carbon                              PSGallery
Carbon_Service                      2.6.0      Carbon                              PSGallery
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
xTimeZone                           1.8.0.0    xTimeZone                           PSGallery
xSqlServerDefaultDir                1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerMoveDatabaseFiles         1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerSQLDataRoot               1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerStartupParam              1.0.0      mlSqlServerDSC                      PSGallery
```

<span data-ttu-id="9769e-153">您也可以使用 `Where-Object` 以更細微的篩選來尋找 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="9769e-153">You can also use `Where-Object` to find DSC resources with more granular filtering.</span></span> <span data-ttu-id="9769e-154">這個方法會比使用內建的篩選參數慢。</span><span class="sxs-lookup"><span data-stu-id="9769e-154">This approach will be slower than using built in filtering parameters.</span></span>

```
PS> Find-DSCResource | Where-Object {$_.Name -like "Time*"}

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
```

<span data-ttu-id="9769e-155">如需有關篩選的詳細資訊，請參閱 [Where-Object](/powershell/module/microsoft.powershell.core/where-object)。</span><span class="sxs-lookup"><span data-stu-id="9769e-155">For more information on filtering, see [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span></span>

## <a name="installing-dsc-resources-using-powershellget"></a><span data-ttu-id="9769e-156">使用 PowerShellGet 安裝 DSC 資源</span><span class="sxs-lookup"><span data-stu-id="9769e-156">Installing DSC Resources using PowerShellGet</span></span>

<span data-ttu-id="9769e-157">若要安裝 DSC 資源，請使用 [Install-Module](/powershell/module/PowershellGet/Install-Module) Cmdlet，指定搜尋結果中顯示在**模組**名稱底下的模組名稱。</span><span class="sxs-lookup"><span data-stu-id="9769e-157">To install a DSC resource, use the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet, specifying the name of the module shown under **Module** name in your search results.</span></span>

<span data-ttu-id="9769e-158">"TimeZone" 資源存在於 "ComputerManagementDSC" 模組中，也就是此範例會安裝的模組。</span><span class="sxs-lookup"><span data-stu-id="9769e-158">The "TimeZone" resource exists in the "ComputerManagementDSC" module, so that is the module this example installs.</span></span>

> [!NOTE]
> <span data-ttu-id="9769e-159">如果您有不受信任的 PowerShell 資源庫，則會看到要求確認的警告，以及指示您如何避免後續的安裝提示。</span><span class="sxs-lookup"><span data-stu-id="9769e-159">If you have not trusted the PowerShell gallery, you see the warning below asking for confirmation, and instructing you how to avoid subsequent prompts on installs.</span></span>

```
PS> Install-Module -Name ComputerManagementDSC

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

<span data-ttu-id="9769e-160">按 'y' 以繼續安裝模組。</span><span class="sxs-lookup"><span data-stu-id="9769e-160">Press 'y' to continue installing the module.</span></span> <span data-ttu-id="9769e-161">安裝之後，您可以使用 [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) 確認已安裝新的資源。</span><span class="sxs-lookup"><span data-stu-id="9769e-161">After install, you can verify that your new resource is installed using [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).</span></span>

```
PS> Get-DSCResource -Name TimeZone -Syntax

TimeZone [String] #ResourceName
{
    IsSingleInstance = [string]{ Yes }
    TimeZone = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
}
```

<span data-ttu-id="9769e-162">您也可以透過指定 `-ModuleName` 參數來檢視新安裝的其他資源。</span><span class="sxs-lookup"><span data-stu-id="9769e-162">You can also view other resources in your newly installed module, by specifying the `-ModuleName` parameter.</span></span>

```
PS> Get-DSCResource -Module ComputerManagementDSC

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      Computer                  ComputerManagementDsc          6.0.0.0    {Name, Credential, DependsOn, ...
PowerShell      OfflineDomainJoin         ComputerManagementDsc          6.0.0.0    {IsSingleInstance, RequestFile...
PowerShell      PowerPlan                 ComputerManagementDsc          6.0.0.0    {IsSingleInstance, Name, Depen...
PowerShell      PowerShellExecutionPolicy ComputerManagementDsc          6.0.0.0    {ExecutionPolicy, ExecutionPol...
PowerShell      ScheduledTask             ComputerManagementDsc          6.0.0.0    {TaskName, ActionArguments, Ac...
PowerShell      TimeZone                  ComputerManagementDsc          6.0.0.0    {IsSingleInstance, TimeZone, D...
PowerShell      VirtualMemory             ComputerManagementDsc          6.0.0.0    {Drive, Type, DependsOn, Initi...
```

## <a name="see-also"></a><span data-ttu-id="9769e-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9769e-163">See also</span></span>

- [<span data-ttu-id="9769e-164">何謂資源？</span><span class="sxs-lookup"><span data-stu-id="9769e-164">What are Resources?</span></span>](../resources/resources.md)
