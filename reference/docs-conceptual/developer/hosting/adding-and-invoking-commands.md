---
title: 加入和叫用命令 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 62be8432-28c1-4ca2-bcdb-d0350163fa8c
caps.latest.revision: 5
ms.openlocfilehash: f776f13fe743a3f5f67de0d94883e3f754040ffc
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367637"
---
# <a name="adding-and-invoking-commands"></a><span data-ttu-id="c4f9f-102">新增及叫用命令</span><span class="sxs-lookup"><span data-stu-id="c4f9f-102">Adding and invoking commands</span></span>

<span data-ttu-id="c4f9f-103">建立執行時間之後，您可以將 Windows PowerShellcommands 和腳本新增至管線，然後以同步或非同步方式叫用管線。</span><span class="sxs-lookup"><span data-stu-id="c4f9f-103">After creating a runspace, you can add Windows PowerShellcommands and scripts to a pipeline, and then invoke the pipeline synchronously or asynchronously.</span></span>

## <a name="creating-a-pipeline"></a><span data-ttu-id="c4f9f-104">建立管線</span><span class="sxs-lookup"><span data-stu-id="c4f9f-104">Creating a pipeline</span></span>

 <span data-ttu-id="c4f9f-105">[System.web](/dotnet/api/system.management.automation.powershell)類別提供數種方法，可將命令、參數和腳本新增至管線。</span><span class="sxs-lookup"><span data-stu-id="c4f9f-105">The [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class provides several methods to add commands, parameters, and scripts to the pipeline.</span></span> <span data-ttu-id="c4f9f-106">您可以藉由呼叫[Begininvoke](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke)的多載，以同步方式叫用管線[，方法是](/dotnet/api/System.Management.Automation.PowerShell.Invoke)呼叫多載的，或以非同步方式叫用。然後， [Endinvoke \*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke)方法，再進行一層。</span><span class="sxs-lookup"><span data-stu-id="c4f9f-106">You can invoke the pipeline synchronously by calling an overload of the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, or asynchronously by calling an overload of the [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) and then the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

### <a name="addcommand"></a><span data-ttu-id="c4f9f-107">AddCommand</span><span class="sxs-lookup"><span data-stu-id="c4f9f-107">AddCommand</span></span>

1. <span data-ttu-id="c4f9f-108">建立一個[system.web](/dotnet/api/system.management.automation.powershell)物件。</span><span class="sxs-lookup"><span data-stu-id="c4f9f-108">Create a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. <span data-ttu-id="c4f9f-109">新增您想要執行的命令。</span><span class="sxs-lookup"><span data-stu-id="c4f9f-109">Add the command that you want to execute.</span></span>

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. <span data-ttu-id="c4f9f-110">叫用命令。</span><span class="sxs-lookup"><span data-stu-id="c4f9f-110">Invoke the command.</span></span>

   ```csharp
   ps.Invoke();
   ```

 <span data-ttu-id="c4f9f-111">如果您在呼叫 system.servicemodel [\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke)方法之前多次呼叫[Addcommand \*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand)方法，第一個命令的結果會以管道傳送至第二個，依此類推，而是以管線傳送的。</span><span class="sxs-lookup"><span data-stu-id="c4f9f-111">If you call the [System.Management.Automation.Powershell.Addcommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) method more than once before you call the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, the result of the first command is piped to the second, and so on.</span></span> <span data-ttu-id="c4f9f-112">如果您不想要使用管線將上一個命令的結果傳送至命令，請改為呼叫[Addstatement \*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement)來新增它。</span><span class="sxs-lookup"><span data-stu-id="c4f9f-112">If you do not want to pipe the result of a previous command to a command, add it by calling the [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) instead.</span></span>

### <a name="addparameter"></a><span data-ttu-id="c4f9f-113">AddParameter</span><span class="sxs-lookup"><span data-stu-id="c4f9f-113">AddParameter</span></span>

 <span data-ttu-id="c4f9f-114">上一個範例會執行不含任何參數的單一命令。</span><span class="sxs-lookup"><span data-stu-id="c4f9f-114">The previous example executes a single command without any parameters.</span></span> <span data-ttu-id="c4f9f-115">例如，您可以使用[Pscommand. Addparameter \*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter)方法將參數新增至命令，下列程式碼會取得在電腦上執行 `PowerShell` 的所有處理常式清單。</span><span class="sxs-lookup"><span data-stu-id="c4f9f-115">You can add parameters to the command by using the [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) method For example, the following code gets a list of all of the processes that are named `PowerShell` running on the machine.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

 <span data-ttu-id="c4f9f-116">您可以藉由重複呼叫[Pscommand. Addparameter \*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter)來新增其他參數。</span><span class="sxs-lookup"><span data-stu-id="c4f9f-116">You can add additional parameters by calling [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) repeatedly.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

 <span data-ttu-id="c4f9f-117">您也可以藉由呼叫[Addparameters \*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters)方法，加入參數名稱和值的字典。</span><span class="sxs-lookup"><span data-stu-id="c4f9f-117">You can also add a dictionary of parameter names and values by calling the [System.Management.Automation.Powershell.Addparameters\*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) method.</span></span>

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a><span data-ttu-id="c4f9f-118">AddStatement</span><span class="sxs-lookup"><span data-stu-id="c4f9f-118">AddStatement</span></span>

 <span data-ttu-id="c4f9f-119">您可以使用[Addstatement \*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement)方法來模擬批次處理，這會將額外的語句新增至管線的結尾，下列程式碼會取得名稱為 `PowerShell` 的執行中進程清單，然後取得執行中服務的清單。</span><span class="sxs-lookup"><span data-stu-id="c4f9f-119">You can simulate batching by using the [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) method, which adds an additional statement to the end of the pipeline The following code gets a list of running processes with the name `PowerShell`, and then gets the list of running services.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a><span data-ttu-id="c4f9f-120">AddScript</span><span class="sxs-lookup"><span data-stu-id="c4f9f-120">AddScript</span></span>

 <span data-ttu-id="c4f9f-121">您可以藉由呼叫[Addscript \*](/dotnet/api/System.Management.Automation.PowerShell.AddScript)方法，來執行現有的腳本。</span><span class="sxs-lookup"><span data-stu-id="c4f9f-121">You can run an existing script by calling the [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method.</span></span> <span data-ttu-id="c4f9f-122">下列範例會將腳本新增至管線並加以執行。</span><span class="sxs-lookup"><span data-stu-id="c4f9f-122">The following example adds a script to the pipeline and runs it.</span></span> <span data-ttu-id="c4f9f-123">這個範例假設名為 `D:\PSScripts` 的資料夾中已經有名為 `MyScript.ps1` 的腳本。</span><span class="sxs-lookup"><span data-stu-id="c4f9f-123">This example assumes there is already a script named `MyScript.ps1` in a folder named `D:\PSScripts`.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

 <span data-ttu-id="c4f9f-124">另外還有一個[Addscript \*](/dotnet/api/System.Management.Automation.PowerShell.AddScript)方法的版本，它會採用名為 `useLocalScope` 的布林參數。</span><span class="sxs-lookup"><span data-stu-id="c4f9f-124">There is also a version of the [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method that takes a boolean parameter named `useLocalScope`.</span></span> <span data-ttu-id="c4f9f-125">如果此參數設定為 `true`，則腳本會在本機範圍中執行。</span><span class="sxs-lookup"><span data-stu-id="c4f9f-125">If this parameter is set to `true`, then the script is run in the local scope.</span></span> <span data-ttu-id="c4f9f-126">下列程式碼會在本機範圍中執行腳本。</span><span class="sxs-lookup"><span data-stu-id="c4f9f-126">The following code will run the script in the local scope.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

### <a name="invoking-a-pipeline-synchronously"></a><span data-ttu-id="c4f9f-127">同步叫用管線</span><span class="sxs-lookup"><span data-stu-id="c4f9f-127">Invoking a pipeline synchronously</span></span>

 <span data-ttu-id="c4f9f-128">將元素新增至管線之後，您就可以叫用它。</span><span class="sxs-lookup"><span data-stu-id="c4f9f-128">After you add elements to the pipeline, you invoke it.</span></span> <span data-ttu-id="c4f9f-129">若要同步叫用管線，您可以呼叫[system.object](/dotnet/api/System.Management.Automation.PowerShell.Invoke)的多載。</span><span class="sxs-lookup"><span data-stu-id="c4f9f-129">To invoke the pipeline synchronously, you call an overload of the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method.</span></span> <span data-ttu-id="c4f9f-130">下列範例顯示如何同步叫用管線。</span><span class="sxs-lookup"><span data-stu-id="c4f9f-130">The following example shows how to synchronously invoke a pipeline.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;

namespace HostPS1e
{
  class HostPS1e
  {
    static void Main(string[] args)
    {
      // Using the PowerShell.Create and AddCommand
      // methods, create a command pipeline.
      PowerShell ps = PowerShell.Create().AddCommand ("Sort-Object");

      // Using the PowerShell.Invoke method, run the command
      // pipeline using the supplied input.
      foreach (PSObject result in ps.Invoke(new int[] { 3, 1, 6, 2, 5, 4 }))
      {
          Console.WriteLine("{0}", result);
      } // End foreach.
    } // End Main.
  } // End HostPS1e.
}
```

### <a name="invoking-a-pipeline-asynchronously"></a><span data-ttu-id="c4f9f-131">非同步叫用管線</span><span class="sxs-lookup"><span data-stu-id="c4f9f-131">Invoking a pipeline asynchronously</span></span>

 <span data-ttu-id="c4f9f-132">您可以藉由呼叫[Begininvoke \*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke)的多載來非同步叫用管線，以建立[IAsyncResult](https://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx)物件，然後再呼叫 Endinvoke （）。 [\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke)方法。</span><span class="sxs-lookup"><span data-stu-id="c4f9f-132">You invoke a pipeline asynchronously by calling an overload of the [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) to create an [IAsyncResult](https://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx) object, and then calling the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

 <span data-ttu-id="c4f9f-133">下列範例顯示如何以非同步方式叫用管線。</span><span class="sxs-lookup"><span data-stu-id="c4f9f-133">The following example shows how to invoke a pipeline asynchronously.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;

namespace HostPS3
{
  class HostPS3
  {
    static void Main(string[] args)
    {
      // Use the PowerShell.Create and PowerShell.AddCommand
      // methods to create a command pipeline that includes
      // Get-Process cmdlet. Do not include spaces immediately
      // before or after the cmdlet name as that will cause
      // the command to fail.
      PowerShell ps = PowerShell.Create().AddCommand("Get-Process");

      // Create an IAsyncResult object and call the
      // BeginInvoke method to start running the
      // command pipeline asynchronously.
      IAsyncResult async = ps.BeginInvoke();

      // Using the PowerShell.Invoke method, run the command
      // pipeline using the default runspace.
      foreach (PSObject result in ps.EndInvoke(async))
      {
        Console.WriteLine("{0,-20}{1}",
                result.Members["ProcessName"].Value,
                result.Members["Id"].Value);
      } // End foreach.
      System.Console.WriteLine("Hit any key to exit.");
      System.Console.ReadKey();
    } // End Main.
  } // End HostPS3.
}
```

## <a name="see-also"></a><span data-ttu-id="c4f9f-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4f9f-134">See Also</span></span>

 [<span data-ttu-id="c4f9f-135">建立 InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="c4f9f-135">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)

 [<span data-ttu-id="c4f9f-136">建立受條件約束的運行空間</span><span class="sxs-lookup"><span data-stu-id="c4f9f-136">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)
