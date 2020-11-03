---
description: 憑證
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/about/about_certificate_provider?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 憑證提供者
ms.openlocfilehash: b3ac701f18ba57d9108a76b7c478b8514075b3ee
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207276"
---
# <a name="certificate-provider"></a>憑證提供者

## <a name="provider-name"></a>提供者名稱

憑證

## <a name="drives"></a>磁碟機

`Cert:`

## <a name="capabilities"></a>功能

**ShouldProcess**

## <a name="short-description"></a>簡短描述

提供 PowerShell 中 x.509 憑證存放區和憑證的存取權。

## <a name="detailed-description"></a>詳細描述

PowerShell **憑證** 提供者可讓您在 powershell 中取得、新增、變更、清除和刪除憑證和憑證存放區。

**憑證** 磁片磁碟機是階層式命名空間，其中包含您電腦上的憑證存放區和憑證。

**憑證** 提供者支援下列 Cmdlet，這些 Cmdlet 將在本文中討論。

- [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location)
- [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)
- [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [Invoke-Item](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [Move-Item](xref:Microsoft.PowerShell.Management.Move-Item)
- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)
- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Get-ItemProperty](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [Clear-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [Get-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Get-AuthenticodeSignature)
- [Set-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

## <a name="types-exposed-by-this-provider"></a>此提供者公開的類型

憑證磁片磁碟機會公開下列類型。

-  (Microsoft.powershell.commands.x509storelocation) 的商店位置，也就是高階容器，可將目前使用者和所有使用者的憑證組成群組。 每個系統都有 CurrentUser 和 LocalMachine (所有使用者) 存放區位置。

- 憑證會儲存 (System.security.cryptography.x509certificates.x509certificate2. System.security.cryptography.x509certificates.x509store) ，也就是儲存和管理憑證的實體存放區。

- X.509 **system.security.cryptography.x509certificates.x509certificate2. X509Certificate2** 憑證，每個憑證都代表電腦上的一個 x.509 憑證。
  憑證是由其指紋來識別。

## <a name="navigating-the-certificate-drive"></a>流覽憑證磁片磁碟機

**憑證** 提供者會將憑證命名空間公開為 `Cert:` PowerShell 中的磁片磁碟機。 此命令會使用 `Set-Location` 命令將目前的位置變更為 LocalMachine 存放區位置中的根憑證存放區。 使用反斜線 (\\) 或正斜線 (/) 來指出磁片磁碟機的層級 `Cert:` 。

```powershell
Set-Location Cert:
```

您也可以使用其他任何 PowerShell 磁片磁碟機中的憑證提供者。 若要從其他位置參照別名，請 `Cert:` 在路徑中使用磁片磁碟機名稱。

```powershell
PS Cert:\> Set-Location -Path LocalMachine\Root
```

若要返回檔案系統磁碟機，請輸入磁碟機名稱。 例如，輸入：

```powershell
Set-Location C:
```

> [!NOTE]
> PowerShell 會使用別名，讓您有熟悉的方式來處理提供者路徑。 和等命令 `dir` `ls` 現在是 [get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)的別名， `cd` 它是 [設定位置](xref:Microsoft.PowerShell.Management.Set-Location)的別名。
> 和 `pwd` 是 [取得位置](xref:Microsoft.PowerShell.Management.Get-Location)的別名。

## <a name="displaying-the-contents-of-the-cert-drive"></a>顯示 Cert：磁片磁碟機的內容

此命令會使用 `Get-ChildItem` Cmdlet 來顯示 CurrentUser 憑證存放區位置中的憑證存放區。

如果您不在 `Cert:` 磁片磁碟機中，請使用絕對路徑。

```powershell
PS Cert:\CurrentUser\> Get-ChildItem
```

### <a name="displaying-certificate-properties-within-the-cert-drive"></a>顯示 Cert：磁片磁碟機內的憑證屬性

這個範例會取得具有的憑證 `Get-Item` ，並將它儲存在變數中。
此範例會使用 ( **DnsNameList** 、 **EnhancedKeyUsageList** 、 **SendAsTrustedIssuer** ) 來顯示新的憑證腳本屬性 `Select-Object` 。

```powershell
$c = Get-Item cert:\LocalMachine\My\52A149D0393CE8A8D4AF0B172ED667A9E3A1F44E
$c | Format-List DnsNameList, EnhancedKeyUsageList, SendAsTrustedIssuer
```

```output
DnsNameList          : {SERVER01.contoso.com}
EnhancedKeyUsageList : {WiFi-Machine (1.3.6.1.4.1.311.42.2.6),
                       Client Authentication (1.3.6.1.5.5.7.3.2)}
SendAsTrustedIssuer  : False
```

### <a name="find-all-codesigning-certificates"></a>尋找所有 CodeSigning 的憑證

此命令會使用 Cmdlet 的 **CodeSigningCert** 和 **遞迴** 參數 `Get-ChildItem` 來取得電腦上具有程式碼簽署授權單位的所有憑證。

```powershell
Get-ChildItem -Path cert: -CodeSigningCert -Recurse
```

### <a name="find-expired-certificates"></a>尋找過期的憑證

此命令會使用 Cmdlet 的 **ExpiringInDays** 參數 `Get-ChildItem` 來取得將在接下來的30天內到期的憑證。

```powershell
Get-ChildItem -Path cert:\LocalMachine\WebHosting -ExpiringInDays 30
```

### <a name="find-server-ssl-certificates"></a>尋找伺服器 SSL 憑證

此命令會使用 Cmdlet 的 **SSLServerAuthentication** 參數 `Get-ChildItem` 來取得 My 和 WebHosting 存放區中的所有伺服器 SSL 憑證。

```powershell
Get-ChildItem -Path cert:\LocalMachine\My, cert:\LocalMachine\WebHosting `
  -SSLServerAuthentication
```

### <a name="find-expired-certificates-on-remote-computers"></a>在遠端電腦上尋找過期的憑證

此命令會使用 `Invoke-Command` Cmdlet `Get-ChildItem` 在 Srv01 和 Srv02 電腦上執行命令。 **ExpiringInDays** 參數中零 (0) 的值會取得已過期之 Srv01 和 Srv02 電腦上的憑證。

```powershell
Invoke-Command -ComputerName Srv01, Srv02 {Get-ChildItem -Path cert:\* `
  -Recurse -ExpiringInDays 0}
```

### <a name="combining-filters-to-find-a-specific-set-of-certificates"></a>結合篩選器來尋找一組特定的憑證

此命令會取得 LocalMachine 存放區位置中具有下列屬性的所有憑證：

- 其 DNS 名稱中的 "fabrikam"
- EKU 中的「用戶端驗證」
- `$true` **SendAsTrustedIssuer** 屬性的值
- 在接下來的30天內不會過期。

**NotAfter** 屬性會儲存憑證到期日。

```powershell
[DateTime] $ValidThrough = (Get-Date) + (New-TimeSpan -Days 30)
Get-ChildItem -Path cert:\* -Recurse -DNSName "*fabrikam*" `
  -EKU "*Client Authentication*" | Where-Object {
                                     $_.SendAsTrustedIssuer -and `
                                     $_.NotAfter -gt $ValidThrough
                                   }
```

## <a name="opening-the-certificates-mmc-snap-in"></a>開啟憑證 MMC 嵌入式管理單元

此 `Invoke-Item` Cmdlet 會使用預設的應用程式來開啟您指定的路徑。 若為憑證，則預設應用程式是 [憑證] MMC 嵌入式管理單元。

此命令會開啟 [憑證] MMC 嵌入式管理單元來管理指定的憑證。

```powershell
Invoke-Item cert:\CurrentUser\my\6B8223358119BB08840DEE50FD8AF9EA776CE66B
```

## <a name="copying-certificates"></a>複製憑證

**憑證** 提供者不支援複製憑證。 當您嘗試複製憑證時，您會看到此錯誤。

```
$path = "Cert:\LocalMachine\Root\E2C0F6662D3C569705B4B31FE2CBF3434094B254"
PS Cert:\LocalMachine\> Copy-Item -Path $path -Destination .\CA\
Copy-Item : Provider operation stopped because the provider does not support
this operation.
At line:1 char:1
+ Copy-Item -Path $path -Destination .\CA\
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotImplemented: (:) [Copy-Item],
                              PSNotSupportedException
    + FullyQualifiedErrorId : NotSupported,
                              Microsoft.PowerShell.Commands.CopyItemCommand
```

## <a name="moving-certificates"></a>移動憑證

### <a name="move-all-ssl-server-authentication-certs-to-the-webhosting-store"></a>將所有 SSL 伺服器驗證憑證移至 WebHosting 存放區

此命令會使用 `Move-Item` Cmdlet，將憑證從「我的存放區」移至 WebHosting 存放區。

`Move-Item` 將不會移動憑證存放區，而且不會將憑證移動至不同的存放區位置，例如，將憑證從 LocalMachine 移至 CurrentUser。 `Move-Item`Cmdlet 會移動憑證，但不會移動私密金鑰。

此命令會使用 Cmdlet 的 **SSLServerAuthentication** 參數 `Get-ChildItem` 來取得「我的」憑證存放區中的 SSL 伺服器驗證憑證。

傳回的憑證會透過管道傳送至 `Move-Item` Cmdlet，此 Cmdlet 會將憑證移至 WebHosting 存放區。

```powershell
Get-ChildItem cert:\LocalMachine\My -SSLServerAuthentication | Move-Item `
  -Destination cert:\LocalMachine\WebHosting
```

## <a name="deleting-certificates-and-private-keys"></a>刪除憑證和私密金鑰

此 `Remove-Item` Cmdlet 會移除您指定的憑證。 `-DeleteKey`動態參數會刪除私密金鑰。

### <a name="delete-a-certificate-from-the-ca-store"></a>從 CA 存放區刪除憑證

此命令會從 CA 憑證存放區刪除憑證，但會原封不動地保留相關聯的私密金鑰。

在 `Cert:` 磁片磁碟機中，此 `Remove-Item` Cmdlet 只支援 **DeleteKey** 、 **Path** 、 **WhatIf** 和 **Confirm** 參數。 會忽略所有其他參數。

```powershell
Remove-Item cert:\LocalMachine\CA\5DDC44652E62BF9AA1116DC41DE44AB47C87BDD0
```

### <a name="delete-a-certificate-using-a-wildcards-in-the-dns-name"></a>使用 DNS 名稱中的萬用字元刪除憑證

此命令會刪除 DNS 名稱包含 "Fabrikam" 的所有憑證。 它會使用 Cmdlet 的 **DNSName** 參數 `Get-ChildItem` 來取得憑證，並使用 `Remove-Item` Cmdlet 來刪除它們。

```powershell
Get-ChildItem -Path cert:\LocalMachine -DnsName *Fabrikam* | Remove-Item
```

### <a name="delete-private-keys-from-a-remote-computer"></a>從遠端電腦刪除私密金鑰

這一系列的命令會啟用委派，然後刪除遠端電腦上的憑證和相關聯的私密金鑰。 若要刪除遠端電腦上的私密金鑰，您必須使用委派的認證。

使用 `Enable-WSManCredSSP` Cmdlet 在 S1 遠端電腦上的用戶端上，啟用 (CredSSP) 驗證的認證安全性服務提供者。
CredSSP 允許委派的驗證。

```powershell
Enable-WSManCredSSP -Role Client -DelegateComputer S1
```

使用 `Connect-WSMan` Cmdlet 將 S1 電腦連接到本機電腦上的 WinRM 服務。 當此命令完成時，S1 電腦會出現在 PowerShell 的本機 `WSMan:` 磁片磁碟機中。

```powershell
Connect-WSMan -ComputerName S1 -Credential Domain01\Admin01
```

現在，您可以使用 WSMan：磁片磁碟機中的 Set-Item Cmdlet，來啟用 WinRM 服務的 CredSSP 屬性。

```powershell
Set-Item -Path WSMan:\S1\Service\Auth\CredSSP -Value $true
```

使用 Cmdlet 在 s1 電腦上啟動遠端會話 `New-PSSession` ，並指定 CredSSP 驗證。 將會話儲存在 `$s` 變數中。

```powershell
$s  = New-PSSession S1 -Authentication CredSSP -Credential Domain01\Admin01
```

最後，使用 `Invoke-Command` Cmdlet 在 `Remove-Item` 變數的會話中執行命令 `$s` 。 此 `Remove-Item` 命令會使用 **DeleteKey** 參數來移除私密金鑰以及指定的憑證。

```powershell
Invoke-Command -Session $s { Remove-Item `
  -Path cert:\LocalMachine\My\D2D38EBA60CAA1C12055A2E1C83B15AD450110C2 `
  -DeleteKey
  }
```

### <a name="delete-expired-certificates"></a>刪除過期的憑證

此命令會使用 Cmdlet 的 **ExpiringInDays** 參數 `Get-ChildItem` ，其值為0，以取得已過期 WebHosting 存放區中的憑證。

包含所傳回憑證的變數會透過管道傳送至 `Remove-Item` Cmdlet，以將其刪除。 此命令會使用 **DeleteKey** 參數來刪除私密金鑰以及憑證。

```powershell
$expired = Get-ChildItem cert:\LocalMachine\WebHosting -ExpiringInDays 0
$expired | Remove-Item -DeleteKey
```

## <a name="creating-certificates"></a>建立憑證

`New-Item`Cmdlet 不會在 **憑證** 提供者中建立新的憑證。 使用 [new-selfsignedcertificate 指令程式](/powershell/module/pkiclient/new-selfsignedcertificate) 來建立憑證以供測試之用。

## <a name="creating-certificate-stores"></a>建立憑證存放區

在 Cert：磁片磁碟機中，此 `New-Item` Cmdlet 會在 LocalMachine 存放區位置中建立憑證存放區。 它支援 **Name** 、 **Path** 、 **WhatIf** 和 **Confirm** 參數。 會忽略所有其他參數。 此命令會傳回代表新憑證存放區的 **system.security.cryptography.x509certificates.x509certificate2. system.security.cryptography.x509certificates.x509store** 。

此命令會在LocalMachine 存放區位置中建立名為 "CustomStore" 的新憑證存放區。

```powershell
New-Item -Path cert:\LocalMachine\CustomStore
```

### <a name="create-a-new-certificate-store-on-a-remote-computer"></a>在遠端電腦上建立新的憑證存放區

此命令會在 Server01 電腦上的 LocalMachine 存放區位置中建立名為 "HostingStore" 的新憑證存放區。

此命令會使用 `Invoke-Command` Cmdlet `New-Item` 在 Server01 電腦上執行命令。 此命令會傳回代表新憑證存放區的 **system.security.cryptography.x509certificates.x509certificate2. system.security.cryptography.x509certificates.x509store** 。

```powershell
Invoke-Command { New-Item -Path cert:\LocalMachine\CustomStore } `
  -ComputerName Server01
```

## <a name="creating-client-certificates-for-ws-man"></a>建立 WS-Man 的用戶端憑證

此命令會建立 **ws-management** 用戶端可以使用的 **ClientCertificate** 專案。 新的 **ClientCertificate** 會在 **ClientCertificate** 目錄下顯示為 "ClientCertificate_1234567890"。 所有的參數都是必要項。 **簽發者必須是簽發者** 憑證的指紋。

```powershell
$cred = Get-Credential
New-Item -Path WSMan:\localhost\ClientCertificate `
         -Issuer 1b3fd224d66c6413fe20d21e38b304226d192dfe `
         -URI wmicimv2/* -Credential $cred
```

## <a name="deleting-certificate-stores"></a>刪除憑證存放區

### <a name="delete-a-certificate-store-from-a-remote-computer"></a>從遠端電腦刪除憑證存放區

此命令會使用 `Invoke-Command` Cmdlet `Remove-Item` 在 S1 和 S2 電腦上執行命令。 此 `Remove-Item` 命令包含 **遞迴** 參數，它會在刪除存放區之前先刪除存放區中的憑證。

```powershell
Invoke-Command { Remove-Item -Path cert:\LocalMachine\TestStore -Recurse } `
  -ComputerName S1, S2
```

## <a name="dynamic-parameters"></a>動態參數

動態參數是 PowerShell 提供者新增的 Cmdlet 參數，而且只有在提供者啟用的磁片磁碟機中使用 Cmdlet 時才能使用。 這些參數在憑證提供者的所有子目錄中都是有效的，但只對憑證有效。

> [!NOTE]
> 針對屬性進行篩選的參數 `EnhancedKeyUsageList` 也會傳回具有空白 `EnhancedKeyUsageList` 屬性值的專案。
> 具有空白 **EnhancedKeyUsageList** 的憑證可用於所有用途。

### <a name="codesigningcert-systemmanagementautomationswitchparameter"></a>CodeSigningCert <System.Management.Automation.SwitchParameter>

#### <a name="cmdlets-supported"></a>支援的 Cmdlet

- [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

此參數會取得其 **EnhancedKeyUsageList** 屬性值中具有「程式碼簽署」的憑證。

### <a name="deletekey-systemmanagementautomationswitchparameter"></a>DeleteKey <System.Management.Automation.SwitchParameter>

#### <a name="cmdlets-supported"></a>支援的 Cmdlet

- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)

此參數刪除憑證時，會刪除相關聯的私密金鑰。

> [!IMPORTANT]
> 若要刪除遠端電腦上存放區中與使用者憑證相關聯的私密金鑰 `Cert:\CurrentUser` ，您必須使用委派的認證。 此 `Invoke-Command` Cmdlet 支援使用 **CredSSP** 參數的認證委派。 使用搭配 `Remove-Item` 和認證委派之前，您應該考慮任何安全性風險 `Invoke-Command` 。

此參數是在 PowerShell 3.0 中引進。

### <a name="dnsname-microsoftpowershellcommandsdnsnamerepresentation"></a>DnsName <Microsoft.PowerShell.Commands.DnsNameRepresentation>

#### <a name="cmdlets-supported"></a>支援的 Cmdlet

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

此參數會取得憑證的 **DNSNameList** 屬性中具有指定功能變數名稱或名稱模式的憑證。 此參數的值可以是「Unicode」或「ASCII」。 Punycode 值會轉換為 Unicode。 `*`允許 () 的萬用字元。

此參數是在 PowerShell 3.0 中引進。

### <a name="documentencryptioncert-systemmanagementautomationswitchparameter"></a>>documentencryptioncert <SwitchParameter>

#### <a name="cmdlets-supported"></a>支援的 Cmdlet

- [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

此參數會取得其 **EnhancedKeyUsageList** 屬性值中具有「檔加密」的憑證。

### <a name="eku-systemstring"></a>EKU <System.String>

#### <a name="cmdlets-supported"></a>支援的 Cmdlet

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

此參數會取得憑證屬性中具有指定文字或文字模式的憑證 `EnhancedKeyUsageList` 。 `*`允許 () 的萬用字元。 `EnhancedKeyUsageList`屬性包含 EKU 的易記名稱和 OID 欄位。

此參數是在 PowerShell 3.0 中引進。

### <a name="expiringindays-systemint32"></a>ExpiringInDays <System.Int32>

#### <a name="cmdlets-supported"></a>支援的 Cmdlet

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

此參數會取得在指定天數內或之前到期的憑證。 值為 0 (零) 可取得已過期的憑證。

此參數是在 PowerShell 3.0 中引進。

### <a name="itemtype-string"></a>ItemType \<String\>

這個參數可讓您指定所建立的專案類型 `New-Item` 。

在 `Certificate` 磁片磁碟機中，允許下列值：

- 憑證提供者
- 憑證
- 市集
- StoreLocation

#### <a name="cmdlets-supported"></a>支援的指令程式

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="sslserverauthentication-systemmanagementautomationswitchparameter"></a>SSLServerAuthentication <System.Management.Automation.SwitchParameter>

#### <a name="cmdlets-supported"></a>支援的 Cmdlet

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

只取得適用於 SSL 虛擬主機的伺服器憑證。 此參數會取得其屬性值中具有「伺服器驗證」的憑證 `EnhancedKeyUsageList` 。

此參數是在 PowerShell 3.0 中引進。

## <a name="script-properties"></a>腳本屬性

新的腳本屬性已新增至代表憑證的 **x509Certificate2** 物件，可讓您輕鬆地搜尋及管理憑證。

- `DnsNameList`：若要填入 `DnsNameList` 屬性，憑證提供者會從 SubjectAlternativeName (SAN) 延伸模組的 DNSName 專案中複製內容。 如果 SAN 延伸模組是空的，就會將憑證的 [主體] 欄位內容填入到屬性中。

- `EnhancedKeyUsageList`：若要填入 `EnhancedKeyUsageList` 屬性，憑證提供者會複製憑證中 EnhancedKeyUsage (EKU) 欄位的 OID 屬性，並為它建立易記名稱。

- `SendAsTrustedIssuer`：若要填入 `SendAsTrustedIssuer` 屬性，憑證提供者會複製 `SendAsTrustedIssuer` 憑證中的屬性。  如需詳細資訊，請參閱 [管理用戶端驗證的受信任](/windows-server/security/tls/what-s-new-in-tls-ssl-schannel-ssp-overview#BKMK_TrustedIssuers)簽發者。

這些新功能可讓您根據憑證的 DNS 名稱和到期日來搜尋它們，並透過它們的增強金鑰使用方法 (EKU) 屬性值來區分用戶端和伺服器驗證憑證。

## <a name="using-the-pipeline"></a>使用管線

提供者 Cmdlet 接受管線輸入。 您可以使用管線將提供者資料從一個 Cmdlet 傳送到另一個提供者 Cmdlet，以簡化工作。
若要深入瞭解如何搭配使用管線與提供者 Cmdlet，請參閱本文中提供的 Cmdlet 參考。

## <a name="getting-help"></a>取得說明

從 PowerShell 3.0 開始，您可以取得提供者 Cmdlet 的自訂說明主題，這些主題說明這些 Cmdlet 在檔案系統磁片磁碟機中的行為。

若要取得針對檔案系統磁片磁碟機自訂的說明主題，請在檔案系統磁片磁碟機中執行 [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 命令，或使用的 `-Path` 參數 `Get-Help` 來指定檔案系統磁片磁碟機。

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path cert:
```

## <a name="see-also"></a>另請參閱

[about_Providers](../../Microsoft.PowerShell.Core/About/about_Providers.md)

[about_Signing](../../Microsoft.PowerShell.Core/About/about_Signing.md)

[Get-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Get-AuthenticodeSignature)

[Set-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

[Get-PfxCertificate](xref:Microsoft.PowerShell.Security.Get-PfxCertificate)
