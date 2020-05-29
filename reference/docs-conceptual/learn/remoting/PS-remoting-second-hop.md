---
ms.date: 05/14/2020
keywords: powershell,cmdlet
title: 在 PowerShell 遠端中進行第二次跳躍
ms.openlocfilehash: 3a9db11726d4c02dc69e52c45da304f7422def39
ms.sourcegitcommit: 843756c8277e7afb874867703963248abc8a6c91
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2020
ms.locfileid: "83439371"
---
# <a name="making-the-second-hop-in-powershell-remoting"></a>在 PowerShell 遠端中進行第二次跳躍

「第二個躍點問題」是指如下所示的情況︰

1. 您已登入 _ServerA_。
2. 從 _ServerA_，啟動遠端 PowerShell 工作階段，連線到 _ServerB_。
3. 您透過 PowerShell 遠端工作階段在 _ServerB_ 上執行的命令，會嘗試存取 _ServerC_ 上的資源。
4. 已拒絕 _ServerC_ 上的資源存取，因為您用來建立 PowerShell 遠端工作階段的認證未從 _ServerB_ 傳遞至 _ServerC_。

解決這個問題的方法有數種︰ 下表依喜好設定的順序列出方法。

|                      組態                       |                                  附註                                  |
| -------------------------------------------------------- | ---------------------------------------------------------------------- |
| CredSSP                                                  | 簡單易用與安全性兼具                                      |
| 以資源為基礎的 Kerberos 限制委派           | 設定更加簡單，安全性更高                             |
| Kerberos 限制委派                          | 安全性高，但需要網域系統管理員                         |
| Kerberos 委派 (未受限)                      | 不建議使用                                                        |
| Just Enough Administration (JEA)                         | 安全性最高，但需要更詳細的設定 |
| 使用 RunAs 的 PSSessionConfiguration                       | 比較容易設定，但需要認證管理                |
| 在 `Invoke-Command` 指令碼區塊內傳遞認證 | 用法最簡單，但必須提供認證                       |

## <a name="credssp"></a>CredSSP

您可以使用[認證安全性支援提供者 (CredSSP)][credssp] 進行驗證。
CredSSP 會在遠端伺服器上快取認證 (_ServerB_)，因此在使用時，可能會讓您暴露在認證遭竊的攻擊風險中。 如果遠端電腦遭到入侵，攻擊者就能存取使用者的認證。 預設會停用 CredSSP (用戶端與伺服器電腦皆是)。 只有在最受信任的環境中才應啟用 CredSSP。 例如，因為網域控制站為高度受信任，所以網域系統管理員會連線到網域控制站。

如需使用 PowerShell 遠端的 CredSSP 時，安全性考量的詳細資訊，請參閱[意外妨害：注意 CredSSP][beware] \(英文\)。

如需認證遭竊攻擊的詳細資訊，請參閱[降低傳遞雜湊 (PtH) 攻擊與竊取其他認證][pth]。

如需有關如何啟用及使用 CredSSP 來進行 PowerShell 遠端處理的範例，請參閱 [使用 CredSSP 來啟用 PowerShell "Second-Hop" 功能][credssp-psblog] \(英文\)。

**優點**

- 這適用於 Windows Server 2008 或更新版本的所有伺服器。

**缺點**

- 有安全性弱點。
- 需要同時設定用戶端和伺服器角色。
- 無法搭配受保護的使用者群組一起使用。 如需詳細資訊，請參閱[受保護的使用者安全性群組][protected-users] (英文)。

## <a name="kerberos-constrained-delegation"></a>Kerberos 限制委派

您可以使用舊版的限制委派 (不以資源為基礎) 來進行第二次跳躍。 請以 [使用任何驗證通訊協定] 選項設定 Kerberos 限制委派，以允許進行通訊協定轉換。

**優點**

- 不需要任何特殊的程式碼
- 不會儲存認證。

**缺點**

- 不支援 WinRM 的第二個躍點。
- 需要網域系統管理員的權限才能設定。
- 必須在遠端伺服器 (_ServerB_) 的 Active Directory 物件上設定。
- 僅限一個網域。 無法跨網域或樹系。
- 需要更新物件和服務主體名稱 (SPN) 的權限。
- _ServerB_ 不需要使用者操作，就能直接代表使用者，將 Kerberos 票證擷取至 _ServerC_。

> [!NOTE]
> 無法委派已設定 [這是機密帳戶，無法委派] 屬性的 Active Directory 帳戶。 如需詳細資訊，請參閱[安全性焦點：分析特殊權限帳戶的「這是機密帳戶，無法委派」][blog] \(英文\) 和 [Kerberos 驗證工具和設定][ktools] \(英文\)

## <a name="resource-based-kerberos-constrained-delegation"></a>以資源為基礎的 Kerberos 限制委派

使用以資源為基礎的 Kerberos 限制委派 (在 Windows Server 2012 中引入) 時，您會設定資源所在伺服器物件上的認證委派。 在上述第二個躍點情節中，您設定了 _ServerC_，以指定其接受之委派認證的來源。

**優點**

- 不會儲存認證。
- 使用 PowerShell Cmdlet 設定。 無須任何特殊程式碼。
- 無須網域系統管理員的權限就能設定。
- 可跨網域與樹系工作。

**缺點**

- 需要 Windows Server 2012 或更新版本。
- 不支援 WinRM 的第二個躍點。
- 需要更新物件和服務主體名稱 (SPN) 的權限。

> [!NOTE]
> 無法委派已設定 [這是機密帳戶，無法委派] 屬性的 Active Directory 帳戶。 如需詳細資訊，請參閱[安全性焦點：分析特殊權限帳戶的「這是機密帳戶，無法委派」][blog] \(英文\) 和 [Kerberos 驗證工具和設定][ktools] \(英文\)

### <a name="example"></a>範例

下列 PowerShell 範例昦 _ServerC_ 上，設定以資源型的限制式委派，以允許來自 _ServerB_ 的委派認證，現在讓我們一起來看看。 這個範例會假設所有伺服器都執行 Windows Server 2012 或更新版本，而且任何伺服器所屬的每個網域都有至少一個 Windows Server 2012 網域控制站。

您必須先新增 `RSAT-AD-PowerShell` 功能以安裝 Active Directory PowerShell 模組，然後將該模組匯入到您的工作階段，之後才能設定限制委派︰

```powershell
Add-WindowsFeature RSAT-AD-PowerShell
Import-Module ActiveDirectory
Get-Command -ParameterName PrincipalsAllowedToDelegateToAccount
```

數個可用的 Cmdlet 現在有 **PrincipalsAllowedToDelegateToAccount** 參數︰

```Output
CommandType Name                 ModuleName
----------- ----                 ----------
Cmdlet      New-ADComputer       ActiveDirectory
Cmdlet      New-ADServiceAccount ActiveDirectory
Cmdlet      New-ADUser           ActiveDirectory
Cmdlet      Set-ADComputer       ActiveDirectory
Cmdlet      Set-ADServiceAccount ActiveDirectory
Cmdlet      Set-ADUser           ActiveDirectory
```

**PrincipalsAllowedToDelegateToAccount** 參數會設定 Active Directory 物件屬性 **msDS-AllowedToActOnBehalfOfOtherIdentity**，此屬性包含存取控制清單 (ACL)，指定哪些帳戶有權委派認證給相關聯的帳戶 (在本例中是 _ServerA_ 的電腦帳戶)。

現在，讓我們設定將用來代表伺服器的變數︰

```powershell
# Set up variables for reuse
$ServerA = $env:COMPUTERNAME
$ServerB = Get-ADComputer -Identity ServerB
$ServerC = Get-ADComputer -Identity ServerC
```

WinRM (以及 PowerShell 遠端) 預設會以電腦帳戶的身分執行。 您可以檢視 `winrm` 服務的 **StartName** 屬性來看到這點︰

```powershell
Get-CimInstance Win32_Service -Filter 'Name="winrm"' | Select-Object StartName
```

```Output
StartName
---------
NT AUTHORITY\NetworkService
```

為了讓 _ServerC_ 允許來自 _ServerB_ 之 PowerShell 遠端工作階段的委派，我們必須在 _ServerC_ 上，將 **PrincipalsAllowedToDelegateToAccount** 參數設為 _ServerB_ 的電腦物件：

```powershell
# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB

# Check the value of the attribute directly
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access

# Check the value of the attribute indirectly
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

Kerberos [金鑰發佈中心 (KDC)](/windows/win32/secauthn/key-distribution-center) 會快取拒絕存取的存取嘗試 (負快取) 達 15 分鐘。 如果 _ServerB_ 先前曾嘗試存取 _ServerC_，您必須叫用下列命令清除 _ServerB_ 上的快取︰

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    klist purge -li 0x3e7
}
```

您也可以重新啟動電腦，或等待至少 15 分鐘的時間以清除快取。

清除快取之後，便可以成功執行程式碼，從 _ServerA_ 經過 _ServerB_ 再到 _ServerC_：

```powershell
# Capture a credential
$cred = Get-Credential Contoso\Alice

# Test kerberos double hop
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    Test-Path \\$($using:ServerC.Name)\C$
    Get-Process lsass -ComputerName $($using:ServerC.Name)
    Get-EventLog -LogName System -Newest 3 -ComputerName $($using:ServerC.Name)
}
```

在此範例中，`$using` 變數用來使 _ServerB_ 可看見 `$ServerC` 變數。
如需 `$using` 變數的詳細資訊，請參閱 [about_Remote_Variables](/powershell/module/Microsoft.PowerShell.Core/About/about_Remote_Variables)。

若要允許多部伺服器委派認證給 _ServerC_，請將 _ServerC_ 上 **PrincipalsAllowedToDelegateToAccount** 參數的值設為陣列︰

```powershell
# Set up variables for each server
$ServerB1 = Get-ADComputer -Identity ServerB1
$ServerB2 = Get-ADComputer -Identity ServerB2
$ServerB3 = Get-ADComputer -Identity ServerB3
$ServerC  = Get-ADComputer -Identity ServerC

# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC `
    -PrincipalsAllowedToDelegateToAccount @($ServerB1,$ServerB2,$ServerB3)
```

如果您想要進行跨網域的第二次跳躍，請新增 _ServerB_ 所屬網域的網域控制站完整網域名稱 (FQDN)︰

```powershell
# For ServerC in Contoso domain and ServerB in other domain
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com
$ServerC = Get-ADComputer -Identity ServerC
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

若要移除委派認證給 ServerC 的能力，請將 _ServerC_ 上 **PrincipalsAllowedToDelegateToAccount** 參數的值設為 `$null`︰

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a>以資源為基礎的 Kerberos 限制委派相關資訊

- [Kerberos 驗證的新功能][whats-new]
- [How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1][kcd2012-1] (Windows Server 2012 如何緩解 Kerberos 限制委派的痛苦，第 1 部分)
- [How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 2][kcd2012-2] (Windows Server 2012 如何緩解 Kerberos 限制委派的痛苦，第 2 部分)
- [了解使用整合式 Windows 驗證之 Azure Active Directory 應用程式 Proxy 部署的 Kerberos 限制委派][kcdpaper]
- [[MS-ADA2] Active Directory Schema Attributes M2.210 Attribute msDS-AllowedToActOnBehalfOfOtherIdentity][MS-ADA2] ([MS-ADA2] Active Directory 結構描述屬性 M2.210 屬性 msDS-AllowedToActOnBehalfOfOtherIdentity)
- [[MS-SFU] Kerberos 通訊協定延伸模組：Service for User 與限制委派通訊協定 1.3.2 S4U2Proxy][MS-SFU] \(英文\)
- [Remote Administration Without Constrained Delegation Using PrincipalsAllowedToDelegateToAccount][remote-admin] (使用 PrincipalsAllowedToDelegateToAccount 進行遠端系統管理，而不需要限制委派)

## <a name="kerberos-delegation-unconstrained"></a>Kerberos 委派 (未受限)

您也可以使用 Kerberos 未受限制的委派進行第二次跳躍。 如同所有 Kerberos 案例一樣，認證不予儲存。 此方法不支援 WinRM 的第二個躍點。

> [!WARNING]
> 此方法無法控制委派認證的使用位置， 而且安全性低於 CredSSP。 此方法只適用於測試案例。

## <a name="just-enough-administration-jea"></a>Just Enough Administration (JEA)

JEA 可讓您限制系統管理員可以在 PowerShell 工作階段期間執行哪些命令。 它可以用來解決第二個躍點問題。

如需 JEA 的資訊，請參閱 [Just Enough Administration](/powershell/scripting/learn/remoting/jea/overview)。

**優點**

- 使用虛擬帳戶時不需要密碼維護。

**缺點**

- 需要 WMF 5.0 或更新版本。
- 需要在每個中繼伺服器 (_ServerB_) 上設定。

## <a name="pssessionconfiguration-using-runas"></a>使用 RunAs 的 PSSessionConfiguration

您可以在 _ServerB_ 上建立工作階段設定，並設定其 **RunAsCredential** 參數。

如需使用 **PSSessionConfiguration** 與 **RunAs** 來解決第二個躍點問題的資訊，請參閱[另一種解決 PowerShell 遠端多個躍點問題的方法][pssessionconfig]。

**優點**

- 適用於 WMF 3.0 或更新版本的任何伺服器。

**缺點**

- 需要在每個中繼伺服器 (_ServerB_) 設定 **PSSessionConfiguration** 和 **RunAs**。
- 使用網域 **RunAs** 帳戶時需要密碼維護

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a>在 Invoke-Command 指令碼區塊內傳遞認證

您可以在呼叫 [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) Cmdlet 的 **ScriptBlock** 參數內傳遞認證。

**優點**

- 不需要特殊的伺服器設定。
- 適用於執行 WMF 2.0 或更新版本的任何伺服器。

**缺點**

- 需要使用不便的程式碼技巧。
- 如果執行 WMF 2.0，需要不同的語法以便傳遞引數至遠端工作階段。

### <a name="example"></a>範例

下列範例示範如何在 **Invoke-Command** 指令碼區塊中傳遞認證︰

```powershell
# This works without delegation, passing fresh creds
# Note $Using:Cred in nested request
$cred = Get-Credential Contoso\Administrator
Invoke-Command -ComputerName ServerB -Credential $cred -ScriptBlock {
    hostname
    Invoke-Command -ComputerName ServerC -Credential $Using:cred -ScriptBlock {hostname}
}
```

## <a name="see-also"></a>另請參閱

[PowerShell 遠端安全性考量](WinRMSecurity.md)

<!-- link references -->
[blog]: /archive/blogs/poshchap/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts
[ktools]: /previous-versions/windows/it-pro/windows-server-2003/cc738673(v=ws.10)
[credssp]: /windows/win32/secauthn/credential-security-support-provider
[beware]: https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp
[pth]: https://www.microsoft.com/download/details.aspx?id=36036
[credssp-psblog]: https://devblogs.microsoft.com/scripting/enable-powershell-second-hop-functionality-with-credssp/
[whats-new]: /previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831747(v=ws.11)
[kcd2012-1]: https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1
[kcd2012-2]: https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2
[kcdpaper]: https://aka.ms/kcdpaper
[MS-ADA2]: /openspecs/windows_protocols/ms-ada2/cea4ac11-a4b2-4f2d-84cc-aebb4a4ad405
[MS-SFU]: /openspecs/windows_protocols/ms-sfu/bde93b0e-f3c9-4ddf-9f44-e1453be7af5a
[remote-admin]: /archive/blogs/taylorb/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount
[pssessionconfig]: /archive/blogs/sergey_babkins_blog/another-solution-to-multi-hop-powershell-remoting
[protected-users]: /windows-server/security/credentials-protection-and-management/protected-users-security-group
