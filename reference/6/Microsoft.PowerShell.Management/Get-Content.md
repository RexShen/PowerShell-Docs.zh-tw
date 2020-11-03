---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-content?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Content
ms.openlocfilehash: 951edd4219b3d35530b691be9faa8595da297b5c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204456"
---
# Get-Content

## 概要
在指定的位置取得項目的內容。

## SYNTAX

### 路徑 (預設值)

```
Get-Content [-ReadCount <Int64>] [-TotalCount <Int64>] [-Tail <Int32>] [-Path] <String[]>
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force] [-Credential <PSCredential>]
 [-Delimiter <String>] [-Wait] [-Raw] [-Encoding <Encoding>] [-AsByteStream] [-Stream <String>]
 [<CommonParameters>]
```

### LiteralPath

```
Get-Content [-ReadCount <Int64>] [-TotalCount <Int64>] [-Tail <Int32>] -LiteralPath <String[]>
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force] [-Credential <PSCredential>]
 [-Delimiter <String>] [-Wait] [-Raw] [-Encoding <Encoding>] [-AsByteStream] [-Stream <String>]
 [<CommonParameters>]
```

## DESCRIPTION

`Get-Content`Cmdlet 會在路徑指定的位置取得專案的內容，例如檔案中的文字或函式的內容。 針對檔案，會一次讀取一行內容，並傳回物件的集合，每個物件都代表一個內容行。

從 PowerShell 3.0 開始， `Get-Content` 也可以從專案的開頭或結尾取得指定的行數。

## 範例

### 範例 1︰取得文字檔的內容

這個範例會取得目前目錄中檔案的內容。 檔案 `LineNumbers.txt` 包含100行（格式為）， **這是第 X 行** ，在數個範例中使用。

```powershell
1..100 | ForEach-Object { Add-Content -Path .\LineNumbers.txt -Value "This is line $_." }
Get-Content -Path .\LineNumbers.txt
```

```Output
This is Line 1
This is Line 2
...
This is line 99.
This is line 100.
```

陣列值1-100 會將管線向下傳送至 `ForEach-Object` Cmdlet。 `ForEach-Object` 使用腳本區塊與 `Add-Content` Cmdlet 來建立檔案 `LineNumbers.txt` 。 變數 `$_` 代表陣列值，因為每個物件都會向下傳送管線。 此 `Get-Content` Cmdlet 會使用 **Path** 參數來指定檔案 `LineNumbers.txt` ，並在 PowerShell 主控台中顯示內容。

### 範例2：限制傳回的行數 Get-Content

此命令會取得檔案的前五行。 **TotalCount** 參數是用來取得前五行的內容。 此範例會使用 `LineNumbers.txt` 範例1中所建立的檔案。

```powershell
Get-Content -Path .\LineNumbers.txt -TotalCount 5
```

```Output
This is Line 1
This is Line 2
This is Line 3
This is Line 4
This is Line 5
```

### 範例3：從文字檔取得特定的內容行

此命令會從檔案取得特定數目的行，然後只顯示該內容的最後一行。 **TotalCount** 參數會取得前25行的內容。 此範例會使用 `LineNumbers.txt` 範例1中所建立的檔案。

```powershell
(Get-Content -Path .\LineNumbers.txt -TotalCount 25)[-1]
```

```Output
This is Line 25
```

此 `Get-Content` 命令會以括弧括住，讓命令完成後再繼續下一個步驟。 `Get-Content`傳回線條的陣列，這可讓您在括弧之後加入索引標記法，以抓取特定行號。 在此情況下， `[-1]` 索引會在傳回的陣列中指定25個抓取行的最後一個索引。

### 範例4：取得文字檔的最後一行

此命令會從檔案取得第一行和最後一行的內容。 此範例會使用 `LineNumbers.txt` 範例1中所建立的檔案。

```powershell
Get-Item -Path .\LineNumbers.txt | Get-Content -Tail 1
```

```Output
This is Line 100
```

此範例會使用 `Get-Item` Cmdlet 來示範您可以使用管線將檔案傳送至 `Get-Content` 參數。 **Tail** 參數會取得檔案的最後一行。 這個方法比取出所有行並使用 `[-1]` 索引標記法更快。

### 範例5：取得替代資料流程的內容

此範例描述如何使用 **Stream** 參數，取得儲存在 Windows NTFS 磁片區上之檔案的替代資料流程內容。 在此範例中，此 `Set-Content` Cmdlet 是用來在名為的檔案中建立範例內容 `Stream.txt` 。

```powershell
Set-Content -Path .\Stream.txt -Value 'This is the content of the Stream.txt file'
# Specify a wildcard to the Stream parameter to display all streams of the recently created file.
Get-Item -Path .\Stream.txt -Stream *
```

```Output
PSPath        : Microsoft.PowerShell.Core\FileSystem::C:\Test\Stream.txt::$DATA
PSParentPath  : Microsoft.PowerShell.Core\FileSystem::C:\Test
PSChildName   : Stream.txt::$DATA
PSDrive       : C
PSProvider    : Microsoft.PowerShell.Core\FileSystem
PSIsContainer : False
FileName      : C:\Test\Stream.txt
Stream        : :$DATA
Length        : 44
```

```powershell
# Retrieve the content of the primary, or $DATA stream.
Get-Content -Path .\Stream.txt -Stream $DATA
```

```Output
This is the content of the Stream.txt file
```

```powershell
# Use the Stream parameter of Add-Content to create a new Stream containing sample content.
Add-Content -Path .\Stream.txt -Stream NewStream -Value 'Added a stream named NewStream to Stream.txt'
# Use Get-Item to verify the stream was created.
Get-Item -Path .\Stream.txt -Stream *
```

```Output
PSPath        : Microsoft.PowerShell.Core\FileSystem::C:\Test\Stream.txt::$DATA
PSParentPath  : Microsoft.PowerShell.Core\FileSystem::C:\Test
PSChildName   : Stream.txt::$DATA
PSDrive       : C
PSProvider    : Microsoft.PowerShell.Core\FileSystem
PSIsContainer : False
FileName      : C:\Test\Stream.txt
Stream        : :$DATA
Length        : 44

PSPath        : Microsoft.PowerShell.Core\FileSystem::C:\Test\Stream.txt:NewStream
PSParentPath  : Microsoft.PowerShell.Core\FileSystem::C:\Test
PSChildName   : Stream.txt:NewStream
PSDrive       : C
PSProvider    : Microsoft.PowerShell.Core\FileSystem
PSIsContainer : False
FileName      : C:\Test\Stream.txt
Stream        : NewStream
Length        : 46
```

```powershell
# Retrieve the content of your newly created Stream.
Get-Content -Path .\Stream.txt -Stream NewStream
```

```Output
Added a stream named NewStream to Stream.txt
```

**Stream** 參數是 [FileSystem 提供者](../microsoft.powershell.core/about/about_filesystem_provider.md#stream-systemstring)的動態參數。
依預設 `Get-Content` ，只會從主要或資料流程抓取資料 `$DATA` 。 **資料流程** 可以用來儲存隱藏的資料，例如屬性、安全性設定或其他資料。

### 範例6：取得原始內容

此範例中的命令會將檔案的內容以一個字串的形式取得，而不是以字串陣列的形式取得。 依預設，如果沒有 **Raw** 動態參數，則會以以分行符號分隔的字串陣列形式傳回內容。 此範例會使用 `LineNumbers.txt` 範例中所建立的檔案
1.

```powershell
$raw = Get-Content -Path .\LineNumbers.txt -Raw
$lines = Get-Content -Path .\LineNumbers.txt
Write-Host "Raw contains $($raw.Count) lines."
Write-Host "Lines contains $($lines.Count) lines."
```

```Output
Raw contains 1 lines.
Lines contains 100 lines.
```

### 範例7：搭配 Get-Content 使用篩選

您可以為 Cmdlet 指定篩選 `Get-Content` 。 使用篩選準則來限定 **路徑** 參數時，您必須包含尾端星號 (`*`) 來指出路徑的內容。

下列命令會取得目錄中所有檔案的內容 `*.log` `C:\Temp` 。

```powershell
Get-Content -Path C:\Temp\* -Filter *.log
```

### 範例8：以位元組陣列形式取得檔案內容

這個範例示範如何以單一物件的形式取得檔案的內容 `[byte[]]` 。

```powershell
$byteArray = Get-Content -Path C:\temp\test.txt -AsByteStream -Raw
Get-Member -InputObject $bytearray
```

```Output
   TypeName: System.Byte[]

Name           MemberType            Definition
----           ----------            ----------
Count          AliasProperty         Count = Length
Add            Method                int IList.Add(System.Object value)
```

第一個命令會使用 **AsByteStream** 參數來取得檔案的位元組資料流程。
**Raw** 參數可確保傳回的位元組是 `[System.Byte[]]` 。 如果未經處理 **的參數不** 存在，則傳回值為位元組資料流程，而 PowerShell 會將其視為 `[System.Object[]]` 。

## PARAMETERS

### -Path

指定取得內容之專案的路徑 `Get-Content` 。 允許使用萬用字元。 路徑需為項目的路徑，而非容器的路徑。 例如，您必須指定一或多個檔案的路徑，而非目錄的路徑。

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

### -ReadCount

指定管線一次傳送多少行的內容。 預設值為 1。
值為 0 (零) 會一次傳送所有內容。

這個參數不會變更顯示的內容，但它會影響顯示內容所花費的時間。 隨著 **ReadCount** 的值增加，傳回第一行所花費的時間也會增加，但是作業的總時間減少。 這可能會造成大型專案的可察覺差異。

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 1
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -TotalCount

指定從檔案或其他項目的開頭算起的行數。 預設值為 -1 (所有行)。

您可以使用 **TotalCount** 參數名稱或其別名 **First** 或 **Head** 。

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases: First, Head

Required: False
Position: Named
Default value: -1
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Tail

指定從檔案或其他項目的結尾算起的行數。 您可以使用 **Tail** 參數名稱或其別名 **Last** 。 此參數是在 PowerShell 3.0 中引進。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: Last

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
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

### -Exclude

以字串陣列指定此 Cmdlet 在作業中排除的專案。
此參數的值會限定 **Path** 參數。

輸入路徑元素或模式，例如 `*.txt`。
允許使用萬用字元。

只有當命令包含專案的內容（例如）時，才會使用 **Exclude** 參數， `C:\Windows\*` 其中的萬用字元會指定目錄的內容 `C:\Windows` 。

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

### -Force

**Force** 會覆寫唯讀屬性或建立目錄來完成檔案路徑。 **Force** 參數不會嘗試變更檔案許可權或覆寫安全性限制。

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
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Delimiter

指定在 `Get-Content` 讀取時，用來將檔案分割成物件的分隔符號。 預設值為 `\n` ，行尾字元。 讀取文字檔時，會傳回 `Get-Content` 字串物件的集合，每個物件的結尾都是行尾字元。 當您輸入不存在於檔案中的分隔符號時，會 `Get-Content` 以單一未分隔物件的形式傳回整個檔案。

您可以使用這個參數，藉由指定檔案分隔符號做為分隔符號，將大型檔案分割成較小的檔案。 分隔符號會保留 (不會被捨棄)，並成為每個檔案區段中的最後一個項目。

**分隔符號** 是動態參數， **FileSystem** 提供者會將它新增至 `Get-Content` Cmdlet。 此參數只適用於檔案系統磁碟機。

> [!NOTE]
> 目前，當 **分隔符號** 參數的值為空字串時，不 `Get-Content` 會傳回任何值。 這是已知的問題。 強制 `Get-Content` 將整個檔案以單一未分隔字串的形式傳回。 輸入不存在於檔案中的值。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: End-of-line character
Accept pipeline input: False
Accept wildcard characters: False
```

### -Wait

在所有現有的行都已輸出之後，將檔案保持開啟。 等候時， `Get-Content` 每秒會檢查檔案一次，並輸出新行（如果有的話）。 您可以按下 **CTRL + C** 來中斷 **等候** 。 如果檔案遭到刪除，則等候也會結束，在這種情況下，會報告非終止錯誤。

**Wait** 是動態參數，FileSystem 提供者會將它新增至 `Get-Content` Cmdlet。 此參數只適用於檔案系統磁碟機。 **Wait** 無法結合 **Raw** 。

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

### -Raw

忽略分行符號，並以一個字串傳回換行字元的整個檔案內容。 依預設，檔案中的分行符號會用來做為分隔符號，以將輸入區隔開至字串陣列。 此參數是在 PowerShell 3.0 中引進。

**Raw** 是動態參數， **FileSystem** 提供者會將此參數新增至 `Get-Content` Cmdlet，此參數只適用于檔案系統磁片磁碟機。

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
- `oem`：針對 MS-DOS 和主控台程式使用預設編碼。
- `unicode`：使用位元組由大到小的位元組順序，以 UTF-16 格式編碼。
- `utf7`：以 UTF-7 格式編碼。
- `utf8`：以 UTF-8 格式編碼。
- `utf8BOM`：使用 (BOM) 的位元組順序標記來編碼 UTF-8 格式
- `utf8NoBOM`：以不含位元組順序標記的 UTF-8 格式來編碼 (BOM) 
- `utf32`：以 UTF-32 格式編碼。

Encoding 是動態參數， **FileSystem** 提供者會將它新增至 `Get-Content` Cmdlet。
此參數僅適用于檔案系統磁片磁碟機。

讀取和寫入二進位檔案時，請使用 **AsByteStream** 參數，並針對 **ReadCount** 參數使用0的值。 **ReadCount** 值為0時，會以單一讀取操作讀取整個檔案。 預設的 **ReadCount** 值1會在每個讀取操作中讀取一個位元組，並將每個位元組轉換為不同的物件，當您使用 `Set-Content` Cmdlet 將位元組寫入檔案時，除非您使用 **AsByteStream** 參數，否則會導致錯誤。

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

### -Stream

從檔案取得指定的替代 NTFS 檔案資料流內容。 輸入資料流名稱。
不支援萬用字元。

**Stream** 是動態參數， **FileSystem** 提供者會將它新增至 `Get-Content` Cmdlet。
此參數只適用于 Windows 系統上的檔案系統磁片磁碟機。 此參數是在 Windows PowerShell 3.0 引進。

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

### -AsByteStream

指定應將內容讀取為位元組資料流程。 **AsByteStream** 參數是在 Windows PowerShell 6.0 中引進。

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

### CommonParameters

這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。 如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 輸入

### System.Int64、System.String[]、System.Management.Automation.PSCredential

您可以透過管道將讀取計數、總數、路徑或認證傳送至 `Get-Content` 。

## 輸出

### System.Byte、System.String

`Get-Content` 傳回字串或位元組。 輸出類型取決於您指定做為輸入的內容類型。

## 注意

此 `Get-Content` Cmdlet 是針對與任何提供者公開的資料搭配使用所設計。 若要取得會話中的提供者，請使用 `Get-PSProvider` Cmdlet。 如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

## 相關連結

[about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Add-Content](Add-Content.md)

[Clear-Content](Clear-Content.md)

[ForEach-Object](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Get-PSProvider](Get-PSProvider.md)

[Set-Content](Set-Content.md)
