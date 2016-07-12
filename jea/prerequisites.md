---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "先決條件"
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: ac9231a475ba84e9051bbd06a65f3f20c9e49846

---

# 必要條件

## 初始狀態
開始本節之前，請確認下列事項︰

1. 系統上有 JEA 可用。 如需目前支援的作業系統和所需的下載項目，請參閱[讀我檔案](./README.md)。
2. 您在要試用 JEA 的電腦上具有系統管理權限。
3. 電腦已加入網域。
請參閱[建立網域控制站](#creating-a-domain-controller)一節，以快速在伺服器上設定新的網域 (如果還沒有)。

## 啟用 PowerShell 遠端
JEA 管理是透過 PowerShell 遠端進行。
在系統管理員的 PowerShell 視窗中執行下列命令，以確保這項功能已啟用且正確設定︰

```PowerShell
Enable-PSRemoting
```

如果您不熟悉 PowerShell 遠端，建議執行 `Get-Help about_Remote` 來了解此重要的基本概念。

## 識別您的使用者或群組
為了示範 JEA 的操作方式，您必須識別要在本指南中使用的非系統管理員使用者和群組。

如果您使用現有的網域，請識別或建立一些非特殊權限使用者和群組。
您將授與 JEA 的非系統管理員存取權。
每當您看到 `$NonAdministrator` 變數出現在指令碼頂端，請將它指派給您選取的非系統管理員使用者或群組。

如果您從頭開始建立新的網域，會比較容易。
請使用附錄中的[設定使用者和群組](creating-a-domain-controller.md#set-up-users-and-groups)一節，來建立非系統管理員使用者和群組。
`$NonAdministrator` 的預設值會是在該節中建立的群組。

## 設定維護角色功能檔案
在 PowerShell 中執行下列命令，建立我們將在下一節中使用的示範角色功能檔案。
稍後在本指南中，您將了解此檔案的用途。

```PowerShell
# Fields in the role capability
$MaintenanceRoleCapabilityCreationParams = @{
    Author = 'Contoso Admin'
    CompanyName = 'Contoso'
    VisibleCmdlets = 'Restart-Service'
    FunctionDefinitions =
            @{ Name = 'Get-UserInfo'; ScriptBlock = { $PSSenderInfo } }
}

# Create the demo module, which will contain the maintenance Role Capability File
New-Item -Path "$env:ProgramFiles\WindowsPowerShell\Modules\Demo_Module" -ItemType Directory
New-ModuleManifest -Path "$env:ProgramFiles\WindowsPowerShell\Modules\Demo_Module\Demo_Module.psd1"
New-Item -Path "$env:ProgramFiles\WindowsPowerShell\Modules\Demo_Module\RoleCapabilities" -ItemType Directory

# Create the Role Capability file
New-PSRoleCapabilityFile -Path "$env:ProgramFiles\WindowsPowerShell\Modules\Demo_Module\RoleCapabilities\Maintenance.psrc" @MaintenanceRoleCapabilityCreationParams
```

## 建立及登錄示範工作階段設定檔
執行下列命令，建立及登錄我們將在下一節中使用的示範工作階段設定檔。
稍後在本指南中，您將了解此檔案的用途。

```PowerShell
# Determine domain
$domain = (Get-CimInstance -ClassName Win32_ComputerSystem).Domain

# Replace with your non-admin group name
$NonAdministrator = "$domain\JEA_NonAdmin_Operator"

# Specify the settings for this JEA endpoint
# Note: You will not be able to use a virtual account if you are using WMF 5.0 on Windows 7 or Windows Server 2008 R2
$JEAConfigParams = @{
    SessionType = 'RestrictedRemoteServer'
    RunAsVirtualAccount = $true
    RoleDefinitions = @{
        $NonAdministrator = @{ RoleCapabilities = 'Maintenance' }
    }
    TranscriptDirectory = "$env:ProgramData\JEAConfiguration\Transcripts"
}

# Set up a folder for the Session Configuration files
if (-not (Test-Path "$env:ProgramData\JEAConfiguration"))
{
    New-Item -Path "$env:ProgramData\JEAConfiguration" -ItemType Directory
}

# Specify the name of the JEA endpoint
$sessionName = 'JEA_Demo'

if (Get-PSSessionConfiguration -Name $sessionName -ErrorAction SilentlyContinue)
{
    Unregister-PSSessionConfiguration -Name $sessionName -ErrorAction Stop
}

New-PSSessionConfigurationFile -Path "$env:ProgramData\JEAConfiguration\JEADemo.pssc" @JEAConfigParams

# Register the session configuration
Register-PSSessionConfiguration -Name $sessionName -Path "$env:ProgramData\JEAConfiguration\JEADemo.pssc"
```

## 啟用 PowerShell 模組記錄 (選擇性)
下列步驟可啟用系統上所有 PowerShell 動作的記錄。
您不需要啟用此設定就能執行 JEA，但此設定在 [JEA 上的報告](reporting-on-jea.md)一節中會很有用。

1. 開啟本機群組原則編輯器
2. 巡覽至 [電腦設定]\[系統管理範本]\[windows 元件]\[Windows PowerShell]
3. 按兩下 [開啟模組記錄]
4. 按一下 [啟用]
5. 在 [選項] 區段中，按一下模組名稱旁邊的 [顯示]
6. 在快顯視窗中輸入 "\*"。 這表示 PowerShell 將會記錄來自所有模組的命令。
7. 按一下 [確定] 並套用原則

注意︰您也可以透過 [群組原則] 啟用全系統 PowerShell 文字記錄。

**恭喜，您現在已設定電腦和示範端點，並準備好開始使用 JEA！**




<!--HONumber=Jul16_HO1-->


