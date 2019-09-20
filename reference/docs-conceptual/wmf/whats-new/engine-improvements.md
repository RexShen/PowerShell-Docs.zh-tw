---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,設定
title: WMF 5.1 的 PowerShell 引擎改善
ms.openlocfilehash: a0af702832c0a90c994650e25918ecacdc33fc4b
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2019
ms.locfileid: "71147648"
---
# <a name="powershell-engine-improvements"></a><span data-ttu-id="6e97a-103">PowerShell 引擎改善</span><span class="sxs-lookup"><span data-stu-id="6e97a-103">PowerShell Engine Improvements</span></span>

<span data-ttu-id="6e97a-104">WMF 5.1 已實作核心 PowerShell 引擎的下列改善︰</span><span class="sxs-lookup"><span data-stu-id="6e97a-104">The following improvements to the core PowerShell engine have been implemented in WMF 5.1:</span></span>

## <a name="performance"></a><span data-ttu-id="6e97a-105">效能</span><span class="sxs-lookup"><span data-stu-id="6e97a-105">Performance</span></span>

<span data-ttu-id="6e97a-106">某些重要區域的效能已改善︰</span><span class="sxs-lookup"><span data-stu-id="6e97a-106">Performance has improved in some important areas:</span></span>

- <span data-ttu-id="6e97a-107">啟動</span><span class="sxs-lookup"><span data-stu-id="6e97a-107">Startup</span></span>
- <span data-ttu-id="6e97a-108">透過管線傳送到像是 `ForEach-Object` 和 `Where-Object` 的 Cmdlet 速度大約可提高 50%</span><span class="sxs-lookup"><span data-stu-id="6e97a-108">Pipelining to cmdlets like `ForEach-Object` and `Where-Object` is approximately 50% faster</span></span>

<span data-ttu-id="6e97a-109">一些改善範例 (結果取決於您的硬體而有所不同)：</span><span class="sxs-lookup"><span data-stu-id="6e97a-109">Some example improvements (your results may vary depending on your hardware):</span></span>

| <span data-ttu-id="6e97a-110">案例</span><span class="sxs-lookup"><span data-stu-id="6e97a-110">Scenario</span></span> | <span data-ttu-id="6e97a-111">5.0 的時間 (毫秒)</span><span class="sxs-lookup"><span data-stu-id="6e97a-111">5.0 Time (ms)</span></span> | <span data-ttu-id="6e97a-112">5.1 的時間 (毫秒)</span><span class="sxs-lookup"><span data-stu-id="6e97a-112">5.1 Time (ms)</span></span> |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | <span data-ttu-id="6e97a-113">900</span><span class="sxs-lookup"><span data-stu-id="6e97a-113">900</span></span> | <span data-ttu-id="6e97a-114">250</span><span class="sxs-lookup"><span data-stu-id="6e97a-114">250</span></span> |
| <span data-ttu-id="6e97a-115">PowerShell 首次執行︰`powershell -command "Unknown-Command"`</span><span class="sxs-lookup"><span data-stu-id="6e97a-115">First ever PowerShell run: `powershell -command "Unknown-Command"`</span></span> | <span data-ttu-id="6e97a-116">30000</span><span class="sxs-lookup"><span data-stu-id="6e97a-116">30000</span></span> | <span data-ttu-id="6e97a-117">13000</span><span class="sxs-lookup"><span data-stu-id="6e97a-117">13000</span></span> |
| <span data-ttu-id="6e97a-118">命令分析快取組建︰`powershell -command "Unknown-Command"`</span><span class="sxs-lookup"><span data-stu-id="6e97a-118">Command analysis cache built: `powershell -command "Unknown-Command"`</span></span> | <span data-ttu-id="6e97a-119">7000</span><span class="sxs-lookup"><span data-stu-id="6e97a-119">7000</span></span> | <span data-ttu-id="6e97a-120">520</span><span class="sxs-lookup"><span data-stu-id="6e97a-120">520</span></span> |
| <code>1..1000000 &#124; % { }</code> | <span data-ttu-id="6e97a-121">1400</span><span class="sxs-lookup"><span data-stu-id="6e97a-121">1400</span></span> | <span data-ttu-id="6e97a-122">750</span><span class="sxs-lookup"><span data-stu-id="6e97a-122">750</span></span> |

> [!NOTE]
> <span data-ttu-id="6e97a-123">與啟動相關的一項變更，可能影響到某些不受支援的案例。</span><span class="sxs-lookup"><span data-stu-id="6e97a-123">One change related to startup might impact some unsupported scenarios.</span></span> <span data-ttu-id="6e97a-124">PowerShell 不再讀取 `$pshome\*.ps1xml` 檔案，這些檔案已轉換成 C#，以避免處理 XML 檔案的一些檔案和 CPU 負荷。</span><span class="sxs-lookup"><span data-stu-id="6e97a-124">PowerShell no longer reads the files `$pshome\*.ps1xml` -- these files have been converted to C# to avoid some file and CPU overhead of processing the XML files.</span></span> <span data-ttu-id="6e97a-125">這些檔案對 V2 的支援仍然不變，因此，若變更檔案內容，對 V5 沒有任何效果，只對 V2 有效果。</span><span class="sxs-lookup"><span data-stu-id="6e97a-125">The files still exist to support V2 side-by-side, so if you change the file contents, it will not have any effect to V5, only V2.</span></span> <span data-ttu-id="6e97a-126">請注意，變更這些檔案內容向來是不受支援的案例。</span><span class="sxs-lookup"><span data-stu-id="6e97a-126">Note that changing the contents of these files was never a supported scenario.</span></span>

<span data-ttu-id="6e97a-127">另一個明顯的變更，是 PowerShell 如何快取匯出的命令和安裝在系統上的模組其他資訊。</span><span class="sxs-lookup"><span data-stu-id="6e97a-127">Another visible change is how PowerShell caches the exported commands and other information for modules that are installed on a system.</span></span> <span data-ttu-id="6e97a-128">以往，此快取儲存於 `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis` 目錄。</span><span class="sxs-lookup"><span data-stu-id="6e97a-128">Previously, this cache was stored in the directory `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`.</span></span> <span data-ttu-id="6e97a-129">在 WMF 5.1，快取是單一的 `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache` 檔案。</span><span class="sxs-lookup"><span data-stu-id="6e97a-129">In WMF 5.1, the cache is a single file `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span> <span data-ttu-id="6e97a-130">如需詳細資料，請參閱[模組分析快取](release-notes.md#module-analysis-cache)。</span><span class="sxs-lookup"><span data-stu-id="6e97a-130">See [Module Analysis Cache](release-notes.md#module-analysis-cache) for more details.</span></span>