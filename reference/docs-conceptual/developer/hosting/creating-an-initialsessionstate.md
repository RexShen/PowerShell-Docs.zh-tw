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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367617"
---
# <a name="creating-an-initialsessionstate"></a>建立 InitialSessionState

PowerShell 命令會在運行空間中執行。
若要在您的應用程式中裝載 PowerShell，您必須建立[system.servicemodel 物件。](/dotnet/api/System.Management.Automation.Runspaces.Runspace)
每個執行時間都有相關聯的[InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)物件。
InitialSessionState 指定運行空間的特性，例如可供該運行空間使用的命令、變數和模組。

## <a name="create-a-default-initialsessionstate"></a>建立預設 InitialSessionState

**InitialSessionState**類別的[CreateDefault](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault)和[CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2)方法可以用來建立**InitialSessionState**物件。
**CreateDefault**方法會建立已載入所有內建命令的**InitialSessionState** ，而**CreateDefault2**方法只會載入裝載 PowerShell 所需的命令（來自的命令Microsoft. PowerShell 模組）。

如果您想要進一步限制主機應用程式中可用的命令，您必須建立受限的運行空間。
如需相關資訊，請參閱[建立受限的運行空間](creating-a-constrained-runspace.md)。

下列程式碼示範如何建立**InitialSessionState**、將它指派給執行時間、將命令新增至該執行時間中的管線，以及叫用命令。
如需新增和叫用命令的詳細資訊，請參閱[新增和](adding-and-invoking-commands.md)叫用命令。

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

## <a name="see-also"></a>另請參閱

[建立受條件約束的運行空間](creating-a-constrained-runspace.md)

[新增和叫用命令](adding-and-invoking-commands.md)
