---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-expression?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-Expression
ms.openlocfilehash: f915a5741ed5c63206da3c35f5322508515bd566
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202767"
---
# Invoke-Expression

## 概要
在本機電腦上執行命令或運算式。

## SYNTAX

```
Invoke-Expression [-Command] <String> [<CommonParameters>]
```

## DESCRIPTION

此 `Invoke-Expression` Cmdlet 會將指定的字串評估或執行為命令，並傳回運算式或命令的結果。 如果沒有 `Invoke-Expression` ，則會傳回在命令列提交的字串 () 不變更。

運算式會在目前的範圍內進行評估和執行。 如需詳細資訊，請參閱 [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)。

> [!CAUTION]
> 在腳本中使用 Cmdlet 時，請採取合理的預防措施 `Invoke-Expression` 。 當您使用 `Invoke-Expression` 來執行使用者輸入的命令時，請先確認命令是安全的，然後再執行它。 一般而言，最好使用預先定義的輸入選項來設計您的指令碼，而不要允許自由輸入。

## 範例

### 範例1：評估運算式

```powershell
$Command = "Get-Process"
$Command
```

```Output
Get-Process
```

```powershell
Invoke-Expression $Command
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id   ProcessName
-------  ------    -----      ----- -----   ------     --   -----------
296       4       1572       1956    20       0.53     1348   AdtAgent
270       6       1328       800     34       0.06     2396   alg
67        2       620        484     20       0.22     716    ati2evxx
1060      15      12904      11840   74       11.48    892    CcmExec
1400      33      25280      37544   223      38.44    2564   communicator
...
```

這個範例示範 `Invoke-Expression` 如何使用來評估運算式。 如果沒有 `Invoke-Expression` ，則會列印運算式，但不會進行評估。

第一個命令會將 `Get-Process` 字串)  (值指派給 `$Command` 變數。

第二個命令會顯示在命令列輸入變數名稱的效果。 PowerShell 會回應字串。

第三個命令會使用 `Invoke-Expression` 來評估字串。

### 範例2：在本機電腦上執行腳本

```powershell
Invoke-Expression -Command "C:\ps-test\testscript.ps1"
"C:\ps-test\testscript.ps1" | Invoke-Expression
```

這些命令會用 `Invoke-Expression` 來在本機電腦上執行腳本 TestScript.ps1。 兩個命令是相等的。 第一個使用 **command** 參數指定要執行的命令。
第二個會使用管線運算子 (`|`) 將命令字串傳送至 `Invoke-Expression` 。

### 範例3：在變數中執行命令

```powershell
$Command = 'Get-Process | where {$_.cpu -gt 1000}'
Invoke-Expression $Command
```

此範例會執行儲存在變數中的命令字串 `$Command` 。

命令字串會以單引號括住，因為它包含一個變數， `$_` 代表目前的物件。 如果是以雙引號括住，則 `$_` 變數會在儲存至變數之前，以其值取代 `$Command` 。

### 範例4：取得並執行 Cmdlet 說明範例

```powershell
$Cmdlet_name = "Get-EventLog"
$Example_number = 1
$Example_code = (Get-Help $Cmdlet_name).examples.example[($Example_number-1)].code
Invoke-Expression $Example_code
```

此命令會取出並執行 Cmdlet 說明主題中的第一個範例 `Get-EventLog` 。

若要執行不同 Cmdlet 的範例，請將變數的值變更 `$Cmdlet_name` 為 Cmdlet 的名稱。 然後，將 `$Example_number` 變數變更為您想要執行的範例編號。 如果範例編號無效，命令就會失敗。

## PARAMETERS

### -Command

指定要執行的命令或運算式。 輸入命令或運算式，或輸入包含命令或運算式的變數。 需要 **命令** 參數。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 輸入

### System.string 或 PSObject

您可以使用管線將代表命令的物件傳送至 `Invoke-Expression` 。
使用 `$Input` 自動變數來代表命令中的輸入物件。

## 輸出

### PSObject

傳回已叫用命令所產生的輸出 () **命令** 參數的值。

## 注意

在大部分情況下，您會使用 PowerShell 的呼叫運算子來叫用運算式，並達到相同的結果。
呼叫運算子是較安全的方法。 如需詳細資訊，請參閱 [about_Operators](../microsoft.powershell.core/about/about_operators.md#call-operator-)。

## 相關連結

[Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)

[about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)

