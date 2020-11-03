---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/install-packageprovider?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-PackageProvider
ms.openlocfilehash: ed69b50019b3393eeeda42a250d65d4dfb809a51
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204179"
---
# Install-PackageProvider

## 概要
安裝一或多個套件管理封裝提供者。

## SYNTAX

### PackageBySearch (預設) 

```
Install-PackageProvider [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Credential <PSCredential>] [-Scope <String>] [-Source <String[]>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### PackageByInputObject

```
Install-PackageProvider [-Scope <String>] [-InputObject] <SoftwareIdentity[]> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION

**Install-packageprovider** 指令程式會安裝符合的套件管理提供者，這些提供者可在以 **PowerShellGet** 註冊的套件來源中使用。
根據預設，這包括可在 PowerShell 資源庫中使用 **PackageManagement** 標記的模組。
**PowerShellGet** 套件管理提供者是用來尋找這些存放庫中的提供者。

此 Cmdlet 也會安裝可使用套件管理啟動載入應用程式所提供的相符套件管理提供者。

此 Cmdlet 也會安裝可在套件管理 Azure Blob 存放區中取得的相符套件管理提供者。
使用啟動載入器提供者來尋找並安裝它們。

為了第一次執行，PackageManagement 需要有網際網路連線，才能下載 Nuget 套件提供者。
但是，如果您的電腦沒有網際網路連線，而且您需要使用 Nuget 或 PowerShellGet 提供者，您可以在另一部電腦上下載它們，然後將它們複製到目的電腦。
使用下列步驟執行這項作業：

1.
執行 `Install-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201 -Force` 以從具有網際網路連線的電腦安裝提供者。

2.
安裝之後，您可以在或中找到安裝的提供者 `$env:ProgramFiles\PackageManagement\ReferenceAssemblies\\\<ProviderName\>\\\<ProviderVersion\>` `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\\\<ProviderName\>\\\<ProviderVersion\>` 。

3.
將 \<ProviderName\> 資料夾（在此案例中為 Nuget 資料夾）放在目的電腦上的對應位置。
如果您的目的電腦是 Nano 伺服器，您需要從 Nano Server 執行 **安裝 install-packageprovider** ，以下載正確的 Nuget 二進位檔。

4.
重新開機 PowerShell 以自動載入封裝提供者。
或者，執行 `Get-PackageProvider -ListAvailable` 以列出電腦上所有可用的封裝提供者。
然後使用 `Import-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201` 將提供者匯入至目前的 PowerShell 會話。

## 範例

### 範例1：從 PowerShell 資源庫安裝套件提供者

```
PS C:\> Install-PackageProvider -Name "Gistprovider" -Verbose
```

此命令會從 PowerShell 資源庫安裝 >gistprovider。

### 範例2：安裝特定版本的套件提供者

```
PS C:\> Find-PackageProvider -Name "Nuget" -AllVersions
PS C:\> Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.216" -Force
```

此範例會安裝指定版本的 Nuget 封裝提供者。

第一個命令會尋找名為 Nuget 的所有套件提供者版本。
第二個命令會安裝指定版本的 Nuget 封裝提供者。

### 範例3：尋找提供者並加以安裝

```
PS C:\> Find-PackageProvider -Name "Gistprovider" | Install-PackageProvider -Verbose
```

此命令會使用 **尋找 install-packageprovider** 和管線來搜尋 Gist 提供者，並加以安裝。

### 範例4：將提供者安裝到目前使用者的模組資料夾

```
PS C:\> Install-PackageProvider -Name Gistprovider -Verbose -Scope CurrentUser
```

此命令會將封裝提供者安裝至 $env： Localappdata\packagemanagement\providerassemblies 有舊版，如此一來，只有目前的使用者可以使用它。

## PARAMETERS

### -AllVersions

指出此 Cmdlet 會安裝所有可用版本的封裝提供者。
根據預設， **安裝-install-packageprovider** 只會傳回最高可用版本。

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

### -Credential

指定具有安裝套件提供者權限的使用者帳戶。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

指出此 Cmdlet 會使用可強制執行的這個 Cmdlet 來強制執行所有動作。
目前，這表示 *Force* 參數的作用與 *ForceBootstrap* 參數相同。

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

指示此 Cmdlet 會自動安裝套件提供者。

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

指定 **SoftwareIdentity** 物件。
使用 **install-packageprovider** Cmdlet 取得 **SoftwareIdentity** 物件，以輸送到 **install-packageprovider** 。

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

### -MaximumVersion

指定您想要安裝的套件提供者所允許的最大版本。
如果您未新增此參數， **install-packageprovider** 會安裝提供者的最高可用版本。

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

指定您想要安裝的套件提供者所允許的最低版本。
如果您未新增此參數， **install-packageprovider** 會安裝套件的最高可用版本，同時也會滿足 *MaximumVersion* 參數所指定的任何需求。

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

指定一或多個封裝提供者模組名稱。
以逗號分隔多個封裝名稱。
不支援萬用字元。

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

### -Proxy

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

### -RequiredVersion

指定您想要安裝之封裝提供者的確切允許版本。
如果您未新增此參數，則 **install-packageprovider** 會安裝提供者的最高可用版本，同時也會滿足 *MaximumVersion* 參數所指定的最大版本。

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

### -Scope

指定提供者的安裝範圍。
此參數可接受的值為： **AllUsers** 和 **CurrentUser** 。

**AllUsers** 範圍會將提供者安裝在可供電腦的所有使用者存取的位置。
根據預設，這是 **$env:P rogramfiles\packagemanagement\providerassemblies.**

**CurrentUser** 範圍會將提供者安裝在只能由目前使用者存取的位置。
根據預設，這是 **$env： LOCALAPPDATA\PackageManagement\ProviderAssemblies.**

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

### -Source

指定一或多個套件來源。
使用 Get-PackageSource Cmdlet 取得可用套件來源的清單。

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

顯示執行 Cmdlet 後會發生的情況。
Cmdlet 並不會執行。

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

### SoftwareIdentity。

您可以使用管線將 **SoftwareIdentity** 物件傳送至此 Cmdlet。
使用 Find-PackageProvider 取得可輸送至 **安裝-install-packageprovider** 的 **SoftwareIdentity** 物件。

## 輸出

## 注意

## 相關連結

[Find-PackageProvider](Find-PackageProvider.md)

[Get-PackageProvider](Get-PackageProvider.md)

[Import-PackageProvider](Import-PackageProvider.md)

