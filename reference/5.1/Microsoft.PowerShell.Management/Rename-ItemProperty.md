---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/rename-itemproperty?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-ItemProperty
ms.openlocfilehash: 5cbd228f78da3bf7fa70a001391bc98f63085a73
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203552"
---
# Rename-ItemProperty

## 概要
重新命名項目的屬性。

## SYNTAX

### 路徑 (預設值)

```
Rename-ItemProperty [-Path] <String> [-Name] <String> [-NewName] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [<CommonParameters>]
```

### LiteralPath

```
Rename-ItemProperty -LiteralPath <String> [-Name] <String> [-NewName] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [<CommonParameters>]
```

## DESCRIPTION

`Rename-ItemProperty`Cmdlet 會變更指定之專案屬性的名稱。
屬性的值不會變更。
例如，您可以使用 `Rename-ItemProperty` 來變更登錄專案的名稱。

## 範例

### 範例 1︰重新命名登錄項目

此命令會將 "HKEY_LOCAL_MACHINE\Software\SmpApplication" 機碼中包含的 config 登錄專案重新命名為 "oldconfig"。

```powershell
Rename-ItemProperty -Path HKLM:\Software\SmpApplication -Name config -NewName oldconfig
```

## PARAMETERS

### -Credential

指定具有執行此動作權限的使用者帳戶。
預設為目前使用者。

輸入使用者名稱，例如 "User01" 或 "Domain01\User01"，或輸入 **PSCredential** 物件，例如 Cmdlet 所產生的物件 `Get-Credential` 。
若您輸入使用者名稱時，會提示您輸入密碼。

> [!WARNING]
> 與 Windows PowerShell 一起安裝的任何提供者皆不支援此參數。

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

強制 Cmdlet 在使用者無法以其他方式存取的物件上重新命名屬性。
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

僅指定 Cmdlet 會在其中作用的項目，不包含其他所有項目。
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

指定項目屬性的路徑。
與 **Path** 參數不同， **LiteralPath** 的值將完全依照其輸入值來使用。
沒有字元會被視為萬用字元。
如果路徑包含逸出字元，請將它括在單引號中。
單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。

```yaml
Type: System.String
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

指定要重新命名之屬性的目前名稱。

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

### -NewName

指定屬性的新名稱。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 2
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

指定要重新命名之項目的路徑。

```yaml
Type: System.String
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
如需詳細資訊，請參閱 [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md)。

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

### None，System.Management.Automation.PSCustomObject

如果您指定 *PassThru* 參數，這個 Cmdlet 會產生代表重新命名之項目屬性的 **PSCustomObject** 。
否則，此 Cmdlet 不會產生任何輸出。

## 注意

`Remove-ItemProperty` 的設計目的是要與任何提供者公開的資料搭配使用。 若要列出工作階段中可用的提供者，請輸入 `Get-PSProvider`。 如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

## 相關連結

[Clear-ItemProperty](Clear-ItemProperty.md)

[Copy-ItemProperty](Copy-ItemProperty.md)

[Get-ItemProperty](Get-ItemProperty.md)

[Move-ItemProperty](Move-ItemProperty.md)

[New-ItemProperty](New-ItemProperty.md)

[Remove-ItemProperty](Remove-ItemProperty.md)

[Rename-Item](Rename-Item.md)

[Set-ItemProperty](Set-ItemProperty.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)
