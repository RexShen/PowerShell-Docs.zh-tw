---
title: 匯入和叫用 Windows PowerShell 工作流程 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50e6f9b1-2678-4f53-9250-7c48843a9549
caps.latest.revision: 5
ms.openlocfilehash: a9497d72a586d0cc64c1d4e090819230285767e8
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564961"
---
# <a name="importing-and-invoking-a-windows-powershell-workflow"></a><span data-ttu-id="9ff4f-102">匯入並叫用 Windows PowerShell 工作流程</span><span class="sxs-lookup"><span data-stu-id="9ff4f-102">Importing and Invoking a Windows PowerShell Workflow</span></span>

<span data-ttu-id="9ff4f-103">Windows PowerShell 3 可讓您匯入和叫用封裝為 Windows PowerShell 模組的工作流程。</span><span class="sxs-lookup"><span data-stu-id="9ff4f-103">Windows PowerShell 3, allows you to import and invoke a workflow that is packaged as a Windows PowerShell module.</span></span> <span data-ttu-id="9ff4f-104">如需 Windows PowerShell 模組的相關資訊，請參閱[撰寫 Windows Powershell 模組](../module/writing-a-windows-powershell-module.md)。</span><span class="sxs-lookup"><span data-stu-id="9ff4f-104">For information about Windows PowerShell modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

<span data-ttu-id="9ff4f-105">[Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)類別是用來做為伺服器上工作流程物件的用戶端 proxy。</span><span class="sxs-lookup"><span data-stu-id="9ff4f-105">The [System.Management.Automation.Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)class is used as a client side proxy for workflow objects on the server.</span></span> <span data-ttu-id="9ff4f-106">下列程式說明如何使用[Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)物件來叫用工作流程。</span><span class="sxs-lookup"><span data-stu-id="9ff4f-106">The following procedure explains how to use a [System.Management.Automation.Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)object to invoke a workflow.</span></span>

### <a name="creating-a-psjobproxy-object-to-execute-workflow-commands-on-a-remote-server"></a><span data-ttu-id="9ff4f-107">建立 PSJobProxy 物件，以在遠端伺服器上執行工作流程命令。</span><span class="sxs-lookup"><span data-stu-id="9ff4f-107">Creating a PSJobProxy object to execute workflow commands on a remote server.</span></span>

1. <span data-ttu-id="9ff4f-108">建立[Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)物件，以建立與遠端運行空間的連接。</span><span class="sxs-lookup"><span data-stu-id="9ff4f-108">Create an [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)object to create a connection to a remote runspace.</span></span>

2. <span data-ttu-id="9ff4f-109">將[Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)物件的[Wsmanconnectioninfo. Shelluri \*](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo.ShellUri)屬性設定為 `Microsoft.PowerShell.Workflow` ，以指定 Windows PowerShell 端點。（目標為的）。</span><span class="sxs-lookup"><span data-stu-id="9ff4f-109">Set the [System.Management.Automation.Runspaces.Wsmanconnectioninfo.Shelluri\*](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo.ShellUri) property of the [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)object to `Microsoft.PowerShell.Workflow` to specify a Windows PowerShell endpoint.</span></span>

3. <span data-ttu-id="9ff4f-110">建立使用完成先前步驟所建立之連線的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="9ff4f-110">Create a runspace that uses the connection created by completing the previous steps.</span></span>

4. <span data-ttu-id="9ff4f-111">建立[system.web](/dotnet/api/System.Management.Automation.PowerShell)物件，並將其[system.web \*](/dotnet/api/System.Management.Automation.PowerShell.Runspace)屬性設定為在上一個步驟中建立的運行空間。</span><span class="sxs-lookup"><span data-stu-id="9ff4f-111">Create a [System.Management.Automation.Powershell](/dotnet/api/System.Management.Automation.PowerShell)object and set its [System.Management.Automation.Powershell.Runspace\*](/dotnet/api/System.Management.Automation.PowerShell.Runspace) property to the runspace created in the previous step.</span></span>

5. <span data-ttu-id="9ff4f-112">將工作流程模組和其命令匯入至[system.web](/dotnet/api/System.Management.Automation.PowerShell)。</span><span class="sxs-lookup"><span data-stu-id="9ff4f-112">Import the workflow module and its commands into the [System.Management.Automation.Powershell](/dotnet/api/System.Management.Automation.PowerShell).</span></span>

6. <span data-ttu-id="9ff4f-113">建立[Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)物件，並使用它在遠端伺服器上執行工作流程命令。</span><span class="sxs-lookup"><span data-stu-id="9ff4f-113">Create a [System.Management.Automation.Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy) object and use it to execute workflow commands on the remote server.</span></span>

## <a name="example"></a><span data-ttu-id="9ff4f-114">範例</span><span class="sxs-lookup"><span data-stu-id="9ff4f-114">Example</span></span>

<span data-ttu-id="9ff4f-115">下列程式碼範例示範如何使用 Windows PowerShell 叫用工作流程。</span><span class="sxs-lookup"><span data-stu-id="9ff4f-115">The following code example demonstrates how to invoke a workflow by using Windows PowerShell.</span></span>

<span data-ttu-id="9ff4f-116">此範例需要 Windows PowerShell 3。</span><span class="sxs-lookup"><span data-stu-id="9ff4f-116">This example requires Windows PowerShell 3.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;
using System.Management.Automation.Runspaces;

namespace WorkflowHostTest
{

class Program
    {
        static void Main(string[] args)
        {
            if (args.Length == 0)
            {
                Console.WriteLine("Specify path to Workflow module");
                return;
            }

            string moduleFile = args[0];

            Console.Write("Creating Remote runspace connection...");
            WSManConnectionInfo connectionInfo = new WSManConnectionInfo();

            //Set the shellURI to workflow endpoint Microsoft.PowerShell.Workflow
            connectionInfo.ShellUri = "Microsoft.PowerShell.Workflow";

            //Create and open a runspace.
            Runspace runspace = RunspaceFactory.CreateRunspace(connectionInfo);
            runspace.Open();
            Console.WriteLine("done");

            PowerShell powershell = PowerShell.Create();
            powershell.Runspace = runspace;
            Console.Write("Setting $VerbosePreference=\"Continue\"...");
            powershell.AddScript("$VerbosePreference=\"Continue\"");
            powershell.Invoke();
            Console.WriteLine("done");

            Console.Write("Importing Workflow module...");
            powershell.Commands.Clear();

            //Import the module in to the PowerShell runspace. A XAML file could also be imported directly by using Import-Module.
            powershell.AddCommand("Import-Module").AddArgument(moduleFile);
            powershell.Invoke();
            Console.WriteLine("done");

            Console.Write("Creating job proxy...");
            powershell.Commands.Clear();
            powershell.AddCommand("Get-Proc").AddArgument("*");
            PSJobProxy job = powershell.AsJobProxy();
            Console.WriteLine("done");

                Console.WriteLine();
                Console.WriteLine("Using job proxy and performing operations...");
                Console.WriteLine("State of Job :" + job.JobStateInfo.State.ToString());
                Console.WriteLine("Starting job...");
                job.StartJob();
                Console.WriteLine("State of Job :" + job.JobStateInfo.State.ToString());

                // use blocking enumerator to wait for objects until job finishes
                job.Output.BlockingEnumerator = true;
                foreach (PSObject o in job.Output)
                {
                    Console.WriteLine(o.Properties["ProcessName"].Value.ToString());
                }

                // wait for a random time before attempting to stop job
                Random random = new Random();
                int time = random.Next(1, 10);
                Console.Write("Sleeping for {0} seconds when job is running on another thread...", time);
                System.Threading.Thread.Sleep(time * 1000);
                Console.WriteLine("done");
                Console.WriteLine("Stopping job...");
                job.StopJob();
                Console.WriteLine("State of Job :" + job.JobStateInfo.State.ToString());
                Console.WriteLine();
                job.Finished.WaitOne();
                Console.WriteLine("Output from job");
                Console.WriteLine("---------------");

                foreach (PSObject o in job.Output)
                {
                    Console.WriteLine(o.Properties["ProcessName"].Value.ToString());
                }

                Console.WriteLine();
                Console.WriteLine("Verbose messages from job");
                Console.WriteLine("-------------------------");
                foreach (VerboseRecord v in job.Verbose)
                {
                    Console.WriteLine(v.Message);
                }

            runspace.Close();
        }
    }
}

```
