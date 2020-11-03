---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/connect-wsman?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Connect-WSMan
ms.openlocfilehash: e22aeef7dbc7ef799127def2606a15fdccbfffe3
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201800"
---
# Connect-WSMan

## 概要
連線到遠端電腦上的 WinRM 服務。

## SYNTAX

### ComputerName (預設值)

```
Connect-WSMan [-ApplicationName <String>] [[-ComputerName] <String>] [-OptionSet <Hashtable>] [-Port <Int32>]
 [-SessionOption <SessionOption>] [-UseSSL] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### URI

```
Connect-WSMan [-ConnectionURI <Uri>] [-OptionSet <Hashtable>] [-Port <Int32>] [-SessionOption <SessionOption>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

## DESCRIPTION
**Connect-WSMan** Cmdlet 會連線到遠端電腦上的 WinRM 服務，並且會建立與遠端電腦的持續連線。
您可以在 WSMan 提供者中使用此 Cmdlet 來連線到遠端電腦上的 WinRM 服務。
不過，您也可以使用此 Cmdlet 來連線到遠端電腦上的 WinRM 服務，再變更為 WSMan 提供者。
遠端電腦會出現在 WSMan 提供者的根目錄。

當用戶端與伺服器電腦位於不同的網域或工作群組時，需要明確宣告的認證。

如需如何中斷與遠端電腦上 WinRM 服務之連線的詳細資訊，請參閱 Disconnect-WSMan Cmdlet。

## 範例

### 範例 1︰連線到遠端電腦

```
PS C:\> Connect-WSMan -ComputerName "server01"
PS C:\> cd wsman:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan

ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01                                      Container
```

此命令會建立與遠端 server01 電腦的連線。

**Connect-WSMan** Cmdlet 通常是在 WSMan 提供者中用來連線到遠端電腦 (在此案例中是 server01 電腦)。
不過，您可以使用該 Cmdlet 來建立與遠端電腦的連線，再變更為 WSMan 提供者。
那些連線會出現在 **ComputerName** 清單中。

### 範例 2︰使用 Administrator 認證連線到遠端電腦

```
PS C:\> $cred = Get-Credential Administrator
PS C:\> Connect-WSMan -ComputerName "server01" -Credential $cred
PS C:\> cd wsman:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan

ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01                                      Container
```

此命令會使用 Administrator 帳戶驗證來建立與遠端系統 server01 的連線。

第一個命令會使用 Get-Credential Cmdlet 來取得 Administrator 認證並將其儲存在 $cred 變數中。
**Get-Credential** 會透過對話方塊或命令列 (視系統登錄設定而定) 提示您輸入使用者名稱的密碼和密碼。

第二個命令會使用 *Credential* 參數，將 $cred 中儲存的認證傳遞至 **連接-WSMan** 。
**Connect-WSMan** 接著會使用 Administrator 認證來連線到遠端系統 server01。

### 範例 3︰透過指定的連接埠連線到遠端電腦

```
PS C:\> Connect-WSMan -ComputerName "server01" -Port 80
PS C:\> cd wsman:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan
ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01                                      Container
```

此命令會透過連接埠 80 建立與遠端 server01 電腦的連線。

### 範例 4︰使用連線選項連線到遠端電腦

```
PS C:\> $a = New-WSManSessionOption -OperationTimeout 30000
PS C:\> Connect-WSMan -ComputerName "server01" -SessionOption $a
PS C:\> cd wsman:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan
ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01                                      Container
```

此範例會使用在 **New-WSManSessionOption** 命令中定義的連線選項來建立與遠端 server01 電腦的連線。

第一個命令會使用 **New-WSManSessionOption** 將一組連線設定選項儲存到 $a 變數中。
在此案例中，工作階段選項會設定 30 秒 (30,000 毫秒) 的連線逾時。

第二個命令會使用 *SessionOption* 參數，將儲存在 $a 變數中的認證傳遞至 **連接-WSMan** 。
然後， **連接-WSMan** 使用指定的會話選項連線到遠端 server01 電腦。

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
Parameter Sets: ComputerName
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
Parameter Sets: ComputerName
Aliases: cn

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ConnectionURI
指定連線端點。
這個字串的格式如下所示：

\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\>

下列字串是此參數的正確格式值：

`http://Server01:8080/WSMAN`

此 URI 必須是完整的 URI。

```yaml
Type: System.Uri
Parameter Sets: URI
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
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

### -OptionSet
對服務指定一組切換參數，以修改或精簡要求的本質。
這些切換參數類似於命令列殼層中使用的切換參數，因為都是服務特定的切換參數。
您可以指定任意數目的選項。

下列範例示範的語法可傳遞 a、b 與 c 參數的值 1、2 與 3：

`-OptionSet @{a=1;b=2;c=3}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases: os

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Port
指定用戶端連線 WinRM 服務時所使用的連接埠。
傳輸為 HTTP 時，預設連接埠為 80。
傳輸為 HTTPS 時，預設連接埠為 443。

當您使用 HTTPS 做為傳輸時， *ComputerName* 參數的值必須符合伺服器的憑證一般名稱 (CN) 。
不過，如果 *SkipCNCheck* 參數指定為 *SessionOption* 參數的一部分，則伺服器憑證一般名稱不必符合伺服器主機名稱。
*SkipCNCheck* 參數只能用於信任的電腦。

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

### -SessionOption
指定 WS-Management 工作階段的擴充選項。
輸入您使用 New-WSManSessionOption Cmdlet 建立的 **SessionOption** 物件。
如需可用選項的詳細資訊，請輸入 `Get-Help New-WSManSessionOption`。

```yaml
Type: Microsoft.WSMan.Management.SessionOption
Parameter Sets: (All)
Aliases: so

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
Parameter Sets: ComputerName
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
此 Cmdlet 不會產生任何輸出。

## 注意

* 您不需要建立 WS-Management 工作階段，就可以在遠端電腦上執行管理命令或查詢遠端電腦上的管理資料。 您可以使用 Invoke-WSManAction 的 *ComputerName* 參數和 set-wsmaninstance 來完成這項作業。 當您使用 *ComputerName* 參數時，PowerShell 會建立用於單一命令的暫時連接。 該命令執行之後，此連線即會關閉。

*

## 相關連結

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

[Test-WSMan](Test-WSMan.md)
