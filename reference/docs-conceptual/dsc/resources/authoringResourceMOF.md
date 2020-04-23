---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 撰寫自訂的 DSC 資源與 MOF
ms.openlocfilehash: 24e9d15bcbe1eddd297daeb04e0713c443e52c38
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "71952895"
---
# <a name="writing-a-custom-dsc-resource-with-mof"></a><span data-ttu-id="317fb-103">撰寫自訂的 DSC 資源與 MOF</span><span class="sxs-lookup"><span data-stu-id="317fb-103">Writing a custom DSC resource with MOF</span></span>

> <span data-ttu-id="317fb-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="317fb-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="317fb-105">本主題中，我們會在 MOF 檔案中定義 Windows PowerShell 預期狀態設定 (DSC) 自訂資源的結構描述，並在 Windows PowerShell 指令碼檔案中實作資源。</span><span class="sxs-lookup"><span data-stu-id="317fb-105">In this topic, we will define the schema for a Windows PowerShell Desired State Configuration (DSC) custom resource in a MOF file, and implement the resource in a Windows PowerShell script file.</span></span> <span data-ttu-id="317fb-106">這個自訂的資源是用於建立和維護網站。</span><span class="sxs-lookup"><span data-stu-id="317fb-106">This custom resource is for creating and maintaining a web site.</span></span>

## <a name="creating-the-mof-schema"></a><span data-ttu-id="317fb-107">建立 MOF 結構描述</span><span class="sxs-lookup"><span data-stu-id="317fb-107">Creating the MOF schema</span></span>

<span data-ttu-id="317fb-108">結構描述會定義可由 DSC 設定指令碼設定之資源的屬性。</span><span class="sxs-lookup"><span data-stu-id="317fb-108">The schema defines the properties of your resource that can be configured by a DSC configuration script.</span></span>

### <a name="folder-structure-for-a-mof-resource"></a><span data-ttu-id="317fb-109">MOF 資源的資料夾結構</span><span class="sxs-lookup"><span data-stu-id="317fb-109">Folder structure for a MOF resource</span></span>

<span data-ttu-id="317fb-110">若要使用 MOF 結構描述實作 DSC 自訂資源，請建立下列資料夾結構。</span><span class="sxs-lookup"><span data-stu-id="317fb-110">To implement a DSC custom resource with a MOF schema, create the following folder structure.</span></span> <span data-ttu-id="317fb-111">MOF 結構描述是定義在 Demo_IISWebsite.schema.mof 檔案中，而資源指令碼是定義在 Demo_IISWebsite.psm1 中。</span><span class="sxs-lookup"><span data-stu-id="317fb-111">The MOF schema is defined in the file Demo_IISWebsite.schema.mof, and the resource script is defined in Demo_IISWebsite.psm1.</span></span> <span data-ttu-id="317fb-112">您也可以建立模組資訊清單 (psd1) 檔案。</span><span class="sxs-lookup"><span data-stu-id="317fb-112">Optionally, you can create a module manifest (psd1) file.</span></span>

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResources (folder)
        |- DSCResources (folder)
            |- Demo_IISWebsite (folder)
                |- Demo_IISWebsite.psd1 (file, optional)
                |- Demo_IISWebsite.psm1 (file, required)
                |- Demo_IISWebsite.schema.mof (file, required)
```

<span data-ttu-id="317fb-113">請注意，你必須在最上層的資料夾下建立名為 DSCResources 的資料夾，而且每個資源的資料夾都必須和資源同名。</span><span class="sxs-lookup"><span data-stu-id="317fb-113">Note that it is necessary to create a folder named DSCResources under the top-level folder, and that the folder for each resource must have the same name as the resource.</span></span>

### <a name="the-contents-of-the-mof-file"></a><span data-ttu-id="317fb-114">MOF 檔案的內容</span><span class="sxs-lookup"><span data-stu-id="317fb-114">The contents of the MOF file</span></span>

<span data-ttu-id="317fb-115">下面的範例 MOF 檔案可用於自訂的網站資源。</span><span class="sxs-lookup"><span data-stu-id="317fb-115">Following is an example MOF file that can be used for a custom website resource.</span></span> <span data-ttu-id="317fb-116">若要依此範例操作，請將這個結構描述儲存至檔案，並呼叫檔案 *Demo_IISWebsite.schema.mof*。</span><span class="sxs-lookup"><span data-stu-id="317fb-116">To follow this example, save this schema to a file, and call the file *Demo_IISWebsite.schema.mof*.</span></span>

```
[ClassVersion("1.0.0"), FriendlyName("Website")]
class Demo_IISWebsite : OMI_BaseResource
{
  [Key] string Name;
  [Required] string PhysicalPath;
  [write,ValueMap{"Present", "Absent"},Values{"Present", "Absent"}] string Ensure;
  [write,ValueMap{"Started","Stopped"},Values{"Started", "Stopped"}] string State;
  [write] string Protocol[];
  [write] string BindingInfo[];
  [write] string ApplicationPool;
  [read] string ID;
};
```

<span data-ttu-id="317fb-117">前列程式碼請注意下列事項：</span><span class="sxs-lookup"><span data-stu-id="317fb-117">Note the following about the previous code:</span></span>

* <span data-ttu-id="317fb-118">`FriendlyName` 定義的名稱，可用來參考 DSC 設定指令碼的這個自訂資源。</span><span class="sxs-lookup"><span data-stu-id="317fb-118">`FriendlyName` defines the name you can use to refer to this custom resource in DSC configuration scripts.</span></span> <span data-ttu-id="317fb-119">在本例中，`Website` 相當於內建 Archive 資源的易記名稱 `Archive`。</span><span class="sxs-lookup"><span data-stu-id="317fb-119">In this example, `Website` is equivalent to the friendly name `Archive` for the built-in Archive resource.</span></span>
* <span data-ttu-id="317fb-120">您為自訂資源定義的類別必須衍生自 `OMI_BaseResource`。</span><span class="sxs-lookup"><span data-stu-id="317fb-120">The class you define for your custom resource must derive from `OMI_BaseResource`.</span></span>
* <span data-ttu-id="317fb-121">屬性上的類型限定詞 `[Key]`，表示這個屬性會唯一識別資源執行個體。</span><span class="sxs-lookup"><span data-stu-id="317fb-121">The type qualifier, `[Key]`, on a property indicates that this property will uniquely identify the resource instance.</span></span> <span data-ttu-id="317fb-122">至少有一個 `[Key]` 屬性是必要屬性。</span><span class="sxs-lookup"><span data-stu-id="317fb-122">At least one `[Key]` property is required.</span></span>
* <span data-ttu-id="317fb-123">`[Required]` 限定詞表示必要屬性 (使用這項資源的任何設定指令碼都必須指定的值)。</span><span class="sxs-lookup"><span data-stu-id="317fb-123">The `[Required]` qualifier indicates that the property is required (a value must be specified in any configuration script that uses this resource).</span></span>
* <span data-ttu-id="317fb-124">`[write]` 限定詞表示，在設定指令碼中使用自訂資源時，這是選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="317fb-124">The `[write]` qualifier indicates that this property is optional when using the custom resource in a configuration script.</span></span> <span data-ttu-id="317fb-125">`[read]` 限定詞表示設定不能設定屬性，且限用於報告。</span><span class="sxs-lookup"><span data-stu-id="317fb-125">The `[read]` qualifier indicates that a property cannot be set by a configuration, and is for reporting purposes only.</span></span>
* <span data-ttu-id="317fb-126">`Values` 限制可指派給在 `ValueMap` 定義的值清單之屬性的值。</span><span class="sxs-lookup"><span data-stu-id="317fb-126">`Values` restricts the values that can be assigned to the property to the list of values defined in `ValueMap`.</span></span> <span data-ttu-id="317fb-127">如需詳細資訊，請參閱 [ValueMap and Value Qualifiers (ValueMap 和值限定詞)](/windows/desktop/WmiSdk/value-map)。</span><span class="sxs-lookup"><span data-stu-id="317fb-127">For more information, see [ValueMap and Value Qualifiers](/windows/desktop/WmiSdk/value-map).</span></span>
* <span data-ttu-id="317fb-128">建議您在資源中包含名為 `Ensure`且值為 `Present` 和 `Absent` 的屬性，以便和內建的 DSC 資源維持一致的樣式。</span><span class="sxs-lookup"><span data-stu-id="317fb-128">Including a property called `Ensure` with values `Present` and `Absent` in your resource is recommended as a way to maintain a consistent style with built-in DSC resources.</span></span>
* <span data-ttu-id="317fb-129">依下列方式命名自訂資源的結構描述檔案：`classname.schema.mof`，其中 `classname` 是遵循結構描述定義 `class` 關鍵字的識別碼。</span><span class="sxs-lookup"><span data-stu-id="317fb-129">Name the schema file for your custom resource as follows: `classname.schema.mof`, where `classname` is the identifier that follows the `class` keyword in your schema definition.</span></span>

### <a name="writing-the-resource-script"></a><span data-ttu-id="317fb-130">撰寫資源指令碼</span><span class="sxs-lookup"><span data-stu-id="317fb-130">Writing the resource script</span></span>

<span data-ttu-id="317fb-131">資源指令碼會實作資源的邏輯。</span><span class="sxs-lookup"><span data-stu-id="317fb-131">The resource script implements the logic of the resource.</span></span> <span data-ttu-id="317fb-132">這個模組中必須包含三個函式，它們是：**Get-TargetResource**、**Set-TargetResource** 和 **Test-TargetResource**。</span><span class="sxs-lookup"><span data-stu-id="317fb-132">In this module, you must include three functions called **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource**.</span></span> <span data-ttu-id="317fb-133">這三個函式都必須使用與您為資源建立的 MOF 結構描述所定義之屬性集相同的參數集。</span><span class="sxs-lookup"><span data-stu-id="317fb-133">All three functions must take a parameter set that is identical to the set of properties defined in the MOF schema that you created for your resource.</span></span> <span data-ttu-id="317fb-134">在本文件中，這個屬性集稱為「資源屬性」。</span><span class="sxs-lookup"><span data-stu-id="317fb-134">In this document, this set of properties is referred to as the "resource properties."</span></span> <span data-ttu-id="317fb-135">將這三個函式存放在 <ResourceName>.psm1 檔案中。</span><span class="sxs-lookup"><span data-stu-id="317fb-135">Store these three functions in a file called <ResourceName>.psm1.</span></span> <span data-ttu-id="317fb-136">在下例中，這些函式存放在 Demo_IISWebsite.psm1 檔案中。</span><span class="sxs-lookup"><span data-stu-id="317fb-136">In the following example, the functions are stored in a file called Demo_IISWebsite.psm1.</span></span>

> [!NOTE]
> <span data-ttu-id="317fb-137">當您在資源上多次執行相同的設定指令碼時，您應該不會收到任何錯誤，而且資源的狀態也應該和只執行一次指令碼的狀態相同。</span><span class="sxs-lookup"><span data-stu-id="317fb-137">When you run the same configuration script on your resource more than once, you should receive no errors and the resource should remain in the same state as running the script once.</span></span> <span data-ttu-id="317fb-138">若要達成這個目標，請確認 **Get-TargetResource** 和 **Test-TargetResource** 函式不變更資源，而且以相同參數順序值多次叫用 **Set-TargetResource** 函式永遠等於只叫用一次。</span><span class="sxs-lookup"><span data-stu-id="317fb-138">To accomplish this, ensure that your **Get-TargetResource** and **Test-TargetResource** functions leave the resource unchanged, and that invoking the **Set-TargetResource** function more than once in a sequence with the same parameter values is always equivalent to invoking it once.</span></span>

<span data-ttu-id="317fb-139">在 **Get-TargetResource** 函式的實作中，使用提供為參數的重要資源屬性值，檢查指定的資源執行個體狀態。</span><span class="sxs-lookup"><span data-stu-id="317fb-139">In the **Get-TargetResource** function implementation, use the key resource property values that are provided as parameters to check the status of the specified resource instance.</span></span> <span data-ttu-id="317fb-140">這個函式必須傳回雜湊表，將所有的資源屬性列為索引鍵，這些屬性的實際值列為對應值。</span><span class="sxs-lookup"><span data-stu-id="317fb-140">This function must return a hash table that lists all the resource properties as keys and the actual values of these properties as the corresponding values.</span></span> <span data-ttu-id="317fb-141">範例請見下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="317fb-141">The following code provides an example.</span></span>

```powershell
# DSC uses the Get-TargetResource function to fetch the status of the resource instance specified in the parameters for the target machine
function Get-TargetResource
{
    param
    (
        [ValidateSet("Present", "Absent")]
        [string]$Ensure = "Present",

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$Name,

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$PhysicalPath,

        [ValidateSet("Started", "Stopped")]
        [string]$State = "Started",

        [string]$ApplicationPool,

        [string[]]$BindingInfo,

        [string[]]$Protocol
    )

        $getTargetResourceResult = $null;

        <# Insert logic that uses the mandatory parameter values to get the website and assign it to a variable called $Website #>
        <# Set $ensureResult to "Present" if the requested website exists and to "Absent" otherwise #>

        # Add all Website properties to the hash table
        # This simple example assumes that $Website is not null
        $getTargetResourceResult = @{
                                      Name = $Website.Name;
                                        Ensure = $ensureResult;
                                        PhysicalPath = $Website.physicalPath;
                                        State = $Website.state;
                                        ID = $Website.id;
                                        ApplicationPool = $Website.applicationPool;
                                        Protocol = $Website.bindings.Collection.protocol;
                                        Binding = $Website.bindings.Collection.bindingInformation;
                                    }

        $getTargetResourceResult;
}
```

<span data-ttu-id="317fb-142">依據設定指令碼中為資源屬性指定的值，**Set-TargetResource** 必須執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="317fb-142">Depending on the values that are specified for the resource properties in the configuration script, the **Set-TargetResource** must do one of the following:</span></span>

* <span data-ttu-id="317fb-143">建立新的網站</span><span class="sxs-lookup"><span data-stu-id="317fb-143">Create a new website</span></span>
* <span data-ttu-id="317fb-144">更新現有的網站</span><span class="sxs-lookup"><span data-stu-id="317fb-144">Update an existing website</span></span>
* <span data-ttu-id="317fb-145">刪除現有的網站</span><span class="sxs-lookup"><span data-stu-id="317fb-145">Delete an existing website</span></span>

<span data-ttu-id="317fb-146">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="317fb-146">The following example illustrates this.</span></span>

```powershell
# The Set-TargetResource function is used to create, delete or configure a website on the target machine.
function Set-TargetResource
{
    [CmdletBinding(SupportsShouldProcess=$true)]
    param
    (
        [ValidateSet("Present", "Absent")]
        [string]$Ensure = "Present",

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$Name,

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$PhysicalPath,

        [ValidateSet("Started", "Stopped")]
        [string]$State = "Started",

        [string]$ApplicationPool,

        [string[]]$BindingInfo,

        [string[]]$Protocol
    )

    <# If Ensure is set to "Present" and the website specified in the mandatory input parameters does not exist, then create it using the specified parameter values #>
    <# Else, if Ensure is set to "Present" and the website does exist, then update its properties to match the values provided in the non-mandatory parameter values #>
    <# Else, if Ensure is set to "Absent" and the website does not exist, then do nothing #>
    <# Else, if Ensure is set to "Absent" and the website does exist, then delete the website #>
}
```

<span data-ttu-id="317fb-147">最後，**Test-TargetResource** 函式必須和 **Get-TargetResource** 及 **Set-TargetResource** 使用相同的參數集。</span><span class="sxs-lookup"><span data-stu-id="317fb-147">Finally, the **Test-TargetResource** function must take the same parameter set as **Get-TargetResource** and **Set-TargetResource**.</span></span> <span data-ttu-id="317fb-148">在 **Test-TargetResource** 的實作中，檢查於索引鍵參數中指定的資源執行個體狀態。</span><span class="sxs-lookup"><span data-stu-id="317fb-148">In your implementation of **Test-TargetResource**, check the status of the resource instance that is specified in the key parameters.</span></span> <span data-ttu-id="317fb-149">如果資源執行個體的實際狀態不符合參數集指定的值，則傳回 **$false**。</span><span class="sxs-lookup"><span data-stu-id="317fb-149">If the actual status of the resource instance does not match the values specified in the parameter set, return **$false**.</span></span> <span data-ttu-id="317fb-150">否則傳回 **$true**。</span><span class="sxs-lookup"><span data-stu-id="317fb-150">Otherwise, return **$true**.</span></span>

<span data-ttu-id="317fb-151">下列程式碼會實作 **Test-TargetResource** 函式。</span><span class="sxs-lookup"><span data-stu-id="317fb-151">The following code implements the **Test-TargetResource** function.</span></span>

```powershell
function Test-TargetResource
{
[CmdletBinding()]
[OutputType([System.Boolean])]
param
(
[ValidateSet("Present","Absent")]
[System.String]
$Ensure,

[parameter(Mandatory = $true)]
[System.String]
$Name,

[parameter(Mandatory = $true)]
[System.String]
$PhysicalPath,

[ValidateSet("Started","Stopped")]
[System.String]
$State,

[System.String[]]
$Protocol,

[System.String[]]
$BindingData,

[System.String]
$ApplicationPool
)

#Write-Verbose "Use this cmdlet to deliver information about command processing."

#Write-Debug "Use this cmdlet to write debug information while troubleshooting."


#Include logic to
$result = [System.Boolean]
#Add logic to test whether the website is present and its status mathes the supplied parameter values. If it does, return true. If it does not, return false.
$result
}
```

<span data-ttu-id="317fb-152">**注意**：為方便偵錯，請在前述三個函式實作中使用 **Write-Verbose** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="317fb-152">**Note**: For easier debugging, use the **Write-Verbose** cmdlet in your implementation of the previous three functions.</span></span>
><span data-ttu-id="317fb-153">這個 Cmdlet 會將文字寫入詳細資訊訊息串流中。</span><span class="sxs-lookup"><span data-stu-id="317fb-153">This cmdlet writes text to the verbose message stream.</span></span>
><span data-ttu-id="317fb-154">預設不顯示詳細資訊訊息串流，但您可以變更 **$VerbosePreference** 變數的值或在 DSC cmdlets = new 中使用 **Verbose** 參數來顯示它。</span><span class="sxs-lookup"><span data-stu-id="317fb-154">By default, the verbose message stream is not displayed, but you can display it by changing the value of the **$VerbosePreference** variable or by using the **Verbose** parameter in the DSC cmdlets = new.</span></span>

### <a name="creating-the-module-manifest"></a><span data-ttu-id="317fb-155">建立模組資訊清單</span><span class="sxs-lookup"><span data-stu-id="317fb-155">Creating the module manifest</span></span>

<span data-ttu-id="317fb-156">最後，使用 **New-ModuleManifest** Cmdlet 定義自訂資源模組的 <ResourceName>.psd1 檔案。</span><span class="sxs-lookup"><span data-stu-id="317fb-156">Finally, use the **New-ModuleManifest** cmdlet to define a <ResourceName>.psd1 file for your custom resource module.</span></span> <span data-ttu-id="317fb-157">當您叫用這個 Cmdlet 時，請參考上節所述的指令碼模組 (.psm1) 檔案。</span><span class="sxs-lookup"><span data-stu-id="317fb-157">When you invoke this cmdlet, reference the script module (.psm1) file described in the previous section.</span></span> <span data-ttu-id="317fb-158">在要匯出的函式清單中包含 **Get-TargetResource**、**Set-TargetResource** 和 **Test-TargetResource**。</span><span class="sxs-lookup"><span data-stu-id="317fb-158">Include **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** in the list of functions to export.</span></span> <span data-ttu-id="317fb-159">以下為資訊清單檔案範例。</span><span class="sxs-lookup"><span data-stu-id="317fb-159">Following is an example manifest file.</span></span>

```powershell
# Module manifest for module 'Demo.IIS.Website'
#
# Generated on: 1/10/2013
#

@{

# Script module or binary module file associated with this manifest.
# RootModule = ''

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = '6AB5ED33-E923-41d8-A3A4-5ADDA2B301DE'

# Author of this module
Author = 'Contoso'

# Company or vendor of this module
CompanyName = 'Contoso'

# Copyright statement for this module
Copyright = 'Contoso. All rights reserved.'

# Description of the functionality provided by this module
Description = 'This Module is used to support the creation and configuration of IIS Websites through Get, Set and Test API on the DSC managed nodes.'

# Minimum version of the Windows PowerShell engine required by this module
PowerShellVersion = '4.0'

# Minimum version of the common language runtime (CLR) required by this module
CLRVersion = '4.0'

# Modules that must be imported into the global environment prior to importing this module
RequiredModules = @("WebAdministration")

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
NestedModules = @("Demo_IISWebsite.psm1")

# Functions to export from this module
FunctionsToExport = @("Get-TargetResource", "Set-TargetResource", "Test-TargetResource")

# Cmdlets to export from this module
#CmdletsToExport = '*'

# HelpInfo URI of this module
# HelpInfoURI = ''
}
```

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="317fb-160">支援 PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="317fb-160">Supporting PsDscRunAsCredential</span></span>

><span data-ttu-id="317fb-161">**注意：** PowerShell 5.0 或更新版本中支援 **PsDscRunAsCredential**。</span><span class="sxs-lookup"><span data-stu-id="317fb-161">**Note:** **PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="317fb-162">您可以在 [DSC 設定](../configurations/configurations.md)資源區塊中使用 **PsDscRunAsCredential** 特性，以指定該資源應該在一組指定的認證下執行。</span><span class="sxs-lookup"><span data-stu-id="317fb-162">The **PsDscRunAsCredential** property can be used in [DSC configurations](../configurations/configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span>
<span data-ttu-id="317fb-163">如需詳細資訊，請參閱[以使用者認證執行 DSC](../configurations/runAsUser.md)。</span><span class="sxs-lookup"><span data-stu-id="317fb-163">For more information, see [Running DSC with user credentials](../configurations/runAsUser.md).</span></span>

<span data-ttu-id="317fb-164">若要從自訂資源內存取使用者內容，您可以使用自動變數 `$PsDscContext`。</span><span class="sxs-lookup"><span data-stu-id="317fb-164">To access the user context from within a custom resource, you can use the automatic variable `$PsDscContext`.</span></span>

<span data-ttu-id="317fb-165">例如，下列程式碼會將資源執行位置的上層使用者內容寫入到詳細的輸出資料流：</span><span class="sxs-lookup"><span data-stu-id="317fb-165">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="rebooting-the-node"></a><span data-ttu-id="317fb-166">重新啟動節點</span><span class="sxs-lookup"><span data-stu-id="317fb-166">Rebooting the Node</span></span>

<span data-ttu-id="317fb-167">若在您 `Set-TargetResource` 函式中採取的動作需要重新啟動，您可以使用全域旗標來告知 LCM 重新啟動節點。</span><span class="sxs-lookup"><span data-stu-id="317fb-167">If the actions taken in your `Set-TargetResource` function require a reboot, you can use a global flag to tell the LCM to reboot the Node.</span></span> <span data-ttu-id="317fb-168">此重新啟動會在 `Set-TargetResource` 函式完成後直接發生。</span><span class="sxs-lookup"><span data-stu-id="317fb-168">This reboot occurs directly after the `Set-TargetResource` function completes.</span></span>

<span data-ttu-id="317fb-169">在您 `Set-TargetResource` 函式的內部，請新增下列這行程式碼。</span><span class="sxs-lookup"><span data-stu-id="317fb-169">Inside your `Set-TargetResource` function, add the following line of code.</span></span>

```powershell
# Include this line if the resource requires a system reboot.
$global:DSCMachineStatus = 1
```

<span data-ttu-id="317fb-170">為了讓 LCM 重新啟動節點，**RebootNodeIfNeeded** 旗標必須設為 `$true`。</span><span class="sxs-lookup"><span data-stu-id="317fb-170">In order for the LCM to reboot the Node, the **RebootNodeIfNeeded** flag needs to be set to `$true`.</span></span> <span data-ttu-id="317fb-171">**ActionAfterReboot** 設定也應設為 **ContinueConfiguration** (預設值)。</span><span class="sxs-lookup"><span data-stu-id="317fb-171">The **ActionAfterReboot** setting should also be set to **ContinueConfiguration**, which is the default.</span></span> <span data-ttu-id="317fb-172">如需設定 LCM 的詳細資訊，請參閱[設定本機設定管理員](../managing-nodes/metaConfig.md)或[設定本機設定管理員 (v4)](../managing-nodes/metaConfig4.md)。</span><span class="sxs-lookup"><span data-stu-id="317fb-172">For more information on configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md), or [Configuring the Local Configuration Manager (v4)](../managing-nodes/metaConfig4.md).</span></span>
