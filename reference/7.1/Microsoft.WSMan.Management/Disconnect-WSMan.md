---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/disconnect-wsman?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disconnect-WSMan
ms.openlocfilehash: 7e2cfc6db38d6537ba83c4dced769dd41a351602
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202143"
---
# Disconnect-WSMan

## 概要
中斷用戶端與遠端電腦上之 WinRM 服務的連線。

## SYNTAX

```
Disconnect-WSMan [[-ComputerName] <String>] [<CommonParameters>]
```

## DESCRIPTION
**Disconnect-WSMan** Cmdlet 會中斷用戶端與遠端電腦上 WinRM 服務的連線。
如果您將 WS-Management 會話儲存在變數中，會話物件仍會保留在變數中，但 WS-Management 會話的狀態會是 [關閉]。
您可以在 WSMan 提供者中使用此 Cmdlet 來中斷用戶端與遠端電腦上之 WinRM 服務的連線。
不過，您也可以使用此 Cmdlet 來中斷與遠端電腦上之 WinRM 服務的連線，再變更為 WSMan 提供者。

如需如何連線到遠端電腦上之 WinRM 服務的詳細資訊，請參閱 Connect-WSMan。

## 範例

### 範例1：刪除遠端電腦的連接

```
PS C:\> Disconnect-WSMan -computer server01
PS C:\> cd WSMan:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan
ComputerName                                  Type
------------                                  ----
localhost                                     Container
```

此命令會刪除名為 server01 之遠端電腦的連接。

此 Cmdlet 通常是在 WSMan 提供者中用來中斷與遠端電腦 (在此案例中是 server01 電腦) 的連線。
不過，您也可以使用「 **中斷連線-WSMan** 」來移除與遠端電腦的連線，然後再變更為 WSMan 提供者。
這些連接不會出現在 ComputerName 清單中。

## PARAMETERS

### -ComputerName
指定要執行管理作業的電腦。
值可以是完整網域名稱、NetBIOS 名稱或 IP 位址。
使用本機電腦名稱、使用 localhost，或使用句點 (.) 來指定本機電腦。
預設值是本機電腦。
當遠端電腦與使用者位於不同網域，您必須使用完整網域名稱。
您可以使用管線將此參數的值傳送至 Cmdlet。

您無法中斷與本機主機的連線。
也就是說，您無法中斷與本機電腦的預設連接。
但是，如果您建立與本機電腦的個別連接，例如使用電腦名稱稱。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
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

## 相關連結

[Connect-WSMan](Connect-WSMan.md)

[Disable-WSManCredSSP](Disable-WSManCredSSP.md)

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

