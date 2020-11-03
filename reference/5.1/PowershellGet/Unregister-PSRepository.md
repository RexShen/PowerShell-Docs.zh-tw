---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/unregister-psrepository?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-PSRepository
ms.openlocfilehash: 0d98d7bbb26d5a50542f0e125e912ea6333714c1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203876"
---
# Unregister-PSRepository

## 概要
取消註冊存放庫。

## SYNTAX

```
Unregister-PSRepository [-Name] <String[]> [<CommonParameters>]
```

## DESCRIPTION

`Unregister-PSRepository`Cmdlet 會為目前使用者取消註冊存放庫。

## 範例

### 範例1：取消註冊存放庫

此範例會將名為 myNuGetSource 的存放庫取消註冊。

```powershell
Unregister-PSRepository -Name "myNuGetSource"
```

### 範例2：取消註冊所有存放庫

這個範例會使用 `Get-PSRepository` 來取得所有已註冊的存放庫，並使用管線運算子將它們傳遞給以 `Unregister-PSRepository` 取消註冊它們。

```powershell
Get-PSRepository | Unregister-PSRepository
```

## PARAMETERS

### -Name

指定要移除之存放庫的名稱陣列。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.String[]

## 輸出

### System.Object

## 注意

## 相關連結

[Get-PSRepository](Get-PSRepository.md)

[Register-PSRepository](Register-PSRepository.md)

[Set-PSRepository](Set-PSRepository.md)
