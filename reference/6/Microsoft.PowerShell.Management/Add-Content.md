---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/add-content?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Content
ms.openlocfilehash: 291ec8f3a3958aa726fafb8032b996296272a21e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202571"
---
# Add-Content

## 概要
新增內容至指定的項目，例如將文字新增到檔案。

## SYNTAX

### 路徑 (預設值)

```
Add-Content [-Path] <string[]> [-Value] <Object[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-NoNewline] [-Encoding <Encoding>] [-AsByteStream] [-Stream <string>]
 [<CommonParameters>]
```

### LiteralPath

```
Add-Content [-Value] <Object[]> -LiteralPath <string[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-NoNewline] [-Encoding <Encoding>] [-AsByteStream] [-Stream <string>]
 [<CommonParameters>]
```

## DESCRIPTION

Cmdlet 會將 `Add-Content` 內容附加至指定的專案或檔案。 您可以在命令中輸入內容或透過指定包含內容的物件指定內容。

如果您需要建立下列範例的檔案或目錄，請參閱 [新專案](New-Item.md)。

## 範例

### 範例1：將字串新增至所有文字檔，但有例外狀況

此範例會將值附加至目前的目錄中的文字檔，但會根據檔案的檔案名來排除這些檔案。

```powershell
Add-Content -Path .\*.txt -Exclude help* -Value 'End of file'
```

**Path** 參數 `.txt` 會指定目前目錄中的所有檔案，但 **Exclude** 參數會忽略符合指定模式的檔案名。 **Value** 參數會指定寫入檔案的文字字串。

### 範例2：在指定檔案的結尾加上日期

此範例會將日期附加至目前目錄中的檔案，並在 PowerShell 主控台中顯示日期。

```powershell
Add-Content -Path .\DateTimeFile1.log, .\DateTimeFile2.log -Value (Get-Date) -PassThru
Get-Content -Path .\DateTimeFile1.log
```

```Output
Tuesday, May 14, 2019 8:24:27 AM
Tuesday, May 14, 2019 8:24:27 AM
5/14/2019 8:24:27 AM
```

`Add-Content`Cmdlet 會在目前的目錄中建立兩個新檔案。 **Value** 參數包含 Cmdlet 的輸出 `Get-Date` 。 **PassThru** 參數會將新增的內容輸出到管線。
因為沒有任何其他 Cmdlet 可接收輸出，所以它會顯示在 PowerShell 主控台中。
此 `Get-Content` Cmdlet 會顯示已更新的檔案 `DateTimeFile1.log` 。

### 範例3：將指定檔案的內容加入至另一個檔案

此範例會從檔案取得內容，並將內容儲存在變數中。 變數是用來將內容附加至另一個檔案。

```powershell
$From = Get-Content -Path .\CopyFromFile.txt
Add-Content -Path .\CopyToFile.txt -Value $From
Get-Content -Path .\CopyToFile.txt
```

- `Get-Content`Cmdlet 會取得的內容 `CopyFromFile.txt` ，並將內容儲存在 `$From` 變數中。
- 此 `Add-Content` Cmdlet 會 `CopyToFile.txt` 使用變數的內容來更新檔案 `$From` 。
- `Get-Content`Cmdlet 會顯示 CopyToFile.txt。

### 範例4：使用管線將指定檔案的內容新增至另一個檔案

此範例會從檔案取得內容，並使用管線將它傳送至 `Add-Content` Cmdlet。

```powershell
Get-Content -Path .\CopyFromFile.txt | Add-Content -Path .\CopyToFile.txt
Get-Content -Path .\CopyToFile.txt
```

`Get-Content`Cmdlet 會取得的內容 `CopyFromFile.txt` 。 結果會透過管道傳送至 `Add-Content` Cmdlet，以更新 `CopyToFile.txt` 。
最後一個 `Get-Content` Cmdlet 隨即顯示 `CopyToFile.txt` 。

### 範例5：建立新的檔案並複製內容

這個範例會建立新的檔案，並將現有檔案的內容複寫到新檔案中。

```powershell
Add-Content -Path .\NewFile.txt -Value (Get-Content -Path .\CopyFromFile.txt)
Get-Content -Path .\NewFile.txt
```

- 此 `Add-Content` Cmdlet 會使用 **Path** 和 **Value** 參數在目前的目錄中建立新檔案。
- `Get-Content`Cmdlet 會取得現有檔案的內容，並將 `CopyFromFile.txt` 其傳遞至 **Value** 參數。 Cmdlet 周圍的括弧 `Get-Content` 可確保命令會在 `Add-Content` 命令開始之前完成。
- 此 `Get-Content` Cmdlet 會顯示新檔案的內容 `NewFile.txt` 。

### 範例6：將內容新增至唯讀檔案

此命令會將值新增至檔案，即使 **IsReadOnly** 檔案屬性設定為 True 也是 **如此** 。
範例中包含建立唯讀檔案的步驟。

```powershell
New-Item -Path .\IsReadOnlyTextFile.txt -ItemType File
Set-ItemProperty -Path .\IsReadOnlyTextFile.txt -Name IsReadOnly -Value $True
Get-ChildItem -Path .\IsReadOnlyTextFile.txt
Add-Content -Path .\IsReadOnlyTextFile.txt -Value 'Add value to read-only text file' -Force
Get-Content -Path .\IsReadOnlyTextFile.txt
```

```Output
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-ar--         1/28/2019     13:35              0 IsReadOnlyTextFile.txt
```

- 此 `New-Item` Cmdlet 會使用 **Path** 和 **ItemType** 參數， `IsReadOnlyTextFile.txt` 在目前的目錄中建立檔案。
- 此 `Set-ItemProperty` Cmdlet 會使用 **Name** 和 **Value** 參數將檔案的 **IsReadOnly** 屬性變更為 True。
- 此 `Get-ChildItem` Cmdlet 會顯示 (0) 的檔案是空的，且 () 的唯讀屬性 `r` 。
- 此 `Add-Content` Cmdlet 會使用 **Path** 參數來指定檔案。 **Value** 參數包含要附加至檔案的文字字串。 **Force** 參數會將文字寫入至唯讀檔案。
- 此 `Get-Content` Cmdlet 會使用 **Path** 參數來顯示檔案的內容。

若要移除唯讀屬性，請使用命令， `Set-ItemProperty` 並將 **Value** 參數設定為 `False` 。

### 範例7：搭配 Add-Content 使用篩選

您可以為 Cmdlet 指定篩選 `Add-Content` 。 使用篩選準則來限定 **路徑** 參數時，您必須包含尾端星號 (`*`) 來指出路徑的內容。

下列命令會將目錄中所有檔案的內容「完成」一字 `*.txt` `C:\Temp` 。

```powershell
Add-Content -Path C:\Temp\* -Filter *.txt -Value "Done"
```

## PARAMETERS

### -AsByteStream

指定應將內容讀取為位元組資料流程。 此參數是在 PowerShell 6.0 中引進。

當您使用 **AsByteStream** 參數搭配 **編碼** 參數時，就會發生警告。 **AsByteStream** 參數會忽略任何編碼，並以位元組資料流程的形式傳回輸出。

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

### -Credential

> [!NOTE]
> 使用 PowerShell 安裝的任何提供者都不支援此參數。
> 若要模擬其他使用者，或在執行此 Cmdlet 時提高認證，請使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Encoding

指定目標檔案的編碼類型。 預設值是 `utf8NoBOM`。

Encoding 是動態參數，FileSystem 提供者會將它新增至 `Add-Content` Cmdlet。 此參數只適用於檔案系統磁碟機。

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

### -Exclude

以字串陣列指定此 Cmdlet 在作業中排除的專案。 此參數的值會限定 **Path** 參數。 輸入路徑元素或模式，例如 `*.txt`。 允許使用萬用字元。 只有當命令包含專案的內容（例如）時，才會使用 **Exclude** 參數， `C:\Windows\*` 其中的萬用字元會指定目錄的內容 `C:\Windows` 。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Filter

指定要限定 **路徑** 參數的篩選準則。 [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md)提供者是唯一支援使用篩選器的已安裝 PowerShell 提供者。 您可以在 [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)中找到 **檔案系統** 篩選器語言的語法。
篩選比其他參數更有效率，因為提供者會在 Cmdlet 取得物件時套用篩選，而不是在抓取物件之後，讓 PowerShell 篩選物件。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Force

覆寫唯讀屬性，可讓您新增內容至唯讀檔案。 例如， **Force** 會覆寫唯讀屬性或建立目錄來完成檔案路徑，但不會嘗試變更檔案權限。

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

### -Include

以字串陣列指定此 Cmdlet 在作業中納入的項目。 此參數的值會限定 **Path** 參數。 輸入路徑元素或模式，例如 `"*.txt"`。 允許使用萬用字元。 **Include** 參數只有當命令包含專案內容時才有效，例如 `C:\Windows\*` ，其中的萬用字元會指定目錄的內容 `C:\Windows` 。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -LiteralPath

指定一個或多個位置的路徑。 **LiteralPath** 的值將完全依照其輸入值來使用。 沒有字元會被視為萬用字元。 如果路徑包含逸出字元，請將它括在單引號中。 單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。

如需詳細資訊，請參閱 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)。

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -NoNewline

指出此 Cmdlet 不會將新的一行或換行內容新增至內容。

輸入物件的字串表示會串連以形成輸出。 輸出字串之間不會插入空格或分行符號。 最後一個輸出字串之後不會加入任何新行。

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

### -PassThru

傳回代表新增內容的物件。 根據預設，此 Cmdlet 不會產生任何輸出。

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

### -Path

指定要接收其他內容的項目路徑。
允許使用萬用字元。
路徑需為項目的路徑，而非容器的路徑。
例如，您必須指定一或多個檔案的路徑，而非目錄的路徑。
如果您指定多個路徑，請使用逗號來分隔路徑。

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Stream

指定內容的替代資料流程。 如果資料流程不存在，此 Cmdlet 會建立該資料流程。 不支援萬用字元。

**Stream** 是動態參數，FileSystem 提供者會將其加入至 `Add-Content` 。 此參數只適用於檔案系統磁碟機。

您可以使用 `Add-Content` Cmdlet 來變更區域的內容 **。識別碼** 替代資料流程。 不過，我們不建議您這樣做，以排除封鎖從網際網路下載之檔案的安全性檢查。 如果您確認下載的檔案是安全的，請使用 `Unblock-File` Cmdlet。

此參數是在 PowerShell 3.0 中引進。

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

### -Value

指定要新增的內容。 輸入加上引號的字串，例如 **此資料僅供內部使用** ，或指定包含內容的物件，例如產生的 **DateTime** 物件 `Get-Date` 。

您無法藉由輸入檔案的路徑來指定檔案的內容，因為路徑只是一個字串。
您可以使用 `Get-Content` 命令取得內容，並將其傳遞至 **Value** 參數。

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
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

這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。 如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 輸入

### System.string、System.object、system.string

您可以透過管道將值、路徑或認證傳送至 `Set-Content` 。

## 輸出

### 無或 System.String

當您使用 **PassThru** 參數時，會 `Add-Content` 產生代表內容的 **system.string** 物件。 否則，此 Cmdlet 不會產生任何輸出。

## 注意

- 當您使用管線將物件傳送至時 `Add-Content` ，會先將物件轉換成字串，然後再將它加入至專案。 物件類型決定字串格式，但是格式可能會不同於物件的預設顯示。 若要控制字串格式，請使用傳送 Cmdlet 的格式化參數。
- 您也可以 `Add-Content` 使用內建的別名來參考 `ac` 。 如需詳細資訊，請參閱 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。
- 此 `Add-Content` Cmdlet 是針對與任何提供者公開的資料搭配使用所設計。 若要列出工作階段中可用的提供者，請輸入 `Get-PSProvider`。 如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

## 相關連結

[about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Clear-Content](Clear-Content.md)

[Get-Content](Get-Content.md)

[Get-Item](Get-Item.md)

[New-Item](New-Item.md)

[Set-Content](Set-Content.md)
