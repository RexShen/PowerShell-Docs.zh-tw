---
ms.date: 07/08/2020
keywords: dsc,powershell,設定,安裝
title: 撰寫單一執行個體 DSC 資源 (最佳做法)
ms.openlocfilehash: cd6048c0f8aeef7fb5458a5f0bfefef25169297c
ms.sourcegitcommit: d26e2237397483c6333abcf4331bd82f2e72b4e3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2020
ms.locfileid: "86217605"
---
# <a name="writing-a-single-instance-dsc-resource-best-practice"></a><span data-ttu-id="f8b37-103">撰寫單一執行個體 DSC 資源 (最佳做法)</span><span class="sxs-lookup"><span data-stu-id="f8b37-103">Writing a single-instance DSC resource (best practice)</span></span>

> [!NOTE]
> <span data-ttu-id="f8b37-104">這個主題會說明要定義在設定中只允許單一執行個體的 DSC 資源時的最佳做法。</span><span class="sxs-lookup"><span data-stu-id="f8b37-104">This topic describes a best practice for defining a DSC resource that allows only a single instance in a configuration.</span></span> <span data-ttu-id="f8b37-105">目前，沒有任何內建 DSC 功能可以執行這項作業。</span><span class="sxs-lookup"><span data-stu-id="f8b37-105">Currently, there is no built-in DSC feature to do this.</span></span> <span data-ttu-id="f8b37-106">這在未來可能會變更。</span><span class="sxs-lookup"><span data-stu-id="f8b37-106">That might change in the future.</span></span>

<span data-ttu-id="f8b37-107">有時，您不想允許在設定中多次使用資源。</span><span class="sxs-lookup"><span data-stu-id="f8b37-107">There are situations where you don't want to allow a resource to be used multiple times in a configuration.</span></span> <span data-ttu-id="f8b37-108">例如，在 [xTimeZone](https://github.com/PowerShell/xTimeZone) 資源的先前實作中，於每個資源區塊中將時區設為不同的設定，設定即可多次呼叫資源：</span><span class="sxs-lookup"><span data-stu-id="f8b37-108">For example, in a previous implementation of the [xTimeZone](https://github.com/PowerShell/xTimeZone) resource, a configuration could call the resource multiple times, setting the time zone to a different setting in each resource block:</span></span>

```powershell
Configuration SetTimeZone
{
    Param
    (
        [String[]]$NodeName = $env:COMPUTERNAME

    )

    Import-DSCResource -ModuleName xTimeZone


    Node $NodeName
    {
         xTimeZone TimeZoneExample
         {

            TimeZone = 'Eastern Standard Time'
         }

         xTimeZone TimeZoneExample2
         {

            TimeZone = 'Pacific Standard Time'

         }

    }
}
```

<span data-ttu-id="f8b37-109">原因是 DSC 資源金鑰的運作方式。</span><span class="sxs-lookup"><span data-stu-id="f8b37-109">This is because of the way DSC resource keys work.</span></span> <span data-ttu-id="f8b37-110">資源必須至少有一個金鑰屬性。</span><span class="sxs-lookup"><span data-stu-id="f8b37-110">A resource must have at least one key property.</span></span> <span data-ttu-id="f8b37-111">如果資源的所有金鑰屬性值組合皆為唯一，則會將資源執行個體視為唯一。</span><span class="sxs-lookup"><span data-stu-id="f8b37-111">A resource instance is considered unique if the combination of the values of all of its key properties is unique.</span></span> <span data-ttu-id="f8b37-112">在其先前實作中，[xTimeZone](https://github.com/PowerShell/xTimeZone) 資源只有一個屬性 (**TimeZone**)，而這個屬性必須是金鑰。</span><span class="sxs-lookup"><span data-stu-id="f8b37-112">In its previous implementation, the [xTimeZone](https://github.com/PowerShell/xTimeZone) resource had only one property--**TimeZone**, which was required to be a key.</span></span> <span data-ttu-id="f8b37-113">因此，上述這類設定會編譯並執行，而不發出警告。</span><span class="sxs-lookup"><span data-stu-id="f8b37-113">Because of this, a configuration such as the one above would compile and run without warning.</span></span> <span data-ttu-id="f8b37-114">每個 **xTimeZone** 資源區塊都視為唯一的。</span><span class="sxs-lookup"><span data-stu-id="f8b37-114">Each of the **xTimeZone** resource blocks is considered unique.</span></span> <span data-ttu-id="f8b37-115">這會導致將設定重複套用至節點，方法是反覆循環時區。</span><span class="sxs-lookup"><span data-stu-id="f8b37-115">This would cause the configuration to be repeatedly applied to the node, cycling the timezone back and forth.</span></span>

<span data-ttu-id="f8b37-116">若要確保設定僅能設定目標節點的時區一次，則資源已更新成新增成為主要屬性的第二個屬性 (**IsSingleInstance**)。</span><span class="sxs-lookup"><span data-stu-id="f8b37-116">To ensure that a configuration could set the time zone for a target node only once, the resource was updated to add a second property, **IsSingleInstance**, that became the key property.</span></span> <span data-ttu-id="f8b37-117">已使用 **ValueMap**，將 **IsSingleInstance** 限制為單一值 "Yes"。</span><span class="sxs-lookup"><span data-stu-id="f8b37-117">The **IsSingleInstance** was limited to a single value, "Yes" by using a **ValueMap**.</span></span> <span data-ttu-id="f8b37-118">資源的舊 MOF 結構描述為︰</span><span class="sxs-lookup"><span data-stu-id="f8b37-118">The old MOF schema for the resource was:</span></span>

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the TimeZone.")] String TimeZone;
};
```

<span data-ttu-id="f8b37-119">資源的已更新 MOF 結構描述為︰</span><span class="sxs-lookup"><span data-stu-id="f8b37-119">The updated MOF schema for the resource is:</span></span>

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the resource is a single instance, the value must be 'Yes'"), ValueMap{"Yes"}, Values{"Yes"}] String IsSingleInstance;
    [Required, Description("Specifies the TimeZone.")] String TimeZone;
};
```

<span data-ttu-id="f8b37-120">資源指令碼也已更新成使用新的參數。</span><span class="sxs-lookup"><span data-stu-id="f8b37-120">The resource script was also updated to use the new parameter.</span></span> <span data-ttu-id="f8b37-121">資源指令碼的變更方式如下：</span><span class="sxs-lookup"><span data-stu-id="f8b37-121">Here how the resource script was changed:</span></span>

```powershell
function Get-TargetResource
{
    [CmdletBinding()]
    [OutputType([Hashtable])]
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateSet('Yes')]
        [String]
        $IsSingleInstance,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $TimeZone
    )

    #Get the current TimeZone
    $CurrentTimeZone = Get-TimeZone

    $returnValue = @{
        TimeZone = $CurrentTimeZone
        IsSingleInstance = 'Yes'
    }

    #Output the target resource
    $returnValue
}

function Set-TargetResource
{
    [CmdletBinding()]
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateSet('Yes')]
        [String]
        $IsSingleInstance,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $TimeZone
    )

    #Output the result of Get-TargetResource function.
    $CurrentTimeZone = Get-TimeZone

    Write-Verbose -Message "Replace the System Time Zone to $TimeZone"

    try
    {
        if($CurrentTimeZone -ne $TimeZone)
        {
            Write-Verbose -Verbose "Setting the TimeZone"
            Set-TimeZone -TimeZone $TimeZone
        }
        else
        {
            Write-Verbose -Verbose "TimeZone already set to $TimeZone"
        }
    }
    catch
    {
        $ErrorMsg = $_.Exception.Message
        Write-Verbose -Verbose $ErrorMsg
    }
}


function Test-TargetResource
{
    [CmdletBinding()]
    [OutputType([Boolean])]
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateSet('Yes')]
        [String]
        $IsSingleInstance,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $TimeZone
    )

    #Output from Get-TargetResource
    $CurrentTimeZone = Get-TimeZone

    if($TimeZone -eq $CurrentTimeZone)
    {
        return $true
    }
    else
    {
        return $false
    }
}

Function Get-TimeZone {
    [CmdletBinding()]
    param()

    & tzutil.exe /g
}

Function Set-TimeZone {
    [CmdletBinding()]
    param(
        [Parameter(Mandatory=$true)]
        [System.String]
        $TimeZone
    )

    try
    {
        & tzutil.exe /s $TimeZone
    }
    catch
    {
        $ErrorMsg = $_.Exception.Message
        Write-Verbose $ErrorMsg
    }
}

Export-ModuleMember -Function *-TargetResource
```

<span data-ttu-id="f8b37-122">請注意，**TimeZone** 屬性不再是索引鍵。</span><span class="sxs-lookup"><span data-stu-id="f8b37-122">Notice that the **TimeZone** property is no longer a key.</span></span> <span data-ttu-id="f8b37-123">現在，如果設定嘗試設定時區兩次 (使用兩個具有不同 **TimeZone** 值的不同 **xTimeZone** 區塊)，則嘗試編譯設定將會導致錯誤︰</span><span class="sxs-lookup"><span data-stu-id="f8b37-123">Now, if a configuration attempts to set the time zone twice (by using two different **xTimeZone** blocks with different **TimeZone** values), attempting to compile the configuration will cause an error:</span></span>

```Output
Test-ConflictingResources : A conflict was detected between resources '[xTimeZone]TimeZoneExample (::15::10::xTimeZone)' and
'[xTimeZone]TimeZoneExample2 (::22::10::xTimeZone)' in node 'CONTOSO-CLIENT'. Resources have identical key properties but there are differences in the
following non-key properties: 'TimeZone'. Values 'Eastern Standard Time' don't match values 'Pacific Standard Time'. Please update these property
values so that they are identical in both cases.
At line:271 char:9
+         Test-ConflictingResources $keywordName $canonicalizedValue $k ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Write-Error], InvalidOperationException
    + FullyQualifiedErrorId : ConflictingDuplicateResource,Test-ConflictingResources
Errors occurred while processing configuration 'SetTimeZone'.
At C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:3705 char:5
+     throw $ErrorRecord
+     ~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (SetTimeZone:String) [], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessConfiguration
```
