---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/reset-computermachinepassword?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Reset-ComputerMachinePassword
ms.openlocfilehash: 1484bc83b9503ce43420b833a1b78b3c4215d98a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203531"
---
# Reset-ComputerMachinePassword

## 概要
重設電腦的電腦帳戶密碼。

## SYNTAX

```
Reset-ComputerMachinePassword [-Server <String>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION
**Reset-computermachinepassword** 指令程式會將電腦用來向網域中的網域控制站進行驗證的電腦帳戶密碼變更。
您可以使用它來重設本機電腦的密碼。

## 範例

### 範例1：重設本機電腦的密碼

```
PS C:\> Reset-ComputerMachinePassword
```

此命令會重設本機電腦的電腦密碼。
此命令會使用目前使用者的認證執行。

### 範例2：使用指定的網域控制站重設本機電腦的密碼

```
PS C:\> Reset-ComputerMachinePassword -Server "DC01" -Credential Domain01\Admin01
```

此命令會使用 DC01 網域控制站重設本機電腦的電腦密碼。
它會使用 *Credential* 參數來指定有權在網域中重設電腦密碼的使用者帳戶。

### 範例3：在遠端電腦上重設密碼

```
$cred = Get-Credential
PS C:\> Invoke-Command -ComputerName "Server01" -ScriptBlock {Reset-ComputerMachinePassword -Credential $using:cred}
```

此命令會使用 Invoke-Command Cmdlet，在 Server01 遠端電腦上執行 **reset-computermachinepassword** 命令。

如需 Windows PowerShell 中之遠端命令的詳細資訊，請參閱 about_Remote 和 **Invoke-Command** 。

## PARAMETERS

### -Credential
指定具有執行此動作權限的使用者帳戶。
預設為目前使用者。

輸入使用者名稱，例如 User01 或 Domain01\User01，或輸入 **PSCredential** 物件，例如 Get-Credential Cmdlet 產生的物件。
如果您輸入使用者名稱，此 Cmdlet 會提示您輸入密碼。

此參數是在 Windows PowerShell 3.0 引進。

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

### -Server
指定此 Cmdlet 設定電腦帳戶密碼時要使用的網域控制站名稱。

這是選擇性參數。
如果您省略此參數，會選擇一個網域控制站來為命令提供服務。

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
這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無
您無法使用管線傳送輸入至此 Cmdlet。

## 輸出

### 無
此 Cmdlet 不會產生任何輸出。

## 注意

## 相關連結

## 相關連結
