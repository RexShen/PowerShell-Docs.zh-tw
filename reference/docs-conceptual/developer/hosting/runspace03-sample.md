---
title: Runspace03 範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 31df99d7-6954-4fdc-b6f5-06ecba094f43
caps.latest.revision: 8
ms.openlocfilehash: 980c75b07e1c35b293d00e6f2bca828499b3bd28
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83561013"
---
# <a name="runspace03-sample"></a><span data-ttu-id="01931-102">Runspace03 範例</span><span class="sxs-lookup"><span data-stu-id="01931-102">Runspace03 Sample</span></span>

<span data-ttu-id="01931-103">這個範例會示範如何使用[system.web](/dotnet/api/system.management.automation.powershell)類別，以同步方式執行腳本，以及如何處理非終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="01931-103">This sample shows how to use the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class to run a script synchronously, and how to handle non-terminating errors.</span></span> <span data-ttu-id="01931-104">指令碼會接收處理序名稱的清單，然後擷取這些處理序。</span><span class="sxs-lookup"><span data-stu-id="01931-104">The script receives a list of process names and then retrieves those processes.</span></span> <span data-ttu-id="01931-105">指令碼的結果會顯示在主控台視窗中，包括執行指令碼時所產生的任何非終止錯誤在內。</span><span class="sxs-lookup"><span data-stu-id="01931-105">The results of the script, including any non-terminating errors that were generated when running the script, are displayed in a console window.</span></span>

## <a name="requirements"></a><span data-ttu-id="01931-106">需求</span><span class="sxs-lookup"><span data-stu-id="01931-106">Requirements</span></span>

<span data-ttu-id="01931-107">此範例需要 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="01931-107">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="01931-108">示範</span><span class="sxs-lookup"><span data-stu-id="01931-108">Demonstrates</span></span>

<span data-ttu-id="01931-109">這個範例會示範下列各項。</span><span class="sxs-lookup"><span data-stu-id="01931-109">This sample demonstrates the following.</span></span>

- <span data-ttu-id="01931-110">建立要執行腳本的[system.web](/dotnet/api/system.management.automation.powershell)物件。</span><span class="sxs-lookup"><span data-stu-id="01931-110">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object to run a script.</span></span>

- <span data-ttu-id="01931-111">將腳本新增至[system.web](/dotnet/api/system.management.automation.powershell)物件的管線。</span><span class="sxs-lookup"><span data-stu-id="01931-111">Adding a script to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="01931-112">將輸入物件從呼叫程式傳遞至腳本。</span><span class="sxs-lookup"><span data-stu-id="01931-112">Passing input objects to the script from the calling program.</span></span>

- <span data-ttu-id="01931-113">同步執行腳本。</span><span class="sxs-lookup"><span data-stu-id="01931-113">Running the script synchronously.</span></span>

- <span data-ttu-id="01931-114">使用[system.web](/dotnet/api/System.Management.Automation.PSObject)物件，從腳本傳回的物件中，解壓縮並顯示內容。</span><span class="sxs-lookup"><span data-stu-id="01931-114">Using [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects to extract and display properties from the objects returned by the script.</span></span>

- <span data-ttu-id="01931-115">正在抓取和顯示腳本執行時所產生的錯誤記錄。</span><span class="sxs-lookup"><span data-stu-id="01931-115">Retrieving and displaying error records that were generated when the script was run.</span></span>

## <a name="example"></a><span data-ttu-id="01931-116">範例</span><span class="sxs-lookup"><span data-stu-id="01931-116">Example</span></span>

<span data-ttu-id="01931-117">這個範例會在 Windows PowerShell 所提供的預設執行時間中，以同步方式執行腳本。</span><span class="sxs-lookup"><span data-stu-id="01931-117">This sample runs a script synchronously in the default runspace provided by Windows PowerShell.</span></span> <span data-ttu-id="01931-118">腳本的輸出和任何產生的非終止錯誤都會顯示在主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="01931-118">The output of the script and any non-terminating errors that were generated are displayed in a console window.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="01931-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01931-119">See Also</span></span>

[<span data-ttu-id="01931-120">撰寫 Windows PowerShell 主機應用程式</span><span class="sxs-lookup"><span data-stu-id="01931-120">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)
