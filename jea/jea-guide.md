# Just Enough Administration (JEA)：簡介

## 目錄
閱讀本文之後，您應該能夠撰寫、部署、使用、維護及稽核 Just Enough Administration (JEA) 部署。
以下是本入門指南涵蓋的主題︰

1.  [簡介](#introduction)︰簡短回顧您應該重視 JEA 的原因

2.  [必要條件](#prerequisites)：設定您的環境

3.  [使用 JEA](#using-jea)︰從了解使用 JEA 的操作員體驗開始

4.  [重現示範](#remake-the-demo-endpoint)︰從頭開始建立 JEA 工作階段設定

5.  [角色功能](#role-capabilities)︰了解如何使用角色功能檔案來自訂 JEA 功能

6.  [端對端 - Active Directory](#end-to-end---active-directory)︰建立全新的端點以管理 Active Directory

7.  [多電腦部署和維護](#multi-machine-deployment-and-maintenance)︰探索部署和撰寫如何隨規模變更

8.  [JEA 上的報告](#reporting-on-jea)︰探索如何對所有 JEA 動作和基礎結構進行稽核與報告

9.  [附錄](#appendix)︰重要技能和討論重點

## 簡介

### 動機
當您將系統的特殊權限存取授與某人時，就是將您的信任界限延伸到該人員。
這會帶來風險，因為系統管理員是受攻擊面。
內部攻擊和認證遭竊是常見的真實情況。

這不是新問題。
您可能很熟悉最低權限原則，並可能透過應用程式使用其提供的某種角色型存取控制 (RBAC)。
不過，這些解決方案的效率和管理能力通常因其廣泛的範圍和不精確而受到限制。
此外，RBAC 涵蓋範圍也有間隙。
例如，在 Windows 中，特殊權限存取主要是二元切換參數，迫使您在將使用者加入 Administrators 群組時，授與不必要的權限。

Just Enough Administration (JEA) 透過 PowerShell 遠端提供 RBAC 平台。
*它可讓特定使用者在伺服器上執行特定管理工作，而不需要授與系統管理員權限。*
這可讓您填滿現有 RBAC 解決方案的間隙，並簡化這些設定的管理工作。

## 必要條件

### 初始狀態
開始本節之前，請確認下列事項︰

1. 系統上有 JEA 可用。 如需目前支援的作業系統和所需的下載項目，請參閱[讀我檔案](./README.md)。
2. 您在要試用 JEA 的電腦上具有系統管理權限。
3. 電腦已加入網域。
請參閱[建立網域控制站](#creating-a-domain-controller)一節，以快速在伺服器上設定新的網域 (如果還沒有)。

### 啟用 PowerShell 遠端
JEA 管理是透過 PowerShell 遠端進行。
在系統管理員的 PowerShell 視窗中執行下列命令，以確保這項功能已啟用且正確設定︰

```PowerShell
Enable-PSRemoting 
```

如果您不熟悉 PowerShell 遠端，建議執行 `Get-Help about_Remote` 來了解此重要的基本概念。

### 識別您的使用者或群組
為了示範 JEA 的操作方式，您必須識別要在本指南中使用的非系統管理員使用者和群組。
  
如果您使用現有的網域，請識別或建立一些非特殊權限使用者和群組。
您將授與 JEA 的非系統管理員存取權。
每當您看到 `$NonAdministrator` 變數出現在指令碼頂端，請將它指派給您選取的非系統管理員使用者或群組。 

如果您從頭開始建立新的網域，會比較容易。
請使用附錄中的[設定使用者和群組](#set-up-users-and-groups)一節，來建立非系統管理員使用者和群組。
`$NonAdministrator` 的預設值會是在該節中建立的群組。

### 設定維護角色功能檔案
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
  
### 建立及登錄示範工作階段設定檔
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
 
### 啟用 PowerShell 模組記錄 (選擇性)
下列步驟可啟用系統上所有 PowerShell 動作的記錄。
您不需要啟用此設定就能執行 JEA，但此設定在 [JEA 上的報告](#reporting-on-jea)一節中會很有用。

1. 開啟本機群組原則編輯器
2. 巡覽至 [電腦設定]\[系統管理範本]\[windows 元件]\[Windows PowerShell]
3. 按兩下 [開啟模組記錄]
4. 按一下 [啟用]
5. 在 [選項] 區段中，按一下模組名稱旁邊的 [顯示]
6. 在快顯視窗中輸入 "*"。 這表示 PowerShell 將會記錄來自所有模組的命令。
7. 按一下 [確定] 並套用原則

注意︰您也可以透過 [群組原則] 啟用全系統 PowerShell 文字記錄。

**恭喜，您現在已設定電腦和示範端點，並準備好開始使用 JEA！**

## 使用 JEA
本節主要在於了解*使用 JEA* 的使用者體驗。
在＜必要條件＞一節中，您已建立一個 JEA 端點示範。
我們將使用此示範來說明 JEA 的操作方式。
在稍後的章節中，本指南會回頭介紹讓該使用者體驗變成可能的動作和檔案。

### 以非系統管理員身分使用 JEA
為了示範 JEA 的操作方式，您必須以非系統管理員使用者身分使用 PowerShell 遠端。
在新的 PowerShell 視窗中執行下列命令：   

```PowerShell
$NonAdminCred = Get-Credential
```

當出現提示時，輸入非系統管理員帳戶的認證。
如果您遵循[設定使用者和群組](#set-up-users-and-groups)一節進行，則會是︰
-   使用者名稱 = "OperatorUser"
-   密碼 = "pa$$w0rd"

接下來，執行下列命令，使用您提供的認證連線到示範端點︰

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEA_Demo -Credential $NonAdminCred 
```

您現在已輸入本機電腦上的互動式遠端 PowerShell 工作階段。 藉由使用 "Credential" 參數，即可*像是* OperatorUser (或您使用的任何帳戶) 進行連線。
提示 `[localhost]: PS>` 的變更表示您正在對遠端工作階段執行。  

在遠端命令提示字元中執行下列命令，以顯示您可以使用的命令︰

```PowerShell
Get-Command 
```

如您所見，這是一般 PowerShell 視窗 (通常可包含數千個命令) 中非常有限的一小組可用命令。
具體來說，它只會顯示 7 個預設 JEA Cmdlet (Clear-Host、Exit-PSSession、Get-Command、Get-FormatData、Get-Help、Measure-Object、Out-Default、Select-Object)，以及兩個明確包含在維護角色功能檔案中的命令。

接下來，讓我們看看此工作階段執行所在的使用者內容，方法是叫用包含在維護角色功能檔案中的自訂函式︰

```PowerShell
Get-UserInfo
```
 
此函式的輸出顯示 "ConnectedUser" 及 "RunAsUser"。
已連線的使用者是連線到遠端工作階段的帳戶 (例如您的帳戶)。
已連線的使用者不需要具有系統管理員權限。
「執行身分」帳戶是實際執行特殊權限動作的帳戶。
以一位使用者的身分連線，並以特殊權限使用者身分執行，我們可以允許非特殊權限使用者執行特定的管理工作，而不需要授與系統管理權限。

若要示範其操作方式，請執行下列命令︰

```PowerShell
Restart-Service -Name Spooler -Verbose
```

一般而言，Restart-Service 需要系統管理員權限才能執行。
不過，透過 JEA 虛擬帳戶，我們就可以使用非特殊權限認證來執行。

因此，JEA 可讓您使用已在使用的命令來完成工作。
但您*不應該*使用的命令又如何？
請嘗試在 JEA 工作階段中執行不同的命令，例如 `Restart-Computer`，並注意 JEA 如何防止這類命令被執行。

```PowerShell
[localhost]: PS> Restart-Computer
The term 'Restart-Computer' is not recognized as the name of a cmdlet, function, script file, or
operable program. Check the spelling of the name, or if a path was included, verify that the path
is correct and try again.
    + CategoryInfo          : ObjectNotFound: (Restart-Computer:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException 
```

最後，若要離開 JEA 限制端點，請執行下列命令︰

```PowerShell
Exit-PSSession
```

這會中斷您與遠端 PowerShell 工作階段的連線。

## 重現示範端點
在本節中，您將了解如何產生您在上一節中所使用之示範端點的相同複本。
本節將介紹了解 JEA 所需的核心概念，包括 PowerShell 工作階段設定和角色功能。 

### PowerShell 工作階段設定
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
這些設定大部分隨附於 Windows，但 "JEA_Demo" 工作階段設定則是在[必要條件](#prerequisites)一節中所設定。
您可以在系統管理員的 PowerShell 提示字元中執行下列命令，來查看所有登錄的工作階段設定︰

```PowerShell
Get-PSSessionConfiguration
```

### PowerShell 工作階段設定檔
您可以登錄新的 *PowerShell 工作階段設定檔*，來建立新的工作階段設定。
工作階段設定檔的副檔名為 ".pssc"。
您可以使用 New-PSSessionConfigurationFile Cmdlet 產生工作階段設定檔。

接下來，您將為 JEA 建立並登錄新的工作階段設定。 

### 產生及修改您的 PowerShell 工作階段設定
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
*RestrictedRemoteServer* 定義遠端管理所需的最低設定。 根據預設，*RestrictedRemoteServer* 端點會公開 Get-Command、Get-FormatData、Select-Object、Get-Help、Measure-Object、Exit-PSSession、Clear-Host 和 Out-Default。
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

### 套用 PowerShell 工作階段設定 

若要從工作階段設定檔建立端點，您必須登錄該檔案。
這需要幾項資訊︰

1. 工作階段設定檔的路徑。
2. 登錄的工作階段設定名稱。 這是使用者使用 `Enter-PSSession` 或 `New-PSSession` 連線到您的端點時，提供給 "ConfigurationName" 參數的相同名稱。

若要登錄本機電腦上的工作階段設定，請執行下列命令︰

```PowerShell
Register-PSSessionConfiguration -Name 'JEADemo2' -Path "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

恭喜您！ 您已設定 JEA 端點。

### 測試您的端點
對您的新端點重新執行[使用 JEA](#using-jea)一節中所列的步驟，確認端點如預期般運作。
提供設定名稱給 Enter-PSSession 時，請務必使用新的端點名稱 (JEADemo2)。

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEADemo2 -Credential $NonAdminCred
```

### 重要概念
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

## 角色功能

### 概觀
在上一節中，您學到 "RoleDefinitions" 欄位會定義哪些群組有權存取哪些角色功能。
您可能想知道：「什麼是角色功能？」
本節將會回答這個問題。  

## PowerShell 角色功能簡介
PowerShell 角色功能定義使用者在 JEA 端點執行「什麼」工作。
它會詳細列出可見命令、可見應用程式等項目的白名單。
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

3.  您使用了 VisibleExternalCommands 來公開一個可執行檔 (ipconfig)。
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

### 建立角色功能
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

# Create a RoleCapabilities folder in the AD_Module folder. PowerShell expects Role Capabilities to be located in a "RoleCapabilities" folder within a module.
New-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\RoleCapabilities' -ItemType Directory

# Create a blank Role Capability in your RoleCapabilities folder. Running this command without any additional parameters just creates a blank template.
New-PSRoleCapabilityFile -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\RoleCapabilities\ADHelpDesk.psrc' 
```

恭喜，您已建立空白角色功能檔案。
下一節將使用此檔案。

### 重要概念
**角色功能 (.psrc)**：定義使用者在 JEA 端點執行「什麼」工作的檔案。
它會詳細列出可見命令、可見主控台應用程式等項目的白名單。
為了讓 PowerShell 偵測角色功能，您必須將其放在有效 PowerShell 模組的 "RoleCapabilities" 資料夾中。

**PowerShell 模組**：PowerShell 功能的套件，
可包含 PowerShell 函式、Cmdlet、DSC 資源、角色功能等等。
若要自動載入，PowerShell 模組必須位於 `$env:PSModulePath` 中的路徑下。 

## 端對端 - Active Directory
假設您的程式範圍已增加。
您現在有責任將 JEA 加入網域控制站，以執行 Active Directory 動作。
技術支援人員將使用 JEA 解除鎖定帳戶、重設密碼，以及執行其他類似動作。

您必須將一組全新的命令公開給一組不同的人員。
除此之外，您還必須公開許多現有的 Active Directory 指令碼。
本節將逐步引導您撰寫這項工作所需的工作階段設定和角色功能。

### 必要條件
為了逐步進行本節，您必須在網域控制站上執行。
如果您無權存取網域控制站，別擔心。
請針對您熟悉的一些其他案例或角色執行，並嘗試跟著做。
如果您要快速地設定新的網域控制站，請參閱附錄：[建立網域控制站](#creating-a-domain-controller)。

### 建立新的角色功能和工作階段設定的步驟

建立新的角色功能乍看之下可能令人卻步，但這項作業可以分成幾個相當簡單的步驟︰

1.  識別您必須啟用的工作
2.  視需要限制這些工作
3.  確認這些工作適用於 JEA
4.  將這些工作放在角色功能檔案中
5.  登錄公開該角色功能的工作階段設定

### 步驟 1︰識別必須公開的內容
建立新的角色功能或工作階段設定之前，您必須識別使用者需要透過 JEA 端點執行的所有工作，以及如何透過 PowerShell 來執行這些工作。
這涉及相當大量的需求收集和研究。
您進行此處理程序的方式將取決於您的組織和目標。
請注意，需求收集和研究在真實世界的處理程序中是不可或缺的一部分。
這可能是採用 JEA 的過程中最困難的步驟。

#### 尋找資源
以下是研究如何建立 Active Directory 管理端點時可參閱的一組線上資源︰
-   [Active Directory PowerShell Overview (Active Directory PowerShell 概觀)](http://blogs.msdn.com/b/adpowershell/archive/2009/03/05/active-directory-powershell-overview.aspx) 
-   [CMD to PowerShell Guide for Active Directory (適用於 Active Directory 的 CMD 到 PowerShell 指南)](http://blogs.technet.com/b/ashleymcglone/archive/2013/01/02/free-download-cmd-to-powershell-guide-for-ad.aspx)

#### 建立清單
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

### 步驟 2：視需要限制工作

現在您已有動作清單，您必須仔細思考每個命令的功能。
這樣做有兩個重要原因︰

1.  您很容易提供比預期更多的功能給使用者。
例如，`Set-ADUser` 是非常強大且彈性的命令。
您可能不想要向技術支援使用者公開它可以執行的所有工作。  

2.  更糟的是，您可能公開允許使用者擺脫 JEA 限制的命令。
如果發生這種情況，JEA 會停止作為安全性界限。
請小心選取命令。
例如，Invoke-Expression 可讓使用者執行不受限制的程式碼。
如需本主題的更多討論，請參閱＜限制命令時的考量＞一節。

檢閱每個命令之後，您決定做出下列限制︰

1.  `Set-ADUser` 只能搭配 "-Title" 參數執行 

2.  `Add-ADGroupMember` 和 `Remove-ADGroupMember` 只能用於特定群組

### 步驟 3：確認這些工作適用於 JEA
在限制的 JEA 環境中可能無法直接實際使用這些 Cmdlet。
此外，JEA 會在 *NoLanguage* 模式下執行，以防止使用者使用變數。
為了確保使用者有流暢的體驗，請務必檢查一些事項。

例如，請考慮 `Set-ADAccountPassword`。
"-NewPassword" 參數需要安全字串。
通常，使用者會建立安全字串並傳入作為變數 (如下所示)︰

```PowerShell
$newPassword = (Read-Host -Prompt "Specify a new password" -AsSecureString)
Set-ADAccountPassword -Identity mollyd -NewPassword $newPassword -Reset
```

不過，NoLanguage 模式會防止使用變數。
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

#### 題外話：新增函式至模組
您將採取第二個方法，撰寫稱為 `Reset-ContosoUserPassword` 的 PowerShell 函式。
此函式將會執行重設使用者的密碼時所需進行的所有作業。
在您的組織中，這可能涉及執行精密複雜的作業。
因為這只是範例，所以您的命令只會重設密碼，並要求使用者在登入時變更密碼。
我們會將它放入您在最後一節中所建立的 Contoso_AD_Module 模組。

1. 在 PowerShell ISE 中，開啟 "Contoso_AD_Module.psm1"
```PowerShell
ISE 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\Contoso_AD_Module.psm1' 
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

### 步驟 4：編輯角色功能檔案
在[建立角色功能](#role-capability-creation)一節中，您已建立空白角色功能檔案。
在本節中，您將在該檔案中填入值。

首先在 ISE 中開啟角色功能檔案。
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

2.  如果您不確定命令是 Cmdlet 或函式，請執行 `Get-Command` 並查看 "CommandType"

3.  如果定義一組允許的值並不容易，則 ValidatePattern 可讓您使用規則運算式來限制參數引數。
您無法對單一參數同時定義 ValidatePattern 和 ValidateSet。

### 步驟 5：登錄新的工作階段設定
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
Description = 'An endpoint for active directory tasks.' 

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
### 測試看看！
取得您的非系統管理員使用者認證︰
```PowerShell
$HelpDeskCred = Get-Credential
```
如果您遵循＜設定使用者和群組＞一節進行，則認證會是︰
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
### 重要概念
**NoLanguage 模式**：當 PowerShell 在 "NoLanguage" 模式時，使用者只能執行命令，而不能使用任何語言項目。
如需詳細資訊，請執行 `Get-Help about_Language_Modes`。

**PowerShell 函式**：PowerShell 函式是您可以透過名稱呼叫的 PowerShell 程式碼片段。
如需詳細資訊，請執行 `Get-Help about_Functions`。

**ValidateSet/ValidatePattern**︰公開命令時，您可以限制特定參數的有效引數。
ValidateSet 是有效命令的特定清單。
ValidatePattern 是該參數引數必須符合的規則運算式。

## 多電腦部署和維護
此時，您已多次將 JEA 部署到本機系統。
因為您的生產環境可能是由多部電腦所組成，所以請務必逐步執行部署處理程序中必須在每部電腦上重複的重要步驟。

### 高階步驟︰
1.  將您的模組 (及角色功能) 複製到每個節點。
2.  將您的工作階段設定檔複製到每個節點。
3.  使用您的工作階段設定執行 `Register-PSSessionConfiguration`。
4.  將一份工作階段設定和工具組複本保留在安全的位置。
當您修改時，最好有一個「單一信任來源」。

### 範例指令碼
以下是部署的範例指令碼。
若要在您的環境中使用，您必須使用實際檔案共用和模組的名稱/路徑。
```PowerShell
# First, copy the session configuration and modules (containing role capability files) onto a file share you have access to.
Copy-Item -Path 'C:\Demo\Demo.pssc' -Destination '\\FileShare\JEA\Demo.pssc'
Copy-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\SomeModule\' -Recurse -Destination '\\FileShare\JEA\SomeModule'

# Next, author a setup script (C:\JEA\Deploy.ps1) to run on each individual node
    # Contents of C:\JEA\Deploy.ps1
    New-Item -ItemType Directory -Path C:\JEADeploy
    Copy-Item -Path '\\FileShare\JEA\Demo.pssc' -Destination 'C:\JEADeploy\'
    Copy-Item -Path '\\FileShare\JEA\SomeModule' -Recurse -Destination 'C:\Program Files\WindowsPowerShell\Modules' # Remember, Role Capability Files are found in modules
    if (Get-PSSessionConfiguration -Name JEADemo -ErrorAction SilentlyContinue)
    {
        Unregister-PSSessionConfiguration -Name JEADemo -ErrorAction Stop
    }

    Register-PSSessionConfiguration -Name JEADemo -Path 'C:\JEADeploy\Demo.pssc'
    Remove-Item -Path 'C:\JEADeploy' # Don't forget to clean up!

# Now, invoke the script on all of the target machines.
# Note: this requires PowerShell Remoting be enabled on each machine. Enabling PowerShell remoting is a requirement to use JEA as well.
# You may need to provide the "-Credential" parameter if your current user account does not have admin permissions on these machines.
Invoke-Command –ComputerName 'Node1', 'Node2', 'Node3', 'NodeN' -FilePath 'C:\JEA\Deploy.ps1'

# Finally, delete the session configuration and role capability files from the file share.
Remove-Item -Path '\\FileShare\JEA\Demo.pssc'
Remove-Item -Path '\\FileShare\JEA\SomeModule' -Recurse
```
### 修改功能
當處理多部電腦時，請務必以一致的方式公開修改。
一旦 JEA 擁有 DSC 資源，這將有助於確保您的環境保持同步。
在這之前，強烈建議您保留工作階段設定的主要複本，並在每次修改時重新部署。

### 移除功能
若要從您的系統中移除 JEA 設定，請在每部電腦上使用下列命令︰
```PowerShell
Unregister-PSSessionConfiguration -Name JEADemo 
```
## JEA 上的報告
因為 JEA 允許非特殊權限使用者在特殊權限內容中執行，所以記錄和稽核格外重要。
在本節中，我們將執行您可以用來協助記錄和報告的所有工具。

### 報告 JEA 動作
#### 潛在文字記錄
摘要說明 PowerShell 工作階段狀況的其中一個最快速方法是回顧人員輸入的內容。
您會看到其命令及這些命令的輸出安然無恙。
即使發生問題，至少您知道。
PowerShell 文字記錄的設計是為了讓您有與事實類似的檢視。

使用工作階段設定中的 "TranscriptDirectory" 欄位時，PowerShell 會自動記錄在指定工作階段中執行之所有動作的文字記錄。
您可以在下列位置，找到本文工作階段的文字記錄："$env:ProgramData\JEAConfiguration\Transcripts"

如您所見，文字記錄會記錄「已連線」的使用者、「執行身分」使用者、在工作階段中執行之命令等相關資訊。
如需 PowerShell 文字記錄的詳細資訊，請參閱這篇[部落格文章](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx)。

#### PowerShell 事件記錄檔
當您開啟模組記錄時，所有 PowerShell 動作也會記錄在一般 Windows 事件記錄檔中。
這比處理文字記錄稍微複雜，但提供給您的詳細程度會很實用。

在 "PowerShell" 作業記錄中，如果您已啟用模組記錄，事件識別碼 4104 會記錄所叫用的每個命令。

#### 其他事件記錄檔
不同於 PowerShell 記錄檔和文字記錄，其他記錄機制不會擷取「已連線的使用者」。
您必須在其他記錄檔與 PowerShell 記錄檔之間進行一些相互關聯，以對應到所執行的動作。

在「Windows 遠端管理」作業記錄中，事件識別碼 193 會記錄連線使用者的 SID 和名稱，以及 RunAs 虛擬帳戶的 SID，以便協助此相互關聯。
您可能也注意到 RunAs 虛擬帳戶的名稱結尾包含連線使用者的網域和使用者名稱。

### 報告 JEA 設定
#### Get-PSSessionConfiguration
為了精確地報告環境的狀態，請務必了解您在電腦上設定的 JEA 端點數目。
`Get-PSSessionConfiguration` 便能執行此作業。
 
#### Get-PSSessionCapability
透過 JEA 端點手動報告任何指定使用者的功能可能相當複雜。
您可能必須檢查幾個角色功能。
所幸 "Get-PSSessionCapability" Cmdlet 可執行此作業。

若要對此進行測試，請從系統管理員的 PowerShell 命令提示字元執行下列命令：
```PowerShell
Get-PSSessionCapability -Username 'CONTOSO\OperatorUser' -ConfigurationName JEADemo
```
## 結論 
完成本指南之後，您應該會有工具和詞彙可建立您自己的 JEA 端點。 感謝您的閱讀！

## 附錄

## 本指南所使用的重要概念
**PowerShell 遠端**：PowerShell 遠端可讓您對遠端電腦執行 PowerShell 命令。
您可以對一或多部電腦執行，並使用暫時或持續連線。
在此示範中，您會使用互動式工作階段從遠端登入本機電腦。
JEA 會限制可透過 PowerShell 遠端使用的功能。
如需 PowerShell 遠端的詳細資訊，請執行 `Get-Help about_Remote`。

**"RunAs" 使用者**︰使用 JEA 時，非系統管理員會以特殊權限「虛擬帳戶」身分執行。
虛擬帳戶只會持續到遠端工作階段期間結束為止。
也就是說，它會在使用者連線到端點時建立，並在使用者結束工作階段時摧毀。
根據預設，虛擬帳戶是本機 Administrator 群組的成員。
在網域控制站上，它是 Domain Admins 的成員。
虛擬帳戶是帳戶建立所在電腦上的本機帳戶，沒有該電腦以外的權限。
這表示它們未登錄在 Active Directory 中 (未指派 RID)。
此外，如果允許的命令/指令碼嘗試存取本機電腦以外的資源，它會使用電腦身分識別 (而不是虛擬帳戶身分識別) 來存取這些資源。

**「已連線」的使用者**︰連線到 JEA 端點且已指派角色的非系統管理員使用者。
這位使用者執行的任何命令，都會在 RunAs 使用者或虛擬帳戶的內容下執行。


### 建立網域控制站

本文假設您的電腦已加入網域。
如果您目前沒有可加入的網域，本節可協助您使用 DSC 快速地建立網域控制站。

#### 必要條件

1.  電腦位於內部網路
2.  電腦未加入現有的網域
3.  電腦執行 Windows Server 2016 或已安裝 WMF 5.0

#### 安裝 xActiveDirectory
如果您的電腦具有使用中的網際網路連線，請在提升權限的 PowerShell 視窗中執行下列命令︰
```PowerShell
Install-Module xActiveDirectory -Force 
```
如果您沒有網際網路連線，請將 xActiveDirectory 安裝到另一部電腦，然後將 xActiveDirectory 資料夾複製到您電腦上的 "C:\Program Files\WindowsPowerShell\Modules" 資料夾。

若要確認安裝是否成功，請執行下列命令：
```PowerShell
Get-Module xActiveDirectory -ListAvailable
``` 

#### 使用 DSC 設定網域
複製 PowerShell 中的下列指令碼，將您的電腦設為新網域中的網域控制站。
**作者的附註︰有所提供的認證未使用的已知問題。  為了安全起見，請記住您的本機系統管理員密碼。**

```PowerShell
Set-Item WSMan:\localhost\Client\TrustedHosts -Value $env:COMPUTERNAME -Force 

# This "MetaConfiguration" sets the DSC Engine to automatically reboot if required
[DscLocalConfigurationManager()]
Configuration MetaConfiguration
{
    Node $env:Computername
    {
        Settings
        {
            RebootNodeIfNeeded = $true
        }
    }
    
}

MetaConfiguration
# Apply the MetaConfiguration
Set-DscLocalConfigurationManager .\MetaConfiguration

# Configure a domain controller of a new "Contoso" domain
configuration DomainController
{
    param
    (
        $node,
        $cred
    )
    Import-DscResource -ModuleName xActiveDirectory

    Node $node
    {
        WindowsFeature ADDS
        {
            Ensure = 'Present'
            Name = 'AD-Domain-Services'
        }

        xADDomain Contoso
        {
            DomainName = 'contoso.com'
            DomainAdministratorCredential = $cred
            SafemodeAdministratorPassword = $cred
            DependsOn = '[WindowsFeature]ADDS'
        }

        file temp
        {
            DestinationPath = 'C:\temp.txt'
            Contents = 'Domain has been created'
            DependsOn = '[xADDomain]Contoso'
        }
    }
}

$ConfigData = @{
    AllNodes = @(
        @{
            NodeName = $env:Computername
            PSDscAllowPlainTextPassword = $true
        }
    )
}

# Enter your desired password for the domain administrator (note, this will be stored as plain text)
DomainController -cred (Get-Credential -Message "Enter desired credential for domain administrator") -node $env:Computername -configurationData $ConfigData

# Apply the configuration to create the domain controller
Start-DSCConfiguration -path .\DomainController -ComputerName $env:Computername -Wait -Force -Verbose
```
您的電腦會重新啟動幾次。
一旦您看到 "C:\temp.txt" 檔案包含「網域已建立」，就知道處理程序完成。 

#### 設定使用者和群組
下列命令會設定您網域中的 Operator 和 Helpdesk 群組，以及屬於該群組的對應非系統管理員使用者。
```PowerShell
# Make Groups
$NonAdminOperatorGroup = New-ADGroup -Name "JEA_NonAdmin_Operator" -GroupScope DomainLocal -PassThru
$NonAdminHelpDeskGroup = New-ADGroup -Name "JEA_NonAdmin_HelpDesk" -GroupScope DomainLocal -PassThru
$TestGroup = New-ADGroup -Name "Test_Group" -GroupScope DomainLocal -PassThru

# Make Users
$OperatorUser = New-ADUser -Name "OperatorUser" -AccountPassword (ConvertTo-SecureString "pa`$`$w0rd" -AsPlainText -Force) -PassThru
Enable-ADAccount -Identity $OperatorUser

$HelpDeskUser = New-ADUser -name "HelpDeskUser" -AccountPassword (ConvertTo-SecureString "pa`$`$w0rd" -AsPlainText -Force) -PassThru
Enable-ADAccount -Identity $HelpDeskUser

# Add Users to Groups
Add-ADGroupMember -Identity $NonAdminOperatorGroup -Members $OperatorUser
Add-ADGroupMember -Identity $NonAdminHelpDeskGroup -Members $HelpDeskUser
```

### 列入黑名單
試用 JEA 之後，您可能想知道它是否可以將命令列入黑名單。
這是合理的要求，但目前不在 JEA 的規劃中，原因如下︰

1.  我們已將 JEA 設計為限制操作員只執行他們所需的動作。
黑名單則相反。

2.  PowerShell 命令作者在設計 PowerShell 命令時並未考慮到 JEA。
在 Windows Server 2016 的全新安裝上，可立即使用的命令約有 1520 個。
這些命令的威脅模式並未納入使用者以提升權限的帳戶身分執行命令的可能性。
例如，特定命令可依設計插入程式碼 (例如核心 PowerShell 模組中的 Add-Type 和 Invoke-Command)。
當您公開我們已知的特定命令時，JEA 可能會警告您，但我們尚未根據新的威脅模式重新評估 Windows 中的所有其他命令。
您必須了解透過 JEA 公開之命令的功能。  

3.  此外，即使 JEA 封鎖了具有程式碼插入弱點的所有命令，也無法保證惡意使用者不會使用其他相關命令來執行列入黑名單的動作。
除非您了解要公開的所有命令，否則您無法保證不會發生特定動作。
不論使用白名單或黑名單，您都有責任了解要公開哪些命令。
您無法管理黑名單會公開的命令數目，因此 JEA 會改用白名單實作。

### 限制命令時的考量
此步驟還有一個值得提出的重點。
所有透過 JEA 公開的功能都必須位於系統管理員限制的區域中。
非系統管理員使用者不應該具有修改透過 JEA 端點使用之指令碼的能力。

另一個相關注意事項是，請務必不要讓 JEA 使用者可以覆寫 JEA 設定，以及將其 JEA 工作階段中的指令碼列入白名單。
公開 `Copy-Item` 等命令時請格外小心！

### 常見的角色功能問題
當您自行執行此處理程序時，可能會遇到一些常見的問題。
下列快速指南說明如何在修改及建立新端點時，找出並修正這些問題︰

#### 函式與Cmdlet
以 PowerShell 撰寫的 PowerShell 命令是 PowerShell 函式。
撰寫為特定 .NET 類別的 PowerShell 命令是 PowerShell Cmdlet。
您可以執行 `Get-Command` 來查看命令類型。

#### VisibleProviders 
您必須公開命令所需的任何提供者。
最常見的是檔案系統提供者，但您可能也需要公開其他提供者，像是登錄提供者。
如需提供者簡介，請參閱這篇 [Hey, Scripting Guy 部落格文章](http://blogs.technet.com/b/heyscriptingguy/archive/2015/04/20/find-and-use-windows-powershell-providers.aspx)。
公開提供者時請小心，通常最好是定義自己的函式來搭配基礎提供者使用，而不是直接公開 JEA 工作階段中的提供者。
如此一來，您仍然可以允許使用者使用檔案、登錄機碼等，但會保留使用者可以使用自訂驗證邏輯處理 **哪些*檔案和登錄機碼的控制權。

<!--HONumber=Jun16_HO1-->


