---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-error?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Error
ms.openlocfilehash: 51698fa0ac5b12a76dec10717d01ef1ec188221c
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2020
ms.locfileid: "93208439"
---
# Write-Error

## 概要
將物件寫入錯誤串流。

## SYNTAX

### NoException (預設值)

```
Write-Error [-Message] <String> [-Category <ErrorCategory>] [-ErrorId <String>] [-TargetObject <Object>]
 [-RecommendedAction <String>] [-CategoryActivity <String>] [-CategoryReason <String>]
 [-CategoryTargetName <String>] [-CategoryTargetType <String>] [<CommonParameters>]
```

### WithException

```
Write-Error -Exception <Exception> [-Message <String>] [-Category <ErrorCategory>] [-ErrorId <String>]
 [-TargetObject <Object>] [-RecommendedAction <String>] [-CategoryActivity <String>] [-CategoryReason <String>]
 [-CategoryTargetName <String>] [-CategoryTargetType <String>] [<CommonParameters>]
```

### ErrorRecord

```
Write-Error -ErrorRecord <ErrorRecord> [-RecommendedAction <String>] [-CategoryActivity <String>]
 [-CategoryReason <String>] [-CategoryTargetName <String>] [-CategoryTargetType <String>] [<CommonParameters>]
```

## DESCRIPTION

Cmdlet 會宣告 `Write-Error` 非終止錯誤。 根據預設，錯誤會透過錯誤串流連同輸出傳送至要顯示的主機程式。

若要寫入非終止錯誤，請輸入錯誤訊息字串、 **ErrorRecord** 物件，或 **Exception** 物件。 使用的其他參數 `Write-Error` 填入錯誤記錄。

非終止錯誤會將錯誤寫入錯誤串流，但是不會停止命令處理。
如果在輸入項目集合中的一個項目上宣告非終止錯誤，命令就會繼續處理集合中的其他項目。

若要宣告終止錯誤，請使用 `Throw` 關鍵字。
如需詳細資訊，請參閱 [about_Throw](../Microsoft.PowerShell.Core/About/about_Throw.md)。

## 範例

### 範例1：寫入 RegistryKey 物件的錯誤

```powershell
Get-ChildItem | ForEach-Object {
    if ($_.GetType().ToString() -eq "Microsoft.Win32.RegistryKey")
    {
        Write-Error "Invalid object" -ErrorId B1 -TargetObject $_
    }
    else
    {
        $_
    }
}
```

此命令會在 `Get-ChildItem` Cmdlet 傳回 `Microsoft.Win32.RegistryKey` 物件（例如 `HKLM:` PowerShell 登錄提供者的或磁片磁碟機中的物件）時，宣告非終止錯誤 `HKCU:` 。

### 範例2：將錯誤訊息寫入主控台

```powershell
Write-Error "Access denied."
```

此命令宣告非終止錯誤，並寫入「拒絕存取」錯誤。 此命令使用 **Message** 參數指定訊息，但是省略選擇性的 **Message** 參數名稱。

### 範例3：將錯誤寫入主控台並指定類別目錄

```powershell
Write-Error -Message "Error: Too many input values." -Category InvalidArgument
```

此命令宣告非終止錯誤，並指定錯誤類別。

### 範例4：使用 Exception 物件撰寫錯誤

```powershell
$E = [System.Exception]@{Source="Get-ParameterNames.ps1";HelpLink="https://go.microsoft.com/fwlink/?LinkID=113425"}
Write-Error -Exception $E -Message "Files not found. The $Files location does not contain any XML files."
```

此命令使用 **Exception** 物件宣告非終止錯誤。

第一個命令使用雜湊表建立 **System.Exception** 物件。 它會將例外狀況物件儲存在 `$E` 變數中。 您可以使用雜湊表建立具有 Null 建構函式類型的任何物件。

第二個命令會使用 `Write-Error` Cmdlet 來宣告非終止錯誤。 **Exception** 參數的值是變數中的 **exception** 物件 `$E` 。

## PARAMETERS

### -Category

指定錯誤的類別。 預設值為 **NotSpecified** 。 此參數可接受的值為：

- NotSpecified
- OpenError
- CloseError
- DeviceError
- DeadlockDetected
- InvalidArgument
- InvalidData
- InvalidOperation
- InvalidResult
- InvalidType
- MetadataError
- NotImplemented
- NotInstalled
- ObjectNotFound
- OperationStopped
- OperationTimeout
- SyntaxError
- ParserError
- PermissionDenied
- ResourceBusy
- ResourceExists
- ResourceUnavailable
- ReadError
- WriteError
- FromStdErr
- SecurityError
- ProtocolError
- ConnectionError
- AuthenticationError
- LimitsExceeded
- QuotaExceeded
- NotEnabled

如需錯誤類別的詳細資訊，請參閱 [ErrorCategory 列舉](https://go.microsoft.com/fwlink/?LinkId=143600)。

```yaml
Type: System.Management.Automation.ErrorCategory
Parameter Sets: NoException, WithException
Aliases:
Accepted values: NotSpecified, OpenError, CloseError, DeviceError, DeadlockDetected, InvalidArgument, InvalidData, InvalidOperation, InvalidResult, InvalidType, MetadataError, NotImplemented, NotInstalled, ObjectNotFound, OperationStopped, OperationTimeout, SyntaxError, ParserError, PermissionDenied, ResourceBusy, ResourceExists, ResourceUnavailable, ReadError, WriteError, FromStdErr, SecurityError, ProtocolError, ConnectionError, AuthenticationError, LimitsExceeded, QuotaExceeded, NotEnabled

Required: False
Position: Named
Default value: NotSpecified
Accept pipeline input: False
Accept wildcard characters: False
```

### -CategoryActivity

指定造成錯誤的動作。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Activity

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CategoryReason

指定活動造成錯誤的方式或原因。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Reason

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CategoryTargetName

指定發生錯誤時正在處理的物件名稱。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: TargetName

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CategoryTargetType

指定發生錯誤時正在處理的物件類型。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: TargetType

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ErrorId

指定識別錯誤的識別碼字串。 字串對於每個錯誤必須是唯一的。

```yaml
Type: System.String
Parameter Sets: NoException, WithException
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ErrorRecord

指定表示錯誤的錯誤記錄物件。 使用物件的屬性可描述錯誤。

若要建立錯誤記錄物件，請使用 `New-Object` Cmdlet 或從自動變數中的陣列取得錯誤記錄物件 `$Error` 。

```yaml
Type: System.Management.Automation.ErrorRecord
Parameter Sets: ErrorRecord
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Exception

指定表示錯誤的例外狀況物件。 使用物件的屬性可描述錯誤。

若要建立例外狀況物件，請使用雜湊表或使用 `New-Object` Cmdlet。

```yaml
Type: System.Exception
Parameter Sets: WithException
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Message

指定錯誤的訊息文字。 如果文字包含空格或特殊字元，請將它括在引號中。 您也可以使用管線將訊息字串傳送至 `Write-Error` 。

```yaml
Type: System.String
Parameter Sets: NoException, WithException
Aliases: Msg

Required: True (NoException), False (WithException)
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -RecommendedAction

指定使用者應該採取以解決或避免錯誤的動作。

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

### -TargetObject

指定發生錯誤時正在處理的物件。 輸入物件、包含物件的變數，或可取得物件的命令。

```yaml
Type: System.Object
Parameter Sets: NoException, WithException
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

### System.String

您可以使用管線將包含錯誤訊息的字串傳送至 `Write-Error` 。

## 輸出

### Error 物件

`Write-Error` 只寫入至錯誤資料流程。 它不會傳回任何物件。

## 注意

`Write-Error` 不會變更自動變數的值 `$?` ，因此不會發出終止錯誤條件的信號。 若要指示終止錯誤，請使用 [$PSCmdlet. WriteError ( # B1 ](/dotnet/api/system.management.automation.cmdlet.writeerror) 方法。

## 相關連結

[about_Automatic_Variables](../microsoft.powershell.core/about/about_automatic_variables.md)

[about_Output_Streams](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[Write-Debug](Write-Debug.md)

[Write-Host](Write-Host.md)

[Write-Output](Write-Output.md)

[Write-Progress](Write-Progress.md)

[Write-Verbose](Write-Verbose.md)

[Write-Warning](Write-Warning.md)
