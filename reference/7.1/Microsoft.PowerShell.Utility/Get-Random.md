---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/20/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-random?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Random
ms.openlocfilehash: 644663c8871233bae84288f83492b518405d14ff
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202804"
---
# Get-Random

## 概要
取得一個隨機數字，或從集合隨機選擇物件。

## SYNTAX

### RandomNumberParameterSet (預設值)

```
Get-Random [-SetSeed <Int32>] [[-Maximum] <Object>] [-Minimum <Object>] [-Count <Int32>] [<CommonParameters>]
```

### RandomListItemParameterSet

```
Get-Random [-SetSeed <Int32>] [-InputObject] <Object[]> [-Count <Int32>] [<CommonParameters>]
```

### ShuffleParameterSet

```
Get-Random [-SetSeed <Int32>] [-InputObject] <Object[]> [-Shuffle] [<CommonParameters>]
```

## DESCRIPTION

`Get-Random`Cmdlet 會取得隨機選取的數位。 如果您將物件集合提交到 `Get-Random` ，它會從集合中取得一或多個隨機選取的物件。

如果沒有參數或輸入， `Get-Random` 命令會傳回隨機選取的32位不帶正負號整數，介於 0 **Int32.MaxValue** (零) 和 int32.maxvalue (`0x7FFFFFFF` ， `2,147,483,647`) 。

您可以使用的參數 `Get-Random` 來指定種子數、最小值和最大值、從提交的集合傳回的物件數目，以及以隨機順序傳回整個集合。

## 範例

### 範例1：取得隨機整數

此命令會取得介於 0 (零 **) 和 int32.maxvalue** 之間的隨機整數。

```powershell
Get-Random
```

```Output
3951433
```

### 範例2：取得0到99之間的隨機整數

```powershell
Get-Random -Maximum 100
```

```Output
47
```

### 範例3：取得介於-100 和99之間的隨機整數

```powershell
Get-Random -Minimum -100 -Maximum 100
```

```Output
56
```

### 範例4：取得隨機浮點數

此命令會取得大於或等於 10.7 且小於 20.92 的隨機浮點數。

```powershell
Get-Random -Minimum 10.7 -Maximum 20.93
```

```Output
18.08467273887
```

### 範例5：從陣列取得隨機整數

這個命令會從指定的陣列取得隨機選取的數字。

```powershell
1, 2, 3, 5, 8, 13 | Get-Random
```

```Output
8
```

### 範例6：從陣列取得數個隨機整數

此命令會從陣列中以隨機順序取得三個隨機選取的數位。

```powershell
1, 2, 3, 5, 8, 13 | Get-Random -Count 3
```

```Output
3
1
13
```

### 範例7：隨機化整個集合

從 PowerShell 7.1 開始，您可以使用隨機 **參數以** 隨機順序傳回整個集合。

```powershell
1, 2, 3, 5, 8, 13 | Get-Random -Shuffle
```

```Output
2
3
5
1
8
13
```

### 範例8：取得隨機的非數值

此命令會從非數字集合中傳回隨機值。

```powershell
"red", "yellow", "blue" | Get-Random
```

```Output
yellow
```

### 範例9：使用 SetSeed 參數

此範例顯示使用 **SetSeed** 參數的效果。

因為 **SetSeed** 會產生非隨機的行為，所以通常只會用來重現結果，例如在偵錯工具或分析腳本時。

```powershell
# Commands with the default seed are pseudorandom
Get-Random -Maximum 100 -SetSeed 23
Get-Random -Maximum 100
Get-Random -Maximum 100
Get-Random -Maximum 100
```

```Output
74
56
84
46
```

```powershell
# Commands with the same seed are not random
Get-Random -Maximum 100 -SetSeed 23
Get-Random -Maximum 100 -SetSeed 23
Get-Random -Maximum 100 -SetSeed 23
```

```Output
74
74
74
```

```powershell
# SetSeed results in a repeatable series
Get-Random -Maximum 100 -SetSeed 23
Get-Random -Maximum 100
Get-Random -Maximum 100
Get-Random -Maximum 100
```

```Output
74
56
84
46
```

### 範例10：取得隨機檔案

這些命令會從本機電腦的磁片磁碟機取得隨機選取的50檔案範例 `C:` 。

```powershell
$Files = Get-ChildItem -Path C:\* -Recurse
$Sample = $Files | Get-Random -Count 50
```

### 範例11：擲出公平骰子

此範例會匯總一個公平的骰子1200次，並計算結果。 第一個命令會 `For-EachObject` `Get-Random` 從管道中的數位 (1-6) 重複呼叫。 結果會依據其值來分組 `Group-Object` ，並以具有的資料表格式化 `Select-Object` 。

```powershell
1..1200 | ForEach-Object {
    1..6 | Get-Random
} | Group-Object | Select-Object Name,Count
```

```Output
Name Count
---- -----
1      206
2      199
3      196
4      226
5      185
6      188
```

### 範例12：使用 Count 參數

您現在可以使用 **Count** 參數，而不需要將物件輸送至 `Get-Random` 。
下列範例會取得三個小於10的亂數字。

```powershell
Get-Random -Count 3 -Maximum 10
```

```Output
9
0
8
```

### 範例13：使用 InputObject 參數搭配空字串或 $null

在此範例中， **InputObject** 參數會指定包含空字串的陣列 (`''`) 和 `$null` 。

```powershell
Get-Random -InputObject @('a','',$null)
```

`Get-Random` 會傳回 `a` 、空字串或 `$null` 。 空的字串會顯示為空白行，並 `$null` 返回 PowerShell 提示字元。

## PARAMETERS

### -Count

指定要傳回的隨機物件或數位數目。 預設值是 1。

搭配使用時 `InputObject` ，如果 **Count** 的值超過集合中的物件數目，就會 `Get-Random` 以隨機順序傳回所有物件。

```yaml
Type: System.Int32
Parameter Sets: RandomNumberParameterSet, RandomListItemParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

指定物件的集合。 `Get-Random` 從集合中隨機選取的物件（依 **計數** 指定的數目）取得隨機選取的物件。 輸入物件、包含物件的變數，或輸入可取得物件的命令或運算式。 您也可以使用管線將物件的集合傳送至 `Get-Random` 。

從 PowerShell 7 開始， **InputObject** 參數會接受可包含空字串或的陣列 `$null` 。 陣列可以沿著管線或 **InputObject** 參數值來傳送。

```yaml
Type: System.Object[]
Parameter Sets: RandomListItemParameterSet, ShuffleParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Maximum

指定隨機數字的最大值。 `Get-Random` 傳回小於 (不等於) 最大值的值。 輸入整數、雙精確度浮點數，或是可以轉換為整數或雙精確度的物件，例如 ( "100" ) 的數值字串。

**Maximum** 的值必須大於 (不等於) **Minimum** 的值。 如果 **最大** 或 **最小** 值為浮點數，則會傳回 `Get-Random` 隨機選取的浮點數。

在64位電腦上，如果 **最小** 值是32位整數，則 **最大** 值的預設 **值為 int32.maxvalue。**

如果 **最小** 值是雙精度浮點數 () ， **最大** 值的預設值就是 **雙** 點。 否則，預設 **值為 int32.maxvalue。**

```yaml
Type: System.Object
Parameter Sets: RandomNumberParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Minimum

指定隨機數字的最小值。 輸入整數、雙精確度浮點數，或是可以轉換為整數或雙精確度的物件，例如 ( "100" ) 的數值字串。 預設值是 0 (零)。

**Minimum** 的值必須小於 (不等於) **Maximum** 的值。 如果 **最大** 或 **最小** 值為浮點數，則會傳回 `Get-Random` 隨機選取的浮點數。

```yaml
Type: System.Object
Parameter Sets: RandomNumberParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SetSeed

指定隨機數字產生器的種子值。 這個種子值會用於目前的命令，以及 `Get-Random` 目前會話中所有後續的命令，直到您再次使用 **SetSeed** 或關閉會話為止。 您無法將種子重設為其預設值。

不需要 **SetSeed** 參數。 根據預設，會 `Get-Random` 使用 [RandomNumberGenerator ( # B1 ](/dotnet/api/system.security.cryptography.randomnumbergenerator) 方法來產生種子值。 因為 **SetSeed** 會產生非隨機的行為，所以通常只會在嘗試重現行為時使用，例如在偵錯工具或分析包含命令的腳本時 `Get-Random` 。

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -隨機

以隨機順序傳回整個集合。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ShuffleParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.Object

您可以透過管線傳送一個或多個物件。 `Get-Random` 從輸送的物件隨機選取值。

## 輸出

### System.Int32、System.Int64、System.Double

`Get-Random` 傳回整數或浮點數，或從提交的集合中隨機選取的物件。

## 注意

`Get-Random` 根據會話開始時的系統時間時鐘，設定每個會話的預設種子。

`Get-Random` 不一定會傳回與輸入值相同的資料類型。 下表顯示每個數值輸入類型的輸出類型。

| 輸入類型 | 輸出類型 |
| :--------: | :---------: |
|   SByte    |   Double    |
|    Byte    |   Double    |
|   Int16    |   Double    |
|   UInt16   |   Double    |
|   Int32    |    Int32    |
|   UInt32   |   Double    |
|   Int64    |    Int64    |
|   UInt64   |   Double    |
|   Double   |   Double    |
|   Single   |   Double    |

從 Windows PowerShell 3.0 開始， `Get-Random` 支援64位的整數。 在 Windows PowerShell 2.0 中，所有值都會轉換 **為 system.string。**

從 PowerShell 7 開始， **RandomListItemParameterSet** 參數集中的 **InputObject** 參數會接受包含空字串或的陣列 `$null` 。 在舊版 PowerShell 中，只有 **RandomNumberParameterSet** 參數集內的 **最大** 參數會接受空字串或 `$null` 。

## 相關連結

