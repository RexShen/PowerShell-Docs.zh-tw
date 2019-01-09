---
ms.date: 12/12/2018
keywords: dsc,powershell,設定,安裝
title: 使用 Import-DSCResource
ms.openlocfilehash: 6bc3c1aa1d34a05e3188666da825322235c0672e
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400769"
---
# <a name="using-import-dscresource"></a><span data-ttu-id="d7055-103">使用 Import-DSCResource</span><span class="sxs-lookup"><span data-stu-id="d7055-103">Using Import-DSCResource</span></span>

<span data-ttu-id="d7055-104">`Import-DScResource` 是動態的關鍵字，只可用於設定指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="d7055-104">`Import-DScResource` is a dynamic keyword, which can only be used inside a Configuration script block.</span></span> <span data-ttu-id="d7055-105">`Import-DSCResource`關鍵字來匯入您的組態中所需的任何資源。</span><span class="sxs-lookup"><span data-stu-id="d7055-105">The `Import-DSCResource` keyword to import any resources needed in your Configuration.</span></span> <span data-ttu-id="d7055-106">下的資源`$phsome`會自動匯入，但它仍然會被視為明確地匯入中所使用的所有資源的最佳做法是您[組態](Configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="d7055-106">Resources under `$phsome` are imported automatically, but it is still considered best practice to explicitly import all resources used in your [Configuration](Configurations.md).</span></span>

<span data-ttu-id="d7055-107">語法`Import-DSCResource`如下所示。</span><span class="sxs-lookup"><span data-stu-id="d7055-107">The syntax for `Import-DSCResource` is shown below.</span></span>

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName(s)>]
```

|<span data-ttu-id="d7055-108">參數</span><span class="sxs-lookup"><span data-stu-id="d7055-108">Parameter</span></span>  |<span data-ttu-id="d7055-109">描述</span><span class="sxs-lookup"><span data-stu-id="d7055-109">Description</span></span>  |
|---------|---------|
|`-Name`|<span data-ttu-id="d7055-110">您必須匯入 DSC 資源名稱。</span><span class="sxs-lookup"><span data-stu-id="d7055-110">The DSC resource name(s) that you must import.</span></span> <span data-ttu-id="d7055-111">如果指定的模組名稱，則命令會搜尋在這個模組中; 這些 DSC 資源否則命令會在所有 DSC 資源路徑中搜尋的 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="d7055-111">If the module name is specified, the command searches for these DSC resources within this module; otherwise the command searches the DSC resources in all DSC resource paths.</span></span> <span data-ttu-id="d7055-112">支援萬用字元。</span><span class="sxs-lookup"><span data-stu-id="d7055-112">Wildcards are supported.</span></span>|
|`-ModuleName`|<span data-ttu-id="d7055-113">容器模組名稱或模組 specification(s)。</span><span class="sxs-lookup"><span data-stu-id="d7055-113">The container module name(s), or module specification(s).</span></span>  <span data-ttu-id="d7055-114">如果您指定要從模組匯入的資源時，命令將嘗試匯入只需將那些資源。</span><span class="sxs-lookup"><span data-stu-id="d7055-114">If you specify resources to import from a module, the command will try to import only those resources.</span></span> <span data-ttu-id="d7055-115">如果您指定了模組只，命令會匯入模組中的所有 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="d7055-115">If you specify the module only, the command imports all the DSC resources in the module.</span></span>|

<span data-ttu-id="d7055-116">您可以使用萬用字元`-Name`參數使用時`Import-DSCResource`。</span><span class="sxs-lookup"><span data-stu-id="d7055-116">You can use wildcards with the `-Name` parameter when using `Import-DSCResource`.</span></span>

```powershell
Import-DscResource -Name * -ModuleName xActiveDirectory;
```

## <a name="example-use-import-dscresource-within-a-configuration"></a><span data-ttu-id="d7055-117">範例：設定中使用 Import-dscresource</span><span class="sxs-lookup"><span data-stu-id="d7055-117">Example: Use Import-DSCResource within a configuration</span></span>

```powershell
Configuration MSDSCConfiguration
{
    # Search for and imports Service, File, and Registry from the module PSDesiredStateConfiguration.
    Import-DSCResource -ModuleName MS_DSC1 -name Service, File, Registry

    # Search for and import Resource1 from the module that defines it.
    # If only –Name parameter is used then resources can belong to different PowerShell modules as well.
    # TimeZone resource is from the ComputerManagementDSC module which is not installed by default.
    Import-DSCResource -Name File, TimeZone

    # Search for and import all DSC resources inside the module PSDesiredStateConfiguration.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration
...
```

> [!NOTE]
> <span data-ttu-id="d7055-118">不支援在相同命令中指定資源名稱和模組名稱的多個值。</span><span class="sxs-lookup"><span data-stu-id="d7055-118">Specifying multiple values for Resource names and modules names in same command are not supported.</span></span> <span data-ttu-id="d7055-119">它可以有不具決定性的行為，如果相同的資源存在於多個模組，從哪一個模組載入哪一個資源的相關。</span><span class="sxs-lookup"><span data-stu-id="d7055-119">It can have non-deterministic behavior about which resource to load from which module in case same resource exists in multiple modules.</span></span> <span data-ttu-id="d7055-120">下列命令會產生錯誤期間編譯。</span><span class="sxs-lookup"><span data-stu-id="d7055-120">Below command will result in error during compilation.</span></span>
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

<span data-ttu-id="d7055-121">使用 Name 參數時要考慮的事項：</span><span class="sxs-lookup"><span data-stu-id="d7055-121">Things to consider when using only the Name parameter:</span></span>

- <span data-ttu-id="d7055-122">這是需要大量資源的作業，視安裝在電腦上的模組數目而定。</span><span class="sxs-lookup"><span data-stu-id="d7055-122">It is a resource-intensive operation depending on the number of modules installed on machine.</span></span>
- <span data-ttu-id="d7055-123">它會載入第一個找到具有指定名稱的資源。</span><span class="sxs-lookup"><span data-stu-id="d7055-123">It will load the first resource found with the given name.</span></span> <span data-ttu-id="d7055-124">在案例中只要有一個以上的資源，與安裝的相同名稱，它無法載入錯誤的資源。</span><span class="sxs-lookup"><span data-stu-id="d7055-124">In the case where there is more than one resource with same name installed, it could load the wrong resource.</span></span>

<span data-ttu-id="d7055-125">建議的用法是指定`–ModuleName`與`-Name`參數，如下所述。</span><span class="sxs-lookup"><span data-stu-id="d7055-125">The recommended usage is to specify `–ModuleName` with the `-Name` parameter, as described below.</span></span>

<span data-ttu-id="d7055-126">這種使用方式的優點如下：</span><span class="sxs-lookup"><span data-stu-id="d7055-126">This usage has the following benefits:</span></span>

- <span data-ttu-id="d7055-127">它可減少限制搜尋範圍對於指定的資源的效能影響。</span><span class="sxs-lookup"><span data-stu-id="d7055-127">It reduces the performance impact by limiting the search scope for the specified resource.</span></span>
- <span data-ttu-id="d7055-128">它會明確定義定義資源，確保正確的資源載入的模組。</span><span class="sxs-lookup"><span data-stu-id="d7055-128">It explicitly defines the module defining the resource, ensuring the correct resource is loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="d7055-129">在 PowerShell 5.0，DSC 資源可以有多個版本，且各版本可於一部電腦上並存安裝。</span><span class="sxs-lookup"><span data-stu-id="d7055-129">In PowerShell 5.0, DSC resources can have multiple versions, and versions can be installed on a computer side-by-side.</span></span> <span data-ttu-id="d7055-130">而其運作方式則是在相同的模組資料夾中，包含多個版本的資源模組。</span><span class="sxs-lookup"><span data-stu-id="d7055-130">This is implemented by having multiple versions of a resource module that are contained in the same module folder.</span></span>
> <span data-ttu-id="d7055-131">如需詳細資訊，請參閱[使用多個版本的資源](sxsresource.md)。</span><span class="sxs-lookup"><span data-stu-id="d7055-131">For more information, see [Using resources with multiple versions](sxsresource.md).</span></span>

## <a name="intellisense-with-import-dscresource"></a><span data-ttu-id="d7055-132">使用 Import-dscresource 的 Intellisense</span><span class="sxs-lookup"><span data-stu-id="d7055-132">Intellisense with Import-DSCResource</span></span>

<span data-ttu-id="d7055-133">當撰寫 ISE 中的 DSC 組態，PowerShell 會提供 IntelliSence 資源和資源內容。</span><span class="sxs-lookup"><span data-stu-id="d7055-133">When authoring the DSC configuration in ISE, PowerShell provides IntelliSence for resources and resource properties.</span></span> <span data-ttu-id="d7055-134">在資源定義`$pshome`會自動載入模組路徑。</span><span class="sxs-lookup"><span data-stu-id="d7055-134">Resource definitions under the `$pshome` module path are loaded automatically.</span></span> <span data-ttu-id="d7055-135">當您匯入使用的資源`Import-DSCResource`關鍵字加入指定的資源定義和 Intellisense 已擴展成包含匯入的資源結構描述。</span><span class="sxs-lookup"><span data-stu-id="d7055-135">When you import resources using the `Import-DSCResource` keyword, the specified resource definitions are added and Intellisense is expanded to include the imported resource's schema.</span></span>

![資源的 Intellisense](/media/resource-intellisense.png)

> [!NOTE]
> <span data-ttu-id="d7055-137">從 PowerShell 5.0 開始，tab 鍵自動完成已新增至 ISE 的 DSC 資源和其屬性。</span><span class="sxs-lookup"><span data-stu-id="d7055-137">Beginning in PowerShell 5.0, tab completion was added to the ISE for DSC resources and their properties.</span></span> <span data-ttu-id="d7055-138">如需詳細資訊，請參閱 <<c0> [ 資源](../resources/resources.md)。</span><span class="sxs-lookup"><span data-stu-id="d7055-138">For more information, see [Resources](../resources/resources.md).</span></span>

<span data-ttu-id="d7055-139">在編譯設定時，PowerShell 會使用匯入的資源定義來驗證在組態中的所有資源區塊。</span><span class="sxs-lookup"><span data-stu-id="d7055-139">When compiling the Configuration, PowerShell uses the imported resource definitions to validate all resource blocks in the configuration.</span></span>
<span data-ttu-id="d7055-140">每個資源區塊會進行驗證，使用資源的結構描述定義，如下列的規則。</span><span class="sxs-lookup"><span data-stu-id="d7055-140">Each resource block is validated, using the resource's schema definition, for the following rules.</span></span>

- <span data-ttu-id="d7055-141">會使用結構描述中定義的屬性。</span><span class="sxs-lookup"><span data-stu-id="d7055-141">Only properties defined in schema are used.</span></span>
- <span data-ttu-id="d7055-142">每個屬性的資料類型正確。</span><span class="sxs-lookup"><span data-stu-id="d7055-142">The data types for each property are correct.</span></span>
- <span data-ttu-id="d7055-143">指定索引鍵屬性。</span><span class="sxs-lookup"><span data-stu-id="d7055-143">Keys properties are specified.</span></span>
- <span data-ttu-id="d7055-144">不使用任何唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="d7055-144">No read-only property is used.</span></span>
- <span data-ttu-id="d7055-145">值的驗證將型別對應。</span><span class="sxs-lookup"><span data-stu-id="d7055-145">Validation on value maps types.</span></span>

<span data-ttu-id="d7055-146">請考慮下列組態：</span><span class="sxs-lookup"><span data-stu-id="d7055-146">Consider the following configuration:</span></span>

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
            Name = “Telnet-Client”
            Ensure = “Invalid”
        }
    }
}
```

<span data-ttu-id="d7055-147">編譯此組態會導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="d7055-147">Compiling this Configuration results in an error.</span></span>

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values ‘Invalid’ is not supported or valid for property ‘Ensure’ on class ‘WindowsFeature’. Please specify only supported values: Present, Absent.
```

<span data-ttu-id="d7055-148">Intellisense 和結構描述驗證可讓您避免複雜，在執行階段剖析和編譯時間，在擷取更多的錯誤。</span><span class="sxs-lookup"><span data-stu-id="d7055-148">Intellisense and schema validation allow you to catch more errors during parse and compilation time, avoiding complications at run time.</span></span>

> [!NOTE]
> <span data-ttu-id="d7055-149">每個 DSC 資源可以有一個名稱，以及**FriendlyName**資源的結構描述所定義。</span><span class="sxs-lookup"><span data-stu-id="d7055-149">Each DSC resource can have a name, and a **FriendlyName** defined by the resource's schema.</span></span> <span data-ttu-id="d7055-150">以下是 「 MSFT_ServiceResource.shema.mof"前兩行。</span><span class="sxs-lookup"><span data-stu-id="d7055-150">Below are the first two lines of "MSFT_ServiceResource.shema.mof".</span></span>
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> <span data-ttu-id="d7055-151">當使用這項資源設定中，您可以指定**MSFT_ServiceResource**或是**服務**。</span><span class="sxs-lookup"><span data-stu-id="d7055-151">When using this resource in a Configuration, you can specify **MSFT_ServiceResource** or **Service**.</span></span>

## <a name="powershell-v4-and-v5-differences"></a><span data-ttu-id="d7055-152">PowerShell v4 和 v5 的差異</span><span class="sxs-lookup"><span data-stu-id="d7055-152">PowerShell v4 and v5 differences</span></span>

<span data-ttu-id="d7055-153">有多個 PowerShell 4.0 vs 中撰寫組態時，您會看到的差異。PowerShell 5.0 及更新版本。</span><span class="sxs-lookup"><span data-stu-id="d7055-153">There are multiple differences you see when authoring Configurations in PowerShell 4.0 vs. PowerShell 5.0 and later.</span></span> <span data-ttu-id="d7055-154">本章節會反白顯示的差異，您會看到與本文相關。</span><span class="sxs-lookup"><span data-stu-id="d7055-154">This section will highlight the differences that you see relevant to this article.</span></span>

### <a name="multiple-resource-versions"></a><span data-ttu-id="d7055-155">多個資源版本</span><span class="sxs-lookup"><span data-stu-id="d7055-155">Multiple Resource Versions</span></span>

<span data-ttu-id="d7055-156">安裝和使用多個版本的資源並排顯示在 PowerShell 4.0 中不支援。</span><span class="sxs-lookup"><span data-stu-id="d7055-156">Installing and using multiple versions of resources side by side was not supported in PowerShell 4.0.</span></span> <span data-ttu-id="d7055-157">如果您注意到資源匯入您的組態問題，請確定您只有一個版本安裝的資源。</span><span class="sxs-lookup"><span data-stu-id="d7055-157">If you notice issues importing resources into your Configuration, ensure that you only have one version of the resource installed.</span></span>

<span data-ttu-id="d7055-158">在下圖中，兩個版本**xPSDesiredStateConfiguration**安裝模組。</span><span class="sxs-lookup"><span data-stu-id="d7055-158">In the image below, two versions of the **xPSDesiredStateConfiguration** module are installed.</span></span>

![已修正的多個資源版本](/media/multiple-resource-versions-broken.md)

<span data-ttu-id="d7055-160">您所需的模組版本的內容複製到模組目錄的上層。</span><span class="sxs-lookup"><span data-stu-id="d7055-160">Copy the contents of your desired module version to the top level of the module directory.</span></span>

![已修正的多個資源版本](/media/multiple-resource-versions-fixed.md)

### <a name="resource-location"></a><span data-ttu-id="d7055-162">資源位置</span><span class="sxs-lookup"><span data-stu-id="d7055-162">Resource location</span></span>

<span data-ttu-id="d7055-163">撰寫和編譯組態，您的資源可以儲存任何指定的目錄中您[PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path)。</span><span class="sxs-lookup"><span data-stu-id="d7055-163">When authoring and compiling Configurations, your resources can be stored in any directory specified by your [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path).</span></span> <span data-ttu-id="d7055-164">在 PowerShell 4.0 中，LCM 會需要儲存在"Program Files\WindowsPowerShell\Modules"下的所有 DSC 資源模組或`$pshome\Modules`。</span><span class="sxs-lookup"><span data-stu-id="d7055-164">In PowerShell 4.0, the LCM requires all DSC resource modules to be stored under "Program Files\WindowsPowerShell\Modules" or `$pshome\Modules`.</span></span> <span data-ttu-id="d7055-165">從 PowerShell 5.0 開始，已移除這項需求，而且資源模組可以儲存任何指定的目錄中`PSModulePath`。</span><span class="sxs-lookup"><span data-stu-id="d7055-165">Beginning in PowerShell 5.0, this requirement was removed, and resource modules can be stored in any directory specified by `PSModulePath`.</span></span>

## <a name="see-also"></a><span data-ttu-id="d7055-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7055-166">See also</span></span>

- [<span data-ttu-id="d7055-167">資源</span><span class="sxs-lookup"><span data-stu-id="d7055-167">Resources</span></span>](../resources/resources.md)
