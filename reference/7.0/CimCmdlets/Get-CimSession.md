---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-cimsession?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimSession
ms.openlocfilehash: dbbbb352d1b3af8a0f05d2805fb42b7bb3ed27d3
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201656"
---
# Get-CimSession

## 概要
從目前的會話取得 CIM 會話物件。

## SYNTAX

### ComputerNameSet (預設值)

```
Get-CimSession [[-ComputerName] <String[]>] [<CommonParameters>]
```

### SessionIdSet

```
Get-CimSession [-Id] <UInt32[]> [<CommonParameters>]
```

### InstanceIdSet

```
Get-CimSession -InstanceId <Guid[]> [<CommonParameters>]
```

### NameSet

```
Get-CimSession -Name <String[]> [<CommonParameters>]
```

## DESCRIPTION

根據預設，此 Cmdlet 會取得在目前 PowerShell 會話中建立的所有 CIM 會話。 您可以使用的參數 `Get-CimSession` 取得特定電腦的會話，也可以使用其名稱或其他識別碼來識別會話。 `Get-CimSession` 不會取得在其他 PowerShell 會話中建立的 CIM 會話，或是在其他電腦上建立的 CIM 會話。

如需 CIM 會話的詳細資訊，請參閱 [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)。

## 範例

### 範例1：從目前的 PowerShell 會話取得 CIM 會話

此範例會使用 [CimSession](New-CimSession.md)建立 cim 會話，然後使用來取得 cim 會話 `Get-CimSession` 。

```powershell
New-CimSession -ComputerName Server01,Server02
Get-CimSession
```

```Output
Id           : 1
Name         : CimSession1
InstanceId   : d1413bc3-162a-4cb8-9aec-4d2c61253d59
ComputerName : Server01
Protocol     : WSMAN

Id           : 2
Name         : CimSession2
InstanceId   : c0095981-52c5-4e7f-a5bb-c4c680541710
ComputerName : Server02
Protocol     : WSMAN
```

### 範例2：取得特定電腦的 CIM 會話

這個範例會取得連接到名為 **Server02** 之電腦的 CIM 會話。

```powershell
Get-CimSession -ComputerName Server02
```

```Output
Id           : 2
Name         : CimSession2
InstanceId   : c0095981-52c5-4e7f-a5bb-c4c680541710
ComputerName : Server02
Protocol     : WSMAN
```

### 範例3：取得 CIM 會話的清單，然後格式化清單

此範例會取得目前 PowerShell 會話中的所有 CIM 會話，並顯示只包含 **ComputerName** 和 **InstanceID** 屬性的資料表。

```powershell
Get-CimSession | Format-Table -Property ComputerName,InstanceId
```

```Output
ComputerName InstanceId
------------ ----------
Server01     d1413bc3-162a-4cb8-9aec-4d2c61253d59
Server02     c0095981-52c5-4e7f-a5bb-c4c680541710
```

### 範例4：取得所有具有特定名稱的 CIM 會話

此範例會取得所有名稱開頭為 **serv** 的 CIM 會話。

```powershell
Get-CimSession -ComputerName Serv*
```

```Output
Id           : 1
Name         : CimSession1
InstanceId   : d1413bc-162a-4cb8-9aec-4d2c61253d59
ComputerName : Server01
Protocol     : WSMAN

Id           : 2
Name         : CimSession2
InstanceId   : c0095981-52c5-4e7f-a5bb-c4c680541710
ComputerName : Server02
Protocol     : WSMAN
```

### 範例5：取得特定的 CIM 會話

此範例會取得 **識別碼** 為2的 CIM 會話。

```powershell
Get-CimSession -ID 2
```

```Output
Id           : 2
Name         : CimSession2
InstanceId   : c0095981-52c5-4e7f-a5bb-c4c680541710
ComputerName : Server02
Protocol     : WSMAN
```

## PARAMETERS

### -ComputerName

指定要取得連接之 CIM 會話的電腦名稱稱。 允許使用萬用字元。

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet
Aliases: CN, ServerName

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Id

指定要取得之 CIM 會話的識別碼。 若為多個識別符，請使用逗號來分隔識別碼，或使用範圍運算子 (`..`) 來指定識別碼的範圍。 **識別碼** 是一個整數，可唯一識別目前 PowerShell 會話內的 CIM 會話。

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

指定要取得之 CIM 會話的實例識別碼。

**InstanceId** 是全域唯一識別碼 (GUID) ，可唯一識別 CIM 會話。 **InstanceId** 是唯一的，即使您有多個會話在 PowerShell 中執行也是一樣。

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

取得一或多個包含指定易記名稱的 CIM 會話。 允許使用萬用字元。

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

### CommonParameters
這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無

## 輸出

### Microsoft.Management.Infrastructure.CimSession

## 注意

## 相關連結

[Format-Table](../microsoft.powershell.utility/format-table.md)

[New-CimSession](New-CimSession.md)

[Remove-CimSession](remove-cimsession.md)

[about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)
