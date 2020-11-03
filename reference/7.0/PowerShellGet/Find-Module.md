---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 03/11/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-module?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-Module
ms.openlocfilehash: 33b7861f4e776b992d3483b9b0776c32a88599fc
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201347"
---
# Find-Module

## 概要
在存放庫中尋找符合指定準則的模組。

## SYNTAX

### 全部

```
Find-Module [[-Name] <string[]>] [-MinimumVersion <string>] [-MaximumVersion <string>]
 [-RequiredVersion <string>] [-AllVersions] [-IncludeDependencies] [-Filter <string>]
 [-Tag <string[]>] [-Includes <string[]>] [-DscResource <string[]>] [-RoleCapability <string[]>]
 [-Command <string[]>] [-Proxy <uri>] [-ProxyCredential <pscredential>] [-Repository <string[]>]
 [-Credential <pscredential>] [-AllowPrerelease] [<CommonParameters>]
```

## DESCRIPTION

此 `Find-Module` Cmdlet 會在存放庫中尋找符合指定準則的模組。
`Find-Module` 傳回所找到的每個模組的 **PSRepositoryItemInfo** 物件。 物件可以向下傳送至 Cmdlet （例如） `Install-Module` 。

第一次 `Find-Module` 嘗試使用存放庫時，系統可能會提示您安裝更新。
如果未向 Cmdlet 註冊存放庫來源 `Register-PSRepository` ，則會傳回錯誤。

`Find-Module` 如果未使用任何參數來限制版本，則會傳回最新版本的模組。 若要取得存放庫的模組版本清單，請使用參數 **allversions 進行篩選** 。

如果指定了 **MinimumVersion** 參數， `Find-Module` 會傳回等於或大於最小值的模組版本。 如果存放庫中有較新的版本可用，則會傳回較新的版本。

如果指定了 **MaximumVersion** 參數，則 `Find-Module` 會傳回不超過所指定版本之模組的最新版本。

如果指定 **RequiredVersion** 參數，則 `Find-Module` 只會傳回與指定版本完全相符的模組版本。 `Find-Module` 搜尋所有可用的模組，因為可能會發生來源之間的名稱衝突。

下列範例使用 [PowerShell 資源庫](https://www.powershellgallery.com/) 作為唯一的已註冊存放庫。 `Get-PSRepository` 顯示已註冊的存放庫。 如果您有多個已註冊的存放庫，請使用 `-Repository` 參數來指定存放庫的名稱。

## 範例

### 範例1：依名稱尋找模組

此範例會尋找預設存放庫中的模組。

```powershell
Find-Module -Name PowerShellGet
```

```Output
Version   Name              Repository           Description
-------   ----              ----------           -----------
2.1.0     PowerShellGet     PSGallery            PowerShell module with commands for discovering...
```

此 `Find-Module` Cmdlet 會使用 **Name** 參數來指定 **PowerShellGet** 模組。

### 範例2：尋找具有類似名稱的模組

此範例使用星號 (`*`) 萬用字元來尋找具有類似名稱的模組。

```powershell
Find-Module -Name PowerShell*
```

```Output
Version   Name                            Repository    Description
-------   ----                            ----------    -----------
0.4.0     powershell-yaml                 PSGallery     Powershell module for serializing and...
2.1.0     PowerShellGet                   PSGallery     PowerShell module with commands for...
1.9       Powershell.Helper.Extension     PSGallery     # Powershell.Helper.Extension...
3.1       PowerShellHumanizer             PSGallery     PowerShell Humanizer wraps Humanizer...
4.0       PowerShellISEModule             PSGallery     a module that adds capability to the ISE
```

此 `Find-Module` Cmdlet 會使用 **Name** 參數搭配星號 (`*`) 萬用字元來尋找包含 **PowerShell** 的所有模組。

### 範例3：依最小版本尋找模組

此範例會搜尋模組的最小版本。 如果存放庫包含較新版本的模組，則會傳回較新的版本。

```powershell
Find-Module -Name PowerShellGet -MinimumVersion 1.6.5
```

```Output
Version   Name             Repository     Description
-------   ----             ----------     -----------
2.1.0     PowerShellGet    PSGallery      PowerShell module with commands for discovering...
```

此 `Find-Module` Cmdlet 會使用 **Name** 參數來指定 **PowerShellGet** 模組。 **MinimumVersion** 指定版本 **1.6.5** 。 `Find-Module` 會傳回 PowerShellGet 版本 **2.1.0** ，因為它超過最小版本，而且是最新版本。

### 範例4：依特定版本尋找模組

這個範例會傳回代表模組特定版本的物件。 如果找不到指定的版本，則會傳回錯誤。

```powershell
Find-Module -Name PowerShellGet -RequiredVersion 1.6.5
```

```Output
Version   Name             Repository     Description
-------   ----             ----------     -----------
1.6.5     PowerShellGet    PSGallery      PowerShell module with commands for discovering...
```

此 `Find-Module` Cmdlet 會使用 **Name** 參數來指定 **PowerShellGet** 模組。 **RequiredVersion** 參數指定 version **1.6.5** 。

### 範例5：在特定存放庫中尋找模組

此範例會使用存放 **庫** 參數來尋找特定存放庫中的模組。

```powershell
Find-Module -Name PowerShellGet -Repository PSGallery
```

```Output
Version   Name             Repository     Description
-------   ----             ----------     -----------
2.1.0     PowerShellGet    PSGallery      PowerShell module with commands for discovering...
```

此 `Find-Module` Cmdlet 會使用 **Name** 參數來指定 **PowerShellGet** 模組。 存放 **庫** 參數指定要搜尋 **PSGallery** 存放庫。

### 範例6：在多個存放庫中尋找模組

這個範例會使用 `Register-PSRepository` 來指定存放庫。 `Find-Module` 使用存放庫來搜尋模組。

```powershell
Register-PSRepository -Name MySource -SourceLocation https://www.myget.org/F/powershellgetdemo/
Find-Module -Name Contoso* -Repository PSGallery, MySource
```

```Output
Repository    Version   Name             Description
----------    -------   ----             -----------
PSGallery     2.0.0.0   ContosoServer    Cmdlets and DSC resources for managing Contoso Server...
MySource      1.2.0.0   ContosoClient    Cmdlets and DSC resources for managing Contoso Client...
```

`Register-PSRepository`Cmdlet 會註冊新的存放庫。 **Name** 參數會指派名稱 **MySource** 。 **SourceLocation** 參數會指定存放庫的位址。

此 `Find-Module` Cmdlet 會使用 **Name** 參數搭配星號 (`*`) 萬用字元來指定 **Contoso** 模組。 存放 **庫** 參數指定要搜尋兩個儲存機制： **PSGallery** 和 **MySource** 。

### 範例7：尋找包含 DSC 資源的模組

此命令會傳回包含 DSC 資源的模組。 **Include** 參數有四個預先定義的功能，可用來搜尋存放庫。 使用 tab 鍵完成以顯示 **包含** 參數所支援的四項功能。

```powershell
Find-Module -Repository PSGallery -Includes DscResource
```

```Output
Version     Name                            Repository    Description
-------     ----                            ----------    -----------
2.7.0       Carbon                          PSGallery     Carbon is a PowerShell module...
8.5.0.0     xPSDesiredStateConfiguration    PSGallery     The xPSDesiredStateConfiguration module...
1.3.1       PackageManagement               PSGallery     PackageManagement (a.k.a. OneGet) is...
2.7.0.0     xWindowsUpdate                  PSGallery     Module with DSC Resources...
3.2.0.0     xCertificate                    PSGallery     This module includes DSC resources...
3.1.0.0     xPowerShellExecutionPolicy      PSGallery     This DSC resource can change the user...
```

此 `Find-Module` Cmdlet 會使用存放 **庫** 參數來搜尋存放庫 **PSGallery** 。
**Include** 參數會指定 **DscResource** ，這是參數可以在儲存機制中搜尋的功能。

### 範例8：尋找具有篩選的模組

在此範例中，若要尋找模組，會使用篩選準則來搜尋存放庫。

針對以 NuGet 為基礎的存放庫， **篩選** 參數會搜尋引數的名稱、描述和標記。

```powershell
Find-Module -Filter AppDomain
```

```Output
Version    Name              Repository           Description
-------    ----              ----------           -----------
1.0.0.0  AppDomainConfig     PSGallery            Manipulate AppDomain configuration...
1.1.0    ClassExplorer       PSGallery            Quickly search the AppDomain for classes...
```

此 `Find-Module` Cmdlet 會使用 **篩選** 參數來搜尋 **AppDomain** 的儲存機制。

## PARAMETERS

### -AllowPrerelease

包含在標記為發行前版本的結果模組中。

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AllVersions

指定要在結果中包含模組的所有版本。 您無法搭配 **MinimumVersion** 、 **MaximumVersion** 或 **RequiredVersion** 參數使用 **allversions 進行篩選** 參數。

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

指定要在模組中尋找的命令陣列。 命令可以是函數或工作流程。

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

### -Credential

指定擁有為指定的套件提供者或來源安裝模組之許可權的使用者帳戶。

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

### -DscResource

指定包含 DSC 資源之模組的名稱或部分名稱。 根據 PowerShell 慣例，當您提供多個引數時，會執行 **或** 搜尋。

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

### -Filter

根據 **PackageManagement** 提供者特定的搜尋語法來指定篩選。 針對 NuGet 模組，此參數相當於使用 [PowerShell 資源庫](https://www.powershellgallery.com/) 網站上的搜尋列來搜尋。

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

### -Includedependencies 來

指出此作業包含相依于 **Name** 參數中指定之模組的所有模組。

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

只傳回包含特定類型之 PowerShell 功能的模組。 例如，您可能只想要尋找包含 **DSCResource** 的模組。 此參數可接受的值如下：

- Cmdlet
- DscResource
- 函式
- RoleCapability

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: DscResource, Cmdlet, Function, RoleCapability

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumVersion

指定要包含在搜尋結果中的模組最大或最新版本。
無法在同一個命令中使用 **MaximumVersion** 和 **RequiredVersion** 。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MinimumVersion

指定要包含於結果中的模組最低版本。 **MinimumVersion** 和 **RequiredVersion** 無法在相同的命令中使用。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

指定要在存放庫中搜尋的模組名稱。 接受以逗號分隔的模組名稱清單。 可使用萬用字元。

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

使用存放 **庫** 參數來指定要搜尋模組的存放庫。 在註冊多個存放庫時使用。 接受以逗號分隔的存放庫清單。 若要註冊存放庫，請使用 `Register-PSRepository` 。 若要顯示已註冊的存放庫，請使用 `Get-PSRepository` 。

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

指定要包含在結果中之模組的確切版本號碼。 **RequiredVersion** 無法在與 **MinimumVersion** 或 **MaximumVersion** 相同的命令中使用。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -RoleCapability

指定角色功能的陣列。

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

### -Tag

指定標記的陣列。 範例標記包括 **DesiredStateConfiguration** 、 **DSC** 、 **DSCResourceKit** 或 **PSModule** 。

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

### System.String[]

### System.String

### System.Uri

### System.Management.Automation.PSCredential

## 輸出

### PSRepositoryItemInfo

`Find-Module` 建立可將管線向下傳送至 Cmdlet 的 **PSRepositoryItemInfo** 物件，例如 `Install-Module` 。

## 注意

此 Cmdlet 會在 powershell 5.0 或更新版本的 PowerShell、Windows 7 或 Windows 2008 R2 和更新版本的 Windows 上執行。

## 相關連結

[Get-PSRepository](Get-PSRepository.md)

[Install-Module](Install-Module.md)

[Publish-Module](Publish-Module.md)

[Save-Module](Save-Module.md)

[Uninstall-Module](Uninstall-Module.md)

[Update-Module](Update-Module.md)

[Register-PSRepository](Register-PSRepository.md)
