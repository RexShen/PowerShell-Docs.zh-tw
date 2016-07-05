---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "重現示範端點"
ms.technology: powershell
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: dabb5023012e90ace3fbc5f347c17821abd92595

---

# 重現示範端點
在本節中，您將了解如何產生您在上一節中所使用之示範端點的相同複本。
本節將介紹了解 JEA 所需的核心概念，包括 PowerShell 工作階段設定和角色功能。

## PowerShell 工作階段設定
當您在上一節中使用 JEA 時，首先會執行下列命令︰

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEA_Demo -Credential $NonAdminCred
```

其中大部分參數一目了然，但 *ConfigurationName* 參數乍看之下可能令人混淆。
該參數指定您要連線的 PowerShell 工作階段設定。

*PowerShell 工作階段設定*是 PowerShell 端點的複雜說法。
這是使用者連線並存取 PowerShell 功能的象徵性「位置」。
根據您設定工作階段設定的方式，它可提供不同的功能給連線使用者。
針對 JEA，我們使用工作階段設定將 PowerShell 限制在一組有限的功能，並以特殊權限虛擬帳戶身分執行。

您的電腦上已經登錄數個 PowerShell 工作階段設定，每個設定的設定方式稍有不同。
這些設定大部分隨附於 Windows，但 "JEA_Demo" 工作階段設定則是在[必要條件](prerequisites.md)一節中所設定。
您可以在系統管理員的 PowerShell 提示字元中執行下列命令，來查看所有登錄的工作階段設定︰

```PowerShell
Get-PSSessionConfiguration
```

## PowerShell 工作階段設定檔
您可以登錄新的 *PowerShell 工作階段設定檔*，來建立新的工作階段設定。
工作階段設定檔的副檔名為 ".pssc"。
您可以使用 New-PSSessionConfigurationFile Cmdlet 產生工作階段設定檔。

接下來，您將為 JEA 建立並登錄新的工作階段設定。

## 產生及修改您的 PowerShell 工作階段設定
執行下列命令，產生 PowerShell 工作階段設定「基本架構」檔案。

```PowerShell
New-PSSessionConfigurationFile -Path "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

> **提示**︰此基本架構檔案預設只會包含最常見的組態設定。
> 使用 `-Full` 參數可將所有適用的設定加入產生的 PSSC。

在 PowerShell ISE 或您偏好的文字編輯器中開啟檔案。

```PowerShell
ise "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

將檔案中的下列欄位更新為底下的值 (記得在您自己的非系統管理員安全性群組中進行取代)︰

```PowerShell
# OLD: SessionType = 'Default'
SessionType = 'RestrictedRemoteServer'

# OLD: TranscriptDirectory = 'C:\Transcripts\'
TranscriptDirectory = "C:\ProgramData\JEAConfiguration\Transcripts"

# OLD: # RunAsVirtualAccount = $true
RunAsVirtualAccount = $true

# OLD: RoleDefinitions = @{ 'CONTOSO\SqlAdmins' = @{ RoleCapabilities = 'SqlAdministration' }; 'CONTOSO\ServerMonitors' = @{ VisibleCmdlets = 'Get-Process' } }
RoleDefinitions = @{'CONTOSO\JEA_NonAdmin_Operator' = @{ RoleCapabilities =  'Maintenance' }}
```

以下是每個項目所代表的意義︰

1.  *SessionType* 欄位定義預設要用於此端點的預設值。
*RestrictedRemoteServer* 定義遠端管理所需的最低設定。
根據預設，*RestrictedRemoteServer* 端點會公開 Get-Command、Get-FormatData、Select-Object、Get-Help、Measure-Object、Exit-PSSession、Clear-Host 和 Out-Default。
它會將 *ExecutionPolicy* 設定為 *RemoteSigned*，並將 *LanguageMode* 設定為 *NoLanguage*。
這些設定的唯一作用是提供安全且最基本的起點，以便設定您的端點。

2.  *RoleDefinitions* 欄位將角色功能指派給特定群組。
它會定義誰可以特殊權限帳戶身分執行什麼工作。
您可以使用此欄位，根據群組成員資格指定任何連線使用者可以使用的功能。
這是 JEA RBAC 功能的核心。
在此範例中，您將對 "Contoso\JEA_NonAdmin_Operator" 群組的成員公開預製的「示範」RoleCapability。

3.  *RunAsVirtualAccount* 欄位指出 PowerShell 應該以此端點的虛擬帳戶身分執行。
根據預設，虛擬帳戶是內建 Administrator 群組的成員。
在網域控制站上，它預設也是 Domain Administrators 群組的成員。
稍後在本指南中，您將了解如何自訂虛擬帳戶的權限。

4.  *TranscriptDirectory* 欄位定義 "Over-The-Shoulder" PowerShell 文字記錄在每個遠端工作階段之後的儲存位置。
這些文字記錄讓您能夠以容易閱讀的方式，來查看在每個工作階段中執行的動作。
如需 PowerShell 文字記錄的詳細資訊，請參閱這篇[部落格文章](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx)。
注意︰定期的 Windows Eventing 也會擷取每位使用者使用 PowerShell 執行的相關資訊。
只不過文字記錄稍微更容易閱讀。

最後，將變更儲存至 *JEADemo2.pssc*。

## 套用 PowerShell 工作階段設定

若要從工作階段設定檔建立端點，您必須登錄該檔案。
這需要幾項資訊︰

1. 工作階段設定檔的路徑。
2. 登錄的工作階段設定名稱。 這是使用者使用 `Enter-PSSession` 或 `New-PSSession` 連線到您的端點時，提供給 "ConfigurationName" 參數的相同名稱。

若要登錄本機電腦上的工作階段設定，請執行下列命令︰

```PowerShell
Register-PSSessionConfiguration -Name 'JEADemo2' -Path "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

恭喜您！ 您已設定 JEA 端點。

## 測試您的端點
對您的新端點重新執行[使用 JEA](using-jea.md)一節中所列的步驟，確認端點如預期般運作。
提供設定名稱給 Enter-PSSession 時，請務必使用新的端點名稱 (JEADemo2)。

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEADemo2 -Credential $NonAdminCred
```

## 重要概念
**PowerShell 工作階段設定**︰有時稱為 *PowerShell 端點*，這是使用者連線並存取 PowerShell 功能的象徵性「位置」。
您可以執行 `Get-PSSessionConfiguration`，列出系統上已登錄的工作階段設定。
以特定方式設定時，PowerShell 工作階段設定可稱為 *JEA 端點*。

**PowerShell 工作階段設定檔 (.pssc)**︰此檔案經登錄後，可定義 PowerShell 工作階段設定的設定。
它會包含可連線到端點的使用者角色、「執行身分」虛擬帳戶等規格。     

**角色定義**︰工作階段設定檔中的欄位，定義授與連線使用者的角色功能。
它會定義*誰*可以特殊權限帳戶身分執行*什麼*工作。
這是 JEA RBAC 功能的核心。

**SessionType**：工作階段設定檔中的欄位，表示工作階段設定的預設值。
針對 JEA 端點，這必須設定為 RestrictedRemoteServer。

**PowerShell 文字記錄**︰包含 PowerShell 工作階段之 "Over-The-Shoulder" 檢視的檔案。
您可以將 PowerShell 設定為使用 TranscriptDirectory 欄位來產生 JEA 工作階段的文字記錄。
如需文字記錄的詳細資訊，請參閱這篇[部落格文章](https://technet.microsoft.com/en-us/magazine/ff687007.aspx)。




<!--HONumber=Jun16_HO4-->


