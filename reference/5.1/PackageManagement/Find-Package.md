---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 04/03/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/find-package?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-Package
ms.openlocfilehash: 71266e097524847502e9ce2e4e59c4908352c859
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202963"
---
# Find-Package

## 概要
尋找可用套件來源中的軟體套件。

## SYNTAX

### NuGet

```
Find-Package [-IncludeDependencies] [-AllVersions] [-Source <String[]>] [-Credential <PSCredential>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [[-Name] <String[]>] [-RequiredVersion <String>]
 [-MinimumVersion <String>] [-MaximumVersion <String>] [-Force] [-ForceBootstrap]
 [-ProviderName <String[]>] [-ConfigFile <String>] [-SkipValidate] [-Headers <String[]>]
 [-FilterOnTag <String[]>] [-Contains <String>] [-AllowPrereleaseVersions] [<CommonParameters>]
```

### PowerShellGet

```
Find-Package [-IncludeDependencies] [-AllVersions] [-Source <String[]>] [-Credential <PSCredential>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [[-Name] <String[]>] [-RequiredVersion <String>]
 [-MinimumVersion <String>] [-MaximumVersion <String>] [-Force] [-ForceBootstrap]
 [-ProviderName <String[]>] [-AllowPrereleaseVersions] [-PackageManagementProvider <String>]
 [-PublishLocation <String>] [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>]
 [-Type <String>] [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>]
 [-DscResource <String[]>] [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense]
 [<CommonParameters>]
```

## DESCRIPTION

`Find-Package` 尋找套件來源中可用的軟體套件。 `Get-PackageProvider` 並 `Get-PackageSource` 顯示您提供者的詳細資料。

## 範例

### 範例1：尋找封裝提供者中的所有可用封裝

此命令會在已註冊的資源庫中尋找所有可用的 PowerShell 模組套件。 使用 `Get-PackageProvider` 取得提供者名稱。

```
Find-Package -ProviderName NuGet
```

```Output
Name               Version   Source     Summary
----               -------   ------     -------
NUnit              3.11.0    MyNuGet    NUnit is a unit-testing framework for all .NET langua...
Newtonsoft.Json    12.0.1    MyNuGet    Json.NET is a popular high-performance JSON framework...
EntityFramework    6.2.0     MyNuGet    Entity Framework is Microsoft's recommended data acce...
MySql.Data         8.0.15    MyNuGet    MySql.Data.MySqlClient .Net Core Class Library
bootstrap          4.3.1     MyNuGet    Bootstrap framework in CSS. Includes fonts and JavaSc...
NuGet.Core         2.14.0    MyNuGet    NuGet.Core is the core framework assembly for NuGet...
```

`Find-Package` 使用 **provider** 參數指定提供者 **NuGet** 。

### 範例2：從套件來源尋找套件

此命令會從指定的套件來源尋找最新版本的套件。 如果未提供套件來源，則會 `Find-Package` 搜尋每個已安裝的套件提供者及其套件來源。 使用 `Get-PackageSource` 取得來源名稱。

```
Find-Package -Name NuGet.Core -Source MyNuGet
```

```Output
Name         Version   Source    Summary
----         -------   ------    -------
NuGet.Core   2.14.0    MyNuGet   NuGet.Core is the core framework assembly for NuGet...
```

`Find-Package` 使用 **Name** 參數來指定套件名稱 **nuget.exe** 。 **Source** 參數會指定在 **MyNuGet** 中搜尋封裝。

### 範例3：尋找套件的所有版本

此命令會從指定的提供者找出所有可用的套件版本。

```
Find-Package -Name NuGet.Core -Source MyNuGet -AllVersions
```

```Output
Name          Version          Source       Summary
----          -------          ------       -------
NuGet.Core    2.14.0           MyNuGet      NuGet.Core is the core framework assembly for NuGet...
NuGet.Core    2.14.0-rtm-832   MyNuGet      NuGet.Core is the core framework assembly for NuGet...
NuGet.Core    2.13.0           MyNuGet      NuGet.Core is the core framework assembly for NuGet...
...
NuGet.Core    1.1.229.159      MyNuGet      NuGet.Core is the core framework assembly for NuGet...
Nuget.Core    1.0.1120.104     MyNuGet      NuGet.Core is the core framework assembly for NuGet...
```

`Find-Package` 使用 **Name** 參數來指定套件 **nuget.exe** 。 **ProviderName** 參數指定要在 **MyNuGet** 中搜尋封裝。 **Allversions 進行篩選** 指定傳回所有可用的版本。

### 範例4：尋找具有特定名稱和版本的套件

此命令會從指定的提供者中尋找特定的封裝版本。

```
Find-Package -Name NuGet.Core -ProviderName NuGet -RequiredVersion 2.9.0
```

```Output
Name          Version          Source       Summary
----          -------          ------       -------
NuGet.Core    2.9.0            MyNuGet      NuGet.Core is the core framework assembly for NuGet...
```

`Find-Package` 使用 **Name** 參數來指定套件名稱 **nuget.exe** 。 **ProviderName** 參數指定要在 **NuGet** 中搜尋套件。 **RequiredVersion** 指定只傳回版本 **2.9.0 版** 。

### 範例5：尋找版本範圍內的套件

此命令會尋找指定套件的版本範圍。

```
Find-Package -Name NuGet.Core -ProviderName NuGet -MinimumVersion 2.7.0 -MaximumVersion 2.9.0 -AllVersions
```

```Output
Name          Version          Source       Summary
----          -------          ------       -------
NuGet.Core    2.9.0            MyNuGet      NuGet.Core is the core framework assembly for NuGet...
NuGet.Core    2.8.6            MyNuGet      NuGet.Core is the core framework assembly for NuGet...
NuGet.Core    2.8.0            MyNuGet      NuGet.Core is the core framework assembly for NuGet...
NuGet.Core    2.7.0            MyNuGet      NuGet.Core is the core framework assembly for NuGet...
```

`Find-Package` 使用 **Name** 參數來指定套件名稱 **nuget.exe** 。 **ProviderName** 參數指定要在 **NuGet** 中搜尋套件。 **MinimumVersion** 會指定最低版本的 **2.7.0** 。 **MaximumVersion** 指定最高版本的 **2.9.0 版** 。
**Allversions 進行篩選** 會根據最小值和最大值來判斷傳回的範圍。

### 範例6：尋找檔案系統中的封裝

此命令會尋找副檔名 `.nupkg` 儲存在本機電腦上的封裝。
這些檔案是從資源庫（例如 **NuGet** ）下載的套件。

```
PS> Find-Package -Source C:\LocalPkg
```

```Output
Name                 Version    Source           Summary
----                 -------    ------           -------
Microsoft.Web.Xdt    3.0.0      C:\LocalPkg\     Microsoft Xml Document Transformation (XDT)...
NuGet.Core           2.14.0     C:\LocalPkg\     NuGet.Core is the core framework assembly...
```

## PARAMETERS

### -AcceptLicense

如果封裝需要授權合約，就會自動接受授權合約。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AllowPrereleaseVersions

在結果中包含標記為發行前版本的套件。

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

### -AllVersions

指出會傳回 `Find-Package` 所有可用的封裝版本。 根據預設， `Find-Package` 只會傳回最新的可用版本。

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

指定所搜尋的命令陣列 `Find-Package` 。

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Read-configfile

指定設定檔。

```yaml
Type: System.String
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Contains

`Find-Package` 如果物件的屬性值中有任何專案與指定的值完全相符，就會取得物件。

```yaml
Type: System.String
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

指定有權搜尋封裝的使用者帳戶。

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

### -DscResource

指定此 Cmdlet 搜尋的 Desired State Configuration (DSC) 資源陣列。

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet
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
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilterOnTag

指定篩選結果的標記。 不包含指定標記的結果會被排除。

```yaml
Type: System.String[]
Parameter Sets: NuGet
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

指出 `Find-Package` 強制 **PackageManagement** 自動安裝封裝提供者。

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

指定封裝的標頭。

```yaml
Type: System.String[]
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Includedependencies 來

指出此 Cmdlet 會在結果中包含套件相依性。

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

### -Include

指定是否 `Find-Package` 應該尋找類別中的所有套件。

接受的值如下：

- Cmdlet
- DscResource
- 函式
- RoleCapability
- 工作流程

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet
Aliases:
Accepted values: Cmdlet, DscResource, Function, RoleCapability, Workflow

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumVersion

指定您想要尋找的最大套件版本。

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

指定您想要尋找的最小套件版本。 如果有更高的版本可用，則會傳回該版本。

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

指定一或多個封裝名稱，或包含萬用字元的封裝名稱。 以逗號分隔多個封裝名稱。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -PackageManagementProvider

指定套件管理提供者的名稱。

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProviderName

指定一或多個封裝提供者名稱。 以逗號分隔多個封裝提供者名稱。
使用 `Get-PackageProvider` 取得可用封裝提供者的清單。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Provider
Accepted values: Bootstrap, NuGet, PowerShellGet

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Proxy

為要求指定 proxy 伺服器，而不是直接連線到網際網路資源。

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

### -PublishLocation

指定發佈封裝的位置。

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequiredVersion

指定您想要尋找的確切套件版本。

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

### -RoleCapability

指定角色功能的陣列。

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### ->scriptpublishlocation

指定封裝的腳本發行位置。

```yaml
Type: System.String
Parameter Sets: PowerShellGet
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
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipValidate

略過封裝認證驗證的參數。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Source

指定一或多個套件來源。 用 `Get-PackageSource` 來取得可用套件來源的清單。 檔案系統目錄可以作為下載封裝的來源。

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

### -Tag

指定要在套件中繼資料中搜尋的一或多個字串。

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Type

指定是否要使用模組、腳本或其中一個來搜尋封裝。

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:
Accepted values: Module, Script, All

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無

`Find-Package` 不接受來自管線的輸入。

## 輸出

### SoftwareIdentify[]

`Find-Package` 輸出 **SoftwareIdentity** 物件。

## 注意

## 相關連結

[about_PackageManagement](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[Get-Package](Get-Package.md)

[Get-PackageProvider](Get-PackageProvider.md)

[Get-PackageSource](Get-PackageSource.md)

[Install-Package](Install-Package.md)

[Save-Package](Save-Package.md)

[Uninstall-Package](Uninstall-Package.md)
