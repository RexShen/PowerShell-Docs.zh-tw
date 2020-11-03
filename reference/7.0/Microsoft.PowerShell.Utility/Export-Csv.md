---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 1/7/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-csv?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Csv
ms.openlocfilehash: cb58276c8582f9cd1f88a114baae2ce5d0039f45
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201811"
---
# Export-Csv

## 概要
將物件轉換成一系列的逗號分隔值 (CSV) 字串，並將字串儲存至檔案。

## SYNTAX

### Delimiter (預設值)

```
Export-Csv -InputObject <PSObject> [[-Path] <String>] [-LiteralPath <String>] [-Force] [-NoClobber]
 [-Encoding <Encoding>] [-Append] [[-Delimiter] <Char>] [-IncludeTypeInformation]
 [-NoTypeInformation] [-QuoteFields <String[]>] [-UseQuotes <QuoteKind>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### UseCulture

```
Export-Csv -InputObject <PSObject> [[-Path] <String>] [-LiteralPath <String>] [-Force] [-NoClobber]
 [-Encoding <Encoding>] [-Append] [-UseCulture] [-IncludeTypeInformation] [-NoTypeInformation]
 [-QuoteFields <String[]>] [-UseQuotes <QuoteKind>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Export-CSV`Cmdlet 會建立您所提交之物件的 CSV 檔案。 每個物件都是一個資料列，其中包含以逗號分隔的物件屬性值清單。 您可以使用 `Export-CSV` Cmdlet 來建立試算表，並與接受 CSV 檔案做為輸入的程式共用資料。

將物件傳送至 Cmdlet 之前，請勿先將物件格式化 `Export-CSV` 。 如果 `Export-CSV` 接收格式化的物件，則 CSV 檔案會包含格式屬性，而不是物件屬性。 若只要匯出選取的物件屬性，請使用 `Select-Object` Cmdlet。

## 範例

### 範例1：將進程屬性匯出至 CSV 檔案

此範例會選取具有特定屬性的 **處理** 程式物件，並將物件匯出至 CSV 檔案。

```powershell
Get-Process -Name WmiPrvSE | Select-Object -Property BasePriority,Id,SessionId,WorkingSet |
  Export-Csv -Path .\WmiData.csv -NoTypeInformation
Import-Csv -Path .\WmiData.csv
```

```Output
BasePriority Id    SessionId WorkingSet
------------ --    --------- ----------
8            976   0         20267008
8            2292  0         36786176
8            3816  0         30351360
8            8604  0         15011840
8            10008 0         8830976
8            11764 0         14237696
8            54632 0         9502720
```

`Get-Process`Cmdlet 會取得 **處理** 程式物件。 **Name** 參數會篩選輸出，只包含 WmiPrvSE 處理物件。 處理常式物件會向下傳送至 `Select-Object` Cmdlet。 `Select-Object` 使用 **Property** 參數來選取處理常式物件屬性的子集。 處理常式物件會向下傳送至 `Export-Csv` Cmdlet。 `Export-Csv` 將處理常式物件轉換成一系列的 CSV 字串。 **Path** 參數指定 WmiData.csv 檔案儲存在目前的目錄中。 **NoTypeInformation** 參數會從 CSV 輸出移除 **#TYPE** 資訊標頭，且在 PowerShell 6 中不需要。 此 `Import-Csv` Cmdlet 會使用 **Path** 參數來顯示位於目前的目錄中的檔案。

### 範例2：將進程匯出至逗號分隔的檔案

這個範例會取得 **處理** 程式物件，並將物件匯出至 CSV 檔案。

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Parent","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","511","2203597099008","35364864","21979136","30048", ...
```

`Get-Process`Cmdlet 會取得 **處理** 程式物件。 處理常式物件會向下傳送至 `Export-Csv` Cmdlet。 `Export-Csv` 將處理常式物件轉換成一系列的 CSV 字串。
**Path** 參數指定 Processes.csv 檔案儲存在目前的目錄中。 **NoTypeInformation** 參數會從 CSV 輸出移除 **#TYPE** 資訊標頭，且在 PowerShell 6 中不需要。 此 `Get-Content` Cmdlet 會使用 **Path** 參數來顯示位於目前的目錄中的檔案。

### 範例3：將進程匯出至分號分隔的檔案

此範例會取得 **處理** 程式物件，並將物件匯出為具有分號分隔符號的檔案。

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -Delimiter ';' -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name";"SI";"Handles";"VM";"WS";"PM";"NPM";"Path";"Parent";"Company";"CPU";"FileVersion"; ...
"ApplicationFrameHost";"4";"509";"2203595321344";"34807808";"21770240";"29504"; ...
```

`Get-Process`Cmdlet 會取得 **處理** 程式物件。 處理常式物件會向下傳送至 `Export-Csv` Cmdlet。 `Export-Csv` 將處理常式物件轉換成一系列的 CSV 字串。
**Path** 參數指定 Processes.csv 檔案儲存在目前的目錄中。 **分隔符號** 參數會指定分號來分隔字串值。 **NoTypeInformation** 參數會從 CSV 輸出移除 **#TYPE** 資訊標頭，且在 PowerShell 6 中不需要。 此 `Get-Content` Cmdlet 會使用 **Path** 參數來顯示位於目前的目錄中的檔案。

### 範例4：使用目前文化特性的清單分隔符號來匯出進程

這個範例會取得 **處理** 程式物件，並將物件匯出到檔案。 分隔符號是目前文化特性的清單分隔符號。

```powershell
(Get-Culture).TextInfo.ListSeparator
Get-Process | Export-Csv -Path .\Processes.csv -UseCulture -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Parent","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","511","2203597099008","35364864","21979136","30048", ...
```

此 `Get-Culture` Cmdlet 會使用 **TextInfo** 和 **ListSeparator** 的 nested 屬性，並顯示目前文化特性的預設清單分隔符號。 `Get-Process`Cmdlet 會取得 **處理** 程式物件。
處理常式物件會向下傳送至 `Export-Csv` Cmdlet。 `Export-Csv` 將處理常式物件轉換成一系列的 CSV 字串。 **Path** 參數指定 Processes.csv 檔案儲存在目前的目錄中。 **UseCulture** 參數會使用目前文化特性的預設清單分隔符號做為分隔符號。 **NoTypeInformation** 參數會從 CSV 輸出移除 **#TYPE** 資訊標頭，且在 PowerShell 6 中不需要。 此 `Get-Content` Cmdlet 會使用 **Path** 參數來顯示位於目前的目錄中的檔案。

### 範例5：匯出具有類型資訊的處理常式

此範例說明如何在 CSV 檔案中包含 **#TYPE** 的標頭資訊。 在 PowerShell 6.0 之前的版本中， **#TYPE** 標頭是預設值。

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -IncludeTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
#TYPE System.Diagnostics.Process
"Name","SI","Handles","VM","WS","PM","NPM","Path","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","507","2203595001856","35139584","20934656","29504", ...
```

`Get-Process`Cmdlet 會取得 **處理** 程式物件。 處理常式物件會向下傳送至 `Export-Csv` Cmdlet。 `Export-Csv` 將處理常式物件轉換成一系列的 CSV 字串。
**Path** 參數指定 Processes.csv 檔案儲存在目前的目錄中。 **IncludeTypeInformation** 會在 CSV 輸出中包含 **#TYPE** 資訊標頭。 此 `Get-Content` Cmdlet 會使用 **Path** 參數來顯示位於目前的目錄中的檔案。

### 範例6：匯出和附加物件至 CSV 檔案

此範例說明如何將物件匯出至 CSV 檔案，並使用 **Append** 參數將物件加入至現有的檔案。

```powershell
$AppService = (Get-Service -DisplayName *Application* | Select-Object -Property DisplayName, Status)
$AppService | Export-Csv -Path .\Services.Csv -NoTypeInformation
Get-Content -Path .\Services.Csv
$WinService = (Get-Service -DisplayName *Windows* | Select-Object -Property DisplayName, Status)
$WinService | Export-Csv -Path ./Services.csv -NoTypeInformation -Append
Get-Content -Path .\Services.Csv
```

```Output
"DisplayName","Status"
"Application Layer Gateway Service","Stopped"
"Application Identity","Running"
"Windows Audio Endpoint Builder","Running"
"Windows Audio","Running"
"Windows Event Log","Running"
```

`Get-Service`Cmdlet 會取得服務物件。 **DisplayName** 參數會傳回包含 Word 應用程式的服務。 服務物件會向下傳送至 `Select-Object` Cmdlet。 `Select-Object` 使用 **Property** 參數來指定 **DisplayName** 和 **Status** 屬性。 `$AppService`變數會儲存物件。

這些 `$AppService` 物件會向下傳送至 `Export-Csv` Cmdlet。 `Export-Csv` 將服務物件轉換成一系列的 CSV 字串。 **Path** 參數指定 Services.csv 檔案儲存在目前的目錄中。 **NoTypeInformation** 參數會從 CSV 輸出移除 **#TYPE** 資訊標頭，且在 PowerShell 6 中不需要。 此 `Get-Content` Cmdlet 會使用 **Path** 參數來顯示位於目前的目錄中的檔案。

`Get-Service`和 `Select-Object` Cmdlet 會針對包含 word 視窗的服務重複執行。 `$WinService`變數會儲存服務物件。 指令 `Export-Csv` 程式會使用 **Append** 參數來指定將 `$WinService` 物件加入至現有的 Services.csv 檔案。 此 `Get-Content` Cmdlet 會重複顯示已更新的檔案，其中包含附加的資料。

### 範例7：管線中的 Format Cmdlet 會建立非預期的結果

此範例示範為什麼在管線內不使用 format Cmdlet 是很重要的。 收到未預期的輸出時，請針對管線語法進行疑難排解。

```powershell
Get-Date | Select-Object -Property DateTime, Day, DayOfWeek, DayOfYear |
 Export-Csv -Path .\DateTime.csv -NoTypeInformation
Get-Content -Path .\DateTime.csv
```

```Output
"DateTime","Day","DayOfWeek","DayOfYear"
"Wednesday, January 2, 2019 14:59:34","2","Wednesday","2"
```

```powershell
Get-Date | Format-Table -Property DateTime, Day, DayOfWeek, DayOfYear |
 Export-Csv -Path .\FTDateTime.csv -NoTypeInformation
Get-Content -Path .\FTDateTime.csv
```

```Output
"ClassId2e4f51ef21dd47e99d3c952918aff9cd","pageHeaderEntry","pageFooterEntry","autosizeInfo", ...
"033ecb2bc07a4d43b5ef94ed5a35d280",,,,"Microsoft.PowerShell.Commands.Internal.Format. ...
"9e210fe47d09416682b841769c78b8a3",,,,,
"27c87ef9bbda4f709f6b4002fa4af63c",,,,,
"4ec4f0187cb04f4cb6973460dfe252df",,,,,
"cf522b78d86c486691226b40aa69e95c",,,,,
```

`Get-Date`Cmdlet 會取得 **DateTime** 物件。 物件會向下傳送至 `Select-Object` Cmdlet。 `Select-Object` 使用 **Property** 參數來選取物件屬性的子集。 物件會向下傳送至 `Export-Csv` Cmdlet。 `Export-Csv` 將物件轉換成 CSV 格式。 **Path** 參數指定 DateTime.csv 檔案儲存在目前的目錄中。 **NoTypeInformation** 參數會從 CSV 輸出移除 **#TYPE** 資訊標頭，且在 PowerShell 6 中不需要。 此 `Get-Content` Cmdlet 會使用 **Path** 參數來顯示位於目前的目錄中的 CSV 檔案。

在 `Format-Table` 管線中使用 Cmdlet 來選取屬性時，會收到未預期的結果。 `Format-Table` 將表格格式物件沿著管線向下傳送至 `Export-Csv` Cmdlet，而不是 **DateTime** 物件。 `Export-Csv` 將表格格式物件轉換成一系列的 CSV 字串。 此 `Get-Content` Cmdlet 會顯示包含表格格式物件的 CSV 檔案。

### 範例8：使用 Force 參數來覆寫唯讀檔案

這個範例會建立一個空白的唯讀檔案，並使用 **Force** 參數來更新檔案。

```powershell
New-Item -Path .\ReadOnly.csv -ItemType File
Set-ItemProperty -Path .\ReadOnly.csv -Name IsReadOnly -Value $true
Get-Process | Export-Csv -Path .\ReadOnly.csv -NoTypeInformation
```

```Output
Export-Csv : Access to the path 'C:\ReadOnly.csv' is denied.
At line:1 char:15
+ Get-Process | Export-Csv -Path .\ReadOnly.csv -NoTypeInformation
+               ~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : OpenError: (:) [Export-Csv], UnauthorizedAccessException
+ FullyQualifiedErrorId : FileOpenFailure,Microsoft.PowerShell.Commands.ExportCsvCommand
```

```powershell
Get-Process | Export-Csv -Path .\ReadOnly.csv -NoTypeInformation -Force
Get-Content -Path .\ReadOnly.csv
```

```Output
"Name";"SI";"Handles";"VM";"WS";"PM";"NPM";"Path";"Parent";"Company";"CPU";"FileVersion"; ...
"ApplicationFrameHost";"4";"509";"2203595321344";"34807808";"21770240";"29504"; ...
```

此 `New-Item` Cmdlet 會使用 **Path** 和 **ItemType** 參數，在目前的目錄中建立 ReadOnly.csv 檔案。 此 `Set-ItemProperty` Cmdlet 會使用 **Name** 和 **Value** 參數將檔案的 **IsReadOnly** 屬性變更為 true。 `Get-Process`Cmdlet 會取得 **處理** 程式物件。 處理常式物件會向下傳送至 `Export-Csv` Cmdlet。 `Export-Csv` 將處理常式物件轉換成一系列的 CSV 字串。 **Path** 參數指定 ReadOnly.csv 檔案儲存在目前的目錄中。 **NoTypeInformation** 參數會從 CSV 輸出移除 **#TYPE** 資訊標頭，且在 PowerShell 6 中不需要。 輸出顯示未寫入檔案，因為拒絕存取。

**Force** 參數會新增至 `Export-Csv` Cmdlet，以強制匯出寫入檔案。 此 `Get-Content` Cmdlet 會使用 **Path** 參數來顯示位於目前的目錄中的檔案。

### 範例9：使用 Force 參數搭配 Append

這個範例示範如何使用 **Force** 與 **Append** 參數。 結合這些參數時，可以將不相符的物件屬性寫入 CSV 檔案。

```powershell
$Content = [PSCustomObject]@{Name = 'PowerShell Core'; Version = '6.0'}
$Content | Export-Csv -Path .\ParmFile.csv -NoTypeInformation
$AdditionalContent = [PSCustomObject]@{Name = 'Windows PowerShell'; Edition = 'Desktop'}
$AdditionalContent | Export-Csv -Path .\ParmFile.csv -NoTypeInformation -Append
```

```Output
Export-Csv : Cannot append CSV content to the following file: ParmFile.csv.
The appended object does not have a property that corresponds to the following column:
Version. To continue with mismatched properties, add the -Force parameter, and then retry
 the command.
At line:1 char:22
+ $AdditionalContent | Export-Csv -Path .\ParmFile.csv -NoTypeInformation -Append
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : InvalidData: (Version:String) [Export-Csv], InvalidOperationException
+ FullyQualifiedErrorId : CannotAppendCsvWithMismatchedPropertyNames,Microsoft.PowerShell. ...
```

```powershell
$AdditionalContent | Export-Csv -Path .\ParmFile.csv -NoTypeInformation -Append -Force
Import-Csv -Path .\ParmFile.csv
```

```Output
Name               Version
----               -------
PowerShell Core    6.0
Windows PowerShell
```

運算式會建立具有 **Name** 和 **Version** 屬性的 **PSCustomObject** 。 這些值會儲存在 `$Content` 變數中。 此 `$Content` 變數會向下傳送至 `Export-Csv` Cmdlet。 `Export-Csv` 使用 **Path** 參數，並將 ParmFile.csv 檔案儲存在目前的目錄中。 **NoTypeInformation** 參數會從 CSV 輸出移除 **#TYPE** 資訊標頭，且在 PowerShell 6 中不需要。

另一個運算式會以 **Name** 和 **Edition** 屬性來建立 **PSCustomObject** 。 這些值會儲存在 `$AdditionalContent` 變數中。 此 `$AdditionalContent` 變數會向下傳送至 `Export-Csv` Cmdlet。 **Append** 參數是用來將資料新增至檔案。 附加失敗，因為 **版本****與版本之間** 的屬性名稱不相符。

`Export-Csv`Cmdlet **force** 參數是用來強制匯出寫入檔案。 已捨棄 **版本** 屬性。 此 `Import-Csv` Cmdlet 會使用 **Path** 參數來顯示位於目前的目錄中的檔案。

### 範例10：使用引號括住兩個數據行來匯出至 CSV

這個範例會將 **DateTime** 物件轉換成 CSV 字串。

```powershell
Get-Date | Export-Csv  -QuoteFields "DateTime","Date" -Path .\FTDateTime.csv
Get-Content -Path .\FTDateTime.csv
```

```Output
DisplayHint,"DateTime","Date",Day,DayOfWeek,DayOfYear,Hour,Kind,Millisecond,Minute,Month,Second,Ticks,TimeOfDay,Year
DateTime,"Thursday, August 22, 2019 11:27:34 AM","8/22/2019 12:00:00 AM",22,Thursday,234,11,Local,569,27,8,34,637020700545699784,11:27:34.5699784,2019
```

### 範例11：只有在需要時才使用引號匯出至 CSV

這個範例會將 **DateTime** 物件轉換成 CSV 字串。

```powershell
Get-Date | Export-Csv  -UseQuotes AsNeeded -Path .\FTDateTime.csv
Get-Content -Path .\FTDateTime.csv
```

```Output
DisplayHint,DateTime,Date,Day,DayOfWeek,DayOfYear,Hour,Kind,Millisecond,Minute,Month,Second,Ticks,TimeOfDay,Year
DateTime,"Thursday, August 22, 2019 11:31:00 AM",8/22/2019 12:00:00 AM,22,Thursday,234,11,Local,713,31,8,0,637020702607132640,11:31:00.7132640,2019
```

## PARAMETERS

### -Append

使用這個參數 `Export-CSV` 可將 CSV 輸出新增至指定檔案的結尾。 如果沒有這個參數， `Export-CSV` 則會取代檔案內容而不發出警告。

此參數是在 Windows PowerShell 3.0 引進。

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

### -Delimiter

指定分隔符號以區隔屬性值。 預設值是逗號 (`,`) 。 輸入字元，例如冒號 (`:`) 。 若要指定分號 (`;`) ，請將它括在引號中。

```yaml
Type: System.Char
Parameter Sets: Delimiter
Aliases:

Required: False
Position: 1
Default value: comma (,)
Accept pipeline input: False
Accept wildcard characters: False
```

### -Encoding

指定匯出之 CSV 檔案的編碼。 預設值是 `utf8NoBOM`。

此參數可接受的值如下：

- `ascii`：使用 ASCII (7 位) 字元集的編碼方式。
- `bigendianunicode`：使用位元組由大到小的位元組順序，以 UTF-16 格式編碼。
- `oem`：針對 MS-DOS 和主控台程式使用預設編碼。
- `unicode`：使用位元組由大到小的位元組順序，以 UTF-16 格式編碼。
- `utf7`：以 UTF-7 格式編碼。
- `utf8`：以 UTF-8 格式編碼。
- `utf8BOM`：使用 (BOM) 的位元組順序標記來編碼 UTF-8 格式
- `utf8NoBOM`：以不含位元組順序標記的 UTF-8 格式來編碼 (BOM) 
- `utf32`：以 UTF-32 格式編碼。

從 PowerShell 6.2 開始， **編碼** 參數也會允許已註冊字碼頁的數值識別碼 (例如 `-Encoding 1251`) 或已註冊字碼頁的字串名稱 (例如 `-Encoding "windows-1251"`) 。 如需詳細資訊，請參閱 .NET 檔中的 [編碼字碼頁](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)。

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

此參數可讓您 `Export-Csv` 以 **唯讀** 屬性覆寫檔案。

結合 **Force** 和 **Append** 參數時，包含不相符之屬性的物件可以寫入 CSV 檔案。 只有符合的屬性會寫入至檔案。 捨棄不相符的屬性。

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

### -IncludeTypeInformation

使用這個參數時，CSV 輸出的第一行會包含 **#TYPE** ，後面接著物件類型的完整名稱。 例如， **#TYPE 的系統診斷** 。

此參數是在 PowerShell 6.0 中引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ITI

Required: False
Position: Named
Default value: #TYPE <Object>
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

指定要匯出為 CSV 字串的物件。 輸入包含物件的變數，或輸入可取得物件的命令或運算式。 您也可以透過管線將物件傳送至 `Export-CSV` 。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -LiteralPath

指定 CSV 輸出檔案的路徑。 與 **Path** 不同， **LiteralPath** 參數值將完全依照其輸入值來使用。 沒有字元會被視為萬用字元。 如果路徑包含 escape 字元，請使用單引號。 單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath, LP

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoClobber

使用此參數，就 `Export-CSV` 不會覆寫現有的檔案。 根據預設，如果檔案存在指定的路徑中， `Export-CSV` 會覆寫檔案而不發出警告。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoTypeInformation

從輸出中移除 **#TYPE** 資訊標頭。 此參數會成為 PowerShell 6.0 中的預設值，並包含以提供回溯相容性。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NTI

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

必要參數，指定要儲存 CSV 輸出檔的位置。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseCulture

使用目前文化特性的清單分隔字元做為專案分隔符號。 若要尋找文化特性的清單分隔符號，請使用下列命令： `(Get-Culture).TextInfo.ListSeparator` 。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UseCulture
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

在執行 Cmdlet 前提示您確認。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

防止 Cmdlet 進行處理或變更。 輸出會顯示執行 Cmdlet 後會發生的狀況。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -QuoteFields

指定應該加上引號的資料行名稱。 使用這個參數時，只會加上指定的資料行。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: QF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseQuotes

指定 CSV 檔案中使用引號的時機。 可能的值包括：

- 永遠不會引述任何事
- 一律將所有專案加上引號 (預設行為) 
- >asneeded-僅包含分隔符號的引號欄位

```yaml
Type: Microsoft.PowerShell.Commands.BaseCsvWritingCommand+QuoteKind
Parameter Sets: (All)
Aliases: UQ

Required: False
Position: Named
Default value: Always
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.Management.Automation.PSObject

您可以使用管線將任何具有擴充類型系統 (ETS) adapter 的物件傳送至 `Export-CSV` 。

## 輸出

### System.String

CSV 清單會傳送至 Path 參數中指定的檔案。

## 注意

`Export-CSV`Cmdlet 會將您提交的物件轉換成一系列的 CSV 字串，並將它們儲存在指定的文字檔中。 您可以使用將 `Export-CSV -IncludeTypeInformation` 物件儲存在 csv 檔案中，然後使用 `Import-Csv` CMDLET 從 csv 檔案中的文字建立物件。

在 CSV 檔案中，每個物件都會利用以逗號分隔的物件屬性值清單來表示。 屬性值會使用 **ToString ( # B1** 方法轉換成字串。 字串會以屬性值名稱表示。 `Export-CSV -IncludeTypeInformation` 不會匯出物件的方法。

CSV 字串的輸出如下所示：

- 如果使用 **IncludeTypeInformation** ，則第一個字串會包含 **#TYPE** 資訊標頭，後面接著物件類型的完整名稱。
  例如， **#TYPE 的系統診斷** 。
- 如果未使用 **IncludeTypeInformation** ，則第一個字串會包含資料行標頭。 標頭包含第一個物件的屬性名稱，做為逗點分隔清單。
- 其餘的字串包含每個物件之屬性值的逗號分隔清單。

從 PowerShell 6.0 開始，的預設行為 `Export-CSV` 是不包含 CSV 中的 **#TYPE** 資訊，而且 **NoTypeInformation** 是隱含的。 **IncludeTypeInformation** 可以用來包含 **#TYPE** 資訊，並模擬 `Export-CSV` PowerShell 6.0 之前的預設行為。

當您將多個物件提交至時 `Export-CSV` ，會 `Export-CSV` 根據您所提交之第一個物件的屬性來組織檔案。 如果其餘的物件不具有指定之屬性的其中之一，該物件的屬性值會是 null，以兩個連續的逗號表示。 如果其餘的物件有其他屬性，那些屬性值將不會包含在檔案中。

您可以使用 `Import-Csv` Cmdlet，從檔案中的 CSV 字串重新建立物件。 產生的物件是 CSV 版本的原始物件，包含屬性值的字串表示，而且不含方法。

`ConvertTo-Csv`和 `ConvertFrom-Csv` Cmdlet 會將物件轉換成 csv 字串和 csv 字串。 `Export-CSV` 與相同 `ConvertTo-CSV` ，不同之處在于它會將 CSV 字串儲存在檔案中。

## 相關連結

[ConvertFrom-Csv](ConvertFrom-Csv.md)

[ConvertTo-Csv](ConvertTo-Csv.md)

[Format-Table](Format-Table.md)

[Import-Csv](Import-Csv.md)

[Select-Object](Select-Object.md)
