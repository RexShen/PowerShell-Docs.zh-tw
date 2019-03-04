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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863564"
---
# <a name="adding-windows-powershell-activities-to-the-visual-studio-toolbox"></a><span data-ttu-id="3e203-102">新增 Windows PowerShell 活動至 Visual Studio 工具箱</span><span class="sxs-lookup"><span data-stu-id="3e203-102">Adding Windows PowerShell Activities to the Visual Studio Toolbox</span></span>

<span data-ttu-id="3e203-103">您撰寫使用工作流程設計工具的 PowerShell 工作流程之前，您必須先將 PowerShell 活動加入的工具箱中的 Visual Studio 工作流程主控台應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="3e203-103">Before you author a PowerShell Workflow using Workflow Designer, you must first add the PowerShell Activities to the Toolbox in a Visual Studio Workflow console application project.</span></span> <span data-ttu-id="3e203-104">下列程序示範如何從 Microsoft.PowerShell.Core.Activities 組件將活動加入至 Visual Studio 工具箱。</span><span class="sxs-lookup"><span data-stu-id="3e203-104">The following procedure shows how to add the activities from the Microsoft.PowerShell.Core.Activities assembly to the Visual Studio toolbox.</span></span>

### <a name="adding-windows-powershell-activities-to-the-toolbox"></a><span data-ttu-id="3e203-105">Windows PowerShell 活動新增至工具箱</span><span class="sxs-lookup"><span data-stu-id="3e203-105">Adding Windows PowerShell Activities to the Toolbox</span></span>

1. <span data-ttu-id="3e203-106">Visual Studio 中建立新的工作流程主控台應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="3e203-106">Create a new Workflow console application project in Visual Studio.</span></span>

2. <span data-ttu-id="3e203-107">在 **檢視**功能表上，按一下**工具箱**。</span><span class="sxs-lookup"><span data-stu-id="3e203-107">On the **View** menu, click **Toolbox**.</span></span>

3. <span data-ttu-id="3e203-108">在 [工具箱] 加入新的索引標籤，工具箱內部按一下滑鼠右鍵，然後按一下**加入索引標籤**，並提供新的索引標籤的名稱，例如 「 PowerShell 活動 」。</span><span class="sxs-lookup"><span data-stu-id="3e203-108">Add a new tab in the Toolbox by right-clicking inside the Toolbox and clicking **Add Tab**, and give the new tab a name such as "PowerShell Activities".</span></span>

   <span data-ttu-id="3e203-109">將索引標籤可讓您群組的 PowerShell 活動從 [工具箱] 中的其他工具不同。</span><span class="sxs-lookup"><span data-stu-id="3e203-109">Adding a tab allows you to group the PowerShell Activities separate from other tools in the Toolbox.</span></span>

4. <span data-ttu-id="3e203-110">在新的工具箱索引標籤中，按一下 **選擇項目...**.**選擇工具箱項目**對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="3e203-110">On the new Toolbox tab, click **Choose Items...**. The **Choose Toolbox Items** dialog appears.</span></span>

5. <span data-ttu-id="3e203-111">在 **選擇工具箱項目** 對話方塊中，按一下**System.Activities**  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="3e203-111">In the **Choose Toolbox Items** dialog, click the **System.Activities** tab.</span></span>

6. <span data-ttu-id="3e203-112">按一下 **[瀏覽]**。</span><span class="sxs-lookup"><span data-stu-id="3e203-112">Click **Browse**.</span></span>

7. <span data-ttu-id="3e203-113">瀏覽至 %WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e 資料夾，然後按兩下 Microsoft.PowerShell.Core.Activities.dll。</span><span class="sxs-lookup"><span data-stu-id="3e203-113">Navigate to the %WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e folder and double-click Microsoft.PowerShell.Core.Activities.dll.</span></span>

8. <span data-ttu-id="3e203-114">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="3e203-114">Click **OK**.</span></span> <span data-ttu-id="3e203-115">Microsoft.PowerShell.Core.Activities 組件所定義的活動現在已提供工具箱 中的。</span><span class="sxs-lookup"><span data-stu-id="3e203-115">The activities defined by the Microsoft.PowerShell.Core.Activities assembly are now available in the toolbox.</span></span>

## <a name="see-also"></a><span data-ttu-id="3e203-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e203-116">See Also</span></span>

[<span data-ttu-id="3e203-117">撰寫 Windows PowerShell 工作流程</span><span class="sxs-lookup"><span data-stu-id="3e203-117">Writing a Windows PowerShell Workflow</span></span>](./writing-a-windows-powershell-workflow.md)

[<span data-ttu-id="3e203-118">使用 Windows PowerShell 活動建立工作流程</span><span class="sxs-lookup"><span data-stu-id="3e203-118">Creating a Workflow with Windows PowerShell Activities</span></span>](./creating-a-workflow-with-windows-powershell-activities.md)