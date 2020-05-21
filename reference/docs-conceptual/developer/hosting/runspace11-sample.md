---
title: Runspace11 範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c90d268-730b-4e73-9dfd-5f288c27aed0
caps.latest.revision: 8
ms.openlocfilehash: 606f06339d0bbec3393c6b2602df3636c1f4e458
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83565378"
---
# <a name="runspace11-sample"></a><span data-ttu-id="44fdd-102">Runspace11 範例</span><span class="sxs-lookup"><span data-stu-id="44fdd-102">Runspace11 Sample</span></span>

<span data-ttu-id="44fdd-103">這個範例會示範如何使用[Proxycommand](/dotnet/api/System.Management.Automation.ProxyCommand)類別來建立 proxy 命令，以呼叫現有的 Cmdlet，但會限制可用的參數集合。</span><span class="sxs-lookup"><span data-stu-id="44fdd-103">This sample shows how to use the [System.Management.Automation.Proxycommand](/dotnet/api/System.Management.Automation.ProxyCommand) class to create a proxy command that calls an existing cmdlet, but restricts the set of available parameters.</span></span> <span data-ttu-id="44fdd-104">Proxy 命令接著會加入用來建立受限 Runspace 的初始工作階段狀態。</span><span class="sxs-lookup"><span data-stu-id="44fdd-104">The proxy command is then added to an initial session state that is used to create a constrained runspace.</span></span> <span data-ttu-id="44fdd-105">這表示使用者只能透過 Proxy 命令使用此 Cmdlet 的功能。</span><span class="sxs-lookup"><span data-stu-id="44fdd-105">This means that the user can access the functionality of the cmdlet only through the proxy command.</span></span>

## <a name="requirements"></a><span data-ttu-id="44fdd-106">需求</span><span class="sxs-lookup"><span data-stu-id="44fdd-106">Requirements</span></span>

<span data-ttu-id="44fdd-107">此範例需要 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="44fdd-107">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="44fdd-108">示範</span><span class="sxs-lookup"><span data-stu-id="44fdd-108">Demonstrates</span></span>

<span data-ttu-id="44fdd-109">這個範例會示範下列各項。</span><span class="sxs-lookup"><span data-stu-id="44fdd-109">This sample demonstrates the following.</span></span>

- <span data-ttu-id="44fdd-110">建立[Commandmetadata](/dotnet/api/System.Management.Automation.CommandMetadata)物件，以描述現有 Cmdlet 的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="44fdd-110">Creating a [System.Management.Automation.Commandmetadata](/dotnet/api/System.Management.Automation.CommandMetadata) object that describes the metadata of an existing cmdlet.</span></span>

- <span data-ttu-id="44fdd-111">建立[Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)物件的程式。</span><span class="sxs-lookup"><span data-stu-id="44fdd-111">Creating an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="44fdd-112">修改 Cmdlet 中繼資料以移除 Cmdlet 的參數。</span><span class="sxs-lookup"><span data-stu-id="44fdd-112">Modifying the cmdlet metadata to remove a parameter of the cmdlet.</span></span>

- <span data-ttu-id="44fdd-113">將 Cmdlet 新增至[Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)物件，並將此 Cmdlet 設為私用。</span><span class="sxs-lookup"><span data-stu-id="44fdd-113">Adding the cmdlet to the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object and making the cmdlet private.</span></span>

- <span data-ttu-id="44fdd-114">建立可呼叫現有 Cmdlet 的 proxy 函式，但只會公開一組受限的參數。</span><span class="sxs-lookup"><span data-stu-id="44fdd-114">Creating a proxy function that calls the existing cmdlet, but exposes only a restricted set of parameters.</span></span>

- <span data-ttu-id="44fdd-115">將 proxy 函式加入至初始會話狀態。</span><span class="sxs-lookup"><span data-stu-id="44fdd-115">Adding the proxy function to the initial session state.</span></span>

- <span data-ttu-id="44fdd-116">建立使用[管理元件](/dotnet/api/System.Management.Automation.Runspaces.Runspace)[物件的 system.servicemodel 物件，](/dotnet/api/system.management.automation.powershell)它會使用工作空間。</span><span class="sxs-lookup"><span data-stu-id="44fdd-116">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object that uses the [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object.</span></span>

- <span data-ttu-id="44fdd-117">使用[system.web](/dotnet/api/system.management.automation.powershell)物件呼叫私用 Cmdlet 和 proxy 函式，以示範受限的運行空間。</span><span class="sxs-lookup"><span data-stu-id="44fdd-117">Calling the private cmdlet and the proxy function using a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object to demonstrate the constrained runspace.</span></span>

## <a name="example"></a><span data-ttu-id="44fdd-118">範例</span><span class="sxs-lookup"><span data-stu-id="44fdd-118">Example</span></span>

<span data-ttu-id="44fdd-119">這會建立私用 Cmdlet 的 proxy 命令，以示範受限的運行空間。</span><span class="sxs-lookup"><span data-stu-id="44fdd-119">This creates a proxy command for a private cmdlet to demonstrate a constrained runspace.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections.Generic;
  using System.Diagnostics;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  #region GetProcCommand

  /// <summary>
  /// This class implements the get-proc cmdlet. It has been copied
  /// verbatim from the GetProcessSample02.cs sample.
  /// </summary>
  [Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
  {
    #region Parameters

    /// <summary>
    /// The names of the processes to act on.
    /// </summary>
    private string[] processNames;

    /// <summary>
    /// Gets or sets the list of process names on which
    /// the Get-Proc cmdlet will work.
    /// </summary>
    [Parameter(Position = 0)]
    [ValidateNotNullOrEmpty]
    public string[] Name
    {
      get { return this.processNames; }
      set { this.processNames = value; }
    }

    #endregion Parameters

    #region Cmdlet Overrides

    /// <summary>
    /// The ProcessRecord method calls the Process.GetProcesses
    /// method to retrieve the processes specified by the Name
    /// parameter. Then, the WriteObject method writes the
    /// associated processes to the pipeline.
    /// </summary>
    protected override void ProcessRecord()
    {
      // If no process names are passed to the cmdlet, get all
      // processes.
      if (this.processNames == null)
      {
        WriteObject(Process.GetProcesses(), true);
      }
      else
      {
        // If process names are passed to cmdlet, get and write
        // the associated processes.
        foreach (string name in this.processNames)
        {
          WriteObject(Process.GetProcessesByName(name), true);
        }
      } // if (processNames...
    } // ProcessRecord

    #endregion Cmdlet Overrides
  } // GetProcCommand

  #endregion GetProcCommand

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace11
  {
    /// <summary>
    /// This shows how to use the ProxyCommand class to create a proxy
    /// command that calls an existing cmdlet, but restricts the set of
    /// available parameters. The proxy command is then added to an initial
    /// session state that is used to create a constrained runspace. This
    /// means that the user can access the cmdlet only through the proxy
    /// command.
    /// </summary>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a CommandMetadata object that describes the metadata of an
    ///    existing cmdlet.
    /// 2. Modifying the cmdlet metadata to remove a parameter of the cmdlet.
    /// 3. Adding the cmdlet to an initial session state and making it private.
    /// 4. Creating a proxy function that calls the existing cmdlet, but exposes
    ///    only a restricted set of parameters.
    /// 6. Adding the proxy function to the initial session state.
    /// 7. Calling the private cmdlet and the proxy function to demonstrate the
    ///    constrained runspace.
    /// </remarks>
    private static void Main()
    {
      // Create a default initial session state. The default initial session state
      // includes all the elements that are provided by Windows PowerShell.
      InitialSessionState iss = InitialSessionState.CreateDefault();

      // Add the get-proc cmdlet to the initial session state.
      SessionStateCmdletEntry cmdletEntry = new SessionStateCmdletEntry("get-proc", typeof(GetProcCommand), null);
      iss.Commands.Add(cmdletEntry);

      // Make the cmdlet private so that it is not accessible.
      cmdletEntry.Visibility = SessionStateEntryVisibility.Private;

      // Set the language mode of the initial session state to NoLanguage to
      //prevent users from using language features. Only the invocation of
      // public commands is allowed.
      iss.LanguageMode = PSLanguageMode.NoLanguage;

      // Create the proxy command using cmdlet metadata to expose the
      // get-proc cmdlet.
      CommandMetadata cmdletMetadata = new CommandMetadata(typeof(GetProcCommand));

      // Remove one of the parameters from the command metadata.
      cmdletMetadata.Parameters.Remove("Name");

      // Generate the body of a proxy function that calls the original cmdlet,
      // but does not have the removed parameter.
      string bodyOfProxyFunction = ProxyCommand.Create(cmdletMetadata);

      // Add the proxy function to the initial session state. The name of the proxy
      // function can be the same as the name of the cmdlet, but to clearly
      // demonstrate that the original cmdlet is not available a different name is
      // used for the proxy function.
      iss.Commands.Add(new SessionStateFunctionEntry("get-procProxy", bodyOfProxyFunction));

      // Create the constrained runspace using the initial session state.
      using (Runspace myRunspace = RunspaceFactory.CreateRunspace(iss))
      {
        myRunspace.Open();

        // Call the private cmdlet to demonstrate that it is not available.
        try
        {
          using (PowerShell powershell = PowerShell.Create())
          {
            powershell.Runspace = myRunspace;
            powershell.AddCommand("get-proc").AddParameter("Name", "*explore*");
            powershell.Invoke();
          }
        }
        catch (CommandNotFoundException e)
        {
          System.Console.WriteLine(
                        "Invoking 'get-proc' failed as expected: {0}: {1}",
                        e.GetType().FullName,
                        e.Message);
        }

        // Call the proxy function to demonstrate that the -Name parameter is
        // not available.
        try
        {
          using (PowerShell powershell = PowerShell.Create())
          {
            powershell.Runspace = myRunspace;
            powershell.AddCommand("get-procProxy").AddParameter("Name", "idle");
            powershell.Invoke();
          }
        }
        catch (ParameterBindingException e)
        {
          System.Console.WriteLine(
                        "\nInvoking 'get-procProxy -Name idle' failed as expected: {0}: {1}",
                        e.GetType().FullName,
                        e.Message);
        }

        // Call the proxy function to demonstrate that it calls into the
        // private cmdlet to retrieve the processes.
        using (PowerShell powershell = PowerShell.Create())
        {
          powershell.Runspace = myRunspace;
          powershell.AddCommand("get-procProxy");
          List<Process> processes = new List<Process>(powershell.Invoke<Process>());
          System.Console.WriteLine(
                        "\nInvoking the get-procProxy function called into the get-proc cmdlet and returned {0} processes",
                        processes.Count);
        }

        // Close the runspace to release resources.
        myRunspace.Close();
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="44fdd-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44fdd-120">See Also</span></span>

[<span data-ttu-id="44fdd-121">撰寫 Windows PowerShell 主機應用程式</span><span class="sxs-lookup"><span data-stu-id="44fdd-121">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)
