---
title: 如何新增 Cmdlet 描述 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47af9d57-bd63-4596-816a-0b717418476b
caps.latest.revision: 10
ms.openlocfilehash: a2e4c4d42566d5a52006924eab02295c37cf3159
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361277"
---
# <a name="how-to-add-a-cmdlet-description"></a><span data-ttu-id="d400a-102">如何新增 Cmdlet 描述</span><span class="sxs-lookup"><span data-stu-id="d400a-102">How to Add a Cmdlet Description</span></span>

<span data-ttu-id="d400a-103">本節說明如何新增在 Cmdlet 說明的 [描述] 部分中顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="d400a-103">This section describes how to add content that is displayed in the DESCRIPTION section of the cmdlet Help.</span></span> <span data-ttu-id="d400a-104">在說明檔中，此內容會新增至每個 Cmdlet 的命令節點。</span><span class="sxs-lookup"><span data-stu-id="d400a-104">In the Help file, this content is added to the Command node for each cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="d400a-105">如需說明檔的完整視圖，請開啟位於 Windows PowerShell 安裝目錄中的其中一個 dll-Help 檔案。</span><span class="sxs-lookup"><span data-stu-id="d400a-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="d400a-106">例如，dll-Help 檔案包含數個 Windows PowerShell 指令程式的內容（content）。</span><span class="sxs-lookup"><span data-stu-id="d400a-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-a-description"></a><span data-ttu-id="d400a-107">若要加入描述</span><span class="sxs-lookup"><span data-stu-id="d400a-107">To Add a Description</span></span>

- <span data-ttu-id="d400a-108">一開始會更詳細地說明 Cmdlet 的基本功能。</span><span class="sxs-lookup"><span data-stu-id="d400a-108">Begin by explaining the basic features of the cmdlet in more detail.</span></span> <span data-ttu-id="d400a-109">在許多情況下，您可以說明 Cmdlet 名稱中使用的詞彙，並以範例說明不熟悉的概念。</span><span class="sxs-lookup"><span data-stu-id="d400a-109">In many cases, you can explain the terms used in the cmdlet name and illustrate unfamiliar concepts with an example.</span></span> <span data-ttu-id="d400a-110">例如，如果 Cmdlet 將資料附加至檔案，則會說明它會將資料新增至現有檔案的結尾。</span><span class="sxs-lookup"><span data-stu-id="d400a-110">For example, if the cmdlet appends data to a file, explain that it adds data to the end of an existing file.</span></span>

- <span data-ttu-id="d400a-111">若要尋找 Cmdlet 的所有功能，請查看參數清單。</span><span class="sxs-lookup"><span data-stu-id="d400a-111">To find all of the features of the cmdlet, review the parameter list.</span></span> <span data-ttu-id="d400a-112">描述 Cmdlet 的主要功能，然後包含其他功能和功能。</span><span class="sxs-lookup"><span data-stu-id="d400a-112">Describe the primary function of the cmdlet, and then include other functions and features.</span></span> <span data-ttu-id="d400a-113">例如，如果 Cmdlet 的 main 函式是要變更一個屬性，但 Cmdlet 可以變更所有屬性，在詳細的描述中就是如此。</span><span class="sxs-lookup"><span data-stu-id="d400a-113">For example, if the main function of the cmdlet is to change one property, but the cmdlet can change all of the properties, say so in the detailed description.</span></span> <span data-ttu-id="d400a-114">如果 Cmdlet 參數讓使用者以不同的方式來請求資訊，請加以說明。</span><span class="sxs-lookup"><span data-stu-id="d400a-114">If the cmdlet parameters let the users solicit information in different ways, explain it.</span></span>

- <span data-ttu-id="d400a-115">除了明顯的用法以外，還包括使用者可以使用 Cmdlet 的方式資訊。</span><span class="sxs-lookup"><span data-stu-id="d400a-115">Include information on ways that users can use the cmdlet, in addition to the obvious uses.</span></span> <span data-ttu-id="d400a-116">例如，您可以使用 `Get-Host` Cmdlet 抓取的物件，在 Windows PowerShell 命令視窗中變更文字的色彩。</span><span class="sxs-lookup"><span data-stu-id="d400a-116">For example, you can use the object that the `Get-Host` cmdlet retrieves to change the color of text in the Windows PowerShell command window.</span></span>

  <span data-ttu-id="d400a-117">範例：「`Get-Acl` Cmdlet 會取得代表檔案或資源之安全描述項的物件。</span><span class="sxs-lookup"><span data-stu-id="d400a-117">Example:  "The `Get-Acl` cmdlet gets objects that represent the security descriptor of a file or resource.</span></span> <span data-ttu-id="d400a-118">安全性描述元包含資源的存取控制清單 (ACL)。</span><span class="sxs-lookup"><span data-stu-id="d400a-118">The security descriptor contains the access control lists (ACLs) of the resource.</span></span> <span data-ttu-id="d400a-119">ACL 會指定使用者和使用者群組存取資源所需的許可權。</span><span class="sxs-lookup"><span data-stu-id="d400a-119">The ACL specifies the permissions that users and user groups have to access the resource."</span></span>

- <span data-ttu-id="d400a-120">詳細描述應描述 Cmdlet，但不應描述 Cmdlet 所使用的概念。</span><span class="sxs-lookup"><span data-stu-id="d400a-120">The detailed description should describe the cmdlet, but it should not describe concepts that the cmdlet uses.</span></span> <span data-ttu-id="d400a-121">將概念定義放在其他筆記中。</span><span class="sxs-lookup"><span data-stu-id="d400a-121">Place concept definitions in Additional Notes.</span></span>

## <a name="see-also"></a><span data-ttu-id="d400a-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d400a-122">See Also</span></span>

[<span data-ttu-id="d400a-123">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="d400a-123">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
