---
title: Runspace08 範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1100d91d-249d-4af7-9854-2d6a423ac2f4
caps.latest.revision: 7
ms.openlocfilehash: 70577a6a42ce26e9791360fa30baae9d7a492daf
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367307"
---
# <a name="runspace08-sample"></a><span data-ttu-id="25dcd-102">Runspace08 範例</span><span class="sxs-lookup"><span data-stu-id="25dcd-102">Runspace08 Sample</span></span>

<span data-ttu-id="25dcd-103">這個範例示範如何將命令和引數新增至[system.web](/dotnet/api/system.management.automation.powershell)物件的管線，以及如何同步執行命令。</span><span class="sxs-lookup"><span data-stu-id="25dcd-103">This sample shows how to add commands and arguments to the pipeline of a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object and how to run the commands synchronously.</span></span>

## <a name="requirements"></a><span data-ttu-id="25dcd-104">需求</span><span class="sxs-lookup"><span data-stu-id="25dcd-104">Requirements</span></span>

<span data-ttu-id="25dcd-105">此範例需要 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="25dcd-105">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="25dcd-106">演示</span><span class="sxs-lookup"><span data-stu-id="25dcd-106">Demonstrates</span></span>

<span data-ttu-id="25dcd-107">這個範例會示範下列各項。</span><span class="sxs-lookup"><span data-stu-id="25dcd-107">This sample demonstrates the following.</span></span>

- <span data-ttu-id="25dcd-108">藉由使用[Runspacefactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory)類別，建立[管理元件](/dotnet/api/System.Management.Automation.Runspaces.Runspace)的 [工作空間] 的物件。</span><span class="sxs-lookup"><span data-stu-id="25dcd-108">Creating a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object by using the [System.Management.Automation.Runspaces.Runspacefactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) class.</span></span>

- <span data-ttu-id="25dcd-109">建立使用此運行空間的[system.web](/dotnet/api/system.management.automation.powershell)物件。</span><span class="sxs-lookup"><span data-stu-id="25dcd-109">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object that uses the runspace.</span></span>

- <span data-ttu-id="25dcd-110">將 Cmdlet 新增至[system.web](/dotnet/api/system.management.automation.powershell)物件的管線。</span><span class="sxs-lookup"><span data-stu-id="25dcd-110">Adding cmdlets to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="25dcd-111">同步執行 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="25dcd-111">Running the cmdlets synchronously.</span></span>

- <span data-ttu-id="25dcd-112">從命令所傳回的[system.web](/dotnet/api/System.Management.Automation.PSObject)物件中，解壓縮屬性。</span><span class="sxs-lookup"><span data-stu-id="25dcd-112">Extracting properties from the [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects returned by the command.</span></span>

## <a name="example"></a><span data-ttu-id="25dcd-113">範例</span><span class="sxs-lookup"><span data-stu-id="25dcd-113">Example</span></span>

<span data-ttu-id="25dcd-114">這個範例會使用[system.web](/dotnet/api/system.management.automation.powershell)物件來執行[取得進程](/powershell/module/Microsoft.PowerShell.Management/Get-Process)和[排序物件](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object)Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="25dcd-114">This sample runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) and [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets by using a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections.Generic;
  using System.Collections.ObjectModel;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace08
  {
    /// <summary>
    /// This sample shows how to use a PowerShell object to run commands. The
    /// PowerShell object builds a pipeline that include the get-process cmdlet,
    /// which is then piped to the sort-object cmdlet. Parameters are added to the
    /// sort-object cmdlet to sort the HandleCount property in descending order.
    /// </summary>
    /// <param name="args">Parameter is not used.</param>
    /// <remarks>
    /// This sample demonstrates:
    /// 1. Creating a PowerShell object
    /// 2. Adding individual commands to the PowerShell object.
    /// 3. Adding parameters to the commands.
    /// 4. Running the pipeline of the PowerShell object synchronously.
    /// 5. Working with PSObject objects to extract properties
    ///    from the objects returned by the commands.
    /// </remarks>
    private static void Main(string[] args)
    {
      Collection<PSObject> results; // Holds the result of the pipeline execution.

      // Create the PowerShell object. Notice that no runspace is specified so a
      // new default runspace is used.
      PowerShell powershell = PowerShell.Create();

      // Use the using statement so that we can dispose of the PowerShell object
      // when we are done.
      using (powershell)
      {
        // Add the get-process cmdlet to the pipeline of the PowerShell object.
        powershell.AddCommand("get-process");

        // Add the sort-object cmdlet and its parameters to the pipeline of
        // the PowerShell object so that we can sort the HandleCount property
        //  in descending order.
        powershell.AddCommand("sort-object").AddParameter("descending").AddParameter("property", "handlecount");

        // Run the commands of the pipeline synchronously.
        results = powershell.Invoke();
      }

      // Even after disposing of the PowerShell object, we still
      // need to set the powershell variable to null so that the
      // garbage collector can clean it up.
      powershell = null;

      Console.WriteLine("Process              HandleCount");
      Console.WriteLine("--------------------------------");

      // Display the results returned by the commands.
      foreach (PSObject result in results)
      {
        Console.WriteLine(
                          "{0,-20} {1}",
                          result.Members["ProcessName"].Value,
                          result.Members["HandleCount"].Value);
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="25dcd-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25dcd-115">See Also</span></span>

[<span data-ttu-id="25dcd-116">撰寫 Windows PowerShell 主應用程式</span><span class="sxs-lookup"><span data-stu-id="25dcd-116">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)