---
external help file: Microsoft.Powershell.Workflow.ServiceCore.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSWorkflow
ms.date: 07/10/2019
online version: https://docs.microsoft.com/powershell/module/psworkflow/new-psworkflowsession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSWorkflowSession
ms.openlocfilehash: 995dd8a6df3ac8ebd7a204d2aefef3fa6aa71e14
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202968"
---
# New-PSWorkflowSession

## 概要
建立工作流程工作階段。

## SYNTAX

```
New-PSWorkflowSession [[-ComputerName] <String[]>] [-Credential <Object>] [-Name <String[]>] [-Port <Int32>]
 [-UseSSL] [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [-EnableNetworkAccess]
 [<CommonParameters>]
```

## DESCRIPTION

此 `New-PSWorkflowSession` Cmdlet 會建立使用者管理的會話 ( **PSSession** ) ，特別針對執行 Windows PowerShell 工作流程而設計。 它使用 Microsoft.PowerShell.Workflow 工作階段設定，其中包含指令碼、型別與格式設定檔案，以及工作流程所需的選項。

您可以使用 `New-PSWorkflowSession` 或其別名 `nwsn` 。

您也可以新增工作流程一般參數到此命令。 如需工作流程一般參數的詳細資訊，請參閱 [about_WorkflowCommonParameters](./about/about_WorkflowCommonParameters.md)

此 Cmdlet 是在 Windows PowerShell 3.0 中引進。

## 範例

### 範例1：在遠端電腦上建立工作流程會話

此範例會在 ServerNode01 遠端電腦上建立 **WorkflowTests** 會話。

```powershell
$params = @{
    ComputerName = "ServerNode01"
    Name = "WorkflowTests"
    SessionOption = (New-PSSessionOption -OutputBufferingMode Drop)
}
New-PSWorkflowSession @params
```

**SessionOption** 參數的值是一個 `New-PSSessionOption` 命令，此命令會將會話中的輸出緩衝處理模式設定為 **Drop** 。

### 範例2：在多部遠端電腦上建立工作流程會話

此範例會在 ServerNode01 和 Server12 電腦上建立工作流程會話。 此命令會使用 **Credential** 參數，以網域系統管理員的權限執行。

```powershell
"ServerNode01", "Server12" |
    New-PSWorkflowSession -Name WorkflowSession -Credential Domain01\Admin01 -ThrottleLimit 150
```

此命令會使用 **ThrottleLimit** 參數，將每個命令的節流限制增加到 150。
此值的優先順序高於在 [] 中設定的預設節流限制（100 **）。**

## PARAMETERS

### -ApplicationName

指定連線 URI 的應用程式名稱區段。

預設值是 `$PSSessionApplicationName` 本機電腦上喜好設定變數的值。 若未定義此喜好設定變數，則預設值是 WSMAN。 這個值適用於大部分用途。 如需詳細資訊，請參閱 [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)。

WinRM 服務會使用應用程式名稱來選取要用來為連線要求提供服務的接聽程式。
此參數的值應該符合遠端電腦上接聽程式之 **URLPrefix** 屬性的值。

```yaml
Type: System.String
Parameter Sets: (All)
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

CredSSP 驗證僅適用于 Windows Vista、Windows Server 2008 和更新版本的 Windows 作業系統。

如需此參數值的詳細資訊，請參閱 [AuthenticationMechanism 列舉](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。

> [!CAUTION]
> 認證安全性服務提供者 (CredSSP) 驗證，其中使用者認證會傳遞至要驗證的遠端電腦，其設計是針對需要在多個資源上進行驗證的命令，例如存取遠端網路共用。 此機制會使得遠端作業的安全性風險變高。 若遠端電腦遭到入侵，傳遞給它的認證便可用來控制網路工作階段。

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -CertificateThumbprint

對於具有執行此動作之權限的使用者帳戶，指定其數位公開金鑰憑證 (X509)。 請輸入憑證的憑證指紋。

憑證將用於用戶端憑證式驗證。 這些憑證只能對應至本機使用者帳戶，無法用於網域帳戶。

若要取得憑證指紋，請使用 `Get-Item` Cmdlet 或 `Get-ChildItem` Windows PowerShell Cert：磁片磁碟機中的 Cmdlet。

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

建立 ( **PSSession** ) 至指定電腦的持續連線。 如果您輸入多個電腦名稱稱，Windows PowerShell 會建立多個 **pssession** ，每一部電腦各一個。 預設是本機電腦。

輸入一或多部遠端電腦的 NetBIOS 名稱、IP 位址或完整網域名稱。 若要指定本機電腦，請輸入電腦名稱、localhost 或句點 (.)。 當電腦與使用者位於不同網域，則必須使用完整網域名稱。 您也可以使用管線將電腦名稱稱（以引號括住）傳送至 `New-PSWorkflowSession` 。

若要在 **ComputerName** 參數的值中使用 IP 位址，命令必須包含 **Credential** 參數。 此外，必須將電腦設定為使用 HTTPS 傳輸，或必須在本機電腦的 WinRM TrustedHosts 清單中包含遠端電腦的 IP 位址。 如需將電腦名稱稱新增到 TrustedHosts 清單的指示，請參閱 [about_Remote_Troubleshooting](../Microsoft.PowerShell.Core/About/about_Remote_Troubleshooting.md)中的「如何將電腦新增到信任的主機清單」。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: 0
Default value: Local computer
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Credential

指定具有執行此動作權限的使用者帳戶。 預設為目前使用者。 輸入使用者名稱，例如 User01、Domain01\User01 或 User@Domain.com ，或輸入 **PSCredential** 物件，例如 Cmdlet 所傳回的物件 `Get-Credential` 。

當您輸入使用者名稱時，此 Cmdlet 會提示您輸入密碼。

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -EnableNetworkAccess

指出此 Cmdlet 會將互動式安全性權杖新增至回送會話。 互動式權杖可讓您在會從其他電腦取得資料的回送工作階段中執行命令。 例如，您可以在會將 XML 檔案從遠端電腦複製到本機電腦的工作階段中執行命令。

回送會話是在同一部電腦上產生和結束的 **PSSession** 。 若要建立回送會話，請不要指定 **ComputerName** 參數，或將其值設為點、localhost 或本機電腦的名稱。

根據預設，會建立具有網路權杖的回送會話，這可能不會提供足夠的許可權來驗證遠端電腦。

**EnableNetworkAccess** 參數只在回送工作階段中有效。 如果您在遠端電腦上建立會話時指定 **EnableNetworkAccess** 參數，則命令會成功，但是會忽略參數。

您也可以允許回送工作階段中的遠端存取，方式是使用 **CredSSP** 參數的 **Authentication** 值，這樣會把工作階段認證委派給其他電腦。

為了保護電腦免于惡意存取，具有互動式權杖的已中斷連線回送會話（使用 **EnableNetworkAccess** 參數所建立的權杖）只能從建立該會話的電腦重新連接。 使用 CredSSP 驗證且已中斷連線的工作階段可從其他電腦重新連線。 如需詳細資訊，請參閱 `Disconnect-PSSession` Cmdlet。

此參數是在 Windows PowerShell 3.0 引進。

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

### -Name

指定工作流程工作階段的易記名稱。 您可以使用名稱搭配其他 Cmdlet，例如 `Get-PSSession` 和 `Enter-PSSession` 。 該名稱對電腦或目前工作階段而言不需要是唯一的。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Session#
Accept pipeline input: False
Accept wildcard characters: False
```

### -Port

指定遠端電腦上要供此連線使用的網路連接埠。 若要連線到遠端電腦，遠端電腦必須接聽連線使用的連接埠。 預設通訊埠為 5985 (WinRM 埠（適用于 HTTP）) 和 5986 (適用于 HTTPS) 的 WinRM 埠。

使用其他埠之前，您必須先將遠端電腦上的 WinRM 接聽程式設定為在該埠上接聽。 使用下列命令來設定接聽程式：

`winrm delete winrm/config/listener?Address=*+Transport=HTTP`

`winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number\>"}`

除非必要，否則請勿使用 **Port** 參數。 命令中的連接埠設定會套用到所有電腦或命令執行所在工作階段。 替代的連接埠設定可能使得命令無法在全部電腦上執行。

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

指定會話的 advanced 選項。 輸入 **SessionOption** 物件，例如使用 Cmdlet 建立的物件 `New-PSSessionOption` 。

選項的預設值取決於 `$PSSessionOption` 喜好設定變數的值（如果已設定）。 否則，將以工作階段設定中設定的選項建立預設值。

會話選項值的優先順序高於 `$PSSessionOption` 喜好設定變數和會話設定中設定之會話的預設值。 不過，它們的優先順序不會高於工作階段設定中設定的最大值、配額或限制。 如需會話設定的詳細資訊，請參閱 [about_Session_Configurations](../Microsoft.PowerShell.Core/About/about_Session_Configurations.md)。

如需會話選項的描述（包括預設值），請參閱 `New-PSSessionOption` 。
如需喜好設定變數的詳細資訊 `$PSSessionOption` ，請參閱 [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)。

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

指定為執行此命令可建立的最大同時連線數。
如果您省略此參數，或輸入 0 (零) 的值，則會使用 **microsoft.powershellworkflow** 會話設定的預設值100。

節流限制僅適用於目前命令，不適用於工作階段或電腦。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSSL

指出此 Cmdlet 會使用安全通訊端層 (SSL) 通訊協定來建立與遠端電腦的連線。 預設不會使用 SSL。

WS-Management 會加密透過網路傳輸的所有 Windows PowerShell 內容。 **UseSSL** 參數是額外的保護，可跨 HTTPS 連接（而非 HTTP 連線）傳送資料。

如果您指定此參數，但命令所用的埠上沒有 SSL，則命令會失敗。

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

### System.servicemodel. PSSession []，System.string。

您可以使用管線將會話或電腦名稱稱傳送至此 Cmdlet。

## 輸出

### System.Management.Automation.Runspaces.PSSession

## 注意

`New-PSWorkflowSession`命令相當於下列命令：

`New-PSSession -ConfigurationName Microsoft.PowerShell.Workflow`

## 相關連結

[Disconnect-PSSession](../Microsoft.PowerShell.Core/Disconnect-PSSession.md)

[New-PSSession](../Microsoft.PowerShell.Core/New-PSSession.md)

[New-PSTransportOption](../Microsoft.PowerShell.Core/New-PSTransportOption.md)

[Register-PSSessionConfiguration](../Microsoft.PowerShell.Core/Register-PSSessionConfiguration.md)

[about_PSSessions](../Microsoft.PowerShell.Core/About/about_PSSessions.md)

[about_Session_Configurations](../Microsoft.PowerShell.Core/About/about_Session_Configurations.md)

[about_Workflows](../PSWorkflow/About/about_Workflows.md)

[about_WorkflowCommonParameters](About/about_WorkflowCommonParameters.md)
