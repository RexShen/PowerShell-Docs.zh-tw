---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-clipboard?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Clipboard
ms.openlocfilehash: 2885b2624f8334e8699e0baea5fc41b3f025fe2a
ms.sourcegitcommit: d757d64ea8c8af4d92596e8fbe15f2f40d48d3ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "93206303"
---
# Get-Clipboard

## 概要
取得目前的 Windows 剪貼簿專案。

## SYNTAX

```
Get-Clipboard [-Format <ClipboardFormat>] [-TextFormatType <TextDataFormat>] [-Raw] [<CommonParameters>]
```

## DESCRIPTION

`Get-Clipboard`Cmdlet 會取得目前的 Windows 剪貼簿專案。 多行文字會以類似于的字串陣列形式傳回 `Get-Content` 。

## 範例

### 範例1：取得剪貼簿的內容，並將它顯示在命令列中

在此範例中，我們在瀏覽器中以滑鼠右鍵按一下影像，然後選擇 [ **複製** ] 動作。 下列命令會顯示儲存在剪貼簿中之影像的 URL 連結。

```powershell
Get-Clipboard
```

```Output
https://en.wikipedia.org/wiki/PowerShell
```

### 範例2：取得特定格式之剪貼簿的內容

在此範例中，我們會在 Windows Explorerby 中將檔案複製到剪貼簿，並在其中選取並按下 <kbd>ctrl-c</kbd>。 您可以使用下列命令，以檔案清單的形式存取剪貼簿的內容：

```powershell
Get-Clipboard -Format FileDropList
```

```Output
    Directory: C:\Git\PS-Docs\PowerShell-Docs\wmf

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         5/7/2019   1:11 PM          10010 TOC.yml
-a----       11/18/2016  10:10 AM             53 md.style
-a----         5/6/2019   9:32 AM           4177 overview.md
-a----        6/28/2018   2:28 PM            345 README.md
```

## PARAMETERS

### -Format

指定剪貼簿的類型或格式。 此參數可接受的值為：

- Text
- FileDropList
- 映像
- 音訊

```yaml
Type: Microsoft.PowerShell.Commands.ClipboardFormat
Parameter Sets: (All)
Aliases:
Accepted values: Text, FileDropList, Image, Audio

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Raw

取得剪貼簿的整個內容。 多行文字會以單一多行字串的形式傳回，而不是字串陣列。

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

### -TextFormatType

指定剪貼簿的文字資料格式類型。 此參數可接受的值為：

- Text
- UnicodeText
- Rtf
- HTML
- CommaSeparatedValue

```yaml
Type: System.Windows.Forms.TextDataFormat
Parameter Sets: (All)
Aliases:
Accepted values: Text, UnicodeText, Rtf, Html, CommaSeparatedValue

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

## 輸出

### System.string、FileInfo、system.object、Image、Image、Image、Image

## 注意

## 相關連結

[Set-Clipboard](Set-Clipboard.md)
