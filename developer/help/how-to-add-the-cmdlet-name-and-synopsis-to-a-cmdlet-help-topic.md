---
title: 如何將 Cmdlet 說明主題中的 Cmdlet 名稱和概要 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d0e1eb1-a962-4406-9625-175cfa3364ad
caps.latest.revision: 10
ms.openlocfilehash: f142548be473da15e702f4fa01835609d75b9d51
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861824"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a><span data-ttu-id="2e2e9-102">如何新增 Cmdlet 名稱和概要至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="2e2e9-102">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>

<span data-ttu-id="2e2e9-103">本節說明如何新增顯示名稱和概要區段中的 cmdlet 說明的內容。</span><span class="sxs-lookup"><span data-stu-id="2e2e9-103">This section describes how to add content that is displayed in the NAME and SYNOPSIS sections of the cmdlet help.</span></span> <span data-ttu-id="2e2e9-104">在說明檔案中，此內容會新增至每個 cmdlet 的命令節點。</span><span class="sxs-lookup"><span data-stu-id="2e2e9-104">In the Help file, this content is added to the Command node for each cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="2e2e9-105">說明檔案，開啟其中一個 dll Help.xml 檔案位於 Windows PowerShell 安裝目錄的完整檢視。</span><span class="sxs-lookup"><span data-stu-id="2e2e9-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="2e2e9-106">比方說，Microsoft.PowerShell.Commands.Management.dll Help.xml 檔案會包含內容的數個 Windows PowerShell cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2e2e9-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-the-cmdlet-name-and-a-synopsis"></a><span data-ttu-id="2e2e9-107">將指令程式的名稱和概要</span><span class="sxs-lookup"><span data-stu-id="2e2e9-107">To Add the Cmdlet Name and a Synopsis</span></span>

- <span data-ttu-id="2e2e9-108">Cmdlet 說明可以顯示兩個 cmdlet 的說明。</span><span class="sxs-lookup"><span data-stu-id="2e2e9-108">The cmdlet Help can display two descriptions for the cmdlet.</span></span> <span data-ttu-id="2e2e9-109">第一個描述是稱為 「 概要的簡短描述。</span><span class="sxs-lookup"><span data-stu-id="2e2e9-109">The first description is a short description that is referred to as the synopsis.</span></span> <span data-ttu-id="2e2e9-110">第二項描述會更詳細的描述中所討論[Cmdlet 說明主題將詳細說明](./how-to-add-a-cmdlet-description.md)。</span><span class="sxs-lookup"><span data-stu-id="2e2e9-110">The second description is a more detailed description that is discussed in [Adding the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span> <span data-ttu-id="2e2e9-111">這兩個這些描述應寫成單一的段落。</span><span class="sxs-lookup"><span data-stu-id="2e2e9-111">Both these descriptions should be written as a single paragraph.</span></span>

- <span data-ttu-id="2e2e9-112">在概要中不重複的 cmdlet 名稱。</span><span class="sxs-lookup"><span data-stu-id="2e2e9-112">In the synopsis do not repeat the cmdlet name.</span></span> <span data-ttu-id="2e2e9-113">通知使用者 Get-server cmdlet 會取得伺服器是簡短，但不是具有資訊價值。</span><span class="sxs-lookup"><span data-stu-id="2e2e9-113">Informing the user that the Get-Server cmdlet gets a server is brief, but not informative.</span></span> <span data-ttu-id="2e2e9-114">相反地，使用同義字，並新增至描述的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="2e2e9-114">Instead, use synonyms and add details to the description.</span></span>

  <span data-ttu-id="2e2e9-115">範例：「 取得物件，表示在本機或遠端電腦。 」</span><span class="sxs-lookup"><span data-stu-id="2e2e9-115">Example: "Gets an object that represents a local or remote computer."</span></span>

- <span data-ttu-id="2e2e9-116">使用簡單的動詞，例如 「 get 」、 「 建立 」 和 「 變更 」 中的概要。</span><span class="sxs-lookup"><span data-stu-id="2e2e9-116">Use simple verbs like "get", "create", and "change" in the synopsis.</span></span> <span data-ttu-id="2e2e9-117">請避免使用 「 設定 」 因為它是含糊不清，而且美觀的字這類 「 修改。 」</span><span class="sxs-lookup"><span data-stu-id="2e2e9-117">Avoid using "set" because it is vague, and fancy words such as "modify."</span></span>

  <span data-ttu-id="2e2e9-118">範例：「 檔案中取得 Authenticode 簽章的相關資訊。 」</span><span class="sxs-lookup"><span data-stu-id="2e2e9-118">Example: "Gets information about the Authenticode signature in a file."</span></span>

- <span data-ttu-id="2e2e9-119">主動語氣來撰寫。</span><span class="sxs-lookup"><span data-stu-id="2e2e9-119">Write in active voice.</span></span> <span data-ttu-id="2e2e9-120">例如，[使用 TimeSpan 物件...]要清楚得多比 「 TimeSpan 物件可用來...」</span><span class="sxs-lookup"><span data-stu-id="2e2e9-120">For example, "Use the TimeSpan object..." is much clearer than "the TimeSpan object can be used to..."</span></span>

- <span data-ttu-id="2e2e9-121">描述取得物件的 cmdlet 時，請避免動詞"display"。</span><span class="sxs-lookup"><span data-stu-id="2e2e9-121">Avoid the verb "display" when describing cmdlets that get objects.</span></span> <span data-ttu-id="2e2e9-122">雖然 Windows PowerShell 會顯示 cmdlet 的資料，務必為使用者介紹的概念，此 cmdlet 會傳回.NET Framework 物件可能不會顯示其資料。</span><span class="sxs-lookup"><span data-stu-id="2e2e9-122">Although Windows PowerShell displays cmdlet data, it is important to introduce users to the concept that the cmdlet returns .NET Framework objects whose data may not be displayed.</span></span> <span data-ttu-id="2e2e9-123">如果強調顯示時，使用者可能不知道此 cmdlet 可能會傳回許多其他有用的屬性和方法，不會顯示。</span><span class="sxs-lookup"><span data-stu-id="2e2e9-123">If you emphasize the display, the user might not realize that the cmdlet may have returned many other useful properties and methods that are not displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="2e2e9-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e2e9-124">See Also</span></span>

 [<span data-ttu-id="2e2e9-125">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="2e2e9-125">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)