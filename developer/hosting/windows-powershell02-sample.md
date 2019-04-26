---
title: Windows PowerShell02 範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92492a7e-257d-47d3-b119-89df3c5545e8
caps.latest.revision: 9
ms.openlocfilehash: 89ad17257ebac56105a93672317a149515e80d32
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082510"
---
# <a name="windows-powershell02-sample"></a><span data-ttu-id="ee078-102">Windows PowerShell02 範例</span><span class="sxs-lookup"><span data-stu-id="ee078-102">Windows PowerShell02 Sample</span></span>

<span data-ttu-id="ee078-103">此範例示範如何使用 runspace 的 runspace 集區，以非同步方式執行命令。</span><span class="sxs-lookup"><span data-stu-id="ee078-103">This sample shows how to run commands asynchronously by using the runspaces of a runspace pool.</span></span> <span data-ttu-id="ee078-104">此範例會產生一份命令，並再執行這些命令，而 Windows PowerShell 引擎便會開啟 runspace 從集區會在需要時。</span><span class="sxs-lookup"><span data-stu-id="ee078-104">The sample generates a list of commands, and then runs those commands while the Windows PowerShell engine opens a runspace from the pool when it is needed.</span></span>

## <a name="requirements"></a><span data-ttu-id="ee078-105">需求</span><span class="sxs-lookup"><span data-stu-id="ee078-105">Requirements</span></span>

- <span data-ttu-id="ee078-106">這個範例需要 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="ee078-106">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="ee078-107">示範</span><span class="sxs-lookup"><span data-stu-id="ee078-107">Demonstrates</span></span>

<span data-ttu-id="ee078-108">此範例示範下列作業：</span><span class="sxs-lookup"><span data-stu-id="ee078-108">This sample demonstrates the following:</span></span>

- <span data-ttu-id="ee078-109">建立 RunspacePool 物件最小和最大數目的 runspace 可同時為開啟。</span><span class="sxs-lookup"><span data-stu-id="ee078-109">Creating a RunspacePool object with a minimum and maximum number of runspaces allowed to be open at the same time.</span></span>

- <span data-ttu-id="ee078-110">建立命令的清單。</span><span class="sxs-lookup"><span data-stu-id="ee078-110">Creating a list of commands.</span></span>

- <span data-ttu-id="ee078-111">以非同步方式執行命令。</span><span class="sxs-lookup"><span data-stu-id="ee078-111">Running the commands asynchronously.</span></span>

- <span data-ttu-id="ee078-112">呼叫[System.Management.Automation.Runspaces.Runspacepool.Getavailablerunspaces\*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces)若要查看有多少 runspace 可用的方法。</span><span class="sxs-lookup"><span data-stu-id="ee078-112">Calling the [System.Management.Automation.Runspaces.Runspacepool.Getavailablerunspaces\*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) method to see how many runspaces are free.</span></span>

- <span data-ttu-id="ee078-113">擷取命令輸出[System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke)方法。</span><span class="sxs-lookup"><span data-stu-id="ee078-113">Capturing the command output with the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

## <a name="example"></a><span data-ttu-id="ee078-114">範例</span><span class="sxs-lookup"><span data-stu-id="ee078-114">Example</span></span>

<span data-ttu-id="ee078-115">此範例示範如何開啟的 runspace 的 runspace 集區，以及如何以非同步方式在那些 runspace 中執行命令。</span><span class="sxs-lookup"><span data-stu-id="ee078-115">This sample shows how to open the runspaces of a runspace pool, and how to asynchronously run commands in those runspaces.</span></span>

[!code-csharp[PowerShell02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs#L11-L96 "PowerShell02.cs")]

## <a name="see-also"></a><span data-ttu-id="ee078-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee078-116">See Also</span></span>

[<span data-ttu-id="ee078-117">撰寫 Windows PowerShell 主機應用程式</span><span class="sxs-lookup"><span data-stu-id="ee078-117">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)