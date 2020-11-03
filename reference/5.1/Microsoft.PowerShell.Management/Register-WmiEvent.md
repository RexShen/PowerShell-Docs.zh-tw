---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 07/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/register-wmievent?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-WmiEvent
ms.openlocfilehash: be29ce6376dea7686c0c063cc5528fbc7d840a9d
ms.sourcegitcommit: 41b072f0b6046d619b0e7f758982783fb648a3d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2020
ms.locfileid: "93205811"
---
# Register-WmiEvent

## 概要
訂閱 Windows Management Instrumentation (WMI) 事件。

## SYNTAX

### class (預設值)

```
Register-WmiEvent [-Namespace <String>] [-Credential <PSCredential>] [-ComputerName <String>] [-Class] <String>
 [-Timeout <Int64>] [[-SourceIdentifier] <String>] [[-Action] <ScriptBlock>] [-MessageData <PSObject>]
 [-SupportEvent] [-Forward] [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

### 查詢

```
Register-WmiEvent [-Namespace <String>] [-Credential <PSCredential>] [-ComputerName <String>] [-Query] <String>
 [-Timeout <Int64>] [[-SourceIdentifier] <String>] [[-Action] <ScriptBlock>] [-MessageData <PSObject>]
 [-SupportEvent] [-Forward] [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

## DESCRIPTION

`Register-WmiEvent`Cmdlet 會訂閱本機電腦或遠端電腦上的 Windows Management Instrumentation (WMI) 事件。

當訂閱的 WMI 事件被引發時，即使事件是發生在遠端電腦上，也會將事件新增到您本機工作階段內的事件佇列中。 若要取得事件佇列中的事件，請使用 `Get-Event` Cmdlet。

您可以使用的參數 `Register-WmiEvent` 來訂閱遠端電腦上的事件，並指定可協助您在佇列中識別事件的事件屬性值。 您也可以使用 **Action** 參數來指定引發訂閱事件時要採取的動作。

當您訂閱某個事件時，會將事件訂閱者新增到您的工作階段中。 若要取得會話中的事件訂閱者，請使用 `Get-EventSubscriber` Cmdlet。 若要取消訂用帳戶，請使用 `Unregister-Event` Cmdlet，此 Cmdlet 會從會話刪除事件訂閱者。

新通用訊息模型 (CIM) Cmdlet （引進 Windows PowerShell 3.0）會執行與 WMI Cmdlet 相同的工作。 CIM Cmdlet 符合 WS-Management (WSMan) 標準和 CIM 標準，可讓 Cmdlet 使用相同的技術來管理執行 Windows 作業系統的電腦，以及執行其他作業系統的電腦。 請 `Register-WmiEvent` 考慮使用 [CimIndicationEvent](../cimcmdlets/register-cimindicationevent.md) Cmdlet，而不是使用。

## 範例

### 範例1：訂閱類別所產生的事件

此命令會訂閱 **Win32_ProcessStartTrace** 類別所產生的事件。 此類別會在每次處理程序啟動時引發事件。

```powershell
Register-WmiEvent -Class 'Win32_ProcessStartTrace' -SourceIdentifier "ProcessStarted"
```

### 範例2：訂閱進程的建立事件

此命令使用查詢來訂閱 Win32_process 執行個體建立事件。

```powershell
$wmiParameters = @{
  Query = "select * from __instancecreationevent within 5 where targetinstance isa 'win32_process'"
  SourceIdentifier = "WMIProcess"
  MessageData = "Test 01"
  TimeOut = 500
}
Register-WmiEvent @wmiParameters
```

### 範例3：使用動作來回應事件

此範例示範如何使用動作來回應事件。 在此情況下，當處理常式啟動時， `Start-Process` 會將目前會話中的任何命令寫入至 XML 檔案。

```powershell
$action = { Get-History | where { $_.commandline -like "*start-process*" } | export-cliXml "commandHistory.clixml" }
Register-WmiEvent -Class 'Win32_ProcessStartTrace' -SourceIdentifier "ProcessStarted" -Action $action
```

```Output
Id    Name            State      HasMoreData   Location  Command
--    ----            -----      -----------   --------  -------
1     ProcessStarted  NotStarted False                   get-history | where {...
```

當您使用 **Action** 參數時，會傳回 `Register-WmiEvent` 代表事件動作的背景工作。 您可以使用 **Job** Cmdlet （例如 `Get-Job` 和 `Receive-Job` ）來管理事件工作。

如需詳細資訊，請參閱 about_Jobs。

### 範例4：在遠端電腦上註冊事件

此範例會登錄以取得 Server01 遠端電腦上的事件。

```powershell
Register-WmiEvent -Class 'Win32_ProcessStartTrace' -SourceIdentifier "Start" -Computername Server01
Get-Event -SourceIdentifier "Start"
```

WMI 會將事件傳回本機電腦，並將它們儲存在目前工作階段內的事件佇列中。 若要抓取事件，請執行本機 `Get-Event` 命令。

## PARAMETERS

### -Action

指定處理事件的命令。 **Action** 參數中的命令會在引發事件時執行，而不會將事件傳送到事件佇列。 以大括弧括住命令 (`{}`) 來建立腳本區塊。

**Action** 的值可以包括 `$Event` 、 `$EventSubscriber` 、 `$Sender` 、 `$EventArgs` 和 `$Args` 自動變數，這些變數會將事件的相關資訊提供給 **Action** 腳本區塊。 如需詳細資訊，請參閱 about_Automatic_Variables。

當您指定動作時，會傳回 `Register-WmiEvent` 代表該動作的事件工作物件。 您可以使用包含 **作業** 名詞 ( **工作 Cmdlet)** 來管理事件工作的 Cmdlet。

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: 101
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Class

指定您要訂閱的事件。 請輸入產生事件的 WMI 類別。 每個命令中都需要 **類別** 或 **查詢** 參數。

```yaml
Type: System.String
Parameter Sets: class
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

指定命令執行所在的電腦名稱稱。 預設是本機電腦。

輸入電腦的 NetBIOS 名稱、IP 位址或完整網域名稱。 若要指定本機電腦，請輸入電腦名稱稱、點 (`.`) 或 localhost。

此參數不必依賴 Windows PowerShell 遠端功能。 即使您的電腦未設定為執行遠端命令，您仍然可以使用 **ComputerName** 參數。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

指定具有執行此動作權限的使用者帳戶。 預設為目前使用者。

輸入使用者名稱（例如 User01 或 Domain01\User01），或輸入 **PSCredential** 物件，例如 Cmdlet 所產生的物件 `Get-Credential` 。 如果您輸入使用者名稱，此 Cmdlet 會提示您輸入密碼。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Forward

指出此 Cmdlet 會將此訂閱的事件傳送到本機電腦上的會話。
當您要訂閱遠端電腦上或遠端工作階段中的事件時，請使用此參數。

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

### -MaxTriggerCount

指定最大觸發程式計數。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MessageData

指定要與這個事件訂閱建立關聯的任何其他資料。 此參數的值會出現在與此訂用帳戶相關聯之所有事件的 **MessageData** 屬性中。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Namespace

指定 WMI 類別的命名空間。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: NS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Query

指定 WMI 查詢語言 (WQL) 的查詢，以識別 WMI 事件類別，例如： `select * from __InstanceDeletionEvent` 。

```yaml
Type: System.String
Parameter Sets: query
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SourceIdentifier

指定您為訂閱選取的名稱。 您所選取的名稱在目前的工作階段中必須是唯一的。 預設值是 Windows PowerShell 所指派的 GUID。

這個參數的值會出現在訂閱者物件以及與此訂閱相關聯之所有事件物件的 **SourceIdentifier** 屬性值中。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 100
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SupportEvent

指出此 Cmdlet 會隱藏事件訂用帳戶。 當目前的訂閱是更複雜事件註冊機制的一部分，而且不應該被獨立探索時，請使用這個參數。

若要查看或取消使用 **SupportEvent** 參數建立的訂閱，請指定和 Cmdlet 的 **Force** 參數 `Get-EventSubscriber` `Unregister-Event` 。

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

### -Timeout

指定 Windows PowerShell 等候此命令完成的時間長度。

預設值為 0 (零) 表示沒有逾時，這會使 Windows PowerShell 無限期等待。

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases: TimeoutMSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無

您無法使用管線將物件傳送至此 Cmdlet。

## 輸出

### 無

此 Cmdlet 不會產生任何輸出。

## 注意

若要在 Windows Vista 或更新版本的 Windows 作業系統中使用此 Cmdlet，請使用 [以系統管理員身分執行] 選項啟動 Windows PowerShell。

事件、事件訂閱與事件佇列僅存在目前工作階段中。 若關閉目前工作階段，便會捨棄事件佇列，並取消事件訂閱。

## 相關連結
