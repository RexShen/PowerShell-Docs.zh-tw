---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 了解 Windows PowerShell 管線
ms.assetid: 6be50926-7943-4ef7-9499-4490d72a63fb
ms.openlocfilehash: c3f1d17432cf3a77c0f5ecae137a4233a28a19d7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
ms.locfileid: "30951064"
---
# <a name="understanding-the-windows-powershell-pipeline"></a><span data-ttu-id="8fa0c-103">了解 Windows PowerShell 管線</span><span class="sxs-lookup"><span data-stu-id="8fa0c-103">Understanding the Windows PowerShell Pipeline</span></span>
<span data-ttu-id="8fa0c-104">管線幾乎可以在 Windows PowerShell 中的所有位置運作。</span><span class="sxs-lookup"><span data-stu-id="8fa0c-104">Piping works virtually everywhere in Windows PowerShell.</span></span> <span data-ttu-id="8fa0c-105">雖然您會在畫面上看到文字，但是 Windows PowerShell 並不會在命令之間傳送文字，</span><span class="sxs-lookup"><span data-stu-id="8fa0c-105">Although you see text on the screen, Windows PowerShell does not pipe text between commands.</span></span> <span data-ttu-id="8fa0c-106">而是傳送物件。</span><span class="sxs-lookup"><span data-stu-id="8fa0c-106">Instead, it pipes objects.</span></span>

<span data-ttu-id="8fa0c-107">用於管線的標記法與其他殼層中所使用的標記法類似，因此第一眼時，Windows PowerShell 引進了新項目可能不大明顯。</span><span class="sxs-lookup"><span data-stu-id="8fa0c-107">The notation used for pipelines is similar to that used in other shells, so at first glance, it may not be apparent that Windows PowerShell introduces something new.</span></span> <span data-ttu-id="8fa0c-108">例如，如果您使用 **Out-Host** Cmdlet 強制逐頁顯示另一個命令的輸出，則輸出看起來就像畫面上所顯示的一般文字 (分成數頁)：</span><span class="sxs-lookup"><span data-stu-id="8fa0c-108">For example, if you use the **Out-Host** cmdlet to force a page-by-page display of output from another command, the output looks just like the normal text displayed on the screen, broken up into pages:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS\System32 | Out-Host -Paging

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\system32

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2005-10-22  11:04 PM        315 $winnt$.inf
-a---        2004-08-04   8:00 AM      68608 access.cpl
-a---        2004-08-04   8:00 AM      64512 acctres.dll
-a---        2004-08-04   8:00 AM     183808 accwiz.exe
-a---        2004-08-04   8:00 AM      61952 acelpdec.ax
-a---        2004-08-04   8:00 AM     129536 acledit.dll
-a---        2004-08-04   8:00 AM     114688 aclui.dll
-a---        2004-08-04   8:00 AM     194048 activeds.dll
-a---        2004-08-04   8:00 AM     111104 activeds.tlb
-a---        2004-08-04   8:00 AM       4096 actmovie.exe
-a---        2004-08-04   8:00 AM     101888 actxprxy.dll
-a---        2003-02-21   6:50 PM     143150 admgmt.msc
-a---        2006-01-25   3:35 PM      53760 admparse.dll
<SPACE> next page; <CR> next line; Q quit
...
```

<span data-ttu-id="8fa0c-109">只要有想要慢慢顯示的冗長輸出，Out-Host -Paging 命令就是有用的管線元素。</span><span class="sxs-lookup"><span data-stu-id="8fa0c-109">The Out-Host -Paging command is a useful pipeline element whenever you have lengthy output that you would like to display slowly.</span></span> <span data-ttu-id="8fa0c-110">它特別適用於 CPU 作業十分密集時。</span><span class="sxs-lookup"><span data-stu-id="8fa0c-110">It is especially useful if the operation is very CPU-intensive.</span></span> <span data-ttu-id="8fa0c-111">因為有準備好顯示的完整頁面時會將處理傳送給 Out-Host Cmdlet，所以在下一個輸出頁面可用之前，管線中前面的 Cmdlet 會停止作業。</span><span class="sxs-lookup"><span data-stu-id="8fa0c-111">Because processing is transferred to the Out-Host cmdlet when it has a complete page ready to display, cmdlets that precede it in the pipeline halt operation until the next page of output is available.</span></span> <span data-ttu-id="8fa0c-112">如果您使用 Windows 工作管理員來監視 Windows PowerShell 所使用的 CPU 和記憶體，就可以看到這種狀況。</span><span class="sxs-lookup"><span data-stu-id="8fa0c-112">You can see this if you use the Windows Task Manager to monitor CPU and memory use by Windows PowerShell.</span></span>

<span data-ttu-id="8fa0c-113">請執行下列命令︰**Get-ChildItem C:\\Windows -Recurse**。</span><span class="sxs-lookup"><span data-stu-id="8fa0c-113">Run the following command: **Get-ChildItem C:\\Windows -Recurse**.</span></span> <span data-ttu-id="8fa0c-114">比較與這個命令的 CPU 和記憶體使用量︰**Get-ChildItem C:\\Windows -Recurse | Out-Host -Paging**。</span><span class="sxs-lookup"><span data-stu-id="8fa0c-114">Compare the CPU and memory usage to this command: **Get-ChildItem C:\\Windows -Recurse | Out-Host -Paging**.</span></span> <span data-ttu-id="8fa0c-115">您在畫面上看到的是文字，但這是因為在主控台視窗中必須將物件呈現為文字。</span><span class="sxs-lookup"><span data-stu-id="8fa0c-115">What you see on the screen is text, but that is because it is necessary to represent objects as text in a console window.</span></span> <span data-ttu-id="8fa0c-116">這只是 Windows PowerShell 內實際進行之作業的呈現。</span><span class="sxs-lookup"><span data-stu-id="8fa0c-116">This is just a representation of what is really going on inside Windows PowerShell.</span></span> <span data-ttu-id="8fa0c-117">例如，請考慮使用 Get-Location Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8fa0c-117">For example, consider the Get-Location cmdlet.</span></span> <span data-ttu-id="8fa0c-118">如果您在目前位置是 C 磁碟機的根目錄時輸入 **Get-Location**，則會看到下列輸出︰</span><span class="sxs-lookup"><span data-stu-id="8fa0c-118">If you type **Get-Location** while your current location is the root of the C drive, you would see the following output:</span></span>

```
PS> Get-Location

Path
----
C:\
```

<span data-ttu-id="8fa0c-119">如果 Windows PowerShell 已傳送文字，則發出 **Get-Location | Out-Host** 這類命令會將一組字元依其在畫面上的顯示順序從 **Get-Location** 傳遞到 **Out-Host**。</span><span class="sxs-lookup"><span data-stu-id="8fa0c-119">If Windows PowerShell pipelined text, issuing a command such as **Get-Location | Out-Host**, would pass from **Get-Location** to **Out-Host** a set of characters in the order they are displayed onscreen.</span></span> <span data-ttu-id="8fa0c-120">換句話說，如果您要忽略標題資訊，則 **Out-Host** 會依序接收到下列字元：'**C'**、'**:'** 和 '**\\'**。</span><span class="sxs-lookup"><span data-stu-id="8fa0c-120">In other words, if you were to ignore the heading information, **Out-Host** would first receive the character '**C'**, then the character '**:'**, then the character '**\\'**.</span></span> <span data-ttu-id="8fa0c-121">**Out-Host** Cmdlet 無法判斷與 **Get-Location** Cmdlet 的字元輸出相關聯的意義。</span><span class="sxs-lookup"><span data-stu-id="8fa0c-121">The **Out-Host** cmdlet could not determine what meaning to associate with the characters output by the **Get-Location** cmdlet.</span></span>

<span data-ttu-id="8fa0c-122">Windows PowerShell 會使用物件，而不是使用文字讓管線中的命令進行通訊。</span><span class="sxs-lookup"><span data-stu-id="8fa0c-122">Instead of using text to let commands in a pipeline communicate, Windows PowerShell uses objects.</span></span> <span data-ttu-id="8fa0c-123">從使用者的觀點來看，物件會將相關資訊封裝成容易將資訊當成一個單元操作的表單，以及擷取您需要的特定項目。</span><span class="sxs-lookup"><span data-stu-id="8fa0c-123">From the standpoint of a user, objects package related information into a form that makes it easier to manipulate the information as a unit, and extract specific items that you need.</span></span>

<span data-ttu-id="8fa0c-124">**Get-Location** 命令不會傳回包含目前路徑的文字。</span><span class="sxs-lookup"><span data-stu-id="8fa0c-124">The **Get-Location** command does not return text that contains the current path.</span></span> <span data-ttu-id="8fa0c-125">它會傳回稱為 **PathInfo** 物件的資訊套件，這個物件包含目前路徑與一些其他資訊。</span><span class="sxs-lookup"><span data-stu-id="8fa0c-125">It returns a package of information called a **PathInfo** object that contains the current path along with some other information.</span></span> <span data-ttu-id="8fa0c-126">**Out-Host** Cmdlet 接著會將此 **PathInfo** 物件傳送到畫面，而 Windows PowerShell 會根據格式規則來決定要顯示的資訊和其顯示方式。</span><span class="sxs-lookup"><span data-stu-id="8fa0c-126">The **Out-Host** cmdlet then sends this **PathInfo** object to the screen, and Windows PowerShell decides what information to display and how to display it based on its formatting rules.</span></span>

<span data-ttu-id="8fa0c-127">事實上，**Get-Location** Cmdlet 的標題資訊輸出只會新增在處理程序結尾，作為格式化畫面顯示資料之處理程序的一部分。</span><span class="sxs-lookup"><span data-stu-id="8fa0c-127">In fact, the heading information output by the **Get-Location** cmdlet is added only at the end of the process, as part of the process of formatting the data for onscreen display.</span></span> <span data-ttu-id="8fa0c-128">您在畫面上看到的內容是資訊摘要，並不是輸出物件的完整呈現。</span><span class="sxs-lookup"><span data-stu-id="8fa0c-128">What you see onscreen is a summary of information, and not a complete representation of the output object.</span></span>

<span data-ttu-id="8fa0c-129">如果 Windows PowerShell 命令的資訊輸出多於我們在主控台視窗中看到的顯示內容，則如何擷取看不到的元素？</span><span class="sxs-lookup"><span data-stu-id="8fa0c-129">Given that there may be more information output from a Windows PowerShell command than what we see displayed in the console window, how can you retrieve the non-visible elements?</span></span> <span data-ttu-id="8fa0c-130">如何檢視額外資料？</span><span class="sxs-lookup"><span data-stu-id="8fa0c-130">How do you view the extra data?</span></span> <span data-ttu-id="8fa0c-131">如果您要使用不同於 Windows PowerShell 一般使用格式的格式來檢視資料，要怎麼做？</span><span class="sxs-lookup"><span data-stu-id="8fa0c-131">And what if you want to view the data in a format different than the one Windows PowerShell normally uses?</span></span>

<span data-ttu-id="8fa0c-132">本章的其餘部分將討論如何選取特定項目並對其格式化以更輕鬆地顯示來探索特定 Windows PowerShell 物件的結構，以及如何將此資訊傳送至替代輸出位置 (例如檔案和印表機)。</span><span class="sxs-lookup"><span data-stu-id="8fa0c-132">The rest of this chapter discusses how you can discover the structure of specific Windows PowerShell objects, selecting specific items and formatting them for easier display, and how to send this information to alternative output locations such as files and printers.</span></span>