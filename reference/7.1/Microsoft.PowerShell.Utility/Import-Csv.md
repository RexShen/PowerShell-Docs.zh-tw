---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-csv?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Csv
ms.openlocfilehash: e33da9b461086e85e1fa074b0bed60ac275894b4
ms.sourcegitcommit: 9a8bb1b459b5939c95e1f6d9499fcb13d01a58c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "93206103"
---
# Import-Csv

## 概要
以逗號分隔值 (CSV) 檔中的專案建立類似表格的自訂物件。

## SYNTAX

### DelimiterPath (預設) 

```
Import-Csv [[-Delimiter] <Char>] [-Path] <String[]> [-Header <String[]>] [-Encoding <Encoding>]
 [<CommonParameters>]
```

### DelimiterLiteralPath

```
Import-Csv [[-Delimiter] <Char>] -LiteralPath <String[]> [-Header <String[]>] [-Encoding <Encoding>]
 [<CommonParameters>]
```

### CulturePath

```
Import-Csv [-Path] <String[]> -UseCulture [-Header <String[]>] [-Encoding <Encoding>]
 [<CommonParameters>]
```

### CultureLiteralPath

```
Import-Csv -LiteralPath <String[]> -UseCulture [-Header <String[]>] [-Encoding <Encoding>]
 [<CommonParameters>]
```

## DESCRIPTION

`Import-Csv`Cmdlet 會從 CSV 檔案中的專案建立類似表格的自訂物件。 CSV 檔案中的每個資料行都會變成自訂物件的屬性，而資料列中的專案則會成為屬性值。 `Import-Csv` 適用于任何 CSV 檔案，包括 Cmdlet 所產生的檔案 `Export-Csv` 。

您可以使用 Cmdlet 的參數 `Import-Csv` 來指定欄標題列和專案分隔符號，或直接 `Import-Csv` 使用目前文化特性的清單分隔字元做為專案分隔符號。

您也可以使用 `ConvertTo-Csv` 和 `ConvertFrom-Csv` Cmdlet，將物件轉換為 CSV 字串 (和回) 。 這些 Cmdlet 與 `Export-CSV` 和 `Import-Csv` Cmdlet 相同，不同之處在于它們不會處理檔案。

如果 CSV 檔案中的標題列專案包含空白或 null 值，則 PowerShell 會插入預設標頭資料列名稱，並顯示警告訊息。

從 PowerShell 6.0 開始， `Import-Csv` 現在支援 W3C 擴充記錄檔格式。

## 範例

### 範例1：匯入處理物件

這個範例示範如何匯出和匯入處理常式物件的 CSV 檔案。

```powershell
Get-Process | Export-Csv -Path .\Processes.csv
$P = Import-Csv -Path .\Processes.csv
$P | Get-Member
```

```Output
   TypeName: System.Management.Automation.PSCustomObject

Name                       MemberType   Definition
----                       ----------   ----------
Equals                     Method       bool Equals(System.Object obj)
GetHashCode                Method       int GetHashCode()
GetType                    Method       type GetType()
ToString                   Method       string ToString()
BasePriority               NoteProperty string BasePriority=8
Company                    NoteProperty string Company=Microsoft Corporation
...
```

```powershell
$P | Format-Table
```

```Output
Name                   SI Handles VM            WS        PM        NPM    Path
----                   -- ------- --            --        --        ---    ----
ApplicationFrameHost   4  407     2199293489152 15884288  15151104  23792  C:\WINDOWS\system32\ApplicationFrameHost.exe
...
wininit                0  157     2199112204288 4591616   1630208   10376
winlogon               4  233     2199125549056 7659520   2826240   10992  C:\WINDOWS\System32\WinLogon.exe
WinStore.App           4  846     873435136     33652736  26607616  55432  C:\Program Files\WindowsApps\Microsoft.WindowsStore_11712.1001.13.0_x64__8weky...
WmiPrvSE               0  201     2199100219392 8830976   3297280   10632  C:\WINDOWS\system32\wbem\wmiprvse.exe
WmiPrvSE               0  407     2199157727232 18509824  12922880  16624  C:\WINDOWS\system32\wbem\wmiprvse.exe
WUDFHost               0  834     2199310204928 51945472  87441408  24984  C:\Windows\System32\WUDFHost.exe
```

`Get-Process`Cmdlet 會將處理常式物件向下傳送至 `Export-Csv` 。 `Export-Csv`Cmdlet 會將處理常式物件轉換為 CSV 字串，並將字串儲存在 Processes.csv 檔案中。 `Import-Csv`Cmdlet 會從 Processes.csv 檔案匯入 CSV 字串。
字串會儲存在變數中 `$P` 。 `$P`變數會向下傳送至 `Get-Member` Cmdlet，以顯示已匯入之 CSV 字串的屬性。 `$P`變數會向下傳送至 `Format-Table` Cmdlet，並顯示物件。

### 範例2：指定分隔符號

此範例說明如何使用 Cmdlet 的 **分隔符號** 參數 `Import-Csv` 。

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -Delimiter :
$P = Import-Csv -Path .\Processes.csv -Delimiter :
$P | Format-Table
```

`Get-Process`Cmdlet 會將處理常式物件向下傳送至 `Export-Csv` 。 `Export-Csv`Cmdlet 會將處理常式物件轉換為 CSV 字串，並將字串儲存在 Processes.csv 檔案中。
**分隔符號** 參數是用來指定冒號分隔符號。 `Import-Csv`Cmdlet 會從 Processes.csv 檔案匯入 CSV 字串。 字串會儲存在變數中 `$P` 。 To `$P` 變數會向下傳送至 `Format-Table` Cmdlet。

### 範例3：指定分隔符號的目前文化特性

此範例說明如何搭配使用 `Import-Csv` Cmdlet 與 **UseCulture** 參數。

```powershell
(Get-Culture).TextInfo.ListSeparator
Get-Process | Export-Csv -Path .\Processes.csv -UseCulture
Import-Csv -Path .\Processes.csv -UseCulture
```

此 `Get-Culture` Cmdlet 會使用 **TextInfo** 和 **ListSeparator** 的 nested 屬性來取得目前文化特性的預設清單分隔符號。 `Get-Process`Cmdlet 會將處理常式物件向下傳送至 `Export-Csv` 。 `Export-Csv`Cmdlet 會將處理常式物件轉換為 CSV 字串，並將字串儲存在 Processes.csv 檔案中。 **UseCulture** 參數會使用目前文化特性的預設清單分隔符號。 `Import-Csv`Cmdlet 會從 Processes.csv 檔案匯入 CSV 字串。

### 範例4：變更匯入物件中的屬性名稱

這個範例示範如何使用的 **Header** 參數 `Import-Csv` ，變更所產生匯入物件中的屬性名稱。

```powershell
Start-Job -ScriptBlock { Get-Process } | Export-Csv -Path .\Jobs.csv -NoTypeInformation
$Header = 'State', 'MoreData', 'StatusMessage', 'Location', 'Command', 'StateInfo', 'Finished', 'InstanceId', 'Id', 'Name', 'ChildJobs', 'BeginTime', 'EndTime', 'JobType', 'Output', 'Error', 'Progress', 'Verbose', 'Debug', 'Warning', 'Information'
# Delete the default header from file
$A = Get-Content -Path .\Jobs.csv
$A = $A[1..($A.Count - 1)]
$A | Out-File -FilePath .\Jobs.csv
$J = Import-Csv -Path .\Jobs.csv -Header $Header
$J
```

```Output
State         : Running
MoreData      : True
StatusMessage :
Location      : localhost
Command       : Get-Process
StateInfo     : Running
Finished      : System.Threading.ManualResetEvent
InstanceId    : a259eb63-6824-4b97-a033-305108ae1c2e
Id            : 1
Name          : Job1
ChildJobs     : System.Collections.Generic.List`1[System.Management.Automation.Job]
BeginTime     : 12/20/2018 18:59:57
EndTime       :
JobType       : BackgroundJob
Output        : System.Management.Automation.PSDataCollection`1[System.Management.Automation.PSObject]
Error         : System.Management.Automation.PSDataCollection`1[System.Management.Automation.ErrorRecord]
Progress      : System.Management.Automation.PSDataCollection`1[System.Management.Automation.ProgressRecord]
Verbose       : System.Management.Automation.PSDataCollection`1[System.Management.Automation.VerboseRecord]
Debug         : System.Management.Automation.PSDataCollection`1[System.Management.Automation.DebugRecord]
Warning       : System.Management.Automation.PSDataCollection`1[System.Management.Automation.WarningRecord]
Information   : System.Management.Automation.PSDataCollection`1[System.Management.Automation.InformationRecord]
```

`Start-Job`Cmdlet 會啟動執行的背景工作 `Get-Process` 。 工作物件會向下傳送至 `Export-Csv` Cmdlet，並轉換成 CSV 字串。 **NoTypeInformation** 參數會從 CSV 輸出移除類型資訊標頭，而且在 PowerShell Core 中是選擇性的。
`$Header`變數包含會取代下列預設值的自訂標頭： **HasMoreData** 、 **JobStateInfo** 、 **PSBeginTime** 、 **PSEndTime** 和 **PSJobTypeName** 。 此 `$A` 變數會使用 `Get-Content` Cmdlet 從 Jobs.csv 檔案取得 CSV 字串。 `$A`變數是用來從檔案移除預設的標頭。 Cmdlet 會將 `Out-File` 新版本的 Jobs.csv 檔案儲存在變數中 `$A` 。 Cmdlet 會匯 `Import-Csv` 入 Jobs.csv 的檔案，並 **使用 Header** 參數來套用 `$Header` 變數。 `$J`變數包含匯入的 **PSCustomObject** ，並在 PowerShell 主控台中顯示物件。

### 範例5：使用 CSV 檔案建立自訂物件

此範例示範如何使用 CSV 檔案，在 PowerShell 中建立自訂物件。

```powershell
Get-Content -Path .\Links.csv
```

```Output
113207,about_Aliases
113208,about_Arithmetic_Operators
113209,about_Arrays
113210,about_Assignment_Operators
113212,about_Automatic_Variables
113213,about_Break
113214,about_Command_Precedence
113215,about_Command_Syntax
144309,about_Comment_Based_Help
113216,about_CommonParameters
113217,about_Comparison_Operators
113218,about_Continue
113219,about_Core_Commands
113220,about_Data_Section
```

```powershell
$A = Import-Csv -Path .\Links.csv -Header 'LinkID', 'TopicTitle'
$A | Get-Member
```

```Output
   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
LinkID      NoteProperty string LinkID=113207
TopicTitle  NoteProperty string TopicTitle=about_Aliases
```

```powershell
$A | Where-Object -Property TopicTitle -Like '*alias*'
```

```Output
LinkID TopicTitle
------ ----------
113207 about_Aliases
```

若要建立 Links.csv 檔案，請使用輸出中所顯示的值 `Get-Content` 。

`Get-Content`Cmdlet 會顯示 Links.csv 檔案。 Cmdlet 會匯 `Import-Csv` 入 Links.csv 的檔案。 **Header** 參數會指定屬性名稱 **LinkId** 和 **TopicTitle** 。 物件會儲存在變數中 `$A` 。 此 `Get-Member` Cmdlet 會顯示 **標頭** 參數中的屬性名稱。 此 `Where-Object` Cmdlet 會選取具有 **TopicTitle** 屬性（包含 **別名** ）的物件。

### 範例6：匯入缺少值的 CSV

此範例說明 `Import-Csv` 當 CSV 檔案中的標頭資料列包含 null 或空白值時，PowerShell 中的 Cmdlet 如何回應。 `Import-Csv` 替代遺漏標頭資料列的預設名稱，該資料行會成為傳回之物件的屬性名稱 `Import-Csv` 。

```powershell
Get-Content -Path .\Projects.csv
```

```Output
ProjectID,ProjectName,,Completed
13,Inventory,Redmond,True
440,,FarEast,True
469,Marketing,Europe,False
```

```powershell
Import-Csv -Path .\Projects.csv
```

```Output
WARNING: One or more headers were not specified. Default names starting with "H" have been used in place of any missing headers.

ProjectID ProjectName H1      Completed
--------- ----------- --      ---------
13        Inventory   Redmond True
440                   FarEast True
469       Marketing   Europe  False
```

```powershell
(Import-Csv -Path .\Projects.csv).H1
```

```Output
WARNING: One or more headers were not specified. Default names starting with "H" have been used in place of any missing headers.
Redmond
FarEast
Europe
```

若要建立 Projects.csv 檔案，請使用範例輸出中所示的值 `Get-Content` 。

`Get-Content`Cmdlet 會顯示 Projects.csv 檔案。 標頭資料列缺少 **專案名稱** 與 **已完成** 之間的值。 `Import-Csv`Cmdlet 會匯入 Projects.csv 檔案並顯示警告訊息，因為 **H1** 是預設的標頭名稱。 此 `(Import-Csv -Path
.\Projects.csv).H1` 命令會取得 **H1** 屬性值並顯示警告。

## PARAMETERS

### -Delimiter

指定 CSV 檔案中用來分隔屬性值的分隔符號。
預設值為逗號 (,)。

輸入字元，例如冒號 (:)。
若要指定分號 (; ) 將它括在單引號中。

如果您在檔案中指定實際字串分隔符號以外的字元，就 `Import-Csv` 無法從 csv 字串建立物件，而且會傳回 csv 字串。

```yaml
Type: System.Char
Parameter Sets: DelimiterPath, DelimiterLiteralPath
Aliases:

Required: False
Position: 1
Default value: comma (,)
Accept pipeline input: False
Accept wildcard characters: False
```

### -Encoding

指定匯入之 CSV 檔案的編碼方式。 預設值是 `utf8NoBOM`。

此參數可接受的值如下：

- `ascii`：使用 ASCII (7 位) 字元集的編碼方式。
- `bigendianunicode`：使用位元組由大到小的位元組順序，以 UTF-16 格式編碼。
- `bigendianutf32`：使用位元組由大到小的順序，以 UTF-32 格式編碼。
- `oem`：針對 MS-DOS 和主控台程式使用預設編碼。
- `unicode`：使用位元組由大到小的位元組順序，以 UTF-16 格式編碼。
- `utf7`：以 UTF-7 格式編碼。
- `utf8`：以 UTF-8 格式編碼。
- `utf8BOM`：使用 (BOM) 的位元組順序標記來編碼 UTF-8 格式
- `utf8NoBOM`：以不含位元組順序標記的 UTF-8 格式來編碼 (BOM) 
- `utf32`：以 UTF-32 格式編碼。

從 PowerShell 6.2 開始， **編碼** 參數也會允許已註冊字碼頁的數值識別碼 (例如 `-Encoding 1251`) 或已註冊字碼頁的字串名稱 (例如 `-Encoding "windows-1251"`) 。 如需詳細資訊，請參閱 .NET 檔中的 [編碼字碼頁](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)。

> [!NOTE]
> 您不再建議使用 **utf-7** *。 在 PowerShell 7.1 中，如果您 `utf7` 針對 **編碼** 參數指定，就會寫入警告。

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### -Header

指定匯入檔案的替代欄標題列。 欄標題會決定所建立物件的屬性名稱 `Import-Csv` 。

以逗號分隔的清單形式輸入資料行標頭。 不要使用引號括住標題字串。 以單引號括住每個資料行標頭。

如果您輸入較少資料行的資料行標頭，則會捨棄其餘的資料行。 如果您輸入的資料行標題超過資料行的資料行，則會使用空的資料行來建立額外的資料行標題。

使用 **Header** 參數時，會從 CSV 檔案中刪除原始的標題列。 否則，會 `Import-Csv` 從標頭資料列中的專案建立額外的物件。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LiteralPath

指定要匯入的 CSV 檔案路徑。 與 **Path** 不同， **LiteralPath** 參數值將完全依照其輸入值來使用。 沒有字元會被視為萬用字元。 如果路徑包含逸出字元，請將它括在單引號中。 單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。

```yaml
Type: System.String[]
Parameter Sets: DelimiterLiteralPath, CultureLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

指定要匯入的 CSV 檔案路徑。
您也可以使用管線將路徑傳送至 `Import-Csv` 。

```yaml
Type: System.String[]
Parameter Sets: DelimiterPath, CulturePath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -UseCulture

使用目前文化特性的清單分隔字元做為專案分隔符號。 若要尋找文化特性的清單分隔符號，請使用下列命令： `(Get-Culture).TextInfo.ListSeparator` 。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CulturePath, CultureLiteralPath
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

### System.String

您可以使用管線將包含路徑的字串傳送至 `Import-Csv` 。

## 輸出

### Object

此 Cmdlet 會傳回 CSV 檔案中內容所描述的物件。

## 注意

由於匯入的物件為 CSV 版本的物件類型，因此無法辨識這些物件，並以格式化物件類型非 CSV 版本的 PowerShell 類型格式化專案來格式化。

命令的結果 `Import-Csv` 是形成類似表格的自訂物件的字串集合。 每個資料列都是不同的字串，因此您可以使用物件的 **count** 屬性來計算資料表資料列的計數。 欄是物件的屬性，而列中的項目是屬性值。

欄標題列會決定欄數和欄名稱。 欄名稱也是物件的屬性名稱。 除非您使用 Header 參數來指定欄標題，否則第一個資料列會被轉譯為 **資料** 行標頭。 如果有任何列包含的值比標題列還多，即會忽略額外的值。

如果資料行標頭資料列遺漏值，或包含 null 或空白值， `Import-Csv` 則會使用 **H** ，後面接著一個數位來表示遺漏的資料行標頭和屬性名稱。

在 CSV 檔案中，每個物件都會利用以逗號分隔的物件屬性值清單來表示。 屬性值會使用物件的 **ToString ( # B1** 方法轉換成字串，因此它們會以屬性值的名稱表示。 `Export-Csv` 不會匯出物件的方法。

`Import-Csv` 也支援 W3C 擴充記錄檔格式。 從開始的行會被 `#` 視為批註，除非批註開頭為 `#Fields:` 且包含分隔的資料行名稱清單，否則會予以忽略。 在此情況下，Cmdlet 會使用這些資料行名稱。 這是 Windows IIS 和其他 web 伺服器記錄的標準格式。 如需詳細資訊，請參閱 [擴充記錄檔格式](https://www.w3.org/TR/WD-logfile.html)。

## 相關連結

[ConvertFrom-Csv](ConvertFrom-Csv.md)

[ConvertTo-Csv](ConvertTo-Csv.md)

[Export-Csv](Export-Csv.md)

[Get-Culture](Get-Culture.md)

