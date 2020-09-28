---
title: PowerShell Core 6.1 的新功能
description: PowerShell Core 6.1 中發行的新功能與變更
ms.date: 09/13/2018
ms.openlocfilehash: 16159059285f89c2ddd85b506b0920f0aa8748ae
ms.sourcegitcommit: d757d64ea8c8af4d92596e8fbe15f2f40d48d3ac
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90846910"
---
# <a name="whats-new-in-powershell-core-61"></a>PowerShell Core 6.1 的新功能

以下是 PowerShell Core 6.1 中已引進的一些主要新功能與變更精選。

還有**許多**「乏味的項目」讓 PowerShell 變得更快且更穩定 (外加許許多多的 Bug 修正)！ 如需變更的完整清單，請參閱 [GitHub 上的變更記錄](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md)。

此外，除了下文所提到的一些名字，我們也感謝[所有社群參與者](https://github.com/PowerShell/PowerShell/graphs/contributors)協助實現這次的發行。

## <a name="net-core-21"></a>.NET Core 2.1

PowerShell Core 6.1 已移至 [5 月發行](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/)的 .NET Core 2.1，並對 PowerShell 做出許多改善，包括：

- 效能改善 (請參閱[下文](#performance-improvements))
- Alpine Linux 支援 (預覽)
- [.NET 通用工具支援](/dotnet/core/tools/global-tools) - 即將在 PowerShell 中推出
- [`Span<T>`](/dotnet/api/system.span-1?view=netcore-2.1)

## <a name="windows-compatibility-pack-for-net-core"></a>適用於 .NET Core 的 Windows 相容性套件

在 Windows 上，.NET 小組提供[適用於 .NET Core 的 Windows 相容性套件](https://blogs.msdn.microsoft.com/dotnet/2017/11/16/announcing-the-windows-compatibility-pack-for-net-core/)，此組件集將一些已移除的 API 重新新增至 Windows 上的 .NET Core。

我們已將 Windows 相容性套件新增至 PowerShell Core 6.1 版，讓任何使用這些 API 的模組或指令碼都可以依賴這些套件提供使用。

Windows 相容性組件可讓 PowerShell Core 使用**隨附於 Windows 10 2018 年 10 月更新和 Windows Server 2019 中 1900 個以上的 Cmdlet**。

## <a name="support-for-application-allow-lists"></a>支援應用程式允許清單

PowerShell Core 6.1 與 Windows PowerShell 5.1 同樣支援 [AppLocker](/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview) 和 [Device Guard](/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control) 應用程式允許清單。 應用程式允許清單可供細微控制哪些二進位檔才能搭配使用 PowerShell [受限語言模式](https://blogs.msdn.microsoft.com/powershell/2017/11/02/powershell-constrained-language-mode/)執行。

## <a name="performance-improvements"></a>效能改善

PowerShell Core 6.0 已做出一些重大的效能改善。 PowerShell Core 6.1 將持續改善特定作業的速度。

例如，`Group-Object` 已加速 66%：

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Group-Object }
```

|    計量    | Windows PowerShell 5.1 | PowerShell Core 6.0 | PowerShell Core 6.1 |
| ------------ | ---------------------- | ------------------- | ------------------- |
| 時間 (秒)   | 25.178                 | 19.653              | 6.641               |
| 加速 (%) | N/A                    | 21.9%               | 66.2%               |

同樣地，類似如下的排序案例已改善超過 15%：

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Sort-Object }
```

|    計量    | Windows PowerShell 5.1 | PowerShell Core 6.0 | PowerShell Core 6.1 |
| ------------ | ---------------------- | ------------------- | ------------------- |
| 時間 (秒)   | 12.170                 | 8.493               | 7.08                |
| 加速 (%) | N/A                    | 30.2%               | 16.6%               |

`Import-Csv` 從 Windows PowerShell 迴歸之後也已大幅加速。
下列範例針對 26,616 個資料列和 6 個資料行使用測試 CSV：

```powershell
Measure-Command {$a = Import-Csv foo.csv}
```

|    計量    | Windows PowerShell 5.1 | PowerShell Core 6.0 |  PowerShell Core 6.1   |
| ------------ | ---------------------- | ------------------- | ---------------------- |
| 時間 (秒)   | 0.441                  | 1.069               | 0.268                  |
| 加速 (%) | N/A                    | -142.4%             | 74.9% (39.2% 來自 WPS) |

最後，從 JSON 到 `PSObject` 的轉換自 Windows PowerShell 之後已加速超過 50%。
下列範例使用 ~2MB 測試 JSON 檔案：

```powershell
Measure-Command {Get-Content .\foo.json | ConvertFrom-Json}
```

|    計量    | Windows PowerShell 5.1 | PowerShell Core 6.0 |  PowerShell Core 6.1   |
| ------------ | ---------------------- | ------------------- | ---------------------- |
| 時間 (秒)   | 0.259                  | 0.577               | 0.125                  |
| 加速 (%) | N/A                    | -122.8%             | 78.3% (51.7% 來自 WPS) |

## <a name="check-system32-for-compatible-built-in-modules-on-windows"></a>查看 `system32` 中是否有符合 Windows 規範的內建模組

在 Windows 10 1809 更新和 Windows Server 2019 中，我們更新了一些內建 PowerShell 模組以將其標記為符合 PowerShell Core 規範。

當 PowerShell Core 6.1 啟動時，它會自動包含 `$windir\System32` 作為 `PSModulePath` 環境變數的一部分。 不過，如果其 `CompatiblePSEdition` 標示為與 `Core` 相容，則只會對 `Get-Module` 和 `Import-Module` 公開模組。

```powershell
Get-Module -ListAvailable
```

> [!NOTE]
> 根據所安裝的角色和功能，您可能會看到不同的可用模組。

```Output
...
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   2.0.1.0    Appx                                Core,Desk {Add-AppxPackage, Get-AppxPackage, Get-AppxPacka...
Manifest   1.0.0.0    BitLocker                           Core,Desk {Unlock-BitLocker, Suspend-BitLocker, Resume-Bit...
Manifest   1.0.0.0    DnsClient                           Core,Desk {Resolve-DnsName, Clear-DnsClientCache, Get-DnsC...
Manifest   1.0.0.0    HgsDiagnostics                      Core,Desk {New-HgsTraceTarget, Get-HgsTrace, Get-HgsTraceF...
Binary     2.0.0.0    Hyper-V                             Core,Desk {Add-VMAssignableDevice, Add-VMDvdDrive, Add-VMF...
Binary     1.1        Hyper-V                             Core,Desk {Add-VMDvdDrive, Add-VMFibreChannelHba, Add-VMHa...
Manifest   2.0.0.0    NetAdapter                          Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetEventPacketCapture               Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                             Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                              Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                              Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                         Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam                       Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetWNV                              Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   2.0.0.0    TrustedPlatformModule               Core,Desk {Get-Tpm, Initialize-Tpm, Clear-Tpm, Unblock-Tpm...
...
```

您可以使用 `-SkipEditionCheck` 切換參數來覆寫此行為以顯示所有模組。
我們也將 `PSEdition` 屬性新增至資料表輸出。

```powershell
Get-Module Net* -ListAvailable -SkipEditionCheck
```

```Output
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                        PSEdition ExportedCommands
---------- -------    ----                        --------- ----------------
Manifest   2.0.0.0    NetAdapter                  Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetConnection               Core,Desk {Get-NetConnectionProfile, Set-NetConnectionProf...
Manifest   1.0.0.0    NetDiagnostics              Desk      Get-NetView
Manifest   1.0.0.0    NetEventPacketCapture       Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                     Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                      Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                      Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                 Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam               Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetTCPIP                    Core,Desk {Get-NetIPAddress, Get-NetIPInterface, Get-NetIP...
Manifest   1.0.0.0    NetWNV                      Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   1.0.0.0    NetworkConnectivityStatus   Core,Desk {Get-DAConnectionStatus, Get-NCSIPolicyConfigura...
Manifest   1.0.0.0    NetworkSwitchManager        Core,Desk {Disable-NetworkSwitchEthernetPort, Enable-Netwo...
Manifest   1.0.0.0    NetworkTransition           Core,Desk {Add-NetIPHttpsCertBinding, Disable-NetDnsTransi...
```

如需此行為的詳細資訊，請參閱 [PowerShell RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-PSCore6-and-Windows-Modules.md)。

## <a name="markdown-cmdlets-and-rendering"></a>Markdown Cmdlet 和轉譯

Markdown 是用於建立可讀取純文字文件的一項標準，這些文件具有基本格式，可轉譯為 HTML。

我們在 6.1 版中新增了一些 Cmdlet，可讓您轉換和轉譯主控台中的 Markdown 文件，包括：

- `ConvertFrom-Markdown`
- `Get-MarkdownOption`
- `Set-MarkdownOption`
- `Show-Markdown`

例如，`Show-Markdown` 會轉譯主控台中的 Markdown 檔案：

![Show-Markdown 範例](media/What-s-New-in-PowerShell-Core-61/markdown_example.png)

如需這些 Cmdlet 運作方式的詳細資訊，請參閱[此 RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md)。

## <a name="experimental-feature-flags"></a>實驗性功能旗標

我們已啟用對[實驗性功能][]的支援。 這可讓 PowerShell 開發人員在設計完成之前，先提供新功能並取得意見反應。 我們也能藉此避免在設計演變的過程中進行重大變更。

請使用 `Get-ExperimentalFeature` 取得一份可用實驗性功能的清單。 您可以使用 `Enable-ExperimentalFeature` 和 `Disable-ExperimentalFeature` 啟用或停用這些功能。

您可以在 [PowerShell RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md) 中深入了解這項功能。

## <a name="web-cmdlet-improvements"></a>Web Cmdlet 改善

感謝 [@markekraus](https://github.com/markekraus)，下列 Web Cmdlet 已做出許多改善：[`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)
和 [`Invoke-RestMethod`](/powershell/module/microsoft.powershell.utility/invoke-restmethod)。

- [PR #6109](https://github.com/PowerShell/PowerShell/pull/6109) - `application-json` 回應的預設編碼設為 UTF-8
- [PR #6018](https://github.com/PowerShell/PowerShell/pull/6018) - `-SkipHeaderValidation` 參數可允許不符合標準的 `Content-Type` 標頭
- [PR #5972](https://github.com/PowerShell/PowerShell/pull/5972) - `Form` 參數可支援簡化的 `multipart/form-data` 支援
- [PR #6338](https://github.com/PowerShell/PowerShell/pull/6338) - 以符合規範且不區分大小寫的方式來處理關聯索引鍵
- [PR #6447](https://github.com/PowerShell/PowerShell/pull/6447) - 在 Web Cmdlet 中新增 `-Resume` 參數

## <a name="remoting-improvements"></a>遠端功能改善

### <a name="powershell-direct-for-containers-tries-to-use-powershell-core-first"></a>適用於容器的 PowerShell Direct 會先嘗試使用 PowerShell Core

[PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct) 是 PowerShell 和 Hyper-V 的功能，可讓您連線到 Hyper-V VM 或容器，而不需要網路連線或其他遠端管理服務。

過去，PowerShell Direct 使用容器上的內建 Windows PowerShell 執行個體進行連線。 現在，PowerShell 會先嘗試使用 `PATH` 環境變數上的任何可用 `pwsh.exe` 進行連線。 如果沒有 `pwsh.exe`，PowerShell Direct 會改為使用 `powershell.exe`。

### <a name="enable-psremoting-now-creates-separate-remoting-endpoints-for-preview-versions"></a>`Enable-PSRemoting` 現在會為預覽版本建立個別遠端端點

`Enable-PSRemoting` 現在會建立兩個遠端工作階段設定：

- 一個用於 PowerShell 的主要版本。 例如： `PowerShell.6` 。 在次要版本更新之間，可依賴此端點作為「全系統」的 PowerShell 6 工作階段設定
- 一個版本特定的工作階段設定，例如：`PowerShell.6.1.0`

如果您想要在相同電腦上安裝多個 PowerShell 6 版本以供存取，此行為會很有用。

此外，PowerShell 的預覽版本現在可在執行 `Enable-PSRemoting` Cmdlet 之後，取得自己的遠端工作階段設定：

```powershell
C:\WINDOWS\system32> Enable-PSRemoting
```

如果您之前尚未設定 WinRM，您的輸出可能會不同。

```Output
WinRM is already set up to receive requests on this computer.
WinRM is already set up for remote management on this computer.
```

然後，您可以看到 PowerShell 6 預覽和穩定組建以及每個特定版本的個別 PowerShell 工作階段設定。

```powershell
Get-PSSessionConfiguration
```

```Output
Name          : PowerShell.6.2-preview.1
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6-preview
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6.1.0
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
```

### <a name="userhostport-syntax-supported-for-ssh"></a>SSH 支援 `user@host:port` 語法

SSH 用戶端通常支援 `user@host:port` 格式的連接字串。 透過新增 SSH 作為 PowerShell 遠端通訊協定，我們已新增對此連接字串格式的支援：

`Enter-PSSession -HostName fooUser@ssh.contoso.com:2222`

## <a name="msi-option-to-add-explorer-shell-context-menu-on-windows"></a>在 Windows 上新增檔案總管殼層操作功能表的 MSI 選項

感謝 [@bergmeister](https://github.com/bergmeister)，現在您可以在 Windows 上啟用操作功能表。 現在，您可以從 Windows 檔案總管中的任何資料夾開啟 PowerShell 6.1 的全系統安裝：

![PowerShell 6 的殼層操作功能表](media/What-s-New-in-PowerShell-Core-61/shell_context_menu.png)

## <a name="goodies"></a>很棒的功能

### <a name="run-as-administrator-in-the-windows-shortcut-jump-list"></a>Windows 捷徑清單中的 [以系統管理員身分執行]

感謝 [@bergmeister](https://github.com/bergmeister)，PowerShell Core 捷徑清單現在包含 [以系統管理員身分執行]：

![PowerShell 6 捷徑清單中的 [以系統管理員身分執行]](media/What-s-New-in-PowerShell-Core-61/jumplist.png)

### <a name="cd---returns-to-previous-directory"></a>`cd -` 返回上一個目錄

```powershell
C:\Windows\System32> cd C:\
C:\> cd -
C:\Windows\System32>
```

或在 Linux 上：

```ShellSession
PS /etc> cd /usr/bin
PS /usr/bin> cd -
PS /etc>
```

此外，`cd` 和 `cd --` 變更為 `$HOME`。

### `Test-Connection`

感謝 [@iSazonov](https://github.com/iSazonov)，[`Test-Connection`](/powershell/module/microsoft.powershell.management/test-connection) Cmdlet 已移植到 PowerShell Core。

### <a name="update-help-as-non-admin"></a>以非系統管理員身分執行 `Update-Help`

經熱烈要求，`Update-Help` 不再需要以系統管理員身分執行。 `Update-Help` 現在預設會將說明儲存至使用者範圍的資料夾。

### <a name="new-methodsproperties-on-pscustomobject"></a>`PSCustomObject` 上的新方法/屬性

感謝 [@iSazonov](https://github.com/iSazonov)，我們已新增方法和屬性至 `PSCustomObject`。 `PSCustomObject` 現在類似其他物件包含 `Count`/`Length` 屬性。

```powershell
$PSCustomObject = [pscustomobject]@{foo = 1}

$PSCustomObject.Length
```

```Output
1
```

```powershell
$PSCustomObject.Count
```

```Output
1
```

這項工作也包含 `ForEach` 和 `Where` 方法，可讓您操作並篩選 `PSCustomObject` 項目：

```powershell
$PSCustomObject.ForEach({$_.foo + 1})
```

```Output
2
```

```powershell
$PSCustomObject.Where({$_.foo -gt 0})
```

```Output
foo
---
  1
```

### `Where-Object -Not`

感謝 @SimonWahlin，我們已將 `-Not` 參數新增至 `Where-Object`。 現在，您可以依不存在的屬性或 Null/空白屬性值來篩選管線上的物件。

例如，此命令會傳回未定義任何相依服務的所有服務：

```powershell
Get-Service | Where-Object -Not DependentServices
```

### <a name="new-modulemanifest-creates-a-bom-less-utf-8-document"></a>`New-ModuleManifest` 會建立無 BOM 的 UTF-8 文件

由於我們在 PowerShell 6.0 中移至無 BOM 的 UTF-8，我們已更新 `New-ModuleManifest` Cmdlet 建立無 BOM 的 UTF-8 文件，而不是 UTF-16 文件。

### <a name="conversions-from-psmethod-to-delegate"></a>從 PSMethod 轉換成委派

感謝 [@powercode](https://github.com/powercode)，我們現在支援從 `PSMethod` 轉換成委派。 這可讓您執行將 `PSMethod` `[M]::DoubleStrLen` 當作委派值傳入 `[M]::AggregateString` 之類的動作：

```powershell
class M {
    static [int] DoubleStrLen([string] $value) { return 2 * $value.Length }

    static [long] AggregateString([string[]] $values, [func[string, int]] $selector) {
        [long] $res = 0
        foreach($s in $values){
            $res += $selector.Invoke($s)
        }
        return $res
    }
}

[M]::AggregateString((gci).Name, [M]::DoubleStrLen)
```

如需這項變更的詳細資訊，請參閱 [PR #5287](https://github.com/PowerShell/PowerShell/pull/5287)。

### <a name="standard-deviation-in-measure-object"></a>`Measure-Object` 中的標準差

感謝 [@CloudyDino](https://github.com/CloudyDino)，我們已將 `StandardDeviation` 屬性新增至 `Measure-Object`：

```powershell
Get-Process | Measure-Object -Property CPU -AllStats
```

```Output
Count             : 308
Average           : 31.3720576298701
Sum               : 9662.59375
Maximum           : 4416.046875
Minimum           :
StandardDeviation : 264.389544720926
Property          : CPU
```

### `GetPfxCertificate -Password`

感謝 [@maybe-hello-world](https://github.com/maybe-hello-world)，`Get-PfxCertificate` 現在包含接受 `SecureString` 的 `Password` 參數。 這可讓您以非互動方式使用它：

```powershell
$certFile = '\\server\share\pwd-protected.pfx'
$certPass = Read-Host -AsSecureString -Prompt 'Enter the password for certificate: '

$certThumbPrint = (Get-PfxCertificate -FilePath $certFile -Password $certPass ).ThumbPrint
```

### <a name="removal-of-the-more-function"></a>移除 `more` 函式

在過去，PowerShell 在 Windows 上提供用來包裝 `more.com` 的函式，稱為 `more`。 該函式現在已移除。

此外，`help` 函式已變更為使用 `more.com` (在 Windows 上) 或 `$env:PAGER` 所指定系統的預設頁面巡覽區 (非 Windows 平台上)。

### <a name="cd-drivename-now-returns-users-to-the-current-working-directory-in-that-drive"></a>`cd DriveName:` 現在會讓使用者返回該磁碟機中的目前工作目錄

之前，使用 `Set-Location` 或 `cd` 返回 PSDrive 會將使用者傳送至該磁碟機的預設位置。

感謝 [@mcbobke](https://github.com/mcbobke)，使用者現在會傳送至該工作階段的上一個已知目前工作目錄。

### <a name="windows-powershell-type-accelerators"></a>Windows PowerShell 類型快速鍵

在 Windows PowerShell 中，我們會包含下列類型快速鍵，以更輕鬆地搭配其各自類型來運作：

- `[adsi]`: `System.DirectoryServices.DirectoryEntry`
- `[adsisearcher]`: `System.DirectoryServices.DirectorySearcher`
- `[wmi]`: `System.Management.ManagementObject`
- `[wmiclass]`: `System.Management.ManagementClass`
- `[wmisearcher]`: `System.Management.ManagementObjectSearcher`

這些類型快速鍵並未包含在 PowerShell 6 中，但已新增至 Windows 上執行的 PowerShell 6.1。

這些類型可方便您建構 AD 和 WMI 物件。

例如，您可以使用 LDAP 進行查詢：

```powershell
[adsi]'LDAP://CN=FooUse,OU=People,DC=contoso,DC=com'
```

下列範例會建立 Win32_OperatingSystem CIM 物件：

```powershell
[wmi]"Win32_OperatingSystem=@"
```

```Output
SystemDirectory : C:\WINDOWS\system32
Organization    : Contoso IT
BuildNumber     : 18234
RegisteredUser  : Contoso Corp.
SerialNumber    : 12345-67890-ABCDE-F0123
Version         : 10.0.18234
```

此範例會傳回 Win32_OperatingSystem 類別的 ManagementClass 物件。

```powershell
[wmiclass]"Win32_OperatingSystem"
```

```Output
   NameSpace: ROOT\cimv2

Name                                Methods              Properties
----                                -------              ----------
Win32_OperatingSystem               {Reboot, Shutdown... {BootDevice, BuildNumber, BuildType, Caption...}
```

### <a name="-lp-alias-for-all--literalpath-parameters"></a>用於所有 `-LiteralPath` 參數的 `-lp` 別名

感謝 [@kvprasoon](https://github.com/kvprasoon)，具有 `-LiteralPath` 參數的所有內建 PowerShell Cmdlet 現在有一個參數別名 `-lp`。

## <a name="breaking-changes"></a>重大變更

### <a name="msi-based-installation-paths-on-windows"></a>Windows 上的 MSI 安裝路徑

在 Windows 上，MSI 套件現在會安裝到下列路徑：

- 若是 6.x 的穩定安裝，則為 `$env:ProgramFiles\PowerShell\6\`
- 若是 6.x 的預覽安裝，則為 `$env:ProgramFiles\PowerShell\6-preview\`

這項變更會確保 PowerShell Core 可透過 Microsoft Update 來更新或接受服務。

如需詳細資訊，請參閱 [PowerShell RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md)。

### <a name="telemetry-can-only-be-disabled-with-an-environment-variable"></a>遙測只能透過環境變數停用

PowerShell Core 會在啟動時將基本遙測資料傳送給 Microsoft。 該資料包括作業系統名稱、作業系統版本和 PowerShell 版本。 這項資料可讓我們更加了解使用 PowerShell 的環境，並讓我們排列新功能和修正的優先順序。

若要退出此遙測，請將環境變數 `POWERSHELL_TELEMETRY_OPTOUT` 設定為 `true`、`yes` 或 `1`。 我們不再支援透過刪除 `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` 檔案來停用遙測。

### <a name="disallowed-basic-auth-over-http-in-powershell-remoting-on-unix-platforms"></a>UNIX 平台上的 PowerShell 遠端功能不允許透過 HTTP 進行基本驗證

為了避免使用未加密的流量，UNIX 平台上的 PowerShell 遠端功能現在需要使用 NTLM/交涉或 HTTPS。

如需這些變更的詳細資訊，請參閱[問題 #6779](https://github.com/PowerShell/PowerShell/issues/6779)。

### <a name="removed-visualbasic-as-a-supported-language-in-add-type"></a>已將 `VisualBasic` 從 Add-Type 支援的語言中移除

在過去，您可以使用 `Add-Type` Cmdlet 編譯 Visual Basic 程式碼。 Visual Basic 很少用於 `Add-Type`。 我們已移除這項功能來縮減 PowerShell 的大小。

### <a name="cleaned-up-uses-of-commandtypesworkflow-and-workflowinfocleaned"></a>已清除 `CommandTypes.Workflow` 和 `WorkflowInfoCleaned` 的使用

如需這些變更的詳細資訊，請參閱 [PR #6708](https://github.com/PowerShell/PowerShell/pull/6708)。

### <a name="group-object-now-sorts-the-groups"></a>Group-Object 現在會對群組進行排序

作為效能改進的一部分，`Group-Object` 現在會傳回已排序的群組清單。
雖然您不應該依賴順序，但如果您想要第一個群組，則可能會被此變更中斷。 我們認為這種效能改進值得改變，因為依賴於先前行為的影響很小。

如需此變更的詳細資訊，請參閱 [問題 #7409](https://github.com/PowerShell/PowerShell/issues/7409) \(英文\)。

<!-- URL references -->
[實驗性功能]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
