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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083513"
---
# <a name="how-to-add-a-cmdlet-description"></a><span data-ttu-id="3e602-102">如何新增 Cmdlet 描述</span><span class="sxs-lookup"><span data-stu-id="3e602-102">How to Add a Cmdlet Description</span></span>

<span data-ttu-id="3e602-103">本節說明如何新增會顯示在 [描述] 部分的 cmdlet 說明的內容。</span><span class="sxs-lookup"><span data-stu-id="3e602-103">This section describes how to add content that is displayed in the DESCRIPTION section of the cmdlet Help.</span></span> <span data-ttu-id="3e602-104">在說明檔案中，此內容會新增至每個 cmdlet 的命令節點。</span><span class="sxs-lookup"><span data-stu-id="3e602-104">In the Help file, this content is added to the Command node for each cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="3e602-105">說明檔案，開啟其中一個 dll Help.xml 檔案位於 Windows PowerShell 安裝目錄的完整檢視。</span><span class="sxs-lookup"><span data-stu-id="3e602-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="3e602-106">比方說，Microsoft.PowerShell.Commands.Management.dll Help.xml 檔案會包含內容的數個 Windows PowerShell cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3e602-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-a-description"></a><span data-ttu-id="3e602-107">若要加入描述</span><span class="sxs-lookup"><span data-stu-id="3e602-107">To Add a Description</span></span>

- <span data-ttu-id="3e602-108">開始說明更多詳細資料中的指令程式的基本功能。</span><span class="sxs-lookup"><span data-stu-id="3e602-108">Begin by explaining the basic features of the cmdlet in more detail.</span></span> <span data-ttu-id="3e602-109">在許多情況下，您可以說明 cmdlet 名稱中使用的詞彙，並說明使用的範例不熟悉的概念。</span><span class="sxs-lookup"><span data-stu-id="3e602-109">In many cases, you can explain the terms used in the cmdlet name and illustrate unfamiliar concepts with an example.</span></span> <span data-ttu-id="3e602-110">例如，如果此 cmdlet 會將資料附加至檔案，說明它將資料加入至現有檔案的結尾。</span><span class="sxs-lookup"><span data-stu-id="3e602-110">For example, if the cmdlet appends data to a file, explain that it adds data to the end of an existing file.</span></span>

- <span data-ttu-id="3e602-111">若要尋找所有 cmdlet 的功能，請檢閱參數清單。</span><span class="sxs-lookup"><span data-stu-id="3e602-111">To find all of the features of the cmdlet, review the parameter list.</span></span> <span data-ttu-id="3e602-112">描述主要功能的 cmdlet，則包含其他功能和特性。</span><span class="sxs-lookup"><span data-stu-id="3e602-112">Describe the primary function of the cmdlet, and then include other functions and features.</span></span> <span data-ttu-id="3e602-113">例如，如果此指令程式的主要功能是變更一個屬性，但 cmdlet 可以變更的所有屬性，說中詳細說明。</span><span class="sxs-lookup"><span data-stu-id="3e602-113">For example, if the main function of the cmdlet is to change one property, but the cmdlet can change all of the properties, say so in the detailed description.</span></span> <span data-ttu-id="3e602-114">如果 cmdlet 參數可讓使用者以不同的方式請求資訊，請將其說明。</span><span class="sxs-lookup"><span data-stu-id="3e602-114">If the cmdlet parameters let the users solicit information in different ways, explain it.</span></span>

- <span data-ttu-id="3e602-115">包含使用者可以使用 cmdlet，除了明顯的使用方式的資訊。</span><span class="sxs-lookup"><span data-stu-id="3e602-115">Include information on ways that users can use the cmdlet, in addition to the obvious uses.</span></span> <span data-ttu-id="3e602-116">例如，您可以使用物件，`Get-Host`指令程式會擷取變更的 Windows PowerShell 命令視窗中的文字色彩。</span><span class="sxs-lookup"><span data-stu-id="3e602-116">For example, you can use the object that the `Get-Host` cmdlet retrieves to change the color of text in the Windows PowerShell command window.</span></span>

  <span data-ttu-id="3e602-117">範例：「 `Get-Acl` Cmdlet 會取得代表檔案或資源的安全性描述元的物件。</span><span class="sxs-lookup"><span data-stu-id="3e602-117">Example:  "The `Get-Acl` cmdlet gets objects that represent the security descriptor of a file or resource.</span></span> <span data-ttu-id="3e602-118">安全性描述元包含資源的存取控制清單 (ACL)。</span><span class="sxs-lookup"><span data-stu-id="3e602-118">The security descriptor contains the access control lists (ACLs) of the resource.</span></span> <span data-ttu-id="3e602-119">ACL 會指定使用者和使用者群組具有存取資源的權限。 」</span><span class="sxs-lookup"><span data-stu-id="3e602-119">The ACL specifies the permissions that users and user groups have to access the resource."</span></span>

- <span data-ttu-id="3e602-120">詳細的描述應描述 cmdlet，但它應該描述此 cmdlet 會使用的概念。</span><span class="sxs-lookup"><span data-stu-id="3e602-120">The detailed description should describe the cmdlet, but it should not describe concepts that the cmdlet uses.</span></span> <span data-ttu-id="3e602-121">將概念定義放在其他注意事項。</span><span class="sxs-lookup"><span data-stu-id="3e602-121">Place concept definitions in Additional Notes.</span></span>

## <a name="see-also"></a><span data-ttu-id="3e602-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e602-122">See Also</span></span>

[<span data-ttu-id="3e602-123">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="3e602-123">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
