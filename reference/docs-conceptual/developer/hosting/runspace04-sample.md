---
title: Runspace04 範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a6a04f15-b5d8-475b-ac9c-e75c58ec8933
caps.latest.revision: 8
ms.openlocfilehash: 3cb370cd1bfe9ce7198980cc1c26fafb126d00a3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360897"
---
# <a name="runspace04-sample"></a><span data-ttu-id="e6d6a-102">Runspace04 範例</span><span class="sxs-lookup"><span data-stu-id="e6d6a-102">Runspace04 Sample</span></span>

<span data-ttu-id="e6d6a-103">這個範例會示範如何使用[system.web](/dotnet/api/system.management.automation.powershell)類別來執行命令，以及如何攔截執行命令時所擲回的終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="e6d6a-103">This sample shows how to use the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class to run commands, and how to catch terminating errors that are thrown when running the commands.</span></span> <span data-ttu-id="e6d6a-104">執行了兩個命令，而最後一個命令傳遞了無效的參數引數。</span><span class="sxs-lookup"><span data-stu-id="e6d6a-104">Two commands are run, and the last command is passed a parameter argument that is not valid.</span></span> <span data-ttu-id="e6d6a-105">如此便不會傳回任何物件，且會擲回終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="e6d6a-105">As a result, no objects are returned and a terminating error is thrown.</span></span>

## <a name="requirements"></a><span data-ttu-id="e6d6a-106">需求</span><span class="sxs-lookup"><span data-stu-id="e6d6a-106">Requirements</span></span>

<span data-ttu-id="e6d6a-107">此範例需要 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="e6d6a-107">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="e6d6a-108">示範</span><span class="sxs-lookup"><span data-stu-id="e6d6a-108">Demonstrates</span></span>

<span data-ttu-id="e6d6a-109">這個範例會示範下列各項。</span><span class="sxs-lookup"><span data-stu-id="e6d6a-109">This sample demonstrates the following.</span></span>

- <span data-ttu-id="e6d6a-110">建立一個[system.web](/dotnet/api/system.management.automation.powershell)物件。</span><span class="sxs-lookup"><span data-stu-id="e6d6a-110">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="e6d6a-111">將命令新增至[system.web](/dotnet/api/system.management.automation.powershell)物件的管線中。</span><span class="sxs-lookup"><span data-stu-id="e6d6a-111">Adding commands to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="e6d6a-112">將參數引數加入至管線。</span><span class="sxs-lookup"><span data-stu-id="e6d6a-112">Adding parameter arguments to the pipeline.</span></span>

- <span data-ttu-id="e6d6a-113">同步叫用命令。</span><span class="sxs-lookup"><span data-stu-id="e6d6a-113">Invoking the commands synchronously.</span></span>

- <span data-ttu-id="e6d6a-114">使用[system.web](/dotnet/api/System.Management.Automation.PSObject)物件，從命令所傳回的物件中，解壓縮並顯示內容。</span><span class="sxs-lookup"><span data-stu-id="e6d6a-114">Using [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects to extract and display properties from the objects returned by the commands.</span></span>

- <span data-ttu-id="e6d6a-115">抓取和顯示在執行命令期間所產生的錯誤記錄。</span><span class="sxs-lookup"><span data-stu-id="e6d6a-115">Retrieving and displaying error records that were generated during the running of the commands.</span></span>

- <span data-ttu-id="e6d6a-116">捕捉和顯示命令擲回的終止例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e6d6a-116">Catching and displaying terminating exceptions thrown by the commands.</span></span>

## <a name="example"></a><span data-ttu-id="e6d6a-117">範例</span><span class="sxs-lookup"><span data-stu-id="e6d6a-117">Example</span></span>

<span data-ttu-id="e6d6a-118">這個範例會在 Windows PowerShell 所提供的預設執行時間中，以同步方式執行命令。</span><span class="sxs-lookup"><span data-stu-id="e6d6a-118">This sample runs commands synchronously in the default runspace provided by Windows PowerShell.</span></span> <span data-ttu-id="e6d6a-119">最後一個命令會擲回終止錯誤，因為不正確參數引數會傳遞給命令。</span><span class="sxs-lookup"><span data-stu-id="e6d6a-119">The last command throws a terminating error because a parameter argument that is not valid is passed to the command.</span></span> <span data-ttu-id="e6d6a-120">會攔截並顯示終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="e6d6a-120">The terminating error is trapped and displayed.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace04
  {
    /// <summary>
    /// This sample shows how to use a PowerShell object to run commands.
    /// The commands generate a terminating exception that the caller
    /// should catch and process.
    /// </summary>
    /// <param name="args">The parameter is not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a PowerShell object to run commands.
    /// 2. Adding commands to the pipeline of  the PowerShell object.
    /// 3. Passing input objects to the commands from the calling program.
    /// 4. Using PSObject objects to extract and display properties from the
    ///    objects returned by the commands.
    /// 5. Retrieving and displaying error records that were generated
    ///    while running the commands.
    /// 6. Catching and displaying terminating exceptions generated
    ///    while running the commands.
    /// </remarks>
    private static void Main(string[] args)
    {
      // Create a PowerShell object.
      using (PowerShell powershell = PowerShell.Create())
      {
        // Add the commands to the PowerShell object.
        powershell.AddCommand("Get-ChildItem").AddCommand("Select-String").AddArgument("*");

        // Run the commands synchronously. Because of the bad regular expression,
        // no objects will be returned. Instead, an exception will be thrown.
        try
        {
          foreach (PSObject result in powershell.Invoke())
          {
            Console.WriteLine("'{0}'", result.ToString());
          }

          // Process any error records that were generated while running the commands.
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
        catch (RuntimeException runtimeException)
        {
          // Trap any exception generated by the commands. These exceptions
          // will all be derived from the RuntimeException exception.
          System.Console.WriteLine(
                        "Runtime exception: {0}: {1}\n{2}",
                        runtimeException.ErrorRecord.InvocationInfo.InvocationName,
                        runtimeException.Message,
                        runtimeException.ErrorRecord.InvocationInfo.PositionMessage);
        }
      }

      System.Console.WriteLine("\nHit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="e6d6a-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6d6a-121">See Also</span></span>

[<span data-ttu-id="e6d6a-122">撰寫 Windows PowerShell 主應用程式</span><span class="sxs-lookup"><span data-stu-id="e6d6a-122">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)