---
title: 將 Windows PowerShell 活動新增至 Visual Studio 工具箱 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c8ef289-0659-42d1-9976-044b144201eb
caps.latest.revision: 6
ms.openlocfilehash: 2a8372d937fc3c959f7d829bb52495048423d506
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359647"
---
# <a name="adding-windows-powershell-activities-to-the-visual-studio-toolbox"></a><span data-ttu-id="d689d-102">新增 Windows PowerShell 活動至 Visual Studio 工具箱</span><span class="sxs-lookup"><span data-stu-id="d689d-102">Adding Windows PowerShell Activities to the Visual Studio Toolbox</span></span>

<span data-ttu-id="d689d-103">使用工作流程設計工具撰寫 PowerShell 工作流程之前，您必須先將 PowerShell 活動新增至 Visual Studio 工作流程主控台應用程式專案中的 [工具箱]。</span><span class="sxs-lookup"><span data-stu-id="d689d-103">Before you author a PowerShell Workflow using Workflow Designer, you must first add the PowerShell Activities to the Toolbox in a Visual Studio Workflow console application project.</span></span> <span data-ttu-id="d689d-104">下列程式顯示如何將活動從 [Microsoft] [...] 元件新增至 [Visual Studio 工具箱]。</span><span class="sxs-lookup"><span data-stu-id="d689d-104">The following procedure shows how to add the activities from the Microsoft.PowerShell.Core.Activities assembly to the Visual Studio toolbox.</span></span>

### <a name="adding-windows-powershell-activities-to-the-toolbox"></a><span data-ttu-id="d689d-105">將 Windows PowerShell 活動新增至工具箱</span><span class="sxs-lookup"><span data-stu-id="d689d-105">Adding Windows PowerShell Activities to the Toolbox</span></span>

1. <span data-ttu-id="d689d-106">在 Visual Studio 中建立新的工作流程主控台應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="d689d-106">Create a new Workflow console application project in Visual Studio.</span></span>

2. <span data-ttu-id="d689d-107">在 [ **View** ] 功能表上，按一下 [**工具箱**]。</span><span class="sxs-lookup"><span data-stu-id="d689d-107">On the **View** menu, click **Toolbox**.</span></span>

3. <span data-ttu-id="d689d-108">在 [工具箱] 中按一下滑鼠右鍵，然後按一下 [加入索引標籤 **]** ，在 [工具箱] 中加入新的索引標籤，然後為新的索引標籤命名，例如「PowerShell 活動」。</span><span class="sxs-lookup"><span data-stu-id="d689d-108">Add a new tab in the Toolbox by right-clicking inside the Toolbox and clicking **Add Tab**, and give the new tab a name such as "PowerShell Activities".</span></span>

   <span data-ttu-id="d689d-109">新增索引標籤可讓您將 PowerShell 活動與 [工具箱] 中的其他工具分開分組。</span><span class="sxs-lookup"><span data-stu-id="d689d-109">Adding a tab allows you to group the PowerShell Activities separate from other tools in the Toolbox.</span></span>

4. <span data-ttu-id="d689d-110">在 [新增工具箱] 索引標籤上，按一下 **[選擇專案**]。[**選擇工具箱專案**] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="d689d-110">On the new Toolbox tab, click **Choose Items...**. The **Choose Toolbox Items** dialog appears.</span></span>

5. <span data-ttu-id="d689d-111">在 [**選擇工具箱專案**] 對話方塊中，按一下 [**系統活動**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="d689d-111">In the **Choose Toolbox Items** dialog, click the **System.Activities** tab.</span></span>

6. <span data-ttu-id="d689d-112">按一下 **[流覽]** 。</span><span class="sxs-lookup"><span data-stu-id="d689d-112">Click **Browse**.</span></span>

7. <span data-ttu-id="d689d-113">流覽至 [%WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e] 資料夾，然後按兩下 [Microsoft]。</span><span class="sxs-lookup"><span data-stu-id="d689d-113">Navigate to the %WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e folder and double-click Microsoft.PowerShell.Core.Activities.dll.</span></span>

8. <span data-ttu-id="d689d-114">按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="d689d-114">Click **OK**.</span></span> <span data-ttu-id="d689d-115">在 [工具箱] 中，現在可以使用 [Microsoft] [活動] 元件所定義的活動。</span><span class="sxs-lookup"><span data-stu-id="d689d-115">The activities defined by the Microsoft.PowerShell.Core.Activities assembly are now available in the toolbox.</span></span>

## <a name="see-also"></a><span data-ttu-id="d689d-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d689d-116">See Also</span></span>

[<span data-ttu-id="d689d-117">撰寫 Windows PowerShell 工作流程</span><span class="sxs-lookup"><span data-stu-id="d689d-117">Writing a Windows PowerShell Workflow</span></span>](./writing-a-windows-powershell-workflow.md)

[<span data-ttu-id="d689d-118">使用 Windows PowerShell 活動建立工作流程</span><span class="sxs-lookup"><span data-stu-id="d689d-118">Creating a Workflow with Windows PowerShell Activities</span></span>](./creating-a-workflow-with-windows-powershell-activities.md)