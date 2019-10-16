---
title: 撰寫 Windows PowerShell 工作流程 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2551ceed-836f-4275-9fc0-ea68446d6a35
caps.latest.revision: 7
ms.openlocfilehash: 4f0be193fb5b5c753d040a48e5f49235ece11708
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366007"
---
# <a name="writing-a-windows-powershell-workflow"></a><span data-ttu-id="25d6e-102">撰寫 Windows PowerShell 工作流程</span><span class="sxs-lookup"><span data-stu-id="25d6e-102">Writing a Windows PowerShell Workflow</span></span>

<span data-ttu-id="25d6e-103">您可以藉由將 Windows PowerShell 元件所公開的活動加入 Visual Studio 中的工作流程設計工具來建立 XAML 工作流程。</span><span class="sxs-lookup"><span data-stu-id="25d6e-103">You can create a XAML workflow by adding activities exposed by Windows PowerShell assemblies to the Workflow designer in Visual Studio.</span></span> <span data-ttu-id="25d6e-104">下列 Windows PowerShell 元件會公開已啟用工作流程的活動。</span><span class="sxs-lookup"><span data-stu-id="25d6e-104">The following Windows PowerShell assemblies expose workflow-enabled activities.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="25d6e-105">如果您想要提供工作流程的說明，XAML 工作流程必須封裝為模組。</span><span class="sxs-lookup"><span data-stu-id="25d6e-105">A XAML workflow must be packaged as a module if you want to provide help for the workflow.</span></span> <span data-ttu-id="25d6e-106">如需模組的相關資訊，請參閱[撰寫 Windows PowerShell 模組](../module/writing-a-windows-powershell-module.md)。</span><span class="sxs-lookup"><span data-stu-id="25d6e-106">For information about modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

- [<span data-ttu-id="25d6e-107">Microsoft. Powershell。活動</span><span class="sxs-lookup"><span data-stu-id="25d6e-107">Microsoft.Powershell.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Activities)

- [<span data-ttu-id="25d6e-108">Microsoft. Powershell. 活動</span><span class="sxs-lookup"><span data-stu-id="25d6e-108">Microsoft.Powershell.Core.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Core.Activities)

- [<span data-ttu-id="25d6e-109">Microsoft. Powershell。活動</span><span class="sxs-lookup"><span data-stu-id="25d6e-109">Microsoft.Powershell.Diagnostics.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Diagnostics.Activities)

- [<span data-ttu-id="25d6e-110">Microsoft. Powershell. 活動</span><span class="sxs-lookup"><span data-stu-id="25d6e-110">Microsoft.Powershell.Management.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Management.Activities)

- [<span data-ttu-id="25d6e-111">Microsoft. Powershell. 活動</span><span class="sxs-lookup"><span data-stu-id="25d6e-111">Microsoft.Powershell.Security.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Security.Activities)

- [<span data-ttu-id="25d6e-112">Microsoft. Powershell. 活動</span><span class="sxs-lookup"><span data-stu-id="25d6e-112">Microsoft.Powershell.Utility.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Utility.Activities)

  <span data-ttu-id="25d6e-113">下列主題說明如何使用 Windows PowerShell 活動來建立工作流程。</span><span class="sxs-lookup"><span data-stu-id="25d6e-113">The following topics describe how to create a Workflow by using Windows PowerShell activities.</span></span>

- [<span data-ttu-id="25d6e-114">將 Windows PowerShell 活動新增至 Visual Studio 工具箱</span><span class="sxs-lookup"><span data-stu-id="25d6e-114">Adding Windows PowerShell Activities to the Visual Studio Toolbox</span></span>](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)

- [<span data-ttu-id="25d6e-115">使用 Windows PowerShell 活動建立工作流程</span><span class="sxs-lookup"><span data-stu-id="25d6e-115">Creating a Workflow with Windows PowerShell Activities</span></span>](./creating-a-workflow-with-windows-powershell-activities.md)

- [<span data-ttu-id="25d6e-116">使用 Windows PowerShell 腳本建立工作流程</span><span class="sxs-lookup"><span data-stu-id="25d6e-116">Creating a Workflow by Using a Windows PowerShell Script</span></span>](./creating-a-workflow-by-using-a-windows-powershell-script.md)

- [<span data-ttu-id="25d6e-117">匯入和叫用 Windows PowerShell 工作流程</span><span class="sxs-lookup"><span data-stu-id="25d6e-117">Importing and Invoking a Windows PowerShell Workflow</span></span>](./importing-and-invoking-a-windows-powershell-workflow.md)

- [<span data-ttu-id="25d6e-118">從 Windows PowerShell Cmdlet 建立工作流程活動</span><span class="sxs-lookup"><span data-stu-id="25d6e-118">Creating a Workflow Activity from a Windows PowerShell Cmdlet</span></span>](./creating-a-workflow-activity-from-a-windows-powershell-cmdlet.md)