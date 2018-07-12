---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,設定
title: WMF 5.1 的 PowerShell 引擎改善
ms.openlocfilehash: 738f72b910de7d44f48309013237d523d0dd40a4
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892887"
---
# <a name="powershell-engine-improvements"></a><span data-ttu-id="8b11c-103">PowerShell 引擎改善</span><span class="sxs-lookup"><span data-stu-id="8b11c-103">PowerShell Engine Improvements</span></span>

<span data-ttu-id="8b11c-104">WMF 5.1 已實作核心 PowerShell 引擎的下列改善︰</span><span class="sxs-lookup"><span data-stu-id="8b11c-104">The following improvements to the core PowerShell engine have been implemented in WMF 5.1:</span></span>

## <a name="performance"></a><span data-ttu-id="8b11c-105">效能</span><span class="sxs-lookup"><span data-stu-id="8b11c-105">Performance</span></span>

<span data-ttu-id="8b11c-106">某些重要區域的效能已改善︰</span><span class="sxs-lookup"><span data-stu-id="8b11c-106">Performance has improved in some important areas:</span></span>

- <span data-ttu-id="8b11c-107">啟動</span><span class="sxs-lookup"><span data-stu-id="8b11c-107">Startup</span></span>
- <span data-ttu-id="8b11c-108">透過管線傳送到像是 `ForEach-Object` 和 `Where-Object` 的 Cmdlet 速度大約可提高 50%</span><span class="sxs-lookup"><span data-stu-id="8b11c-108">Pipelining to cmdlets like `ForEach-Object` and `Where-Object` is approximately 50% faster</span></span>

<span data-ttu-id="8b11c-109">一些改善範例 (結果取決於您的硬體而有所不同)：</span><span class="sxs-lookup"><span data-stu-id="8b11c-109">Some example improvements (your results may vary depending on your hardware):</span></span>

| <span data-ttu-id="8b11c-110">案例</span><span class="sxs-lookup"><span data-stu-id="8b11c-110">Scenario</span></span> | <span data-ttu-id="8b11c-111">5.0 的時間 (毫秒)</span><span class="sxs-lookup"><span data-stu-id="8b11c-111">5.0 Time (ms)</span></span> | <span data-ttu-id="8b11c-112">5.1 的時間 (毫秒)</span><span class="sxs-lookup"><span data-stu-id="8b11c-112">5.1 Time (ms)</span></span> |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | <span data-ttu-id="8b11c-113">900</span><span class="sxs-lookup"><span data-stu-id="8b11c-113">900</span></span> | <span data-ttu-id="8b11c-114">250</span><span class="sxs-lookup"><span data-stu-id="8b11c-114">250</span></span> |
| <span data-ttu-id="8b11c-115">PowerShell 首次執行︰`powershell -command "Unknown-Command"`</span><span class="sxs-lookup"><span data-stu-id="8b11c-115">First ever PowerShell run: `powershell -command "Unknown-Command"`</span></span> | <span data-ttu-id="8b11c-116">30000</span><span class="sxs-lookup"><span data-stu-id="8b11c-116">30000</span></span> | <span data-ttu-id="8b11c-117">13000</span><span class="sxs-lookup"><span data-stu-id="8b11c-117">13000</span></span> |
| <span data-ttu-id="8b11c-118">命令分析快取組建︰`powershell -command "Unknown-Command"`</span><span class="sxs-lookup"><span data-stu-id="8b11c-118">Command analysis cache built: `powershell -command "Unknown-Command"`</span></span> | <span data-ttu-id="8b11c-119">7000</span><span class="sxs-lookup"><span data-stu-id="8b11c-119">7000</span></span> | <span data-ttu-id="8b11c-120">520</span><span class="sxs-lookup"><span data-stu-id="8b11c-120">520</span></span> |
| <code>1..1000000 &#124; % { }</code> | <span data-ttu-id="8b11c-121">1400</span><span class="sxs-lookup"><span data-stu-id="8b11c-121">1400</span></span> | <span data-ttu-id="8b11c-122">750</span><span class="sxs-lookup"><span data-stu-id="8b11c-122">750</span></span> |

> [!Note]
> <span data-ttu-id="8b11c-123">與啟動相關的一項變更，可能影響到某些不受支援的案例。</span><span class="sxs-lookup"><span data-stu-id="8b11c-123">One change related to startup might impact some unsupported scenarios.</span></span>
> <span data-ttu-id="8b11c-124">PowerShell 不再讀取 `$pshome\*.ps1xml` 檔案，這些檔案已轉換成 C#，以避免處理 XML 檔案的一些檔案和 CPU 負荷。</span><span class="sxs-lookup"><span data-stu-id="8b11c-124">PowerShell no longer reads the files `$pshome\*.ps1xml` -- these files have been converted to C# to avoid some file and CPU overhead of processing the XML files.</span></span>
> <span data-ttu-id="8b11c-125">這些檔案對 V2 的支援仍然不變，因此，若變更檔案內容，對 V5 沒有任何效果，只對 V2 有效果。</span><span class="sxs-lookup"><span data-stu-id="8b11c-125">The files still exist to support V2 side-by-side, so if you change the file contents, it will not have any effect to V5, only V2.</span></span>
> <span data-ttu-id="8b11c-126">請注意，變更這些檔案內容向來是不受支援的案例。</span><span class="sxs-lookup"><span data-stu-id="8b11c-126">Note that changing the contents of these files was never a supported scenario.</span></span>

<span data-ttu-id="8b11c-127">另一個明顯的變更，是 PowerShell 如何快取匯出的命令和安裝在系統上的模組其他資訊。</span><span class="sxs-lookup"><span data-stu-id="8b11c-127">Another visible change is how PowerShell caches the exported commands and other information for modules that are installed on a system.</span></span>
<span data-ttu-id="8b11c-128">以往，此快取儲存於 `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis` 目錄。</span><span class="sxs-lookup"><span data-stu-id="8b11c-128">Previously, this cache was stored in the directory `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`.</span></span>
<span data-ttu-id="8b11c-129">在 WMF 5.1，快取是單一的 `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache` 檔案。</span><span class="sxs-lookup"><span data-stu-id="8b11c-129">In WMF 5.1, the cache is a single file `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span>
<span data-ttu-id="8b11c-130">如需詳細資料，請參閱[模組分析快取](scenarios-features.md#module-analysis-cache)。</span><span class="sxs-lookup"><span data-stu-id="8b11c-130">See [Module Analysis Cache](scenarios-features.md#module-analysis-cache) for more details.</span></span>