---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 使用 Tab 鍵擴充
ms.openlocfilehash: d96cbf848f464aff29a7bed9b70d0b6a000aa808
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "67031019"
---
# <a name="using-tab-expansion"></a><span data-ttu-id="e8783-103">使用 Tab 鍵擴充</span><span class="sxs-lookup"><span data-stu-id="e8783-103">Using Tab Expansion</span></span>

<span data-ttu-id="e8783-104">命令列殼層通常會提供方法，透過加速命令輸入以及提供提示，來自動完成長檔案或命令的名稱。</span><span class="sxs-lookup"><span data-stu-id="e8783-104">Command-line shells often provide a way to complete the names of long files or commands automatically, speeding up command entry and providing hints.</span></span> <span data-ttu-id="e8783-105">PowerShell 可讓您按 <kbd>Tab</kbd> 鍵，來填入檔案名稱和 Cmdlet 名稱。</span><span class="sxs-lookup"><span data-stu-id="e8783-105">PowerShell allows you to fill in file names and cmdlet names by pressing the <kbd>Tab</kbd> key.</span></span>

> [!NOTE]
> <span data-ttu-id="e8783-106">Tab 鍵擴充由內部函式 TabExpansion 或 TabExpansion2 所控制。</span><span class="sxs-lookup"><span data-stu-id="e8783-106">Tab expansion is controlled by the internal function TabExpansion or TabExpansion2.</span></span> <span data-ttu-id="e8783-107">因為可以修改或覆寫這個函式，所以這項討論只是預設 PowerShell 設定行為的指南。</span><span class="sxs-lookup"><span data-stu-id="e8783-107">Since this function can be modified or overridden, this discussion is a guide to the behavior of the default PowerShell configuration.</span></span>

<span data-ttu-id="e8783-108">若要自動從可用的選項中填入檔案名稱或路徑，請輸入部分名稱，然後按 <kbd>Tab</kbd> 鍵。</span><span class="sxs-lookup"><span data-stu-id="e8783-108">To fill in a filename or path from the available choices automatically, type part of the name and press the <kbd>Tab</kbd> key.</span></span> <span data-ttu-id="e8783-109">PowerShell 會自動將名稱擴充到找到的第一個相符項目。</span><span class="sxs-lookup"><span data-stu-id="e8783-109">PowerShell will automatically expand the name to the first match that it finds.</span></span> <span data-ttu-id="e8783-110">重複按 <kbd>Tab</kbd> 鍵，會循環顯示所有可用選項。</span><span class="sxs-lookup"><span data-stu-id="e8783-110">Pressing the <kbd>Tab</kbd> key repeatedly will cycle through all of the available choices.</span></span>

<span data-ttu-id="e8783-111">Cmdlet 名稱的 Tab 鍵擴充略有不同。</span><span class="sxs-lookup"><span data-stu-id="e8783-111">The tab expansion of cmdlet names is slightly different.</span></span> <span data-ttu-id="e8783-112">若要對 Cmdlet 名稱使用 Tab 鍵擴充，請輸入名稱的完整第一個部分 (動詞) 和後面的連字號。</span><span class="sxs-lookup"><span data-stu-id="e8783-112">To use tab expansion on a cmdlet name, type the entire first part of the name (the verb) and the hyphen that follows it.</span></span> <span data-ttu-id="e8783-113">您可以填入名稱的更多部分來進行局部比對。</span><span class="sxs-lookup"><span data-stu-id="e8783-113">You can fill in more of the name for a partial match.</span></span> <span data-ttu-id="e8783-114">例如，如果您鍵入 `get-co`，然後按 <kbd>Tab</kbd> 鍵，則 PowerShell 會自動將此項目展開到 `Get-Command` Cmdlet (請注意，這也會將字母的大小寫變更為其標準形式)。</span><span class="sxs-lookup"><span data-stu-id="e8783-114">For example, if you type `get-co` and then press the <kbd>Tab</kbd> key, PowerShell will automatically expand this to the `Get-Command` cmdlet (notice that it also changes the case of letters to their standard form).</span></span> <span data-ttu-id="e8783-115">如果您再次按下 <kbd>Tab</kbd> 鍵，PowerShell 會以僅有的其他相符 Cmdlet 名稱 (`Get-Content`) 取代此項目。</span><span class="sxs-lookup"><span data-stu-id="e8783-115">If you press <kbd>Tab</kbd> key again, PowerShell replaces this with the only other matching cmdlet name, `Get-Content`.</span></span>

<span data-ttu-id="e8783-116">您可以對同一行重複使用 Tab 鍵擴充。</span><span class="sxs-lookup"><span data-stu-id="e8783-116">You can use tab expansion repeatedly on the same line.</span></span> <span data-ttu-id="e8783-117">例如，您可以對 `Get-Content` Cmdlet 的名稱使用 Tab 鍵展開，方法是輸入：</span><span class="sxs-lookup"><span data-stu-id="e8783-117">For example, you can use tab expansion on the name of the `Get-Content` cmdlet by entering:</span></span>

```
PS> Get-Con<Tab>
```

<span data-ttu-id="e8783-118">按 <kbd>Tab</kbd> 鍵時，命令會擴充到︰</span><span class="sxs-lookup"><span data-stu-id="e8783-118">When you press the <kbd>Tab</kbd> key, the command expands to:</span></span>

```
PS> Get-Content
```

<span data-ttu-id="e8783-119">您接著可以局部指定 Active Setup 記錄檔的路徑，並再次使用 Tab 鍵擴充︰</span><span class="sxs-lookup"><span data-stu-id="e8783-119">You can then partially specify the path to the Active Setup log file and use tab expansion again:</span></span>

```
PS> Get-Content c:\windows\acts<Tab>
```

<span data-ttu-id="e8783-120">按 <kbd>Tab</kbd> 鍵時，命令會擴充到︰</span><span class="sxs-lookup"><span data-stu-id="e8783-120">When you press the <kbd>Tab</kbd> key, the command expands to:</span></span>

```
PS> Get-Content C:\windows\actsetup.log
```

> [!NOTE]
> <span data-ttu-id="e8783-121">Tab 鍵擴充處理程序的一個限制是一律會將 Tab 鍵解譯為嘗試完成文字。</span><span class="sxs-lookup"><span data-stu-id="e8783-121">One limitation of the tab expansion process is that tabs are always interpreted as attempts to complete a word.</span></span> <span data-ttu-id="e8783-122">若您將命令範例複製並貼上 PowerShell 主控台，請確認未在該範例使用 Tab 鍵，如果有的話將無法預測結果，而且幾乎可以肯定不是您所預期的結果。</span><span class="sxs-lookup"><span data-stu-id="e8783-122">If you copy and paste command examples into a PowerShell console, make sure that the sample does not contain tabs; if it does, the results will be unpredictable and will almost certainly not be what you intended.</span></span>
