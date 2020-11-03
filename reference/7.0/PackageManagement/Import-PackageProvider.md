---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/import-packageprovider?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PackageProvider
ms.openlocfilehash: a4068cd7607868608bce8e334421523325abdfa1
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201507"
---
# Import-PackageProvider

## 概要
將套件管理封裝提供者加入至目前的會話。

## SYNTAX

```
Import-PackageProvider [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Force] [-ForceBootstrap] [<CommonParameters>]
```

## DESCRIPTION

`Import-PackageProvider`Cmdlet 會將一或多個封裝提供者加入至目前的會話。
您匯入的提供者必須安裝在本機電腦上。

若要取得可用提供者的清單，請執行 `Get-PackageProvider -ListAvailable` 。
請注意，套件提供者名稱可以與其模組名稱不同。

基於安全性理由， **PackageManagement** 要求以 c # 為基礎的提供者必須包含 `provider.manifest` 。 如需有關如何建立已插入之提供者的詳細資訊 `provider.manifest` ，請參閱 `.csproj` 中的專案檔 [https://github.com/oneget/oneget](https://github.com/oneget/oneget) 。

## 範例

### 範例1：從本機電腦匯入封裝提供者

```powershell
PS C:\> Import-PackageProvider -Name "Nuget"
```

此命令會在安裝到本機電腦之後，匯入 Nuget 提供者。

### 範例2：匯入特定版本的封裝提供者

```powershell
PS C:\> Find-PackageProvider -Name "Nuget" -AllVersions
Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Force
Get-PackageProvider -ListAvailable
Import-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Verbose
```

此命令會尋找、安裝和匯入特定版本的 Nuget 封裝提供者。

## PARAMETERS

### -Force

強制執行命令而不要求使用者確認。
重新匯入封裝提供者。

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

### -ForceBootstrap

指出此 Cmdlet 會強制套件管理自動安裝封裝提供者。

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

### -MaximumVersion

指定您想要匯入的套件提供者所允許的最大版本。 如果您沒有加入此參數，則會匯 `Import-PackageProvider` 入提供者的最高可用版本。

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

### -MinimumVersion

指定您要匯入的套件提供者所允許的最低版本。 如果您未新增此參數，則會匯 `Import-PackageProvider` 入最高可用的套件版本，此套件也會滿足使用 *MaximumVersion* 參數所指定的最大版本。

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

### -Name

指定一或多個封裝提供者名稱。 不允許使用萬用字元。

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

### -RequiredVersion

指定您想要匯入之封裝提供者的確切版本。 如果您未新增此參數，則會匯 `Import-PackageProvider` 入提供者的最高可用版本，同時也會滿足使用 **MaximumVersion** 參數所指定的最大版本。

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

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### Install-packageprovider。

您可以使用管線將所傳回的 **install-packageprovider** 物件傳送 `Get-PackageProvider` 至 `Import-PackageProvider` 。

## 輸出

## 注意

## 相關連結

[about_PackageManagement](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[Unregister-PackageSource](Unregister-PackageSource.md)

[Get-PackageSource](Get-PackageSource.md)

[Register-PackageSource](Register-PackageSource.md)

[Get-PackageProvider](Get-PackageProvider.md)
