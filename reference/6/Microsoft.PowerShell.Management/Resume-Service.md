---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/resume-service?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Resume-Service
ms.openlocfilehash: 00de396b049259904433843e01879c75e3982ca1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202436"
---
# Resume-Service

## 概要
繼續一或多個擱置 (暫停) 的服務。

## SYNTAX

### InputObject (預設值)

```
Resume-Service [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 預設

```
Resume-Service [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### DisplayName

```
Resume-Service [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

**Resume Service 指令程式** 會針對每個指定的服務，將繼續訊息傳送至 Windows 服務控制器。
如果服務暫停，則會繼續。
如果目前正在執行，則會忽略該訊息。
您可以依服務的服務名稱或顯示名稱來指定服務，也可以使用 *InputObject* 參數來傳送代表您要繼續之服務的服務物件。

## 範例

### 範例1：在本機電腦上繼續服務

```
PS C:\> Resume-Service "sens"
```

此命令會在本機電腦上繼續執行系統事件通知服務。
服務名稱在命令中是以 sens 表示。
此命令會使用 *Name* 參數來指定服務的服務名稱，但是此命令會省略參數名稱，因為參數名稱是選擇性的。

### 範例2：繼續所有已暫停的服務

```
PS C:\> Get-Service | Where-Object {$_.Status -eq "Paused"} | Resume-Service
```

此命令會繼續電腦上所有已暫停的服務。
Get-Service Cmdlet 命令會取得電腦上的所有服務。
管線運算子 (|) 將結果傳遞給 Where-Object Cmdlet，其會選取 [ **狀態** ] 屬性為 [已暫停] 的服務。
下一個管線運算子會將結果傳送至 **Resume-Service** ，以繼續暫停的服務。

在實務上，您會先使用 *WhatIf* 參數來判斷此命令的效果，然後再執行它。

## PARAMETERS

### -DisplayName

指定要繼續之服務的顯示名稱。
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

指定此 Cmdlet 省略的服務。
此參數的值會限定 *Name* 參數。
輸入名稱元素或模式，例如 s*。
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

指定要繼續的服務。
此參數的值會限定 *Name* 參數。
輸入名稱元素或模式，例如 s*。
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

指定代表要繼續之服務的 **ServiceController** 物件。
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

指定要繼續之服務的服務名稱。

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: ServiceName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -PassThru

傳回代表服務的物件。
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

如果您指定 *PassThru* 參數，此 Cmdlet 會產生代表已繼續服務的 **system.serviceprocess.dll ServiceController** 物件。
否則，此 Cmdlet 不會產生任何輸出。

## 注意

* 已暫停之服務的狀態已暫停。 當服務繼續執行時，其狀態會是 [正在執行]。
* **Resume-服務** 只有在目前的使用者有權執行此動作時，才能控制服務。 若命令無法正確運作，您可能沒有必要的權限。
* 若要尋找系統上服務的服務名稱和顯示名稱，請輸入 `Get-Service`。 服務名稱會出現在 [ **名稱** ] 資料行中，而顯示名稱會出現在 [ **DisplayName** ] 欄位中。

## 相關連結

[Get-Service](Get-Service.md)

[New-Service](New-Service.md)

[Restart-Service](Restart-Service.md)

[Set-Service](Set-Service.md)

[Start-Service](Start-Service.md)

[Stop-Service](Stop-Service.md)

[Suspend-Service](Suspend-Service.md)

[Remove-Service](Remove-Service.md)
