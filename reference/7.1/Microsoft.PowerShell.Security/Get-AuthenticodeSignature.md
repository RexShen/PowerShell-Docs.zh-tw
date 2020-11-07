---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 04/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-authenticodesignature?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-AuthenticodeSignature
ms.openlocfilehash: 44608ba9fa2324f9d6d381801876c831ed8b3db8
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2020
ms.locfileid: "94347290"
---
# Get-AuthenticodeSignature

## 概要
取得檔案的 Authenticode 簽章的相關資訊。

## SYNTAX

### ByPath (預設值)

```
Get-AuthenticodeSignature [-FilePath] <String[]> [<CommonParameters>]
```

### ByLiteralPath

```
Get-AuthenticodeSignature -LiteralPath <String[]> [<CommonParameters>]
```

### ByContent

```
Get-AuthenticodeSignature -SourcePathOrExtension <String[]> -Content <Byte[]> [<CommonParameters>]
```

## DESCRIPTION

`Get-AuthenticodeSignature`Cmdlet 會取得檔案或檔案內容的 Authenticode 簽章相關資訊做為位元組陣列。 如果檔案未簽署，會抓取資訊但欄位是空白的。

## 範例

### 範例1：取得檔案的 Authenticode 簽章

```powershell
Get-AuthenticodeSignature -FilePath "C:\Test\NewScript.ps1"
```

此命令會取得 NewScript.ps1 檔案中 Authenticode 簽章的相關詳細資訊。 它會使用 **FilePath** 參數來指定檔案。

### 範例2：取得多個檔案的 Authenticode 簽章

```powershell
Get-AuthenticodeSignature test.ps1, test1.ps1, sign-file.ps1, makexml.ps1
```

此命令會取得命令列中列出之四個檔案的 Authenticode 簽章的相關資訊。 在此範例中，會省略 **FilePath** 參數的名稱（這是選擇性的）。

### 範例3：只針對多個檔案取得有效的 Authenticode 簽章

```powershell
Get-ChildItem $PSHOME\*.* | ForEach-object {Get-AuthenticodeSignature $_} | Where-Object {$_.status -eq "Valid"}
```

此命令 `$PSHOME` 會列出目錄中具有有效 Authenticode 簽章的所有檔案。 `$PSHOME`自動變數包含 PowerShell 安裝目錄的路徑。

此命令會使用 `Get-ChildItem` Cmdlet 來取得目錄中的檔案 `$PSHOME` 。 它會使用的模式 *。* 若要排除目錄 (，雖然它也會排除檔案名) 中沒有句點的檔案。

此命令會使用管線運算子 (`|`) 將檔案傳送 `$PSHOME` 至 `ForEach-Object` Cmdlet，其中 `Get-AuthenticodeSignature` 會針對每個檔案呼叫。

命令的結果 `Get-AuthenticodeSignature` 會傳送至 `Where-Object` 只選取狀態為有效之簽章物件的命令。

### 範例4：取得指定為位元組陣列的檔案內容的 Authenticode 簽章

```powershell
Get-AuthenticodeSignature -Content (Get-Content foo.ps1 -AsByteStream) -SourcePathorExtension ps1
```

此命令會取得檔案內容之 Authenticode 簽章的相關資訊。 在此範例中，會指定副檔名以及檔案的內容。

## PARAMETERS

### -Content

檔案的內容，作為要抓取 Authenticode 簽章的位元組陣列。 此參數必須搭配 **SourcePathOrExtension** 參數使用。 檔案內容的格式必須是 Unicode (UTF-16LE) 格式。

```yaml
Type: System.Byte[]
Parameter Sets: ByContent
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -FilePath

指定要檢查之檔案的路徑。 允許使用萬用字元，但它們必須指向單一檔案。 當您指定此參數的值時，不需要在命令列輸入 **FilePath** 。

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -LiteralPath

指定要檢查之檔案的路徑。 **LiteralPath** 參數值與 **FilePath** 不同，會完全依照其輸入值來使用。 沒有字元會被視為萬用字元。 如果路徑包含 escape 字元，請將它括在單引號中。 單引號可告知 PowerShell 不要將任何字元解釋為 escape 字元。

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SourcePathOrExtension

要抓取 Authenticode 簽章之內容的檔案或檔案類型路徑。 此參數會搭配將檔案內容當做位元組陣列傳遞的 **內容** 使用。

```yaml
Type: System.String[]
Parameter Sets: ByContent
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 輸入

### System.String

您可以使用管線將包含檔案路徑的字串傳送至 `Get-AuthenticodeSignature` 。

## 輸出

### System.Management.Automation.Signature

`Get-AuthenticodeSignature` 傳回其取得之每個簽章的簽章物件。

## 注意

此 Cmdlet 僅適用于 Windows 平臺。

如需 PowerShell 中 Authenticode 簽章的相關資訊，請參閱 [about_Signing](../Microsoft.PowerShell.Core/About/about_Signing.md)。

## 相關連結

[Get-executionpolicy](Get-ExecutionPolicy.md)

[Set-AuthenticodeSignature](Set-AuthenticodeSignature.md)

[Set-ExecutionPolicy](Set-ExecutionPolicy.md)

[about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[about_Signing](../Microsoft.PowerShell.Core/About/about_Signing.md)
