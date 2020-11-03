---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/disable-wsmancredssp?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-WSManCredSSP
ms.openlocfilehash: e88f230575e1e3106efc211e3f95dd82ec62146c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202147"
---
# Disable-WSManCredSSP

## 概要
停用電腦上的 CredSSP 驗證。

## SYNTAX

```
Disable-WSManCredSSP [-Role] <String> [<CommonParameters>]
```

## DESCRIPTION
**Disable-WSManCredSSP** Cmdlet 會在用戶端或伺服器電腦上停用「認證安全性支援提供者 (CredSSP)」驗證。
使用 CredSSP 驗證時，會將使用者認證傳遞到遠端電腦進行驗證。

使用此 Cmdlet，透過在 *Role* 參數中指定 Client 來停用用戶端上的 CredSSP。
此 Cmdlet 會執行下列動作：

- 停用用戶端上的 CredSSP。 此 Cmdlet 會將 WS-Management 設定 **\<localhost|computername\> \Client\Auth\CredSSP** 設定為 false。
- 從用戶端上的 Windows CredSSP 原則 **AllowFreshCredentials** 移除任何 WSMan/* 設定。

使用此 Cmdlet，透過在 *Role* 中指定 Server 來停用 CredSSP。
此 Cmdlet 會執行下列動作：

- 停用伺服器上的 CredSSP。 此 Cmdlet 會將 WS-Management 設定 **\<localhost|computername\> \Service\Auth\CredSSP** 設定為 false。

注意：CredSSP 驗證會將使用者認證從本機電腦委派給遠端電腦。
此做法會使得遠端作業的安全性風險變高。
若遠端電腦遭到入侵，當認證被傳遞給它時，該認證便可用來控制網路工作階段。

## 範例

### 範例 1︰停用用戶端上的 CredSSP

```
PS C:\> Disable-WSManCredSSP -Role Client
```

此命令會停用用戶端上的 CredSSP，這樣會防止委派給伺服器。

### 範例 2︰停用用戶端上的 CredSSP

```
PS C:\> Disable-WSManCredSSP -Role Server
```

此命令會停用伺服器上的 CredSSP，這樣會防止接受用戶端的委派。

## PARAMETERS

### -Role
指定是否要停用 CredSSP 做為用戶端或伺服器。
此參數可接受的值包括：Client 和 Server。

如果您指定 Client，此 Cmdlet 會執行下列動作：

- 停用用戶端上的 CredSSP。 此 Cmdlet 會將 WS-Management 設定 **\<localhost|computername\> \Client\Auth\CredSSP** 設定為 false。
- 從用戶端上的 Windows CredSSP 原則 **AllowFreshCredentials** 移除任何 WSMan/* 設定。

如果您指定 Server，此 Cmdlet 會執行下列動作：

- 停用伺服器上的 CredSSP。 此 Cmdlet 會將 WS-Management 設定 **\<localhost|computername\> \Service\Auth\CredSSP** 設定為 false。

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

### 無
此 Cmdlet 不會產生任何輸出。

## 注意

* 若要啟用 CredSSP 驗證，請使用 Enable-WSManCredSSP Cmdlet。

*

## 相關連結

[Connect-WSMan](Connect-WSMan.md)

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

