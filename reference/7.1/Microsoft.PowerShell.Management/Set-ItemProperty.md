---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-itemproperty?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-ItemProperty
ms.openlocfilehash: 26f26ff48d0c2d68c9c814da192ce1846edfe9b1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202060"
---
# Set-ItemProperty

## 概要
建立或變更項目屬性的值。

## SYNTAX

### propertyValuePathSet (預設值)

```
Set-ItemProperty [-Path] <String[]> [-Name] <String> [-Value] <Object> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-Type <RegistryValueKind>] [<CommonParameters>]
```

### propertyPSObjectPathSet

```
Set-ItemProperty [-Path] <String[]> -InputObject <PSObject> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-Type <RegistryValueKind>] [<CommonParameters>]
```

### propertyValueLiteralPathSet

```
Set-ItemProperty -LiteralPath <String[]> [-Name] <String> [-Value] <Object> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-Type <RegistryValueKind>] [<CommonParameters>]
```

### propertyPSObjectLiteralPathSet

```
Set-ItemProperty -LiteralPath <String[]> -InputObject <PSObject> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-Type <RegistryValueKind>] [<CommonParameters>]
```

## DESCRIPTION

`Set-ItemProperty`Cmdlet 會變更指定專案的屬性值。
您可以使用此 Cmdlet 來建立或變更項目的屬性。
例如，您可以使用將 `Set-ItemProperty` file 物件的 **IsReadOnly** 屬性值設定為 `$True` 。

您也可以使用 `Set-ItemProperty` 來建立及變更登錄值和資料。
例如，您可以將新登錄項目新增到機碼並建立或變更其值。

## 範例

### 範例1：設定檔案的屬性

此命令會將 "final.doc" 檔案的 **IsReadOnly** 屬性值設定為 "true"。
它會使用 **路徑** 來指定檔案、指定屬性名稱的 **名稱** ，以及指定新值的 **值** 參數。

檔案是 **FileInfo** 物件，而 **IsReadOnly** 只是它的其中一個屬性。
若要查看所有屬性，請輸入 `Get-Item C:\GroupFiles\final.doc | Get-Member -MemberType
Property` 。

`$true`自動變數代表值 "TRUE"。
如需詳細資訊，請參閱 [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)。

```powershell
Set-ItemProperty -Path C:\GroupFiles\final.doc -Name IsReadOnly -Value $true
```

### 範例2：建立登錄專案和值

此範例示範如何使用 `Set-ItemProperty` 建立新的登錄專案，並將值指派給專案。 它會在機碼中的 "ContosoCompany" 機碼中建立 "NoOfEmployees" 專案 `HKLM\Software` ，並將其值設定為823。

由於登錄專案被視為登錄機碼的屬性，也就是用 `Set-ItemProperty` 來建立登錄專案，以及建立和變更其值的專案。

```powershell
Set-ItemProperty -Path "HKLM:\Software\ContosoCompany" -Name "NoOfEmployees" -Value 823
Get-ItemProperty -Path "HKLM:\Software\ContosoCompany"
```

```Output
PSPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software\contosocompany
PSParentPath  : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software
PSChildName   : contosocompany
PSDrive       : HKLM
PSProvider    : Microsoft.PowerShell.Core\Registry
NoOfLocations : 2
NoOfEmployees : 823
```

```powershell
Set-ItemProperty -Path "HKLM:\Software\ContosoCompany" -Name "NoOfEmployees" -Value 824
Get-ItemProperty -Path "HKLM:\Software\ContosoCompany"
```

```Output
PSPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software\contosocompany
PSParentPath  : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software
PSChildName   : contosocompany
PSDrive       : HKLM
PSProvider    : Microsoft.PowerShell.Core\Registry
NoOfLocations : 2
NoOfEmployees : 824
```

第一個命令會建立登錄專案。
它會使用 **path** 來指定 `HKLM:` 磁片磁碟機的路徑和 "software\mycompany 機" 機碼。
命令使用 **Name** 來指定專案名稱和 **值** ，以指定值。

第二個命令會使用 `Get-ItemProperty` Cmdlet 來查看新的登錄專案。
如果您使用 `Get-Item` 或 `Get-ChildItem` Cmdlet，這些專案就不會出現，因為它們是索引鍵的屬性，而不是專案或子專案的屬性。

第三個命令會將 **NoOfEmployees** 專案的值變更為824。

您也可以使用 `New-ItemProperty` Cmdlet 來建立登錄專案及其值，然後使用 `Set-ItemProperty` 來變更值。

如需磁片磁碟機的詳細資訊 `HKLM:` ，請輸入 `Get-Help Get-PSDrive` 。
如需有關如何使用 PowerShell 來管理登錄的詳細資訊，請輸入 `Get-Help Registry` 。

### 範例3：使用管線修改專案

這些命令示範如何使用管線運算子 () 將 `|` 專案傳送至其中 `Set-ItemProperty` 。

命令的第一個部分會使用 `Get-ChildItem` 來取得代表 "Weekly.txt" 檔案的物件。 此命令會使用管線運算子將檔案物件傳送至 `Set-ItemProperty` 。
`Set-ItemProperty`命令使用 **Name** 和 **Value** 參數指定屬性及其新值。

此命令相當於使用 **InputObject** 參數來指定取得的物件 `Get-ChildItem` 。

```powershell
Get-ChildItem weekly.txt | Set-ItemProperty -Name IsReadOnly -Value $True
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

強制 Cmdlet 在使用者無法以其他方式存取的專案上設定屬性。
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

### -InputObject

指定具有此 Cmdlet 所變更屬性的物件。
輸入包含物件的變數，或輸入可取得物件的命令。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: propertyPSObjectPathSet, propertyPSObjectLiteralPathSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -LiteralPath

指定一個或多個位置的路徑。 **LiteralPath** 的值將完全依照其輸入值來使用。 沒有字元會被視為萬用字元。 如果路徑包含逸出字元，請將它括在單引號中。 單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。

如需詳細資訊，請參閱 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。

```yaml
Type: System.String[]
Parameter Sets: propertyValueLiteralPathSet, propertyPSObjectLiteralPathSet
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

指定屬性的名稱。

```yaml
Type: System.String
Parameter Sets: propertyValuePathSet, propertyValueLiteralPathSet
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

傳回代表項目屬性的物件。
根據預設，此 Cmdlet 不會產生任何輸出。

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

使用要修改的屬性，指定專案的路徑。
允許使用萬用字元。

```yaml
Type: System.String[]
Parameter Sets: propertyValuePathSet, propertyPSObjectPathSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Type

**類型** 是登錄提供者新增至 Cmdlet 的動態參數 `Set-ItemProperty` 。
這個參數只能在登錄磁片磁碟機中運作。

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
Type: Microsoft.Win32.RegistryValueKind
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Value

指定屬性的值。

```yaml
Type: System.Object
Parameter Sets: propertyValuePathSet, propertyValueLiteralPathSet
Aliases:

Required: True
Position: 2
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

### System.Management.Automation.PSObject

您可以透過管道將物件傳送至此 Cmdlet。

## 輸出

### None，System.Management.Automation.PSCustomObject

如果您指定 **PassThru** 參數，此 Cmdlet 會產生代表已變更之專案及其新屬性值的 **PSCustomObject** 物件。
否則，此 Cmdlet 不會產生任何輸出。

## 注意

`Set-ItemProperty` 的設計目的是要與任何提供者公開的資料搭配使用。 若要列出工作階段中可用的提供者，請輸入 `Get-PSProvider`。 如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

## 相關連結

[Clear-ItemProperty](Clear-ItemProperty.md)

[Copy-ItemProperty](Copy-ItemProperty.md)

[Get-ItemProperty](Get-ItemProperty.md)

[Move-ItemProperty](Move-ItemProperty.md)

[New-ItemProperty](New-ItemProperty.md)

[Remove-ItemProperty](Remove-ItemProperty.md)

[Rename-ItemProperty](Rename-ItemProperty.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

