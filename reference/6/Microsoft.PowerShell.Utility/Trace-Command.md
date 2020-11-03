---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/trace-command?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Trace-Command
ms.openlocfilehash: 9147be62c881e81a4ff1352a1b9fe7a34d2610cd
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204391"
---
# Trace-Command

## 概要
設定並啟動指定運算式或命令的追蹤。

## SYNTAX

### expressionSet (預設值)

```
Trace-Command [-InputObject <PSObject>] [-Name] <String[]> [[-Option] <PSTraceSourceOptions>]
 [-Expression] <ScriptBlock> [-ListenerOption <TraceOptions>] [-FilePath <String>] [-Force] [-Debugger]
 [-PSHost] [<CommonParameters>]
```

### commandSet

```
Trace-Command [-InputObject <PSObject>] [-Name] <String[]> [[-Option] <PSTraceSourceOptions>]
 [-Command] <String> [-ArgumentList <Object[]>] [-ListenerOption <TraceOptions>] [-FilePath <String>] [-Force]
 [-Debugger] [-PSHost] [<CommonParameters>]
```

## DESCRIPTION
指令程式會設定 `Trace-Command` 並啟動指定運算式或命令的追蹤。
它的運作方式類似 Set-TraceSource，但只適用於指定的命令。

## 範例

### 範例1：追蹤元資料處理、參數系結和運算式

此範例會開始追蹤元資料處理、參數系結，以及建立和終結運算式的 Cmdlet `Get-Process Notepad` 。

```powershell
Trace-Command -Name metadata,parameterbinding,cmdlet -Expression {Get-Process Notepad} -PSHost
```

它會使用 **Name** 參數來指定追蹤來源，使用 **Expression** 參數指定命令，並使用 **PSHost** 參數將輸出傳送至主控台。 因為它並未指定任何追蹤選項或接聽程式選項，所以此命令會使用預設值：

- 所有追蹤選項
- 無接聽程式選項

### 範例2：追蹤 ParameterBinding 作業的動作

此範例會追蹤 PowerShell 的 **ParameterBinding** 作業動作，同時處理 `Get-Alias` 接受管線輸入的運算式。

```powershell
$A = "i*"
Trace-Command ParameterBinding {Get-Alias $Input} -PSHost -InputObject $A
```

在中 `Trace-Command` ， **InputObject** 參數會將物件傳遞至追蹤期間正在處理的運算式。

第一個命令會將字串儲存 `i*` 在 `$A` 變數中。 第二個命令會使用 `Trace-Command` Cmdlet 搭配 ParameterBinding 追蹤來源。 **PSHost** 參數會將輸出傳送至主控台。

正在處理的運算式是 `Get-Alias $Input` `$Input` 與 **InputObject** 參數相關聯的變數。 **InputObject** 參數會將變數傳遞 `$A` 給運算式。 實際上，追蹤期間處理的命令為 `Get-Alias -InputObject $A" or "$A | Get-Alias` 。

## PARAMETERS

### -ArgumentList

指定要追蹤之命令的參數和參數值。 **ArgumentList** 的別名是 **Args** 。 此功能特別適用於動態參數偵錯。

如需有關 **ArgumentList** 行為的詳細資訊，請參閱 [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md#splatting-with-arrays)。

```yaml
Type: System.Object[]
Parameter Sets: commandSet
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Command

指定追蹤期間處理的命令。

```yaml
Type: System.String
Parameter Sets: commandSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Debugger

指出此 Cmdlet 會將追蹤輸出傳送至偵錯工具。 您可以在任何使用者模式或核心模式的偵錯工具或 Visual Studio 中檢視輸出。 這個參數也會選取預設的追蹤接聽程式。

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

### -Expression

指定追蹤期間處理的運算式。 以大括弧括住運算式 (`{}`) 。

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: expressionSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

指定 Cmdlet 將追蹤輸出傳送至其中的檔案。 這個參數也會選取檔案追蹤接聽程式。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath, Path

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

強制執行命令而不要求使用者確認。 搭配 **FilePath** 參數使用。 即使使用 **Force** 參數，Cmdlet 也無法覆寫安全性限制。

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

### -InputObject

指定在追蹤期間處理的運算式的輸入。 您可以輸入代表運算式接受之輸入的變數，或透過管線傳送物件。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ListenerOption

在輸出中，將選擇性資料指定為每個追蹤訊息的前置詞。 此參數可接受的值為：

- 無
- LogicalOperationStack
- Datetime
- 時間戳記
- ProcessId
- ThreadId
- 呼叫堆疊

預設值為 **None** 。

如果要指定多個選項，請以逗點加以區隔，但不含空格，並將其括在引號中，例如 "ProcessID,ThreadID"。

```yaml
Type: System.Diagnostics.TraceOptions
Parameter Sets: (All)
Aliases:
Accepted values: None, LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

指定要追蹤的 PowerShell 元件陣列。 輸入每個元件的追蹤來源名稱。 允許使用萬用字元。 若要尋找電腦上的追蹤來源，請輸入 `Get-TraceSource` 。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Option

決定追蹤的事件類型。 此參數可接受的值為：

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
Parameter Sets: (All)
Aliases:
Accepted values: None, Constructor, Dispose, Finalizer, Method, Property, Delegates, Events, Exception, Lock, Error, Errors, Warning, Verbose, WriteLine, Data, Scope, ExecutionFlow, Assert, All

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PSHost

指出此 Cmdlet 會將追蹤輸出傳送至 PowerShell 主機。 這個參數也會選取 PSHost 追蹤接聽程式。

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

### System.Management.Automation.PSObject

您可以透過管線將表示輸入的物件傳送至運算式 `Trace-Command` 。

## 輸出

### System.Management.Automation.PSObject

在偵錯資料流中傳回命令追蹤。

## 注意

- 追蹤是開發人員用來偵錯及改善程式的方法。 當進行追蹤時，程式會產生有關內部處理中每個步驟的詳細訊息。

- PowerShell 追蹤 Cmdlet 是設計來協助 PowerShell 開發人員，但它們可供所有使用者使用。 它們可讓您監視殼層功能的幾乎各個層面。

- 若要尋找已啟用追蹤的 PowerShell 元件，請輸入 `Get-Help Get-TraceSource` 。

  追蹤來源是每個 PowerShell 元件的一部分，可管理追蹤並產生元件的追蹤訊息。 如果要追蹤元件，您必須識別其追蹤來源。

  追蹤接聽程式會接收追蹤的輸出，並將其顯示給使用者。 您可以選擇將追蹤資料傳送至使用者模式或核心模式的偵錯工具、主機或主控台、檔案，或是從 **TraceListener** 類別衍生的自訂接聽程式。

- 當您使用 commandSet 參數集時，PowerShell 會處理命令，就像在管線中處理一樣。 例如，命令探索不會針對每個連入物件重複。

- **Name** 、 **Expression** 、 **Option** 及 **Command** 參數的名稱是選擇性的。 如果您省略參數名稱，未命名的參數值必須以下列順序顯示： **Name** 、 **Expression** 、 **Option** 或 **Name** 、 **Command****選項** 。 如果包含參數名稱，參數可以任何順序顯示。

## 相關連結

[Get-TraceSource](Get-TraceSource.md)

[Measure-Command](Measure-Command.md)

[Set-TraceSource](Set-TraceSource.md)
