---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 02/20/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/register-cimindicationevent?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-CimIndicationEvent
ms.openlocfilehash: 11690649b2e7918785eb39c81b2099ad55e49ef5
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202495"
---
# Register-CimIndicationEvent

## 概要
使用篩選運算式或查詢運算式來訂閱指示。

## SYNTAX

### ClassNameComputerSet (預設) 

```
Register-CimIndicationEvent [-Namespace <String>] [-ClassName] <String>
 [-OperationTimeoutSec <UInt32>] [-ComputerName <String>] [[-SourceIdentifier] <String>]
 [[-Action] <ScriptBlock>] [-MessageData <PSObject>] [-SupportEvent] [-Forward]
 [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

### ClassNameSessionSet

```
Register-CimIndicationEvent [-Namespace <String>] [-ClassName] <String>
 [-OperationTimeoutSec <UInt32>] -CimSession <CimSession> [[-SourceIdentifier] <String>]
 [[-Action] <ScriptBlock>] [-MessageData <PSObject>] [-SupportEvent] [-Forward]
 [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

### QueryExpressionSessionSet

```
Register-CimIndicationEvent [-Namespace <String>] [-Query] <String> [-QueryDialect <String>]
 [-OperationTimeoutSec <UInt32>] -CimSession <CimSession> [[-SourceIdentifier] <String>]
 [[-Action] <ScriptBlock>] [-MessageData <PSObject>] [-SupportEvent] [-Forward]
 [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

### QueryExpressionComputerSet

```
Register-CimIndicationEvent [-Namespace <String>] [-Query] <String> [-QueryDialect <String>]
 [-OperationTimeoutSec <UInt32>] [-ComputerName <String>] [[-SourceIdentifier] <String>]
 [[-Action] <ScriptBlock>] [-MessageData <PSObject>] [-SupportEvent] [-Forward]
 [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

## DESCRIPTION

此 `Register-CimIndicationEvent` Cmdlet 會使用指示類別名稱或查詢運算式來訂閱指示。 使用 **SourceIdentifier** 參數將名稱提供給訂用帳戶。

此 Cmdlet 會傳回 **EventSubscription** 物件。 您可以使用此物件來取消訂用帳戶。

## 範例

### 範例1：註冊類別所產生的事件

這個範例會訂閱名為 **Win32_ProcessStartTrace** 的類別所產生的事件。 此類別會在每次處理程序啟動時引發事件。

```powershell
Register-CimIndicationEvent -ClassName 'Win32_ProcessStartTrace' -SourceIdentifier "ProcessStarted"
Get-Event -SourceIdentifier "ProcessStarted"
```

此 `Get-Event` Cmdlet 會取得具有 **ProcessStarted** 訂用帳戶的事件。 如需詳細資訊，請參閱 [取得事件](../Microsoft.PowerShell.Utility/Get-Event.md)。

> [!NOTE]
> 在此範例中，您必須以系統管理員身分執行 PowerShell。

### 範例2：使用查詢來註冊事件

這個範例會使用查詢來訂閱在名為 **Win32_LocalTime** 之類別的實例中有變更時所產生的事件。

```powershell
$query = "SELECT * FROM CIM_InstModification WHERE TargetInstance ISA 'Win32_LocalTime'"
Register-CimIndicationEvent -Query $query -SourceIdentifier "Timer"
```

### 範例3：當事件抵達時執行腳本

此範例顯示如何使用動作來回應事件。 變數會 `$action` 保存腳本區塊以進行 **動作** ，這會使用 `$event` 變數來存取從 CIM 接收的事件。

```powershell
$action = {
  $name = $event.SourceEventArgs.NewEvent.ProcessName
  $id = $event.SourceEventArgs.NewEvent.ProcessId
  Write-Host -Object "New Process Started : Name = $name
 ID = $id"
}
Register-CimIndicationEvent -ClassName 'Win32_ProcessStartTrace' -SourceIdentifier "ProcessStarted" -Action $action
```

如需詳細資訊，請參閱 [Win32_ProcessStartTrace](/previous-versions/windows/desktop/krnlprov/win32-processstarttrace)。

### 範例4：在遠端電腦上註冊事件

此範例會訂閱名為 **Server01** 的遠端電腦上的事件。 從 CIM 伺服器收到的事件會儲存在目前 PowerShell 會話的事件佇列中，然後執行本機 `Get-Event` 以取得事件。

```powershell
Register-CimIndicationEvent -ClassName 'Win32_ProcessStartTrace' -SourceIdentifier "ProcessStarted" -ComputerName Server01
Get-Event -SourceIdentifier "ProcessStarted"
```

## PARAMETERS

### -Action

指定處理事件的命令。 此參數所指定的命令會在引發事件時執行，而不會將事件傳送到事件佇列。 以大括弧括住命令 (`{}`) 來建立腳本區塊。

使用 **action** 指定的腳本區塊可以包括 `$Event` 、 `$EventSubscriber` 、 `$Sender` 、 `$SourceEventArgs` 和 `$SourceArgs` 自動變數，這些變數會將事件的相關資訊提供給 **action** 腳本區塊。 如需詳細資訊，請參閱 [關於自動變數](../microsoft.powershell.core/about/about_automatic_variables.md)。

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CimSession

使用指定的 CIM 會話來執行命令。 輸入包含 CIM 會話的變數，或輸入可建立或取得 CIM 會話的命令，例如 `New-CimSession` 或 `Get-CimSession` Cmdlet。 如需詳細資訊，請參閱 [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)。

```yaml
Type: Microsoft.Management.Infrastructure.CimSession
Parameter Sets: ClassNameSessionSet, QueryExpressionSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ClassName

指定您要訂閱的指示類別。 您可以使用 tab 鍵自動完成來流覽類別清單，因為 PowerShell 會從本機 WMI 伺服器取得類別清單，以提供類別名稱的清單。

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

指定要在其上執行 CIM 作業的電腦名稱稱。 您可以指定完整功能變數名稱 (FQDN) 、NetBIOS 名稱或 IP 位址。

如果您指定這個參數，此 Cmdlet 會使用 WsMan 通訊協定建立指定電腦的暫時會話。 如果您未指定這個參數，此 Cmdlet 會使用元件物件模型 (COM) 在本機系統上執行操作。

如果在同一部電腦上執行多個作業，請使用 CIM 會話連線，以獲得更好的效能。

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, QueryExpressionComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Forward

指出將訂用帳戶的事件轉送到本機電腦上的會話。 當您要訂閱遠端電腦上或遠端工作階段中的事件時，請使用此參數。

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

參數，表示在觸發指定的時間之後，訂閱者應該自動取消註冊。 如果此值等於或小於零，則不會在未註冊事件的情況下觸發事件的次數限制。

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

指定 CIM 作業的命名空間。 預設命名空間為 **root/cimv2** 。 您可以使用 tab 鍵自動完成來流覽命名空間清單，因為 PowerShell 會取得本機 WMI 伺服器的命名空間清單，以提供命名空間清單。

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

### -OperationTimeoutSec

指定 Cmdlet 等候電腦回應的時間長度。 根據預設，此參數的值為0，表示此 Cmdlet 會使用伺服器的預設超時值。

如果 **OperationTimeoutSec** 參數設定為小於健全連接重試超時時間3分鐘的值，則超過 **OperationTimeoutSec** 參數值的網路失敗就無法復原，因為伺服器上的作業會在用戶端重新連線之前超時。

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases: OT

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Query

指定要在 CIM 伺服器上執行的查詢。 如果指定的值包含雙引號 `"` 、單引號 `'` 或反斜線， `\` 您必須在前面加上反斜線字元，以將這些字元加上引號。 如果指定的值使用 WQL LIKE 運算子，您必須以方括弧括住下列字元 `[]` ：百分比 `%` 、底線 `_` 或左方括弧 `[` 。

```yaml
Type: System.String
Parameter Sets: QueryExpressionSessionSet, QueryExpressionComputerSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -QueryDialect

指定用於 **查詢** 參數的查詢語言。 此參數可接受的值為： **WQL** 或 **CQL** 。 預設值為 **WQL** 。

```yaml
Type: System.String
Parameter Sets: QueryExpressionSessionSet, QueryExpressionComputerSet
Aliases:

Required: False
Position: Named
Default value: WQL
Accept pipeline input: False
Accept wildcard characters: False
```

### -SourceIdentifier

指定訂用帳戶的名稱。 您指定的名稱在目前的會話中必須是唯一的。 預設值是 PowerShell 所指派的 GUID。 這個值會出現在訂閱者物件的 **SourceIdentifier** 屬性值以及與此訂閱相關聯之所有事件物件的值中。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SupportEvent

指出事件訂閱已隱藏。 當目前的訂閱是更複雜事件註冊機制的一部分，而且不應該被獨立探索時，請使用這個參數。

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

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無

此 Cmdlet 不接受任何輸入物件。

## 輸出

### System.Object

此 Cmdlet 會輸出 **EventSubscription** 物件。

## 注意

## 相關連結

[Get-Event](../microsoft.powershell.utility/get-event.md)

[Remove-Event](../microsoft.powershell.utility/remove-event.md)

[Unregister-Event](../microsoft.powershell.utility/unregister-event.md)

[Write-Host](../microsoft.powershell.utility/write-host.md)

[Get-CimSession](Get-CimSession.md)

[New-CimSession](New-CimSession.md)
