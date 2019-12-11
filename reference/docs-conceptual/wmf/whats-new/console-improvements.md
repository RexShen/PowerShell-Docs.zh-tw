---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
title: WMF 5.1 的主控台改善
ms.openlocfilehash: d0dd8e3c31dc0ddebab1bb899468b77a9292954d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "71147628"
---
# <a name="console-improvements-in-wmf-51"></a><span data-ttu-id="e8eb1-103">WMF 5.1 的主控台改善</span><span class="sxs-lookup"><span data-stu-id="e8eb1-103">Console Improvements in WMF 5.1</span></span>

## <a name="powershell-console-improvements"></a><span data-ttu-id="e8eb1-104">PowerShell 主控台改善</span><span class="sxs-lookup"><span data-stu-id="e8eb1-104">PowerShell console improvements</span></span>

<span data-ttu-id="e8eb1-105">WMF 5.1 的 powershell.exe 已進行下列變更，以改善主控台體驗︰</span><span class="sxs-lookup"><span data-stu-id="e8eb1-105">The following changes have been made to powershell.exe in WMF 5.1 to improve the console experience:</span></span>

### <a name="vt100-support"></a><span data-ttu-id="e8eb1-106">VT100 支援</span><span class="sxs-lookup"><span data-stu-id="e8eb1-106">VT100 support</span></span>

<span data-ttu-id="e8eb1-107">Windows 10 新增了對 [VT100 逸出序列](/windows/console/console-virtual-terminal-sequences)的支援。</span><span class="sxs-lookup"><span data-stu-id="e8eb1-107">Windows 10 added support for [VT100 escape sequences](/windows/console/console-virtual-terminal-sequences).</span></span>
<span data-ttu-id="e8eb1-108">PowerShell 在計算表格寬度時，會忽略某些 VT100 格式逸出序列。</span><span class="sxs-lookup"><span data-stu-id="e8eb1-108">PowerShell will ignore certain VT100 formatting escape sequences when calculating table widths.</span></span>

<span data-ttu-id="e8eb1-109">PowerShell 也新增了可用於將程式碼格式化的新 API，以判斷是否支援 VT100。</span><span class="sxs-lookup"><span data-stu-id="e8eb1-109">PowerShell also added a new API that can be used in formatting code to determine if VT100 is supported.</span></span> <span data-ttu-id="e8eb1-110">例如：</span><span class="sxs-lookup"><span data-stu-id="e8eb1-110">For example:</span></span>

```powershell
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

<span data-ttu-id="e8eb1-111">以下是可用來反白 `Select-String` 相符項目的完整[範例](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7)。</span><span class="sxs-lookup"><span data-stu-id="e8eb1-111">Here is a complete [example](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) that can be used to highlight matches from `Select-String`.</span></span> <span data-ttu-id="e8eb1-112">將範例儲存在名為 `MatchInfo.format.ps1xml` 的檔案中，然後在您的設定檔或其他位置執行 `Update-FormatData -Prepend MatchInfo.format.ps1xml` 以便加以使用。</span><span class="sxs-lookup"><span data-stu-id="e8eb1-112">Save the example in a file named `MatchInfo.format.ps1xml`, then to use it, in your profile or elsewhere, run `Update-FormatData -Prepend MatchInfo.format.ps1xml`.</span></span>

<span data-ttu-id="e8eb1-113">請注意，從 Windows 10 年度更新版開始才支援 VT100 逸出序列。</span><span class="sxs-lookup"><span data-stu-id="e8eb1-113">Note that VT100 escape sequences are only supported starting with the Windows 10 Anniversary update.</span></span>
<span data-ttu-id="e8eb1-114">舊版系統不支援它們。</span><span class="sxs-lookup"><span data-stu-id="e8eb1-114">They are not supported on earlier systems.</span></span>

### <a name="vi-mode-support-in-psreadline"></a><span data-ttu-id="e8eb1-115">PSReadline 的 Vi 模式支援</span><span class="sxs-lookup"><span data-stu-id="e8eb1-115">Vi mode support in PSReadline</span></span>

<span data-ttu-id="e8eb1-116">[PSReadline](https://github.com/PowerShell/PSReadLine) 加入了對 vi 模式的支援。</span><span class="sxs-lookup"><span data-stu-id="e8eb1-116">[PSReadline](https://github.com/PowerShell/PSReadLine) adds support for vi mode.</span></span> <span data-ttu-id="e8eb1-117">若要使用 vi 模式，請執行 `Set-PSReadlineOption -EditMode Vi`。</span><span class="sxs-lookup"><span data-stu-id="e8eb1-117">To use vi mode, run `Set-PSReadlineOption -EditMode Vi`.</span></span>

### <a name="redirected-stdin-with-interactive-input"></a><span data-ttu-id="e8eb1-118">以互動輸入重新導向的 stdin</span><span class="sxs-lookup"><span data-stu-id="e8eb1-118">Redirected stdin with interactive input</span></span>

<span data-ttu-id="e8eb1-119">在舊版中，重新導向 stdin 且要以互動方式輸入命令時，需要使用 `powershell -File -` 啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="e8eb1-119">In earlier versions, starting PowerShell with `powershell -File -` was required when stdin was redirected and you wanted to enter commands interactively.</span></span>

<span data-ttu-id="e8eb1-120">有了 WMF 5.1，即不再需要此難以探索的選項。</span><span class="sxs-lookup"><span data-stu-id="e8eb1-120">With WMF 5.1, this hard to discover option is no longer necessary.</span></span> <span data-ttu-id="e8eb1-121">您不需使用任何選項就能啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="e8eb1-121">You can start PowerShell without any options.</span></span>

<span data-ttu-id="e8eb1-122">請注意，PSReadline 不支援重新導向的 stdin，而具有重新導向之 stdin 的內建命令列編輯體驗極受限制，例如，方向鍵無法運作。</span><span class="sxs-lookup"><span data-stu-id="e8eb1-122">Note that PSReadline does not support redirected stdin, and the built-in command-line editing experience with redirected stdin is extremely limited, for example, arrow keys don't work.</span></span> <span data-ttu-id="e8eb1-123">新版的 PSReadline 應該會解決這個問題。</span><span class="sxs-lookup"><span data-stu-id="e8eb1-123">A future release of PSReadline should address this issue.</span></span>