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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080317"
---
# <a name="writing-a-windows-powershell-workflow"></a><span data-ttu-id="ff83b-102">撰寫 Windows PowerShell 工作流程</span><span class="sxs-lookup"><span data-stu-id="ff83b-102">Writing a Windows PowerShell Workflow</span></span>

<span data-ttu-id="ff83b-103">您可以加入至工作流程設計工具在 Visual Studio 中的 Windows PowerShell 組件所公開的活動，以建立 XAML 工作流程。</span><span class="sxs-lookup"><span data-stu-id="ff83b-103">You can create a XAML workflow by adding activities exposed by Windows PowerShell assemblies to the Workflow designer in Visual Studio.</span></span> <span data-ttu-id="ff83b-104">下列 Windows PowerShell 組件公開 （expose) 啟用工作流程的活動。</span><span class="sxs-lookup"><span data-stu-id="ff83b-104">The following Windows PowerShell assemblies expose workflow-enabled activities.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ff83b-105">XAML 工作流程必須封裝成模組，如果您想要提供工作流程的說明。</span><span class="sxs-lookup"><span data-stu-id="ff83b-105">A XAML workflow must be packaged as a module if you want to provide help for the workflow.</span></span> <span data-ttu-id="ff83b-106">如需模組的資訊，請參閱[撰寫 Windows PowerShell 模組](../module/writing-a-windows-powershell-module.md)。</span><span class="sxs-lookup"><span data-stu-id="ff83b-106">For information about modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

- [<span data-ttu-id="ff83b-107">Microsoft.Powershell.Activities</span><span class="sxs-lookup"><span data-stu-id="ff83b-107">Microsoft.Powershell.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Activities)

- [<span data-ttu-id="ff83b-108">Microsoft.Powershell.Core.Activities</span><span class="sxs-lookup"><span data-stu-id="ff83b-108">Microsoft.Powershell.Core.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Core.Activities)

- [<span data-ttu-id="ff83b-109">Microsoft.Powershell.Diagnostics.Activities</span><span class="sxs-lookup"><span data-stu-id="ff83b-109">Microsoft.Powershell.Diagnostics.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Diagnostics.Activities)

- [<span data-ttu-id="ff83b-110">Microsoft.Powershell.Management.Activities</span><span class="sxs-lookup"><span data-stu-id="ff83b-110">Microsoft.Powershell.Management.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Management.Activities)

- [<span data-ttu-id="ff83b-111">Microsoft.Powershell.Security.Activities</span><span class="sxs-lookup"><span data-stu-id="ff83b-111">Microsoft.Powershell.Security.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Security.Activities)

- [<span data-ttu-id="ff83b-112">Microsoft.Powershell.Utility.Activities</span><span class="sxs-lookup"><span data-stu-id="ff83b-112">Microsoft.Powershell.Utility.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Utility.Activities)

  <span data-ttu-id="ff83b-113">下列主題說明如何使用 Windows PowerShell 活動建立工作流程。</span><span class="sxs-lookup"><span data-stu-id="ff83b-113">The following topics describe how to create a Workflow by using Windows PowerShell activities.</span></span>

- [<span data-ttu-id="ff83b-114">將 Windows PowerShell 活動加入至 Visual Studio 工具箱</span><span class="sxs-lookup"><span data-stu-id="ff83b-114">Adding Windows PowerShell Activities to the Visual Studio Toolbox</span></span>](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)

- [<span data-ttu-id="ff83b-115">使用 Windows PowerShell 活動建立工作流程</span><span class="sxs-lookup"><span data-stu-id="ff83b-115">Creating a Workflow with Windows PowerShell Activities</span></span>](./creating-a-workflow-with-windows-powershell-activities.md)

- [<span data-ttu-id="ff83b-116">使用 Windows PowerShell 指令碼建立工作流程</span><span class="sxs-lookup"><span data-stu-id="ff83b-116">Creating a Workflow by Using a Windows PowerShell Script</span></span>](./creating-a-workflow-by-using-a-windows-powershell-script.md)

- [<span data-ttu-id="ff83b-117">匯入和叫用 Windows PowerShell 工作流程</span><span class="sxs-lookup"><span data-stu-id="ff83b-117">Importing and Invoking a Windows PowerShell Workflow</span></span>](./importing-and-invoking-a-windows-powershell-workflow.md)

- [<span data-ttu-id="ff83b-118">從 Windows PowerShell Cmdlet 建立工作流程活動</span><span class="sxs-lookup"><span data-stu-id="ff83b-118">Creating a Workflow Activity from a Windows PowerShell Cmdlet</span></span>](./creating-a-workflow-activity-from-a-windows-powershell-cmdlet.md)