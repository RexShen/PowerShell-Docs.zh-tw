---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 05/24/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/uninstall-package?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Uninstall-Package
ms.openlocfilehash: 4be80765181e045f24b1f90243de21f38533bfba
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203691"
---
# Uninstall-Package

## 概要
卸載一或多個軟體套件。

## SYNTAX

### PackageByInputObject

```
Uninstall-Package [-InputObject] <SoftwareIdentity[]> [-AllVersions] [-Force] [-ForceBootstrap]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### PackageBySearch

```
Uninstall-Package [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ProviderName <String[]>] [<CommonParameters>]
```

### NuGet： PackageByInputObject

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-Destination <String>] [-ExcludeVersion] [-Scope <String>] [-SkipDependencies]
 [<CommonParameters>]
```

### NuGet： PackageBySearch

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-Destination <String>] [-ExcludeVersion] [-Scope <String>] [-SkipDependencies]
 [<CommonParameters>]
```

### PowerShellGet： PackageByInputObject

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-Scope <String>]
 [-PackageManagementProvider <String>] [-Type <String>] [-AllowClobber] [-SkipPublisherCheck]
 [-InstallUpdate] [-NoPathUpdate] [-AllowPrereleaseVersions] [<CommonParameters>]
```

### PowerShellGet： PackageBySearch

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-Scope <String>]
 [-PackageManagementProvider <String>] [-Type <String>] [-AllowClobber] [-SkipPublisherCheck]
 [-InstallUpdate] [-NoPathUpdate] [-AllowPrereleaseVersions] [<CommonParameters>]
```

## DESCRIPTION

`Uninstall-Package`Cmdlet 會從本機電腦卸載一或多個軟體套件。 若要尋找已安裝的套件，請使用 `Get-Package` Cmdlet。

## 範例

### 範例1：卸載套件

`Uninstall-Package`Cmdlet 會卸載套件。 **Name** 參數指定要卸載的封裝。 如果安裝了多個版本的封裝，則會卸載最新版本。

```
PS> Uninstall-Package -Name NuGet.Core
```

### 範例2：使用管線卸載套件

`Get-Package` 找出特定的封裝，並將 **SoftwareIdentity** 物件沿著管線向下傳送至 `Uninsall-Package` Cmdlet。

```
PS> Get-Package -Name NuGet.Core -RequiredVersion 2.14.0 | Uninstall-Package
```

此 `Get-Package` Cmdlet 會使用 **Name** 和 **RequiredVersion** 參數來指定封裝。
**SoftwareIdentity** 物件會沿著管線向下傳送。 `Uninstall-Package`Cmdlet 會以 **InputObject** 的形式接收物件，並移除封裝。

或者， `Uninstall-Package` Cmdlet 可以指定 **InputObject** 參數的值：

`Uninstall-Package -InputObject ( Get-Package -Name NuGet.Core -RequiredVersion 2.14.0 )`

## PARAMETERS

### -AllowClobber

覆寫與現有命令衝突的警告訊息。 覆寫與要安裝的命令同名的現有命令。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AllowPrereleaseVersions

允許將標示為發行前版本的套件卸載。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AllVersions

指出此 Cmdlet 會卸載所有版本的封裝。

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

### -Destination

指定輸入物件路徑的字串。

```yaml
Type: System.String
Parameter Sets: NuGet:PackageByInputObject, NuGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ExcludeVersion

切換以排除資料夾路徑中的版本號碼。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageByInputObject, NuGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

強制執行命令而不要求使用者確認。

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

強制 **PackageManagement** 自動安裝指定套件的封裝提供者。

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

### -InputObject

接受管線輸入，以從 Cmdlet 指定封裝的 **SoftwareIdentity** 物件 `Get-Package` 。 **InputObject** 接受 **SoftwareIdentity** 物件做為 `Get-Package` 值或包含物件的變數。

```yaml
Type: Microsoft.PackageManagement.Packaging.SoftwareIdentity[]
Parameter Sets: PackageByInputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -InstallUpdate

指出 `Uninstall-Package` 卸載更新。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumVersion

指定您想要卸載的最大允許套件版本。 如果您未指定此參數，則會 `Uninstall-Package` 卸載封裝的最新版本。

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MinimumVersion

指定您想要卸載的最小允許套件版本。 如果您未新增此參數，則會 `Uninstall-Package` 卸載封裝的最新版本，以滿足 **MaximumVersion** 參數所指定的任何版本。

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

指定一或多個封裝名稱。 多個封裝名稱必須以逗號分隔。

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoPathUpdate

**NoPathUpdate** 僅適用于 `Install-Script` Cmdlet。 **NoPathUpdate** 是提供者所加入的動態參數，而且不受支援 `Uninstall-Package` 。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PackageManagementProvider

指定 **PackageManagement** 提供者。

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProviderName

指定要搜尋封裝的一或多個封裝提供者名稱。 您可以執行 `Get-PackageProvider` 來取得套件提供者名稱。

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases: Provider
Accepted values: Bootstrap, NuGet, PowerShellGet

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -RequiredVersion

指定您想要卸載之套件的確切允許版本。 如果您未新增此參數，則會 `Uninstall-Package` 卸載封裝的最新版本，以滿足 **MaximumVersion** 參數所指定的任何版本。

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Scope

指定要將封裝卸載的範圍。 此參數可接受的值如下：

- CurrentUser
- AllUsers

```yaml
Type: System.String
Parameter Sets: NuGet:PackageByInputObject, NuGet:PackageBySearch, PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipDependencies

略過卸載軟體相依性。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageByInputObject, NuGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipPublisherCheck

可讓您取得比已安裝版本還新的套件版本。 例如，已安裝的套件已由受信任的發行者進行數位簽署，但新版本未經過數位簽署。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Type

指定是否要使用模組、腳本或兩者來搜尋封裝。 此參數可接受的值如下：

- 模組
- 指令碼
- 全部

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:
Accepted values: Module, Script, All

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

顯示執行 Cmdlet 時會發生 `Uninstall-Package` 的情況。 不會執行此 Cmdlet。

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

### `Uninstall-Package` 接受來自管線的 **SoftwareIdentity** 物件做為輸入。

## 輸出

### `Uninstall-Package` 不會產生任何輸出。

## 注意

在命令中包含封裝提供者可以讓 Cmdlet 提供動態參數。 動態參數是封裝提供者專用的。 此 `Get-Help` Cmdlet 會列出 Cmdlet 的參數集，並包含提供者的參數集。 例如， `Uninstall-Package` 具有 **PowerShellGet** 參數集，其中包含 `-NoPathUpdate` 、 `AllowClobber` 和 `SkipPublisherCheck` 。

## 相關連結

[about_PackageManagement](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[Find-Package](Find-Package.md)

[Get-Package](Get-Package.md)

[Install-Package](Install-Package.md)

[Save-Package](Save-Package.md)
