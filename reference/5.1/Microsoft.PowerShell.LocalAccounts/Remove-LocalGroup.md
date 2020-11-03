---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/remove-localgroup?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-LocalGroup
ms.openlocfilehash: 6a2f921972fef1794581b301df6e7439e56c7f47
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203624"
---
# Remove-LocalGroup

## 概要
刪除本機安全性群組。

## SYNTAX

### InputObject

```
Remove-LocalGroup [-InputObject] <LocalGroup[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 預設

```
Remove-LocalGroup [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### SecurityIdentifier

```
Remove-LocalGroup [-SID] <SecurityIdentifier[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
**LocalGroup** 指令 Cmdlet 會刪除本機安全性群組。
此 Cmdlet 只會刪除本機群組。
它不會刪除屬於該群組的使用者帳戶、電腦帳戶或群組帳戶。
您無法復原已刪除的群組。

如果您刪除群組，然後再建立另一個具有相同組名的群組，則必須為新群組設定新的許可權。
新群組不會繼承指派給該群組的許可權。

> [!NOTE]
> 64位系統上的32位 PowerShell 無法使用 LocalAccounts 模組。

## 範例

### 範例1：刪除安全性群組

```
PS C:\> Remove-LocalGroup -Name "SecurityGroup04"
```

此命令會刪除名為 SecurityGroup04 的群組。

## PARAMETERS

### -InputObject
指定此 Cmdlet 刪除的安全性群組陣列。
若要取得群組，請使用 Get-LocalGroup Cmdlet。

```yaml
Type: Microsoft.PowerShell.Commands.LocalGroup[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Name
指定此 Cmdlet 所刪除之安全性群組的名稱陣列。

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SID
指定此 Cmdlet 所刪除之安全性群組 (Sid) 的安全識別碼陣列。

```yaml
Type: System.Security.Principal.SecurityIdentifier[]
Parameter Sets: SecurityIdentifier
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
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

### SecurityAccountsManager. LocalGroup，System.string，SecurityIdentifier....。
您可以使用管線將安全性群組、字串或 SID 傳送給此 Cmdlet。

## 輸出

### 無
此 Cmdlet 不會產生任何輸出。

## 注意

* 此 Cmdlet 無法刪除下列預設群組：

- 系統管理員
- Backup Operators
- Cryptographic Operators
- Distributed COM Users
- Event Log Readers
- Guests
- Hyper-V 系統管理員
- IIS_IUSRS
- Network Configuration Operators
- 效能記錄使用者
- 效能監視器使用者
- Power Users
- Remote Desktop Users
- 遠端管理使用者
- Replicator
- 使用者
- WinRMRemoteWMIUsers__

* **PrincipalSource** 屬性是 **LocalUser** 、 **LocalGroup** 和 **LocalPrincipal** 物件的屬性，可描述物件的來源。 可能的來源如下所示：

- 本機
- Active Directory
- Azure Active Directory 群組
- Microsoft 帳戶

只有 Windows 10、Windows Server 2016 和更新版本的 Windows 作業系統才支援 **PrincipalSource** 。 針對較舊的版本，屬性為空白。

## 相關連結

[Get-LocalGroup](Get-LocalGroup.md)

[New-LocalGroup](New-LocalGroup.md)

[Rename-LocalGroup](Rename-LocalGroup.md)

[Set-LocalGroup](Set-LocalGroup.md)
