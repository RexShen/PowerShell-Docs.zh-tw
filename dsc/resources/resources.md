---
ms.date: 12/12/2018
keywords: dsc,powershell,設定,安裝
title: DSC 資源
ms.openlocfilehash: 1f77b5e6630a2e3de6e1d1a05638f94d2df039ae
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046686"
---
# <a name="dsc-resources"></a><span data-ttu-id="0cec3-103">DSC 資源</span><span class="sxs-lookup"><span data-stu-id="0cec3-103">DSC Resources</span></span>

><span data-ttu-id="0cec3-104">適用於：Windows PowerShell 4.0 中，Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="0cec3-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="0cec3-105">預期狀態設定 (DSC) 資源提供 DSC 設定的建置組塊。</span><span class="sxs-lookup"><span data-stu-id="0cec3-105">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="0cec3-106">資源會公開可以設定的屬性 (結構描述)，而且這些屬性包含本機設定管理員 (LCM) 稱之為「make it so (讓它變成這樣)」的 PowerShell 指令碼函式。</span><span class="sxs-lookup"><span data-stu-id="0cec3-106">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="0cec3-107">資源可以建立某些物件的模型，像檔案一樣平常或如 IIS 伺服器設定一樣專用。</span><span class="sxs-lookup"><span data-stu-id="0cec3-107">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span>  <span data-ttu-id="0cec3-108">類似資源的群組會併入 DSC 模組，將所有必要的檔案組織到可攜式結構中，而且包含中繼資料以識別資源的原訂用法。</span><span class="sxs-lookup"><span data-stu-id="0cec3-108">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

<span data-ttu-id="0cec3-109">每個資源都有 \* 判斷使用中的資源所需的語法的結構描述[組態](../configurations/configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="0cec3-109">Each resource has a \*schema that determines the syntax needed to use the resource in a [Configuration](../configurations/configurations.md).</span></span> <span data-ttu-id="0cec3-110">可以透過下列方式定義資源的結構描述：</span><span class="sxs-lookup"><span data-stu-id="0cec3-110">A resource's schema can be defined in the following ways:</span></span>

- <span data-ttu-id="0cec3-111">**'.Schema.mof'** 檔案：大部分的資源定義他們*結構描述*'.schema.mof' 在檔案中，使用[Managed 物件格式](/windows/desktop/wmisdk/managed-object-format--mof-)。</span><span class="sxs-lookup"><span data-stu-id="0cec3-111">**'Schema.Mof'** file: Most resources define their *schema* in a 'schema.mof' file, using [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>
- <span data-ttu-id="0cec3-112">**'\<資源名稱\>。 schema.psm1'** 檔案：[複合資源](../configurations/compositeConfigs.md)定義其*結構描述*在 '<ResourceName>。 schema.psm1' 檔案中，使用[參數區塊](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters)。</span><span class="sxs-lookup"><span data-stu-id="0cec3-112">**'\<Resource Name\>.schema.psm1'** file: [Composite Resources](../configurations/compositeConfigs.md) define their *schema* in a '<ResourceName>.schema.psm1' file using a [Parameter Block](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).</span></span>
- <span data-ttu-id="0cec3-113">**'\<資源名稱\>.psm1'** 檔案：類別型的 DSC 資源定義他們*結構描述*類別定義中。</span><span class="sxs-lookup"><span data-stu-id="0cec3-113">**'\<Resource Name\>.psm1'** file: Class based DSC resources define their *schema* in the class definition.</span></span> <span data-ttu-id="0cec3-114">語法項目會標示為類別的屬性。</span><span class="sxs-lookup"><span data-stu-id="0cec3-114">Syntax items are denoted as Class properties.</span></span> <span data-ttu-id="0cec3-115">如需詳細資訊，請參閱 < [< about_classes >](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc)。</span><span class="sxs-lookup"><span data-stu-id="0cec3-115">For more information, see [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span></span>

<span data-ttu-id="0cec3-116">若要擷取的 DSC 資源的語法，請使用[Get-dscresource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet 搭配`-Syntax`參數。</span><span class="sxs-lookup"><span data-stu-id="0cec3-116">To retrieve the syntax for a DSC resource, use the [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet with the `-Syntax` parameter.</span></span> <span data-ttu-id="0cec3-117">這種使用方式，類似於使用[Get-command](/powershell/module/microsoft.powershell.core/get-command)與`-Syntax`參數，以取得 cmdlet 的語法。</span><span class="sxs-lookup"><span data-stu-id="0cec3-117">This usage is similar to using [Get-Command](/powershell/module/microsoft.powershell.core/get-command) with the `-Syntax` parameter to get cmdlet syntax.</span></span> <span data-ttu-id="0cec3-118">您看到的輸出會顯示您所指定之資源的資源區塊所用的範本。</span><span class="sxs-lookup"><span data-stu-id="0cec3-118">The output you see will show the template used for a resource block for the resource you specify.</span></span>

```powershell
Get-DscResource -Syntax Service
```

<span data-ttu-id="0cec3-119">雖然此資源的語法可能在未來變更，您看到的輸出應該會類似如下的輸出。</span><span class="sxs-lookup"><span data-stu-id="0cec3-119">The output you see should be similar to the output below, though this resource's syntax could change in the future.</span></span> <span data-ttu-id="0cec3-120">喜歡 cmdlet 語法*金鑰*方括號所示，都是選擇性。</span><span class="sxs-lookup"><span data-stu-id="0cec3-120">Like cmdlet syntax, the *keys* seen in square brackets, are optional.</span></span> <span data-ttu-id="0cec3-121">指定每個索引鍵所預期的資料的類型的類型。</span><span class="sxs-lookup"><span data-stu-id="0cec3-121">The types specify the type of data each key expects.</span></span>

> [!NOTE]
> <span data-ttu-id="0cec3-122">**請確定**金鑰是選擇性的因為它會預設為"Present"。</span><span class="sxs-lookup"><span data-stu-id="0cec3-122">The **Ensure** key is optional because it defaults to "Present".</span></span>

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

<span data-ttu-id="0cec3-123">在組態中，內**服務**資源區塊可能會看起來像這樣來**請確定**多工緩衝處理器服務正在執行。</span><span class="sxs-lookup"><span data-stu-id="0cec3-123">Inside a Configuration, a **Service** resource block might look like this to **Ensure** that the Spooler service is running.</span></span>

> [!NOTE]
> <span data-ttu-id="0cec3-124">之前在組態中使用的資源，您必須匯入使用[Import-dscresource](../configurations/import-dscresource.md)。</span><span class="sxs-lookup"><span data-stu-id="0cec3-124">Before using a resource in a Configuration, you must import it using [Import-DSCResource](../configurations/import-dscresource.md).</span></span>

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

<span data-ttu-id="0cec3-125">設定可以包含多個相同的資源類型執行個體。</span><span class="sxs-lookup"><span data-stu-id="0cec3-125">Configurations can contain multiple instances of the same resource type.</span></span> <span data-ttu-id="0cec3-126">每個執行個體必須具有唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="0cec3-126">Each instance must be uniquely named.</span></span> <span data-ttu-id="0cec3-127">在下列範例中，第二個**服務**資源區塊會新增至"DHCP"服務設定。</span><span class="sxs-lookup"><span data-stu-id="0cec3-127">In the following example, a second **Service** resource block is added to configure the "DHCP" service.</span></span>

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
> <span data-ttu-id="0cec3-128">從 PowerShell 5.0 開始，已新增 DSC intellisense。</span><span class="sxs-lookup"><span data-stu-id="0cec3-128">Beginning in PowerShell 5.0, intellisense was added for DSC.</span></span> <span data-ttu-id="0cec3-129">這項新功能可讓您使用\< 索引標籤\>並\<Ctrl + 空格鍵\>到自動完成索引鍵的名稱。</span><span class="sxs-lookup"><span data-stu-id="0cec3-129">This new feature allows you to use \<TAB\> and \<Ctrl+Space\> to auto-complete key names.</span></span>

![資源 Tab 鍵自動完成](../media/resource-tabcompletion.png)

## <a name="built-in-resources"></a><span data-ttu-id="0cec3-131">內建資源</span><span class="sxs-lookup"><span data-stu-id="0cec3-131">Built-in resources</span></span>

<span data-ttu-id="0cec3-132">除了社群資源，還有 Windows、 Linux、 資源和資源跨節點相依性的內建資源。</span><span class="sxs-lookup"><span data-stu-id="0cec3-132">In addition to community resources, there are built-in resources for Windows, resources for Linux, and resources for cross-node dependency.</span></span> <span data-ttu-id="0cec3-133">您可以使用上述步驟，以判斷這些資源和使用方式的語法。</span><span class="sxs-lookup"><span data-stu-id="0cec3-133">You can use the steps above to determine the syntax of these resources and how to use them.</span></span> <span data-ttu-id="0cec3-134">提供這些資源的頁面都已封存底下**參考**。</span><span class="sxs-lookup"><span data-stu-id="0cec3-134">The pages that serve these resources have been archived under **Reference**.</span></span>

<span data-ttu-id="0cec3-135">Windows 內建資源</span><span class="sxs-lookup"><span data-stu-id="0cec3-135">Windows built-in resources</span></span>

* [<span data-ttu-id="0cec3-136">封存資源</span><span class="sxs-lookup"><span data-stu-id="0cec3-136">Archive Resource</span></span>](../reference/resources/windows/archiveResource.md)
* [<span data-ttu-id="0cec3-137">環境資源</span><span class="sxs-lookup"><span data-stu-id="0cec3-137">Environment Resource</span></span>](../reference/resources/windows/environmentResource.md)
* [<span data-ttu-id="0cec3-138">檔案資源</span><span class="sxs-lookup"><span data-stu-id="0cec3-138">File Resource</span></span>](../reference/resources/windows/fileResource.md)
* [<span data-ttu-id="0cec3-139">群組資源</span><span class="sxs-lookup"><span data-stu-id="0cec3-139">Group Resource</span></span>](../reference/resources/windows/groupResource.md)
* [<span data-ttu-id="0cec3-140">GroupSet 資源</span><span class="sxs-lookup"><span data-stu-id="0cec3-140">GroupSet Resource</span></span>](../reference/resources/windows/groupSetResource.md)
* [<span data-ttu-id="0cec3-141">記錄檔資源</span><span class="sxs-lookup"><span data-stu-id="0cec3-141">Log Resource</span></span>](../reference/resources/windows/logResource.md)
* [<span data-ttu-id="0cec3-142">封裝資源</span><span class="sxs-lookup"><span data-stu-id="0cec3-142">Package Resource</span></span>](../reference/resources/windows/packageResource.md)
* [<span data-ttu-id="0cec3-143">ProcessSet 資源</span><span class="sxs-lookup"><span data-stu-id="0cec3-143">ProcessSet Resource</span></span>](../reference/resources/windows/ProcessSetResource.md)
* [<span data-ttu-id="0cec3-144">登錄資源</span><span class="sxs-lookup"><span data-stu-id="0cec3-144">Registry Resource</span></span>](../reference/resources/windows/registryResource.md)
* [<span data-ttu-id="0cec3-145">指令碼資源</span><span class="sxs-lookup"><span data-stu-id="0cec3-145">Script Resource</span></span>](../reference/resources/windows/scriptResource.md)
* [<span data-ttu-id="0cec3-146">服務資源</span><span class="sxs-lookup"><span data-stu-id="0cec3-146">Service Resource</span></span>](../reference/resources/windows/serviceResource.md)
* [<span data-ttu-id="0cec3-147">ServiceSet 資源</span><span class="sxs-lookup"><span data-stu-id="0cec3-147">ServiceSet Resource</span></span>](../reference/resources/windows/serviceSetResource.md)
* [<span data-ttu-id="0cec3-148">使用者資源</span><span class="sxs-lookup"><span data-stu-id="0cec3-148">User Resource</span></span>](../reference/resources/windows/userResource.md)
* [<span data-ttu-id="0cec3-149">WindowsFeature 資源</span><span class="sxs-lookup"><span data-stu-id="0cec3-149">WindowsFeature Resource</span></span>](../reference/resources/windows/windowsFeatureResource.md)
* [<span data-ttu-id="0cec3-150">WindowsFeatureSet 資源</span><span class="sxs-lookup"><span data-stu-id="0cec3-150">WindowsFeatureSet Resource</span></span>](../reference/resources/windows/windowsFeatureSetResource.md)
* [<span data-ttu-id="0cec3-151">WindowsOptionalFeature 資源</span><span class="sxs-lookup"><span data-stu-id="0cec3-151">WindowsOptionalFeature Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureResource.md)
* [<span data-ttu-id="0cec3-152">WindowsOptionalFeatureSet 資源</span><span class="sxs-lookup"><span data-stu-id="0cec3-152">WindowsOptionalFeatureSet Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureSetResource.md)
* [<span data-ttu-id="0cec3-153">WindowsPackageCabResource 資源</span><span class="sxs-lookup"><span data-stu-id="0cec3-153">WindowsPackageCabResource Resource</span></span>](../reference/resources/windows/windowsPackageCabResource.md)
* [<span data-ttu-id="0cec3-154">WindowsProcess 資源</span><span class="sxs-lookup"><span data-stu-id="0cec3-154">WindowsProcess Resource</span></span>](../reference/resources/windows/windowsProcessResource.md)

<span data-ttu-id="0cec3-155">[跨節點相依性](../configurations/crossNodeDependencies.md)資源</span><span class="sxs-lookup"><span data-stu-id="0cec3-155">[Cross-Node dependency](../configurations/crossNodeDependencies.md) resources</span></span>

* [<span data-ttu-id="0cec3-156">WaitForAll 資源</span><span class="sxs-lookup"><span data-stu-id="0cec3-156">WaitForAll Resource</span></span>](../reference/resources/windows/waitForAllResource.md)
* [<span data-ttu-id="0cec3-157">WaitForSome 資源</span><span class="sxs-lookup"><span data-stu-id="0cec3-157">WaitForSome Resource</span></span>](../reference/resources/windows/waitForSomeResource.md)
* [<span data-ttu-id="0cec3-158">WaitForAny 資源</span><span class="sxs-lookup"><span data-stu-id="0cec3-158">WaitForAny Resource</span></span>](../reference/resources/windows/waitForAnyResource.md)

<span data-ttu-id="0cec3-159">封裝管理資源</span><span class="sxs-lookup"><span data-stu-id="0cec3-159">Package Management resources</span></span>

* [<span data-ttu-id="0cec3-160">PackageManagement 資源</span><span class="sxs-lookup"><span data-stu-id="0cec3-160">PackageManagement Resource</span></span>](../reference/resources/packagemanagement/PackageManagementDscResource.md)
* [<span data-ttu-id="0cec3-161">PackageManagementSource 資源</span><span class="sxs-lookup"><span data-stu-id="0cec3-161">PackageManagementSource Resource</span></span>](../reference/resources/packagemanagement/PackageManagementSourceDscResource.md)

<span data-ttu-id="0cec3-162">Linux 上的資源</span><span class="sxs-lookup"><span data-stu-id="0cec3-162">Linux resources</span></span>

* [<span data-ttu-id="0cec3-163">Linux 封存資源</span><span class="sxs-lookup"><span data-stu-id="0cec3-163">Linux Archive Resource</span></span>](../reference/resources/linux/lnxArchiveResource.md)
* [<span data-ttu-id="0cec3-164">Linux 環境資源</span><span class="sxs-lookup"><span data-stu-id="0cec3-164">Linux Environment Resource</span></span>](../reference/resources/linux/lnxEnvironmentResource.md)
* [<span data-ttu-id="0cec3-165">Linux FileLine 資源</span><span class="sxs-lookup"><span data-stu-id="0cec3-165">Linux FileLine Resource</span></span>](../reference/resources/linux/lnxFileLineResource.md)
* [<span data-ttu-id="0cec3-166">Linux 檔案資源</span><span class="sxs-lookup"><span data-stu-id="0cec3-166">Linux File Resource</span></span>](../reference/resources/linux/lnxFileResource.md)
* [<span data-ttu-id="0cec3-167">Linux 群組資源</span><span class="sxs-lookup"><span data-stu-id="0cec3-167">Linux Group Resource</span></span>](../reference/resources/linux/lnxGroupResource.md)
* [<span data-ttu-id="0cec3-168">Linux 套件資源</span><span class="sxs-lookup"><span data-stu-id="0cec3-168">Linux Package Resource</span></span>](../reference/resources/linux/lnxPackageResource.md)
* [<span data-ttu-id="0cec3-169">Linux 指令碼資源</span><span class="sxs-lookup"><span data-stu-id="0cec3-169">Linux Script Resource</span></span>](../reference/resources/linux/lnxScriptResource.md)
* [<span data-ttu-id="0cec3-170">Linux 服務資源</span><span class="sxs-lookup"><span data-stu-id="0cec3-170">Linux Service Resource</span></span>](../reference/resources/linux/lnxServiceResource.md)
* [<span data-ttu-id="0cec3-171">Linux SshAuthorizedKeys 資源</span><span class="sxs-lookup"><span data-stu-id="0cec3-171">Linux SshAuthorizedKeys Resource</span></span>](../reference/resources/linux/lnxSshAuthorizedKeysResource.md)
* [<span data-ttu-id="0cec3-172">Linux 使用者資源</span><span class="sxs-lookup"><span data-stu-id="0cec3-172">Linux User Resource</span></span>](../reference/resources/linux/lnxUserResource.md)
