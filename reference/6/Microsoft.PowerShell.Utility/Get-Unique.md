---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-unique?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Unique
ms.openlocfilehash: e6831d953008f215bac50fd2b6ec36f88256a2fb
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204580"
---
# Get-Unique

## 概要
從排序的清單中傳回唯一項目。

## SYNTAX

### AsString (預設值)

```
Get-Unique [-InputObject <PSObject>] [-AsString] [<CommonParameters>]
```

### UniqueByType

```
Get-Unique [-InputObject <PSObject>] [-OnType] [<CommonParameters>]
```

## DESCRIPTION

此 `Get-Unique` Cmdlet 會比較已排序清單中的每個專案與下一個專案、消除重複專案，並只傳回每個專案的一個實例。 清單必須排序，此 Cmdlet 才能正常運作。

`Get-Unique` 會區分大小寫。 因此，只有字元大小寫不同的字串會被視為唯一的字串。

## 範例

### 範例 1︰取得文字檔中的唯一文字

這些命令會尋找文字檔案中的唯一文字數目。

```powershell
$A = $( foreach ($line in Get-Content C:\Test1\File1.txt) {
    $line.tolower().split(" ")
  }) | Sort-Object | Get-Unique
$A.count
```

第一個命令會取得 File.txt 檔案的內容。 它會將每一行文字轉換成小寫字母，然後在空格 ("") 將每個字分割到不同行。 然後，它會將產生的清單依字母順序排序 (預設) ，並使用 `Get-Unique` Cmdlet 來排除任何重複的字組。 結果會儲存在變數中 `$A` 。

第二個命令會使用中字串集合的 **Count** 屬性 `$A` 來判斷中有多少個專案 `$A` 。

### 範例 2︰取得陣列中的唯一整數

此命令會尋找整數的集合的唯一成員。

```powershell
1,1,1,1,12,23,4,5,4643,5,3,3,3,3,3,3,3 | Sort-Object | Get-Unique
```

```Output
1
3
4
5
12
23
4643
```

第一個命令會接受在命令列中輸入的整數陣列，使用管線將它們傳送至 `Sort-Object` Cmdlet 進行排序，然後使用管線將它們傳送至 `Get-Unique` ，以消除重複的專案。

### 範例 3︰取得目錄中唯一的物件類型

此命令會使用 `Get-ChildItem` Cmdlet 來抓取本機目錄的內容，其中包括檔案和目錄。

```powershell
Get-ChildItem | Sort-Object {$_.GetType()} | Get-Unique -OnType
```

管線運算子 (|) 將結果傳送至 `Sort-Object` Cmdlet。 `$_.GetType()`語句會將 **GetType** 方法套用到每個檔案或目錄。 然後， `Sort-Object` 依類型排序專案。 另一個管線運算子會將結果傳送至 `Get-Unique` 。 **OnType** 參數會指示 `Get-Unique` 每個類型只傳回一個物件。

### 範例 4︰取得唯一的處理程序

此命令會取得電腦上執行之處理程序的名稱，並排除重複項目。

```powershell
Get-Process | Sort-Object | Select-Object processname | Get-Unique -AsString
```

此 `Get-Process` 命令會取得電腦上的所有處理常式。 管線運算子 (|) 會將結果傳遞給 `Sort-Object` ，根據預設，ProcessName 會依字母順序排序處理常式。 結果會透過管道傳送至 `Select-Object` Cmdlet，此 Cmdlet 只會選取每個物件的 ProcessName 屬性值。 結果接著會以管道傳送至 `Get-Unique` 來消除重複專案。

**AsString** 參數會指示 `Get-Unique` 將 **ProcessName** 值視為字串。
如果沒有這個參數，會 `Get-Unique` 將 **ProcessName** 值視為物件，並且只傳回物件的一個實例，也就是清單中的第一個進程名稱。

## PARAMETERS

### -AsString

指出此 Cmdlet 會使用資料做為字串。 如果沒有這個參數，資料會被視為物件，因此當您將相同類型的物件集合提交到時（ `Get-Unique` 例如檔案集合），它只會傳回一個 (第一個) 。 您可以使用此參數來尋找物件屬性的唯一值，例如檔案名稱。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AsString
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

指定的輸入 `Get-Unique` 。 輸入包含物件的變數，或輸入可取得物件的命令或運算式。

此 Cmdlet 會將使用 **InputObject** 提交的輸入視為集合。 它不會列舉集合中的個別專案。 由於集合為單一項目，因此使用 **InputObject** 提交的輸入一律會依原樣傳回。

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

### -OnType

指出此 Cmdlet 只會針對每個類型傳回一個物件。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UniqueByType
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

### System.Management.Automation.PSObject

您可以透過管道將任何類型的物件傳送至 `Get-Unique` 。

## 輸出

### System.Management.Automation.PSObject

傳回的物件類型 `Get-Unique` 取決於輸入。

## 注意

您也可以 `Get-Unique` 使用內建的別名來參考 `gu` 。 如需詳細資訊，請參閱 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。

如果要排序清單，請使用 Sort-Object。 您也可以使用的 **unique** 參數 `Sort-Object` 來尋找清單中的唯一專案。

## 相關連結

[Select-Object](Select-Object.md)

[Sort-Object](Sort-Object.md)
