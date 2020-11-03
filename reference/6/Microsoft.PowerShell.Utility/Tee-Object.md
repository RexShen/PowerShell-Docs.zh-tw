---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/tee-object?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Tee-Object
ms.openlocfilehash: 1f892ece313ddc0074afbeaf3f3243c0bb9f31d0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204392"
---
# Tee-Object

## 概要
將命令輸出儲存至檔案或變數，同時將它透過管線傳送。

## SYNTAX

### File (預設值)

```
Tee-Object [-InputObject <PSObject>] [-FilePath] <String> [-Append] [<CommonParameters>]
```

### LiteralFile

```
Tee-Object [-InputObject <PSObject>] -LiteralPath <String> [<CommonParameters>]
```

### 變數

```
Tee-Object [-InputObject <PSObject>] -Variable <String> [<CommonParameters>]
```

## DESCRIPTION

`Tee-Object`指令程式會將輸出重新導向，也就是說，它會以兩個方向傳送命令的輸出 (例如字母 T) 。 它會將輸出儲存至檔案或變數，同時將它透過管線傳送。 如果 `Tee-Object` 是管線中的最後一個命令，命令輸出就會顯示在提示字元中。

## 範例

### 範例1：將進程輸出至檔案和主控台

此範例會取得在電腦上執行的處理常式清單，並將結果傳送至檔案。
因為沒有指定第二個路徑，因此處理程序也會顯示在主控台中。

```powershell
Get-Process | Tee-Object -FilePath "C:\Test1\testfile2.txt"
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)    Id ProcessName
-------  ------    -----      ----- -----   ------    -- -----------
83       4     2300       4520    39     0.30    4032 00THotkey
272      6     1400       3944    34     0.06    3088 alg
81       3      804       3284    21     2.45     148 ApntEx
81       4     2008       5808    38     0.75    3684 Apoint
...
```

### 範例2：將進程輸出到變數和 `Select-Object`

這個範例會取得在電腦上執行的處理常式清單、將它們儲存到 `$proc` 變數，然後將它們傳送至 `Select-Object` 。

```powershell
Get-Process notepad | Tee-Object -Variable proc | Select-Object processname,handles
```

```Output
ProcessName                              Handles
-----------                              -------
notepad                                  43
notepad                                  37
notepad                                  38
notepad                                  38
```

`Select-Object`Cmdlet 會選取 **ProcessName** 並 **處理** 屬性。 請注意， `$proc` 變數包含所傳回的預設資訊 `Get-Process` 。

### 範例3：將系統檔案輸出到兩個記錄檔

此範例會將系統檔案清單儲存在兩個記錄檔中，也就是累計檔案和目前的檔案。

```powershell
Get-ChildItem -Path D: -File -System -Recurse |
  Tee-Object -FilePath "c:\test\AllSystemFiles.txt" -Append |
    Out-File c:\test\NewSystemFiles.txt
```

此命令會使用 `Get-ChildItem` Cmdlet 對 D：磁片磁碟機上的系統檔案進行遞迴搜尋。 管線運算子 (|) 會將清單傳送至，這會將清單附加至 AllSystemFiles.txt 檔案，然後將清單 `Tee-Object` 向下傳遞至 `Out-File` Cmdlet，以將清單儲存在 NewSystemFiles.txt 檔案中。

## PARAMETERS

### -Append

指出 Cmdlet 會將輸出附加至指定的檔案。 如果沒有這個參數，新內容會取代檔案中的任何現有內容而不會發出警告。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: File
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

指定此 Cmdlet 將物件儲存到萬用字元的檔案，但必須解析為單一檔案。

```yaml
Type: System.String
Parameter Sets: File
Aliases: Path

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -InputObject

指定要儲存和顯示的物件。 輸入包含物件的變數，或輸入可取得物件的命令或運算式。 您也可以使用管線將物件傳送至 `Tee-Object` 。

當您搭配使用 **inputobject** 參數與時， `Tee-Object` 不會將命令結果傳送至，而是 `Tee-Object` 會將 **inputobject** 值視為單一物件（即使值是集合）。

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

指定此 Cmdlet 將物件儲存到其中的檔案。 **LiteralPath** 參數值與 **FilePath** 不同，會完全依照其輸入值來使用。 沒有字元會被視為萬用字元。 如果路徑包含逸出字元，請將它括在單引號中。 單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。

```yaml
Type: System.String
Parameter Sets: LiteralFile
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Variable

指定 Cmdlet 用來儲存物件的變數。 輸入不含上述貨幣正負號 () 的變數名稱 `$` 。

```yaml
Type: System.String
Parameter Sets: Variable
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.Management.Automation.PSObject

您可以透過管線將物件傳送至 `Tee-Object` 。

## 輸出

### System.Management.Automation.PSObject

`Tee-Object` 傳回它重新導向的物件。

## 注意

您也可以使用 `Out-File` Cmdlet 或重新導向運算子，這兩個都會將輸出儲存在檔案中，但不會將輸出傳送至管線。

從 PowerShell 6 開始，在 `Tee-Object` 寫入檔案時，會使用不使用 BOM 的 utf-8 編碼。 如果您需要不同的編碼方式，請使用 `Out-File` Cmdlet 搭配 **編碼** 參數。

## 相關連結

[Compare-Object](Compare-Object.md)

[ForEach-Object](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Group-Object](Group-Object.md)

[Measure-Object](Measure-Object.md)

[New-Object](New-Object.md)

[Select-Object](Select-Object.md)

[Sort-Object](Sort-Object.md)

[Where-Object](../Microsoft.PowerShell.Core/Where-Object.md)

[about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)
