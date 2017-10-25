---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "排序物件"
ms.assetid: 8530caa8-3ed4-4c56-aed7-1295dd9ba199
ms.openlocfilehash: 2df45c64656e74dc8b72957ce59f2a5e5ee663b6
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2017
---
# <a name="sorting-objects"></a><span data-ttu-id="5bd9c-103">排序物件</span><span class="sxs-lookup"><span data-stu-id="5bd9c-103">Sorting Objects</span></span>
<span data-ttu-id="5bd9c-104">我們會組織顯示的資料，讓您可以使用 **Sort-Object** Cmdlet 更輕鬆地進行掃描。</span><span class="sxs-lookup"><span data-stu-id="5bd9c-104">We can organize displayed data to make it easier to scan by using the **Sort-Object** cmdlet.</span></span> <span data-ttu-id="5bd9c-105">**Sort-Object** 會使用一或多個屬性的名稱作為排序依據，並傳回根據這些屬性值進行排序的資料。</span><span class="sxs-lookup"><span data-stu-id="5bd9c-105">**Sort-Object** takes the name of one or more properties to sort on, and returns data sorted by the values of those properties.</span></span>

<span data-ttu-id="5bd9c-106">請考慮列出 Win32_SystemDriver 執行個體的問題。</span><span class="sxs-lookup"><span data-stu-id="5bd9c-106">Consider the problem of listing Win32_SystemDriver instances.</span></span> <span data-ttu-id="5bd9c-107">如果我們要依序根據 **State** 和 **Name** 來進行排序，則做法是輸入：</span><span class="sxs-lookup"><span data-stu-id="5bd9c-107">If we want to sort by **State** and then by **Name**, we can do it by typing:</span></span>

```
Get-WmiObject -Class Win32_SystemDriver | Sort-Object -Property State,Name | Format-Table -Property Name,State,Started,DisplayName -AutoSize -Wrap
```

<span data-ttu-id="5bd9c-108">雖然這會是冗長的顯示，但是您可以看到以相同狀態群組在一起的項目︰</span><span class="sxs-lookup"><span data-stu-id="5bd9c-108">Although this is a lengthy display, you can see items with the same state grouped together:</span></span>

```
Name           State   Started DisplayName
----           -----   ------- -----------
ACPI           Running    True Microsoft ACPI Driver
AFD            Running    True AFD
AmdK7          Running    True AMD K7 Processor Driver
AsyncMac       Running    True RAS Asynchronous Media Driver
...
Abiosdsk       Stopped   False Abiosdsk
ACPIEC         Stopped   False ACPIEC
aec            Stopped   False Microsoft Kernel Acoustic Echo Canceller
...
```

<span data-ttu-id="5bd9c-109">您也可以指定 **Descending** 參數，以相反順序來排序物件。</span><span class="sxs-lookup"><span data-stu-id="5bd9c-109">You can also sort the objects in reverse order by specifying the **Descending** parameter.</span></span> <span data-ttu-id="5bd9c-110">這會反轉排序順序，以反向字母順序排序名稱，並依遞減大小排序數字。</span><span class="sxs-lookup"><span data-stu-id="5bd9c-110">This reverses the sort order so that names are sorted in reverse alphabetical order and numbers are sorted by descending size.</span></span>

```
PS> Get-WmiObject -Class Win32_SystemDriver | Sort-Object -Property State,Name -Descending | Format-Table -Property Name,State,Started,DisplayName -AutoSize -Wrap

Name           State   Started DisplayName
----           -----   ------- -----------
WS2IFSL        Stopped   False Windows Socket 2.0 Non-IFS Service Provider Supp
                               ort Environment
wceusbsh       Stopped   False Windows CE USB Serial Host Driver...
...
wdmaud         Running    True Microsoft WINMM WDM Audio Compatibility Driver
Wanarp         Running    True Remote Access IP ARP Driver
...
```

