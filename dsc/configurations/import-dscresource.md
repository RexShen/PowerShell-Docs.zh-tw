---
ms.date: 12/12/2018
keywords: dsc,powershell,設定,安裝
title: 使用 Import-DSCResource
ms.openlocfilehash: ee0b2f0469c6507c8f0148138198597a9e57cdd7
ms.sourcegitcommit: c581c4c8036edf55147e7bce4b00c860da6c5a8b
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/25/2019
ms.locfileid: "56803407"
---
# <a name="using-import-dscresource"></a>使用 Import-DSCResource

`Import-DScResource` 是動態的關鍵字，只可用於設定指令碼區塊。 `Import-DSCResource`關鍵字來匯入您的組態中所需的任何資源。 下的資源`$pshome`會自動匯入，但它仍然會被視為明確地匯入中所使用的所有資源的最佳做法是您[組態](Configurations.md)。

語法`Import-DSCResource`如下所示。  依名稱指定模組，就必須列出每個新的一行上。

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>]
```

|參數  |描述  |
|---------|---------|
|`-Name`|您必須匯入 DSC 資源名稱。 如果指定的模組名稱，則命令會搜尋在這個模組中; 這些 DSC 資源否則命令會在所有 DSC 資源路徑中搜尋的 DSC 資源。 支援萬用字元。|
|`-ModuleName`|模組名稱或模組規格中。  如果您指定要從模組匯入的資源時，命令將嘗試匯入只需將那些資源。 如果您指定了模組只，命令會匯入模組中的所有 DSC 資源。|

```powershell
Import-DscResource -ModuleName xActiveDirectory;
```

## <a name="example-use-import-dscresource-within-a-configuration"></a>範例： 使用 Import-dscresource 設定中

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
    Import-DSCResource -ModuleName ComputerManagementDsc
...
```

> [!NOTE]
> 不支援在相同命令中指定資源名稱和模組名稱的多個值。 它可以有不具決定性的行為，如果相同的資源存在於多個模組，從哪一個模組載入哪一個資源的相關。 下列命令會產生錯誤期間編譯。
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

使用 Name 參數時要考慮的事項：

- 這是需要大量資源的作業，視安裝在電腦上的模組數目而定。
- 它會載入第一個找到具有指定名稱的資源。 在案例中只要有一個以上的資源，與安裝的相同名稱，它無法載入錯誤的資源。

建議的用法是指定`–ModuleName`與`-Name`參數，如下所述。

這種使用方式的優點如下：

- 它可減少限制搜尋範圍對於指定的資源的效能影響。
- 它會明確定義定義資源，確保正確的資源載入的模組。

> [!NOTE]
> 在 PowerShell 5.0，DSC 資源可以有多個版本，且各版本可於一部電腦上並存安裝。 而其運作方式則是在相同的模組資料夾中，包含多個版本的資源模組。
> 如需詳細資訊，請參閱[使用多個版本的資源](sxsresource.md)。

## <a name="intellisense-with-import-dscresource"></a>使用 Import-dscresource 的 Intellisense

當撰寫 ISE 中的 DSC 組態，PowerShell 會提供 IntelliSence 資源和資源內容。 在資源定義`$pshome`會自動載入模組路徑。 當您匯入使用的資源`Import-DSCResource`關鍵字加入指定的資源定義和 Intellisense 已擴展成包含匯入的資源結構描述。

![資源的 Intellisense](/media/resource-intellisense.png)

> [!NOTE]
> 從 PowerShell 5.0 開始，tab 鍵自動完成已新增至 ISE 的 DSC 資源和其屬性。 如需詳細資訊，請參閱 <<c0> [ 資源](../resources/resources.md)。

在編譯設定時，PowerShell 會使用匯入的資源定義來驗證在組態中的所有資源區塊。
每個資源區塊會進行驗證，使用資源的結構描述定義，如下列的規則。

- 會使用結構描述中定義的屬性。
- 每個屬性的資料類型正確。
- 指定索引鍵屬性。
- 不使用任何唯讀屬性。
- 值的驗證將型別對應。

請考慮下列組態：

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

編譯此組態會導致錯誤。

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values ‘Invalid’ is not supported or valid for property ‘Ensure’ on class ‘WindowsFeature’. Please specify only supported values: Present, Absent.
```

Intellisense 和結構描述驗證可讓您避免複雜，在執行階段剖析和編譯時間，在擷取更多的錯誤。

> [!NOTE]
> 每個 DSC 資源可以有一個名稱，以及**FriendlyName**資源的結構描述所定義。 以下是 「 MSFT_ServiceResource.shema.mof"前兩行。
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> 當使用這項資源設定中，您可以指定**MSFT_ServiceResource**或是**服務**。

## <a name="powershell-v4-and-v5-differences"></a>PowerShell v4 和 v5 的差異

有多個 PowerShell 4.0 vs 中撰寫組態時，您會看到的差異。PowerShell 5.0 及更新版本。 本章節會反白顯示的差異，您會看到與本文相關。

### <a name="multiple-resource-versions"></a>多個資源版本

安裝和使用多個版本的資源並排顯示在 PowerShell 4.0 中不支援。 如果您注意到資源匯入您的組態問題，請確定您只有一個版本安裝的資源。

在下圖中，兩個版本**xPSDesiredStateConfiguration**安裝模組。

![已修正的多個資源版本](/media/multiple-resource-versions-broken.md)

您所需的模組版本的內容複製到模組目錄的上層。

![已修正的多個資源版本](/media/multiple-resource-versions-fixed.md)

### <a name="resource-location"></a>資源位置

撰寫和編譯組態，您的資源可以儲存任何指定的目錄中您[PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path)。 在 PowerShell 4.0 中，LCM 會需要儲存在"Program Files\WindowsPowerShell\Modules"下的所有 DSC 資源模組或`$pshome\Modules`。 從 PowerShell 5.0 開始，已移除這項需求，而且資源模組可以儲存任何指定的目錄中`PSModulePath`。

## <a name="see-also"></a>另請參閱

- [資源](../resources/resources.md)
