---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/24/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-psbreakpoint?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSBreakpoint
ms.openlocfilehash: 3f6720ee2235438a3f71c4efd6fb4083360bd520
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204403"
---
# Set-PSBreakpoint

## 概要
在行、命令或變數上設定中斷點。

## SYNTAX

### Line (預設值)

```
Set-PSBreakpoint [-Action <ScriptBlock>] [[-Column] <Int32>] [-Line] <Int32[]> [-Script] <String[]>
 [<CommonParameters>]
```

### Command

```
Set-PSBreakpoint [-Action <ScriptBlock>] -Command <String[]> [[-Script] <String[]>] [<CommonParameters>]
```

### 變數

```
Set-PSBreakpoint [-Action <ScriptBlock>] [[-Script] <String[]>] -Variable <String[]>
 [-Mode <VariableAccessMode>] [<CommonParameters>]
```

## DESCRIPTION

Cmdlet 會在 `Set-PSBreakpoint` 腳本中或在目前會話中執行的任何命令中設定中斷點。 在另一個中斷點停止時，您可以使用，在 `Set-PSBreakpoint` 執行腳本或執行命令之前，或在調試期間設定中斷點。

`Set-PSBreakpoint` 無法在遠端電腦上設定中斷點。 若要在遠端電腦上執行指令碼偵錯，請將指令碼複製到本機電腦，然後在本機偵錯。

每個 `Set-PSBreakpoint` 命令都會建立下列三種中斷點類型的其中一種：

- 行中斷點：在特定行和資料行座標上設定中斷點。
- 命令中斷點-在命令和函式上設定中斷點。
- 變數中斷點-在變數上設定中斷點。

您可以在單一命令中的多行、命令或變數上設定中斷點 `Set-PSBreakpoint` ，但每個 `Set-PSBreakpoint` 命令只會設定一種類型的中斷點。

PowerShell 會在中斷點暫時停止執行，並將控制權交給偵錯工具。 命令提示字元會變更為 `DBG\>` ，而且會有一組偵錯工具命令可供使用。 不過，您可以使用 **Action** 參數來指定替代回應，例如中斷點的條件或執行其他工作（例如記錄或診斷）的指示。

此 `Set-PSBreakpoint` Cmdlet 是專為偵測 PowerShell 腳本而設計的數個 Cmdlet 之一。
如需 PowerShell 偵錯工具的詳細資訊，請參閱 [about_Debuggers](../Microsoft.PowerShell.Core/About/about_Debuggers.md)。

## 範例

### 範例1：在行上設定中斷點

此範例會在 Sample.ps1 腳本中的第5行設定中斷點。 當腳本執行時，會在執行第5行之前立即停止執行。

```powershell
Set-PSBreakpoint -Script "sample.ps1" -Line 5
```

```output
Column     : 0
Line       : 5
Action     :
Enabled    : True
HitCount   : 0
Id         : 0
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

當您以行號設定新的中斷點時，此 `Set-PSBreakpoint` Cmdlet 會產生行中斷點物件 ( **System.management.automation.linebreakpoint** ) ，其中包含中斷點識別碼和計數。

### 範例2：在函式上設定中斷點

此範例會在 Sample.ps1 Cmdlet 的函式上建立命令中斷點 `Increment` 。 在每次呼叫指定函式之前，指令碼就會停止執行。

```powershell
Set-PSBreakpoint -Command "Increment" -Script "sample.ps1"
```

```Output
Command    : Increment
Action     :
Enabled    : True
HitCount   : 0
Id         : 1
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

結果就是一個命令中斷點物件。 在腳本執行之前， **擊中數** 屬性的值為0。

### 範例3：在變數上設定中斷點

這個範例會在 Sample.ps1 腳本的 **伺服器** 變數上設定中斷點。 它會使用值為 **ReadWrite** 的 **Mode** 參數，在讀取變數的值且剛好在值變更之前停止執行。

```powershell
Set-PSBreakpoint -Script "sample.ps1" -Variable "Server" -Mode ReadWrite
```

### 範例4：在以指定文字開頭的每個命令上設定中斷點

這個範例會在 Sample.ps1 腳本中的每個命令上設定一個中斷點，其開頭為 "write" （例如） `Write-Host` 。

```powershell
Set-PSBreakpoint -Script Sample.ps1 -Command "write*"
```

### 範例5：根據變數的值設定中斷點

此範例 `DiskTest` 只會在變數的值大於2時，才會在 Test.ps1 腳本的函式中停止執行 `$Disk` 。

```powershell
Set-PSBreakpoint -Script "test.ps1" -Command "DiskTest" -Action { if ($Disk -gt 2) { break } }
```

**動作** 的值是腳本區塊，會測試函式中的變數值 `$Disk` 。

`break`如果符合條件，此動作會使用關鍵字來停止執行。 替代 (和預設) **繼續** 。

### 範例6：在函式上設定中斷點

此範例會在函數上設定中斷點 `CheckLog` 。 因為命令並未指定指令碼，所以會在於目前工作階段中執行的任何項目上設定中斷點。 偵錯工具會在呼叫函式時中斷，而不是在宣告時中斷。

```
PS> Set-PSBreakpoint -Command "checklog"
Id       : 0
Command  : checklog
Enabled  : True
HitCount : 0
Action   :

function CheckLog {
>> get-eventlog -log Application |
>> where {($_.source -like "TestApp") -and ($_.Message -like "*failed*")}
>>}
>>
PS> Checklog
DEBUG: Hit breakpoint(s)
DEBUG:  Function breakpoint on 'prompt:Checklog'
```

### 範例7：在多行上設定中斷點

此範例會在 Sample.ps1 腳本中設定三個行中斷點。 它會在指令碼中每一指定行上的欄位 2 位置設定一個中斷點。 **Action** 參數中指定的動作會套用至所有中斷點。

```powershell
PS C:\> Set-PSBreakpoint -Script "sample.ps1" -Line 1, 14, 19 -Column 2 -Action {&(log.ps1)}
```

```Output
Column     : 2
Line       : 1
Action     :
Enabled    : True
HitCount   : 0
Id         : 6
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1


Column     : 2
Line       : 14
Action     :
Enabled    : True
HitCount   : 0
Id         : 7
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1


Column     : 2
Line       : 19
Action     :
Enabled    : True
HitCount   : 0
Id         : 8
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

## PARAMETERS

### -Action

指定在每個中斷點執行的命令，而非中斷。 輸入包含命令的指令碼區塊。 您可以使用此參數設定條件式中斷點或執行其他工作，例如測試或記錄。

如果省略此參數或未指定任何動作，就會在中斷點停止執行並啟動偵錯工具。

使用 **action** 參數時，action 腳本區塊會在每個中斷點執行。 除非指令碼區塊包含 Break 關鍵字，否則不會停止執行。 如果您在指令碼區塊中使用 Continue 關鍵字，就會繼續執行到下一個中斷點為止。

如需詳細資訊，請參閱 [about_Script_Blocks](../Microsoft.PowerShell.Core/About/about_Script_Blocks.md)、 [about_Break](../Microsoft.PowerShell.Core/About/about_Break.md)和 [about_Continue](../Microsoft.PowerShell.Core/About/about_Continue.md)。

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Column

指定指令碼檔案中，執行將停止之欄位的欄位編號。 請只輸入一個欄位編號。 預設值為欄位 1。

資料行值會與 **Line** 參數的值搭配使用，以指定中斷點。 如果 **Line** 參數指定多行， **column** 參數會在每個指定行上的指定資料行上設定中斷點。 PowerShell 會在包含指定行和資料行位置之字元的語句或運算式之前停止執行。

欄位是從左上角邊界處從欄位編號 1 (不是 0) 開始計算。 如果您指定指令碼中不存在的欄位，系統並不會宣告錯誤，但中斷點永遠不會執行。

```yaml
Type: System.Int32
Parameter Sets: Line
Aliases:

Required: False
Position: 2
Default value: 1
Accept pipeline input: False
Accept wildcard characters: False
```

### -Command

設定命令中斷點。 輸入 Cmdlet 名稱，例如 `Get-Process` 或函數名稱。 允許使用萬用字元。

執行會在每個命令的每個執行個體執行之前停止。 如果命令是函式，執行就會在每次呼叫函式時，以及在 BEGIN、PROCESS 及 END 區段中停止。

```yaml
Type: System.String[]
Parameter Sets: Command
Aliases: C

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Line

在指令碼中設定行中斷點。 輸入一個或多個行編號，並使用逗號分隔。 PowerShell 會在每個指定行開始執行語句之前立即停止。

行是從指令碼檔案左上角邊界從行編號 1 (不是 0) 開始計算。
如果您指定了空白行，執行就會在下一個非空白行之前停止。 如果行超出範圍，就永遠不會命中中斷點。

```yaml
Type: System.Int32[]
Parameter Sets: Line
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Mode

指定觸發變數中斷點的存取模式。 預設值為 **Write** 。

只有當命令中使用 **Variable** 參數時，此參數才有效。 此模式適用於命令中設定的所有中斷點。 此參數可接受的值為：

- 在將新值寫入變數之前，立即進行 **寫入** -停止執行。
- 讀取-在讀取變數時執行 **讀取** ，也就是在存取它的值時，要指派、顯示或使用這些變數的值。 在讀取模式中，變數的值變更時不會停止執行。
- **ReadWrite** -在讀取或寫入變數時停止執行。

```yaml
Type: System.Management.Automation.VariableAccessMode
Parameter Sets: Variable
Aliases:
Accepted values: Read, Write, ReadWrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Script

指定此 Cmdlet 在中設定中斷點的指令檔陣列。 輸入一個或多個指令碼檔案的路徑與檔案名稱。 如果檔案是在目前的目錄中，您可以省略路徑。
允許使用萬用字元。

根據預設，會在於目前工作階段中執行的任何命令上設定變數中斷點與命令中斷點。 只有設定行中斷點時才需要此參數。

```yaml
Type: System.String[]
Parameter Sets: Line, Command, Variable
Aliases:

Required: True (Line), False (Command, Variable)
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Variable

指定此 Cmdlet 在上設定中斷點的變數陣列。 輸入以逗號分隔的變數清單，而不使用貨幣符號 (`$`) 。

使用 **mode** 參數來判斷觸發中斷點的存取模式。 預設模式 (Write) 會在將新值寫入變數之前停止執行。

```yaml
Type: System.String[]
Parameter Sets: Variable
Aliases: V

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無
您無法透過管道傳送輸入 `Set-PSBreakpoint` 。

## 輸出

### 中斷點物件 (System.Management.Automation.LineBreakpoint、System.Management.Automation.VariableBreakpoint、System.Management.Automation.CommandBreakpoint)

`Set-PSBreakpoint` 傳回物件，表示它所設定的每一個中斷點。

## 注意

- `Set-PSBreakpoint` 無法在遠端電腦上設定中斷點。 若要在遠端電腦上執行指令碼偵錯，請將指令碼複製到本機電腦，然後在本機偵錯。
- 當您在一個以上的行、命令或變數上設定中斷點時，會 `Set-PSBreakpoint` 為每個專案產生中斷點物件。
- 在命令提示字元設定函式或變數的中斷點時，您可以在建立函式或變數之前或之後設定中斷點。

## 相關連結

[Disable-PSBreakpoint](Disable-PSBreakpoint.md)

[Enable-PSBreakpoint](Enable-PSBreakpoint.md)

[Get-PSBreakpoint](Get-PSBreakpoint.md)

[Get-PSCallStack](Get-PSCallStack.md)

[Remove-PSBreakpoint](Remove-PSBreakpoint.md)
