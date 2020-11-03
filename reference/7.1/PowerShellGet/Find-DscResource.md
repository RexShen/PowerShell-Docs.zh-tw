---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/04/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-dscresource?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-DscResource
ms.openlocfilehash: 9953a7912d29517249fa215b154c1dfae46585d1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204147"
---
# Find-DscResource

## 概要
尋找 Desired State Configuration (DSC) 資源。

## SYNTAX

### 全部

```
Find-DscResource [[-Name] <String[]>] [-ModuleName <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-RequiredVersion <String>] [-AllVersions] [-AllowPrerelease]
 [-Tag <String[]>] [-Filter <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Repository <String[]>] [<CommonParameters>]
```

## DESCRIPTION

此 `Find-DscResource` Cmdlet 會搜尋已註冊的存放庫，以找出模組中包含的 DSC 資源。 依預設會 `Find-DscResource` 搜尋所有已註冊的存放庫。

針對所找到的每個模組 `Find-DscResource` ，會傳回 **PSGetDscResourceInfo** 物件。
**PSGetDscResourceInfo** 物件可以透過管線傳送至 `Install-Module` Cmdlet。
`Install-Module` 安裝模組。

## 範例

### 範例1：尋找所有 DSC 資源

`Find-DscResource` 從已註冊的存放庫傳回 DSC 資源。 若要搜尋特定的存放庫，請使用存放 **庫** 參數。

```powershell
Find-DscResource
```

```Output
Name                           Version    ModuleName                     Repository
----                           -------    ----------                     ----------
Carbon_Privilege               2.8.1      Carbon                         PSGallery
Carbon_ScheduledTask           2.8.1      Carbon                         PSGallery
Carbon_Service                 2.8.1      Carbon                         PSGallery
PackageManagement              1.4        PackageManagement              PSGallery
PackageManagementSource        1.4        PackageManagement              PSGallery
PSModule                       2.1.4      PowerShellGet                  PSGallery
PSRepository                   2.1.4      PowerShellGet                  PSGallery
xArchive                       8.7.0.0    xPSDesiredStateConfiguration   PSGallery
xDSCWebService                 8.7.0.0    xPSDesiredStateConfiguration   PSGallery
xEnvironment                   8.7.0.0    xPSDesiredStateConfiguration   PSGallery
```

### 範例2：依名稱尋找 DSC 資源

`Find-DscResource` 依名稱尋找 DSC 資源。 使用逗號來分隔資源名稱的陣列。

```powershell
Find-DscResource -Name xWebsite, xWebApplication, xWebSiteDefaults
```

```Output
Name               Version    ModuleName            Repository
----               -------    ----------            ----------
xWebApplication    2.6.0.0    xWebAdministration    PSGallery
xWebsite           2.6.0.0    xWebAdministration    PSGallery
xWebSiteDefaults   2.6.0.0    xWebAdministration    PSGallery
```

`Find-DscResource` 使用 **Name** 參數來尋找指定的 DSC 資源陣列。

### 範例3：尋找 DSC 資源並加以安裝

`Find-DscResource` 尋找 DSC 資源，並將該物件向下傳送要安裝的管線。
安裝之後，請使用 `Get-InstalledModule` 來查看結果。

相同模組中的多個資源可以向下傳送至 `Install-Module` 。
`Install-Module` 嘗試只安裝一次模組。

```powershell
Find-DscResource -Name xWebsite | Install-Module
```

`Find-DscResource` 使用 **Name** 參數來尋找名為 **xWebsite** 的資源。 物件會向下傳送至 `Install-Module` Cmdlet。 `Install-Module` 安裝資源的 **>xwebadministration** 模組。

### 範例4：尋找模組中的所有 DSC 資源

`Find-DscResource` 尋找包含在指定模組中的所有 DSC 資源。 預設會顯示目前的版本。 若要顯示其他版本，請使用 **allversions 進行篩選** 或 **RequiredVersions** 參數。

```powershell
Find-DscResource -ModuleName xWebAdministration
```

```Output
Name                                Version    ModuleName              Repository
----                                -------    ----------              ----------
WebApplicationHandler               2.6.0.0    xWebAdministration      PSGallery
xIisFeatureDelegation               2.6.0.0    xWebAdministration      PSGallery
xIisHandler                         2.6.0.0    xWebAdministration      PSGallery
xIisLogging                         2.6.0.0    xWebAdministration      PSGallery
```

`Find-DscResource` 使用 **ModuleName** 參數來指定 **>xwebadministration** ，並尋找模組中包含的 DSC 資源。 會顯示每個資源的目前版本。

### 範例5：依標記和所需版本尋找 DSC 資源

您可以使用 parameters **標記** 和 **RequiredVersion** 來找出 DSC 資源。 **標記** 會顯示存放庫中包含指定標籤的每個資源目前的版本。
**RequiredVersion** 需要 **ModuleName** 參數，而 **Name** 參數是選擇性的。 **Name** 和 **ModuleName** 參數會限制輸出。 使用 **allversions 進行篩選** 參數來顯示 DSC 資源的可用版本。

```powershell
Find-DscResource -ModuleName xWebAdministration -Tag DSC -RequiredVersion 1.20
```

```output
Name                    Version    ModuleName             Repository
----                    -------    ----------             ----------
xIisFeatureDelegation   1.20.0.0   xWebAdministration     PSGallery
xIisHandler             1.20.0.0   xWebAdministration     PSGallery
xIisLogging             1.20.0.0   xWebAdministration     PSGallery
xIisMimeTypeMapping     1.20.0.0   xWebAdministration     PSGallery
```

### 範例6：使用篩選準則尋找資源

`Find-DscResource` 尋找所有資源，並使用 **篩選** 參數來指定依 **網域** 的結果。 **篩選** 參數會在物件的描述或模組名稱中尋找篩選值。 使用 `Select-Object` Cmdlet 來查看物件的屬性。

```powershell
Find-DscResource -Filter Domain
```

```output
Name                    Version    ModuleName                 Repository
----                    -------    ----------                 ---------
xComputer               4.1.0.0    xComputerManagement        PSGallery
Computer                6.4.0.0    ComputerManagementDsc      PSGallery
xDSCDomainjoin          1.1        xDSCDomainjoin             PSGallery
xDisk                   1.0        xDisk                      PSGallery
xDSCFirewall            1.6.21     xDSCFirewall               PSGallery
dmAwsTagInstance        1.0.1      domainAwsDSCResources      PSGallery
```

## PARAMETERS

### -AllowPrerelease

在結果中包含標示為發行前版本的資源。

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

**Allversions 進行篩選** 參數會顯示 DSC 資源的每個可用版本。 您無法搭配 **MinimumVersion** 、 **MaximumVersion** 或 **RequiredVersion** 參數使用 **allversions 進行篩選** 參數。

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

### -Filter

根據 **PackageManagement** 提供者的搜尋語法尋找資源。 例如，在 [ **ModuleName** ] 和 [ **描述** ] 屬性中指定要搜尋的文字。

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

### -MaximumVersion

指定要包含在結果中之資源的最大版本。 無法在同一個命令中使用 **MaximumVersion** 和 **RequiredVersion** 參數。

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

指定要包含在結果中之資源的最小版本。 **MinimumVersion** 和 **RequiredVersion** 參數無法在相同的命令中使用。

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

### -ModuleName

指定包含 DSC 資源的模組。

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

指定資源的名稱。 預設值為 [所有資源]。 使用逗號來分隔資源名稱的陣列。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
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
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ProxyCredential

指定具有使用 **proxy** 參數中所指定 proxy 伺服器之許可權的使用者帳戶。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Repository

指定要搜尋資源的儲存機制。 使用逗號來分隔存放庫名稱的陣列。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequiredVersion

指定要包含在結果中的模組確切版本號碼。 **RequiredVersion** 和 **MinimumVersion** 參數無法在相同的命令中使用。

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

### -Tag

指定將存放庫中的模組分類的標記。 使用逗號來分隔標記的陣列。

```yaml
Type: System.String[]
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

## 輸出

### PSGetDscResourceInfo

`Find-DscResource` 傳回 **PSGetDscResourceInfo** 物件。

## 注意

## 相關連結

[Get-InstalledModule](Get-InstalledModule.md)

[Install-Module](Install-Module.md)

[Register-PSRepository](Register-PSRepository.md)

[Select-Object](../Microsoft.PowerShell.Utility/Select-Object.md)

[Uninstall-Module](Uninstall-Module.md)

