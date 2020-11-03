---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-service?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Service
ms.openlocfilehash: df4fda68508e21700235d2b772c6dd43c8e1fe1e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203495"
---
# Set-Service

## 概要
啟動、停止並擱置服務，然後變更其屬性。

## SYNTAX

### Name (預設值)

```
Set-Service [-ComputerName <String[]>] [-Name] <String> [-DisplayName <String>]
 [-Description <String>] [-StartupType <ServiceStartMode>] [-Status <String>] [-PassThru] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### InputObject

```
Set-Service [-ComputerName <String[]>] [-DisplayName <String>] [-Description <String>]
 [-StartupType <ServiceStartMode>] [-Status <String>] [-InputObject <ServiceController>] [-PassThru]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

此 `Set-Service` Cmdlet 會變更服務的屬性，例如 **Status** 、 **Description** 、 **DisplayName** 和 **StartupType** 。 `Set-Service` 可以啟動、停止、暫停或暫停服務。 若要識別服務，請輸入其服務名稱或提交服務物件。 或者，將服務名稱或服務物件沿著管線向下傳送至 `Set-Service` 。

## 範例

### 範例1：變更顯示名稱

在此範例中，服務的顯示名稱已變更。 若要查看原始顯示名稱，請使用 `Get-Service` 。

```powershell
Set-Service -Name LanmanWorkstation -DisplayName "LanMan Workstation"
```

`Set-Service` 使用 **Name** 參數來指定服務的名稱 **LanmanWorkstation** 。 **DisplayName** 參數指定新的顯示名稱 [ **LanMan 工作站** ]。

### 範例2：變更服務的啟動類型

此範例顯示如何變更服務的啟動類型。

```powershell
Set-Service -Name BITS -StartupType Automatic
Get-Service BITS | Select-Object -Property Name, StartType, Status
```

```Output
Name  StartType   Status
----  ---------   ------
BITS  Automatic  Running
```

`Set-Service` 使用 **Name** 參數來指定服務的名稱（ **BITS** ）。 **StartupType** 參數會將服務設定為 **自動** 。

`Get-Service` 使用 **Name** 參數來指定 **BITS** 服務，並將物件沿著管線向下傳送。 `Select-Object` 使用 **Property** 參數來顯示 **BITS** 服務的狀態。

### 範例3：變更服務的描述

此範例會變更 BITS 服務的描述，並顯示結果。

`Get-CimInstance`使用 Cmdlet 的原因是它會傳回包含服務 **描述** 的 **Win32_Service** 物件。

```powershell
Get-CimInstance Win32_Service -Filter 'Name = "BITS"'  | Format-List  Name, Description
```

```Output
Name        : BITS
Description : Transfers files in the background using idle network bandwidth. If the service is
              disabled, then any applications that depend on BITS, such as Windows Update or MSN
              Explorer, will be unable to automatically download programs and other information.
```

```powershell
Set-Service -Name BITS -Description "Transfers files in the background using idle network bandwidth."
Get-CimInstance Win32_Service -Filter 'Name = "BITS"' | Format-List  Name, Description
```

```Output
Name        : BITS
Description : Transfers files in the background using idle network bandwidth.
```

`Get-CimInstance` 將物件向下傳送至管線， `Format-List` 並顯示服務的名稱和描述。 為了進行比較，此命令會在更新描述之前和之後執行。

`Set-Service` 使用 **Name** 參數來指定 **BITS** 服務。 **Description** 參數會指定服務描述的更新文字。

### 範例4：啟動服務

在此範例中，會啟動服務。

```powershell
Set-Service -Name WinRM -Status Running -PassThru
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  WinRM              Windows Remote Management (WS-Manag...
```

`Set-Service` 使用 **Name** 參數來指定服務 **WinRM** 。 **Status** 參數會使用執行的 **值來** 啟動服務。 **PassThru** 參數會輸出顯示結果的 **ServiceController** 物件。

### 範例5：暫止服務

此範例會使用管線來暫停至服務。

```powershell
Get-Service -Name Schedule | Set-Service -Status Paused
```

`Get-Service` 使用 **Name** 參數來指定 **排程** 服務，然後將物件沿著管線向下傳送。 `Set-Service` 使用 **Status** 參數將服務設定為 **暫停** 。

### 範例6：停止服務

此範例會使用變數來停止服務。

```powershell
$S = Get-Service -Name Schedule
Set-Service -InputObject $S -Status Stopped
```

`Get-Service` 使用 **Name** 參數來指定服務（ **Schedule** ）。 物件會儲存在變數中 `$S` 。 `Set-Service` 使用 **InputObject** 參數並指定儲存的物件 `$S` 。 **Status** 參數會將服務設定為「 **已停止** 」。

## PARAMETERS

### -ComputerName

指定一或多部電腦。 針對 [遠端電腦]，輸入 NetBIOS 名稱、IP 位址或完整功能變數名稱。 如果未指定 **ComputerName** 參數，則命令會在本機電腦上執行。

此參數不依賴 PowerShell 遠端功能。 即使您的電腦未設定為執行遠端命令，您也可以使用 **ComputerName** 參數。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: cn

Required: False
Position: Named
Default value: Local computer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Confirm

在執行之前提示您確認 `Set-Service` 。

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

### -Description

指定服務的新描述。

服務描述會顯示在 [ **電腦管理]、[服務** ] 中。 **描述** 不是 `Get-Service` **ServiceController** 物件的屬性。 若要查看服務描述，請使用傳回 `Get-CimInstance` 代表服務的 **Win32_Service** 物件。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DisplayName

指定服務的新顯示名稱。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: DN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

指定代表要變更之服務的 **ServiceController** 物件。 輸入包含物件的變數，或輸入可取得物件的命令或運算式，例如 `Get-Service` 命令。 您可以使用管線將服務物件傳送至 `Set-Service` 。

```yaml
Type: System.ServiceProcess.ServiceController
Parameter Sets: InputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

指定要變更之服務的服務名稱。 不允許使用萬用字元。 您可以使用管線將服務名稱傳送至 `Set-Service` 。

```yaml
Type: System.String
Parameter Sets: Name
Aliases: ServiceName, SN

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -PassThru

傳回代表已變更之服務的 **ServiceController** 物件。 依預設， `Set-Service` 不會產生任何輸出。

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

### -StartupType

設定服務的啟動類型。 此參數可接受的值為：

- **自動** -服務會在系統啟動時啟動或由作業系統啟動。
  如果自動啟動的服務依賴手動啟動的服務，以手動方式啟動的服務也會在系統啟動時自動啟動。
- **停用** -服務已停用，且無法由使用者或應用程式啟動。
- **手動** -此服務只會由使用者以手動方式啟動，使用服務控制管理員或由應用程式啟動。
- **開機** -表示該服務是由系統載入器啟動的設備磁碟機。 這個值僅適用於裝置驅動程式。
- **系統** -表示服務是由 ' IOInitSystem ( # A1 ' 函式啟動的設備磁碟機。 這個值僅適用於裝置驅動程式。

 預設值為 [ **自動** ]。

```yaml
Type: System.ServiceProcess.ServiceStartMode
Parameter Sets: (All)
Aliases: StartMode, SM, ST
Accepted values: Boot, System, Automatic, Manual, Disabled

Required: False
Position: Named
Default value: Automatic
Accept pipeline input: False
Accept wildcard characters: False
```

### -Status

指定服務的狀態。

此參數可接受的值如下：

- 已 **暫停** 。 暫停服務。
- **正在** 執行。 啟動服務。
- **已停止** 。 停止服務。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Paused, Running, Stopped

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

顯示執行時所發生 `Set-Service` 的情況。 不會執行此 Cmdlet。

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

您可以使用管線將服務物件或包含服務名稱的字串傳送至 `Set-Service` 。

## 輸出

### System.ServiceProcess.ServiceController

依預設， `Set-Service` 不會傳回任何物件。 使用 **PassThru** 參數輸出 **ServiceController** 物件。

## 注意

`Set-Service` 需要較高的許可權。 使用 [ **以系統管理員身分執行** ] 選項。

`Set-Service` 只有在目前的使用者有權管理服務時，才能控制服務。 如果命令無法正確運作，您可能沒有必要的許可權。

若要尋找服務的服務名稱或顯示名稱，請使用 `Get-Service` 。 服務名稱是在 [ **名稱** ] 資料行中，而顯示名稱則是在 [ **DisplayName** ] 欄位中。

## 相關連結

[Get-Service](Get-Service.md)

[New-Service](New-Service.md)

[Restart-Service](Restart-Service.md)

[Resume-Service](Resume-Service.md)

[Start-Service](Start-Service.md)

[Stop-Service](Stop-Service.md)

[Suspend-Service](Suspend-Service.md)
