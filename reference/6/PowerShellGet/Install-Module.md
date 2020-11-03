---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 08/03/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/install-module?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-Module
ms.openlocfilehash: 67d68427ba8e3c305b50ccbc19c6d48d574e3351
ms.sourcegitcommit: 4fc8cf397cb725ae973751d1d5d542f34f0db2d7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2020
ms.locfileid: "93205839"
---
# Install-Module

## 概要
從存放庫下載一或多個模組，並將它們安裝在本機電腦上。

## SYNTAX

### NameParameterSet (預設值)

```
Install-Module [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] [-Credential <PSCredential>] [-Scope <String>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllowClobber] [-SkipPublisherCheck] [-Force]
 [-AllowPrerelease] [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InputObject

```
Install-Module [-InputObject] <PSObject[]> [-Credential <PSCredential>] [-Scope <String>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllowClobber] [-SkipPublisherCheck] [-Force]
 [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

此 `Install-Module` Cmdlet 會從線上存放庫中取得一或多個符合指定準則的模組。 此 Cmdlet 會確認搜尋結果是有效的模組，並將模組資料夾複製到安裝位置。 安裝後不會自動匯入已安裝的模組。
您可以根據指定模組的最小值、最大值和確切版本，篩選要安裝的模組。

如果要安裝的模組具有相同的名稱或版本，或包含現有模組中的命令，則會顯示警告訊息。 在您確認要安裝模組並覆寫警告之後，請使用 `-Force` 和 `-AllowClobber` 參數。 根據您的存放庫設定，您可能需要回答提示，讓模組安裝繼續進行。

這些範例會使用 [PowerShell 資源庫](https://www.powershellgallery.com/) 作為唯一的已註冊存放庫。 `Get-PSRepository` 顯示已註冊的存放庫。 如果您有多個已註冊的存放庫，請使用 `-Repository` 參數來指定存放庫的名稱。

## 範例

### 範例1：尋找並安裝模組

此範例會尋找存放庫中的模組，並安裝該模組。

```powershell
Find-Module -Name PowerShellGet | Install-Module
```

會 `Find-Module` 使用 **Name** 參數來指定 **PowerShellGet** 模組。 根據預設，會從存放庫下載最新版本的模組。 物件會向下傳送至 `Install-Module` Cmdlet。 `Install-Module` 為中的所有使用者安裝模組 `$env:ProgramFiles\PowerShell\Modules` 。

### 範例2：依名稱安裝模組

在此範例中，會安裝最新版本的 **PowerShellGet** 模組。

```powershell
Install-Module -Name PowerShellGet
```

會 `Install-Module` 使用 **Name** 參數來指定 **PowerShellGet** 模組。 根據預設，會從存放庫下載最新版本的模組並安裝。

### 範例3：使用最小版本來安裝模組

在此範例中，會安裝 **PowerShellGet** 模組的最小版本。 **MinimumVersion** 參數指定應安裝的模組最低版本。 如果有較新版本的模組可供使用，則會為所有使用者下載並安裝該版本。

```powershell
Install-Module -Name PowerShellGet -MinimumVersion 2.0.1
```

會 `Install-Module` 使用 **Name** 參數來指定 **PowerShellGet** 模組。 **MinimumVersion** 參數指定從存放庫下載 **2.0.1** 版，並安裝該版本。 因為版本 **2.0.4 版** 可用，所以會為所有使用者下載並安裝該版本。

### 範例4：安裝特定版本的模組

在此範例中，會安裝特定版本的 **PowerShellGet** 模組。

```powershell
Install-Module -Name PowerShellGet -RequiredVersion 2.0.0
```

會 `Install-Module` 使用 **Name** 參數來指定 **PowerShellGet** 模組。 **RequiredVersion** 參數指定為所有使用者下載並安裝版本 **2.0.0** 。

### 範例5：僅針對目前的使用者安裝模組

此範例會下載並安裝最新版本的模組，僅適用于目前的使用者。

```powershell
Install-Module -Name PowerShellGet -Scope CurrentUser
```

會 `Install-Module` 使用 **Name** 參數來指定 **PowerShellGet** 模組。
`Install-Module` 將最新版本的 **PowerShellGet** 下載並安裝到目前使用者的目錄中 `$home\Documents\PowerShell\Modules` 。

## PARAMETERS

### -AcceptLicense

針對需要授權的模組， **AcceptLicense** 會在安裝期間自動接受授權合約。 如需詳細資訊，請參閱 [要求接受授權的模組](/powershell/scripting/gallery/concepts/module-license-acceptance)。

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

### -AllowClobber

覆寫有關電腦上現有命令之安裝衝突的警告訊息。
覆寫現有的命令，其名稱與模組所安裝的命令相同。
**AllowClobber** 和 **Force** 可以在命令中一起使用 `Install-Module` 。

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

### -AllowPrerelease

可讓您安裝標示為發行前版本的模組。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

在執行 Cmdlet 前提示您確認 `Install-Module` 。

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

### -Force

安裝模組並覆寫有關模組安裝衝突的警告訊息。 如果電腦上已有相同名稱的模組，則 **強制** 允許安裝多個版本。 如果有現有的模組具有相同的名稱和版本，請 **強制** 覆寫該版本。 **Force** 和 **AllowClobber** 可以在命令中一起使用 `Install-Module` 。

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

用於管線輸入。

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -MaximumVersion

指定要安裝之單一模組的最大版本。 安裝的版本必須小於或等於 **MaximumVersion** 。 如果您想要安裝多個模組，則不能使用 **MaximumVersion** 。 無法在同一個命令中使用 **MaximumVersion** 和 **RequiredVersion** `Install-Module` 。

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MinimumVersion

指定要安裝之單一模組的最小版本。 安裝的版本必須大於或等於 **MinimumVersion** 。 如果有較新版本的模組可供使用，則會安裝較新的版本。 如果您想要安裝多個模組，則無法使用 **MinimumVersion** 。
**MinimumVersion** 和 **RequiredVersion** 無法在相同的命令中使用 `Install-Module` 。

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

指定要從線上元件庫安裝的確切模組名稱。 接受以逗號分隔的模組名稱清單。 模組名稱必須符合存放庫中的模組名稱。 用 `Find-Module` 來取得模組名稱的清單。

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
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

使用存放 **庫** 參數來指定要用來下載及安裝模組的存放庫。 在註冊多個存放庫時使用。 在命令中指定已註冊存放庫的名稱 `Install-Module` 。 若要註冊存放庫，請使用 `Register-PSRepository` 。
若要顯示已註冊的存放庫，請使用 `Get-PSRepository` 。

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequiredVersion

指定要安裝之單一模組的確切版本。 如果指定版本的存放庫中沒有相符的，則會顯示錯誤。 如果您想要安裝多個模組，則無法使用 **RequiredVersion** 。 **RequiredVersion** 無法在與 `Install-Module` **MinimumVersion** 或 **MaximumVersion** 相同的命令中使用。

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Scope

指定模組的安裝範圍。 此參數可接受的值為 **AllUsers** 和 **CurrentUser** 。

**AllUsers** 範圍會在可供電腦的所有使用者存取的位置中安裝模組：

`$env:ProgramFiles\PowerShell\Modules`

**CurrentUser** 會將模組安裝在只能供電腦目前使用者存取的位置。 例如：

`$home\Documents\PowerShell\Modules`

未定義 **範圍** 時，會根據 PowerShellGet 版本設定預設值。

- 在 PowerShellGet 版本2.0.0 和更新版本中，預設值為 **CurrentUser** ，不需要提高安裝的許可權。
- 在 PowerShellGet 1.x 版中，預設值為 **AllUsers** ，這需要提高安裝的許可權。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipPublisherCheck

可讓您安裝已存在於電腦上的較新版本模組。 例如，當現有的模組由受信任的發行者以數位方式簽署，但新版本未由受信任的發行者進行數位簽署。

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

### -WhatIf

顯示命令執行時所發生的情況 `Install-Module` 。 Cmdlet 並不會執行。

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

### PSRepositoryItemInfo

`Find-Module` 建立可以向下傳送到管線的 **PSRepositoryItemInfo** 物件 `Install-Module` 。

### System.String[]

### 管理. PSObject []

### System.String

### System.Management.Automation.PSCredential

### System.Uri

## 輸出

### PSRepositoryItemInfo。

使用 **PassThru** 參數時，會 `Install-Module` 輸出模組的 **PSRepositoryItemInfo** 物件。 這是您從 Cmdlet 取得的相同資訊 `Find-Module` 。

## 注意

`Install-Module` 在 Windows 7 或 Windows 2008 R2 和更新版本的 Windows 上，于 PowerShell 5.0 或更新版本上執行。

安全性最佳作法是在第一次執行任何 Cmdlet 或函式之前，先評估模組的程式碼。 為了避免執行包含惡意程式碼的模組，安裝之後不會自動匯入已安裝的模組。

如果存放庫中沒有 **名稱** 參數所指定的模組名稱，則會傳回 `Install-Module` 錯誤。

若要安裝多個模組，請使用 **Name** 參數，並指定以逗號分隔的模組名稱陣列。 如果您指定多個模組名稱，則無法使用 **MinimumVersion** 、 **MaximumVersion** 或 **RequiredVersion** 。 `Find-Module` 建立可以向下傳送到管線的 **PSRepositoryItemInfo** 物件 `Install-Module` 。 管線是另一種方式，可指定要在單一命令中安裝的多個模組。

根據預設，會將 **AllUsers** 範圍的模組安裝在中 `$env:ProgramFiles\PowerShell\Modules` 。 當您安裝 PowerShell Desired State Configuration (DSC) 資源時，預設值會造成混淆。

模組安裝失敗，而且如果 `.psm1` `.psd1` 資料夾內沒有相同名稱的、或，則無法匯入 `.dll` 。 使用 **Force** 參數來安裝模組。

如果現有模組的版本符合 **name** 參數所指定的名稱，且未使用 **MinimumVersion** 或 **RequiredVersion** 參數，則會以 `Install-Module` 無訊息模式繼續，但不會安裝模組。

如果現有模組的版本大於 **MinimumVersion** 參數的值，或等於 **RequiredVersion** 參數的值，則會以 `Install-Module` 無訊息模式繼續，但不會安裝模組。

如果現有的模組與 **MinimumVersion** 或 **RequiredVersion** 參數所指定的值不相符，則命令中會發生錯誤 `Install-Module` 。 例如，如果現有已安裝模組的版本低於 **MinimumVersion** 值，或不等於 **RequiredVersion** 值。

模組安裝也會安裝模組發行者所需的任何相依模組。
發行者會在模組資訊清單中指定所需的模組及其版本。

## 相關連結

[Find-Module](Find-Module.md)

[Get-PSRepository](Get-PSRepository.md)

[Import-Module](../Microsoft.PowerShell.Core/Import-Module.md)

[Publish-Module](Publish-Module.md)

[Register-PSRepository](Register-PSRepository.md)

[Uninstall-Module](Uninstall-Module.md)

[Update-Module](Update-Module.md)

[about_Module](../Microsoft.PowerShell.Core/About/about_Modules.md)
