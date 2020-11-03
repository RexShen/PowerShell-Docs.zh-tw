---
description: 描述 PowerShell 偵錯工具。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 08/06/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_debuggers?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Debuggers
ms.openlocfilehash: 6765c33e4508e19dfca7f291f8452f1bb4730747
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207344"
---
# <a name="about-debuggers"></a>關於偵錯工具

## <a name="short-description"></a>簡短描述
描述 PowerShell 偵錯工具。

## <a name="long-description"></a>詳細描述

偵錯工具是指在腳本執行時檢查腳本，以識別並更正腳本指令中錯誤的流程。 PowerShell 偵錯工具可協助您檢查和識別腳本、函式、命令、PowerShell Desired State Configuration (DSC) 設定或運算式中的錯誤和效率不佳。

從 PowerShell 5.0 開始，已更新 PowerShell 偵錯工具，以在主控台或 Windows PowerShell ISE 遠端電腦上執行的腳本、函式、命令、設定或運算式。 您可以執行 `Enter-PSSession` 以啟動互動式遠端 PowerShell 會話，以便在遠端電腦上設定中斷點和偵錯工具腳本檔案和命令。 `Enter-PSSession` 功能已更新為可讓您重新連線，並輸入在遠端電腦上執行腳本或命令的中斷連線會話。 如果執行中的腳本叫用中斷點，您的用戶端會話就會自動啟動偵錯工具。 如果執行腳本的已中斷連線會話已到達中斷點，並在中斷點停止， `Enter-PSSession` 則在您重新連線到會話之後，會自動啟動命令列偵錯工具。

您可以使用 PowerShell 偵錯工具的功能來檢查 PowerShell 腳本、函式、命令或運算式是否正在執行。 PowerShell 偵錯工具包含一組 Cmdlet，可讓您設定中斷點、管理中斷點，以及查看呼叫堆疊。

## <a name="debugger-cmdlets"></a>偵錯工具 Cmdlet

PowerShell 偵錯工具包含下列一組 Cmdlet：

- `Set-PSBreakpoint`：在行、變數和命令上設定中斷點。
- `Get-PSBreakpoint`：取得目前會話中的中斷點。
- `Disable-PSBreakpoint`：關閉目前會話中的中斷點。
- `Enable-PSBreakpoint`：重新啟用目前會話中的中斷點。
- `Remove-PSBreakpoint`：刪除目前會話中的中斷點。
- `Get-PSCallStack`：顯示目前的呼叫堆疊。

## <a name="starting-and-stopping-the-debugger"></a>啟動和停止偵錯工具

若要啟動偵錯工具，請設定一或多個中斷點。 然後，執行您要進行偵錯工具的腳本、命令或函數。

當您到達中斷點時，執行會停止，並將控制權轉換至偵錯工具。

若要停止偵錯工具，請執行腳本、命令或函數，直到完成為止。 或者，輸入 `stop` 或 `t` 。

### <a name="debugger-commands"></a>偵錯工具命令

當您在 PowerShell 主控台中使用偵錯工具時，請使用下列命令來控制執行。 在 Windows PowerShell ISE 中，使用 [調試] 功能表上的命令。

注意：如需有關如何在其他主應用程式中使用偵錯工具的詳細資訊，請參閱主機應用程式檔集。

- `s`， `StepInto` ：執行下一個語句，然後停止。

- `v``StepOver`：執行下一個語句，但略過函數和調用。 這會執行已跳過的陳述式，但不會逐步執行。

- `Ctrl+Break`： (在 ISE 中中斷所有) 會中斷到 PowerShell 主控台或 Windows PowerShell ISE 內的執行中腳本。 請注意<kbd>Ctrl</kbd>， + Windows PowerShell 2.0、3.0 和4.0 中的 Ctrl<kbd>Break</kbd>會關閉程式。 Break 全都適用于本機和遠端互動執行的腳本。

- `o`：從目前的函式中 `StepOut` 移出; 如果是 nested，則向上移一層。 如果在主體中，它會繼續到結束或下一個中斷點。 這會執行已跳過的陳述式，但不會逐步執行。

- `c``Continue`：會繼續執行，直到腳本完成或到達下一個中斷點為止。 這會執行已跳過的陳述式，但不會逐步執行。

- `l``List`：顯示正在執行之腳本的一部分。 依預設，它會顯示目前的行、前五行，以及10個後續的行。
  若要繼續列出腳本，請按 ENTER。

- `l <m>``List`：顯示以指定的行號開頭之腳本的16行 `<m>` 。

- `l <m> <n>``List`：顯示 `<n>` 腳本的行，以指定的行號為開頭 `<m>` 。

- `q`、 `Stop` 、 `Exit` ：停止執行腳本，並結束偵錯工具。 如果您要藉由執行指令程式來進行工作的偵錯工具，命令會中斷偵錯工具的連結 `Debug-Job` `Exit` ，並允許工作繼續執行。

- `k``Get-PsCallStack`：顯示目前的呼叫堆疊。

- `<Enter>`：如果步驟 (s) 、跨距 (v) 或清單 (l) ，則重複最後一個命令。 否則，代表提交動作。

- `?``h`：顯示偵錯工具命令說明。

若要結束偵錯工具，您可以使用 Stop (q) 。

從 PowerShell 5.0 開始，您可以執行 [結束] 命令來結束您藉由執行或來啟動的嵌套式偵錯工具 `Debug-Job` `Debug-Runspace` 。

藉由使用這些偵錯工具命令，您可以執行腳本、停止關注點、檢查變數值和系統狀態，然後繼續執行腳本，直到找出問題為止。

注意：如果您逐步執行具有重新導向運算子的語句，例如 ">"，則 PowerShell 偵錯工具會逐步執行腳本中所有其餘的語句。

顯示腳本變數的值

當您在偵錯工具中時，您也可以輸入命令、顯示變數的值、使用指令程式，以及在命令列執行腳本。

除了下列自動變數之外，您可以在正在進行調試的腳本中顯示所有變數的目前值：

```powershell
$_
$Args
$Input
$MyInvocation
$PSBoundParameters
```

如果您嘗試顯示上述任何變數的值，您會取得偵錯工具所使用之內部管線中的變數值，而不是指令碼中的變數值。

若要針對正在進行調試的腳本顯示這些變數的值，請在腳本中，將自動變數的值指派給新的變數。 然後，您可以顯示新變數的值。

例如，套用至物件的

```powershell
$scriptArgs = $Args
$scriptArgs
```

在本主題的範例中， `$MyInvocation` 會重新指派變數的值，如下所示：

```powershell
$scriptname = $MyInvocation.MyCommand.Path
```

## <a name="the-debugger-environment"></a>偵錯工具環境

當您到達中斷點時，您會進入偵錯工具環境。 命令提示字元會變更，使其開頭為 "[DBG]："。

如需自訂提示的詳細資訊，請參閱 [about_Prompts](about_prompts.md)。

此外，在某些主機應用程式（例如 PowerShell 主控台）中 (但不是在 Windows PowerShell 整合式腳本環境 [ISE] ) 中，會開啟內嵌的提示以進行調試。 您可以在命令提示字元中出現重複的大於字元 (ASCII 62) 來偵測嵌套提示。

例如，以下是 PowerShell 主控台中的預設偵錯工具提示：

```
[DBG]: PS (get-location)>>>
```

您可以使用自動變數來尋找嵌套層級 `$NestedPromptLevel` 。

此外，自動變數 `$PSDebugContext` 是在區域範圍中定義的。 您可以使用變數的存在， `$PsDebugContext` 判斷您是否在偵錯工具中。

例如：

```powershell
if ($PSDebugContext) {"Debugging"} else {"Not Debugging"}
```

您可以 `$PSDebugContext` 在偵錯工具中使用變數的值。

```
[DBG]: PS>>> $PSDebugContext.InvocationInfo

Name   CommandLineParameters  UnboundArguments  Location
----   ---------------------  ----------------  --------
=      {}                     {}                C:\ps-test\vote.ps1 (1)
```

## <a name="debugging-and-scope"></a>調試和範圍

中斷偵錯工具並不會變更您正在操作的範圍，但當您到達腳本中的中斷點時，您會移至腳本範圍中。 腳本範圍是您執行偵錯工具之範圍的子系。

若要尋找腳本範圍中定義的變數和別名，請使用或 Cmdlet 的 Scope 參數 `Get-Alias` `Get-Variable` 。

例如，下列命令會取得本機 (腳本) 範圍中的變數：

```powershell
Get-Variable -scope 0
```

您可以將命令縮寫為：

```powershell
gv -s 0
```

這是只查看您在腳本中定義且在偵錯工具中定義之變數的實用方式。

在命令列進行偵錯工具

當您設定變數中斷點或命令中斷點時，您只能在腳本檔案中設定中斷點。 不過，根據預設，中斷點會設定在目前會話中執行的任何作業。

例如，如果您在變數上設定中斷點 `$name` ，偵錯工具會在您 `$name` 執行的任何腳本、命令、函數、腳本 Cmdlet 或運算式中的任何變數上中斷，直到您停用或移除中斷點為止。

這可讓您在更實際的內容中進行腳本的偵測，這些內容可能會受到會話和使用者設定檔中的函式、變數和其他腳本影響。

行中斷點是腳本檔專用的，因此只會在腳本檔案中設定。

## <a name="debugging-functions"></a>調試函數

當您在具有、和區段的函式上設定中斷點時 `Begin` `Process` `End` ，偵錯工具會在每個區段的第一行中斷。

例如：

```powershell
function test-cmdlet {
    begin {
        write-output "Begin"
    }
    process {
        write-output "Process"
    }
    end {
        write-output "End"
    }
}

C:\PS> Set-PSBreakpoint -command test-cmdlet

C:\PS> test-cmdlet

Begin
Entering debug mode. Use h or ? for help.

Hit Command breakpoint on 'prompt:test-cmdlet'

test-cmdlet

[DBG]: C:\PS> c
Process
Entering debug mode. Use h or ? for help.

Hit Command breakpoint on 'prompt:test-cmdlet'

test-cmdlet

[DBG]: C:\PS> c
End
Entering debug mode. Use h or ? for help.

Hit Command breakpoint on 'prompt:test-cmdlet'

test-cmdlet

# [DBG]: C:\PS>
```

## <a name="debugging-remote-scripts"></a>對遠端腳本進行調試

從 PowerShell 5.0 開始，您可以在遠端會話、主控台或 Windows PowerShell ISE 中執行 PowerShell 偵錯工具。
`Enter-PSSession` 功能已更新為可讓您重新連接並輸入在遠端電腦上執行的已中斷連線會話，以及目前正在執行的腳本。 如果執行中的腳本叫用中斷點，您的用戶端會話就會自動啟動偵錯工具。

以下範例會示範其運作方式，並在第6、11、22和25行的腳本中設定中斷點。 請注意，在此範例中，當偵錯工具啟動時，有兩個識別提示：會話執行所在的電腦名稱稱，以及可讓您知道您處於偵錯工具模式的 DBG 提示。

```powershell
Enter-Pssession -Cn localhost
[localhost]: PS C:\psscripts> Set-PSBreakpoint .\ttest19.ps1 6,11,22,25

ID Script          Line     Command          Variable          Action
-- ------          ----     -------          --------          ------
0 ttest19.ps1          6
1 ttest19.ps1          11
2 ttest19.ps1          22
3 ttest19.ps1          25

[localhost]: PS C:\psscripts> .\ttest19.ps1
Hit Line breakpoint on 'C:\psscripts\ttest19.ps1:11'

At C:\psscripts\ttest19.ps1:11 char:1
+ $winRMName = "WinRM"
# + ~

[localhost]: [DBG]: PS C:\psscripts>> list

6:      1..5 | foreach { sleep 1; Write-Output "hello2day $_" }
7:  }
# 8:

9:  $count = 10
10:  $psName = "PowerShell"
11:* $winRMName = "WinRM"
12:  $myVar = 102
# 13:

14:  for ($i=0; $i -lt $count; $i++)
15:  {
16:      sleep 1
17:      Write-Output "Loop iteration is: $i"
18:      Write-Output "MyVar is $myVar"
# 19:

20:      hello2day
# 21:


[localhost]: [DBG]: PS C:\psscripts>> stepover
At C:\psscripts\ttest19.ps1:12 char:1
+ $myVar = 102
# + ~

[localhost]: [DBG]: PS C:\psscripts>> quit
[localhost]: PS C:\psscripts> Exit-PSSession
PS C:\psscripts>
```

## <a name="examples"></a>範例

此測試腳本會偵測作業系統的版本，並顯示系統適當的訊息。 它包含函式、函式呼叫和變數。

下列命令會顯示測試腳本檔案的內容：

```powershell
PS C:\PS-test>  Get-Content test.ps1

function psversion {
  "PowerShell " + $PSVersionTable.PSVersion
  if ($PSVersionTable.PSVersion.Major -lt 6) {
    "Upgrade to PowerShell 6.0!"
  }
  else {
    "Have you run a background job today (start-job)?"
  }
}

$scriptName = $MyInvocation.MyCommand.Path
psversion
"Done $scriptName."
```

若要開始，請在腳本中的相關點設定中斷點，例如行、命令、變數或函數。

首先，在目前目錄中 Test.ps1 腳本的第一行建立行中斷點。

```powershell
PS C:\ps-test> Set-PSBreakpoint -line 1 -script test.ps1
```

您可以將此命令縮寫為：

```powershell
PS C:\ps-test> spb 1 -s test.ps1
```

此命令會傳回 ( **system.management.automation.linebreakpoint** ) 的行中斷點物件。

```
Column     : 0
Line       : 1
Action     :
Enabled    : True
HitCount   : 0
Id         : 0
Script     : C:\ps-test\test.ps1
ScriptName : C:\ps-test\test.ps1
```

現在，啟動腳本。

```powershell
PS C:\ps-test> .\test.ps1
```

當腳本到達第一個中斷點時，中斷點訊息會指出偵錯工具為作用中狀態。 它描述中斷點，並預覽腳本的第一行，也就是函式宣告。 命令提示字元也會變更，以指出偵錯工具有控制權。

預覽行包含預覽命令的腳本名稱和行號。

```powershell
Entering debug mode. Use h or ? for help.

Hit Line breakpoint on 'C:\ps-test\test.ps1:1'

test.ps1:1   function psversion {
# DBG>
```

使用 (s 的步驟命令) 執行腳本中的第一個語句，以及預覽下一個語句。 下一個語句會使用 `$MyInvocation` 自動變數，將變數的值設定 `$scriptName` 為腳本檔案的路徑和檔案名。

```powershell
DBG> s
test.ps1:11  $scriptName = $MyInvocation.MyCommand.Path
```

此時 `$scriptName` 不會填入變數，但您可以藉由顯示變數的值來確認變數的值。 此處的值為 `$null`。

```powershell
DBG> $scriptname
# DBG>
```

使用 (s 的其他步驟命令) 執行目前的語句，並預覽腳本中的下一個語句。 下一個語句會呼叫 PsVersion 函數。

```powershell
DBG> s
test.ps1:12  psversion
```

此時 `$scriptName` 會填入變數，但您可以藉由顯示變數的值來確認變數的值。 在此情況下，此值會設定為腳本路徑。

```powershell
DBG> $scriptName
C:\ps-test\test.ps1
```

使用其他步驟命令來執行函式呼叫。 按 ENTER 鍵，或輸入 "s" 進行步驟。

```powershell
DBG> s
test.ps1:2       "PowerShell " + $PSVersionTable.PSVersion
```

偵錯工具訊息包含函式中之語句的預覽。 若要執行這個語句並預覽函式中的下一個語句，您可以使用 `Step` 命令。 但在此情況下，請使用 StepOut 命令 (o) 。 它會完成函式 (的執行，除非它到達中斷點) ，並逐步執行至腳本中的下一個語句。

```powershell
DBG> o
Windows PowerShell 2.0
Have you run a background job today (start-job)?
test.ps1:13  "Done $scriptName"
```

因為我們是在腳本中的最後一個語句，所以 Step、StepOut 和 Continue 命令都有相同的效果。 在此情況下，請使用 StepOut (o) 。

```powershell
Done C:\ps-test\test.ps1
PS C:\ps-test>
```

StepOut 命令會執行最後一個命令。 標準命令提示字元指出偵錯工具已結束，並將控制權傳回給命令處理器。

現在，再次執行偵錯工具。 首先，若要刪除目前的中斷點，請使用 `Get-PsBreakpoint` 和 `Remove-PsBreakpoint` Cmdlet。  (如果您認為您可能會重複使用中斷點，請使用 `Disable-PsBreakpoint` Cmdlet 而不是 `Remove-PsBreakpoint` 。 ) 

```powershell
PS C:\ps-test> Get-PSBreakpoint| Remove-PSBreakpoint
```

您可以將此命令縮寫為：

```powershell
PS C:\ps-test> gbp | rbp
```

或者，藉由撰寫函數來執行命令，例如下列函式：

```powershell
function delbr { gbp | rbp }
```

現在，在變數上建立中斷點 `$scriptname` 。

```powershell
PS C:\ps-test> Set-PSBreakpoint -variable scriptname -script test.ps1
```

您可以將命令縮寫為：

```powershell
PS C:\ps-test> sbp -v scriptname -s test.ps1
```

現在，啟動腳本。 腳本到達變數中斷點。 預設模式為 [寫入]，因此會在變更變數值的語句之前停止執行。

```powershell
PS C:\ps-test> .\test.ps1
Hit Variable breakpoint on 'C:\ps-test\test.ps1:$scriptName'
(Write access)

test.ps1:11  $scriptName = $MyInvocation.MyCommand.Path
# DBG>
```

顯示變數目前的值 `$scriptName` ，也就是 `$null` 。

```powershell
DBG> $scriptName
# DBG>
```

使用步驟命令 (s) 執行填入變數的語句。
然後，顯示變數的新值 `$scriptName` 。

```powershell
DBG> $scriptName
C:\ps-test\test.ps1
```powershell

Use a Step command (s) to preview the next statement in the script.

```powershell
DBG> s
test.ps1:12  psversion
```

下一個語句是 PsVersion 函數的呼叫。 若要略過函式但仍執行它，請使用跨距命令 (v) 。 如果您在使用跨距時已在函式中，則不會有效。 會顯示函式呼叫，但不會執行。

```powershell
DBG> v
Windows PowerShell 2.0
Have you run a background job today (start-job)?
test.ps1:13  "Done $scriptName"
```

跨距命令會執行函式，並預覽腳本中的下一個語句，以列印最後一行。

使用 Stop 命令 (t) 結束偵錯工具。 命令提示字元會還原為標準的命令提示字元。

```powershell
C:\ps-test>
```

若要刪除中斷點，請使用 `Get-PsBreakpoint` 和 `Remove-PsBreakpoint` Cmdlet。

```powershell
PS C:\ps-test> Get-PSBreakpoint| Remove-PSBreakpoint
```

在 PsVersion 函式上建立新的命令中斷點。

```powershell
PS C:\ps-test> Set-PSBreakpoint -command psversion -script test.ps1
```

您可以將此命令縮寫為：

```powershell
PS C:\ps-test> sbp -c psversion -s test.ps1
```

現在，執行腳本。

```powershell
PS C:\ps-test> .\test.ps1
Hit Command breakpoint on 'C:\ps-test\test.ps1:psversion'

test.ps1:12  psversion
# DBG>
```

腳本會在函式呼叫中到達中斷點。 至此，尚未呼叫函數。 這讓您有機會使用的 Action 參數 `Set-PSBreakpoint` 來設定執行中斷點的條件，或是執行準備或診斷工作，例如開機記錄或叫用診斷或安全性腳本。

若要設定動作，請使用 Continue 命令 (c) 結束腳本，並使用 `Remove-PsBreakpoint` 命令來刪除目前的中斷點。  (中斷點是唯讀的，因此您無法將動作加入至目前的中斷點。 ) 

```powershell
DBG> c
Windows PowerShell 2.0
Have you run a background job today (start-job)?
Done C:\ps-test\test.ps1

PS C:\ps-test> Get-PSBreakpoint| Remove-PSBreakpoint
PS C:\ps-test>
```

現在，使用動作建立新的命令中斷點。 下列命令會使用動作來設定命令中斷點， `$scriptName` 此動作會在呼叫函式時記錄變數的值。 因為不會在動作中使用 Break 關鍵字，所以不會停止執行。  (倒引號 (') 是行接續字元。 ) 

```powershell
PS C:\ps-test> Set-PSBreakpoint -command psversion -script test.ps1  `
-action { add-content "The value of `$scriptName is $scriptName." `
-path action.log}
```

您也可以新增動作來設定中斷點的條件。 在下列命令中，只有當執行原則設定為 RemoteSigned 時，才會執行命令中斷點，這是限制最嚴格的原則，仍允許您執行腳本。  (倒引號 (') 是接續字元。 ) 

```powershell
PS C:\ps-test> Set-PSBreakpoint -script test.ps1 -command psversion `
-action { if ((Get-ExecutionPolicy) -eq "RemoteSigned") { break }}
```

動作中的 Break 關鍵字會指示偵錯工具執行中斷點。
您也可以使用 Continue 關鍵字，指示偵錯工具在不中斷的情況下執行。 因為 default 關鍵字是 Continue，所以您必須指定 Break 來停止執行。

現在，執行腳本。

```powershell
PS C:\ps-test> .\test.ps1
Hit Command breakpoint on 'C:\ps-test\test.ps1:psversion'

test.ps1:12  psversion
```

因為執行原則設定為 **RemoteSigned** ，所以會在函式呼叫時停止執行。

至此，您可能會想要檢查呼叫堆疊。 使用 `Get-PsCallStack` Cmdlet 或 `Get-PsCallStack` 偵錯工具命令 (k) 。 下列命令會取得目前的呼叫堆疊。

```powershell
DBG> k
2: prompt
1: .\test.ps1: $args=[]
0: prompt: $args=[]
```

此範例只會示範使用 PowerShell 偵錯工具的許多方式。

如需偵錯工具 Cmdlet 的詳細資訊，請輸入下列命令：

```powershell
help <cmdlet-name> -full
```

例如，輸入：

```powershell
help Set-PSBreakpoint -full
```

## <a name="other-debugging-features-in-powershell"></a>PowerShell 中的其他調試功能

除了 PowerShell 偵錯工具之外，PowerShell 還包含數個可供您用來偵測腳本和函式的其他功能。

- Windows PowerShell ISE 包含互動式圖形偵錯工具。 如需詳細資訊，請啟動 Windows PowerShell ISE，然後按下 F1。

- 此 `Set-PSDebug` Cmdlet 提供非常基本的腳本調試功能，包括逐步執行和追蹤。

- 使用指令 `Set-StrictMode` 程式可偵測未初始化變數的參考、參考不存在之物件的屬性，以及函式不正確語法。

- 將診斷語句新增至腳本，例如顯示變數值的語句、從命令列讀取輸入的語句，或報告目前指令的語句。 使用包含此工作之寫入動詞的 Cmdlet，例如 `Write-Host` 、 `Write-Debug` 、 `Write-Warning` 和 `Write-Verbose` 。

## <a name="see-also"></a>另請參閱

- [停用->disable-psbreakpoint](xref:Microsoft.PowerShell.Utility.Disable-PSBreakpoint)
- [啟用->disable-psbreakpoint](xref:Microsoft.PowerShell.Utility.Enable-PSBreakpoint)
- [>disable-psbreakpoint](xref:Microsoft.PowerShell.Utility.Get-PSBreakpoint)
- [Get-pscallstack](xref:Microsoft.PowerShell.Utility.Get-PSCallStack)
- [移除->disable-psbreakpoint](xref:Microsoft.PowerShell.Utility.Remove-PSBreakpoint)
- [Set-PSBreakpoint](xref:Microsoft.PowerShell.Utility.Set-PSBreakpoint)
- [Write-Debug](xref:Microsoft.PowerShell.Utility.Write-Debug)
- [Write-Verbose](xref:Microsoft.PowerShell.Utility.Write-Verbose)

