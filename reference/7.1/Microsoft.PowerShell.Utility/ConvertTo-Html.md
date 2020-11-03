---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-html?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Html
ms.openlocfilehash: 27a1d2994dee46b9e5bfd54132ff4a665330c2b4
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/10/2020
ms.locfileid: "93205995"
---
# ConvertTo-Html

## 概要
將 .NET 物件轉換成可在網頁瀏覽器中顯示的 HTML。

## SYNTAX

### 頁面 (預設) 

```
ConvertTo-Html [-InputObject <PSObject>] [[-Property] <Object[]>] [[-Body] <String[]>]
 [[-Head] <String[]>] [[-Title] <String>] [-As <String>] [-CssUri <Uri>] [-PostContent <String[]>]
 [-PreContent <String[]>] [-Meta <Hashtable>] [-Charset <String>] [-Transitional]
 [<CommonParameters>]
```

### 片段

```
ConvertTo-Html [-InputObject <PSObject>] [[-Property] <Object[]>] [-As <String>] [-Fragment]
 [-PostContent <String[]>] [-PreContent <String[]>] [<CommonParameters>]
```

## DESCRIPTION

`ConvertTo-Html`Cmdlet 會將 .net 物件轉換成可在網頁瀏覽器中顯示的 HTML。 您可以使用這個 Cmdlet 在網頁中顯示命令的輸出。

您可以使用的參數來 `ConvertTo-Html` 選取物件屬性、指定表格或清單格式、指定 HTML 頁標題、在物件的前後新增文字，以及只傳回表格或清單片段，而不是 STRICT DTD 頁面。

當您將多個物件提交至時 `ConvertTo-Html` ，PowerShell 會根據您所提交之第一個物件的屬性，建立 (或列出) 的資料表。 如果剩餘的物件不具有其中一個指定的屬性，該物件的屬性值將會是空的儲存格。 如果其餘的物件有其他屬性，那些屬性值將不會包含在檔案中。

## 範例

### 範例1：建立網頁以顯示日期

```powershell
ConvertTo-Html -InputObject (Get-Date)
```

此命令建立一個顯示目前日期之屬性的 HTML 網頁。 它會使用 **InputObject** 參數將命令的結果提交 `Get-Date` 至 `ConvertTo-Html` Cmdlet。

### 範例2：建立可顯示 PowerShell 別名的網頁

```powershell
Get-Alias | ConvertTo-Html | Out-File aliases.htm
Invoke-Item aliases.htm
```

此命令會建立 HTML 網頁，以列出目前主控台中的 PowerShell 別名。

此命令會使用 `Get-Alias` Cmdlet 來取得別名。 它使用管線運算子 (`|`) 將別名傳送至 `ConvertTo-Html` Cmdlet，此 Cmdlet 會建立 HTML 網頁。 此命令也會使用 `Out-File` Cmdlet 將 HTML 程式碼傳送至檔案 `aliases.htm` 。

### 範例3：建立可顯示 PowerShell 事件的網頁

```powershell
`Get-EventLog` -LogName "Windows PowerShell" | ConvertTo-Html | Out-File pslog.htm
```

此命令會建立一個名為 `pslog.htm` 的 HTML 網頁，以顯示本機電腦上 Windows PowerShell 事件記錄檔中的事件。

它會使用 `Get-EventLog` Cmdlet 取得 Windows PowerShell 記錄檔中的事件，然後使用管線運算子 () 將 `|` 事件傳送至 `ConvertTo-Html` Cmdlet。 此命令也會使用 `Out-File` Cmdlet 將 HTML 程式碼傳送至檔案 `pslog.htm` 。

此命令也會使用 `Out-File` Cmdlet 將 HTML 程式碼傳送至檔案 `pslog.htm` 。

### 範例4：建立網頁以顯示進程

```powershell
Get-Process |
  ConvertTo-Html -Property Name, Path, Company -Title "Process Information" |
    Out-File proc.htm
Invoke-Item proc.htm
```

這些命令建立並開啟一個 HTML 網頁，當中列出本機電腦上處理程序的名稱、路徑及公司。

第一個命令會使用 `Get-Process` Cmdlet 來取得代表電腦上執行之處理常式的物件。 此命令會使用管線運算子 (`|`) 將處理常式物件傳送至 `ConvertTo-Html` Cmdlet。

此命令會使用 **Property** 參數來選取要包含在資料表中之進程物件的三個屬性。 命令使用 **title** 參數指定 HTML 網頁的標題。 此命令也會使用 `Out-File` Cmdlet 將產生的 HTML 傳送至名為 Proc.htm 的檔案。

第二個命令會使用 `Invoke-Item` Cmdlet `Proc.htm` 在預設瀏覽器中開啟。

### 範例5：建立用來顯示服務物件的網頁

```powershell
Get-Service | ConvertTo-Html -CssUri "test.css"
```

```Output
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"  "https://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html>
<head>
<title>HTML TABLE</title>
<link rel="stylesheet" type="text/css" href="test.css" />
...
```

此命令會建立 Cmdlet 所傳回之服務物件的 HTML 網頁 `Get-Service` 。 此命令會使用 **CssUri** 參數指定 HTML 網頁的級聯樣式表。

**CssUri** 參數會將其他 `<link rel="stylesheet" type="text/css" href="test.css">` 標記新增至產生的 HTML。 標記中的 HREF 屬性包含樣式表的名稱。

### 範例6：建立網頁以顯示服務物件

```powershell
Get-Service | ConvertTo-Html -As LIST | Out-File services.htm
```

此命令會建立 Cmdlet 所傳回之服務物件的 HTML 網頁 `Get-Service` 。 命令使用 **As** 參數指定清單格式。 Cmdlet 會 `Out-File` 將產生的 HTML 傳送至檔案 `Services.htm` 。

### 範例7：建立目前日期的 web 資料表

```powershell
Get-Date | ConvertTo-Html -Fragment
```

```Output
<table>
<colgroup>...</colgroup>
<tr><th>DisplayHint</th><th>DateTime</th><th>Date</th><th>Day</th><th>DayOfWeek</th><th>DayOfYear</th><th>Hour</th>
<th>Kind</th><th>Millisecond</th><th>Minute</th><th>Month</th><th>Second</th><th>Ticks</th><th>TimeOfDay</th><th>Year</th></tr>
<tr><td>DateTime</td><td>Monday, May 05, 2008 10:40:04 AM</td><td>5/5/2008 12:00:00 AM</td><td>5</td><td>Monday</td>
<td>126</td><td>10</td><td>Local</td><td>123</td><td>40</td><td>5</td><td>4</td><td>633455808041237213</td><td>10:40:04.12
37213</td><td>2008</td></tr>
</table>
```

此命令會使用 `ConvertTo-Html` 來產生目前日期的 HTML 表格。 此命令會使用 `Get-Date` Cmdlet 來取得目前的日期。 它使用管線運算子 (|) 將結果傳送至 `ConvertTo-Html` Cmdlet。

此 `ConvertTo-Html` 命令包含 **片段** 參數，此參數會將輸出限制為 HTML 表格。 因此，會省略 HTML 網頁的其他元素，例如 `<HEAD>` 和 `<BODY>` 標記。

### 範例8：建立可顯示 PowerShell 事件的網頁

```powershell
Get-EventLog -Log "Windows PowerShell" | ConvertTo-Html -Property id, level, task
```

此命令會使用 `Get-EventLog` Cmdlet 從 Windows PowerShell 事件記錄檔取得事件。

它使用管線運算子 (`|`) 將事件傳送至 `ConvertTo-Html` Cmdlet，以將事件轉換成 HTML 格式。

此 `ConvertTo-Html` 命令會使用 **Property** 參數，只選取事件 **的 ID** 、 **Level** 及 **Task** 屬性。

### 範例9：建立可顯示指定服務的網頁

```powershell
$htmlParams = @{
  Title = "Windows Services: Server01"
  Body = Get-Date
  PreContent = "<P>Generated by Corporate IT</P>"
  PostContent = "For details, contact Corporate IT."
}
Get-Service A* |
  ConvertTo-Html @htmlParams |
    Out-File Services.htm
Invoke-Item Services.htm
```

此命令會建立並開啟一個網頁，顯示電腦上以開頭的服務。它使用的 **Title** 、 **Body** 、 **PreContent** 和 **PostContent** 參數 `ConvertTo-Html` 來自訂輸出。

命令的第一個部分 `Get-Service` 會使用 Cmdlet 來取得電腦上以開頭的服務。此命令會使用管線運算子 (`|`) 將結果傳送至 `ConvertTo-Html` Cmdlet。 此命令也會使用 `Out-File` Cmdlet 將輸出傳送至 Services.htm 的檔案。

分號 (`;`) 結束第一個命令並啟動第二個命令，此命令會使用 `Invoke-Item` Cmdlet `Services.htm` 在預設瀏覽器中開啟檔案。

### 範例10：設定 HTML 的中繼屬性和字元集

```powershell
Get-Service | ConvertTo-HTML -Meta @{
  refresh=10
  author="Author's Name"
  keywords="PowerShell, HTML, ConvertTo-HTML"
} -Charset "UTF-8"
```

此命令會建立網頁的 HTML，其具有重新整理、撰寫和關鍵字的中繼標記。
頁面的字元集設定為 UTF-8

### 範例11：將 HTML 設定為 XHTML 轉換 DTD

```powershell
Get-Service | ConvertTo-HTML -Transitional
```

此命令會將傳回的 HTML DOCTYPE 設定為 XHTML 轉換 DTD

## PARAMETERS

### -As

決定要將物件的格式設定為表格或清單。 有效的值為 **資料表** 和 **清單** 。 預設值為 **Table** 。

**資料表** 值會產生類似于 PowerShell 資料表格式的 HTML 資料表。 標題列會顯示屬性名稱。 每個表格列皆代表一個物件，並會顯示該物件每個屬性的值。

**List** 值會為每個類似于 PowerShell 清單格式的物件產生兩個數據行的 HTML 資料表。 第一個資料行顯示內容名稱。 第二欄顯示內容值。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Table, List

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Body

指定要在開頭 `<BODY>` 標記之後新增的文字。 該位置預設不會有任何文字。

```yaml
Type: System.String[]
Parameter Sets: Page
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -字元集

指定要加入至開頭標記的文字 `<charset>` 。 該位置預設不會有任何文字。

此參數是在 PowerShell 6.0 中引進。

```yaml
Type: System.String
Parameter Sets: Page
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CssUri

指定套用到 HTML 檔案之階層式樣式表 (CSS) 的統一資源識別項 (URI)。 URI 包含在輸出中的樣式表連結內。

```yaml
Type: System.Uri
Parameter Sets: Page
Aliases: cu, uri

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Fragment

只產生 HTML 表格。 將會省略 HTML、HEAD、TITLE 及 BODY 標記。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Fragment
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Head

指定 `<HEAD>` 標記的內容。 預設為 `<title\>HTML TABLE</title>`。 如果您使用 **Head** 參數，則會忽略 **Title** 參數。

```yaml
Type: System.String[]
Parameter Sets: Page
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

指定要以 HTML 呈現的物件。 輸入包含物件的變數，或輸入可取得物件的命令或運算式。

如果您使用此參數提交多個物件（例如電腦上的所有服務），則 `ConvertTo-Html` 會建立一個資料表，以顯示集合或物件陣列的屬性。 若要建立個別物件的表格，請使用管線運算子將物件輸送至 `ConvertTo-Html` 。

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

### -中繼

指定要加入至開頭標記的文字 `<meta>` 。 該位置預設不會有任何文字。

此參數是在 PowerShell 6.0 中引進。

```yaml
Type: System.Collections.Hashtable
Parameter Sets: Page
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PostContent

指定要在結尾 `</TABLE>` 標記之後新增的文字。 該位置預設不會有任何文字。

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

### -PreContent

指定要在開頭 `<TABLE>` 標記之前新增的文字。 該位置預設不會有任何文字。

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

### -Property

將物件的指定屬性包含在 HTML 中。 **Property** 參數的值可以是新的計算屬性。 計算的屬性可以是腳本區塊或雜湊表。 有效的索引鍵/值組為：

-  (或標籤的名稱) - `<string>` (新增至 PowerShell 6.x) 
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
Accept wildcard characters: False
```

### -Title

指定 HTML 檔案的標題，也就是出現在 `<TITLE>` 標記之間的文字。

```yaml
Type: System.String
Parameter Sets: Page
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -過渡

將 **doctype** 變更為 **xhtml 轉換 Dtd** ，預設 **DOCTYPE** 為 **xhtml Strict dtd** 。

此參數是在 PowerShell 6.0 中引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Page
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

您可以透過管道將任何 .NET 物件傳送至 `ConvertTo-Html` 。

## 輸出

### System.string 或 System.Xml.Xml檔

`ConvertTo-Html` 傳回組成有效 HTML 的一連串字串。

## 注意

若要使用此 Cmdlet，請使用管線將一或多個物件傳送至 Cmdlet，或使用 **InputObject** 參數來指定物件。 當輸入是由多個物件組成時，這兩個方法的輸出會非常不一樣。

- 當您使用管線將多個物件傳送至 Cmdlet 時，PowerShell 會一次將物件傳送至 Cmdlet。 因此， `ConvertTo-Html` 會建立顯示個別物件的資料表。 例如，如果您使用管線將電腦上的處理常式傳送至 `ConvertTo-Html` ，則產生的表格會顯示所有的處理常式。

- 當您使用 **InputObject** 參數提交多個物件時，會 `ConvertTo-Html` 以集合或陣列的形式接收這些物件。 因此，它會建立顯示陣列及其屬性 (而非顯示陣列中的項目) 的表格。 例如，如果您使用 **InputObject** 將電腦上的處理常式提交至 `ConvertTo-Html` ，則產生的資料表會顯示物件陣列和其屬性。

  為了符合 XHTML 嚴格 DTD，會據以修改 DOCTYPE 標記：

   `<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"   "https://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"\>`

## 相關連結

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[ConvertTo-Csv](ConvertTo-Csv.md)

[ConvertTo-Json](ConvertTo-Json.md)

[ConvertTo-Xml](ConvertTo-Xml.md)

[Export-Clixml](Export-Clixml.md)

[Import-Clixml](Import-Clixml.md)
