---
ms.date: 07/10/2019
keywords: jea,powershell,安全性
title: JEA 上的稽核和報告
ms.openlocfilehash: 2afefe83acecc1fc3643d49766120ffecc25378f
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "70017789"
---
# <a name="auditing-and-reporting-on-jea"></a>JEA 上的稽核和報告

部署 JEA 之後，您需要定期稽核 JEA 設定。 稽核有助於您評估正確的人員是否具有 JEA 端點存取權，以及他們的指派角色是否仍然適當。

## <a name="find-registered-jea-sessions-on-a-machine"></a>在電腦上尋找已註冊的 JEA 工作階段

若要檢查哪些 JEA 工作階段已在電腦上註冊，請使用 [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) Cmdlet。

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }
```

```Output
Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed,
                CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

端點的有效權限列於 **Permission** 屬性中。 這些使用者有權連線至 JEA 端點。 但是，他們能存取哪些角色和命令則由用來註冊端點之[工作階段設定檔](session-configurations.md)中的 **RoleDefinitions** 欄位決定。 展開 **RoleDefinitions** 屬性中的資料，以評估已註冊的 JEA 端點中角色對應。

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{
  Name = 'Role Capabilities'
  Expression = { $_.Value.RoleCapabilities }
}
```

## <a name="find-available-role-capabilities-on-the-machine"></a>在電腦上尋找可用的角色功能

JEA 會從儲存在 PowerShell 模組內 **RoleCapabilities** 資料夾的 `.psrc` 檔案中取得角色功能。 下列函式會尋找電腦上所有可用的角色功能。

```powershell
function Find-LocalRoleCapability {
    $results = @()

    # Find modules with a "RoleCapabilities" subfolder and add any PSRC files to the result set
    Get-Module -ListAvailable | ForEach-Object {
        $psrcpath = Join-Path -Path $_.ModuleBase -ChildPath 'RoleCapabilities'
        if (Test-Path $psrcpath) {
            $results += Get-ChildItem -Path $psrcpath -Filter *.psrc
        }
    }

    # Format the results nicely to make it easier to read
    $results | Select-Object @{ Name = 'Name'; Expression = { $_.Name.TrimEnd('.psrc') }}, @{
        Name = 'Path'; Expression = { $_.FullName }
    } | Sort-Object Name
}
```

> [!NOTE]
> 如果多個角色功能共用相同的名稱，則此函式的結果順序不一定是角色功能的選取順序。

## <a name="check-effective-rights-for-a-specific-user"></a>檢查特定使用者的有效權限

[Get-pssessioncapability](/powershell/module/microsoft.powershell.core/Get-PSSessionCapability) Cmdlet 會根據使用者的群組成員資格，列舉 JEA 端點上的所有可用命令。
`Get-PSSessionCapability` 的輸出會與指定使用者在 JEA 工作階段中執行 `Get-Command -CommandType All` 的輸出相同。

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

如果您的使用者不是會授與額外 JEA 權限之群組的永久成員，則這個 Cmdlet 可能不會反映這些額外的權限。 使用 Just-in-Time 特殊權限的存取管理系統來允許使用者暫時屬於某個安全性群組時，會發生此情況。 請仔細評估使用者與角色及功能的對應，以確保使用者僅具有成功完成工作所需的存取層級。

## <a name="powershell-event-logs"></a>PowerShell 事件記錄檔

如果您已在系統上啟用模組或指令碼區塊記錄，您可在 Windows 事件記錄檔中找到使用者在 JEA 工作階段中執行之每個命令的事件。 若要尋找這些事件，請開啟 **Microsoft-Windows-PowerShell/Operational** 事件記錄檔，然後尋找事件識別碼為 **4104** 的事件。

每個事件記錄檔項目會包含命令執行所在工作階段的相關資訊。 針對 JEA 工作階段，事件包含 **ConnectedUser** 和 **RunAsUser** 的相關資訊。 **ConnectedUser** 是建立 JEA 工作階段的實際使用者。 **RunAsUser** 用來執行命令的帳戶 JEA。

應用程式事件記錄檔會顯示正在由 **RunAsUser** 進行的變更。 因此必須啟用模組和指令碼記錄，才能將特定的命令引動過程追蹤回 **ConnectedUser**。

## <a name="application-event-logs"></a>應用程式事件記錄檔

在與外部應用程式或服務互動之 JEA 工作階段中執行的命令，可能會將事件記錄至自己的事件記錄檔。 不同於 PowerShell 記錄檔和文字記錄，其他記錄機制不會擷取 JEA 工作階段的連線使用者。 反之，這些應用程式只會記錄虛擬執行身分使用者。
若要判斷誰執行了命令，您必須參閱[工作階段文字記錄](#session-transcripts)，或相互關聯 PowerShell 事件記錄檔與應用程式事件記錄檔中顯示的時間和使用者。

WinRM 記錄檔也可協助您相互關聯應用程式事件記錄檔中的執行身分使用者與連線使用者。 **Microsoft-Windows-Windows 遠端管理/作業**記錄檔中的事件識別碼 **193** 會針對每個新的 JEA 工作階段，記錄連線使用者與執行身分使用者的安全性識別碼 (SID) 和帳戶名稱。

## <a name="session-transcripts"></a>工作階段文字記錄

如果您已設定 JEA 為每個使用者工作階段建立文字記錄，則每個使用者動作的文字副本將儲存在指定的資料夾中。

下列命令 (以系統管理員身分) 會尋找所有文字記錄目錄。

```powershell
Get-PSSessionConfiguration |
  Where-Object { $_.TranscriptDirectory -ne $null } |
    Format-Table Name, TranscriptDirectory
```

每份文字記錄開頭為工作階段的啟動時間、連線到工作階段的使用者，以及指派給他們的 JEA 身分識別等資訊。

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

文字記錄的本文包含使用者所叫用每個命令的相關資訊。 因為命令針對 PowerShell 遠端轉換的方式，使用此命令的正確語法不適用於 JEA 工作階段。 不過，您仍可以判斷已執行的有效命令。 以下是範例文字記錄程式碼片段，來自在 JEA 工作階段中執行 `Get-Service Dns` 的使用者：

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

**CommandInvocation** 行是針對使用者執行的每個命令所撰寫。 **ParameterBindings** 會記錄命令所提供的每個參數和值。 在上述範例中，您可以看到參數 **Name** 以值 **Dns** 提供給 `Get-Service` Cmdlet。

每個命令的輸出也會觸發 **CommandInvocation**，通常為 `Out-Default`。 `Out-Default` 的 **InputObject** 是由命令傳回的 PowerShell 物件。 物件的詳細資料會列印在下面幾行，密切模擬使用者會看到的情況。

## <a name="see-also"></a>另請參閱

[*PowerShell ♥ 藍色小組*安全性部落格文章](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
