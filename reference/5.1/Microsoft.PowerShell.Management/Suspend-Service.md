---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/suspend-service?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Suspend-Service
ms.openlocfilehash: 529edca36e63d9a72d2a300ebc8c6c26033db0d8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203460"
---
# Suspend-Service

## 概要
暫停一或多個執行中的服務。

## SYNTAX

### InputObject (預設值)

```
Suspend-Service [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 預設

```
Suspend-Service [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### DisplayName

```
Suspend-Service [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

**暫止服務指令程式** 會針對每個指定的服務，將暫止訊息傳送至 Windows 服務控制器。
暫止時，服務仍在執行中，但它的動作會在繼續之前停止，例如使用 Resume-Service Cmdlet。
您可以依服務的服務名稱或顯示名稱來指定服務，也可以使用 *InputObject* 參數來傳送代表您要暫停之服務的服務物件。

## 範例

### 範例1：暫止服務

```
PS C:\> Suspend-Service -DisplayName "Telnet"
```

此命令會暫停本機電腦上的 Telnet service (Tlntsvr) 服務。

### 範例2：顯示擱置服務時所發生的情況

```
PS C:\> Suspend-Service -Name lanman* -WhatIf
```

此命令會指出當您暫停服務名稱開頭為 lanman 的服務時，會發生什麼情況。
若要暫停服務，請重新執行沒有 *WhatIf* 參數的命令。

### 範例3：取得和暫停服務

```
PS C:\> Get-Service schedule | Suspend-Service
```

此命令會使用 **get-help** Cmdlet 來取得物件，該物件代表電腦上 (排程) 服務工作排程器。
管線運算子 (|) 將結果傳遞至擱置服務的擱置 **服務** ，這會暫停服務。

### 範例4：暫停所有可暫停的服務

```
PS C:\> Get-Service | Where-Object {$_.CanPauseAndContinue -eq "True"} | Suspend-Service -Confirm
```

此命令會暫停電腦上所有可暫停的服務。
它會使用 **get-help** 來取得代表電腦上之服務的物件。
管線運算子會將結果傳遞至 Where-Object Cmdlet，此 Cmdlet 只會選取具有 **CanPauseAndContinue** 屬性 $True 值的服務。
另一個管線運算子會將結果傳遞至 **暫止的服務** 。
*Confirm* 參數會在暫停每個服務之前提示您確認。

## PARAMETERS

### -DisplayName

指定要暫停之服務的顯示名稱。
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

指定要從指定服務中省略的服務。
此參數的值會限定 *Name* 參數。
輸入名稱元素或模式，例如 "s*"。
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

### -Include

指定要暫停的服務。
此參數的值會限定 *Name* 參數。
輸入名稱元素或模式，例如 "s*"。
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

### -InputObject

指定代表要暫停之服務的 **ServiceController** 物件。
輸入包含物件的變數，或輸入可取得物件的命令或運算式。

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

指定要暫停之服務的服務名稱。
允許使用萬用字元。

參數名稱為選擇性。
您可以使用 *名稱* 或其別名、 *ServiceName* ，也可以省略參數名稱。

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

傳回代表您正在使用之項目的物件。
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

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.ServiceProcess.ServiceController、System.String

您可以使用管線將服務物件或包含服務名稱的字串傳送至此 Cmdlet。

## 輸出

### 無、System.ServiceProcess.ServiceController

如果您指定 *PassThru* 參數，此 Cmdlet 會產生代表服務的 **system.serviceprocess.dll ServiceController** 物件。
否則，此 Cmdlet 不會產生任何輸出。

## 注意

* 只有當目前的使用者有權進行此作業時， **暫停服務** 才能控制服務。 若命令無法正確運作，您可能沒有必要的權限。
* **暫止服務** 只能暫停支援暫止和繼續的服務。 若要判斷特定服務是否可以暫止，請使用 Get-Service Cmdlet 搭配 **CanPauseAndContinue** 屬性。 例如： `Get-Service wmi | Format-List Name, CanPauseAndContinue` 。 若要尋找電腦上所有可暫停的服務，請輸入 `Get-Service | Where-Object {$_.CanPauseAndContinue -eq $true}` 。
* 若要尋找系統上服務的服務名稱和顯示名稱，請輸入 **Get-service** 。 服務名稱會出現在 [ **名稱** ] 資料行中，而顯示名稱會出現在 [ **DisplayName** ] 欄位中。

## 相關連結

[Get-Service](Get-Service.md)

[New-Service](New-Service.md)

[Restart-Service](Restart-Service.md)

[Resume-Service](Resume-Service.md)

[Set-Service](Set-Service.md)

[Start-Service](Start-Service.md)

[Stop-Service](Stop-Service.md)
