---
title: PowerShell 7 模組相容性
ms.date: 02/03/2020
description: 本文列出 PowerShell 7 的狀態，包含針對其他 Microsoft 產品所發佈的 Powershell 模組。
ms.openlocfilehash: 718ba0f502a23bc2c2a9268d65d3b8129de0af49
ms.sourcegitcommit: 7f712e12ec5b3f3f3e695da804b050ea0ce58b3a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94661370"
---
# <a name="powershell-7-module-compatibility"></a>PowerShell 7 模組相容性

此文章包含 Microsoft 所發行的 PowerShell 模組清單。 這些模組能針對各種 Microsoft 產品與服務提供管理及支援。 這些模組已更新為可透過原生方式搭配 PowerShell 7 運作，或是已通過與 PowerShell 7 的相容性測試。 隨著我們完成更多模組的識別及測試，此清單也會更新其中的資訊。

如果您針對特定模組有可分享的資訊或問題，請在 [WindowsCompatibility 存放庫](https://github.com/PowerShell/WindowsCompatibility) \(英文\) 中提出問題。

## <a name="windows-management-modules"></a>Windows 管理模組

根據 Windows 版本，以及模組針對該版本之封裝方式的不同，Windows 管理模組會具有不同的安裝方式。

在 Windows Server 上，請以系統管理員身分搭配 [Install-WindowsFeature](/powershell/module/servermanager/install-windowsfeature) Cmdlet 使用功能名稱。 例如：

```powershell
Install-WindowsFeature -Name ActiveDirectory
```

在 Windows 10 上，Windows 管理模組是以 [Windows 選用功能]  或 [Windows 功能]  的形式提供。 下列命令必須使用 [以系統管理員身分執行]  從提高權限的工作階段執行。

- 針對 Windows 選用功能

  若要取得 [選用功能] 的清單，請執行下列命令：

  ```powershell
  Get-WindowsOptionalFeature -Online
  ```

  若要安裝功能：

  ```powershell
  Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V-Management-PowerShell
  ```

  如需詳細資訊，請參閱：

  - [Get-WindowsOptionalFeature](/powershell/module/dism/get-windowsoptionalfeature)
  - [Enable-WindowsOptionalFeature](/powershell/module/dism/enable-windowsoptionalfeature)

- 針對 Windows 功能

  若要取得 [Windows 功能] 的清單，請執行下列命令：

  ```powershell
  Get-WindowsCapability -online
  ```

  請注意，功能套件的名稱會以 `~~~~0.0.1.0` 作為結尾。 您必須使用完整名稱來安裝功能：

  ```powershell
  Add-WindowsCapability -Online -Name Rsat.ServerManager.Tools~~~~0.0.1.0
  ```

  如需詳細資訊，請參閱：

  - [Get-WindowsCapability](/powershell/module/dism/get-windowscapability)
  - [Add-WindowsCapability](/powershell/module/dism/add-windowscapability)

### <a name="module-list"></a>模組清單

| 模組名稱                        | 狀態                               | 支援的 OS                       |
| ---------------------------------- | ------------------------------------ | ---------------------------------- |
| ActiveDirectory                    | 原生相容                  | 具有 RSAT-AD-PowerShell 的 Windows Server 1809+<br>具有 Rsat.ActiveDirectory.DS-LDS.Tools 的 Windows 10 1809+ |
| ADDSDeployment                     | 搭配相容性階層作業       |  Windows Server 2019 1809+         |
| ADFS                               | 未搭配相容性層進行測試    |                                    |
| AppBackgroundTask                  | 原生相容                  | Windows 10 1903+                   |
| AppLocker                          | 未搭配相容性層進行測試    |                                    |
| AppvClient                         | 未搭配相容性層進行測試    |                                    |
| Appx                               | 原生相容**                | Windows Server 1809+<br>Windows 10 1809+<br>**必須搭配 PowerShell 7.1 使用相容性層 |
| AssignedAccess                     | 原生相容                  | Windows 10 1809+                   |
| BestPractices                      | 不支援相容性階層 |                                    |
| BitLocker                          | 原生相容                  | 具有 BitLocker 的 Windows Server 1809+<br>Windows 10 1809+ |
| BitsTransfer                       | 原生相容                  | Windows Server 20H1<br>Windows 10 20H1 |
| BootEventCollector                 | 未搭配相容性層進行測試    |                                        |
| BranchCache                        | 原生相容                  | Windows Server 1809+<br>Windows 10 1809+ |
| CimCmdlets                         | 原生相容                  | 內建於 PowerShell 7 |
| ClusterAwareUpdating               | 未搭配相容性層進行測試    |                         |
| ConfigCI                           | 未搭配相容性層進行測試    |                         |
| Defender                           | 原生相容                  | Windows Server 1809+<br>Windows 10 1809+  |
| DeliveryOptimization               | 原生相容                  | Windows Server 1903+<br>Windows 10 1903+  |
| DFSN                               | 原生相容                  | 具有 FS-DFS-Namespace 的 Windows Server 1809+<br>具有 Rsat.FailoverCluster.Management.Tools 的 Windows 10 1809+ |
| DFSR                               | 未搭配相容性層進行測試    |                                   |
| DhcpServer                         | 未搭配相容性層進行測試    |                                   |
| DirectAccessClientComponents       | 原生相容                  | Windows Server 1809+<br>Windows 10 1809+  |
| Dism                               | 原生相容                  | Windows Server 1903+<br>Windows 10 1903+  |
| DnsClient                          | 原生相容                  | Windows Server 1809+<br>Windows 10 1809+  |
| DnsServer                          | 原生相容                  | 具有 DNS 或 RSAT-DNS-Server 的 Windows Server 1809+<br>具有 Rsat.Dns.Tools 的 Windows 10 1809+ |
| EventTracingManagement             | 原生相容                  | Windows Server 1809+<br>Windows 10 1809+  |
| FailoverClusters                   | 未搭配相容性層進行測試    |                                  |
| FailoverClusterSet                 | 未搭配相容性層進行測試    |                                  |
| FileServerResourceManager          | 原生相容                  | 具有 FS-Resource-Manager 的 Windows Server 1809+ |
| GroupPolicy                        | 未搭配相容性層進行測試    |                                               |
| HgsClient                          | 原生相容                  | 具有 Hyper-V 或 RSAT-Shielded-VM-Tools 的 Windows Server 1903+<br>具有 Rsat.Shielded.VM.Tools 的 Windows 10 1903+ |
| HgsDiagnostics                     | 原生相容                  | 具有 Hyper-V 或 RSAT-Shielded-VM-Tools 的 Windows Server 1809+<br>具有 Rsat.Shielded.VM.Tools 的 Windows 10 1809+ |
| Hyper-V                            | 原生相容                  | 具有 Hyper-V-PowerShell 的 Windows Server 1809+<br>具有 Microsoft-Hyper-V-Management-PowerShell 的 Windows 10 1809+ |
| IISAdministration                  | 未搭配相容性層進行測試    |                                               |
| International                      | 原生相容                  | Windows Server 1903+<br>Windows 10 1903+      |
| IpamServer                         | 未搭配相容性層進行測試    |                                               |
| iSCSI                              | 未搭配相容性層進行測試    |                                               |
| IscsiTarget                        | 未搭配相容性層進行測試    |                                               |
| ISE                                | 未搭配相容性層進行測試    |                                               |
| Kds                                | 原生相容                  | Windows Server 20H1<br>Windows 10 20H1        |
| Microsoft.PowerShell.Archive       | 原生相容                  | 內建於 PowerShell 7                       |
| Microsoft.PowerShell.Diagnostics   | 原生相容                  | 內建於 PowerShell 7                       |
| Microsoft.PowerShell.Host          | 原生相容                  | 內建於 PowerShell 7                       |
| Microsoft.PowerShell.LocalAccounts | 原生相容                  | Windows Server 1809+<br>Windows 10 1809+      |
| Microsoft.PowerShell.Management    | 原生相容                  | 內建於 PowerShell 7                       |
| Microsoft.PowerShell.ODataUtils    | 未搭配相容性層進行測試    |                                               |
| Microsoft.PowerShell.Security      | 原生相容                  | 內建於 PowerShell 7                       |
| Microsoft.PowerShell.Utility       | 原生相容                  | 內建於 PowerShell 7                       |
| Microsoft.WSMan.Management         | 原生相容                  | 內建於 PowerShell 7                       |
| MMAgent                            | 原生相容                  | Windows Server 1809+<br>Windows 10 1809+      |
| MPIO                               | 原生相容                  | 具有 Multipath-IO 的 Windows Server 1809+        |
| MsDtc                              | 未搭配相容性層進行測試    |                                               |
| NetAdapter                         | 原生相容                  | Windows Server 1809+<br>Windows 10 1809+      |
| NetConnection                      | 原生相容                  | Windows Server 1809+<br>Windows 10 1809+      |
| NetEventPacketCapture              | 原生相容                  | Windows Server 1809+<br>Windows 10 1809+      |
| NetLbfo                            | 原生相容                  | Windows Server 1809+<br>Windows 10 1809+      |
| NetLldpAgent                       | 未搭配相容性層進行測試    |                                               |
| NetNat                             | 原生相容                  | Windows Server 1809+<br>Windows 10 1809+      |
| NetQos                             | 原生相容                  | Windows Server 1809+<br>Windows 10 1809+      |
| NetSecurity                        | 原生相容                  | Windows Server 1809+<br>Windows 10 1809+      |
| NetSwitchTeam                      | 原生相容                  | Windows Server 1809+<br>Windows 10 1809+      |
| NetTCPIP                           | 原生相容                  | Windows Server 1809+<br>Windows 10 1809+      |
| NetWNV                             | 未搭配相容性層進行測試    |                                               |
| NetworkConnectivityStatus          | 原生相容                  | Windows Server 1809+<br>Windows 10 1809+      |
| NetworkController                  | 未搭配相容性層進行測試    |                                               |
| NetworkControllerDiagnostics       | 未搭配相容性層進行測試    |                                               |
| NetworkLoadBalancingClusters       | 未搭配相容性層進行測試    |                                               |
| NetworkSwitchManager               | 原生相容                  | Windows Server 1809+<br>Windows 10 1809+      |
| NetworkTransition                  | 原生相容                  | Windows Server 1809+<br>Windows 10 1809+      |
| NFS                                | 原生相容                  | Windows Server 1809+<br>具有 Rsat.ServerManager.Tools 的 Windows 10 1809+ |
| PackageManagement                  | 原生相容                  | 內建於 PowerShell 7                       |
| PcsvDevice                         | 原生相容                  | Windows Server 1809+<br>Windows 10 1809+      |
| PersistentMemory                   | 未搭配相容性層進行測試    |                                               |
| PKI                                | 未搭配相容性層進行測試    |                                               |
| PnpDevice                          | 原生相容                  | Windows Server 1809+<br>Windows 10 1809+      |
| PowerShellGet                      | 原生相容                  | 內建於 PowerShell 7                       |
| PrintManagement                    | 原生相容                  | 具有 Print-Services 的 Windows Server 1903+<br>Windows 10 1903+  |
| ProcessMitigations                 | 原生相容                  | Windows Server 1903+<br>Windows 10 1903+      |
| 佈建                       | 未搭配相容性層進行測試    |                                               |
| PSDesiredStateConfiguration        | 部分                            | 內建於 PowerShell 7                       |
| PSDiagnostics                      | 原生相容                  | 內建於 PowerShell 7                       |
| PSScheduledJob                     | 不支援相容性階層 | 內建於 PowerShell 5.1                     |
| PSWorkflow                         | 未搭配相容性層進行測試    |                                               |
| PSWorkflowUtility                  | 未搭配相容性層進行測試    |                                               |
| RemoteAccess                       | 未搭配相容性層進行測試    |                                               |
| RemoteDesktop                      | 未搭配相容性層進行測試    |                                               |
| ScheduledTasks                     | 原生相容                  | Windows Server 1809+<br>Windows 10 1809+      |
| SecureBoot                         | 原生相容                  | Windows Server 1809+<br>Windows 10 1809+      |
| ServerCore                         | 未搭配相容性層進行測試    |                                               |
| ServerManager                      | 原生相容                  | Windows Server 1809+<br>具有 Rsat.ServerManager.Tools 的 Windows 10 1809+<br>_請參閱下列附註_ |
| ServerManagerTasks                 | 未搭配相容性層進行測試    |                                               |
| ShieldedVMDataFile                 | 原生相容                  | 具有 RSAT-Shielded-VM-Tools 的 Windows Server 1903+<br>具有 Rsat.Shielded.VM.Tools 的 Windows 10 1903+ |
| ShieldedVMProvisioning             | 原生相容                  | 具有 HostGuardian 的 Windows Server 1809+<br>具有 HostGuardian 的 Windows 10 1809+  |
| ShieldedVMTemplate                 | 原生相容                  | 具有 RSAT-Shielded-VM-Tools 的 Windows Server 1809+<br>具有 Rsat.Shielded.VM.Tools 的 Windows 10 1809+ |
| SmbShare                           | 原生相容                  | Windows Server 1809+<br>Windows 10 1809+      |
| SmbWitness                         | 原生相容                  | Windows Server 1809+<br>Windows 10 1809+      |
| SMISConfig                         | 原生相容                  | 具有 WindowsStorageManagementService 的 Windows Server 1903+ |
| SMS                                | 未搭配相容性層進行測試    |                                               |
| SoftwareInventoryLogging           | 原生相容                  | Windows Server 1809+                          |
| StartLayout                        | 原生相容                  | 具有桌面體驗的 Windows Server 1809+<br>Windows 10 1809+ |
| 儲存體                            | 原生相容                  | Windows Server 1809+<br>Windows 10 1809+      |
| StorageBusCache                    | 未搭配相容性層進行測試    |                                               |
| StorageMigrationService            | 未搭配相容性層進行測試    |                                               |
| StorageQOS                         | 原生相容                  | 具有 RSAT-Clustering-PowerShell 的 Windows Server 1809+<br>具有 Rsat.FailoverCluster.Management.Tools 的 Windows 10 1809+ |
| StorageReplica                     | 未搭配相容性層進行測試    |                                               |
| SyncShare                          | 原生相容                  | 具有 FS-SyncShareService 的 Windows Server 1809+ |
| SystemInsights                     | 未搭配相容性層進行測試    |                                               |
| TLS                                | 未搭配相容性層進行測試    |                                               |
| TroubleshootingPack                | 原生相容                  | Windows 10 1903+                              |
| TrustedPlatformModule              | 原生相容                  | Windows Server 1809+<br>Windows 10 1809+      |
| UEV                                | 原生相容                  | Windows Server ??具有桌面體驗之伺服器的未來版本??<br>Windows 10 1903+ |
| UpdateServices                     | 不支援相容性階層 |                                               |
| VpnClient                          | 原生相容                  | Windows Server 1809+<br>Windows 10 1809+      |
| Wdac                               | 原生相容                  | Windows Server 1809+<br>Windows 10 1809+      |
| WebAdministration                  | 未搭配相容性層進行測試    |                                               |
| WHEA                               | 原生相容                  | Windows Server 1903+<br>Windows 10 1903+      |
| WindowsDeveloperLicense            | 原生相容                  | 具有桌面體驗的 Windows Server 1809+<br>Windows 10 1809+ |
| WindowsErrorReporting              | 原生相容                  | Windows Server 1809+<br>Windows 10 1809+      |
| WindowsSearch                      | 原生相容                  | Windows 10 1903+                              |
| WindowsServerBackup                | 原生相容                  | 具有 Windows-Server-Backup 的 Windows Server 19H2 |
| WindowsUpdate                      | 原生相容                  | Windows Server 1809+<br>Windows 10 1809+       |
| WindowsUpdateProvider              | 原生相容                  | Windows Server 1809+<br>Windows 10 1809+       |

## <a name="notes"></a>注意

### <a name="servermanager-module"></a>ServerManager 模組

在 PowerShell 7 中，此模組在格式化輸出時會發生些微相容性問題。 例如，`Get-WindowsFeature` Cmdlet 會傳回包含所有屬性的適當物件，但預設的顯示格式設定會讓某些屬性變成空白。 您可使用 `Select-Object` 或直接成員存取，在物件屬性中取得實際的值。

