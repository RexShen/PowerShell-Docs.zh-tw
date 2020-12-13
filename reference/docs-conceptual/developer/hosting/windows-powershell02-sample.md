---
ms.date: 09/13/2016
ms.topic: reference
title: Windows PowerShell02 範例
description: Windows PowerShell02 範例
ms.openlocfilehash: 61dedd72d93d4000edf9a12f12bbb49fbaeb9f3c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657348"
---
# <a name="windows-powershell02-sample"></a><span data-ttu-id="5e853-103">Windows PowerShell02 範例</span><span class="sxs-lookup"><span data-stu-id="5e853-103">Windows PowerShell02 Sample</span></span>

<span data-ttu-id="5e853-104">此範例示範如何使用執行空間集區的執行程式，以非同步方式執行命令。</span><span class="sxs-lookup"><span data-stu-id="5e853-104">This sample shows how to run commands asynchronously using the runspaces of a runspace pool.</span></span> <span data-ttu-id="5e853-105">此範例會產生命令清單，然後在 Windows PowerShell 引擎在需要時從集區開啟執行程式時，執行這些命令。</span><span class="sxs-lookup"><span data-stu-id="5e853-105">The sample generates a list of commands, and then runs those commands while the Windows PowerShell engine opens a runspace from the pool when it is needed.</span></span>

## <a name="requirements"></a><span data-ttu-id="5e853-106">規格需求</span><span class="sxs-lookup"><span data-stu-id="5e853-106">Requirements</span></span>

- <span data-ttu-id="5e853-107">此範例需要 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="5e853-107">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="5e853-108">示範</span><span class="sxs-lookup"><span data-stu-id="5e853-108">Demonstrates</span></span>

<span data-ttu-id="5e853-109">本範例示範以下項目:</span><span class="sxs-lookup"><span data-stu-id="5e853-109">This sample demonstrates the following:</span></span>

- <span data-ttu-id="5e853-110">建立 RunspacePool 物件，其允許同時開啟的最小和最大執行空間數目。</span><span class="sxs-lookup"><span data-stu-id="5e853-110">Creating a RunspacePool object with a minimum and maximum number of runspaces allowed to be open at the same time.</span></span>
- <span data-ttu-id="5e853-111">建立命令的清單。</span><span class="sxs-lookup"><span data-stu-id="5e853-111">Creating a list of commands.</span></span>
- <span data-ttu-id="5e853-112">以非同步方式執行命令。</span><span class="sxs-lookup"><span data-stu-id="5e853-112">Running the commands asynchronously.</span></span>
- <span data-ttu-id="5e853-113">呼叫 [Runspacepool. Getavailablerunspaces \*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) 方法，查看有多少個可用的空間。</span><span class="sxs-lookup"><span data-stu-id="5e853-113">Calling the [System.Management.Automation.Runspaces.Runspacepool.Getavailablerunspaces\*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) method to see how many runspaces are free.</span></span>
- <span data-ttu-id="5e853-114">使用 [Endinvoke \*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) 方法，來捕捉命令輸出。</span><span class="sxs-lookup"><span data-stu-id="5e853-114">Capturing the command output with the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

## <a name="example"></a><span data-ttu-id="5e853-115">範例</span><span class="sxs-lookup"><span data-stu-id="5e853-115">Example</span></span>

<span data-ttu-id="5e853-116">此範例說明如何開啟執行空間集區的執行程式，以及如何以非同步方式在這些執行空間中執行命令。</span><span class="sxs-lookup"><span data-stu-id="5e853-116">This sample shows how to open the runspaces of a runspace pool, and how to asynchronously run commands in those runspaces.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs" range="11-96":::

## <a name="see-also"></a><span data-ttu-id="5e853-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e853-117">See Also</span></span>

[<span data-ttu-id="5e853-118">撰寫 Windows PowerShell 主機應用程式</span><span class="sxs-lookup"><span data-stu-id="5e853-118">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)
