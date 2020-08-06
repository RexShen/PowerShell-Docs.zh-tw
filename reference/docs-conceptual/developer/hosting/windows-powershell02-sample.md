---
title: Windows PowerShell02 範例 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: a82366a88addb08e186eede79e621d90d915c50f
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779381"
---
# <a name="windows-powershell02-sample"></a><span data-ttu-id="256cd-102">Windows PowerShell02 範例</span><span class="sxs-lookup"><span data-stu-id="256cd-102">Windows PowerShell02 Sample</span></span>

<span data-ttu-id="256cd-103">這個範例會示範如何使用執行時間集區的執行空間，以非同步方式執行命令。</span><span class="sxs-lookup"><span data-stu-id="256cd-103">This sample shows how to run commands asynchronously using the runspaces of a runspace pool.</span></span> <span data-ttu-id="256cd-104">此範例會產生命令的清單，然後在 Windows PowerShell 引擎視需要從集區開啟執行時間時，執行這些命令。</span><span class="sxs-lookup"><span data-stu-id="256cd-104">The sample generates a list of commands, and then runs those commands while the Windows PowerShell engine opens a runspace from the pool when it is needed.</span></span>

## <a name="requirements"></a><span data-ttu-id="256cd-105">需求</span><span class="sxs-lookup"><span data-stu-id="256cd-105">Requirements</span></span>

- <span data-ttu-id="256cd-106">此範例需要 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="256cd-106">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="256cd-107">示範</span><span class="sxs-lookup"><span data-stu-id="256cd-107">Demonstrates</span></span>

<span data-ttu-id="256cd-108">本範例示範以下項目:</span><span class="sxs-lookup"><span data-stu-id="256cd-108">This sample demonstrates the following:</span></span>

- <span data-ttu-id="256cd-109">建立 RunspacePool 物件，其中包含允許同時開啟的最小和最大執行空間數目。</span><span class="sxs-lookup"><span data-stu-id="256cd-109">Creating a RunspacePool object with a minimum and maximum number of runspaces allowed to be open at the same time.</span></span>
- <span data-ttu-id="256cd-110">建立命令清單。</span><span class="sxs-lookup"><span data-stu-id="256cd-110">Creating a list of commands.</span></span>
- <span data-ttu-id="256cd-111">以非同步方式執行命令。</span><span class="sxs-lookup"><span data-stu-id="256cd-111">Running the commands asynchronously.</span></span>
- <span data-ttu-id="256cd-112">呼叫[Runspacepool. Getavailablerunspaces \*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces)方法，查看有多少個可用的多工。</span><span class="sxs-lookup"><span data-stu-id="256cd-112">Calling the [System.Management.Automation.Runspaces.Runspacepool.Getavailablerunspaces\*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) method to see how many runspaces are free.</span></span>
- <span data-ttu-id="256cd-113">使用[Endinvoke \*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke)方法，來捕捉命令輸出。</span><span class="sxs-lookup"><span data-stu-id="256cd-113">Capturing the command output with the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

## <a name="example"></a><span data-ttu-id="256cd-114">範例</span><span class="sxs-lookup"><span data-stu-id="256cd-114">Example</span></span>

<span data-ttu-id="256cd-115">這個範例會示範如何開啟執行時間集區的執行空間，以及如何以非同步方式在這些執行空間中執行命令。</span><span class="sxs-lookup"><span data-stu-id="256cd-115">This sample shows how to open the runspaces of a runspace pool, and how to asynchronously run commands in those runspaces.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs" range="11-96":::

## <a name="see-also"></a><span data-ttu-id="256cd-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="256cd-116">See Also</span></span>

[<span data-ttu-id="256cd-117">撰寫 Windows PowerShell 主機應用程式</span><span class="sxs-lookup"><span data-stu-id="256cd-117">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)
