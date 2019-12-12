---
title: Runspace05 範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1685cfc4-b32c-4bed-b221-e0c4482db955
caps.latest.revision: 9
ms.openlocfilehash: eb227b5fa5e91f59b6fc99981ff5affca1cf63fd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360877"
---
# <a name="runspace05-sample"></a>Runspace05 範例

這個範例會示範如何將嵌入式管理單元新增至[Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)物件，以便在開啟執行時間時可以使用嵌入式管理單元的 Cmdlet。 此嵌入式管理單元提供一個使用[GetProcessSample01 範例](../cmdlet/getprocesssample01-sample.md)所定義的「取得程式」指令程式，此 Cmdlet 是以同步方式[執行。](/dotnet/api/system.management.automation.powershell)

## <a name="requirements"></a>需求

此範例需要 Windows PowerShell 2.0。

## <a name="demonstrates"></a>示範

這個範例會示範下列各項。

- 建立[Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)物件的程式。

- 將嵌入式管理單元新增至[Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)物件中。

- 建立一個使用[Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)物件的 system.servicemodel 物件，它[是由它](/dotnet/api/System.Management.Automation.Runspaces.Runspace)所產生的。

- 建立使用此運行空間的[system.web](/dotnet/api/system.management.automation.powershell)物件。

- 將嵌入式管理單元的 get-proc Cmdlet 新增至[system.web](/dotnet/api/system.management.automation.powershell)物件的管線。

- 同步執行命令。

- 從命令所傳回的[system.web](/dotnet/api/System.Management.Automation.PSObject)物件中，解壓縮屬性。

## <a name="example"></a>範例

這個範例會建立一個使用[Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)物件的執行時間，以定義當執行時間開啟時可用的元素。 在此範例中，會將定義 Proc Cmdlet 的嵌入式管理單元新增至初始會話狀態。

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections.ObjectModel;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace05
  {
    /// <summary>
    /// This sample shows how to define an initial session state that is
    /// used when creating a runspace. The sample invokes a command from
    /// a Windows PowerShell snap-in that is present in the console file.
    /// </summary>
    /// <param name="args">The parameter is not used.</param>
    /// <remarks>
    /// This sample assumes that user has coppied the GetProcessSample01.dll
    /// that is produced by the GetProcessSample01 sample to the current
    /// directory.
    /// This sample demonstrates the following:
    /// 1. Creating a default initial session state.
    /// 2. Adding a snap-in to the initial session state.
    /// 3. Creating a runspace that uses the initial session state.
    /// 4. Creating a PowerShell object that uses the runspace.
    /// 5. Adding the snap-in's get-proc cmdlet to the PowerShell object.
    /// 6. Using PSObject objects to extract and display properties from
    ///    the objects returned by the cmdlet.
    /// </remarks>
    private static void Main(string[] args)
    {
      // Create the default initial session state. The default initial
      // session state contains all the elements provided by Windows
      // PowerShell.
      InitialSessionState iss = InitialSessionState.CreateDefault();
      PSSnapInException warning;
      iss.ImportPSSnapIn("GetProcPSSnapIn01", out warning);

      // Create a runspace. Notice that no PSHost object is supplied to the
      // CreateRunspace method so the default host is used. See the Host
      // samples for more information on creating your own custom host.
      using (Runspace myRunSpace = RunspaceFactory.CreateRunspace(iss))
      {
        myRunSpace.Open();

        // Create a PowerShell object.
        using (PowerShell powershell = PowerShell.Create())
        {
          // Add the snap-in cmdlet and specify the runspace.
          powershell.AddCommand("GetProcPSSnapIn01\\get-proc");
          powershell.Runspace = myRunSpace;

          // Run the cmdlet synchronously.
          Collection<PSObject> results = powershell.Invoke();

          Console.WriteLine("Process              HandleCount");
          Console.WriteLine("--------------------------------");

          // Display the results.
          foreach (PSObject result in results)
          {
            Console.WriteLine(
                              "{0,-20} {1}",
                              result.Members["ProcessName"].Value,
                              result.Members["HandleCount"].Value);
          }
        }

        // Close the runspace to release any resources.
        myRunSpace.Close();
      }
      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell 主應用程式](./writing-a-windows-powershell-host-application.md)