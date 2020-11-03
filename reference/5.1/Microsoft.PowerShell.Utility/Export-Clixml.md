---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-clixml?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Clixml
ms.openlocfilehash: 8485591165cce0425c85d52fbd31d40614af6249
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203319"
---
# Export-Clixml

## 概要
建立一或多個物件的 XML 表示法，並將它儲存在檔案中。

## SYNTAX

### ByPath (預設值)

```
Export-Clixml [-Path] <String> -InputObject <PSObject> [-Depth <Int32>] [-Force] [-NoClobber]
 [-Encoding <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByLiteralPath

```
Export-Clixml -LiteralPath <String> -InputObject <PSObject> [-Depth <Int32>] [-Force] [-NoClobber]
 [-Encoding <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Export-Clixml`Cmdlet 會建立通用語言基礎結構 (CLI) 物件或物件的 XML 標記法，並將它儲存在檔案中。 然後，您可以使用 `Import-Clixml` Cmdlet，根據該檔案的內容重新建立已儲存的物件。
如需 CLI 的詳細資訊，請參閱 [語言獨立性](/dotnet/standard/language-independence)。

這個 Cmdlet 類似于 `ConvertTo-Xml` ，但會將 `Export-Clixml` 產生的 XML 儲存在檔案中。 `ConvertTo-XML` 傳回 XML，讓您可以在 PowerShell 中繼續處理。

`Export-Clixml`在 Windows 電腦上有一個很重要的用途，就是以 XML 形式安全地匯出認證和安全字串。 如需範例，請參閱範例3。

## 範例

### 範例1：將字串匯出至 XML 檔案

這個範例會建立 XML 檔案，該檔案會儲存在目前的目錄中， **此為測試** 的字串表示。

```powershell
"This is a test" | Export-Clixml -Path .\sample.xml
```

**此為測試** 的字串會沿著管線向下傳送。 `Export-Clixml` 使用 **Path** 參數來建立 `sample.xml` 在目前的目錄中名為的 XML 檔。

### 範例2：將物件匯出至 XML 檔案

此範例會示範如何將物件匯出至 XML 檔案，然後從檔案匯入 XML 來建立物件。

```powershell
Get-Acl C:\test.txt | Export-Clixml -Path .\FileACL.xml
$fileacl = Import-Clixml -Path .\FileACL.xml
```

`Get-Acl`Cmdlet 會取得檔案的安全描述項 `Test.txt` 。 它會將物件沿著管線向下傳送，以將安全描述項傳遞給 `Export-Clixml` 。 以 XML 為基礎的物件表示會儲存在名為的檔案中 `FileACL.xml` 。

`Import-Clixml`Cmdlet 會從檔案中的 XML 建立物件 `FileACL.xml` 。 然後，它會將物件儲存在 `$fileacl` 變數中。

### 範例3：加密匯出的認證物件

在此範例中，藉由執行 Cmdlet 來儲存在變數中的認證 `$Credential` `Get-Credential` ，您可以執行 `Export-Clixml` Cmdlet 以將認證儲存至磁片。

> [!IMPORTANT]
> `Export-Clixml` 只會在 Windows 上匯出加密的認證。 在非 Windows 作業系統（例如 macOS 和 Linux）上，認證會以純文字格式匯出。

```powershell
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential | Export-Clixml $Credxmlpath
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential = Import-Clixml $Credxmlpath
```

此 `Export-Clixml` Cmdlet 會使用 Windows [資料保護 API](/previous-versions/windows/apps/hh464970(v=win.10))來加密認證物件。
加密可確保只有電腦上的使用者帳戶可以解密 credential 物件的內容。 匯出的檔案 `CLIXML` 不能用於不同的電腦或不同的使用者。

在此範例中，用來儲存認證的檔案會以表示 `TestScript.ps1.credential` 。 將 **>testscript** 取代為您要用來載入認證的腳本名稱。

您會將管線下的認證物件傳送至 `Export-Clixml` ，並將它儲存到 `$Credxmlpath` 您在第一個命令中指定的路徑。

若要將認證自動匯入至您的指令碼，請執行最後兩個命令。 執行 `Import-Clixml` 以將安全的認證物件匯入您的腳本中。 這項匯入消除了在腳本中公開純文字密碼的風險。

## PARAMETERS

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

### -Depth

指定 XML 表示法中包含多少層的內含物件。 預設值是 `2`。

您可以在檔案中覆寫物件類型的預設值 `Types.ps1xml` 。 如需詳細資訊，請參閱 [about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 2
Accept pipeline input: False
Accept wildcard characters: False
```

### -Encoding

指定目標檔案的編碼類型。 預設值為 **Unicode** 。

此參數可接受的值如下：

- `ASCII` 使用 ASCII (7 位) 字元集。
- `BigEndianUnicode` 以位元組由大到小的順序使用 UTF-16。
- `Default` 使用與系統的作用中字碼頁對應的編碼， (通常是 ANSI) 。
- `OEM` 使用對應至系統目前 OEM 字碼頁的編碼方式。
- `Unicode` 使用 UTF-16 和位元組由小到小的位元組順序。
- `UTF7` 使用 UTF-7。
- `UTF8` 使用 UTF-8。
- `UTF32` 以位元組由小到大的位元組順序使用 UTF-32。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, Default, OEM, Unicode, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: Unicode
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

強制執行命令而不要求使用者確認。

會導致 Cmdlet 清除輸出檔案的唯讀屬性 (如有必要)。 當命令完成時，Cmdlet 將會嘗試重設唯讀屬性。

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

### -InputObject

指定要轉換的物件。 輸入包含物件的變數，或輸入可取得物件的命令或運算式。 您也可以透過管線將物件傳送至 `Export-Clixml` 。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

指定將儲存物件之 XML 表示法的檔案的路徑。 與 **Path** 不同， **LiteralPath** 參數的值會完全依照其輸入值來使用。 沒有字元會被視為萬用字元。 如果路徑包含逸出字元，請將它括在單引號中。 單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoClobber

指出此 Cmdlet 不會覆寫現有檔案的內容。 根據預設，如果檔案存在指定的路徑中， `Export-Clixml` 會覆寫檔案而不發出警告。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

指定將儲存物件之 XML 表示法的檔案的路徑。

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

顯示執行 Cmdlet 後會發生的情況。 不會執行此 Cmdlet。

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

您可以將任何物件管線至 `Export-Clixml` 。

## 輸出

### System.IO.FileInfo

`Export-Clixml` 建立包含 XML 的檔案。

## 注意

## 相關連結

[ConvertTo-Html](ConvertTo-Html.md)

[ConvertTo-Xml](ConvertTo-Xml.md)

[Export-Csv](Export-Csv.md)

[Import-Clixml](Import-Clixml.md)

[Join-Path](../Microsoft.PowerShell.Management/Join-Path.md)

[將認證安全地儲存在磁碟上](https://powershellcookbook.com/recipe/PukO/securely-store-credentials-on-disk)

[使用 PowerShell 將認證傳遞給舊版系統](https://devblogs.microsoft.com/scripting/use-powershell-to-pass-credentials-to-legacy-systems/)

[Windows.Security.Cryptography.DataProtection](/uwp/api/windows.security.cryptography.dataprotection)
