---
title: Windows PowerShell 主應用程式快速入門 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5a134b81-bd0c-4e1c-a2f0-9acbe852745a
caps.latest.revision: 9
ms.openlocfilehash: 9a080b6db7416ae6bf65a1b0353e9f17a56cc6c5
ms.sourcegitcommit: 00cf9a99972ce40db7c25b9a3fc6152dec6bddb6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64530613"
---
# <a name="windows-powershell-host-quickstart"></a><span data-ttu-id="75368-102">Windows PowerShell 主機快速入門</span><span class="sxs-lookup"><span data-stu-id="75368-102">Windows PowerShell Host Quickstart</span></span>

<span data-ttu-id="75368-103">若要在您的應用程式中裝載 Windows PowerShell，使用[System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell)類別。</span><span class="sxs-lookup"><span data-stu-id="75368-103">To host Windows PowerShell in your application, you use the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class.</span></span>
<span data-ttu-id="75368-104">這個類別提供建立命令的管線，然後在 runspace 中執行這些命令的方法。</span><span class="sxs-lookup"><span data-stu-id="75368-104">This class provides methods that create a pipeline of commands and then execute those commands in a runspace.</span></span>
<span data-ttu-id="75368-105">建立主應用程式的最簡單方式是使用預設的 runspace。</span><span class="sxs-lookup"><span data-stu-id="75368-105">The simplest way to create a host application is to use the default runspace.</span></span>
<span data-ttu-id="75368-106">預設的 runspace 中包含所有的核心 Windows PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="75368-106">The default runspace contains all of the core Windows PowerShell commands.</span></span>
<span data-ttu-id="75368-107">如果您想您的應用程式公開 （expose） 的 Windows PowerShell 命令的子集，您必須建立自訂的 runspace。</span><span class="sxs-lookup"><span data-stu-id="75368-107">If you want your application to expose only a subset of the Windows PowerShell commands, you must create a custom runspace.</span></span>

## <a name="using-the-default-runspace"></a><span data-ttu-id="75368-108">使用預設的 runspace</span><span class="sxs-lookup"><span data-stu-id="75368-108">Using the default runspace</span></span>

<span data-ttu-id="75368-109">若要開始，我們將使用預設的 runspace，並使用的方法[System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell)類別將命令、 參數、 陳述式和指令碼新增至管線。</span><span class="sxs-lookup"><span data-stu-id="75368-109">To start, we'll use the default runspace, and use the methods of the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class to add commands, parameters, statements, and scripts to a pipeline.</span></span>

### <a name="addcommand"></a><span data-ttu-id="75368-110">AddCommand</span><span class="sxs-lookup"><span data-stu-id="75368-110">AddCommand</span></span>

<span data-ttu-id="75368-111">您使用[System.Management.Automation.Powershell.AddCommand](/dotnet/api/System.Management.Automation.PowerShell.AddCommand)方法，將命令加入至管線。</span><span class="sxs-lookup"><span data-stu-id="75368-111">You use the [System.Management.Automation.Powershell.AddCommand](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) method to add commands to the pipeline.</span></span>
<span data-ttu-id="75368-112">例如，假設您想要取得的電腦上執行的處理序清單。</span><span class="sxs-lookup"><span data-stu-id="75368-112">For example, suppose you want to get the list of running processes on the machine.</span></span>
<span data-ttu-id="75368-113">若要執行此命令的方式如下所示。</span><span class="sxs-lookup"><span data-stu-id="75368-113">The way to run this command is as follows.</span></span>

1. <span data-ttu-id="75368-114">建立[System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell)物件。</span><span class="sxs-lookup"><span data-stu-id="75368-114">Create a [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) object.</span></span>

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. <span data-ttu-id="75368-115">新增您想要執行的命令。</span><span class="sxs-lookup"><span data-stu-id="75368-115">Add the command that you want to execute.</span></span>

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. <span data-ttu-id="75368-116">叫用命令。</span><span class="sxs-lookup"><span data-stu-id="75368-116">Invoke the command.</span></span>

   ```csharp
   ps.Invoke();
   ```

<span data-ttu-id="75368-117">如果您呼叫 AddCommand 方法超過一次呼叫前先[System.Management.Automation.Powershell.Invoke](/dotnet/api/System.Management.Automation.PowerShell.Invoke)方法，第一個命令的結果會輸送到第二個，依此類推。</span><span class="sxs-lookup"><span data-stu-id="75368-117">If you call the AddCommand method more than once before you call the [System.Management.Automation.Powershell.Invoke](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, the result of the first command is piped to the second, and so on.</span></span>
<span data-ttu-id="75368-118">如果您不想透過管道傳送命令前一個命令的結果，會將它加入藉由呼叫[System.Management.Automation.Powershell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement)改。</span><span class="sxs-lookup"><span data-stu-id="75368-118">If you do not want to pipe the result of a previous command to a command, add it by calling the [System.Management.Automation.Powershell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) instead.</span></span>

### <a name="addparameter"></a><span data-ttu-id="75368-119">AddParameter</span><span class="sxs-lookup"><span data-stu-id="75368-119">AddParameter</span></span>

<span data-ttu-id="75368-120">前一個範例會執行不含任何參數的單一命令。</span><span class="sxs-lookup"><span data-stu-id="75368-120">The previous example executes a single command without any parameters.</span></span>
<span data-ttu-id="75368-121">可以透過將參數新增至命令[System.Management.Automation.PSCommand.AddParameter](/dotnet/api/System.Management.Automation.PSCommand.AddParameter)方法。</span><span class="sxs-lookup"><span data-stu-id="75368-121">You can add parameters to the command by using the [System.Management.Automation.PSCommand.AddParameter](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) method.</span></span>
<span data-ttu-id="75368-122">例如，下列程式碼會取得一份所有程序會在名為`PowerShell`機器上執行。</span><span class="sxs-lookup"><span data-stu-id="75368-122">For example, the following code gets a list of all of the processes that are named `PowerShell` running on the machine.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

<span data-ttu-id="75368-123">您可以重複呼叫 AddParameter 方法，以新增其他參數。</span><span class="sxs-lookup"><span data-stu-id="75368-123">You can add additional parameters by calling the AddParameter method repeatedly.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

<span data-ttu-id="75368-124">您也可以藉由呼叫來新增參數名稱和值的字典[System.Management.Automation.PowerShell.AddParameters](/dotnet/api/System.Management.Automation.PowerShell.AddParameters)方法。</span><span class="sxs-lookup"><span data-stu-id="75368-124">You can also add a dictionary of parameter names and values by calling the [System.Management.Automation.PowerShell.AddParameters](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) method.</span></span>

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a><span data-ttu-id="75368-125">AddStatement</span><span class="sxs-lookup"><span data-stu-id="75368-125">AddStatement</span></span>

<span data-ttu-id="75368-126">您可以使用批次處理來模擬[System.Management.Automation.PowerShell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement)方法，將其他的陳述式加入至管線的尾端。</span><span class="sxs-lookup"><span data-stu-id="75368-126">You can simulate batching by using the [System.Management.Automation.PowerShell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) method, which adds an additional statement to the end of the pipeline.</span></span>
<span data-ttu-id="75368-127">下列程式碼取得的執行中處理序名稱清單`PowerShell`，然後取得執行中服務的清單。</span><span class="sxs-lookup"><span data-stu-id="75368-127">The following code gets a list of running processes with the name `PowerShell`, and then gets the list of running services.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a><span data-ttu-id="75368-128">AddScript</span><span class="sxs-lookup"><span data-stu-id="75368-128">AddScript</span></span>

<span data-ttu-id="75368-129">您可以執行現有的指令碼，藉由呼叫[System.Management.Automation.PowerShell.AddScript](/dotnet/api/System.Management.Automation.PowerShell.AddScript)方法。</span><span class="sxs-lookup"><span data-stu-id="75368-129">You can run an existing script by calling the [System.Management.Automation.PowerShell.AddScript](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method.</span></span>
<span data-ttu-id="75368-130">下列範例會將指令碼新增至管線，並執行它。</span><span class="sxs-lookup"><span data-stu-id="75368-130">The following example adds a script to the pipeline and runs it.</span></span>
<span data-ttu-id="75368-131">這個範例假設已經有名稱為指令碼`MyScript.ps1`在名為的資料夾中`D:\PSScripts`。</span><span class="sxs-lookup"><span data-stu-id="75368-131">This example assumes there is already a script named `MyScript.ps1` in a folder named `D:\PSScripts`.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

<span data-ttu-id="75368-132">另外還有 AddScript 方法接受名為的布林值參數的版本`useLocalScope`。</span><span class="sxs-lookup"><span data-stu-id="75368-132">There is also a version of the AddScript method that takes a boolean parameter named `useLocalScope`.</span></span>
<span data-ttu-id="75368-133">如果此參數設為`true`，則指令碼會執行本機範圍內。</span><span class="sxs-lookup"><span data-stu-id="75368-133">If this parameter is set to `true`, then the script is run in the local scope.</span></span>
<span data-ttu-id="75368-134">下列程式碼會在本機的範圍內執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="75368-134">The following code will run the script in the local scope.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

## <a name="creating-a-custom-runspace"></a><span data-ttu-id="75368-135">建立自訂的 runspace</span><span class="sxs-lookup"><span data-stu-id="75368-135">Creating a custom runspace</span></span>

<span data-ttu-id="75368-136">雖然先前的範例中使用的預設 runspace 載入所有的核心 Windows PowerShell 命令，您可以建立自訂的 runspace 可載入的指定的子集的所有命令。</span><span class="sxs-lookup"><span data-stu-id="75368-136">While the default runspace used in the previous examples loads all of the core Windows PowerShell commands, you can create a custom runspace that loads only a specified subset of all commands.</span></span>
<span data-ttu-id="75368-137">您可能想要這樣做可以改善效能 （載入大量的命令會影響效能），或限制使用者能夠執行作業。</span><span class="sxs-lookup"><span data-stu-id="75368-137">You might want to do this to improve performance (loading a larger number of commands is a performance hit), or to restrict the capability of the user to perform operations.</span></span>
<span data-ttu-id="75368-138">會公開有限的數目的命令的 runspace 稱為受限的 runspace。</span><span class="sxs-lookup"><span data-stu-id="75368-138">A runspace that exposes only a limited number of commands is called a constrained runspace.</span></span>
<span data-ttu-id="75368-139">若要建立受限的 runspace，您使用[System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace)並[System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)類別。</span><span class="sxs-lookup"><span data-stu-id="75368-139">To create a constrained runspace, you use the [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) and [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) classes.</span></span>

### <a name="creating-an-initialsessionstate-object"></a><span data-ttu-id="75368-140">建立 InitialSessionState 物件</span><span class="sxs-lookup"><span data-stu-id="75368-140">Creating an InitialSessionState object</span></span>

<span data-ttu-id="75368-141">若要建立自訂的 runspace，您必須先建立[System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)物件。</span><span class="sxs-lookup"><span data-stu-id="75368-141">To create a custom runspace, you must first create an [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>
<span data-ttu-id="75368-142">在下列範例中，我們會使用[System.Management.Automation.Runspaces.RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory)建立 runspace，建立預設 InitialSessionState 物件之後。</span><span class="sxs-lookup"><span data-stu-id="75368-142">In the following example, we use the [System.Management.Automation.Runspaces.RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) to create a runspace after creating a default InitialSessionState object.</span></span>

```csharp
InitialSessionState iss = InitialSessionState.CreateDefault();
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
ps.Invoke();
```

### <a name="constraining-the-runspace"></a><span data-ttu-id="75368-143">限制的 runspace</span><span class="sxs-lookup"><span data-stu-id="75368-143">Constraining the runspace</span></span>

<span data-ttu-id="75368-144">在上述範例中，我們已建立預設值[System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState)載入所有內建的核心 Windows PowerShell 的物件。</span><span class="sxs-lookup"><span data-stu-id="75368-144">In the previous example, we created a default [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object that loads all of the built-in core Windows PowerShell.</span></span>
<span data-ttu-id="75368-145">我們可能也會有稱為[System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2)方法用來建立 InitialSessionState 物件，會載入只有 Microsoft.PowerShell.Core 中的命令嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="75368-145">We could also have called the [System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) method to create an InitialSessionState object that would load only the commands in the Microsoft.PowerShell.Core snapin.</span></span>
<span data-ttu-id="75368-146">若要建立更受限的 runspace，您必須建立一個空的 InitialSessionState 物件呼叫[System.Management.Automation.Runspaces.InitialSessionState.Create](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create)方法，然後新增命令InitialSessionState。</span><span class="sxs-lookup"><span data-stu-id="75368-146">To create a more constrained runspace, you must create an empty InitialSessionState object by calling the [System.Management.Automation.Runspaces.InitialSessionState.Create](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) method, and then add commands to the InitialSessionState.</span></span>

<span data-ttu-id="75368-147">使用您指定的命令會載入 runspace 提供大幅改善的效能。</span><span class="sxs-lookup"><span data-stu-id="75368-147">Using a runspace that loads only the commands that you specify provides significantly improved performance.</span></span>

<span data-ttu-id="75368-148">您使用的方法[System.Management.Automation.Runspaces.SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry)類別來定義初始工作階段狀態的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="75368-148">You use the methods of the [System.Management.Automation.Runspaces.SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) class to define cmdlets for the initial session state.</span></span>
<span data-ttu-id="75368-149">下列範例會建立空的初始工作階段狀態，然後定義並加入`Get-Command`和`Import-Module`命令來初始工作階段狀態。</span><span class="sxs-lookup"><span data-stu-id="75368-149">The following example creates an empty initial session state, then defines and adds the `Get-Command` and `Import-Module` commands to the initial session state.</span></span>
<span data-ttu-id="75368-150">然後，我們會建立 runspace，受到初始工作階段狀態，並在該 runspace 中執行命令。</span><span class="sxs-lookup"><span data-stu-id="75368-150">We then create a runspace constrained by that initial session state, and execute the commands in that runspace.</span></span>

<span data-ttu-id="75368-151">建立初始工作階段狀態。</span><span class="sxs-lookup"><span data-stu-id="75368-151">Create the initial session state.</span></span>

```csharp
InitialSessionState iss = InitialSessionState.Create();
```

<span data-ttu-id="75368-152">定義，並將命令加入至初始工作階段狀態。</span><span class="sxs-lookup"><span data-stu-id="75368-152">Define and add commands to the initial session state.</span></span>

```csharp
SessionStateCmdletEntry getCommand = new SessionStateCmdletEntry(
        "Get-Command", typeof(Microsoft.PowerShell.Commands.GetCommandCommand), "");
SessionStateCmdletEntry importModule = new SessionStateCmdletEntry(
        "Import-Module", typeof(Microsoft.PowerShell.Commands.ImportModuleCommand), "");
iss.Commands.Add(getCommand);
iss.Commands.Add(importModule);
```

<span data-ttu-id="75368-153">建立並開啟 runspace。</span><span class="sxs-lookup"><span data-stu-id="75368-153">Create and open the runspace.</span></span>

```csharp
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
```

<span data-ttu-id="75368-154">執行命令，並顯示結果。</span><span class="sxs-lookup"><span data-stu-id="75368-154">Execute a command and show the result.</span></span>

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

<span data-ttu-id="75368-155">當執行時，此程式碼的輸出會看起來像這樣。</span><span class="sxs-lookup"><span data-stu-id="75368-155">When run, the output of this code will look as follows.</span></span>

```powershell
Get-Command
Import-Module
```
