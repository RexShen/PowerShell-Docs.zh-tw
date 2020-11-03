---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/get-wsmancredssp?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-WSManCredSSP
ms.openlocfilehash: 814be4153687268123114b4036b640eeb0f0da71
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "93196720"
---
# Get-WSManCredSSP

## 概要
取得用戶端的「認證安全性支援提供者」相關設定。

## SYNTAX

```
Get-WSManCredSSP [<CommonParameters>]
```

## DESCRIPTION
**WSManCredSSP** 指令程式會取得用戶端和伺服器的「認證安全性支援提供者」相關設定。
輸出會指出「認證安全性支援提供者 (CredSSP)」驗證已啟用或已停用。
此 Cmdlet 也會顯示 CredSSP 之 **AllowFreshCredentials** 原則的設定資訊。

當您使用 CredSSP 驗證時，使用者的認證會被傳遞到遠端電腦進行驗證。
此類型的驗證是針對會從另一個遠端工作階段建立遠端工作階段的命令所設計。
例如，若您想在遠端電腦上執行背景工作，請使用此類型的驗證。

此 Cmdlet 會執行下列動作：

- 取得用戶端 ( **\<localhost|computername\> \Client\Auth\CredSSP** ) 上的 WS-Management CredSSP 設定。
- 取得 Windows CredSSP 原則設定 **AllowFreshCredentials** 。
- 取得伺服器上的 WS-Management CredSSP 設定 ( **\<localhost|computername\> \Service\Auth\CredSSP** ) 。

注意：CredSSP 驗證會將使用者認證從本機電腦委派給遠端電腦。
此做法會使得遠端作業的安全性風險變高。
若遠端電腦遭到入侵，當認證被傳遞給它時，該認證便可用來控制網路工作階段。

## 範例

### 範例 1︰顯示 CredSSP 設定

```
PS C:\> Get-WSManCredSSP
```

此命令會顯示用戶端與伺服器的 CredSSP 設定資訊。

輸出會識別此電腦是否已針對 CredSSP 設定。

若電腦已針對 CredSSP 設定，輸出如下：

`The machine is configured to allow delegating fresh credentials to the following target(s): wsman/server02.accounting.fabrikam.com`

若電腦未針對 CredSSP 設定，輸出如下：

`The machine is not configured to allow delegating fresh credentials.`

## PARAMETERS

### CommonParameters
這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無
此 Cmdlet 不接受任何輸入。

## 輸出

### 無
此 Cmdlet 不會產生任何輸出。

## 注意

* 若要停用 CredSSP 驗證，請使用 Disable-WSManCredSSP Cmdlet。 若要啟用 CredSSP 驗證，請使用 Enable-WSManCredSSP Cmdlet。

## 相關連結

[Connect-WSMan](Connect-WSMan.md)

[Disable-WSManCredSSP](Disable-WSManCredSSP.md)

[Disconnect-WSMan](Disconnect-WSMan.md)

[Enable-WSManCredSSP](Enable-WSManCredSSP.md)

[Get-WSManInstance](Get-WSManInstance.md)

[Invoke-WSManAction](Invoke-WSManAction.md)

[New-WSManInstance](New-WSManInstance.md)

[New-WSManSessionOption](New-WSManSessionOption.md)

[Remove-WSManInstance](Remove-WSManInstance.md)

[Set-WSManInstance](Set-WSManInstance.md)

[Set-WSManQuickConfig](Set-WSManQuickConfig.md)

[Test-WSMan](Test-WSMan.md)
