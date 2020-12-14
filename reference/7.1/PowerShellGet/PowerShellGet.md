---
Download Help Link: https://aka.ms/powershell71-help
Help Version: 7.1.0.0
keywords: powershell,cmdlet
Locale: en-US
Module Guid: 1d73a601-4a6c-43c5-ba3f-619b18bbb404
Module Name: PowerShellGet
ms.date: 06/09/2017
schema: 2.0.0
title: PowerShellGet
ms.openlocfilehash: 577dc9a56da98d975b777e6cd48ecdcaafd3128d
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2020
ms.locfileid: "94892364"
---
# PowerShellGet 模組

## 說明

PowerShellGet 是一個模組，其中包含用於探索、安裝、更新及發佈 PowerShell 成品（例如模組、DSC 資源、角色功能和腳本）的命令。

> [!IMPORTANT]
> 從2020年4月起，PowerShell 資源庫不再支援傳輸層安全性 (TLS) 1.0 和1.1 版。 如果您不是使用 TLS 1.2 或更高版本，當您嘗試存取 PowerShell 資源庫時，將會收到錯誤。 使用下列命令，以確保您使用的是 TLS 1.2：
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> 如需詳細資訊，請參閱 PowerShell blog 中的 [公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) 。

## PowerShellGet Cmdlet

### [Find-Command](Find-Command.md)
尋找模組中的 PowerShell 命令。

### [Find-DscResource](Find-DscResource.md)
尋找 Desired State Configuration (DSC) 資源。

### [Find-Module](Find-Module.md)
在存放庫中尋找符合指定準則的模組。

### [Find-RoleCapability](Find-RoleCapability.md)
尋找模組中的角色功能。

### [Find-Script](Find-Script.md)
尋找腳本。

### [Get-InstalledModule](Get-InstalledModule.md)
取得由 PowerShellGet 安裝之電腦上的模組清單。

### [Get-InstalledScript](Get-InstalledScript.md)
取得已安裝的腳本。

### [Get-PSRepository](Get-PSRepository.md)
取得 PowerShell 存放庫。

### [Install-Module](Install-Module.md)
從存放庫下載一或多個模組，並將它們安裝在本機電腦上。

### [Install-Script](Install-Script.md)
安裝腳本。

### [New-ScriptFileInfo](New-ScriptFileInfo.md)
建立含有中繼資料的指令檔。

### [Publish-Module](Publish-Module.md)
將指定的模組從本機電腦發行至線上資源庫。

### [Publish-Script](Publish-Script.md)
發佈腳本。

### [Register-PSRepository](Register-PSRepository.md)
註冊 PowerShell 存放庫。

### [Save-Module](Save-Module.md)
將模組及其相依性儲存在本機電腦上，但不會安裝模組。

### [Save-Script](Save-Script.md)
儲存腳本。

### [Set-PSRepository](Set-PSRepository.md)
設定已註冊存放庫的值。

### [Test-ScriptFileInfo](Test-ScriptFileInfo.md)
驗證腳本的批註區塊。

### [Uninstall-Module](Uninstall-Module.md)
解除安裝模組。

### [Uninstall-Script](Uninstall-Script.md)
卸載腳本。

### [Unregister-PSRepository](Unregister-PSRepository.md)
取消註冊存放庫。

### [Update-Module](Update-Module.md)
將來自線上組件庫之指定模組的最新版本下載並安裝至本機電腦。

### [Update-ModuleManifest](Update-ModuleManifest.md)
更新模組資訊清單檔案。

### [Update-Script](Update-Script.md)
更新腳本。

### [Update-ScriptFileInfo](Update-ScriptFileInfo.md)
更新腳本的資訊。
