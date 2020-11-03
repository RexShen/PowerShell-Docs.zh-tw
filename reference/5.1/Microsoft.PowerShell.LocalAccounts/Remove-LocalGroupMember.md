---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/remove-localgroupmember?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-LocalGroupMember
ms.openlocfilehash: 6e6264a65c343657c2f2f87384d76cc3f1554d3d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203627"
---
# Remove-LocalGroupMember

## 概要
從本機群組移除成員。

## SYNTAX

### Group

```
Remove-LocalGroupMember [-Group] <LocalGroup> [-Member] <LocalPrincipal[]> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### 預設

```
Remove-LocalGroupMember [-Member] <LocalPrincipal[]> [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### SecurityIdentifier

```
Remove-LocalGroupMember [-Member] <LocalPrincipal[]> [-SID] <SecurityIdentifier> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION
**LocalGroupMember** 指令 Cmdlet 會從本機群組中移除使用者或群組。

> [!NOTE]
> 64位系統上的32位 PowerShell 無法使用 LocalAccounts 模組。

## 範例

### 範例1：從 Administrators 群組移除成員

```
PS C:\> Remove-LocalGroupMember -Group "Administrators" -Member "Admin02", "MicrosoftAccount\username@Outlook.com", "AzureAD\DavidChew@contoso.com", "CONTOSO\Domain Admins"
```

此命令會從本機系統管理員群組中移除數個成員。
此 Cmdlet 移除的成員包括本機使用者帳戶、Microsoft 帳戶、Azure Active Directory 帳戶和網域群組。
此範例會在 Outlook.com 中使用帳戶的使用者名稱預留位置值。

## PARAMETERS

### -Group
指定此 Cmdlet 從中移除成員的安全性群組。

```yaml
Type: Microsoft.PowerShell.Commands.LocalGroup
Parameter Sets: Group
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -成員
指定此 Cmdlet 從安全性群組移除的使用者或群組陣列。
您可以依名稱、安全識別碼 (SID) 或 **LocalPrincipal** 物件來指定使用者或群組。
指定 S-R-I-s-S 中的 SID 字串。
. .
format。

```yaml
Type: Microsoft.PowerShell.Commands.LocalPrincipal[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Name
指定此 Cmdlet 從中移除成員的安全性群組名稱。

```yaml
Type: System.String
Parameter Sets: Default
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SID
指定此 Cmdlet 從中移除成員之安全性群組的安全識別碼。

```yaml
Type: System.Security.Principal.SecurityIdentifier
Parameter Sets: SecurityIdentifier
Aliases:

Required: True
Position: 0
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

### SecurityAccountsManager. LocalPrincipal，System.string，SecurityIdentifier....。
您可以使用管線將本機主體、字串或 SID 傳送給此 Cmdlet。

## 輸出

### 無
此 Cmdlet 不會產生任何輸出。

## 注意

* **PrincipalSource** 屬性是 **LocalUser** 、 **LocalGroup** 和 **LocalPrincipal** 物件的屬性，可描述物件的來源。 可能的來源如下所示：

- 本機
- Active Directory
- Azure Active Directory 群組
- Microsoft 帳戶

只有 Windows 10、Windows Server 2016 和更新版本的 Windows 作業系統才支援 **PrincipalSource** 。 針對較舊的版本，屬性為空白。

## 相關連結

[Add-LocalGroupMember](Add-LocalGroupMember.md)

[Get-LocalGroupMember](Get-LocalGroupMember.md)

[New-LocalGroup](New-LocalGroup.md)
