---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/new-cimsession?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-CimSession
ms.openlocfilehash: 85b7f62686ed5f4aef267041ef624e3d7e388038
ms.sourcegitcommit: 9a53e53e7a3ef9ac0a212c61005efff9e9902452
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "93206091"
---
# New-CimSession

## 概要

建立 CIM 會話。

## SYNTAX

### CredentialParameterSet (預設) 

```
New-CimSession [-Authentication <PasswordAuthenticationMechanism>] [[-Credential] <PSCredential>]
 [[-ComputerName] <String[]>] [-Name <String>] [-OperationTimeoutSec <UInt32>] [-SkipTestConnection]
 [-Port <UInt32>] [-SessionOption <CimSessionOptions>] [<CommonParameters>]
```

### CertificateParameterSet

```
New-CimSession [-CertificateThumbprint <String>] [[-ComputerName] <String[]>] [-Name <String>]
 [-OperationTimeoutSec <UInt32>] [-SkipTestConnection] [-Port <UInt32>]
 [-SessionOption <CimSessionOptions>] [<CommonParameters>]
```

## DESCRIPTION

此 `New-CimSession` Cmdlet 會建立 CIM 會話。 CIM 會話是代表連接到本機電腦或遠端電腦的用戶端物件。 CIM 會話包含連接的相關資訊，例如 **ComputerName** 、使用的通訊協定或不同的識別碼。

此 Cmdlet 會傳回可供所有其他 CIM Cmdlet 使用的 CIM 會話物件。

## 範例

### 範例1：使用預設選項建立 CIM 會話

此範例會使用預設選項建立本機 CIM 會話。 如果未指定 **ComputerName** ，則會在 `New-CimSession` 本機電腦上建立 DCOM 會話。

```powershell
New-CimSession
```

### 範例2：建立特定電腦的 CIM 會話

此範例會建立 **ComputerName** 所指定電腦的 CIM 會話。
依預設， `New-CimSession` 會在指定 **ComputerName** 時建立 WSMan 會話。

```powershell
New-CimSession -ComputerName Server01
```

### 範例3：建立多部電腦的 CIM 會話

此範例會在以逗號分隔的清單中，為 **ComputerName** 指定的每一部電腦建立 CIM 會話。

```powershell
New-CimSession -ComputerName Server01,Server02,Server03
```

### 範例4：建立具有易記名稱的 CIM 會話

此範例會在以逗號分隔的清單中，為 **ComputerName** 指定的每一部電腦建立遠端 CIM 會話，並藉由指定 **名稱** 將易記名稱指派給新的會話。

```powershell
New-CimSession -ComputerName Server01,Server02 -Name FileServers
Get-CimSession -Name File*
```

您可以使用 CIM 會話的易記名稱，參考其他 CIM Cmdlet 中的會話，例如， [CimSession](Get-CimSession.md)。

### 範例5：使用 PSCredential 物件建立電腦的 CIM 會話

此範例會使用 **Credential** 指定的 **PSCredential** 物件，以及 **驗證** 所指定的驗證類型，建立與 **ComputerName** 所指定電腦的 CIM 會話。

```powershell
New-CimSession -ComputerName Server01 -Credential $cred -Authentication Negotiate
```

您可以使用 Cmdlet 來建立 **PSCredential** 物件 [`Get-Credential`](../Microsoft.PowerShell.Security/Get-Credential.md) 。

### 範例6：使用特定埠建立電腦的 CIM 會話

此範例會使用 **埠** 指定的 TCP 通訊埠，建立電腦 **名稱** 所指定之電腦的 CIM 會話。

```powershell
New-CimSession -ComputerName Server01 -Port 1234
```

### 範例7：使用 DCOM 建立 CIM 會話

此範例會使用分散式 COM (DCOM) 通訊協定（而非 WSMan）來建立 CIM 會話。

```powershell
$SessionOption = New-CimSessionOption -Protocol DCOM
New-CimSession -ComputerName Server1 -SessionOption $SessionOption
```

## PARAMETERS

### -Authentication

指定用於使用者認證的驗證類型。 此參數可接受的值為：

- 預設
- Digest
- 交涉
- 基本
- Kerberos
- NtlmDomain
- CredSsp

您無法使用 **NtlmDomain** authentication 類型連接到本機電腦。 **CredSSP** 驗證只有在 windows Vista、windows Server 2008 和更新版本的 windows 中才能使用。

> [!CAUTION]
> 認證安全性服務提供者 (CredSSP) 驗證是針對需要在多個資源上進行驗證的命令所設計，例如存取遠端網路共用。 此機制會使得遠端作業的安全性風險變高。 若遠端電腦遭到入侵，傳遞給它的認證便可用來控制網路工作階段。

```yaml
Type: Microsoft.Management.Infrastructure.Options.PasswordAuthenticationMechanism
Parameter Sets: CredentialParameterSet
Aliases:
Accepted values: Default, Digest, Negotiate, Basic, Kerberos, NtlmDomain, CredSsp

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -CertificateThumbprint

指定具有執行此動作之許可權的使用者帳戶的數位公開金鑰憑證 (x.509) 。 請輸入憑證的憑證指紋。

憑證將用於用戶端憑證式驗證。 這些憑證只能對應至本機使用者帳戶，無法用於網域帳戶。

若要取得憑證指紋，請使用 [`Get-Item`](../Microsoft.Powershell.Management/Get-Item.md) [`Get-ChildItem`](../Microsoft.Powershell.Management/Get-ChildItem.md) PowerShell 憑證提供者中的或 Cmdlet。

如需詳細資訊，請參閱 [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md)。

```yaml
Type: System.String
Parameter Sets: CertificateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ComputerName

指定要建立 CIM 會話的電腦名稱稱。 指定單一電腦名稱稱，或以逗號分隔的多個電腦名稱稱。

如果未指定 **ComputerName** ，則會建立本機電腦的 CIM 會話。 您可以用下列其中一種格式來指定電腦名稱稱的值：

- 一或多個 NetBIOS 名稱
- 一或多個 IP 位址
- 一或多個完整功能變數名稱。

如果電腦與使用者位於不同的網域，您必須指定完整功能變數名稱。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, ServerName

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Credential

指定具有執行此動作權限的使用者帳戶。 如果未指定 **認證** ，則會使用目前的使用者帳戶。

使用下列其中一種格式來指定 **認證** 的值：

- 使用者名稱： "User01"
- 功能變數名稱和使用者名稱： "Domain01\User01"
- 使用者主體名稱： " User@Domain.com "
- PSCredential 物件，例如 Cmdlet 所傳回的物件 [`Get-Credential`](../Microsoft.PowerShell.Security/Get-Credential.md) 。

當您輸入使用者名稱時，會提示您輸入密碼。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: CredentialParameterSet
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

指定 CIM 會話的易記名稱。

使用其他 Cmdlet 時，您可以使用此名稱來參考 CIM 會話，例如 [CimSession](Get-CimSession.md) Cmdlet。
該名稱對電腦或目前工作階段而言不需要是唯一的。

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

### -OperationTimeoutSec

Cmdlet 等候伺服器回應的持續時間。

根據預設，此參數的值為0，表示此 Cmdlet 會使用伺服器的預設超時值。

如果 **OperationTimeoutSec** 參數設定為小於健全連接重試超時時間3分鐘的值，則超過 **OperationTimeoutSec** 參數值的網路失敗就無法復原，因為伺服器上的作業會在用戶端重新連線之前超時。

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases: OT

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Port

指定遠端電腦上要供此連線使用的網路連接埠。 若要連線到遠端電腦，遠端電腦必須接聽連線使用的連接埠。 預設連接埠是 5985 (用於 HTTP 的 WinRM 連接埠) 和 5986 (用於 HTTPS 的 WinRM 連接埠)。

使用替代連接埠之前，必須先將遠端電腦上的 WinRM 接聽程式設定為在該連接埠進行接聽。 使用下列命令來設定接聽程式：

`winrm delete winrm/config/listener?Address=*+Transport=HTTP`

`winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number>"}`

除非必要，否則請勿使用 **Port** 參數。 命令中的連接埠設定會套用到所有電腦或命令執行所在工作階段。 替代的連接埠設定可能使得命令無法在全部電腦上執行。

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SessionOption

設定新 CIM 會話的 advanced 選項。 輸入使用 Cmdlet 建立之 **CimSessionOption** 物件的名稱 [`New-CimSessionOption`](New-CimSessionOption.md) 。

```yaml
Type: Microsoft.Management.Infrastructure.Options.CimSessionOptions
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SkipTestConnection

根據預設，此 `New-CimSession` Cmdlet 會建立與遠端 WS-Management 端點的連線，有兩個原因：驗證遠端伺服器是否正在接聽使用 **port** 參數指定的埠號碼，以及驗證指定的帳號認證。 您可以使用標準 WS-Identity 操作來完成驗證。 如果遠端 WS-Management 端點無法使用 WS 識別，或減少一些資料傳輸時間，您可以新增 **SkipTestConnection** 交換器參數。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 輸入

### 無

此 Cmdlet 不接受任何輸入。

## 輸出

### Microsoft.Management.Infrastructure.CimSession

## 注意

## 相關連結

[Get-ChildItem](../Microsoft.Powershell.Management/Get-ChildItem.md)

[Get-Credential](../Microsoft.PowerShell.Security/Get-Credential.md)

[Get-Item](../Microsoft.Powershell.Management/Get-Item.md)

[Get-CimSession](Get-CimSession.md)

[Remove-CimSession](Remove-CimSession.md)

[New-CimSessionOption](New-CimSessionOption.md)

[about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)
