---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/03/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-command?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-Command
ms.openlocfilehash: 1cd86a1c9abe6c8a4af9f68ed17ea1876ff1bd20
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204167"
---
# Find-Command

## 概要
尋找模組中的 PowerShell 命令。

## SYNTAX

### 全部

```
Find-Command [[-Name] <String[]>] [-ModuleName <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-RequiredVersion <String>] [-AllVersions] [-AllowPrerelease]
 [-Tag <String[]>] [-Filter <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Repository <String[]>] [<CommonParameters>]
```

## DESCRIPTION

`Find-Command`Cmdlet 會尋找 PowerShell 命令，例如 Cmdlet、別名、函式和工作流程。 `Find-Command` 搜尋已註冊存放庫中的模組。

針對所找到的每個命令 `Find-Command` ，會傳回 **PSGetCommandInfo** 物件。 **PSGetCommandInfo** 物件可以向下傳送至 `Install-Module` Cmdlet。
`Install-Module` 安裝包含命令的模組。

## 範例

### 範例 1︰在指定的存放庫中尋找所有命令

Cmdlet 會在 `Find-Command` 已註冊的存放庫中搜尋模組。

```powershell
Find-Command -Repository PSGallery | Select-Object -First 10
```

```output
Name                                Version    ModuleName          Repository
----                                -------    ----------          ----------
Disable-AzureRmDataCollection       5.8.3      AzureRM.profile     PSGallery
Disable-AzureRmContextAutosave      5.8.3      AzureRM.profile     PSGallery
Enable-AzureRmDataCollection        5.8.3      AzureRM.profile     PSGallery
Enable-AzureRmContextAutosave       5.8.3      AzureRM.profile     PSGallery
Remove-AzureRmEnvironment           5.8.3      AzureRM.profile     PSGallery
Get-AzureRmEnvironment              5.8.3      AzureRM.profile     PSGallery
Set-AzureRmEnvironment              5.8.3      AzureRM.profile     PSGallery
Add-AzureRmEnvironment              5.8.3      AzureRM.profile     PSGallery
Get-AzureRmSubscription             5.8.3      AzureRM.profile     PSGallery
Connect-AzureRmAccount              5.8.3      AzureRM.profile     PSGallery
```

`Find-Command` 使用存放 **庫** 參數來指定已註冊的存放庫名稱。 物件會向下傳送到管線。 `Select-Object` 接收物件，並使用 **第一個** 參數來顯示前10個結果。

### 範例 2︰依名稱尋找命令

`Find-Command` 可以使用命令的名稱，找出存放庫中的模組。 命令名稱有可能存在於多個 **ModuleNames** 中。

```powershell
Find-Command -Repository PSGallery -Name Get-TargetResource
```

```Output
Name                  Version    ModuleName                      Repository
----                  -------    ----------                      ----------
Get-TargetResource    3.1.0.0    xPowerShellExecutionPolicy      PSGallery
Get-TargetResource    1.0.0      xInternetExplorerHomePage       PSGallery
Get-TargetResource    1.2.0.0    SystemLocaleDsc                 PSGallery
```

`Find-Command` 使用存放 **庫** 參數來搜尋 **PSGallery** 。 **Name** 參數會指定 **get-targetresource** 命令。

### 範例3：依名稱尋找命令並安裝模組

`Find-Command` 可以找到命令和模組，然後將物件傳送至 `Install-Module` 。 如果命令包含在多個模組中，請使用 `Find-Command` Cmdlet **模組名稱** 參數。
否則，可能會安裝您不想要安裝的模組。

```powershell
PS> Find-Command -Name Get-TargetResource -Repository PSGallery -ModuleName SystemLocaleDsc |
    Install-Module

PS> Get-InstalledModule

Version   Name               Repository   Description
-------   ----               ----------   -----------
1.2.0.0   SystemLocaleDsc    PSGallery    This DSC Resource allows configuration of the Windows...
```

`Find-Command` 使用 **Name** 參數來指定 **get-targetresource** 命令。 存放 **庫** 參數會搜尋 **PSGallery** 。 **ModuleName** 參數指定您想要安裝的模組（ **SystemLocaleDsc** ）。 物件會沿著管線向下傳送 `Install-Module` ，而且會安裝模組。 安裝完成之後，您可以使用 `Get-InstalledModule` 來顯示結果。

### 範例 4︰尋找命令並儲存其模組

```
PS> Find-Command -Name Invoke-ScriptAnalyzer -Repository PSGallery | Save-Module -Path C:\Test\Modules -Verbose

VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/PSScriptAnalyzer/1.18.0'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/PSScriptAnalyzer/1.18.0'.
VERBOSE: Completed downloading 'PSScriptAnalyzer'.
VERBOSE: Module 'PSScriptAnalyzer' was saved successfully to path 'C:\Test\Modules\PSScriptAnalyzer\1.18.0'.
```

`Find-Command`使用 **名稱** 和 **儲存** 機制參數，在 **PSGallery** 存放庫中搜尋命令 **調用-ScriptAnalyzer** 。 物件會向下傳送到管線 `Save-Module` 。 **Path** 參數會決定要儲存模組的位置。 **Verbose** 是選擇性參數，但會在 PowerShell 主控台中顯示狀態輸出。 詳細資訊輸出有助於進行疑難排解。

## PARAMETERS

### -AllowPrerelease

在結果中包含標示為發行前版本的模組。

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

指出此 Cmdlet 會取得模組的所有版本。

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

根據 **PackageManagement** 提供者的搜尋語法尋找模組。 例如，在 [ **ModuleName** ] 和 [ **描述** ] 屬性中指定要搜尋的文字。

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

指定要搜尋命令的模組名稱。 預設為所有模組。

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

指定要在存放庫中搜尋的命令名稱。 使用逗號來分隔命令名稱的陣列。

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

指定具有使用 **Proxy** 參數所指定 Proxy 伺服器之權限的使用者帳戶。

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

指定要搜尋命令的存放庫。 使用逗號來分隔存放庫名稱的陣列。 預設為所有存放庫。

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

指定要包含於結果中的模組版本。

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

### PSGetCommandInfo

`Find-Command` 輸出 **PSGetCommandInfo** 物件。

## 注意

## 相關連結

[Get-InstalledModule](Get-InstalledModule.md)

[Install-Module](Install-Module.md)

[Save-Module](Save-Module.md)

[Select-Object](../Microsoft.PowerShell.Utility/Select-Object.md)

[Uninstall-Module](Uninstall-Module.md)

