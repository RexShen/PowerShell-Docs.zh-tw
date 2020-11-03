---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/16/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-module?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-Module
ms.openlocfilehash: e00f371b1bd9129d2463bb5a31b106d165c34f4d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202116"
---
# Update-Module

## 概要
將來自線上組件庫之指定模組的最新版本下載並安裝至本機電腦。

## SYNTAX

### 全部

```
Update-Module [[-Name] <String[]>] [-RequiredVersion <String>] [-MaximumVersion <String>]
 [-Credential <PSCredential>] [-Scope <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Force] [-AllowPrerelease] [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Update-Module`Cmdlet 會從線上元件庫安裝模組的最新版本。 安裝之前，系統會提示您確認更新。 只有安裝在本機電腦上的模組才會安裝更新 `Install-Module` 。 `Update-Module` 搜尋 `$env:PSModulePath` 已安裝的模組。

`Update-Module` 未指定參數時，會更新所有已安裝的模組。 若要指定要更新的模組，請使用 **Name** 參數。 您可以使用 **RequiredVersion** 參數來更新為模組的特定版本。

如果已安裝的模組已是最新版本，則不會更新模組。 如果在中找不到模組 `$env:PSModulePath` ，則會顯示錯誤。

若要顯示已安裝的模組，請使用 `Get-InstalledModule` 。

## 範例

### 範例 1：更新所有模組

此範例會將所有已安裝的模組更新為線上元件庫中的最新版本。

```powershell
Update-Module
```

### 範例 2：透過名稱更新模組

此範例會將特定模組更新為線上元件庫中的最新版本。

```powershell
Update-Module -Name SpeculationControl
```

`Update-Module` 使用 **Name** 參數來更新特定模組（ **SpeculationControl** ）。

### 範例3：查看 Update-Module 的執行

此範例會執行假設案例，以顯示執行時所發生的情況 `Update-Module` 。 命令不會執行。

```powershell
Update-Module -WhatIf
```

```Output
What if: Performing the operation "Update-Module" on target "Version '2.8.0' of module
  'Carbon', updating to version '2.8.1'".
What if: Performing the operation "Update-Module" on target "Version '1.0.10' of module
  'SpeculationControl', updating to version '1.0.14'".
```

`Update-Module` 使用 **WhatIf** 參數顯示如果已執行，會發生什麼事 `Update-Module` 。

### 範例 4：將模組更新至指定版本

在此範例中，模組會更新為特定版本。 版本必須存在於線上元件庫中，否則會顯示錯誤。

```powershell
Update-Module -Name SpeculationControl -RequiredVersion 1.0.14
```

`Update-Module` 使用 **Name** 參數來指定模組（ **SpeculationControl** ）。 **RequiredVersion** 參數會指定版本 **1.0.14** 。

### 範例5：不確認即更新模組

此範例不會要求確認，從線上元件庫將模組更新為最新版本。 如果已安裝模組， **Force** 參數會重新安裝模組。

```powershell
Update-Module -Name SpeculationControl -Force
```

`Update-Module` 使用 **Name** 參數來指定模組（ **SpeculationControl** ）。 **Force** 參數會更新模組，而不會要求使用者確認。

## PARAMETERS

### -AcceptLicense

如果套件需要，則會在安裝期間自動接受授權合約。

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

可讓您使用標記為發行前版本的較新模組來更新模組。

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

### -Confirm

在執行之前提示您確認 `Update-Module` 。

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

指定具有更新模組之許可權的使用者帳戶。

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

強制更新每個指定的模組，而不提示要求確認。 如果已安裝模組，請 **強制** 重新安裝模組。

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

### -MaximumVersion

指定單一模組的最新版本來更新。 如果您嘗試更新多個模組，就無法新增此參數。 無法在同一個命令中使用 **MaximumVersion** 和 **RequiredVersion** 參數。

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

指定要更新的一個或多個模組的名稱。 `Update-Module` 搜尋 `$env:PSModulePath` 要更新的模組。 如果找不到符合指定之模組名稱的相符專案 `$env:PSModulePath` ，則會發生錯誤。

模組名稱中接受萬用字元。 如果您將萬用字元新增至指定的名稱，而且找不到相符專案，則不會發生任何錯誤。

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

### -PassThru

傳回代表您正在使用之項目的物件。 根據預設，此 Cmdlet 不會產生任何輸出。

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

指定擁有使用 **proxy** 參數所指定 proxy 伺服器之許可權的使用者帳戶。

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

### -RequiredVersion

指定要將現有已安裝的模組更新至哪一個正確版本。 **RequiredVersion** 指定的版本必須存在於線上元件庫中，否則會顯示錯誤。 如果在單一命令中更新一個以上的模組，您就無法使用 **RequiredVersion** 。

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

### -Scope

指定模組的安裝範圍。 此參數可接受的值為 **AllUsers** 和 **CurrentUser** 。 如果未指定 **範圍** ，則更新會安裝在 **CurrentUser** 範圍中。

**AllUsers** 範圍需要較高的許可權，並將模組安裝在可供電腦的所有使用者存取的位置：

`$env:ProgramFiles\PowerShell\Modules`

**CurrentUser** 不需要較高的許可權，而且會將模組安裝在僅供電腦目前使用者存取的位置：

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
Default value: CurrentUser
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

顯示執行時所發生 `Update-Module` 的情況。 不會執行此 Cmdlet。

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

### System.String[]

### System.String

### System.Management.Automation.PSCredential

### System.Uri

## 輸出

### System.Object

## 注意

針對 PowerShell 6.0 版和更新版本，預設安裝範圍一律為 **CurrentUser** 。
**CurrentUser** 、的模組更新 `$home\Documents\PowerShell\Modules` 不需要較高的許可權。 **AllUsers** 、的模組更新 `$env:ProgramFiles\PowerShell\Modules` 需要較高的許可權。

`Update-Module` 在 Windows 7 或 Windows 2008 R2 和更新版本的 Windows 上，于 powershell 3.0 或更新版本的 PowerShell 上執行。

如果未使用安裝 **名稱** 參數所指定的模組 `Install-Module` ，則會發生錯誤。

您只能藉由執行， `Update-Module` 在從線上元件庫安裝的模組上執行 `Install-Module` 。

如果 `Update-Module` 嘗試更新使用中的二進位檔，則會傳回 `Update-Module` 識別問題處理常式的錯誤。 系統會在進程停止後通知使用者重試 `Update-Module` 。

## 相關連結

[Find-Module](Find-Module.md)

[Get-InstalledModule](Get-InstalledModule.md)

[Install-Module](Install-Module.md)

[Publish-Module](Publish-Module.md)

[Uninstall-Module](Uninstall-Module.md)

