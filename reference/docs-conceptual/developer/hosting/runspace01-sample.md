---
title: Runspace01 範例 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1ac286512f3cb3b97a6b3179c9dd45f1fefe1ecf
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772190"
---
# <a name="runspace01-sample"></a><span data-ttu-id="ea144-102">Runspace01 範例</span><span class="sxs-lookup"><span data-stu-id="ea144-102">Runspace01 Sample</span></span>

<span data-ttu-id="ea144-103">這個範例示範如何使用[system.web](/dotnet/api/system.management.automation.powershell)類別，以同步方式執行「[處理常式](/powershell/module/Microsoft.PowerShell.Management/Get-Process)」 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ea144-103">This sample shows how to use the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class to run the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synchronously.</span></span> <span data-ttu-id="ea144-104">[取得程式](/powershell/module/Microsoft.PowerShell.Management/Get-Process)指令程式會針對在本機電腦上執行的每個進程傳回[system.webserver。](/dotnet/api/System.Diagnostics.Process)</span><span class="sxs-lookup"><span data-stu-id="ea144-104">The [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects for each process running on the local computer.</span></span> <span data-ttu-id="ea144-105">然後，系統會從傳回的物件中將[Processname \*](/dotnet/api/System.Diagnostics.Process.ProcessName)和[Handlecount \*](/dotnet/api/System.Diagnostics.Process.Handlecount)屬性的值解壓縮，並顯示在主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="ea144-105">The values of the [System.Diagnostics.Process.Processname\*](/dotnet/api/System.Diagnostics.Process.ProcessName) and [System.Diagnostics.Process.Handlecount\*](/dotnet/api/System.Diagnostics.Process.Handlecount) properties are then extracted from the returned objects and displayed in a console window.</span></span>

## <a name="requirements"></a><span data-ttu-id="ea144-106">需求</span><span class="sxs-lookup"><span data-stu-id="ea144-106">Requirements</span></span>

 <span data-ttu-id="ea144-107">此範例需要 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="ea144-107">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="ea144-108">示範</span><span class="sxs-lookup"><span data-stu-id="ea144-108">Demonstrates</span></span>

- <span data-ttu-id="ea144-109">建立要執行命令的[system.web](/dotnet/api/system.management.automation.powershell)物件。</span><span class="sxs-lookup"><span data-stu-id="ea144-109">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object to run a command.</span></span>

- <span data-ttu-id="ea144-110">將命令新增至[system.web](/dotnet/api/system.management.automation.powershell)物件的管線。</span><span class="sxs-lookup"><span data-stu-id="ea144-110">Adding a command to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="ea144-111">同步執行命令。</span><span class="sxs-lookup"><span data-stu-id="ea144-111">Running the command synchronously.</span></span>

- <span data-ttu-id="ea144-112">使用[system.web](/dotnet/api/System.Management.Automation.PSObject)物件，從命令所傳回的物件中解壓縮屬性。</span><span class="sxs-lookup"><span data-stu-id="ea144-112">Using [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects to extract properties from the objects returned by the command.</span></span>

## <a name="example"></a><span data-ttu-id="ea144-113">範例</span><span class="sxs-lookup"><span data-stu-id="ea144-113">Example</span></span>

 <span data-ttu-id="ea144-114">這個範例會在 Windows PowerShell 所提供的預設執行時間中，以同步方式執行「[取得進程](/powershell/module/Microsoft.PowerShell.Management/Get-Process)」 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ea144-114">This sample runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synchronously in the default runspace provided by Windows PowerShell.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Management.Automation;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace01
  {
    /// <summary>
    /// This sample uses the PowerShell class to execute
    /// the get-process cmdlet synchronously. The name and
    /// handlecount are then extracted from the PSObjects
    /// returned and displayed.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a PowerShell object to run a command.
    /// 2. Adding a command to the pipeline of the PowerShell object.
    /// 3. Running the command synchronously.
    /// 4. Using PSObject objects to extract properties from the objects
    ///    returned by the command.
    /// </remarks>
    private static void Main(string[] args)
    {
      // Create a PowerShell object. Creating this object takes care of
      // building all of the other data structures needed to run the command.
      using (PowerShell powershell = PowerShell.Create().AddCommand("get-process"))
      {
        Console.WriteLine("Process              HandleCount");
        Console.WriteLine("--------------------------------");

        // Invoke the command synchronously and display the
        // ProcessName and HandleCount properties of the
        // objects that are returned.
        foreach (PSObject result in powershell.Invoke())
        {
          Console.WriteLine(
                      "{0,-20} {1}",
                      result.Members["ProcessName"].Value,
                      result.Members["HandleCount"].Value);
        }
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="ea144-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea144-115">See Also</span></span>
