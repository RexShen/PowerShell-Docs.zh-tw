---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/new-localgroup?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-LocalGroup
ms.openlocfilehash: de66ad724d3cfee2d296d3b431618768a9cd38da
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203631"
---
# New-LocalGroup

## 概要
建立本機安全性群組。

## SYNTAX

```
New-LocalGroup [-Description <String>] [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
**LocalGroup 指令程式** 會在安全性帳戶管理員中建立本機安全性群組。

> [!NOTE]
> 64位系統上的32位 PowerShell 無法使用 LocalAccounts 模組。

## 範例

### 範例1：建立安全性群組

```
PS C:\> New-LocalGroup -Name "SecurityGroup04"
```

此命令會建立名為 SecurityGroup04 的群組。

## PARAMETERS

### -Description
指定群組的批註。
長度上限為48個字元。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name
指定群組的名稱。
最大長度是 256 個字元。

```yaml
Type: System.String
Parameter Sets: (All)
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

### System.String
您可以使用管線傳送字串至此 Cmdlet。

## 輸出

### SecurityAccountsManager. LocalGroup。
此 Cmdlet 會傳回安全性群組。

## 注意

* **PrincipalSource** 屬性是 **LocalUser** 、 **LocalGroup** 和 **LocalPrincipal** 物件的屬性，可描述物件的來源。 可能的來源如下所示：

- 本機
- Active Directory
- Azure Active Directory 群組
- Microsoft 帳戶

只有 Windows 10、Windows Server 2016 和更新版本的 Windows 作業系統才支援 **PrincipalSource** 。 針對較舊的版本，屬性為空白。

## 相關連結

[Get-LocalGroup](Get-LocalGroup.md)

[Remove-LocalGroup](Remove-LocalGroup.md)

[Rename-LocalGroup](Rename-LocalGroup.md)

[Set-LocalGroup](Set-LocalGroup.md)
