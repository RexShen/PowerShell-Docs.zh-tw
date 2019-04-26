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
ms.openlocfilehash: 93a8c11099a9883127bca87422e1acaebfd2c093
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082289"
---
# <a name="how-to-write-a-powershell-module-manifest"></a>如何撰寫 PowerShell 模組資訊清單

當您撰寫完您的 Windows PowerShell 模組，您可以選擇性地加入的模組資訊清單。 模組資訊清單是您可以使用包含模組的相關資訊的 PowerShell 指令碼檔案。 例如，您可以描述作者，指定檔案 （例如巢狀模組） 模組中執行指令碼來自訂使用者的環境中，載入類型和格式的檔案、 定義系統需求和限制模組匯出的成員。

## <a name="creating-a-module-manifest"></a>建立模組資訊清單

A*模組資訊清單*是 Windows PowerShell 資料檔 (.psd1) 描述模組的內容，並決定如何處理模組。 資訊清單檔案本身是文字檔案，其中包含索引鍵和值的雜湊表。 您連結到模組的資訊清單檔案的模組，與相同命名，然後將它放在模組目錄的根目錄中。

針對只包含單一的.psm1 或二進位組件的簡單模組，模組資訊清單是選擇性的。 不過，建議您使用的是可能的話，模組資訊清單，因為它們是適用於以協助您組織您的程式碼，以及維護版本設定資訊。 此外，模組資訊清單才能匯出安裝在全域組件快取中的組件。 也需要支援 「 可更新的說明 」 功能的模組的模組資訊清單。 也就是使用可更新的說明**HelpInfoUri**模組資訊清單來尋找說明資訊 (HelpInfo XML) 檔案，其中包含模組的已更新的說明檔案位置中的索引鍵。 如需有關可更新說明的詳細資訊，請參閱 <<c0> [ 支援可更新說明](./supporting-updatable-help.md)。

### <a name="to-create-and-use-a-module-manifest"></a>建立和使用模組資訊清單

1. 若要建立模組資訊清單，您會有數個選項：

   1. 直接使用最少需要的資訊，建立雜湊表，並將它儲存到您的模組名稱相同的.psd1 檔案。 一旦您已經這樣做，您可以開啟檔案，並手動新增適當的值。

      `'@{ModuleVersion="1.0"}' > myModuleName.psd1`

   2. 或者，您也可以呼叫[New-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet，搭配一或多個預設值傳遞為參數。 (請注意，只需要產生資訊清單中，不過檔案的名稱。)提供的所有資訊清單值您明確指定，且包含適當的預設值的其餘部分，這會建立模組資訊清單。

      `New-ModuleManifest myModuleName.psd1 -ModuleVersion "2.0" -Author "YourNameHere"`

   3. 最後，您可以也建立空白的.psd1 檔案，並將在本主題底部的範本複製到檔案，並填入相關的值。 唯一的實際需求在此情況下是確定檔案命名為與模組相同。

2. 在任何其他項目中加入您想要在檔案中的資訊清單。

   一般而言，這可能會完成任何您喜歡，如 [記事本] 的文字編輯器中。 不過這就技術上而言是包含程式碼，因此您可能想要編輯的實際指令碼或開發環境中，例如 PowerShell ISE 指令碼檔案。 同樣地，請注意，所有的項目資訊清單檔案的選擇性的除了 ModuleVersion 數目。

   如需索引鍵和值，您可以在模組資訊清單的描述，請參閱 <<c0>  **模組資訊清單的項目**如下。 如需詳細資訊，請參閱中的參數說明[New-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet。

3. （選擇性） 您可以選擇將額外的程式碼新增至您的模組資訊清單，來解決任何基底的模組資訊清單的項目會未涵蓋的案例。

   基於安全性考量，PowerShell 會執行在模組資訊清單檔案中的一小部分可用的作業。 一般而言，您可以使用**如果**陳述式、 算術和比較運算子和基本的 PowerShell 資料型別。

4. 當您建立您的模組資訊清單之後時，您可以進行測試 （若要確認資訊清單是所述的任何路徑更正） 藉由呼叫[Test-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest)。

   `Test-ModuleManifest myModuleName.psd1`

5. 請確定您的模組資訊清單位於最上層目錄，其中包含您的模組。

   當您複製到系統模組，並將它匯入時，則 PowerShell 會使用模組資訊清單匯入您的模組。

6. （選擇性） 您可以直接測試您的模組資訊清單，藉由呼叫[Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module)由點執行本身的資訊清單。

   `Import-Module .\myModuleName.psd1`

## <a name="module-manifest-elements"></a>模組資訊清單的項目

下表說明您可以在模組資訊清單的項目

|元素|Default|描述|
|-------------|-------------|-----------------|
|RootModule<br /><br /> 型別： 字串|' '|指令碼模組或二進位模組檔案與此資訊清單相關聯。 舊版的 PowerShell 呼叫 ModuleToProcess 的這個項目。<br /><br /> 可能的根模組的類型可以是空 (這麼做會讓這**Manifest**模組)，指令碼模組的名稱 (.psm1，這樣的處理**指令碼**模組)，或二進位模組 （.exe 或.dll 的名稱這可讓這**二進位**模組)。 將模組資訊清單 (.psd1) 或指令碼檔案 (.ps1) 的名稱放在這個項目會導致發生錯誤。|
|ModuleVersion<br /><br /> 型別： 字串|1.0|此模組的版本號碼。 字串必須是可以將轉換成 [System.Version]。 也就是 ' #。 #。 #。 #。 #'。 `Import-Module` 會載入找到的第一個模組 **$psModulePath**的符合名稱，且至少為最高的 ModuleVersion 為`-MinimumVersion`參數。 若要匯入特定版本，請使用`-RequiredVersion`參數，而是。<br /><br /> 範例： `ModuleVersion = '1.0'`|
|GUID<br /><br /> 型別： 字串|自動產生 GUID|用來唯一識別此模組的識別碼。 請注意，目前無法匯入模組的 GUID。<br /><br /> 範例： `GUID = 'cfc45206-1e49-459d-a8ad-5b571ef94857'`|
|作者<br /><br /> 型別： 字串|無|此模組的作者。<br /><br /> 範例： `Author = 'AuthorNameHere'`|
|CompanyName<br /><br /> 型別： 字串|Unknown|公司或廠商，此模組。<br /><br /> 範例： `CompanyName = 'Fabrikam'`|
|著作權<br /><br /> 型別： 字串|（c) [currentYear] [作者]。 著作權所有，並保留一切權利。|此模組的著作權聲明。<br /><br /> 範例： `Copyright = '2016 AuthorName. All rights reserved.'`|
|描述<br /><br /> 型別： 字串|' '|此模組所提供之功能的描述。<br /><br /> 範例： `Description = 'This is a description of a module.'`|
|PowerShellVersion<br /><br /> 型別： 字串|' '|此模組所需的 Windows PowerShell 引擎的最小版本。 目前有效的值為 1.0、 2.0、 3.0、 4.0 和 5.0。<br /><br /> 範例： `PowerShellVersion = '5.0'`|
|PowerShellHostName<br /><br /> 型別： 字串|' '|指定 Windows PowerShell 主應用程式所需的模組名稱。 這個名稱是由 Windows PowerShell 提供。 若要尋找主機程式名稱，在程式中，輸入： `$host.name` 。<br /><br /> 範例： `PowerShellHostName = 'Windows PowerShell ISE Host'`|
|PowerShellHostVersion<br /><br /> 型別： 字串|' '|此模組所需的 Windows PowerShell 主機的最小版本。<br /><br /> 範例： `PowerShellHostVersion = '2.0'`|
|DotNetFrameworkVersion<br /><br /> 型別： 字串|' '|此模組所需的 Microsoft.NET Framework 的最低版本。<br /><br /> 範例： `DotNetFrameworkVersion = '3.5'`|
|CLRVersion<br /><br /> 型別： 字串|' '|Common language runtime (CLR) 此模組所需的最小版本。<br /><br /> 範例： `CLRVersion = '3.5'`|
|ProcessorArchitecture<br /><br /> 型別： 字串|' '|處理器架構 （無、 X86，Amd64） 此模組所需。 有效值為 x86、AMD64、IA64 和 None (未知或未指定)。<br /><br /> 範例： `ProcessorArchitecture = 'x86'`|
|RequiredModules<br /><br /> 類型: [字串 []]|@()|必須匯入全域環境，再匯入此模組的模組。 這會載入列，除非它們已經載入任何模組。 （例如，某些模組可能已經載入不同的模組。）。 您也可指定要載入使用的特定版本`RequiredVersion`而非`ModuleVersion`。 當使用`ModuleVersion`會載入指定的版本至少提供的最新版本。<br /><br /> 範例： `RequiredModules = @(@{ModuleName="myDependentModule"; ModuleVersion="2.0"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})`<br /><br /> 範例： `RequiredModules = @(@{ModuleName="myDependentModule"; RequiredVersion="1.5"; Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})`|
|RequiredAssemblies<br /><br /> 類型: [字串 []]|@()|必須先載入才能匯入此模組的組件。<br /><br /> 請注意，不同於 RequiredModules，PowerShell 會載入 RequiredAssemblies 是否尚未載入。|
|ScriptsToProcess<br /><br /> 類型: [字串 []]|@()|匯入模組時，呼叫端的工作階段狀態中執行的指令碼 (.ps1) 檔案。 這可能是全域的工作階段狀態，或在巢狀模組，另一個模組的工作階段狀態。 您可以使用這些指令碼來準備環境，您可能會使用登入指令碼一樣。<br /><br /> 載入任何模組資訊清單中列出之前，會執行這些指令碼。|
|TypesToProcess<br /><br /> 類型: [物件 []]|@()|輸入匯入此模組時要載入的檔案 (.ps1xml)。|
|FormatsToProcess<br /><br /> 類型: [物件 []]|@()|格式匯入此模組時要載入的檔案 (.ps1xml)。|
|NestedModules<br /><br /> 類型: [物件 []]|@()|要作為巢狀模組的 RootModule/ModuleToProcess 中指定的模組匯入模組。<br /><br /> 將模組名稱新增至這個項目是類似於呼叫`Import-Module`從您的指令碼或組件程式碼。 主要差異是您更輕鬆地查看哪些要載入這裡資訊清單檔中。 此外，以下載入模組時，您將尚未有載入實際的模組。<br /><br /> 除了其他模組中，您可能也會載入此處的指令碼 (.ps1) 檔案。 這些檔案會在根模組的內容中執行。 （這相當於來源中的根模組的指令碼的點。）|
|FunctionsToExport<br /><br /> 輸入：String|'*'|指定模組匯出 （允許字元的萬用字元） 的函式，呼叫端的工作階段狀態。 根據預設，會匯出所有函式。 您可以使用此金鑰來限制模組匯出的函式。<br /><br /> 呼叫者工作階段狀態可以是全域的工作階段狀態，或在巢狀模組，另一個模組的工作階段狀態。 當鏈結巢狀的模組，所有巢狀模組所匯出的函式會匯出全域工作階段狀態，除非使用 FunctionsToExport 金鑰鏈結中的模組會限制的函式。<br /><br /> 如果資訊清單也會匯出函式的別名，此金鑰可以移除 AliasesToExport 機碼中的函式會列出其別名，但此機碼不能加入清單的函式的別名。|
|CmdletsToExport<br /><br /> 輸入：String|'*'|指定模組匯出 （允許字元的萬用字元） 的 cmdlet。 根據預設，會匯出所有的 cmdlet。 您可以使用此金鑰來限制模組匯出的 cmdlet。<br /><br /> 呼叫者工作階段狀態可以是全域的工作階段狀態，或在巢狀模組，另一個模組的工作階段狀態。 時您會將巢狀的模組的鏈結，巢狀模組所匯出的所有 cmdlet 會最終都匯出全域工作階段狀態除非鏈結中的模組會限制使用 CmdletsToExport 金鑰的 cmdlet。<br /><br /> 如果資訊清單也會匯出別名的 cmdlet，此金鑰可以移除 AliasesToExport 機碼中的 cmdlet 會列出其別名，但這個機碼無法將 cmdlet 別名加入至清單。|
|VariablesToExport<br /><br /> 輸入：String|'*'|指定呼叫端的工作階段狀態模組匯出 （允許字元的萬用字元） 的變數。 根據預設，會匯出所有的變數。 您可以使用此金鑰來限制模組匯出的變數。<br /><br /> 呼叫者工作階段狀態可以是全域的工作階段狀態，或在巢狀模組，另一個模組的工作階段狀態。 當您鏈結巢狀的模組時，巢狀模組所匯出的所有變數會都匯出全域工作階段狀態，除非鏈結中的模組使用 VariablesToExport 金鑰限制變數。<br /><br /> 如果資訊清單也會匯出別名的變數，此金鑰可以 AliasesToExport 索引鍵中移除列出其別名的變數，但這個機碼不能將變數的別名新增到清單。|
|AliasesToExport<br /><br /> 輸入：String|'*'|指定呼叫端的工作階段狀態模組匯出 （允許字元的萬用字元） 的別名。 根據預設，會匯出所有的別名。 您可以使用此金鑰來限制模組匯出的別名。<br /><br /> 呼叫者工作階段狀態可以是全域的工作階段狀態，或在巢狀模組，另一個模組的工作階段狀態。 時您會將巢狀的模組的鏈結，巢狀模組所匯出的所有別名會最終都匯出全域工作階段狀態除非鏈結中的模組會限制使用 AliasesToExport 索引鍵的別名。|
|ModuleList<br /><br /> 類型: [字串 []]|@()|指定此模組會封裝的所有模組。 這些模組可以依名稱 （以逗號分隔字串） 或雜湊表輸入模組名稱和 GUID 的索引鍵。 雜湊表也可以有選擇性的 ModuleVersion 索引鍵。 ModuleList 索引鍵被設計來做為模組詳細目錄。 這些模組不會自動處理。|
|檔案清單<br /><br /> 類型: [字串 []]|@()|此模組所隨附的所有檔案的清單。 為 ModuleList，FileList 可以協助您為 [清查] 清單中，與否則不會處理。|
|PrivateData<br /><br /> 類型: [object]|' '|指定要傳遞至根模組的 RootModule/ModuleToProcess 索引鍵所指定的任何私用資料。|
|HelpInfoURI<br /><br /> 型別： 字串|' '|此模組 HelpInfo URI。|
|DefaultCommandPrefix<br /><br /> 型別： 字串|' '|此模組中，匯出命令的預設前置詞。 覆寫預設前置詞使用`Import-Module`-前置詞。|

## <a name="sample-module-manifest"></a>範例模組資訊清單

下列範例模組資訊清單會顯示模組資訊清單中的索引鍵和預設值。 此範例中，利用建立`New-ModuleManifest`指令程式在 Windows PowerShell 3.0。 在建立多個模組時，您可以使用這個指令程式來建立可修改不同的模組資訊清單範本。

```powershell
#
# Module manifest for module 'myManifest'
#
# Generated by: User01
#
# Generated on: 1/24/2012
#

@{

# Script module or binary module file associated with this manifest
#RootModule = ''

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = 'd0a9150d-b6a4-4b17-a325-e3a24fed0aa9'

# Author of this module
Author = 'User01'

# Company or vendor of this module
CompanyName = 'Unknown'

# Copyright statement for this module
Copyright = '(c) 2012 User01. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the Windows PowerShell engine required by this module
# PowerShellVersion = ''

# Name of the Windows PowerShell host required by this module
# PowerShellHostName = ''

# Minimum version of the Windows PowerShell host required by this module
# PowerShellHostVersion = ''

# Minimum version of the .NET Framework required by this module
# DotNetFrameworkVersion = ''

# Minimum version of the common language runtime (CLR) required by this module
# CLRVersion = ''

# Processor architecture (None, X86, Amd64) required by this module
# ProcessorArchitecture = ''

# Modules that must be imported into the global environment prior to importing this module
# RequiredModules = @()

# Assemblies that must be loaded prior to importing this module
# RequiredAssemblies = @()

# Script files (.ps1) that are run in the caller's environment prior to importing this module
# ScriptsToProcess = @()

# Type files (.ps1xml) to be loaded when importing this module
# TypesToProcess = @()

# Format files (.ps1xml) to be loaded when importing this module
# FormatsToProcess = @()

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
# NestedModules = @()

# Functions to export from this module
FunctionsToExport = '*'

# Cmdlets to export from this module
CmdletsToExport = '*'

# Variables to export from this module
VariablesToExport = '*'

# Aliases to export from this module
AliasesToExport = '*'

# List of all modules packaged with this module
# ModuleList = @()

# List of all files packaged with this module
# FileList = @()

# Private data to pass to the module specified in RootModule/ModuleToProcess
# PrivateData = ''

# HelpInfo URI of this module
# HelpInfoURI = ''

# Default prefix for commands exported from this module. Override the default prefix using Import-Module -Prefix.
# DefaultCommandPrefix = ''

}

```

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell 模組](./writing-a-windows-powershell-module.md)
