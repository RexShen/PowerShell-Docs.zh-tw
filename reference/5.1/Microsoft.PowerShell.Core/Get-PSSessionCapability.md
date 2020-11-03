---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssessioncapability?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSessionCapability
ms.openlocfilehash: d76baaef31c27184bc355b6f0fc79ca67b986157
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202295"
---
# Get-PSSessionCapability

## 概要
取得特定使用者對於限制工作階段設定的能力。

## SYNTAX

```
Get-PSSessionCapability [-ConfigurationName] <String> [-Username] <String> [-Full] [<CommonParameters>]
```

## DESCRIPTION
**Get-PSSessionCapability** Cmdlet 會取得特定使用者對於限制工作階段設定的能力。
若要稽核使用者的自訂工作階段設定，請使用此 Cmdlet。

從 Windows PowerShell 5.0 開始，您可以在工作階段設定 (.pssc) 檔案中使用 **RoleDefinitions** 屬性。
使用這個屬性可讓您根據群組成員資格，授與使用者對於單一限制端點不同的能力。
**Get-PSSessionCapability** Cmdlet 在稽核這些端點時可讓您決定授與使用者的實際能力，降低複雜性。

根據預設， **Get-PSSessionCapability** Cmdlet 會傳回一份指定使用者可在指定端點中執行的命令清單。
這相當於使用者在指定的端點中執行 **Get-Command** 。
搭配 *Full* 參數執行時，此 Cmdlet 會傳回 **InitialSessionState** 物件。
此物件包含針對指定端點，指定使用者會互動的 Windows PowerShell Runspace 相關詳細資料。
它包含語言模式、執行原則和環境變數等資訊。

## 範例

### 範例 1︰取得使用者可用的命令

```
PS C:\> Get-PSSessionCapability -ConfigurationName Endpoint1 -Username 'CONTOSO\User'
```

這個範例會在連接到本機電腦上的端點1限制端點時，傳回使用者 CONTOSO\User 可用的命令。

### 範例 2︰取得使用者的 Runspace 相關詳細資料

```
PS C:\> Get-PSSessionCapability -ConfigurationName Endpoint1 -Username 'CONTOSO\User' -Full
```

此範例會傳回使用者 CONTOSO\User 在連接至端點1限制端點時，會互動的運行時的詳細資料。

## PARAMETERS

### -ConfigurationName
指定您要檢查的限制工作階段設定 (端點)。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Full
指出此 Cmdlet 會傳回指定使用者在指定限制端點的整個初始工作階段狀態。

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

### -Username
指定您要檢查其能力的使用者。

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

### CommonParameters
這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

## 輸出

### System.Management.Automation.AliasInfo

### System.Management.Automation.FunctionInfo

### System.Management.Automation.Runspaces.InitialSessionState

## 注意

## 相關連結

[New-PSRoleCapabilityFile](New-PSRoleCapabilityFile.md)
