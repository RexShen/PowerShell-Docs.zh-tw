---
title: 附錄 A - 說明語法
description: 本文說明如何閱讀和了解使用 Get-Help 所呈現的 Cmdlet 語法。
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: e8e28f66c02370b098f63a0396ef8a724cf3a1bd
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2020
ms.locfileid: "84437979"
---
# <a name="appendix-a---help-syntax"></a><span data-ttu-id="c5fb8-103">附錄 A - 說明語法</span><span class="sxs-lookup"><span data-stu-id="c5fb8-103">Appendix A - Help Syntax</span></span>

<span data-ttu-id="c5fb8-104">下列範例顯示 `Get-EventLog` Cmdlet 說明的 **SYNTAX** 區段。</span><span class="sxs-lookup"><span data-stu-id="c5fb8-104">The following example shows the **SYNTAX** section of the help for the `Get-EventLog` cmdlet.</span></span>

```powershell
help Get-EventLog
```

```Output
NAME
    Get-EventLog

SYNOPSIS
    Gets the events in an event log, or a list of the event logs, on the local or remote
    computers.


SYNTAX
    Get-EventLog [-LogName] <String> [[-InstanceId] <Int64[]>] [-After <DateTime>]
    [-AsBaseObject] [-Before <DateTime>] [-ComputerName <String[]>] [-EntryType {Error |
    Information | FailureAudit | SuccessAudit | Warning}] [-Index <Int32[]>] [-Message
    <String>] [-Newest <Int32>] [-Source <String[]>] [-UserName <String[]>]
    [<CommonParameters>]

    Get-EventLog [-AsString] [-ComputerName <String[]>] [-List] [<CommonParameters>]
```

<span data-ttu-id="c5fb8-105">此範例中只顯示說明的相關部分。</span><span class="sxs-lookup"><span data-stu-id="c5fb8-105">Only the relevant portion of the help is shown in this example.</span></span>

<span data-ttu-id="c5fb8-106">語法主要由數組左右方括弧 (`[]`) 組成。</span><span class="sxs-lookup"><span data-stu-id="c5fb8-106">The syntax is primarily made up of several sets of opening and closing brackets (`[]`).</span></span> <span data-ttu-id="c5fb8-107">根據其使用方式而定，會有兩個不同的意義。</span><span class="sxs-lookup"><span data-stu-id="c5fb8-107">These have two different meanings depending on how they're used.</span></span> <span data-ttu-id="c5fb8-108">包含在方括弧內的任何項目都是選擇性的，除非它們是一組空的方括弧 `[]`。</span><span class="sxs-lookup"><span data-stu-id="c5fb8-108">Anything contained within square brackets is optional unless they're a set of empty square brackets `[]`.</span></span> <span data-ttu-id="c5fb8-109">只有在 `<string[]>` 之類的資料類型之後，才會出現空的方括弧。</span><span class="sxs-lookup"><span data-stu-id="c5fb8-109">Empty square brackets only appear after a datatype such as `<string[]>`.</span></span> <span data-ttu-id="c5fb8-110">這表示特定參數可以接受一個以上該類型的值。</span><span class="sxs-lookup"><span data-stu-id="c5fb8-110">This means that particular parameter can accept more than one value of that type.</span></span>

<span data-ttu-id="c5fb8-111">`Get-EventLog` 的第一個參數集中的第一個參數是 **LogName**。</span><span class="sxs-lookup"><span data-stu-id="c5fb8-111">The first parameter in the first parameter set of `Get-EventLog` is **LogName**.</span></span> <span data-ttu-id="c5fb8-112">LogName 是用方括弧括住，這表示它是位置參數。</span><span class="sxs-lookup"><span data-stu-id="c5fb8-112">LogName is surrounded by square brackets which means that it's a positional parameter.</span></span> <span data-ttu-id="c5fb8-113">換句話說，只要已在正確的位置指定，那麼指定參數本身的名稱就會是選擇性。</span><span class="sxs-lookup"><span data-stu-id="c5fb8-113">In other words, specifying the name of the parameter itself is optional as long as it's specified in the correct position.</span></span> <span data-ttu-id="c5fb8-114">參數名稱後面角括弧 (`<>`) 中的資訊指出它需要單一**字串**值。</span><span class="sxs-lookup"><span data-stu-id="c5fb8-114">The information in the angle brackets (`<>`) after the parameter name indicates that it needs a single **string** value.</span></span> <span data-ttu-id="c5fb8-115">整個參數名稱和資料類型不會以方括弧括住，因此使用此參數集時，需要 **LogName** 參數。</span><span class="sxs-lookup"><span data-stu-id="c5fb8-115">The entire parameter name and datatype are not surrounded by square brackets so the **LogName** parameter is required when using this parameter set.</span></span>

```powershell
Get-EventLog [-LogName] <String>
```

<span data-ttu-id="c5fb8-116">第二個參數是 **InstanceId**。</span><span class="sxs-lookup"><span data-stu-id="c5fb8-116">The second parameter is **InstanceId**.</span></span> <span data-ttu-id="c5fb8-117">請注意，參數名稱和資料類型都完全以方括弧括住。</span><span class="sxs-lookup"><span data-stu-id="c5fb8-117">Notice that the parameter name and the datatype are both completely surrounded by square brackets.</span></span> <span data-ttu-id="c5fb8-118">這表示 **InstanceId** 參數是選擇性的，不是強制的。</span><span class="sxs-lookup"><span data-stu-id="c5fb8-118">This means that the **InstanceId** parameter is optional, not mandatory.</span></span> <span data-ttu-id="c5fb8-119">也請注意，**InstanceId** 是以自己的一組方括弧括住。</span><span class="sxs-lookup"><span data-stu-id="c5fb8-119">Also notice that **InstanceId** is surrounded by its own set of square brackets.</span></span> <span data-ttu-id="c5fb8-120">如同使用 **LogName** 參數，這表示參數具位置性。</span><span class="sxs-lookup"><span data-stu-id="c5fb8-120">As with the **LogName** parameter, this means the parameter is positional.</span></span> <span data-ttu-id="c5fb8-121">資料類型後面有最後的一組方括弧。</span><span class="sxs-lookup"><span data-stu-id="c5fb8-121">There's one last set of square brackets after the datatype.</span></span> <span data-ttu-id="c5fb8-122">這表示它可以接受陣列或逗號分隔清單格式的一個以上值。</span><span class="sxs-lookup"><span data-stu-id="c5fb8-122">This means that it can accept more than one value in the form of an array or a comma-separated list.</span></span>

```
[[-InstanceId] <Int64[]>]
```

<span data-ttu-id="c5fb8-123">第二個參數集具有 **List** 參數。</span><span class="sxs-lookup"><span data-stu-id="c5fb8-123">The second parameter set has a **List** parameter.</span></span> <span data-ttu-id="c5fb8-124">因為參數名稱後面沒有資料類型，所以它是切換參數。</span><span class="sxs-lookup"><span data-stu-id="c5fb8-124">It's a switch parameter because there's no datatype following the parameter name.</span></span> <span data-ttu-id="c5fb8-125">指定 **List** 參數時，此值為 **True**。</span><span class="sxs-lookup"><span data-stu-id="c5fb8-125">When the **List** parameter is specified, the value is **True**.</span></span> <span data-ttu-id="c5fb8-126">若未指定，則值為 **False**。</span><span class="sxs-lookup"><span data-stu-id="c5fb8-126">When it's not specified, the value is **False**.</span></span>

```
[-List]
```

<span data-ttu-id="c5fb8-127">您也可以使用 **Syntax** 參數，使用 `Get-Command` 來擷取命令的語法資訊。</span><span class="sxs-lookup"><span data-stu-id="c5fb8-127">The syntax information for a command can also be retrieved using `Get-Command` using the **Syntax** parameter.</span></span> <span data-ttu-id="c5fb8-128">這是我經常會使用的便利捷徑。</span><span class="sxs-lookup"><span data-stu-id="c5fb8-128">This is a handy shortcut that I use all the time.</span></span> <span data-ttu-id="c5fb8-129">它可讓我快速了解如何使用命令，而不需要篩檢多頁的說明資訊。</span><span class="sxs-lookup"><span data-stu-id="c5fb8-129">It allows me to quickly learn how to use a command without having to sift through multiple pages of help information.</span></span> <span data-ttu-id="c5fb8-130">如果最後需要更多資訊，我將會還原為使用實際的說明內容。</span><span class="sxs-lookup"><span data-stu-id="c5fb8-130">If I end up needing more information, then I'll revert to using the actual help content.</span></span>

```powershell
Get-Command -Name Get-EventLog -Syntax
```

```Output
Get-EventLog [-LogName] <string> [[-InstanceId] <long[]>] [-ComputerName <string[]>] [-Newest <int>]
 [-After <datetime>] [-Before <datetime>] [-UserName <string[]>] [-Index <int[]> ]
 [-EntryType <string[]>] [-Source <string[]>] [-Message <string>] [-AsBaseObject]
 [<CommonParameters>]

Get-EventLog [-ComputerName <string[]>] [-List] [-AsString] [<CommonParameters>]
```

<span data-ttu-id="c5fb8-131">您在 PowerShell 中使用說明系統的情況越多，就會更容易記住所有不同的細節。</span><span class="sxs-lookup"><span data-stu-id="c5fb8-131">The more you use the help system in PowerShell, the easier remembering all of the different nuances becomes.</span></span> <span data-ttu-id="c5fb8-132">當您發現時，使用它已變成您的第二個本質了。</span><span class="sxs-lookup"><span data-stu-id="c5fb8-132">Before you know it, using it becomes second nature.</span></span>
