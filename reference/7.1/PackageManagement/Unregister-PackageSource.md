---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 05/24/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/unregister-packagesource?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-PackageSource
ms.openlocfilehash: 7f923c3d1b35f956479abd17e14861835dc80497
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204168"
---
# Unregister-PackageSource

## 概要
移除已註冊的套件來源。

## SYNTAX

### SourceBySearch

```
Unregister-PackageSource [[-Source] <String>] [-Location <String>] [-Credential <PSCredential>]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ProviderName <String>] [<CommonParameters>]
```

### SourceByInputObject

```
Unregister-PackageSource -InputObject <PackageSource[]> [-Credential <PSCredential>] [-Force]
 [-ForceBootstrap] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### NuGet： SourceByInputObject

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### NuGet： SourceBySearch

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### PowerShellGet： SourceByInputObject

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

### PowerShellGet： SourceBySearch

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

## DESCRIPTION

此 `Unregister-PackageSource` Cmdlet 會移除註冊的套件來源。 套件來源一律受套件提供者管理。 若要尋找套件來源，請使用 `Get-PackageSource` Cmdlet。

## 範例

### 範例1：取消註冊 Nuget 提供者的套件來源

`Unregister-PackageSource`Cmdlet 會從本機電腦取消註冊封裝來源。 **Location** 和 **Provider** 參數可以用來進一步指定要移除的來源。

```
PS> Unregister-PackageSource -Source MyNuGet
```

此 `Unregister-PackageSource` Cmdlet 會使用 **source** 參數來指定要移除的來源。

### 範例2：使用 Register-packagesource 物件取消註冊封裝

這個範例會使用 `Get-PackageSource` 和 `Unregister-PackageSource` 來取消註冊封裝來源。 **Register-packagesource** 物件儲存在變數中。

```
PS> $pkgsource = Get-PackageSource -Name MyNuGet
PS> Unregister-PackageSource -InputObject $pkgsource
```

`$pkgsource`變數會儲存 Cmdlet **PackageSource** 所建立的 register-packagesource `Get-PackageSource` 。
`Unregister-PackageSource` 使用 `$pkgsource` 做為 **InputObject** 參數的輸入。

或者， `Unregister-PackageSource` Cmdlet 可以指定 **InputObject** 參數的值：

`Unregister-PackageSource -InputObject ( Get-PackageSource -Name MyNuGet )`

## PARAMETERS

### -Read-configfile

指定設定檔。

```yaml
Type: System.String
Parameter Sets: NuGet:SourceByInputObject, NuGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

指定擁有存取電腦和執行命令之許可權的使用者帳戶。 輸入使用者名稱（例如 **User01** 、 **Domain01\User01** ），或輸入由 Cmdlet 產生的 **PSCredential** 物件 `Get-Credential` 。 如果您輸入使用者名稱，系統就會提示您輸入密碼。

如果未指定 **Credential** 參數，則會使用目前的使用者帳戶。

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

強制執行命令而不要求使用者確認。 覆寫防止 `Unregister-PackageSource` 無法成功的限制，但安全性除外。

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

指出 `Unregister-PackageSource` 強制 **PackageManagement** 自動卸載指定套件來源的封裝提供者。

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

接受從 Cmdlet 指定 **register-packagesource** 物件的管線輸入 `Get-PackageSource` 。 **InputObject** 接受 **register-packagesource** 物件做為 `Get-PackageSource` 值或包含物件的變數。

```yaml
Type: Microsoft.PackageManagement.Packaging.PackageSource[]
Parameter Sets: SourceByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Location

指定封裝來源指向的位置。 此參數的值可以是 URI、檔案路徑或封裝提供者所支援的任何其他目的地格式。

```yaml
Type: System.String
Parameter Sets: SourceBySearch
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
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProviderName

指定提供者名稱。

```yaml
Type: System.String
Parameter Sets: SourceBySearch
Aliases: Provider
Accepted values: Bootstrap, NuGet, PowerShellGet

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PublishLocation

指定發行位置。

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### ->scriptpublishlocation

指定腳本發行位置。

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
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
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipValidate

略過驗證套件來源認證的參數。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:SourceByInputObject, NuGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Source

指定套件來源的易記名稱。

```yaml
Type: System.String
Parameter Sets: SourceBySearch
Aliases: Name

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

在執行之前提示您確認 `Unregister-PackageSource` 。

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

顯示執行 Cmdlet 時會發生 `Unregister-PackageSource` 的情況。 不會執行此 Cmdlet。

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

### `Unregister-PackageSource` 接受來自管線的 **register-packagesource** 物件做為輸入。

## 輸出

### `Unregister-PackageSource` 不會產生任何輸出。

## 注意

在命令中包含封裝提供者可以讓 Cmdlet 提供動態參數。 動態參數是封裝提供者專用的。 此 `Get-Help` Cmdlet 會列出 Cmdlet 的參數集，並包含提供者的參數集。

## 相關連結

[about_PackageManagement](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[Get-Credential](../Microsoft.PowerShell.Security/Get-Credential.md)

[Get-PackageSource](Get-PackageSource.md)

[Register-PackageSource](Register-PackageSource.md)

[Set-PackageSource](Set-PackageSource.md)

