---
title: 使用 Windows PowerShell 腳本來建立工作流程 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 70532e7e-9cac-43c3-9687-e77011ecc878
caps.latest.revision: 4
ms.openlocfilehash: 5eb2186cbceee21f8b4a8c88b812e9c71f15e0af
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366027"
---
# <a name="creating-a-workflow-by-using-a-windows-powershell-script"></a><span data-ttu-id="8dbaf-102">使用 Windows PowerShell 指令碼建立工作流程</span><span class="sxs-lookup"><span data-stu-id="8dbaf-102">Creating a Workflow by Using a Windows PowerShell Script</span></span>

<span data-ttu-id="8dbaf-103">您可以撰寫 Windows PowerShell 腳本來建立工作流程。</span><span class="sxs-lookup"><span data-stu-id="8dbaf-103">You can create a workflow by writing a Windows PowerShell script.</span></span> <span data-ttu-id="8dbaf-104">若要建立工作流程，請在腳本主體之前，使用 workflow 關鍵字，後面接著工作流程名稱。</span><span class="sxs-lookup"><span data-stu-id="8dbaf-104">To create a workflow, use the workflow keyword followed by a name for the workflow before the body of the script.</span></span> <span data-ttu-id="8dbaf-105">例如：</span><span class="sxs-lookup"><span data-stu-id="8dbaf-105">For example:</span></span>

```powershell

workflow Invoke-HelloWorld {"Hello World from workflow"}
```

<span data-ttu-id="8dbaf-106">您可以透過與任何其他 Windows PowerShell 命令相同的方式來尋找工作流程。</span><span class="sxs-lookup"><span data-stu-id="8dbaf-106">You find the workflow in the same way you would any other Windows PowerShell command.</span></span>

## <a name="implementing-parallel-and-sequence"></a><span data-ttu-id="8dbaf-107">實作為平行和順序</span><span class="sxs-lookup"><span data-stu-id="8dbaf-107">Implementing Parallel and Sequence</span></span>

<span data-ttu-id="8dbaf-108">[Windows Workflow Foundation](https://msdn.microsoft.com/en-us/library/ms735967.aspx)支援以平行方式執行活動。</span><span class="sxs-lookup"><span data-stu-id="8dbaf-108">[Windows Workflow Foundation](https://msdn.microsoft.com/en-us/library/ms735967.aspx) supports execution of activities in parallel.</span></span> <span data-ttu-id="8dbaf-109">若要在 Windows PowerShell 腳本中執行這項功能，請在腳本區塊前面使用 `parallel` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="8dbaf-109">To implement this capability in a Windows PowerShell script, use the `parallel` keyword in front of a script block.</span></span> <span data-ttu-id="8dbaf-110">您也可以使用 `foreach -parallel` 結構來平行逐一查看物件的集合。</span><span class="sxs-lookup"><span data-stu-id="8dbaf-110">You can also use the `foreach -parallel` construction to iterate through a collection of objects in parallel.</span></span> <span data-ttu-id="8dbaf-111">若要在平行區塊內依序執行一組活動，請將活動群組括在腳本區塊中，然後在區塊前面加上 sequence 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="8dbaf-111">To execute a group of activities in sequential order within a parallel block, enclose that group of activities in a script block and precede the block with the sequence keyword.</span></span>

## <a name="joining-computers-to-a-domain"></a><span data-ttu-id="8dbaf-112">將電腦加入網域</span><span class="sxs-lookup"><span data-stu-id="8dbaf-112">Joining Computers to a Domain</span></span>

<span data-ttu-id="8dbaf-113">下列腳本會建立一個工作流程，它會檢查使用者指定之電腦群組的網域狀態，並將它們加入網域（如果尚未聯結），然後重新檢查狀態。</span><span class="sxs-lookup"><span data-stu-id="8dbaf-113">The following script creates a workflow that checks the domain status of a group of user-specified computers, joins them to a domain if they are not already joined, and then checks the status again.</span></span> <span data-ttu-id="8dbaf-114">這是[使用 Windows PowerShell 活動建立工作流程](./creating-a-workflow-with-windows-powershell-activities.md)中說明的 XAML 工作流程腳本版本。</span><span class="sxs-lookup"><span data-stu-id="8dbaf-114">This is a script version of the XAML workflow explained in [Creating a Workflow with Windows PowerShell Activities](./creating-a-workflow-with-windows-powershell-activities.md).</span></span>

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