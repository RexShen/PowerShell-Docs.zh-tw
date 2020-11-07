---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/receive-pssession?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Receive-PSSession
ms.openlocfilehash: b0177a00bbbf93659775ee94f7d4898a99f570f3
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2020
ms.locfileid: "94345573"
---
# Receive-PSSession

## 概要

針對已中斷連線的工作階段取得其命令結果

## SYNTAX

### 工作階段 (預設)

```
Receive-PSSession [-Session] <PSSession> [-OutTarget <OutTarget>] [-JobName <String>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### Id

```
Receive-PSSession [-Id] <Int32> [-OutTarget <OutTarget>] [-JobName <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### ComputerSessionName

```
Receive-PSSession [-ComputerName] <String> [-ApplicationName <String>] [-ConfigurationName <String>]
 -Name <String> [-OutTarget <OutTarget>] [-JobName <String>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [-Port <Int32>]
 [-UseSSL] [-SessionOption <PSSessionOption>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ComputerInstanceId

```
Receive-PSSession [-ComputerName] <String> [-ApplicationName <String>] [-ConfigurationName <String>]
 -InstanceId <Guid> [-OutTarget <OutTarget>] [-JobName <String>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [-Port <Int32>]
 [-UseSSL] [-SessionOption <PSSessionOption>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ConnectionUriSessionName

```
Receive-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri> [-AllowRedirection]
 -Name <String> [-OutTarget <OutTarget>] [-JobName <String>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-SessionOption <PSSessionOption>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ConnectionUriInstanceId

```
Receive-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri> [-AllowRedirection]
 -InstanceId <Guid> [-OutTarget <OutTarget>] [-JobName <String>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-SessionOption <PSSessionOption>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceId

```
Receive-PSSession -InstanceId <Guid> [-OutTarget <OutTarget>] [-JobName <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### 會話

```
Receive-PSSession -Name <String> [-OutTarget <OutTarget>] [-JobName <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION

`Receive-PSSession`Cmdlet 會取得已中斷連線 ( **PSSession** ) 的 PowerShell 會話中執行命令的結果。 如果會話目前已連線，則 `Receive-PSSession` 會取得會話中斷連接時正在執行的命令結果。 如果會話仍處於中斷線上狀態，則會 `Receive-PSSession` 連接到會話、繼續所有已暫停的命令，並取得會話中執行之命令的結果。

此 Cmdlet 是在 PowerShell 3.0 中引進。

除了命令之外，您還可以使用 `Receive-PSSession` `Connect-PSSession` 。
`Receive-PSSession` 可以連接到在其他會話或其他電腦上啟動的任何已中斷連線或重新連線的會話。

`Receive-PSSession`適用于 **PSSessions** 使用 `Disconnect-PSSession` Cmdlet 或 `Invoke-Command` **InDisconnectedSession** 參數刻意中斷連線的 pssession。 或意外中斷連線，因為網路中斷。

如果您使用此 `Receive-PSSession` Cmdlet 來連線到沒有任何命令正在執行或已暫止的會話，則會 `Receive-PSSession` 連接到會話，但不會傳回任何輸出或錯誤。

如需中斷連線工作階段功能的詳細資訊，請參閱 [about_Remote_Disconnected_Sessions](./About/about_Remote_Disconnected_Sessions.md)。

某些範例會使用展開來減少行長度，並提高可讀性。 如需詳細資訊，請參閱 [about_Splatting](./About/about_Splatting.md)。

## 範例

### 範例1：連接到 PSSession

此範例會連線到遠端電腦上的會話，並取得會話中執行之命令的結果。

```powershell
Receive-PSSession -ComputerName Server01 -Name ITTask
```

`Receive-PSSession`使用 **ComputerName** 參數指定遠端電腦。 **Name** 參數會識別 Server01 電腦上的 ITTask 會話。 此範例會取得在 ITTask 會話中執行之命令的結果。

因為命令不使用 **OutTarget** 參數，所以結果會出現在命令列上。

### 範例2：取得已中斷連線會話上所有命令的結果

此範例會取得在兩部遠端電腦上所有已中斷連線的會話中執行之所有命令的結果。

如果有任何會話未中斷連線或未執行命令，則 `Receive-PSSession` 不會連接到會話，也不會傳回任何輸出或錯誤。

```powershell
Get-PSSession -ComputerName Server01, Server02 | Receive-PSSession
```

`Get-PSSession` 使用 **ComputerName** 參數來指定遠端電腦。 物件會向下傳送到管線 `Receive-PSSession` 。

### 範例3：取得會話中執行之腳本的結果

此範例會使用 `Receive-PSSession` Cmdlet 來取得在遠端電腦的會話中執行之腳本的結果。

```powershell
$parms = @{
  ComputerName = "Server01"
  Name = "ITTask"
  OutTarget = "Job"
  JobName = "ITTaskJob01"
  Credential = "Domain01\Admin01"
}
Receive-PSSession @parms
```

```Output
Id     Name            State         HasMoreData     Location
--     ----            -----         -----------     --------
16     ITTaskJob01     Running       True            Server01
```

命令使用 **ComputerName** 與 **Name** 參數，識別已中斷連線的工作階段。
它會使用 **OutTarget** 參數搭配作業的值，以指示 `Receive-PSSession` 將結果作為作業傳回。 **JobName** 參數會在重新連接的會話中指定作業的名稱。
**Credential** 參數會 `Receive-PSSession` 使用網域系統管理員的許可權來執行命令。

輸出會顯示 `Receive-PSSession` 在目前的會話中，以作業形式傳回結果。 若要取得工作結果，請使用 `Receive-Job` 命令

### 範例4：在網路中斷之後取得結果

此範例會在 `Receive-PSSession` 網路中斷中斷會話連線之後，使用 Cmdlet 來取得工作的結果。 PowerShell 會在接下來的四分鐘內，每秒自動嘗試重新連線會話一次，而且只有在四分鐘間隔中的所有嘗試都失敗時，才會放棄投入時間。

```
PS> $s = New-PSSession -ComputerName Server01 -Name AD -ConfigurationName ADEndpoint
PS> $s

Id  Name   ComputerName    State        ConfigurationName     Availability
--  ----   ------------    -----        -----------------     ------------
8   AD      Server01       Opened       ADEndpoint               Available


PS> Invoke-Command -Session $s -FilePath \\Server12\Scripts\SharedScripts\New-ADResolve.ps1

Running "New-ADResolve.ps1"

# Network outage
# Restart local computer
# Network access is not re-established within 4 minutes


PS> Get-PSSession -ComputerName Server01

Id  Name   ComputerName    State          ConfigurationName      Availability
--  ----   ------------    -----          -----------------      ------------
1  Backup  Server01        Disconnected   Microsoft.PowerShell           None
8  AD      Server01        Disconnected   ADEndpoint                     None


PS> Receive-PSSession -ComputerName Server01 -Name AD -OutTarget Job -JobName AD

Job Id   Name      State         HasMoreData     Location
--       ----      -----         -----------     --------
16       ADJob     Running       True            Server01


PS> Get-PSSession -ComputerName Server01

Id  Name    ComputerName    State         ConfigurationName     Availability
--  ----    ------------    -----         -----------------     ------------
1  Backup   Server01        Disconnected  Microsoft.PowerShell          Busy
8  AD       Server01        Opened        ADEndpoint               Available
```

此 `New-PSSession` Cmdlet 會在 Server01 電腦上建立會話，並將會話儲存在 `$s` 變數中。 此 `$s` 變數會顯示狀態為開啟 **狀態** ，且 **可用性** 可以使用。 這些值表示您已連接到會話，而且可以在會話中執行命令。

此 `Invoke-Command` Cmdlet 會在變數中的會話中執行腳本 `$s` 。 指令碼開始執行並傳回資料，但是網路中斷而中斷了工作階段。 使用者必須結束工作階段並重新啟動本機電腦。

當電腦重新開機時，使用者會啟動 PowerShell 並執行 `Get-PSSession` 命令，以取得 Server01 電腦上的會話。 輸出顯示 Server01 電腦上仍有 **AD** 會話。 此 **狀態** 表示 **AD** 會話已中斷連線。 [無] 的 [ **可用性** ] 值表示會話未連接到任何用戶端會話。

此 `Receive-PSSession` Cmdlet 會重新連接至 **AD** 會話，並取得會話中執行之腳本的結果。 此命令會使用 **OutTarget** 參數，在名為 **adjob 之** 的作業中要求結果。 此命令會傳回工作物件，且輸出會指出腳本仍在執行中。

`Get-PSSession`Cmdlet 可用來檢查工作狀態。 輸出會確認 Cmdlet 重新連線 `Receive-PSSession` 至 **AD** 會話，該會話現在已開啟且可供命令使用。 而且，腳本會繼續執行，並取得腳本結果。

### 範例5：重新連線至已中斷連線的會話

此範例會使用指令 `Receive-PSSession` 程式來重新連線到刻意中斷連線的會話，並取得會話中執行之工作的結果。

```
PS> $parms = @{
      InDisconnectedSession = $True
      ComputerName = "Server01", "Server02", "Server30"
      FilePath = "\\Server12\Scripts\SharedScripts\Get-BugStatus.ps1"
      Name = "BugStatus"
      SessionOption = @{IdleTimeout = 86400000}
      ConfigurationName = "ITTasks"
    }
PS> Invoke-Command @parms
PS> Exit


PS> $s = Get-PSSession -ComputerName Server01, Server02, Server30 -Name BugStatus
PS> $s

Id  Name   ComputerName    State         ConfigurationName     Availability
--  ----   ------------    -----         -----------------     ------------
1  ITTask  Server01        Disconnected  ITTasks                       None
8  ITTask  Server02        Disconnected  ITTasks                       None
2  ITTask  Server30        Disconnected  ITTasks                       None


PS> $Results = Receive-PSSession -Session $s
PS> $s

Id  Name   ComputerName    State         ConfigurationName     Availability
--  ----   ------------    -----         -----------------     ------------
1  ITTask  Server01        Opened        ITTasks                  Available
8  ITTask  Server02        Opened        ITTasks                  Available
2  ITTask  Server30        Opened        ITTasks                  Available


PS> $Results

Bug Report - Domain 01
----------------------
ComputerName          BugCount          LastUpdated
--------------        ---------         ------------
Server01              121               Friday, December 30, 2011 5:03:34 PM
```

此 `Invoke-Command` Cmdlet 會在三部遠端電腦上執行腳本。 因為腳本會收集並匯總來自多個資料庫的資料，所以通常會將腳本花在很長的時間才能完成。 此命令會使用 **InDisconnectedSession** 參數來啟動腳本，然後立即中斷會話的連線。 **SessionOption** 參數會擴充已中斷連線會話的 **IdleTimeout** 值。 中斷連線的會話在中斷連接時，會被視為閒置。 請務必將閒置超時時間設定為足夠的時間，讓命令可以完成，而且您可以重新連線到會話。 只有當您建立 **PSSession** 時才可以設定 **IdleTimeout** ，而且只有在中斷與其的連接時才會變更。 當您連接至 **PSSession** 或接收其結果時，無法變更 **IdleTimeout** 值。 執行命令之後，使用者會結束 PowerShell 並關閉電腦。

下一天，使用者會繼續 Windows、啟動 PowerShell，並使用 `Get-PSSession` 來取得腳本執行所在的會話。 此命令會依電腦名稱稱、會話名稱和會話設定的名稱來識別會話，並將會話儲存在 `$s` 變數中。 `$s`系統會顯示變數的值，並顯示會話已中斷連線，但不在忙碌中。

`Receive-PSSession`Cmdlet 會連接到變數中的會話 `$s` 並取得其結果。
命令會將結果儲存在 `$Results` 變數中。 `$s`變數隨即顯示，並顯示會話已連線且可供命令使用。

變數中的腳本結果 `$Results` 會顯示在 PowerShell 主控台中。 如果有任何結果非預期，使用者可以在會話中執行命令來調查根本原因。

### 範例6：在已中斷連線的會話中執行工作

此範例顯示在已中斷連線的會話中執行的工作會發生什麼事。

```
PS> $s = New-PSSession -ComputerName Server01 -Name Test
PS> $j = Invoke-Command -Session $s { 1..1500 | Foreach-Object {"Return $_"; sleep 30}} -AsJob
PS> $j

Id     Name           State         HasMoreData     Location
--     ----           -----         -----------     --------
16     Job1           Running       True            Server01


PS> $s | Disconnect-PSSession

Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1  Test   Server01        Disconnected  Microsoft.PowerShell          None


PS> $j

Id     Name           State         HasMoreData     Location
--     ----           -----         -----------     --------
16     Job1           Disconnected  True            Server01


PS> Receive-Job $j -Keep

Return 1
Return 2


PS> $s2 = Connect-PSSession -ComputerName Server01 -Name Test
PS> $j2 = Receive-PSSession -ComputerName Server01 -Name Test
PS> Receive-Job $j

Return 3
Return 4
```

此 `New-PSSession` Cmdlet 會在 Server01 電腦上建立測試會話。 命令會將工作階段儲存於 `$s` 變數中。

此 `Invoke-Command` Cmdlet 會在變數中的會話中執行命令 `$s` 。 此命令會使用 **AsJob** 參數將命令當作工作執行，並在目前的會話中建立工作物件。
此命令會傳回儲存在變數中的工作物件 `$j` 。 `$j`變數會顯示工作物件。

變數中的會話物件 `$s` 會沿著管線向下傳送 `Disconnect-PSSession` ，且會話會中斷連線。

`$j`變數隨即顯示，並顯示中斷連接工作物件到變數中的效果 `$j` 。 工作狀態現在為「已中斷連線」。

`Receive-Job`會在變數中的作業上執行 `$j` 。 輸出顯示作業在會話與工作中斷連接之前，開始傳回輸出。

此 `Connect-PSSession` Cmdlet 會在相同的用戶端會話中執行。 此命令會重新連接至 Server01 電腦上的測試會話，並將會話儲存在 `$s2` 變數中。

`Receive-PSSession`Cmdlet 會取得會話中執行之工作的結果。 因為此命令是在相同的會話中執行，所以 `Receive-PSSession` 預設會以作業形式傳回結果，並重複使用相同的工作物件。 此命令會將工作儲存在 `$j2` 變數中。 `Receive-Job`Cmdlet 會取得變數中工作的結果 `$j` 。

## PARAMETERS

### -AllowRedirection

指出此 Cmdlet 允許將此連線重新導向至替代的統一資源識別項 (URI) 。

使用 **ConnectionURI** 參數時，遠端目的地可傳回重新導向至不同 URI 的指示。 根據預設，PowerShell 不會重新導向連線，但是您可以使用這個參數讓它重新導向連接。

您也可以變更 **MaximumConnectionRedirectionCount** 工作階段選項值，限制連線重新導向的次數。 使用 Cmdlet 的 **MaximumRedirection** 參數， `New-PSSessionOption` 或設定喜好設定變數的 **MaximumConnectionRedirectionCount** 屬性 `$PSSessionOption` 。 預設值為 5。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -ApplicationName

指定應用程式。 此 Cmdlet 只會連接到使用指定應用程式的會話。

輸入連線 URI 的應用程式名稱區段。 例如，在下列連接 URI 中，WSMan 是應用程式名稱： `http://localhost:5985/WSMAN` 。

工作階段的應用程式名稱儲存在工作階段的 **Runspace.ConnectionInfo.AppName** 屬性中。

參數的值可用來選取和篩選會話。 它不會變更會話使用的應用程式。

```yaml
Type: System.String
Parameter Sets: ComputerSessionName, ComputerInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Authentication

指定在命令中用來驗證使用者認證的機制，以重新連線到中斷連線的會話。 此參數可接受的值為：

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
Parameter Sets: ComputerSessionName, ComputerInstanceId, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -CertificateThumbprint

指定具有連線至已中斷連線工作階段權限之使用者帳戶的數位公開金鑰憑證 (X509)。 請輸入憑證的憑證指紋。

憑證將用於用戶端憑證式驗證。 憑證只能對應至本機使用者帳戶，而且無法使用網域帳戶。

若要取得憑證指紋，請 `Get-Item` `Get-ChildItem` 在 PowerShell 磁片磁碟機中使用或命令 `Cert:` 。

```yaml
Type: System.String
Parameter Sets: ComputerSessionName, ComputerInstanceId, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

指定儲存已中斷連線工作階段的電腦。 會話會儲存在伺服器端的電腦上，或連接的接收端。 預設是本機電腦。

輸入一部電腦 (FQDN) 的 NetBIOS 名稱、IP 位址或完整功能變數名稱。
不允許使用萬用字元。 若要指定本機電腦，請輸入電腦名稱稱、點 (`.`) 、 `$env:COMPUTERNAME` 或 localhost。

```yaml
Type: System.String
Parameter Sets: ComputerSessionName, ComputerInstanceId
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ConfigurationName

指定會話設定的名稱。 此 Cmdlet 只會連接到使用指定會話設定的會話。

輸入工作階段設定的設定名稱或完整資源 URI。 若您僅指定設定名稱，則會在前面加上下列架構 URI：

`http://schemas.microsoft.com/powershell`.

工作階段的設定名稱儲存在工作階段的 **ConfigurationName** 屬性中。

參數的值可用來選取和篩選會話。 它不會變更會話使用的會話設定。

如需會話設定的詳細資訊，請參閱 [about_Session_Configurations](./About/about_Session_Configurations.md)。

```yaml
Type: System.String
Parameter Sets: ComputerSessionName, ComputerInstanceId, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ConnectionUri

指定 URI，定義用來重新連線至已中斷連線會話的連接端點。

此 URI 必須是完整的 URI。 字串的格式如下所示：

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

預設值如下：

`http://localhost:5985/WSMAN`

如果您未指定連接 URI，您可以使用 **UseSSL** 、 **ComputerName** 、 **Port** 及 **ApplicationName** 參數來指定連接 uri 值。

URI 的 **Transport** 區段有效值為 HTTP 與 HTTPS。 如果您指定具有傳輸區段的連線 URI，但未指定埠，則會使用標準埠：80（適用于 HTTP）和443（適用于 HTTPS）來建立會話。 若要使用 PowerShell 遠端的預設埠，請指定 HTTP 的埠5985或 HTTPS 的5986。

如果目的地電腦將連線重新導向至不同的 URI，除非您在命令中使用 **AllowRedirection** 參數，否則 PowerShell 會禁止重新導向。

```yaml
Type: System.Uri
Parameter Sets: ConnectionUriSessionName, ConnectionUriInstanceId
Aliases: URI, CU

Required: True
Position: 0
Default value: http://localhost:5985/WSMAN
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Credential

指定具有連線至已中斷連線工作階段權限的使用者帳戶。 預設為目前使用者。

輸入使用者名稱（例如 **User01** 或 **Domain01\User01** ），或輸入 Cmdlet 所產生的 **PSCredential** 物件 `Get-Credential` 。 如果您輸入使用者名稱，系統就會提示您輸入密碼。

認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。

> [!NOTE]
> 如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerSessionName, ComputerInstanceId, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

指定已中斷連線會話的識別碼。 只有當已中斷連線的會話先前連接到目前的會話時， **識別碼** 參數才有效。

當會話儲存在本機電腦上，但未連接到目前的會話時，此參數有效，但不有效。

```yaml
Type: System.Int32
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -InstanceId

指定已中斷連線工作階段的執行個體識別碼。 實例識別碼是 GUID，可唯一識別本機或遠端電腦上的 **PSSession** 。 實例識別碼儲存在 **PSSession** 的 **InstanceID** 屬性中。

```yaml
Type: System.Guid
Parameter Sets: ComputerInstanceId, ConnectionUriInstanceId, InstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -JobName

指定傳回之作業的易記名稱 `Receive-PSSession` 。

`Receive-PSSession` 當 **OutTarget** 參數的值為 job，或在已中斷連線會話中執行的工作在目前的會話中啟動時，會傳回工作。

如果在已中斷連線的會話中執行的工作是在目前會話中啟動，則 PowerShell 會重複使用會話中的原始工作物件，並忽略 **JobName** 參數的值。

如果在已中斷連線的會話中執行的工作是在不同的會話中啟動，則 PowerShell 會建立新的工作物件。 它會使用預設名稱，但是您可以使用此參數來變更名稱。

如果 **OutTarget** 參數的預設值或明確值不是工作，則命令會成功，但是 **JobName** 參數沒有任何作用。

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

### -Name

指定已中斷連線工作階段的好記名稱。

```yaml
Type: System.String
Parameter Sets: ComputerSessionName, ConnectionUriSessionName, SessionName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutTarget

決定如何傳回工作階段結果。 此參數可接受的值為：

- **作業** 。 以非同步方式，傳回工作物件中的結果。 您可以使用 **JobName** 參數，指定工作的名稱或新名稱。
- **主機** 。 將結果傳回命令列 (同步)。 若正在繼續命令，或結果包含大量物件，則回應可能會延遲。

**OutTarget** 參數的預設值為 Host。 如果在已中斷連線的會話中接收的命令是在目前會話中啟動，則 **OutTarget** 參數的預設值會是命令啟動的形式。 如果命令是以作業的形式啟動，則預設會以工作傳回。 否則，預設會將它傳回至主機程式。

主機程式在命令列顯示傳回的物件時，通常不會有延遲，但是也可能不同。

```yaml
Type: Microsoft.PowerShell.Commands.OutTarget
Parameter Sets: (All)
Aliases:
Accepted values: Default, Host, Job

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Port

指定遠端電腦用來重新連線至會話的網路埠。 若要連接到遠端電腦，它必須在連線使用的埠上接聽。 預設的埠是5985，也就是 HTTP 的 WinRM 埠和5986，也就是 HTTPS 的 WinRM 埠。

使用替代埠之前，您必須先將遠端電腦上的 WinRM 接聽程式設定為在該埠上接聽。 若要設定接聽程式，請在 PowerShell 提示字元中輸入下列兩個命令：

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

除非必要，否則請勿使用 **Port** 參數。 命令中設定的埠會套用到命令執行所在的所有電腦或會話。 替代的連接埠設定可能使得命令無法在全部電腦上執行。

```yaml
Type: System.Int32
Parameter Sets: ComputerSessionName, ComputerInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Session

指定已中斷連線的工作階段。 輸入包含 **pssession** 的變數，或輸入可建立或取得 **pssession** 的命令，例如 `Get-PSSession` 命令。

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: Session
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SessionOption

指定會話的 advanced 選項。 輸入 **SessionOption** 物件（例如您使用 Cmdlet 建立的物件 `New-PSSessionOption` ），或輸入雜湊表，其中索引鍵為會話選項名稱，而值為會話選項值。

選項的預設值取決於 `$PSSessionOption` 喜好設定變數的值（如果已設定）。 否則，將以工作階段設定中設定的選項建立預設值。

會話選項值的優先順序高於 `$PSSessionOption` 喜好設定變數和會話設定中設定之會話的預設值。 不過，它們的優先順序不會高於會話設定中所設定的最大值、配額或限制。

如需包含預設值之會話選項的描述，請參閱 `New-PSSessionOption` 。 如需 **$PSSessionOption** 喜好設定變數的詳細資訊，請參閱 [about_Preference_Variables](./About/about_Preference_Variables.md)。 如需會話設定的詳細資訊，請參閱 [about_Session_Configurations](./About/about_Session_Configurations.md)。

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerSessionName, ComputerInstanceId, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSSL

指出此 Cmdlet 會使用安全通訊端層 (SSL) 通訊協定來連線到中斷連線的會話。 預設不會使用 SSL。

WS-Management 加密透過網路傳輸的所有 PowerShell 內容。 **UseSSL** 為額外的保護，可使用 HTTPS 連線取代 HTTP 連線來傳送資料。

如果您使用此參數，而且在用於命令的埠上無法使用 SSL，則命令會失敗。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerSessionName, ComputerInstanceId
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

在執行 Cmdlet 前提示您確認。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

顯示執行 Cmdlet 後會發生的情況。 不會執行此 Cmdlet。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.Management.Automation.Runspaces.PSSession

您可以使用管線將會話物件傳送至此 Cmdlet，例如 Cmdlet 所傳回的物件 `Get-PSSession` 。

### System.Int32

您可以透過管線將會話識別碼傳送至此 Cmdlet。

### System.Guid

您可以透過管線將會話的實例識別碼傳送至此 Cmdlet。

### System.String

您可以透過管線將會話名稱傳送至此 Cmdlet。

## 輸出

### 管理. 作業或 PSObject

此 Cmdlet 會傳回在已中斷連線會話中執行的命令結果（如果有的話）。 如果 **OutTarget** 參數的值或預設值為 job，則會傳回 `Receive-PSSession` 工作物件。 否則，它會傳回代表該命令結果的物件。

## 注意

此 Cmdlet 僅適用于 Windows 平臺。

`Receive-PSSession` 只從已中斷連線的會話取得結果。 只有在執行 PowerShell 3.0 或更新版本的電腦上連線或終止的會話，才能中斷連線並重新連接。

如果在已中斷連線的會話中執行的命令未產生結果，或是結果已經傳回至另一個會話，則 `Receive-PSSession` 不會產生任何輸出。

會話的輸出緩衝處理模式會決定會話中斷連線時，會話中的命令如何管理輸出。 當會話的 **OutputBufferingMode** 選項值為 Drop 且輸出緩衝區已滿時，命令就會開始刪除輸出。 `Receive-PSSession` 無法復原此輸出。 如需輸出緩衝處理模式選項的詳細資訊，請參閱 [PSSessionOption](New-PSSessionOption.md) 和 [>new-pstransportoption](New-PSTransportOption.md) Cmdlet 的說明文章。

當您連接到 **pssession** 或接收結果時，無法變更 **PSSession** 的空閒超時值。 的 **SessionOption** 參數 `Receive-PSSession` 會採用具有 **IdleTimeout** 值的 **SessionOption** 物件。 不過，當 **IdleTimeout** **SessionOption** 它 **IdleTimeout** `$PSSessionOption` 連接到 **PSSession** 或接收結果時，會忽略 SessionOption 物件的 idletimeout 值和變數的 idletimeout 值。

- 當您建立 **pssession** 時，可以使用 **PSSession** `New-PSSession` 或 `Invoke-Command` Cmdlet，以及從 **pssession** 中斷連接時，設定和變更 pssession 的閒置時間。
- **PSSession** 的 **IdleTimeout** 屬性對中斷連線的會話而言是不可或缺的，因為它會決定中斷連線的會話在遠端電腦上的維護時間。 已中斷連線的工作階段一被中斷連線，便被視為閒置，即使命令仍然在已中斷連線的工作階段中執行也是如此。

如果您使用指令程式的 **AsJob** 參數在遠端會話中啟動啟動作業 `Invoke-Command` ，則會在目前的會話中建立工作物件，即使工作是在遠端會話中執行也一樣。 如果您中斷遠端會話的連線，目前會話中的工作物件就會與工作中斷連線。 工作物件包含傳回的任何結果，但不會從已中斷連線會話中的作業接收新的結果。

如果不同的用戶端連接到包含執行中工作的會話，則新連線的會話將無法使用傳遞至原始會話中原始工作物件的結果。 只有未傳遞至原始工作物件的結果，才能在重新連線的工作階段中使用。

同樣地，如果您在會話中啟動腳本，然後從會話中斷連線，則在中斷連接之前，腳本傳遞給會話的任何結果都不會提供給連線到該會話的另一個用戶端使用。

若要防止您要中斷連線的會話中遺失資料，請使用 Cmdlet 的 **InDisconnectedSession** 參數 `Invoke-Command` 。 因為此參數會避免將結果傳回目前工作階段，因此重新連線至工作階段時，所有結果都可供使用。

您也可以使用 `Invoke-Command` Cmdlet `Start-Job` 在遠端會話中執行命令，以避免資料遺失。 在此狀況下，工作物件將建立於遠端工作階段中。 您無法使用 `Receive-PSSession` Cmdlet 來取得工作結果。 相反地，請使用 `Connect-PSSession` Cmdlet 連接到會話，然後使用 `Invoke-Command` Cmdlet `Receive-Job` 在會話中執行命令。

當包含執行中工作的會話中斷連線，然後重新連線時，只有在作業已中斷連線並重新連線至相同會話，且重新連線的命令未指定新工作名稱時，才會重複使用原始工作物件。 如果會話重新連線至不同的用戶端會話，或指定了新的作業名稱，則 PowerShell 會為新會話建立新的工作物件。

當您中斷連接 **PSSession** 時，會話狀態會中斷連線，而且可用性為 None。

- **State** 屬性的值是相對於目前工作階段。 值為「已中斷連線」表示 **PSSession** 未連接到目前的會話。 但是，它並不表示 **PSSession** 與所有會話中斷連接。 它可能連線不同的工作階段。
  若要判斷是否可以連線或重新連線工作階段，請使用 **Availability** 屬性。
- **Availability** 值為 None 表示您可以連線工作階段。 「忙碌」值表示您無法連接到 **PSSession** ，因為它已連接到另一個會話。
- 如需會話的 **State** 屬性值的詳細資訊，請參閱 MSDN library 中的 [ runspacestate](/dotnet/api/system.management.automation.runspaces.runspacestate) 。
- 如需會話的 **Availability** 屬性值的詳細資訊，請參閱 [RunspaceAvailability](/dotnet/api/system.management.automation.runspaces.runspaceavailability)。

## 相關連結

[about_PSSessions](./About/about_PSSessions.md)

[about_Remote](./About/about_Remote.md)

[about_Remote_Disconnected_Sessions](./About/about_Remote_Disconnected_Sessions.md)

[about_Session_Configurations](./About/about_Session_Configurations.md)

[Connect-PSSession](Connect-PSSession.md)

[Enter-PSSession](Enter-PSSession.md)

[Exit-PSSession](Exit-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Invoke-Command](Invoke-Command.md)

[New-PSSession](New-PSSession.md)

[New-PSSessionOption](New-PSSessionOption.md)

[New-PSTransportOption](New-PSTransportOption.md)

[Remove-PSSession](Remove-PSSession.md)
