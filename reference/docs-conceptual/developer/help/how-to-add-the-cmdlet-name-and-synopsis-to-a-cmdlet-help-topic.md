---
title: 如何新增 Cmdlet 名稱和概要至 Cmdlet 說明主題
ms.date: 09/13/2016
ms.openlocfilehash: 399defcb596ff9e9a596f4cd25ebcb6bcb7c34d2
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2020
ms.locfileid: "86892875"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a><span data-ttu-id="5f8d7-102">如何新增 Cmdlet 名稱和概要至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="5f8d7-102">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>

<span data-ttu-id="5f8d7-103">本節說明如何新增 [Cmdlet 說明] 的 [**名稱**] 和 [**概要**] 區段中所顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="5f8d7-103">This section describes how to add content that is displayed in the **NAME** and **SYNOPSIS** sections of the cmdlet help.</span></span> <span data-ttu-id="5f8d7-104">在說明檔中，此內容會新增至每個 Cmdlet 的命令節點。</span><span class="sxs-lookup"><span data-stu-id="5f8d7-104">In the Help file, this content is added to the Command node for each cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="5f8d7-105">如需說明檔的完整視圖，請開啟 `dll-Help.xml` 位於 PowerShell 安裝目錄中的其中一個檔案。</span><span class="sxs-lookup"><span data-stu-id="5f8d7-105">For a complete view of a Help file, open one of the `dll-Help.xml` files located in the PowerShell installation directory.</span></span> <span data-ttu-id="5f8d7-106">例如，檔案 `Microsoft.PowerShell.Commands.Management.dll-Help.xml` 包含數個 PowerShell Cmdlet 的內容。</span><span class="sxs-lookup"><span data-stu-id="5f8d7-106">For example, the `Microsoft.PowerShell.Commands.Management.dll-Help.xml` file contains content for several of the PowerShell cmdlets.</span></span>

## <a name="to-add-the-cmdlet-name-and-a-synopsis"></a><span data-ttu-id="5f8d7-107">新增 Cmdlet 名稱和概要</span><span class="sxs-lookup"><span data-stu-id="5f8d7-107">To Add the Cmdlet Name and a Synopsis</span></span>

- <span data-ttu-id="5f8d7-108">Cmdlet 說明可以顯示 Cmdlet 的兩個描述。</span><span class="sxs-lookup"><span data-stu-id="5f8d7-108">The cmdlet Help can display two descriptions for the cmdlet.</span></span> <span data-ttu-id="5f8d7-109">第一個描述是簡短的描述，稱為「摘要」。</span><span class="sxs-lookup"><span data-stu-id="5f8d7-109">The first description is a short description that is referred to as the synopsis.</span></span> <span data-ttu-id="5f8d7-110">第二個描述是更詳細的描述，會在[將詳細描述新增至 Cmdlet 說明主題](./how-to-add-a-cmdlet-description.md)中討論。</span><span class="sxs-lookup"><span data-stu-id="5f8d7-110">The second description is a more detailed description that is discussed in [Adding the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span>
  <span data-ttu-id="5f8d7-111">這兩個描述都應該寫成一個段落。</span><span class="sxs-lookup"><span data-stu-id="5f8d7-111">Both these descriptions should be written as a single paragraph.</span></span>

- <span data-ttu-id="5f8d7-112">在 [摘要] 中，請勿重複 Cmdlet 名稱。</span><span class="sxs-lookup"><span data-stu-id="5f8d7-112">In the synopsis do not repeat the cmdlet name.</span></span> <span data-ttu-id="5f8d7-113">通知使用者 `Get-Server` Cmdlet 取得伺服器是簡短的，但沒有資訊。</span><span class="sxs-lookup"><span data-stu-id="5f8d7-113">Informing the user that the `Get-Server` cmdlet gets a server is brief, but not informative.</span></span> <span data-ttu-id="5f8d7-114">請改用同義字，並將詳細資料加入至描述。</span><span class="sxs-lookup"><span data-stu-id="5f8d7-114">Instead, use synonyms and add details to the description.</span></span>

  <span data-ttu-id="5f8d7-115">範例：「取得代表本機或遠端電腦的物件」。</span><span class="sxs-lookup"><span data-stu-id="5f8d7-115">Example: "Gets an object that represents a local or remote computer."</span></span>

- <span data-ttu-id="5f8d7-116">在概要中使用簡單動詞，例如 "get"、"create" 和 "change"。</span><span class="sxs-lookup"><span data-stu-id="5f8d7-116">Use simple verbs like "get", "create", and "change" in the synopsis.</span></span> <span data-ttu-id="5f8d7-117">請避免使用「set」，因為它是不清楚的，而是「修改」之類的單字。</span><span class="sxs-lookup"><span data-stu-id="5f8d7-117">Avoid using "set" because it is vague, and fancy words such as "modify."</span></span>

  <span data-ttu-id="5f8d7-118">範例：「取得檔案中 Authenticode 簽章的相關資訊」。</span><span class="sxs-lookup"><span data-stu-id="5f8d7-118">Example: "Gets information about the Authenticode signature in a file."</span></span>

- <span data-ttu-id="5f8d7-119">以現用語音撰寫。</span><span class="sxs-lookup"><span data-stu-id="5f8d7-119">Write in active voice.</span></span> <span data-ttu-id="5f8d7-120">例如，「使用 TimeSpan 物件 ...」比「TimeSpan 物件可以用來 ...」更清楚</span><span class="sxs-lookup"><span data-stu-id="5f8d7-120">For example, "Use the TimeSpan object..." is much clearer than "the TimeSpan object can be used to..."</span></span>

- <span data-ttu-id="5f8d7-121">描述取得物件的 Cmdlet 時，請避免動詞「顯示」。</span><span class="sxs-lookup"><span data-stu-id="5f8d7-121">Avoid the verb "display" when describing cmdlets that get objects.</span></span> <span data-ttu-id="5f8d7-122">雖然 Windows PowerShell 會顯示指令程式資料，但請務必向使用者介紹此 Cmdlet 會傳回資料可能不會顯示 .NET Framework 物件的概念。</span><span class="sxs-lookup"><span data-stu-id="5f8d7-122">Although Windows PowerShell displays cmdlet data, it is important to introduce users to the concept that the cmdlet returns .NET Framework objects whose data may not be displayed.</span></span> <span data-ttu-id="5f8d7-123">如果您強調顯示，使用者可能不知道 Cmdlet 可能傳回許多其他有用的屬性和不會顯示的方法。</span><span class="sxs-lookup"><span data-stu-id="5f8d7-123">If you emphasize the display, the user might not realize that the cmdlet may have returned many other useful properties and methods that are not displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="5f8d7-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f8d7-124">See Also</span></span>

[<span data-ttu-id="5f8d7-125">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="5f8d7-125">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
