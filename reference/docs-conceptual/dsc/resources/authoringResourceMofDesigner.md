---
ms.date: 07/08/2020
keywords: dsc,powershell,設定,安裝
title: 使用 [資源設計工具] 工具
ms.openlocfilehash: 04fd2fbcc5afd9f1c7cbfaa44d6bdfde93bca399
ms.sourcegitcommit: d26e2237397483c6333abcf4331bd82f2e72b4e3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2020
ms.locfileid: "86217486"
---
# <a name="using-the-resource-designer-tool"></a>使用 [資源設計工具] 工具

> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

資源設計工具是一組 Cmdlet 工具，由 **xDscResourceDesigner** 模組所公開，讓建立 Windows PowerShell 預期狀態設定 (DSC) 資源變得更為容易。 這項資源中的 Cmdlet 會協助您建立新資源的 MOF 結構描述、指令碼模組和目錄結構。 如需 DSC 資源的詳細資訊，請參閱[建置自訂的 Windows PowerShell 預期狀態設定資源](authoringResource.md)。
在本主題中，我們會建立管理 Active Directory 使用者的 DSC 資源。 請使用 [Install-Module](/powershell/module/PowershellGet/Install-Module) Cmdlet 安裝 **xDscResourceDesigner** 模組。

## <a name="creating-resource-properties"></a>建立資源屬性

首先決定資源要公開的屬性。 本例中，我們會定義具有下列屬性的 Active Directory 使用者。

參數名稱描述

- **UserName**：唯一識別使用者的索引鍵屬性。
- **Ensure**：指定使用者帳戶應為 Present 或 Absent。 這個參數只會有兩個可能的值。
- **DomainCredential**：使用者的網域密碼。
- **Password**：使用者視需要允許設定變更使用者密碼所要使用的密碼。

我們使用 `New-xDscResourceProperty` Cmdlet 建立屬性。 下列 PowerShell 命令會建立上述的屬性。

```powershell
$UserName = New-xDscResourceProperty –Name UserName -Type String -Attribute Key
$Ensure = New-xDscResourceProperty –Name Ensure -Type String -Attribute Write –ValidateSet "Present", "Absent"
$DomainCredential = New-xDscResourceProperty –Name DomainCredential -Type PSCredential -Attribute Write
$Password = New-xDscResourceProperty –Name Password -Type PSCredential -Attribute Write
```

## <a name="create-the-resource"></a>建立資源

資源屬性既已建立，即可呼叫 `New-xDscResource` Cmdlet 來建立資源。 `New-xDscResource` Cmdlet 會使用屬性清單作為參數。 它也會使用應建立模組位置的路徑、新資源的名稱和包含它的模組名稱。 下列 PowerShell 命令會建立資源。

```powershell
New-xDscResource –Name Demo_ADUser –Property $UserName, $Ensure, $DomainCredential, $Password –Path 'C:\Program Files\WindowsPowerShell\Modules' –ModuleName Demo_DSCModule
```

`New-xDscResource` Cmdlet 會建立 MOF 結構描述、基本架構資源指令碼、新資源的必要目錄結構和公開新資源的模組資訊清單。

MOF 結構描述檔案位在 `C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof`，其內容如下所示。

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

資源指令碼位在 `C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1`。
它不包含實作資源的實際邏輯，您必須自己加入。 基本架構指令碼的內容如下。

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

## <a name="updating-the-resource"></a>更新資源

如果必須新增或修改資源的參數清單，則可呼叫 `Update-xDscResource` Cmdlet。 此 Cmdlet 會用新的參數清單更新資源。 如果資源指令碼中已加入邏輯，它會保持不變。

例如，假設您想要在資源中包含使用者最後一次的登入時間。 您可呼叫 `New-xDscResourceProperty` 來建立新的屬性，然後呼叫 `Update-xDscResource` 將新屬性新增至屬性清單中，不用再重新撰寫一次資源。

```powershell
$lastLogon = New-xDscResourceProperty –Name LastLogon –Type Hashtable –Attribute Write –Description "For mapping users to their last log on time"
Update-xDscResource –Name 'Demo_ADUser' –Property $UserName, $Ensure, $DomainCredential, $Password, $lastLogon -Force
```

## <a name="testing-a-resource-schema"></a>測試資源的結構描述

[資源設計工具] 工具會多公開一個 Cmdlet，其可用來測試您手動撰寫的 MOF 結構描述的有效性。 呼叫 `Test-xDscSchema` Cmdlet，將 MOF 資源結構描述的路徑傳遞為參數。 此 Cmdlet 會輸出結構描述中的所有錯誤。

### <a name="see-also"></a>另請參閱

#### <a name="concepts"></a>概念

[建置自訂的 Windows PowerShell 預期狀態設定資源](authoringResource.md)

#### <a name="other-resources"></a>其他資源

[xDscResourceDesigner 模組](https://www.powershellgallery.com/packages/xDscResourceDesigner/1.12.0.0)
