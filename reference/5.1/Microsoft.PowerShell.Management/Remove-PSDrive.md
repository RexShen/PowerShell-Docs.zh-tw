---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-psdrive?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSDrive
ms.openlocfilehash: 4b9b466be3d52877056b948e4cc373991784416a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203556"
---
# Remove-PSDrive

## 概要
刪除暫存的 PowerShell 磁片磁碟機，並中斷對應網路磁碟機機的連線。

## SYNTAX

### Name (預設值)

```
Remove-PSDrive [-Name] <String[]> [-PSProvider <String[]>] [-Scope <String>] [-Force] [-WhatIf] [-Confirm]
 [-UseTransaction] [<CommonParameters>]
```

### LiteralName

```
Remove-PSDrive [-LiteralName] <String[]> [-PSProvider <String[]>] [-Scope <String>] [-Force] [-WhatIf]
 [-Confirm] [-UseTransaction] [<CommonParameters>]
```

## DESCRIPTION

此 `Remove-PSDrive` Cmdlet 會刪除使用 Cmdlet 所建立的暫存 PowerShell 磁片磁碟機 `New-PSDrive` 。

從 Windows PowerShell 3.0 開始， `Remove-PSDrive` 也會中斷對應網路磁碟機機的連接，包括（但不限於）使用的參數建立的磁片磁碟機 `Persist` `New-PSDrive` 。

`Remove-PSDrive` 無法刪除 Windows 實體或邏輯磁碟機。

從 Windows PowerShell 3.0 開始，當外部磁片磁碟機連接到電腦時，PowerShell 會自動將 New-psdrive 新增至代表新磁片磁碟機的檔案系統。
您不需要重新開機 PowerShell。
同樣地，當外部磁片磁碟機與電腦中斷連線時，PowerShell 會自動刪除代表已移除之磁片磁碟機的 New-psdrive。

## 範例

### 範例 1︰移除檔案系統磁碟機

此命令會移除名為"smp" 的暫時檔案系統磁碟機。

```powershell
Remove-PSDrive -Name smp
```

### 範例 2：移除對應的網路磁碟機

此命令會使用 `Remove-PSDrive` 來中斷連接 X：和 S：對應的網路磁碟機機。

```powershell
Get-PSDrive X, S | Remove-PSDrive
```

## PARAMETERS

### -Force

移除目前的 PowerShell 磁片磁碟機。

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

### -LiteralName

指定磁碟機的名稱。

**LiteralName** 的值將完全依照其輸入值來使用。
沒有字元會被視為萬用字元。
如果名稱包含逸出字元，請將它括在單引號中 (')。
單引號指示 PowerShell 不要將任何字元解釋為 escape 序列。

```yaml
Type: System.String[]
Parameter Sets: LiteralName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

指定要移除之磁碟機的名稱。
不要在磁碟機名稱後面輸入冒號 (:)。

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -PSProvider

指定 **PSProvider** 物件的陣列。
此 Cmdlet 會移除並中斷連接與指定 PowerShell 提供者相關聯的所有磁片磁碟機。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Scope

指定磁碟機的範圍。
此參數可接受的值為： Global、Local 和 Script，或相對於目前範圍的數位。 範圍編號0至範圍數目。 目前的範圍號碼為0，而其父系為1。
如需詳細資訊，請參閱 [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
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

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 輸入

### System.Management.Automation.PSDriveInfo

您可以使用管線將磁片磁碟機物件（例如 `Get-PSDrive` Cmdlet）傳送至 `Remove-PSDrive` Cmdlet。

## 輸出

### 無

此 Cmdlet 不會傳回任何輸出。

## 注意

- 此 `Remove-PSDrive` Cmdlet 是針對與任何 PowerShell 提供者公開的資料搭配使用所設計。 若要列出會話中的提供者，請使用 `Get-PSProvider` Cmdlet。 如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

## 相關連結

[Get-PSDrive](Get-PSDrive.md)

[New-PSDrive](New-PSDrive.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)
