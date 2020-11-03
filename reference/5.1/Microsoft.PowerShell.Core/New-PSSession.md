---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pssession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSSession
ms.openlocfilehash: 1835d0bd4294161f83728a63e8da8fc64c2bf9e0
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205383"
---
# New-PSSession

## 概要
建立連到本機或遠端電腦的持續連線。

## SYNTAX

### ComputerName (預設值)

```
New-PSSession [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-Name <String[]>]
 [-EnableNetworkAccess] [-ConfigurationName <String>] [-Port <Int32>] [-UseSSL]
 [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### Uri

```
New-PSSession [-Credential <PSCredential>] [-Name <String[]>] [-EnableNetworkAccess]
 [-ConfigurationName <String>] [-ThrottleLimit <Int32>] [-ConnectionUri] <Uri[]> [-AllowRedirection]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### VMId

```
New-PSSession -Credential <PSCredential> [-Name <String[]>] [-ConfigurationName <String>]
 [-VMId] <Guid[]> [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### VMName

```
New-PSSession -Credential <PSCredential> [-Name <String[]>] [-ConfigurationName <String>]
 -VMName <String[]> [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### 工作階段

```
New-PSSession [[-Session] <PSSession[]>] [-Name <String[]>] [-EnableNetworkAccess]
 [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### ContainerId

```
New-PSSession [-Name <String[]>] [-ConfigurationName <String>] -ContainerId <String[]>
 [-RunAsAdministrator] [-ThrottleLimit <Int32>] [<CommonParameters>]
```

## DESCRIPTION

`New-PSSession`Cmdlet 會在本機或遠端電腦上建立 ( **PSSession** ) 的 PowerShell 會話。 當您建立 **PSSession** 時，PowerShell 會建立與遠端電腦的持續連線。

使用 **PSSession** 來執行多個共用資料的命令，例如函數或變數的值。 若要在 **PSSession** 中執行命令，請使用 `Invoke-Command` Cmdlet。 若要使用 **PSSession** 與遠端電腦直接互動，請使用 `Enter-PSSession` Cmdlet。 如需詳細資訊，請參閱 [about_PSSessions](about/about_PSSessions.md)。

您可以使用或的 **ComputerName** 參數，在遠端電腦上執行命令，而不需要建立 **PSSession** `Enter-PSSession` `Invoke-Command` 。 當您使用 **ComputerName** 參數時，PowerShell 會建立用於命令的暫時連接，然後關閉。

## 範例

### 範例1：在本機電腦上建立會話

```powershell
$s = New-PSSession
```

此命令會在本機電腦上建立新的 **pssession** ，並將 **pssession** 儲存在 `$s` 變數中。

您現在可以使用這個 **PSSession** 在本機電腦上執行命令。

### 範例2：在遠端電腦上建立會話

```powershell
$Server01 = New-PSSession -ComputerName Server01
```

此命令會在 Server01 電腦上建立新的 **PSSession** ，並將它儲存在 `$Server01` 變數中。

建立多個 **PSSession** 物件時，請將它們指派給具有有用名稱的變數。 這可協助您管理後續命令中的 **PSSession** 物件。

### 範例3：在多部電腦上建立會話

```powershell
$s1, $s2, $s3 = New-PSSession -ComputerName Server01,Server02,Server03
```

此命令會建立三個 **PSSession** 物件，在 **ComputerName** 參數所指定的每一部電腦上建立一個。

此命令會使用指派運算子 (=) 將新的 **PSSession** 物件指派給變數： `$s1` 、 `$s2` 、 `$s3` 。 它會將 Server01 **pssession** 指派給 `$s1` 、將 Server02 **pssession** 指派給 `$s2` ，以及將 Server03 **pssession** 指派給 `$s3` 。

當您將多個物件指派給一系列的變數時，PowerShell 會將每個物件分別指派給數列中的變數。 如果物件數目多於變數數目，就會將所有剩餘的物件指派給最後一個變數。 如果變數數目多於物件數目，則剩餘的變數會是空的 (null)。

### 範例4：建立具有指定埠的會話

```powershell
New-PSSession -ComputerName Server01 -Port 8081 -UseSSL -ConfigurationName E12
```

此命令會在連線到伺服器埠8081並使用 SSL 通訊協定的 Server01 電腦上建立新的 **PSSession** 。 新的 **PSSession** 會使用稱為 E12 的替代會話設定。

設定連接埠之前，您必須先將遠端電腦上的 WinRM 接聽程式設定為在連接埠 8081 進行接聽。 如需詳細資訊，請參閱 **Port** 參數的描述。

### 範例5：根據現有的會話建立會話

```powershell
New-PSSession -Session $s -Credential Domain01\User01
```

此命令會使用與現有 **PSSession** 相同的屬性來建立 **PSSession** 。 當現有 **PSSession** 的資源已用盡，且需要新的 **pssession** 來卸載部分需求時，您可以使用此命令格式。

命令使用的 **Session** 參數 `New-PSSession` 來指定儲存在變數中的 **PSSession** `$s` 。 它使用 Domain1\Admin01 使用者的認證來完成命令。

### 範例6：在不同網域中建立具有全域領域的會話

```powershell
$global:s = New-PSSession -ComputerName Server1.Domain44.Corpnet.Fabrikam.com -Credential Domain01\Admin01
```

此範例示範如何在不同網域中的電腦上建立具有全域領域的 **PSSession** 。

根據預設，在命令列建立的 **pssession** 物件是使用區域範圍所建立，而在腳本中建立的 **pssession** 物件具有腳本領域。

若要建立具有全域領域的 **pssession** ，請建立新的 **pssession** ，然後將 **pssession** 儲存在轉換成全域領域的變數中。 在此情況下， `$s` 變數會轉換成全域領域。

此命令使用 **ComputerName** 參數來指定遠端電腦。 由於電腦是在與使用者帳戶不同的網域中，因此電腦的完整名稱會與使用者的認證一起指定。

### 範例7：建立許多電腦的會話

```powershell
$rs = Get-Content C:\Test\Servers.txt | New-PSSession -ThrottleLimit 50
```

此命令會在 Servers.txt 檔案中列出的每一部200電腦上建立 **pssession** ，並將產生的 **pssession** 儲存在 `$rs` 變數中。 **PSSession** 物件的節流閥限制為50。

當電腦的名稱是儲存在資料庫、試算表、文字檔或其他可轉換成文字的格式中時，可以使用此命令格式。

### 範例8：使用 URI 建立會話

```powershell
$s = New-PSSession -URI http://Server01:91/NewSession -Credential Domain01\User01
```

此命令會在 Server01 電腦上建立 **PSSession** ，並將它儲存在 `$s` 變數中。 它使用 **URI** 參數來指定傳輸通訊協定、遠端電腦、埠，以及替代會話設定。 它也會使用 **Credential** 參數來指定具有在遠端電腦上建立會話之許可權的使用者帳戶。

### 範例9：在一組會話中執行背景工作

```powershell
$s = New-PSSession -ComputerName (Get-Content Servers.txt) -Credential Domain01\Admin01 -ThrottleLimit 16
Invoke-Command -Session $s -ScriptBlock {Get-Process PowerShell} -AsJob
```

這些命令會建立一組 **pssession** 物件，然後在每個 **pssession** 物件中執行背景工作。

第一個命令會在 Servers.txt 檔案中列出的每一部電腦上建立新的 **PSSession** 。 它會使用 `New-PSSession` Cmdlet 來建立 **PSSession** 。 **ComputerName** 參數的值是一個命令，此命令會使用 `Get-Content` Cmdlet 取得 Servers.txt 檔案的電腦名稱稱清單。

此命令會使用 **Credential** 參數來建立具有網域系統管理員許可權的 **PSSession** 物件，並使用 **ThrottleLimit** 參數將命令限制為16個並行連接。 此命令會將 **PSSession** 物件儲存在 `$s` 變數中。

第二個命令會使用 Cmdlet 的 **AsJob** 參數 `Invoke-Command` 啟動背景工作，在 `Get-Process PowerShell` 中的每個 **PSSession** 物件中執行命令 `$s` 。

如需 PowerShell 背景工作的詳細資訊，請參閱 [about_Jobs](About/about_Jobs.md) 和 [about_Remote_Jobs](About/about_Remote_Jobs.md)。

### 範例10：使用其 URI 建立電腦的會話

```powershell
New-PSSession -ConnectionURI https://management.exchangelabs.com/Management
```

此命令會建立 **PSSession** 物件，以連接到由 URI 指定的電腦，而不是電腦名稱稱。

### 範例11：建立會話選項

```powershell
$so = New-PSSessionOption -SkipCACheck
New-PSSession -ConnectionUri https://management.exchangelabs.com/Management -SessionOption $so -Credential Server01\Admin01
```

這個範例示範如何建立會話選項物件，並使用 **SessionOption** 參數。

第一個命令會使用 `New-PSSessionOption` Cmdlet 來建立會話選項。 它會將產生的 **SessionOption** 物件儲存在 `$so` 變數中。

第二個命令會在新的工作階段中使用該選項。 此命令會使用 `New-PSSession` Cmdlet 來建立新的會話。 SessionOption 參數的值是變數中的 **SessionOption** 物件 `$so` 。

## PARAMETERS

### -AllowRedirection

指出此 Cmdlet 允許將此連線重新導向至替代的統一資源識別項 (URI) 。

使用 **ConnectionURI** 參數時，遠端目的地可傳回重新導向至不同 URI 的指示。 根據預設，PowerShell 不會重新導向連線，但是您可以使用這個參數讓它重新導向連接。

您也可以變更 **MaximumConnectionRedirectionCount** 工作階段選項值，限制連線重新導向的次數。 使用 Cmdlet 的 **MaximumRedirection** 參數， `New-PSSessionOption` 或設定 **$PSSessionOption** 喜好設定變數的 **MaximumConnectionRedirectionCount** 屬性。 預設值為 5。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ApplicationName

指定連線 URI 的應用程式名稱區段。 當您沒有在命令中使用 **ConnectionURI** 參數時，請使用這個參數來指定應用程式名稱。

預設值是 `$PSSessionApplicationName` 本機電腦上喜好設定變數的值。 若未定義此喜好設定變數，則預設值是 WSMAN。 這個值適用於大部分用途。 如需詳細資訊，請參閱 [about_Preference_Variables](About/about_Preference_Variables.md)。

WinRM 服務會使用應用程式名稱來選取要用來為連線要求提供服務的接聽程式。
此參數的值應該符合遠端電腦上接聽程式之 **URLPrefix** 屬性的值。

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Authentication

指定用來驗證使用者認證的機制。
此參數可接受的值為：

- 預設
- 基本
- Credssp
- Digest
- Kerberos
- 交涉
- NegotiateWithImplicitCredential

預設值為 Default。

如需此參數值的詳細資訊，請參閱 [AuthenticationMechanism 列舉](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。

> [!CAUTION]
> 認證安全性支援提供者 (CredSSP) 驗證，其中使用者認證會傳遞至要驗證的遠端電腦，其設計是針對需要在多個資源上進行驗證的命令，例如存取遠端網路共用。 此機制會使得遠端作業的安全性風險變高。 若遠端電腦遭到入侵，傳遞給它的認證便可用來控制網路工作階段。

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerName, Uri
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CertificateThumbprint

對於具有執行此動作之權限的使用者帳戶，指定其數位公開金鑰憑證 (X509)。 請輸入憑證的憑證指紋。

憑證將用於用戶端憑證式驗證。 這些憑證只能對應至本機使用者帳戶，無法用於網域帳戶。

若要取得憑證，請使用 `Get-Item` `Get-ChildItem` PowerShell Cert：磁片磁碟機中的或命令。

```yaml
Type: System.String
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

指定電腦名稱的陣列。 此 Cmdlet 會建立 ( **PSSession** ) 至指定電腦的持續連線。 如果您輸入多個電腦名稱稱，則會 `New-PSSession` 建立多個 **PSSession** 物件（每一部電腦各一個）。 預設是本機電腦。

輸入一或多部遠端電腦的 NetBIOS 名稱、IP 位址或完整網域名稱。 若要指定本機電腦，請輸入電腦名稱、localhost 或句點 (.)。 當電腦與使用者位於不同網域，則必須使用完整網域名稱。 您也可以使用管線將電腦名稱稱（以引號括住）傳送至 `New-PSSession` 。

若要在 **ComputerName** 參數的值中使用 IP 位址，命令必須包含 **Credential** 參數。 此外，必須將電腦設定為使用 HTTPS 傳輸，或必須在本機電腦的 WinRM TrustedHosts 清單中包含遠端電腦的 IP 位址。 如需將電腦名稱稱新增到 TrustedHosts 清單的指示，請參閱 [about_Remote_Troubleshooting](about/about_Remote_Troubleshooting.md)中的「如何將電腦新增到信任的主機清單」。

若要在 **ComputerName** 參數的值中包含本機電腦，請使用 [以系統管理員身分執行] 選項啟動 Windows PowerShell。

```yaml
Type: System.String[]
Parameter Sets: ComputerName
Aliases: Cn

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -ConfigurationName

指定用於新 **PSSession** 的會話設定。

輸入工作階段設定的設定名稱或完整資源 URI。 如果您只指定設定名稱，則會在前面加上下列架構 URI： `http://schemas.microsoft.com/PowerShell` 。

工作階段的工作階段設定是位於遠端電腦上。 如果遠端電腦上沒有指定的工作階段設定，則命令會失敗。

預設值是 `$PSSessionConfigurationName` 本機電腦上喜好設定變數的值。 若未設定此喜好設定變數，則預設為 Microsoft.PowerShell。 如需詳細資訊，請參閱 [about_Preference_Variables](About/about_Preference_Variables.md)。

```yaml
Type: System.String
Parameter Sets: ComputerName, Uri, VMId, VMName, ContainerId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ConnectionUri

指定定義會話之連接端點的 URI。 此 URI 必須是完整的 URI。 這個字串的格式如下所示：

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

預設值如下：

`http://localhost:5985/WSMAN`

如果您未指定 **ConnectionURI** ，可以使用 **UseSSL** 、 **ComputerName** 、 **Port** 及 **ApplicationName** 參數來指定 **ConnectionURI** 值。

URI 的 Transport 區段有效值為 HTTP 與 HTTPS。 若指定含傳輸區段的連線 URI，但未指定連接埠，將會以標準連接埠 80 (適用於 HTTP) 和 443 (適用於 HTTPS) 建立工作階段。 若要使用 PowerShell 遠端的預設埠，請指定 HTTP 的埠5985或 HTTPS 的5986。

如果目的地電腦將連線重新導向至不同的 URI，除非您在命令中使用 **AllowRedirection** 參數，否則 PowerShell 會禁止重新導向。

```yaml
Type: System.Uri[]
Parameter Sets: Uri
Aliases: URI, CU

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ContainerId

指定容器的識別碼陣列。 此 Cmdlet 會啟動每個指定容器的互動式會話。 使用 `docker ps` 命令來取得容器識別碼的清單。 如需詳細資訊，請參閱 [docker ps](https://docs.docker.com/engine/reference/commandline/ps/) 命令的說明。

```yaml
Type: System.String[]
Parameter Sets: ContainerId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Credential

指定具有執行此動作之許可權的使用者帳戶。 預設為目前使用者。

輸入使用者名稱（例如 **User01** 或 **Domain01\User01** ），或輸入 Cmdlet 所產生的 **PSCredential** 物件 `Get-Credential` 。 如果您輸入使用者名稱，系統就會提示您輸入密碼。

認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。

> [!NOTE]
> 如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, Uri, VMId, VMName
Aliases:

Required: True (VMId, VMName), False (ComputerName, Uri)
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -EnableNetworkAccess

指出此 Cmdlet 會將互動式安全性權杖新增至回送會話。 互動式權杖可讓您在會從其他電腦取得資料的回送工作階段中執行命令。 例如，您可以在會將 XML 檔案從遠端電腦複製到本機電腦的工作階段中執行命令。

回送會話是在同一部電腦上產生和結束的 **PSSession** 。 若要建立回送會話，請省略 **ComputerName** 參數，或將其值設為點 (. ) 、localhost 或本機電腦的名稱。

根據預設，此 Cmdlet 會使用網路權杖建立回送會話，這可能不會提供足夠的許可權來驗證遠端電腦。

**EnableNetworkAccess** 參數只在回送工作階段中有效。 如果您在遠端電腦上建立會話時使用 **EnableNetworkAccess** ，則命令會成功，但是會忽略參數。

您也可以在回送會話中啟用遠端存取，方法是使用 **驗證** 參數的 CredSSP 值，該參數會將會話認證委派給其他電腦。

為了保護電腦免于惡意存取，具有互動式權杖（使用 **EnableNetworkAccess** 參數所建立）的已中斷連線回送會話，只能從建立會話的電腦重新連接。 使用 CredSSP 驗證且已中斷連線的工作階段可從其他電腦重新連線。 如需詳細資訊，請參閱`Disconnect-PSSession`。

此參數是在 PowerShell 3.0 中引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, Uri, Session
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

指定 **PSSession** 的易記名稱。

當您使用其他 Cmdlet 時，您可以使用名稱來參考 **PSSession** ，例如 `Get-PSSession` 和 `Enter-PSSession` 。 該名稱對電腦或目前工作階段而言不需要是唯一的。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Port

指定遠端電腦上要供此連線使用的網路連接埠。 若要連線到遠端電腦，遠端電腦必須接聽連線使用的連接埠。 預設的埠是5985，也就是 HTTP 的 WinRM 埠和5986，也就是 HTTPS 的 WinRM 埠。

使用其他埠之前，您必須先將遠端電腦上的 WinRM 接聽程式設定為在該埠上接聽。 使用下列命令來設定接聽程式：

1. `winrm delete winrm/config/listener?Address=*+Transport=HTTP`
2. `winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number\>"}`

除非必要，否則請勿使用 **Port** 參數。 命令中的連接埠設定會套用到所有電腦或命令執行所在工作階段。 替代的連接埠設定可能使得命令無法在全部電腦上執行。

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

### -RunAsAdministrator

指出 **PSSession** 以系統管理員身分執行。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ContainerId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Session

指定 **pssession** 物件的陣列，這個 Cmdlet 會使用這個陣列做為新 **PSSession** 的模型。 此參數會建立新的 **pssession** 物件，這些物件與指定的 **pssession** 物件具有相同的屬性。

輸入包含 **pssession** 物件的變數，或輸入可建立或取得 **pssession** 物件的命令，例如 `New-PSSession` 或 `Get-PSSession` 命令。

產生的 **PSSession** 物件具有相同的電腦名稱稱、應用程式名稱、連線 URI、埠、設定名稱、節流限制，以及安全通訊端層 (SSL) 值做為原始，但它們具有不同的顯示名稱、識別碼和實例識別碼 (GUID) 。

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SessionOption

指定會話的 advanced 選項。 輸入 **SessionOption** 物件（例如您使用 Cmdlet 建立的物件 `New-PSSessionOption` ），或輸入雜湊表，其中索引鍵為會話選項名稱，而值為會話選項值。

選項的預設值取決於 `$PSSessionOption` 喜好設定變數的值（如果已設定）。 否則，將以工作階段設定中設定的選項建立預設值。

會話選項值的優先順序高於 `$PSSessionOption` 喜好設定變數和會話設定中設定之會話的預設值。 不過，它們的優先順序不會高於工作階段設定中設定的最大值、配額或限制。

如需包含預設值之會話選項的描述，請參閱 `New-PSSessionOption` 。 如需喜好設定變數的詳細資訊 `$PSSessionOption` ，請參閱 [about_Preference_Variables](About/about_Preference_Variables.md)。 如需會話設定的詳細資訊，請參閱 [about_Session_Configurations](About/about_Session_Configurations.md)。

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

指定為執行此命令可建立的最大同時連線數。
若省略此參數，或輸入值為 0 (零)，則會使用預設值 32。

節流限制僅適用於目前命令，不適用於工作階段或電腦。

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

指出此 Cmdlet 會使用 SSL 通訊協定來建立與遠端電腦的連接。
預設不會使用 SSL。

WS-Management 加密透過網路傳輸的所有 PowerShell 內容。 **UseSSL** 參數提供額外的保護，可跨 HTTPS 連接（而非 HTTP 連線）傳送資料。

如果您使用此參數，但是命令所用的埠上無法使用 SSL，則命令會失敗。

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

### -VMId

指定虛擬機器的識別碼陣列。 此 Cmdlet 會在每個指定的虛擬機器之間啟動互動式會話。 若要查看可供您使用的虛擬機器，請使用下列命令：

`Get-VM | Select-Object -Property Name, ID`

```yaml
Type: System.Guid[]
Parameter Sets: VMId
Aliases: VMGuid

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -VMName

指定虛擬機器名稱的陣列。 此 Cmdlet 會在每個指定的虛擬機器之間啟動互動式會話。 若要查看可供您使用的虛擬機器，請使用 `Get-VM` Cmdlet。

```yaml
Type: System.String[]
Parameter Sets: VMName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.String、System.URI、System.Management.Automation.Runspaces.PSSession

您可以使用管線將字串、URI 或會話物件傳送至此 Cmdlet。

## 輸出

### System.Management.Automation.Runspaces.PSSession

## 注意

- 此 Cmdlet 會使用 PowerShell 遠端基礎結構。 若要使用這個 Cmdlet，本機電腦和任何遠端電腦都必須設定 PowerShell 遠端功能。 如需詳細資訊，請參閱[about_Remote_Requirements](About/about_Remote_Requirements.md)。
- 若要在本機電腦上建立 **PSSession** ，請使用 [以系統管理員身分執行] 選項啟動 PowerShell。
- 當您完成 **pssession** 之後，請使用 `Remove-PSSession` Cmdlet 來刪除 **pssession** 並釋放其資源。

## 相關連結

[Connect-PSSession](Connect-PSSession.md)

[Disconnect-PSSession](Disconnect-PSSession.md)

[Enter-PSSession](Enter-PSSession.md)

[Exit-PSSession](Exit-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Invoke-Command](Invoke-Command.md)

[Receive-PSSession](Receive-PSSession.md)

[Remove-PSSession](Remove-PSSession.md)
