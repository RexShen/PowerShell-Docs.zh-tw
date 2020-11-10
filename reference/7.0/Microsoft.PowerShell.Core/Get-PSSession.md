---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssession?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSession
ms.openlocfilehash: 5e7fdf1eeee1360777f801ae140d013bf9194977
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388972"
---
# Get-PSSession

## 概要
取得本機和遠端電腦上的 PowerShell 會話。

## SYNTAX

### Name (預設值)

```
Get-PSSession [-Name <String[]>] [<CommonParameters>]
```

### ComputerName

```
Get-PSSession [-ComputerName] <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 [-Name <String[]>] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-ThrottleLimit <Int32>]
 [-State <SessionFilterState>] [-SessionOption <PSSessionOption>] [<CommonParameters>]
```

### ComputerInstanceId

```
Get-PSSession [-ComputerName] <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 -InstanceId <Guid[]> [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-ThrottleLimit <Int32>]
 [-State <SessionFilterState>] [-SessionOption <PSSessionOption>] [<CommonParameters>]
```

### ConnectionUri

```
Get-PSSession [-ConnectionUri] <Uri[]> [-ConfigurationName <String>] [-AllowRedirection] [-Name <String[]>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-ThrottleLimit <Int32>] [-State <SessionFilterState>] [-SessionOption <PSSessionOption>] [<CommonParameters>]
```

### ConnectionUriInstanceId

```
Get-PSSession [-ConnectionUri] <Uri[]> [-ConfigurationName <String>] [-AllowRedirection] -InstanceId <Guid[]>
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-ThrottleLimit <Int32>] [-State <SessionFilterState>] [-SessionOption <PSSessionOption>] [<CommonParameters>]
```

### VMNameInstanceId

```
Get-PSSession [-ConfigurationName <String>] -InstanceId <Guid[]> [-State <SessionFilterState>]
 -VMName <String[]> [<CommonParameters>]
```

### ContainerId

```
Get-PSSession [-ConfigurationName <String>] [-Name <String[]>] [-State <SessionFilterState>]
 -ContainerId <String[]> [<CommonParameters>]
```

### ContainerIdInstanceId

```
Get-PSSession [-ConfigurationName <String>] -InstanceId <Guid[]> [-State <SessionFilterState>]
 -ContainerId <String[]> [<CommonParameters>]
```

### VMId

```
Get-PSSession [-ConfigurationName <String>] [-Name <String[]>] [-State <SessionFilterState>] -VMId <Guid[]>
 [<CommonParameters>]
```

### VMIdInstanceId

```
Get-PSSession [-ConfigurationName <String>] -InstanceId <Guid[]> [-State <SessionFilterState>] -VMId <Guid[]>
 [<CommonParameters>]
```

### VMName

```
Get-PSSession [-ConfigurationName <String>] [-Name <String[]>] [-State <SessionFilterState>] -VMName <String[]>
 [<CommonParameters>]
```

### InstanceId

```
Get-PSSession [-InstanceId <Guid[]>] [<CommonParameters>]
```

### Id

```
Get-PSSession [-Id] <Int32[]> [<CommonParameters>]
```

## DESCRIPTION

Cmdlet 會在 `Get-PSSession` 本機和遠端電腦上 ( **pssession** ) 取得使用者管理的 PowerShell 會話。

從 Windows PowerShell 3.0 開始，會話會儲存在每個連線遠端端的電腦上。 您可以使用的 **ComputerName** 或 **ConnectionUri** 參數 `Get-PSSession` 取得連接到本機電腦或遠端電腦的會話，即使它們不是在目前的會話中建立也一樣。

如果沒有參數，會 `Get-PSSession` 取得在目前會話中建立的所有會話。

使用篩選參數，包括 **Name** 、 **ID** 、 **InstanceID** 、 **State** 、 **ApplicationName** 和 **ConfigurationName** ，以便從傳回的會話中進行選取 `Get-PSSession` 。

`Get-PSSession`當您使用 **ComputerName** 或 **ConnectionUri** 參數時，請使用其餘的參數來設定執行命令的暫存連接。

注意：在 Windows PowerShell 2.0 中，如果沒有參數， `Get-PSSession` 則會取得在目前會話中建立的所有會話。 **ComputerName** 參數會取得在目前會話中建立的會話，並連接到指定的電腦。

如需 PowerShell 會話的詳細資訊，請參閱 [about_PSSessions](about/about_PSSessions.md)。

## 範例

### 範例1：取得在目前會話中建立的會話

```powershell
Get-PSSession
```

此命令會取得在目前會話中建立的所有 **pssession** 。 它不會取得在其他會話或其他電腦上建立的 **pssession** ，即使它們已連線到這部電腦。

### 範例2：取得連接到本機電腦的會話

```powershell
Get-PSSession -ComputerName "localhost"
```

此命令會取得連接到本機電腦的 **pssession** 。 若要指示本機電腦，請輸入電腦名稱稱、localhost 或點 (。 ) 

此命令傳回本機電腦上的所有工作階段，即使它們是在不同的工作階段中或不同的電腦上所建立。

### 範例3：取得連接到電腦的會話

```powershell
Get-PSSession -ComputerName "Server02"
```

```Output
 Id Name            ComputerName    State         ConfigurationName     Availability
 -- ----            ------------    -----         -----------------     ------------
  2 Session3        Server02       Disconnected  ITTasks                       Busy
  1 ScheduledJobs   Server02       Opened        Microsoft.PowerShell     Available
  3 Test            Server02       Disconnected  Microsoft.PowerShell          Busy
```

此命令取得連線到 Server02 電腦的 **pssession** 。

此命令傳回 Server02 上的所有工作階段，即使它們是在不同的工作階段中或不同的電腦上所建立。

輸出顯示有兩個工作階段的狀態為 Disconnected，且可用性為 Busy。 它們是在不同的工作階段中所建立，並且目前都正在使用中。 ScheduledJobs 會話是在目前的會話中建立的，且已開啟且可用。

### 範例4：儲存此命令的結果

```powershell
New-PSSession -ComputerName Server01, Server02, Server03
$s1, $s2, $s3 = Get-PSSession
```

此範例顯示如何將命令的結果儲存 `Get-PSSession` 在多個變數中。

第一個命令會使用 `New-PSSession` Cmdlet，在三部遠端電腦上建立 **pssession** 。

第二個命令會使用 `Get-PSSession` Cmdlet 來取得三個 **pssession** 。 然後，它會將每個 **pssession** 儲存在個別的變數中。

當 PowerShell 將物件陣列指派給變數陣列時，它會將第一個物件指派給第一個變數，將第二個物件指派給第二個變數，依此類推。 如果物件數目多於變數數目，它會將所有剩餘的物件指派給陣列中的最後一個變數。 如果變數數目多於物件數目，便不使用多餘的變數。

### 範例5：使用實例識別碼刪除會話

```powershell
Get-PSSession | Format-Table -Property ComputerName, InstanceID
$s = Get-PSSession -InstanceID a786be29-a6bb-40da-80fb-782c67f7db0f
Remove-PSSession -Session $s
```

這個範例示範如何使用其實例 ID 取得 **pssession** ，然後再刪除 **pssession** 。

第一個命令會取得在目前會話中建立的所有 **pssession** 。 它會將 **pssession** 傳送至 Format-Table Cmdlet，此 Cmdlet 會顯示每個 **PSSession** 的 **ComputerName** 和 **InstanceID** 屬性。

第二個命令 `Get-PSSession` 會使用 Cmdlet 來取得特定的 **PSSession** ，並將它儲存在 `$s` 變數中。 此命令會使用 **InstanceID** 參數來識別 **PSSession** 。

第三個命令使用 Remove-PSSession Cmdlet 來刪除變數 **PSSession** 中的 PSSession `$s` 。

### 範例6：取得具有特定名稱的會話

此範例中的命令會尋找具有特定名稱格式且使用特定工作階段設定的工作階段，然後連線到該工作階段。 您可以使用與此類似的命令來尋找同事在其中啟動工作的工作階段，然後進行連線來完成工作。

```powershell
Get-PSSession -ComputerName Server02, Server12 -Name BackupJob* -ConfigurationName ITTasks -SessionOption @{OperationTimeout=240000}
```

```Output
 Id Name            ComputerName    State         ConfigurationName     Availability
 -- ----            ------------    -----         -----------------     ------------
  3 BackupJob04     Server02        Disconnected        ITTasks                  None
```

```powershell
$s = Get-PSSession -ComputerName Server02 -Name BackupJob04 -ConfigurationName ITTasks | Connect-PSSession
$s
```

```Output
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 5 BackupJob04     Server02        Opened        ITTasks                  Available
```

第一個命令會取得 Server02 和 Server12 遠端電腦上名稱開頭為 BackupJob 並使用 ITTasks 會話設定的會話。此命令會使用 **name** 參數來指定名稱模式，並使用 **ConfigurationName** 參數來指定會話設定。 **SessionOption** 參數的值是一個雜湊表，它會將 **OperationTimeout** 的值設定為 240000 毫秒 (4 分鐘)。 此設定可讓命令更多時間完成。 **ConfigurationName** 和 **SessionOption** 參數是用來設定在每部 `Get-PSSession` 電腦上執行 Cmdlet 的臨時會話。輸出會顯示命令傳回 BackupJob04 會話。 會話已中斷連線，而且 **可用性** 為 None，表示它不在使用中。

第二個命令會使用 `Get-PSSession` Cmdlet 來取得 BackupJob04 會話，並使用 Connect-PSSession Cmdlet 來連接會話。 命令會將工作階段儲存於 $s 變數中。

第三個命令取得 $s 變數中的工作階段。 輸出顯示 `Connect-PSSession` 命令成功。 工作階段的狀態為 **Opened** 並且可供使用。

### 範例7：使用識別碼來取得會話

```powershell
Get-PSSession -Id 2
```

此命令會取得識別碼為2的 **PSSession** 。 由於 **id** 屬性的值只有在目前的會話中是唯一的，因此 **id** 參數僅對本機命令有效。

## PARAMETERS

### -AllowRedirection

指出此 Cmdlet 允許將此連線重新導向至替代的統一資源識別項 (URI) 。 根據預設，PowerShell 不會重新導向連接。

此參數會設定 `Get-PSSession` 使用 **ConnectionUri** 參數來執行命令所建立的暫時連接。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ConnectionUriInstanceId, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -ApplicationName

指定應用程式的名稱。 此 Cmdlet 只會連接到使用指定應用程式的會話。

輸入連線 URI 的應用程式名稱區段。 例如，在下列連接 URI 中，應用程式名稱為 WSMan： `http://localhost:5985/WSMAN` 。 工作階段的應用程式名稱儲存在工作階段的 **Runspace.ConnectionInfo.AppName** 屬性中。

此參數的值可用來選取與篩選工作階段。 它不會變更工作階段使用的應用程式。

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerName
Aliases:

Required: False
Position: Named
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Authentication

指定用來驗證命令執行所在之會話認證的機制 `Get-PSSession` 。

此參數會設定建立的暫存連接，以 `Get-PSSession` 使用 **ComputerName** 或 **ConnectionUri** 參數來執行命令。

此參數可接受的值為：

- 預設
- 基本
- Credssp
- Digest
- Kerberos
- 交涉
- NegotiateWithImplicitCredential.

預設值為 Default。

如需此參數值的詳細資訊，請參閱 [AuthenticationMechanism 列舉](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。

注意：使用者認證會傳遞至要驗證之遠端電腦的「認證安全性支援提供者 (CredSSP)」驗證，是設計用於需要在一個以上資源進行驗證的命令，例如存取遠端網路共用。 此機制會使得遠端作業的安全性風險變高。 若遠端電腦遭到入侵，傳遞給它的認證便可用來控制網路工作階段。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -CertificateThumbprint

指定使用者帳戶的數位公開金鑰憑證 (X509) ，該帳戶有權建立 `Get-PSSession` 執行命令的會話。 請輸入憑證的憑證指紋。

此參數會設定建立的暫存連接，以 `Get-PSSession` 使用 **ComputerName** 或 **ConnectionUri** 參數來執行命令。

憑證將用於用戶端憑證式驗證。 這些憑證只能對應至本機使用者帳戶，無法用於網域帳戶。

若要取得憑證指紋，請使用 PowerShell Cert：磁片磁碟機中的 Get-Item 或 Get-ChildItem 命令。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

指定電腦名稱的陣列。 取得連線到指定之電腦的工作階段。
不允許使用萬用字元。 沒有任何預設值。

從 Windows PowerShell 3.0 開始， **PSSession** 物件會儲存在每個連接遠端的電腦上。 為了取得指定電腦上的會話，PowerShell 會建立每台電腦的暫時連線，然後執行 `Get-PSSession` 命令。

輸入一或多部電腦的 NetBIOS 名稱、IP 位址或完整網域名稱。 若要指定本機電腦，請輸入電腦名稱、localhost 或句點 (.)。

注意：此參數只會從執行 Windows PowerShell 3.0 或更新版本之 PowerShell 的電腦取得會話。 舊版不會儲存工作階段。

```yaml
Type: System.String[]
Parameter Sets: ComputerInstanceId, ComputerName
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ConfigurationName

指定設定的名稱。 此 Cmdlet 只會取得使用指定會話設定的會話。

輸入工作階段設定的設定名稱或完整資源 URI。 如果您只指定設定名稱，則會在前面加上下列架構 URI： `http://schemas.microsoft.com/powershell` 。 工作階段的設定名稱儲存在工作階段的 **ConfigurationName** 屬性中。

此參數的值可用來選取與篩選工作階段。 它不會變更工作階段使用的工作階段設定。

如需會話設定的詳細資訊，請參閱 [about_Session_Configurations](About/about_Session_Configurations.md)。

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri, VMNameInstanceId, ContainerId, ContainerIdInstanceId, VMId, VMIdInstanceId, VMName
Aliases:

Required: False
Position: Named
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ConnectionUri

指定 URI，以定義執行命令之暫存會話的連接端點 `Get-PSSession` 。 此 URI 必須是完整的 URI。

此參數會設定 `Get-PSSession` 使用 **ConnectionUri** 參數來執行命令所建立的暫時連接。

此字串的格式為：

`<Transport>://<ComputerName>:<Port\>/<ApplicationName>`

預設值為： `http://localhost:5985/WSMAN` 。

如果您未指定 **ConnectionUri** ，您可以使用 **UseSSL** 、 **ComputerName** 、 **Port** 及 **ApplicationName** 參數來指定 **ConnectionUri** 值。 URI 的 Transport 區段有效值為 HTTP 與 HTTPS。 若指定含傳輸區段的連線 URI，但未指定連接埠，將會以標準連接埠 80 (適用於 HTTP) 和 443 (適用於 HTTPS) 建立工作階段。 若要使用 PowerShell 遠端的預設埠，請指定 HTTP 的埠5985或 HTTPS 的5986。

如果目的地電腦將連線重新導向至不同的 URI，除非您在命令中使用 **AllowRedirection** 參數，否則 PowerShell 會禁止重新導向。

此參數是在 Windows PowerShell 3.0 引進。

此參數只會從執行 Windows PowerShell Windows PowerShell 3.0 或更新版本的電腦取得會話。 舊版不會儲存工作階段。

```yaml
Type: System.Uri[]
Parameter Sets: ConnectionUriInstanceId, ConnectionUri
Aliases: URI, CU

Required: True
Position: 0
Default value: Http://localhost:5985/WSMAN
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ContainerId

指定容器的識別碼陣列。 此 Cmdlet 會啟動每個指定容器的互動式會話。 使用 `docker ps` 命令來取得容器識別碼的清單。 如需詳細資訊，請參閱 [docker ps](https://docs.docker.com/engine/reference/commandline/ps/) 命令的說明。

```yaml
Type: System.String[]
Parameter Sets: ContainerId, ContainerIdInstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Credential

指定使用者認證。 此 Cmdlet 會以指定使用者的許可權執行命令。 指定具有連線到遠端電腦之許可權的使用者帳戶，然後執行 `Get-PSSession` 命令。 預設為目前使用者。

輸入使用者名稱（例如 **User01** 或 **Domain01\User01** ），或輸入 Cmdlet 所產生的 **PSCredential** 物件 `Get-Credential` 。 如果您輸入使用者名稱，系統就會提示您輸入密碼。

認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。

> [!NOTE]
> 如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。

此參數會設定為 `Get-PSSession` 使用 **ComputerName** 或 **ConnectionUri** 參數來執行命令所建立的暫時連接。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

指定會話識別碼的陣列。 此 Cmdlet 只會取得具有指定識別碼的會話。 輸入一或多個識別碼 (以逗號分隔)，或使用範圍運算子 (..) 來指定某個範圍的識別碼。 您不能使用 ID 參數搭配 **ComputerName** 參數。

識別碼是一個整數，可唯一識別目前會話中的使用者管理會話。 它比較容易記住並輸入 **InstanceId** ，但是它只有在目前的會話內是唯一的。 工作階段的識別碼儲存在工作階段的 ID 屬性中。

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InstanceId

指定會話的實例識別碼陣列。 此 Cmdlet 只會取得具有指定實例識別碼的會話。

執行個體識別碼是 GUID，可唯一識別本機或遠端電腦上的某個階段作業。 **InstanceID** 是唯一的，即使您有多個會話在 PowerShell 中執行也是一樣。

工作階段的執行個體識別碼儲存在工作階段的 **InstanceID** 屬性中。

```yaml
Type: System.Guid[]
Parameter Sets: ComputerInstanceId, ConnectionUriInstanceId, VMNameInstanceId, ContainerIdInstanceId, VMIdInstanceId
Aliases:

Required: True (ComputerInstanceId, ConnectionUriInstanceId, ContainerIdInstanceId, VMIdInstanceId, VMNameInstanceId), False (InstanceId)
Position: Named
Default value: All sessions
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

指定會話名稱的陣列。 此 Cmdlet 只會取得具有指定易記名稱的會話。 允許使用萬用字元。

工作階段的好記名稱儲存在工作階段的 **Name** 屬性中。

```yaml
Type: System.String[]
Parameter Sets: Name, ComputerName, ConnectionUri, ContainerId, VMId, VMName
Aliases:

Required: False
Position: Named
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Port

指定用於執行命令的暫存連接所指定的網路埠 `Get-PSSession` 。 若要連線到遠端電腦，遠端電腦必須接聽連線使用的連接埠。 預設的埠是5985，也就是 HTTP 的 WinRM 埠和5986，也就是 HTTPS 的 WinRM 埠。

使用替代連接埠之前，必須先將遠端電腦上的 WinRM 接聽程式設定為在該連接埠進行接聽。 若要設定接聽程式，請在 PowerShell 提示字元中輸入下列兩個命令：

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

此參數會設定為 `Get-PSSession` 使用 **ComputerName** 或 **ConnectionUri** 參數來執行命令所建立的暫時連接。

除非必要，否則請勿使用 **Port** 參數。 命令中設定的 **埠** 會套用到命令執行所在的所有電腦或會話。 替代的連接埠設定可能使得命令無法在全部電腦上執行。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Int32
Parameter Sets: ComputerInstanceId, ComputerName
Aliases:

Required: False
Position: Named
Default value: 5985, 5986
Accept pipeline input: False
Accept wildcard characters: False
```

### -SessionOption

指定會話的 advanced 選項。 輸入 **SessionOption** 物件 (例如您使用 New-PSSessionOption Cmdlet 建立的物件) 或者雜湊表，其中索引鍵為工作階段選項名稱，而值為工作階段選項值。

選項的預設值是由 $PSSessionOption 喜好設定變數的值所決定 (若設定了該變數)。 否則，將以工作階段設定中設定的選項建立預設值。

工作階段選項值優先順序高於 $PSSessionOption 喜好設定變數與工作階段設定中設定的工作階段預設值。 不過，它們的優先順序不會高於工作階段設定中設定的最大值、配額或限制。

如需會話選項的描述（包括預設值），請參閱 `New-PSSessionOption` 。
如需喜好設定變數的詳細資訊 `$PSSessionOption` ，請參閱 [about_Preference_Variables](About/about_Preference_Variables.md)。 如需會話設定的詳細資訊，請參閱 [about_Session_Configurations](About/about_Session_Configurations.md)。

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -State

指定會話狀態。 此 Cmdlet 只會取得處於指定狀態的會話。 此參數可接受的值包括：全部、已開啟、已中斷連線、已關閉和已中斷。 預設值為 All。

工作階段狀態值是相對於目前的工作階段。 不是在目前的工作階段中建立，也未連線到目前之工作階段的工作階段，即使它們已連線到不同的工作階段，其狀態也會是 Disconnected。

工作階段的狀態儲存在工作階段的 **State** 屬性中。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: Microsoft.PowerShell.Commands.SessionFilterState
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri, VMNameInstanceId, ContainerId, ContainerIdInstanceId, VMId, VMIdInstanceId, VMName
Aliases:
Accepted values: All, Opened, Disconnected, Closed, Broken

Required: False
Position: Named
Default value: All
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

指定可建立以執行命令的並行連接數目上限 `Get-PSSession` 。 若省略此參數，或輸入值為 0 (零)，則會使用預設值 32。 節流限制僅適用於目前命令，不適用於工作階段或電腦。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Int32
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSSL

指出此 Cmdlet 會使用安全通訊端層 (SSL) 通訊協定來建立命令執行所在的連接 `Get-PSSession` 。 預設不會使用 SSL。 若您使用此參數，但是命令所用的連接埠上無法使用 SSL，則命令會失敗。

此參數會設定建立的暫存連接，以 `Get-PSSession` 使用 **ComputerName** 參數執行命令。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerInstanceId, ComputerName
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -VMId

指定虛擬機器的識別碼陣列。 此 Cmdlet 會在每個指定的虛擬機器之間啟動互動式會話。 若要查看可供您使用的虛擬機器，請使用下列命令：

`Get-VM | Select-Object -Property Name, ID`

```yaml
Type: System.Guid[]
Parameter Sets: VMId, VMIdInstanceId
Aliases: VMGuid

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -VMName

指定虛擬機器名稱的陣列。 此 Cmdlet 會在每個指定的虛擬機器之間啟動互動式會話。 若要查看可供您使用的虛擬機器，請使用 `Get-VM` Cmdlet。

```yaml
Type: System.String[]
Parameter Sets: VMNameInstanceId, VMName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無

您無法使用管線傳送輸入至此 Cmdlet。

## 輸出

### System.Management.Automation.Runspaces.PSSession

## 注意

- 此 Cmdlet 會取得使用者管理的會話 **PSSession** 物件，例如使用新的-PSSession、 `Enter-PSSession` 和 Invoke-Command Cmdlet 所建立的物件。 它不會取得當您啟動 PowerShell 時所建立的系統管理會話。
- 從 Windows PowerShell 3.0 開始， **PSSession** 物件會儲存在位於伺服器端或接收端連接端的電腦上。 為了取得儲存在本機電腦或遠端電腦上的會話，PowerShell 會為指定的電腦建立暫時的會話，並在會話中執行查詢命令。
- 若要取得連線到遠端電腦的工作階段，請使用 **ComputerName** 或 **ConnectionUri** 參數來指定遠端電腦。 若要篩選取得的會話 `Get-PSSession` ，請使用 **Name** 、 **ID** 、 **InstanceID** 和 **State** 參數。 使用其餘的參數來設定使用的暫時會話 `Get-PSSession` 。
- 當您使用 **ComputerName** 或 **ConnectionUri** 參數時， `Get-PSSession` 只會從執行 Windows PowerShell 3.0 和更新版本 PowerShell 的電腦取得會話。
- **PSSession** 的 **State** 屬性值是相對於目前的會話。
  因此，[已 **中斷** 連線] 值表示 **PSSession** 未連接到目前的會話。 但是，它並不表示 **PSSession** 與所有會話中斷連接。 它可能連線不同的工作階段。 若要判斷您是否可以從目前的會話連線或重新連線到 **PSSession** ，請使用 **Availability** 屬性。

**Availability** 值為 **None** 表示您可以連線工作階段。 「 **忙碌** 」值表示您無法連接到 **PSSession** ，因為它已連接到另一個會話。

如需會話的 **State** 屬性值的詳細資訊，請參閱 [ runspacestate 列舉](/dotnet/api/system.management.automation.runspaces.runspacestate)。

如需會話的 **Availability** 屬性值的詳細資訊，請參閱 [RunspaceAvailability 列舉](/dotnet/api/system.management.automation.runspaces.runspaceavailability)。

## 相關連結

[Connect-PSSession](Connect-PSSession.md)

[Disconnect-PSSession](Disconnect-PSSession.md)

[Receive-PSSession](Receive-PSSession.md)

[Enter-PSSession](Enter-PSSession.md)

[Exit-PSSession](Exit-PSSession.md)

[Invoke-Command](Invoke-Command.md)

[New-PSSession](New-PSSession.md)

[Remove-PSSession](Remove-PSSession.md)

[about_PSSessions](About/about_PSSessions.md)

[about_Remote](About/about_Remote.md)
