---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-file?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-File
ms.openlocfilehash: 3a3d431276074d7c2b66b442307071076fdfebd5
ms.sourcegitcommit: d757d64ea8c8af4d92596e8fbe15f2f40d48d3ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "93206304"
---
# Out-File

## 概要
將輸出傳送到檔案。

## SYNTAX

### ByPath (預設值)

```
Out-File [-FilePath] <string> [[-Encoding] <Encoding>] [-Append] [-Force] [-NoClobber]
 [-Width <int>] [-NoNewline] [-InputObject <psobject>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByLiteralPath

```
Out-File [[-Encoding] <Encoding>] -LiteralPath <string> [-Append] [-Force] [-NoClobber]
 [-Width <int>] [-NoNewline] [-InputObject <psobject>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Out-File`Cmdlet 會將輸出傳送至檔案。 它會隱含地使用 PowerShell 的格式化系統寫入檔案。 檔案會接收與終端機相同的顯示表示。 這表示，除非所有輸入物件都是字串，否則輸出可能不適合以程式設計方式處理。
當您需要指定輸出參數時，請使用 `Out-File` 而不是重新導向運算子 (`>`) 。 如需重新導向的詳細資訊，請參閱 [about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)。

## 範例

### 範例1：傳送輸出並建立檔案

此範例示範如何將本機電腦的進程清單傳送至檔案。 如果檔案不存在，則會 `Out-File` 在指定的路徑中建立檔案。

```powershell
Get-Process | Out-File -FilePath .\Process.txt
Get-Content -Path .\Process.txt
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     29    22.39      35.40      10.98   42764   9 Application
     53    99.04     113.96       0.00   32664   0 CcmExec
     27    96.62     112.43     113.00   17720   9 Code
```

此 `Get-Process` Cmdlet 會取得在本機電腦上執行的進程清單。 **處理** 程式物件會向下傳送至 `Out-File` Cmdlet。 `Out-File` 使用 **FilePath** 參數，並在目前目錄中建立名為 **Process.txt** 的檔案。 此 `Get-Content` 命令會從檔案取得內容，並將其顯示在 PowerShell 主控台中。

### 範例2：防止覆寫現有的檔案

此範例會防止覆寫現有的檔案。 根據預設，會 `Out-File` 覆寫現有的檔案。

```powershell
Get-Process | Out-File -FilePath .\Process.txt -NoClobber
```

```Output
Out-File : The file 'C:\Test\Process.txt' already exists.
At line:1 char:15
+ Get-Process | Out-File -FilePath .\Process.txt -NoClobber
+               ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
```

此 `Get-Process` Cmdlet 會取得在本機電腦上執行的進程清單。 **處理** 程式物件會向下傳送至 `Out-File` Cmdlet。 `Out-File` 使用 **FilePath** 參數，並嘗試寫入至目前目錄中名為 **Process.txt** 的檔案。 **NoClobber** 參數會防止檔案遭到覆寫，並顯示該檔案已經存在的訊息。

### 範例3：以 ASCII 格式將輸出傳送至檔案

此範例示範如何使用特定編碼類型來編碼輸出。

```powershell
$Procs = Get-Process
Out-File -FilePath .\Process.txt -InputObject $Procs -Encoding ASCII -Width 50
```

此 `Get-Process` Cmdlet 會取得在本機電腦上執行的進程清單。 **處理** 程式物件會儲存在變數中 `$Procs` 。 `Out-File` 使用 **FilePath** 參數，並在目前目錄中建立名為 **Process.txt** 的檔案。 **InputObject** 參數會將中的處理常式物件傳遞 `$Procs` 至檔案 **Process.txt** 。 **Encoding** 參數會將輸出轉換為 **ASCII** 格式。 **寬度** 參數會將檔案中的每一行限制為50個字元，因此某些資料可能會被截斷。

### 範例4：使用提供者並將輸出傳送至檔案

此範例顯示 `Out-File` 當您不在 **FileSystem** 提供者磁片磁碟機時，如何使用此 Cmdlet。 使用 `Get-PSProvider` Cmdlet 來查看您本機電腦上的提供者。 如需詳細資訊，請參閱 [about_Providers](../Microsoft.Powershell.Core/About/about_Providers.md)。

```
PS> Set-Location -Path Alias:

PS> Get-Location

Path
----
Alias:\

PS> Get-ChildItem | Out-File -FilePath C:\TestDir\AliasNames.txt

PS> Get-Content -Path C:\TestDir\AliasNames.txt

CommandType     Name
-----------     ----
Alias           % -> ForEach-Object
Alias           ? -> Where-Object
Alias           ac -> Add-Content
Alias           cat -> Get-Content
```

`Set-Location`命令使用 **Path** 參數將目前位置設定為登錄提供者 `Alias:` 。 `Get-Location`Cmdlet 會顯示的完整路徑 `Alias:` 。
`Get-ChildItem` 將物件沿著管線向下傳送至 `Out-File` Cmdlet。 `Out-File` 使用 **FilePath** 參數來指定輸出的完整路徑和檔案名， **C:\TestDir\AliasNames.txt** 。 此 `Get-Content` Cmdlet 會使用 **Path** 參數，並在 PowerShell 主控台中顯示檔案的內容。

## PARAMETERS

### -Append

將輸出新增到現有檔案的結尾。

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

### -Encoding

指定目標檔案的編碼類型。 預設值是 `utf8NoBOM`。

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
Position: 1
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

指定輸出檔案的路徑。

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases: Path

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

覆寫唯讀屬性，並覆寫現有的唯讀檔案。 **Force** 參數不會覆寫安全性限制。

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

### -InputObject

指定要寫入檔案的物件。 輸入包含物件的變數，或輸入可取得物件的命令或運算式。

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

### -LiteralPath

指定輸出檔案的路徑。 **LiteralPath** 參數的使用方式與輸入的完全相同。
不接受萬用字元。 如果路徑包含逸出字元，請將它括在單引號中。 單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。 如需詳細資訊，請參閱 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -NoClobber

**NoClobber** 可防止覆寫現有的檔案，並顯示該檔案已經存在的訊息。 根據預設，如果檔案存在指定的路徑中， `Out-File` 會覆寫檔案而不發出警告。

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

### -NoNewline

指定寫入檔案的內容不會以分行符號結尾。 輸入物件的字串表示會串連以形成輸出。 輸出字串之間不會插入空格或分行符號。 最後一個輸出字串之後不會加入任何新行。

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

### -Width

指定每一行輸出的字元數目。 任何額外的字元都會被截斷，而不會換行顯示。 如果未使用此參數，則寬度取決於主控制項的特性。 PowerShell 主控台的預設值為80個字元。

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

顯示執行 Cmdlet 後會發生的情況。 Cmdlet 並不會執行。

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

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.Management.Automation.PSObject

您可以透過管線將任何物件傳送至 `Out-File` 。

## 輸出

### 無

`Out-File` 不會產生任何輸出。

## 注意

輸入物件會自動格式化，因為它們會在終端機中，但是您可以使用 `Format-*` Cmdlet 來明確控制檔案輸出的格式。 例如， `Get-Date | Format-List | Out-File out.txt`

若要將 PowerShell 命令的輸出傳送至 `Out-File` Cmdlet，請使用管線。 或者，您可以將資料儲存在變數中，然後使用 **InputObject** 參數將資料傳遞給 `Out-File` Cmdlet。

`Out-File` 將資料儲存至檔案，但不會對管線產生任何輸出物件。

## 相關連結

[about_Providers](../Microsoft.Powershell.Core/About/about_Providers.md)

[about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[Out-Default](../Microsoft.PowerShell.Core/Out-Default.md)

[Out-Host](../Microsoft.PowerShell.Core/Out-Host.md)

[Out-Null](../Microsoft.PowerShell.Core/Out-Null.md)

[Out-String](Out-String.md)

[Tee-Object](Tee-Object.md)

