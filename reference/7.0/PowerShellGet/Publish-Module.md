---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 10/03/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/publish-module?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Publish-Module
ms.openlocfilehash: 169a286fba9f8ce266294d611437247acc71cff8
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201835"
---
# Publish-Module

## 概要
將指定的模組從本機電腦發行至線上資源庫。

## SYNTAX

### ModuleNameParameterSet (預設) 

```
Publish-Module -Name <String> [-RequiredVersion <String>] [-NuGetApiKey <String>]
 [-Repository <String>] [-Credential <PSCredential>] [-FormatVersion <Version>]
 [-ReleaseNotes <String[]>] [-Tags <String[]>] [-LicenseUri <Uri>] [-IconUri <Uri>]
 [-ProjectUri <Uri>] [-Exclude <String[]>] [-Force] [-AllowPrerelease] [-SkipAutomaticTags]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ModulePathParameterSet

```
Publish-Module -Path <String> [-NuGetApiKey <String>] [-Repository <String>]
 [-Credential <PSCredential>] [-FormatVersion <Version>] [-ReleaseNotes <String[]>]
 [-Tags <String[]>] [-LicenseUri <Uri>] [-IconUri <Uri>] [-ProjectUri <Uri>] [-Force]
 [-SkipAutomaticTags] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

此 `Publish-Module` Cmdlet 會使用 API 金鑰（儲存為資源庫中使用者設定檔的一部分），將模組發佈至以 NuGet 為基礎的線上資源庫。 您可以指定依模組名稱，或依包含模組之資料夾的路徑來發行模組。

當您依名稱指定模組時， `Publish-Module` 會發佈可透過執行所找到的第一個模組 `Get-Module -ListAvailable <Name>` 。 如果您指定要發佈之模組的最低版本，則 `Publish-Module` 會發行第一個版本大於或等於您所指定之最小版本的模組。

發行模組時需要在模組之資源庫頁面上所顯示的中繼資料。 必要的中繼資料包含模組名稱、版本、描述和作者。 雖然大部分的中繼資料都是取自模組資訊清單，但有些中繼資料必須在參數中指定 `Publish-Module` ，例如 **Tag** 、 **ReleaseNote** 、 **IconUri** 、 **ProjectUri** 和 **LicenseUri** ，因為這些參數符合以 NuGet 為基礎的資源庫中的欄位。

## 範例

### 範例1：發佈模組

在此範例中，MyDscModule 會使用 API 金鑰來指出模組擁有者的線上資源庫帳戶，以發佈至線上元件庫。 如果 MyDscModule 不是指定名稱、版本、描述和作者的有效資訊清單模組，就會發生錯誤。

```powershell
Publish-Module -Name "MyDscModule" -NuGetApiKey "11e4b435-6cb4-4bf7-8611-5162ed75eb73"
```

### 範例2：使用資源庫中繼資料發佈模組

在此範例中，MyDscModule 會使用 API 金鑰來指出模組擁有者的資源庫帳戶，以發佈至線上元件庫。 提供的額外中繼資料會顯示在資源庫中模組的網頁上。 擁有者會新增模組的兩個搜尋標記，並將其與 Active Directory 相關聯;新增簡短的發行附注。 如果 MyDscModule 不是指定名稱、版本、描述和作者的有效資訊清單模組，就會發生錯誤。

```powershell
Publish-Module -Name "MyDscModule" -NuGetApiKey "11e4b435-6cb4-4bf7-8611-5162ed75eb73" -LicenseUri "http://contoso.com/license" -Tag "Active Directory","DSC" -ReleaseNote "Updated the ActiveDirectory DSC Resources to support adding users."
```

## PARAMETERS

### -AllowPrerelease

允許標示為發行前版本的模組發佈。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ModuleNameParameterSet
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

在執行之前提示您確認 `Publish-Module` 。

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

指定有許可權可針對指定的套件提供者或來源發佈模組的使用者帳戶。

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

### -Exclude

定義要從已發行的模組中排除的檔案。

```yaml
Type: System.String[]
Parameter Sets: ModuleNameParameterSet
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
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -FormatVersion

只接受 **ValidateSet** 屬性所指定的有效值。

如需詳細資訊，請參閱 [ValidateSet 屬性聲明](/powershell/scripting/developer/cmdlet/validateset-attribute-declaration) 和 [ValidateSetAttribute](/dotnet/api/system.management.automation.validatesetattribute)。

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:
Accepted values: 2.0

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IconUri

指定模組的圖示 URL。 指定的圖示會顯示在模組的資源庫網頁上。

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

### -LicenseUri

指定您要發行之模組的授權條款 URL。

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

### -Name

指定您要發行之模組的名稱。 `Publish-Module` 在中搜尋指定的模組名稱 `$Env:PSModulePath` 。

```yaml
Type: System.String
Parameter Sets: ModuleNameParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -NuGetApiKey

指定您想要用來將模組發行至線上元件庫的 API 金鑰。 API 金鑰是線上元件庫中設定檔的一部分，而且可以在資源庫中的 [使用者帳戶] 頁面上找到。 API 金鑰是 NuGet 特有的功能。

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

### -Path

指定您要發行之模組的路徑。 此參數會接受包含模組之資料夾的路徑。

```yaml
Type: System.String
Parameter Sets: ModulePathParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ProjectUri

指定此專案之網頁的 URL。

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

### -ReleaseNotes

指定字串，其中包含您想要提供給此模組版本之使用者使用的版本資訊或批註。

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

### -Repository

指定由執行註冊之存放庫的易記名稱 `Register-PSRepository` 。 存放庫必須具有 **PublishLocation** ，這是有效的 NuGet URI。
您可以藉由執行來設定 **PublishLocation** `Set-PSRepository` 。

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

### -RequiredVersion

指定要發行之單一模組的確切版本。

```yaml
Type: System.String
Parameter Sets: ModuleNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipAutomaticTags

移除包含為標記的命令和資源。 略過自動將標記新增至模組。

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

### -Tags

將一或多個標記新增至您要發佈的模組。 範例標記包括 DesiredStateConfiguration、DSC、DSCResourceKit 或 PSModule。 以逗號分隔多個標記。

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

### -WhatIf

顯示執行時所發生的情況 `Publish-Module` 。 Cmdlet 並不會執行。

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

### System.String

### System.Management.Automation.PSCredential

## 輸出

### System.Object

## 注意

`Publish-Module` 在 Windows 7 或 Windows 2008 R2 和更新版本的 Windows 上，于 powershell 3.0 或更新版本的 PowerShell 上執行。

發行模組時需要在模組之資源庫頁面上所顯示的中繼資料。 必要的中繼資料包含模組名稱、版本、描述和作者。 大部分的中繼資料都是取自模組資訊清單，但有些中繼資料可以在參數中指定 `Publish-Module` ，例如 **Tag** 、 **ReleaseNote** 、 **IconUri** 、 **ProjectUri** 和 **LicenseUri** 。 如需詳細資訊，請參閱 [影響 POWERSHELL 資源庫 UI 的套件資訊清單值](/powershell/scripting/gallery/concepts/package-manifest-affecting-ui)。

## 相關連結

[Find-Module](Find-Module.md)

[Install-Module](Install-Module.md)

[Register-PSRepository](Register-PSRepository.md)

[Set-PSRepository](Set-PSRepository.md)

[Uninstall-Module](Uninstall-Module.md)

[Update-Module](Update-Module.md)
