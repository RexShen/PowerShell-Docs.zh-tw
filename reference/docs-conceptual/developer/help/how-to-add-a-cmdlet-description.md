---
ms.date: 09/13/2016
ms.topic: reference
title: 如何新增 Cmdlet 描述
description: 如何新增 Cmdlet 描述
ms.openlocfilehash: 08d21a281881678423bbe3c382279875ed2868db
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651218"
---
# <a name="how-to-add-a-cmdlet-description"></a><span data-ttu-id="c5362-103">如何新增 Cmdlet 描述</span><span class="sxs-lookup"><span data-stu-id="c5362-103">How to Add a Cmdlet Description</span></span>

<span data-ttu-id="c5362-104">本節說明如何新增在 Cmdlet 說明的 [ **描述** ] 部分中顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="c5362-104">This section describes how to add content that is displayed in the **DESCRIPTION** section of the cmdlet Help.</span></span> <span data-ttu-id="c5362-105">在說明檔中，此內容會新增至每個 Cmdlet 的 **命令** 節點。</span><span class="sxs-lookup"><span data-stu-id="c5362-105">In the Help file, this content is added to the **Command** node for each cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="c5362-106">如需說明檔的完整觀點，請開啟 `dll-Help.xml` 位於 PowerShell 安裝目錄中的其中一個檔案。</span><span class="sxs-lookup"><span data-stu-id="c5362-106">For a complete view of a Help file, open one of the `dll-Help.xml` files located in the PowerShell installation directory.</span></span> <span data-ttu-id="c5362-107">例如，檔案 `Microsoft.PowerShell.Commands.Management.dll-Help.xml` 包含數個 PowerShell Cmdlet 的內容。</span><span class="sxs-lookup"><span data-stu-id="c5362-107">For example, the `Microsoft.PowerShell.Commands.Management.dll-Help.xml` file contains content for several of the PowerShell cmdlets.</span></span>

### <a name="to-add-a-description"></a><span data-ttu-id="c5362-108">若要加入描述</span><span class="sxs-lookup"><span data-stu-id="c5362-108">To Add a Description</span></span>

- <span data-ttu-id="c5362-109">一開始會更詳細地說明 Cmdlet 的基本功能。</span><span class="sxs-lookup"><span data-stu-id="c5362-109">Begin by explaining the basic features of the cmdlet in more detail.</span></span> <span data-ttu-id="c5362-110">在許多情況下，您可以說明 Cmdlet 名稱中所使用的詞彙，並使用範例來說明不熟悉的概念。</span><span class="sxs-lookup"><span data-stu-id="c5362-110">In many cases, you can explain the terms used in the cmdlet name and illustrate unfamiliar concepts with an example.</span></span> <span data-ttu-id="c5362-111">例如，如果 Cmdlet 將資料附加至檔案，則說明它會將資料新增至現有檔案的結尾。</span><span class="sxs-lookup"><span data-stu-id="c5362-111">For example, if the cmdlet appends data to a file, explain that it adds data to the end of an existing file.</span></span>

- <span data-ttu-id="c5362-112">若要尋找 Cmdlet 的所有功能，請檢查參數清單。</span><span class="sxs-lookup"><span data-stu-id="c5362-112">To find all of the features of the cmdlet, review the parameter list.</span></span> <span data-ttu-id="c5362-113">描述 Cmdlet 的主要功能，然後包含其他功能和功能。</span><span class="sxs-lookup"><span data-stu-id="c5362-113">Describe the primary function of the cmdlet, and then include other functions and features.</span></span> <span data-ttu-id="c5362-114">例如，如果 Cmdlet 的 main 函式是變更一個屬性，則 Cmdlet 可以變更所有屬性，例如在詳細的描述中。</span><span class="sxs-lookup"><span data-stu-id="c5362-114">For example, if the main function of the cmdlet is to change one property, but the cmdlet can change all of the properties, say so in the detailed description.</span></span> <span data-ttu-id="c5362-115">如果 Cmdlet 參數讓使用者以不同的方式來請求資訊，請加以說明。</span><span class="sxs-lookup"><span data-stu-id="c5362-115">If the cmdlet parameters let the users solicit information in different ways, explain it.</span></span>

- <span data-ttu-id="c5362-116">除了明顯的用途之外，還包含使用者可以使用 Cmdlet 的方法資訊。</span><span class="sxs-lookup"><span data-stu-id="c5362-116">Include information on ways that users can use the cmdlet, in addition to the obvious uses.</span></span> <span data-ttu-id="c5362-117">例如，您可以使用 Cmdlet 抓取的物件 `Get-Host` 來變更 Windows PowerShell 命令視窗中的文字色彩。</span><span class="sxs-lookup"><span data-stu-id="c5362-117">For example, you can use the object that the `Get-Host` cmdlet retrieves to change the color of text in the Windows PowerShell command window.</span></span>

  <span data-ttu-id="c5362-118">範例：「 `Get-Acl` Cmdlet 會取得物件，以代表檔案或資源的安全描述項。</span><span class="sxs-lookup"><span data-stu-id="c5362-118">Example: "The `Get-Acl` cmdlet gets objects that represent the security descriptor of a file or resource.</span></span> <span data-ttu-id="c5362-119">安全性描述元包含資源的存取控制清單 (ACL)。</span><span class="sxs-lookup"><span data-stu-id="c5362-119">The security descriptor contains the access control lists (ACLs) of the resource.</span></span> <span data-ttu-id="c5362-120">ACL 會指定使用者和使用者群組存取資源所需的許可權。</span><span class="sxs-lookup"><span data-stu-id="c5362-120">The ACL specifies the permissions that users and user groups have to access the resource."</span></span>

- <span data-ttu-id="c5362-121">詳細描述應該描述 Cmdlet，但不應該描述 Cmdlet 所使用的概念。</span><span class="sxs-lookup"><span data-stu-id="c5362-121">The detailed description should describe the cmdlet, but it should not describe concepts that the cmdlet uses.</span></span> <span data-ttu-id="c5362-122">將概念定義放在其他附注中。</span><span class="sxs-lookup"><span data-stu-id="c5362-122">Place concept definitions in Additional Notes.</span></span>

## <a name="see-also"></a><span data-ttu-id="c5362-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5362-123">See Also</span></span>

[<span data-ttu-id="c5362-124">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="c5362-124">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
