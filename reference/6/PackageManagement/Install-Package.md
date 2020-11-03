---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 05/23/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/install-package?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-Package
ms.openlocfilehash: f4b7ab67d331075c4b227a50bd07e542f72602f9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203703"
---
# Install-Package

## 概要
安裝一或多個軟體套件。

## SYNTAX

### PackageBySearch (預設) 

```
Install-Package [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Source <String[]>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ProviderName <String[]>] [<CommonParameters>]
```

### PackageByInputObject

```
Install-Package [-InputObject] <SoftwareIdentity[]> [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### NuGet： PackageBySearch

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ConfigFile <String>]
 [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>] [-Contains <String>]
 [-AllowPrereleaseVersions] [-Destination <String>] [-ExcludeVersion] [-Scope <String>]
 [-SkipDependencies] [<CommonParameters>]
```

### NuGet： PackageByInputObject

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ConfigFile <String>]
 [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>] [-Contains <String>]
 [-AllowPrereleaseVersions] [-Destination <String>] [-ExcludeVersion] [-Scope <String>]
 [-SkipDependencies] [<CommonParameters>]
```

### PowerShellGet： PackageBySearch

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-AllowPrereleaseVersions]
 [-Scope <String>] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [-AllowClobber]
 [-SkipPublisherCheck] [-InstallUpdate] [-NoPathUpdate] [<CommonParameters>]
```

### PowerShellGet： PackageByInputObject

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-AllowPrereleaseVersions]
 [-Scope <String>] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [-AllowClobber]
 [-SkipPublisherCheck] [-InstallUpdate] [-NoPathUpdate] [<CommonParameters>]
```

## DESCRIPTION

`Install-Package`Cmdlet 會在本機電腦上安裝一或多個軟體套件。 如果您有多個軟體來源，請使用 `Get-PackageProvider` 和 `Get-PackageSource` 來顯示關於提供者的詳細資料。

## 範例

### 範例1：依封裝名稱安裝封裝

`Install-Package`Cmdlet 會安裝軟體套件及其相依性。

```
PS> Install-Package -Name NuGet.Core -Source MyNuGet -Credential Contoso\TestUser
```

`Install-Package` 使用參數來指定封裝 **名稱** 和 **來源** 。 **Credential** 參數使用具有安裝套件許可權的網域使用者帳戶。 此命令會提示您輸入使用者帳戶密碼。

### 範例2：使用 Find-Package 安裝套件

在此範例中，所傳回的物件 `Find-Package` 會向下傳送管線並由安裝 `Install-Package` 。

```
PS> Find-Package -Name NuGet.Core -Source MyNuGet | Install-Package
```

`Find-Package` 使用 **名稱** 和 **來源** 參數來尋找封裝。 物件會沿著管線向下傳送，並 `Install-Package` 在本機電腦上安裝封裝。

### 範例3：指定版本範圍來安裝封裝

`Install-Package` 使用 **MinimumVersion** 和 **MaximumVersion** 參數指定軟體版本的範圍。

```
PS> Install-Package -Name NuGet.Core -Source MyNuGet -MinimumVersion 2.8.0 -MaximumVersion 2.9.0
```

`Install-Package` 使用 **名稱** 和 **來源** 參數來尋找封裝。 **MinimumVersion** 和 **MaximumVersion** 參數會指定軟體版本的範圍。 已安裝範圍中的最高版本。

## PARAMETERS

### -AcceptLicense

 **AcceptLicense** 會在安裝期間自動接受授權合約。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AllowClobber

覆寫與現有命令衝突的警告訊息。 覆寫與要安裝的命令同名的現有命令。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AllowPrereleaseVersions

允許安裝標記為發行前版本的套件。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject, PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AllVersions

`Install-Package` 安裝所有可用的套件版本。 依預設，只會安裝最新版本。

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

### -Command

指定一或多個搜尋的命令 `Install-Package` 。

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Read-configfile

指定包含設定檔的路徑。

```yaml
Type: System.String
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Contains

`Install-Package` 如果 **Contains** 參數指定的值符合物件的任何屬性值，就會取得物件。

```yaml
Type: System.String
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

指定擁有存取電腦和執行命令之許可權的使用者帳戶。 輸入使用者名稱（例如 **User01** 、 **Domain01\User01** ），或輸入由 Cmdlet 產生的 **PSCredential** 物件 `Get-Credential` 。 如果您輸入使用者名稱，系統就會提示您輸入密碼。

如果未指定 **Credential** 參數，會 `Install-Package` 使用目前的使用者。

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

### -Destination

指定輸入物件的路徑。

```yaml
Type: System.String
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DscResource

指定要搜尋的一或多個 Desired State Configuration (DSC) 資源 `Install-Package` 。 使用 `Find-DscResource` Cmdlet 來尋找 DSC 資源。

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
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
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Filter

指定要在 [ **名稱** ] 和 [ **描述** ] 屬性內搜尋的字詞。

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilterOnTag

指定篩選結果並排除不包含指定標記之結果的標記。

```yaml
Type: System.String[]
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

強制執行命令而不要求使用者確認。 覆寫防止 `Install-Package` 無法成功的限制，但安全性除外。

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

### -Headers

指定封裝標頭。

```yaml
Type: System.String[]
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Include

指定是否 `Install-Package` 應該尋找所有套件類型。 此參數可接受的值如下：

- Cmdlet
- DscResource
- 函式
- RoleCapability
- 工作流程

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:
Accepted values: Cmdlet, DscResource, Function, RoleCapability, Workflow

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

接受管線輸入。 使用封裝的 **SoftwareIdentity** 類型指定封裝。
`Find-Package` 輸出 **SoftwareIdentity** 物件。

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

指出會 `Install-Package` 安裝更新。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumVersion

指定您想要安裝的最大允許套件版本。 如果您未指定此參數，則會 `Install-Package` 安裝套件的最新版本。

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

指定您想要安裝的最小允許套件版本。 如果您未新增此參數，則會 `Install-Package` 安裝套件的最新版本，以滿足 **MaximumVersion** 參數所指定的任何版本。

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

**NoPathUpdate** 僅適用于 `Install-Script` Cmdlet。 **NoPathUpdate** 是提供者所加入的動態參數，而且不受支援 `Install-Package` 。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PackageManagementProvider

指定 **PackageManagement** 提供者的名稱。

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProviderName

指定要將套件搜尋範圍限定在其中的一或多個套件提供者名稱。 您可以執行 `Get-PackageProvider` 來取得套件提供者名稱。

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

指定擁有使用 **proxy** 參數所指定 proxy 伺服器之許可權的使用者帳戶。

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

### -PublishLocation

指定封裝發佈位置的路徑。

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequiredVersion

指定您想要安裝之套件的確切允許版本。 如果您未新增此參數，則會 `Install-Package` 安裝套件的最新版本，以滿足 **MaximumVersion** 參數所指定的任何版本。

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

### -RoleCapability

指定角色功能的陣列。

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Scope

指定要安裝套件的範圍。 此參數可接受的值如下：

- CurrentUser
- AllUsers

```yaml
Type: System.String
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject, PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### ->scriptpublishlocation

指定腳本發佈位置的路徑。

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptSourceLocation

指定腳本來源位置。

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipDependencies

略過軟體相依性的安裝。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
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
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipValidate

略過驗證封裝認證的參數。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Source

指定一或多個套件來源。 多個套件來源名稱必須以逗號分隔。
您可以藉由執行 Cmdlet 來取得套件來源名稱 `Get-PackageSource` 。

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Tag

指定要在套件中繼資料中搜尋的一或多個字串。

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
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
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
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

顯示執行 Cmdlet 時會發生 `Install-Package` 的情況。 Cmdlet 並不會執行。

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

### `Install-Package` 接受來自管線的輸入。

## 輸出

### SoftwareIdentity[]

## 注意

在命令中包含封裝提供者可以讓 Cmdlet 提供動態參數。 動態參數是封裝提供者專用的。 此 `Get-Help` Cmdlet 會列出 Cmdlet 的參數集，並包含提供者的參數集。 例如， `Install-Package` 具有 **PowerShellGet** 參數集，其中包含 `-NoPathUpdate` 、 `AllowClobber` 和 `SkipPublisherCheck` 。

## 相關連結

[about_PackageManagement](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[Find-DscResource](../PowershellGet/Find-DscResource.md)

[Get-Help](../Microsoft.PowerShell.Core/Get-Help.md)

[Get-Package](Get-Package.md)

[Get-PackageProvider](Get-PackageProvider.md)

[Get-PackageSource](Get-PackageSource.md)

[Find-Package](Find-Package.md)

[Save-Package](Save-Package.md)

[Uninstall-Package](Uninstall-Package.md)
