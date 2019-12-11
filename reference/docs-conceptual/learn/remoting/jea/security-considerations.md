---
ms.date: 07/10/2019
keywords: jea,powershell,安全性
title: JEA 安全性考量
ms.openlocfilehash: befc24fec368c4f6d60477daf63bf17e9431133e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "70017769"
---
# <a name="jea-security-considerations"></a>JEA 安全性考量

JEA 可協助您減少電腦上的永久系統管理員數目來改善安全性的態勢。 JEA 使用 PowerShell 工作階段設定建立新的進入點，供使用者管理系統。 需要提升電腦存取權 (但非無限) 以執行系統管理工作的使用者，可獲授與 JEA 端點的存取權。 因為 JEA 允許這些使用者不必有完整的系統管理員存取權即可執行系統管理命令，您可以將這些使用者從高度權限的安全性群組中移除。

## <a name="run-as-account"></a>執行身分帳戶

每個 JEA 端點都有指定的**執行身分**帳戶。 這是執行連線使用者動作的帳戶。 此帳戶是可在[工作階段設定檔](session-configurations.md)中設定，且您選擇的帳戶與端點的安全性有很大的關係。

**虛擬帳戶**是設定**執行身分**帳戶的建議方式。 虛擬帳戶是一次性、暫時的本機帳戶，針對連線使用者而建立，以便在其 JEA 工作階段期間使用。 他們的工作階段一終止，虛擬帳戶便會損毀，無法再使用。 連線的使用者不知道虛擬帳戶的認證。 您無法使用虛擬帳戶透過遠端桌面或未受限制的 PowerShell 端點等其他方式來存取系統。

根據預設，虛擬帳戶屬於電腦上的本機 **Administrators** 群組。 這可讓他們有完整權限可管理系統上的任何資源，但沒有權限來管理網路上的資源。
向其他電腦進行驗證時，使用者內容會是本機電腦帳戶，而不是虛擬帳戶。

網域控制站是特殊案例，因為沒有本機 **Administrators** 群組。 但虛擬帳戶屬於 **Domain Admins**，且可以管理網域控制站的目錄服務。 網域身分識別仍然限用於 JEA 工作階段具現化所在的網域控制站。 所有網路存取似乎都改來自網域控制站電腦物件。

在這兩種情況下，您可以明確地定義虛擬帳戶所屬的安全性群組。 當工作不需本機或網域系統管理員權限也能執行時，會是較佳的做法。 如果您已經為系統管理員定義安全性群組，請將虛擬帳戶成員資格授與該群組。 虛擬帳戶群組成員資格僅限於工作站和成員伺服器的本機安全性群組。 在網域控制站上，虛擬帳戶必須是網域安全性群組的成員。
虛擬帳戶新增至一或多個安全性群組之後，即不再屬於預設群組 (本機或網域系統管理員)。

下表摘列虛擬帳戶可能的設定選項和結果權限：

|        電腦類型         | 虛擬帳戶群組設定 |                   本機使用者內容                    | 網路使用者內容 |
| ---------------------------- | ----------------------------------- | ------------------------------------------------------- | -------------------- |
| 網域控制站            | Default                             | 網域使用者，'*DOMAIN*\Domain Admins' 的成員         | 電腦帳戶     |
| 網域控制站            | 網域群組 A 和 B               | 網域使用者，'*DOMAIN*\A', '*DOMAIN*\B' 的成員       | 電腦帳戶     |
| 成員伺服器或工作站 | Default                             | 本機使用者，'*BUILTIN*\Administrators' 的成員        | 電腦帳戶     |
| 成員伺服器或工作站 | 本機群組 C 和 D                | 本機使用者，'*COMPUTER*\C' 和 '*COMPUTER*\D' 的成員 | 電腦帳戶     |

當您查看安全性稽核事件與應用程式事件記錄檔時，您會看到每個 JEA 使用者工作階段都有唯一的虛擬帳戶。 這個唯一帳戶可協助您從 JEA 端點中使用者動作回溯到執行命令的原始使用者。 虛擬帳戶名稱遵循 `WinRM Virtual Users\WinRM_VA_<ACCOUNTNUMBER>_<DOMAIN>_<sAMAccountName>` 格式。例如，如果網域 **Contoso** 中使用者 **Alice** 重新啟動 JEA 端點中的服務，則與任何服務控制管理員事件建立關聯的使用者名稱會是 `WinRM Virtual Users\WinRM_VA_1_contoso_alice`。

**群組受控服務帳戶 (gMSA)** 適用於成員伺服器需要在 JEA 工作階段中存取網路資源時。 例如，使用 JEA 端點來控制不同電腦上所裝載的 REST API 服務時。 輕鬆撰寫函式來叫用 REST API，但您需要有網路識別身分才能使用 API 驗證身分。 使用群組受控服務帳戶可促成「第二個躍點」，同時仍可控制可以使用帳戶的電腦。 gMSA 的有效權限由 gMSA 帳戶所屬安全性群組 (本機或網域) 定義。

JEA 端點設定為使用 gMSA 帳戶之後，所有 JEA 使用者動作似乎都來自相同的 gMSA。 從動作回溯到特定使用者的唯一方法，是在 PowerShell 工作階段文字記錄中識別執行的命令集合。

未指定**執行身分**帳戶時，會使用**傳遞認證**。 PowerShell 使用連線使用者的認證在遠端伺服器上執行命令。 這需要您授與連線使用者特殊權限管理群組的直接存取權。 JEA **不**建議使用此設定。 如果連線使用者已經有系統管理員權限，他們可以避免使用 JEA 並透過其他未受限制的方式來管理系統。 如需詳細資訊，請參閱下節中的 [JEA 無法防止系統管理員](#jea-doesnt-protect-against-admins)。

**標準執行身分帳戶**可讓您指定整個 PowerShell 工作階段執行的任何使用者帳戶。 使用固定**執行身分**帳戶 (搭配 `-RunAsCredential` 參數) 的工作階段設定不會察覺 JEA。 角色定義不再如預期運作。 每位獲授權存取端點的使用者皆獲指派相同角色。

您不應該在 JEA 端點上使用 **RunAsCredential**，因為難以從動作回溯到特定的使用者，且缺乏將使用者對應至角色的支援。

## <a name="winrm-endpoint-acl"></a>WinRM 端點 ACL

如同一般的 PowerShell 遠端端點，每個 JEA 端點都有個別的存取控制清單 (ACL)，可控制誰可以向 JEA 端點驗證身分。 如果設定不當，受信任的使用者可能無法存取 JEA 端點，且未受信任的使用者可能取得存取權。 WinRM ACL 不會影響將使用者對應至 JEA 角色。 對應是由用來登錄端點的工作階段設定檔 **RoleDefinitions** 欄位所控制。

根據預設，當 JEA 端點有多個角色功能時，WinRM ACL 會設定為允許存取所有的對應使用者。 例如，使用下列命令設定的 JEA 工作階段，會將完整存取權授與 `CONTOSO\JEA_Lev1` 和 `CONTOSO\JEA_Lev2`。

```powershell
$roles = @{ 'CONTOSO\JEA_Lev1' = 'Lev1Role'; 'CONTOSO\JEA_Lev2' = 'Lev2Role' }
New-PSSessionConfigurationFile -Path '.\jea.pssc' -SessionType RestrictedRemoteServer -RoleDefinitions $roles -RunAsVirtualAccount
Register-PSSessionConfiguration -Path '.\jea.pssc' -Name 'MyJEAEndpoint'
```

您可以使用 [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) Cmdlet 稽核使用者權限。

```powershell
Get-PSSessionConfiguration -Name 'MyJEAEndpoint' | Select-Object Permission
```

```Output
Permission
----------
CONTOSO\JEA_Lev1 AccessAllowed
CONTOSO\JEA_Lev2 AccessAllowed
```

若要變更哪些使用者可以存取，請執行 `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -ShowSecurityDescriptorUI` 以取得互動式提示或執行 `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -SecurityDescriptorSddl <SDDL string>` 來更新權限。 使用者需要至少有「叫用」  權利才能存取 JEA 端點。

您可建立一個 JEA 端點，不對應至每個具有存取權的使用者已定義角色。 這些使用者可以啟動 JEA 工作階段，但只能存取預設的 Cmdlet。 您可以藉由執行 `Get-PSSessionCapability` 稽核 JEA 端點中的使用者權限。 如需詳細資訊，請參閱 [JEA 上的稽核和報告](audit-and-report.md)。

## <a name="least-privilege-roles"></a>最低權限角色

在設計 JEA 角色時，請務必記得在幕後執行的虛擬和群組受控服務帳戶，通常可無限制存取本機電腦。 JEA 角色功能可協助限制可在該特殊權限內容中執行的命令和應用程式。
設計不當的角色會允許危險命令，可能允許使用者突破 JEA 界限或取得敏感性資訊的存取權。

例如，請考慮下列角色功能項目：

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\*-Process'
}
```

此角色功能可讓使用者執行任何 PowerShell Cmdlet，並使用來自 **Microsoft.PowerShell.Management** 模組的名詞 **Process**。 使用者可能需要存取像 `Get-Process` 這樣的 Cmdlet 來了解哪些應用程式正在系統上執行，以及存取 `Stop-Process` 來終止任何未回應的應用程式。 不過，此項目也允許 `Start-Process`，這可以用來以完整的系統管理員權限啟動任意程式。 程式不需要安裝在本機系統上。 已連線的使用者可從授與使用者本機系統管理員權限、執行惡意程式碼及執行其他作業的檔案共用來啟動程式。

這項相同角色功能的更安全版本應該如下︰

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\Get-Process', 'Microsoft.PowerShell.Management\Stop-Process'
}
```

避免在角色功能中使用萬用字元。 請務必定期[稽核有效的使用者權限](audit-and-report.md#check-effective-rights-for-a-specific-user)，以了解哪些命令可供使用者存取。

## <a name="jea-doesnt-protect-against-admins"></a>JEA 無法防止系統管理員

JEA 的核心原則之一是允許非管理員執行一些管理工作。 JEA 無法防止已有系統管理員權限的使用者。 屬於 **Domain Admins**、本機 **Administrators** 或其他高度權限群組的使用者，可以透過其他方式規避 JEA 防護。 例如，他們可以使用 RDP 登入、使用遠端 MMC 主控台或連接至未受限制的 PowerShell 端點。 系統上的本機管理員也可以修改 JEA 設定，允許其他使用者或變更角色功能以擴充使用者可以在其 JEA 工作階段中執行的範圍。 因此務必要評估您的 JEA 使用者擴充權限，看看他們是否有其他方法可取得系統的特殊權限存取。

常見的做法是使用 JEA 進行一般日常維護，且擁有 Just-in-Time 的特殊權限存取管理解決方案，讓使用者在緊急情況下暫時成為本機管理員。 這有助於確保使用者在系統上不是永久的系統管理員，但如果 (且唯有) 他們完成之工作流程會記錄他們對那些權限的使用，便可以取得那些權限。
