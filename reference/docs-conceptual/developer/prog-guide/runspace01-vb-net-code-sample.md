---
title: Runspace01 (VB.NET) 程式碼範例 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: d40424283057b389d8a4aafeb8ddfa44284f3ba1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87778659"
---
# <a name="runspace01-vbnet-code-sample"></a><span data-ttu-id="d9217-102">Runspace01 (VB.NET) 程式碼範例</span><span class="sxs-lookup"><span data-stu-id="d9217-102">Runspace01 (VB.NET) Code Sample</span></span>

<span data-ttu-id="d9217-103">以下是[建立主控台應用程式（可執行指定的命令](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program)）中所述之運行空間的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="d9217-103">Here are the code samples for the runspace described in [Creating a Console Application That Runs a Specified Command](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).</span></span> <span data-ttu-id="d9217-104">若要這樣做，應用程式會叫用運行空間，然後叫用命令。</span><span class="sxs-lookup"><span data-stu-id="d9217-104">To do this, the application invokes a runspace, and then invokes a command.</span></span> <span data-ttu-id="d9217-105"> (請注意，此應用程式不會指定執行空間設定資訊，也不會明確建立管線。 ) 所叫用的命令是 `Get-Process` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d9217-105">(Note that this application does not specify runspace configuration information, nor does it explicitly create a pipeline.) The command that is invoked is the `Get-Process` cmdlet.</span></span>

## <a name="code-sample"></a><span data-ttu-id="d9217-106">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="d9217-106">Code Sample</span></span>

```vb
Imports System
Imports System.Collections.Generic
Imports System.Text
Imports System.Management.Automation
Imports System.Management.Automation.Host
Imports System.Management.Automation.Runspaces

Namespace Microsoft.Samples.PowerShell.Runspaces

    Module Runspace01
        ' <summary>
        ' This sample uses the RunspaceInvoke class to execute
        ' the get-process cmdlet synchronously. The name and
        ' handlecount are then extracted from  the PSObjects
        ' returned and displayed.
        ' </summary>
        ' <param name="args">Unused</param>
        ' <remarks>
        ' This sample demonstrates the following:
        ' 1. Creating an instance of the RunspaceInvoke class.
        ' 2. Using this instance to invoke a PowerShell command.
        ' 3. Using PSObject to extract properties from the objects
        '    returned by this command.
        ' </remarks>
        Sub Main()
            ' Create an instance of the RunspaceInvoke class.
            ' This takes care of all building all of the other
            ' data structures needed...
            Dim invoker As RunspaceInvoke = New RunspaceInvoke()

            Console.WriteLine("Process              HandleCount")
            Console.WriteLine("--------------------------------")

            ' Now invoke the runspace and display the objects that are
            ' returned...
            For Each result As PSObject In invoker.Invoke("get-process")
                Console.WriteLine("{0,-20} {1}", _
                    result.Members("ProcessName").Value, _
                    result.Members("HandleCount").Value)
            Next
            System.Console.WriteLine("Hit any key to exit...")
            System.Console.ReadKey()
        End Sub
    End Module
End Namespace
```

<!-- TODO!!!: [!code-csharp[Runspace01.vb](../../powershell-sdk-samples/SDK-2.0/vb/Runspace01/Runspace01.vb#L09-L53 "Runspace01.vb")] -->

## <a name="see-also"></a><span data-ttu-id="d9217-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9217-107">See Also</span></span>

[<span data-ttu-id="d9217-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="d9217-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
