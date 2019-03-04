---
title: Runspace06 範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 471c85f3-9287-45c2-b4bc-833caa1b7634
caps.latest.revision: 8
ms.openlocfilehash: 8621878a339751d2cef842af6f5b3d5d2e270346
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862614"
---
# <a name="runspace06-sample"></a><span data-ttu-id="9ab96-102">Runspace06 範例</span><span class="sxs-lookup"><span data-stu-id="9ab96-102">Runspace06 Sample</span></span>

<span data-ttu-id="9ab96-103">此範例示範如何將模組加入[System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)物件，以便在 runspace 開啟時載入的模組。</span><span class="sxs-lookup"><span data-stu-id="9ab96-103">This sample shows how to add a module to an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object so that the module is loaded when the runspace is opened.</span></span> <span data-ttu-id="9ab96-104">模組提供 Get-proc cmdlet (由[GetProcessSample02 範例](../cmdlet/getprocesssample02-sample.md))，以同步方式執行使用[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)物件。</span><span class="sxs-lookup"><span data-stu-id="9ab96-104">The module provides a Get-Proc cmdlet (defined by the [GetProcessSample02 Sample](../cmdlet/getprocesssample02-sample.md)) that is run synchronously by using a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

## <a name="requirements"></a><span data-ttu-id="9ab96-105">需求</span><span class="sxs-lookup"><span data-stu-id="9ab96-105">Requirements</span></span>

<span data-ttu-id="9ab96-106">這個範例需要 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="9ab96-106">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="9ab96-107">示範</span><span class="sxs-lookup"><span data-stu-id="9ab96-107">Demonstrates</span></span>

<span data-ttu-id="9ab96-108">此範例示範下列項目。</span><span class="sxs-lookup"><span data-stu-id="9ab96-108">This sample demonstrates the following.</span></span>

- <span data-ttu-id="9ab96-109">建立[System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)物件。</span><span class="sxs-lookup"><span data-stu-id="9ab96-109">Creating an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="9ab96-110">新增模組[System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)物件。</span><span class="sxs-lookup"><span data-stu-id="9ab96-110">Adding the module to the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="9ab96-111">建立[System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace)使用的物件[System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)物件。</span><span class="sxs-lookup"><span data-stu-id="9ab96-111">Creating a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object that uses the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="9ab96-112">建立[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)使用 runspace 的物件。</span><span class="sxs-lookup"><span data-stu-id="9ab96-112">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object that uses the runspace.</span></span>

- <span data-ttu-id="9ab96-113">將模組的程序的 get cmdlet 新增至的管線[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)物件。</span><span class="sxs-lookup"><span data-stu-id="9ab96-113">Adding the module's get-proc cmdlet to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="9ab96-114">以同步方式執行命令。</span><span class="sxs-lookup"><span data-stu-id="9ab96-114">Running the command synchronously.</span></span>

- <span data-ttu-id="9ab96-115">擷取屬性從[System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject)命令所傳回的物件。</span><span class="sxs-lookup"><span data-stu-id="9ab96-115">Extracting properties from the [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) objects returned by the command.</span></span>

## <a name="example"></a><span data-ttu-id="9ab96-116">範例</span><span class="sxs-lookup"><span data-stu-id="9ab96-116">Example</span></span>

<span data-ttu-id="9ab96-117">此範例會建立使用的 runspace [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)物件來定義在 runspace 開啟時可用的項目。</span><span class="sxs-lookup"><span data-stu-id="9ab96-117">This sample creates a runspace that uses an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object to define the elements that are available when the runspace is opened.</span></span> <span data-ttu-id="9ab96-118">在此範例中，模組中定義的 Get-proc cmdlet 會加入初始工作階段狀態。</span><span class="sxs-lookup"><span data-stu-id="9ab96-118">In this sample, a module that defines a Get-Proc cmdlet is added to the initial session state.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9ab96-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ab96-119">See Also</span></span>

[<span data-ttu-id="9ab96-120">撰寫 Windows PowerShell 主機應用程式</span><span class="sxs-lookup"><span data-stu-id="9ab96-120">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)