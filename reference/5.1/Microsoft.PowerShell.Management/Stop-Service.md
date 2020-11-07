---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-service?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Service
ms.openlocfilehash: 77ce507d0eaf476e2c24f41e433bd69fdcb416bb
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2020
ms.locfileid: "94342564"
---
# Stop-Service

## 概要
停止一或多個執行中的服務。

## SYNTAX

### InputObject (預設值)

```
Stop-Service [-Force] [-NoWait] [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>]
 [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 預設

```
Stop-Service [-Force] [-NoWait] [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### DisplayName

```
Stop-Service [-Force] [-NoWait] [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Stop-Service`Cmdlet 會為每個指定的服務傳送停止訊息給 Windows 服務控制器。 您可以依服務的服務名稱或顯示名稱來指定服務，也可以使用 **InputObject** 參數來傳送代表您要停止之服務的服務物件。

## 範例

### 範例1：停止本機電腦上的服務

```
PS C:\> Stop-Service -Name "sysmonlog"
```

此命令會停止本機電腦上的 Performance Logs and Alerts (SysmonLog) 服務。

### 範例2：使用顯示名稱停止服務

```
PS C:\> Get-Service -DisplayName "telnet" | Stop-Service
```

此命令會停止本機電腦上的 Telnet 服務。 命令使用 `Get-Service` 來取得代表 Telnet 服務的物件。 管線運算子 (`|`) 將物件輸送至 `Stop-Service` ，這會停止服務。

### 範例3：停止具有相依服務的服務

```
PS C:\> Get-Service -Name "iisadmin" | Format-List -Property Name, DependentServices
PS C:\> Stop-Service -Name "iisadmin" -Force -Confirm
```

此範例會停止本機電腦上的 IISAdmin 服務。 因為停止這項服務也會停止相依于 IISAdmin 服務的服務，所以最好是 `Stop-Service` 在列出相依于 IISAdmin 服務之服務的命令前面。

第一個命令會列出與 IISAdmin 相依的服務。 它會使用 `Get-Service` 來取得代表 IISAdmin 服務的物件。 管線運算子 (`|`) 將結果傳遞給 `Format-List` Cmdlet。 命令使用的 **Property** 參數 `Format-List` ，只列出服務的 **Name** 和 **DependentServices** 屬性。

第二個命令會停止 IISAdmin 服務。 需要 **Force** 參數才能停止具有相依服務的服務。 此命令會使用 **Confirm** 參數，在停止每個服務之前要求使用者確認。

## PARAMETERS

### -DisplayName

指定要停止之服務的顯示名稱。
允許使用萬用字元。

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

強制 Cmdlet 停止服務，即使該服務具有相依的服務。

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

指定此 Cmdlet 停止的服務。 此參數的值會限定 **Name** 參數。 輸入名稱元素或模式，例如 s*。 允許使用萬用字元。

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

指定代表要停止之服務的 **ServiceController** 物件。 輸入包含物件的變數，或輸入可取得物件的命令或運算式。

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

指定要停止之服務的服務名稱。 允許使用萬用字元。

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

### -NoWait

指出此 Cmdlet 使用 no wait 選項。

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

如果您使用 **PassThru** 參數，此 Cmdlet 會產生代表服務的 **system.serviceprocess.dll ServiceController** 物件。 否則，此 Cmdlet 不會產生任何輸出。

## 注意

您也可以 `Stop-Service` 使用內建的別名 **spsv** 來參考。 如需詳細資訊，請參閱 about_Aliases。

`Stop-Service` 只有當目前的使用者有權進行此作業時，才能控制服務。 若命令無法正確運作，您可能沒有必要的權限。

若要尋找系統上服務的服務名稱和顯示名稱，請輸入 `Get-Service`。 服務名稱會出現在 [ **名稱** ] 資料行中，而顯示名稱會出現在 [ **DisplayName** ] 欄位中。

## 相關連結

[Get-Service](Get-Service.md)

[New-Service](New-Service.md)

[Restart-Service](Restart-Service.md)

[Resume-Service](Resume-Service.md)

[Set-Service](Set-Service.md)

[Start-Service](Start-Service.md)

[Suspend-Service](Suspend-Service.md)
