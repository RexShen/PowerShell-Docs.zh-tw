---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/get-packageprovider?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PackageProvider
ms.openlocfilehash: 66a6bfeda557894e224753018ff9087de9887cc7
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2020
ms.locfileid: "94892844"
---
# Get-PackageProvider

## 概要
傳回連接到套件管理的封裝提供者清單。

## SYNTAX

```
Get-PackageProvider [[-Name] <String[]>] [-ListAvailable] [-Force] [-ForceBootstrap] [<CommonParameters>]
```

## DESCRIPTION
**Install-packageprovider** 指令程式會傳回連接至套件管理的封裝提供者清單。
這些提供者的範例包括 PSModule、NuGet 和 Chocolatey。
您可以根據一或多個提供者名稱的所有或部分來篩選結果。

## 範例

### 範例1：取得所有目前載入的封裝提供者

```
PS C:\> Get-PackageProvider
```

此命令會取得目前在本機電腦上載入之所有封裝提供者的清單。

### 範例2：取得所有可用的封裝提供者

```
PS C:\> Get-PackageProvider -ListAvailable
```

此命令會取得本機電腦上可用的所有封裝提供者清單。

### 範例3：動態取得封裝提供者

```
PS C:\> Get-PackageProvider -Name "Chocolatey" -ForceBootstrap
```

如果您的電腦未安裝 Chocolatey 提供者，此命令會自動安裝 Chocolatey 提供者。

## PARAMETERS

### -Force
指出此 Cmdlet 會使用可強制執行的這個 Cmdlet 來強制執行所有其他動作。
在 **install-packageprovider** 中，這表示 *Force* 參數的作用與 *ForceBootstrap* 參數相同。

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
指出此 Cmdlet 會強制套件管理自動安裝封裝提供者。

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

### -ListAvailable
取得所有已安裝的提供者。
**Install-packageprovider** 會取得 **PSModulePath** 環境變數所列路徑中的提供者，以及套件提供者元件資料夾：

**$env:P rogramFiles\PackageManagement\ProviderAssemblies * * * * $env： Localappdata\packagemanagement\providerassemblies 有舊版**

如果沒有這個參數， **install-packageprovider** 只會取得目前會話中載入的提供者。

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

### -Name
指定一或多個提供者名稱，或部分提供者名稱。
以逗號分隔多個提供者名稱。
這個參數的有效值包括您隨封裝安裝的提供者名稱;PackageManagement 隨附一組預設的提供者，包括 **PSModule** 和 **MSI** 提供者。

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

### CommonParameters
這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

## 輸出

### Install-packageprovider []

## 注意

> [!IMPORTANT]
> 從2020年4月起，PowerShell 資源庫不再支援傳輸層安全性 (TLS) 1.0 和1.1 版。 如果您不是使用 TLS 1.2 或更高版本，當您嘗試存取 PowerShell 資源庫時，將會收到錯誤。 使用下列命令，以確保您使用的是 TLS 1.2：
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> 如需詳細資訊，請參閱 PowerShell blog 中的 [公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) 。

## 相關連結

[about_PackageManagement](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[Get-PackageSource](Get-PackageSource.md)

[Register-PackageSource](Register-PackageSource.md)

[Unregister-PackageSource](Unregister-PackageSource.md)
