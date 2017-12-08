---
title: "WMF 5.1 的主控台改善"
ms.date: 2016-07-13
keywords: "PowerShell、DSC、WMF"
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
ms.openlocfilehash: fc0c78f59a2c4cda5c6aad625a5eaf5121485bad
ms.sourcegitcommit: 26f4e52f3dd008b51b7eae7b634f0216eec6200e
ms.translationtype: HT
ms.contentlocale: zh-TW
---
# <a name="console-improvements-in-wmf-51"></a><span data-ttu-id="12a5f-103">WMF 5.1 的主控台改善</span><span class="sxs-lookup"><span data-stu-id="12a5f-103">Console Improvements in WMF 5.1</span></span>#

## <a name="powershell-console-improvements"></a><span data-ttu-id="12a5f-104">PowerShell 主控台改善</span><span class="sxs-lookup"><span data-stu-id="12a5f-104">PowerShell console improvements</span></span>

<span data-ttu-id="12a5f-105">WMF 5.1 的 powershell.exe 已進行下列變更，以改善主控台體驗︰</span><span class="sxs-lookup"><span data-stu-id="12a5f-105">The following changes have been made to powershell.exe in WMF 5.1 to improve the console experience:</span></span>

###<a name="vt100-support"></a><span data-ttu-id="12a5f-106">VT100 支援</span><span class="sxs-lookup"><span data-stu-id="12a5f-106">VT100 support</span></span>

<span data-ttu-id="12a5f-107">Windows 10 新增了對 [VT100 逸出序列](https://msdn.microsoft.com/en-us/library/windows/desktop/mt638032(v=vs.85).aspx)的支援。</span><span class="sxs-lookup"><span data-stu-id="12a5f-107">Windows 10 added support for [VT100 escape sequences](https://msdn.microsoft.com/en-us/library/windows/desktop/mt638032(v=vs.85).aspx).</span></span>
<span data-ttu-id="12a5f-108">PowerShell 在計算表格寬度時，會忽略某些 VT100 格式逸出序列。</span><span class="sxs-lookup"><span data-stu-id="12a5f-108">PowerShell will ignore certain VT100 formatting escape sequences when calculating table widths.</span></span>

<span data-ttu-id="12a5f-109">PowerShell 也新增了可用於將程式碼格式化的新 API，以判斷是否支援 VT100。</span><span class="sxs-lookup"><span data-stu-id="12a5f-109">PowerShell also added a new API that can be used in formatting code to determine if VT100 is supported.</span></span> <span data-ttu-id="12a5f-110">例如：</span><span class="sxs-lookup"><span data-stu-id="12a5f-110">For example:</span></span>

```
if ($host.UI.SupportsVirtualTerminal)
{
    $esc = [char]0x1b
    "A yellow ${esc}[93mhello${esc}[0m"
}
else
{
    "A default hello"
}
```
<span data-ttu-id="12a5f-111">以下是可用來反白 Select-String 相符項目的完整[範例](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7)。</span><span class="sxs-lookup"><span data-stu-id="12a5f-111">Here is a complete [example](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) that can be used to highlight matches from Select-String.</span></span>
<span data-ttu-id="12a5f-112">將範例儲存在名為 `MatchInfo.format.ps1xml` 的檔案中，然後在您的設定檔或其他位置執行 `Update-FormatData -Prepend MatchInfo.format.ps1xml` 以便加以使用。</span><span class="sxs-lookup"><span data-stu-id="12a5f-112">Save the example in a file named `MatchInfo.format.ps1xml`, then to use it, in your profile or elsewhere, run `Update-FormatData -Prepend MatchInfo.format.ps1xml`.</span></span>

<span data-ttu-id="12a5f-113">請注意，從 Windows 10 年度更新版開始才支援 VT100 逸出序列，舊版系統不支援。</span><span class="sxs-lookup"><span data-stu-id="12a5f-113">Note that VT100 escape sequences are only supported starting with the Windows 10 Anniversary update; they are not supported on earlier systems.</span></span>   

### <a name="vi-mode-support-in-psreadline"></a><span data-ttu-id="12a5f-114">PSReadline 的 Vi 模式支援</span><span class="sxs-lookup"><span data-stu-id="12a5f-114">Vi mode support in PSReadline</span></span>

<span data-ttu-id="12a5f-115">[PSReadline](https://github.com/lzybkr/PSReadLine) 加入了對 vi 模式的支援。</span><span class="sxs-lookup"><span data-stu-id="12a5f-115">[PSReadline](https://github.com/lzybkr/PSReadLine) adds support for vi mode.</span></span> <span data-ttu-id="12a5f-116">若要使用 vi 模式，請執行 `Set-PSReadlineOption -EditMode Vi`。</span><span class="sxs-lookup"><span data-stu-id="12a5f-116">To use vi mode, run `Set-PSReadlineOption -EditMode Vi`.</span></span>

### <a name="redirected-stdin-with-interactive-input"></a><span data-ttu-id="12a5f-117">以互動輸入重新導向的 stdin</span><span class="sxs-lookup"><span data-stu-id="12a5f-117">Redirected stdin with interactive input</span></span> 

<span data-ttu-id="12a5f-118">在舊版中，重新導向 stdin 且要以互動方式輸入命令時，需要使用 `powershell -File -` 啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="12a5f-118">In earlier versions, starting PowerShell with `powershell -File -` was required when stdin was redirected and you wanted to enter commands interactively.</span></span>

<span data-ttu-id="12a5f-119">有了 WMF 5.1，即不再需要此難以探索的選項。</span><span class="sxs-lookup"><span data-stu-id="12a5f-119">With WMF 5.1, this hard to discover option is no longer necessary.</span></span> <span data-ttu-id="12a5f-120">可以啟動 PowerShell 而不使用任何選項，例如 `powershell`。</span><span class="sxs-lookup"><span data-stu-id="12a5f-120">You can start PowerShell without any options, e.g. `powershell`.</span></span>

<span data-ttu-id="12a5f-121">請注意，PSReadline 目前不支援重新導向的 stdin，而附重新導向的 stdin 的內建命令列編輯經驗極受限制，例如方向鍵無法運作。</span><span class="sxs-lookup"><span data-stu-id="12a5f-121">Note that PSReadline does not currently support redirected stdin, and the built-in command-line editing experience with redirected stdin is extremely limited, for example, arrow keys don't work.</span></span> <span data-ttu-id="12a5f-122">新版的 PSReadline 應該會解決這個問題。</span><span class="sxs-lookup"><span data-stu-id="12a5f-122">A future release of PSReadline should address this issue.</span></span>   
