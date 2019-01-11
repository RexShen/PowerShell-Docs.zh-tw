---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 在 PowerShell 遠端中進行第二次跳躍
ms.openlocfilehash: 06ca43e3e0524d89ec6f66f6553c4c75072beaf3
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400725"
---
# <a name="making-the-second-hop-in-powershell-remoting"></a>在 PowerShell 遠端中進行第二次跳躍

「第二個躍點問題」是指如下所示的情況︰

1. 您已登入 _ServerA_。
2. 從 _ServerA_，啟動遠端 PowerShell 工作階段，連線到 _ServerB_。
3. 您透過 PowerShell 遠端工作階段在 _ServerB_ 上執行的命令，會嘗試存取 _ServerC_ 上的資源。
4. 已拒絕 _ServerC_ 上的資源存取，因為您用來建立 PowerShell 遠端工作階段的認證未從 _ServerB_ 傳遞至 _ServerC_。

解決這個問題的方法有數種︰ 在本主題中，我們將探討幾個最受歡迎的第二個躍點問題解決方案。

## <a name="credssp"></a>CredSSP

您可以使用[認證安全性支援提供者 (CredSSP)](https://msdn.microsoft.com/library/windows/desktop/bb931352.aspx) 進行驗證。 CredSSP 會在遠端伺服器上快取認證 (_ServerB_)，因此在使用時，可能會讓您暴露在認證遭竊的攻擊風險中。 如果遠端電腦遭到入侵，攻擊者就能存取使用者的認證。 預設會停用 CredSSP (用戶端與伺服器電腦皆是)。 只有在最受信任的環境中才應啟用 CredSSP。 例如，因為網域控制站為高度受信任，所以網域系統管理員會連線到網域控制站。

如需有關使用 CredSSP 進行 PowerShell 遠端時的安全性考量的詳細資訊，請參閱[意外破壞︰請注意 CredSSP](https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp)。

如需認證遭竊攻擊的詳細資訊，請參閱[降低傳遞雜湊 (PtH) 攻擊與竊取其他認證](https://www.microsoft.com/en-us/download/details.aspx?id=36036)。

如需如何啟用及使用 CredSSP 進行 PowerShell 遠端功能的範例，請參閱 [Using CredSSP to solve the second-hop problem](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/) (使用 CredSSP 來解決第二個躍點問題)。

### <a name="pros"></a>優點

- 這適用於 Windows Server 2008 或更新版本的所有伺服器。

### <a name="cons"></a>缺點

- 有安全性弱點。
- 需要同時設定用戶端和伺服器角色。

## <a name="kerberos-delegation-unconstrained"></a>Kerberos 委派 (未受限)

您也可以使用 Kerberos 未受限制的委派進行第二次跳躍。 不過，這個方法無法控制委派認證的使用位置。

>**注意：** 無法委派已設定 [這是機密帳戶，無法委派] 屬性的 Active Directory 帳戶。 如需詳細資訊，請參閱[安全性焦點：特殊權限帳戶分析 '是機密帳戶，無法委派'](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/)和[Kerberos 驗證工具和設定](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)

### <a name="pros"></a>優點

- 不需要任何特殊的程式碼。

### <a name="cons"></a>缺點

- 不支援 WinRM 的第二個躍點。
- 無法控制認證的使用位置，造成安全性漏洞。

## <a name="kerberos-constrained-delegation"></a>Kerberos 限制委派

您可以使用舊版的限制委派 (不以資源為基礎) 來進行第二次跳躍。

>**注意：** 無法委派已設定 [這是機密帳戶，無法委派] 屬性的 Active Directory 帳戶。 如需詳細資訊，請參閱[安全性焦點：特殊權限帳戶分析 '是機密帳戶，無法委派'](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/)和[Kerberos 驗證工具和設定](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)

### <a name="pros"></a>優點

- 不需要任何特殊的程式碼

### <a name="cons"></a>缺點

- 不支援 WinRM 的第二個躍點。
- 必須在遠端伺服器 (_ServerB_) 的 Active Directory 物件上設定。
- 僅限一個網域。 無法跨網域或樹系。
- 需要更新物件和服務主體名稱 (SPN) 的權限。

## <a name="resource-based-kerberos-constrained-delegation"></a>以資源為基礎的 Kerberos 限制委派

使用以資源為基礎的 Kerberos 限制委派 (在 Windows Server 2012 中引入) 時，您會設定資源所在伺服器物件上的認證委派。
在上述的第二個躍點案例中，您會設定 _ServerC_ 以指定它接受委派認證的來源。

>**注意：** 無法委派已設定 [這是機密帳戶，無法委派] 屬性的 Active Directory 帳戶。 如需詳細資訊，請參閱[安全性焦點：特殊權限帳戶分析 '是機密帳戶，無法委派'](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/)和[Kerberos 驗證工具和設定](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)

### <a name="pros"></a>優點

- 不會儲存認證。
- 使用 PowerShell Cmdlet 進行設定相當容易 -- 不需要特殊的程式碼。
- 不需要任何特殊網域存取。
- 可跨網域與樹系工作。
- PowerShell 程式碼。

### <a name="cons"></a>缺點

- 需要 Windows Server 2012 或更新版本。
- 不支援 WinRM 的第二個躍點。
- 需要更新物件和服務主體名稱 (SPN) 的權限。

### <a name="example"></a>範例

讓我們看看在 _ServerC_ 上設定以資源為基礎之限制委派的 PowerShell 範例，以允許來自 _ServerB_ 的委派認證。
這個範例會假設所有伺服器都執行 Windows Server 2012 或更新版本，而且任何伺服器所屬的每個網域都有至少一個 Windows Server 2012 網域控制站。

您必須先新增 `RSAT-AD-PowerShell` 功能以安裝 Active Directory PowerShell 模組，然後將該模組匯入到您的工作階段，之後才能設定限制委派︰

```powershell
PS C:\> Add-WindowsFeature RSAT-AD-PowerShell

PS C:\> Import-Module ActiveDirectory
```
數個可用的 Cmdlet 現在有 **PrincipalsAllowedToDelegateToAccount** 參數︰

```powershell
PS C:\> Get-Command -ParameterName PrincipalsAllowedToDelegateToAccount

CommandType Name                 ModuleName
----------- ----                 ----------
Cmdlet      New-ADComputer       ActiveDirectory
Cmdlet      New-ADServiceAccount ActiveDirectory
Cmdlet      New-ADUser           ActiveDirectory
Cmdlet      Set-ADComputer       ActiveDirectory
Cmdlet      Set-ADServiceAccount ActiveDirectory
Cmdlet      Set-ADUser           ActiveDirectory
```

**PrincipalsAllowedToDelegateToAccount** 參數會設定 Active Directory 物件屬性 **msDS-AllowedToActOnBehalfOfOtherIdentity**，其中包含存取控制清單 (ACL)，指定哪些帳戶有權可委派認證給相關聯的帳戶 (在本例中，它會是 _Server_ 的電腦帳戶)。

現在，讓我們設定將用來代表伺服器的變數︰

```powershell
# Set up variables for reuse
$ServerA = $env:COMPUTERNAME
$ServerB = Get-ADComputer -Identity ServerB
$ServerC = Get-ADComputer -Identity ServerC
```

WinRM (以及 PowerShell 遠端) 預設會以電腦帳戶的身分執行。 您可以檢視 `winrm` 服務的 **StartName** 屬性來看到這點︰

```powershell
PS C:\> Get-WmiObject win32_service -filter 'name="winrm"' | Format-List StartName

StartName : NT AUTHORITY\NetworkService
```

為了讓 _ServerC_ 從 _ServerB_ 上的 PowerShell 遠端工作階段允許委派，我們會藉由將 _ServerC_ 上的 **PrincipalsAllowedToDelegateToAccount** 參數設為 _ServerB_ 的電腦物件來授與存取權：

```powershell
# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB

# Check the value of the attribute directly
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access

# Check the value of the attribute indirectly
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

Kerberos [金鑰發行中心 (KDC)](https://msdn.microsoft.com/library/windows/desktop/aa378170(v=vs.85).aspx) 會快取遭拒的存取嘗試達 15 分鐘 (負快取)。 如果 _ServerB_ 先前曾嘗試存取 _ServerC_，您必須叫用下列命令清除 _ServerB_ 上的快取︰

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

在此範例中，`$using` 變數用來使 _ServerB_ 可看見 `$ServerC` 變數。 如需 `$using` 變數的詳細資訊，請參閱 [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx)。

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

- [Kerberos 驗證的新功能](https://technet.microsoft.com/library/hh831747.aspx)
- [How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1](https://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1) (Windows Server 2012 如何緩解 Kerberos 限制委派的痛苦，第 1 部分)
- [How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 2](https://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2) (Windows Server 2012 如何緩解 Kerberos 限制委派的痛苦，第 2 部分)
- [了解使用整合式 Windows 驗證之 Azure Active Directory 應用程式 Proxy 部署的 Kerberos 限制委派](https://aka.ms/kcdpaper)
- [[MS-ADA2]:Active Directory 架構屬性 M2.210 Attribute msDS AllowedToActOnBehalfOfOtherIdentity](https://msdn.microsoft.com/library/hh554126.aspx)
- [[MS-SFU]: Kerberos Protocol Extensions: Service for User and Constrained Delegation Protocol 1.3.2 S4U2Proxy](https://msdn.microsoft.com/library/cc246079.aspx) ([MS-SFU]：Kerberos 通訊協定延伸模組：Service for User 與限制委派通訊協定 1.3.2 S4U2Proxy)
- [Resource Based Kerberos Constrained Delegation](https://blog.kloud.com.au/2013/07/11/kerberos-constrained-delegation/) (以資源為基礎的 Kerberos 限制委派)
- [Remote Administration Without Constrained Delegation Using PrincipalsAllowedToDelegateToAccount](https://blogs.msdn.microsoft.com/taylorb/2012/11/06/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount/) (使用 PrincipalsAllowedToDelegateToAccount 進行遠端系統管理，而不需要限制委派)

## <a name="pssessionconfiguration-using-runas"></a>使用 RunAs 的 PSSessionConfiguration

您可以在 _ServerB_ 上建立工作階段設定，並設定其 **RunAsCredential** 參數。

如需使用 PSSessionConfiguration 和 RunAs 來解決第二個躍點問題的資訊，請參閱 [Another solution to multi-hop PowerShell remoting](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/) (PowerShell 遠端進行多重躍點的另一個解決方案)。

### <a name="pros"></a>優點

- 適用於 WMF 3.0 或更新版本的任何伺服器。

### <a name="cons"></a>缺點

- 需要在每個中繼伺服器 (_ServerB_) 設定 **PSSessionConfiguration** 和 **RunAs**。
- 使用網域 **RunAs** 帳戶時需要密碼維護

## <a name="just-enough-administration-jea"></a>Just Enough Administration (JEA)

JEA 可讓您限制系統管理員可以在 PowerShell 工作階段期間執行哪些命令。 它可以用來解決第二個躍點問題。

如需 JEA 的資訊，請參閱 [Just Enough Administration](https://docs.microsoft.com/powershell/jea/overview)。

### <a name="pros"></a>優點

- 使用虛擬帳戶時不需要密碼維護。

### <a name="cons"></a>缺點

- 需要 WMF 5.0 或更新版本。
- 需要在每個中繼伺服器 (_ServerB_) 上設定。

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a>在 Invoke-Command 指令碼區塊內傳遞認證

您可以在呼叫 [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) Cmdlet 的 **ScriptBlock** 參數內傳遞認證。

### <a name="pros"></a>優點

- 不需要特殊的伺服器設定。
- 適用於執行 WMF 2.0 或更新版本的任何伺服器。

### <a name="cons"></a>缺點

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