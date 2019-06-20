---
title: 建立 InitialSessionState |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ae707db-52e0-408c-87fa-b35c42eaaab1
caps.latest.revision: 5
ms.openlocfilehash: 9140d03e046def2fbbcc2a842b9ea1b9e1fa2985
ms.sourcegitcommit: 13f24786ed39ca1c07eff2b73a1974c366e31cb8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2019
ms.locfileid: "67263843"
---
# <a name="creating-an-initialsessionstate"></a><span data-ttu-id="86490-102">建立 InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="86490-102">Creating an InitialSessionState</span></span>

<span data-ttu-id="86490-103">在的 runspace 中執行 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="86490-103">PowerShell commands run in a runspace.</span></span>
<span data-ttu-id="86490-104">若要裝載應用程式中的 PowerShell，您必須建立[System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace)物件。</span><span class="sxs-lookup"><span data-stu-id="86490-104">To host PowerShell in your application, you must create a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object.</span></span>
<span data-ttu-id="86490-105">具有每個 runspace [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)與其相關聯的物件。</span><span class="sxs-lookup"><span data-stu-id="86490-105">Every runspace has an [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object associated with it.</span></span>
<span data-ttu-id="86490-106">InitialSessionState 指定例如命令、 變數和模組可供該 runspace 的 runspace 的特性。</span><span class="sxs-lookup"><span data-stu-id="86490-106">The InitialSessionState specifies characteristics of the runspace, such as which commands, variables, and modules are available for that runspace.</span></span>

## <a name="create-a-default-initialsessionstate"></a><span data-ttu-id="86490-107">建立預設 InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="86490-107">Create a default InitialSessionState</span></span>

<span data-ttu-id="86490-108">[CreateDefault](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault)並[CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2)方法**InitialSessionState**類別可用來建立**InitialSessionState**物件。</span><span class="sxs-lookup"><span data-stu-id="86490-108">The [CreateDefault](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) and [CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) methods of the **InitialSessionState** class can be used to create an **InitialSessionState** object.</span></span>
<span data-ttu-id="86490-109">**CreateDefault**方法會建立**InitialSessionState**所有內建的命令載入，同時**CreateDefault2**方法載入的命令需要主機 PowerShell （Microsoft.PowerShell.Core 模組從命令）。</span><span class="sxs-lookup"><span data-stu-id="86490-109">The **CreateDefault** method creates an **InitialSessionState** with all of the built-in commands loaded, while the **CreateDefault2** method loads only the commands required to host PowerShell (the commands from the Microsoft.PowerShell.Core module).</span></span>

<span data-ttu-id="86490-110">如果您想要進一步限制主應用程式中可用的命令要建立受限的 runspace。</span><span class="sxs-lookup"><span data-stu-id="86490-110">If you want to further limit the commands available in your host application you need to create a constrained runspace.</span></span>
<span data-ttu-id="86490-111">如需資訊，請參閱[建立受限的 runspace](creating-a-constrained-runspace.md)。</span><span class="sxs-lookup"><span data-stu-id="86490-111">For information, see [Creating a constrained runspace](creating-a-constrained-runspace.md).</span></span>

<span data-ttu-id="86490-112">下列程式碼示範如何建立**InitialSessionState**、 將它指派給 runspace、 將命令加入至該 runspace 中中的管線和叫用命令。</span><span class="sxs-lookup"><span data-stu-id="86490-112">The following code shows how to create an **InitialSessionState**, assign it to a runspace, add commands to the pipeline in that runspace, and invoke the commands.</span></span>
<span data-ttu-id="86490-113">如需有關新增和叫用命令的詳細資訊，請參閱[加入和叫用命令](adding-and-invoking-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="86490-113">For more information about adding and invoking commands, see [Adding and invoking commands](adding-and-invoking-commands.md).</span></span>

```csharp
namespace SampleHost
{
  using System;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;

  class HostP4b
  {
    static void Main(string[] args)
    {
      // Call the InitialSessionState.CreateDefault method to create
      // an empty InitialSessionState object, and then add the
      // elements that will be available when the runspace is opened.
      InitialSessionState iss = InitialSessionState.CreateDefault();
      SessionStateVariableEntry var1 = new
          SessionStateVariableEntry("test1",
                                    "MyVar1",
                                    "Initial session state MyVar1 test");
      iss.Variables.Add(var1);

      SessionStateVariableEntry var2 = new
          SessionStateVariableEntry("test2",
                                    "MyVar2",
                                    "Initial session state MyVar2 test");
      iss.Variables.Add(var2);

      // Call the RunspaceFactory.CreateRunspace(InitialSessionState)
      // method to create the runspace where the pipeline is run.
      Runspace rs = RunspaceFactory.CreateRunspace(iss);
      rs.Open();

      // Call the PowerShell.Create() method to create the PowerShell object,
      // and then specify the runspace and commands to the pipeline.
      // and create the command pipeline.
      PowerShell ps = PowerShell.Create();
      ps.Runspace = rs;
      ps.AddCommand("Get-Variable");
      ps.AddArgument("test*");

      Console.WriteLine("Variable             Value");
      Console.WriteLine("--------------------------");

      // Call the PowerShell.Invoke() method to run
      // the pipeline synchronously.
      foreach (PSObject result in ps.Invoke())
      {
        Console.WriteLine("{0,-20}{1}",
            result.Members["Name"].Value,
            result.Members["Value"].Value);
      } // End foreach.

      // Close the runspace to free resources.
      rs.Close();

    } // End Main.
  } // End SampleHost.
}
```

## <a name="see-also"></a><span data-ttu-id="86490-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86490-114">See Also</span></span>

[<span data-ttu-id="86490-115">建立受限的 runspace</span><span class="sxs-lookup"><span data-stu-id="86490-115">Creating a constrained runspace</span></span>](creating-a-constrained-runspace.md)

[<span data-ttu-id="86490-116">新增和叫用命令</span><span class="sxs-lookup"><span data-stu-id="86490-116">Adding and invoking commands</span></span>](adding-and-invoking-commands.md)
