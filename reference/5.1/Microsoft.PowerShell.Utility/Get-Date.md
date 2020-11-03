---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-date?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Date
ms.openlocfilehash: f550d352ca6e400307feba9ec16cea4632603b62
ms.sourcegitcommit: ea9270bacee7dd1b9df2519384de277576357ce2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "93206147"
---
# Get-Date

## 概要
取得目前的日期和時間。

## SYNTAX

### net (預設) 

```
Get-Date [[-Date] <DateTime>] [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 [-Format <String>] [<CommonParameters>]
```

### UFormat

```
Get-Date [[-Date] <DateTime>] [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 [-UFormat <String>] [<CommonParameters>]
```

## DESCRIPTION

`Get-Date`Cmdlet 會取得代表目前日期或您所指定日期的 **DateTime** 物件。 `Get-Date` 可以用數種 .NET 和 UNIX 格式來格式化日期和時間。 您可以使用 `Get-Date` 來產生日期或時間字元字串，然後將字串傳送到其他 Cmdlet 或程式。

`Get-Date` 使用電腦的文化特性設定來決定如何格式化輸出。 若要查看電腦的設定，請使用 `(Get-Culture).DateTimeFormat` 。

## 範例

### 範例1：取得目前的日期和時間

在此範例中，會 `Get-Date` 顯示目前的系統日期和時間。 輸出會是完整日期和完整時間格式。

```powershell
Get-Date
```

```Output
Tuesday, June 25, 2019 14:53:32
```

### 範例2：取得目前日期和時間的元素

這個範例會示範如何使用 `Get-Date` 來取得日期或時間元素。 參數會使用引數 **Date** 、 **Time** 或 **DateTime** 。

```powershell
Get-Date -DisplayHint Date
```

```Output
Tuesday, June 25, 2019
```

`Get-Date` 使用 **DisplayHint** 參數搭配 **date** 引數，以只取得日期。

### 範例3：使用 .NET 格式規範取得日期和時間

在此範例中，會使用 .NET 格式規範來自訂輸出的格式。 輸出是 **字串** 物件。

```powershell
Get-Date -Format "dddd MM/dd/yyyy HH:mm K"
```

```Output
Tuesday 06/25/2019 16:17 -07:00
```

`Get-Date` 使用 **Format** 參數來指定數個格式規範。

此範例中使用的 .NET 格式規範定義如下：

| 規範 | 定義 |
| --- | --- |
| `dddd` | 一周中的日-完整名稱 |
| `MM` | 月份數 |
| `dd` | 月中的日-2 位數 |
| `yyyy` | 以4位數格式表示的年份 |
| `HH:mm` | 時間（24小時制）-無秒數 |
| `K` | 從通用時間座標 (UTC) 的時區位移 |

如需 .NET 格式規範的詳細資訊，請參閱 [自訂日期和時間格式字串](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8)。

### 範例4：取得 UFormat 規範的日期和時間

在此範例中，會使用數個 **UFormat** 格式規範來自訂輸出的格式。
輸出是 **字串** 物件。

```powershell
Get-Date -UFormat "%A %m/%d/%Y %R %Z"
```

```Output
Tuesday 06/25/2019 16:19 -07
```

`Get-Date` 使用 **UFormat** 參數來指定數個格式規範。

此範例中使用的 **UFormat** 格式規範定義如下：

| 規範 | 定義 |
| --- | --- |
| `%A` | 一周中的日-完整名稱 |
| `%m` | 月份數 |
| `%d` | 月中的日-2 位數 |
| `%Y` | 以4位數格式表示的年份 |
| `%R` | 時間（24小時制）-無秒數 |
| `%Z` | 從通用時間座標 (UTC) 的時區位移 |

如需有效 **UFormat** 格式規範的清單，請參閱 [附注](#notes) 一節。

### 範例5：取得一年中的日期日

在此範例中，屬性是用來取得年度的數位日。

西曆有365天，但有366天的閏年度除外。 例如，2020年12月31日是第366天。

```powershell
(Get-Date -Year 2020 -Month 12 -Day 31).DayOfYear
```

```Output
366
```

`Get-Date` 使用三個參數來指定日期： **Year** 、 **Month** 和 **Day** 。 此命令會以括弧括住，以便 **DayofYear** 屬性評估結果。

### 範例6：檢查是否已針對日光節約時間調整日期

此範例會使用布林方法，以確認日期是否以日光節約時間進行調整。

```powershell
$DST = Get-Date
$DST.IsDaylightSavingTime()
```

```Output
True
```

變數會 `$DST` 儲存的結果 `Get-Date` 。 `$DST` 使用 **IsDaylightSavingTime** 方法來測試是否針對日光節約時間調整日期。

### 範例7：將目前時間轉換成 UTC 時間

在此範例中，目前的時間會轉換成 UTC 時間。 系統地區設定的 UTC 時差會用來轉換時間。 [ [附注](#notes) ] 區段中的資料表會列出有效的 **UFormat** 格式規範。

```powershell
Get-Date -UFormat "%A %B/%d/%Y %T %Z"
$Time = Get-Date
$Time.ToUniversalTime()
```

```Output
Wednesday June/26/2019 10:45:26 -07

Wednesday, June 26, 2019 17:45:26
```

`Get-Date` 使用 **UFormat** 參數搭配格式規範，以顯示目前的系統日期和時間。 格式規範 **% Z** 代表 **-07** 的 UTC 時差。

`$Time`變數會儲存目前的系統日期和時間。 `$Time` 使用 **>datetime.touniversaltime ( # B1** 方法，根據電腦的 UTC 時差來轉換時間。

### 範例8：建立時間戳記

在此範例中，格式規範會建立目錄名稱的時間戳記 **字串** 物件。 時間戳記包含日期、時間和 UTC 時差。

```powershell
$timestamp = Get-Date -Format o | ForEach-Object { $_ -replace ":", "." }
New-Item -Path C:\Test\$timestamp -Type Directory
```

```Output
    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         6/27/2019    07:59                2019-06-27T07.59.24.4603750-07.00
```

`$timestamp`變數會儲存命令的結果 `Get-Date` 。 `Get-Date` 使用 **格式** 參數搭配小寫的格式規範 `o` 來建立時間戳記 **字串** 物件。 物件會向下傳送到管線 `ForEach-Object` 。 **ScriptBlock** 包含 `$_` 表示目前管線物件的變數。 時間戳記字串是由以句號取代的冒號分隔。

`New-Item` 使用 **Path** 參數指定新目錄的位置。 路徑包含 `$timestamp` 變數做為目錄名稱。 **Type** 參數會指定建立目錄。

## PARAMETERS

### -Date

指定日期和時間。 Time 是選擇性的，如果未指定，則會傳回00:00:00。

以系統地區設定的標準格式輸入日期和時間。

例如，在美式英文中：

`Get-Date -Date "6/25/2019 12:30:22"` 傳回2019年6月25日星期二的12:30:22

```yaml
Type: System.DateTime
Parameter Sets: (All)
Aliases: LastWriteTime

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -日

指定要顯示的月份日期。 輸入從 1 到 31 的值。

如果指定的值大於一個月中的天數，則 PowerShell 會將天數加上月份。 例如， `Get-Date -Month 2 -Day 31` 顯示 3 **月 3** 日，而不是 **2 月31日** 。

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

### -DisplayHint

決定要顯示日期和時間的哪些元素。

接受的值如下：

- **Date** ：只顯示日期
- **時間** ：只顯示時間
- **DateTime** ：顯示日期和時間

```yaml
Type: Microsoft.PowerShell.Commands.DisplayHintType
Parameter Sets: (All)
Aliases:
Accepted values: Date, Time, DateTime

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Format

使用格式規範所指定的 Microsoft .NET Framework 格式來顯示日期和時間。
**Format** 參數會輸出 **String** 物件。

如需可用 .NET 格式規範的清單，請參閱 [自訂日期和時間格式字串](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8)。

使用 **Format** 參數時，只會 `Get-Date` 取得顯示日期所需的 **DateTime** 物件屬性。 如此一來， **DateTime** 物件的部分屬性和方法可能無法使用。

從 PowerShell 5.0 開始，您可以使用下列其他格式作為 **Format** 參數的值。

- **FileDate** 。 以本機時程表示的目前日期的檔案或路徑易記表示。 格式 `yyyyMMdd` (區分大小寫，使用4位數年份、2位數月份和2位數的日) 。 例如：
  20190627.

- **FileDateUniversal** 。 以通用時程表示的目前日期的檔案或路徑易記表示 (UTC) 。 格式 `yyyyMMddZ` (區分大小寫，使用4位數的年份、2位數的月份、2位數的日期，以及 `Z` 做為 UTC 指標) 的字母。 例如：20190627Z。

- **FileDateTime** 。 以24小時制格式，以本機時程表示的目前日期和時間的檔案或路徑易記表示。 格式 `yyyyMMddTHHmmssffff` (區分大小寫、使用4位數的年份、2位數的月份、2位數的日期、 `T` 以時間分隔符號表示的字母、2位數的小時、2位數分鐘、2位數的秒數，以及4位數的毫秒) 。 例如：20190627T0840107271。

- **FileDateTimeUniversal** 。 以24小時格式表示的目前日期和時間的檔案或路徑易記標記法 (UTC) 。 格式 `yyyyMMddTHHmmssffffZ` (區分大小寫、使用4位數的年份、2位數的月份、2位數的日期、 `T` 以時間分隔符號表示的字母、2位數的小時、2位數分鐘、2位數秒、4位數毫秒，以及 `Z` 做為 UTC 指標) 的字母。 例如：20190627T1540500718Z。

```yaml
Type: System.String
Parameter Sets: net
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -小時

指定要顯示的小時。 輸入0到23之間的值。

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

### -毫秒

指定日期中的毫秒。 輸入0到999的值。

此參數是在 PowerShell 3.0 中引進。

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

### -分鐘

指定要顯示的分鐘。 輸入0到59的值。

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

### -月

指定要顯示的月份。 輸入1到12的值。

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

### -秒

指定要顯示的秒。 輸入0到59的值。

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

### -UFormat

使用 UNIX 格式顯示日期和時間。 **UFormat** 參數會輸出字串物件。

**UFormat** 規範的前面會加上百分比符號 (`%`) ，例如、 `%m` `%d` 和 `%Y` 。 [附注](#notes)區段包含有效 **UFormat** 規範的資料表。

使用 **UFormat** 參數時，只會 `Get-Date` 取得顯示日期所需的 **DateTime** 物件屬性。 如此一來， **DateTime** 物件的部分屬性和方法可能無法使用。

```yaml
Type: System.String
Parameter Sets: UFormat
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -年

指定要顯示的年份。 輸入從1到9999的值。

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

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 管線輸入

`Get-Date` 接受管線輸入。 例如： `Get-ChildItem | Get-Date` 。

## 輸出

### System.string 或 System.string

`Get-Date` 傳回 **DateTime** 物件，但使用 **Format** 和 **UFormat** 參數時除外。 **Format** 或 **UFormat** 參數會傳回 **字串** 物件。

將 **DateTime** 物件向下傳送至 `Add-Content` 需要字串輸入的 Cmdlet 時，PowerShell 會將物件轉換成 **字串** 物件。

方法會 `(Get-Date).ToString()` 將 **DateTime** 物件轉換成 **String** 物件。

若要顯示物件的屬性和方法，請將物件沿著管線向下傳送至 `Get-Member` 。
例如： `Get-Date | Get-Member` 。

## 注意

**DateTime** 物件是適用于系統地區設定的完整日期和完整時間格式。

有效的 **UFormat** 規範會顯示在下表中：

| 格式規範 |                                 意義                     |         範例          |
| ---- | ----------------------------------------------------------------------- | ------------------------ |
| `%A` | 一周中的日-完整名稱                                             | 星期一                   |
| `%a` | 一周中的日-縮寫名稱                                      | Mon                      |
| `%B` | 月份名稱-完整                                                       | 一月                  |
| `%b` | 月份名稱-縮寫                                                | 一月                      |
| `%C` | 世紀                                                                 | 20適用于2019              |
| `%c` | 日期和時間-縮寫                                             | 星期四6月 27 08:44:18 2019 |
| `%D` | 日期（mm/dd/yy 格式）                                                 | 06/27/19                 |
| `%d` | 月中的日-2 位數                                             | 05                       |
| `%e` | 月份中的日期-前面加上空格的數位                            | \<space\>.5               |
| `%G` | 與 ' Y ' 相同                                                             |                          |
| `%g` | 與 ' y ' 相同                                                             |                          |
| `%H` | 24小時制的小時                                                  | 17                       |
| `%h` | 與 ' b ' 相同                                                             |                          |
| `%I` | 12小時制的小時格式                                                  | 05                       |
| `%j` | 年中的日                                                         | 1-366                    |
| `%k` | 與 ' H ' 相同                                                             |                          |
| `%l` | 與「I」相同 (我)                                               | 05                       |
| `%M` | 分鐘                                                                 | 35                       |
| `%m` | 月份數                                                            | 06                       |
| `%n` | 換行字元                                                       |                          |
| `%p` | AM 或 PM                                                                |                          |
| `%R` | 時間（24小時制）-無秒數                                      | 17:45                    |
| `%r` | 12小時制的時間                                                  | 上午09:15:36              |
| `%S` | 秒                                                                 | 05                       |
| `%s` | 自 00:00:00 1970 年1月1日起經過的秒數                          | 1150451174.95705         |
| `%t` | 水準定位字元                                                |                          |
| `%T` | 24 小時制的時間格式                                                  | 17:45:52                 |
| `%U` | 與 ' W ' 相同                                                             |                          |
| `%u` | 周中的日-數位                                                | 星期日 = 0               |
| `%V` | 年中的周                                                        | 01-53                    |
| `%w` | 與 ' u ' 相同                                                             |                          |
| `%W` | 年中的周                                                        | 00-52                    |
| `%X` | 與 ' t ' 相同                                                             |                          |
| `%x` | 地區設定標準格式的日期                                      | 06/27/19 （英文）-US  |
| `%Y` | 以4位數格式表示的年份                                                  | 2019                     |
| `%y` | 以2位數格式表示的年份                                                  | 19                       |
| `%Z` | 從通用時間座標 (UTC) 的時區位移                   | -07                      |

## 相關連結

[ForEach-Object](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Get-Culture](Get-Culture.md)

[Get-Member](Get-Member.md)

[New-Item](../Microsoft.PowerShell.Management/New-Item.md)

[New-TimeSpan](New-TimeSpan.md)

[Set-Date](Set-Date.md)
