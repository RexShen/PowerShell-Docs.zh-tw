---
ms.date: 12/12/2018
keywords: dsc,powershell,設定,安裝
title: DSC 資源
ms.openlocfilehash: 1f77b5e6630a2e3de6e1d1a05638f94d2df039ae
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076613"
---
# <a name="dsc-resources"></a><span data-ttu-id="8ddcd-103">DSC 資源</span><span class="sxs-lookup"><span data-stu-id="8ddcd-103">DSC Resources</span></span>

><span data-ttu-id="8ddcd-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="8ddcd-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="8ddcd-105">預期狀態設定 (DSC) 資源提供 DSC 設定的建置組塊。</span><span class="sxs-lookup"><span data-stu-id="8ddcd-105">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="8ddcd-106">資源會公開可以設定的屬性 (結構描述)，而且這些屬性包含本機設定管理員 (LCM) 稱之為「make it so (讓它變成這樣)」的 PowerShell 指令碼函式。</span><span class="sxs-lookup"><span data-stu-id="8ddcd-106">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="8ddcd-107">資源可以建立某些物件的模型，像檔案一樣平常或如 IIS 伺服器設定一樣專用。</span><span class="sxs-lookup"><span data-stu-id="8ddcd-107">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span>  <span data-ttu-id="8ddcd-108">類似資源的群組會併入 DSC 模組，將所有必要的檔案組織到可攜式結構中，而且包含中繼資料以識別資源的原訂用法。</span><span class="sxs-lookup"><span data-stu-id="8ddcd-108">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

<span data-ttu-id="8ddcd-109">每個資源都有一個\*結構描述，可判斷在[設定](../configurations/configurations.md)中使用資源所需的語法。</span><span class="sxs-lookup"><span data-stu-id="8ddcd-109">Each resource has a \*schema that determines the syntax needed to use the resource in a [Configuration](../configurations/configurations.md).</span></span> <span data-ttu-id="8ddcd-110">您可以透過下列方式定義資源的結構描述：</span><span class="sxs-lookup"><span data-stu-id="8ddcd-110">A resource's schema can be defined in the following ways:</span></span>

- <span data-ttu-id="8ddcd-111">**'Schema.Mof'** 檔案：大部分的資源都會使用[受控物件格式](/windows/desktop/wmisdk/managed-object-format--mof-)，在 '.schema.mof' 檔案中定義其「結構描述」。</span><span class="sxs-lookup"><span data-stu-id="8ddcd-111">**'Schema.Mof'** file: Most resources define their *schema* in a 'schema.mof' file, using [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>
- <span data-ttu-id="8ddcd-112">**'\<資源名稱\>.schema.psm1'** 檔案：[複合資源](../configurations/compositeConfigs.md)會使用[參數區塊](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters)，在 '<ResourceName>.schema.psm1' 檔案中定義其「結構描述」。</span><span class="sxs-lookup"><span data-stu-id="8ddcd-112">**'\<Resource Name\>.schema.psm1'** file: [Composite Resources](../configurations/compositeConfigs.md) define their *schema* in a '<ResourceName>.schema.psm1' file using a [Parameter Block](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).</span></span>
- <span data-ttu-id="8ddcd-113">**'\<資源名稱\>.psm1'** 檔案：以類別為基礎的 DSC 資源會在類別定義中定義其「結構描述」。</span><span class="sxs-lookup"><span data-stu-id="8ddcd-113">**'\<Resource Name\>.psm1'** file: Class based DSC resources define their *schema* in the class definition.</span></span> <span data-ttu-id="8ddcd-114">語法項目會標示為 Class 屬性。</span><span class="sxs-lookup"><span data-stu-id="8ddcd-114">Syntax items are denoted as Class properties.</span></span> <span data-ttu-id="8ddcd-115">如需詳細資訊，請參閱 [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc)。</span><span class="sxs-lookup"><span data-stu-id="8ddcd-115">For more information, see [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span></span>

<span data-ttu-id="8ddcd-116">若要擷取 DSC 資源的語法，請搭配 `-Syntax` 參數使用 [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8ddcd-116">To retrieve the syntax for a DSC resource, use the [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet with the `-Syntax` parameter.</span></span> <span data-ttu-id="8ddcd-117">此使用方式類似於搭配 `-Syntax` 參數使用 [Get-Command](/powershell/module/microsoft.powershell.core/get-command) 來取得 Cmdlet 語法。</span><span class="sxs-lookup"><span data-stu-id="8ddcd-117">This usage is similar to using [Get-Command](/powershell/module/microsoft.powershell.core/get-command) with the `-Syntax` parameter to get cmdlet syntax.</span></span> <span data-ttu-id="8ddcd-118">您看到的輸出將顯示針對您指定之資源的資源區塊所使用的範本。</span><span class="sxs-lookup"><span data-stu-id="8ddcd-118">The output you see will show the template used for a resource block for the resource you specify.</span></span>

```powershell
Get-DscResource -Syntax Service
```

<span data-ttu-id="8ddcd-119">雖然此資源的語法未來可能變更，但您看到的輸出應該類似下列輸出。</span><span class="sxs-lookup"><span data-stu-id="8ddcd-119">The output you see should be similar to the output below, though this resource's syntax could change in the future.</span></span> <span data-ttu-id="8ddcd-120">如同 Cmdlet 語法，方括弧中的「索引鍵」均為選擇性。</span><span class="sxs-lookup"><span data-stu-id="8ddcd-120">Like cmdlet syntax, the *keys* seen in square brackets, are optional.</span></span> <span data-ttu-id="8ddcd-121">類型會指定每個索引鍵所預期的資料類型。</span><span class="sxs-lookup"><span data-stu-id="8ddcd-121">The types specify the type of data each key expects.</span></span>

> [!NOTE]
> <span data-ttu-id="8ddcd-122">**Ensure** 索引鍵是選擇性的，因為它會預設為 "Present"。</span><span class="sxs-lookup"><span data-stu-id="8ddcd-122">The **Ensure** key is optional because it defaults to "Present".</span></span>

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

<span data-ttu-id="8ddcd-123">在設定內部，**服務**資源區塊可能看起來像這樣，以**確保**多工緩衝處理器服務正在執行。</span><span class="sxs-lookup"><span data-stu-id="8ddcd-123">Inside a Configuration, a **Service** resource block might look like this to **Ensure** that the Spooler service is running.</span></span>

> [!NOTE]
> <span data-ttu-id="8ddcd-124">在設定中使用資源之前，您必須先使用 [Import-DSCResource](../configurations/import-dscresource.md) 來匯入該資源。</span><span class="sxs-lookup"><span data-stu-id="8ddcd-124">Before using a resource in a Configuration, you must import it using [Import-DSCResource](../configurations/import-dscresource.md).</span></span>

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

<span data-ttu-id="8ddcd-125">設定可以包含相同資源類型的多個執行個體。</span><span class="sxs-lookup"><span data-stu-id="8ddcd-125">Configurations can contain multiple instances of the same resource type.</span></span> <span data-ttu-id="8ddcd-126">每個執行個體都必須具有唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="8ddcd-126">Each instance must be uniquely named.</span></span> <span data-ttu-id="8ddcd-127">在下列範例中，會新增第二個**服務**資源區塊來設定 "DHCP" 服務。</span><span class="sxs-lookup"><span data-stu-id="8ddcd-127">In the following example, a second **Service** resource block is added to configure the "DHCP" service.</span></span>

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
> <span data-ttu-id="8ddcd-128">從 PowerShell 5.0 開始，已針對 DSC 新增 IntelliSense。</span><span class="sxs-lookup"><span data-stu-id="8ddcd-128">Beginning in PowerShell 5.0, intellisense was added for DSC.</span></span> <span data-ttu-id="8ddcd-129">此新功能可讓您使用 \<TAB\> 和 \<Ctrl+空格鍵\> 自動完成索引鍵名稱。</span><span class="sxs-lookup"><span data-stu-id="8ddcd-129">This new feature allows you to use \<TAB\> and \<Ctrl+Space\> to auto-complete key names.</span></span>

![資源 Tab 鍵自動完成](../media/resource-tabcompletion.png)

## <a name="built-in-resources"></a><span data-ttu-id="8ddcd-131">內建資源</span><span class="sxs-lookup"><span data-stu-id="8ddcd-131">Built-in resources</span></span>

<span data-ttu-id="8ddcd-132">除了社群資源，還提供適用於 Windows 的內建資源、適用於 Linux 的資源，以及適用於跨節點相依性的資源。</span><span class="sxs-lookup"><span data-stu-id="8ddcd-132">In addition to community resources, there are built-in resources for Windows, resources for Linux, and resources for cross-node dependency.</span></span> <span data-ttu-id="8ddcd-133">您可以使用上述步驟，來判斷這些資源的語法以及使用它們的方式。</span><span class="sxs-lookup"><span data-stu-id="8ddcd-133">You can use the steps above to determine the syntax of these resources and how to use them.</span></span> <span data-ttu-id="8ddcd-134">提供這些資源的頁面都已封存於**參考**下方。</span><span class="sxs-lookup"><span data-stu-id="8ddcd-134">The pages that serve these resources have been archived under **Reference**.</span></span>

<span data-ttu-id="8ddcd-135">Windows 內建資源</span><span class="sxs-lookup"><span data-stu-id="8ddcd-135">Windows built-in resources</span></span>

* [<span data-ttu-id="8ddcd-136">封存資源</span><span class="sxs-lookup"><span data-stu-id="8ddcd-136">Archive Resource</span></span>](../reference/resources/windows/archiveResource.md)
* [<span data-ttu-id="8ddcd-137">環境資源</span><span class="sxs-lookup"><span data-stu-id="8ddcd-137">Environment Resource</span></span>](../reference/resources/windows/environmentResource.md)
* [<span data-ttu-id="8ddcd-138">檔案資源</span><span class="sxs-lookup"><span data-stu-id="8ddcd-138">File Resource</span></span>](../reference/resources/windows/fileResource.md)
* [<span data-ttu-id="8ddcd-139">群組資源</span><span class="sxs-lookup"><span data-stu-id="8ddcd-139">Group Resource</span></span>](../reference/resources/windows/groupResource.md)
* [<span data-ttu-id="8ddcd-140">GroupSet 資源</span><span class="sxs-lookup"><span data-stu-id="8ddcd-140">GroupSet Resource</span></span>](../reference/resources/windows/groupSetResource.md)
* [<span data-ttu-id="8ddcd-141">記錄檔資源</span><span class="sxs-lookup"><span data-stu-id="8ddcd-141">Log Resource</span></span>](../reference/resources/windows/logResource.md)
* [<span data-ttu-id="8ddcd-142">封裝資源</span><span class="sxs-lookup"><span data-stu-id="8ddcd-142">Package Resource</span></span>](../reference/resources/windows/packageResource.md)
* [<span data-ttu-id="8ddcd-143">ProcessSet 資源</span><span class="sxs-lookup"><span data-stu-id="8ddcd-143">ProcessSet Resource</span></span>](../reference/resources/windows/ProcessSetResource.md)
* [<span data-ttu-id="8ddcd-144">登錄資源</span><span class="sxs-lookup"><span data-stu-id="8ddcd-144">Registry Resource</span></span>](../reference/resources/windows/registryResource.md)
* [<span data-ttu-id="8ddcd-145">指令碼資源</span><span class="sxs-lookup"><span data-stu-id="8ddcd-145">Script Resource</span></span>](../reference/resources/windows/scriptResource.md)
* [<span data-ttu-id="8ddcd-146">服務資源</span><span class="sxs-lookup"><span data-stu-id="8ddcd-146">Service Resource</span></span>](../reference/resources/windows/serviceResource.md)
* [<span data-ttu-id="8ddcd-147">ServiceSet 資源</span><span class="sxs-lookup"><span data-stu-id="8ddcd-147">ServiceSet Resource</span></span>](../reference/resources/windows/serviceSetResource.md)
* [<span data-ttu-id="8ddcd-148">使用者資源</span><span class="sxs-lookup"><span data-stu-id="8ddcd-148">User Resource</span></span>](../reference/resources/windows/userResource.md)
* [<span data-ttu-id="8ddcd-149">WindowsFeature 資源</span><span class="sxs-lookup"><span data-stu-id="8ddcd-149">WindowsFeature Resource</span></span>](../reference/resources/windows/windowsFeatureResource.md)
* [<span data-ttu-id="8ddcd-150">WindowsFeatureSet 資源</span><span class="sxs-lookup"><span data-stu-id="8ddcd-150">WindowsFeatureSet Resource</span></span>](../reference/resources/windows/windowsFeatureSetResource.md)
* [<span data-ttu-id="8ddcd-151">WindowsOptionalFeature 資源</span><span class="sxs-lookup"><span data-stu-id="8ddcd-151">WindowsOptionalFeature Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureResource.md)
* [<span data-ttu-id="8ddcd-152">WindowsOptionalFeatureSet 資源</span><span class="sxs-lookup"><span data-stu-id="8ddcd-152">WindowsOptionalFeatureSet Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureSetResource.md)
* [<span data-ttu-id="8ddcd-153">WindowsPackageCabResource 資源</span><span class="sxs-lookup"><span data-stu-id="8ddcd-153">WindowsPackageCabResource Resource</span></span>](../reference/resources/windows/windowsPackageCabResource.md)
* [<span data-ttu-id="8ddcd-154">WindowsProcess 資源</span><span class="sxs-lookup"><span data-stu-id="8ddcd-154">WindowsProcess Resource</span></span>](../reference/resources/windows/windowsProcessResource.md)

<span data-ttu-id="8ddcd-155">[跨節點相依性](../configurations/crossNodeDependencies.md)資源</span><span class="sxs-lookup"><span data-stu-id="8ddcd-155">[Cross-Node dependency](../configurations/crossNodeDependencies.md) resources</span></span>

* [<span data-ttu-id="8ddcd-156">WaitForAll 資源</span><span class="sxs-lookup"><span data-stu-id="8ddcd-156">WaitForAll Resource</span></span>](../reference/resources/windows/waitForAllResource.md)
* [<span data-ttu-id="8ddcd-157">WaitForSome 資源</span><span class="sxs-lookup"><span data-stu-id="8ddcd-157">WaitForSome Resource</span></span>](../reference/resources/windows/waitForSomeResource.md)
* [<span data-ttu-id="8ddcd-158">WaitForAny 資源</span><span class="sxs-lookup"><span data-stu-id="8ddcd-158">WaitForAny Resource</span></span>](../reference/resources/windows/waitForAnyResource.md)

<span data-ttu-id="8ddcd-159">套件管理資源</span><span class="sxs-lookup"><span data-stu-id="8ddcd-159">Package Management resources</span></span>

* [<span data-ttu-id="8ddcd-160">PackageManagement 資源</span><span class="sxs-lookup"><span data-stu-id="8ddcd-160">PackageManagement Resource</span></span>](../reference/resources/packagemanagement/PackageManagementDscResource.md)
* [<span data-ttu-id="8ddcd-161">PackageManagementSource 資源</span><span class="sxs-lookup"><span data-stu-id="8ddcd-161">PackageManagementSource Resource</span></span>](../reference/resources/packagemanagement/PackageManagementSourceDscResource.md)

<span data-ttu-id="8ddcd-162">Linux 資源</span><span class="sxs-lookup"><span data-stu-id="8ddcd-162">Linux resources</span></span>

* [<span data-ttu-id="8ddcd-163">Linux 封存資源</span><span class="sxs-lookup"><span data-stu-id="8ddcd-163">Linux Archive Resource</span></span>](../reference/resources/linux/lnxArchiveResource.md)
* [<span data-ttu-id="8ddcd-164">Linux 環境資源</span><span class="sxs-lookup"><span data-stu-id="8ddcd-164">Linux Environment Resource</span></span>](../reference/resources/linux/lnxEnvironmentResource.md)
* [<span data-ttu-id="8ddcd-165">Linux FileLine 資源</span><span class="sxs-lookup"><span data-stu-id="8ddcd-165">Linux FileLine Resource</span></span>](../reference/resources/linux/lnxFileLineResource.md)
* [<span data-ttu-id="8ddcd-166">Linux 檔案資源</span><span class="sxs-lookup"><span data-stu-id="8ddcd-166">Linux File Resource</span></span>](../reference/resources/linux/lnxFileResource.md)
* [<span data-ttu-id="8ddcd-167">Linux 群組資源</span><span class="sxs-lookup"><span data-stu-id="8ddcd-167">Linux Group Resource</span></span>](../reference/resources/linux/lnxGroupResource.md)
* [<span data-ttu-id="8ddcd-168">Linux 套件資源</span><span class="sxs-lookup"><span data-stu-id="8ddcd-168">Linux Package Resource</span></span>](../reference/resources/linux/lnxPackageResource.md)
* [<span data-ttu-id="8ddcd-169">Linux 指令碼資源</span><span class="sxs-lookup"><span data-stu-id="8ddcd-169">Linux Script Resource</span></span>](../reference/resources/linux/lnxScriptResource.md)
* [<span data-ttu-id="8ddcd-170">Linux 服務資源</span><span class="sxs-lookup"><span data-stu-id="8ddcd-170">Linux Service Resource</span></span>](../reference/resources/linux/lnxServiceResource.md)
* [<span data-ttu-id="8ddcd-171">Linux SshAuthorizedKeys 資源</span><span class="sxs-lookup"><span data-stu-id="8ddcd-171">Linux SshAuthorizedKeys Resource</span></span>](../reference/resources/linux/lnxSshAuthorizedKeysResource.md)
* [<span data-ttu-id="8ddcd-172">Linux 使用者資源</span><span class="sxs-lookup"><span data-stu-id="8ddcd-172">Linux User Resource</span></span>](../reference/resources/linux/lnxUserResource.md)
