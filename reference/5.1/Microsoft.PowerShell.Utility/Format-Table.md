---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-table?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Table
ms.openlocfilehash: 4880e4adc9b4ebc339eb44a114e8e6d8bea398a6
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/10/2020
ms.locfileid: "93205899"
---
# Format-Table

## 概要
將輸出格式化為表格。

## SYNTAX

### 全部

```
Format-Table [-AutoSize] [-RepeatHeader] [-HideTableHeaders] [-Wrap] [[-Property] <Object[]>]
 [-GroupBy <Object>] [-View <String>] [-ShowError] [-DisplayError] [-Force] [-Expand <String>]
 [-InputObject <PSObject>] [<CommonParameters>]
```

## DESCRIPTION

Cmdlet 會將 `Format-Table` 命令的輸出格式化為表格，並在每個資料行中使用物件的已選取屬性。 物件類型會決定每個資料行中顯示的預設配置和屬性。 您可以使用 **Property** 參數來選取要顯示的屬性。

PowerShell 會使用預設格式器來定義如何顯示物件類型。 您可以使用檔案 `.ps1xml` 來建立自訂視圖，以顯示具有指定屬性的輸出資料表。 建立自訂視圖之後，請使用 **view** 參數以您的自訂視圖顯示資料表。 如需有關 views 的詳細資訊，請參閱 [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)。

您可以使用雜湊表，在顯示物件之前先將其加入至物件，並指定資料表中的資料行標題。 若要加入計算屬性，請使用 **property** 或 **GroupBy** 參數。 如需雜湊表的相關詳細資訊，請參閱 [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)。

## 範例

### 範例1：設定 PowerShell 主機的格式

此範例會顯示資料表中 PowerShell 之主機程式的相關資訊。

```powershell
Get-Host | Format-Table -AutoSize
```

指令 `Get-Host` 程式會 **InternalHost** 代表主機的........... 物件。 物件會沿著管線向下傳送 `Format-Table` ，並顯示在資料表中。 **AutoSize** 參數會調整資料行寬度，以將截斷降至最低。

### 範例2：依根據 basepriority 格式化進程

在此範例中，處理常式會顯示在具有相同 **根據 basepriority** 屬性的群組中。

```powershell
Get-Process | Sort-Object -Property BasePriority | Format-Table -GroupBy BasePriority -Wrap
```

指令 `Get-Process` 程式會取得代表電腦上每個處理常式的物件，並將其傳送到管線 `Sort-Object` 。 物件會依照其 **根據 basepriority** 屬性的順序排序。

排序的物件會向下傳送到管線 `Format-Table` 。 **GroupBy** 參數會根據其 **根據 basepriority** 屬性的值，將處理常式資料排列成群組。 **Wrap** 參數可確保資料不會被截斷。

### 範例3：依開始日期格式化進程

此範例會顯示電腦上執行之處理常式的相關資訊。 物件會進行排序，並 `Format-Table` 使用視圖依其開始日期將物件分組。

```powershell
Get-Process | Sort-Object StartTime | Format-Table -View StartTime
```

`Get-Process` 取得代表電腦上執行之處理 **程式的處理常式** 物件。 物件會沿著管線向下傳送至 `Sort-Object` ，並根據 **StartTime** 屬性來排序。

排序的物件會向下傳送到管線 `Format-Table` 。 **View** 參數會指定在 PowerShell 檔案中針對 system.string 物件定義的 **StartTime** View。 `DotNetTypes.format.ps1xml` **System.Diagnostics.Process** **StartTime** view 會將每個處理常式的開始時間轉換為簡短日期，然後依開始日期將處理常式分組。

檔案 `DotNetTypes.format.ps1xml` 包含處理常式的 **優先權** 視圖。 您可以 `format.ps1xml` 使用自訂的視圖來建立自己的檔案。

### 範例4：針對資料表輸出使用自訂視圖

在此範例中，自訂視圖會顯示目錄的內容。 自訂視圖會將 **CreationTime** 資料行加入到所建立之 **DirectoryInfo** 和 **FileInfo** 物件的資料表輸出中 `Get-ChildItem` 。

此範例中的自訂視圖是從 PowerShell 原始程式碼中定義的視圖所建立。 如需有關用來建立此範例視圖的視圖和程式碼的詳細資訊，請參閱 [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md#sample-xml-for-a-format-table-custom-view)。

```powershell
Get-ChildItem  -Path C:\Test | Format-Table -View mygciview
```

```Output
    Directory: C:\Test

Mode                LastWriteTime              CreationTime         Length Name
----                -------------              ------------         ------ ----
d-----        11/4/2019     15:54       9/24/2019     15:54                Archives
d-----        8/27/2019     14:22       8/27/2019     14:22                Drawings
d-----       10/23/2019     09:38       2/25/2019     09:38                Files
-a----        11/7/2019     11:07       11/7/2019     11:07          11345 Alias.txt
-a----        2/27/2019     15:15       2/27/2019     15:15            258 alias_out.txt
-a----        2/27/2019     15:16       2/27/2019     15:16            258 alias_out2.txt
```

`Get-ChildItem` 取得目前目錄的內容 `C:\Test` 。 **DirectoryInfo** 和 **FileInfo** 物件會沿著管線向下傳送。
`Format-Table`使用 **View** 參數來指定包含 **CreationTime** 資料行的自訂視圖 **mygciview** 。

的預設 `Format-Table` 輸出 `Get-ChildItem` 不包含 **CreationTime** 資料行。

### 範例5：使用資料表輸出的屬性

這個範例會使用 **Property** 參數，在顯示內容 **名稱** 和 **DependentServices** 的兩個數據行資料表中顯示所有電腦的服務。

```powershell
Get-Service | Format-Table -Property Name, DependentServices
```

`Get-Service` 取得電腦上的所有服務，並將 **system.serviceprocess.dll 的 ServiceController** 物件向下傳送到管線。 `Format-Table` 使用 **Property** 參數來指定 **名稱** 和 **DependentServices** 屬性會顯示在資料表中。

**Name** 和 **DependentServices** 是物件類型的兩個屬性。 若要查看所有屬性： `Get-Service | Get-Member -MemberType Properties` 。

### 範例6：設定進程的格式並計算其執行時間

這個範例會顯示一個資料表，其中包含本機電腦的「 **記事本** 」處理常式的處理常式名稱和總執行時間。 總執行時間是從目前時間減去每個處理程序開始時間計算得來的。

```powershell
Get-Process notepad |
  Format-Table ProcessName, @{Label="TotalRunningTime"; Expression={(Get-Date) - $_.StartTime}}
```

```Output
ProcessName TotalRunningTime
----------- ----------------
notepad     03:20:00.2751767
notepad     00:00:16.7710520
```

`Get-Process` 取得所有本機電腦的「 **記事本** 」處理常式，並將物件沿著管線向下傳送。 `Format-Table` 顯示具有兩個數據行的資料表： **ProcessName** 、 `Get-Process` 屬性和 **TotalRunningTime** （計算屬性）。

**TotalRunningTime** 屬性是由含有兩個索引鍵、 **標籤** 和 **運算式** 的雜湊表所指定。 **標籤** 索引鍵會指定屬性名稱。 **Expression** 索引鍵會指定計算。 運算式會取得每個處理常式物件的 **StartTime** 屬性，並從命令的結果減去它 `Get-Date` ，以取得目前的日期和時間。

### 範例7：設定記事本進程的格式

這個範例會使用 `Get-CimInstance` 來取得本機電腦上所有 **記事本** 處理常式的執行時間。 您可以使用 `Get-CimInstance` With **ComputerName** 參數來取得遠端電腦的資訊。

```powershell
$Processes = Get-CimInstance -Class win32_process -Filter "name='notepad.exe'"
$Processes | Format-Table ProcessName, @{ Label = "Total Running Time"; Expression={(Get-Date) - $_.CreationDate}}
```

```Output
ProcessName Total Running Time
----------- ------------------
notepad.exe 03:39:39.6260693
notepad.exe 00:19:56.1376922
```

`Get-CimInstance` 取得 WMI **Win32_Process** 類別的實例，該類別會描述所有名為 **notepad.exe** 的本機電腦進程。 處理常式物件會儲存在 `$Processes` 變數中。

變數中的處理常式物件 `$Processes` 會向下傳送到管線中 `Format-Table` ，這會顯示 **ProcessName** 屬性和新的計算屬性，即 **總執行時間** 。

此命令會將新的計算屬性名稱（ **總執行時間** ）指派給 **Label** 索引鍵。 **運算式** 索引鍵的腳本區塊會計算目前日期的處理常式建立日期，以計算程式執行的時間長度。 `Get-Date`Cmdlet 會取得目前的日期。 建立日期會從目前日期減去。 結果是 **總執行時間** 的值。

### 範例8：針對格式錯誤進行疑難排解

下列範例顯示使用運算式新增 **DisplayError** 或 **ShowError** 參數的結果。

```powershell
Get-Date | Format-Table DayOfWeek,{ $_ / $null } -DisplayError
```

```Output
DayOfWeek  $_ / $null
--------- ------------
Wednesday #ERR
```

```powershell
Get-Date | Format-Table DayOfWeek,{ $_ / $null } -ShowError
```

```Output
DayOfWeek  $_ / $null
--------- ------------
Wednesday
Failed to evaluate expression " $_ / $null ".
    + CategoryInfo          : InvalidArgument: (11/27/2019 12:53:41:PSObject) [], RuntimeException
    + FullyQualifiedErrorId : mshExpressionError
```

## PARAMETERS

### -AutoSize

指出此 Cmdlet 會根據資料的寬度調整資料行大小和資料行數目。 根據預設，欄大小和欄數是由檢視決定。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -DisplayError

指出此 Cmdlet 會在命令列上顯示錯誤。 當您要將命令中的運算式格式化 `Format-Table` ，而且需要針對運算式進行疑難排解時，這個參數可以用來做為調試輔助。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Expand

指定集合物件的格式以及集合中的物件。 這個參數是設計來將支援 [ICollection](/dotnet/api/system.collections.icollection) ([system.object](/dotnet/api/system.collections) 的物件格式化) 介面。 預設值為 **EnumOnly** 。
此參數可接受的值如下：

- **EnumOnly** ：顯示集合中物件的屬性。
- **CoreOnly** ：顯示集合物件的屬性。
- **Both** ：顯示集合物件的屬性，以及集合中物件的屬性。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CoreOnly, EnumOnly, Both

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

指出此 Cmdlet 會指示 Cmdlet 顯示所有錯誤資訊。 搭配 **DisplayError** 或 **ShowError** 參數使用。 根據預設，將錯誤物件寫入錯誤或顯示串流時，只會顯示某些錯誤資訊。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -GroupBy

根據屬性值，在個別的資料表中指定排序的輸出。 例如，您可以使用 **GroupBy** ，根據其狀態在不同的資料表中列出服務。

輸入運算式或屬性。 **GroupBy** 參數需要排序物件。
使用 `Sort-Object` Cmdlet `Format-Table` 來將物件分組。

**GroupBy** 參數的值可以是新的計算屬性。 計算的屬性可以是腳本區塊或雜湊表。 有效的索引鍵/值組為：

- 名稱 (或標籤) - `<string>`
- 運算式 `<string>` 或 `<script block>`
- 字串 `<string>`

如需詳細資訊，請參閱 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)。

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -HideTableHeaders

省略表格中的欄標題。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

指定要格式化的物件。 輸入包含物件的變數，或輸入可取得物件的命令或運算式。

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

### -Property

指定顯示中出現的物件屬性及其出現順序。 輸入一或多個屬性名稱（以逗號分隔），或使用雜湊表顯示計算屬性。 允許使用萬用字元。

如果您省略這個參數，顯示在顯示中的屬性將取決於第一個物件的屬性。 例如，如果第一個物件具有 **PropertyA** 和 **PropertyB** ，但後續的物件具有 **PropertyA** 、 **PropertyB** 和 **PropertyC** ，則只會顯示 **PropertyA** 和 **PropertyB** 標頭。

**Property** 參數是選擇性的。 您無法在相同的命令中使用 **Property** 與 **View** 參數。

**Property** 參數的值可以是新的計算屬性。 計算的屬性可以是腳本區塊或雜湊表。 有效的索引鍵/值組為：

- 名稱 (或標籤) `<string>`
- 運算式 `<string>` 或 `<script block>`
- 字串 `<string>`
- 寬度- `<int32>` -必須大於 `0`
- 對齊-值可以是 `Left` 、 `Center` 或 `Right`

如需詳細資訊，請參閱 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)。

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -RepeatHeader

在每個畫面填滿之後重複顯示資料表的標頭。 當輸出輸送至分頁（例如 `less` 或） `more` 或使用螢幕讀取器進行分頁時，重複的標頭會很有用。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -ShowError

此參數會透過管線傳送錯誤。 當您要將命令中的運算式格式化 `Format-Table` ，而且需要針對運算式進行疑難排解時，這個參數可以用來做為調試輔助。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -View

在 PowerShell 5.1 及更早版本中，預設的視圖會定義在中儲存的檔案中 `*.format.ps1xml` `$PSHOME` 。

**View** 參數可讓您為數據表指定替代的格式或自訂的視圖。 您可以使用預設的 PowerShell views 或建立自訂的視圖。 如需如何建立自訂視圖的詳細資訊，請參閱 [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)。

**View** 參數的替代和自訂視圖必須使用資料表格式，否則 `Format-Table` 會失敗。 如果替代視圖是清單，請使用 `Format-List` Cmdlet。 如果替代視圖不是清單或資料表，請使用 `Format-Custom` Cmdlet。

您無法在相同的命令中使用 **Property** 與 **View** 參數。

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

### -Wrap

將超過欄寬度的文字顯示於下一行。 根據預設，系統會截斷超過欄寬度的文字。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.Management.Automation.PSObject

您可以將任何物件沿著管線向下傳送至 `Format-Table` 。

## 輸出

### Microsoft.PowerShell.Commands.Internal.Format

`Format-Table` 傳回代表資料表的格式物件。

## 注意

## 相關連結

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)

[about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)

[Export-FormatData](Export-FormatData.md)

[Format-Custom](Format-Custom.md)

[Format-Hex](Format-Hex.md)

[Format-List](Format-List.md)

[Format-Wide](Format-Wide.md)

[Get-FormatData](Get-FormatData.md)

[Get-Member](Get-Member.md)

[Get-CimInstance](../CimCmdlets/Get-CimInstance.md)

[Update-FormatData](Update-FormatData.md)
