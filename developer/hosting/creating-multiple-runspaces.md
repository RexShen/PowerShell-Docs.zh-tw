---
title: 建立多個執行空間 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42c40c7f-1ee7-4021-950c-2e013c8f2a4a
caps.latest.revision: 4
ms.openlocfilehash: 606a2ee4e70d303bf1b1d69b7523eb8649f9be0c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082952"
---
# <a name="creating-multiple-runspaces"></a><span data-ttu-id="203eb-102">建立多個 Runspace</span><span class="sxs-lookup"><span data-stu-id="203eb-102">Creating multiple runspaces</span></span>

<span data-ttu-id="203eb-103">如果您建立大量的 runspace，您可以考慮建立 runspace 集區。</span><span class="sxs-lookup"><span data-stu-id="203eb-103">If you create a large number of runspaces, you might consider creating a runspace pool.</span></span> <span data-ttu-id="203eb-104">使用[System.Management.Automation.Runspaces.Runspacepool](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool)物件，而不是使用相同的特性，建立大量的個別的 runspace 可改善效能。</span><span class="sxs-lookup"><span data-stu-id="203eb-104">Using a [System.Management.Automation.Runspaces.Runspacepool](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool) object, rather than creating a large number of individual runspaces with the same characteristics, can improve performance.</span></span>

## <a name="creating-and-using-a-runspace-pool"></a><span data-ttu-id="203eb-105">建立和使用 runspace 集區。</span><span class="sxs-lookup"><span data-stu-id="203eb-105">Creating and using a runspace pool.</span></span>

 <span data-ttu-id="203eb-106">下列範例示範如何建立 runspace 集區以及如何在集區的 runspace 中，以非同步方式執行命令。</span><span class="sxs-lookup"><span data-stu-id="203eb-106">The following example shows how to create a runspace pool and how to run a command asynchronously in a runspace of the pool.</span></span>

```csharp
namespace HostRunspacePool
{
  using System;
  using System.Collections.ObjectModel;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;

  /// <summary>
  /// This class provides the Main entry point for the Host application.
  /// </summary>
  internal class HostRunspacePool
  {
    /// <summary>
    /// This sample demonstrates the following.
    /// 1. Creating and opening a runspace pool.
    /// 2. Creating a PowerShell object.
    /// 3. Adding commands and arguments to the PowerShell object.
    /// 4. Running the commands asynchronously using the runspace
    ///    of the runspace pool.
    /// </summary>
    /// <param name="args">Parameter is not used.</param>
    private static void Main(string[] args)
    {
      // Create a pool of runspaces.
      using (RunspacePool rsp = RunspaceFactory.CreateRunspacePool())
      {
        rsp.Open();

        // Create a PowerShell object to run the following command.
        //  get-process wmi*
        PowerShell gpc = PowerShell.Create();
        // Specify the runspace to use and add commands.
        gpc.RunspacePool = rsp;
        gpc.AddCommand("Get-Process").AddArgument("wmi*");

        // Invoke the command asynchronously.
        IAsyncResult gpcAsyncResult = gpc.BeginInvoke();
        // Get the results of running the command.
        PSDataCollection<PSObject> gpcOutput = gpc.EndInvoke(gpcAsyncResult);

        // Process the output.
        Console.WriteLine("The output from running the command: get-process wmi*");
        for (int i= 0; i < gpcOutput.Count; i++)
        {
         Console.WriteLine(
                           "Process Name: {0} Process Id: {1}",
                           gpcOutput[i].Properties["ProcessName"].Value,
                           gpcOutput[i].Properties["Id"].Value);
        }
      } // End using.
    } // End Main entry point.
  } // End HostPs5 class.
}
```

## <a name="see-also"></a><span data-ttu-id="203eb-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="203eb-107">See Also</span></span>

 [<span data-ttu-id="203eb-108">建立 InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="203eb-108">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)
