---
ms.date: 12/12/2018
keywords: dsc,powershell,設定,安裝
title: 使用 Import-DSCResource
ms.openlocfilehash: 4bc269ab1dd4696298b4f33f7661473aae869eba
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417418"
---
# <a name="using-import-dscresource"></a>使用 Import-DSCResource

`Import-DScResource` 是動態關鍵字，只能在設定指令碼區塊中使用。 `Import-DSCResource` 關鍵字用於匯入設定中所需的任何資源。 `$pshome` 下的資源會自動匯入，但明確地匯入[設定](Configurations.md)中使用的所有資源仍被視為最佳做法。

`Import-DSCResource` 語法如下所示。  依名稱指定模組時，需要在新行上列出每個模組。

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>] [-ModuleVersion <ModuleVersion>]
```

|參數  |描述  |
|---------|---------|
|`-Name`|您必須匯入 DSC 資源名稱。 如果指定了模組名稱，則該命令將在此模組中搜尋這些 DSC 資源；否則該命令會在所有 DSC 資源路徑中搜尋 DSC 資源。 支援萬用字元。|
|`-ModuleName`|模組名稱，或模組規格。  如果您指定了要從模組匯入的資源，該命令將嘗試僅匯入這些資源。 如果僅指定模組，則該命令將匯入模組中的所有 DSC 資源。|
|`-ModuleVersion`|從 PowerShell 5.0 開始，您可以指定設定應使用的模組版本。 如需詳細資訊，請參閱[匯入所安裝資源的特定版本](sxsresource.md)。|

```powershell
Import-DscResource -ModuleName xActiveDirectory
```

## <a name="example-use-import-dscresource-within-a-configuration"></a>範例：在設定中使用 Import-DSCResource

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
> 不支援在相同命令中為資源名稱和模組名稱指定多個值。 在多個模組中存在相同資源的情況下，它可能具有關於從哪一個模組載入哪一個資源的非確定性行為。 以下命令將導致編譯期間發生錯誤。
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

僅使用 Name 參數時要考慮的事項：

- 這是需要大量資源的作業，具體取決於電腦上安裝的模組數目。
- 它會載入使用指定名稱找到的第一個資源。 如果安裝了多個具有相同名稱的資源，則可能會載入錯誤的資源。

建議的用法是使用 `-Name` 參數指定 `–ModuleName`，如下所述。

此用法提供了下列優點：

- 它透過限制指定資源的搜尋範圍來降低效能影響。
- 它明確定義了定義資源的模組，確保載入正確的資源。

> [!NOTE]
> 在 PowerShell 5.0，DSC 資源可以有多個版本，且各版本可於一部電腦上並存安裝。 而其運作方式則是在相同的模組資料夾中，包含多個版本的資源模組。
> 如需詳細資訊，請參閱[使用多個版本的資源](sxsresource.md)。

## <a name="intellisense-with-import-dscresource"></a>使用 Import-DSCResource 的 Intellisense

在 ISE 中撰寫 DSC 設定時，PowerShell 會為資源和資源內容提供 IntelliSense。 `$pshome` 模組路徑下的資源定義會自動載入。 使用 `Import-DSCResource` 關鍵字匯入資源時，將加入指定的資源定義，並擴展 Intellisense 以包含匯入的資源結構描述。

![資源 Intellisense](../media/resource-intellisense.png)

> [!NOTE]
> 從 PowerShell 5.0 開始，Tab 鍵自動完成已新增至 ISE 以取得 DSC 資源和其屬性。 如需詳細資訊，請參閱[資源](../resources/resources.md)。

在編譯設定時，PowerShell 會使用匯入的資源定義來驗證設定中的所有資源區塊。
使用資源的結構描述定義驗證每個資源區塊，以用於下列規則。

- 僅使用結構描述中定義的屬性。
- 每個屬性的資料類型都是正確的。
- 指定索引鍵屬性。
- 不使用任何唯讀屬性。
- 驗證值對應類型。

請考慮下列設定：

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

編譯此設定會導致錯誤。

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values 'Invalid' is not supported or valid for property 'Ensure' on class 'WindowsFeature'. Please specify only supported values: Present, Absent.
```

Intellisense 和結構描述驗證允許您在剖析和編譯時間擷取更多的錯誤，從而避免在執行階段出現複雜情況。

> [!NOTE]
> 每個 DSC 資源都可以有一個名稱，以及由結構描述所定義的 **FriendlyName**。 以下是 "MSFT_ServiceResource.shema.mof" 的前兩行。
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> 在設定中使用此資源時，您可以指定 **MSFT_ServiceResource** 或 **Service**。

## <a name="powershell-v4-and-v5-differences"></a>PowerShell v4 和 v5 的差異

在 PowerShell 4.0 與PowerShell 5.0 及更新版本中撰寫設定時，您會看到多種差異。 本節將重點介紹您認為與本文相關的差異。

### <a name="multiple-resource-versions"></a>多個資源版本

PowerShell 4.0 不支援並排安裝和使用多個版本的資源。 如果您發現將資源匯入設定時出現問題，請確定您只安裝了一個版本的資源。

在下圖中，安裝了 **xPSDesiredStateConfiguration** 模組的兩個版本。

![已修正多個資源版本](../media/multiple-resource-versions-broken.png)

將所需模組版本的內容複製到模組目錄的上層。

![已修正多個資源版本](../media/multiple-resource-versions-fixed.png)

### <a name="resource-location"></a>資源位置

在撰寫和編譯設定時，您的資源可以儲存在 [PSModulePath](/powershell/scripting/developer/module/modifying-the-psmodulepath-installation-path) 指定的任何目錄中。 在 PowerShell 4.0 中，LCM 要求所有 DSC 資源模組都儲存在 "Program Files\WindowsPowerShell\Modules" 或 `$pshome\Modules` 下。 從 PowerShell 5.0 開始，已移除此需求，資源模組可以儲存在 `PSModulePath` 指定的任何目錄中。

### <a name="moduleversion-added"></a>已新增 ModuleVersion

從 PowerShell 5.0 開始，`-ModuleVersion` 參數可讓您指定要在設定中使用的模組版本。

## <a name="see-also"></a>另請參閱

- [資源](../resources/resources.md)
