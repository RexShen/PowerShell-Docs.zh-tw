---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/08/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-modulemanifest?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-ModuleManifest
ms.openlocfilehash: 0924366eac2e6ee0e8a250db916d354ee6993cb7
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2020
ms.locfileid: "94892033"
---
# Update-ModuleManifest

## 概要
更新模組資訊清單檔案。

## SYNTAX

### 全部

```
Update-ModuleManifest [-Path] <String> [-NestedModules <Object[]>] [-Guid <Guid>] [-Author <String>]
 [-CompanyName <String>] [-Copyright <String>] [-RootModule <String>] [-ModuleVersion <Version>]
 [-Description <String>] [-ProcessorArchitecture <ProcessorArchitecture>]
 [-CompatiblePSEditions <String[]>] [-PowerShellVersion <Version>] [-ClrVersion <Version>]
 [-DotNetFrameworkVersion <Version>] [-PowerShellHostName <String>]
 [-PowerShellHostVersion <Version>] [-RequiredModules <Object[]>] [-TypesToProcess <String[]>]
 [-FormatsToProcess <String[]>] [-ScriptsToProcess <String[]>] [-RequiredAssemblies <String[]>]
 [-FileList <String[]>] [-ModuleList <Object[]>] [-FunctionsToExport <String[]>]
 [-AliasesToExport <String[]>] [-VariablesToExport <String[]>] [-CmdletsToExport <String[]>]
 [-DscResourcesToExport <String[]>] [-PrivateData <Hashtable>] [-Tags <String[]>]
 [-ProjectUri <Uri>] [-LicenseUri <Uri>] [-IconUri <Uri>] [-ReleaseNotes <String[]>]
 [-Prerelease <String>] [-HelpInfoUri <Uri>] [-PassThru] [-DefaultCommandPrefix <String>]
 [-ExternalModuleDependencies <String[]>] [-PackageManagementProviders <String[]>]
 [-RequireLicenseAcceptance] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Update-ModuleManifest`指令程式會更新) 檔 (的模組資訊清單 `.psd1` 。

## 範例

### 範例1：更新模組資訊清單

此範例會更新現有的模組資訊清單檔案。 展開用來將參數值傳遞給 `Update-ModuleManifest` 。 如需詳細資訊，請參閱 [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)。

```powershell
$Parms = @{
  Path = "C:\Test\TestManifest.psd1"
  Author = "TestUser1"
  CompanyName = "Contoso Corporation"
  Copyright = "(c) 2019 Contoso Corporation. All rights reserved."
}

Update-ModuleManifest @Parms
```

`$Parms` 是儲存 **路徑**、 **作者**、 **公司名稱** 和 **著作權** 之參數值的 splat。 `Update-ModuleManifest` 從取得參數值 `@Parms` ，並更新 **TestManifest.psd1** 的模組資訊清單。

## PARAMETERS

### -AliasesToExport

指定模組匯出的別名。 允許使用萬用字元。

使用此參數來限制模組匯出的別名。 **AliasesToExport** 可以從匯出的別名清單中移除別名，但不能將別名新增至清單。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -作者

指定模組作者。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ClrVersion

指定模組所需要的 Microsoft .NET Framework Common Language Runtime (CLR) 最低版本。

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CmdletsToExport

指定模組匯出的 Cmdlet。 允許使用萬用字元。

使用此參數來限制模組匯出的 Cmdlet。 **CmdletsToExport** 可以從匯出的 Cmdlet 清單中移除 Cmdlet，但是無法將 Cmdlet 新增至清單。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -公司名稱

指定建立模組的公司或廠商。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CompatiblePSEditions

指定模組的相容 **PSEditions** 。 如需 **PSEdition** 的相關資訊，請參閱 [具有相容 PowerShell 版本的模組](/powershell/scripting/gallery/concepts/module-psedition-support)。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Desktop, Core

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

在執行之前提示您確認 `Update-ModuleManifest` 。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -著作權

指定模組的著作權聲明。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DefaultCommandPrefix

指定預設的命令前置詞。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Description

指定模組的描述。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DotNetFrameworkVersion

指定模組所需要的 Microsoft .NET Framework 最低版本。

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DscResourcesToExport

指定模組匯出的 Desired State Configuration (DSC) 資源。 允許使用萬用字元。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ExternalModuleDependencies

指定外部模組相依性的陣列。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FileList

指定模組中所包含的所有項目。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FormatsToProcess

指定匯 `.ps1xml` 入模組時所執行)  (格式檔案。

當您匯入模組時，PowerShell 會 `Update-FormatData` 使用指定的檔案來執行 Cmdlet。
因為格式化檔案未設定範圍，所以它們會影響會話中所有的會話狀態。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FunctionsToExport

指定模組匯出的函式。 允許使用萬用字元。

使用此參數來限制模組匯出的函式。 **FunctionsToExport** 可以從匯出的別名清單中移除函式，但無法將函數新增至清單。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Guid

指定模組的唯一識別碼。 GUID 可用來區別具有相同名稱的模組。

```yaml
Type: System.Guid
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -HelpInfoUri

指定模組 **HELPINFO XML** 檔案的網際網路位址。 輸入以 **HTTP** 或 **HTTPS** 開頭 (URI) 的統一資源識別項。

**HELPINFO XML** 檔案支援 PowerShell 3.0 版中引進的可更新說明功能。 它包含模組可下載說明檔案位置的相關資訊，以及每個支援的地區設定最新說明檔案的版本號碼。

如需「可更新的說明」的詳細資訊，請參閱 [about_Updatable_Help](../Microsoft.PowerShell.Core/About/about_Updatable_Help.md)。
如需 **HELPINFO XML** 檔案的相關資訊，請參閱 [支援可更新](/powershell/scripting/developer/module/supporting-updatable-help)的說明。

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IconUri

指定模組的圖示 URL。 指定的圖示會顯示在該模組的資源庫網頁上。

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LicenseUri

指定模組的授權條款 URL。

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ModuleList

指定模組中包含的模組陣列。

輸入每個模組名稱做為字串或含 **ModuleName** 和 **ModuleVersion** 索引鍵的雜湊表。 雜湊表也可以有選用的 **GUID** 索引鍵。 您可以在參數值中結合字串和雜湊表。

這個索引鍵被設計來做為模組詳細目錄。 系統不會自動處理此索引鍵值中所列的模組。

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ModuleVersion

指定模組的版本。

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NestedModules

指定腳本模組 (`.psm1`) 和二進位模組， (`.dll`) 匯入模組的會話狀態。 **NestedModules** 機碼中的檔案會依它們在值中的列出循序執行。

輸入每個模組名稱做為字串或含 **ModuleName** 和 **ModuleVersion** 索引鍵的雜湊表。 雜湊表也可以有選用的 **GUID** 索引鍵。 您可以在參數值中結合字串和雜湊表。

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PackageManagementProviders

指定封裝管理提供者的陣列。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

傳回代表您正在使用之專案的物件。 依預設， `Update-ModuleManifest` 不會產生任何輸出。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

指定模組資訊清單的路徑和檔案名。 輸入副檔名為的路徑和檔案名 `.psd1` ，例如 `$PSHOME\Modules\MyModule\MyModule.psd1` 。

如果您指定現有檔案的路徑，則 `Update-ModuleManifest` 會在沒有警告的情況下取代檔案，除非檔案具有唯讀屬性。

資訊清單應該位於模組的目錄中，且資訊清單檔案名應該與模組目錄名稱相同，但是 `.psd1` 副檔名為。

您無法使用變數（例如 `$PSHOME` 或 `$HOME` ）來回應 **路徑** 參數值的提示。 如果要使用變數，請在命令中包含 **Path** 參數。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PowerShellHostName

指定模組所需之 PowerShell 主機程式的名稱。 輸入主機程式的名稱，例如 PowerShell ISE 主機或 ConsoleHost。 不允許使用萬用字元。

若要尋找主機程式的名稱，請在程式中輸入 `$Host.Name` 。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PowerShellHostVersion

指定適用于模組的 PowerShell 主機程式的最小版本。 輸入版本號碼，例如 1.1。

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PowerShellVersion

指定可使用此模組的 PowerShell 最低版本。 例如，您可以將3.0、4.0 或5.0 指定為此參數的值。

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -發行前版本

指出模組為發行前版本。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PrivateData

指定匯入模組時傳遞給模組的資料。

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProcessorArchitecture

指定模組需要的處理器架構。

此參數可接受的值為：

- Amd64
- Arm
- IA64
- MSIL
- 無 (未知或未指定) 
- X86

```yaml
Type: System.Reflection.ProcessorArchitecture
Parameter Sets: (All)
Aliases:
Accepted values: None, MSIL, X86, IA64, Amd64, Arm

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProjectUri

指定與這個專案相關之網頁的 URL。

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ReleaseNotes

指定字串陣列，其中包含您想要用於此版本腳本的版本資訊或批註。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequiredAssemblies

指定模組所需 () 檔案的元件 `.dll` 。 輸入組件檔案名稱。
PowerShell 會在更新類型或格式、匯入嵌套模組，或匯入在 **RootModule** 索引鍵值中指定的模組檔案之前，先載入指定的元件。

使用這個參數來指定模組所需的所有元件，包括必須載入的元件，以更新 **FormatsToProcess** 或 **TypesToProcess** 索引鍵中列出的任何格式或類型檔案，即使這些元件也在 **NestedModules** 索引鍵中列為二進位模組。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequiredModules

指定必須在全域工作階段狀態的模組。 如果必要的模組不在全域會話狀態中，則 PowerShell 會將它們匯入。 如果無法使用必要的模組，則 `Import-Module` 命令會失敗。

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequireLicenseAcceptance

指定模組需要接受授權。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RootModule

指定模組的主要或根檔案。 輸入腳本 (的檔案名 `.ps1`) 、腳本模組 (`.psm1`) 、模組資訊清單 () `.psd1` 、元件 () 、 `.dll` Cmdlet 定義 XML 檔案 (`.cdxml`) 或工作流程 (`.xaml`) 。 匯入模組時，從根模組檔案匯出的成員會匯入呼叫者工作階段狀態。

如果模組有資訊清單檔案，但 **RootModule** 索引鍵中沒有指定根檔案，資訊清單會變成模組的主要檔案。 而且，模組會變成資訊清單模組 (ModuleType = 資訊清單) 。

若要從 `.psm1` 具有資訊清單之模組中的或檔案匯出成員 `.dll` ，則必須在資訊清單中的 **RootModule** 或 **NestedModules** 索引鍵的值中指定這些檔案的名稱。 否則，不會匯出其成員。

在 PowerShell 2.0 中，此機碼稱為 **ModuleToProcess**。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptsToProcess

指定匯 `.ps1` 入模組時，在呼叫者會話狀態中執行的腳本 () 檔。
您可以使用這些指令碼來準備環境，就像您使用登入指令碼一般。

如果要指定在模組工作階段狀態中執行的指令碼，請使用 **NestedModules** 索引鍵。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Tags

指定標記的陣列。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypesToProcess

指定匯入模組時要執行的類型檔案 (`.ps1xml`) 。

當您匯入模組時，PowerShell 會 `Update-TypeData` 使用指定的檔案來執行 Cmdlet。
因為類型檔案未設定範圍，所以它們會影響會話中所有的會話狀態。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -VariablesToExport

指定模組匯出的變數。 允許使用萬用字元。

使用此參數來限制模組匯出的變數。 **VariablesToExport** 可以從匯出的變數清單中移除變數，但它無法將變數新增至清單。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

顯示執行時所發生 `Update-ModuleManifest` 的情況。 不會執行此 Cmdlet。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.String

## 輸出

### System.Object

## 注意

> [!IMPORTANT]
> 從2020年4月起，PowerShell 資源庫不再支援傳輸層安全性 (TLS) 1.0 和1.1 版。 如果您不是使用 TLS 1.2 或更高版本，當您嘗試存取 PowerShell 資源庫時，將會收到錯誤。 使用下列命令，以確保您使用的是 TLS 1.2：
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> 如需詳細資訊，請參閱 PowerShell blog 中的 [公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) 。

## 相關連結
