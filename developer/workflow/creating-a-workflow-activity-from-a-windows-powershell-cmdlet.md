---
title: 從 Windows PowerShell Cmdlet 建立工作流程活動 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4174e84f-d516-4aca-b418-273047dcfb07
caps.latest.revision: 7
ms.openlocfilehash: 5761ed2168a46d6ed9a2e50554d459f5b93223ee
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858524"
---
# <a name="creating-a-workflow-activity-from-a-windows-powershell-cmdlet"></a><span data-ttu-id="51650-102">從 Windows PowerShell Cmdlet 建立工作流程活動</span><span class="sxs-lookup"><span data-stu-id="51650-102">Creating a Workflow Activity from a Windows PowerShell Cmdlet</span></span>

<span data-ttu-id="51650-103">任何 Windows PowerShell 模組或指令程式可以封裝為工作流程活動所使用的方法[Microsoft.Powershell.Activities.Activitygenerator](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator)類別。</span><span class="sxs-lookup"><span data-stu-id="51650-103">Any Windows PowerShell module or cmdlet can be packaged as a Workflow activity by using the methods of the [Microsoft.Powershell.Activities.Activitygenerator](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator) class.</span></span> <span data-ttu-id="51650-104">使用[Microsoft.Powershell.Activities.Activitygenerator.Generatefrommoduleinfo\*](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator.GenerateFromModuleInfo)， [Microsoft.Powershell.Activities.Activitygenerator.Generatefromcommandinfo\*](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator.GenerateFromCommandInfo)，並[Microsoft.Powershell.Activities.Activitygenerator.Generatefromname\*](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator.GenerateFromName)方法[Microsoft.Powershell.Activities.Activitygenerator](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator)類別來產生C#程式碼代表的活動。</span><span class="sxs-lookup"><span data-stu-id="51650-104">Use the [Microsoft.Powershell.Activities.Activitygenerator.Generatefrommoduleinfo\*](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator.GenerateFromModuleInfo), [Microsoft.Powershell.Activities.Activitygenerator.Generatefromcommandinfo\*](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator.GenerateFromCommandInfo), and [Microsoft.Powershell.Activities.Activitygenerator.Generatefromname\*](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator.GenerateFromName) methods of the [Microsoft.Powershell.Activities.Activitygenerator](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator) class to generate C# code that represents an activity.</span></span> <span data-ttu-id="51650-105">您可以再編譯所產生的C#可以新增至專案，以做為活動的組件的程式碼。</span><span class="sxs-lookup"><span data-stu-id="51650-105">You can then compile the resulting C# code into an assembly that can be added to a project as an activity.</span></span>

<span data-ttu-id="51650-106">您可以再編譯所產生的C#組件可加入至專案做為活動具有下列格式使用命令列將程式碼。</span><span class="sxs-lookup"><span data-stu-id="51650-106">You can then compile the resulting C# code into an assembly that can be added to a project as an activity by using a command line with the following form.</span></span>

<span data-ttu-id="51650-107">**csc /nologo /out:AssemblyName /target: library /reference:System.Activities.Activity /reference:Microsoft.PowerShell.Activities codefile.cs**</span><span class="sxs-lookup"><span data-stu-id="51650-107">**csc /nologo /out:AssemblyName /target:library /reference:System.Activities.Activity /reference:Microsoft.PowerShell.Activities codefile.cs**</span></span>

## <a name="example"></a><span data-ttu-id="51650-108">範例</span><span class="sxs-lookup"><span data-stu-id="51650-108">Example</span></span>

<span data-ttu-id="51650-109">下列範例示範如何產生C#活動，從 Windows PowerShell 模組的程式碼。</span><span class="sxs-lookup"><span data-stu-id="51650-109">The following example demonstrates how to generate C# code for an activity from a Windows PowerShell module.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.IO;
using System.Management.Automation;
using System.Collections.ObjectModel;
using Microsoft.PowerShell.Activities;

namespace MakeActivity
{
    class Program
    {
        static void Main(string[] args)

        {
            StreamWriter CodeFile = new StreamWriter("c:\\\\testmodule\\codefile.cs");
            Collection<PSModuleInfo> ModuleInfos = new Collection<PSModuleInfo> { };
            PSModuleInfo ModuleInfo;
            string ActivityCode = "";
            string ModulePath = "";
            Console.Write("Type the full path and filename of the module to process:");
            ModulePath = Console.ReadLine();

            PowerShell ps = PowerShell.Create();

            ps.AddCommand("Import-Module").AddArgument(ModulePath);
            ps.AddParameter("PassThru");
            ModuleInfos = ps.Invoke<PSModuleInfo>();

            ModuleInfo = (PSModuleInfo)ModuleInfos[0];

            ActivityCode = ActivityGenerator.GenerateFromModuleInfo(ModuleInfo, "MyNamespace").First<String>();

           CodeFile.Write(ActivityCode);
            Console.ReadLine();

        }
    }
}

```

## <a name="example"></a><span data-ttu-id="51650-110">範例</span><span class="sxs-lookup"><span data-stu-id="51650-110">Example</span></span>

<span data-ttu-id="51650-111">下列範例示範如何產生C#活動，從 Windows PowerShell cmdlet 的程式碼。</span><span class="sxs-lookup"><span data-stu-id="51650-111">The following example demonstrates how to generate C# code for an activity from a Windows PowerShell cmdlet.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.IO;
using System.Management.Automation;
using System.Collections.ObjectModel;
using Microsoft.PowerShell.Activities;

namespace MakeActivity
{
    class Program
    {
        static void Main(string[] args)

        {
            StreamWriter CodeFile = new StreamWriter("c:\\\\testmodule\\codefile.cs");
            Collection<PSModuleInfo> ModuleInfos = new Collection<PSModuleInfo> { };
            PSModuleInfo ModuleInfo;
            Collection<CommandInfo> CommandInfos = new Collection<CommandInfo> { };
            CommandInfo MyCommand;
            string ActivityCode = "";
            string ModulePath = "";
            Console.Write("Type the full path and filename of the module to process:");
            ModulePath = Console.ReadLine();

            PowerShell ps = PowerShell.Create();

            ps.AddCommand("Import-Module").AddArgument(ModulePath);
            ps.AddParameter("PassThru");
            ModuleInfos = ps.Invoke<PSModuleInfo>();

            ModuleInfo = (PSModuleInfo)ModuleInfos[0];

            ps.AddCommand("Get-Command").AddArgument(ModuleInfo);
            CommandInfos = ps.Invoke<CommandInfo>();

            MyCommand = CommandInfos[0];

            ActivityCode = ActivityGenerator.GenerateFromCommandInfo(MyCommand, "MyNamespace");

           CodeFile.Write(ActivityCode);
            Console.ReadLine();

        }
    }
}

```