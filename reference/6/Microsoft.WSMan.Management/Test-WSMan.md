---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/test-wsman?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-WSMan
ms.openlocfilehash: 0cf40af09354314a28af216642d09a5c1fa7479d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202547"
---
# Test-WSMan

## 概要
測試 WinRM 服務是否已在本機或遠端電腦上執行。

## SYNTAX

```
Test-WSMan [[-ComputerName] <String>] [-Authentication <AuthenticationMechanism>] [-Port <Int32>] [-UseSSL]
 [-ApplicationName <String>] [-Credential <PSCredential>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

## DESCRIPTION

**Test-WSMan** Cmdlet 會提交身分識別要求，以判斷 WinRM 服務是否正在本機或遠端電腦上執行。
若測試的電腦正在執行該服務，則此 Cmdlet 會顯示已測試之服務的 WS-Management 身分識別結構描述、通訊協定版本、產品廠商與產品版本。

## 範例

### 範例 1︰判斷 WinRM 服務的狀態

```
PS C:\> Test-WSMan
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 0.0.0 SP: 0.0 Stack: 2.0
```

此命令會判斷 WinRM 服務是否已在本機電腦或遠端電腦上執行。

### 範例 2︰判斷遠端電腦上 WinRM 服務的狀態

```
PS C:\> Test-WSMan -ComputerName "server01"
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 0.0.0 SP: 0.0 Stack: 2.0
```

此命令會判斷 WinRM 服務是否正在 server01 電腦上執行。

### 範例 3︰判斷 WinRM 服務的狀態和作業系統版本

```
PS C:\> Test-WSMan -Authentication default
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 6.0.6001 SP: 1.0 Stack: 2.0
```

此命令會使用驗證參數，來測試 WS-Management (WinRM) 服務是否正在本機電腦上執行。

使用驗證參數可讓 **Test-WSMan** 傳回作業系統版本。

### 範例 4︰判斷遠端電腦上的 WinRM 服務狀態和作業系統版本

```
PS C:\> Test-WSMan -ComputerName "server01" -Authentication default
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 6.1.7021 SP: 0.0 Stack: 2.0
```

此命令會使用驗證參數，來查看 WS-Management (WinRM) 服務是否正在名為 server01 的電腦上執行。

使用驗證參數可讓 **Test-WSMan** 傳回作業系統版本。

## PARAMETERS

### -ApplicationName

指定連線中的應用程式名稱。
*ApplicationName* 參數的預設值是 WSMAN。
遠端端點的完整識別碼使用下列格式：

\<transport\>://\<server\>:\<port\>/\<ApplicationName\>

例如：`http://server01:8080/WSMAN`

裝載工作階段的網際網路資訊服務 (IIS)，會使用此端點轉送要求至指定的應用程式。
此預設設定 WSMAN 適用於大部分用途。
如果有許多電腦與執行 PowerShell 的一部電腦建立遠端連線，則會使用此參數。
在此案例中，IIS 會裝載管理 Web 服務 (WS-Management) 以獲得較佳效率。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Authentication

指定用於伺服器的驗證機制。
此參數可接受的值為：

- 基本。
Basic 配置使用純文字方式將使用者名稱與密碼傳送至伺服器或 Proxy。
- 預設值：
使用 WS-Management 通訊協定實作的驗證方法。
這是預設值。
- 摘要。
Digest 為查問-回應配置，於查問中使用伺服器指定的資料字串。
- Kerberos。
用戶端電腦和伺服器使用 Kerberos 憑證相互驗證。
- Negotiate。
Negotiate 為查問-回應配置，會與伺服器或 Proxy 交涉以決定要用於驗證的配置。
例如，此參數值允許交涉，以決定要使用 Kerberos 通訊協定或 NTLM。
- CredSSP。
使用認證安全性支援提供者 (CredSSP) 驗證，讓使用者能夠委派認證。
此選項是針對下列命令所設計：命令在遠端電腦上執行，但是收集來自其他遠端電腦上的資料，或是在其他遠端電腦上執行其他命令。

注意：CredSSP 會將使用者認證從本機電腦委派給遠端電腦。
此做法會使得遠端作業的安全性風險變高。
若遠端電腦遭到入侵，當認證被傳遞給它時，該認證便可用來控制網路工作階段。

重要：若未指定 *Authentication* 參數，就會以匿名方式將 **Test-WSMan** 要求傳送到遠端電腦，而不使用驗證。
若以匿名方式提出要求，它就不會傳回任何作業系統版本特定的資訊。
相反地，此 Cmdlet 會為作業系統版本與 Service Pack 等級顯示 Null 值 (OS：0.0.0 SP：0.0)。

```yaml
Type: Microsoft.WSMan.Management.AuthenticationMechanism
Parameter Sets: (All)
Aliases: auth, am
Accepted values: None, Default, Digest, Negotiate, Basic, Kerberos, ClientCertificate, Credssp

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CertificateThumbprint

對於具有執行此動作之權限的使用者帳戶，指定其數位公開金鑰憑證 (X509)。
請輸入憑證的憑證指紋。

憑證將用於用戶端憑證式驗證。
這些憑證只能對應至本機使用者帳戶，無法用於網域帳戶。

若要取得憑證指紋，請使用 PowerShell Cert：磁片磁碟機中的 Get-Item 或 Get-ChildItem 命令。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

指定要執行管理作業的電腦。
值可以是完整網域名稱、NetBIOS 名稱或 IP 位址。
使用本機電腦名稱、使用 localhost，或使用句點 (.) 來指定本機電腦。
預設值是本機電腦。
當遠端電腦與使用者位於不同網域，您必須使用完整網域名稱。
您可以使用管線將此參數的值傳送至 Cmdlet。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: cn

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Credential

指定具有執行此動作權限的使用者帳戶。
預設為目前使用者。
輸入使用者名稱，例如 User01、Domain01\User01 或 User@Domain.com 。
或者，輸入 **PSCredential** 物件，例如 Get-Credential Cmdlet 所傳回的物件。
當您輸入使用者名稱時，此 Cmdlet 會提示您輸入密碼。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases: cred, c

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Port

指定用戶端連線 WinRM 服務時所使用的連接埠。
傳輸為 HTTP 時，預設連接埠為 80。
傳輸為 HTTPS 時，預設連接埠為 443。

當您使用 HTTPS 做為傳輸時， *ComputerName* 參數的值必須符合伺服器的憑證一般名稱 (CN) 。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSSL

指定使用安全通訊端層 (SSL) 通訊協定來建立遠端電腦連線。
預設不會使用 SSL。

WS-Management 會加密透過網路傳輸的所有 PowerShell 內容。
*UseSSL* 參數可讓您指定 HTTPS （而非 HTTP）的額外保護。
若用於連線的連接埠上無法使用 SSL，且您指定此參數，則命令會失敗。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無

此 Cmdlet 不接受任何輸入。

## 輸出

### 無

這個 Cmdlet 不會產生任何輸出物件。

## 注意

* 根據預設， **Test-WSMan** Cmdlet 會以不使用驗證的方式查詢 WinRM 服務，而且它不會傳回任何作業系統版本特定的資訊。 相反地，它會為作業系統版本與 Service Pack 等級顯示 Null 值 (OS：0.0.0 SP：0.0)。

*

## 相關連結

[Connect-WSMan](Connect-WSMan.md)

[Disable-WSManCredSSP](Disable-WSManCredSSP.md)

[Disconnect-WSMan](Disconnect-WSMan.md)

[Enable-WSManCredSSP](Enable-WSManCredSSP.md)

[Get-WSManCredSSP](Get-WSManCredSSP.md)

[Get-WSManInstance](Get-WSManInstance.md)

[Invoke-WSManAction](Invoke-WSManAction.md)

[New-WSManInstance](New-WSManInstance.md)

[New-WSManSessionOption](New-WSManSessionOption.md)

[Remove-WSManInstance](Remove-WSManInstance.md)

[Set-WSManInstance](Set-WSManInstance.md)

[Set-WSManQuickConfig](Set-WSManQuickConfig.md)
