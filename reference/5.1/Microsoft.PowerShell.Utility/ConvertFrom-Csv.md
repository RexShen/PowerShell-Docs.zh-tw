---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/21/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-csv?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-Csv
ms.openlocfilehash: 483f3767af4df9e5e044ab3b46811f22b63a5723
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203363"
---
# ConvertFrom-Csv

## 概要
將以逗號分隔值 (CSV) 格式的物件屬性轉換為原始物件的 CSV 版本。

## SYNTAX

### Delimiter (預設值)

```
ConvertFrom-Csv [-InputObject] <psobject[]> [[-Delimiter] <char>] [-Header <string[]>]
 [<CommonParameters>]
```

### UseCulture

```
ConvertFrom-Csv [-InputObject] <psobject[]> -UseCulture [-Header <string[]>] [<CommonParameters>]
```

## DESCRIPTION

`ConvertFrom-Csv`Cmdlet 會從 Cmdlet 所產生的 CSV 可變長度的字串建立物件 `ConvertTo-Csv` 。

您可以使用這個 Cmdlet 的參數來指定資料行標頭資料列，以決定所產生物件的屬性名稱、指定專案分隔符號，或指示此 Cmdlet 使用目前文化特性的清單分隔符號做為分隔符號。

建立的物件 `ConvertFrom-Csv` 是原始物件的 CSV 版本。 CSV 物件的屬性值是原始物件屬性值的字串版本。 物件的 CSV 版本不含任何方法。

您也可以使用 `Export-Csv` 和 `Import-Csv` Cmdlet，將物件轉換為檔案中的 CSV 字串 (並返回) 。 這些 Cmdlet 與 `ConvertTo-Csv` 和 `ConvertFrom-Csv` Cmdlet 相同，不同之處在于它們會將 CSV 字串儲存在檔案中。

## 範例

### 範例1：將本機電腦上的處理常式轉換為 CSV 格式

此範例示範如何將本機電腦上的處理常式轉換為 CSV 格式，然後將它們還原為物件形式。

```powershell
$P = Get-Process | ConvertTo-Csv
$P | ConvertFrom-Csv
```

此 `Get-Process` Cmdlet 會將管線向下傳送至 `ConvertTo-Csv` 。 `ConvertTo-Csv`Cmdlet 會將處理常式物件轉換成一系列 CSV 字串。 此 `ConvertFrom-Csv` Cmdlet 會將 csv 字串轉換為原始處理常式物件的 csv 版本。 CSV 字串會儲存在變數中 `$P` 。

### 範例2：將資料物件轉換為 CSV 格式，然後轉換為 CSV 物件格式

此範例示範如何將資料物件轉換為 CSV 格式，然後轉換為 CSV 物件格式。

```powershell
$Date = Get-Date | ConvertTo-Csv -Delimiter ';'
ConvertFrom-Csv -InputObject $Date -Delimiter ';'
```

第一個命令會使用 `Get-Date` 將目前的日期和時間傳送到管線 `ConvertTo-Csv` 。 `ConvertTo-Csv`Cmdlet 會將日期物件轉換成一系列 CSV 字串。
**分隔符號** 參數是用來指定分號分隔符號。 字串會儲存在變數中 `$Date` 。

### 範例3：使用 header 參數變更屬性的名稱

這個範例示範如何使用的 **Header** 參數 `ConvertFrom-Csv` ，變更所產生匯入物件中的屬性名稱。

```powershell
$J = Start-Job -ScriptBlock { Get-Process } | ConvertTo-Csv  -NoTypeInformation
$Header = 'State', 'MoreData', 'StatusMessage', 'Location', 'Command', 'StateInfo', 'Finished', 'InstanceId', 'Id', 'Name', 'ChildJobs', 'BeginTime', 'EndTime', 'JobType', 'Output', 'Error', 'Progress', 'Verbose', 'Debug', 'Warning', 'Information'
# Delete the default header from $J
$J = $J[1..($J.count - 1)]
$J | ConvertFrom-Csv -Header $Header
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

`Start-Job`Cmdlet 會啟動執行的背景工作 `Get-Process` 。 工作物件會向下傳送至管線 `ConvertTo-Csv` ，並轉換成 CSV 字串。 **NoTypeInformation** 參數會從 CSV 輸出移除類型資訊標頭，而且在 PowerShell Core 中是選擇性的。 `$Header`變數包含會取代下列預設值的自訂標頭： **HasMoreData** 、 **JobStateInfo** 、 **PSBeginTime** 、 **PSEndTime** 和 **PSJobTypeName** 。 `$J`變數包含 CSV 字串，用來移除預設標頭。 `ConvertFrom-Csv`Cmdlet 會將 CSV 字串轉換成 **PSCustomObject** ，並使用 **Header** 參數來套用 `$Header` 變數。

### 範例4：轉換服務物件的 CSV 字串

此範例說明如何搭配使用 `ConvertFrom-Csv` Cmdlet 與 **UseCulture** 參數。

```powershell
(Get-Culture).TextInfo.ListSeparator
$Services = (Get-Service | ConvertTo-Csv)
ConvertFrom-Csv -InputObject $Services -UseCulture
```

此 `Get-Culture` Cmdlet 會使用 **TextInfo** 和 **ListSeparator** 的 nested 屬性來取得目前文化特性的預設清單分隔符號。 此 `Get-Service` Cmdlet 會將管線下的服務物件傳送至 `ConvertTo-Csv` 。 會 `ConvertTo-Csv` 將服務物件轉換成一系列的 CSV 字串。 CSV 字串會儲存在變數中 `$Services` 。 此 `ConvertFrom-Csv` Cmdlet 會使用 **InputObject** 參數，並轉換變數中的 CSV 字串 `$Services` 。 **UseCulture** 參數會使用目前文化特性的預設清單分隔符號。

使用 **UseCulture** 參數時，請確定目前文化特性的預設清單分隔字元符合 CSV 字串中使用的分隔符號。 否則，就 `ConvertFrom-Csv` 無法從 CSV 字串產生物件。

## PARAMETERS

### -Delimiter

指定 CSV 字串中用來分隔屬性值的分隔符號。
預設值為逗號 (,)。

輸入字元，例如冒號 (:)。
若要指定分號 (; ) 將它括在單引號中。

如果您在檔案中指定實際字串分隔符號以外的字元，就 `ConvertFrom-Csv` 無法從 csv 字串建立物件，而且會傳回 csv 字串。

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

### -Header

指定匯入字串的替代欄標題列。 欄標題會決定所建立物件的屬性名稱 `ConvertFrom-Csv` 。

以逗號分隔的清單形式輸入資料行標頭。 不要使用引號括住標題字串。 以單引號括住每個資料行標頭。

如果您輸入較少資料行的資料行標頭，則會捨棄其餘的資料行。 如果您輸入的資料行標題超過資料行的資料行，則會使用空的資料行來建立額外的資料行標題。

使用 **Header** 參數時，請省略 CSV 字串中的資料行標頭字串。 否則，此 Cmdlet 會從標頭資料列中的專案建立額外的物件。

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

### -InputObject

指定要轉換為物件的 CSV 字串。 輸入包含 CSV 字串的變數，或輸入可取得 CSV 字串的命令或運算式。 您也可以透過管道將 CSV 字串傳送至 `ConvertFrom-Csv` 。

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
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
Parameter Sets: UseCulture
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

您可以透過管道將 CSV 字串傳送至此 Cmdlet。

## 輸出

### System.Management.Automation.PSObject

此 Cmdlet 會傳回 CSV 字串中屬性所描述的物件。

## 注意

由於匯入的物件為 CSV 版本的物件類型，因此無法辨識這些物件，並以格式化物件類型非 CSV 版本的 PowerShell 類型格式化專案來格式化。

在 CSV 格式中，每個物件都會利用以逗號分隔的物件屬性值清單來表示。 屬性值會轉換成字串 (使用物件) 的 **ToString ( # B2** 方法，因此會以屬性值的名稱表示。 此 Cmdlet 不會匯出物件的方法。

## 相關連結

[ConvertTo-Csv](ConvertTo-Csv.md)

[Export-Csv](Export-Csv.md)

[Import-Csv](Import-Csv.md)
