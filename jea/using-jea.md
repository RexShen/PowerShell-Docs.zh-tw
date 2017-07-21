---
ms.date: 2017-06-12
author: rpsqrd
ms.topic: conceptual
keywords: "jea,powershell,安全性"
title: "使用 JEA"
ms.openlocfilehash: 9996a432bca27240e0f08adf932126ced116985d
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="using-jea"></a><span data-ttu-id="50073-103">使用 JEA</span><span class="sxs-lookup"><span data-stu-id="50073-103">Using JEA</span></span>

> <span data-ttu-id="50073-104">適用對象：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="50073-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="50073-105">本主題說明您可以連線到並使用 JEA 端點的各種方式。</span><span class="sxs-lookup"><span data-stu-id="50073-105">This topic describes the various ways you can connect to and use a JEA endpoint.</span></span>

## <a name="using-jea-interactively"></a><span data-ttu-id="50073-106">以互動方式使用 JEA</span><span class="sxs-lookup"><span data-stu-id="50073-106">Using JEA interactively</span></span>

<span data-ttu-id="50073-107">如果您要測試您的 JEA 設定，或有要讓使用者執行的簡單工作，可以像一般 PowerShell 遠端工作階段一樣地使用 JEA。</span><span class="sxs-lookup"><span data-stu-id="50073-107">If you are testing your JEA configuration or have simple tasks for users to perform, you can use JEA the same way you would a regular PowerShell remoting session.</span></span>
<span data-ttu-id="50073-108">針對複雜的遠端工作，建議改用[隱含遠端](#using-jea-with-implicit-remoting)，允許使用者在本機操作資料物件，以便讓您的使用者可以比較輕鬆。</span><span class="sxs-lookup"><span data-stu-id="50073-108">For complex remoting tasks, it is recommended to use [implicit remoting](#using-jea-with-implicit-remoting) instead to make it easier for your users by allowing users to operate with the data objects locally.</span></span>

<span data-ttu-id="50073-109">若要以互動方式使用 JEA，您需要︰</span><span class="sxs-lookup"><span data-stu-id="50073-109">To use JEA interactively, you will need:</span></span>
- <span data-ttu-id="50073-110">要連線的目標電腦名稱 (可以是本機電腦)</span><span class="sxs-lookup"><span data-stu-id="50073-110">The name of the computer you are connecting to (can be the local machine)</span></span>
- <span data-ttu-id="50073-111">在該電腦上登錄的 JEA 端點名稱</span><span class="sxs-lookup"><span data-stu-id="50073-111">The name of the JEA endpoint registered on that computer</span></span>
- <span data-ttu-id="50073-112">能存取 JEA 端點的電腦認證</span><span class="sxs-lookup"><span data-stu-id="50073-112">Credentials for the computer that have access to the JEA endpoint</span></span>

<span data-ttu-id="50073-113">憑著此資訊，您可以使用 [New-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSSession) 或 [Enter-PSSession](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/enter-pssession)，啟動 JEA 工作階段。</span><span class="sxs-lookup"><span data-stu-id="50073-113">With that information in hand, you can start a JEA session using [New-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSSession) or [Enter-PSSession](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/enter-pssession).</span></span>

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

<span data-ttu-id="50073-114">如果您目前登入的帳戶可以存取 JEA 端點，則可以省略 `-Credential` 參數。</span><span class="sxs-lookup"><span data-stu-id="50073-114">If the account you're currently logged in as has access to the JEA endpoint, you can omit the `-Credential` parameter.</span></span>

<span data-ttu-id="50073-115">當 PowerShell 命令提示字元變更為 `[localhost]: PS>`，您會知道現在正在與遠端 JEA 工作階段互動。</span><span class="sxs-lookup"><span data-stu-id="50073-115">When the PowerShell prompt changes to `[localhost]: PS>` you will know that you are now interacting with the remote JEA session.</span></span>
<span data-ttu-id="50073-116">您可以執行 `Get-Command` 以檢查可用的命令。</span><span class="sxs-lookup"><span data-stu-id="50073-116">You can run `Get-Command` to check which commands are available.</span></span>
<span data-ttu-id="50073-117">您必須洽詢系統管理員以了解關於可用的參數或允許的參數值是否有任何限制。</span><span class="sxs-lookup"><span data-stu-id="50073-117">You will need to consult with your administrator to learn if there are any restrictions on the available parameters or allowable parameter values.</span></span>

<span data-ttu-id="50073-118">提醒您，JEA 工作階段在 NoLanguage 模式下運作，因此您平常使用 PowerShell 的部分方法可能無法使用。</span><span class="sxs-lookup"><span data-stu-id="50073-118">As a reminder, JEA sessions operate in NoLanguage mode, so some of the ways you typically use PowerShell may not be available.</span></span>
<span data-ttu-id="50073-119">例如，您不能使用變數來儲存資料，或檢查從 Cmdlet 傳回的物件上的屬性。</span><span class="sxs-lookup"><span data-stu-id="50073-119">For instance, you cannot use variables to store data or inspect the properties on objects returned from cmdlets.</span></span>
<span data-ttu-id="50073-120">以下範例顯示您目前可能使用 PowerShell 的方法，以及讓相同命令在 NoLanguage 模式下運作的兩種方法。</span><span class="sxs-lookup"><span data-stu-id="50073-120">The below example shows an example of how you may be using PowerShell today, and two approaches to get the same command working in NoLanguage mode.</span></span>

```powershell
# Using variables in NoLanguage mode is disallowed, so the following will not work
# $vm = Get-VM -Name 'SQL01'
# Start-VM -VM $vm

# You can use pipes to pass data through to commands that accept input from the pipeline
Get-VM -Name 'SQL01' | Start-VM

# You can also wrap subcommands in parentheses and enter them inline as arguments
Start-VM -VM (Get-VM -Name 'SQL01')

# Better yet, use parameter sets that don't require extra data to be passed in when possible
Start-VM -VMName 'SQL01'
```

<span data-ttu-id="50073-121">如需使這種方法變困難的更複雜命令引動過程，請考慮使用[隱含遠端](#using-jea-with-implicit-remoting)或[建立自訂函式](role-capabilities.md#creating-custom-functions)，包裝您想要的功能。</span><span class="sxs-lookup"><span data-stu-id="50073-121">For more complex command invocations that make this approach difficult, consider using [implicit remoting](#using-jea-with-implicit-remoting) or [creating custom functions](role-capabilities.md#creating-custom-functions) that wrap the functionality you desire.</span></span>

## <a name="using-jea-with-implicit-remoting"></a><span data-ttu-id="50073-122">以隱含遠端來使用 JEA</span><span class="sxs-lookup"><span data-stu-id="50073-122">Using JEA with implicit remoting</span></span>

<span data-ttu-id="50073-123">PowerShell 支援替代遠端模型，您可以在本機電腦上，從遠端電腦匯入 Proxy Cmdlet，並與其互動，如同它們是本機命令。</span><span class="sxs-lookup"><span data-stu-id="50073-123">PowerShell supports an alternative remoting model where you can import proxy cmdlets from a remote machine on your local computer and interact with them as if they were local commands.</span></span>
<span data-ttu-id="50073-124">這稱為隱含遠端，會在[這篇 *Hey, Scripting Guy!* 部落格文章](https://blogs.technet.microsoft.com/heyscriptingguy/2013/09/08/remoting-the-implicit-way/)中詳細說明。</span><span class="sxs-lookup"><span data-stu-id="50073-124">This is called implicit remoting, and is explained well in [this *Hey, Scripting Guy!* blog post](https://blogs.technet.microsoft.com/heyscriptingguy/2013/09/08/remoting-the-implicit-way/).</span></span>
<span data-ttu-id="50073-125">隱含遠端在使用 JEA 時特別有用，因為它可讓您能夠以完整的語言模式使用 JEA Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="50073-125">Implicit remoting is particularly useful when working with JEA because it allows you to work with JEA cmdlets in a full language mode.</span></span>
<span data-ttu-id="50073-126">這表示您可以使用 tab 鍵自動完成、變數、操作物件，甚至使用本機指令碼，更輕鬆地對 JEA 端點自動化作業。</span><span class="sxs-lookup"><span data-stu-id="50073-126">This means you can use tab completion, variables, manipulate objects, and even use local scripts to more easily automate against a JEA endpoint.</span></span>
<span data-ttu-id="50073-127">每當您叫用 Proxy 命令時，資料會傳送至遠端電腦上的 JEA 端點並且在該處執行。</span><span class="sxs-lookup"><span data-stu-id="50073-127">Anytime you invoke a proxy command, the data will be sent to the JEA endpoint on the remote machine and executed there.</span></span>

<span data-ttu-id="50073-128">隱含遠端的運作方式是從現有 PowerShell 工作階段匯入 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="50073-128">Implicit remoting works by importing cmdlets from an existing PowerShell session.</span></span>
<span data-ttu-id="50073-129">您可以選擇為每個 Proxy Cmdlet 的名詞，使用您選擇的字串來加上前置詞，以區別哪些命令是針對遠端系統。</span><span class="sxs-lookup"><span data-stu-id="50073-129">You can optionally choose to prefix the nouns of each proxy cmdlet with a string of your choosing to distinguish which commands are for the remote system.</span></span>
<span data-ttu-id="50073-130">會建立包含所有 Proxy 命令的暫存指令碼模組，並且可在本機 PowerShell 工作階段的持續時間內使用。</span><span class="sxs-lookup"><span data-stu-id="50073-130">A temporary script module containing all of the proxy commands will be created and can be used for the duration of your local PowerShell session.</span></span>

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> <span data-ttu-id="50073-131">有些系統可能無法匯入整個 JEA 工作階段，因為預設的 JEA Cmdlet 中有條件約束。</span><span class="sxs-lookup"><span data-stu-id="50073-131">Some systems may not be able to import an entire JEA session due to constraints in the default JEA cmdlets.</span></span>
> <span data-ttu-id="50073-132">若要解決這個問題，您可以只從 JEA 工作階段匯入需要的命令，方法是明確地提供其名稱給 `-CommandName` 參數。</span><span class="sxs-lookup"><span data-stu-id="50073-132">To get around this, only import the commands you need from the JEA session by explicitly providing their names to the `-CommandName` parameter.</span></span>
> <span data-ttu-id="50073-133">未來的更新將會解決在受影響的系統上匯入整個 JEA 工作階段的問題。</span><span class="sxs-lookup"><span data-stu-id="50073-133">A future update will address the issue with importing entire JEA sessions on affected systems.</span></span>

<span data-ttu-id="50073-134">如果您因為預設 JEA 參數的條件約束而無法匯入 JEA 工作階段，可以依照下列步驟，從匯入的集合篩選掉預設命令。</span><span class="sxs-lookup"><span data-stu-id="50073-134">If you are unable to import a JEA session due to constraints on the default JEA parameters, you can follow the steps below to filter out the default commands from the imported set.</span></span>
<span data-ttu-id="50073-135">您仍然可以使用像是 `Select-Object` 的命令 -- 您會在 JEA 工作階段中使用安裝在您電腦上的本機版本，而不是遠端版本。</span><span class="sxs-lookup"><span data-stu-id="50073-135">You will still be able to use commands like `Select-Object` -- you'll just use the local version installed on your computer instead of the remote one in the JEA session.</span></span>

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Get a list of all the commands on the JEA endpoint
$commands = Invoke-Command -Session $jeasession -ScriptBlock { Get-Command }

# Filter out the default cmdlets
$jeaDefaultCmdlets = 'Clear-Host', 'Exit-PSSession', 'Get-Command', 'Get-FormatData', 'Get-Help', 'Measure-Object', 'Out-Default', 'Select-Object'
$filteredCommands = $commands.Name | Where-Object { $jeaDefaultCmdlets -notcontains $_ }

# Import only commands explicitly added in role capabilities and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA' -CommandName $filteredCommands 
```

<span data-ttu-id="50073-136">您也可以使用 [Export-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/Export-PSSession) 從隱含遠端保存代理 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="50073-136">You can also persist the proxied cmdlets from implicit remoting using [Export-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/Export-PSSession).</span></span>
<span data-ttu-id="50073-137">如需隱含遠端的詳細資訊，請參閱 [Import-PSSession](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.utility/import-pssession) 和 [Import-Module](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/import-module) 的說明文件。</span><span class="sxs-lookup"><span data-stu-id="50073-137">For more information about implicit remoting, check out the help documentation for [Import-PSSession](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.utility/import-pssession) and [Import-Module](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/import-module).</span></span>

## <a name="using-jea-programatically"></a><span data-ttu-id="50073-138">以程式設計方式使用 JEA</span><span class="sxs-lookup"><span data-stu-id="50073-138">Using JEA programatically</span></span>

<span data-ttu-id="50073-139">JEA 也可用在自動化系統和使用者應用程式，例如公司內部的技術支援應用程式和網站。</span><span class="sxs-lookup"><span data-stu-id="50073-139">JEA can also be used in automation systems and in user applications, such as in-house helpdesk apps and web sites.</span></span>
<span data-ttu-id="50073-140">方式與建置和未受限制之 PowerShell 端點通訊的應用程式相同，但有一點要注意，程式應該要注意 JEA 會限制可以在遠端工作階段中執行的命令。</span><span class="sxs-lookup"><span data-stu-id="50073-140">The approach is the same as that for building apps that talk to unconstrained PowerShell endpoints, with the caveat that the program should be aware that JEA is limiting the commands that can be run in the remote session.</span></span>

<span data-ttu-id="50073-141">對於簡單的一次性工作，您可以使用 [Invoke-Command](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/invoke-command)，使用 JEA 執行一組命令。</span><span class="sxs-lookup"><span data-stu-id="50073-141">For simple, one-off tasks, you can use [Invoke-Command](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/invoke-command) to run a set of commands using JEA.</span></span>

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

<span data-ttu-id="50073-142">若要檢查哪些命令可用於當您連線到 JEA 工作階段時，請執行 `Get-Command` 並逐一查看結果，以便檢查允許的參數。</span><span class="sxs-lookup"><span data-stu-id="50073-142">To check which commands are available for use when you connect to a JEA session, run `Get-Command` and iterate through the results to check for the allowed parameters.</span></span>

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

<span data-ttu-id="50073-143">如果您正在建置 C# 應用程式，可以在 [WSManConnectionInfo](https://msdn.microsoft.com/en-us/library/system.management.automation.runspaces.wsmanconnectioninfo(v=vs.85).aspx) 物件中指定設定名稱，建立連線至 JEA 工作階段的 PowerShell 執行空間。</span><span class="sxs-lookup"><span data-stu-id="50073-143">If you are building a C# app, you can create a PowerShell runspace that connects to a JEA session by specifying the configuration name in a [WSManConnectionInfo](https://msdn.microsoft.com/en-us/library/system.management.automation.runspaces.wsmanconnectioninfo(v=vs.85).aspx) object.</span></span>

```csharp

// using System.Management.Automation;
var computerName = "SERVER01";
var configName   = "JEAMaintenance";
var creds        = // create a PSCredential object here (https://msdn.microsoft.com/en-us/library/system.management.automation.pscredential(v=vs.85).aspx)

WSManConnectionInfo connectionInfo = new WSManConnectionInfo(
                    false,                 // Use SSL
                    computerName,          // Computer name
                    5985,                  // WSMan Port
                    "/wsman",              // WSMan Path
                    string.Format(CultureInfo.InvariantCulture, "http://schemas.microsoft.com/powershell/{0}", configName),  // Connection URI with config name
                    creds);                // Credentials
// Now, use the connection info to create a runspace where you can run the commands
using (Runspace runspace = RunspaceFactory.CreateRunspace(connectionInfo))
{
    // Open the runspace
    runspace.Open();

    using (PowerShell ps = PowerShell.Create())
    {
        // Set the PowerShell object to use the JEA runspace
        ps.Runspace = runspace;

        // Now you can add and invoke commands
        ps.AddCommand("Get-Command");
        foreach (var result in ps.Invoke())
        {
            Console.WriteLine(result);
        }
    }

    // Close the runspace
    runspace.Close();
}
```

## <a name="using-jea-with-powershell-direct"></a><span data-ttu-id="50073-144">搭配使用 PowerShell Direct 和 JEA</span><span class="sxs-lookup"><span data-stu-id="50073-144">Using JEA with PowerShell Direct</span></span>

<span data-ttu-id="50073-145">在 Windows 10 和 Windows Server 2016 中的 Hyper-V 提供 [PowerShell Direct](https://msdn.microsoft.com/en-us/virtualization/hyperv_on_windows/user_guide/vmsession)，這項功能允許 Hyper-V 系統管理員使用 PowerShell 管理虛擬機器，不論虛擬機器上的網路設定或遠端管理設定為何。</span><span class="sxs-lookup"><span data-stu-id="50073-145">Hyper-V in Windows 10 and Windows Server 2016 offers [PowerShell Direct](https://msdn.microsoft.com/en-us/virtualization/hyperv_on_windows/user_guide/vmsession), a feature which allows Hyper-V administrators to manage virtual machines with PowerShell regardless of the network configuration or remote management settings on the virtual machine.</span></span>

<span data-ttu-id="50073-146">您可以使用 PowerShell Direct 搭配 JEA，讓您的 Hyper-V 系統管理員具有 VM 的有限存取權，這適用於您失去 VM 的網路連線，且需要資料中心系統管理員修正網路設定的情況。</span><span class="sxs-lookup"><span data-stu-id="50073-146">You can use PowerShell Direct with JEA to give a Hyper-V administrator limited access to your VM, which can be useful if you lose network connectivity to your VM and need a datacenter admin to fix the network settings.</span></span>

<span data-ttu-id="50073-147">不需要額外的設定即可透過 PowerShell Direct 來使用 JEA，不過在虛擬機器內執行的作業系統必須是 Windows 10 或 Windows Server 2016。</span><span class="sxs-lookup"><span data-stu-id="50073-147">No additional configuration is required to use JEA over PowerShell Direct, however the operating system running inside the virtual machine must be Windows 10 or Windows Server 2016.</span></span>
<span data-ttu-id="50073-148">Hyper-V 系統管理員可利用 PSRemoting Cmdlet 的 `-VMName` 或 `-VMId` 參數連線到 JEA 端點︰</span><span class="sxs-lookup"><span data-stu-id="50073-148">The Hyper-V admin can connect to the JEA endpoint by using the `-VMName` or `-VMId` parameters on PSRemoting cmdlets:</span></span>

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

<span data-ttu-id="50073-149">強烈建議您建立沒有其他系統管理權限的專屬本機使用者，供您的 Hyper-V 系統管理員使用。</span><span class="sxs-lookup"><span data-stu-id="50073-149">It is strongly recommended that you create a dedicated local user with no other rights to manage the system for your Hyper-V administrators to use.</span></span>
<span data-ttu-id="50073-150">請記住，根據預設，即使無權限的使用者也仍然可以登入 Windows 電腦，包括使用不受限制的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="50073-150">Remember that even an unprivileged user can still log into a Windows machine by default, including using unconstrained PowerShell.</span></span>
<span data-ttu-id="50073-151">那樣會允許他們瀏覽 (部分) 檔案系統，並深入了解您的作業系統環境。</span><span class="sxs-lookup"><span data-stu-id="50073-151">That will allow them to browse (some of) the file system and learn more about your OS environment.</span></span>
<span data-ttu-id="50073-152">若要將 Hyper-V 系統管理員鎖定於只能使用 PowerShell Direct 與 JEA 來存取 VM，您將會需要拒絕 Hyper-V 系統管理員 JEA 帳戶的本機登入權限。</span><span class="sxs-lookup"><span data-stu-id="50073-152">To lock down a Hyper-V administrator to only access a VM using PowerShell Direct with JEA, you will need to deny local logon rights to the Hyper-V admin's JEA account.</span></span>

