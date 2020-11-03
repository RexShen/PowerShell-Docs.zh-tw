---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-itemproperty?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-ItemProperty
ms.openlocfilehash: 9ae9c0e7c17a6a63da5487cce138ddce129b975b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203560"
---
# Remove-ItemProperty

## 概要
刪除項目的屬性及其值。

## SYNTAX

### 路徑 (預設值)

```
Remove-ItemProperty [-Path] <String[]> [-Name] <String[]> [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction] [<CommonParameters>]
```

### LiteralPath

```
Remove-ItemProperty -LiteralPath <String[]> [-Name] <String[]> [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [-UseTransaction] [<CommonParameters>]
```

## DESCRIPTION

`Remove-ItemProperty`Cmdlet 會從專案中刪除屬性和其值。
您可以使用它來刪除登錄值和它們所儲存的資料。

## 範例

### 範例 1：刪除登錄值

此命令會從 "HKEY_LOCAL_MACHINE\Software" 登錄機碼的 "SmpApplication" 子機碼中刪除 "SmpProperty" 登錄值及其資料。

因為命令是從檔案系統磁片磁碟機 () 發出 `PS C:\>` ，所以它會包含 "SmpApplication" 子機碼的完整路徑，包括磁片磁碟機、 `HKLM:` 和 "Software" 機碼。

它會使用 **Name** 參數來識別要刪除的登錄值。

```powershell
Remove-ItemProperty -Path "HKLM:\Software\SmpApplication" -Name "SmpProperty"
```

### 範例 2︰從 HKCU 位置刪除登錄值

這些命令會從 "HKEY_CURRENT_USER\Software\MyCompany" 的 "MyApp" 子機碼中刪除 "Options" 登錄值及其資料。

第一個命令會使用 `Set-Location` Cmdlet 將目前的位置變更為 **HKEY_CURRENT_USER** 磁片磁碟機 (`HKCU:`) 和 "Software\MyCompany\MyApp" 子機碼。

第二個命令會使用 `Remove-ItemProperty` 從 "MyApp" 子機碼移除 "Options" 登錄值及其資料。
因為 **路徑** 是必要的，所以命令會使用點 ( '. ') ，表示目前的位置。
它會使用 **Name** 來指定要刪除的登錄值。
它會使用 **Confirm** 參數，在刪除值之前要求使用者提示。

```
PS C:\> Set-Location HKCU:\Software\MyCompany\MyApp
PS HKCU:\Software\MyCompany\MyApp> Remove-ItemProperty -Path . -Name "Options" -Confirm
```

### 範例 3︰使用管線移除登錄值

此命令會從 "HKLM\Software\MyCompany" 登錄機碼中刪除 "NoOfEmployees" 登錄值及其資料。

此命令會使用 `Get-Item` Cmdlet 來取得代表登錄機碼的專案。
它使用管線運算子 (`|`) 傳送物件至 `Remove-ItemProperty` 。
然後，它會使用的 **name** 參數 `Remove-ItemProperty` 來指定登錄值的名稱。

```powershell
Get-Item -Path HKLM:\Software\MyCompany | Remove-ItemProperty -Name NoOfEmployees
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

指定此 Cmdlet 省略的項目。
此參數的值會限定 **Path** 參數。
輸入路徑元素或模式，例如 "*.txt"。
允許使用萬用字元。

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

以提供者的格式或語言指定篩選。
此參數的值會限定 **Path** 參數。

篩選的語法 (包括是否使用萬用字元) 取決於提供者。
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

強制 Cmdlet 對使用者無法以其他方式存取的物件移除屬性。
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

以字串陣列指定此 Cmdlet 在作業中納入的項目。
此參數的值會限定 **Path** 參數。
輸入路徑元素或模式，例如 "*.txt"。
允許使用萬用字元。

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

指定屬性之目前位置的路徑。
與 **Path** 參數不同， **LiteralPath** 的值將完全依照其輸入值來使用。
沒有字元會被視為萬用字元。
如果路徑包含逸出字元，請將它括在單引號中。
單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

指定要移除的屬性名稱。
允許使用萬用字元。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Path

指定要移除其屬性的項目路徑。
允許使用萬用字元。

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -UseTransaction

將命令加入使用中交易。
只有交易為處理中狀態時，此參數才有效。
如需詳細資訊，請參閱 about_Transactions。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
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

### System.String

您可以使用管線將包含路徑 (但不是常值路徑) 的字串傳送至此 Cmdlet。

## 輸出

### 無

此 Cmdlet 不會傳回任何輸出。

## 注意

在 PowerShell 登錄提供者中，登錄值會被視為登錄機碼或子機碼的屬性。 您可以使用 **ItemProperty** Cmdlet 來管理這些值。

`Remove-ItemProperty` 的設計目的是要與任何提供者公開的資料搭配使用。 若要列出工作階段中可用的提供者，請輸入 `Get-PSProvider`。 如需詳細資訊，請參閱 about_Providers。

## 相關連結

[Get-Item](Get-Item.md)

[Clear-ItemProperty](Clear-ItemProperty.md)

[Copy-ItemProperty](Copy-ItemProperty.md)

[Get-ItemProperty](Get-ItemProperty.md)

[Move-ItemProperty](Move-ItemProperty.md)

[New-ItemProperty](New-ItemProperty.md)

[Remove-Item](Remove-Item.md)

[Rename-ItemProperty](Rename-ItemProperty.md)

[Set-ItemProperty](Set-ItemProperty.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)
