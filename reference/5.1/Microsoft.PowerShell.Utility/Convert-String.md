---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convert-string?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Convert-String
ms.openlocfilehash: 29ec9e21277bae02ab94ce5e862787c86a87b439
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203360"
---
# Convert-String

## 概要
將字串格式化以符合範例。

## SYNTAX

```
Convert-String [-Example <System.Collections.Generic.List`1[System.Management.Automation.PSObject]>]
 -InputObject <String> [<CommonParameters>]
```

## DESCRIPTION

**Convert 字串** Cmdlet 會將字串格式化，以符合範例的格式。

## 範例

### 範例1：轉換字串的格式

```powershell
"Mu Han", "Jim Hance", "David Ahs", "Kim Akers" | Convert-String -Example "Ed Wilson=Wilson, E."
```

```output
Han, M.
Hance, J.
Ahs, D.
Akers, K.
```

第一個命令會建立包含 first 和 last 名稱的陣列。

第二個命令會根據範例將名稱格式化。
它會先將姓氏放在輸出中，後面接著初始。

### 範例2：簡化字串的格式

```powershell
$composers = @("Johann Sebastian Bach", "Wolfgang Amadeus Mozart", "Frederic Francois Chopin", "Johannes Brahms")
$composers | Convert-String -Example "first middle last=last, first"
```

```output
Bach, Johann
Mozart, Wolfgang
Chopin, Frederic
Brahms, Johannes
```

第一個命令會建立一個陣列，其中包含名字、中間名和姓氏。
請注意，最後一個專案沒有中間名。

第二個命令會根據範例將名稱格式化。
它會先將姓氏放在輸出中，後面接著第一個名稱。
已移除所有的中間名;沒有中間名的專案會正確處理。

### 範例3：當字串不符合範例時的輸出管理

```powershell
$composers = @("Johann Sebastian Bach", "Wolfgang Amadeus Mozart", "Frederic Francois Chopin", "Johannes Brahms")
$composers | Convert-String -Example "first middle last=middle, first"
```

```output
Sebastian, Johann
Amadeus, Wolfgang
Francois, Frederic
```

第一個命令會建立一個陣列，其中包含名字、中間名和姓氏。
請注意，最後一個專案沒有中間名。

第二個命令會根據範例將名稱格式化。
它會先將 **中間名** 放在輸出中，後面接著名字。
**$Composers** 中的最後一個專案已略過，因為它不符合範例模式：它沒有中間名。

### 範例4：具有美加空格的警告

```powershell
$composers = @("Antonio Vivaldi", "Richard Wagner ", "Franz Schubert", "Johannes Brahms ")
$composers | Convert-String -Example "Patti Fuller = Fuller, P."
```

```output
 Wagner, R.
 Brahms, J.
```

第一個命令會建立第一個和最後一個名稱的陣列。
請注意，第二個和第四個專案在姓氏之後有額外的尾端空格。

第二個命令會轉換符合範例模式的所有字串： _單字、空格、單字和最後尾端空格_ ，全都在等號前面。
此外，請記下輸出中的前置空格。

### 範例5：使用多個模式來格式化處理常式資訊

```powershell
$ExamplePatterns = @(
    @{before='"Hello","World"'; after='World: Hello'},
    @{before='"Hello","1"'; after='1: Hello'},
    @{before='"Hello-World","22"'; after='22: Hello-World'},
    @{before='"hello world","333"'; after='333: hello world'}
)
$Processes = Get-Process   | Select-Object -Property ProcessName, Id | ConvertTo-Csv -NoTypeInformation
$Processes | Convert-String -Example $ExamplePatterns
```

```output
Id: ProcessName
4368: AGSService
8896: Amazon Music Helper
4420: AppleMobileDeviceService
...
11140: git-bash
0: Idle
...
56: Secure System
...
13028: WmiPrvSE
2724: WUDFHost
2980: WUDFHost
3348: WUDFHost
```

**$ExamplePatterns** 透過範例在資料中定義不同的預期模式。

第一個模式是 `@{before='"Hello","World"'; after='World: Hello'}` ，如下所示：以 _雙引號括住的字串、逗號，_ 然後再以 
 _引號括住第二個字組;_ 
_字串中沒有空格。在輸出上：先放置第二個單字，_ 
 _沒有引號，然後輸入一個空格，然後是第一個單字，沒有引號。_

第二個模式是 `@{before='"Hello","1"'; after='1: Hello'}` ，如下所示：以 _雙引號括住的字串、逗號，_ 然後以 
 _引號括住的數位;_ 
_字串中沒有空格。在輸出上：先將數位放在前面，_ 
 _沒有引號，然後輸入一個空格，再加上單字，而不使用引號。_

第三個模式的 `@{before='"Hello-World","22"'; after='22: Hello-World'}` 讀取方式如下：會 _預期字串，其中兩個單字之間的連字號都以雙引號括住_ ，然後以逗號括住，然後以 
 _引號括住數位;_ 
_逗號和第三個雙引號之間沒有空格。_ 
_在輸出上：先放置數位，不加引號，然後輸入一個空格，_ 
然後 _再加上連字號的單字，沒有引號。_

第四個和最後一個模式的讀取如下所示 `@{before='"hello world","333"'; after='333: hello world'}` ：預期的字串會以雙引號 _括住的兩個字_ 組，然後以雙引號括住，然後以 
 _引號括住數位;_ 
_逗號和第三個雙引號之間沒有空格。_ 
_在輸出上：先放置數位，不加引號，然後輸入一個空格，_ 
然後 _是空格之間有空格的單字，沒有引號。_

第一個命令會使用 Get-Process Cmdlet 取得所有處理常式。
此命令會將它們傳遞給 Select-Object Cmdlet，以選取進程名稱和處理序識別碼。 在管線的結尾，此命令會使用 ConvertTo-Csv Cmdlet，將輸出轉換成逗點分隔值，而不使用類型資訊。
命令會將結果儲存在 **$Processes** 變數中。
**$Processes** 現在包含進程名稱和 PID。

第二個命令會指定變更輸入專案順序的範例變數。
此命令會將 **$Processes** 中的每個字串。

>**注意** 第四個模式會隱含地指出以空格分隔的兩個或多個單字相符。
>
>如果沒有第四個模式，則只會比對以雙引號括住之字串的第一個字組。

## PARAMETERS

### -範例

指定目標格式的範例清單。
指定以等於 (=) 號分隔的配對，並以左邊的來源模式和右邊的目標模式，如下列範例所示：

* `-Example "Hello World=World, Hello"`
* `-Example "Hello World=World: Hello",'"Hello","1"=1: Hello'`

>**注意** 第二個範例會使用模式清單

或者，指定包含屬性 **之前** 和 **之後** 的雜湊表清單。

* `-Example @{before='"Hello","World"'; after='World: Hello'}, @{before='"Hello","1"'; after='1: Hello'}`

>**注意** 請避免在等號前後使用空格，因為它們被視為模式的一部分。

```yaml
Type: System.Collections.Generic.List`1[System.Management.Automation.PSObject]
Parameter Sets: (All)
Aliases: E

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

指定要格式化的字串。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### String

您可以透過管道將字串傳送至此 Cmdlet。

## 輸出

### String

這個 Cmdlet 會傳回字串。

## 注意

## 相關連結

[ConvertFrom-String](ConvertFrom-String.md)

[ConvertTo-Csv](ConvertTo-Csv.md)

[Get-Process](../Microsoft.PowerShell.Management/Get-Process.md)

[Out-String](Out-String.md)

[Select-Object](Select-Object.md)
