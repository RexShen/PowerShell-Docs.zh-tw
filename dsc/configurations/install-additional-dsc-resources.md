---
ms.date: 12/12/2018
keywords: dsc，powershell、 資源、 資源庫、 安裝程式
title: 安裝額外的 DSC 資源
ms.openlocfilehash: ecaf176230ccd934b57b1c27d72ff83e6ba906e9
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400835"
---
# <a name="install-additional-dsc-resources"></a><span data-ttu-id="4c7d4-103">安裝額外的 DSC 資源</span><span class="sxs-lookup"><span data-stu-id="4c7d4-103">Install Additional DSC Resources</span></span>

<span data-ttu-id="4c7d4-104">PowerShell 包含幾個的立即可用資源的 Desired State Configuration (DSC)。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-104">PowerShell includes several Out-of-the-box resources for Desired State Configuration (DSC).</span></span> <span data-ttu-id="4c7d4-105">**PSDesiredStateConfiguration**模組包含的所有 OOB DSC 資源可在您的 PowerShell 的特定執行個體上取得。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-105">The **PSDesiredStateConfiguration** module contains all of the OOB DSC resources available on your specific instance of PowerShell.</span></span>

<span data-ttu-id="4c7d4-106">這是包含在 PowerShell 4.0 和資源的功能描述的 OOB 資源的清單。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-106">This is a list of the OOB resources included in PowerShell 4.0 and a description of the resource's capabilities.</span></span>

> [!NOTE]
> <span data-ttu-id="4c7d4-107">這是不完整的清單中，OOB 資源數目變得與每個版本的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-107">This is an incomplete list, as the number of OOB resources has grown with each version of PowerShell.</span></span>

|<span data-ttu-id="4c7d4-108">資源</span><span class="sxs-lookup"><span data-stu-id="4c7d4-108">Resource</span></span>  |<span data-ttu-id="4c7d4-109">描述</span><span class="sxs-lookup"><span data-stu-id="4c7d4-109">Description</span></span>  |
|---------|---------|
|<span data-ttu-id="4c7d4-110">**File**</span><span class="sxs-lookup"><span data-stu-id="4c7d4-110">**File**</span></span>|<span data-ttu-id="4c7d4-111">控制檔案和目錄的狀態。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-111">Controls the state of files and directories.</span></span> <span data-ttu-id="4c7d4-112">將從檔案複製**來源**要**目的地**，加以更新時**來源**藉由比較日期、 總和檢查碼，以及雜湊的變更。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-112">Copies files from a **Source** to a **Destination** and updates them when the **Source** changes by comparing dates, checksums, and hashes.</span></span>|
|<span data-ttu-id="4c7d4-113">**Archive**</span><span class="sxs-lookup"><span data-stu-id="4c7d4-113">**Archive**</span></span>|<span data-ttu-id="4c7d4-114">解壓縮封存和指定的位置。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-114">Unpacks archives and a specified location.</span></span> <span data-ttu-id="4c7d4-115">驗證具有指定的封存**總和檢查碼**。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-115">Validates the archives with a specified **Checksum**.</span></span>|
|<span data-ttu-id="4c7d4-116">**Environment**</span><span class="sxs-lookup"><span data-stu-id="4c7d4-116">**Environment**</span></span>|<span data-ttu-id="4c7d4-117">管理的環境變數。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-117">Manages environment variables.</span></span>|
|<span data-ttu-id="4c7d4-118">**群組**</span><span class="sxs-lookup"><span data-stu-id="4c7d4-118">**Group**</span></span>|<span data-ttu-id="4c7d4-119">管理本機群組，並控制群組成員資格。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-119">Manages local groups and controls group membership.</span></span>|
|<span data-ttu-id="4c7d4-120">**Log**</span><span class="sxs-lookup"><span data-stu-id="4c7d4-120">**Log**</span></span>|<span data-ttu-id="4c7d4-121">寫入訊息至`Microsoft-Windows-Desired State Configuration/Analytic`事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-121">Writes messages to the `Microsoft-Windows-Desired State Configuration/Analytic` event log.</span></span>|
|<span data-ttu-id="4c7d4-122">**套件**</span><span class="sxs-lookup"><span data-stu-id="4c7d4-122">**Package**</span></span>|<span data-ttu-id="4c7d4-123">安裝或解除安裝使用的套件**引數**， **LogPath**， **ReturnCode**，其他設定。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-123">Installs or uninstalls packages using **Arguments**, **LogPath**, **ReturnCode**, other settings.</span></span>|
|<span data-ttu-id="4c7d4-124">**Registry**</span><span class="sxs-lookup"><span data-stu-id="4c7d4-124">**Registry**</span></span>|<span data-ttu-id="4c7d4-125">管理登錄機碼和值。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-125">Manages registry keys and values.</span></span>|
|<span data-ttu-id="4c7d4-126">**Script**</span><span class="sxs-lookup"><span data-stu-id="4c7d4-126">**Script**</span></span>|<span data-ttu-id="4c7d4-127">可讓您設計您自己[取得測試設定](../resources/get-test-set.md)指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-127">Allows you to design your own [get-test-set](../resources/get-test-set.md) script blocks.</span></span>|
|<span data-ttu-id="4c7d4-128">**Service**</span><span class="sxs-lookup"><span data-stu-id="4c7d4-128">**Service**</span></span>|<span data-ttu-id="4c7d4-129">設定 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-129">Configures Windows services.</span></span>|
|<span data-ttu-id="4c7d4-130">**User**</span><span class="sxs-lookup"><span data-stu-id="4c7d4-130">**User**</span></span> |<span data-ttu-id="4c7d4-131">管理本機使用者和屬性。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-131">Manages local users and attributes.</span></span>|
|<span data-ttu-id="4c7d4-132">**WindowsFeature**</span><span class="sxs-lookup"><span data-stu-id="4c7d4-132">**WindowsFeature**</span></span>|<span data-ttu-id="4c7d4-133">管理角色和功能。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-133">Manages roles and features.</span></span>|
|<span data-ttu-id="4c7d4-134">**WindowsProcess**</span><span class="sxs-lookup"><span data-stu-id="4c7d4-134">**WindowsProcess**</span></span>|<span data-ttu-id="4c7d4-135">設定 Windows 處理程序。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-135">Configures Windows processes.</span></span>|

<span data-ttu-id="4c7d4-136">OOB 資源可讓一般作業的不錯的起點。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-136">The OOB resources allow a good starting point for common operations.</span></span> <span data-ttu-id="4c7d4-137">如果 OOB 資源不符合您的需求，您可以撰寫您自己[自訂資源](../resources/authoringResource.md)。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-137">If the OOB resources do not meet your needs, you can write your own [Custom Resource](../resources/authoringResource.md).</span></span> <span data-ttu-id="4c7d4-138">撰寫自訂的資源，為您解決問題之前，您應該瀏覽大量已由 Microsoft 和 PowerShell 社群的 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-138">Before you write a custom resource to solve your problem, you should look through the vast number of DSC resources that have already been created by both Microsoft and the PowerShell community.</span></span>

<span data-ttu-id="4c7d4-139">您可以在同時尋找 DSC 資源[PowerShell 資源庫](https://www.powershellgallery.com/)並[GitHub](https://github.com/)。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-139">You can find DSC resources in both the [PowerShell Gallery](https://www.powershellgallery.com/) and [GitHub](https://github.com/).</span></span> <span data-ttu-id="4c7d4-140">您也可以直接從 PowerShell 主控台中使用安裝 DSC 資源[PowerShellGet](/powershell/module/powershellget/)。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-140">You can also install DSC resources directly from the PowerShell console using [PowerShellGet](/powershell/module/powershellget/).</span></span>

## <a name="installing-powershellget"></a><span data-ttu-id="4c7d4-141">安裝 PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="4c7d4-141">Installing PowerShellGet</span></span>

<span data-ttu-id="4c7d4-142">若要判斷您是否已有**PowerShell**取得，或若要取得安裝協助，請參閱下列指南：[安裝 PowerShellGet](/powershell/gallery/installing-psget)</span><span class="sxs-lookup"><span data-stu-id="4c7d4-142">To determine if you already have **PowerShell** get, or to get help installing it, see the following guide: [Installing PowerShellGet](/powershell/gallery/installing-psget).</span></span>

## <a name="finding-dsc-resources-using-powershellget"></a><span data-ttu-id="4c7d4-143">尋找使用 PowerShellGet 的 DSC 資源</span><span class="sxs-lookup"><span data-stu-id="4c7d4-143">Finding DSC resources using PowerShellGet</span></span>

<span data-ttu-id="4c7d4-144">一次**PowerShellGet**安裝在您系統上，您可以尋找並安裝在裝載的 DSC 資源[PowerShell 資源庫](https://www.powershellgallery.com/)。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-144">Once **PowerShellGet** is installed on your system, you can find and install DSC resources hosted in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>

<span data-ttu-id="4c7d4-145">首先，使用[Find-dscresource](/powershell/module/powershellget/find-dscresource) cmdlet 來尋找 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-145">First, use the [Find-DSCResource](/powershell/module/powershellget/find-dscresource) cmdlet to find DSC resources.</span></span> <span data-ttu-id="4c7d4-146">當您執行`Find-DSCResource`第一次，您會看到下列提示來安裝 「 NuGet 提供者 」。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-146">When you run `Find-DSCResource` for the first time, you see the following prompt to install the "NuGet provider".</span></span>

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

<span data-ttu-id="4c7d4-147">之後按 'y' 安裝"NuGet"提供者，您會看到一份您可以從 「 PowerShell 資源庫安裝的 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-147">After pressing 'y', the "NuGet" provider is installed, you see a list of DSC resources that you can install from the PowerShell Gallery.</span></span>

> [!NOTE]
> <span data-ttu-id="4c7d4-148">因為它是非常大，不會顯示清單。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-148">List is not shown because it is very large.</span></span>

<span data-ttu-id="4c7d4-149">您也可以指定`-Name`參數中使用萬用字元，或`-Filter`不含萬用字元來縮小搜尋範圍的參數。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-149">You can also specify the `-Name` parameter using wildcards, or `-Filter` parameter without wildcards to narrow down your search.</span></span> <span data-ttu-id="4c7d4-150">此範例會嘗試尋找 「 時區 」 DSC 資源使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-150">This example attempts to find a "TimeZone" DSC resource using the wildcards.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4c7d4-151">目前沒有中的 bug `Find-DSCResource` cmdlet，以防止在兩者中使用萬用字元`-Name`和`-Filter`參數。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-151">Currently there is a bug in the `Find-DSCResource` cmdlet that prevents using wildcards in both the `-Name` and `-Filter` parameters.</span></span> <span data-ttu-id="4c7d4-152">下列第二個範例顯示如何因應措施，使用`Where-Object`。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-152">The second example below shows a workaround using `Where-Object`.</span></span>

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

<span data-ttu-id="4c7d4-153">您也可以使用`Where-Object`來尋找具有更細微的篩選的 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-153">You can also use `Where-Object` to find DSC resources with more granular filtering.</span></span> <span data-ttu-id="4c7d4-154">這個方法會比使用內建的篩選參數慢。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-154">This approach will be slower than using built in filtering parameters.</span></span>

```
PS> Find-DSCResource | Where-Object {$_.Name -like "Time*"}

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
```

<span data-ttu-id="4c7d4-155">如需有關篩選的詳細資訊，請參閱 < [Where-object](/powershell/module/microsoft.powershell.core/where-object)。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-155">For more information on filtering, see [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span></span>

## <a name="installing-dsc-resources-using-powershellget"></a><span data-ttu-id="4c7d4-156">安裝使用 PowerShellGet 的 DSC 資源</span><span class="sxs-lookup"><span data-stu-id="4c7d4-156">Installing DSC Resources using PowerShellGet</span></span>

<span data-ttu-id="4c7d4-157">若要安裝 DSC 資源，請使用[Install-module](/powershell/module/PowershellGet/Install-Module) cmdlet，並指定下方顯示的模組名稱**模組**名稱在您的搜尋結果中。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-157">To install a DSC resource, use the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet, specifying the name of the module shown under **Module** name in your search results.</span></span>

<span data-ttu-id="4c7d4-158">「 時區 」 資源存在於"ComputerManagementDSC 」 模組，因此也就是模組此範例會安裝。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-158">The "TimeZone" resource exists in the "ComputerManagementDSC" module, so that is the module this example installs.</span></span>

> [!NOTE]
> <span data-ttu-id="4c7d4-159">如果您有不受信任 「 PowerShell 資源庫，您會看到以下要求確認，警告，並指示您要如何避免後續提示上安裝。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-159">If you have not trusted the PowerShell gallery, you see the warning below asking for confirmation, and instructing you how to avoid subsequent prompts on installs.</span></span>

```
PS> Install-Module -Name ComputerManagementDSC

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

<span data-ttu-id="4c7d4-160">按 'y' 以繼續安裝模組。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-160">Press 'y' to continue installing the module.</span></span> <span data-ttu-id="4c7d4-161">安裝之後，您可以確認已安裝使用新的資源[Get-dscresource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-161">After install, you can verify that your new resource is installed using [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).</span></span>

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

<span data-ttu-id="4c7d4-162">您也可以檢視您新安裝的模組中的其他資源，藉由指定`-ModuleName`參數。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-162">You can also view other resources in your newly installed module, by specifying the `-ModuleName` parameter.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4c7d4-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c7d4-163">See also</span></span>

- [<span data-ttu-id="4c7d4-164">何謂資源？</span><span class="sxs-lookup"><span data-stu-id="4c7d4-164">What are Resources?</span></span>](../resources/resources.md)
