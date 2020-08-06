---
title: Runspace09 範例 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6110fcb96af25f55682064c466ba2add6377902d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783138"
---
# <a name="runspace09-sample"></a><span data-ttu-id="49a57-102">Runspace09 範例</span><span class="sxs-lookup"><span data-stu-id="49a57-102">Runspace09 Sample</span></span>

<span data-ttu-id="49a57-103">這個範例示範如何將腳本新增至[system.web](/dotnet/api/system.management.automation.powershell)物件的管線，以及如何以非同步方式執行腳本。</span><span class="sxs-lookup"><span data-stu-id="49a57-103">This sample shows how to add a script to the pipeline of a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object and how to run the script asynchronously.</span></span> <span data-ttu-id="49a57-104">事件為用來處理指令碼的輸出。</span><span class="sxs-lookup"><span data-stu-id="49a57-104">Events are used to handle the output of the script.</span></span>

## <a name="requirements"></a><span data-ttu-id="49a57-105">需求</span><span class="sxs-lookup"><span data-stu-id="49a57-105">Requirements</span></span>

<span data-ttu-id="49a57-106">此範例需要 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="49a57-106">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="49a57-107">示範</span><span class="sxs-lookup"><span data-stu-id="49a57-107">Demonstrates</span></span>

<span data-ttu-id="49a57-108">這個範例會示範下列各項。</span><span class="sxs-lookup"><span data-stu-id="49a57-108">This sample demonstrates the following.</span></span>

- <span data-ttu-id="49a57-109">建立使用此運行空間的[system.web](/dotnet/api/system.management.automation.powershell)物件。</span><span class="sxs-lookup"><span data-stu-id="49a57-109">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object that uses the runspace.</span></span>

- <span data-ttu-id="49a57-110">將腳本新增至[system.web](/dotnet/api/system.management.automation.powershell)物件的管線。</span><span class="sxs-lookup"><span data-stu-id="49a57-110">Adding a script the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="49a57-111">使用[Begininvoke \*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke)方法，以非同步方式執行管線。</span><span class="sxs-lookup"><span data-stu-id="49a57-111">Using the [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) method to run the pipeline asynchronously.</span></span>

- <span data-ttu-id="49a57-112">使用[system.web](/dotnet/api/system.management.automation.powershell)物件的事件來處理腳本的輸出作業。」</span><span class="sxs-lookup"><span data-stu-id="49a57-112">Using the events of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object to process the output of the script.</span></span>

- <span data-ttu-id="49a57-113">使用 system.servicemodel [\*](/dotnet/api/System.Management.Automation.PowerShell.Stop)方法來中斷管線的叫用（Stop）。</span><span class="sxs-lookup"><span data-stu-id="49a57-113">Using the [System.Management.Automation.Powershell.Stop\*](/dotnet/api/System.Management.Automation.PowerShell.Stop) method to interrupt the invocation of the pipeline.</span></span>

## <a name="example"></a><span data-ttu-id="49a57-114">範例</span><span class="sxs-lookup"><span data-stu-id="49a57-114">Example</span></span>

<span data-ttu-id="49a57-115">這個範例會執行腳本，以產生從1到10的數位，而且每個數位之間會有延遲。</span><span class="sxs-lookup"><span data-stu-id="49a57-115">This sample runs to run a script that generates the numbers from 1 to 10 with delays between each number.</span></span> <span data-ttu-id="49a57-116">腳本會以非同步方式執行，並使用事件來處理輸出。</span><span class="sxs-lookup"><span data-stu-id="49a57-116">The script is run asynchronously and events are used to handle the output.</span></span>

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

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace09
  {
    /// <summary>
    /// This sample shows how to use a PowerShell object to run a
    /// script that generates the numbers from 1 to 10 with delays
    /// between each number. The pipeline of the PowerShell object
    /// is run asynchronously and events are used to handle the output.
    /// </summary>
    /// <param name="args">The parameter is not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a PowerShell object.
    /// 2. Adding a script to the pipeline of the PowerShell object.
    /// 3. Using the BeginInvoke method to run the pipeline asynchronously.
    /// 4. Using the events of the PowerShell object to process the
    ///    output of the script.
    /// 5. Using the PowerShell.Stop() method to interrupt the invocation of
    ///    the pipeline.
    /// </remarks>
    private static void Main(string[] args)
    {
      Console.WriteLine("Print the numbers from 1 to 10. Hit any key to halt processing\n");

      using (PowerShell powershell = PowerShell.Create())
      {
        // Add a script to the PowerShell object. The script generates the
        // numbers from 1 to 10 in half second intervals.
        powershell.AddScript("1..10 | foreach {$_ ; start-sleep -milli 500}");

        // Add the event handlers.  If we did not care about hooking the DataAdded
        // event, we would let BeginInvoke create the output stream for us.
        PSDataCollection<PSObject> output = new PSDataCollection<PSObject>();
        output.DataAdded += new EventHandler<DataAddedEventArgs>(Output_DataAdded);
        powershell.InvocationStateChanged += new EventHandler<PSInvocationStateChangedEventArgs>(Powershell_InvocationStateChanged);

        // Invoke the pipeline asynchronously.
        IAsyncResult asyncResult = powershell.BeginInvoke<PSObject, PSObject>(null, output);

        // Wait for things to happen. If the user hits a key before the
        // script has completed, then call the PowerShell Stop() method
        // to halt processing.
        Console.ReadKey();
        if (powershell.InvocationStateInfo.State != PSInvocationState.Completed)
        {
          // Stop the invocation of the pipeline.
          Console.WriteLine("\nStopping the pipeline!\n");
          powershell.Stop();

          // Wait for the Windows PowerShell state change messages to be displayed.
          System.Threading.Thread.Sleep(500);
          Console.WriteLine("\nPress a key to exit");
          Console.ReadKey();
        }
      }
    }

    /// <summary>
    /// The output data added event handler. This event is called when
    /// data is added to the output pipe. It reads the data that is
    /// available and displays it on the console.
    /// </summary>
    /// <param name="sender">The output pipe this event is associated with.</param>
    /// <param name="e">Parameter is not used.</param>
    private static void Output_DataAdded(object sender, DataAddedEventArgs e)
    {
      PSDataCollection<PSObject> myp = (PSDataCollection<PSObject>)sender;

      Collection<PSObject> results = myp.ReadAll();
      foreach (PSObject result in results)
      {
        Console.WriteLine(result.ToString());
      }
    }

    /// <summary>
    /// This event handler is called when the pipeline state is changed.
    /// If the state change is to Completed, the handler issues a message
    /// asking the user to exit the program.
    /// </summary>
    /// <param name="sender">This parameter is not used.</param>
    /// <param name="e">The PowerShell state information.</param>
    private static void Powershell_InvocationStateChanged(object sender, PSInvocationStateChangedEventArgs e)
    {
      Console.WriteLine("PowerShell object state changed: state: {0}\n", e.InvocationStateInfo.State);
      if (e.InvocationStateInfo.State == PSInvocationState.Completed)
      {
        Console.WriteLine("Processing completed, press a key to exit!");
      }
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="49a57-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49a57-117">See Also</span></span>

[<span data-ttu-id="49a57-118">撰寫 Windows PowerShell 主機應用程式</span><span class="sxs-lookup"><span data-stu-id="49a57-118">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)
