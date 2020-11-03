---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enter-PSSession
ms.openlocfilehash: 40d9da7d2e7e3233608b893b026c2b89c7155ab1
ms.sourcegitcommit: 9dddf1d2e91ebcd347fcfb7bf6ef670d49a12ab7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "93205755"
---
# Enter-PSSession

## 概要
啟動遠端電腦的互動式工作階段。

## SYNTAX

### ComputerName (預設值)

```
Enter-PSSession [-ComputerName] <String> [-EnableNetworkAccess] [-Credential <PSCredential>]
 [-ConfigurationName <String>] [-Port <Int32>] [-UseSSL] [-ApplicationName <String>]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### 工作階段

```
Enter-PSSession [[-Session] <PSSession>] [<CommonParameters>]
```

### Uri

```
Enter-PSSession [[-ConnectionUri] <Uri>] [-EnableNetworkAccess] [-Credential <PSCredential>]
 [-ConfigurationName <String>] [-AllowRedirection] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### InstanceId

```
Enter-PSSession [-InstanceId <Guid>] [<CommonParameters>]
```

### Id

```
Enter-PSSession [[-Id] <Int32>] [<CommonParameters>]
```

### 名稱

```
Enter-PSSession [-Name <String>] [<CommonParameters>]
```

### VMId

```
Enter-PSSession [-VMId] <Guid> -Credential <PSCredential> [-ConfigurationName <String>] [<CommonParameters>]
```

### VMName

```
Enter-PSSession [-VMName] <String> -Credential <PSCredential> [-ConfigurationName <String>]
 [<CommonParameters>]
```

### ContainerId

```
Enter-PSSession [-ContainerId] <String> [-ConfigurationName <String>] [-RunAsAdministrator]
 [<CommonParameters>]
```

## DESCRIPTION

`Enter-PSSession`Cmdlet 會啟動單一遠端電腦的互動式會話。 在會話期間，您輸入的命令會在遠端電腦上執行，就像您直接在遠端電腦上輸入一樣。 您一次只能有一個互動式工作階段。

通常，您會使用 **ComputerName** 參數來指定遠端電腦的名稱。
不過，您也可以使用針對互動式會話使用 Cmdlet 所建立的會話 `New-PSSession` 。 不過，您無法使用 `Disconnect-PSSession` 、 `Connect-PSSession` 或 `Receive-PSSession` Cmdlet 來中斷與互動式會話的連線或重新連接。

若要結束互動式會話並中斷與遠端電腦的連線，請使用 `Exit-PSSession` Cmdlet 或輸入 `exit` 。

## 範例

### 範例1：啟動互動式會話

```
PS C:\> Enter-PSSession
[localhost]: PS C:\>
```

此命令會在本機電腦上啟動互動式工作階段。 命令提示字元的變更，指出您現在在不同的工作階段中執行命令。

您輸入的命令會在新的工作階段中執行，而結果會以文字傳回預設的工作階段。

### 範例2：使用互動式會話

第一個命令會使用指令 `Enter-PSSession` 程式來啟動 Server01 遠端電腦的互動式會話。 當工作階段啟動時，命令提示字元會變成包含電腦名稱。
第二個命令會取得 Windows PowerShell 的進程，並將輸出重新導向至 Process.txt 的檔案。 命令會提交給遠端電腦，且此檔案會儲存在遠端電腦上。
第三個命令使用 **Exit** 關鍵字結束互動式會話，並關閉連接。
第四個命令確認 Process.txt 檔案位於遠端電腦上。 `Get-ChildItem`本機電腦上的 ( "dir" ) 命令找不到該檔案。

```powershell
PS C:\> Enter-PSSession -ComputerName Server01
[Server01]: PS C:\>
[Server01]: PS C:\> Get-Process PowerShell > C:\ps-test\Process.txt
[Server01]: PS C:\> exit
PS C:\>
PS C:\> dir C:\ps-test\process.txt
Get-ChildItem : Cannot find path 'C:\ps-test\process.txt' because it does not exist.
At line:1 char:4
+ dir <<<<  c:\ps-test\process.txt
```

此命令會顯示如何在遠端電腦中使用互動式工作階段。

### 範例3：使用 Session 參數

```powershell
PS C:\> $s = New-PSSession -ComputerName Server01
PS C:\> Enter-PSSession -Session $s
[Server01]: PS C:\>
```

這些命令使用的 **Session** 參數 `Enter-PSSession` ，在現有的 Windows PowerShell 會話中執行互動式會話 ( **PSSession** ) 。

### 範例4：啟動互動式會話，並指定埠和認證參數

```powershell
PS C:\> Enter-PSSession -ComputerName Server01 -Port 90 -Credential Domain01\User01
[Server01]: PS C:\>
```

此命令會啟動 Server01 電腦的互動式工作階段。 它會使用 **port** 參數來指定埠，並使用 **Credential** 參數來指定具有連線到遠端電腦之許可權的使用者帳戶。

### 範例5：停止互動式會話

```powershell
PS C:\> Enter-PSSession -ComputerName Server01
[Server01]: PS C:\> Exit-PSSession
PS C:\>
```

此範例顯示如何啟動和停止互動式工作階段。 第一個命令會使用 `Enter-PSSession` Cmdlet 來啟動 Server01 電腦的互動式會話。

第二個命令會使用 `Exit-PSSession` Cmdlet 來結束會話。 您也可以使用 **Exit** 關鍵字結束互動式會話。 `Exit-PSSession` 和 **Exit** 有相同的效果。

## PARAMETERS

### -AllowRedirection

允許重新導向此連線至替代「統一資源識別項 (URI)」。 依預設，不允許重新導向。

使用 **ConnectionURI** 參數時，遠端目的地可傳回重新導向至不同 URI 的指示。 根據預設，Windows PowerShell 不會重新導向連線，但是您可以使用此參數允許它重新導向連線。

您也可以變更 **MaximumConnectionRedirectionCount** 工作階段選項值，限制連線重新導向的次數。 使用 Cmdlet 的 **MaximumRedirection** 參數， `New-PSSessionOption` 或設定喜好設定變數的 **MaximumConnectionRedirectionCount** 屬性 `$PSSessionOption` 。 預設值為 5。

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

**WinRM** 服務會使用應用程式名稱來選取接聽程式，以服務連線要求。 此參數的值應該符合遠端電腦上接聽程式之 **URLPrefix** 屬性的值。

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

指定用來驗證使用者認證的機制。 此參數可接受的值為：

- 預設
- 基本
- Credssp
- Digest
- Kerberos
- 交涉
- NegotiateWithImplicitCredential

預設值為 Default。

CredSSP 驗證僅適用于 Windows Vista、Windows Server 2008 和更新版本的 Windows 作業系統。

如需此參數值的詳細資訊，請參閱 [AuthenticationMechanism 列舉](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。

注意：使用者認證會傳遞至要驗證之遠端電腦的「認證安全性支援提供者 (CredSSP)」驗證，是設計用於需要在一個以上資源進行驗證的命令，例如存取遠端網路共用。 此機制會使得遠端作業的安全性風險變高。 若遠端電腦遭到入侵，傳遞給它的認證便可用來控制網路工作階段。

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

若要取得憑證，請使用 `Get-Item` `Get-ChildItem` Windows PowerShell Cert：磁片磁碟機中的或命令。

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

指定電腦名稱稱。 此 Cmdlet 會啟動與指定遠端電腦的互動式會話。 僅輸入電腦名稱。 預設是本機電腦。

輸入電腦的 NetBIOS 名稱、IP 位址或完整網域名稱。 您也可以使用管線將電腦名稱稱傳送至 `Enter-PSSession` 。

若要在 **ComputerName** 參數的值中使用 IP 位址，命令必須包含 **Credential** 參數。 此外，必須將電腦設定為使用 HTTPS 傳輸，或必須在本機電腦的 WinRM TrustedHosts 清單中包含遠端電腦的 IP 位址。 如需將電腦名稱稱新增到 TrustedHosts 清單的指示，請參閱 [about_Remote_Troubleshooting](About/about_Remote_Troubleshooting.md)中的「如何將電腦新增到信任的主機清單」。

注意：在 Windows Vista 和更新版本的 Windows 作業系統中，若要在 **ComputerName** 參數的值中包含本機電腦，您必須使用 [以系統管理員身分執行] 選項啟動 Windows PowerShell。

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -ConfigurationName

指定用於互動式工作階段的工作階段設定。

輸入工作階段設定的設定名稱或完整資源 URI。 如果您只指定設定名稱，則會在前面加上下列架構 URI： `http://schemas.microsoft.com/powershell` 。

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

URI 的 Transport 區段有效值為 HTTP 與 HTTPS。 如果您指定具有傳輸區段的連線 URI，但未指定埠，則會使用標準埠：80（適用于 HTTP）和443（適用于 HTTPS）來建立會話。 若要使用預設連接埠於 Windows PowerShell 遠端功能，請為 HTTP 指定連接埠 5985，或是為 HTTPS 指定連接埠 5986。

若目的地電腦將連線重新導向至不同 URI，除非您在命令中使用 **AllowRedirection** 參數，否則 Windows PowerShell 會禁止重新導向。

```yaml
Type: System.Uri
Parameter Sets: Uri
Aliases: URI, CU

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ContainerId

指定容器的識別碼。

```yaml
Type: System.String
Parameter Sets: ContainerId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Credential

指定具有執行此動作權限的使用者帳戶。 預設為目前使用者。

輸入使用者名稱（例如 **User01** 或 **Domain01\User01** ），或輸入 Cmdlet 所產生的 **PSCredential** 物件 `Get-Credential` 。 如果您輸入使用者名稱，系統就會提示您輸入密碼。

認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。

> [!NOTE]
> 如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, Uri, VMId, VMName
Aliases:

Required: True (VMId, VMName), False (ComputerName, Uri)
Position: 1
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -EnableNetworkAccess

指出此 Cmdlet 會將互動式安全性權杖新增至回送會話。 互動式權杖可讓您在會從其他電腦取得資料的回送工作階段中執行命令。 例如，您可以在會將 XML 檔案從遠端電腦複製到本機電腦的工作階段中執行命令。

回送會話是在同一部電腦上產生和結束的 **PSSession** 。 若要建立回送會話，請省略 **ComputerName** 參數，或將其值設為。  (點) 、localhost 或本機電腦的名稱。

根據預設，系統會使用網路權杖建立回送會話，這可能不會提供足夠的許可權來驗證遠端電腦。

**EnableNetworkAccess** 參數只在回送工作階段中有效。 如果您在遠端電腦上建立會話時使用 **EnableNetworkAccess** ，則命令會成功，但是會忽略參數。

您也可以允許回送工作階段中的遠端存取，方式是使用 **CredSSP** 參數的 **Authentication** 值，這樣會把工作階段認證委派給其他電腦。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

指定現有工作階段的識別碼。 `Enter-PSSession` 針對互動式會話使用指定的會話。

若要尋找會話的識別碼，請使用 `Get-PSSession` Cmdlet。

```yaml
Type: System.Int32
Parameter Sets: Id
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InstanceId

指定現有工作階段的執行個體識別碼。 `Enter-PSSession` 針對互動式會話使用指定的會話。

執行個體識別碼是 GUID。 若要尋找會話的實例識別碼，請使用 `Get-PSSession` Cmdlet。 您也可以使用 **Session** 、 **Name** 或 **ID** 參數來指定現有的會話。 或者，您可以使用 **ComputerName** 參數來啟動暫時會話。

```yaml
Type: System.Guid
Parameter Sets: InstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

指定現有工作階段的好記名稱。 `Enter-PSSession` 針對互動式會話使用指定的會話。

如果您指定的名稱符合多個工作階段，此命令會失敗。 您也可以使用 **Session** 、 **InstanceID** 或 **ID** 參數來指定現有的會話。 或者，您可以使用 **ComputerName** 參數來啟動暫時會話。

若要建立會話的易記名稱，請使用 Cmdlet 的 **name** 參數 `New-PSSession` 。

```yaml
Type: System.String
Parameter Sets: Name
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Port

指定遠端電腦上用於此命令的網路埠。 若要連線到遠端電腦，遠端電腦必須接聽連線使用的連接埠。 預設的埠是5985，也就是 HTTP 的 WinRM 埠和5986，也就是 HTTPS 的 WinRM 埠。

使用替代連接埠之前，必須先將遠端電腦上的 WinRM 接聽程式設定為在該連接埠進行接聽。 使用下列命令來設定接聽程式：

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

指定用於互動式會話的 Windows PowerShell 會話 ( **PSSession** ) 。 這個參數接受工作階段物件。 您也可以使用 **Name** 、 **InstanceID** 或 **ID** 參數來指定 **PSSession** 。

輸入包含會話物件的變數，或輸入可建立或取得會話物件的命令，例如 `New-PSSession` 或 `Get-PSSession` 命令。 您也可以使用管線將會話物件傳送至 `Enter-PSSession` 。 您只能使用此參數提交一個 **PSSession** 。 如果您輸入的變數包含一個以上的 **PSSession** ，命令會失敗。

當您使用 `Exit-PSSession` 或 **EXIT** 關鍵字時，互動式會話會結束，但您建立的 **PSSession** 會保持開啟且可供使用。

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: Session
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SessionOption

設定工作階段的進階選項。 輸入 **SessionOption** 物件（例如您使用 Cmdlet 建立的物件 `New-PSSessionOption` ），或輸入雜湊表，其中索引鍵為會話選項名稱，而值為會話選項值。

選項的預設值取決於 `$PSSessionOption` 喜好設定變數的值（如果已設定）。 否則，將以工作階段設定中設定的選項建立預設值。

會話選項值的優先順序高於 `$PSSessionOption` 喜好設定變數和會話設定中設定之會話的預設值。 不過，它們的優先順序不會高於工作階段設定中設定的最大值、配額或限制。

如需會話選項的描述（包括預設值），請參閱 `New-PSSessionOption` 。
如需喜好設定變數的詳細資訊 `$PSSessionOption` ，請參閱 [about_Preference_Variables](About/about_Preference_Variables.md)。 如需會話設定的詳細資訊，請參閱 [about_Session_Configurations](About/about_Session_Configurations.md)。

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

### -UseSSL

指出此 Cmdlet 會使用安全通訊端層 (SSL) 通訊協定來建立與遠端電腦的連線。 預設不會使用 SSL。

WS-Management 會加密透過網路傳輸的所有 Windows PowerShell 內容。 **UseSSL** 參數是額外的保護，可跨 HTTPS 連接（而非 HTTP 連線）傳送資料。

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

指定虛擬機器的識別碼。

```yaml
Type: System.Guid
Parameter Sets: VMId
Aliases: VMGuid

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -VMName

指定虛擬機器的名稱。

```yaml
Type: System.String
Parameter Sets: VMName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.string，System.object。 PSSession。

您可以使用管線將電腦名稱稱（字串）或會話物件傳送至此 Cmdlet。

## 輸出

### 無

此 Cmdlet 不會傳回任何輸出。

## 注意

若要連線遠端電腦，您必須是遠端電腦上 Administrators 群組的成員。 若要在本機電腦上啟動互動式會話，您必須使用 [以 **系統管理員身分執行** ] 選項啟動 PowerShell。

當您使用時 `Enter-PSSession` ，遠端電腦上的使用者設定檔會用於互動式會話。 遠端使用者設定檔中的命令，包括用來新增 PowerShell 模組的命令，以及變更命令提示字元的命令，會在顯示遠端提示字元之前執行。

`Enter-PSSession` 針對互動式會話使用本機電腦上的 UI 文化特性設定。 若要尋找本機 UI 文化特性，請使用 `$UICulture` 自動變數。

`Enter-PSSession` 需要 `Get-Command` 、 `Out-Default` 和 `Exit-PSSession` Cmdlet。 如果遠端電腦上的會話設定中未包含這些 Cmdlet，則 `Enter-PSSession` 命令會失敗。

不同于 `Invoke-Command` ，這會在命令傳送到遠端電腦之前剖析並解讀命令， `Enter-PSSession` 而不需要解釋，就會將命令直接傳送至遠端電腦。

如果您想要輸入的會話正忙於處理命令，則 PowerShell 回應命令之前可能會有延遲 `Enter-PSSession` 。 您會在會話可用時立即連線。 若要取消 `Enter-PSSession` 命令，請按下<kbd>CTRL</kbd> + <kbd>C</kbd>。

## 相關連結

[Exit-PSSession](Exit-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Invoke-Command](Invoke-Command.md)

[New-PSSession](New-PSSession.md)

[Remove-PSSession](Remove-PSSession.md)

[Connect-PSSession](Connect-PSSession.md)

[Disconnect-PSSession](Disconnect-PSSession.md)

[Receive-PSSession](Receive-PSSession.md)

[about_PSSessions](About/about_PSSessions.md)

[about_Remote](About/about_Remote.md)
