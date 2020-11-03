---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-filehash?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-FileHash
ms.openlocfilehash: 6b6b0bdfe635ba0d11c4694efa8af6c23d9acdcd
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201684"
---
# Get-FileHash

## 概要
使用指定的雜湊演算法來計算檔案的雜湊值。

## SYNTAX

### 路徑 (預設值)

```
Get-FileHash [-Path] <String[]> [[-Algorithm] <String>] [<CommonParameters>]
```

### LiteralPath

```
Get-FileHash [-LiteralPath] <String[]> [[-Algorithm] <String>] [<CommonParameters>]
```

### StreamParameterSet

```
Get-FileHash [-InputStream] <Stream> [[-Algorithm] <String>] [<CommonParameters>]
```

## DESCRIPTION

此 `Get-FileHash` Cmdlet 會使用指定的雜湊演算法來計算檔案的雜湊值。
雜湊值是對應至檔案內容的唯一值。 雜湊會指派唯一值至檔案內容，而非依檔案名稱、副檔名或其他指定項目來識別檔案的內容。 您可以在不修改檔案內容的情況下變更檔案名稱與副檔名，這樣不會變更雜湊值。 同樣地，檔案的內容可以變更，而不需要變更名稱或副檔名。 不過，即使只變更檔案內容中的一個字元，也會造成檔案的雜湊值變更。

雜湊值的目的是提供以密碼編譯的安全方式來確認檔案內容未經變更。 雖然某些雜湊演算法（包括 MD5 和 SHA1）不再被視為安全的攻擊，但是安全雜湊演算法的目標是要將它轉譯為不可能變更檔案的內容，不論是不小心，或是惡意或未經授權的嘗試，並維持相同的雜湊值。 您也可以使用雜湊值來判斷兩個檔案是否具有完全相同的內容。 若兩個檔案的雜湊值完全相同，則檔案的內容也完全相同。

根據預設，此 `Get-FileHash` Cmdlet 會使用 SHA256 演算法，雖然可以使用目標作業系統所支援的任何雜湊演算法。

## 範例

### 範例1：計算檔案的雜湊值

此範例會使用 `Get-FileHash` Cmdlet 來計算檔案的雜湊值 `/etc/apt/sources.list` 。 使用的雜湊演算法是預設的 **SHA256** 。 輸出會透過管道傳送至 `Format-List` Cmdlet，以將輸出格式化為清單。

```powershell
Get-FileHash /etc/apt/sources.list | Format-List
```

```Output
Algorithm : SHA256
Hash      : 3CBCFDDEC145E3382D592266BE193E5BE53443138EE6AB6CA09FF20DF609E268
Path      : /etc/apt/sources.list
```

### 範例2：計算 ISO 檔案的雜湊值

此範例會使用 `Get-FileHash` Cmdlet 和 **SHA384** 演算法來計算系統管理員已從網際網路下載的 ISO 檔案的雜湊值。 輸出會透過管道傳送至 `Format-List` Cmdlet，以將輸出格式化為清單。

```powershell
Get-FileHash C:\Users\user1\Downloads\Contoso8_1_ENT.iso -Algorithm SHA384 | Format-List
```

```Output
Algorithm : SHA384
Hash      : 20AB1C2EE19FC96A7C66E33917D191A24E3CE9DAC99DB7C786ACCE31E559144FEAFC695C58E508E2EBBC9D3C96F21FA3
Path      : C:\Users\user1\Downloads\Contoso8_1_ENT.iso
```

### 範例3：計算資料流程的雜湊值

在此範例中，我們會使用 **系統 .net** ，從 [Powershell 版本頁面](https://github.com/PowerShell/PowerShell/releases/tag/v6.2.4)下載套件。 [發行] 頁面也會記錄每個封裝檔案的 SHA256 雜湊。 我們可以將已發佈的雜湊值與我們用來計算的雜湊值進行比較 `Get-FileHash` 。

```powershell
$wc = [System.Net.WebClient]::new()
$pkgurl = 'https://github.com/PowerShell/PowerShell/releases/download/v6.2.4/powershell_6.2.4-1.debian.9_amd64.deb'
$publishedHash = '8E28E54D601F0751922DE24632C1E716B4684876255CF82304A9B19E89A9CCAC'
$FileHash = Get-FileHash -InputStream ($wc.OpenRead($pkgurl))
$FileHash.Hash -eq $publishedHash
```

```Output
True
```

### 範例4：計算字串的雜湊

PowerShell 不會提供 Cmdlet 來計算字串的雜湊。 不過，您可以將字串寫入資料流程，並使用的 **InputStream** 參數 `Get-FileHash` 來取得雜湊值。

```powershell
$stringAsStream = [System.IO.MemoryStream]::new()
$writer = [System.IO.StreamWriter]::new($stringAsStream)
$writer.write("Hello world")
$writer.Flush()
$stringAsStream.Position = 0
Get-FileHash -InputStream $stringAsStream | Select-Object Hash
```

```Output
Hash
----
64EC88CA00B268E5BA1A35678A1B5316D212F4F366B2477232534A8AECA37F3C
```

## PARAMETERS

### -演算法

指定密碼編譯雜湊函式，用來計算指定檔案或資料流程內容的雜湊值。 密碼編譯雜湊函式具有屬性，因此找不到具有相同雜湊值的兩個不同檔案。 雜湊函式經常被用於數位簽章與資料完整性用途。 此參數可接受的值為：

- SHA1
- SHA256
- SHA384
- SHA512
- MD5

若未指定值，或省略參數，則預設值是 SHA256。

基於安全性理由，MD5 與 SHA1 (不再被視為安全) 只應該用於簡單的變更驗證，而不應該用於為需要保護以避免受攻擊或遭竄改的檔案產生雜湊值。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: SHA1, SHA256, SHA384, SHA512, MD5

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputStream

指定輸入資料流程。

```yaml
Type: System.IO.Stream
Parameter Sets: StreamParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LiteralPath

指定檔案的路徑。 與 **Path** 參數不同， **LiteralPath** 參數的值將完全依照其輸入值來使用。 沒有字元會被視為萬用字元。 如果路徑包含逸出字元，請將路徑括在單引號中。 單引號指示 PowerShell 不要將字元解釋為 escape 序列。

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

指定一或多個檔案的路徑做為陣列。 允許使用萬用字元。

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.String

您可以使用管線將字串傳送至 `Get-FileHash` Cmdlet，其中包含一個或多個檔案的路徑。

## 輸出

### Get-filehash。

`Get-FileHash` 傳回物件，這個物件表示指定檔案的路徑、計算的雜湊值，以及用來計算雜湊的演算法。

## 注意

## 相關連結

[Format-List](Format-List.md)
