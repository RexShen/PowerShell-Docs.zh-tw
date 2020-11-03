---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 09/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-psrolecapabilityfile?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSRoleCapabilityFile
ms.openlocfilehash: 3dca5f922f31690bb78ccc610b4ed44b7423ca47
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202715"
---
# New-PSRoleCapabilityFile

## 概要
建立檔案，該檔案會定義要透過會話設定公開的一組功能。

## SYNTAX

```
New-PSRoleCapabilityFile [-Path] <String> [-Guid <Guid>] [-Author <String>] [-Description <String>]
 [-CompanyName <String>] [-Copyright <String>] [-ModulesToImport <Object[]>] [-VisibleAliases <String[]>]
 [-VisibleCmdlets <Object[]>] [-VisibleFunctions <Object[]>] [-VisibleExternalCommands <String[]>]
 [-VisibleProviders <String[]>] [-ScriptsToProcess <String[]>] [-AliasDefinitions <IDictionary[]>]
 [-FunctionDefinitions <IDictionary[]>] [-VariableDefinitions <Object>] [-EnvironmentVariables <IDictionary>]
 [-TypesToProcess <String[]>] [-FormatsToProcess <String[]>] [-AssembliesToLoad <String[]>]
 [<CommonParameters>]
```

## DESCRIPTION

此 `New-PSRoleCapabilityFile` Cmdlet 會建立一個檔案，該檔案會定義一組可透過會話設定檔公開的使用者功能。 這包括判斷使用者可以使用哪些 Cmdlet、函式和腳本。 功能檔案是人們可讀取的文字檔，其中包含會話設定屬性和值的雜湊表。 檔案的副檔名為 .psrc，且可供一個以上的會話設定使用。

的所有參數 `New-PSRoleCapabilityFile` 都是選擇性的，但 **Path** 參數除外，後者會指定檔案的檔案路徑。 如果您在執行 Cmdlet 時未包含參數，則會話設定檔中的對應索引鍵會被批註化，除非在參數描述中注明。 例如，如果您未包含 **AssembliesToLoad** 參數，則會將會話設定檔的該區段標記為批註。

若要在會話設定中使用角色功能檔案，請先將檔案放在有效 PowerShell 模組資料夾的 **RoleCapabilities** 子資料夾中。 然後，在 PowerShell 會話設定的 [ **RoleDefinitions** ] 欄位中依名稱參考檔案， (. .pssc) 檔。

此 Cmdlet 是在 Windows PowerShell 5.0 中引進。

## 範例

### 範例1：建立空白角色功能檔案

這個範例會建立新的角色功能檔案，該檔案會使用預設 (空白的) 值。 您稍後可以在文字編輯器中編輯檔案，以變更這些設定。

```powershell
New-PSRoleCapabilityFile -Path ".\ExampleFile.psrc"
```

### 範例2：建立角色功能檔案，讓使用者重新開機服務和任何 VDI 電腦

這個範例會建立一個範例角色功能檔案，讓使用者能夠重新開機符合特定名稱模式的服務和電腦。 名稱篩選是藉由將 **ValidatePattern** 參數設定為正則運算式來定義 `VDI\d+` 。

```powershell
$roleParameters = @{
    Path = ".\Maintenance.psrc"
    Author = "User01"
    CompanyName = "Fabrikam Corporation"
    Description = "This role enables users to restart any service and restart any VDI computer."
    ModulesToImport = "Microsoft.PowerShell.Core"
    VisibleCmdlets = "Restart-Service", @{
                      Name = "Restart-Computer"
                      Parameters = @{ Name = "ComputerName"; ValidatePattern = "VDI\d+" }
    }
}
New-PSRoleCapabilityFile @roleParameters
```

## PARAMETERS

### -AliasDefinitions

將指定的別名新增至使用角色功能檔案的會話。 輸入包含下列索引鍵的雜湊表：

- Name： 別名的名稱。 此為必要索引鍵。
- 值。 別名代表的命令。 此為必要索引鍵。
- 描述 描述別名的文字字串。 此為選擇性索引鍵。
- 選項。 別名選項。 此為選擇性索引鍵。 預設值為 None。 此參數可接受的值為： None、ReadOnly、常數、私用或 AllScope。

例如：`@{Name="hlp";Value="Get-Help";Description="Gets help";Options="ReadOnly"}`

```yaml
Type: System.Collections.IDictionary[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AssembliesToLoad

指定要載入至使用角色功能檔案之會話的元件。

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

### -作者

指定建立角色功能檔案的使用者。

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

### -公司名稱

識別建立角色功能檔案的公司。
預設值為 [未知]。

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

### -著作權

指定角色功能檔案的著作權。 如果您省略此參數，則會 `New-PSRoleCapabilityFile` 使用 **Author** 參數的值產生著作權語句。

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

指定角色功能檔案的描述。

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

### -EnvironmentVariables

為公開此角色功能檔案的會話指定環境變數。 輸入雜湊表，其中索引鍵為環境變數名稱，值為環境變數值。

例如：`EnvironmentVariables=@{TestShare="\\\\Server01\TestShare"}`

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FormatsToProcess

指定在使用角色功能檔案的會話中執行的格式化檔案 (. .ps1xml) 。 此參數的值必須是格式化檔案的完整路徑或絕對路徑。

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

### -FunctionDefinitions

將指定的函式加入至公開角色功能的會話。 輸入包含下列索引鍵的雜湊表：

- Name： 函數的名稱。 此為必要索引鍵。
- ScriptBlock. 函式主體。 輸入指令碼區塊。 此為必要索引鍵。
- 選項。 函式選項。 此為選擇性索引鍵。 預設值為 None。 此參數可接受的值包括：無、ReadOnly、常數、私用或 AllScope。

例如：

`@{Name="Get-PowerShellProcess";ScriptBlock={Get-Process PowerShell};Options="AllScope"}`

```yaml
Type: System.Collections.IDictionary[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Guid

指定角色功能檔案的唯一識別碼。 如果您省略此參數，則會產生檔案的 `New-PSRoleCapabilityFile` GUID。 若要在 PowerShell 中建立新的 GUID，請輸入 `[guid]::NewGuid()` 。

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

### -ModulesToImport

指定自動匯入至使用角色功能檔案之會話的模組。 根據預設，列出模組中的所有命令都是可見的。 搭配 **VisibleCmdlets** 或 **VisibleFunctions** 使用時，可以限制指定模組中可見的命令。

此參數的值中所使用的每個模組都可以用字串或雜湊表表示。 模組字串只包含模組的名稱。 模組雜湊表可包括 **ModuleName** 、 **ModuleVersion** 和 **GUID** 索引鍵。 只有 **ModuleName** 索引鍵是必要的。

例如，以下的值包含字串和雜湊表。 字串或雜湊表以任何順序組成的任何組合都是有效的。

`"TroubleshootingPack", @{ModuleName="PSDiagnostics"; ModuleVersion="1.0.0.0";GUID="c61d6278-02a3-4618-ae37-a524d40a7f44"}`

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

### -Path

指定角色功能檔案的路徑和檔案名。 檔案的副檔名必須是 `.psrc` 副檔名。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptsToProcess

指定要加入至使用角色功能檔案之會話的腳本。 輸入指令碼的路徑和檔案名稱。 此參數的值必須是指令檔名的完整路徑或絕對路徑。

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

指定要加入至使用角色功能檔案之會話的類型檔案 (. .ps1xml) 。 輸入類型檔案名。 此參數的值必須是類型檔案名的完整路徑或絕對路徑。

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

### -VariableDefinitions

指定要加入至使用角色功能檔案之會話的變數。 輸入包含下列索引鍵的雜湊表：

- Name： 變數的名稱。 此為必要索引鍵。
- 值。 變數值。 此為必要索引鍵。
- 選項。 變數選項。 此為選擇性索引鍵。 預設值為 None。 此參數可接受的值包括：無、ReadOnly、常數、私用或 AllScope。

例如：`@{Name="WarningPreference";Value="SilentlyContinue";Options="AllScope"}`

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Visiblealiase

將會話中的別名限制為此參數的值中指定的別名，以及您在 **AliasDefinition** 參數中定義的任何別名。 支援使用萬用字元。
根據預設，會話中會顯示所有由 PowerShell 引擎定義的別名，以及模組匯出的所有別名。

例如，若要將可用的別名限制為 gm 和 gcm，請使用此語法： `VisibleAliases="gcm", "gp"`

當角色功能檔案中包含任何 **可見** 的參數時，PowerShell 會 `Import-Module` 從會話中移除該 Cmdlet 和其 `ipmo` 別名。

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

### -VisibleCmdlets

將工作階段中的 Cmdlet 限制為此參數的值中指定的 Cmdlet。 支援萬用字元和模組限定名稱。

根據預設，會話中的模組會在會話中顯示所有 Cmdlet。 使用 **SessionType** 和 **ModulesToImport** 參數決定要在工作階段中匯入哪些模組和嵌入式管理單元。 如果 **ModulesToImport** 中沒有任何模組公開 Cmdlet，則會 `New-PSRoleCapabilityFile` 嘗試載入適當的模組。

當會話設定檔中包含任何 **可見** 的參數時，PowerShell 會 `Import-Module` 從會話中移除該 Cmdlet 和其 `ipmo` 別名。

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -了 visibleexternalcommands

將會話中可執行檔外部二進位檔、腳本和命令，限制為此參數的值中指定的二進位檔、腳本和命令。

依預設，在此會話中不會顯示任何外部命令。

當會話設定檔中包含任何 **可見** 的參數時，PowerShell 會 `Import-Module` 從會話中移除該 Cmdlet 和其 `ipmo` 別名。

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

### -VisibleFunctions

將會話中的函式限制為此參數的值中指定的函式，以及您在 **FunctionDefinitions** 參數中定義的任何函數。 支援使用萬用字元。

依預設，會話中的模組匯出的所有函式都會顯示在該會話中。 您可以使用 **SessionType** 和 **ModulesToImport** 參數來判斷要將哪些模組匯入到會話中。

當會話設定檔中包含任何 **可見** 的參數時，PowerShell 會 `Import-Module` 從會話中移除該 Cmdlet 和其 `ipmo` 別名。

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -VisibleProviders

將會話中的 PowerShell 提供者限制為此參數的值中指定的提供者。
支援使用萬用字元。

依預設，會話中的模組匯出的所有提供者都會顯示在會話中。 您可以使用 **SessionType** 和 **ModulesToImport** 參數來判斷要將哪些模組匯入到會話中。

當會話設定檔中包含任何 **可見** 的參數時，PowerShell 會 `Import-Module` 從會話中移除該 Cmdlet 和其 `ipmo` 別名。

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

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

## 輸出

## 注意

## 相關連結

[New-PSSessionConfigurationFile](New-PSSessionConfigurationFile.md)

[Get-PSSessionCapability](Get-PSSessionCapability.md)
