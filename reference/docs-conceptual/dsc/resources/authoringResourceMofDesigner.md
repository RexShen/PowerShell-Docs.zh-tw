---
ms.date: 06/12/2017
keywords: dsc,powershell,設定,安裝
title: 使用 [資源設計工具] 工具
ms.openlocfilehash: 9e7488e922bdca70bb152e7e976077e43cfad7af
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83692192"
---
# <a name="using-the-resource-designer-tool"></a><span data-ttu-id="b1541-103">使用 [資源設計工具] 工具</span><span class="sxs-lookup"><span data-stu-id="b1541-103">Using the Resource Designer tool</span></span>

> <span data-ttu-id="b1541-104">適用於：Windows PowerShell 4.0、Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b1541-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="b1541-105">資源設計工具是一組 Cmdlet 工具，由 **xDscResourceDesigner** 模組所公開，讓建立 Windows PowerShell 預期狀態設定 (DSC) 資源變得更為容易。</span><span class="sxs-lookup"><span data-stu-id="b1541-105">The Resource Designer tool is a set of cmdlets exposed by the **xDscResourceDesigner** module that make creating Windows PowerShell Desired State Configuration (DSC) resources easier.</span></span> <span data-ttu-id="b1541-106">這項資源中的 Cmdlet 會協助您建立新資源的 MOF 結構描述、指令碼模組和目錄結構。</span><span class="sxs-lookup"><span data-stu-id="b1541-106">The cmdlets in this resource help create the MOF schema, the script module, and the directory structure for your new resource.</span></span> <span data-ttu-id="b1541-107">如需 DSC 資源的詳細資訊，請參閱[建置自訂的 Windows PowerShell 預期狀態設定資源](authoringResource.md)。</span><span class="sxs-lookup"><span data-stu-id="b1541-107">For more information about DSC resources, see [Build Custom Windows PowerShell Desired State Configuration Resources](authoringResource.md).</span></span> <span data-ttu-id="b1541-108">在本主題中，我們會建立管理 Active Directory 使用者的 DSC 資源。</span><span class="sxs-lookup"><span data-stu-id="b1541-108">In this topic, we will create a DSC resource that manages Active Directory users.</span></span> <span data-ttu-id="b1541-109">請使用 [Install-Module](/powershell/module/PowershellGet/Install-Module) Cmdlet 安裝 **xDscResourceDesigner** 模組。</span><span class="sxs-lookup"><span data-stu-id="b1541-109">Use the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to install the **xDscResourceDesigner** module.</span></span>

## <a name="creating-resource-properties"></a><span data-ttu-id="b1541-110">建立資源屬性</span><span class="sxs-lookup"><span data-stu-id="b1541-110">Creating resource properties</span></span>
<span data-ttu-id="b1541-111">首先決定資源要公開的屬性。</span><span class="sxs-lookup"><span data-stu-id="b1541-111">The first thing we need to do is decide on properties that the resource will expose.</span></span> <span data-ttu-id="b1541-112">本例中，我們會定義具有下列屬性的 Active Directory 使用者。</span><span class="sxs-lookup"><span data-stu-id="b1541-112">For this example, we will define an Active Directory user with the following properties.</span></span>

<span data-ttu-id="b1541-113">參數名稱描述</span><span class="sxs-lookup"><span data-stu-id="b1541-113">Parameter name  Description</span></span>

* <span data-ttu-id="b1541-114">**UserName**：唯一識別使用者的索引鍵屬性。</span><span class="sxs-lookup"><span data-stu-id="b1541-114">**UserName**: Key property that uniquely identifies a user.</span></span>
* <span data-ttu-id="b1541-115">**Ensure**：指定使用者帳戶應為 Present 或 Absent。</span><span class="sxs-lookup"><span data-stu-id="b1541-115">**Ensure**: Specifies whether the user account should be Present or Absent.</span></span> <span data-ttu-id="b1541-116">這個參數只會有兩個可能的值。</span><span class="sxs-lookup"><span data-stu-id="b1541-116">This parameter will have only two possible values.</span></span>
* <span data-ttu-id="b1541-117">**DomainCredential**：使用者的網域密碼。</span><span class="sxs-lookup"><span data-stu-id="b1541-117">**DomainCredential**: The domain password for the user.</span></span>
* <span data-ttu-id="b1541-118">**Password**：使用者視需要允許設定變更使用者密碼所要使用的密碼。</span><span class="sxs-lookup"><span data-stu-id="b1541-118">**Password**: The desired password for the user to allow a configuration to change the user password if necessary.</span></span>

<span data-ttu-id="b1541-119">我們使用 **New-xDscResourceProperty** Cmdlet 建立屬性。</span><span class="sxs-lookup"><span data-stu-id="b1541-119">To create the properties, we use the **New-xDscResourceProperty** cmdlet.</span></span> <span data-ttu-id="b1541-120">下列 PowerShell 命令會建立上述的屬性。</span><span class="sxs-lookup"><span data-stu-id="b1541-120">The following PowerShell commands create the properties described above.</span></span>

```powershell
$UserName = New-xDscResourceProperty –Name UserName -Type String -Attribute Key
$Ensure = New-xDscResourceProperty –Name Ensure -Type String -Attribute Write –ValidateSet "Present", "Absent"
$DomainCredential = New-xDscResourceProperty –Name DomainCredential -Type PSCredential -Attribute Write
$Password = New-xDscResourceProperty –Name Password -Type PSCredential -Attribute Write
```

## <a name="create-the-resource"></a><span data-ttu-id="b1541-121">建立資源</span><span class="sxs-lookup"><span data-stu-id="b1541-121">Create the resource</span></span>

<span data-ttu-id="b1541-122">資源屬性既已建立，我們就可以呼叫 **New-xDscResource** Cmdlet 來建立資源。</span><span class="sxs-lookup"><span data-stu-id="b1541-122">Now that the resource properties have been created, we can call the **New-xDscResource** cmdlet to create the resource.</span></span> <span data-ttu-id="b1541-123">**New-xDscResource** Cmdlet 會使用屬性清單作為參數。</span><span class="sxs-lookup"><span data-stu-id="b1541-123">The **New-xDscResource** cmdlet takes the list of properties as parameters.</span></span> <span data-ttu-id="b1541-124">它也會使用應建立模組位置的路徑、新資源的名稱和包含它的模組名稱。</span><span class="sxs-lookup"><span data-stu-id="b1541-124">It also takes the path where the module should be created, the name of the new resource, and the name of the module in which it is contained.</span></span> <span data-ttu-id="b1541-125">下列 PowerShell 命令會建立資源。</span><span class="sxs-lookup"><span data-stu-id="b1541-125">The following PowerShell command creates the resource.</span></span>

```powershell
New-xDscResource –Name Demo_ADUser –Property $UserName, $Ensure, $DomainCredential, $Password –Path 'C:\Program Files\WindowsPowerShell\Modules' –ModuleName Demo_DSCModule
```

<span data-ttu-id="b1541-126">**New-xDscResource** Cmdlet 會建立 MOF 結構描述、基本架構資源指令碼、新資源的必要目錄結構和公開新資源的模組資訊清單。</span><span class="sxs-lookup"><span data-stu-id="b1541-126">The **New-xDscResource** cmdlet creates the MOF schema, a skeleton resource script, the required directory structure for your new resource, and a manifest for the module that exposes the new resource.</span></span>

<span data-ttu-id="b1541-127">MOF 結構描述檔案位於 **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof**，其內容如下。</span><span class="sxs-lookup"><span data-stu-id="b1541-127">The MOF schema file is at **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof**, and its contents are as follows.</span></span>

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

<span data-ttu-id="b1541-128">資源指令碼位於 **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**。</span><span class="sxs-lookup"><span data-stu-id="b1541-128">The resource script is at **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**.</span></span>
<span data-ttu-id="b1541-129">它不包含實作資源的實際邏輯，您必須自己加入。</span><span class="sxs-lookup"><span data-stu-id="b1541-129">It does not include the actual logic to implement the resource, which you must add yourself.</span></span> <span data-ttu-id="b1541-130">基本架構指令碼的內容如下。</span><span class="sxs-lookup"><span data-stu-id="b1541-130">The contents of the skeleton script are as follows.</span></span>

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

## <a name="updating-the-resource"></a><span data-ttu-id="b1541-131">更新資源</span><span class="sxs-lookup"><span data-stu-id="b1541-131">Updating the resource</span></span>

<span data-ttu-id="b1541-132">如果您需要新增或修改資源的參數清單，您可以呼叫 **Update-xDscResource** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b1541-132">If you need to add or modify the parameter list of the resource, you can call the **Update-xDscResource** cmdlet.</span></span> <span data-ttu-id="b1541-133">此 Cmdlet 會用新的參數清單更新資源。</span><span class="sxs-lookup"><span data-stu-id="b1541-133">The cmdlet updates the resource with a new parameter list.</span></span> <span data-ttu-id="b1541-134">如果資源指令碼中已加入邏輯，它會保持不變。</span><span class="sxs-lookup"><span data-stu-id="b1541-134">If you have already added logic in your resource script, it is left intact.</span></span>

<span data-ttu-id="b1541-135">例如，假設您想要在資源中包含使用者最後一次的登入時間。</span><span class="sxs-lookup"><span data-stu-id="b1541-135">For example, suppose you want to include the last log in time for the user in our resource.</span></span> <span data-ttu-id="b1541-136">不用再重新撰寫一次資源，您可以呼叫 **New-xDscResourceProperty** 建立新的屬性，然後呼叫 **Update-xDscResource** 將新屬性加入屬性清單中。</span><span class="sxs-lookup"><span data-stu-id="b1541-136">Rather than writing the resource again completely, you can call the **New-xDscResourceProperty** to create the new property, and then call **Update-xDscResource** and add your new property to the properties list.</span></span>

```powershell
$lastLogon = New-xDscResourceProperty –Name LastLogon –Type Hashtable –Attribute Write –Description "For mapping users to their last log on time"
Update-xDscResource –Name 'Demo_ADUser' –Property $UserName, $Ensure, $DomainCredential, $Password, $lastLogon -Force
```

## <a name="testing-a-resource-schema"></a><span data-ttu-id="b1541-137">測試資源的結構描述</span><span class="sxs-lookup"><span data-stu-id="b1541-137">Testing a resource schema</span></span>

<span data-ttu-id="b1541-138">[資源設計工具] 工具會多公開一個 Cmdlet，其可用來測試您手動撰寫的 MOF 結構描述的有效性。</span><span class="sxs-lookup"><span data-stu-id="b1541-138">The Resource Designer tool exposes one more cmdlet that can be used to test the validity of a MOF schema that you have written manually.</span></span> <span data-ttu-id="b1541-139">呼叫 **Test-xDscSchema** Cmdlet，將 MOF 資源結構描述的路徑當參數傳遞。</span><span class="sxs-lookup"><span data-stu-id="b1541-139">Call the **Test-xDscSchema** cmdlet, passing the path of a MOF resource schema as a parameter.</span></span> <span data-ttu-id="b1541-140">此 Cmdlet 會輸出結構描述中的所有錯誤。</span><span class="sxs-lookup"><span data-stu-id="b1541-140">The cmdlet will output any errors in the schema.</span></span>

### <a name="see-also"></a><span data-ttu-id="b1541-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1541-141">See Also</span></span>

#### <a name="concepts"></a><span data-ttu-id="b1541-142">概念</span><span class="sxs-lookup"><span data-stu-id="b1541-142">Concepts</span></span>
[<span data-ttu-id="b1541-143">建置自訂的 Windows PowerShell 預期狀態設定資源</span><span class="sxs-lookup"><span data-stu-id="b1541-143">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](authoringResource.md)

#### <a name="other-resources"></a><span data-ttu-id="b1541-144">其他資源</span><span class="sxs-lookup"><span data-stu-id="b1541-144">Other Resources</span></span>
[<span data-ttu-id="b1541-145">xDscResourceDesigner 模組</span><span class="sxs-lookup"><span data-stu-id="b1541-145">xDscResourceDesigner Module</span></span>](https://www.powershellgallery.com/packages/xDscResourceDesigner/1.12.0.0)
