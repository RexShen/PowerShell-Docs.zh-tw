---
manager: carmonm
ms.topic: article
author: rpsqrd
ms.author: ryanpu
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-12-05
title: "JEA 安全性考量"
ms.technology: powershell
ms.openlocfilehash: 03d34a7c8241aee1578a1cf2e794046578669dce
ms.sourcegitcommit: f75fc25411ce6a768596d3438e385c43c4f0bf71
translationtype: HT
---
# <a name="jea-security-considerations"></a>JEA 安全性考量

> 適用對象：Windows PowerShell 5.0

JEA 可協助您減少電腦上的永久系統管理員數目來改善安全性的態勢。
它是藉由建立新的進入點，供使用者管理系統 (PowerShell 工作階段設定)，這個進入點預設會嚴密鎖定，以避免誤用。
需要部分 (但非無限) 電腦存取權以執行系統管理工作的使用者，可以授與他們對 JEA 端點的存取權。
由於 JEA 允許他們執行系統管理命令而不必具有直接的系統管理員存取權，您便可以將這些使用者從高度權限的安全性群組移除 (使其成為標準使用者)。

本主題會更詳細地描述 JEA 安全性模型與最佳做法。

## <a name="run-as-account"></a>執行身分帳戶

每個 JEA 端點有指定的「執行身分」帳戶，也就是執行連線使用者動作所用的帳戶。
此帳戶是可在[工作階段設定檔](session-configurations.md)中設定，且您選擇的帳戶與端點的安全性有很大的關係。

**虛擬帳戶**是設定執行身分帳戶的建議方式。
虛擬帳戶是一次性、暫時的本機帳戶，針對連線使用者而建立，以便在其 JEA 工作階段期間使用。
他們的工作階段一終止，虛擬帳戶便會損毀，無法再使用。
連線使用者不知道虛擬帳戶的認證，且無法使用虛擬帳戶透過其他方式存取系統，例如遠端桌面或未受限制的 PowerShell 端點。

根據預設，虛擬帳戶屬於電腦上的本機系統管理員群組。
這可讓他們有完整權限可管理系統上的任何資源，但沒有權限來管理網路上的資源。
向其他電腦進行驗證時，使用者內容將是本機電腦帳戶，而不是虛擬帳戶。

在 Active Directory 網域控制站上，虛擬帳戶預設會取得「網域系統管理員」權限。
這是因為網域控制站上沒有本機系統管理員群組。
因此，網域控制站上的虛擬帳戶是網域帳戶，並可在其他電腦上使用。
在網域控制站上設定 JEA 工作階段時，您必須小心避免公開可用來管理網路上其他電腦的命令。

在這兩種情況下，您可以明確地定義虛擬帳戶應該屬於哪些安全性群組。
當您執行的工作也可以不需本機/網域系統管理員權限而執行時，會是比較好的做法。
如果您已經為系統管理員定義安全性群組，可以直接將虛擬帳戶成員資格授與該群組，為它提供所需的權限。
虛擬帳戶群組成員資格僅限於工作站和成員伺服器上的本機安全性群組，但在網域控制站上，他們只能是網域安全性群組的成員。
一旦您指定虛擬帳戶所屬的一或多個安全性群組，它將不再屬於預設群組 (本機系統管理員或網域系統管理員)。

下表摘要列出針對虛擬帳戶的可能設定選項和產生的權限

電腦類型                | 虛擬帳戶群組設定 | 本機使用者內容                                      | 網路使用者內容
-----------------------------|-------------------------------------|---------------------------------------------------------|--------------------------------------------------
網域控制站            | Default                             | 網域使用者，'*DOMAIN*\Domain Admins' 的成員         | 網域使用者，'*DOMAIN*\Domain Admins' 的成員
網域控制站            | 網域群組 A 和 B               | 網域使用者，'*DOMAIN*\A', '*DOMAIN*\B' 的成員       | 網域使用者，'*DOMAIN*\A', '*DOMAIN*\B' 的成員
成員伺服器或工作站 | Default                             | 本機使用者，'*BUILTIN*\Administrators' 的成員        | 電腦帳戶
成員伺服器或工作站 | 本機群組 C 和 D                | 本機使用者，'*COMPUTER*\C' 和 '*COMPUTER*\D' 的成員 | 電腦帳戶

當您查看安全性稽核事件與應用程式事件記錄檔時，您會看到每個 JEA 使用者工作階段都有唯一的虛擬帳戶。
這可協助您從 JEA 端點中的使用者動作回溯到執行命令的原始使用者。
虛擬帳戶名稱採用下列格式："WinRM Virtual Users\\WinRM\_VA\_帳戶號碼\_網域\_SAM 帳戶名稱" 例如，如果網域 "Contoso" 中的使用者 "Alice" 重新啟動 JEA 端點中的服務，則與任何服務控制管理員事件相關聯的使用者名稱會是 "WinRM Virtual Users\\WinRM\_VA\_1\_contoso\_alice"。


**群組受管理的服務帳戶 (gMSA)** 適用於成員伺服器需要在 JEA 工作階段中存取網路資源時。
範例使用案例是用來控制不同電腦上所裝載之 REST API 存取的 JEA 端點。
很容易即可撰寫函式，在 REST API 上進行所需的引動過程，但為了向 API 進行驗證，您需要網路身分識別。
使用群組受管理的服務帳戶可促成「第二個躍點」，同時仍可控制哪些電腦可以使用帳戶。
gMSA 的有效權限由 gMSA 帳戶所屬安全性群組 (本機或網域) 定義。

JEA 端點設定為使用 gMSA 帳戶之後，所有 JEA 使用者的動作會顯示為來自相同的群組受管理的服務帳戶。
從動作回溯到特定使用者的唯一方法，是在 PowerShell 工作階段文字記錄中識別執行的命令集合。

**傳遞認證**如果您未指定執行身分帳戶，PowerShell 會使用連線使用者的認證在遠端伺服器上執行命令。
不建議針對 JEA 使用此設定，因為您需要授與連線使用者對特殊權限管理群組的直接存取權。
如果連線使用者已經有系統管理員權限，他們可以完全避免使用 JEA 並透過其他未受限制的方式來管理系統。
請參閱下節，了解 [JEA 無法防止系統管理員](#jea-does-not-protect-against-admins)的詳細資訊。

**標準執行身分帳戶**可讓您指定整個 PowerShell 工作階段將執行的任何使用者帳戶。
這是一項重要的差異，因為已設定為使用固定執行身分帳戶 (使用 `-RunAsCredential` 參數) 的工作階段設定不會察覺 JEA。
這表示角色定義不再如預期般運作，且獲得授權存取端點的每個使用者都會被指派相同的角色。

您不應該在 JEA 端點上使用 RunAsCredential，因為難以從動作回溯到特定的使用者，並且也缺乏將使用者對應至角色的支援。

## <a name="winrm-endpoint-acl"></a>WinRM 端點 ACL

如同一般的 PowerShell 遠端端點，每個 JEA 端點在 WinRM 設定中都有個別的存取控制清單 (ACL) 設定，控制誰可以向 JEA 端點進行驗證。
如果設定不當，受信任的使用者可能無法存取 JEA 端點，和/或不受信任的使用者可能取得存取權。
不過，WinRM ACL 不會影響將使用者對應至 JEA 角色。
那是由系統上登錄的工作階段設定檔中的 *RoleDefinitions* 欄位所控制。

根據預設，當您使用工作階段設定檔和一或多個角色功能登錄 JEA 端點時，WinRM ACL 會設定為允許所有對應至端點的一或多個角色存取權。
例如，使用下列命令設定的 JEA 工作階段，會授與完整存取權給 *CONTOSO\JEA\_Lev1* 和 *CONTOSO\JEA\_Lev2*。

```powershell
$roles = @{ 'CONTOSO\JEA_Lev1' = 'Lev1Role'; 'CONTOSO\JEA_Lev2' = 'Lev2Role' }
New-PSSessionConfigurationFile -Path '.\jea.pssc' -SessionType RestrictedRemoteServer -RoleDefinitions $roles -RunAsVirtualAccount
Register-PSSessionConfiguration -Path '.\jea.pssc' -Name 'MyJEAEndpoint'
```

您可以使用 [Get-PSSessionConfiguration](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) Cmdlet 稽核使用者權限。

```powershell
PS C:\> Get-PSSessionConfiguration -Name 'MyJEAEndpoint' | Select-Object Permission

Permission
----------
CONTOSO\JEA_Lev1 AccessAllowed
CONTOSO\JEA_Lev2 AccessAllowed
```

若要變更哪些使用者可以存取，請執行 `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -ShowSecurityDescriptorUI` 以取得互動式提示或執行 `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -SecurityDescriptorSddl <SDDL string>` 來更新權限。
使用者需要至少有「叫用」權利才能存取 JEA 端點。

如果其他使用者也獲得授與 JEA 端點的存取權，但不屬於工作階段設定檔中定義的任何角色，他們可以啟動 JEA 工作階段，但只有預設 Cmdlet 的存取權。
您可以藉由執行 `Get-PSSessionCapability` 稽核 JEA 端點中的使用者權限。
請參閱 [JEA 上的稽核和報告](audit-and-report.md)一文，以取得有關稽核使用者可在 JEA 端點存取之命令的詳細資訊。

## <a name="least-privilege-roles"></a>最低權限角色

在設計 JEA 角色時，請務必記得在幕後執行的虛擬或群組受管理的服務帳戶，通常具有無限制的存取權可管理本機電腦。
透過限制可使用特殊權限的內容執行的應用程式與命令，JEA 角色功能可協助限制該帳戶的用途。
設計不當的角色可能會允許執行危險命令，可能允許使用者突破 JEA 界限或取得機密資訊的存取權。

例如，請考慮下列角色功能項目：

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\*-Process'
}
```

此角色功能可讓使用者執行任何 PowerShell Cmdlet，並使用來自 Microsoft.PowerShell.Management 模組的名詞 "Process"。
使用者可能需要存取像是 `Get-Process` 的 Cmdlet，以了解什麼應用程式在系統上執行，並存取 `Stop-Process` 以終止任何停止回應的應用程式。
不過，此項目也允許 `Start-Process`，這可以用來以完整的系統管理員權限啟動任意程式。
程式不需要在本機系統上安裝，因此敵人可以在提供連線使用者本機系統管理員權限的檔案共用上啟動程式、執行惡意程式碼等等。

這項相同角色功能的更安全版本應該如下︰

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\Get-Process', 'Microsoft.PowerShell.Management\Stop-Process'
}
```

請避免在角色功能使用萬用字元，並且務必要定期[稽核有效的使用者權限](audit-and-report.md#check-effective-rights-for-a-specific-user)，以了解使用者可以存取哪些命令。

## <a name="jea-does-not-protect-against-admins"></a>JEA 無法防止系統管理員

JEA 的核心原則之一是它可讓非系統管理員執行「一些」管理工作。
JEA 無法防止已經有系統管理員權限的使用者。
屬於「網域系統管理員」、「本機系統管理員」或環境中其他高權限群組的使用者，仍然可以透過其他方式登入電腦，以避開 JEA 的保護。
例如，他們可以使用 RDP 登入、使用遠端 MMC 主控台或連接至未受限制的 PowerShell 端點。
系統上的本機系統管理員也可以修改 JEA 設定，允許其他使用者管理系統，或變更角色功能以擴充使用者可以在其 JEA 工作階段中執行的動作範圍。
因此務必要評估您的 JEA 使用者延伸權限，看看他們是否有其他方法可取得系統的特殊權限存取。

常見的做法是使用 JEA 進行一般日常維護，並且擁有「即時 」(Just-in-Time) 的特殊權限存取管理解決方案，可讓使用者在緊急情況下暫時成為本機系統管理員。
這有助於確保使用者在系統上不是永久的系統管理員，但如果 (並且唯有) 他們完成的工作流程會記錄他們對那些權限的使用，便可以取得那些權限。