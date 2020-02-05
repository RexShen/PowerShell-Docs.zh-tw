---
ms.date: 07/10/2019
keywords: jea,powershell,安全性
title: 使用 JEA
ms.openlocfilehash: 912e7a3c46be40ff5b5dfa37fe92b67bab5f98dc
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/04/2020
ms.locfileid: "76995433"
---
# <a name="using-jea"></a><span data-ttu-id="5b6a0-103">使用 JEA</span><span class="sxs-lookup"><span data-stu-id="5b6a0-103">Using JEA</span></span>

<span data-ttu-id="5b6a0-104">本文描述您可以連線到並使用 JEA 端點的各種方式。</span><span class="sxs-lookup"><span data-stu-id="5b6a0-104">This article describes the various ways you can connect to and use a JEA endpoint.</span></span>

## <a name="using-jea-interactively"></a><span data-ttu-id="5b6a0-105">以互動方式使用 JEA</span><span class="sxs-lookup"><span data-stu-id="5b6a0-105">Using JEA interactively</span></span>

<span data-ttu-id="5b6a0-106">如果您要測試 JEA 設定，或有要供使用者運用的簡單工作，可以如同一般 PowerShell 遠端工作階段一樣地使用 JEA。</span><span class="sxs-lookup"><span data-stu-id="5b6a0-106">If you're testing your JEA configuration or have simple tasks for users, you can use JEA the same way you would a regular PowerShell remoting session.</span></span> <span data-ttu-id="5b6a0-107">針對複雜的遠端工作，建議使用[隱含遠端](#using-jea-with-implicit-remoting)。</span><span class="sxs-lookup"><span data-stu-id="5b6a0-107">For complex remoting tasks, it's recommended to use [implicit remoting](#using-jea-with-implicit-remoting).</span></span> <span data-ttu-id="5b6a0-108">隱含遠端處理可讓使用者與資料物件在本機運作。</span><span class="sxs-lookup"><span data-stu-id="5b6a0-108">Implicit remoting allows users to operate with the data objects locally.</span></span>

<span data-ttu-id="5b6a0-109">若要以互動方式使用 JEA，您需要︰</span><span class="sxs-lookup"><span data-stu-id="5b6a0-109">To use JEA interactively, you need:</span></span>

- <span data-ttu-id="5b6a0-110">要連線的目標電腦名稱 (可以是本機電腦)</span><span class="sxs-lookup"><span data-stu-id="5b6a0-110">The name of the computer you're connecting to (can be the local machine)</span></span>
- <span data-ttu-id="5b6a0-111">在該電腦上登錄的 JEA 端點名稱</span><span class="sxs-lookup"><span data-stu-id="5b6a0-111">The name of the JEA endpoint registered on that computer</span></span>
- <span data-ttu-id="5b6a0-112">在該電腦上能存取 JEA 端點的電腦認證</span><span class="sxs-lookup"><span data-stu-id="5b6a0-112">Credentials that have access to the JEA endpoint on that computer</span></span>

<span data-ttu-id="5b6a0-113">有了此資訊，您可以使用 [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) 或 [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) Cmdlet 來啟動 JEA 工作階段。</span><span class="sxs-lookup"><span data-stu-id="5b6a0-113">Given that information, you can start a JEA session using the [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) or [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlets.</span></span>

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

<span data-ttu-id="5b6a0-114">如果您目前的使用者帳戶可以存取 JEA 端點，則可以省略**認證**參數。</span><span class="sxs-lookup"><span data-stu-id="5b6a0-114">If the current user account has access to the JEA endpoint, you can omit the **Credential** parameter.</span></span>

<span data-ttu-id="5b6a0-115">當 PowerShell 命令提示字元變更為 `[localhost]: PS>`，您會知道現在正在與遠端 JEA 工作階段互動。</span><span class="sxs-lookup"><span data-stu-id="5b6a0-115">When the PowerShell prompt changes to `[localhost]: PS>` you know that you're now interacting with the remote JEA session.</span></span> <span data-ttu-id="5b6a0-116">您可以執行 `Get-Command` 以檢查可用的命令。</span><span class="sxs-lookup"><span data-stu-id="5b6a0-116">You can run `Get-Command` to check which commands are available.</span></span> <span data-ttu-id="5b6a0-117">請洽詢系統管理員以了解可用的參數，或允許的參數值是否有任何限制。</span><span class="sxs-lookup"><span data-stu-id="5b6a0-117">Consult with your administrator to learn if there are any restrictions on the available parameters or allowed parameter values.</span></span>

<span data-ttu-id="5b6a0-118">請記住，JEA 工作階段在 NoLanguage 模式中運作。</span><span class="sxs-lookup"><span data-stu-id="5b6a0-118">Remember, JEA sessions operate in NoLanguage mode.</span></span> <span data-ttu-id="5b6a0-119">您可能會無法使用 PowerShell 的一些平常使用方式。</span><span class="sxs-lookup"><span data-stu-id="5b6a0-119">Some of the ways you typically use PowerShell may not be available.</span></span> <span data-ttu-id="5b6a0-120">例如，您不能使用變數來儲存資料，或檢查從 Cmdlet 傳回的物件上屬性。</span><span class="sxs-lookup"><span data-stu-id="5b6a0-120">For instance, you can't use variables to store data or inspect the properties on objects returned from cmdlets.</span></span> <span data-ttu-id="5b6a0-121">下列範例示範兩種方法，讓相同的命令在 NoLanguage 模式下運作。</span><span class="sxs-lookup"><span data-stu-id="5b6a0-121">The following example shows two approaches to get the same commands to work in NoLanguage mode.</span></span>

```powershell
# Using variables is prohibited in NoLanguage mode. The following will not work:
# $vm = Get-VM -Name 'SQL01'
# Start-VM -VM $vm

# You can use pipes to pass data through to commands that accept input from the pipeline
Get-VM -Name 'SQL01' | Start-VM

# You can also wrap subcommands in parentheses and enter them inline as arguments
Start-VM -VM (Get-VM -Name 'SQL01')

# You can also use parameter sets that don't require extra data to be passed in
Start-VM -VMName 'SQL01'
```

<span data-ttu-id="5b6a0-122">如需使這種方法變困難的更複雜命令引動過程，請考慮使用[隱含遠端](#using-jea-with-implicit-remoting)或[建立自訂函式](role-capabilities.md#creating-custom-functions)，其包裝您需要的功能。</span><span class="sxs-lookup"><span data-stu-id="5b6a0-122">For more complex command invocations that make this approach difficult, consider using [implicit remoting](#using-jea-with-implicit-remoting) or [creating custom functions](role-capabilities.md#creating-custom-functions) that wrap the functionality you require.</span></span>

## <a name="using-jea-with-implicit-remoting"></a><span data-ttu-id="5b6a0-123">以隱含遠端來使用 JEA</span><span class="sxs-lookup"><span data-stu-id="5b6a0-123">Using JEA with implicit remoting</span></span>

<span data-ttu-id="5b6a0-124">PowerShell 具有隱含遠端模型，可讓您從遠端電腦匯入 Proxy Cmdlet 並與其互動，如同它們是本機命令一樣。</span><span class="sxs-lookup"><span data-stu-id="5b6a0-124">PowerShell has an implicit remoting model that lets you import proxy cmdlets from a remote machine and interact with them as if they were local commands.</span></span> <span data-ttu-id="5b6a0-125">如需隱含遠端的說明，請參閱 **Hey, Scripting Guy!**</span><span class="sxs-lookup"><span data-stu-id="5b6a0-125">Implicit remoting is explained in this **Hey, Scripting Guy!**</span></span> <span data-ttu-id="5b6a0-126">[部落格文章](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/)。</span><span class="sxs-lookup"><span data-stu-id="5b6a0-126">[blog post](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/).</span></span>
<span data-ttu-id="5b6a0-127">隱含遠端在使用 JEA 時很有用，因為可讓您能夠以完整的語言模式使用 JEA Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5b6a0-127">Implicit remoting is useful when working with JEA because it allows you to work with JEA cmdlets in a full language mode.</span></span> <span data-ttu-id="5b6a0-128">您可以使用 Tab 鍵自動完成、變數、操作物件，甚至使用本機指令碼對 JEA 端點自動執行工作。</span><span class="sxs-lookup"><span data-stu-id="5b6a0-128">You can use tab completion, variables, manipulate objects, and even use local scripts to automate tasks against a JEA endpoint.</span></span> <span data-ttu-id="5b6a0-129">每當您叫用 Proxy 命令時，資料會傳送至遠端電腦上的 JEA 端點並且在該處執行。</span><span class="sxs-lookup"><span data-stu-id="5b6a0-129">Anytime you invoke a proxy command, the data is sent to the JEA endpoint on the remote machine and executed there.</span></span>

<span data-ttu-id="5b6a0-130">隱含遠端的運作方式是從現有 PowerShell 工作階段匯入 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5b6a0-130">Implicit remoting works by importing cmdlets from an existing PowerShell session.</span></span> <span data-ttu-id="5b6a0-131">您可以選擇為每個 Proxy Cmdlet 的名詞，使用您選擇的字串來加上前置詞。</span><span class="sxs-lookup"><span data-stu-id="5b6a0-131">You can optionally choose to prefix the nouns of each proxy cmdlet with a string of your choosing.</span></span> <span data-ttu-id="5b6a0-132">前置詞可讓您區別哪些命令適用於遠端系統。</span><span class="sxs-lookup"><span data-stu-id="5b6a0-132">The prefix allows you to distinguish the commands that are for the remote system.</span></span> <span data-ttu-id="5b6a0-133">會建立包含所有 Proxy 命令的暫存指令碼模組，且可在本機 PowerShell 工作階段的持續時間內匯入。</span><span class="sxs-lookup"><span data-stu-id="5b6a0-133">A temporary script module containing all the proxy commands is created and imported for the duration of your local PowerShell session.</span></span>

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> <span data-ttu-id="5b6a0-134">有些系統可能無法匯入整個 JEA 工作階段，因為預設的 JEA Cmdlet 中有條件約束。</span><span class="sxs-lookup"><span data-stu-id="5b6a0-134">Some systems may not be able to import an entire JEA session due to constraints in the default JEA cmdlets.</span></span> <span data-ttu-id="5b6a0-135">若要解決這個問題，您可以只從 JEA 工作階段匯入需要的命令，方法是明確地提供其名稱給 `-CommandName` 參數。</span><span class="sxs-lookup"><span data-stu-id="5b6a0-135">To get around this, only import the commands you need from the JEA session by explicitly providing their names to the `-CommandName` parameter.</span></span> <span data-ttu-id="5b6a0-136">未來的更新將會解決在受影響的系統上匯入整個 JEA 工作階段的問題。</span><span class="sxs-lookup"><span data-stu-id="5b6a0-136">A future update will address the issue with importing entire JEA sessions on affected systems.</span></span>

<span data-ttu-id="5b6a0-137">如果您因為預設參數的 JEA 條件約束而無法匯入 JEA 工作階段，請遵循下列步驟，從匯入的集合篩選掉預設命令。</span><span class="sxs-lookup"><span data-stu-id="5b6a0-137">If you're unable to import a JEA session because of JEA constraints on the default parameters, follow the steps below to filter out the default commands from the imported set.</span></span> <span data-ttu-id="5b6a0-138">您可以使用像是 `Select-Object` 的命令，但您會使用安裝在您電腦上的本機版本，而不是從遠端 JEA 工作階段匯入的版本。</span><span class="sxs-lookup"><span data-stu-id="5b6a0-138">You can continue use commands like `Select-Object`, but you'll just use the local version installed on your computer instead of the one imported from the remote JEA session.</span></span>

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

<span data-ttu-id="5b6a0-139">您也可以使用 [Export-PSSession](/powershell/microsoft.powershell.utility/Export-PSSession) 從隱含遠端保存代理 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5b6a0-139">You can also persist the proxied cmdlets from implicit remoting using [Export-PSSession](/powershell/microsoft.powershell.utility/Export-PSSession).</span></span>
<span data-ttu-id="5b6a0-140">如需隱含遠端的詳細資訊，請參閱 [Import-PSSession](/powershell/microsoft.powershell.utility/import-pssession) 和 [Import-Module](/powershell/microsoft.powershell.core/import-module) 的說明文件。</span><span class="sxs-lookup"><span data-stu-id="5b6a0-140">For more information about implicit remoting, see the documentation for [Import-PSSession](/powershell/microsoft.powershell.utility/import-pssession) and [Import-Module](/powershell/microsoft.powershell.core/import-module).</span></span>

## <a name="using-jea-programmatically"></a><span data-ttu-id="5b6a0-141">以程式設計方式使用 JEA</span><span class="sxs-lookup"><span data-stu-id="5b6a0-141">Using JEA programmatically</span></span>

<span data-ttu-id="5b6a0-142">JEA 也可用在自動化系統和使用者應用程式，例如公司內部的技術支援應用程式和網站。</span><span class="sxs-lookup"><span data-stu-id="5b6a0-142">JEA can also be used in automation systems and in user applications, such as in-house helpdesk apps and websites.</span></span> <span data-ttu-id="5b6a0-143">該方法和用來建置與未受限制 PowerShell 端點通訊之應用程式的方法相同。</span><span class="sxs-lookup"><span data-stu-id="5b6a0-143">The approach is the same as that for building apps that talk to unconstrained PowerShell endpoints.</span></span> <span data-ttu-id="5b6a0-144">請確定該程式設計為可與 JEA 所加諸的限制搭配使用。</span><span class="sxs-lookup"><span data-stu-id="5b6a0-144">Ensure the program is designed to work with limitation imposed by JEA.</span></span>

<span data-ttu-id="5b6a0-145">針對簡單的一次性工作，您可以使用 [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command)，在 JEA 工作階段中執行一組命令。</span><span class="sxs-lookup"><span data-stu-id="5b6a0-145">For simple, one-off tasks, you can use [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) to run commands in a JEA session.</span></span>

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

<span data-ttu-id="5b6a0-146">若要檢查哪些命令可用於當您連線到 JEA 工作階段時，請執行 `Get-Command` 並逐一查看結果，以便檢查允許的參數。</span><span class="sxs-lookup"><span data-stu-id="5b6a0-146">To check which commands are available for use when you connect to a JEA session, run `Get-Command` and iterate through the results to check for the allowed parameters.</span></span>

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

<span data-ttu-id="5b6a0-147">如果您正在建置 C# 應用程式，可以在 [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo) 物件中指定設定名稱，建立連線至 JEA 工作階段的 PowerShell 執行空間。</span><span class="sxs-lookup"><span data-stu-id="5b6a0-147">If you're building a C# app, you can create a PowerShell runspace that connects to a JEA session by specifying the configuration name in a [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo) object.</span></span>

```csharp
// using System.Management.Automation;
var computerName = "SERVER01";
var configName   = "JEAMaintenance";
// See https://docs.microsoft.com/dotnet/api/system.management.automation.pscredential
var creds        = // create a PSCredential object here

WSManConnectionInfo connectionInfo = new WSManConnectionInfo(
    false,                 // Use SSL
    computerName,          // Computer name
    5985,                  // WSMan Port
    "/wsman",              // WSMan Path
                           // Connection URI with config name
    string.Format(CultureInfo.InvariantCulture, "https://schemas.microsoft.com/powershell/{0}", configName),
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

## <a name="using-jea-with-powershell-direct"></a><span data-ttu-id="5b6a0-148">搭配使用 PowerShell Direct 和 JEA</span><span class="sxs-lookup"><span data-stu-id="5b6a0-148">Using JEA with PowerShell Direct</span></span>

<span data-ttu-id="5b6a0-149">在 Windows 10 和 Windows Server 2016 中的 Hyper-V 提供 [PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct)，這項功能允許 Hyper-V 系統管理員使用 PowerShell 管理虛擬機器，不論虛擬機器上的網路設定或遠端管理設定為何。</span><span class="sxs-lookup"><span data-stu-id="5b6a0-149">Hyper-V in Windows 10 and Windows Server 2016 offers [PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct), a feature that allows Hyper-V administrators to manage virtual machines with PowerShell regardless of the network configuration or remote management settings on the virtual machine.</span></span>

<span data-ttu-id="5b6a0-150">您可以使用 PowerShell Direct 與 JEA，來提供 Hyper-V 系統管理員對您 VM 的有限存取權。</span><span class="sxs-lookup"><span data-stu-id="5b6a0-150">You can use PowerShell Direct with JEA to give a Hyper-V administrator limited access to your VM.</span></span>
<span data-ttu-id="5b6a0-151">如果您遺失與 VM 的網路連線，並需要資料中心系統管理員來修正網路設定，這相當實用。</span><span class="sxs-lookup"><span data-stu-id="5b6a0-151">This can be useful if you lose network connectivity to your VM and need a datacenter admin to fix the network settings.</span></span>

<span data-ttu-id="5b6a0-152">不需要額外設定即可透過 PowerShell Direct 使用 JEA。</span><span class="sxs-lookup"><span data-stu-id="5b6a0-152">No additional configuration is required to use JEA over PowerShell Direct.</span></span> <span data-ttu-id="5b6a0-153">不過，虛擬機器內執行的客體作業系統必須是 Windows 10、Windows Server 2016 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="5b6a0-153">However, the guest operating system running inside the virtual machine must be Windows 10, Windows Server 2016, or higher.</span></span> <span data-ttu-id="5b6a0-154">Hyper-V 系統管理員可利用 PSRemoting Cmdlet 的 `-VMName` 或 `-VMId` 參數連線到 JEA 端點︰</span><span class="sxs-lookup"><span data-stu-id="5b6a0-154">The Hyper-V admin can connect to the JEA endpoint by using the `-VMName` or `-VMId` parameters on PSRemoting cmdlets:</span></span>

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

<span data-ttu-id="5b6a0-155">建議您建立專用的使用者帳戶，其具有管理系統以供 Hyper-V 系統管理員使用所需的最低權限。</span><span class="sxs-lookup"><span data-stu-id="5b6a0-155">It's recommended you create a dedicated user account with the minimum rights needed to manage the system for use by a Hyper-V administrator.</span></span> <span data-ttu-id="5b6a0-156">請記住，根據預設，即使無權限的使用者也可以登入 Windows 電腦，包括使用未受限制的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="5b6a0-156">Remember, even an unprivileged user can sign into a Windows machine by default, including using unconstrained PowerShell.</span></span> <span data-ttu-id="5b6a0-157">那樣會允許他們瀏覽檔案系統，並深入了解您的作業系統環境。</span><span class="sxs-lookup"><span data-stu-id="5b6a0-157">That allows them to browse the file system and learn more about your OS environment.</span></span> <span data-ttu-id="5b6a0-158">若要鎖定 Hyper-V 系統管理員並限制其只能使用 PowerShell Direct 與 JEA 來存取 VM，則您必須拒絕 Hyper-V 系統管理員 JEA 帳戶的本機登入權限。</span><span class="sxs-lookup"><span data-stu-id="5b6a0-158">To lock down a Hyper-V administrator and limit them to only access a VM using PowerShell Direct with JEA, you must deny local logon rights to the Hyper-V admin's JEA account.</span></span>
