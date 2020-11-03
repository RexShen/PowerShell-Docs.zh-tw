---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-tracesource?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-TraceSource
ms.openlocfilehash: 7a1f7e2879b0eeefe8771a5e5a8bf763e48ff106
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201235"
---
# Set-TraceSource

## 概要
設定、啟動和停止 PowerShell 元件的追蹤。

## SYNTAX

### optionsSet (預設值)

```
Set-TraceSource [-Name] <String[]> [[-Option] <PSTraceSourceOptions>] [-ListenerOption <TraceOptions>]
 [-FilePath <String>] [-Force] [-Debugger] [-PSHost] [-PassThru] [<CommonParameters>]
```

### removeAllListenersSet

```
Set-TraceSource [-Name] <String[]> [-RemoveListener <String[]>] [<CommonParameters>]
```

### removeFileListenersSet

```
Set-TraceSource [-Name] <String[]> [-RemoveFileListener <String[]>] [<CommonParameters>]
```

## DESCRIPTION

**TraceSource 指令程式會設定** 、啟動和停止 PowerShell 元件的追蹤。
您可以使用它來指定要追蹤的元件和傳送追蹤輸出的位置。

## 範例

### 範例1：追蹤 ParameterBinding 元件

```
PS C:\> Set-TraceSource -Name "ParameterBinding" -Option ExecutionFlow -PSHost -ListenerOption "ProcessId,TimeStamp"
```

此命令會啟動 PowerShell ParameterBinding 元件的追蹤。
它會使用 *Name* 參數來指定追蹤來源、選取 ExecutionFlow 追蹤事件的 *Option* 參數，並使用 *PSHost* 參數來選取將輸出傳送至主控台的 PowerShell 主機接聽程式。
*ListenerOption* 參數會將 ProcessID 和 TimeStamp 值加入到追蹤訊息前置詞。

### 範例2：停止追蹤

```
PS C:\> Set-TraceSource -Name "ParameterBinding" -RemoveListener "Host"
```

此命令會停止追蹤 PowerShell 的 ParameterBinding 元件。
它會使用 *Name* 參數來識別正在追蹤的元件，以及使用 *RemoveListener* 參數來識別追蹤接聽程式。

## PARAMETERS

### -Debugger

指出此 Cmdlet 會將追蹤輸出傳送至偵錯工具。
您可以在任何使用者模式或核心模式偵錯工具或 Microsoft Visual Studio 中檢視輸出。
這個參數也會選取預設的追蹤接聽程式。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: optionsSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

指定此 Cmdlet 將追蹤輸出傳送至其中的檔案。
這個參數也會選取檔案追蹤接聽程式。
如果您使用這個參數來啟動追蹤，請使用 *RemoveFileListener* 參數來停止追蹤。

```yaml
Type: System.String
Parameter Sets: optionsSet
Aliases: PSPath, Path

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

指出此 Cmdlet 會覆寫唯讀檔案。
搭配 *FilePath* 參數使用。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: optionsSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ListenerOption

在輸出中，將選擇性資料指定為每個追蹤訊息的前置詞。
此參數可接受的值為：

- 無
- LogicalOperationStack
- Datetime
- 時間戳記
- ProcessId
- ThreadId
- 呼叫堆疊

預設值為 None。

如果要指定多個選項，請以逗點加以區隔，但不含空格，並將其括在引號中，例如 "ProcessID,ThreadID"。

```yaml
Type: System.Diagnostics.TraceOptions
Parameter Sets: optionsSet
Aliases:
Accepted values: None, LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

指定要追蹤的元件。
輸入每個元件的追蹤來源名稱。
允許使用萬用字元。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Option

指定要追蹤的事件種類。
此參數可接受的值為：

- 無
- 建構函式
- 處置
- 完成項
- 方法
- 屬性
- 委派
- 事件
- 例外狀況
- 鎖定
- 錯誤
- Errors
- 警告
- 「詳細資訊」
- WriteLine
- 資料
- 範圍
- ExecutionFlow
- Assert
- 全部

All 為預設值。

下列的值為其他值的組合：

- ExecutionFlow：(Constructor、Dispose、Finalizer、Method、Delegates、Events 及 Scope)
- Data：(Constructor、Dispose、Finalizer、Property、Verbose 及 WriteLine)
- Errors：(Error 和 Exception)。

如果要指定多個選項，請以逗點加以區隔，但不含空格，並將其括在引號中，例如 "Constructor,Dispose"。

```yaml
Type: System.Management.Automation.PSTraceSourceOptions
Parameter Sets: optionsSet
Aliases:
Accepted values: None, Constructor, Dispose, Finalizer, Method, Property, Delegates, Events, Exception, Lock, Error, Errors, Warning, Verbose, WriteLine, Data, Scope, ExecutionFlow, Assert, All

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

傳回代表您正在使用之項目的物件。
根據預設，此 Cmdlet 不會產生任何輸出。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: optionsSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PSHost

表示，此 Cmdlet 會將追蹤輸出傳送至 PowerShell 主機。
這個參數也會選取 PSHost 追蹤接聽程式。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: optionsSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RemoveFileListener

藉由移除與指定檔案相關聯的檔案追蹤接聽程式來停止追蹤。
輸入追蹤輸出檔的路徑和檔案名稱。

```yaml
Type: System.String[]
Parameter Sets: removeFileListenersSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RemoveListener

藉由移除追蹤接聽程式來停止追蹤。

使用 *RemoveListener* 的下列值：

- 若要移除 PSHost (主控台) ，請輸入 `Host` 。
- 若要移除偵錯工具，請輸入 `Debug` 。
- 若要移除所有追蹤接聽程式，請輸入 `*` 。

若要移除檔案追蹤接聽程式，請使用 *RemoveFileListener* 參數。

```yaml
Type: System.String[]
Parameter Sets: removeAllListenersSet
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

您可以使用管線將包含名稱的字串傳送至 **TraceSource** 。

## 輸出

### 無或 System.Management.Automation.PSTraceSource

當您使用 *PassThru* 參數時， **TraceSource** 會產生代表追蹤會話的 **system.management.automation.pstracesource** 物件。
否則，此 Cmdlet 不會產生任何輸出。

## 注意

* 追蹤是開發人員用來偵錯及改善程式的方法。 當進行追蹤時，程式會產生有關內部處理中每個步驟的詳細訊息。

  PowerShell 追蹤 Cmdlet 是設計來協助 PowerShell 開發人員，但它們可供所有使用者使用。
它們可讓您監視 PowerShell 功能的幾乎每個層面。

  追蹤來源是每個 PowerShell 元件的一部分，可管理追蹤並產生元件的追蹤訊息。
如果要追蹤元件，您必須識別其追蹤來源。

  追蹤接聽程式會接收追蹤的輸出，並將其顯示給使用者。
您可以選擇將追蹤資料傳送至使用者模式或核心模式的偵錯工具、主控台、檔案，或從 **TraceListener** 類別衍生的自訂接聽程式。

* 若要啟動追蹤，請使用 *Name* 參數來指定追蹤來源和 *FilePath* 、 *偵錯工具* 或 *PSHost* 參數，以指定 (輸出) 目的地的接聽程式。 您可以使用 *Options* 參數來判斷所追蹤的事件種類，以及用來設定追蹤輸出的 *ListenerOption* 參數。
* 若要變更追蹤的設定，請輸入 **TraceSource** 命令，就像開始追蹤一樣。 PowerShell 辨識出追蹤來源已在追蹤中。 它會停止追蹤、新增設定，並啟動或重新啟動追蹤。
* 若要停止追蹤，請使用 *RemoveListener* 參數。 若要停止使用檔案接聽程式的追蹤 (使用 *FilePath* 參數) 啟動的追蹤，請使用 *RemoveFileListener* 參數。 當您移除接聽程式，追蹤會隨即停止。
* 如果要判斷可追蹤的元件，請使用 Get-TraceSource。 當元件正在使用中時，每個模組的追蹤來源會自動載入，而且會出現在 **TraceSource** 的輸出中。

## 相關連結

[Get-TraceSource](Get-TraceSource.md)

[Trace-Command](Trace-Command.md)
