---
title: Runspace01 範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42c1c59c-6da5-4cda-9562-e8059177fee1
caps.latest.revision: 11
ms.openlocfilehash: eec9c616fc6d5240db185f764a3ea2c8f9575d03
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367417"
---
# <a name="runspace01-sample"></a>Runspace01 範例

這個範例示範如何使用[system.web](/dotnet/api/system.management.automation.powershell)類別，以同步方式執行「[處理常式](/powershell/module/Microsoft.PowerShell.Management/Get-Process)」 Cmdlet。 [取得程式](/powershell/module/Microsoft.PowerShell.Management/Get-Process)指令程式會針對在本機電腦上執行的每個進程傳回[system.webserver。](/dotnet/api/System.Diagnostics.Process) 然後，系統會從傳回的物件中將[Processname *](/dotnet/api/System.Diagnostics.Process.ProcessName)和[Handlecount *](/dotnet/api/System.Diagnostics.Process.Handlecount)屬性的值解壓縮，並顯示在主控台視窗中。

## <a name="requirements"></a>需求

 此範例需要 Windows PowerShell 2.0。

## <a name="demonstrates"></a>演示

- 建立要執行命令的[system.web](/dotnet/api/system.management.automation.powershell)物件。

- 將命令新增至[system.web](/dotnet/api/system.management.automation.powershell)物件的管線。

- 同步執行命令。

- 使用[system.web](/dotnet/api/System.Management.Automation.PSObject)物件，從命令所傳回的物件中解壓縮屬性。

## <a name="example"></a>範例

 這個範例會在 Windows PowerShell 所提供的預設執行時間中，以同步方式執行「[取得進程](/powershell/module/Microsoft.PowerShell.Management/Get-Process)」 Cmdlet。

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
