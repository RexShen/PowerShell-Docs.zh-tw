---
title: Windows PowerShell 主機快速入門 |Microsoft Docs
ms.date: 09/12/2016
ms.openlocfilehash: fea6bd5ae49ecf552c583271ee9d869b1ccebae8
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779398"
---
# <a name="windows-powershell-host-quickstart"></a><span data-ttu-id="63718-102">Windows PowerShell 主機快速入門</span><span class="sxs-lookup"><span data-stu-id="63718-102">Windows PowerShell Host Quickstart</span></span>

<span data-ttu-id="63718-103">若要在您的應用程式中裝載 Windows PowerShell，請使用[system.web](/dotnet/api/System.Management.Automation.PowerShell)類別。</span><span class="sxs-lookup"><span data-stu-id="63718-103">To host Windows PowerShell in your application, you use the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class.</span></span>
<span data-ttu-id="63718-104">這個類別會提供方法來建立命令的管線，然後在運行空間中執行這些命令。</span><span class="sxs-lookup"><span data-stu-id="63718-104">This class provides methods that create a pipeline of commands and then execute those commands in a runspace.</span></span>
<span data-ttu-id="63718-105">建立主應用程式的最簡單方式是使用預設的運行時。</span><span class="sxs-lookup"><span data-stu-id="63718-105">The simplest way to create a host application is to use the default runspace.</span></span>
<span data-ttu-id="63718-106">預設的執行時間包含所有核心 Windows PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="63718-106">The default runspace contains all of the core Windows PowerShell commands.</span></span>
<span data-ttu-id="63718-107">如果您想要讓應用程式只公開部分的 Windows PowerShell 命令，您必須建立自訂的執行時間。</span><span class="sxs-lookup"><span data-stu-id="63718-107">If you want your application to expose only a subset of the Windows PowerShell commands, you must create a custom runspace.</span></span>

## <a name="using-the-default-runspace"></a><span data-ttu-id="63718-108">使用預設的運行空間</span><span class="sxs-lookup"><span data-stu-id="63718-108">Using the default runspace</span></span>

<span data-ttu-id="63718-109">首先，我們將使用預設的執行時間，並使用[system.web](/dotnet/api/System.Management.Automation.PowerShell)類別的方法，將命令、參數、語句和腳本新增至管線。</span><span class="sxs-lookup"><span data-stu-id="63718-109">To start, we'll use the default runspace, and use the methods of the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class to add commands, parameters, statements, and scripts to a pipeline.</span></span>

### <a name="addcommand"></a><span data-ttu-id="63718-110">AddCommand</span><span class="sxs-lookup"><span data-stu-id="63718-110">AddCommand</span></span>

<span data-ttu-id="63718-111">您可以使用[AddCommand](/dotnet/api/System.Management.Automation.PowerShell.AddCommand)方法，將命令新增至管線。</span><span class="sxs-lookup"><span data-stu-id="63718-111">You use the [System.Management.Automation.Powershell.AddCommand](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) method to add commands to the pipeline.</span></span>
<span data-ttu-id="63718-112">例如，假設您想要取得電腦上正在執行的進程清單。</span><span class="sxs-lookup"><span data-stu-id="63718-112">For example, suppose you want to get the list of running processes on the machine.</span></span>
<span data-ttu-id="63718-113">執行此命令的方式如下所示。</span><span class="sxs-lookup"><span data-stu-id="63718-113">The way to run this command is as follows.</span></span>

1. <span data-ttu-id="63718-114">建立一個[system.web](/dotnet/api/System.Management.Automation.PowerShell)物件。</span><span class="sxs-lookup"><span data-stu-id="63718-114">Create a [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) object.</span></span>

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. <span data-ttu-id="63718-115">新增您想要執行的命令。</span><span class="sxs-lookup"><span data-stu-id="63718-115">Add the command that you want to execute.</span></span>

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. <span data-ttu-id="63718-116">叫用命令。</span><span class="sxs-lookup"><span data-stu-id="63718-116">Invoke the command.</span></span>

   ```csharp
   ps.Invoke();
   ```

<span data-ttu-id="63718-117">如果您在呼叫[AddCommand 方法之前](/dotnet/api/System.Management.Automation.PowerShell.Invoke)多次呼叫，則第一個命令的結果會以管道傳送至第二個命令，依此類推。</span><span class="sxs-lookup"><span data-stu-id="63718-117">If you call the AddCommand method more than once before you call the [System.Management.Automation.Powershell.Invoke](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, the result of the first command is piped to the second, and so on.</span></span>
<span data-ttu-id="63718-118">如果您不想要使用管線將上一個命令的結果傳送至命令，請改為呼叫[AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement)來加入它。</span><span class="sxs-lookup"><span data-stu-id="63718-118">If you do not want to pipe the result of a previous command to a command, add it by calling the [System.Management.Automation.Powershell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) instead.</span></span>

### <a name="addparameter"></a><span data-ttu-id="63718-119">AddParameter</span><span class="sxs-lookup"><span data-stu-id="63718-119">AddParameter</span></span>

<span data-ttu-id="63718-120">上一個範例會執行不含任何參數的單一命令。</span><span class="sxs-lookup"><span data-stu-id="63718-120">The previous example executes a single command without any parameters.</span></span>
<span data-ttu-id="63718-121">您可以使用[PSCommand. AddParameter](/dotnet/api/System.Management.Automation.PSCommand.AddParameter)方法，將參數新增至命令。</span><span class="sxs-lookup"><span data-stu-id="63718-121">You can add parameters to the command by using the [System.Management.Automation.PSCommand.AddParameter](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) method.</span></span>
<span data-ttu-id="63718-122">例如，下列程式碼會取得在電腦上執行且名為的所有處理常式清單 `PowerShell` 。</span><span class="sxs-lookup"><span data-stu-id="63718-122">For example, the following code gets a list of all of the processes that are named `PowerShell` running on the machine.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

<span data-ttu-id="63718-123">您可以重複呼叫 AddParameter 方法，以新增其他參數。</span><span class="sxs-lookup"><span data-stu-id="63718-123">You can add additional parameters by calling the AddParameter method repeatedly.</span></span>

```csharp                   
PowerShell.Create().AddCommand("Get-ChildItem")
                   .AddParameter("Path", @"c:\Windows")
                   .AddParameter("Filter", "*.exe")
                   .Invoke();
```

<span data-ttu-id="63718-124">您也可以藉由呼叫[AddParameters](/dotnet/api/System.Management.Automation.PowerShell.AddParameters)方法，加入參數名稱和值的字典。</span><span class="sxs-lookup"><span data-stu-id="63718-124">You can also add a dictionary of parameter names and values by calling the [System.Management.Automation.PowerShell.AddParameters](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) method.</span></span>

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Path", @"c:\Windows");
parameters.Add("Filter", "*.exe");

PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a><span data-ttu-id="63718-125">AddStatement</span><span class="sxs-lookup"><span data-stu-id="63718-125">AddStatement</span></span>

<span data-ttu-id="63718-126">您可以使用[AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement)方法來模擬批次處理，這會將額外的語句新增至管線的結尾。</span><span class="sxs-lookup"><span data-stu-id="63718-126">You can simulate batching by using the [System.Management.Automation.PowerShell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) method, which adds an additional statement to the end of the pipeline.</span></span>
<span data-ttu-id="63718-127">下列程式碼會取得名稱為的執行中進程清單 `PowerShell` ，然後取得正在執行的服務清單。</span><span class="sxs-lookup"><span data-stu-id="63718-127">The following code gets a list of running processes with the name `PowerShell`, and then gets the list of running services.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a><span data-ttu-id="63718-128">AddScript</span><span class="sxs-lookup"><span data-stu-id="63718-128">AddScript</span></span>

<span data-ttu-id="63718-129">您可以藉由呼叫[AddScript](/dotnet/api/System.Management.Automation.PowerShell.AddScript)方法來執行現有的腳本。</span><span class="sxs-lookup"><span data-stu-id="63718-129">You can run an existing script by calling the [System.Management.Automation.PowerShell.AddScript](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method.</span></span>
<span data-ttu-id="63718-130">下列範例會將腳本新增至管線並加以執行。</span><span class="sxs-lookup"><span data-stu-id="63718-130">The following example adds a script to the pipeline and runs it.</span></span>
<span data-ttu-id="63718-131">這個範例假設在名為的資料夾中已經有名為的腳本 `MyScript.ps1` `D:\PSScripts` 。</span><span class="sxs-lookup"><span data-stu-id="63718-131">This example assumes there is already a script named `MyScript.ps1` in a folder named `D:\PSScripts`.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

<span data-ttu-id="63718-132">另外還有一個版本的 AddScript 方法，它會採用名為的布林參數 `useLocalScope` 。</span><span class="sxs-lookup"><span data-stu-id="63718-132">There is also a version of the AddScript method that takes a boolean parameter named `useLocalScope`.</span></span>
<span data-ttu-id="63718-133">如果此參數設定為 `true` ，則腳本會在本機範圍中執行。</span><span class="sxs-lookup"><span data-stu-id="63718-133">If this parameter is set to `true`, then the script is run in the local scope.</span></span>
<span data-ttu-id="63718-134">下列程式碼會在本機範圍中執行腳本。</span><span class="sxs-lookup"><span data-stu-id="63718-134">The following code will run the script in the local scope.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

## <a name="creating-a-custom-runspace"></a><span data-ttu-id="63718-135">建立自訂運行空間</span><span class="sxs-lookup"><span data-stu-id="63718-135">Creating a custom runspace</span></span>

<span data-ttu-id="63718-136">雖然先前範例中使用的預設執行時間會載入所有核心 Windows PowerShell 命令，但是您可以建立自訂的執行時間，只載入所有命令的指定子集。</span><span class="sxs-lookup"><span data-stu-id="63718-136">While the default runspace used in the previous examples loads all of the core Windows PowerShell commands, you can create a custom runspace that loads only a specified subset of all commands.</span></span>
<span data-ttu-id="63718-137">您可能想要這麼做，以改善效能 (載入較大量的命令是) 的效能，或限制使用者執行作業的能力。</span><span class="sxs-lookup"><span data-stu-id="63718-137">You might want to do this to improve performance (loading a larger number of commands is a performance hit), or to restrict the capability of the user to perform operations.</span></span>
<span data-ttu-id="63718-138">只公開有限數目的命令的運行空間稱為受限制的運行空間。</span><span class="sxs-lookup"><span data-stu-id="63718-138">A runspace that exposes only a limited number of commands is called a constrained runspace.</span></span>
<span data-ttu-id="63718-139">若要建立受條件約束的執行空間，您可以使用 tialSessionState 類別和[System.Management.Automation.Runspaces.Ini](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)的執行[空間](/dotnet/api/System.Management.Automation.Runspaces.Runspace)。</span><span class="sxs-lookup"><span data-stu-id="63718-139">To create a constrained runspace, you use the [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) and [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) classes.</span></span>

### <a name="creating-an-initialsessionstate-object"></a><span data-ttu-id="63718-140">建立 InitialSessionState 物件</span><span class="sxs-lookup"><span data-stu-id="63718-140">Creating an InitialSessionState object</span></span>

<span data-ttu-id="63718-141">若要建立自訂的運行時，您必須先建立[System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)物件。</span><span class="sxs-lookup"><span data-stu-id="63718-141">To create a custom runspace, you must first create an [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>
<span data-ttu-id="63718-142">在下列範例中，我們會使用[RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) ，在建立預設 InitialSessionState 物件後建立運行空間。</span><span class="sxs-lookup"><span data-stu-id="63718-142">In the following example, we use the [System.Management.Automation.Runspaces.RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) to create a runspace after creating a default InitialSessionState object.</span></span>

```csharp
InitialSessionState iss = InitialSessionState.CreateDefault();
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
ps.Invoke();
```

### <a name="constraining-the-runspace"></a><span data-ttu-id="63718-143">限制運行空間</span><span class="sxs-lookup"><span data-stu-id="63718-143">Constraining the runspace</span></span>

<span data-ttu-id="63718-144">在上述範例中，我們建立了預設的[System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)物件，它會載入所有內建的核心 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="63718-144">In the previous example, we created a default [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object that loads all of the built-in core Windows PowerShell.</span></span>
<span data-ttu-id="63718-145">我們也可以呼叫[System.Management.Automation.Runspaces.InitialSessionState. CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2)方法來建立 InitialSessionState 物件，它只會載入中的命令。</span><span class="sxs-lookup"><span data-stu-id="63718-145">We could also have called the [System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) method to create an InitialSessionState object that would load only the commands in the Microsoft.PowerShell.Core snapin.</span></span>
<span data-ttu-id="63718-146">若要建立更受限制的運行時，您必須藉由呼叫[System.Management.Automation.Runspaces.InitialSessionState. create](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create)方法來建立空的 InitialSessionState 物件，然後將命令新增至 InitialSessionState。</span><span class="sxs-lookup"><span data-stu-id="63718-146">To create a more constrained runspace, you must create an empty InitialSessionState object by calling the [System.Management.Automation.Runspaces.InitialSessionState.Create](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) method, and then add commands to the InitialSessionState.</span></span>

<span data-ttu-id="63718-147">使用只載入您指定之命令的運行空間，可以大幅提升效能。</span><span class="sxs-lookup"><span data-stu-id="63718-147">Using a runspace that loads only the commands that you specify provides significantly improved performance.</span></span>

<span data-ttu-id="63718-148">您可以使用[SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry)類別的方法，來定義初始會話狀態的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="63718-148">You use the methods of the [System.Management.Automation.Runspaces.SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) class to define cmdlets for the initial session state.</span></span>
<span data-ttu-id="63718-149">下列範例會建立空的初始會話狀態，然後定義和命令，並將其新增 `Get-Command` `Import-Module` 至初始會話狀態。</span><span class="sxs-lookup"><span data-stu-id="63718-149">The following example creates an empty initial session state, then defines and adds the `Get-Command` and `Import-Module` commands to the initial session state.</span></span>
<span data-ttu-id="63718-150">接著，我們會建立該初始會話狀態所限制的運行時，並執行該運行空間中的命令。</span><span class="sxs-lookup"><span data-stu-id="63718-150">We then create a runspace constrained by that initial session state, and execute the commands in that runspace.</span></span>

<span data-ttu-id="63718-151">建立初始會話狀態。</span><span class="sxs-lookup"><span data-stu-id="63718-151">Create the initial session state.</span></span>

```csharp
InitialSessionState iss = InitialSessionState.Create();
```

<span data-ttu-id="63718-152">定義並將命令新增至初始會話狀態。</span><span class="sxs-lookup"><span data-stu-id="63718-152">Define and add commands to the initial session state.</span></span>

```csharp
SessionStateCmdletEntry getCommand = new SessionStateCmdletEntry(
        "Get-Command", typeof(Microsoft.PowerShell.Commands.GetCommandCommand), "");
SessionStateCmdletEntry importModule = new SessionStateCmdletEntry(
        "Import-Module", typeof(Microsoft.PowerShell.Commands.ImportModuleCommand), "");
iss.Commands.Add(getCommand);
iss.Commands.Add(importModule);
```

<span data-ttu-id="63718-153">建立並開啟該運行空間。</span><span class="sxs-lookup"><span data-stu-id="63718-153">Create and open the runspace.</span></span>

```csharp
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
```

<span data-ttu-id="63718-154">執行命令並顯示結果。</span><span class="sxs-lookup"><span data-stu-id="63718-154">Execute a command and show the result.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
Collection<CommandInfo> result = ps.Invoke<CommandInfo>();
foreach (var entry in result)
{
       Console.WriteLine(entry.Name);
}
```

<span data-ttu-id="63718-155">執行時，此程式碼的輸出看起來會像這樣。</span><span class="sxs-lookup"><span data-stu-id="63718-155">When run, the output of this code will look as follows.</span></span>

```powershell
Get-Command
Import-Module
```
