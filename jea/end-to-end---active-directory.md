---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "端對端   Active Directory"
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: 5954eb797df43de6f132a434ecad7049ee0221fb
ms.openlocfilehash: 204909c16d5e3e2099f6ba4247929d61445cd654

---

# 端對端 - Active Directory
假設您的程式範圍已增加。
您現在有責任將 JEA 加入網域控制站，以執行 Active Directory 動作。
技術支援人員將使用 JEA 解除鎖定帳戶、重設密碼，以及執行其他類似動作。

您必須將一組全新的命令公開給一組不同的人員。
除此之外，您還必須公開許多現有的 Active Directory 指令碼。
本節將逐步引導您撰寫這項工作所需的工作階段設定和角色功能。

## 必要條件
為了逐步進行本節，您必須在網域控制站上執行。
如果您無權存取網域控制站，別擔心。
請針對您熟悉的一些其他案例或角色執行，並嘗試跟著做。
如果您要快速地設定新的網域控制站，請參閱附錄：[建立網域控制站](#creating-a-domain-controller)。

## 建立新的角色功能和工作階段設定的步驟

建立新的角色功能乍看之下可能令人卻步，但這項作業可以分成幾個相當簡單的步驟︰

1.  識別您必須啟用的工作
2.  視需要限制這些工作
3.  確認這些工作適用於 JEA
4.  將這些工作放在角色功能檔案中
5.  登錄公開該角色功能的工作階段設定

## 步驟 1︰識別必須公開的內容
建立新的角色功能或工作階段設定之前，您必須識別使用者需要透過 JEA 端點執行的所有工作，以及如何透過 PowerShell 來執行這些工作。
這涉及相當大量的需求收集和研究。
您進行此處理程序的方式將取決於您的組織和目標。
請注意，需求收集和研究在真實世界的處理程序中是不可或缺的一部分。
這可能是採用 JEA 的過程中最困難的步驟。

### 尋找資源
以下是研究如何建立 Active Directory 管理端點時可參閱的一組線上資源︰
-   [Active Directory PowerShell Overview (Active Directory PowerShell 概觀)](http://blogs.msdn.com/b/adpowershell/archive/2009/03/05/active-directory-powershell-overview.aspx)
-   [CMD to PowerShell Guide for Active Directory (適用於 Active Directory 的 CMD 到 PowerShell 指南)](http://blogs.technet.com/b/ashleymcglone/archive/2013/01/02/free-download-cmd-to-powershell-guide-for-ad.aspx)

### 建立清單
以下是您將在本節其餘部分執行的一組十個動作。
請記住，這只是範例，您的組織需求可能不同︰

|動作                                                         |PowerShell 命令                                             |
|---------------------------------------------------------------|---------------------------------------------------------------|
|解除鎖定帳戶                                                 |`Unlock-ADAccount`                                             |
|密碼重設                                                 |`Set-ADAccountPassword` 與 `Set-ADUser -ChangePasswordAtLogon`|
|變更使用者的職稱                                          |`Set-ADUser -Title`                                            |  
|尋找已鎖定、已停用、非作用中等 AD 帳戶 |`Search-ADAccount`                                             |
|新增使用者至群組                                              |`Add-ADGroupMember -Identity (with whitelist) -Members`        |
|從群組中移除使用者                                         |`Remove-ADGroupMember -Identity (with whitelist) -Members`     |
|啟用使用者帳戶                                          |`Enable-ADAccount`                                             |
|停用使用者帳戶                                         |`Disable-ADAccount`                                            |

## 步驟 2：視需要限制工作

現在您已有動作清單，您必須仔細思考每個命令的功能。
這樣做有兩個重要原因︰

1.  這樣很容易提供使用者超出預計的功能。
例如，`Set-ADUser` 是非常強大且彈性的命令。
您可能不想要向技術支援使用者公開它可以執行的所有工作。  

2.  更糟的是，您可能公開允許使用者擺脫 JEA 限制的命令。
如果發生這種情況，JEA 會停止作為安全性界限。
請小心選取命令。
例如，Invoke-Expression 可讓使用者執行不受限制的程式碼。
如需本主題的更多討論，請參閱＜限制命令時的考量＞一節。

檢閱每個命令之後，您決定做出下列限制︰

1.  `Set-ADUser` 只能搭配 -Title 參數執行

2.  `Add-ADGroupMember` 和 `Remove-ADGroupMember` 只能用於特定群組

### 步驟 3：確認這些工作適用於 JEA
在限制的 JEA 環境中可能無法直接實際使用這些 Cmdlet。
JEA 會在 *NoLanguage* 模式下執行，以防止使用者使用變數。
為了確保使用者有流暢的體驗，請務必檢查一些事項。

例如，請考慮 `Set-ADAccountPassword`。
-NewPassword 參數需要安全字串。
通常，使用者會建立安全字串並傳入作為變數 (如下所示)︰

```PowerShell
$newPassword = Read-Host -Prompt "Specify a new password" -AsSecureString
Set-ADAccountPassword -Identity mollyd -NewPassword $newPassword -Reset
```

不過，*NoLanguage* 模式會防止使用變數。
您可以透過兩個方式來解決這項限制︰

1.  您可以要求使用者執行命令，而不指派變數。
這設定起來很容易，但對於使用端點的操作員可能很麻煩。
誰會想要在您每次重設密碼時輸入此命令？
```PowerShell
Set-ADAccountPassword -Identity mollyd -NewPassword (Read-Host -Prompt "Specify a new password" -AsSecureString) -Reset
```

2.  您可以透過公開給使用者的指令碼或函式來掩飾此複雜性。
您公開的指令碼和函式會在不受限制的內容中執行；您可以撰寫函式來使用變數並呼叫其他命令，而不會發生任何問題。
這種方法簡化了使用者體驗、避免發生錯誤、減少所需的 PowerShell 知識，並降低不小心公開過多功能的情況。
唯一的缺點就是撰寫和維護函式的成本。

### 題外話：新增函式至模組
您將採取第二個方法，撰寫稱為 `Reset-ContosoUserPassword` 的 PowerShell 函式。
此函式將會執行重設使用者的密碼時所需進行的所有作業。
在您的組織中，這可能涉及執行精密複雜的作業。
因為這只是範例，所以您的命令只會重設密碼，並要求使用者在登入時變更密碼。
我們會將它放入您在最後一節中所建立的 Contoso_AD_Module 模組。

1. 在 PowerShell ISE 中，開啟 "Contoso_AD_Module.psm1"
```PowerShell
ise 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\Contoso_AD_Module.psm1'
```

2. 按 Crtl+J 開啟程式碼片段功能表。

3. 按向下鍵直到您找到 [函式]，然後按 Enter 鍵。
這會為函式建立非常基本的架構。

4. 將函式重新命名為 "Reset-ContosoUserPassword"。  

5. 將其中一個參數重新命名為 "Identity"，並刪除第二個參數。

6. 將下列內容複製到函式主體。
```PowerShell
# Get the new password
$NewPassword = Read-Host -Prompt "Enter a new password" -AsSecureString
# Reset the password
Set-ADAccountPassword -Identity $Identity -NewPassword $NewPassword -Reset
# Require the user to reset at next logon
Set-ADUser -Identity $Identity -ChangePasswordAtLogon
```

7. 儲存檔案。
最後的結果應該如下所示︰
```PowerShell
function Reset-ContosoUserPassword ($Identity)
{
# Get the new password
$NewPassword = Read-Host -Prompt "Enter a new password" -AsSecureString
# Reset the password
Set-ADAccountPassword -Identity $Identity -NewPassword $NewPassword -Reset
# Require the user to reset at next logon
Set-ADUser -Identity $Identity -ChangePasswordAtLogon
}
```
現在，您的使用者只要呼叫 `Reset-ContosoUserPassword`，就能建立內嵌安全字串，而不需要記住此語法。

## 步驟 4：編輯角色功能檔案
在[建立角色功能](#role-capability-creation)一節中，您已建立空白角色功能檔案。
在本節中，您將在該檔案中填入值。

首先在 PowerShell ISE 中開啟角色功能檔案。
```PowerShell
ise 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\RoleCapabilities\ADHelpDesk.psrc'
```
以下列變更更新檔案：
```PowerShell
# OLD: VisibleCmdlets = 'Invoke-Cmdlet1', @{ Name = 'Invoke-Cmdlet2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }
VisibleCmdlets =
    'Unlock-ADAccount',
    'Search-ADAccount',
    'Enable-ADAccount',
    'Disable-ADAccount',
    @{ Name = 'Set-ADUser'; Parameters = @{ Name = 'Title'; ValidateSet = 'Manager', 'Engineer' }},
    @{ Name = 'Add-ADGroupMember'; Parameters =
        @{Name = 'Identity'; ValidateSet = 'TestGroup'},
        @{Name = 'Members'}},
    @{ Name = 'Remove-ADGroupMember'; Parameters =
        @{Name = 'Identity'; ValidateSet = 'TestGroup'},
        @{Name = 'Members'}}

# OLD: VisibleFunctions = 'Invoke-Function1', @{ Name = 'Invoke-Function2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }
VisibleFunctions = 'Reset-ContosoUserPassword'
```

上述變更有一些注意事項︰
1.  PowerShell 會嘗試自動載入您的角色功能所需的模組。
如果您注意到模組發生未自動載入的問題，您可能必須在 "ModulesToImport" 欄位中明確地列出模組名稱。

2.  如果您不確定命令是 Cmdlet 或函式，請執行 `Get-Command` 並查看 "CommandType" 屬性。

3.  如果定義一組允許的值並不容易，則 ValidatePattern 可讓您使用規則運算式來限制參數引數。
您無法對單一參數同時定義 ValidatePattern 和 ValidateSet。

## 步驟 5：登錄新的工作階段設定
接下來，您將建立新的工作階段設定檔，該檔案會向 "JEA_NonAdmin_HelpDesk" AD 群組的成員公開您的角色功能。

首先在 PowerShell ISE 中建立及開啟新的空白工作階段設定檔。
```PowerShell
New-PSSessionConfigurationFile -Path "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc"
ise "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc"
```
修改 PSSC 檔案中的下列欄位。
如果您在自己的環境中執行，則應該以您自己的非系統管理員使用者或群組取代 "CONTOSO\JEA_NonAdmins_Helpdesk"。
```PowerShell
# OLD: Description = ''
Description = 'An endpoint for Active Directory tasks.'

# OLD: SessionType = 'Default'
SessionType = 'RestrictedRemoteServer'

# OLD: TranscriptDirectory = 'C:\Transcripts\'
TranscriptDirectory = "C:\ProgramData\JEAConfiguration\Transcripts"

# OLD: RunAsVirtualAccount = $true
RunAsVirtualAccount = $true

# OLD: RoleDefinitions = @{ 'CONTOSO\SqlAdmins' = @{ RoleCapabilities = 'SqlAdministration' }; 'CONTOSO\ServerMonitors' = @{ VisibleCmdlets = 'Get-Process' } }
RoleDefinitions = @{ 'CONTOSO\JEA_NonAdmin_HelpDesk' = @{ RoleCapabilities =  'ADHelpDesk' }}
```
儲存並登錄工作階段設定
```PowerShell
Register-PSSessionConfiguration -Name ADHelpDesk -Path "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc"
```
## 測試看看！
取得您的非系統管理員使用者認證︰
```PowerShell
$HelpDeskCred = Get-Credential
```
如果您遵循[設定使用者和群組](creating-a-domain-controller.md#set-up-users-and-groups)一節進行，則認證會是︰
-   使用者名稱 = "HelpDeskUser"
-   密碼 = "pa$$w0rd"

使用非系統管理員認證從遠端登入 AD 技術支援端點︰
```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName ADHelpDesk -Credential $HelpDeskCred
```
使用 Set-ADUser 重設使用者的職稱。
```PowerShell
Set-ADUser -Identity OperatorUser -Title Engineer
```
確認標題已變更。
```PowerShell
Get-ADUser -Identity OperatorUser -Property Title
```
現在，使用 Add-ADGroupMember 將新增使用者至 TestGroup。
注意︰請確定您已事先建立 TestGroup。
```PowerShell
Add-ADGroupMember TestGroup -Member OperatorUser -Verbose
```
結束工作階段︰
```PowerShell
Exit-PSSession
```
## 重要概念
**NoLanguage 模式**：當 PowerShell 在 "NoLanguage" 模式時，使用者只能執行命令，而不能使用任何語言項目。
如需詳細資訊，請執行 `Get-Help about_Language_Modes`。

**PowerShell 函式**：PowerShell 函式是您可以透過名稱呼叫的 PowerShell 程式碼片段。
如需詳細資訊，請執行 `Get-Help about_Functions`。

**ValidateSet/ValidatePattern**︰公開命令時，您可以限制特定參數的有效引數。
ValidateSet 是有效引數的特定清單。
ValidatePattern 是該參數引數必須符合的規則運算式。




<!--HONumber=Jul16_HO1-->


