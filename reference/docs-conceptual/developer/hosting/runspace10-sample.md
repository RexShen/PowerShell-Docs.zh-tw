---
title: Runspace10 範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c265084-e072-46ca-9844-c3c0e275d6b0
caps.latest.revision: 7
ms.openlocfilehash: 1a73c0b6731073b1bac941e323416e8c45d2c252
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83565235"
---
# <a name="runspace10-sample"></a><span data-ttu-id="ab5aa-102">Runspace10 範例</span><span class="sxs-lookup"><span data-stu-id="ab5aa-102">Runspace10 Sample</span></span>

<span data-ttu-id="ab5aa-103">這個範例會示範如何建立預設初始會話狀態、如何將 Cmdlet 新增至[Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)、如何建立使用初始會話狀態的執行時間，以及如何使用[system.web](/dotnet/api/system.management.automation.powershell)物件來執行此命令，以及如何執行該命令。</span><span class="sxs-lookup"><span data-stu-id="ab5aa-103">This sample shows how to create a default initial session state, how to add a cmdlet to the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState), how to create a runspace that uses the initial session state, and how to run the command by using a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

## <a name="requirements"></a><span data-ttu-id="ab5aa-104">需求</span><span class="sxs-lookup"><span data-stu-id="ab5aa-104">Requirements</span></span>

<span data-ttu-id="ab5aa-105">此範例需要 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="ab5aa-105">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="ab5aa-106">示範</span><span class="sxs-lookup"><span data-stu-id="ab5aa-106">Demonstrates</span></span>

<span data-ttu-id="ab5aa-107">這個範例會示範下列各項。</span><span class="sxs-lookup"><span data-stu-id="ab5aa-107">This sample demonstrates the following.</span></span>

- <span data-ttu-id="ab5aa-108">建立[Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)物件的程式。</span><span class="sxs-lookup"><span data-stu-id="ab5aa-108">Creating an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="ab5aa-109">將 Cmdlet （由主應用程式定義）新增至[Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)物件。</span><span class="sxs-lookup"><span data-stu-id="ab5aa-109">Adding a cmdlet (defined by the Host application) to the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="ab5aa-110">建立使用物件的[system.web 工作空間](/dotnet/api/System.Management.Automation.Runspaces.Runspace)物件。</span><span class="sxs-lookup"><span data-stu-id="ab5aa-110">Creating a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object that uses the object.</span></span>

- <span data-ttu-id="ab5aa-111">建立使用[管理元件](/dotnet/api/System.Management.Automation.Runspaces.Runspace)[物件的 system.servicemodel 物件，](/dotnet/api/system.management.automation.powershell)它會使用工作空間。</span><span class="sxs-lookup"><span data-stu-id="ab5aa-111">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object that uses the [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object.</span></span>

- <span data-ttu-id="ab5aa-112">將命令新增至[system.web](/dotnet/api/system.management.automation.powershell)物件的管線。</span><span class="sxs-lookup"><span data-stu-id="ab5aa-112">Adding the command to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="ab5aa-113">從命令所傳回的[system.web](/dotnet/api/System.Management.Automation.PSObject)物件中，解壓縮屬性。</span><span class="sxs-lookup"><span data-stu-id="ab5aa-113">Extracting properties from the [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects returned by the command.</span></span>

## <a name="example"></a><span data-ttu-id="ab5aa-114">範例</span><span class="sxs-lookup"><span data-stu-id="ab5aa-114">Example</span></span>

<span data-ttu-id="ab5aa-115">這個範例會建立一個使用[Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)物件的執行時間，以定義當執行時間開啟時可用的元素。</span><span class="sxs-lookup"><span data-stu-id="ab5aa-115">This sample creates a runspace that uses an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object to define the elements that are available when the runspace is opened.</span></span> <span data-ttu-id="ab5aa-116">在此範例中，會在初始會話狀態中新增 Get-Proc Cmdlet （由主應用程式定義），而 Cmdlet 會使用[system.web](/dotnet/api/system.management.automation.powershell)物件同步執行。</span><span class="sxs-lookup"><span data-stu-id="ab5aa-116">In this sample, the Get-Proc cmdlet (defined by the Host application) is added to the initial session state, and the cmdlet is run synchronously by using a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections.Generic;
  using System.Collections.ObjectModel;
  using System.Diagnostics;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  #region GetProcCommand

  /// <summary>
  /// Class that implements the GetProcCommand.
  /// </summary>
  [Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
  {
    #region Cmdlet Overrides

    /// <summary>
    /// For each of the requested process names, retrieve and write
    /// the associated processes.
    /// </summary>
    protected override void ProcessRecord()
    {
      // Get the current processes.
      Process[] processes = Process.GetProcesses();

      // Write the processes to the pipeline making them available
      // to the next cmdlet. The second argument (true) tells the
      // system to enumerate the array, and send one process object
      // at a time to the pipeline.
      WriteObject(processes, true);
    }

    #endregion Overrides
  } // End GetProcCommand class.

  #endregion GetProcCommand

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace10
  {
    /// <summary>
    /// This sample shows how to create a default initial session state, how to add
    /// add a cmdlet to the InitialSessionState object, and then how to create
    /// a Runspace object.
    /// </summary>
    /// <param name="args">Parameter is not used.</param>
    /// This sample demonstrates:
    /// 1. Creating an InitialSessionState object.
    /// 2. Adding a cmdlet to the InitialSessionState object.
    /// 3. Creating a runspace that uses the InitialSessionState object.
    /// 4. Creating a PowerShell object that uses the Runspace object.
    /// 5. Running the added command synchronously.
    /// 6. Working with PSObject objects to extract properties
    ///    from the objects returned by the pipeline.
    private static void Main(string[] args)
    {
      // Create a default InitialSessionState object. The default
      // InitialSessionState object contains all the elements provided
      // by Windows PowerShell.
      InitialSessionState iss = InitialSessionState.CreateDefault();

      // Add the get-proc cmdlet to the InitialSessionState object.
      SessionStateCmdletEntry ssce = new SessionStateCmdletEntry("get-proc", typeof(GetProcCommand), null);
      iss.Commands.Add(ssce);

      // Create a Runspace object that uses the InitialSessionState object.
      // Notice that no PSHost object is specified, so the default host is used.
      // See the Hosting samples for information on creating your own custom host.
      using (Runspace myRunSpace = RunspaceFactory.CreateRunspace(iss))
      {
        myRunSpace.Open();

        using (PowerShell powershell = PowerShell.Create())
        {
          powershell.Runspace = myRunSpace;

          // Add the get-proc cmdlet to the pipeline of the PowerShell object.
          powershell.AddCommand("get-proc");

          Collection<PSObject> results = powershell.Invoke();

          Console.WriteLine("Process              HandleCount");
          Console.WriteLine("--------------------------------");

          // Display the output of the pipeline.
          foreach (PSObject result in results)
          {
             Console.WriteLine(
                               "{0,-20} {1}",
                               result.Members["ProcessName"].Value,
                               result.Members["HandleCount"].Value);
          }
        }

        // Close the runspace to release resources.
        myRunSpace.Close();
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="ab5aa-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab5aa-117">See Also</span></span>

[<span data-ttu-id="ab5aa-118">撰寫 Windows PowerShell 主機應用程式</span><span class="sxs-lookup"><span data-stu-id="ab5aa-118">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)
