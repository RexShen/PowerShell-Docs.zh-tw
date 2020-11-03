---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-itemproperty?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-ItemProperty
ms.openlocfilehash: b1ee17e09a85c7f8afd3b41e7f9fb8b8dd5f019e
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201771"
---
# New-ItemProperty

## 概要
建立項目的新屬性，並設定其值。

## SYNTAX

### 路徑 (預設值)

```
New-ItemProperty [-Path] <String[]> [-Name] <String> [-PropertyType <String>] [-Value <Object>] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### LiteralPath

```
New-ItemProperty -LiteralPath <String[]> [-Name] <String> [-PropertyType <String>] [-Value <Object>] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`New-ItemProperty`Cmdlet 會為指定的專案建立新的屬性，並設定其值。
一般而言，這個 Cmdlet 是用來建立新的登錄值，因為登錄值是登錄機碼項目的屬性。

這個 Cmdlet 並不會將屬性新增到物件。

- 若要將屬性加入至物件的實例，請使用 `Add-Member` Cmdlet。
- 若要將屬性新增到特定類型的所有物件，請修改 Types.ps1的 xml 檔。

## 範例

### 範例1：新增登錄專案

此命令會將新的登錄專案 "NoOfEmployees" 新增至 "HKLM： \ Software hive" 的 "MyCompany" 機碼。

第一個命令使用 **path** 參數來指定 "MyCompany" 登錄機碼的路徑。
它會使用 **name** 參數來指定專案的名稱，並使用 **Value** 參數來指定其值。

第二個命令會使用 `Get-ItemProperty` Cmdlet 來查看新的登錄專案。

```powershell
New-ItemProperty -Path "HKLM:\Software\MyCompany" -Name "NoOfEmployees" -Value 822
Get-ItemProperty "HKLM:\Software\MyCompany"
```

```output
PSPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software\mycompany
PSParentPath  : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software
PSChildName   : mycompany
PSDrive       : HKLM
PSProvider    : Microsoft.PowerShell.Core\Registry
NoOfLocations : 2
NoOfEmployees : 822
```

### 範例2：將登錄專案新增至機碼

這個命令會將新登錄項目新增到登錄機碼。
為了指定索引鍵，它會使用管線運算子 (`|`) 將代表金鑰的物件傳送至 `New-ItemProperty` 。

命令的第一個部分會使用 `Get-Item` Cmdlet 來取得 "MyCompany" 登錄機碼。
管線運算子會將命令的結果傳送至 `New-ItemProperty` ，這會將新的登錄專案 ( "NoOfLocations" ) ，並將其值 (3) 新增至 "MyCompany" 索引鍵。

```powershell
Get-Item -Path "HKLM:\Software\MyCompany" | New-ItemProperty -Name NoOfLocations -Value 3
```

此命令的運作方式是因為 PowerShell 的參數系結功能會將傳回的 `RegistryKey` 物件路徑 `Get-Item` 與的 **LiteralPath** 參數產生關聯 `New-ItemProperty` 。 如需詳細資訊，請參閱 [about_Pipelines](../Microsoft.PowerShell.Core/About/about_pipelines.md)。

### 範例3：使用 Here-String 在登錄中建立 MultiString 值

此範例會使用此處的字串來建立 MultiString 值。

```powershell
$newValue = New-ItemProperty -Path "HKLM:\SOFTWARE\ContosoCompany\" -Name 'HereString' -PropertyType MultiString -Value @"
This is text which contains newlines
It can also contain "quoted" strings
"@
$newValue.multistring
```

```output
This is text which contains newlines
It can also contain "quoted" strings
```

### 範例4：使用陣列在登錄中建立 MultiString 值

此範例顯示如何使用值的陣列來建立 `MultiString` 值。

```powershell
$newValue = New-ItemProperty -Path "HKLM:\SOFTWARE\ContosoCompany\" -Name 'MultiString' -PropertyType MultiString -Value ('a','b','c')
$newValue.multistring[0]
```

```output
a
```

## PARAMETERS

### -Credential

> [!NOTE]
> 使用 PowerShell 安裝的任何提供者都不支援此參數。
> 若要模擬其他使用者，或在執行此 Cmdlet 時提高認證，請使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Exclude

以字串陣列指定此 Cmdlet 在作業中排除的專案。 此參數的值會限定 **Path** 參數。 輸入路徑元素或模式，例如 `*.txt`。 允許使用萬用字元。 只有當命令包含專案的內容（例如）時，才會使用 **Exclude** 參數， `C:\Windows\*` 其中的萬用字元會指定目錄的內容 `C:\Windows` 。

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

### -Filter

指定要限定 **路徑** 參數的篩選準則。 [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md)提供者是唯一支援使用篩選器的已安裝 PowerShell 提供者。 您可以在 [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)中找到 **檔案系統** 篩選器語言的語法。
篩選比其他參數更有效率，因為提供者會在 Cmdlet 取得物件時套用篩選，而不是在抓取物件之後，讓 PowerShell 篩選物件。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Force

強制 Cmdlet 在使用者無法以其他方式存取的物件上建立屬性。
實作會依提供者而異。
如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Include

以字串陣列指定此 Cmdlet 在作業中納入的項目。 此參數的值會限定 **Path** 參數。 輸入路徑元素或模式，例如 `"*.txt"`。 允許使用萬用字元。 **Include** 參數只有當命令包含專案內容時才有效，例如 `C:\Windows\*` ，其中的萬用字元會指定目錄的內容 `C:\Windows` 。

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

### -LiteralPath

指定一個或多個位置的路徑。 **LiteralPath** 的值將完全依照其輸入值來使用。 沒有字元會被視為萬用字元。 如果路徑包含逸出字元，請將它括在單引號中。 單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。

如需詳細資訊，請參閱 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

指定新屬性的名稱。
如果屬性是登錄項目，這個參數便會指定該項目的名稱。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

指定專案的路徑。
允許使用萬用字元。
此參數會識別這個 Cmdlet 要加入新屬性的專案。

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -PropertyType

指定此 Cmdlet 所新增的屬性類型。
此參數可接受的值為：

- **字串** ：指定以 null 終止的字串。 相當於 **REG_SZ** 。
- **ExpandString** ：指定以 null 終止的字串，其中包含在抓取值時展開之環境變數的未展開參考。 相當於 **REG_EXPAND_SZ** 。
- **Binary** ：以任何形式指定二進位資料。 相當於 **REG_BINARY** 。
- **DWord** ：指定32位的二進位數。 相當於 **REG_DWORD** 。
- **MultiString** ：指定以 null 終止的字串陣列（以兩個 null 字元結束）。
  相當於 **REG_MULTI_SZ** 。
- **Qword** ：指定64位的二進位數。 相當於 **REG_QWORD** 。
- **未知** ：表示不支援的登錄資料類型，例如 **REG_RESOURCE_LIST** 。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Type

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Value

指定屬性值。
如果屬性是登錄項目，這個參數便會指定該項目的值。

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Confirm

在執行 Cmdlet 前提示您確認。

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

### -WhatIf

顯示執行 Cmdlet 後會發生的情況。
Cmdlet 並不會執行。

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

這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。 如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 輸入

### 無

您無法使用管線傳送輸入至此 Cmdlet。

## 輸出

### System.Management.Automation.PSCustomObject

`New-ItemProperty` 傳回包含新屬性的自訂物件。

## 注意

`New-ItemProperty` 的設計目的是要與任何提供者公開的資料搭配使用。 若要列出工作階段中可用的提供者，請輸入 `Get-PSProvider`。 如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

## 相關連結

[Clear-ItemProperty](Clear-ItemProperty.md)

[Copy-ItemProperty](Copy-ItemProperty.md)

[Get-ItemProperty](Get-ItemProperty.md)

[Move-ItemProperty](Move-ItemProperty.md)

[Remove-ItemProperty](Remove-ItemProperty.md)

[Rename-ItemProperty](Rename-ItemProperty.md)

[Set-ItemProperty](Set-ItemProperty.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)
