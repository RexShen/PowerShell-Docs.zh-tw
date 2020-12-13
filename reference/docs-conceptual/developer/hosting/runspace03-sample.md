---
ms.date: 09/13/2016
ms.topic: reference
title: Runspace03 範例
description: Runspace03 範例
ms.openlocfilehash: fff699bf0545bb1419aa45b8c46bbd9c2cf0a99e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657856"
---
# <a name="runspace03-sample"></a><span data-ttu-id="44020-103">Runspace03 範例</span><span class="sxs-lookup"><span data-stu-id="44020-103">Runspace03 Sample</span></span>

<span data-ttu-id="44020-104">這個範例會示範如何使用 system.string [類別來](/dotnet/api/system.management.automation.powershell) 同步執行腳本，以及如何處理非終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="44020-104">This sample shows how to use the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class to run a script synchronously, and how to handle non-terminating errors.</span></span> <span data-ttu-id="44020-105">指令碼會接收處理序名稱的清單，然後擷取這些處理序。</span><span class="sxs-lookup"><span data-stu-id="44020-105">The script receives a list of process names and then retrieves those processes.</span></span> <span data-ttu-id="44020-106">指令碼的結果會顯示在主控台視窗中，包括執行指令碼時所產生的任何非終止錯誤在內。</span><span class="sxs-lookup"><span data-stu-id="44020-106">The results of the script, including any non-terminating errors that were generated when running the script, are displayed in a console window.</span></span>

## <a name="requirements"></a><span data-ttu-id="44020-107">規格需求</span><span class="sxs-lookup"><span data-stu-id="44020-107">Requirements</span></span>

<span data-ttu-id="44020-108">此範例需要 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="44020-108">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="44020-109">示範</span><span class="sxs-lookup"><span data-stu-id="44020-109">Demonstrates</span></span>

<span data-ttu-id="44020-110">這個範例會示範下列各項。</span><span class="sxs-lookup"><span data-stu-id="44020-110">This sample demonstrates the following.</span></span>

- <span data-ttu-id="44020-111">建立要執行腳本的 [系統. 管理. Powershell](/dotnet/api/system.management.automation.powershell) 物件。</span><span class="sxs-lookup"><span data-stu-id="44020-111">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object to run a script.</span></span>

- <span data-ttu-id="44020-112">將腳本加入至 [system.object](/dotnet/api/system.management.automation.powershell) 物件的管線。</span><span class="sxs-lookup"><span data-stu-id="44020-112">Adding a script to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="44020-113">將輸入物件從呼叫程式傳遞至腳本。</span><span class="sxs-lookup"><span data-stu-id="44020-113">Passing input objects to the script from the calling program.</span></span>

- <span data-ttu-id="44020-114">以同步方式執行腳本。</span><span class="sxs-lookup"><span data-stu-id="44020-114">Running the script synchronously.</span></span>

- <span data-ttu-id="44020-115">使用 [system.string](/dotnet/api/System.Management.Automation.PSObject) 物件，從腳本所傳回的物件中解壓縮並顯示內容。</span><span class="sxs-lookup"><span data-stu-id="44020-115">Using [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects to extract and display properties from the objects returned by the script.</span></span>

- <span data-ttu-id="44020-116">抓取並顯示腳本執行時所產生的錯誤記錄。</span><span class="sxs-lookup"><span data-stu-id="44020-116">Retrieving and displaying error records that were generated when the script was run.</span></span>

## <a name="example"></a><span data-ttu-id="44020-117">範例</span><span class="sxs-lookup"><span data-stu-id="44020-117">Example</span></span>

<span data-ttu-id="44020-118">這個範例會在 Windows PowerShell 所提供的預設執行空間中，以同步方式執行腳本。</span><span class="sxs-lookup"><span data-stu-id="44020-118">This sample runs a script synchronously in the default runspace provided by Windows PowerShell.</span></span> <span data-ttu-id="44020-119">腳本的輸出和產生的任何非終止錯誤都會顯示在主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="44020-119">The output of the script and any non-terminating errors that were generated are displayed in a console window.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace03
  {
    /// <summary>
    /// This sample shows how to use the PowerShell class to run a
    /// script that retrieves process information for the list of
    /// process names passed to the script. It shows how to pass input
    /// objects to a script and how to retrieve error objects as well
    /// as the output objects.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a PowerSHell object to run a script.
    /// 2. Adding a script to the pipeline of the PowerShell object.
    /// 3. Passing input objects to the script from the calling program.
    /// 4. Running the script synchronously.
    /// 5. Using PSObject objects to extract and display properties from
    ///    the objects returned by the script.
    /// 6. Retrieving and displaying error records that were generated
    ///    when the script was run.
    /// </remarks>
    private static void Main(string[] args)
    {
      // Define a list of processes to look for.
      string[] processNames = new string[]
      {
        "lsass", "nosuchprocess", "services", "nosuchprocess2"
      };

      // The script to run to get these processes. Input passed
      // to the script will be available in the $input variable.
      string script = "$input | get-process -name {$_}";

      // Create a PowerShell object. Creating this object takes care of
      // building all of the other data structures needed to run the script.
      using (PowerShell powershell = PowerShell.Create())
      {
        powershell.AddScript(script);

        Console.WriteLine("Process              HandleCount");
        Console.WriteLine("--------------------------------");

        // Invoke the script synchronously and display the
        // ProcessName and HandleCount properties of the
        // objects that are returned.
        foreach (PSObject result in powershell.Invoke(processNames))
        {
          Console.WriteLine(
                            "{0,-20} {1}",
                            result.Members["ProcessName"].Value,
                            result.Members["HandleCount"].Value);
        }

        // Process any error records that were generated while running
        //  the script.
        Console.WriteLine("\nThe following non-terminating errors occurred:\n");
        PSDataCollection<ErrorRecord> errors = powershell.Streams.Error;
        if (errors != null && errors.Count > 0)
        {
          foreach (ErrorRecord err in errors)
          {
            System.Console.WriteLine("    error: {0}", err.ToString());
          }
        }
      }

      System.Console.WriteLine("\nHit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="44020-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44020-120">See Also</span></span>

[<span data-ttu-id="44020-121">撰寫 Windows PowerShell 主機應用程式</span><span class="sxs-lookup"><span data-stu-id="44020-121">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)
