---
ms.date: 07/10/2019
keywords: jea,powershell,安全性
title: 使用 JEA
ms.openlocfilehash: 1c424eb4a476dd0db3cc69c0e6f14c89a3c523ba
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "80500522"
---
# <a name="using-jea"></a>使用 JEA

本文描述您可以連線到並使用 JEA 端點的各種方式。

## <a name="using-jea-interactively"></a>以互動方式使用 JEA

如果您要測試 JEA 設定，或有要供使用者運用的簡單工作，可以如同一般 PowerShell 遠端工作階段一樣地使用 JEA。 針對複雜的遠端工作，建議使用[隱含遠端](#using-jea-with-implicit-remoting)。 隱含遠端處理可讓使用者與資料物件在本機運作。

若要以互動方式使用 JEA，您需要︰

- 要連線的目標電腦名稱 (可以是本機電腦)
- 在該電腦上登錄的 JEA 端點名稱
- 在該電腦上能存取 JEA 端點的電腦認證

有了此資訊，您可以使用 [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) 或 [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) Cmdlet 來啟動 JEA 工作階段。

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

如果您目前的使用者帳戶可以存取 JEA 端點，則可以省略**認證**參數。

當 PowerShell 命令提示字元變更為 `[localhost]: PS>`，您會知道現在正在與遠端 JEA 工作階段互動。 您可以執行 `Get-Command` 以檢查可用的命令。 請洽詢系統管理員以了解可用的參數，或允許的參數值是否有任何限制。

請記住，JEA 工作階段在 NoLanguage 模式中運作。 您可能會無法使用 PowerShell 的一些平常使用方式。 例如，您不能使用變數來儲存資料，或檢查從 Cmdlet 傳回的物件上屬性。 下列範例示範兩種方法，讓相同的命令在 NoLanguage 模式下運作。

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

如需使這種方法變困難的更複雜命令引動過程，請考慮使用[隱含遠端](#using-jea-with-implicit-remoting)或[建立自訂函式](role-capabilities.md#creating-custom-functions)，其包裝您需要的功能。

## <a name="using-jea-with-implicit-remoting"></a>以隱含遠端來使用 JEA

PowerShell 具有隱含遠端模型，可讓您從遠端電腦匯入 Proxy Cmdlet 並與其互動，如同它們是本機命令一樣。 如需隱含遠端的說明，請參閱 **Hey, Scripting Guy!** [部落格文章](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/)。
隱含遠端在使用 JEA 時很有用，因為可讓您能夠以完整的語言模式使用 JEA Cmdlet。 您可以使用 Tab 鍵自動完成、變數、操作物件，甚至使用本機指令碼對 JEA 端點自動執行工作。 每當您叫用 Proxy 命令時，資料會傳送至遠端電腦上的 JEA 端點並且在該處執行。

隱含遠端的運作方式是從現有 PowerShell 工作階段匯入 Cmdlet。 您可以選擇為每個 Proxy Cmdlet 的名詞，使用您選擇的字串來加上前置詞。 前置詞可讓您區別哪些命令適用於遠端系統。 會建立包含所有 Proxy 命令的暫存指令碼模組，且可在本機 PowerShell 工作階段的持續時間內匯入。

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> 有些系統可能無法匯入整個 JEA 工作階段，因為預設的 JEA Cmdlet 中有條件約束。 若要解決這個問題，您可以只從 JEA 工作階段匯入需要的命令，方法是明確地提供其名稱給 `-CommandName` 參數。 未來的更新將會解決在受影響的系統上匯入整個 JEA 工作階段的問題。

如果您因為預設參數的 JEA 條件約束而無法匯入 JEA 工作階段，請遵循下列步驟，從匯入的集合篩選掉預設命令。 您可以使用像是 `Select-Object` 的命令，但您會使用安裝在您電腦上的本機版本，而不是從遠端 JEA 工作階段匯入的版本。

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

您也可以使用 [Export-PSSession](/powershell/module/microsoft.powershell.utility/Export-PSSession) 從隱含遠端保存代理 Cmdlet。
如需隱含遠端的詳細資訊，請參閱 [Import-PSSession](/powershell/module/microsoft.powershell.utility/import-pssession) 和 [Import-Module](/powershell/module/microsoft.powershell.core/import-module) 的說明文件。

## <a name="using-jea-programmatically"></a>以程式設計方式使用 JEA

JEA 也可用在自動化系統和使用者應用程式，例如公司內部的技術支援應用程式和網站。 該方法和用來建置與未受限制 PowerShell 端點通訊之應用程式的方法相同。 請確定該程式設計為可與 JEA 所加諸的限制搭配使用。

針對簡單的一次性工作，您可以使用 [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command)，在 JEA 工作階段中執行一組命令。

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

若要檢查哪些命令可用於當您連線到 JEA 工作階段時，請執行 `Get-Command` 並逐一查看結果，以便檢查允許的參數。

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

如果您正在建置 C# 應用程式，可以在 [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo) 物件中指定設定名稱，建立連線至 JEA 工作階段的 PowerShell 執行空間。

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

## <a name="using-jea-with-powershell-direct"></a>搭配使用 PowerShell Direct 和 JEA

在 Windows 10 和 Windows Server 2016 中的 Hyper-V 提供 [PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct)，這項功能允許 Hyper-V 系統管理員使用 PowerShell 管理虛擬機器，不論虛擬機器上的網路設定或遠端管理設定為何。

您可以使用 PowerShell Direct 與 JEA，來提供 Hyper-V 系統管理員對您 VM 的有限存取權。
如果您遺失與 VM 的網路連線，並需要資料中心系統管理員來修正網路設定，這相當實用。

不需要額外設定即可透過 PowerShell Direct 使用 JEA。 不過，虛擬機器內執行的客體作業系統必須是 Windows 10、Windows Server 2016 或更新版本。 Hyper-V 系統管理員可利用 PSRemoting Cmdlet 的 `-VMName` 或 `-VMId` 參數連線到 JEA 端點︰

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

建議您建立專用的使用者帳戶，其具有管理系統以供 Hyper-V 系統管理員使用所需的最低權限。 請記住，根據預設，即使無權限的使用者也可以登入 Windows 電腦，包括使用未受限制的 PowerShell。 那樣會允許他們瀏覽檔案系統，並深入了解您的作業系統環境。 若要鎖定 Hyper-V 系統管理員並限制其只能使用 PowerShell Direct 與 JEA 來存取 VM，則您必須拒絕 Hyper-V 系統管理員 JEA 帳戶的本機登入權限。
