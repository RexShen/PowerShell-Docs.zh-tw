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
ms.openlocfilehash: 1113c0d1cd68bb97d2f96b529f755b62137d1f40
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366037"
---
# <a name="importing-and-invoking-a-windows-powershell-workflow"></a>匯入並叫用 Windows PowerShell 工作流程

Windows PowerShell 3 可讓您匯入和叫用封裝為 Windows PowerShell 模組的工作流程。 如需 Windows PowerShell 模組的相關資訊，請參閱[撰寫 Windows Powershell 模組](../module/writing-a-windows-powershell-module.md)。

[Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)類別是用來做為伺服器上工作流程物件的用戶端 proxy。 下列程式說明如何使用[Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)物件來叫用工作流程。

### <a name="creating-a-psjobproxy-object-to-execute-workflow-commands-on-a-remote-server"></a>建立 PSJobProxy 物件，以在遠端伺服器上執行工作流程命令。

1. 建立[Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)物件，以建立與遠端運行空間的連接。

2. 將[Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)物件的[Wsmanconnectioninfo. Shelluri *](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo.ShellUri)屬性設定為，以 `Microsoft.PowerShell.Workflow` 指定 Windows PowerShell 端點的，以供您使用。

3. 建立使用完成先前步驟所建立之連線的執行階段版本。

4. 建立[system.web](/dotnet/api/System.Management.Automation.PowerShell)物件，並將其[system.web *](/dotnet/api/System.Management.Automation.PowerShell.Runspace)屬性設定為在上一個步驟中建立的運行空間。

5. 將工作流程模組和其命令匯入至[system.web](/dotnet/api/System.Management.Automation.PowerShell)。

6. 建立[Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)物件，並使用它在遠端伺服器上執行工作流程命令。

## <a name="example"></a>範例

下列程式碼範例示範如何使用 Windows PowerShell 叫用工作流程。

此範例需要 Windows PowerShell 3。

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