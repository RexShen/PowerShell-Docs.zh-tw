---
ms.date: 07/08/2020
keywords: dsc,powershell,設定,安裝
title: 撰寫自訂的 DSC 資源與 MOF
description: 此文章在 MOF 檔案中定義 DSC 自訂資源的結構描述，並將該資源實作到 PowerShell 指令檔中。
ms.openlocfilehash: e79a37699c468b2c55c307c96f1c193a2c1595b3
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667176"
---
# <a name="writing-a-custom-dsc-resource-with-mof"></a>撰寫自訂的 DSC 資源與 MOF

> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

在此文章中，我們會在 MOF 檔案中定義 Windows PowerShell Desired State Configuration (DSC) 自訂資源的結構描述，並在 Windows PowerShell 指令檔中實作該資源。
這個自訂的資源是用於建立和維護網站。

## <a name="creating-the-mof-schema"></a>建立 MOF 結構描述

結構描述會定義可由 DSC 設定指令碼設定之資源的屬性。

### <a name="folder-structure-for-a-mof-resource"></a>MOF 資源的資料夾結構

若要使用 MOF 結構描述實作 DSC 自訂資源，請建立下列資料夾結構。 MOF 結構描述是定義在 `Demo_IISWebsite.schema.mof` 檔案中，資源指令碼則是定義在 `Demo_IISWebsite.psm1` 中。 您也可以建立模組資訊清單 (psd1) 檔案。

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResources (folder)
        |- DSCResources (folder)
            |- Demo_IISWebsite (folder)
                |- Demo_IISWebsite.psd1 (file, optional)
                |- Demo_IISWebsite.psm1 (file, required)
                |- Demo_IISWebsite.schema.mof (file, required)
```

> [!NOTE]
> 您必須在最上層資料夾下建立名為 DSCResources 的資料夾，且每個資源的資料夾都必須和資源同名。

### <a name="the-contents-of-the-mof-file"></a>MOF 檔案的內容

下面的範例 MOF 檔案可用於自訂的網站資源。 若要依此範例操作，請將這個結構描述儲存至檔案，並呼叫檔案 `Demo_IISWebsite.schema.mof`。

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

前列程式碼請注意下列事項：

- `FriendlyName` 定義的名稱，可用來參考 DSC 設定指令碼的這個自訂資源。 在本例中，`Website` 相當於內建 Archive 資源的易記名稱 `Archive`。
- 您為自訂資源定義的類別必須衍生自 `OMI_BaseResource`。
- 屬性上的類型限定詞 `[Key]`，表示這個屬性會唯一識別資源執行個體。 至少有一個 `[Key]` 屬性是必要屬性。
- `[Required]` 限定詞表示必要屬性 (使用這項資源的任何設定指令碼都必須指定的值)。
- `[write]` 限定詞表示，在設定指令碼中使用自訂資源時，這是選擇性屬性。 `[read]` 限定詞表示設定不能設定屬性，且限用於報告。
- `Values` 限制可指派給在 `ValueMap` 定義的值清單之屬性的值。 如需詳細資訊，請參閱 [ValueMap and Value Qualifiers (ValueMap 和值限定詞)](/windows/desktop/WmiSdk/value-map)。
- 建議您在資源中包含名為 `Ensure`且值為 `Present` 和 `Absent` 的屬性，以便和內建的 DSC 資源維持一致的樣式。
- 依下列方式命名自訂資源的結構描述檔案：`classname.schema.mof`，其中 `classname` 是遵循結構描述定義 `class` 關鍵字的識別碼。

### <a name="writing-the-resource-script"></a>撰寫資源指令碼

資源指令碼會實作資源的邏輯。 這個模組中必須包含三個函式，它們是：`Get-TargetResource`、`Set-TargetResource` 和 `Test-TargetResource`。 這三個函式都必須使用與您為資源建立的 MOF 結構描述所定義之屬性集相同的參數集。 在本文件中，這個屬性集稱為「資源屬性」。 將這三個函式存放在名為 `<ResourceName>.psm1` 的檔案中。 在下列範例中，這些函式儲存在 `Demo_IISWebsite.psm1` 檔案中。

> [!NOTE]
> 當您在資源上多次執行相同的設定指令碼時，您應該不會收到任何錯誤，而且資源的狀態也應該和只執行一次指令碼的狀態相同。 若要達成這個目標，請確認 `Get-TargetResource` 和 `Test-TargetResource` 函式不變更資源，而且以相同參數順序值多次叫用 `Set-TargetResource` 函式永遠等於只叫用一次。

在 `Get-TargetResource` 函式的實作中，使用提供為參數的重要資源屬性值，檢查指定的資源執行個體狀態。 這個函式必須傳回雜湊表，將所有的資源屬性列為索引鍵，這些屬性的實際值列為對應值。 範例請見下列程式碼。

```powershell
# DSC uses the Get-TargetResource function to fetch the status of the resource instance
# specified in the parameters for the target machine
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

        <#
          Insert logic that uses the mandatory parameter values to get the website and
          assign it to a variable called $Website
          Set $ensureResult to "Present" if the requested website exists and to "Absent" otherwise
        #>

        # Add all Website properties to the hash table
        # This simple example assumes that $Website is not null
        $getTargetResourceResult = @{
            Name = $Website.Name
            Ensure = $ensureResult
            PhysicalPath = $Website.physicalPath
            State = $Website.state
            ID = $Website.id
            ApplicationPool = $Website.applicationPool
            Protocol = $Website.bindings.Collection.protocol
            Binding = $Website.bindings.Collection.bindingInformation
        }

        $getTargetResourceResult
}
```

依據設定指令碼中為資源屬性指定的值，`Set-TargetResource` 必須執行下列其中一項：

- 建立新的網站
- 更新現有的網站
- 刪除現有的網站

下列範例將說明這點。

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

    <#
        If Ensure is set to "Present" and the website specified in the mandatory input parameters
          does not exist, then create it using the specified parameter values
        Else, if Ensure is set to "Present" and the website does exist, then update its properties
          to match the values provided in the non-mandatory parameter values
        Else, if Ensure is set to "Absent" and the website does not exist, then do nothing
        Else, if Ensure is set to "Absent" and the website does exist, then delete the website
    #>
}
```

最後，`Test-TargetResource` 函式必須和 `Get-TargetResource` 及 `Set-TargetResource` 使用相同的參數集。 在 `Test-TargetResource` 的實作中，檢查於索引鍵參數中指定的資源執行個體狀態。 如果資源執行個體的實際狀態不符合參數集指定的值，則傳回 `$false`。 否則，傳回 `$true`。

下列程式碼會實作 `Test-TargetResource` 函式。

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

    # Get the current state
    $currentState = Get-TargetResource -Ensure $Ensure -Name $Name -PhysicalPath $PhysicalPath -State $State -ApplicationPool $ApplicationPool -BindingInfo $BindingInfo -Protocol $Protocol

    # Write-Verbose "Use this cmdlet to deliver information about command processing."

    # Write-Debug "Use this cmdlet to write debug information while troubleshooting."

    # Include logic to
    $result = [System.Boolean]
    # Add logic to test whether the website is present and its status matches the supplied
    # parameter values. If it does, return true. If it does not, return false.
    $result
}
```

> [!NOTE]
> 為方便偵錯，請在前述三個函式實作中使用 `Write-Verbose` Cmdlet。 這個 Cmdlet 會將文字寫入詳細資訊訊息串流中。 預設不顯示詳細資訊訊息串流，但您可以變更 **$VerbosePreference** 變數的值或在 DSC cmdlets = new 中使用 **Verbose** 參數來顯示它。

### <a name="creating-the-module-manifest"></a>建立模組資訊清單

最後，使用 `New-ModuleManifest` Cmdlet，定義自訂資源模組的 `<ResourceName>.psd1` 檔案。 當您叫用這個 Cmdlet 時，請參考上節所述的指令碼模組 (.psm1) 檔案。 在要匯出的函式清單中包含 `Get-TargetResource`、`Set-TargetResource` 和 `Test-TargetResource`。 以下為資訊清單檔案範例。

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

## <a name="supporting-psdscrunascredential"></a>支援 PsDscRunAsCredential

> [!Note]
> PowerShell 5.0 或更新版本中支援 **PsDscRunAsCredential** 。

您可以在 [DSC 設定](../configurations/configurations.md)資源區塊中使用 **PsDscRunAsCredential** 特性，以指定該資源應該在一組指定的認證下執行。 如需詳細資訊，請參閱[以使用者認證執行 DSC](../configurations/runAsUser.md)。

若要從自訂資源內存取使用者內容，您可以使用自動變數 `$PsDscContext`。

例如，下列程式碼會將資源執行位置的上層使用者內容寫入到詳細的輸出資料流：

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="rebooting-the-node"></a>重新啟動節點

若在您 `Set-TargetResource` 函式中採取的動作需要重新啟動，您可以使用全域旗標來告知 LCM 重新啟動節點。 此重新啟動會在 `Set-TargetResource` 函式完成後直接發生。

在您 `Set-TargetResource` 函式的內部，請新增下列這行程式碼。

```powershell
# Include this line if the resource requires a system reboot.
$global:DSCMachineStatus = 1
```

為了讓 LCM 重新啟動節點， **RebootNodeIfNeeded** 旗標必須設為 `$true`。
**ActionAfterReboot** 設定也應設為 **ContinueConfiguration** (預設值)。 如需設定 LCM 的詳細資訊，請參閱[設定本機設定管理員](../managing-nodes/metaConfig.md)或[設定本機設定管理員 (v4)](../managing-nodes/metaConfig4.md)。
