---
title: 建立受條件約束的運行空間 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 30ecb80dbd96278ee9aa5a609d27bfc4eaa423e9
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779806"
---
# <a name="creating-a-constrained-runspace"></a>建立受限 Runspace

基於效能或安全性考慮，您可能會想要限制主機應用程式可使用的 Windows PowerShell 命令。 若要這麼做，您可以藉由呼叫System.Management.Automation.Runspaces.Initialsessionstate 來建立空的[System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) [。建立 *](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create)方法，然後只新增您想要使用的命令。

 使用只載入您指定之命令的運行空間，可以大幅提升效能。

 您可以使用[SessionstateCmdletentry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry)類別的方法，來定義初始會話狀態的 Cmdlet。

 您也可以將命令設為私用。 私用命令可以由主應用程式使用，而不是由應用程式的使用者所使用。

## <a name="adding-commands-to-an-empty-runspace"></a>將命令新增至空白的運行空間

 下列範例示範如何建立空的 InitialSessionState，並在其中新增命令。

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections.ObjectModel;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using Microsoft.PowerShell.Commands;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for the application.
  /// </summary>
  internal class Runspace10b
  {
    /// <summary>
    /// This sample shows how to create an empty initial session state,
    /// how to add commands to the session state, and then how to create a
    /// runspace that has only those two commands. A PowerShell object
    /// is used to run the Get-Command cmdlet to show that only two commands
    /// are available.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    private static void Main(string[] args)
    {
      // Create an empty InitialSessionState and then add two commands.
      InitialSessionState iss = InitialSessionState.Create();

      // Add the Get-Process and Get-Command cmdlets to the session state.
      SessionStateCmdletEntry ssce1 = new SessionStateCmdletEntry(
                                                            "get-process",
                                                            typeof(GetProcessCommand),
                                                            null);
      iss.Commands.Add(ssce1);

      SessionStateCmdletEntry ssce2 = new SessionStateCmdletEntry(
                                                            "get-command",
                                                            typeof(GetCommandCommand),
                                                            null);
      iss.Commands.Add(ssce2);

      // Create a runspace.
      using (Runspace myRunSpace = RunspaceFactory.CreateRunspace(iss))
      {
        myRunSpace.Open();
        using (PowerShell powershell = PowerShell.Create())
        {
          powershell.Runspace = myRunSpace;

          // Create a pipeline with the Get-Command command.
          powershell.AddCommand("get-command");

          Collection<PSObject> results = powershell.Invoke();

          Console.WriteLine("Verb                 Noun");
          Console.WriteLine("----------------------------");

          // Display each result object.
          foreach (PSObject result in results)
          {
            Console.WriteLine(
                             "{0,-20} {1}",
                             result.Members["verb"].Value,
                             result.Members["Noun"].Value);
          }
        }

        // Close the runspace and release any resources.
        myRunSpace.Close();
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="making-commands-private"></a>將命令設為私用

 您也可以藉由將命令的[Commandinfo](/dotnet/api/System.Management.Automation.CommandInfo.Visibility)設定為[SessionStateEntryVisibility](/dotnet/api/System.Management.Automation.SessionStateEntryVisibility) **private**，使其成為私用的命令。 主應用程式和其他命令可以呼叫該命令，但應用程式的使用者不能。 在下列範例中， [get-childitem](/powershell/module/Microsoft.PowerShell.Management/Get-ChildItem)命令是私用的。

```csharp
defaultSessionState = InitialSessionState.CreateDefault();
commandIndex = GetIndexOfEntry(defaultSessionState.Commands, "get-childitem");
defaultSessionState.Commands[commandIndex].Visibility = SessionStateEntryVisibility.Private;

this.runspace = RunspaceFactory.CreateRunspace(defaultSessionState);
this.runspace.Open();
```

## <a name="see-also"></a>另請參閱

 [建立 InitialSessionState](./creating-an-initialsessionstate.md)
