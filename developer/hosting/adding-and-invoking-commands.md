---
title: 新增和叫用命令 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 62be8432-28c1-4ca2-bcdb-d0350163fa8c
caps.latest.revision: 5
ms.openlocfilehash: 31371797ee57f07075da3436e0b42b2ca01aaffd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857344"
---
# <a name="adding-and-invoking-commands"></a><span data-ttu-id="f5b26-102">新增及叫用命令</span><span class="sxs-lookup"><span data-stu-id="f5b26-102">Adding and invoking commands</span></span>

<span data-ttu-id="f5b26-103">建立 runspace 之後, 您可以將 Windows PowerShellcommands 和指令碼新增至管線中，並接著在同步或非同步方式叫用管線。</span><span class="sxs-lookup"><span data-stu-id="f5b26-103">After creating a runspace, you can add Windows PowerShellcommands and scripts to a pipeline, and then invoke the pipeline synchronously or asynchronously.</span></span>

## <a name="creating-a-pipeline"></a><span data-ttu-id="f5b26-104">建立管線</span><span class="sxs-lookup"><span data-stu-id="f5b26-104">Creating a pipeline</span></span>

 <span data-ttu-id="f5b26-105">[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)類別提供數種方法來將命令、 參數和指令碼新增至管線。</span><span class="sxs-lookup"><span data-stu-id="f5b26-105">The [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class provides several methods to add commands, parameters, and scripts to the pipeline.</span></span> <span data-ttu-id="f5b26-106">您可以叫用管線以同步方式呼叫的多載[System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke)方法，或以非同步方式呼叫的多載[System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) ，然後[System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke)方法。</span><span class="sxs-lookup"><span data-stu-id="f5b26-106">You can invoke the pipeline synchronously by calling an overload of the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, or asynchronously by calling an overload of the [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) and then the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

### <a name="addcommand"></a><span data-ttu-id="f5b26-107">AddCommand</span><span class="sxs-lookup"><span data-stu-id="f5b26-107">AddCommand</span></span>

1. <span data-ttu-id="f5b26-108">建立[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)物件。</span><span class="sxs-lookup"><span data-stu-id="f5b26-108">Create a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. <span data-ttu-id="f5b26-109">新增您想要執行的命令。</span><span class="sxs-lookup"><span data-stu-id="f5b26-109">Add the command that you want to execute.</span></span>

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. <span data-ttu-id="f5b26-110">叫用命令。</span><span class="sxs-lookup"><span data-stu-id="f5b26-110">Invoke the command.</span></span>

   ```csharp
   ps.Invoke();
   ```

 <span data-ttu-id="f5b26-111">如果您呼叫[System.Management.Automation.Powershell.Addcommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand)方法超過一次，然後再呼叫[System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke)方法、 結果第一個命令會輸送到第二個，依此類推。</span><span class="sxs-lookup"><span data-stu-id="f5b26-111">If you call the [System.Management.Automation.Powershell.Addcommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) method more than once before you call the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, the result of the first command is piped to the second, and so on.</span></span> <span data-ttu-id="f5b26-112">如果您不想透過管道傳送命令前一個命令的結果，會將它加入藉由呼叫[System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement)改。</span><span class="sxs-lookup"><span data-stu-id="f5b26-112">If you do not want to pipe the result of a previous command to a command, add it by calling the [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) instead.</span></span>

### <a name="addparameter"></a><span data-ttu-id="f5b26-113">AddParameter</span><span class="sxs-lookup"><span data-stu-id="f5b26-113">AddParameter</span></span>

 <span data-ttu-id="f5b26-114">前一個範例會執行不含任何參數的單一命令。</span><span class="sxs-lookup"><span data-stu-id="f5b26-114">The previous example executes a single command without any parameters.</span></span> <span data-ttu-id="f5b26-115">可以透過將參數新增至命令[System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter)方法，例如下列程式碼會取得一份所有程序會在名為`PowerShell`上執行機器。</span><span class="sxs-lookup"><span data-stu-id="f5b26-115">You can add parameters to the command by using the [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) method For example, the following code gets a list of all of the processes that are named `PowerShell` running on the machine.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

 <span data-ttu-id="f5b26-116">您可以新增額外的參數，藉由呼叫[System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter)重複。</span><span class="sxs-lookup"><span data-stu-id="f5b26-116">You can add additional parameters by calling [System.Management.Automation.Pscommand.Addparameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) repeatedly.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

 <span data-ttu-id="f5b26-117">您也可以藉由呼叫來新增參數名稱和值的字典[System.Management.Automation.Powershell.Addparameters\*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters)方法。</span><span class="sxs-lookup"><span data-stu-id="f5b26-117">You can also add a dictionary of parameter names and values by calling the [System.Management.Automation.Powershell.Addparameters\*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) method.</span></span>

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a><span data-ttu-id="f5b26-118">AddStatement</span><span class="sxs-lookup"><span data-stu-id="f5b26-118">AddStatement</span></span>

 <span data-ttu-id="f5b26-119">您可以使用批次處理來模擬[System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement)方法，將其他的陳述式加入至管線，下列程式碼會取得執行程序名稱的清單結尾`PowerShell`，然後取得執行中服務的清單。</span><span class="sxs-lookup"><span data-stu-id="f5b26-119">You can simulate batching by using the [System.Management.Automation.Powershell.Addstatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) method, which adds an additional statement to the end of the pipeline The following code gets a list of running processes with the name `PowerShell`, and then gets the list of running services.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a><span data-ttu-id="f5b26-120">AddScript</span><span class="sxs-lookup"><span data-stu-id="f5b26-120">AddScript</span></span>

 <span data-ttu-id="f5b26-121">您可以執行現有的指令碼，藉由呼叫[System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript)方法。</span><span class="sxs-lookup"><span data-stu-id="f5b26-121">You can run an existing script by calling the [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method.</span></span> <span data-ttu-id="f5b26-122">下列範例會將指令碼新增至管線，並執行它。</span><span class="sxs-lookup"><span data-stu-id="f5b26-122">The following example adds a script to the pipeline and runs it.</span></span> <span data-ttu-id="f5b26-123">這個範例假設已經有名稱為指令碼`MyScript.ps1`在名為的資料夾中`D:\PSScripts`。</span><span class="sxs-lookup"><span data-stu-id="f5b26-123">This example assumes there is already a script named `MyScript.ps1` in a folder named `D:\PSScripts`.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

 <span data-ttu-id="f5b26-124">另外還有一份[System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript)方法接受名為的布林參數`useLocalScope`。</span><span class="sxs-lookup"><span data-stu-id="f5b26-124">There is also a version of the [System.Management.Automation.Powershell.Addscript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method that takes a boolean parameter named `useLocalScope`.</span></span> <span data-ttu-id="f5b26-125">如果此參數設為`true`，則指令碼會執行本機範圍內。</span><span class="sxs-lookup"><span data-stu-id="f5b26-125">If this parameter is set to `true`, then the script is run in the local scope.</span></span> <span data-ttu-id="f5b26-126">下列程式碼會在本機的範圍內執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="f5b26-126">The following code will run the script in the local scope.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

### <a name="invoking-a-pipeline-synchronously"></a><span data-ttu-id="f5b26-127">以同步方式叫用管線</span><span class="sxs-lookup"><span data-stu-id="f5b26-127">Invoking a pipeline synchronously</span></span>

 <span data-ttu-id="f5b26-128">您將項目新增至管線之後，您叫用它。</span><span class="sxs-lookup"><span data-stu-id="f5b26-128">After you add elements to the pipeline, you invoke it.</span></span> <span data-ttu-id="f5b26-129">若要以同步方式叫用管線時，您會呼叫的多載[System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke)方法。</span><span class="sxs-lookup"><span data-stu-id="f5b26-129">To invoke the pipeline synchronously, you call an overload of the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method.</span></span> <span data-ttu-id="f5b26-130">下列範例示範如何以同步方式叫用管線。</span><span class="sxs-lookup"><span data-stu-id="f5b26-130">The following example shows how to synchronously invoke a pipeline.</span></span>

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

### <a name="invoking-a-pipeline-asynchronously"></a><span data-ttu-id="f5b26-131">以非同步方式叫用管線</span><span class="sxs-lookup"><span data-stu-id="f5b26-131">Invoking a pipeline asynchronously</span></span>

 <span data-ttu-id="f5b26-132">您叫用管線以非同步方式呼叫的多載[System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke)來建立[IAsyncResult](http://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx)物件，並接著呼叫[System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke)方法。</span><span class="sxs-lookup"><span data-stu-id="f5b26-132">You invoke a pipeline asynchronously by calling an overload of the [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) to create an [IAsyncResult](http://msdn.microsoft.com/library/system.iasyncresult\(v=vs.110\).aspx) object, and then calling the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

 <span data-ttu-id="f5b26-133">下列範例示範如何叫用管線 asynchronoulsy。</span><span class="sxs-lookup"><span data-stu-id="f5b26-133">The following example shows how to invoke a pipeline asynchronoulsy.</span></span>

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
      // Get-Process cmdlet. Do not include spaces immediatly
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

## <a name="see-also"></a><span data-ttu-id="f5b26-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5b26-134">See Also</span></span>

 [<span data-ttu-id="f5b26-135">建立 InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="f5b26-135">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)

 [<span data-ttu-id="f5b26-136">建立受限的 runspace</span><span class="sxs-lookup"><span data-stu-id="f5b26-136">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)
