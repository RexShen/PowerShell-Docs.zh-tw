---
ms.date: 09/13/2016
ms.topic: reference
title: Runspace01 範例
description: Runspace01 範例
ms.openlocfilehash: f47f79dd507db258119016353dc5a72d110d9252
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657909"
---
# <a name="runspace01-sample"></a>Runspace01 範例

此範例示範如何使用 [system.servicemodel 類別，](/dotnet/api/system.management.automation.powershell) 以同步方式執行 [取得程式](/powershell/module/Microsoft.PowerShell.Management/Get-Process) Cmdlet。 [取得進程](/powershell/module/Microsoft.PowerShell.Management/Get-Process)指令程式會傳回在本機電腦上執行之每個進程的[處理常式](/dotnet/api/System.Diagnostics.Process)物件。 然後，系統會從傳回的物件中，將 [Processname *](/dotnet/api/System.Diagnostics.Process.ProcessName) 和 [Handlecount *](/dotnet/api/System.Diagnostics.Process.Handlecount) 屬性的值解壓縮，並顯示在主控台視窗中。

## <a name="requirements"></a>規格需求

 此範例需要 Windows PowerShell 2.0。

## <a name="demonstrates"></a>示範

- 建立要執行命令的 [系統. 管理](/dotnet/api/system.management.automation.powershell) 物件。

- 將命令加入至 [system.object](/dotnet/api/system.management.automation.powershell) 物件的管線。

- 以同步方式執行命令。

- 使用 [system.string](/dotnet/api/System.Management.Automation.PSObject) 物件從命令所傳回的物件中解壓縮屬性。

## <a name="example"></a>範例

 此範例會在 Windows PowerShell 所提供的預設執行空間中，以同步方式執行 [取得程式](/powershell/module/Microsoft.PowerShell.Management/Get-Process) Cmdlet。

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

## <a name="see-also"></a>另請參閱
