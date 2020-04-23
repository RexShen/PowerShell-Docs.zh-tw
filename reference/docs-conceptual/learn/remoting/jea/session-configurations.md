---
ms.date: 07/10/2019
keywords: jea,powershell,安全性
title: JEA 工作階段設定
ms.openlocfilehash: 650d0d11ef13605847d0822249e29e3491180629
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "70017729"
---
# <a name="jea-session-configurations"></a>JEA 工作階段設定

JEA 端點透過建立和登錄 PowerShell 工作階段設定檔在系統上登錄。 工作階段設定定義誰可以使用 JEA 端點，以及他們可以存取哪些角色。 它們也會定義適用於 JEA 工作階段所有使用者的全域設定。

## <a name="create-a-session-configuration-file"></a>建立工作階段設定檔

若要登錄 JEA 端點，您必須指定該端點的設定方式。 有許多選項要考慮。 最重要的選項如下：

- 誰可以存取 JEA 端點
- 他們獲指派哪些角色
- JEA 實際使用哪些身分識別
- JEA 端點的名稱

這些選項全都定義在副檔名為 `.pssc` 的 PowerShell 資料檔中，稱為 PowerShell 工作階段設定檔。 工作階段設定檔可使用任何文字編輯器編輯。

執行下列命令以建立空白的範本設定檔。

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> 根據預設，範本檔只包含最常見的設定選項。 使用 `-Full` 參數可將所有適用的設定加入產生的 PSSC。

`-SessionType RestrictedRemoteServer` 欄位指出 JEA 使用工作階段設定進行安全管理。 這種類型的工作階段會以 **NoLanguage** 模式運作，且只能存取下列預設命令 (和別名)︰

- Clear-Host (cls, clear)
- Exit-PSSession (exsn, exit)
- Get-Command (gcm)
- Get-FormatData
- Get-Help
- Measure-Object (measure)
- Out-Default
- Select-Object (select)

沒有可用的 PowerShell 提供者或任何外部程式 (可執行檔或指令碼) 。

如需語言模式的詳細資訊，請參閱[about_Language_modes](/powershell/module/microsoft.powershell.core/about/about_language_modes)。

### <a name="choose-the-jea-identity"></a>選擇 JEA 身分識別

在幕後，JEA 執行連線使用者的命令時，需要一個可使用的身分識別 (帳戶) 。
您定義 JEA 在工作階段設定檔中使用的身分識別。

#### <a name="local-virtual-account"></a>本機虛擬帳戶

本機虛擬帳戶適用於當針對 JEA 端點定義的角色全都用來管理本機電腦，且本機系統管理員帳戶就足以順利執行命令的情況。
虛擬帳戶是特定使用者獨有的暫時帳戶，並且持續時間僅限於他們的 PowerShell 工作階段期間。 在成員伺服器或工作站上，虛擬帳戶屬於本機電腦的 **Administrators** 群組。 在 Active Directory 網域控制站上，虛擬帳戶預設屬於網域的 **Domain Admins** 群組。

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

如果工作階段設定定義的角色不需要完整系統管理權限，您就可以指定虛擬帳戶所屬的安全性群組。 在成員伺服器或工作站上，指定的安全性群組必須是本機群組，而非來自網域的群組。

指定一或多個安全性群組時，虛擬帳戶不會指派給本機或網域的 Administrators 群組。

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

> [!NOTE]
> 虛擬帳戶會暫時獲得授與在本機伺服器安全性原則中以服務方式登入的權限。 若其中一個指定的 VirtualAccountGroups 已在原則中獲得授與此權限，則將無法再新增個別的虛擬帳戶並會從原則中移除。 這在例如對網域控制站所進行的修訂會經過仔細稽核的網域控制站案例中很有用。 此項目僅適用於包含 2018 年 11 月或更新彙總的 Windows Server 2016，以及包含 2019 年 1 月或更新彙總的 Windows Server 2019。

#### <a name="group-managed-service-account"></a>群組受控服務帳戶

當 JEA 使用者需要存取網路資源，例如檔案共用和 Web 服務時，群組受控服務帳戶 (gMSA) 是適用的身分識別。 GMSA 提供的網域身分識別，可用來驗證網域中任何電腦上的資源。 您指派的資源決定 GMSA 提供的權限。 除非電腦或服務系統管理員已明確授與這些 GMSA 權限，否則您不會有任何電腦或服務的管理權限。

```powershell
# Configure JEA sessions to use the GMSA in the local computer's domain
# with the sAMAccountName of 'MyJEAGMSA'
GroupManagedServiceAccount = 'Domain\MyJEAGMSA'
```

應在有必要時才使用 GMSA：

- 使用 GMSA 時很難從動作回溯到使用者。 每個使用者都會共用相同的執行身分識別。 您必須檢閱 PowerShell 工作階段文字記錄和記錄檔，讓個別的使用者與其動作相互關聯。

- GMSA 可以存取許多連線使用者不需要存取的網路資源。 請務必嘗試限制在 JEA 工作階段中有效的權限，以遵循最低權限的原則。

> [!NOTE]
> 群組受控服務帳戶僅適用於已加入網域，使用 PowerShell 5.1 或更新版本的電腦。

如需保護 JEA 工作階段的詳細資訊，請參閱[安全性考量](security-considerations.md)一文。

### <a name="session-transcripts"></a>工作階段文字記錄

建議您將 JEA端點設定為自動記錄使用者工作階段的文字記錄。 PowerShell 工作階段文字記錄包含連線使用者、指派給他們的執行身分識別，以及使用者所執行的命令等相關資訊。 對於必須了解誰對系統執行特定變更的稽核小組而言，它們可能很實用。

若要在工作階段設定檔中設定自動文字記錄，請提供要儲存文字記錄的資料夾路徑。

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

**本機系統**帳戶會將文字記錄寫入資料夾，這需要該目錄的讀取和寫入權限。 標準使用者應該無法存取此資料夾。 限制有權稽核文字記錄的安全性系統管理員數目。

### <a name="user-drive"></a>使用者磁碟機

如果您的連線使用者需要在 JEA 端點來回複製檔案，您可在工作階段設定檔中啟用使用者磁碟機。 使用者磁碟機是 **PSDrive**，且對應至每個連線使用者的唯一資料夾。 這個資料夾允許使用者在系統中來回複製檔案，但不讓他們存取完整的檔案系統，也不公開 FileSystem 提供者。 使用者磁碟機內容會在工作階段之間持續存在，以應付網路連線可能中斷的情況。

```powershell
MountUserDrive = $true
```

根據預設，使用者磁碟機可讓您儲存每個使用者最多 50 MB 的資料。 您可以使用 *UserDriveMaximumSize* 欄位限制使用者可以取用的資料量。

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

若不想讓使用者磁碟機中的資料持續存在，您可以設定系統的排程工作，每晚自動清理資料夾。

> [!NOTE]
> 使用者磁碟機僅適用於 PowerShell 5.1 或更新版本。

如需 PSDrive 的詳細資訊，請參閱[管理 PowerShell 磁碟機](/powershell/scripting/samples/managing-windows-powershell-drives)。

### <a name="role-definitions"></a>角色定義

工作階段設定檔中的角色定義會定義「使用者」  對「角色」  的對應。 此欄位包含的每個使用者或群組會在登錄 JEA 端點後，自動獲得 JEA 端點的權限。
每個使用者或群組只能作為索引鍵包含在雜湊表中一次，但可以指派多個角色給它。 角色功能的名稱應該是角色功能檔案的名稱，不含 `.psrc` 副檔名。

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

如果使用者屬於角色定義中的多個群組，他們可以存取每個群組的角色。 當兩個角色授與同一 Cmdlet 存取權時，使用者將獲得最寬鬆的參數集。

在角色定義欄位中指定本機使用者或群組時，請務必使用電腦名稱，不要使用 **localhost** 或萬用字元。 您可以藉由檢查 `$env:COMPUTERNAME` 變數來檢查電腦名稱。

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a>角色功能搜尋順序

如上述範例所示，會以角色功能檔案的基底名稱來參考角色功能。 檔案的基底名稱是不含副檔名的檔名。 如果系統上有多個同名的角色功能，PowerShell 會使用其隱含搜尋順序，來選取有效的角色功能檔案。 JEA **不會**提供存取權給同名的所有角色功能檔案。

JEA 使用 `$env:PSModulePath` 環境變數來判斷要掃描哪些路徑以取得角色功能檔案。 在每個路徑中，JEA 會尋找包含 "RoleCapabilities" 子資料夾的有效 PowerShell 模組。 如同匯入模組一般，相較於具有相同名稱的自訂角色功能，JEA 較偏好 Windows 隨附的角色功能。

針對所有其他的命名衝突，則由 Windows 在目錄中列舉檔案的順序來決定先後順序。 順序不一定依字母順序排列。 第一個符合指定名稱的角色功能檔案會用於連線使用者。 因為角色功能搜尋順序不具決定性，所以**強烈建議**角色功能使用唯一的檔名。

### <a name="conditional-access-rules"></a>條件式存取原則

包含在 **RoleDefinitions** 欄位的所有使用者和群組會自動獲得 JEA 端點的存取權。 條件式存取規則可讓您精簡此存取權，並要求使用者屬於不會影響他們獲派角色的其他安全性群組。 這適用於您想要使用 JEA 整合 Just-in-Time 特殊權限存取管理解決方案、智慧卡驗證或其他多因素驗證解決方案的情況。

工作階段設定檔中的 RequiredGroups 欄位定義了條件式存取規則。
在那裡，您可以包含雜湊表 (選擇性地為巢狀)，該雜湊表會使用 'And' 及 'Or' 索引鍵來建構您的規則。 以下是如何使用此欄位的一些範例：

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
> 條件式存取規則僅適用於 PowerShell 5.1 或更新版本。

### <a name="other-properties"></a>其他屬性

工作階段設定檔也可以執行工作角色功能檔案的一切操作，但無法提供連線使用者對不同命令的存取權。 如果您想要允許所有使用者存取特定 Cmdlet、函式或提供者，則您可以直接在工作階段設定檔中完成。
如需工作階段設定檔中支援屬性的完整清單，請執行 `Get-Help New-PSSessionConfigurationFile -Full`。

## <a name="testing-a-session-configuration-file"></a>測試工作階段設定檔

您可以使用 [Test-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile) Cmdlet 測試工作階段設定。 如已使用手動方式編輯 `.pssc` 檔案，建議您測試工作階段設定檔。 測試可確保語法正確。 如果工作階段設定檔未通過此測試，即無法在系統上登錄。

## <a name="sample-session-configuration-file"></a>範例工作階段設定檔

下例示範如何建立及驗證 JEA 的工作階段設定。 為了便利性和可讀性起見，角色定義會建立並儲存在 `$roles` 變數中。 這不是必要操作。

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

若要變更 JEA 工作階段設定的屬性，包括將使用者對應至角色，您必須[取消登錄](register-jea.md#unregistering-jea-configurations)。 然後，使用更新的工作階段設定檔，[重新登錄](register-jea.md) JEA 工作階段設定。

## <a name="next-steps"></a>後續步驟

- [登錄 JEA 設定](register-jea.md)
- [編寫 JEA 角色](role-capabilities.md)
