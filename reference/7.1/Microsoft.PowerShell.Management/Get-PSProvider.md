---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-psprovider?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSProvider
ms.openlocfilehash: e11a62163f70615f33825c46999d37077b1c3d93
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202224"
---
# Get-PSProvider

## 概要
取得指定 PowerShell 提供者的相關資訊。

## SYNTAX

```
Get-PSProvider [[-PSProvider] <String[]>] [<CommonParameters>]
```

## DESCRIPTION

`Get-PSProvider`Cmdlet 會取得目前會話中的 PowerShell 提供者。
您可以取得工作階段中的特定磁碟機或所有磁碟機。

PowerShell 提供者可讓您存取各種資料存放區，就好像它們是檔案系統磁片磁碟機一樣。
如需 PowerShell 提供者的詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

## 範例

### 範例 1︰顯示所有可用提供者的清單

```powershell
Get-PSProvider
```

此命令會顯示所有可用 PowerShell 提供者的清單。

### 範例2：顯示以指定字母開頭之所有 PowerShell 提供者的清單

```powershell
Get-PSProvider f*, r* | Format-List
```

此命令會顯示所有名稱以字母 f 或 r 開頭的 PowerShell 提供者清單。

### 範例 3︰尋找將提供者新增到您工作階段的嵌入式管理單元或模組

```powershell
Get-PSProvider | Format-Table name, module, pssnapin -auto
```

```Output
Name        Module       PSSnapIn
----        ------       --------
Test        TestModule
WSMan                    Microsoft.WSMan.Management
Alias                    Microsoft.PowerShell.Core
Environment              Microsoft.PowerShell.Core
FileSystem               Microsoft.PowerShell.Core
Function                 Microsoft.PowerShell.Core
Registry                 Microsoft.PowerShell.Core
Variable                 Microsoft.PowerShell.Core
Certificate              Microsoft.PowerShell.Security
```

```powershell
Get-PSProvider | Where {$_.pssnapin -eq "Microsoft.PowerShell.Security"}
```

```Output
Name            Capabilities      Drives
----            ------------      ------
Certificate     ShouldProcess     {cert}
```

這些命令會尋找已將提供者新增至您會話的 PowerShell 嵌入式管理單元或模組。
所有的 PowerShell 專案（包括提供者）都源自嵌入式管理單元或模組。

這些命令會使用傳回之 **ProviderInfo** 物件的 PSSnapin 和 Module 屬性 `Get-PSProvider` 。
這些屬性的值包含新增提供者的嵌入式管理單元或模組的名稱。

第一個命令會取得工作階段中的所有提供者，並使用它們的 Name、Module 和 PSSnapin 屬性值，以表格方式設定格式。

第二個命令會使用 `Where-Object` Cmdlet 來取得來自 **Microsoft. 安全性** 嵌入式管理單元的提供者。

### 範例 4︰解析檔案系統提供者之 Home 屬性的路徑

```powershell
C:\> Resolve-Path ~
```

```Output
Path
----
C:\Users\User01
```

```powershell
PS C:\> (get-psprovider FileSystem).home
```

```Output
C:\Users\User01
```

此範例顯示波狀符號 (~) 代表 FileSystem 提供者的 **Home** 屬性值。
**Home** 屬性值為選擇性，但針對 **FileSystem** 提供者，它會定義為 `$env:homedrive\$env:homepath` 或 `$home` 。

## PARAMETERS

### -PSProvider

指定此 Cmdlet 取得其資訊之 PowerShell 提供者的名稱或名稱。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 輸入

### String[]

您可以透過管道將一或多個提供者名稱字串傳送至此 Cmdlet。

## 輸出

### System.Management.Automation.ProviderInfo

此 Cmdlet 會傳回代表會話中 PowerShell 提供者的物件。

## 注意

## 相關連結

