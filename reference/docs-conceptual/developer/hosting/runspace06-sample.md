---
title: Runspace06 範例 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c16324c61ee3c7123777294952999f75b2f7aef2
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87771986"
---
# <a name="runspace06-sample"></a><span data-ttu-id="1974e-102">Runspace06 範例</span><span class="sxs-lookup"><span data-stu-id="1974e-102">Runspace06 Sample</span></span>

<span data-ttu-id="1974e-103">這個範例會示範如何將模組新增至[System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)物件，以便在開啟執行時間時載入模組。</span><span class="sxs-lookup"><span data-stu-id="1974e-103">This sample shows how to add a module to an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object so that the module is loaded when the runspace is opened.</span></span> <span data-ttu-id="1974e-104">此模組會提供[GetProcessSample02 範例](../cmdlet/getprocesssample02-sample.md)) 所定義的 (，此 Cmdlet 是以同步方式使用[system.web](/dotnet/api/system.management.automation.powershell)物件來執行。</span><span class="sxs-lookup"><span data-stu-id="1974e-104">The module provides a Get-Proc cmdlet (defined by the [GetProcessSample02 Sample](../cmdlet/getprocesssample02-sample.md)) that is run synchronously by using a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

## <a name="requirements"></a><span data-ttu-id="1974e-105">需求</span><span class="sxs-lookup"><span data-stu-id="1974e-105">Requirements</span></span>

<span data-ttu-id="1974e-106">此範例需要 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="1974e-106">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="1974e-107">示範</span><span class="sxs-lookup"><span data-stu-id="1974e-107">Demonstrates</span></span>

<span data-ttu-id="1974e-108">這個範例會示範下列各項。</span><span class="sxs-lookup"><span data-stu-id="1974e-108">This sample demonstrates the following.</span></span>

- <span data-ttu-id="1974e-109">建立[System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)物件。</span><span class="sxs-lookup"><span data-stu-id="1974e-109">Creating an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="1974e-110">將模組新增至[System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)物件。</span><span class="sxs-lookup"><span data-stu-id="1974e-110">Adding the module to the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="1974e-111">建立一個使用[System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)物件的 system.servicemodel. 工作[空間](/dotnet/api/System.Management.Automation.Runspaces.Runspace)物件。</span><span class="sxs-lookup"><span data-stu-id="1974e-111">Creating a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object that uses the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="1974e-112">建立使用此運行空間的[system.web](/dotnet/api/system.management.automation.powershell)物件。</span><span class="sxs-lookup"><span data-stu-id="1974e-112">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object that uses the runspace.</span></span>

- <span data-ttu-id="1974e-113">將模組的 get-proc Cmdlet 新增至[system.web](/dotnet/api/system.management.automation.powershell)物件的管線。</span><span class="sxs-lookup"><span data-stu-id="1974e-113">Adding the module's get-proc cmdlet to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="1974e-114">同步執行命令。</span><span class="sxs-lookup"><span data-stu-id="1974e-114">Running the command synchronously.</span></span>

- <span data-ttu-id="1974e-115">從命令所傳回的[system.web](/dotnet/api/System.Management.Automation.PSObject)物件中，解壓縮屬性。</span><span class="sxs-lookup"><span data-stu-id="1974e-115">Extracting properties from the [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects returned by the command.</span></span>

## <a name="example"></a><span data-ttu-id="1974e-116">範例</span><span class="sxs-lookup"><span data-stu-id="1974e-116">Example</span></span>

<span data-ttu-id="1974e-117">這個範例會建立一個使用[System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)物件的執行時間，以定義當執行時間開啟時可用的元素。</span><span class="sxs-lookup"><span data-stu-id="1974e-117">This sample creates a runspace that uses an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object to define the elements that are available when the runspace is opened.</span></span> <span data-ttu-id="1974e-118">在此範例中，會將定義 Proc Cmdlet 的模組新增至初始會話狀態。</span><span class="sxs-lookup"><span data-stu-id="1974e-118">In this sample, a module that defines a Get-Proc cmdlet is added to the initial session state.</span></span>

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
  internal class Runspace06
  {
    /// <summary>
    /// This sample shows how to define an initial session state that is
    /// used when creating a runspace. The sample invokes a command from
    /// a binary module that is loaded by the initial session state.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    /// <remarks>
    /// This sample assumes that user has coppied the GetProcessSample02.dll
    /// that is produced by the GetProcessSample02 sample to the current
    /// directory.
    /// This sample demonstrates the following:
    /// 1. Creating a default initial session state.
    /// 2. Adding a module to the initial session state.
    /// 3. Creating a runspace that uses the initial session state.
    /// 4. Creating a PowerShell object that uses the runspace.
    /// 5. Adding the module's get-proc cmdlet to the PowerShell object.
    /// 6. Running the command synchronously.
    /// 7. Using PSObject objects to extract and display properties from
    ///    the objects returned by the cmdlet.
    /// </remarks>
    private static void Main(string[] args)
    {
        // Create the default initial session state and add the module.
      InitialSessionState iss = InitialSessionState.CreateDefault();
      iss.ImportPSModule(new string[] { @".\GetProcessSample02.dll" });

      // Create a runspace. Notice that no PSHost object is supplied to the
      // CreateRunspace method so the default host is used. See the Host
      // samples for more information on creating your own custom host.
      using (Runspace myRunSpace = RunspaceFactory.CreateRunspace(iss))
      {
        myRunSpace.Open();

        // Create a PowerShell object.
        using (PowerShell powershell = PowerShell.Create())
        {
          // Add the cmdlet and specify the runspace.
          powershell.AddCommand(@"GetProcessSample02\get-proc");
          powershell.Runspace = myRunSpace;

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

## <a name="see-also"></a><span data-ttu-id="1974e-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1974e-119">See Also</span></span>

[<span data-ttu-id="1974e-120">撰寫 Windows PowerShell 主機應用程式</span><span class="sxs-lookup"><span data-stu-id="1974e-120">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)
