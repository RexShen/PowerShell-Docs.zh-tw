---
ms.date: 07/08/2020
keywords: dsc,powershell,設定,安裝
title: 使用 [資源設計工具] 工具
description: 資源設計工具是一組 Cmdlet，由 xDscResourceDesigner 模組所公開，可讓建立 PowerShell DSC 資源變得更為容易。
ms.openlocfilehash: efe36d045ac3fba3823cb1f812bb5761d238fdf1
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656488"
---
# <a name="using-the-resource-designer-tool"></a><span data-ttu-id="16371-104">使用 [資源設計工具] 工具</span><span class="sxs-lookup"><span data-stu-id="16371-104">Using the Resource Designer tool</span></span>

> <span data-ttu-id="16371-105">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="16371-105">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="16371-106">資源設計工具是一組 Cmdlet 工具，由 **xDscResourceDesigner** 模組所公開，讓建立 Windows PowerShell 預期狀態設定 (DSC) 資源變得更為容易。</span><span class="sxs-lookup"><span data-stu-id="16371-106">The Resource Designer tool is a set of cmdlets exposed by the **xDscResourceDesigner** module that make creating Windows PowerShell Desired State Configuration (DSC) resources easier.</span></span> <span data-ttu-id="16371-107">這項資源中的 Cmdlet 會協助您建立新資源的 MOF 結構描述、指令碼模組和目錄結構。</span><span class="sxs-lookup"><span data-stu-id="16371-107">The cmdlets in this resource help create the MOF schema, the script module, and the directory structure for your new resource.</span></span> <span data-ttu-id="16371-108">如需 DSC 資源的詳細資訊，請參閱[建置自訂的 Windows PowerShell 預期狀態設定資源](authoringResource.md)。</span><span class="sxs-lookup"><span data-stu-id="16371-108">For more information about DSC resources, see [Build Custom Windows PowerShell Desired State Configuration Resources](authoringResource.md).</span></span> <span data-ttu-id="16371-109">在此文章中，我們將會建立管理 Active Directory 使用者的 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="16371-109">In this article, we will create a DSC resource that manages Active Directory users.</span></span> <span data-ttu-id="16371-110">請使用 [Install-Module](/powershell/module/PowershellGet/Install-Module) Cmdlet 安裝 **xDscResourceDesigner** 模組。</span><span class="sxs-lookup"><span data-stu-id="16371-110">Use the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to install the **xDscResourceDesigner** module.</span></span>

## <a name="creating-resource-properties"></a><span data-ttu-id="16371-111">建立資源屬性</span><span class="sxs-lookup"><span data-stu-id="16371-111">Creating resource properties</span></span>

<span data-ttu-id="16371-112">首先決定資源要公開的屬性。</span><span class="sxs-lookup"><span data-stu-id="16371-112">The first thing we need to do is decide on properties that the resource will expose.</span></span> <span data-ttu-id="16371-113">本例中，我們會定義具有下列屬性的 Active Directory 使用者。</span><span class="sxs-lookup"><span data-stu-id="16371-113">For this example, we will define an Active Directory user with the following properties.</span></span>

<span data-ttu-id="16371-114">參數名稱描述</span><span class="sxs-lookup"><span data-stu-id="16371-114">Parameter name  Description</span></span>

- <span data-ttu-id="16371-115">**UserName** ：唯一識別使用者的索引鍵屬性。</span><span class="sxs-lookup"><span data-stu-id="16371-115">**UserName** : Key property that uniquely identifies a user.</span></span>
- <span data-ttu-id="16371-116">**Ensure** ：指定使用者帳戶應為 Present 或 Absent。</span><span class="sxs-lookup"><span data-stu-id="16371-116">**Ensure** : Specifies whether the user account should be Present or Absent.</span></span> <span data-ttu-id="16371-117">這個參數只會有兩個可能的值。</span><span class="sxs-lookup"><span data-stu-id="16371-117">This parameter will have only two possible values.</span></span>
- <span data-ttu-id="16371-118">**DomainCredential** ：使用者的網域密碼。</span><span class="sxs-lookup"><span data-stu-id="16371-118">**DomainCredential** : The domain password for the user.</span></span>
- <span data-ttu-id="16371-119">**Password** ：使用者視需要允許設定變更使用者密碼所要使用的密碼。</span><span class="sxs-lookup"><span data-stu-id="16371-119">**Password** : The desired password for the user to allow a configuration to change the user password if necessary.</span></span>

<span data-ttu-id="16371-120">我們使用 `New-xDscResourceProperty` Cmdlet 建立屬性。</span><span class="sxs-lookup"><span data-stu-id="16371-120">To create the properties, we use the `New-xDscResourceProperty` cmdlet.</span></span> <span data-ttu-id="16371-121">下列 PowerShell 命令會建立上述的屬性。</span><span class="sxs-lookup"><span data-stu-id="16371-121">The following PowerShell commands create the properties described above.</span></span>

```powershell
$UserName = New-xDscResourceProperty –Name UserName -Type String -Attribute Key
$Ensure = New-xDscResourceProperty –Name Ensure -Type String -Attribute Write –ValidateSet "Present", "Absent"
$DomainCredential = New-xDscResourceProperty –Name DomainCredential -Type PSCredential -Attribute Write
$Password = New-xDscResourceProperty –Name Password -Type PSCredential -Attribute Write
```

## <a name="create-the-resource"></a><span data-ttu-id="16371-122">建立資源</span><span class="sxs-lookup"><span data-stu-id="16371-122">Create the resource</span></span>

<span data-ttu-id="16371-123">資源屬性既已建立，即可呼叫 `New-xDscResource` Cmdlet 來建立資源。</span><span class="sxs-lookup"><span data-stu-id="16371-123">Now that the resource properties have been created, we can call the `New-xDscResource` cmdlet to create the resource.</span></span> <span data-ttu-id="16371-124">`New-xDscResource` Cmdlet 會使用屬性清單作為參數。</span><span class="sxs-lookup"><span data-stu-id="16371-124">The `New-xDscResource` cmdlet takes the list of properties as parameters.</span></span> <span data-ttu-id="16371-125">它也會使用應建立模組位置的路徑、新資源的名稱和包含它的模組名稱。</span><span class="sxs-lookup"><span data-stu-id="16371-125">It also takes the path where the module should be created, the name of the new resource, and the name of the module in which it is contained.</span></span> <span data-ttu-id="16371-126">下列 PowerShell 命令會建立資源。</span><span class="sxs-lookup"><span data-stu-id="16371-126">The following PowerShell command creates the resource.</span></span>

```powershell
New-xDscResource –Name Demo_ADUser –Property $UserName, $Ensure, $DomainCredential, $Password –Path 'C:\Program Files\WindowsPowerShell\Modules' –ModuleName Demo_DSCModule
```

<span data-ttu-id="16371-127">`New-xDscResource` Cmdlet 會建立 MOF 結構描述、基本架構資源指令碼、新資源的必要目錄結構和公開新資源的模組資訊清單。</span><span class="sxs-lookup"><span data-stu-id="16371-127">The `New-xDscResource` cmdlet creates the MOF schema, a skeleton resource script, the required directory structure for your new resource, and a manifest for the module that exposes the new resource.</span></span>

<span data-ttu-id="16371-128">MOF 結構描述檔案位在 `C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof`，其內容如下所示。</span><span class="sxs-lookup"><span data-stu-id="16371-128">The MOF schema file is at `C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof`, and its contents are as follows.</span></span>

```
[ClassVersion("1.0.0.0"), FriendlyName("Demo_ADUser")]
class Demo_ADUser : OMI_BaseResource
{
  [Key] string UserName;
  [Write, ValueMap{"Present","Absent"}, Values{"Present","Absent"}] string Ensure;
  [Write, EmbeddedInstance("MSFT_Credential")] String DomainCredential;
  [Write, EmbeddedInstance("MSFT_Credential")] String Password;
};
```

<span data-ttu-id="16371-129">資源指令碼位在 `C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1`。</span><span class="sxs-lookup"><span data-stu-id="16371-129">The resource script is at `C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1`.</span></span>
<span data-ttu-id="16371-130">它不包含實作資源的實際邏輯，您必須自己加入。</span><span class="sxs-lookup"><span data-stu-id="16371-130">It does not include the actual logic to implement the resource, which you must add yourself.</span></span> <span data-ttu-id="16371-131">基本架構指令碼的內容如下。</span><span class="sxs-lookup"><span data-stu-id="16371-131">The contents of the skeleton script are as follows.</span></span>

```powershell
function Get-TargetResource
{
  [CmdletBinding()]
  [OutputType([System.Collections.Hashtable])]
  param
  (
    [parameter(Mandatory = $true)]
    [System.String]
    $UserName
  )

  #Write-Verbose "Use this cmdlet to deliver information about command processing."

  #Write-Debug "Use this cmdlet to write debug information while troubleshooting."

  <#
  $returnValue = @{
  UserName = [System.String]
  Ensure = [System.String]
  DomainAdminCredential = [System.Management.Automation.PSCredential]
  Password = [System.Management.Automation.PSCredential]
  }

  $returnValue
  #>
}

function Set-TargetResource
{
  [CmdletBinding()]
  param
  (
    [parameter(Mandatory = $true)]
    [System.String]
    $UserName,

    [ValidateSet("Present","Absent")]
    [System.String]
    $Ensure,

    [System.Management.Automation.PSCredential]
    $DomainAdminCredential,

    [System.Management.Automation.PSCredential]
    $Password
  )

  #Write-Verbose "Use this cmdlet to deliver information about command processing."

  #Write-Debug "Use this cmdlet to write debug information while troubleshooting."

  #Include this line if the resource requires a system reboot.
  #$global:DSCMachineStatus = 1
}

function Test-TargetResource
{
  [CmdletBinding()]
  [OutputType([System.Boolean])]
  param
  (
    [parameter(Mandatory = $true)]
    [System.String]
    $UserName,

    [ValidateSet("Present","Absent")]
    [System.String]
    $Ensure,

    [System.Management.Automation.PSCredential]
    $DomainAdminCredential,

    [System.Management.Automation.PSCredential]
    $Password
  )

  #Write-Verbose "Use this cmdlet to deliver information about command processing."

  #Write-Debug "Use this cmdlet to write debug information while troubleshooting."

  <#
  $result = [System.Boolean]

  $result
  #>
}

Export-ModuleMember -Function *-TargetResource
```

## <a name="updating-the-resource"></a><span data-ttu-id="16371-132">更新資源</span><span class="sxs-lookup"><span data-stu-id="16371-132">Updating the resource</span></span>

<span data-ttu-id="16371-133">如果必須新增或修改資源的參數清單，則可呼叫 `Update-xDscResource` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="16371-133">If you need to add or modify the parameter list of the resource, you can call the `Update-xDscResource` cmdlet.</span></span> <span data-ttu-id="16371-134">此 Cmdlet 會用新的參數清單更新資源。</span><span class="sxs-lookup"><span data-stu-id="16371-134">The cmdlet updates the resource with a new parameter list.</span></span> <span data-ttu-id="16371-135">如果資源指令碼中已加入邏輯，它會保持不變。</span><span class="sxs-lookup"><span data-stu-id="16371-135">If you have already added logic in your resource script, it is left intact.</span></span>

<span data-ttu-id="16371-136">例如，假設您想要在資源中包含使用者最後一次的登入時間。</span><span class="sxs-lookup"><span data-stu-id="16371-136">For example, suppose you want to include the last log in time for the user in our resource.</span></span> <span data-ttu-id="16371-137">您可呼叫 `New-xDscResourceProperty` 來建立新的屬性，然後呼叫 `Update-xDscResource` 將新屬性新增至屬性清單中，不用再重新撰寫一次資源。</span><span class="sxs-lookup"><span data-stu-id="16371-137">Rather than writing the resource again completely, you can call the `New-xDscResourceProperty` to create the new property, and then call `Update-xDscResource` and add your new property to the properties list.</span></span>

```powershell
$lastLogon = New-xDscResourceProperty –Name LastLogon –Type Hashtable –Attribute Write –Description "For mapping users to their last log on time"
Update-xDscResource –Name 'Demo_ADUser' –Property $UserName, $Ensure, $DomainCredential, $Password, $lastLogon -Force
```

## <a name="testing-a-resource-schema"></a><span data-ttu-id="16371-138">測試資源的結構描述</span><span class="sxs-lookup"><span data-stu-id="16371-138">Testing a resource schema</span></span>

<span data-ttu-id="16371-139">[資源設計工具] 工具會多公開一個 Cmdlet，其可用來測試您手動撰寫的 MOF 結構描述的有效性。</span><span class="sxs-lookup"><span data-stu-id="16371-139">The Resource Designer tool exposes one more cmdlet that can be used to test the validity of a MOF schema that you have written manually.</span></span> <span data-ttu-id="16371-140">呼叫 `Test-xDscSchema` Cmdlet，將 MOF 資源結構描述的路徑傳遞為參數。</span><span class="sxs-lookup"><span data-stu-id="16371-140">Call the `Test-xDscSchema` cmdlet, passing the path of a MOF resource schema as a parameter.</span></span> <span data-ttu-id="16371-141">此 Cmdlet 會輸出結構描述中的所有錯誤。</span><span class="sxs-lookup"><span data-stu-id="16371-141">The cmdlet will output any errors in the schema.</span></span>

### <a name="see-also"></a><span data-ttu-id="16371-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16371-142">See Also</span></span>

#### <a name="concepts"></a><span data-ttu-id="16371-143">概念</span><span class="sxs-lookup"><span data-stu-id="16371-143">Concepts</span></span>

[<span data-ttu-id="16371-144">建置自訂的 Windows PowerShell 預期狀態設定資源</span><span class="sxs-lookup"><span data-stu-id="16371-144">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](authoringResource.md)

#### <a name="other-resources"></a><span data-ttu-id="16371-145">其他資源</span><span class="sxs-lookup"><span data-stu-id="16371-145">Other Resources</span></span>

[<span data-ttu-id="16371-146">xDscResourceDesigner 模組</span><span class="sxs-lookup"><span data-stu-id="16371-146">xDscResourceDesigner Module</span></span>](https://www.powershellgallery.com/packages/xDscResourceDesigner/1.12.0.0)
