---
description: 說明如何在主控台提示中建立自訂 PowerShell 讀取輸入的方式。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/04/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_psconsolehostreadline?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSConsoleHostReadLine
ms.openlocfilehash: 59373f7a69f5a27411c9087bb666929321f654c0
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208616"
---
# <a name="about_psconsolehostreadline"></a>about_PSConsoleHostReadLine

## <a name="short-description"></a>簡短描述
說明如何在主控台提示中建立自訂 PowerShell 讀取輸入的方式。

## <a name="long-description"></a>詳細描述

從 Windows PowerShell 3.0 開始，您可以撰寫名為 PSConsoleHostReadLine 的函式，它會覆寫主控台輸入的預設處理方式。

### <a name="examples"></a>範例

下列範例會啟動 [記事本]，並從使用者建立的文字檔取得輸入：

```powershell
function PSConsoleHostReadLine
{
  $inputFile = Join-Path $env:TEMP PSConsoleHostReadLine
  Set-Content $inputFile "PS > "

  # Notepad opens. Enter your command in it, save the file, and then exit.
  notepad $inputFile | Out-Null
  $userInput = Get-Content $inputFile
  $resultingCommand = $userInput.Replace("PS >", "")
  $resultingCommand
}
```

### <a name="remarks"></a>REMARKS

根據預設，PowerShell 會從主控台讀取輸入，在所謂的「處理後模式」中，Windows 主控台子系統會處理所有 keypresses、F7 功能表和其他輸入。 當您按 Enter 或 Tab 鍵時，PowerShell 會取得您所輸入的文字到該點為止。 在按下 Enter 或 Tab 鍵之前，無法得知您已按下 Ctrl-R、Ctrl A、Ctrl-E 或任何其他按鍵。在 Windows PowerShell 3.0 中，PSConsoleHostReadLine 函數可解決此問題。 當您在 PowerShell 主控台主機中定義名為 PSConsoleHostReadline 的函式時，PowerShell 會呼叫該函式，而不是「處理後模式」輸入機制。

### <a name="see-also"></a>另請參閱

[about_Prompts](about_Prompts.md)
