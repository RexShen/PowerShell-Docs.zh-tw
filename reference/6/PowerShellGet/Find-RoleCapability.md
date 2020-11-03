---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/05/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-rolecapability?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-RoleCapability
ms.openlocfilehash: 78bf8a2105da04e1a0d71185014006870183fa84
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204287"
---
# Find-RoleCapability

## 概要
尋找模組中的角色功能。

## SYNTAX

### 全部

```
Find-RoleCapability [[-Name] <String[]>] [-ModuleName <String>] [-MinimumVersion <String>] 
[-MaximumVersion <String>] [-RequiredVersion <String>] [-AllVersions] [-AllowPrerelease] 
[-Tag <String[]>] [-Filter <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] 
[-Repository <String[]>] [<CommonParameters>]
```

## DESCRIPTION

此 `Find-RoleCapability` Cmdlet 會搜尋已註冊的存放庫，以尋找 PowerShell 角色功能和模組。

針對所找到的每個角色功能 `Find-RoleCapability` ，會傳回 **PSGetRoleCapabilityInfo** 物件。 **PSGetRoleCapabilityInfo** 物件可以透過管線傳送至 `Install-Module` 或 `Save-Module` Cmdlet。

PowerShell 角色功能定義使用者可以在 (JEA) 端點的足夠系統管理中使用哪些命令和應用程式。 角色功能是由副檔名為的檔案所定義 `.psrc` 。

## 範例

### 範例1：尋找角色功能

`Find-RoleCapability` 在每個已註冊的存放庫中尋找角色功能。 若要搜尋特定的存放庫，請使用存放 **庫** 參數。

```powershell
Find-RoleCapability
```

```output
Name             Version    ModuleName     Repository
----             -------    ----------     ----------
General-Lev1     1.0        JeaExamples    PSGallery
General-Lev2     1.0        JeaExamples    PSGallery
IIS-Lev1         1.0        JeaExamples    PSGallery
IIS-Lev2         1.0        JeaExamples    PSGallery
```

### 範例2：依名稱尋找角色功能

`Find-RoleCapability` 依名稱尋找角色功能。 使用逗號來分隔名稱陣列。

```powershell
Find-RoleCapability -Name General-Lev1, IIS-Lev2
```

```output
Name             Version    ModuleName     Repository
----             -------    ----------     ----------
General-Lev1     1.0        JeaExamples    PSGallery
IIS-Lev2         1.0        JeaExamples    PSGallery
```

### 範例3：尋找並儲存角色功能的模組

`Find-RoleCapability`Cmdlet 會尋找角色功能，並將物件沿著管線向下傳送。
`Save-Module` 將角色功能的模組儲存至檔案系統。 `Get-ChildItem` 顯示模組目錄的內容。

```
PS> Find-RoleCapability -Name General-Lev1 | Save-Module -Path C:\Test\Modules

PS> Get-ChildItem -Path C:\Test\Modules\JeaExamples\1.0\

    Directory: C:\Test\Modules\JeaExamples\1.0

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----          6/4/2019    16:37                RoleCapabilities
-a----          2/5/2019    18:46           1702 CreateRegisterPSSC.ps1
-a----          2/5/2019    18:46           7656 JeaExamples.psd1
-a----         10/1/2018    08:16            595 JeaExamples.psm1
```

`Find-RoleCapability` 使用 **Name** 參數來指定 **一般 Lev1** 角色功能。
物件會向下傳送到管線。 `Save-Module` 使用檔案系統位置的 **Path** 參數來儲存模組。 儲存模組之後，請 `Get-ChildItem` 指定模組的 **路徑** ，並顯示 **JeaExamples** 模組目錄的內容。

### 範例4：尋找並安裝角色功能的模組

`Find-RoleCapability` 尋找模組並將物件沿著管線向下傳送。 `Install-Module` 安裝模組。 安裝之後，請使用 `Get-InstalledModule` 來查看結果。

```
PS> Find-RoleCapability -Name General-Lev1 | Install-Module -Verbose

VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/JeaExamples/1.0.0'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/JeaExamples/1.0.0'.
VERBOSE: Completed downloading 'JeaExamples'.
VERBOSE: InstallPackageLocal' - name='JeaExamples', version='1.0',
VERBOSE: Validating the 'JeaExamples' module contents
VERBOSE: Test-ModuleManifest successfully validated the module manifest file
VERBOSE: Module 'JeaExamples' was installed successfully to path

PS> Get-InstalledModule

Version    Name            Repository     Description
-------    ----            ----------     -----------
1.0        JeaExamples     PSGallery      Some example Jea roles for general server maintenance...
```

`Find-RoleCapability` 使用 **Name** 參數來指定 **一般 Lev1** 角色功能。
物件會向下傳送到管線。 `Install-Module` 使用 **Verbose** 參數，在安裝期間顯示狀態訊息。 安裝完成之後， `Get-InstalledModule` 輸出會確認已安裝 **JeaExamples** 模組。

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

指出此 Cmdlet 會取得模組的所有版本。 **Allversions 進行篩選** 參數會顯示模組的每個可用版本。

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

指定要包含在結果中之模組的最大版本。 無法在同一個命令中使用 **MaximumVersion** 和 **RequiredVersion** 參數。

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

指定要包含於結果中的模組最低版本。 **MinimumVersion** 和 **RequiredVersion** 參數無法在相同的命令中使用。

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

指定要在其中搜尋角色功能的模組名稱。 預設為所有模組。

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

指定角色功能的名稱。 預設值為所有角色功能。 使用逗號來分隔資源名稱的陣列。

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

指定要搜尋角色功能的存放庫。 使用逗號來分隔存放庫名稱的陣列。

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

### System.Uri

### System.Management.Automation.PSCredential

## 輸出

### PSGetRoleCapabilityInfo

Cmdlet 會傳回 `Find-RoleCapability` **PSGetRoleCapabilityInfo** 物件。

## 注意

## 相關連結

[Get-ChildItem](../Microsoft.PowerShell.Management/Get-ChildItem.md)

[Get-InstalledModule](Get-InstalledModule.md)

[Install-Module](Install-Module.md)

[New-PSRoleCapabilityFile](../Microsoft.PowerShell.Core/New-PSRoleCapabilityFile.md)

[Save-Module](Save-Module.md)
