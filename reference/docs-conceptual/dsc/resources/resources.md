---
ms.date: 02/28/2020
keywords: dsc,powershell,設定,安裝
title: DSC 資源
ms.openlocfilehash: 863898d910cc3c75c3e5977a5b6b0657ba7ed512
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "78278236"
---
# <a name="dsc-resources"></a><span data-ttu-id="8331e-103">DSC 資源</span><span class="sxs-lookup"><span data-stu-id="8331e-103">DSC Resources</span></span>

> <span data-ttu-id="8331e-104">適用於 Windows PowerShell 4.0 與更新版本。</span><span class="sxs-lookup"><span data-stu-id="8331e-104">Applies to Windows PowerShell 4.0 and up.</span></span>

## <a name="overview"></a><span data-ttu-id="8331e-105">概觀</span><span class="sxs-lookup"><span data-stu-id="8331e-105">Overview</span></span>

<span data-ttu-id="8331e-106">預期狀態設定 (DSC) 資源提供 DSC 設定的建置組塊。</span><span class="sxs-lookup"><span data-stu-id="8331e-106">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="8331e-107">資源會公開可以設定的屬性 (結構描述)，而且這些屬性包含本機設定管理員 (LCM) 稱之為「make it so (讓它變成這樣)」的 PowerShell 指令碼函式。</span><span class="sxs-lookup"><span data-stu-id="8331e-107">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="8331e-108">資源可以建立某些物件的模型，像檔案一樣平常或如 IIS 伺服器設定一樣專用。</span><span class="sxs-lookup"><span data-stu-id="8331e-108">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span> <span data-ttu-id="8331e-109">類似資源的群組會併入 DSC 模組，將所有必要的檔案組織到可攜式結構中，而且包含中繼資料以識別資源的原訂用法。</span><span class="sxs-lookup"><span data-stu-id="8331e-109">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

<span data-ttu-id="8331e-110">每個資源都有一個\*結構描述，可判斷在[設定](../configurations/configurations.md)中使用資源所需的語法。</span><span class="sxs-lookup"><span data-stu-id="8331e-110">Each resource has a \*schema that determines the syntax needed to use the resource in a [Configuration](../configurations/configurations.md).</span></span>
<span data-ttu-id="8331e-111">您可以透過下列方式定義資源的結構描述：</span><span class="sxs-lookup"><span data-stu-id="8331e-111">A resource's schema can be defined in the following ways:</span></span>

- <span data-ttu-id="8331e-112">**'Schema.Mof'** 檔案：大部分的資源都會使用[受控物件格式](/windows/desktop/wmisdk/managed-object-format--mof-)，在 '.schema.mof' 檔案中定義其「結構描述」  。</span><span class="sxs-lookup"><span data-stu-id="8331e-112">**'Schema.Mof'** file: Most resources define their _schema_ in a 'schema.mof' file, using [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>
- <span data-ttu-id="8331e-113">**'\<資源名稱\>.schema.psm1'** 檔案：[複合資源](../configurations/compositeConfigs.md)會使用[參數區塊](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters)，在 '<ResourceName>.schema.psm1' 檔案中定義其「結構描述」  。</span><span class="sxs-lookup"><span data-stu-id="8331e-113">**'\<Resource Name\>.schema.psm1'** file: [Composite Resources](../configurations/compositeConfigs.md) define their *schema* in a '<ResourceName>.schema.psm1' file using a [Parameter Block](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).</span></span>
- <span data-ttu-id="8331e-114">**'\<資源名稱\>.psm1'** 檔案：以類別為基礎的 DSC 資源會在類別定義中定義其「結構描述」  。</span><span class="sxs-lookup"><span data-stu-id="8331e-114">**'\<Resource Name\>.psm1'** file: Class based DSC resources define their _schema_ in the class definition.</span></span> <span data-ttu-id="8331e-115">語法項目會標示為 Class 屬性。</span><span class="sxs-lookup"><span data-stu-id="8331e-115">Syntax items are denoted as Class properties.</span></span> <span data-ttu-id="8331e-116">如需詳細資訊，請參閱 [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc)。</span><span class="sxs-lookup"><span data-stu-id="8331e-116">For more information, see [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span></span>

<span data-ttu-id="8331e-117">若要擷取 DSC 資源的語法，請搭配 `-Syntax` 參數使用 [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8331e-117">To retrieve the syntax for a DSC resource, use the [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet with the `-Syntax` parameter.</span></span> <span data-ttu-id="8331e-118">此使用方式類似於搭配 `-Syntax` 參數使用 [Get-Command](/powershell/module/microsoft.powershell.core/get-command) 來取得 Cmdlet 語法。</span><span class="sxs-lookup"><span data-stu-id="8331e-118">This usage is similar to using [Get-Command](/powershell/module/microsoft.powershell.core/get-command) with the `-Syntax` parameter to get cmdlet syntax.</span></span> <span data-ttu-id="8331e-119">您看到的輸出將顯示針對您指定之資源的資源區塊所使用的範本。</span><span class="sxs-lookup"><span data-stu-id="8331e-119">The output you see will show the template used for a resource block for the resource you specify.</span></span>

```powershell
Get-DscResource -Syntax Service
```

<span data-ttu-id="8331e-120">雖然此資源的語法未來可能變更，但您看到的輸出應該類似下列輸出。</span><span class="sxs-lookup"><span data-stu-id="8331e-120">The output you see should be similar to the output below, though this resource's syntax could change in the future.</span></span> <span data-ttu-id="8331e-121">如同 Cmdlet 語法，方括弧中的「索引鍵」  均為選擇性。</span><span class="sxs-lookup"><span data-stu-id="8331e-121">Like cmdlet syntax, the _keys_ seen in square brackets, are optional.</span></span> <span data-ttu-id="8331e-122">類型會指定每個索引鍵所預期的資料類型。</span><span class="sxs-lookup"><span data-stu-id="8331e-122">The types specify the type of data each key expects.</span></span>

> [!NOTE]
> <span data-ttu-id="8331e-123">**Ensure** 索引鍵是選擇性的，因為它會預設為 "Present"。</span><span class="sxs-lookup"><span data-stu-id="8331e-123">The **Ensure** key is optional because it defaults to "Present".</span></span>

```output
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

<span data-ttu-id="8331e-124">在設定內部，**服務**資源區塊可能看起來像這樣，以**確保**多工緩衝處理器服務正在執行。</span><span class="sxs-lookup"><span data-stu-id="8331e-124">Inside a Configuration, a **Service** resource block might look like this to **Ensure** that the Spooler service is running.</span></span>

> [!NOTE]
> <span data-ttu-id="8331e-125">在設定中使用資源之前，您必須先使用 [Import-DSCResource](../configurations/import-dscresource.md) 來匯入該資源。</span><span class="sxs-lookup"><span data-stu-id="8331e-125">Before using a resource in a Configuration, you must import it using [Import-DSCResource](../configurations/import-dscresource.md).</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }
    }
}
```

<span data-ttu-id="8331e-126">設定可以包含相同資源類型的多個執行個體。</span><span class="sxs-lookup"><span data-stu-id="8331e-126">Configurations can contain multiple instances of the same resource type.</span></span> <span data-ttu-id="8331e-127">每個執行個體都必須具有唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="8331e-127">Each instance must be uniquely named.</span></span> <span data-ttu-id="8331e-128">在下列範例中，會新增第二個**服務**資源區塊來設定 "DHCP" 服務。</span><span class="sxs-lookup"><span data-stu-id="8331e-128">In the following example, a second **Service** resource block is added to configure the "DHCP" service.</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }

        # To configure a second service resource block, add another Service resource block and use a unique name.
        Service "DHCP:Running"
        {
            Name = "DHCP"
            State = "Running"
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="8331e-129">從 PowerShell 5.0 開始，已針對 DSC 新增 IntelliSense。</span><span class="sxs-lookup"><span data-stu-id="8331e-129">Beginning in PowerShell 5.0, intellisense was added for DSC.</span></span> <span data-ttu-id="8331e-130">此新功能可讓您使用 <kbd>TAB</kbd> 與 <kbd>Ctr</kbd>+<kbd>空格鍵</kbd>來自動完成機碼名稱。</span><span class="sxs-lookup"><span data-stu-id="8331e-130">This new feature allows you to use <kbd>TAB</kbd> and <kbd>Ctr</kbd>+<kbd>Space</kbd> to auto-complete key names.</span></span>

![資源 Tab 鍵自動完成](media/resources/resource-tabcompletion.png)

## <a name="types-of-resources"></a><span data-ttu-id="8331e-132">資源類型</span><span class="sxs-lookup"><span data-stu-id="8331e-132">Types of resources</span></span>

<span data-ttu-id="8331e-133">Windows 具有內建資源，而 Linux 則具有 OS 特定資源。</span><span class="sxs-lookup"><span data-stu-id="8331e-133">Windows comes with built in resources and Linux has OS specific resources.</span></span> <span data-ttu-id="8331e-134">有適用於[跨節點相依性](../configurations/crossNodeDependencies.md)的資源、套件管理資源，以及[由社群所有及維護的資源](https://github.com/dsccommunity) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="8331e-134">There are resources for [cross-node dependencies](../configurations/crossNodeDependencies.md), package management resources, as well as[community owned and maintained resources](https://github.com/dsccommunity).</span></span> <span data-ttu-id="8331e-135">您可以使用上述步驟來判斷這些資源的語法以及其使用方式。</span><span class="sxs-lookup"><span data-stu-id="8331e-135">You can use the above steps to determine the syntax of these resources and how to use them.</span></span> <span data-ttu-id="8331e-136">提供這些資源的頁面都已封存於**參考**下方。</span><span class="sxs-lookup"><span data-stu-id="8331e-136">The pages that serve these resources have been archived under **Reference**.</span></span>

### <a name="windows-built-in-resources"></a><span data-ttu-id="8331e-137">Windows 內建資源</span><span class="sxs-lookup"><span data-stu-id="8331e-137">Windows built-in resources</span></span>

- [<span data-ttu-id="8331e-138">封存資源</span><span class="sxs-lookup"><span data-stu-id="8331e-138">Archive Resource</span></span>](../reference/resources/windows/archiveResource.md)
- [<span data-ttu-id="8331e-139">環境資源</span><span class="sxs-lookup"><span data-stu-id="8331e-139">Environment Resource</span></span>](../reference/resources/windows/environmentResource.md)
- [<span data-ttu-id="8331e-140">檔案資源</span><span class="sxs-lookup"><span data-stu-id="8331e-140">File Resource</span></span>](../reference/resources/windows/fileResource.md)
- [<span data-ttu-id="8331e-141">群組資源</span><span class="sxs-lookup"><span data-stu-id="8331e-141">Group Resource</span></span>](../reference/resources/windows/groupResource.md)
- [<span data-ttu-id="8331e-142">GroupSet 資源</span><span class="sxs-lookup"><span data-stu-id="8331e-142">GroupSet Resource</span></span>](../reference/resources/windows/groupSetResource.md)
- [<span data-ttu-id="8331e-143">記錄檔資源</span><span class="sxs-lookup"><span data-stu-id="8331e-143">Log Resource</span></span>](../reference/resources/windows/logResource.md)
- [<span data-ttu-id="8331e-144">封裝資源</span><span class="sxs-lookup"><span data-stu-id="8331e-144">Package Resource</span></span>](../reference/resources/windows/packageResource.md)
- [<span data-ttu-id="8331e-145">ProcessSet 資源</span><span class="sxs-lookup"><span data-stu-id="8331e-145">ProcessSet Resource</span></span>](../reference/resources/windows/ProcessSetResource.md)
- [<span data-ttu-id="8331e-146">登錄資源</span><span class="sxs-lookup"><span data-stu-id="8331e-146">Registry Resource</span></span>](../reference/resources/windows/registryResource.md)
- [<span data-ttu-id="8331e-147">指令碼資源</span><span class="sxs-lookup"><span data-stu-id="8331e-147">Script Resource</span></span>](../reference/resources/windows/scriptResource.md)
- [<span data-ttu-id="8331e-148">服務資源</span><span class="sxs-lookup"><span data-stu-id="8331e-148">Service Resource</span></span>](../reference/resources/windows/serviceResource.md)
- [<span data-ttu-id="8331e-149">ServiceSet 資源</span><span class="sxs-lookup"><span data-stu-id="8331e-149">ServiceSet Resource</span></span>](../reference/resources/windows/serviceSetResource.md)
- [<span data-ttu-id="8331e-150">使用者資源</span><span class="sxs-lookup"><span data-stu-id="8331e-150">User Resource</span></span>](../reference/resources/windows/userResource.md)
- [<span data-ttu-id="8331e-151">WindowsFeature 資源</span><span class="sxs-lookup"><span data-stu-id="8331e-151">WindowsFeature Resource</span></span>](../reference/resources/windows/windowsFeatureResource.md)
- [<span data-ttu-id="8331e-152">WindowsFeatureSet 資源</span><span class="sxs-lookup"><span data-stu-id="8331e-152">WindowsFeatureSet Resource</span></span>](../reference/resources/windows/windowsFeatureSetResource.md)
- [<span data-ttu-id="8331e-153">WindowsOptionalFeature 資源</span><span class="sxs-lookup"><span data-stu-id="8331e-153">WindowsOptionalFeature Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureResource.md)
- [<span data-ttu-id="8331e-154">WindowsOptionalFeatureSet 資源</span><span class="sxs-lookup"><span data-stu-id="8331e-154">WindowsOptionalFeatureSet Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureSetResource.md)
- [<span data-ttu-id="8331e-155">WindowsPackageCabResource 資源</span><span class="sxs-lookup"><span data-stu-id="8331e-155">WindowsPackageCabResource Resource</span></span>](../reference/resources/windows/windowsPackageCabResource.md)
- [<span data-ttu-id="8331e-156">WindowsProcess 資源</span><span class="sxs-lookup"><span data-stu-id="8331e-156">WindowsProcess Resource</span></span>](../reference/resources/windows/windowsProcessResource.md)

### <a name="cross-node-dependency-resources"></a><span data-ttu-id="8331e-157">跨節點相依性資源</span><span class="sxs-lookup"><span data-stu-id="8331e-157">Cross-Node dependency resources</span></span>

- [<span data-ttu-id="8331e-158">WaitForAll 資源</span><span class="sxs-lookup"><span data-stu-id="8331e-158">WaitForAll Resource</span></span>](../reference/resources/windows/waitForAllResource.md)
- [<span data-ttu-id="8331e-159">WaitForSome 資源</span><span class="sxs-lookup"><span data-stu-id="8331e-159">WaitForSome Resource</span></span>](../reference/resources/windows/waitForSomeResource.md)
- [<span data-ttu-id="8331e-160">WaitForAny 資源</span><span class="sxs-lookup"><span data-stu-id="8331e-160">WaitForAny Resource</span></span>](../reference/resources/windows/waitForAnyResource.md)

### <a name="package-management-resources"></a><span data-ttu-id="8331e-161">套件管理資源</span><span class="sxs-lookup"><span data-stu-id="8331e-161">Package Management resources</span></span>

- [<span data-ttu-id="8331e-162">PackageManagement 資源</span><span class="sxs-lookup"><span data-stu-id="8331e-162">PackageManagement Resource</span></span>](../reference/resources/packagemanagement/PackageManagementDscResource.md)
- [<span data-ttu-id="8331e-163">PackageManagementSource 資源</span><span class="sxs-lookup"><span data-stu-id="8331e-163">PackageManagementSource Resource</span></span>](../reference/resources/packagemanagement/PackageManagementSourceDscResource.md)

#### <a name="linux-resources"></a><span data-ttu-id="8331e-164">Linux 資源</span><span class="sxs-lookup"><span data-stu-id="8331e-164">Linux resources</span></span>

- [<span data-ttu-id="8331e-165">Linux 封存資源</span><span class="sxs-lookup"><span data-stu-id="8331e-165">Linux Archive Resource</span></span>](../reference/resources/linux/lnxArchiveResource.md)
- [<span data-ttu-id="8331e-166">Linux 環境資源</span><span class="sxs-lookup"><span data-stu-id="8331e-166">Linux Environment Resource</span></span>](../reference/resources/linux/lnxEnvironmentResource.md)
- [<span data-ttu-id="8331e-167">Linux FileLine 資源</span><span class="sxs-lookup"><span data-stu-id="8331e-167">Linux FileLine Resource</span></span>](../reference/resources/linux/lnxFileLineResource.md)
- [<span data-ttu-id="8331e-168">Linux 檔案資源</span><span class="sxs-lookup"><span data-stu-id="8331e-168">Linux File Resource</span></span>](../reference/resources/linux/lnxFileResource.md)
- [<span data-ttu-id="8331e-169">Linux 群組資源</span><span class="sxs-lookup"><span data-stu-id="8331e-169">Linux Group Resource</span></span>](../reference/resources/linux/lnxGroupResource.md)
- [<span data-ttu-id="8331e-170">Linux 套件資源</span><span class="sxs-lookup"><span data-stu-id="8331e-170">Linux Package Resource</span></span>](../reference/resources/linux/lnxPackageResource.md)
- [<span data-ttu-id="8331e-171">Linux 指令碼資源</span><span class="sxs-lookup"><span data-stu-id="8331e-171">Linux Script Resource</span></span>](../reference/resources/linux/lnxScriptResource.md)
- [<span data-ttu-id="8331e-172">Linux 服務資源</span><span class="sxs-lookup"><span data-stu-id="8331e-172">Linux Service Resource</span></span>](../reference/resources/linux/lnxServiceResource.md)
- [<span data-ttu-id="8331e-173">Linux SshAuthorizedKeys 資源</span><span class="sxs-lookup"><span data-stu-id="8331e-173">Linux SshAuthorizedKeys Resource</span></span>](../reference/resources/linux/lnxSshAuthorizedKeysResource.md)
- [<span data-ttu-id="8331e-174">Linux 使用者資源</span><span class="sxs-lookup"><span data-stu-id="8331e-174">Linux User Resource</span></span>](../reference/resources/linux/lnxUserResource.md)
