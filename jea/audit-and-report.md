---
ms.date: 06/12/2017
keywords: jea,powershell,安全性
title: JEA 上的稽核和報告
ms.openlocfilehash: e68206cd6fe94c51507f42ae2c3e6702f6fd4e0f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2018
---
# <a name="auditing-and-reporting-on-jea"></a>JEA 上的稽核和報告

> 適用對象：Windows PowerShell 5.0

部署 JEA 之後，您會想要定期稽核 JEA 設定。
這有助於您評估正確的人員是否具有 JEA 端點的存取權，以及他們的指派角色是否仍然適當。

本主題說明您可以稽核 JEA 端點的各種方式。

## <a name="find-registered-jea-sessions-on-a-machine"></a>在電腦上尋找已註冊的 JEA 工作階段

若要檢查哪些 JEA 工作階段已在電腦上註冊，請使用 [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) Cmdlet。

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
PS C:\> Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }


Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed, CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

端點的有效權限詳列於 "Permission" 屬性。
這些使用者有權連接到 JEA 端點，但他們能存取哪些角色 (乃至於命令) 則由用來註冊端點的[工作階段設定檔](session-configurations.md)中的 "RoleDefinitions" 欄位決定。

您可以展開 "RoleDefinitions" 屬性中的資料來評估已註冊的 JEA 端點中的角色對應。

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{ Name = 'Role Capabilities'; Expression = { $_.Value.RoleCapabilities } }
```

## <a name="find-available-role-capabilities-on-the-machine"></a>在電腦上尋找可用的角色功能

角色功能檔案將只會在它們儲存於有效 PowerShell 模組內的 "RoleCapabilities" 資料夾時才會被 JEA 使用。
您可以搜尋可用模組清單，以在電腦上尋找所有可用的角色功能。

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
    $results | Select-Object @{ Name = 'Name'; Expression = { $_.Name.TrimEnd('.psrc') }}, @{ Name = 'Path'; Expression = { $_.FullName }} | Sort-Object Name
}
```

> [!NOTE]
> 如果多個角色功能共用相同的名稱，則此函式的結果順序不一定是角色功能的選取順序。

## <a name="check-effective-rights-for-a-specific-user"></a>檢查特定使用者的有效權限

一旦您設定好 JEA 端點，便可以檢查哪些命令可供特定使用者在 JEA 工作階段中使用。
您可以使用 [Get-PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) 列舉所有適用於使用者的命令，如果他們要使用其目前群組成員資格來啟動 JEA 工作階段。
`Get-PSSessionCapability` 的輸出會與指定使用者在 JEA 工作階段中執行 `Get-Command -CommandType All` 的輸出相同。

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

如果您的使用者不是會授與額外 JEA 權限之群組的永久成員，這個 Cmdlet 可能不會反映這些額外的權限。
使用 Just-in-Time 特殊權限的存取管理系統來允許使用者暫時屬於某個安全性群組時，通常會是如此。
請務必仔細評估使用者與角色的對應，以及每個角色的內容，以確保使用者只能夠存取成功執行其工作所需的最少命令。

## <a name="powershell-event-logs"></a>PowerShell 事件記錄檔

如果您已在系統上啟用模組和/或指令碼區塊記錄，將可在 Windows 事件記錄檔中，找到使用者在其 JEA 工作階段中執行之每個命令的事件。
若要尋找這些事件，請開啟 Windows 事件檢視器、瀏覽至 [Microsoft-Windows-PowerShell/Operational] 事件記錄檔，然後尋找事件識別碼為 **4104** 的事件。

每個事件記錄檔項目會包含命令執行所在工作階段的相關資訊。
對於 JEA 工作階段，這包含 **ConnectedUser** 的重要資訊，它是建立 JEA 工作階段的實際使用者，也包含 **RunAsUser** 的重要資訊，這會識別 JEA 用來執行命令的帳戶。
應用程式事件記錄檔會顯示 RunAsUser 正在進行的變更，因此啟用文字記錄或模組/指令碼記錄十分重要，如此才能從特定命令引動過程回溯到使用者。

## <a name="application-event-logs"></a>應用程式事件記錄檔

當您在與外部應用程式或服務互動的 JEA 工作階段中執行命令時，這些應用程式可能會將事件記錄到自己的事件記錄檔。
不同於 PowerShell 記錄檔和文字記錄，其他記錄機制不會擷取 JEA 工作階段的連線使用者，而只會記錄虛擬執行身分使用者或群組受管理的服務帳戶。
若要判斷誰執行命令，您必須參考[工作階段文字記錄](#session-transcripts)，或相互關聯 PowerShell 事件記錄檔與應用程式事件記錄檔中顯示的時間和使用者。

WinRM 記錄檔也可協助您相互關聯應用程式事件記錄檔中的執行身分使用者與連線使用者。
**Microsoft-Windows-Windows 遠端管理/作業**記錄檔中的事件識別碼 **193** 會記錄每次建立 JEA 工作階段時，連線使用者與執行身分使用者的安全性識別碼 (SID) 和帳戶名稱。

## <a name="session-transcripts"></a>工作階段文字記錄

如果您已設定 JEA 為每個使用者工作階段建立文字記錄，每個使用者動作的文字副本將儲存在指定的資料夾。

若要尋找所有文字記錄目錄，請以系統管理員身分在設定了 JEA 的電腦上執行下列命令：

```powershell
Get-PSSessionConfiguration | Where-Object { $_.TranscriptDirectory -ne $null } | Format-Table Name, TranscriptDirectory
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

在文字記錄的本文中，會記錄使用者叫用之每個命令的相關資訊。
因為針對 PowerShell 遠端轉換命令的方式，使用者所執行命令的正確語法無法在 JEA 工作階段中取得，但是您仍可以判斷所執行的有效命令。
以下是範例文字記錄程式碼片段，來自在 JEA 工作階段中執行 `Get-Service Dns` 的使用者：

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

對於使用者執行的每個命令，會寫入一列 "CommandInvocation"，描述使用者叫用的 Cmdlet 或函式。
ParameterBindings 接在每個 CommandInvocation 之後，告訴您與命令一起提供的每個參數和值。
在上述範例中，您可以看到針對 "Get-Service" Cmdlet 提供 "Name" 參數 "Dns" 值。

每個命令的輸出也會觸發 CommandInvocation，通常為 Out-Default。
Out-Default 的 InputObject 是由命令傳回的 PowerShell 物件。
物件的詳細資料會列印在下面幾行，密切模擬使用者會看到的情況。

## <a name="see-also"></a>另請參閱

- [在 JEA 工作階段中稽核使用者動作](audit-and-report.md)
- [*PowerShell ♥ 藍色小組*安全性部落格文章](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)