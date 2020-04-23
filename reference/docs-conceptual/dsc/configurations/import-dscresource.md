---
ms.date: 12/12/2018
keywords: dsc,powershell,設定,安裝
title: 使用 Import-DSCResource
ms.openlocfilehash: a041169ad557becf7ca87641d9ce5222ee8f6beb
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "79402445"
---
# <a name="using-import-dscresource"></a><span data-ttu-id="0e0c4-103">使用 Import-DSCResource</span><span class="sxs-lookup"><span data-stu-id="0e0c4-103">Using Import-DSCResource</span></span>

<span data-ttu-id="0e0c4-104">`Import-DScResource` 是動態關鍵字，只能在設定指令碼區塊中使用。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-104">`Import-DScResource` is a dynamic keyword, which can only be used inside a Configuration script block.</span></span> <span data-ttu-id="0e0c4-105">`Import-DSCResource` 關鍵字用於匯入設定中所需的任何資源。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-105">The `Import-DSCResource` keyword to import any resources needed in your Configuration.</span></span> <span data-ttu-id="0e0c4-106">`$pshome` 下的資源會自動匯入，但明確地匯入[設定](Configurations.md)中使用的所有資源仍被視為最佳做法。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-106">Resources under `$pshome` are imported automatically, but it is still considered best practice to explicitly import all resources used in your [Configuration](Configurations.md).</span></span>

<span data-ttu-id="0e0c4-107">`Import-DSCResource` 語法如下所示。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-107">The syntax for `Import-DSCResource` is shown below.</span></span>  <span data-ttu-id="0e0c4-108">依名稱指定模組時，需要在新行上列出每個模組。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-108">When specifying modules by name, it is a requirement to list each on a new line.</span></span>

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>] [-ModuleVersion <ModuleVersion>]
```

|<span data-ttu-id="0e0c4-109">參數</span><span class="sxs-lookup"><span data-stu-id="0e0c4-109">Parameter</span></span>  |<span data-ttu-id="0e0c4-110">描述</span><span class="sxs-lookup"><span data-stu-id="0e0c4-110">Description</span></span>  |
|---------|---------|
|`-Name`|<span data-ttu-id="0e0c4-111">您必須匯入 DSC 資源名稱。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-111">The DSC resource name(s) that you must import.</span></span> <span data-ttu-id="0e0c4-112">如果指定了模組名稱，則該命令將在此模組中搜尋這些 DSC 資源；否則該命令會在所有 DSC 資源路徑中搜尋 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-112">If the module name is specified, the command searches for these DSC resources within this module; otherwise the command searches the DSC resources in all DSC resource paths.</span></span> <span data-ttu-id="0e0c4-113">支援萬用字元。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-113">Wildcards are supported.</span></span>|
|`-ModuleName`|<span data-ttu-id="0e0c4-114">模組名稱，或模組規格。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-114">The module name, or module specification.</span></span>  <span data-ttu-id="0e0c4-115">如果您指定了要從模組匯入的資源，該命令將嘗試僅匯入這些資源。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-115">If you specify resources to import from a module, the command will try to import only those resources.</span></span> <span data-ttu-id="0e0c4-116">如果僅指定模組，則該命令將匯入模組中的所有 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-116">If you specify the module only, the command imports all the DSC resources in the module.</span></span>|
|`-ModuleVersion`|<span data-ttu-id="0e0c4-117">從 PowerShell 5.0 開始，您可以指定設定應使用的模組版本。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-117">Beginning in PowerShell 5.0, you can specify which version of a module a configuration should use.</span></span> <span data-ttu-id="0e0c4-118">如需詳細資訊，請參閱[匯入所安裝資源的特定版本](sxsresource.md)。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-118">For more information, see [Import a specific version of an installed resource](sxsresource.md).</span></span>|

```powershell
Import-DscResource -ModuleName xActiveDirectory
```

## <a name="example-use-import-dscresource-within-a-configuration"></a><span data-ttu-id="0e0c4-119">範例：在設定中使用 Import-DSCResource</span><span class="sxs-lookup"><span data-stu-id="0e0c4-119">Example: Use Import-DSCResource within a configuration</span></span>

```powershell
Configuration MSDSCConfiguration
{
    # Search for and imports Service, File, and Registry from the module PSDesiredStateConfiguration.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration -Name Service, File, Registry

    # Search for and import Resource1 from the module that defines it.
    # If only –Name parameter is used then resources can belong to different PowerShell modules as well.
    # TimeZone resource is from the ComputerManagementDSC module which is not installed by default.
    # As a best practice, list each requirement on a different line if possible.  This makes reviewing
    # multiple changes in source control a bit easier.
    Import-DSCResource -Name File
    Import-DSCResource -Name TimeZone

    # Search for and import all DSC resources inside the module PSDesiredStateConfiguration.
    # When specifying the modulename parameter, it is a requirement to list each on a new line.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration
    # In PowerShell 5.0 and later, you can specify a ModuleVersion parameter
    Import-DSCResource -ModuleName ComputerManagementDsc -ModuleVersion 6.0.0.0
...
```

> [!NOTE]
> <span data-ttu-id="0e0c4-120">不支援在相同命令中為資源名稱和模組名稱指定多個值。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-120">Specifying multiple values for Resource names and modules names in same command are not supported.</span></span> <span data-ttu-id="0e0c4-121">在多個模組中存在相同資源的情況下，它可能具有關於從哪一個模組載入哪一個資源的非確定性行為。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-121">It can have non-deterministic behavior about which resource to load from which module in case same resource exists in multiple modules.</span></span> <span data-ttu-id="0e0c4-122">以下命令將導致編譯期間發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-122">Below command will result in error during compilation.</span></span>
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

<span data-ttu-id="0e0c4-123">僅使用 Name 參數時要考慮的事項：</span><span class="sxs-lookup"><span data-stu-id="0e0c4-123">Things to consider when using only the Name parameter:</span></span>

- <span data-ttu-id="0e0c4-124">這是需要大量資源的作業，具體取決於電腦上安裝的模組數目。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-124">It is a resource-intensive operation depending on the number of modules installed on machine.</span></span>
- <span data-ttu-id="0e0c4-125">它會載入使用指定名稱找到的第一個資源。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-125">It will load the first resource found with the given name.</span></span> <span data-ttu-id="0e0c4-126">如果安裝了多個具有相同名稱的資源，則可能會載入錯誤的資源。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-126">In the case where there is more than one resource with same name installed, it could load the wrong resource.</span></span>

<span data-ttu-id="0e0c4-127">建議的用法是使用 `-Name` 參數指定 `–ModuleName`，如下所述。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-127">The recommended usage is to specify `–ModuleName` with the `-Name` parameter, as described below.</span></span>

<span data-ttu-id="0e0c4-128">此用法提供了下列優點：</span><span class="sxs-lookup"><span data-stu-id="0e0c4-128">This usage has the following benefits:</span></span>

- <span data-ttu-id="0e0c4-129">它透過限制指定資源的搜尋範圍來降低效能影響。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-129">It reduces the performance impact by limiting the search scope for the specified resource.</span></span>
- <span data-ttu-id="0e0c4-130">它明確定義了定義資源的模組，確保載入正確的資源。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-130">It explicitly defines the module defining the resource, ensuring the correct resource is loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="0e0c4-131">在 PowerShell 5.0，DSC 資源可以有多個版本，且各版本可於一部電腦上並存安裝。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-131">In PowerShell 5.0, DSC resources can have multiple versions, and versions can be installed on a computer side-by-side.</span></span> <span data-ttu-id="0e0c4-132">而其運作方式則是在相同的模組資料夾中，包含多個版本的資源模組。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-132">This is implemented by having multiple versions of a resource module that are contained in the same module folder.</span></span>
> <span data-ttu-id="0e0c4-133">如需詳細資訊，請參閱[使用多個版本的資源](sxsresource.md)。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-133">For more information, see [Using resources with multiple versions](sxsresource.md).</span></span>

## <a name="intellisense-with-import-dscresource"></a><span data-ttu-id="0e0c4-134">使用 Import-DSCResource 的 Intellisense</span><span class="sxs-lookup"><span data-stu-id="0e0c4-134">Intellisense with Import-DSCResource</span></span>

<span data-ttu-id="0e0c4-135">在 ISE 中撰寫 DSC 設定時，PowerShell 會為資源和資源內容提供 IntelliSense。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-135">When authoring the DSC configuration in ISE, PowerShell provides IntelliSence for resources and resource properties.</span></span> <span data-ttu-id="0e0c4-136">`$pshome` 模組路徑下的資源定義會自動載入。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-136">Resource definitions under the `$pshome` module path are loaded automatically.</span></span> <span data-ttu-id="0e0c4-137">使用 `Import-DSCResource` 關鍵字匯入資源時，將加入指定的資源定義，並擴展 Intellisense 以包含匯入的資源結構描述。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-137">When you import resources using the `Import-DSCResource` keyword, the specified resource definitions are added and Intellisense is expanded to include the imported resource's schema.</span></span>

![資源 Intellisense](media/import-dscresource/resource-intellisense.png)

> [!NOTE]
> <span data-ttu-id="0e0c4-139">從 PowerShell 5.0 開始，Tab 鍵自動完成已新增至 ISE 以取得 DSC 資源和其屬性。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-139">Beginning in PowerShell 5.0, tab completion was added to the ISE for DSC resources and their properties.</span></span> <span data-ttu-id="0e0c4-140">如需詳細資訊，請參閱[資源](../resources/resources.md)。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-140">For more information, see [Resources](../resources/resources.md).</span></span>

<span data-ttu-id="0e0c4-141">在編譯設定時，PowerShell 會使用匯入的資源定義來驗證設定中的所有資源區塊。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-141">When compiling the Configuration, PowerShell uses the imported resource definitions to validate all resource blocks in the configuration.</span></span>
<span data-ttu-id="0e0c4-142">使用資源的結構描述定義驗證每個資源區塊，以用於下列規則。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-142">Each resource block is validated, using the resource's schema definition, for the following rules.</span></span>

- <span data-ttu-id="0e0c4-143">僅使用結構描述中定義的屬性。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-143">Only properties defined in schema are used.</span></span>
- <span data-ttu-id="0e0c4-144">每個屬性的資料類型都是正確的。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-144">The data types for each property are correct.</span></span>
- <span data-ttu-id="0e0c4-145">指定索引鍵屬性。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-145">Keys properties are specified.</span></span>
- <span data-ttu-id="0e0c4-146">不使用任何唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-146">No read-only property is used.</span></span>
- <span data-ttu-id="0e0c4-147">驗證值對應類型。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-147">Validation on value maps types.</span></span>

<span data-ttu-id="0e0c4-148">請考慮下列設定：</span><span class="sxs-lookup"><span data-stu-id="0e0c4-148">Consider the following configuration:</span></span>

```powershell
Configuration SchemaValidationInCorrectEnumValue
{
    # It is best practice to explicitly import all resources used in your Configuration.
    # This includes resources that are imported automatically, like WindowsFeature.
    Import-DSCResource -Name WindowsFeature
    Node localhost
    {
        WindowsFeature ROLE1
        {
            Name = "Telnet-Client"
            Ensure = "Invalid"
        }
    }
}
```

<span data-ttu-id="0e0c4-149">編譯此設定會導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-149">Compiling this Configuration results in an error.</span></span>

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values 'Invalid' is not supported or valid for property 'Ensure' on class 'WindowsFeature'. Please specify only supported values: Present, Absent.
```

<span data-ttu-id="0e0c4-150">Intellisense 和結構描述驗證允許您在剖析和編譯時間擷取更多的錯誤，從而避免在執行階段出現複雜情況。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-150">Intellisense and schema validation allow you to catch more errors during parse and compilation time, avoiding complications at run time.</span></span>

> [!NOTE]
> <span data-ttu-id="0e0c4-151">每個 DSC 資源都可以有一個名稱，以及由結構描述所定義的 **FriendlyName**。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-151">Each DSC resource can have a name, and a **FriendlyName** defined by the resource's schema.</span></span> <span data-ttu-id="0e0c4-152">以下是 "MSFT_ServiceResource.shema.mof" 的前兩行。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-152">Below are the first two lines of "MSFT_ServiceResource.shema.mof".</span></span>
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> <span data-ttu-id="0e0c4-153">在設定中使用此資源時，您可以指定 **MSFT_ServiceResource** 或 **Service**。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-153">When using this resource in a Configuration, you can specify **MSFT_ServiceResource** or **Service**.</span></span>

## <a name="powershell-v4-and-v5-differences"></a><span data-ttu-id="0e0c4-154">PowerShell v4 和 v5 的差異</span><span class="sxs-lookup"><span data-stu-id="0e0c4-154">PowerShell v4 and v5 differences</span></span>

<span data-ttu-id="0e0c4-155">在 PowerShell 4.0 與PowerShell 5.0 及更新版本中撰寫設定時，您會看到多種差異。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-155">There are multiple differences you see when authoring Configurations in PowerShell 4.0 vs. PowerShell 5.0 and later.</span></span> <span data-ttu-id="0e0c4-156">本節將重點介紹您認為與本文相關的差異。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-156">This section will highlight the differences that you see relevant to this article.</span></span>

### <a name="multiple-resource-versions"></a><span data-ttu-id="0e0c4-157">多個資源版本</span><span class="sxs-lookup"><span data-stu-id="0e0c4-157">Multiple Resource Versions</span></span>

<span data-ttu-id="0e0c4-158">PowerShell 4.0 不支援並排安裝和使用多個版本的資源。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-158">Installing and using multiple versions of resources side by side was not supported in PowerShell 4.0.</span></span> <span data-ttu-id="0e0c4-159">如果您發現將資源匯入設定時出現問題，請確定您只安裝了一個版本的資源。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-159">If you notice issues importing resources into your Configuration, ensure that you only have one version of the resource installed.</span></span>

<span data-ttu-id="0e0c4-160">在下圖中，安裝了 **xPSDesiredStateConfiguration** 模組的兩個版本。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-160">In the image below, two versions of the **xPSDesiredStateConfiguration** module are installed.</span></span>

![已修正多個資源版本](media/import-dscresource/multiple-resource-versions-broken.png)

<span data-ttu-id="0e0c4-162">將所需模組版本的內容複製到模組目錄的上層。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-162">Copy the contents of your desired module version to the top level of the module directory.</span></span>

![已修正多個資源版本](media/import-dscresource/multiple-resource-versions-fixed.png)

### <a name="resource-location"></a><span data-ttu-id="0e0c4-164">資源位置</span><span class="sxs-lookup"><span data-stu-id="0e0c4-164">Resource location</span></span>

<span data-ttu-id="0e0c4-165">在撰寫和編譯設定時，您的資源可以儲存在 [PSModulePath](/powershell/scripting/developer/module/modifying-the-psmodulepath-installation-path) 指定的任何目錄中。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-165">When authoring and compiling Configurations, your resources can be stored in any directory specified by your [PSModulePath](/powershell/scripting/developer/module/modifying-the-psmodulepath-installation-path).</span></span> <span data-ttu-id="0e0c4-166">在 PowerShell 4.0 中，LCM 要求所有 DSC 資源模組都儲存在 "Program Files\WindowsPowerShell\Modules" 或 `$pshome\Modules` 下。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-166">In PowerShell 4.0, the LCM requires all DSC resource modules to be stored under "Program Files\WindowsPowerShell\Modules" or `$pshome\Modules`.</span></span> <span data-ttu-id="0e0c4-167">從 PowerShell 5.0 開始，已移除此需求，資源模組可以儲存在 `PSModulePath` 指定的任何目錄中。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-167">Beginning in PowerShell 5.0, this requirement was removed, and resource modules can be stored in any directory specified by `PSModulePath`.</span></span>

### <a name="moduleversion-added"></a><span data-ttu-id="0e0c4-168">已新增 ModuleVersion</span><span class="sxs-lookup"><span data-stu-id="0e0c4-168">ModuleVersion added</span></span>

<span data-ttu-id="0e0c4-169">從 PowerShell 5.0 開始，`-ModuleVersion` 參數可讓您指定要在設定中使用的模組版本。</span><span class="sxs-lookup"><span data-stu-id="0e0c4-169">Beginning in PowerShell 5.0, the `-ModuleVersion` parameter allows you to specify which version of a module to use within your configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="0e0c4-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e0c4-170">See also</span></span>

- [<span data-ttu-id="0e0c4-171">資源</span><span class="sxs-lookup"><span data-stu-id="0e0c4-171">Resources</span></span>](../resources/resources.md)
