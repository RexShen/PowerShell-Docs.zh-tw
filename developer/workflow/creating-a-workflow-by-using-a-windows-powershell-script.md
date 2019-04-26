---
title: 使用 Windows PowerShell 指令碼建立工作流程 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 70532e7e-9cac-43c3-9687-e77011ecc878
caps.latest.revision: 4
ms.openlocfilehash: 5eb2186cbceee21f8b4a8c88b812e9c71f15e0af
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080368"
---
# <a name="creating-a-workflow-by-using-a-windows-powershell-script"></a><span data-ttu-id="4688f-102">使用 Windows PowerShell 指令碼建立工作流程</span><span class="sxs-lookup"><span data-stu-id="4688f-102">Creating a Workflow by Using a Windows PowerShell Script</span></span>

<span data-ttu-id="4688f-103">您可以藉由撰寫 Windows PowerShell 指令碼建立工作流程。</span><span class="sxs-lookup"><span data-stu-id="4688f-103">You can create a workflow by writing a Windows PowerShell script.</span></span> <span data-ttu-id="4688f-104">若要建立工作流程，使用工作流程關鍵字後面的指令碼主體之前的工作流程的名稱。</span><span class="sxs-lookup"><span data-stu-id="4688f-104">To create a workflow, use the workflow keyword followed by a name for the workflow before the body of the script.</span></span> <span data-ttu-id="4688f-105">例如：</span><span class="sxs-lookup"><span data-stu-id="4688f-105">For example:</span></span>

```powershell

workflow Invoke-HelloWorld {"Hello World from workflow"}
```

<span data-ttu-id="4688f-106">您可以找到工作流程中相同的方式就和任何其他 Windows PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="4688f-106">You find the workflow in the same way you would any other Windows PowerShell command.</span></span>

## <a name="implementing-parallel-and-sequence"></a><span data-ttu-id="4688f-107">實作 Parallel 和 Sequence</span><span class="sxs-lookup"><span data-stu-id="4688f-107">Implementing Parallel and Sequence</span></span>

<span data-ttu-id="4688f-108">[Windows Workflow Foundation](https://msdn.microsoft.com/en-us/library/ms735967.aspx)支援平行執行的活動。</span><span class="sxs-lookup"><span data-stu-id="4688f-108">[Windows Workflow Foundation](https://msdn.microsoft.com/en-us/library/ms735967.aspx) supports execution of activities in parallel.</span></span> <span data-ttu-id="4688f-109">若要使用 Windows PowerShell 指令碼中實作這項功能，使用`parallel`關鍵字前面的指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="4688f-109">To implement this capability in a Windows PowerShell script, use the `parallel` keyword in front of a script block.</span></span> <span data-ttu-id="4688f-110">您也可以使用`foreach -parallel`建構來逐一查看集合的物件，以平行方式。</span><span class="sxs-lookup"><span data-stu-id="4688f-110">You can also use the `foreach -parallel` construction to iterate through a collection of objects in parallel.</span></span> <span data-ttu-id="4688f-111">若要平行區塊內依序執行一組活動，指令碼區塊括住該群組的活動，並在前面加上順序關鍵字的區塊。</span><span class="sxs-lookup"><span data-stu-id="4688f-111">To execute a group of activities in sequential order within a parallel block, enclose that group of activities in a script block and precede the block with the sequence keyword.</span></span>

## <a name="joining-computers-to-a-domain"></a><span data-ttu-id="4688f-112">將電腦加入網域</span><span class="sxs-lookup"><span data-stu-id="4688f-112">Joining Computers to a Domain</span></span>

<span data-ttu-id="4688f-113">下列指令碼會建立的工作流程，會檢查一組使用者指定電腦的網域狀態、 將它們加入網域，如果他們未已經加入，然後再檢查一次狀態。</span><span class="sxs-lookup"><span data-stu-id="4688f-113">The following script creates a workflow that checks the domain status of a group of user-specified computers, joins them to a domain if they are not already joined, and then checks the status again.</span></span> <span data-ttu-id="4688f-114">這是 XAML 工作流程中所述的指令碼版本[使用 Windows PowerShell 活動建立工作流程](./creating-a-workflow-with-windows-powershell-activities.md)。</span><span class="sxs-lookup"><span data-stu-id="4688f-114">This is a script version of the XAML workflow explained in [Creating a Workflow with Windows PowerShell Activities](./creating-a-workflow-with-windows-powershell-activities.md).</span></span>

```powershell
workflow Join-Domain
{
    param([string[]] $ComputerName, [PSCredential] $DomainCred, [PsCredential] $MachineCred)

    foreach -parallel($Computer in $ComputerName)
    {
        sequence {
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        Add-Computer -PSComputerName $Computer -PSCredential $DomainCred
        Restart-Computer -ComputerName $Computer -Credential $MachineCred -For PowerShell -Force -Wait -PSComputerName ""
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        }
    }
 }

```