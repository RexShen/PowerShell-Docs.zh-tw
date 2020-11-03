---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/connect-pssession?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Connect-PSSession
ms.openlocfilehash: 61f1d13628763710f01cf0c2ec413f446e4bdd39
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205544"
---
# Connect-PSSession

## 概要
重新連線至已中斷連線的工作階段。

## SYNTAX

### Name (預設值)

```
Connect-PSSession -Name <String[]> [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 工作階段

```
Connect-PSSession [-Session] <PSSession[]> [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ComputerNameGuid

```
Connect-PSSession -ComputerName <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 -InstanceId <Guid[]> [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-SessionOption <PSSessionOption>]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ComputerName

```
Connect-PSSession -ComputerName <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 [-Name <String[]>] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-SessionOption <PSSessionOption>]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ConnectionUriGuid

```
Connect-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri[]> [-AllowRedirection]
 -InstanceId <Guid[]> [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-SessionOption <PSSessionOption>] [-ThrottleLimit <Int32>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### ConnectionUri

```
Connect-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri[]> [-AllowRedirection] [-Name <String[]>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-SessionOption <PSSessionOption>] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceId

```
Connect-PSSession -InstanceId <Guid[]> [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Id

```
Connect-PSSession [-ThrottleLimit <Int32>] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

**連接 PSSession** Cmdlet 會重新連線至已中斷連線 ( **pssession** ) 的使用者管理 PowerShell 會話。
它適用于刻意中斷連線的會話，例如使用 Disconnect-PSSession Cmdlet 或 Invoke-Command Cmdlet 的 *InDisconnectedSession* 參數，以及不慎中斷連線的會話，例如暫時性網路中斷。

**Connect-PSSession** 可連接到由相同使用者啟動的任何已中斷連線的會話。
這些包括從其他電腦上的其他會話啟動或中斷連線的電腦。

不過， **連接 PSSession** 無法連線到已中斷或已關閉的會話，或使用 Enter-PSSession Cmdlet 啟動的互動式會話。
您也無法連線其他使用者啟動的工作階段，除非您可以提供建立工作階段之使用者的認證。

如需中斷連線工作階段功能的詳細資訊，請參閱 about_Remote_Disconnected_Sessions。

此 Cmdlet 是在 Windows PowerShell 3.0 中引進。

## 範例

### 範例1：重新連接到會話

```
PS C:\> Connect-PSSession -ComputerName Server01 -Name ITTask
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 4 ITTask          Server01        Opened        ITTasks                  Available
```

此命令重新連線至 Server01 電腦上的 ITTask 工作階段。

輸出顯示命令成功。
會話的 **狀態** 是開啟的，而且 **可用性** 可以使用，這表示您可以在會話中執行命令。

### 範例2：中斷連線和重新連接的效果

```
PS C:\> Get-PSSession

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 Backups         Localhost       Opened        Microsoft.PowerShell     Available


PS C:\> Get-PSSession | Disconnect-PSSession

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 Backups         Localhost       Disconnected  Microsoft.PowerShell          None


PS C:\> Get-PSSession | Connect-PSSession

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 Backups         Localhost       Opened        Microsoft.PowerShell     Available
```

此範例顯示中斷連線再重新連線工作階段的作用。

第一個命令使用 Get-PSSession Cmdlet。
若無 *ComputerName* 參數，命令只會取得目前工作階段中所建立的工作階段。

輸出顯示命令取得本機電腦上的 Backups 工作階段。
會話的 **狀態** 會開啟，並提供 **可用性** 。

第二個命令會使用 **取得 pssession** Cmdlet 來取得在目前會話中建立的 **PSSession** 物件，以及 **中斷連接 PSSession** Cmdlet 來中斷會話的連線。
輸出顯示 Backups 工作階段已中斷連線。
會話的 **狀態** 為「已中斷連線」，且 **可用性** 為「無」。

第三個命令會使用 **取得 pssession** Cmdlet 來取得在目前會話中建立的 **pssession** 物件，以及 **連接 pssession** 指令程式以重新連接會話。
輸出顯示 Backups 工作階段已重新連線。
會話的 **狀態** 會開啟，並提供 **可用性** 。

如果您在未中斷連線的會話上使用 **連接 PSSession** Cmdlet，此命令不會影響會話，且不會產生任何錯誤。

### 範例3：企業案例中的一系列命令

```
The administrator starts by creating a sessions on a remote computer and running a script in the session.The first command uses the **New-PSSession** cmdlet to create the ITTask session on the Server01 remote computer. The command uses the *ConfigurationName* parameter to specify the ITTasks session configuration. The command saves the sessions in the $s variable.
PS C:\> $s = New-PSSession -ComputerName Server01 -Name ITTask -ConfigurationName ITTasks

 The second command **Invoke-Command** cmdlet to start a background job in the session in the $s variable. It uses the *FilePath* parameter to run the script in the background job.
PS C:\> Invoke-Command -Session $s {Start-Job -FilePath \\Server30\Scripts\Backup-SQLDatabase.ps1}
Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
2      Job2            Running       True            Server01             \\Server30\Scripts\Backup...

The third command uses the Disconnect-PSSession cmdlet to disconnect from the session in the $s variable. The command uses the *OutputBufferingMode* parameter with a value of Drop to prevent the script from being blocked by having to deliver output to the session. It uses the *IdleTimeoutSec* parameter to extend the session time-out to 15 hours.When the command is completed, the administrator locks her computer and goes home for the evening.
PS C:\> Disconnect-PSSession -Session $s -OutputBufferingMode Drop -IdleTimeoutSec 60*60*15
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Disconnected  ITTasks               None

Later that evening, the administrator starts her home computer, logs on to the corporate network, and starts PowerShell. The fourth command uses the Get-PSSession cmdlet to get the sessions on the Server01 computer. The command finds the ITTask session.The fifth command uses the **Connect-PSSession** cmdlet to connect to the ITTask session. The command saves the session in the $s variable.
PS C:\> Get-PSSession -ComputerName Server01 -Name ITTask

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Disconnected  ITTasks               None


PS C:\> $s = Connect-PSSession -ComputerName Server01 -Name ITTask


Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Opened        ITTasks               Available

The sixth command uses the **Invoke-Command** cmdlet to run a Get-Job command in the session in the $s variable. The output shows that the job finished successfully.The seventh command uses the **Invoke-Command** cmdlet to run a Receive-Job command in the session in the $s variable in the session. The command saves the results in the $BackupSpecs variable.The eighth command uses the **Invoke-Command** cmdlet to runs another script in the session. The command uses the value of the $BackupSpecs variable in the session as input to the script.


PS C:\> Invoke-Command -Session $s {Get-Job}

Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
2      Job2            Completed     True            Server01             \\Server30\Scripts\Backup...

PS C:\> Invoke-Command -Session $s {$BackupSpecs = Receive-Job -JobName Job2}

PS C:\> Invoke-Command -Session $s {\\Server30\Scripts\New-SQLDatabase.ps1 -InitData $BackupSpecs.Initialization}

The ninth command disconnects from the session in the $s variable.The administrator closes PowerShell and closes the computer. She can reconnect to the session on the next day and check the script status from her work computer.
PS C:\> Disconnect-PSSession -Session $s -OutputBufferingMode Drop -IdleTimeoutSec 60*60*15
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Disconnected  ITTasks               None
```

此一系列命令示範如何在企業案例中使用 **Connect-PSSession** Cmdlet。
在此案例中，系統管理員在遠端電腦工作階段中啟動長時間執行的工作。
啟動工作之後，系統管理員從工作階段中斷連線，之後就回家了。
稍後，系統管理員登入家用電腦，並確認工作已完成，直到完成為止。

## PARAMETERS

### -AllowRedirection

指出此 Cmdlet 允許將此連接重新導向至替代 URI。

使用 *ConnectionURI* 參數時，遠端目的地可傳回重新導向至不同 URI 的指示。
根據預設，PowerShell 不會重新導向連線，但是您可以使用此參數允許它重新導向連接。

您也可以變更 **MaximumConnectionRedirectionCount** 工作階段選項值，限制連線重新導向的次數。
使用 New-PSSessionOption Cmdlet 的 *MaximumRedirection* 參數，或設定 **$PSSessionOption** 喜好設定變數的 **MaximumConnectionRedirectionCount** 屬性。
預設值為 5。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ConnectionUri, ConnectionUriGuid
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ApplicationName

指定應用程式的名稱。
此 Cmdlet 只會連接到使用指定應用程式的會話。

輸入連線 URI 的應用程式名稱區段。
例如，在下列連接 URI 中，應用程式名稱為 WSMan： `http://localhost:5985/WSMAN` 。
工作階段的應用程式名稱儲存在工作階段的 **Runspace.ConnectionInfo.AppName** 屬性中。

此參數的值可用來選取與篩選工作階段。
它不會變更工作階段使用的應用程式。

```yaml
Type: System.String
Parameter Sets: ComputerNameGuid, ComputerName
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

如需此參數值的詳細資訊，請參閱 MSDN library 中的 [AuthenticationMechanism 列舉](https://msdn.microsoft.com/library/system.management.automation.runspaces.authenticationmechanism) 。

注意：使用者認證會傳遞至要驗證之遠端電腦的「認證安全性支援提供者 (CredSSP)」驗證，是設計用於需要在一個以上資源進行驗證的命令，例如存取遠端網路共用。
此機制會使得遠端作業的安全性風險變高。
若遠端電腦遭到入侵，傳遞給它的認證便可用來控制網路工作階段。

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUri, ConnectionUriGuid
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CertificateThumbprint

指定具有連線至已中斷連線工作階段權限之使用者帳戶的數位公開金鑰憑證 (X509)。 請輸入憑證的憑證指紋。

憑證將用於用戶端憑證式驗證。
這些帳戶只能對應至本機使用者帳戶。
它們無法使用網域帳戶。

若要取得憑證指紋，請使用 PowerShell Cert：磁片磁碟機中的 Get-Item 或 Get-ChildItem 命令。

```yaml
Type: System.String
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUri, ConnectionUriGuid
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

指定儲存中斷連線工作階段的電腦。
會話會儲存在位於伺服器端或接收端連接端點的電腦上。
預設是本機電腦。

輸入電腦的 NetBIOS 名稱、IP 位址或完整網域名稱。
不允許使用萬用字元。
若要指定本機電腦，請輸入電腦名稱稱、localhost 或點 (。 ) 

```yaml
Type: System.String[]
Parameter Sets: ComputerNameGuid, ComputerName
Aliases: Cn

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ConfigurationName

只連線使用指定工作階段設定的工作階段。

輸入工作階段設定的設定名稱或完整資源 URI。
如果您只指定設定名稱，則會在前面加上下列架構 URI： `http://schemas.microsoft.com/powershell` 。
工作階段的設定名稱儲存在工作階段的 **ConfigurationName** 屬性中。

此參數的值可用來選取與篩選工作階段。
它不會變更工作階段使用的工作階段設定。

如需會話設定的詳細資訊，請參閱 [about_Session_Configurations](About/about_Session_Configurations.md)。

```yaml
Type: System.String
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUri, ConnectionUriGuid
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ConnectionUri

針對已中斷連線的會話，指定連接端點的 Uri。

此 URI 必須是完整的 URI。
這個字串的格式如下所示：

`\<Transport\>://\<ComputerName\>:\<Port\>/\<ApplicationName\>`

預設值如下：

`http://localhost:5985/WSMAN`

如果您沒有指定連接 URI，您可以使用 *UseSSL* 和 *Port* 參數來指定連接 uri 值。

URI 的 **Transport** 區段有效值為 HTTP 與 HTTPS。
若指定含傳輸區段的連線 URI，但未指定連接埠，將會以標準連接埠 80 (適用於 HTTP) 和 443 (適用於 HTTPS) 建立工作階段。
若要使用 PowerShell 遠端的預設埠，請指定 HTTP 的埠5985或 HTTPS 的5986。

如果目的地電腦將連線重新導向至不同的 URI，除非您在命令中使用 *AllowRedirection* 參數，否則 PowerShell 會禁止重新導向。

```yaml
Type: System.Uri[]
Parameter Sets: ConnectionUri, ConnectionUriGuid
Aliases: URI, CU

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Credential

指定具有連線至已中斷連線工作階段權限的使用者帳戶。
預設為目前使用者。

輸入使用者名稱（例如 **User01** 或 **Domain01\User01** ），或輸入 Cmdlet 所產生的 **PSCredential** 物件 `Get-Credential` 。 如果您輸入使用者名稱，系統就會提示您輸入密碼。

認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。

> [!NOTE]
> 如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUri, ConnectionUriGuid
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

指定已中斷連線工作階段的識別碼。
只有當已中斷連線的會話先前連接到目前的會話時， *識別碼* 參數才有效。

當工作階段儲存在本機電腦，但是未連線目前工作階段，則此參數有效，但沒有作用。

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InstanceId

指定已中斷連線工作階段的執行個體識別碼。

實例識別碼是 GUID，可唯一識別本機或遠端電腦上的 **PSSession** 。

實例識別碼儲存在 **PSSession** 的 **InstanceID** 屬性中。

```yaml
Type: System.Guid[]
Parameter Sets: ComputerNameGuid, ConnectionUriGuid, InstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

指定已中斷連線工作階段的好記名稱。

```yaml
Type: System.String[]
Parameter Sets: Name, ComputerName, ConnectionUri
Aliases:

Required: True (Name), False (ComputerName, ConnectionUri)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Port

指定遠端電腦上用來重新連線至工作階段的網路連接埠。
若要連線到遠端電腦，遠端電腦必須接聽連線使用的連接埠。
預設的埠是5985，也就是 HTTP 的 WinRM 埠和5986，也就是 HTTPS 的 WinRM 埠。

使用替代連接埠之前，必須先將遠端電腦上的 WinRM 接聽程式設定為在該連接埠進行接聽。
若要設定接聽程式，請在 PowerShell 提示字元中輸入下列兩個命令：

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

除非必要，否則請勿使用 *Port* 參數。
在命令中設定的連接埠，將套用於執行命令所在的所有電腦或工作階段。
替代的連接埠設定可能使得命令無法在全部電腦上執行。

```yaml
Type: System.Int32
Parameter Sets: ComputerNameGuid, ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Session

指定已中斷連線的工作階段。
輸入包含 **pssession** 物件的變數，或輸入可建立或取得 **pssession** 物件的命令，例如 Get-PSSession 命令。

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SessionOption

指定會話的 advanced 選項。
輸入 **SessionOption** 物件 (例如您使用 New-PSSessionOption Cmdlet 建立的物件) 或者雜湊表，其中索引鍵為工作階段選項名稱，而值為工作階段選項值。

選項的預設值是由 $PSSessionOption 喜好設定變數的值所決定 (若設定了該變數)。
否則，將以工作階段設定中設定的選項建立預設值。

工作階段選項值優先順序高於 $PSSessionOption 喜好設定變數與工作階段設定中設定的工作階段預設值。
不過，它們的優先順序不會高於工作階段設定中設定的最大值、配額或限制。

如需包含預設值之會話選項的描述，請參閱 < 新 PSSessionOption。
如需 **$PSSessionOption** 喜好設定變數的詳細資訊，請參閱 [about_Preference_Variables](About/about_Preference_Variables.md)。
如需會話設定的詳細資訊，請參閱 [about_Session_Configurations](About/about_Session_Configurations.md)。

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUri, ConnectionUriGuid
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

指定為執行此命令可建立的最大同時連線數。
若省略此參數，或輸入值為 0，則會使用預設值 32。

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

指出此 Cmdlet 會使用安全通訊端層 (SSL) 通訊協定來連線到中斷連線的會話。 預設不會使用 SSL。

WS-Management 加密透過網路傳輸的所有 PowerShell 內容。
*UseSSL* 參數是額外的保護，可跨 HTTPS 連接（而非 HTTP 連線）傳送資料。

如果您使用此參數，但是命令所用的埠上無法使用 SSL，則命令會失敗。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerNameGuid, ComputerName
Aliases:

Required: False
Position: Named
Default value: None
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

顯示執行 Cmdlet 後會發生的情況。
Cmdlet 並不會執行。

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

您可以使用管線將會話 ( **PSSession** ) 傳送至此 Cmdlet。

## 輸出

### System.Management.Automation.Runspaces.PSSession

此 Cmdlet 會傳回物件，代表它重新連接的會話。

## 注意

* **Connect-PSSession** 只會重新連接到已中斷連線的會話，也就是具有 [ **狀態** ] 屬性值為 [已中斷連線] 的會話。 只有連接到或結束的會話，才能中斷執行 Windows PowerShell 3.0 或更新版本的電腦。
* 如果您在未中斷連線的會話上使用 **連接 PSSession** ，此命令不會影響會話，也不會產生錯誤。
* 使用 *EnableNetworkAccess* 參數所建立之互動式權杖的已中斷連線回送會話，只能從建立該會話的電腦重新連接。 此限制可防止電腦遭受惡意存取。
* **PSSession** 的 **State** 屬性值是相對於目前的會話。
因此，[已 **中斷** 連線] 值表示 **PSSession** 未連接到目前的會話。 但是，它並不表示 **PSSession** 與所有會話中斷連接。 它可能連線不同的工作階段。 若要判斷是否可以連線或重新連線工作階段，請使用 **Availability** 屬性。

  **Availability** 值為 None 表示您可以連線工作階段。
「忙碌」值表示您無法連接到 **PSSession** ，因為它已連接到另一個會話。

  如需會話的 **State** 屬性值的詳細資訊，請參閱 MSDN library 中的 [ runspacestate 列舉](https://msdn.microsoft.com/library/system.management.automation.runspaces.runspacestate) 。

  如需會話的 **Availability** 屬性值的詳細資訊，請參閱 MSDN library 中的 [RunspaceAvailability 列舉](https://msdn.microsoft.com/library/system.management.automation.runspaces.runspaceavailability) 。

* 當您連接到 **pssession** 時，無法變更 **PSSession** 的空閒超時值。 *Connect-PSSession* 的 **SessionOption** 參數接受具有 **IdleTimeout** 值的 **SessionOption** 物件。 不過，連接至 **PSSession** 時，會忽略 **SessionOption** 物件的 **idletimeout** 值和 $PSSessionOption 變數的 **idletimeout** 值。

  當您建立 **pssession** 時，可以使用 **新的-PSSession** 或 **Invoke 命令** Cmdlet，以及當您中斷與 **pssession** 的連接時，設定和變更 **pssession** 的閒置時間。

  **PSSession** 的 **IdleTimeout** 屬性對中斷連線的會話而言是不可或缺的，因為它會決定中斷連線的會話在遠端電腦上的維護時間。
已中斷連線的工作階段一被中斷連線，便被視為閒置，即使命令仍然在已中斷連線的工作階段中執行也是如此。

## 相關連結

[Disconnect-PSSession](Disconnect-PSSession.md)

[Enter-PSSession](Enter-PSSession.md)

[Exit-PSSession](Exit-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSession](New-PSSession.md)

[New-PSSessionOption](New-PSSessionOption.md)

[New-PSTransportOption](New-PSTransportOption.md)

[Receive-PSSession](Receive-PSSession.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Remove-PSSession](Remove-PSSession.md)
