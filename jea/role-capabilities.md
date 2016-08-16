---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "角色功能"
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: 81fd386d58576a8930093b4f18ce36a4ff6cecd0
ms.openlocfilehash: a3dd4a217f5b1fd80e97adf802c65073ca015bbc

---

# 角色功能

## 概觀
在上一節中，您學到 "RoleDefinitions" 欄位會定義哪些群組有權存取哪些角色功能。
您可能想知道：「什麼是角色功能？」
本節將會回答這個問題。  

## PowerShell 角色功能簡介
PowerShell 角色功能定義使用者在 JEA 端點執行「什麼」工作。
它會詳細列出可見命令、可見應用程式等項目的允許清單。
角色功能是由副檔名為 ".psrc" 的檔案定義。

## 角色功能內容
我們將從檢查及修改您先前使用的示範角色功能檔案開始。
假設您在環境中已部署自己的工作階段設定，但收到意見反應，指出您必須變更公開給使用者的功能。
操作員必須能夠重新啟動電腦，而且他們也想要能夠取得網路設定的相關資訊。
此外，安全性小組已告訴您，不接受在沒有任何限制的情況下允許使用者執行 "Restart-Service"。
您必須限制操作員可以重新啟動的服務。

若要進行這些變更，請先以系統管理員身分執行 PowerShell ISE，然後開啟下列檔案︰

```
C:\Program Files\WindowsPowerShell\Modules\Demo_Module\RoleCapabilities\Maintenance.psrc
```

現在在檔案中尋找並更新以下幾行︰

```PowerShell
# OLD: VisibleCmdlets = 'Restart-Service'
VisibleCmdlets = 'Restart-Computer',
                 @{
                     Name = 'Restart-Service'
                     Parameters = @{ Name = 'Name'; ValidateSet = 'Spooler' }
                 },
                 'NetTCPIP\Get-*'

# OLD: VisibleExternalCommands = 'Item1', 'Item2'
VisibleExternalCommands = 'C:\Windows\system32\ipconfig.exe'
```

這包含了一些有趣的範例︰

1.  您已限制 Restart-Service，讓操作員只能使用含 -Name參數的 Restart-Service，而且只能提供 "Spooler" 作為傳遞給該參數的引數。
如果需要，您也可以使用規則運算式，限制引數使用 "ValidatePattern"，而不是 "ValidateSet"。

2.  您使用了 "Get" 動詞命令，從 NetTCPIP 模組公開所有命令。
因為 "Get" 命令通常不會變更系統狀態，所以這是相對較安全的動作。
即便如此，還是強烈鼓勵您密切檢查透過 JEA 公開的每個命令。

3.  您使用了 VisibleExternalCommands 公開可執行檔 (ipconfig)。
您也可以使用此欄位來公開完整的 PowerShell 指令碼。
請務必提供外部命令的完整路徑，以確保不會改為執行置於使用者路徑中名稱類似 (且潛在惡意) 的程式。

儲存檔案，然後再次連線到示範端點以確認變更有效。

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEADemo2 -Credential $NonAdminCred
Get-Command
```
因為您只修改角色功能檔案，所以不需要重新登錄工作階段設定。
當使用者連線時，PowerShell 會自動尋找您更新的角色功能。
由於角色功能會在工作階段啟動時載入，因此現有的工作階段不會受到角色功能檔案更新的影響。

現在，確認您可以執行 Restart-Computer 並提供 -WhatIf 參數來重新啟動電腦 (除非您真的想要重新啟動電腦)。

```PowerShell
Restart-Computer -WhatIf
```

確認您可以執行 "ipconfig"

```PowerShell
ipconfig
```

最後，確認 Restart-Service 僅適用於多工緩衝處理器服務。

```PowerShell
Restart-Service Spooler # This should work
Restart-Service WSearch # This should fail
```

完成時，結束工作階段。

```PowerShell
Exit-PSSession
```

## 建立角色功能
在下一節中，您將為 AD 技術支援使用者建立 JEA 端點。
為了準備，我們將針對該節建立要填入的空白角色功能檔案。
角色功能必須在有效 PowerShell 模組的 "RoleCapabilities" 資料夾中建立，才能在工作階段啟動時進行解析。

PowerShell 模組基本上是 PowerShell 功能的套件，
可包含 PowerShell 函式、Cmdlet、DSC 資源、角色功能等等。
您可以在 PowerShell 主控台中執行 `Get-Help about_Modules`，來尋找模組的相關資訊。

若要使用空白角色功能檔案建立新的 PowerShell 模組，請執行下列命令︰  

```PowerShell
# Create a new folder for the module.
New-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module' -ItemType Directory

# Add a module manifest to contain metadata for this module.
New-ModuleManifest -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\Contoso_AD_Module.psd1' -RootModule Contoso_AD_Module.psm1

# Create a blank script module. You'll use this for custom functions in the next section.
New-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\Contoso_AD_Module.psm1' -ItemType File

# Create a RoleCapabilities folder in the Contoso_AD_Module folder. PowerShell expects Role Capabilities to be located in a "RoleCapabilities" folder within a module.
New-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\RoleCapabilities' -ItemType Directory

# Create a blank Role Capability in your RoleCapabilities folder. Running this command without any additional parameters just creates a blank template.
New-PSRoleCapabilityFile -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\RoleCapabilities\ADHelpDesk.psrc'
```

恭喜，您已建立空白角色功能檔案。
下一節將使用此檔案。

## 重要概念
**角色功能 (.psrc)**：定義使用者在 JEA 端點執行「哪些」工作的檔案。
它會詳細列出可見命令、可見主控台應用程式等項目的允許清單。
為了讓 PowerShell 偵測角色功能，您必須將其放在有效 PowerShell 模組的 "RoleCapabilities" 資料夾中。

**PowerShell 模組**：PowerShell 功能的套件，
可包含 PowerShell 函式、Cmdlet、DSC 資源、角色功能等等。
若要自動載入，PowerShell 模組必須位於 `$env:PSModulePath` 中的路徑下。




<!--HONumber=Jul16_HO1-->


