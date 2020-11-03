---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/1/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/rename-computer?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-Computer
ms.openlocfilehash: e2d4f321609a386c6795949a4a706323b4889f69
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204339"
---
# Rename-Computer

## 概要
重新命名電腦。

## SYNTAX

```
Rename-Computer [-ComputerName <String>] [-PassThru] [-DomainCredential <PSCredential>]
 [-LocalCredential <PSCredential>] [-NewName] <String> [-Force] [-Restart] [-WsmanAuthentication <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

Cmdlet 會重新 `Rename-Computer` 命名本機電腦或遠端電腦。
它會在每個命令中重新命名一部電腦。

此 Cmdlet 是在 Windows PowerShell 3.0 中引進。

## 範例

### 範例1：重新命名本機電腦

此命令會將本機電腦重新命名為 `Server044` ，然後重新開機，以使變更生效。

```powershell
Rename-Computer -NewName "Server044" -DomainCredential Domain01\Admin01 -Restart
```

### 範例2：重新命名遠端電腦

此命令會將 `Srv01` 電腦重新命名為 `Server001` 。 電腦未重新開機。

**DomainCredential** 參數會指定有權重新命名網域中電腦的使用者認證。

**Force** 參數會抑制確認提示。

```powershell
Rename-Computer -ComputerName "Srv01" -NewName "Server001" -DomainCredential Domain01\Admin01 -Force
```

## PARAMETERS

### -ComputerName

重新命名指定的遠端電腦。
預設是本機電腦。

輸入遠端電腦的 NetBIOS 名稱、IP 位址或完整網域名稱。
若要指定本機電腦，請輸入電腦名稱稱、點 (`.`) 或 `localhost` 。

此參數不依賴 PowerShell 遠端功能。
**ComputerName** `Rename-Computer` 即使您的電腦未設定為執行遠端命令，您也可以使用 ComputerName 參數。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local Computer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -DomainCredential

指定具有連線網域權限的使用者帳戶。
需要明確認證才能重新命名已加入網域的電腦。

輸入使用者名稱（例如 `User01` 或）， `Domain01\User01` 或輸入 **PSCredential** 物件，例如 Cmdlet 所產生的物件 `Get-Credential` 。

如果您輸入使用者名稱，此 Cmdlet 會提示您輸入密碼。

若要指定具有 **ComputerName** 參數指定電腦連線權限的使用者帳戶，請使用 **LocalCredential** 參數。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

強制執行命令而不要求使用者確認。

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

### -LocalCredential

指定具有連線到 **ComputerName** 參數所指定電腦之權限的使用者帳戶。 預設為目前使用者。

輸入使用者名稱（例如 `User01` 或）， `Domain01\User01` 或輸入 **PSCredential** 物件，例如 Cmdlet 所產生的物件 `Get-Credential` 。

如果您輸入使用者名稱，此 Cmdlet 會提示您輸入密碼。

若要指定具有連線網域之權限的使用者帳戶，請使用 **DomainCredential** 參數。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current User
Accept pipeline input: False
Accept wildcard characters: False
```

### -NewName

指定電腦的新名稱。
這是必要參數。

標準名稱可包含字母 (`a-z`) 、 (`A-Z`) 、數位 (`0-9`) 和連字號 () `-` ，但 () 不能有空格或句號 `.` 。 名稱不能完全由數位組成，而且長度可能不能超過63個字元

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

傳回命令的結果。
否則，此 Cmdlet 不會產生任何輸出。

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

### -Restart

指出此 Cmdlet 會重新開機已重新命名的電腦。
通常必須重新啟動才能使變更生效。

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

### -WsmanAuthentication

指定當此 Cmdlet 使用 WSMan 通訊協定時，用來驗證使用者認證的機制。 此參數可接受的值為：

- **基本**
- **CredSSP**
- **預設值**
- **Digest**
- **Kerberos**
- **洽談**

預設值為 **Default** 。

如需此參數值的詳細資訊，請參閱 [AuthenticationMechanism 列舉](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。

> [!WARNING]
> 認證安全性服務提供者 (CredSSP) 驗證，其中使用者認證會傳遞至要驗證的遠端電腦，其設計是針對需要在多個資源上進行驗證的命令，例如存取遠端網路共用。
> 此機制會使得遠端作業的安全性風險變高。
> 如果遠端電腦遭到入侵，傳遞給它的認證可以用來控制 > 網路會話。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, CredSSP, Digest, Kerberos

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

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 輸入

### 無

此 Cmdlet 沒有透過值輸入的參數。
不過，您可以使用管線將物件之 **ComputerName** 和 **NewName** 屬性的值傳送到此 Cmdlet。

## 輸出

### Microsoft.PowerShell.Commands.ComputerChangeInfo

如果您指定 **PassThru** 參數，此 Cmdlet 會傳回 **ComputerChangeInfo** 物件。
否則，它不會傳回任何輸出。

## 注意

## 相關連結

[Restart-Computer](Restart-Computer.md)

[Stop-Computer](Stop-Computer.md)
