---
ms.date: 10/16/2019
ms.topic: reference
title: 如何撰寫 PowerShell 模組資訊清單
description: 如何撰寫 PowerShell 模組資訊清單
ms.openlocfilehash: 42db71968ccac1cc3c1c05c5be2e72327e5e28d9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647705"
---
# <a name="how-to-write-a-powershell-module-manifest"></a>如何撰寫 PowerShell 模組資訊清單

撰寫 PowerShell 模組之後，您可以新增選擇性的模組資訊清單，其中包含模組的相關資訊。 例如，您可以描述作者、指定模組中的檔案 (例如) 的嵌套模組、執行腳本來自訂使用者的環境、載入類型和格式化檔案、定義系統需求，以及限制模組所匯出的成員。

## <a name="creating-a-module-manifest"></a>建立模組資訊清單

**模組資訊清單** 是 () 的 PowerShell 資料檔案 `.psd1` ，可描述模組的內容並判斷模組的處理方式。 資訊清單檔是一個文字檔，其中包含索引鍵和值的雜湊表。 您可以藉由將資訊清單命名為與模組相同的資訊清單檔，並將資訊清單儲存在模組的根目錄中，來將資訊清單檔連結至模組。

針對只包含單一 `.psm1` 或二元元件的簡單模組，模組資訊清單是選擇性的。 但是，建議您盡可能使用模組資訊清單，因為這些資訊清單有助於您組織程式碼及維護版本設定資訊。 此外，需要模組資訊清單才能匯出安裝在 [全域組件快取](/dotnet/framework/app-domains/gac)中的元件。 支援可更新之說明功能的模組也需要模組資訊清單。 「可更新的說明」會使用模組資訊清單中的 **HelpInfoUri** 索引鍵來尋找說明資訊 (HelpInfo XML) 檔案，其中包含模組的已更新說明檔的位置。 如需「可更新的說明」的詳細資訊，請參閱 [支援可更新](./supporting-updatable-help.md)的說明。

### <a name="to-create-and-use-a-module-manifest"></a>建立和使用模組資訊清單

1. 建立模組資訊清單的最佳作法是使用 [ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) Cmdlet。 您可以使用參數來指定一個或多個資訊清單的預設索引鍵和值。 唯一的需求是為檔案命名。 `New-ModuleManifest` 使用您指定的值建立模組資訊清單，並包含剩餘的索引鍵和其預設值。 如果您需要建立多個模組，請使用 `New-ModuleManifest` 建立可針對不同模組修改的模組資訊清單範本。 如需預設模組資訊清單的範例，請參閱 [範例模組資訊清單](#sample-module-manifest)。

   `New-ModuleManifest -Path C:\myModuleName.psd1 -ModuleVersion "2.0" -Author "YourNameHere"`

   替代方法是使用 **ModuleVersion** 所需的最基本資訊，手動建立模組資訊清單的雜湊表。 您可以使用與模組相同的名稱來儲存檔案，並使用 `.psd1` 副檔名。 然後，您可以編輯檔案並新增適當的索引鍵和值。

1. 在資訊清單檔中新增您想要的任何其他元素。

   若要編輯資訊清單檔，請使用您偏好的任何文字編輯器。 但是，資訊清單檔案是包含程式碼的腳本檔案，因此您可能想要在腳本或開發環境（例如 Visual Studio Code）中編輯它。 資訊清單檔的所有元素都是選擇性的，但 **ModuleVersion** 號碼除外。

   如需可包含在模組資訊清單中的索引鍵和值的描述，請參閱 [模組資訊清單元素](#module-manifest-elements) 表格。 如需詳細資訊，請參閱 [ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) Cmdlet 中的參數描述。

1. 若要解決基底模組資訊清單專案可能未涵蓋的任何情況，您可以選擇將額外的程式碼新增至模組資訊清單。

   基於安全性考慮，PowerShell 只會在模組資訊清單檔案中執行一小部分的可用作業。 一般而言，您可以使用 `if` 語句、算術和比較運算子，以及基本的 PowerShell 資料類型。

1. 建立模組資訊清單之後，您可以進行測試，以確認資訊清單中所描述的任何路徑是否正確。 若要測試您的模組資訊清單，請使用 [測試 ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest)。

   `Test-ModuleManifest myModuleName.psd1`

1. 請確定您的模組資訊清單位於包含模組的目錄最上層。

   當您將模組複製到系統並匯入它時，PowerShell 會使用模組資訊清單來匯入您的模組。

1. （選擇性）您可以直接在資訊清單本身的情況下，透過點 [來源對模組](/powershell/module/Microsoft.PowerShell.Core/Import-Module) 資訊清單進行測試。

   `Import-Module .\myModuleName.psd1`

## <a name="module-manifest-elements"></a>模組資訊清單元素

下表說明您可以在模組資訊清單中包含的元素。

|元素|預設|描述|
|-------------|-------------|-----------------|
|**RootModule**<br /> 輸入： `String`|`<empty string>`|與此資訊清單相關聯的腳本模組或二進位模組檔案。 先前的 PowerShell 版本稱為此元素 **ModuleToProcess**。<br /> 根模組的可能類型可以是空的，它會建立 **資訊清單** 模組、腳本模組的名稱 (`.psm1`) ，或二進位模組的名稱 (`.exe` 或 `.dll`) 。 將模組資訊清單的名稱 (`.psd1`) 或 `.ps1` 此元素中 () 的指令檔會導致錯誤。 <br /> 範例： `RootModule = 'ScriptModule.psm1'`|
|**ModuleVersion**<br /> 輸入： `Version`|`'0.0.1'`|此課程模組的版本號碼。 如果未指定值， `New-ModuleManifest`   則會使用預設值。 例如，字串必須能夠轉換成型別 `Version` `#.#.#.#.#` 。 `Import-Module` 載入它在 **$PSModulePath** 上找到的第一個模組，該模組會與該名稱相符，而且至少要有 **ModuleVersion** 做為 **MinimumVersion** 參數。 若要匯入特定版本，請使用 `Import-Module` Cmdlet 的 **RequiredVersion** 參數。<br /> 範例： `ModuleVersion = '1.0'`|
|**GUID**<br /> 輸入： `GUID`|`'<GUID>'`|用來唯一識別此模組的識別碼。 如果未指定值，請 `New-ModuleManifest` 會自動產生值。 您目前無法依 **GUID** 匯入模組。 <br /> 範例： `GUID = 'cfc45206-1e49-459d-a8ad-5b571ef94857'`|
|**Author** (作者)<br /> 輸入： `String`|`'<Current user>'`|此課程模組的作者。 如果未指定值， `New-ModuleManifest` 則會使用目前的使用者。 <br /> 範例： `Author = 'AuthorNameHere'`|
|**CompanyName**<br /> 輸入： `String`|`'Unknown'`|此課程模組的公司或廠商。 如果未指定值， `New-ModuleManifest` 則會使用預設值。<br /> 範例： `CompanyName = 'Fabrikam'`|
|**Copyright** (著作權)<br /> 輸入： `String`|`'(c) <Author>. All rights reserved.'`| 此課程模組的著作權陳述。 如果未指定值，則會 `New-ModuleManifest` 使用目前使用者的預設值做為 `<Author>` 。 若要指定作者，請使用 **author** 參數。 <br /> 範例： `Copyright = '2019 AuthorName. All rights reserved.'`|
|**說明**<br /> 輸入： `String`|`<empty string>`|此課程模組提供的功能描述。<br /> 範例： `Description = 'This is the module's description.'`|
|**PowerShellVersion**<br /> 輸入： `Version`|`<empty string>`|此課程模組所需的最小 PowerShell 引擎版本。 有效的值為1.0、2.0、3.0、4.0、5.0、5.1、6和7。<br /> 範例： `PowerShellVersion = '5.0'`|
|**PowerShellHostName**<br /> 輸入： `String`|`<empty string>`|此課程模組所需的 PowerShell 主機名稱。 此名稱是由 PowerShell 所提供。 若要尋找主機程式的名稱，請在程式中輸入： `$host.name` 。<br /> 範例： `PowerShellHostName = 'ConsoleHost'`|
|**PowerShellHostVersion**<br /> 輸入： `Version`|`<empty string>`|此課程模組所需之 PowerShell 主機的最小版本。<br /> 範例： `PowerShellHostVersion = '2.0'`|
|**DotNetFrameworkVersion**<br /> 輸入： `Version`|`<empty string>`|此課程模組所需的 Microsoft .NET Framework 最小版本。 這項必要條件僅適用于 PowerShell Desktop edition，例如 PowerShell 5.1。<br /> 範例： `DotNetFrameworkVersion = '3.5'`|
|**CLRVersion**<br /> 輸入： `Version`|`<empty string>`|此課程模組所需的 common language runtime (CLR) 的最小版本。 這項必要條件僅適用于 PowerShell Desktop edition，例如 PowerShell 5.1。<br /> 範例： `CLRVersion = '3.5'`|
|**ProcessorArchitecture**<br /> 輸入： `ProcessorArchitecture`|`<empty string>`|此課程模組所需的處理器架構 (None、X86、Amd64) 。 有效的值為 x86、AMD64、Arm、IA64、MSIL 和 None (未知或未指定的) 。<br /> 範例： `ProcessorArchitecture = 'x86'`|
|**RequiredModules**<br /> 輸入： `Object[]`|`@()`|匯入此模組之前，必須先匯入至全域環境的模組。 這會載入任何列出的模組，除非它們已經載入。 例如，有些模組可能已經由其他模組載入。 您可以使用而不是指定要載入的特定版本 `RequiredVersion` `ModuleVersion` 。 當 `ModuleVersion` 使用時，它會載入最新版本，並在指定的版本中提供最小值。 您可以在參數值中結合字串和雜湊表。<br /> 範例： `RequiredModules = @("MyModule", @{ModuleName="MyDependentModule"; ModuleVersion="2.0"; GUID="cfc45206-1e49-459d-a8ad-5b571ef94857"})`<br /> 範例： `RequiredModules = @("MyModule", @{ModuleName="MyDependentModule"; RequiredVersion="1.5"; GUID="cfc45206-1e49-459d-a8ad-5b571ef94857"})`|
|**RequiredAssemblies**<br /> 輸入： `String[]`|`@()`|匯入此模組之前必須先載入的元件。 指定 `.dll` 模組所需 () 檔案名的元件。<br /> PowerShell 會在更新類型或格式、匯入嵌套模組，或匯入在 RootModule 索引鍵值中指定的模組檔案之前，先載入指定的元件。 使用這個參數來列出模組所需的所有元件。<br /> 範例： `RequiredAssemblies = @("assembly1.dll", "assembly2.dll", "assembly3.dll")`|
|**ScriptsToProcess**<br /> 輸入： `String[]`|`@()`|腳本 (`.ps1`) 在匯入模組時，在呼叫者會話狀態中執行的檔案。 這可以是全域會話狀態，也可以是其他模組的會話狀態（針對嵌套模組）。 您可以使用這些腳本來準備環境，就像您可能會在腳本中使用記錄一樣。<br /> 這些腳本會在載入資訊清單中列出的任何模組之前執行。 <br /> 範例： `ScriptsToProcess = @("script1.ps1", "script2.ps1", "script3.ps1")`|
|**TypesToProcess**<br /> 輸入： `String[]`|`@()`|匯 `.ps1xml` 入此模組時，請輸入要載入)  (的檔案。 <br /> 範例： `TypesToProcess = @("type1.ps1xml", "type2.ps1xml", "type3.ps1xml")`|
|**FormatsToProcess**<br /> 輸入： `String[]`|`@()`|匯 `.ps1xml` 入此模組時， () 要載入的格式檔案。 <br /> 範例： `FormatsToProcess = @("format1.ps1xml", "format2.ps1xml", "format3.ps1xml")`|
|**NestedModules**<br /> 輸入： `Object[]`|`@()`|要匯入為 **RootModule** 中所指定模組之嵌套模組的模組 (Alias：**ModuleToProcess**) 。<br /> 將模組名稱加入此專案，類似于在 `Import-Module` 您的腳本或元件程式碼中呼叫。 使用資訊清單檔案的主要差異在於，您可以更輕鬆地查看您要載入的內容。 而且，如果模組無法載入，您還不會載入實際的模組。<br /> 除了其他模組以外，您也可以在這裡載入腳本 (`.ps1`) 檔案。 這些檔案會在根模組的內容中執行。 這相當於根模組中的腳本點。 <br /> 範例： `NestedModules = @("script.ps1", @{ModuleName="MyModule"; ModuleVersion="1.0.0.0"; GUID="50cdb55f-5ab7-489f-9e94-4ec21ff51e59"})`|
|**FunctionsToExport**<br /> 輸入： `String[]`|`@()`|指定要從這個模組匯出的函式，為了達到最佳效能，請不要使用萬用字元，也不要刪除專案，如果沒有要匯出的函式，則使用空陣列。 依預設，不會匯出任何函式。 您可以使用此索引鍵來列出模組所匯出的函式。<br /> 模組會將函式匯出到呼叫者的會話狀態。 呼叫者的會話狀態可以是全域會話狀態，也可以是其他模組的會話狀態。 連結嵌套模組時，會將嵌套模組匯出的所有函式匯出到全域會話狀態，除非鏈中的模組使用 **FunctionsToExport** 索引鍵來限制函數。<br /> 如果資訊清單匯出函式的別名，此索引鍵可以移除其別名列在 **AliasesToExport** 索引鍵中的函式，但此索引鍵無法將函式別名新增至清單。 <br /> 範例： `FunctionsToExport = @("function1", "function2", "function3")`|
|**CmdletsToExport**<br /> 輸入： `String[]`|`@()`|指定要從這個模組匯出的 Cmdlet，為了達到最佳效能，請不要使用萬用字元，也不要刪除專案，如果沒有要匯出的 Cmdlet，請使用空的陣列。 依預設，不會匯出任何 Cmdlet。 您可以使用此金鑰來列出模組所匯出的 Cmdlet。<br /> 呼叫者的會話狀態可以是全域會話狀態，也可以是其他模組的會話狀態。 當您要連結嵌套模組時，所有由嵌套模組匯出的 Cmdlet 都會匯出至全域會話狀態，除非鏈中的模組使用 **CmdletsToExport** 索引鍵來限制 Cmdlet。<br /> 如果資訊清單匯出 Cmdlet 的別名，此機碼可以移除別名列在 **AliasesToExport** 機碼中的 Cmdlet，但此金鑰無法將 Cmdlet 別名新增至清單。 <br /> 範例： `CmdletsToExport = @("Get-MyCmdlet", "Set-MyCmdlet", "Test-MyCmdlet")`|
|**VariablesToExport**<br /> 輸入： `String[]`|`'*'`|指定模組匯出到呼叫者會話狀態的變數。 允許使用萬用字元。 預設會匯出所有 () 的變數 `'*'` 。 您可以使用此金鑰來限制模組匯出的變數。<br /> 呼叫者的會話狀態可以是全域會話狀態，也可以是其他模組的會話狀態。 當您要連結嵌套模組時，除非鏈中的模組使用 **VariablesToExport** 索引鍵來限制變數，否則所有由嵌套模組匯出的變數都會匯出至全域會話狀態。<br /> 如果資訊清單也會匯出變數的別名，此索引鍵可以移除別名在 **AliasesToExport** 索引鍵中列出的變數，但此索引鍵無法將變數別名新增至清單。 <br /> 範例： `VariablesToExport = @('$MyVariable1', '$MyVariable2', '$MyVariable3')`|
|**AliasesToExport**<br /> 輸入： `String[]`|`@()`|指定要從此模組匯出的別名，為了達到最佳效能，請不要使用萬用字元，也不要刪除專案，如果沒有要匯出的別名，請使用空的陣列。 依預設，不會匯出任何別名。 您可以使用此索引鍵來列出模組匯出的別名。<br /> 模組會將別名匯出到呼叫者的會話狀態。 呼叫者的會話狀態可以是全域會話狀態，也可以是其他模組的會話狀態。 當您要連結嵌套模組時，除非鏈中的模組使用 **AliasesToExport** 索引鍵來限制別名，否則所有由嵌套模組匯出的別名最後都會匯出至全域會話狀態。 <br /> 範例： `AliasesToExport = @("MyAlias1", "MyAlias2", "MyAlias3")`|
|**DscResourcesToExport**<br /> 輸入： `String[]`|`@()`|指定要從此模組匯出的 DSC 資源。 允許使用萬用字元。 <br /> 範例： `DscResourcesToExport = @("DscResource1", "DscResource2", "DscResource3")`|
|**ModuleList**<br /> 輸入： `Object[]`|`@()`|指定以此模組封裝的所有模組。 您可以使用以逗號分隔的字串，或使用 **ModuleName** 和 **GUID** 索引鍵的雜湊表，以名稱輸入這些模組。 雜湊表也可以有選擇性的 **ModuleVersion** 索引鍵。 **ModuleList** 索引鍵是設計來作為模組清查。 這些模組不會自動處理。 <br /> 範例： `ModuleList = @("SampleModule", "MyModule", @{ModuleName="MyModule"; ModuleVersion="1.0.0.0"; GUID="50cdb55f-5ab7-489f-9e94-4ec21ff51e59"})`|
|**FileList** (檔案清單)<br /> 輸入： `String[]`|`@()`|以此課程模組封裝的所有檔案清單。 如同 **ModuleList**， **FileList** 是清查清單，不會進行任何處理。 <br /> 範例： `FileList = @("File1", "File2", "File3")`|
|**PrivateData**<br /> 輸入： `Object`|`@{...}`|指定必須傳遞給 **RootModule** (Alias： **ModuleToProcess**) 金鑰所指定之根模組的任何私用資料。 **PrivateData** 是包含數個元素的雜湊表 **：標記**、 **LicenseUri**、 **ProjectURI**、 **IconUri**、 **ReleaseNotes**、 **發行** 前版本、 **RequireLicenseAcceptance** 和 **ExternalModuleDependencies**。 |
|**Tags** (標籤) <br /> 輸入： `String[]` |`@()`| 標記可協助線上元件庫中的模組探索。 <br /> 範例： `Tags = "PackageManagement", "PowerShell", "Manifest"`|
|**LicenseUri**<br /> 輸入： `Uri` |`<empty string>`| 此課程模組的授權 URL。 <br /> 範例： `LicenseUri = 'https://www.contoso.com/license'`|
|**ProjectUri**<br /> 輸入： `Uri` |`<empty string>`| 此專案的主要網站 URL。 <br /> 範例： `ProjectUri = 'https://www.contoso.com/project'`|
|**IconUri**<br /> 輸入： `Uri` |`<empty string>`| 代表此模組的圖示 URL。 <br /> 範例： `IconUri = 'https://www.contoso.com/icons/icon.png'`|
|**ReleaseNotes**<br /> 輸入： `String` |`<empty string>`| 指定模組的版本資訊。 <br /> 範例： `ReleaseNotes = 'The release notes provide information about the module.`|
|**發佈**<br /> 輸入： `String` |`<empty string>`| 此參數已在 PowerShellGet 1.6.6 中新增。 在線上元件庫中將模組識別為發行前版本的 **發行** 前版本字串。 <br /> 範例： `PreRelease = 'This module is a prerelease version.`|
|**RequireLicenseAcceptance**<br /> 輸入： `Boolean`|`$true`| 此參數已在 PowerShellGet 1.5 中新增。 旗標，指出模組是否需要明確的使用者接受以進行安裝、更新或儲存。 <br /> 範例： `RequireLicenseAcceptance = $false`|
|**ExternalModuleDependencies**<br /> 輸入： `String[]` |`@()`| 此參數已在 PowerShellGet v2 中新增。 此模組相依的外部模組清單。 <br /> 範例： `ExternalModuleDependencies =  @("ExtModule1", "ExtModule2", "ExtModule3")`|
|**HelpInfoURI**<br /> 輸入： `String`|`<empty string>`|此模組的 HelpInfo URI。 <br /> 範例： `HelpInfoURI = 'https://www.contoso.com/help'`|
|**DefaultCommandPrefix**<br /> 輸入： `String`|`<empty string>`|從此模組匯出的命令預設前置詞。 使用覆寫預設前置詞 `Import-Module -Prefix` 。 <br /> 範例： `DefaultCommandPrefix = 'My'`|

## <a name="sample-module-manifest"></a>範例模組資訊清單

下列範例模組資訊清單是 `New-ModuleManifest` 在 PowerShell 7 中建立的，並包含預設索引鍵和值。

```powershell
#
# Module manifest for module 'SampleModuleManifest'
#
# Generated by: User01
#
# Generated on: 10/15/2019
#

@{

# Script module or binary module file associated with this manifest.
# RootModule = ''

# Version number of this module.
ModuleVersion = '0.0.1'

# Supported PSEditions
# CompatiblePSEditions = @()

# ID used to uniquely identify this module
GUID = 'b632e90c-df3d-4340-9f6c-3b832646bf87'

# Author of this module
Author = 'User01'

# Company or vendor of this module
CompanyName = 'Unknown'

# Copyright statement for this module
Copyright = '(c) User01. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the PowerShell engine required by this module
# PowerShellVersion = ''

# Name of the PowerShell host required by this module
# PowerShellHostName = ''

# Minimum version of the PowerShell host required by this module
# PowerShellHostVersion = ''

# Minimum version of Microsoft .NET Framework required by this module. This prerequisite is valid for the PowerShell Desktop edition only.
# DotNetFrameworkVersion = ''

# Minimum version of the common language runtime (CLR) required by this module. This prerequisite is valid for the PowerShell Desktop edition only.
# CLRVersion = ''

# Processor architecture (None, X86, Amd64) required by this module
# ProcessorArchitecture = ''

# Modules that must be imported into the global environment prior to importing this module
# RequiredModules = @()

# Assemblies that must be loaded prior to importing this module
# RequiredAssemblies = @()

# Script files (.ps1) that are run in the caller's environment prior to importing this module.
# ScriptsToProcess = @()

# Type files (.ps1xml) to be loaded when importing this module
# TypesToProcess = @()

# Format files (.ps1xml) to be loaded when importing this module
# FormatsToProcess = @()

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
# NestedModules = @()

# Functions to export from this module, for best performance, do not use wildcards and do not delete the entry, use an empty array if there are no functions to export.
FunctionsToExport = @()

# Cmdlets to export from this module, for best performance, do not use wildcards and do not delete the entry, use an empty array if there are no cmdlets to export.
CmdletsToExport = @()

# Variables to export from this module
VariablesToExport = '*'

# Aliases to export from this module, for best performance, do not use wildcards and do not delete the entry, use an empty array if there are no aliases to export.
AliasesToExport = @()

# DSC resources to export from this module
# DscResourcesToExport = @()

# List of all modules packaged with this module
# ModuleList = @()

# List of all files packaged with this module
# FileList = @()

# Private data to pass to the module specified in RootModule/ModuleToProcess. This may also contain a PSData hashtable with additional module metadata used by PowerShell.
PrivateData = @{

    PSData = @{

        # Tags applied to this module. These help with module discovery in online galleries.
        # Tags = @()

        # A URL to the license for this module.
        # LicenseUri = ''

        # A URL to the main website for this project.
        # ProjectUri = ''

        # A URL to an icon representing this module.
        # IconUri = ''

        # ReleaseNotes of this module
        # ReleaseNotes = ''

        # Prerelease string of this module
        # Prerelease = ''

        # Flag to indicate whether the module requires explicit user acceptance for install/update/save
        RequireLicenseAcceptance = $true

        # External dependent modules of this module
        # ExternalModuleDependencies = @()

    } # End of PSData hashtable

} # End of PrivateData hashtable

# HelpInfo URI of this module
# HelpInfoURI = ''

# Default prefix for commands exported from this module. Override the default prefix using Import-Module -Prefix.
# DefaultCommandPrefix = ''

}
```

## <a name="see-also"></a>請參閱

[about_Comparison_Operators](/powershell/module/microsoft.powershell.core/about/about_comparison_operators)

[about_If](/powershell/module/microsoft.powershell.core/about/about_if)

[全域組件快取](/dotnet/framework/app-domains/gac)

[Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module)

[New-ModuleManifest](/powershell/module/microsoft.powershell.core/new-modulemanifest)

[Test-ModuleManifest](/powershell/module/microsoft.powershell.core/test-modulemanifest)

[Update-ModuleManifest](/powershell/module/powershellget/update-modulemanifest)

[撰寫 Windows PowerShell 模組](./writing-a-windows-powershell-module.md)
