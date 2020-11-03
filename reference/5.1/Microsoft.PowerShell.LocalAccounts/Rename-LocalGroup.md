---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/rename-localgroup?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-LocalGroup
ms.openlocfilehash: 566d33bdeb52323cca41fa9757d36334b40f1654
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204099"
---
# Rename-LocalGroup

## 概要
重新命名本機安全性群組。

## SYNTAX

### InputObject

```
Rename-LocalGroup [-InputObject] <LocalGroup> [-NewName] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 預設

```
Rename-LocalGroup [-Name] <String> [-NewName] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### SecurityIdentifier

```
Rename-LocalGroup [-NewName] <String> [-SID] <SecurityIdentifier> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
LocalGroup 指令 Cmdlet 會 **重新** 命名本機安全性群組。

> [!NOTE]
> 64位系統上的32位 PowerShell 無法使用 LocalAccounts 模組。

## 範例

### 範例1：變更群組的名稱

```
PS C:\> Rename-LocalGroup -Name "SecurityGroup" -NewName "SecurityGroup04"
```

此命令會重新命名名為 SecurityGroup 的安全性群組。

## PARAMETERS

### -InputObject
指定此 Cmdlet 重新命名的安全性群組。
若要取得安全性群組，請使用 Get-LocalGroup Cmdlet。

```yaml
Type: Microsoft.PowerShell.Commands.LocalGroup
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Name
指定此 Cmdlet 重新命名之安全性群組的名稱。

```yaml
Type: System.String
Parameter Sets: Default
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -NewName
指定安全性群組的新名稱。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SID
指定此 Cmdlet 重新命名之安全性群組 (SID) 的安全識別碼。

```yaml
Type: System.Security.Principal.SecurityIdentifier
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

* **PrincipalSource** 屬性是 **LocalUser** 、 **LocalGroup** 和 **LocalPrincipal** 物件的屬性，可描述物件的來源。 可能的來源如下所示：

- 本機
- Active Directory
- Azure Active Directory 群組
- Microsoft 帳戶

只有 Windows 10、Windows Server 2016 和更新版本的 Windows 作業系統才支援 **PrincipalSource** 。 針對較舊的版本，屬性為空白。

## 相關連結

[Get-LocalGroup](Get-LocalGroup.md)

[New-LocalGroup](New-LocalGroup.md)

[Remove-LocalGroup](Remove-LocalGroup.md)

[Set-LocalGroup](Set-LocalGroup.md)
