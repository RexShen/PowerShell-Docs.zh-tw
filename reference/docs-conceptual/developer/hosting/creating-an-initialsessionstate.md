---
ms.date: 09/13/2016
ms.topic: reference
title: 建立 InitialSessionState
description: 建立 InitialSessionState
ms.openlocfilehash: d58a32c2ae8a22132f3095d093e3cb322f65c486
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649418"
---
# <a name="creating-an-initialsessionstate"></a><span data-ttu-id="b4e5f-103">建立 InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="b4e5f-103">Creating an InitialSessionState</span></span>

<span data-ttu-id="b4e5f-104">PowerShell 命令會在執行空間中執行。</span><span class="sxs-lookup"><span data-stu-id="b4e5f-104">PowerShell commands run in a runspace.</span></span>
<span data-ttu-id="b4e5f-105">若要在您的應用程式中裝載 PowerShell，您必須建立[system.servicemodel 物件。](/dotnet/api/System.Management.Automation.Runspaces.Runspace)</span><span class="sxs-lookup"><span data-stu-id="b4e5f-105">To host PowerShell in your application, you must create a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object.</span></span>
<span data-ttu-id="b4e5f-106">每個執行時間都有與其相關聯的 [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) 物件。</span><span class="sxs-lookup"><span data-stu-id="b4e5f-106">Every runspace has an [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object associated with it.</span></span>
<span data-ttu-id="b4e5f-107">>initialsessionstate 會指定運行空間的特性，例如可供該運行空間使用的命令、變數和模組。</span><span class="sxs-lookup"><span data-stu-id="b4e5f-107">The InitialSessionState specifies characteristics of the runspace, such as which commands, variables, and modules are available for that runspace.</span></span>

## <a name="create-a-default-initialsessionstate"></a><span data-ttu-id="b4e5f-108">建立預設 >initialsessionstate</span><span class="sxs-lookup"><span data-stu-id="b4e5f-108">Create a default InitialSessionState</span></span>

<span data-ttu-id="b4e5f-109">**>initialsessionstate** 類別的 [CreateDefault](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault)和 [CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2)方法可以用來建立 **>initialsessionstate** 物件。</span><span class="sxs-lookup"><span data-stu-id="b4e5f-109">The [CreateDefault](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) and [CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) methods of the **InitialSessionState** class can be used to create an **InitialSessionState** object.</span></span>
<span data-ttu-id="b4e5f-110">**CreateDefault** 方法會建立一個 **>initialsessionstate** ，其中包含所有載入的內建命令，而 **CreateDefault2** 方法只會載入裝載 PowerShell 的必要命令， () 的命令。</span><span class="sxs-lookup"><span data-stu-id="b4e5f-110">The **CreateDefault** method creates an **InitialSessionState** with all of the built-in commands loaded, while the **CreateDefault2** method loads only the commands required to host PowerShell (the commands from the Microsoft.PowerShell.Core module).</span></span>

<span data-ttu-id="b4e5f-111">如果您想要進一步限制主機應用程式中可用的命令，您必須建立受限的運行時。</span><span class="sxs-lookup"><span data-stu-id="b4e5f-111">If you want to further limit the commands available in your host application you need to create a constrained runspace.</span></span>
<span data-ttu-id="b4e5f-112">如需詳細資訊，請參閱 [建立受限的運行](creating-a-constrained-runspace.md)時。</span><span class="sxs-lookup"><span data-stu-id="b4e5f-112">For information, see [Creating a constrained runspace](creating-a-constrained-runspace.md).</span></span>

<span data-ttu-id="b4e5f-113">下列程式碼示範如何建立 **>initialsessionstate**、將它指派給執行時間、將命令新增至該執行時間中的管線，以及叫用命令。</span><span class="sxs-lookup"><span data-stu-id="b4e5f-113">The following code shows how to create an **InitialSessionState**, assign it to a runspace, add commands to the pipeline in that runspace, and invoke the commands.</span></span>
<span data-ttu-id="b4e5f-114">如需新增和叫用命令的詳細資訊，請參閱 [新增和](adding-and-invoking-commands.md)叫用命令。</span><span class="sxs-lookup"><span data-stu-id="b4e5f-114">For more information about adding and invoking commands, see [Adding and invoking commands](adding-and-invoking-commands.md).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b4e5f-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4e5f-115">See Also</span></span>

[<span data-ttu-id="b4e5f-116">建立受限 Runspace</span><span class="sxs-lookup"><span data-stu-id="b4e5f-116">Creating a constrained runspace</span></span>](creating-a-constrained-runspace.md)

[<span data-ttu-id="b4e5f-117">新增及叫用命令</span><span class="sxs-lookup"><span data-stu-id="b4e5f-117">Adding and invoking commands</span></span>](adding-and-invoking-commands.md)
