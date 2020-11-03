---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/find-packageprovider?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-PackageProvider
ms.openlocfilehash: 96e8829b6939c40c85fb924ae65d73f48d2e475b
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201524"
---
# Find-PackageProvider

## 概要
傳回可供安裝的套件管理封裝提供者的清單。

## SYNTAX

```
Find-PackageProvider [[-Name] <String[]>] [-AllVersions] [-Source <String[]>] [-IncludeDependencies]
 [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-RequiredVersion <String>]
 [-MinimumVersion <String>] [-MaximumVersion <String>] [-Force] [-ForceBootstrap] [<CommonParameters>]
```

## DESCRIPTION

**Install-packageprovider** 指令程式會尋找相符的 PackageManagement 提供者，該提供者可在以 PowerShellGet 註冊的套件來源中使用。
這些是可使用 Install-PackageProvider Cmdlet 進行安裝的封裝提供者。
根據預設，這包括可在 PowerShell 資源庫中提供 **PackageManagement** 和 **提供者** 標記的模組。

**Install-packageprovider** 也會尋找套件管理 Azure Blob 存放區中提供的相符套件管理提供者。
使用啟動載入器提供者來尋找並安裝它們。

## 範例

### 範例1：尋找所有可用的封裝提供者

```
PS C:\> Find-PackageProvider
```

此命令會取得套件管理所支援的存放庫上可用之所有套件提供者的清單。
根據預設，這些封裝提供者可在 PowerShell 資源庫和使用套件管理啟動載入應用程式中取得。

### 範例2：尋找提供者的所有版本

```
PS C:\> Find-PackageProvider -Name "Nuget" -AllVersions
```

此命令會尋找名為 Nuget 的所有套件提供者版本。

### 範例3：從指定的來源尋找提供者

```
PS C:\> Find-PackageProvider -Name "Gistprovider" -Source "PSGallery"
```

此命令會使用指定的套件來源，尋找可用的封裝提供者。

## PARAMETERS

### -AllVersions

指出此 Cmdlet 會傳回所有可用版本的封裝提供者。
根據預設， **install-packageprovider** 只會傳回最新的可用版本。

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

### -Credential

指定有權搜尋封裝提供者的使用者帳戶。

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

### -Force

強制執行命令而不要求使用者確認。
目前，這相當於 *ForceBootstrap* 參數。

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

### -Includedependencies 來

指出此 Cmdlet 包含相依性。

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

指定您想要尋找之封裝提供者的最大允許版本。
如果您未新增此參數， **install-packageprovider** 會尋找提供者的最高可用版本。

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

指定您想要尋找的封裝提供者所允許的最低版本。
如果您未新增此參數， **install-packageprovider** 會尋找最高可用的套件版本，此套件也會滿足 *MaximumVersion* 參數所指定的最大指定版本。

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

指定一或多個封裝提供者模組名稱，或包含萬用字元的提供者名稱。
以逗號分隔多個封裝名稱。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Proxy

指定要求的 proxy 伺服器，而不是直接連接到網際網路資源。

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyCredential

指定具有使用 **Proxy** 參數所指定 Proxy 伺服器之權限的使用者帳戶。

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

### -RequiredVersion

指定您想要尋找之封裝提供者的確切允許版本。
如果您未新增此參數，則 **install-packageprovider** 會尋找提供者的最高可用版本，同時也會滿足 *MaximumVersion* 參數所指定的最大版本。

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

### -Source

指定一或多個套件來源。
您可以使用 Get-PackageSource Cmdlet 取得可用套件來源的清單。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

## 輸出

### SoftwareIdentity。

此 Cmdlet 會傳回 **SoftwareIdentity** 物件。
您可以使用管線將 **SoftwareIdentity** 物件輸送到 **安裝 install-packageprovider** ，以安裝 **install-packageprovider** 的結果。

## 注意

## 相關連結

[about_PackageManagement](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[Unregister-PackageSource](Unregister-PackageSource.md)

[Get-PackageSource](Get-PackageSource.md)

[Register-PackageSource](Register-PackageSource.md)

[Install-PackageProvider](Install-PackageProvider.md)
