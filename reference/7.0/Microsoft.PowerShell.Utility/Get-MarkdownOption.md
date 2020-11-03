---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Module Name: Microsoft.PowerShell.Utility
online version: https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Utility/Get-MarkdownOption?view=powershell-7&WT.mc_id=ps-gethelp
ms.date: 01/30/2020
schema: 2.0.0
ms.openlocfilehash: f39add03a3b0250172cbb117a4233bb01958d9d3
ms.sourcegitcommit: b0488ca6557501184f20c8343b0ed5147b09e3fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "93205263"
---
# Get-MarkdownOption

## 概要
傳回在主控台中用來呈現 Markdown 內容的目前色彩和樣式。

## SYNTAX

```
Get-MarkdownOption [<CommonParameters>]
```

## DESCRIPTION

傳回在主控台中用來呈現 Markdown 內容的目前色彩和樣式。 在此 Cmdlet 的輸出中顯示的字串包含用來變更所轉譯 Markdown 文字之色彩和樣式的 ANSI 轉義碼。

如需 Markdown 的詳細資訊，請參閱 [CommonMark](https://commonmark.org/) 網站。

## 範例

### 範例 1-取得目前的色彩和樣式

```powershell
Get-MarkdownOption
```

```Output
Header1         : [7m
Header2         : [4;93m
Header3         : [4;94m
Header4         : [4;95m
Header5         : [4;96m
Header6         : [4;97m
Code            : [48;2;155;155;155;38;2;30;30;30m
Link            : [4;38;5;117m
Image           : [33m
EmphasisBold    : [1m
EmphasisItalics : [36m
```

> [!NOTE]
> 輸出中所顯示的字串值為 ANSI escape 序列 () **之後的** 字元 `[char]0x1B` 。 如需 ANSI escape 程式碼工作的詳細資訊，請參閱 [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code)。

## PARAMETERS

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無

## 輸出

### MarkdownRender. PSMarkdownOptionInfo

## 注意

## 相關連結

[Set-MarkdownOption](Set-MarkdownOption.md)

[ConvertFrom-Markdown](ConvertFrom-Markdown.md)

[Show-Markdown](Show-Markdown.md)

[ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code)

[CommonMark](https://commonmark.org/)
