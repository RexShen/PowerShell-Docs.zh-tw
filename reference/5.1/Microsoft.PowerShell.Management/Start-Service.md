---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/start-service?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Service
ms.openlocfilehash: f9aacc2d27ef0f0ec6f3c3854f1da07f32a13383
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2020
ms.locfileid: "94342649"
---
# Start-Service

## 概要
啟動一或多個已停止的服務。

## SYNTAX

### InputObject (預設值)

```
Start-Service [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 預設

```
Start-Service [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### DisplayName

```
Start-Service [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

指令 `Start-Service` 程式會將啟動訊息傳送給每個指定服務的 Windows 服務控制器。 如果服務正在執行，系統會忽略該訊息，且沒有錯誤。 您可以依服務的服務名稱或顯示名稱來指定服務，或是使用 **InputObject** 參數來提供代表您要啟動之服務的服務物件。

## 範例

### 範例 1︰使用名稱啟動服務

此範例會啟動本機電腦上的 EventLog 服務。 **Name** 參數會依服務的服務名稱來識別服務。

```powershell
Start-Service -Name "eventlog"
```

### 範例 2︰顯示資訊，但不啟動服務

此範例顯示當您啟動的服務具有包含 "remote" 的顯示名稱時，會發生什麼事。

```powershell
Start-Service -DisplayName *remote* -WhatIf
```

**DisplayName** 參數會依據服務的顯示名稱（而非其服務名稱）來識別服務。 **WhatIf** 參數會讓 Cmdlet 顯示當您執行命令時所發生的情況，但不會進行變更。

### 範例 3︰啟動服務，並在文字檔中記錄動作

此範例會啟動電腦上的 Windows Management Instrumentation (WMI) 服務，並將動作的記錄新增至 services.txt 檔。

```powershell
$s = Get-Service wmi
Start-Service -InputObject $s -PassThru | Format-List >> services.txt
```

首先我們 `Get-Service` 會使用來取得代表 WMI 服務的物件，並將它儲存在 `$s` 變數中。 接下來，我們會啟動服務。 如果沒有 **PassThru** 參數，則不 `Start-Service` 會建立任何輸出。 管線運算子 (|) 將物件輸出傳遞 `Start-Service` 給 `Format-List` Cmdlet，以將物件格式化為其屬性的清單。 附加重新導向運算子 () 會將 \> \> 輸出重新導向至 services.txt 的檔案。 輸出會新增至現有檔案的結尾。

### 範例 4︰啟動停用的服務

此範例示範如何在服務的啟動類型為 **停用** 時啟動服務。

```
PS> Start-Service tlntsvr
Start-Service : Service 'Telnet (TlntSvr)' cannot be started due to the following error: Cannot start service TlntSvr on computer '.'.
At line:1 char:14
+ Start-Service  <<<< tlntsvr

PS> Get-CimInstance win32_service | Where-Object Name -eq "tlntsvr"
ExitCode  : 0
Name      : TlntSvr
ProcessId : 0
StartMode : Disabled
State     : Stopped
Status    : OK

PS> Set-Service tlntsvr -StartupType manual
PS> Start-Service tlntsvr
```

第一次嘗試啟動 Telnet 服務 (tlntsvr) 失敗。 此 `Get-CimInstance` 命令會顯示 Tlntsvr 服務的 **StartMode** 屬性已 **停用** 。 Cmdlet 會將 `Set-Service` 啟動類型變更為 **手動** 。 現在，我們可以重新提交 `Start-Service` 命令。 這次命令會執行成功。 若要確認命令是否成功，請執行 `Get-Service` 。

## PARAMETERS

### -DisplayName

指定要啟動之服務的顯示名稱。 允許使用萬用字元。

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

指定此 Cmdlet 省略的服務。 此參數的值會限定 **Name** 參數。 輸入名稱元素或模式，例如 `s*` 。 允許使用萬用字元。

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

指定此 Cmdlet 啟動的服務。 此參數的值會限定 **Name** 參數。 輸入名稱元素或模式，例如 `s*` 。 允許使用萬用字元。

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

指定代表要啟動之服務的 **ServiceController** 物件。 輸入包含物件的變數，或輸入可取得物件的命令或運算式。

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

指定要啟動之服務的服務名稱。

參數名稱為選擇性。 您可以使用 **名稱** 或其別名、 **ServiceName** ，也可以省略參數名稱。

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

您可以使用管線將代表服務的物件，或是包含服務名稱的字串傳送至此 Cmdlet。

## 輸出

### 無、System.ServiceProcess.ServiceController

如果您指定 **PassThru** ，此 Cmdlet 會產生代表該服務的 **System.ServiceProcess.ServiceController** 物件。 否則，此 Cmdlet 不會產生任何輸出。

## 注意

- 您也可以 `Start-Service` 使用內建的別名來參考 `sasv` 。 如需詳細資訊，請參閱 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。
- `Start-Service` 只有在目前的使用者有權進行此作業時，才能控制服務。 若命令無法正確運作，您可能沒有必要的權限。
- 若要尋找系統上服務的服務名稱和顯示名稱，請輸入 `Get-Service`。
  服務名稱會出現在 [ **名稱** ] 資料行中，而顯示名稱會出現在 [ **DisplayName** ] 欄位中。
- 您只能啟動啟動類型為 [手動]、[自動] 或 [自動] (延遲開始) 的服務。 您無法啟動啟動類型是 Disabled 的服務。 如果 `Start-Service` 命令因訊息而失敗 `Cannot start service \<service-name\> on computer` ，請使用 `Get-CimInstance` 來尋找服務的啟動類型，如果您需要的話，請使用 `Set-Service` Cmdlet 來變更服務的啟動類型。
- 某些服務，例如效能記錄及警示 (SysmonLog)，在沒有執行任何工作時會自動停止。 當 PowerShell 啟動幾乎立即停止的服務時，它會顯示下列訊息： `Service \<display-name\> start failed.`

## 相關連結

[Get-Service](Get-Service.md)

[New-Service](New-Service.md)

[Restart-Service](Restart-Service.md)

[Resume-Service](Resume-Service.md)

[Set-Service](Set-Service.md)

[Stop-Service](Stop-Service.md)

[Suspend-Service](Suspend-Service.md)
