---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/restart-service?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Restart-Service
ms.openlocfilehash: 491940351042843af60fe85f8f1b39d41688675f
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2020
ms.locfileid: "94342836"
---
# Restart-Service

## 概要
停止然後啟動一或多個服務。

## SYNTAX

### InputObject (預設值)

```
Restart-Service [-Force] [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>]
 [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 預設

```
Restart-Service [-Force] [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### DisplayName

```
Restart-Service [-Force] [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

Cmdlet 會傳送 `Restart-Service` 停止訊息，然後將啟動訊息傳送至指定服務的 Windows 服務控制器。 如果服務已停止，它會啟動而不會以錯誤訊息通知您。 您可以依服務的服務名稱或顯示名稱來指定服務，或是使用 **InputObject** 參數來傳送代表每個要重新啟動之服務的物件。

## 範例

### 範例 1：重新啟動本機電腦上的服務

```powershell
PS C:\> Restart-Service -Name winmgmt
```

此命令會重新啟動本機電腦上的 Windows Management Instrumentation 服務 (WinMgmt)。

### 範例 2：排除服務

```powershell
PS C:\> Restart-Service -DisplayName "net*" -Exclude "net logon"
```

此命令會重新啟動除了 Net Logon 服務之外，所有顯示名稱開頭為 Net 的服務。

### 範例 3：啟動所有已停止的網路服務

```powershell
PS C:\> Get-Service -Name "net*" | Where-Object {$_.Status -eq "Stopped"} | Restart-Service
```

此命令啟動電腦上所有已停止的網路服務。

此命令會使用 `Get-Service` Cmdlet 取得代表服務名稱以 net 開頭之服務的物件。 管線運算子 (`|`) 會將服務物件傳送至 `Where-Object` Cmdlet，此 Cmdlet 只會選取狀態為 [已停止] 的服務。 另一個管線運算子會將選取的服務傳送至 `Restart-Service` 。

在實務上，您會先使用 **WhatIf** 參數來判斷此命令的效果，然後再執行它。

## PARAMETERS

### -DisplayName

指定要重新啟動之服務的顯示名稱。 允許使用萬用字元。

```yaml
Type: System.String[]
Parameter Sets: DisplayName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Exclude

指定此 Cmdlet 省略的服務。 此參數的值會限定 **Name** 參數。 輸入名稱元素或模式，例如 s*。 允許使用萬用字元。

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

### -Force

強制執行命令而不要求使用者確認。

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

### -Include

指定此 Cmdlet 重新開機的服務。 此參數的值會限定 **Name** 參數。 輸入名稱元素或模式，例如 s*。 允許使用萬用字元。

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

指定代表要重新開機之服務的 **ServiceController** 物件。 輸入包含物件的變數，或輸入可取得物件的命令或運算式。

```yaml
Type: System.ServiceProcess.ServiceController[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

指定要重新啟動之服務的服務名稱。

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: ServiceName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -PassThru

傳回代表服務的物件。 根據預設，此 Cmdlet 不會產生任何輸出。

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

### System.ServiceProcess.ServiceController、System.String

您可以使用管線將服務物件或包含服務名稱的字串傳送至此 Cmdlet。

## 輸出

### 無、System.ServiceProcess.ServiceController

如果您指定 **PassThru** 參數，此 Cmdlet 會產生代表重新啟動之服務的 **System.ServiceProcess.ServiceController** 物件。 否則，此 Cmdlet 不會產生任何輸出。

## 注意


- `Restart-Service` 只有當目前的使用者有權進行此作業時，才能控制服務。 若命令無法正確運作，您可能沒有必要的權限。
- 若要尋找系統上服務的服務名稱和顯示名稱，請輸入 `Get-Service` "。
  服務名稱會出現在 [ **名稱** ] 資料行中，而顯示名稱會出現在 [ **DisplayName** ] 欄位中。

## 相關連結

[Get-Service](Get-Service.md)

[New-Service](New-Service.md)

[Resume-Service](Resume-Service.md)

[Set-Service](Set-Service.md)

[Start-Service](Start-Service.md)

[Stop-Service](Stop-Service.md)

[Suspend-Service](Suspend-Service.md)
