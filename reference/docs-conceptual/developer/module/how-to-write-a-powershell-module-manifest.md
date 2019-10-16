---
title: 如何撰寫 PowerShell 模組資訊清單 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e082c2e3-12ce-4032-9caf-bf6b2e0dcf81
caps.latest.revision: 23
ms.openlocfilehash: 1265855b82b0bfaa7b2717c8eb348b822c19f561
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367097"
---
# <a name="how-to-write-a-powershell-module-manifest"></a>如何撰寫 PowerShell 模組資訊清單

撰寫 Windows PowerShell 模組之後，您可以選擇性地新增模組資訊清單。 模組資訊清單是 PowerShell 腳本檔案，可供您用來包含模組的相關資訊。 例如，您可以描述作者、指定模組中的檔案（例如，嵌套模組）、執行腳本以自訂使用者的環境、載入類型和格式檔案、定義系統需求，以及限制模組匯出的成員。

## <a name="creating-a-module-manifest"></a>建立模組資訊清單

*模組資訊清單*是一種 Windows PowerShell 資料檔（. .psd1），可描述模組的內容，並決定模組的處理方式。 資訊清單檔案本身是一個文字檔，其中包含索引鍵和值的雜湊表。 您可以將資訊清單檔案與模組命名為相同的模組，並將它放在模組目錄的根目錄中。

針對只包含單一 .psm1 或二進位元件的簡單模組，模組資訊清單是選擇性的。 不過，建議您盡可能使用模組資訊清單，因為它們有助於您組織程式碼及維護版本設定資訊。 此外，也需要模組資訊清單，才能匯出安裝在全域組件快取中的元件。 支援可更新的說明功能的模組也需要模組資訊清單。 也就是說，「可更新的說明」會使用模組資訊清單中的**HelpInfoUri**索引鍵來尋找說明資訊（HelpInfo XML）檔案，其中包含模組的已更新說明檔的位置。 如需「可更新的說明」的詳細資訊，請參閱[支援可更新的協助](./supporting-updatable-help.md)。

### <a name="to-create-and-use-a-module-manifest"></a>若要建立和使用模組資訊清單

1. 若要建立模組資訊清單，您有數個選項：

   1. 直接以所需的最少資訊建立雜湊表，並將它儲存至與模組同名的 .psd1 檔案。 完成此動作之後，您就可以開啟檔案，並手動新增適當的值。

      `'@{ModuleVersion="1.0"}' > myModuleName.psd1`

   2. 或者，呼叫[new-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) Cmdlet，並將一或多個預設值當做參數傳入。 （請注意，只有檔案的名稱才需要產生資訊清單。）這會建立模組資訊清單，其中包含您所提供的所有資訊清單值，以及包含適當預設值的其餘部分。

      `New-ModuleManifest myModuleName.psd1 -ModuleVersion "2.0" -Author "YourNameHere"`

   3. 最後，您也可以建立空白的 .psd1 檔案，並將本主題底部的範本複製到檔案中，並填入相關的值。 在此情況下，唯一真正的需求是確保檔案的名稱與模組相同。

2. 將任何其他專案加入您想要在檔案中擁有的資訊清單。

   一般來說，這可能會在您偏好的任何文字編輯器（例如 [記事本]）中完成。 不過，在技術上，這是包含程式碼的腳本檔案，因此您可能會想要在實際的腳本或開發環境中編輯它，例如 Visual Studio Code。 同樣地，請注意，資訊清單檔的所有元素都是選擇性的，但 ModuleVersion 號碼除外。

   如需可在模組資訊清單中擁有之金鑰和值的描述，請參閱下面的**模組資訊清單元素**。 如需其他資訊，請參閱[new-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) Cmdlet 中的參數說明。

3. （選擇性）您可以選擇將額外的程式碼新增至模組資訊清單，以解決基底模組資訊清單元素不會涵蓋的任何案例。

   由於安全性考慮，PowerShell 只會在模組資訊清單檔案中執行一小部分的可用作業。 一般來說，您可以使用**if**語句、算術和比較運算子，以及基本的 PowerShell 資料類型。

4. 建立模組資訊清單之後，您可以測試它（以確認資訊清單中所描述的任何路徑是否正確）與[new-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest)的呼叫。

   `Test-ModuleManifest myModuleName.psd1`

5. 請確定您的模組資訊清單位於包含模組的目錄最上層。

   當您將模組複製到系統上並將它匯入時，PowerShell 會使用模組資訊清單來匯入您的模組。

6. （選擇性）您可以在資訊清單本身的情況下，直接透過點對匯[入模組](/powershell/module/Microsoft.PowerShell.Core/Import-Module)的呼叫來測試模組資訊清單。

   `Import-Module .\myModuleName.psd1`

## <a name="module-manifest-elements"></a>模組資訊清單元素

下表描述可在模組資訊清單中擁有的元素

|元素|Default|描述|
|-------------|-------------|-----------------|
|RootModule<br /><br /> 類型：字串|' '|與這個資訊清單相關聯的腳本模組或二進位模組檔案。 先前的 PowerShell 版本稱為此元素 ModuleToProcess。<br /><br /> 根模組的可能類型可以是空的（這會使其成為**資訊清單**模組）、腳本模組的名稱（.psm1，這會使其成為**腳本**模組），或二進位模組（.exe 或 .dll）的名稱，這會使其成為**二進位**模組。 將模組資訊清單的名稱（. .psd1）或腳本檔案（ps1）放在這個專案中，會導致發生錯誤。|
|ModuleVersion<br /><br /> 類型：字串|1.0|此模組的版本號碼。 字串必須能夠轉換成 [System.object]。 也就是 ' #. #. #. #. # '。 `Import-Module` 會載入它在符合名稱的 **$psModulePath**上找到的第一個模組，而且至少要有 ModuleVersion，做為 `-MinimumVersion` 參數。 若要匯入特定版本，請改用 @ no__t-0 參數。<br /><br /> 範例： `ModuleVersion = '1.0'`|
|GUID<br /><br /> 類型：字串|自動產生的 GUID|用來唯一識別此模組的識別碼。 請注意，您目前無法依 GUID 匯入模組。<br /><br /> 範例： `GUID = 'cfc45206-1e49-459d-a8ad-5b571ef94857'`|
|作者<br /><br /> 類型：字串|無|此課程模組的作者。<br /><br /> 範例： `Author = 'AuthorNameHere'`|
|CompanyName<br /><br /> 類型：字串|Unknown|本課程模組的公司或廠商。<br /><br /> 範例： `CompanyName = 'Fabrikam'`|
|著作權<br /><br /> 類型：字串|（c） [currentYear] [Author]。 著作權所有，並保留一切權利。|本課程模組的著作權聲明。<br /><br /> 範例： `Copyright = '2016 AuthorName. All rights reserved.'`|
|描述<br /><br /> 類型：字串|' '|此模組所提供的功能描述。<br /><br /> 範例： `Description = 'This is a description of a module.'`|
|PowerShellVersion<br /><br /> 類型：字串|' '|此模組所需之 Windows PowerShell 引擎的最低版本。 目前有效的值為1.0、2.0、3.0、4.0 和5.0。<br /><br /> 範例： `PowerShellVersion = '5.0'`|
|PowerShellHostName<br /><br /> 類型：字串|' '|指定模組所需的 Windows PowerShell 主機名稱。 這個名稱是由 Windows PowerShell 提供。 若要尋找主機程式的名稱，請在程式中輸入： `$host.name`。<br /><br /> 範例： `PowerShellHostName = 'Windows PowerShell ISE Host'`|
|PowerShellHostVersion<br /><br /> 類型：字串|' '|此模組所需的 Windows PowerShell 主機最低版本。<br /><br /> 範例： `PowerShellHostVersion = '2.0'`|
|DotNetFrameworkVersion<br /><br /> 類型：字串|' '|本課程模組所需的 Microsoft .NET Framework 最低版本。<br /><br /> 範例： `DotNetFrameworkVersion = '3.5'`|
|CLRVersion<br /><br /> 類型：字串|' '|此模組所需的最小 common language runtime （CLR）版本。<br /><br /> 範例： `CLRVersion = '3.5'`|
|ProcessorArchitecture<br /><br /> 類型：字串|' '|此模組所需的處理器架構（None、X86、Amd64）。 有效值為 x86、AMD64、IA64 和 None (未知或未指定)。<br /><br /> 範例： `ProcessorArchitecture = 'x86'`|
|RequiredModules<br /><br /> 類型： [string []]|@()|在匯入此模組之前，必須先匯入至全域環境的模組。 這會載入任何列出的模組，除非它們已經載入。 (例如，有些模組可能已經由其他模組載入)。 您也可以使用 `RequiredVersion` 來指定要載入的特定版本，而不是 `ModuleVersion`。 當使用 `ModuleVersion` 時，它會載入最少指定版本的最新可用版本。<br /><br /> 範例： `RequiredModules = @(@{ModuleName="myDependentModule"; ModuleVersion="2.0"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})`<br /><br /> 範例： `RequiredModules = @(@{ModuleName="myDependentModule"; RequiredVersion="1.5"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})`|
|RequiredAssemblies<br /><br /> 類型： [string []]|@()|必須在匯入此模組之前載入的元件。<br /><br /> 請注意，不同于 RequiredModules，PowerShell 會載入 RequiredAssemblies （如果尚未載入）。|
|Scriptstoprocess 索引<br /><br /> 類型： [string []]|@()|匯入模組時，在呼叫者會話狀態中執行的腳本（ps1）檔案。 這可能是全域會話狀態，或是針對嵌套模組，也就是另一個模組的會話狀態。 您可以使用這些腳本來準備環境，就像您可以使用登入腳本一樣。<br /><br /> 這些腳本會在載入資訊清單中列出的任何模組之前執行。|
|TypesToProcess<br /><br /> 類型： [string []]|@()|匯入此模組時要載入的類型檔案（. types.ps1xml）。|
|FormatsToProcess<br /><br /> 類型： [string []]|@()|匯入此模組時要載入的格式檔案（. types.ps1xml）。|
|NestedModules<br /><br /> 類型： [string []]|@()|要以 RootModule/ModuleToProcess 中指定之模組的嵌套模組形式匯入的模組。<br /><br /> 將模組名稱加入這個專案類似于從您的腳本或元件程式碼中呼叫 `Import-Module`。 主要的差異在於，您可以更輕鬆地在資訊清單檔案中看到您要載入的內容。 此外，如果模組無法在此載入，您尚未載入實際的模組。<br /><br /> 除了其他模組之外，您也可以在這裡載入腳本（ps1）檔案。 這些檔案會在根模組的內容中執行。 （這相當於您根模組中的腳本點來源）。|
|FunctionsToExport<br /><br /> 類型： [string []]|@()|指定模組匯出的函式（允許但不鼓勵使用萬用字元）給呼叫者的會話狀態。 根據預設，不會匯出任何函式。 您可以使用此索引鍵來列出模組匯出的函式。<br /><br /> 呼叫者的會話狀態可以是全域會話狀態，或是針對嵌套模組，另一個模組的會話狀態。 連結嵌套模組時，除非鏈中的模組使用 FunctionsToExport 索引鍵來限制函式，否則，所有由嵌套模組匯出的函式都會匯出到全域會話狀態。<br /><br /> 如果資訊清單也會匯出函式的別名，此索引鍵可以移除其別名列在 AliasesToExport 索引鍵中的函式，但此索引鍵無法將函式別名加入清單中。|
|CmdletsToExport<br /><br /> 類型： [string []]|@()|指定模組匯出的 Cmdlet （允許使用萬用字元，但不建議您這樣做）。 根據預設，不會匯出任何 Cmdlet。 您可以使用此金鑰來列出模組匯出的 Cmdlet。<br /><br /> 呼叫者的會話狀態可以是全域會話狀態，或是針對嵌套模組，另一個模組的會話狀態。 當您要連結嵌套模組時，所有由嵌套模組匯出的 Cmdlet 最後都會匯出到全域會話狀態，除非鏈中的模組使用 CmdletsToExport 金鑰來限制此 Cmdlet。<br /><br /> 如果資訊清單也會匯出 Cmdlet 的別名，此機碼可以移除其別名列在 AliasesToExport 機碼中的 Cmdlet，但此金鑰無法將 Cmdlet 別名新增至清單。|
|VariablesToExport<br /><br /> 類型：字串|'*'|指定模組匯出的變數（允許的萬用字元）給呼叫者的會話狀態。 根據預設，會匯出所有的變數。 您可以使用此金鑰來限制模組匯出的變數。<br /><br /> 呼叫者的會話狀態可以是全域會話狀態，或是針對嵌套模組，另一個模組的會話狀態。 當您要連結嵌套模組時，所有由嵌套模組匯出的變數都會匯出到全域會話狀態，除非鏈中的模組使用 VariablesToExport 索引鍵來限制變數。<br /><br /> 如果資訊清單也會匯出變數的別名，此索引鍵可以移除別名列在 AliasesToExport 索引鍵中的變數，但此索引鍵無法將變數別名加入清單中。|
|AliasesToExport<br /><br /> 類型： [string []]|@()|指定模組匯出的別名（允許但不鼓勵使用萬用字元）給呼叫者的會話狀態。 根據預設，不會匯出任何別名。 您可以使用此金鑰來列出模組匯出的別名。<br /><br /> 呼叫者的會話狀態可以是全域會話狀態，或是針對嵌套模組，另一個模組的會話狀態。 當您要連結嵌套模組時，所有由嵌套模組匯出的別名最終都會匯出到全域會話狀態，除非鏈中的模組使用 AliasesToExport 索引鍵來限制別名。|
|ModuleList<br /><br /> 類型： [string []]|@()|指定與此模組一起封裝的所有模組。 這些模組可以依名稱（以逗號分隔的字串）輸入，或以具有 ModuleName 和 GUID 索引鍵的雜湊表來輸入。 雜湊表也可以有選擇性的 ModuleVersion 索引鍵。 ModuleList 索引鍵是設計來作為模組清查。 這些模組不會自動處理。|
|FileList<br /><br /> 類型： [string []]|@()|此課程模組所封裝之所有檔案的清單。 如同 ModuleList，FileList 可協助您做為清查清單，但不會進行處理。|
|PrivateData<br /><br /> 類型： [物件]|@{...}|指定需要傳遞至 RootModule/ModuleToProcess 索引鍵所指定之根模組的任何私用資料。|
|HelpInfoURI<br /><br /> 類型：字串|' '|此模組的 HelpInfo URI。|
|DefaultCommandPrefix<br /><br /> 類型：字串|' '|從這個模組匯出之命令的預設前置詞。 使用 `Import-Module`-前置詞覆寫預設前置詞。|

## <a name="sample-module-manifest"></a>範例模組資訊清單

下列範例模組資訊清單會顯示模組資訊清單中的索引鍵和預設值。 這個範例是使用 Windows PowerShell 3.0 中的 `New-ModuleManifest` Cmdlet 所建立。 建立多個模組時，您可以使用這個指令程式來建立可針對不同模組修改的資訊清單範本。

```powershell
#
# Module manifest for module 'myManifest'
#
# Generated by: User01
#
# Generated on: 2019-10-09
#

@{

# Script module or binary module file associated with this manifest.
# RootModule = ''

# Version number of this module.
ModuleVersion = '1.0'

# Supported PSEditions
# CompatiblePSEditions = @()

# ID used to uniquely identify this module
GUID = 'b888e5a2-8578-4c0b-938d-0cd9b5b836ba'

# Author of this module
Author = 'User01'

# Company or vendor of this module
CompanyName = 'Unknown'

# Copyright statement for this module
Copyright = '(c) 2019 User01. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the Windows PowerShell engine required by this module
# PowerShellVersion = ''

# Name of the Windows PowerShell host required by this module
# PowerShellHostName = ''

# Minimum version of the Windows PowerShell host required by this module
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

    } # End of PSData hashtable

} # End of PrivateData hashtable

# HelpInfo URI of this module
# HelpInfoURI = ''

# Default prefix for commands exported from this module. Override the default prefix using Import-Module -Prefix.
# DefaultCommandPrefix = ''

}

```

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell 模組](./writing-a-windows-powershell-module.md)
