---
description: 說明如何在主控台提示中建立自訂 PowerShell 讀取輸入的方式。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/04/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_psconsolehostreadline?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSConsoleHostReadLine
ms.openlocfilehash: 143fa763c109b5645f992c3bb0a3097a8b2d9e90
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206723"
---
# <a name="about_psconsolehostreadline"></a><span data-ttu-id="3429b-104">about_PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="3429b-104">about_PSConsoleHostReadLine</span></span>

## <a name="short-description"></a><span data-ttu-id="3429b-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="3429b-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="3429b-106">說明如何在主控台提示中建立自訂 PowerShell 讀取輸入的方式。</span><span class="sxs-lookup"><span data-stu-id="3429b-106">Explains how to create a customize how PowerShell reads input at the console prompt.</span></span>

## <a name="long-description"></a><span data-ttu-id="3429b-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="3429b-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="3429b-108">從 Windows PowerShell 3.0 開始，您可以撰寫名為 PSConsoleHostReadLine 的函式，它會覆寫主控台輸入的預設處理方式。</span><span class="sxs-lookup"><span data-stu-id="3429b-108">Starting in Windows PowerShell 3.0, you can write a function named PSConsoleHostReadLine that overrides the default way that console input is processed.</span></span>

### <a name="examples"></a><span data-ttu-id="3429b-109">範例</span><span class="sxs-lookup"><span data-stu-id="3429b-109">EXAMPLES</span></span>

<span data-ttu-id="3429b-110">下列範例會啟動 [記事本]，並從使用者建立的文字檔取得輸入：</span><span class="sxs-lookup"><span data-stu-id="3429b-110">The following example launches Notepad and gets input from a text File that the user creates:</span></span>

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

### <a name="remarks"></a><span data-ttu-id="3429b-111">REMARKS</span><span class="sxs-lookup"><span data-stu-id="3429b-111">REMARKS</span></span>

<span data-ttu-id="3429b-112">根據預設，PowerShell 會從主控台讀取輸入，在所謂的「處理後模式」中，Windows 主控台子系統會處理所有 keypresses、F7 功能表和其他輸入。</span><span class="sxs-lookup"><span data-stu-id="3429b-112">By default, PowerShell reads input from the console in what is known as "Cooked Mode" -- in which the Windows console subsystem handles all the keypresses, F7 menus, and other input.</span></span> <span data-ttu-id="3429b-113">當您按 Enter 或 Tab 鍵時，PowerShell 會取得您所輸入的文字到該點為止。</span><span class="sxs-lookup"><span data-stu-id="3429b-113">When you press Enter or Tab, PowerShell gets the text that you have typed up to that point.</span></span> <span data-ttu-id="3429b-114">在按下 Enter 或 Tab 鍵之前，無法得知您已按下 Ctrl-R、Ctrl A、Ctrl-E 或任何其他按鍵。在 Windows PowerShell 3.0 中，PSConsoleHostReadLine 函數可解決此問題。</span><span class="sxs-lookup"><span data-stu-id="3429b-114">There is no way for it to know that you pressed Ctrl-R, Ctrl-A, Ctrl-E, or any other keys before pressing Enter or Tab. In Windows PowerShell 3.0, the PSConsoleHostReadLine function solves this issue.</span></span> <span data-ttu-id="3429b-115">當您在 PowerShell 主控台主機中定義名為 PSConsoleHostReadline 的函式時，PowerShell 會呼叫該函式，而不是「處理後模式」輸入機制。</span><span class="sxs-lookup"><span data-stu-id="3429b-115">When you define a function named PSConsoleHostReadline in the PowerShell console host, PowerShell calls that function instead of the "Cooked Mode" input mechanism.</span></span>

### <a name="see-also"></a><span data-ttu-id="3429b-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3429b-116">SEE ALSO</span></span>

[<span data-ttu-id="3429b-117">about_Prompts</span><span class="sxs-lookup"><span data-stu-id="3429b-117">about_Prompts</span></span>](about_Prompts.md)

