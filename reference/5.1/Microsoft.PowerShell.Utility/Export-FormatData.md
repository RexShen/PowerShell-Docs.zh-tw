---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-formatdata?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-FormatData
ms.openlocfilehash: 9f88dc77288a0fd24efdbb486e54bc60c2658c14
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203304"
---
# Export-FormatData

## 概要
在格式化檔案中儲存來自目前工作階段的格式化資料。

## SYNTAX

### ByPath (預設值)

```
Export-FormatData -InputObject <ExtendedTypeDefinition[]> -Path <String> [-Force] [-NoClobber]
 [-IncludeScriptBlock] [<CommonParameters>]
```

### ByLiteralPath

```
Export-FormatData -InputObject <ExtendedTypeDefinition[]> -LiteralPath <String> [-Force] [-NoClobber]
 [-IncludeScriptBlock] [<CommonParameters>]
```

## DESCRIPTION

此 `Export-FormatData` Cmdlet 會從目前會話中的格式化物件，建立 Windows PowerShell 格式設定檔案 ( # B0 xml) 。 它會採用傳回的 **ExtendedTypeDefinition** 物件， `Get-FormatData` 並將它們儲存在 XML 格式的檔案中。

Windows PowerShell 會使用格式化檔案 (format.ps1xml) 中的資料在工作階段中產生 Microsoft .NET Framework 物件的預設顯示。 您可以檢視及編輯格式化檔案，然後使用 Update-FormatData Cmdlet 將格式化資料新增至工作階段。

如需 Windows PowerShell 中格式化檔案的詳細資訊，請參閱 [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)。

## 範例

### 範例1：匯出會話格式資料

```powershell
Get-FormatData -TypeName "*" | Export-FormatData -Path "allformat.ps1xml" -IncludeScriptBlock
```

此命令會將工作階段中的所有格式資料匯出到 AllFormat.ps1xml 檔案。

此命令會使用 `Get-FormatData` Cmdlet 來取得會話中的格式資料。 `*` **TypeName** 參數的所有) 值 (會指示 Cmdlet 取得會話中的所有資料。

此命令會使用管線運算子 (`|`) 將格式資料從 `Get-FormatData` 命令傳送至 `Export-FormatData` Cmdlet，以將格式資料匯出至 AllFormat.ps1 的檔案。

此 `Export-FormatData` 命令會使用 **IncludeScriptBlock** 參數，將腳本區塊包含在檔案中的格式資料。

### 範例2：匯出類型的格式資料

```powershell
$F = Get-FormatData -TypeName "helpinfoshort"
Export-FormatData -InputObject $F -Path "c:\test\help.format.ps1xml" -IncludeScriptBlock
```

這些命令會將 **HelpInfoShort** 類型的格式資料匯出到 Help.format.ps1的 xml 檔。

第一個命令會使用 `Get-FormatData` Cmdlet 來取得 **HelpInfoShort** 類型的格式資料，並將它儲存在 `$F` 變數中。

第二個命令會使用 Cmdlet 的 **InputObject** 參數 `Export-FormatData` 來輸入變數中儲存的格式資料 `$F` 。 它也會使用 **IncludeScriptBlock** 參數將腳本區塊包含在輸出中。

### 範例3：不使用腳本區塊匯出格式資料

```powershell
Get-FormatData -TypeName "System.Diagnostics.Process" | Export-FormatData -Path process.format.ps1xml
Update-FormatData -PrependPath ".\process.format.ps1xml"
Get-Process p*
```

```Output
Handles  NPM(K)  PM(K)  WS(K) VM(M)   CPU(s)    Id ProcessName
-------  ------  -----  ----- -----   ------    -- -----------
323                                       5600 powershell
336                                       3900 powershell_ise
138                                       4076 PresentationFontCache
```

此範例顯示從命令省略 **IncludeScriptBlock** 參數的效果 `Export-FormatData` 。

第一個命令會使用 `Get-FormatData` Cmdlet 來取得 Get-Process Cmdlet **所傳回** 之 system.string 物件的格式資料。 此命令會使用管線運算子 (`|`) 將格式化資料傳送至 `Export-FormatData` Cmdlet，此 Cmdlet 會將資料匯出至目前目錄中 Process.format.ps1的 xml 檔。

在此情況下，此 `Export-FormatData` 命令不會使用 **IncludeScriptBlock** 參數。

第二個命令會使用 `Update-FormatData` Cmdlet 將 Process.format.ps1xml 檔案新增至目前的會話。 此命令會使用 **PrependPath** 參數，以確保在處理常式物件的標準格式化資料之前，可以找到 Process.format.ps1xml 檔案中處理常式物件的格式化資料。

第三個命令會顯示此變更的效果。 此命令會使用 `Get-Process` Cmdlet 來取得名稱以 P 開頭的處理常式。輸出顯示顯示中遺失使用腳本區塊計算的屬性值。

## PARAMETERS

### -Force

強制執行命令而不要求使用者確認。

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

### -IncludeScriptBlock

指出是否匯出格式資料中的腳本區塊。

因為指令碼區塊包含程式碼，可能被用於惡意用途，所以預設不會將它們匯出。

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

指定要匯出的格式資料物件。 輸入包含物件的變數，或輸入可取得物件的命令，例如 `Get-FormatData` 命令。 您也可以透過管線將物件傳送 `Get-FormatData` 至 `Export-FormatData` 。

```yaml
Type: System.Management.Automation.ExtendedTypeDefinition[]
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

指定輸出檔案的位置。 與 **Path** 參數不同， **LiteralPath** 的值將完全依照其輸入值來使用。 沒有字元會被視為萬用字元。 如果路徑包含逸出字元，請將它括在單引號中。 單引號告知 Windows PowerShell 不要將任何字元視為逸出序列。

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

指出此 Cmdlet 不會覆寫現有的檔案。 依預設， `Export-FormatData` 會覆寫檔案而不發出警告，除非檔案具有唯讀屬性。

若要指示 `Export-FormatData` 覆寫唯讀檔案，請使用 **Force** 參數。

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

### -Path

指定輸出檔案的位置。
輸入路徑 (選擇性) 與副檔名為 format.ps1xml 的檔案名稱。
如果您省略路徑，會 `Export-FormatData` 在目前的目錄中建立檔案。

如果您使用 .ps1xml 以外的副檔名，此 `Update-FormatData` Cmdlet 將無法辨識該檔案。

如果您指定現有的檔案，則 `Export-FormatData` 會覆寫檔案而不發出警告，除非檔案具有唯讀屬性。 若要覆寫唯讀檔案，請使用 **Force** 參數。 若要防止覆寫檔案，請使用 **NoClobber** 參數。

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases: FilePath

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.Management.Automation.ExtendedTypeDefinition

您可以透過管線將 **ExtendedTypeDefinition** 物件傳送 `Get-FormatData` 至 `Export-FormatData` 。

## 輸出

### 無

`Export-FormatData` 不會傳回任何物件。
它會產生一個檔案，並將檔案儲存在指定路徑。

## 注意

- 若要使用任何格式化檔案 (包括匯出的格式化檔案)，工作階段的執行原則必須允許執行指令碼和設定檔。 如需詳細資訊，請參閱 [about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)。

## 相關連結

[Get-FormatData](Get-FormatData.md)

[Update-FormatData](Update-FormatData.md)
