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
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057904"
---
# <a name="runspace01-sample"></a>Runspace01 範例

此範例示範如何使用[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)類別來執行[Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet 以同步方式。 [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet 會傳回[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)本機電腦上執行每個處理序的物件。 值[System.Diagnostics.Process.Processname*](/dotnet/api/System.Diagnostics.Process.ProcessName)並[System.Diagnostics.Process.Handlecount*](/dotnet/api/System.Diagnostics.Process.Handlecount)屬性然後從傳回的物件中擷取並顯示在主控台中視窗。

## <a name="requirements"></a>需求

 這個範例需要 Windows PowerShell 2.0。

## <a name="demonstrates"></a>示範

- 建立[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)執行命令的物件。

- 將命令加入至的管線[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)物件。

- 以同步方式執行命令。

- 使用[System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject)命令所傳回的物件中擷取屬性的物件。

## <a name="example"></a>範例

 此範例會執行[Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process)指令程式以同步方式在 Windows PowerShell 所提供的預設 runspace。

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
