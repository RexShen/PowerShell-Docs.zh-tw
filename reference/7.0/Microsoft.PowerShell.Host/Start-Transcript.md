---
external help file: Microsoft.PowerShell.ConsoleHost.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Host
ms.date: 04/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.host/start-transcript?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Transcript
ms.openlocfilehash: 5f964cec2458309eb736bf2d2930fc65a72b0fe4
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201867"
---
# Start-Transcript

## 概要
在文字檔中建立所有或部分 PowerShell 會話的記錄。

## SYNTAX

### ByPath (預設值)

```
Start-Transcript [[-Path] <String>] [-Append] [-Force] [-NoClobber] [-IncludeInvocationHeader]
 [-UseMinimalHeader] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

### ByLiteralPath

```
Start-Transcript [[-LiteralPath] <String>] [-Append] [-Force] [-NoClobber]
 [-IncludeInvocationHeader] [-UseMinimalHeader] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

### ByOutputDirectory

```
Start-Transcript [[-OutputDirectory] <String>] [-Append] [-Force] [-NoClobber]
 [-IncludeInvocationHeader] [-UseMinimalHeader] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

## DESCRIPTION

`Start-Transcript`Cmdlet 會建立所有或部分 PowerShell 會話的記錄至文字檔。 文字記錄包含使用者輸入的所有命令，以及顯示在主控台上的所有輸出。

從 Windows PowerShell 5.0 開始，會 `Start-Transcript` 在為所有文字記錄產生的檔案名中包含主機名稱。 當您的企業記錄會集中管理時，這特別有用。
Cmdlet 所建立的檔案會 `Start-Transcript` 在名稱中包含隨機字元，以防止在同時啟動兩個或多個文字記錄時，可能會覆寫或重複。
這也可以防止未經授權探索儲存於集中式檔案共用中的文字記錄。

## 範例

### 範例 1︰使用預設設定啟動文字記錄檔

```powershell
Start-Transcript
```

此命令會在預設檔案位置中啟動文字記錄。

### 範例 2︰啟動特定位置上的文字記錄檔

```powershell
Start-Transcript -Path "C:\transcripts\transcript0.txt" -NoClobber
```

此命令會在中的檔案中啟動文字記錄 `Transcript0.txt` `C:\transcripts` 。 由於使用了 **NoClobber** 參數，此命令會防止任何現有的檔案遭到覆寫。 如果檔案 `Transcript0.txt` 已存在，則命令會失敗。

## PARAMETERS

### -Append

指出此 Cmdlet 會將新的文字記錄新增到現有檔案的結尾。 使用 **Path** 參數指定檔案。

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

### -Force

可讓 Cmdlet 將文字記錄附加到現有的唯讀檔案。 針對唯讀檔案使用時，此 Cmdlet 會將檔案權限變更為讀寫。 若使用了此參數，此 Cmdlet 便無法覆寫安全性限制。

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

### -IncludeInvocationHeader

指出此 Cmdlet 會在執行命令時記錄時間戳記。

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

### -UseMinimalHeader

在文字記錄前面加上簡短的標頭，而不是預設包含的詳細標頭。 此參數已新增至 PowerShell 6.2。

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

### -LiteralPath

指定文字記錄檔的位置。 與 **Path** 參數不同， **LiteralPath** 參數的值將完全依照其輸入值來使用。 沒有字元會被視為萬用字元。 如果路徑包含逸出字元，請將它括在單引號中。 單引號會通知 PowerShell 不要將任何字元解釋為 escape 序列。

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoClobber

指出此 Cmdlet 將不會覆寫現有的檔案。 根據預設，如果文字記錄檔存在於指定的路徑中， `Start-Transcript` 會覆寫檔案而不發出警告。

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

### -OutputDirectory

指定要用來儲存文字記錄的特定路徑和資料夾。 PowerShell 會自動指派文字記錄名稱。

```yaml
Type: System.String
Parameter Sets: ByOutputDirectory
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

指定文字記錄檔的位置。 輸入檔案的路徑 `.txt` 。 不允許使用萬用字元。

如果您未指定路徑，則會 `Start-Transcript` 使用全域變數值中的路徑 `$Transcript` 。 如果您尚未建立此變數，請將文字記錄 `Start-Transcript` 儲存在檔案中 `$Home\My Documents directory as \PowerShell_transcript.<time-stamp>.txt` 。

如果路徑中不存在任何目錄，命令就會失敗。

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: False
Position: 0
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

顯示執行 Cmdlet 後會發生的情況。
Cmdlet 並不會執行。

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

### 無

您無法使用管線將物件傳送至此 Cmdlet。

## 輸出

### System.String

此 Cmdlet 會傳回包含確認訊息和輸出檔路徑的字串。

## 注意

若要停止文字記錄，請使用 `Stop-Transcript` Cmdlet。

若要記錄整個會話，請將 `Start-Transcript` 命令新增至您的設定檔。 如需詳細資訊，請參閱 [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)。

## 相關連結

[Stop-Transcript](Stop-Transcript.md)
