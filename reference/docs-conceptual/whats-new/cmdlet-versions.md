---
ms.date: 02/03/2020
keywords: powershell, core
title: 模組與 Cmdlet 的發行歷程記錄
description: 本文列出內含於各種 PowerShell 版本的模組與 Cmdlet。
ms.openlocfilehash: 43ea0cde106e9f0aafe9c18726589f931724b35f
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2020
ms.locfileid: "94342853"
---
# <a name="release-history-of-modules-and-cmdlets"></a>模組與 Cmdlet 的發行歷程記錄

本文列出內含於各種 PowerShell 版本的模組與 Cmdlet。 這是在版本資訊中找到的資訊摘要。 您可以在版本資訊中找到更多詳細資訊：

- [PowerShell 7.0 的新功能](what-s-new-in-powershell-70.md)
- [PowerShell 6.2 的新功能](what-s-new-in-powershell-core-62.md)
- [PowerShell 6.1 的新功能](what-s-new-in-powershell-core-61.md)
- [PowerShell 6.0 的新功能](what-s-new-in-powershell-core-60.md)
- [PowerShell 6.0 中的中斷性變更](breaking-changes-ps6.md)
- [PowerShell 6.0 中的已知問題](known-issues-ps6.md)

這是正在處理的工作。 請協助我們將此資訊維持在最新狀態。

## <a name="module-release-history"></a>模組版本歷程記錄

|         模組名稱/PS 版本          |   5.1   |   6.x   |   7.0   |   7.1   |     附註     |
| ----------------------------------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| CimCmdlets                                | &check; | &check; | &check; | &check; | 僅限 Windows |
| ISE (於 2.0 中引進)                   | &check; |         |         |         | 僅限 Windows |
| Microsoft.PowerShell.Archive              | &check; | &check; | &check; | &check; |              |
| Microsoft.PowerShell.Core                 | &check; | &check; | &check; | &check; |              |
| Microsoft.PowerShell.Diagnostics          | &check; | &check; | &check; | &check; | 僅限 Windows |
| Microsoft.PowerShell.Host                 | &check; | &check; | &check; | &check; |              |
| Microsoft.PowerShell.LocalAccounts        | &check; |         |         |         | 僅限 Windows |
| Microsoft.PowerShell.Management           | &check; | &check; | &check; | &check; |              |
| Microsoft.PowerShell.ODataUtils           | &check; |         |         |         | 僅限 Windows |
| Microsoft.PowerShell.Operation.Validation | &check; |         |         |         | 僅限 Windows |
| Microsoft.PowerShell.Security             | &check; | &check; | &check; | &check; |              |
| Microsoft.PowerShell.Utility              | &check; | &check; | &check; | &check; |              |
| Microsoft.WsMan.Management                | &check; | &check; | &check; | &check; | 僅限 Windows |
| PackageManagement                         | &check; | &check; | &check; | &check; |              |
| PowershellGet                             | &check; | &check; | &check; | &check; |              |
| PSDesiredStateConfiguration               | &check; | &check; | &check; | &check; |              |
| PSDiagnostics                             | &check; | &check; | &check; | &check; | 僅限 Windows |
| PSReadline 1.x                            | &check; |         |         |         | 僅限 Windows |
| PSReadline 2.x                            |         | &check; | &check; | &check; |              |
| PSScheduledJob                            | &check; |         |         |         | 僅限 Windows |
| PSWorkflow                                | &check; |         |         |         | 僅限 Windows |
| PSWorkflowUtility                         | &check; |         |         |         | 僅限 Windows |
| ThreadJob                                 |         | &check; | &check; | &check; | 可以安裝在 PowerShell 5.1 中 |

## <a name="cmdlet-release-history"></a>Cmdlet 版本歷程記錄

### <a name="cimcmdlets"></a>CimCmdlets

|         Cmdlet 名稱         |   5.1   |   6.x   |   7.0   |   7.1   |     附註     |
| --------------------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| Export-BinaryMiLog          | &check; | &check; | &check; | &check; | 僅限 Windows |
| Get-CimAssociatedInstance   | &check; | &check; | &check; | &check; | 僅限 Windows |
| Get-CimClass                | &check; | &check; | &check; | &check; | 僅限 Windows |
| Get-CimInstance             | &check; | &check; | &check; | &check; | 僅限 Windows |
| Get-CimSession              | &check; | &check; | &check; | &check; | 僅限 Windows |
| Import-BinaryMiLog          | &check; | &check; | &check; | &check; | 僅限 Windows |
| Invoke-CimMethod            | &check; | &check; | &check; | &check; | 僅限 Windows |
| New-CimInstance             | &check; | &check; | &check; | &check; | 僅限 Windows |
| New-CimSession              | &check; | &check; | &check; | &check; | 僅限 Windows |
| New-CimSessionOption        | &check; | &check; | &check; | &check; | 僅限 Windows |
| Register-CimIndicationEvent | &check; | &check; | &check; | &check; | 僅限 Windows |
| Remove-CimInstance          | &check; | &check; | &check; | &check; | 僅限 Windows |
| Remove-CimSession           | &check; | &check; | &check; | &check; | 僅限 Windows |
| Set-CimInstance             | &check; | &check; | &check; | &check; | 僅限 Windows |

### <a name="ise-introduced-in-20"></a>ISE (於 2.0 中引進)

|    Cmdlet 名稱    |   5.1   | 6.x  |  7.0  |  7.1  |     附註     |
| ----------------- | :-----: | :--- | :---: | :---: | ------------ |
| Get-IseSnippet    | &check; |      |       |       | 僅限 Windows |
| Import-IseSnippet | &check; |      |       |       | 僅限 Windows |
| New-IseSnippet    | &check; |      |       |       | 僅限 Windows |

### <a name="microsoftpowershellarchive"></a>Microsoft.PowerShell.Archive

|   Cmdlet 名稱    |   5.1   |   6.x   |   7.0   |   7.1   | 附註 |
| ---------------- | :-----: | :-----: | :-----: | :-----: | ---- |
| Compress-Archive | &check; | &check; | &check; | &check; |      |
| Expand-Archive   | &check; | &check; | &check; | &check; |      |

### <a name="microsoftpowershellcore"></a>Microsoft.PowerShell.Core

|            Cmdlet 名稱            |   5.1   |   6.x   |   7.0   |   7.1   |            附註            |
| --------------------------------- | :-----: | :-----: | :-----: | :-----: | -------------------------- |
| Add-History                       | &check; | &check; | &check; | &check; |                            |
| Add-PSSnapin                      | &check; |         |         |         | 僅限 Windows               |
| Clear-History                     | &check; | &check; | &check; | &check; |                            |
| Clear-Host                        | &check; | &check; | &check; | &check; |                            |
| Connect-PSSession                 | &check; | &check; | &check; | &check; | 僅限 Windows               |
| Debug-Job                         | &check; | &check; | &check; | &check; |                            |
| Disable-ExperimentalFeature       |         |   6.2   | &check; | &check; |                            |
| Disable-PSRemoting                | &check; | &check; | &check; | &check; | 僅限 Windows               |
| Disable-PSSessionConfiguration    | &check; | &check; | &check; | &check; | 僅限 Windows               |
| Disconnect-PSSession              | &check; | &check; | &check; | &check; | 僅限 Windows               |
| Enable-ExperimentalFeature        |         |   6.2   | &check; | &check; |                            |
| Enable-PSRemoting                 | &check; | &check; | &check; | &check; | 僅限 Windows               |
| Enable-PSSessionConfiguration     | &check; | &check; | &check; | &check; | 僅限 Windows               |
| Enter-PSHostProcess               | &check; | &check; | &check; | &check; | 已在 6.2 中加入新增 Linux 支援 |
| Enter-PSSession                   | &check; | &check; | &check; | &check; |                            |
| Exit-PSHostProcess                | &check; | &check; | &check; | &check; | 已在 6.2 中加入新增 Linux 支援 |
| Exit-PSSession                    | &check; | &check; | &check; | &check; |                            |
| Export-Console                    | &check; |         |         |         | 僅限 Windows               |
| Export-ModuleMember               | &check; | &check; | &check; | &check; |                            |
| ForEach-Object                    | &check; | &check; | &check; | &check; |                            |
| Get-Command                       | &check; | &check; | &check; | &check; |                            |
| Get-ExperimentalFeature           |         |   6.2   | &check; | &check; |                            |
| Get-Help                          | &check; | &check; | &check; | &check; |                            |
| Get-History                       | &check; | &check; | &check; | &check; |                            |
| Get-Job                           | &check; | &check; | &check; | &check; |                            |
| Get-Module                        | &check; | &check; | &check; | &check; |                            |
| Get-PSHostProcessInfo             | &check; | &check; | &check; | &check; | 已在 6.2 中加入新增 Linux 支援 |
| Get-PSSession                     | &check; | &check; | &check; | &check; |                            |
| Get-PSSessionCapability           | &check; | &check; | &check; | &check; |                            |
| Get-PSSessionConfiguration        | &check; | &check; | &check; | &check; |                            |
| Get-PSSnapin                      | &check; |         |         |         | 僅限 Windows               |
| Get-Verb                          | &check; |         |         |         | 已移至 Microsoft.PowerShell.Utility 6.0+ |
| Import-Module                     | &check; | &check; | &check; | &check; |                            |
| Invoke-Command                    | &check; | &check; | &check; | &check; |                            |
| Invoke-History                    | &check; | &check; | &check; | &check; |                            |
| New-Module                        | &check; | &check; | &check; | &check; |                            |
| New-ModuleManifest                | &check; | &check; | &check; | &check; |                            |
| New-PSRoleCapabilityFile          | &check; | &check; | &check; | &check; |                            |
| New-PSSession                     | &check; | &check; | &check; | &check; |                            |
| New-PSSessionConfigurationFile    | &check; | &check; | &check; | &check; | 僅限 Windows               |
| New-PSSessionOption               | &check; | &check; | &check; | &check; |                            |
| New-PSTransportOption             | &check; | &check; | &check; | &check; |                            |
| Out-Default                       | &check; | &check; | &check; | &check; |                            |
| Out-Host                          | &check; | &check; | &check; | &check; |                            |
| Out-Null                          | &check; | &check; | &check; | &check; |                            |
| Receive-Job                       | &check; | &check; | &check; | &check; |                            |
| Receive-PSSession                 | &check; | &check; | &check; | &check; | 僅限 Windows               |
| Register-ArgumentCompleter        | &check; | &check; | &check; | &check; |                            |
| Register-PSSessionConfiguration   | &check; | &check; | &check; | &check; | 僅限 Windows               |
| Remove-Job                        | &check; | &check; | &check; | &check; |                            |
| Remove-Module                     | &check; | &check; | &check; | &check; |                            |
| Remove-PSSession                  | &check; | &check; | &check; | &check; |                            |
| Remove-PSSnapin                   | &check; |         |         |         | 僅限 Windows               |
| Resume-Job                        | &check; |         |         |         |                            |
| Save-Help                         | &check; | &check; | &check; | &check; |                            |
| Set-PSDebug                       | &check; | &check; | &check; | &check; |                            |
| Set-PSSessionConfiguration        | &check; | &check; | &check; | &check; | 僅限 Windows               |
| Set-StrictMode                    | &check; | &check; | &check; | &check; |                            |
| Start-Job                         | &check; | &check; | &check; | &check; |                            |
| Stop-Job                          | &check; | &check; | &check; | &check; |                            |
| Suspend-Job                       | &check; |         |         |         | 僅限 Windows               |
| Test-ModuleManifest               | &check; | &check; | &check; | &check; |                            |
| Test-PSSessionConfigurationFile   | &check; | &check; | &check; | &check; | 僅限 Windows               |
| Unregister-PSSessionConfiguration | &check; | &check; | &check; | &check; | 僅限 Windows               |
| Update-Help                       | &check; | &check; | &check; | &check; |                            |
| Wait-Job                          | &check; | &check; | &check; | &check; |                            |
| Where-Object                      | &check; | &check; | &check; | &check; |                            |

### <a name="microsoftpowershelldiagnostics"></a>Microsoft.PowerShell.Diagnostics

|  Cmdlet 名稱   |   5.1   |   6.x   |   7.0   |   7.1   |     附註     |
| -------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| Export-Counter | &check; |         |         |         | 僅限 Windows |
| Get-Counter    | &check; |         | &check; | &check; | 僅限 Windows |
| Get-WinEvent   | &check; | &check; | &check; | &check; | 僅限 Windows |
| Import-Counter | &check; |         |         |         | 僅限 Windows |
| New-WinEvent   | &check; | &check; | &check; | &check; | 僅限 Windows |

### <a name="microsoftpowershellhost"></a>Microsoft.PowerShell.Host

|   Cmdlet 名稱    |   5.1   |   6.x   |   7.0   |   7.1   | 附註 |
| ---------------- | :-----: | :-----: | :-----: | :-----: | ---- |
| Start-Transcript | &check; | &check; | &check; | &check; |      |
| Stop-Transcript  | &check; | &check; | &check; | &check; |      |

### <a name="microsoftpowershelllocalaccounts"></a>Microsoft.PowerShell.LocalAccounts

|       Cmdlet 名稱       |   5.1   | 6.x  |  7.0  |  7.1  |     附註     |
| ----------------------- | :-----: | :--- | :---: | :---: | ------------ |
| Add-LocalGroupMember    | &check; |      |       |       | 僅限 Windows |
| Disable-LocalUser       | &check; |      |       |       | 僅限 Windows |
| Enable-LocalUser        | &check; |      |       |       | 僅限 Windows |
| Get-LocalGroup          | &check; |      |       |       | 僅限 Windows |
| Get-LocalGroupMember    | &check; |      |       |       | 僅限 Windows |
| Get-LocalUser           | &check; |      |       |       | 僅限 Windows |
| New-LocalGroup          | &check; |      |       |       | 僅限 Windows |
| New-LocalUser           | &check; |      |       |       | 僅限 Windows |
| Remove-LocalGroup       | &check; |      |       |       | 僅限 Windows |
| Remove-LocalGroupMember | &check; |      |       |       | 僅限 Windows |
| Remove-LocalUser        | &check; |      |       |       | 僅限 Windows |
| Rename-LocalGroup       | &check; |      |       |       | 僅限 Windows |
| Rename-LocalUser        | &check; |      |       |       | 僅限 Windows |
| Set-LocalGroup          | &check; |      |       |       | 僅限 Windows |
| Set-LocalUser           | &check; |      |       |       | 僅限 Windows |

### <a name="microsoftpowershellmanagement"></a>Microsoft.PowerShell.Management

|          Cmdlet 名稱          |   5.1   |   6.x   |   7.0   |   7.1   |               附註               |
| ----------------------------- | :-----: | :-----: | :-----: | :-----: | -------------------------------- |
| Add-Computer                  | &check; |         |         |         | 僅限 Windows                     |
| Add-Content                   | &check; | &check; | &check; | &check; |                                  |
| Checkpoint-Computer           | &check; |         |         |         | 僅限 Windows                     |
| Clear-Content                 | &check; | &check; | &check; | &check; |                                  |
| Clear-EventLog                | &check; |         |         |         | 僅限 Windows                     |
| Clear-Item                    | &check; | &check; | &check; | &check; |                                  |
| Clear-ItemProperty            | &check; | &check; | &check; | &check; |                                  |
| Clear-RecycleBin              | &check; |         | &check; | &check; | 僅限 Windows                     |
| Complete-Transaction          | &check; |         |         |         | 僅限 Windows                     |
| Convert-Path                  | &check; | &check; | &check; | &check; |                                  |
| Copy-Item                     | &check; | &check; | &check; | &check; |                                  |
| Copy-ItemProperty             | &check; | &check; | &check; | &check; |                                  |
| Debug-Process                 | &check; | &check; | &check; | &check; |                                  |
| Disable-ComputerRestore       | &check; |         |         |         | 僅限 Windows                     |
| Enable-ComputerRestore        | &check; |         |         |         | 僅限 Windows                     |
| Get-ChildItem                 | &check; | &check; | &check; | &check; |                                  |
| Get-Clipboard                 | &check; |         | &check; | &check; | 在 macOS 上不支援           |
| Get-ComputerInfo              | &check; | &check; | &check; | &check; | 僅限 Windows                     |
| Get-ComputerRestorePoint      | &check; |         |         |         | 僅限 Windows                     |
| Get-Content                   | &check; | &check; | &check; | &check; |                                  |
| Get-ControlPanelItem          | &check; |         |         |         | 僅限 Windows                     |
| Get-EventLog                  | &check; |         |         |         | 僅限 Windows                     |
| Get-HotFix                    | &check; |         | &check; | &check; | 僅限 Windows                     |
| Get-Item                      | &check; | &check; | &check; | &check; |                                  |
| Get-ItemProperty              | &check; | &check; | &check; | &check; |                                  |
| Get-ItemPropertyValue         | &check; | &check; | &check; | &check; |                                  |
| Get-Location                  | &check; | &check; | &check; | &check; |                                  |
| Get-Process                   | &check; | &check; | &check; | &check; |                                  |
| Get-PSDrive                   | &check; | &check; | &check; | &check; |                                  |
| Get-PSProvider                | &check; | &check; | &check; | &check; |                                  |
| Get-Service                   | &check; | &check; | &check; | &check; | 僅限 Windows                     |
| Get-TimeZone                  | &check; | &check; | &check; | &check; | 僅限 Windows                     |
| Get-Transaction               | &check; |         |         |         | 僅限 Windows                     |
| Get-WmiObject                 | &check; |         |         |         | 僅限 Windows                     |
| Invoke-Item                   | &check; | &check; | &check; | &check; |                                  |
| Invoke-WmiMethod              | &check; |         |         |         | 僅限 Windows                     |
| Join-Path                     | &check; | &check; | &check; | &check; |                                  |
| Limit-EventLog                | &check; |         |         |         | 僅限 Windows                     |
| Move-Item                     | &check; | &check; | &check; | &check; |                                  |
| Move-ItemProperty             | &check; | &check; | &check; | &check; |                                  |
| New-EventLog                  | &check; |         |         |         | 僅限 Windows                     |
| New-Item                      | &check; | &check; | &check; | &check; |                                  |
| New-ItemProperty              | &check; | &check; | &check; | &check; |                                  |
| New-PSDrive                   | &check; | &check; | &check; | &check; |                                  |
| New-Service                   | &check; | &check; | &check; | &check; | 僅限 Windows                     |
| New-WebServiceProxy           | &check; |         |         |         | 僅限 Windows                     |
| Pop-Location                  | &check; | &check; | &check; | &check; |                                  |
| Push-Location                 | &check; | &check; | &check; | &check; |                                  |
| Register-WmiEvent             | &check; |         |         |         | 僅限 Windows                     |
| Remove-Computer               | &check; |         |         |         | 僅限 Windows                     |
| Remove-EventLog               | &check; |         |         |         | 僅限 Windows                     |
| Remove-Item                   | &check; | &check; | &check; | &check; |                                  |
| Remove-ItemProperty           | &check; | &check; | &check; | &check; |                                  |
| Remove-PSDrive                | &check; | &check; | &check; | &check; |                                  |
| Remove-Service                |         | &check; | &check; | &check; | 僅限 Windows                     |
| Remove-WmiObject              | &check; |         |         |         | 僅限 Windows                     |
| Rename-Computer               | &check; | &check; | &check; | &check; | 僅限 Windows                     |
| Rename-Item                   | &check; | &check; | &check; | &check; |                                  |
| Rename-ItemProperty           | &check; | &check; | &check; | &check; |                                  |
| Reset-ComputerMachinePassword | &check; |         |         |         | 僅限 Windows                     |
| Resolve-Path                  | &check; | &check; | &check; | &check; |                                  |
| Restart-Computer              | &check; | &check; | &check; | &check; | 在 7.1 中新增 Linux/macOS 支援 |
| Restart-Service               | &check; | &check; | &check; | &check; | 僅限 Windows                     |
| Restore-Computer              | &check; |         |         |         | 僅限 Windows                     |
| Resume-Service                | &check; | &check; | &check; | &check; | 僅限 Windows                     |
| Set-Clipboard                 | &check; |         | &check; | &check; |                                  |
| Set-Content                   | &check; | &check; | &check; | &check; |                                  |
| Set-Item                      | &check; | &check; | &check; | &check; |                                  |
| Set-ItemProperty              | &check; | &check; | &check; | &check; |                                  |
| Set-Location                  | &check; | &check; | &check; | &check; |                                  |
| Set-Service                   | &check; | &check; | &check; | &check; | 僅限 Windows                     |
| Set-TimeZone                  | &check; | &check; | &check; | &check; | 僅限 Windows                     |
| Set-WmiInstance               | &check; |         |         |         | 僅限 Windows                     |
| Show-ControlPanelItem         | &check; |         |         |         | 僅限 Windows                     |
| Show-EventLog                 | &check; |         |         |         | 僅限 Windows                     |
| Split-Path                    | &check; | &check; | &check; | &check; |                                  |
| Start-Process                 | &check; | &check; | &check; | &check; |                                  |
| Start-Service                 | &check; | &check; | &check; | &check; | 僅限 Windows                     |
| Start-Transaction             | &check; |         |         |         | 僅限 Windows                     |
| Stop-Computer                 | &check; | &check; | &check; | &check; | 在 7.1 中新增 Linux/macOS 支援 |
| Stop-Process                  | &check; | &check; | &check; | &check; |                                  |
| Stop-Service                  | &check; | &check; | &check; | &check; | 僅限 Windows                     |
| Suspend-Service               | &check; | &check; | &check; | &check; | 僅限 Windows                     |
| Test-ComputerSecureChannel    | &check; |         |         |         | 僅限 Windows                     |
| Test-Connection               | &check; | &check; | &check; | &check; |                                  |
| Test-Path                     | &check; | &check; | &check; | &check; |                                  |
| Undo-Transaction              | &check; |         |         |         | 僅限 Windows                     |
| Use-Transaction               | &check; |         |         |         | 僅限 Windows                     |
| Wait-Process                  | &check; | &check; | &check; | &check; | 無法在 Linux/macOS 上運作     |
| Write-EventLog                | &check; |         |         |         | 僅限 Windows                     |

### <a name="microsoftpowershellodatautils"></a>Microsoft.PowerShell.ODataUtils

|        Cmdlet 名稱        |   5.1   | 6.x  |  7.0  |  7.1  |     附註     |
| ------------------------- | :-----: | :--- | :---: | :---: | ------------ |
| Export-ODataEndpointProxy | &check; |      |       |       | 僅限 Windows |

### <a name="microsoftpowershelloperationvalidation"></a>Microsoft.PowerShell.Operation.Validation

|        Cmdlet 名稱         |   5.1   | 6.x  |  7.0  |  7.1  |     附註     |
| -------------------------- | :-----: | :--- | :---: | :---: | ------------ |
| Get-OperationValidation    | &check; |      |       |       | 僅限 Windows |
| Invoke-OperationValidation | &check; |      |       |       | 僅限 Windows |

### <a name="microsoftpowershellsecurity"></a>Microsoft.PowerShell.Security

|        Cmdlet 名稱        |   5.1   |   6.x   |   7.0   |   7.1   |                  附註                   |
| ------------------------- | :-----: | :-----: | :-----: | :-----: | --------------------------------------- |
| ConvertFrom-SecureString  | &check; | &check; | &check; | &check; |                                         |
| ConvertTo-SecureString    | &check; | &check; | &check; | &check; |                                         |
| Get-Acl                   | &check; | &check; | &check; | &check; | 僅限 Windows                            |
| Get-AuthenticodeSignature | &check; | &check; | &check; | &check; | 僅限 Windows                            |
| Get-CmsMessage            | &check; | &check; | &check; | &check; | 7\.1 中新增的 Linux/macOS 支援    |
| Get-Credential            | &check; | &check; | &check; | &check; |                                         |
| Get-executionpolicy       | &check; | &check; | &check; | &check; | 在 Linux/macOS 上傳回 **未受限制** |
| Get-PfxCertificate        | &check; | &check; | &check; | &check; |                                         |
| New-FileCatalog           | &check; | &check; | &check; | &check; | 僅限 Windows                            |
| Protect-CmsMessage        | &check; | &check; | &check; | &check; | 7\.1 中新增的 Linux/macOS 支援    |
| Set-Acl                   | &check; | &check; | &check; | &check; | 僅限 Windows                            |
| Set-AuthenticodeSignature | &check; | &check; | &check; | &check; | 僅限 Windows                            |
| Set-ExecutionPolicy       | &check; | &check; | &check; | &check; | 在 Linux/macOS 上不會執行任何動作             |
| Test-FileCatalog          | &check; | &check; | &check; | &check; | 僅限 Windows                            |
| Unprotect-CmsMessage      | &check; | &check; | &check; | &check; | 7\.1 中新增的 Linux/macOS 支援    |

### <a name="microsoftpowershellutility"></a>Microsoft.PowerShell.Utility

|        Cmdlet 名稱        |   5.1   |   6.x   |   7.0   |   7.1   |                   附註                    |
| ------------------------- | :-----: | :-----: | :-----: | :-----: | ----------------------------------------- |
| Add-Member                | &check; | &check; | &check; | &check; |                                           |
| Add-Type                  | &check; | &check; | &check; | &check; |                                           |
| Clear-Variable            | &check; | &check; | &check; | &check; |                                           |
| Compare-Object            | &check; | &check; | &check; | &check; |                                           |
| ConvertFrom-Csv           | &check; | &check; | &check; | &check; |                                           |
| ConvertFrom-Json          | &check; | &check; | &check; | &check; |                                           |
| ConvertFrom-Markdown      |         |   6.1   | &check; | &check; |                                           |
| ConvertFrom-SddlString    | &check; | &check; | &check; | &check; | 僅限 Windows                              |
| ConvertFrom-String        | &check; |         |         |         |                                           |
| ConvertFrom-StringData    | &check; | &check; | &check; | &check; |                                           |
| Convert-String            | &check; |         |         |         |                                           |
| ConvertTo-Csv             | &check; | &check; | &check; | &check; |                                           |
| ConvertTo-Html            | &check; | &check; | &check; | &check; |                                           |
| ConvertTo-Json            | &check; | &check; | &check; | &check; |                                           |
| ConvertTo-Xml             | &check; | &check; | &check; | &check; |                                           |
| Debug-Runspace            | &check; | &check; | &check; | &check; |                                           |
| Disable-PSBreakpoint      | &check; | &check; | &check; | &check; |                                           |
| Disable-RunspaceDebug     | &check; | &check; | &check; | &check; |                                           |
| Enable-PSBreakpoint       | &check; | &check; | &check; | &check; |                                           |
| Enable-RunspaceDebug      | &check; | &check; | &check; | &check; |                                           |
| Export-Alias              | &check; | &check; | &check; | &check; |                                           |
| Export-Clixml             | &check; | &check; | &check; | &check; |                                           |
| Export-Csv                | &check; | &check; | &check; | &check; |                                           |
| Export-FormatData         | &check; | &check; | &check; | &check; |                                           |
| Export-PSSession          | &check; | &check; | &check; | &check; |                                           |
| Format-Custom             | &check; | &check; | &check; | &check; |                                           |
| Format-Hex                | &check; | &check; | &check; | &check; |                                           |
| Format-List               | &check; | &check; | &check; | &check; |                                           |
| Format-Table              | &check; | &check; | &check; | &check; |                                           |
| Format-Wide               | &check; | &check; | &check; | &check; |                                           |
| Get-Alias                 | &check; | &check; | &check; | &check; |                                           |
| Get-Culture               | &check; | &check; | &check; | &check; |                                           |
| Get-Date                  | &check; | &check; | &check; | &check; |                                           |
| Get-Error                 |         |         | &check; | &check; |                                           |
| Get-Event                 | &check; | &check; | &check; | &check; | 在 Linux/macOS 上沒有可用的事件來源 |
| Get-EventSubscriber       | &check; | &check; | &check; | &check; |                                           |
| Get-FileHash              | &check; | &check; | &check; | &check; |                                           |
| Get-FormatData            | &check; | &check; | &check; | &check; |                                           |
| Get-Host                  | &check; | &check; | &check; | &check; |                                           |
| Get-MarkdownOption        |         |   6.1   | &check; | &check; |                                           |
| Get-Member                | &check; | &check; | &check; | &check; |                                           |
| Get-PSBreakpoint          | &check; | &check; | &check; | &check; |                                           |
| Get-PSCallStack           | &check; | &check; | &check; | &check; |                                           |
| Get-Random                | &check; | &check; | &check; | &check; |                                           |
| Get-Runspace              | &check; | &check; | &check; | &check; |                                           |
| Get-RunspaceDebug         | &check; | &check; | &check; | &check; |                                           |
| Get-TraceSource           | &check; | &check; | &check; | &check; |                                           |
| Get-TypeData              | &check; | &check; | &check; | &check; |                                           |
| Get-UICulture             | &check; | &check; | &check; | &check; |                                           |
| Get-Unique                | &check; | &check; | &check; | &check; |                                           |
| Get-Uptime                |         | &check; | &check; | &check; |                                           |
| Get-Variable              | &check; | &check; | &check; | &check; |                                           |
| Get-Verb                  |         | &check; | &check; | &check; | 從 Microsoft.PowerShelll.Core 移動     |
| Group-Object              | &check; | &check; | &check; | &check; |                                           |
| Import-Alias              | &check; | &check; | &check; | &check; |                                           |
| Import-Clixml             | &check; | &check; | &check; | &check; |                                           |
| Import-Csv                | &check; | &check; | &check; | &check; |                                           |
| Import-LocalizedData      | &check; | &check; | &check; | &check; |                                           |
| Import-PowerShellDataFile | &check; | &check; | &check; | &check; |                                           |
| Import-PSSession          | &check; | &check; | &check; | &check; |                                           |
| Invoke-Expression         | &check; | &check; | &check; | &check; |                                           |
| Invoke-RestMethod         | &check; | &check; | &check; | &check; |                                           |
| Invoke-WebRequest         | &check; | &check; | &check; | &check; |                                           |
| Join-String               |         | &check; | &check; | &check; |                                           |
| Measure-Command           | &check; | &check; | &check; | &check; |                                           |
| Measure-Object            | &check; | &check; | &check; | &check; |                                           |
| New-Alias                 | &check; | &check; | &check; | &check; |                                           |
| New-Event                 | &check; | &check; | &check; | &check; | 在 Linux/macOS 上沒有可用的事件來源 |
| New-Guid                  | &check; | &check; | &check; | &check; |                                           |
| New-Object                | &check; | &check; | &check; | &check; |                                           |
| New-TemporaryFile         | &check; | &check; | &check; | &check; |                                           |
| New-TimeSpan              | &check; | &check; | &check; | &check; |                                           |
| New-Variable              | &check; | &check; | &check; | &check; |                                           |
| Out-File                  | &check; | &check; | &check; | &check; |                                           |
| Out-GridView              | &check; |         | &check; | &check; | 僅限 Windows                              |
| Out-Printer               | &check; |         | &check; | &check; | 僅限 Windows                              |
| Out-String                | &check; | &check; | &check; | &check; |                                           |
| Read-Host                 | &check; | &check; | &check; | &check; |                                           |
| Register-EngineEvent      | &check; | &check; | &check; | &check; | 在 Linux/macOS 上沒有可用的事件來源 |
| Register-ObjectEvent      | &check; | &check; | &check; | &check; |                                           |
| Remove-Alias              |         | &check; | &check; | &check; |                                           |
| Remove-Event              | &check; | &check; | &check; | &check; | 在 Linux/macOS 上沒有可用的事件來源 |
| Remove-PSBreakpoint       | &check; | &check; | &check; | &check; |                                           |
| Remove-TypeData           | &check; | &check; | &check; | &check; |                                           |
| Remove-Variable           | &check; | &check; | &check; | &check; |                                           |
| Select-Object             | &check; | &check; | &check; | &check; |                                           |
| Select-String             | &check; | &check; | &check; | &check; |                                           |
| Select-Xml                | &check; | &check; | &check; | &check; |                                           |
| Send-MailMessage          | &check; | &check; | &check; | &check; |                                           |
| Set-Alias                 | &check; | &check; | &check; | &check; |                                           |
| Set-Date                  | &check; | &check; | &check; | &check; |                                           |
| Set-MarkdownOption        |         |   6.1   | &check; | &check; |                                           |
| Set-PSBreakpoint          | &check; | &check; | &check; | &check; |                                           |
| Set-TraceSource           | &check; | &check; | &check; | &check; |                                           |
| Set-Variable              | &check; | &check; | &check; | &check; |                                           |
| Show-Command              | &check; |         | &check; | &check; | 僅限 Windows                              |
| Show-Markdown             |         |   6.1   | &check; | &check; |                                           |
| Sort-Object               | &check; | &check; | &check; | &check; |                                           |
| Start-Sleep               | &check; | &check; | &check; | &check; |                                           |
| Tee-Object                | &check; | &check; | &check; | &check; |                                           |
| Test-Json                 |         | &check; | &check; | &check; |                                           |
| Trace-Command             | &check; | &check; | &check; | &check; |                                           |
| Unblock-File              | &check; | &check; | &check; | &check; | 在 7.0 中已加入對 macOS 的支援            |
| Unregister-Event          | &check; | &check; | &check; | &check; | 在 Linux/macOS 上沒有可用的事件來源 |
| Update-FormatData         | &check; | &check; | &check; | &check; |                                           |
| Update-List               | &check; |         | &check; | &check; |                                           |
| Update-TypeData           | &check; | &check; | &check; | &check; |                                           |
| Wait-Debugger             | &check; | &check; | &check; | &check; |                                           |
| Wait-Event                | &check; | &check; | &check; | &check; |                                           |
| Write-Debug               | &check; | &check; | &check; | &check; |                                           |
| Write-Error               | &check; | &check; | &check; | &check; |                                           |
| Write-Host                | &check; | &check; | &check; | &check; |                                           |
| Write-Information         | &check; | &check; | &check; | &check; |                                           |
| Write-Output              | &check; | &check; | &check; | &check; |                                           |
| Write-Progress            | &check; | &check; | &check; | &check; |                                           |
| Write-Verbose             | &check; | &check; | &check; | &check; |                                           |
| Write-Warning             | &check; | &check; | &check; | &check; |                                           |

### <a name="microsoftwsmanmanagement"></a>Microsoft.WsMan.Management

|      Cmdlet 名稱       |   5.1   |   6.x   |   7.0   |   7.1   |     附註     |
| ---------------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| Connect-WSMan          | &check; | &check; | &check; | &check; | 僅限 Windows |
| Disable-WSManCredSSP   | &check; | &check; | &check; | &check; | 僅限 Windows |
| Disconnect-WSMan       | &check; | &check; | &check; | &check; | 僅限 Windows |
| Enable-WSManCredSSP    | &check; | &check; | &check; | &check; | 僅限 Windows |
| Get-WSManCredSSP       | &check; | &check; | &check; | &check; | 僅限 Windows |
| Get-WSManInstance      | &check; | &check; | &check; | &check; | 僅限 Windows |
| Invoke-WSManAction     | &check; | &check; | &check; | &check; | 僅限 Windows |
| New-WSManInstance      | &check; | &check; | &check; | &check; | 僅限 Windows |
| New-WSManSessionOption | &check; | &check; | &check; | &check; | 僅限 Windows |
| Remove-WSManInstance   | &check; | &check; | &check; | &check; | 僅限 Windows |
| Set-WSManInstance      | &check; | &check; | &check; | &check; | 僅限 Windows |
| Set-WSManQuickConfig   | &check; | &check; | &check; | &check; | 僅限 Windows |
| Test-WSMan             | &check; | &check; | &check; | &check; | 僅限 Windows |

### <a name="packagemanagement"></a>PackageManagement

|       Cmdlet 名稱        |   5.1   |   6.x   |   7.0   |   7.1   | 附註 |
| ------------------------ | :-----: | :-----: | :-----: | :-----: | ---- |
| Find-Package             | &check; | &check; | &check; | &check; |      |
| Find-PackageProvider     | &check; | &check; | &check; | &check; |      |
| Get-Package              | &check; | &check; | &check; | &check; |      |
| Get-PackageProvider      | &check; | &check; | &check; | &check; |      |
| Get-PackageSource        | &check; | &check; | &check; | &check; |      |
| Import-PackageProvider   | &check; | &check; | &check; | &check; |      |
| Install-Package          | &check; | &check; | &check; | &check; |      |
| Install-PackageProvider  | &check; | &check; | &check; | &check; |      |
| Register-PackageSource   | &check; | &check; | &check; | &check; |      |
| Save-Package             | &check; | &check; | &check; | &check; |      |
| Set-PackageSource        | &check; | &check; | &check; | &check; |      |
| Uninstall-Package        | &check; | &check; | &check; | &check; |      |
| Unregister-PackageSource | &check; | &check; | &check; | &check; |      |

### <a name="powershellget"></a>PowershellGet

|           Cmdlet 名稱           |   5.1   |   6.x   |   7.0   |   7.1   | 附註 |
| ------------------------------- | :-----: | :-----: | :-----: | :-----: | ---- |
| Find-Command                    | &check; | &check; | &check; | &check; |      |
| Find-DscResource                | &check; | &check; | &check; | &check; |      |
| Find-Module                     | &check; | &check; | &check; | &check; |      |
| Find-RoleCapability             | &check; | &check; | &check; | &check; |      |
| Find-Script                     | &check; | &check; | &check; | &check; |      |
| Get-CredsFromCredentialProvider |         | &check; | &check; | &check; |      |
| Get-InstalledModule             | &check; | &check; | &check; | &check; |      |
| Get-InstalledScript             | &check; | &check; | &check; | &check; |      |
| Get-PSRepository                | &check; | &check; | &check; | &check; |      |
| Install-Module                  | &check; | &check; | &check; | &check; |      |
| Install-Script                  | &check; | &check; | &check; | &check; |      |
| New-ScriptFileInfo              | &check; | &check; | &check; | &check; |      |
| Publish-Module                  | &check; | &check; | &check; | &check; |      |
| Publish-Script                  | &check; | &check; | &check; | &check; |      |
| Register-PSRepository           | &check; | &check; | &check; | &check; |      |
| Save-Module                     | &check; | &check; | &check; | &check; |      |
| Save-Script                     | &check; | &check; | &check; | &check; |      |
| Set-PSRepository                | &check; | &check; | &check; | &check; |      |
| Test-ScriptFileInfo             | &check; | &check; | &check; | &check; |      |
| Uninstall-Module                | &check; | &check; | &check; | &check; |      |
| Uninstall-Script                | &check; | &check; | &check; | &check; |      |
| Unregister-PSRepository         | &check; | &check; | &check; | &check; |      |
| Update-Module                   | &check; | &check; | &check; | &check; |      |
| Update-ModuleManifest           | &check; | &check; | &check; | &check; |      |
| Update-Script                   | &check; | &check; | &check; | &check; |      |
| Update-ScriptFileInfo           | &check; | &check; | &check; | &check; |      |

### <a name="psdesiredstateconfiguration"></a>PSDesiredStateConfiguration

|                Cmdlet 名稱                 |   5.1   |   6.x   |   7.0   |   7.1   |     附註     |
| ------------------------------------------ | :-----: | :-----: | :-----: | :-----: | ------------ |
| Disable-DscDebug                           | &check; |         |         |         | 僅限 Windows |
| Enable-DscDebug                            | &check; |         |         |         | 僅限 Windows |
| Get-DscConfiguration                       | &check; |         |         |         | 僅限 Windows |
| Get-DscConfigurationStatus                 | &check; |         |         |         | 僅限 Windows |
| Get-DscLocalConfigurationManager           | &check; |         |         |         | 僅限 Windows |
| Get-DscResource                            | &check; | &check; | &check; | &check; |              |
| Invoke-DscResource                         | &check; |         | &check; | &check; |              |
| New-DSCCheckSum                            | &check; | &check; | &check; | &check; |              |
| Publish-DscConfiguration                   | &check; |         |         |         | 僅限 Windows |
| Remove-DscConfigurationDocument            | &check; |         |         |         | 僅限 Windows |
| Restore-DscConfiguration                   | &check; |         |         |         | 僅限 Windows |
| Set-DscLocalConfigurationManager           | &check; |         |         |         | 僅限 Windows |
| Start-DscConfiguration                     | &check; |         |         |         | 僅限 Windows |
| Stop-DscConfiguration                      | &check; |         |         |         | 僅限 Windows |
| Test-DscConfiguration                      | &check; |         |         |         | 僅限 Windows |
| Update-DscConfiguration                    | &check; |         |         |         | 僅限 Windows |

### <a name="psdiagnostics"></a>PSDiagnostics

|         Cmdlet 名稱          |   5.1   |   6.x   |   7.0   |   7.1   |     附註     |
| ---------------------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| Disable-PSTrace              | &check; |   6.2   | &check; | &check; | 僅限 Windows |
| Disable-PSWSManCombinedTrace | &check; |   6.2   | &check; | &check; | 僅限 Windows |
| Disable-WSManTrace           | &check; | &check; | &check; | &check; | 僅限 Windows |
| Enable-PSTrace               | &check; | &check; | &check; | &check; | 僅限 Windows |
| Enable-PSWSManCombinedTrace  | &check; | &check; | &check; | &check; | 僅限 Windows |
| Enable-WSManTrace            | &check; |   6.2   | &check; | &check; | 僅限 Windows |
| Get-LogProperties            | &check; |   6.2   | &check; | &check; | 僅限 Windows |
| Set-LogProperties            | &check; |   6.2   | &check; | &check; | 僅限 Windows |
| Start-Trace                  | &check; |   6.2   | &check; | &check; | 僅限 Windows |
| Stop-Trace                   | &check; |   6.2   | &check; | &check; | 僅限 Windows |

### <a name="psreadline"></a>PSReadline

|         Cmdlet 名稱         |   5.1   |   6.x   |   7.0   |   7.1   | 附註 |
| --------------------------- | :-----: | :-----: | :-----: | :-----: | ---- |
| Get-PSReadlineKeyHandler    | &check; | &check; | &check; | &check; |      |
| Get-PSReadlineOption        | &check; | &check; | &check; | &check; |      |
| PSConsoleHostReadline       | &check; | &check; | &check; | &check; |      |
| Remove-PSReadlineKeyHandler | &check; | &check; | &check; | &check; |      |
| Set-PSReadlineKeyHandler    | &check; | &check; | &check; | &check; |      |
| Set-PSReadlineOption        | &check; | &check; | &check; | &check; |      |

### <a name="psscheduledjob"></a>PSScheduledJob

|       Cmdlet 名稱       |   5.1   | 6.x  |  7.0  |  7.1  |     附註     |
| ----------------------- | :-----: | :--- | :---: | :---: | ------------ |
| Add-JobTrigger          | &check; |      |       |       | 僅限 Windows |
| Disable-JobTrigger      | &check; |      |       |       | 僅限 Windows |
| Disable-ScheduledJob    | &check; |      |       |       | 僅限 Windows |
| Enable-JobTrigger       | &check; |      |       |       | 僅限 Windows |
| Enable-ScheduledJob     | &check; |      |       |       | 僅限 Windows |
| Get-JobTrigger          | &check; |      |       |       | 僅限 Windows |
| Get-ScheduledJob        | &check; |      |       |       | 僅限 Windows |
| Get-ScheduledJobOption  | &check; |      |       |       | 僅限 Windows |
| New-JobTrigger          | &check; |      |       |       | 僅限 Windows |
| New-ScheduledJobOption  | &check; |      |       |       | 僅限 Windows |
| Register-ScheduledJob   | &check; |      |       |       | 僅限 Windows |
| Remove-JobTrigger       | &check; |      |       |       | 僅限 Windows |
| Set-JobTrigger          | &check; |      |       |       | 僅限 Windows |
| Set-ScheduledJob        | &check; |      |       |       | 僅限 Windows |
| Set-ScheduledJobOption  | &check; |      |       |       | 僅限 Windows |
| Unregister-ScheduledJob | &check; |      |       |       | 僅限 Windows |

### <a name="psworkflow--psworkflowutility"></a>PSWorkflow & PSWorkflowUtility

|          Cmdlet 名稱          |   5.1   | 6.x  |  7.0  |  7.1  |     附註     |
| ----------------------------- | :-----: | :--- | :---: | :---: | ------------ |
| New-PSWorkflowExecutionOption | &check; |      |       |       | 僅限 Windows |
| New-PSWorkflowSession         | &check; |      |       |       | 僅限 Windows |
| Invoke-AsWorkflow             | &check; |      |       |       | 僅限 Windows |

### <a name="threadjob"></a>ThreadJob

|   Cmdlet 名稱   |  5.1  |   6.x   |   7.0   |   7.1   | 附註 |
| --------------- | :---: | :-----: | :-----: | :-----: | ---- |
| Start-ThreadJob |       | &check; | &check; | &check; | 可以安裝在 PowerShell 5.1 中 |
