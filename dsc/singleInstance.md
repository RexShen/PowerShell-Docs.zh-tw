---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,設定,安裝"
title: "撰寫單一執行個體 DSC 資源 (最佳做法)"
ms.openlocfilehash: 4510bec5b4600334b845831ec6700da01e1a110c
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="writing-a-single-instance-dsc-resource-best-practice"></a><span data-ttu-id="30dbe-103">撰寫單一執行個體 DSC 資源 (最佳做法)</span><span class="sxs-lookup"><span data-stu-id="30dbe-103">Writing a single-instance DSC resource (best practice)</span></span>

><span data-ttu-id="30dbe-104">**注意︰**本主題所描述的最佳做法用於定義設定中僅允許單一執行個體的 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="30dbe-104">**Note:** This topic describes a best practice for defining a DSC resource that allows only a single instance in a configuration.</span></span> <span data-ttu-id="30dbe-105">目前，沒有任何內建 DSC 功能可以執行這項作業。</span><span class="sxs-lookup"><span data-stu-id="30dbe-105">Currently, there is no built-in DSC feature to do this.</span></span> <span data-ttu-id="30dbe-106">這在未來可能會變更。</span><span class="sxs-lookup"><span data-stu-id="30dbe-106">That might change in the future.</span></span>

<span data-ttu-id="30dbe-107">有時，您不想允許在設定中多次使用資源。</span><span class="sxs-lookup"><span data-stu-id="30dbe-107">There are situations where you don't want to allow a resource to be used multiple times in a configuration.</span></span> <span data-ttu-id="30dbe-108">例如，在 [xTimeZone](https://github.com/PowerShell/xTimeZone) 資源的先前實作中，於每個資源區塊中將時區設為不同的設定，設定即可多次呼叫資源：</span><span class="sxs-lookup"><span data-stu-id="30dbe-108">For example, in a previous implementation of the [xTimeZone](https://github.com/PowerShell/xTimeZone) resource, a configuration could call the resource multiple times, setting the time zone to a different setting in each resource block:</span></span>

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

<span data-ttu-id="30dbe-109">原因是 DSC 資源金鑰的運作方式。</span><span class="sxs-lookup"><span data-stu-id="30dbe-109">This is because of the way DSC resource keys work.</span></span> <span data-ttu-id="30dbe-110">資源必須至少有一個金鑰屬性。</span><span class="sxs-lookup"><span data-stu-id="30dbe-110">A resource must have at least one key property.</span></span> <span data-ttu-id="30dbe-111">如果資源的所有金鑰屬性值組合皆為唯一，則會將資源執行個體視為唯一。</span><span class="sxs-lookup"><span data-stu-id="30dbe-111">A resource instance is considered unique if the combination of the values of all of its key properties is unique.</span></span> <span data-ttu-id="30dbe-112">在其先前實作中，[xTimeZone](https://github.com/PowerShell/xTimeZone) 資源只有一個屬性 (**TimeZone**)，而這個屬性必須是金鑰。</span><span class="sxs-lookup"><span data-stu-id="30dbe-112">In its previous implementation, the [xTimeZone](https://github.com/PowerShell/xTimeZone) resource had only one property--**TimeZone**, which was required to be a key.</span></span> <span data-ttu-id="30dbe-113">因此，上述這類設定會編譯並執行，而不發出警告。</span><span class="sxs-lookup"><span data-stu-id="30dbe-113">Because of this, a configuration such as the one above would compile and run without warning.</span></span> <span data-ttu-id="30dbe-114">每個 **xTimeZone** 資源區塊都視為唯一的。</span><span class="sxs-lookup"><span data-stu-id="30dbe-114">Each of the **xTimeZone** resource blocks is considered unique.</span></span> <span data-ttu-id="30dbe-115">這會導致將設定重複套用至節點，方法是反覆循環時區。</span><span class="sxs-lookup"><span data-stu-id="30dbe-115">This would cause the configuration to be repeatedly applied to the node, cycling the timezone back and forth.</span></span>

<span data-ttu-id="30dbe-116">若要確保設定僅能設定目標節點的時區一次，則資源已更新成新增成為主要屬性的第二個屬性 (**IsSingleInstance**)。</span><span class="sxs-lookup"><span data-stu-id="30dbe-116">To ensure that a configuration could set the time zone for a target node only once, the resource was updated to add a second property, **IsSingleInstance**, that became the key property.</span></span> <span data-ttu-id="30dbe-117">已使用 **ValueMap**，將 **IsSingleInstance** 限制為單一值 "Yes"。</span><span class="sxs-lookup"><span data-stu-id="30dbe-117">The **IsSingleInstance** was limited to a single value, "Yes" by using a **ValueMap**.</span></span> <span data-ttu-id="30dbe-118">資源的舊 MOF 結構描述為︰</span><span class="sxs-lookup"><span data-stu-id="30dbe-118">The old MOF schema for the resource was:</span></span>

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the TimeZone.")] String TimeZone;
};
```

<span data-ttu-id="30dbe-119">資源的已更新 MOF 結構描述為︰</span><span class="sxs-lookup"><span data-stu-id="30dbe-119">The updated MOF schema for the resource is:</span></span>

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the resource is a single instance, the value must be 'Yes'"), ValueMap{"Yes"}, Values{"Yes"}] String IsSingleInstance;
    [Required, Description("Specifies the TimeZone.")] String TimeZone;
};
```

<span data-ttu-id="30dbe-120">資源指令碼也已更新成使用新的參數。</span><span class="sxs-lookup"><span data-stu-id="30dbe-120">The resource script was also updated to use the new parameter.</span></span> <span data-ttu-id="30dbe-121">以下是舊的資源指令碼：</span><span class="sxs-lookup"><span data-stu-id="30dbe-121">Here is the old resource script:</span></span>

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
    [CmdletBinding(SupportsShouldProcess=$true)]
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
    
    if($PSCmdlet.ShouldProcess("'$TimeZone'","Replace the System Time Zone"))
    {
        try
        {
            if($CurrentTimeZone -ne $TimeZone)
            {
                Write-Verbose -Verbose "Setting the TimeZone"
                Set-TimeZone -TimeZone $TimeZone}
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

<span data-ttu-id="30dbe-122">請注意，**TimeZone** 屬性不再是索引鍵。</span><span class="sxs-lookup"><span data-stu-id="30dbe-122">Notice that the **TimeZone** property is no longer a key.</span></span> <span data-ttu-id="30dbe-123">現在，如果設定嘗試設定時區兩次 (使用兩個具有不同 **TimeZone** 值的不同 **xTimeZone** 區塊)，則嘗試編譯設定將會導致錯誤︰</span><span class="sxs-lookup"><span data-stu-id="30dbe-123">Now, if a configuration attempts to set the time zone twice (by using two different **xTimeZone** blocks with different **TimeZone** values), attempting to compile the configuration will cause an error:</span></span>

```powershell
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
   
