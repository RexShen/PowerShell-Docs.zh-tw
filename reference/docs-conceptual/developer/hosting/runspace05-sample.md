---
title: Runspace05 範例 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 2d274028d2357a26cd75cf70a033abbf907f5c4d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772156"
---
# <a name="runspace05-sample"></a><span data-ttu-id="a8f40-102">Runspace05 範例</span><span class="sxs-lookup"><span data-stu-id="a8f40-102">Runspace05 Sample</span></span>

<span data-ttu-id="a8f40-103">這個範例示範如何將嵌入式管理單元新增至[System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)物件，以便在開啟執行時間時使用嵌入式管理單元的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a8f40-103">This sample shows how to add a snap-in to an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object so that the cmdlet of the snap-in is available when the runspace is opened.</span></span> <span data-ttu-id="a8f40-104">此嵌入式管理單元提供的[GetProcessSample01 範例](../cmdlet/getprocesssample01-sample.md)) 所定義的 (，會以同步方式使用[system.web](/dotnet/api/system.management.automation.powershell)物件來執行。</span><span class="sxs-lookup"><span data-stu-id="a8f40-104">The snap-in provides a Get-Proc cmdlet (defined by the [GetProcessSample01 Sample](../cmdlet/getprocesssample01-sample.md)) that is run synchronously by using a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

## <a name="requirements"></a><span data-ttu-id="a8f40-105">需求</span><span class="sxs-lookup"><span data-stu-id="a8f40-105">Requirements</span></span>

<span data-ttu-id="a8f40-106">此範例需要 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="a8f40-106">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="a8f40-107">示範</span><span class="sxs-lookup"><span data-stu-id="a8f40-107">Demonstrates</span></span>

<span data-ttu-id="a8f40-108">這個範例會示範下列各項。</span><span class="sxs-lookup"><span data-stu-id="a8f40-108">This sample demonstrates the following.</span></span>

- <span data-ttu-id="a8f40-109">建立[System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)物件。</span><span class="sxs-lookup"><span data-stu-id="a8f40-109">Creating an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="a8f40-110">將嵌入式管理單元新增至[System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)物件。</span><span class="sxs-lookup"><span data-stu-id="a8f40-110">Adding the snap-in to the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="a8f40-111">建立一個使用[System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)物件的 system.servicemodel. 工作[空間](/dotnet/api/System.Management.Automation.Runspaces.Runspace)物件。</span><span class="sxs-lookup"><span data-stu-id="a8f40-111">Creating a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object that uses the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="a8f40-112">建立使用此運行空間的[system.web](/dotnet/api/system.management.automation.powershell)物件。</span><span class="sxs-lookup"><span data-stu-id="a8f40-112">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object that uses the runspace.</span></span>

- <span data-ttu-id="a8f40-113">將嵌入式管理單元的 get-proc Cmdlet 新增至[system.web](/dotnet/api/system.management.automation.powershell)物件的管線。</span><span class="sxs-lookup"><span data-stu-id="a8f40-113">Adding the snap-in's get-proc cmdlet to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="a8f40-114">同步執行命令。</span><span class="sxs-lookup"><span data-stu-id="a8f40-114">Running the command synchronously.</span></span>

- <span data-ttu-id="a8f40-115">從命令所傳回的[system.web](/dotnet/api/System.Management.Automation.PSObject)物件中，解壓縮屬性。</span><span class="sxs-lookup"><span data-stu-id="a8f40-115">Extracting properties from the [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects returned by the command.</span></span>

## <a name="example"></a><span data-ttu-id="a8f40-116">範例</span><span class="sxs-lookup"><span data-stu-id="a8f40-116">Example</span></span>

<span data-ttu-id="a8f40-117">這個範例會建立一個使用[System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)物件的執行時間，以定義當執行時間開啟時可用的元素。</span><span class="sxs-lookup"><span data-stu-id="a8f40-117">This sample creates a runspace that uses an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object to define the elements that are available when the runspace is opened.</span></span> <span data-ttu-id="a8f40-118">在此範例中，會將定義 Proc Cmdlet 的嵌入式管理單元新增至初始會話狀態。</span><span class="sxs-lookup"><span data-stu-id="a8f40-118">In this sample, a snap-in that defines a Get-Proc cmdlet is added to the initial session state.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a8f40-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8f40-119">See Also</span></span>

[<span data-ttu-id="a8f40-120">撰寫 Windows PowerShell 主機應用程式</span><span class="sxs-lookup"><span data-stu-id="a8f40-120">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)
