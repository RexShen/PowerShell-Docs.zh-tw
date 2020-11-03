---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 08/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/enable-wsmancredssp?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-WSManCredSSP
ms.openlocfilehash: 3dd2aa9c1f35de80d86dde508aaa9a3c964dff05
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208688"
---
# Enable-WSManCredSSP

## 概要
在電腦上啟用 (CredSSP) 驗證的認證安全性支援提供者。

## SYNTAX

### 全部

```
Enable-WSManCredSSP [[-DelegateComputer] <String[]>] [-Force] [-Role] <String> [<CommonParameters>]
```

## DESCRIPTION

此 `Enable-WSManCredSSP` Cmdlet 會在用戶端或伺服器電腦上啟用 CredSSP 驗證。
使用 CredSSP 驗證時，會將使用者認證傳遞到遠端電腦進行驗證。 此類型的驗證是針對會從另一個遠端工作階段建立遠端工作階段的命令所設計。 例如，若您想在遠端電腦上執行背景工作，請使用此類型的驗證。

`Enable-WSManCredSSP` 可以在 **用戶端** 或 **伺服器** 上啟用 CredSSP。 若要在用戶端上啟用 CredSSP，請在 **Role** 參數中指定 **client** 。 用戶端會在伺服器驗證完成時，將明確的認證委派給伺服器。 若要在伺服器上啟用 CredSSP，請在 **Role** 參數中指定 **server** 。 伺服器作為用戶端的委派。 如需詳細資訊，請參閱參數一節中的 **角色** 。

> [!CAUTION]
> CredSSP 驗證會將使用者認證從本機電腦委派給遠端電腦。 此做法會使得遠端作業的安全性風險變高。 若遠端電腦遭到入侵，當認證被傳遞給它時，該認證便可用來控制網路工作階段。

## 範例

### 範例 1︰委派用戶端認證

此範例可讓您使用完整功能變數名稱將用戶端認證委派給電腦。

```powershell
Enable-WSManCredSSP -Role "Client" -DelegateComputer "Server02.fabrikam.com"
```

```Output
cfg         : http://schemas.microsoft.com/wbem/wsman/1/config/client/auth
lang        : en-US
Basic       : true
Digest      : true
Kerberos    : true
Negotiate   : true
Certificate : true
CredSSP     : true
```

### 範例 2︰將用戶端認證委派給網域中的所有電腦

此範例允許將用戶端認證委派給 **fabrikam.com** 網域中的所有電腦。 星號 (`*`) 萬用字元指定所有電腦。

> [!NOTE]
> 使用萬用字元搭配 **DelegateComputer** 參數可以在比所需更多的電腦上啟用 CredSSP。

```powershell
Enable-WSManCredSSP -Role "Client" -DelegateComputer "*.fabrikam.com"
```

```Output
cfg         : http://schemas.microsoft.com/wbem/wsman/1/config/client/auth
lang        : en-US
Basic       : true
Digest      : true
Kerberos    : true
Negotiate   : true
Certificate : true
CredSSP     : true
```

### 範例 3︰將用戶端認證委派給多部電腦

此範例允許將用戶端認證委派給多部電腦。

```powershell
$servers = "server02.fabrikam.com", "server03.fabrikam.com", "server04.fabrikam.com"
Enable-WSManCredSSP -Role "Client" -DelegateComputer $servers
```

```Output
cfg         : http://schemas.microsoft.com/wbem/wsman/1/config/client/auth
lang        : en-US
Basic       : true
Digest      : true
Kerberos    : true
Negotiate   : true
Certificate : true
CredSSP     : true
```

`$servers`變數包含伺服器名稱的清單。 `Enable-WSManCredSSP` 使用 **Role** 參數指定 **用戶端** 角色。 **DelegateComputer** 會從變數中取得電腦名稱稱 `$servers` 。

### 範例 4︰允許電腦做為委派對象

此範例可讓電腦做為另一部電腦的委派。 `Enable-WSManCredSSP`先前範例中所示的 Cmdlet 只會在用戶端上啟用 CredSSP 驗證，並指定可代表其採取動作的遠端電腦。 為了讓遠端電腦成為用戶端的委派，WSMan 的 **服務** 節點中的 CredSSP 專案必須設定為 true。 此範例會將 WSMan 的 **服務** 節點中的 CredSSP 專案設定為 true。

```powershell
Enable-WSManCredSSP -Role "Server"
```

### 範例 5︰使用 Set-Item 允許電腦做為委派對象

此範例允許電腦做為另一部電腦的委派對象。 上述 `Enable-WSManCredSSP` 範例所示的命令只會在用戶端電腦上啟用 CredSSP 驗證，而且它們會指定可代表用戶端電腦採取行動的遠端電腦。 若要讓遠端電腦可做為用戶端的委派對象，必須將 WSMan 提供者之 Service 目錄中的 CredSSP 項目設定為 True。

```powershell
Connect-WSMan -ComputerName "server02"
Set-Item -Path "WSMan:\server02\service\auth\credSSP" -Value $True
```

`Connect-WSMan` 建立與遠端電腦 server02 的連接。 `Set-Item` 使用 **Path** 參數來指定 **WSMan** 提供者的位置。 **Value** 參數會將 **服務** 設定設定為 true。

## PARAMETERS

### -DelegateComputer

指定要委派用戶端認證的伺服器。 最佳做法是使用完整功能變數名稱。

接受萬用字元，但可以在需要的電腦上啟用 CredSSP。

如果 **Role** 參數是 **Client** ，您必須指定這個參數。 如果 **Role** 是 **Server** ，請勿指定此參數。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Force

強制執行命令而不要求使用者確認。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Role

指定是否要啟用 CredSSP 做為用戶端或伺服器。 此參數可接受的值為： **用戶端** 和 **伺服器** 。

如果您指定 **用戶端** ，則會執行下列動作。 這些設定可讓用戶端將明確宣告的認證委派給伺服器 (當達成使用伺服器驗證時)。

- 啟用用戶端上的 CredSSP。
- 將 WS-Management 設定設定 `\<localhost|computername\>\Client\Auth\CredSSP` 為 true。
- 將 Windows CredSSP 原則 **AllowFreshCredentials** 設定為用戶端上的 **WSMan/委派** 。

如果您指定 **Server** ，則會執行下列動作。 此原則設定可讓伺服器做為用戶端的委派對象。

- 啟用伺服器上的 CredSSP。
- 將 WS-Management 設定設定 `\<localhost|computername\>\Service\Auth\CredSSP` 為 true。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Client, Server

Required: True
Position: 0
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

### System.Xml.XmlElement

如果已成功啟用 CredSSP 驗證，此 Cmdlet 會產生 **XMLElement** 物件。

## 注意

若要停用 CredSSP 驗證，請使用 `Disable-WSManCredSSP` Cmdlet。

## 相關連結

[Connect-WSMan](Connect-WSMan.md)

[Disable-WSManCredSSP](Disable-WSManCredSSP.md)

[Disconnect-WSMan](Disconnect-WSMan.md)

[Get-WSManCredSSP](Get-WSManCredSSP.md)

[Get-WSManInstance](Get-WSManInstance.md)

[Invoke-WSManAction](Invoke-WSManAction.md)

[New-WSManInstance](New-WSManInstance.md)

[New-WSManSessionOption](New-WSManSessionOption.md)

[Remove-WSManInstance](Remove-WSManInstance.md)

[Set-WSManInstance](Set-WSManInstance.md)

[Set-WSManQuickConfig](Set-WSManQuickConfig.md)

[Test-WSMan](Test-WSMan.md)
