---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 04/04/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Computer
ms.openlocfilehash: 89e43220a8d5ac675ea232db09cf3edec2ca2b97
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203567"
---
# Remove-Computer

## 概要
將本機電腦從其網域中移除。

## SYNTAX

### Local (預設值)

```
Remove-Computer [[-UnjoinDomainCredential] <PSCredential>] [-Restart] [-Force] [-PassThru]
 [-WorkgroupName <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 遠端

```
Remove-Computer -UnjoinDomainCredential <PSCredential> [-LocalCredential <PSCredential>] [-Restart]
 [-ComputerName <String[]>] [-Force] [-PassThru] [-WorkgroupName <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION

Cmdlet 會將 `Remove-Computer` 本機電腦和遠端電腦從其目前網域中移除。

當您將電腦從網域中移除時， `Remove-Computer` 也會停用該電腦的網域帳戶。 您必須提供明確的認證，將電腦從其網域中退出，即使它們是目前使用者的認證。 您必須重新開機電腦，才能讓變更生效。 此外，當您將電腦從網域中移除時，必須將它移到工作群組中。 請使用 **WorkgroupName** 參數來指定工作群組。

若要將電腦從工作組移到網域、從一個工作組移到另一個工作組，或是從一個網域移到另一個網域，請使用 `Add-Computer` Cmdlet。

若要取得此命令的結果，請使用 **Verbose** 和 **PassThru** 參數。 若要抑制使用者提示，請使用 **Force** 參數。

`Remove-Computer` 從網域移除本機電腦和遠端電腦。 它包含認證參數，用來指定連線到遠端電腦及從網域退出時所要使用的替代認證； **Restart** 參數，用來重新啟動受影響的電腦；以及 **WorkgroupName** 參數，用來指定電腦要加入的工作群組名稱。

## 範例

### 範例1：將本機電腦從其網域中移除

此範例會將本機電腦從其加入的網域中移除。

```powershell
Remove-Computer -UnjoinDomaincredential Domain01\Admin01 -PassThru -Verbose -Restart
```

**UnjoinDomainCredential** 參數提供網域系統管理員的認證。 **PassThru** 和 **詳細** 資訊一般參數會顯示命令成功或失敗的相關資訊。 **Restart** 參數會重新開機電腦以完成移除操作。

當未指定工作組名稱時，會將電腦從其網域中移除之後，移至名為的工作組。

### 範例2：將數部電腦移至舊版工作組

此範例會從其網域移除檔案中列出的所有電腦 `OldServers.txt` ，並將它們移至 **舊版** 工作組。

```powershell
Remove-Computer -ComputerName (Get-Content OldServers.txt) -LocalCredential Domain01\Admin01 -UnJoinDomainCredential Domain01\Admin01 -WorkgroupName "Legacy" -Force -Restart
```

**LocalCredential** 參數提供具有連線到遠端電腦之許可權的使用者認證。 **UnjoinDomainCredential** 參數提供有許可權可從其網域移除電腦的使用者認證。 **Force** 參數會抑制每部電腦的確認提示。 **重新開機** 參數會在每一部電腦從其網域中移除後，重新開機電腦。

### 範例3：在沒有確認的情況下，從工作組移除電腦

此範例會將遠端電腦、Server01 和本機電腦從其網域中移除，並將其新增至 **本機** 工作組。

```powershell
Remove-Computer -ComputerName "Server01", "localhost" -UnjoinDomainCredential Domain01\Admin01 -WorkgroupName "Local" -Restart -Force
```

**Force** 參數會抑制每部電腦的確認提示。 **重新開機** 參數會重新開機電腦，讓變更生效。

## PARAMETERS

### -ComputerName

指定要從其網域中移除的電腦。 預設是本機電腦。

輸入遠端電腦 (FQDN) 的 NetBIOS 名稱、IP 位址或完整功能變數名稱。 若要指定本機電腦，請輸入電腦名稱、句點 (.)，或者 localhost。

此參數不依賴 PowerShell 遠端功能。 **ComputerName** `Remove-Computer` 即使您的電腦未設定為執行遠端命令，您也可以使用 ComputerName 參數。

此參數是在 PowerShell 3.0 中引進。

```yaml
Type: System.String[]
Parameter Sets: Remote
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Force

抑制使用者提示。 依預設， `Remove-Computer` 會在移除每部電腦之前提示您確認。

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

指定具有連線到 **ComputerName** 參數所指定電腦之許可權的使用者帳戶。 預設為目前使用者。

輸入使用者名稱（例如 `User01` 或）， `Domain01\User01` 或輸入 **PSCredential** 物件，例如 Cmdlet 所產生的物件 `Get-Credential` 。 如果您輸入使用者名稱，此 Cmdlet 會提示您輸入密碼。 若要指定具有將電腦從其目前網域中移除之權限的使用者帳戶，請使用 **UnjoinDomainCredential** 參數。

此參數是在 PowerShell 3.0 中引進。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Remote
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

傳回命令的結果。 否則，此 Cmdlet 不會產生任何輸出。

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

指出此 Cmdlet 會重新開機正在移除的電腦。 通常必須重新啟動才能使變更生效。

此參數是在 PowerShell 3.0 中引進。

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

### -UnjoinDomainCredential

指定具有將電腦從其目前網域中移除之權限的使用者帳戶。
必須由這個參數提供明確的認證 (即使值是目前使用者的認證)，才能將遠端電腦從網域中移除。

輸入使用者名稱（例如 User01 或 Domain01\User01），或輸入 **PSCredential** 物件，例如所產生的物件 `Get-Credential` 。 如果您輸入使用者名稱，此 Cmdlet 會提示您輸入密碼。

若要指定具有連線到遠端電腦之權限的使用者帳戶，請使用 **LocalCredential** 參數。

此參數是在 PowerShell 3.0 中引進。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Local, Remote
Aliases: Credential

Required: False (Local), True (Remote)
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WorkgroupName

指定在將電腦從其網域中移除後，要讓它們加入的工作群組名稱。 預設值為 **WORKGROUP** 。 當您將電腦從網域中移除時，必須將它新增到工作群組中。

此參數是在 PowerShell 3.0 中引進。

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

顯示執行 Cmdlet 後會發生的情況。 Cmdlet 並不會執行。

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

### System.String

您可以透過管線將電腦名稱稱傳送至 thisCmdlet。

## 輸出

### Microsoft.PowerShell.Commands.ComputerChangeInfo

當您使用 **PassThru** 參數時，會傳回 `Remove-Computer` **ComputerChangeInfo** 物件。
否則，此 Cmdlet 不會產生任何輸出。

## 注意

這個 Cmdlet 不會將電腦從工作群組中移除。

## 相關連結

[Add-Computer](Add-Computer.md)

[Checkpoint-Computer](Checkpoint-Computer.md)

[Remove-Computer](Remove-Computer.md)

[Rename-Computer](Rename-Computer.md)

[Restart-Computer](Restart-Computer.md)

[Restore-Computer](Restore-Computer.md)

[Stop-Computer](Stop-Computer.md)

[Test-Connection](Test-Connection.md)
