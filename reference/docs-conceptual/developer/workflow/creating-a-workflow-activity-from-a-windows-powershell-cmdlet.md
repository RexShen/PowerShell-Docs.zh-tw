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
ms.openlocfilehash: f45b5e985fa38ca4ff41707f1842ddb8b930e2b1
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557494"
---
# <a name="creating-a-workflow-activity-from-a-windows-powershell-cmdlet"></a>從 Windows PowerShell Cmdlet 建立工作流程活動

您可以使用[Activitygenerator](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator)類別的方法，將任何 Windows PowerShell 模組或 Cmdlet 封裝為工作流程活動。 使用[Activitygenerator. Generatefrommoduleinfo *](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator.GenerateFromModuleInfo)、 [Activitygenerator Generatefromcommandinfo * 和](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator.GenerateFromCommandInfo)類別的 Activitygenerator [*](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator.GenerateFromName)方法，來產生代表活動的 c # 程式碼（Class）. Generatefromname * （）的（[活動）](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator) 。 接著，您可以將產生的 c # 程式碼編譯成可新增至專案做為活動的元件。

接著，您可以使用具有下列格式的命令列，將產生的 c # 程式碼編譯成可當做活動加入至專案的元件。

**csc/nologo/out： AssemblyName/target： library/reference： codefile.cs 中的活動/reference： Microsoft。活動**

## <a name="example"></a>範例

下列範例示範如何從 Windows PowerShell 模組產生活動的 c # 程式碼。

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

## <a name="example"></a>範例

下列範例示範如何從 Windows PowerShell Cmdlet 產生活動的 c # 程式碼。

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
