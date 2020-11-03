---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/remove-cimsession?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-CimSession
ms.openlocfilehash: eae279aa9c5d3a99a9a522254c5b792970f74297
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93205187"
---
# Remove-CimSession

## 概要
移除一或多個 CIM 會話。

## SYNTAX

### CimSessionSet (預設) 

```
Remove-CimSession [-CimSession] <CimSession[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ComputerNameSet

```
Remove-CimSession [-ComputerName] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### SessionIdSet

```
Remove-CimSession [-Id] <UInt32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceIdSet

```
Remove-CimSession -InstanceId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### NameSet

```
Remove-CimSession -Name <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

此 `Remove-CimSession` Cmdlet 會從本機 PowerShell 會話中移除一個或多個 CIM 會話物件。

## 範例

### 範例1：移除所有 CIM 會話

此範例會使用 [CimSession 指令程式](Get-CimSession.md) 來抓取本機電腦上所有可用的 CIM 會話，然後使用來移除它們 `Remove-CimSession` 。

```powershell
Get-CimSession | Remove-CimSession
```

### 範例2：移除特定的 CIM 會話

此範例會移除 **識別碼** 值為5的 CIM 會話。

```powershell
Remove-CimSession -Id 5
```

### 範例3：使用 WhatIf 參數顯示要移除的 CIM 會話清單

此範例會使用一般參數 **WhatIf** 來指定不應完成移除，但只會輸出完成時所發生的情況。

```powershell
Remove-CimSession -Name a* -WhatIf
```

## PARAMETERS

### -CimSession

指定要關閉之 CIM 會話的會話物件。

輸入包含 CIM 會話的變數，或輸入可建立或取得 CIM 會話的命令，例如 [`New-CimSession`](New-CimSession.md) 或 [`Get-CimSession`](Get-CimSession.md) Cmdlet。
如需詳細資訊，請參閱 [about_CimSessions](../Microsoft.PowerShell.Core/About/about_CimSession.md)。

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimSessionSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -ComputerName

指定電腦名稱的陣列。 移除連接到指定電腦的會話。 您可以指定完整功能變數名稱 (FQDN) 或 NetBIOS 名稱。

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet
Aliases: CN, ServerName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Id

指定要移除之 CIM 會話的識別碼。 指定一或多個以逗號分隔的識別碼，或使用範圍運算子 (`..`) 來指定識別碼的範圍。 **識別碼** 是一個整數，可唯一識別目前 PowerShell 會話中的 CIM 會話。

如需範圍運算子的詳細資訊，請參閱 [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md)。

```yaml
Type: System.UInt32[]
Parameter Sets: SessionIdSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InstanceId

指定要移除之 CIM 會話的實例識別碼。 **InstanceId** 是唯一識別 CIM 會話 (GUID) 的全域唯一識別碼。 **InstanceId** 是唯一的，即使您有多個會話在 PowerShell 中執行也是一樣。

**Instanceid** 儲存在代表 CIM 會話之物件的 **instanceid** 屬性中。

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

指定要移除之 CIM 會話的易記名稱。 您可以使用萬用字元搭配此參數。

```yaml
Type: System.String[]
Parameter Sets: NameSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
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

顯示執行 Cmdlet 後會發生的情況。 Cmdlet 並不會執行。

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

### 無

此 Cmdlet 不接受任何輸入物件。

## 輸出

### System.Object

此 Cmdlet 會傳回包含 CIM 會話資訊的物件。

## 注意

## 相關連結

[Get-CimSession](Get-CimSession.md)

[New-CimSession](New-CimSession.md)

[about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)

