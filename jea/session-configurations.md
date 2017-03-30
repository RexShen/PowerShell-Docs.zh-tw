---
manager: carmonm
ms.topic: article
author: rpsqrd
ms.author: ryanpu
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2017-03-08
title: "JEA 工作階段設定"
ms.technology: powershell
ms.openlocfilehash: e98214d1777a1530b5a18ac9df1a6185d6d73979
ms.sourcegitcommit: 910f090edd401870fe137553c3db00d562024a4c
translationtype: HT
---
# <a name="jea-session-configurations"></a>JEA 工作階段設定

> 適用對象：Windows PowerShell 5.0

JEA 端點透過以特定方式建立和登錄 PowerShell 工作階段設定檔以在系統上登錄。
工作階段設定決定「誰」可以使用 JEA 端點，以及他們可以存取哪些角色。
工作階段設定也會定義適用於 JEA 工作階段中任何角色之使用者的全域設定。

本主題描述如何建立 PowerShell 工作階段設定檔，並登錄 JEA 端點。

## <a name="create-a-session-configuration-file"></a>建立工作階段設定檔

為了登錄 JEA 端點，您必須指定該端點應該如何設定。
在這裡有許多選項要考慮，最重要的一項是誰應該可以存取 JEA 端點、將指派什麼角色給他們、JEA 將在幕後使用哪一個身分識別，以及 JEA 端點的名稱為何。
這些全都定義在 PowerShell 工作階段設定檔中，這個檔案是結尾副檔名為 .pssc 的 PowerShell 資料檔。

若要建立 JEA 端點的基本架構工作階段設定檔，請執行下列命令。

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> 此基本架構檔案預設只會包含最常見的設定選項。
> 使用 `-Full` 參數可將所有適用的設定加入產生的 PSSC。

您可以在任何文字編輯器中開啟工作階段設定檔。
`-SessionType RestrictedRemoteServer` 欄位指出 JEA 將使用工作階段設定以進行安全管理。
以這種方式設定的工作階段會以 [NoLanguage 模式](https://technet.microsoft.com/en-us/library/dn433292.aspx)運作，且只能使用下列 8 種預設 Cmdlet (和別名)︰

- Clear-Host (cls, clear)
- Exit-PSSession (exsn, exit)
- Get-Command (gcm)
- Get-FormatData
- Get-Help
- Measure-Object (measure)
- Out-Default
- Select-Object (select)

沒有 PowerShell 提供者或任何外部程式 (可執行檔、指令碼等等) 可用。

您有想要為 JEA 工作階段設定的數個其他欄位。
下列各節會介紹它們。

### <a name="choose-the-jea-identity"></a>選擇 JEA 身分識別

在幕後，JEA 執行連線使用者的命令時，需要一個可使用的身分識別 (帳戶) 。
您決定 JEA 將在工作階段設定檔中使用哪一個身分識別。

#### <a name="local-virtual-account"></a>本機虛擬帳戶

如果此 JEA 端點支援的角色全都用來管理本機電腦，且本機系統管理員帳戶就足以順利執行命令，則您應該將 JEA 設定為使用本機虛擬帳戶。
虛擬帳戶是特定使用者獨有的暫時帳戶，並且持續時間僅限於他們的 PowerShell 工作階段期間。
在成員伺服器或工作站上，虛擬帳戶屬於本機電腦的 **Administrators** 群組，並且可以存取大部分的系統資源。
在 Active Directory 網域控制站上，虛擬帳戶預設屬於網域的 **Domain Admins** 群組。

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

如果工作階段設定所支援的角色不需要這類廣泛的權限，則您可以選擇是否指定虛擬帳戶所屬的安全性群組。
在成員伺服器或工作站上，指定的安全性群組必須是本機群組，而非來自網域的群組。

指定一或多個安全性群組時，虛擬帳戶將不再屬於本機或網域系統管理員群組。

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

#### <a name="group-managed-service-account"></a>群組受管理的服務帳戶


針對需要 JEA 使用者以存取網路資源，例如其他電腦或 Web 服務的情況，群組受管理的服務帳戶 (gMSA) 是更適合使用的身分識別。
gMSA 帳戶為您提供可以用來對網域中任何電腦上的資源進行驗證的網域身分識別。
gMSA 帳戶提供給您的權限由您正在存取的資源決定。
您不會在任何電腦或服務上自動擁有系統管理權限，除非電腦/服務系統管理員已明確授與 gMSA 帳戶系統管理員權限。

```powershell
# Configure JEA sessions to use the gMSA account in the local computer's domain with the sAMAccountName of 'MyJEAgMSA'
GroupManagedServiceAccount = 'MyJEAgMSA'
```

gMSA 帳戶應該只用於因為一些原因而需要存取網路資源時︰

- 使用 gMSA 帳戶時從動作回溯到使用者比較困難，因為每個使用者都共用相同的執行身分識別。 您必須參閱 PowerShell 工作階段文字記錄以及記錄檔，以讓使用者與他們的動作相互關聯。

- gMSA 帳戶可能可以存取許多連線使用者不需要存取的網路資源。 請務必嘗試限制在 JEA 工作階段中有效的權限，以遵循最低權限的原則。

> [!NOTE]
> 群組受管理的服務帳戶僅適用於 Windows PowerShell 5.1 或更新版本，以及在已加入網域的電腦上。


#### <a name="more-information-about-run-as-users"></a>執行身分使用者的詳細資訊

如需執行身分識別的詳細資訊，以及它們如何納入 JEA 工作階段的安全性，請參閱[安全性考量](security-considerations.md)文章。

### <a name="session-transcripts"></a>工作階段文字記錄

建議您將 JEA 工作階段設定檔設定為自動記錄使用者工作階段的文字記錄。
PowerShell 工作階段文字記錄包含連線使用者、指派給他們的執行身分識別，以及使用者所執行的命令等相關資訊。
對於必須了解誰對系統執行了特定變更的稽核小組而言，它們可能很實用。

若要在工作階段設定檔中設定自動文字記錄，請提供要儲存文字記錄的資料夾路徑。

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

指定的資料夾應該設定為防止使用者修改或刪除其中的任何資料。
本機系統帳戶會將文字記錄寫入資料夾，這需要該目錄的讀取和寫入權限。
標準使用者應該無法存取該資料夾，並且只有有限的一組安全性系統管理員有權可稽核文字記錄。

### <a name="user-drive"></a>使用者磁碟機

如果您的連線使用者將需要從 JEA 端點複製檔案或將檔案複製到 JEA 端點才能執行命令，則您可以啟用工作階段設定檔中的使用者磁碟機。
使用者磁碟機是 [PSDrive](https://msdn.microsoft.com/en-us/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives)，且對應至每個連線使用者的唯一資料夾。
這個資料夾可作為他們在系統中複製檔案的空間，而不讓他們存取完整的檔案系統或公開檔案系統提供者。
使用者磁碟機內容會在工作階段之間持續存在，以應付網路連線可能中斷的情況。

```powershell
MountUserDrive = $true
```

根據預設，使用者磁碟機可讓您儲存每個使用者最多 50 MB 的資料。
您可以使用 *UserDriveMaxmimumSize* 欄位限制使用者可以取用的資料量。

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

若不想讓使用者磁碟機中的資料持續存在，您可以在系統上設定排定的工作，每晚自動清理資料夾。

> [!NOTE]
> 使用者磁碟機僅適用於 Windows PowerShell 5.1 或更新版本。

### <a name="role-definitions"></a>角色定義

工作階段設定檔中的角色定義會定義「使用者」對「角色」的對應。
此欄位包含的每個使用者或群組會在登錄 JEA 端點時自動獲得 JEA 端點的權限。
每個使用者或群組只能作為索引鍵包含在雜湊表中一次，但可以指派多個角色給它。
角色功能的名稱應該是角色功能檔案的名稱，不含 .psrc 副檔名。

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

如果使用者屬於角色定義中的多個群組，他們將可以存取每個群組的角色。
如果兩個角色授與對相同 Cmdlet 的存取權，使用者將獲得最寬鬆的參數集。

### <a name="role-capability-search-order"></a>角色功能搜尋順序
如上述範例所示，會以角色功能檔案的一般名稱 (不含副檔名的檔名) 來參考角色功能。
如果系統上有多個相同一般名稱的角色功能，PowerShell 將使用其隱含搜尋順序，來選取有效的角色功能檔案。
它將**不會**提供存取權給同名的所有角色功能檔案。

JEA 使用 `$env:PSModulePath` 環境變數來判斷要掃描哪些路徑以取得角色功能檔案。
在每個路徑中，JEA 會尋找包含 "RoleCapabilities" 子資料夾的有效 PowerShell 模組。
如同匯入模組一般，相較於具有相同名稱的自訂角色功能，JEA 較偏好 Windows 隨附的角色功能。
針對所有其他的命名衝突，會由 Windows 列舉目錄中檔案的順序來決定順序 (不保證依字母順序)。
第一個符合需求名稱的角色功能檔案將會用於連線使用者。

由於在兩個 (或更多) 角色功能共用相同名稱時，角色功能搜尋順序具有不確定性，「強烈建議」您確保電腦上的角色功能都使用唯一的名稱。

### <a name="conditional-access-rules"></a>條件式存取原則

包含在 RoleDefinitions 欄位的所有使用者和群組會自動獲得 JEA 端點的存取權。
條件式存取規則可讓您精簡此存取權，並要求使用者屬於不會影響指派給他們之角色的其他安全性群組。
這適用於您想要整合「即時」(Just-in-Time) 特殊權限存取管理解決方案、智慧卡驗證或其他多因素驗證解決方案與 JEA。

工作階段設定檔中的 RequiredGroups 欄位定義了條件式存取規則。
在那裡，您可以包含雜湊表 (選擇性地為巢狀)，該雜湊表會使用 'And' 及 'Or' 索引鍵來建構您的規則。
以下是如何運用此欄位的一些範例︰

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

> [!NOTE]
> 條件式存取原則僅適用於 Windows PowerShell 5.1 或更新版本。

### <a name="other-properties"></a>其他屬性
工作階段設定檔也可以執行工作角色功能檔案的一切操作，但無法提供連線使用者對不同命令的存取權。
如果您想要允許所有使用者存取特定 Cmdlet、函式或提供者，則您可以直接在工作階段設定檔中完成。
如需工作階段設定檔中支援屬性的完整清單，請執行 `Get-Help New-PSSessionConfigurationFile -Full`。

## <a name="testing-a-session-configuration-file"></a>測試工作階段設定檔

您可以使用 [Test-PSSessionConfigurationFile](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile) Cmdlet 測試工作階段設定。
如果您已使用文字編輯器手動編輯 pssc 檔案，強烈建議您測試您的工作階段設定檔，以確定語法正確。
如果工作階段設定檔未通過此測試，它將無法順利在系統上登錄。

## <a name="sample-session-configuration-file"></a>範例工作階段設定檔

以下是完整的範例，示範如何建立及驗證 JEA 的工作階段設定。
請注意，為了便利性和可讀性起見，角色定義會建立並儲存在 `$roles` 變數。
並不要求須執行這項操作。

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a>更新工作階段設定檔

如果您需要變更 JEA 工作階段設定的屬性，包括將使用者對應至角色，您必須[取消登錄](register-jea.md#unregistering-jea-configurations)並[重新登錄](register-jea.md) JEA 工作階段設定。
當您重新登錄 JEA 工作階段設定時，請使用包含您想要之變更的已更新 PowerShell 工作階段設定檔。

## <a name="next-steps"></a>接下來的步驟

- [登錄 JEA 設定](register-jea.md)
- [編寫 JEA 角色](role-capabilities.md)
