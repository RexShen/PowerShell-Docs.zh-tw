---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/invoke-wsmanaction?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-WSManAction
ms.openlocfilehash: 1eeeb912ab32ec5334959daba1e352f20fec15b1
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208687"
---
# Invoke-WSManAction

## 概要
在由資源 URI 與選取器所指定的物件上叫用動作。

## SYNTAX

### URI (預設) 

```
Invoke-WSManAction [-Action] <String> [-ConnectionURI <Uri>] [-FilePath <String>] [-OptionSet <Hashtable>]
 [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>] [-ValueSet <Hashtable>] [-ResourceURI] <Uri>
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

### ComputerName

```
Invoke-WSManAction [-Action] <String> [-ApplicationName <String>] [-ComputerName <String>] [-FilePath <String>]
 [-OptionSet <Hashtable>] [-Port <Int32>] [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>]
 [-UseSSL] [-ValueSet <Hashtable>] [-ResourceURI] <Uri> [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

## DESCRIPTION

Invoke-WSManAction 會在由 RESOURCE_URI 所指定 (其中，參數是以機碼/值組的形式指定) 的物件上執行動作。

此 Cmdlet 會使用 WSMan 連線/傳輸層來執行動作。

## 範例

### 範例 1

```powershell
Invoke-WSManAction -Action startservice -ResourceURI wmicimv2/win32_service  -SelectorSet @{name="spooler"} -Authentication default
```

```Output
xsi         : http://www.w3.org/2001/XMLSchema-instance
p           : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim         : http://schemas.dmtf.org/wbem/wscim/1/common
lang        : en-US
ReturnValue : 0
```

此命令會呼叫對應至多工緩衝處理器服務之 Win32_Service WMI 類別執行個體的 StartService 方法。

傳回值指出動作是否成功。
在此案例中，0 的傳回值表示成功。
5 的傳回值表示服務已啟動。

### 範例 2

```powershell
Invoke-WSManAction -Action stopservice -ResourceURI wmicimv2/Win32_Service -SelectorSet @{Name="spooler"} -FilePath:input.xml -Authentication default
```

```Output
xsi         : http://www.w3.org/2001/XMLSchema-instance
p           : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim         : http://schemas.dmtf.org/wbem/wscim/1/common
lang        : en-US
ReturnValue : 0
```

此命令會使用來自檔案的輸入，在多工緩衝處理器服務上呼叫 StopService 方法。
該檔案 (Input.xml) 包含下列內容：

`<p:StopService_INPUT xmlns:p="http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service" />`

傳回值指出動作是否成功。
在此案例中，0 的傳回值表示成功。
5 的傳回值表示服務已啟動。

### 範例 3

```powershell
Invoke-WSManAction -Action create -ResourceURI wmicimv2/win32_process -ValueSet @{commandline="notepad.exe";currentdirectory="C:\"}
```

```Output
xsi         : http://www.w3.org/2001/XMLSchema-instance
p           : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Process
cim         : http://schemas.dmtf.org/wbem/wscim/1/common
lang        : en-US
ProcessId   : 6356
ReturnValue : 0
```

此命令會呼叫 Win32_Process 類別的 Create 方法。
它會將方法傳遞給兩個參數值，Notepad.exe 和 "C： \" 。
如此一來，就會建立新的程式來執行「記事本」，而新進程的目前的目錄會設定為 "C： \" 。

### 範例 4

```powershell
Invoke-WSManAction -Action startservice -ResourceURI wmicimv2/win32_service  -SelectorSet @{name="spooler"} -ComputerName server01 -Authentication default
```

```Output
xsi         : http://www.w3.org/2001/XMLSchema-instance
p           : http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service
cim         : http://schemas.dmtf.org/wbem/wscim/1/common
lang        : en-US
ReturnValue : 0
```

此命令會呼叫對應至多工緩衝處理器服務之 Win32_Service WMI 類別執行個體的 StartService 方法。
因為已指定 ComputerName 參數，該命令會針對遠端 server01 電腦執行。

傳回值指出動作是否成功。
在此案例中，0 的傳回值表示成功。
5 的傳回值表示服務已啟動。

## PARAMETERS

### -Action

指定要在由 ResourceURI 與選取器所指定之管理物件上執行的方法。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ApplicationName

指定連線中的應用程式名稱。
ApplicationName 參數的預設值是 WSMAN。
遠端端點的完整識別碼使用下列格式：

\<transport\>://\<server\>:\<port\>/\<ApplicationName\>

例如：

`http://server01:8080/WSMAN`

裝載工作階段的網際網路資訊服務 (IIS)，會使用此端點轉送要求至指定的應用程式。
此預設設定 "WSMAN" 適用於大部分用途。
此參數是設計用於下列狀況：多部電腦建立遠端連線至同一部執行 Windows PowerShell 的電腦。
在此案例中，IIS 會裝載管理 Web 服務 (WS-Management) 以獲得較佳效率。

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: Wsman
Accept pipeline input: False
Accept wildcard characters: False
```

### -Authentication

指定用於伺服器的驗證機制。
可能的值包括：

- Basic：Basic 配置使用純文字方式將使用者名稱與密碼傳送至伺服器或 Proxy。
- Default：使用 WS-Management 通訊協定實作的驗證方法。 這是預設值。
- Digest：Digest 為查問-回應配置，於查問中使用伺服器指定的資料字串。
- Kerberos：用戶端電腦和伺服器使用 Kerberos 憑證相互驗證。
- Negotiate：Negotiate 為查問-回應配置，會與伺服器或 Proxy 交涉以決定要用於驗證的配置。 例如，此參數值允許交涉以決定要使用 Kerberos 通訊協定或 NTLM。
- CredSSP：使用允許使用者委派認證的「認證安全性支援提供者 (CredSSP)」驗證。 此選項是針對下列命令所設計：命令在遠端電腦上執行，但是收集來自其他遠端電腦上的資料，或是在其他遠端電腦上執行其他命令。

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

若要取得憑證指紋，請在 Windows PowerShell Cert: 磁碟機中使用 Get-Item 或 Get-ChildItem 命令。

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
Position: Named
Default value: Localhost
Accept pipeline input: False
Accept wildcard characters: False
```

### -ConnectionURI

指定連線端點。
此字串的格式為：

\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\>

下列字串是此參數的正確格式值：

`http://Server01:8080/WSMAN`

此 URI 必須是完整的 URI。

```yaml
Type: System.Uri
Parameter Sets: URI
Aliases: CURI, CU

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

指定具有執行此動作權限的使用者帳戶。
預設為目前使用者。
輸入使用者名稱，例如 "User01"、"Domain01\User01" 或 User@Domain.com 。
或者，輸入 PSCredential 物件，例如 Get-Credential Cmdlet 傳回的物件。
當您輸入使用者名稱時，會提示您輸入密碼。

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

### -FilePath

指定用來更新管理資源之檔案的路徑。
您可以使用 ResourceURI 參數與 SelectorSet 參數來指定管理資源。
例如，下列命令使用 FilePath 參數：

`Invoke-WSManAction -Action stopservice -ResourceUri wmicimv2/Win32_Service -SelectorSet @{Name="spooler"} -FilePath c:\input.xml -Authentication default`

此命令會使用來自檔案的輸入，在多工緩衝處理器服務上呼叫 StopService 方法。
該檔案 (Input.xml) 包含下列內容：

`<p:StopService_INPUT xmlns:p="http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service" />`

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

### -OptionSet

將一組參數傳遞至服務，以修改或精簡要求的本質。
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
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Port

指定用戶端連線 WinRM 服務時所使用的連接埠。
傳輸為 HTTP 時，預設連接埠為 80。
傳輸為 HTTPS 時，預設連接埠為 443。
使用 HTTPS 做為傳輸時，ComputerName 參數的值必須符合伺服器憑證一般名稱 (CN)。
不過，如果 SkipCNCheck 參數指定為 SessionOption 參數的一部分，則伺服器憑證一般名稱不必符合伺服器主機名稱。
SkipCNCheck 參數只能用於信任的電腦。

```yaml
Type: System.Int32
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ResourceURI

包含資源類別或執行個體的「統一資源識別項 (URI)」。
URI 可用來識別電腦上的特定類型資源，例如磁碟或處理程序。

URI 是由前置詞與資源路徑所組成。
例如：

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases: ruri

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SelectorSet

指定一組值組，用來選取特定管理資源執行個體。
當有一個以上的資源實例存在時，就會使用 *SelectorSet* 。
*SelectorSet* 的值必須是雜湊表。

下列範例顯示如何輸入此參數的值：

`-SelectorSet @{Name="WinRM";ID="yyy"}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SessionOption

定義 WS-Management 工作階段的一組擴充選項。
輸入使用 New-WSManSessionOption Cmdlet 所建立的 SessionOption 物件。
如需可用選項的詳細資訊，請參閱 New-WSManSessionOption。

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
UseSSL 參數可讓您指定 HTTPS 額外保護，以取代 HTTP。
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

### -ValueSet

指定有助於修改管理資源的雜湊表。
您可以使用 ResourceURI 和 SelectorSet 參數來指定管理資源。
ValueSet 參數的值必須為雜湊表。

```yaml
Type: System.Collections.Hashtable
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

此 Cmdlet 不會產生任何輸出。

## 注意

## 相關連結

[Invoke-WmiMethod](../Microsoft.PowerShell.Management/Invoke-WmiMethod.md)

[Connect-WSMan](Connect-WSMan.md)

[Disable-WSManCredSSP](Disable-WSManCredSSP.md)

[Disconnect-WSMan](Disconnect-WSMan.md)

[Enable-WSManCredSSP](Enable-WSManCredSSP.md)

[Get-WSManCredSSP](Get-WSManCredSSP.md)

[Get-WSManInstance](Get-WSManInstance.md)

[New-WSManInstance](New-WSManInstance.md)

[New-WSManSessionOption](New-WSManSessionOption.md)

[Remove-WSManInstance](Remove-WSManInstance.md)

[Set-WSManInstance](Set-WSManInstance.md)

[Set-WSManQuickConfig](Set-WSManQuickConfig.md)

[Test-WSMan](Test-WSMan.md)
