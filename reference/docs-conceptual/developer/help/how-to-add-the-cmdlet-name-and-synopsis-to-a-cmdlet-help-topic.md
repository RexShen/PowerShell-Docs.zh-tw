---
ms.date: 09/13/2016
ms.topic: reference
title: 如何新增 Cmdlet 名稱和概要至 Cmdlet 說明主題
description: 如何新增 Cmdlet 名稱和概要至 Cmdlet 說明主題
ms.openlocfilehash: aeeb0cdd1d6d17b88067928ff952dc57a9441917
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659059"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a><span data-ttu-id="b2dba-103">如何新增 Cmdlet 名稱和概要至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="b2dba-103">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>

<span data-ttu-id="b2dba-104">本節說明如何新增在 Cmdlet 說明的 **名稱** 和 **概要** 區段中顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="b2dba-104">This section describes how to add content that is displayed in the **NAME** and **SYNOPSIS** sections of the cmdlet help.</span></span> <span data-ttu-id="b2dba-105">在說明檔中，此內容會新增至每個 Cmdlet 的命令節點。</span><span class="sxs-lookup"><span data-stu-id="b2dba-105">In the Help file, this content is added to the Command node for each cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="b2dba-106">如需說明檔的完整觀點，請開啟 `dll-Help.xml` 位於 PowerShell 安裝目錄中的其中一個檔案。</span><span class="sxs-lookup"><span data-stu-id="b2dba-106">For a complete view of a Help file, open one of the `dll-Help.xml` files located in the PowerShell installation directory.</span></span> <span data-ttu-id="b2dba-107">例如，檔案 `Microsoft.PowerShell.Commands.Management.dll-Help.xml` 包含數個 PowerShell Cmdlet 的內容。</span><span class="sxs-lookup"><span data-stu-id="b2dba-107">For example, the `Microsoft.PowerShell.Commands.Management.dll-Help.xml` file contains content for several of the PowerShell cmdlets.</span></span>

## <a name="to-add-the-cmdlet-name-and-a-synopsis"></a><span data-ttu-id="b2dba-108">新增 Cmdlet 名稱和概要</span><span class="sxs-lookup"><span data-stu-id="b2dba-108">To Add the Cmdlet Name and a Synopsis</span></span>

- <span data-ttu-id="b2dba-109">Cmdlet 說明可以顯示指令程式的兩個描述。</span><span class="sxs-lookup"><span data-stu-id="b2dba-109">The cmdlet Help can display two descriptions for the cmdlet.</span></span> <span data-ttu-id="b2dba-110">第一個描述是簡短描述，稱為「摘要」。</span><span class="sxs-lookup"><span data-stu-id="b2dba-110">The first description is a short description that is referred to as the synopsis.</span></span> <span data-ttu-id="b2dba-111">第二個描述是更詳細的描述，會在 [將詳細描述新增至 Cmdlet 說明主題](./how-to-add-a-cmdlet-description.md)中討論。</span><span class="sxs-lookup"><span data-stu-id="b2dba-111">The second description is a more detailed description that is discussed in [Adding the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span>
  <span data-ttu-id="b2dba-112">這兩個描述應該撰寫成單一段落。</span><span class="sxs-lookup"><span data-stu-id="b2dba-112">Both these descriptions should be written as a single paragraph.</span></span>

- <span data-ttu-id="b2dba-113">在概要中，不會重複 Cmdlet 名稱。</span><span class="sxs-lookup"><span data-stu-id="b2dba-113">In the synopsis do not repeat the cmdlet name.</span></span> <span data-ttu-id="b2dba-114">通知使用者 `Get-Server` Cmdlet 取得伺服器是短暫的，但無法提供資訊。</span><span class="sxs-lookup"><span data-stu-id="b2dba-114">Informing the user that the `Get-Server` cmdlet gets a server is brief, but not informative.</span></span> <span data-ttu-id="b2dba-115">相反地，請使用同義字並將詳細資料新增至描述。</span><span class="sxs-lookup"><span data-stu-id="b2dba-115">Instead, use synonyms and add details to the description.</span></span>

  <span data-ttu-id="b2dba-116">範例：「取得代表本機或遠端電腦的物件」。</span><span class="sxs-lookup"><span data-stu-id="b2dba-116">Example: "Gets an object that represents a local or remote computer."</span></span>

- <span data-ttu-id="b2dba-117">使用簡單的動詞命令，例如 "get"、"create" 和 "change" （在摘要中）。</span><span class="sxs-lookup"><span data-stu-id="b2dba-117">Use simple verbs like "get", "create", and "change" in the synopsis.</span></span> <span data-ttu-id="b2dba-118">請避免使用「設定」，因為它是模糊的，而像是「修改」的單字。</span><span class="sxs-lookup"><span data-stu-id="b2dba-118">Avoid using "set" because it is vague, and fancy words such as "modify."</span></span>

  <span data-ttu-id="b2dba-119">範例：「取得檔案中 Authenticode 簽章的相關資訊」。</span><span class="sxs-lookup"><span data-stu-id="b2dba-119">Example: "Gets information about the Authenticode signature in a file."</span></span>

- <span data-ttu-id="b2dba-120">以主動語音撰寫。</span><span class="sxs-lookup"><span data-stu-id="b2dba-120">Write in active voice.</span></span> <span data-ttu-id="b2dba-121">例如，「使用 TimeSpan 物件 ...」比「可以使用 TimeSpan 物件 ...」更清楚</span><span class="sxs-lookup"><span data-stu-id="b2dba-121">For example, "Use the TimeSpan object..." is much clearer than "the TimeSpan object can be used to..."</span></span>

- <span data-ttu-id="b2dba-122">描述取得物件的 Cmdlet 時，請避免動詞 "display"。</span><span class="sxs-lookup"><span data-stu-id="b2dba-122">Avoid the verb "display" when describing cmdlets that get objects.</span></span> <span data-ttu-id="b2dba-123">雖然 Windows PowerShell 會顯示 Cmdlet 資料，但請務必為使用者介紹 Cmdlet 所傳回的概念，.NET Framework 可能不會顯示其資料的物件。</span><span class="sxs-lookup"><span data-stu-id="b2dba-123">Although Windows PowerShell displays cmdlet data, it is important to introduce users to the concept that the cmdlet returns .NET Framework objects whose data may not be displayed.</span></span> <span data-ttu-id="b2dba-124">如果您強調顯示，使用者可能不知道 Cmdlet 可能傳回許多其他有用的屬性和不會顯示的方法。</span><span class="sxs-lookup"><span data-stu-id="b2dba-124">If you emphasize the display, the user might not realize that the cmdlet may have returned many other useful properties and methods that are not displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="b2dba-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2dba-125">See Also</span></span>

[<span data-ttu-id="b2dba-126">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="b2dba-126">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
