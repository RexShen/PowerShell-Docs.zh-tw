---
title: 如何撰寫 PowerShell 模組資訊清單 |Microsoft Docs
ms.custom: ''
ms.date: 10/16/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e082c2e3-12ce-4032-9caf-bf6b2e0dcf81
caps.latest.revision: 23
ms.openlocfilehash: 4aa6c020cf0e82a4ffcad6f6c7540688d3369aa6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72561290"
---
# <a name="how-to-write-a-powershell-module-manifest"></a>如何撰寫 PowerShell 模組資訊清單

撰寫 PowerShell 模組之後，您可以新增包含模組相關資訊的選擇性模組資訊清單。 例如，您可以描述作者、指定模組中的檔案（例如，嵌套模組）、執行腳本以自訂使用者的環境、載入類型和格式檔案、定義系統需求，以及限制模組匯出的成員。

## <a name="creating-a-module-manifest"></a>建立模組資訊清單

**模組資訊清單**是 PowerShell 資料檔（`.psd1`），可描述模組的內容，並決定模組的處理方式。 資訊清單檔案是文字檔，其中包含索引鍵和值的雜湊表。 您可以將資訊清單檔連結至模組，方法是將資訊清單命名為與模組相同，並將資訊清單儲存在模組的根目錄中。

針對只包含單一 `.psm1` 或二進位元件的簡單模組，模組資訊清單是選擇性的。 但建議您盡可能使用模組資訊清單，因為它們有助於您組織程式碼及維護版本設定資訊。 此外，需要模組資訊清單才能匯出安裝在[全域組件快取](/dotnet/framework/app-domains/gac)中的元件。 支援可更新的說明功能的模組也需要模組資訊清單。 「可更新的說明」使用模組資訊清單中的**HelpInfoUri**索引鍵來尋找說明資訊（HelpInfo XML）檔案，其中包含模組的已更新說明檔的位置。 如需「可更新的說明」的詳細資訊，請參閱[支援可更新的協助](./supporting-updatable-help.md)。

### <a name="to-create-and-use-a-module-manifest"></a>若要建立和使用模組資訊清單

1. 建立模組資訊清單的最佳做法是使用[new-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) Cmdlet。 您可以使用參數來指定一或多個資訊清單的預設索引鍵和值。 唯一的需求是將檔案命名為。 `New-ModuleManifest` 會使用您指定的值建立模組資訊清單，並包含其餘的索引鍵及其預設值。 如果您需要建立多個模組，請使用 `New-ModuleManifest` 來建立可針對不同模組修改的模組資訊清單範本。 如需預設模組資訊清單的範例，請參閱[範例模組資訊清單](#sample-module-manifest)。

   `New-ModuleManifest -Path C:\myModuleName.psd1 -ModuleVersion "2.0" -Author "YourNameHere"`

   另一個替代方式是使用所需的最少資訊（ **ModuleVersion**）手動建立模組資訊清單的雜湊表。 您可以使用與模組相同的名稱來儲存檔案，並使用 `.psd1` 的副檔名。 接著，您可以編輯檔案，並新增適當的索引鍵和值。

1. 在資訊清單檔中新增您想要的任何其他元素。

   若要編輯資訊清單檔，請使用您偏好的任何文字編輯器。 不過，資訊清單檔案是包含程式碼的腳本檔案，因此您可能會想要在腳本或開發環境（例如 Visual Studio Code）中編輯它。 資訊清單檔案的所有元素都是選擇性的，但**ModuleVersion**號碼除外。

   如需可在模組資訊清單中包含的索引鍵和值的說明，請參閱[模組資訊清單元素](#module-manifest-elements)表。 如需詳細資訊，請參閱[new-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) Cmdlet 中的參數說明。

1. 若要解決基底模組資訊清單元素可能不會涵蓋的任何案例，您可以選擇將其他程式碼加入模組資訊清單。

   基於安全性考慮，PowerShell 只會在模組資訊清單檔案中執行一小部分的可用作業。 一般來說，您可以使用 `if` 語句、算術和比較運算子，以及基本的 PowerShell 資料類型。

1. 建立模組資訊清單之後，您可以測試它，以確認資訊清單中所描述的任何路徑是否正確。 若要測試您的模組資訊清單，請使用[測試 new-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest)。

   `Test-ModuleManifest myModuleName.psd1`

1. 請確定您的模組資訊清單位於包含模組的目錄最上層。

   當您將模組複製到系統上並將它匯入時，PowerShell 會使用模組資訊清單來匯入您的模組。

1. （選擇性）您可以在資訊清單本身的情況下，直接透過點對匯[入模組](/powershell/module/Microsoft.PowerShell.Core/Import-Module)的呼叫來測試模組資訊清單。

   `Import-Module .\myModuleName.psd1`

## <a name="module-manifest-elements"></a>模組資訊清單元素

下表描述可在模組資訊清單中包含的元素。

|元素|Default|描述|
|-------------|-------------|-----------------|
|**RootModule**<br /> 類型：`String`|`<empty string>`|與這個資訊清單相關聯的腳本模組或二進位模組檔案。 先前的 PowerShell 版本稱為此元素**ModuleToProcess**。<br /> 根模組的可能類型可以是空的，它會建立**資訊清單**模組、腳本模組的名稱（`.psm1`），或二進位模組的名稱（`.exe` 或 `.dll`）。 將模組資訊清單的名稱（`.psd1`）或腳本檔案（`.ps1`）放在此元素中會造成錯誤。 <br /> 範例： `RootModule = 'ScriptModule.psm1'`|
|**ModuleVersion**<br /> 類型：`Version`|`'0.0.1'`|此模組的版本號碼。 如果未指定值，`New-ModuleManifest` 會使用預設值。 字串必須能夠轉換成類型 `Version` 例如 `#.#.#.#.#`。 `Import-Module` 會載入它在符合名稱的 **$PSModulePath**上找到的第一個模組，而且至少有**ModuleVersion**，做為**MinimumVersion**參數。 若要匯入特定版本，請使用 `Import-Module` Cmdlet 的**RequiredVersion**參數。<br /> 範例： `ModuleVersion = '1.0'`|
|**GUID**<br /> 類型：`GUID`|`'<GUID>'`|用來唯一識別此模組的識別碼。 如果未指定值，`New-ModuleManifest` 會會自動產生值。 您目前無法依**GUID**匯入模組。 <br /> 範例： `GUID = 'cfc45206-1e49-459d-a8ad-5b571ef94857'`|
|**Author** (作者)<br /> 類型：`String`|`'<Current user>'`|此課程模組的作者。 如果未指定值，`New-ModuleManifest` 會使用目前的使用者。 <br /> 範例： `Author = 'AuthorNameHere'`|
|**CompanyName**<br /> 類型：`String`|`'Unknown'`|本課程模組的公司或廠商。 如果未指定值，`New-ModuleManifest` 會使用預設值。<br /> 範例： `CompanyName = 'Fabrikam'`|
|**Copyright** (著作權)<br /> 類型：`String`|`'(c) <Author>. All rights reserved.'`| 本課程模組的著作權聲明。 如果未指定值，`New-ModuleManifest` 會使用預設與目前的使用者做為 `<Author>`。 若要指定作者，請使用**author**參數。 <br /> 範例： `Copyright = '2019 AuthorName. All rights reserved.'`|
|**描述**<br /> 類型：`String`|`<empty string>`|此模組所提供的功能描述。<br /> 範例： `Description = 'This is the module's description.'`|
|**PowerShellVersion**<br /> 類型：`Version`|`<empty string>`|此模組所需的最小 PowerShell 引擎版本。 有效的值為1.0、2.0、3.0、4.0、5.0、5.1、6和7。<br /> 範例： `PowerShellVersion = '5.0'`|
|**PowerShellHostName**<br /> 類型：`String`|`<empty string>`|此模組所需的 PowerShell 主機名稱。 這個名稱是由 PowerShell 提供。 若要尋找主機程式的名稱，請在程式中輸入： `$host.name`。<br /> 範例： `PowerShellHostName = 'ConsoleHost'`|
|**PowerShellHostVersion**<br /> 類型：`Version`|`<empty string>`|此模組所需的 PowerShell 主機最低版本。<br /> 範例： `PowerShellHostVersion = '2.0'`|
|**DotNetFrameworkVersion**<br /> 類型：`Version`|`<empty string>`|本課程模組所需的 Microsoft .NET Framework 最低版本。 這項必要條件僅適用于 PowerShell Desktop 版本，例如 PowerShell 5.1。<br /> 範例： `DotNetFrameworkVersion = '3.5'`|
|**CLRVersion**<br /> 類型：`Version`|`<empty string>`|此模組所需的最小 common language runtime （CLR）版本。 這項必要條件僅適用于 PowerShell Desktop 版本，例如 PowerShell 5.1。<br /> 範例： `CLRVersion = '3.5'`|
|**ProcessorArchitecture**<br /> 類型：`ProcessorArchitecture`|`<empty string>`|此模組所需的處理器架構（None、X86、Amd64）。 有效值為 x86、AMD64、Arm、IA64、MSIL 和 None （未知或未指定）。<br /> 範例： `ProcessorArchitecture = 'x86'`|
|**RequiredModules**<br /> 類型：`Object[]`|`@()`|在匯入此模組之前，必須先匯入至全域環境的模組。 這會載入任何列出的模組，除非它們已經載入。 例如，有些模組可能已經由其他模組載入。 您可以使用 `RequiredVersion` 來指定要載入的特定版本，而不是 `ModuleVersion`。 使用 `ModuleVersion` 時，它會載入最少指定版本的可用最新版本。 您可以在參數值中結合字串和雜湊表。<br /> 範例： `RequiredModules = @("MyModule", @{ModuleName="MyDependentModule"; ModuleVersion="2.0"; GUID="cfc45206-1e49-459d-a8ad-5b571ef94857"})`<br /> 範例： `RequiredModules = @("MyModule", @{ModuleName="MyDependentModule"; RequiredVersion="1.5"; GUID="cfc45206-1e49-459d-a8ad-5b571ef94857"})`|
|**RequiredAssemblies**<br /> 類型：`String[]`|`@()`|必須在匯入此模組之前載入的元件。 指定模組所需的元件（`.dll`）檔案名。<br /> PowerShell 會先載入指定的元件，再更新類型或格式、匯入嵌套模組，或匯入 RootModule 索引鍵值中所指定的模組檔案。 使用此參數來列出模組所需的所有元件。<br /> 範例： `RequiredAssemblies = @("assembly1.dll", "assembly2.dll", "assembly3.dll")`|
|**Scriptstoprocess 索引**<br /> 類型：`String[]`|`@()`|匯入模組時，在呼叫者會話狀態中執行的腳本（`.ps1`）檔案。 這可能是全域會話狀態，或是針對嵌套模組，也就是另一個模組的會話狀態。 您可以使用這些腳本來準備環境，就像您可以使用 [登入腳本] 一樣。<br /> 這些腳本會在載入資訊清單中列出的任何模組之前執行。 <br /> 範例： `ScriptsToProcess = @("script1.ps1", "script2.ps1", "script3.ps1")`|
|**TypesToProcess**<br /> 類型：`String[]`|`@()`|匯入此模組時要載入的類型檔案（`.ps1xml`）。 <br /> 範例： `TypesToProcess = @("type1.ps1xml", "type2.ps1xml", "type3.ps1xml")`|
|**FormatsToProcess**<br /> 類型：`String[]`|`@()`|匯入此模組時要載入的格式檔案（`.ps1xml`）。 <br /> 範例： `FormatsToProcess = @("format1.ps1xml", "format2.ps1xml", "format3.ps1xml")`|
|**NestedModules**<br /> 類型：`Object[]`|`@()`|要匯入為**RootModule** （別名：**ModuleToProcess**）中所指定模組之嵌套模組的模組。<br /> 將模組名稱加入這個專案類似于從您的腳本或元件程式碼中呼叫 `Import-Module`。 使用資訊清單檔案的主要差異在於，您可以更輕鬆地查看所要載入的內容。 而且，如果模組無法載入，您還不會載入實際的模組。<br /> 除了其他模組之外，您也可以在這裡載入腳本（`.ps1`）檔案。 這些檔案會在根模組的內容中執行。 這相當於根模組中的腳本點來源。 <br /> 範例： `NestedModules = @("script.ps1", @{ModuleName="MyModule"; ModuleVersion="1.0.0.0"; GUID="50cdb55f-5ab7-489f-9e94-4ec21ff51e59"})`|
|**FunctionsToExport**<br /> 類型：`String[]`|`@()`|指定要從這個模組匯出的函式，若要獲得最佳效能，請不要使用萬用字元，也不要刪除專案，如果沒有可匯出的函式，請使用空陣列。 根據預設，不會匯出任何函式。 您可以使用此索引鍵來列出模組匯出的函式。<br /> 模組會將函式匯出至呼叫者的會話狀態。 呼叫者的會話狀態可以是全域會話狀態，或是針對嵌套模組，另一個模組的會話狀態。 連結嵌套模組時，除非鏈中的模組使用**FunctionsToExport**索引鍵來限制函式，否則，所有由嵌套模組匯出的函式都會匯出到全域會話狀態。<br /> 如果資訊清單匯出函式的別名，此索引鍵可以移除其別名列在**AliasesToExport**索引鍵中的函式，但此索引鍵無法將函式別名加入清單中。 <br /> 範例： `FunctionsToExport = @("function1", "function2", "function3")`|
|**CmdletsToExport**<br /> 類型：`String[]`|`@()`|指定要從這個模組匯出的 Cmdlet，為了達到最佳效能，請不要使用萬用字元，也不要刪除專案，如果沒有可匯出的 Cmdlet，請使用空陣列。 根據預設，不會匯出任何 Cmdlet。 您可以使用此金鑰來列出模組匯出的 Cmdlet。<br /> 呼叫者的會話狀態可以是全域會話狀態，或是針對嵌套模組，另一個模組的會話狀態。 當您要連結嵌套模組時，所有由嵌套模組匯出的 Cmdlet 都會匯出到全域會話狀態，除非鏈中的模組使用**CmdletsToExport**金鑰來限制此 Cmdlet。<br /> 如果資訊清單匯出 Cmdlet 的別名，此金鑰可以移除**AliasesToExport**機碼中列出其別名的 Cmdlet，但此金鑰無法將 Cmdlet 別名新增至清單。 <br /> 範例： `CmdletsToExport = @("Get-MyCmdlet", "Set-MyCmdlet", "Test-MyCmdlet")`|
|**VariablesToExport**<br /> 類型：`String[]`|`'*'`|指定模組匯出至呼叫者會話狀態的變數。 允許使用萬用字元。 預設會匯出所有變數（`'*'`）。 您可以使用此金鑰來限制模組匯出的變數。<br /> 呼叫者的會話狀態可以是全域會話狀態，或是針對嵌套模組，另一個模組的會話狀態。 當您要連結嵌套模組時，所有由嵌套模組匯出的變數都會匯出到全域會話狀態，除非鏈中的模組使用**VariablesToExport**索引鍵來限制變數。<br /> 如果資訊清單也會匯出變數的別名，此索引鍵可以移除別名列在**AliasesToExport**索引鍵中的變數，但此索引鍵無法將變數別名加入清單中。 <br /> 範例： `VariablesToExport = @('$MyVariable1', '$MyVariable2', '$MyVariable3')`|
|**AliasesToExport**<br /> 類型：`String[]`|`@()`|指定要從這個模組匯出的別名，為了達到最佳效能，請不要使用萬用字元，也不要刪除專案，如果沒有可匯出的別名，請使用空陣列。 根據預設，不會匯出任何別名。 您可以使用此金鑰來列出模組匯出的別名。<br /> 此模組會將別名匯出至呼叫者的會話狀態。 呼叫者的會話狀態可以是全域會話狀態，或是針對嵌套模組，另一個模組的會話狀態。 當您要連結嵌套模組時，所有由嵌套模組匯出的別名最終都會匯出到全域會話狀態，除非鏈中的模組使用**AliasesToExport**索引鍵來限制別名。 <br /> 範例： `AliasesToExport = @("MyAlias1", "MyAlias2", "MyAlias3")`|
|**DscResourcesToExport**<br /> 類型：`String[]`|`@()`|指定要從這個模組匯出的 DSC 資源。 允許使用萬用字元。 <br /> 範例： `DscResourcesToExport = @("DscResource1", "DscResource2", "DscResource3")`|
|**ModuleList**<br /> 類型：`Object[]`|`@()`|指定與此模組一起封裝的所有模組。 這些模組可以依名稱輸入、使用逗點分隔字串，或當做具有**ModuleName**和**GUID**金鑰的雜湊表。 雜湊表也可以有選擇性的**ModuleVersion**索引鍵。 **ModuleList**索引鍵是設計來作為模組清查。 這些模組不會自動處理。 <br /> 範例： `ModuleList = @("SampleModule", "MyModule", @{ModuleName="MyModule"; ModuleVersion="1.0.0.0"; GUID="50cdb55f-5ab7-489f-9e94-4ec21ff51e59"})`|
|**FileList** (檔案清單)<br /> 類型：`String[]`|`@()`|此課程模組所封裝之所有檔案的清單。 如同**ModuleList**， **FileList**是一份清查清單，不會進行其他處理。 <br /> 範例： `FileList = @("File1", "File2", "File3")`|
|**PrivateData**<br /> 類型：`Object`|`@{...}`|指定需要傳遞至**RootModule** （Alias： **ModuleToProcess**）索引鍵所指定之根模組的任何私用資料。 **PrivateData**是包含數個元素的雜湊表 **： Tags**、 **LicenseUri**、 **ProjectURI**、 **IconUri**、 **ReleaseNotes**、**發行**前版本、 **RequireLicenseAcceptance**和**ExternalModuleDependencies**。 |
|**Tags** (標籤) <br /> 類型：`String[]` |`@()`| 標籤有助於線上資源庫中的模組探索。 <br /> 範例： `Tags = "PackageManagement", "PowerShell", "Manifest"`|
|**LicenseUri**<br /> 類型：`Uri` |`<empty string>`| 此模組的授權 URL。 <br /> 範例： `LicenseUri = 'https://www.contoso.com/license'`|
|**ProjectUri**<br /> 類型：`Uri` |`<empty string>`| 這個專案之主要網站的 URL。 <br /> 範例： `ProjectUri = 'https://www.contoso.com/project'`|
|**IconUri**<br /> 類型：`Uri` |`<empty string>`| 代表此模組的圖示 URL。 <br /> 範例： `IconUri = 'https://www.contoso.com/icons/icon.png'`|
|**ReleaseNotes**<br /> 類型：`String` |`<empty string>`| 指定模組的版本資訊。 <br /> 範例： `ReleaseNotes = 'The release notes provide information about the module.`|
|**版**<br /> 類型：`String` |`<empty string>`| 已在 PowerShell 7 中新增此參數。 預先**發行**的字串，可將模組識別為線上元件庫中的發行前版本。 <br /> 範例： `PreRelease = 'This module is a prerelease version.`|
|**RequireLicenseAcceptance**<br /> 類型：`Boolean`|`$true`| 已在 PowerShell 7 中新增此參數。 旗標，指出模組是否需要明確的使用者接受以進行安裝、更新或儲存。 <br /> 範例： `RequireLicenseAcceptance = $false`|
|**ExternalModuleDependencies**<br /> 類型：`String[]` |`@()`| 已在 PowerShell 7 中新增此參數。 此模組相依的外部模組清單。 <br /> 範例： `ExternalModuleDependencies =  @("ExtModule1", "ExtModule2", "ExtModule3")`|
|**HelpInfoURI**<br /> 類型：`String`|`<empty string>`|此模組的 HelpInfo URI。 <br /> 範例： `HelpInfoURI = 'https://www.contoso.com/help'`|
|**DefaultCommandPrefix**<br /> 類型：`String`|`<empty string>`|從這個模組匯出之命令的預設前置詞。 使用 `Import-Module -Prefix`覆寫預設前置詞。 <br /> 範例： `DefaultCommandPrefix = 'My'`|

## <a name="sample-module-manifest"></a>範例模組資訊清單

下列範例模組資訊清單是使用 PowerShell 7 中的 `New-ModuleManifest` 所建立，並包含預設的索引鍵和值。

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

## <a name="see-also"></a>另請參閱

[about_Comparison_Operators](/powershell/module/microsoft.powershell.core/about/about_comparison_operators)

[about_If](/powershell/module/microsoft.powershell.core/about/about_if)

[全域組件快取](/dotnet/framework/app-domains/gac)

[Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module)

[New-ModuleManifest](/powershell/module/microsoft.powershell.core/new-modulemanifest)

[Test-ModuleManifest](/powershell/module/microsoft.powershell.core/test-modulemanifest)

[Update-ModuleManifest](/powershell/module/powershellget/update-modulemanifest)

[撰寫 Windows PowerShell 模組](./writing-a-windows-powershell-module.md)
