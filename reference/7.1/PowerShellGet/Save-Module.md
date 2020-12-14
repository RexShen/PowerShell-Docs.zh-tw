---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 11/11/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/save-module?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Save-Module
ms.openlocfilehash: 9aff0ff794bea42da7690a77357c1d76f747a004
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2020
ms.locfileid: "94892152"
---
# Save-Module

## 概要
將模組及其相依性儲存在本機電腦上，但不會安裝模組。

## SYNTAX

### NameAndPathParameterSet (預設) 

```
Save-Module [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] [-Path] <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AllowPrerelease]
 [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### NameAndLiteralPathParameterSet

```
Save-Module [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] -LiteralPath <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AllowPrerelease]
 [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InputObjectAndLiteralPathParameterSet

```
Save-Module [-InputObject] <PSObject[]> -LiteralPath <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### InputObjectAndPathParameterSet

```
Save-Module [-InputObject] <PSObject[]> [-Path] <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

此 `Save-Module` Cmdlet 會從已註冊的存放庫下載模組和任何相依性。
`Save-Module` 下載並儲存模組的最新版本。 檔案會儲存至本機電腦上的指定路徑。 未安裝此模組，但內容可供系統管理員進行檢查。 然後可以將儲存的模組複製到 `$env:PSModulePath` 離線電腦的適當位置。

`Get-PSRepository` 顯示本機電腦的已註冊存放庫。 您可以使用 `Find-Module` Cmdlet 來搜尋已註冊的存放庫。

## 範例

### 範例1：儲存模組

在此範例中，模組和其相依性會儲存至本機電腦。

```powershell
Save-Module -Name PowerShellGet -Path C:\Test\Modules -Repository PSGallery
Get-ChildItem -Path C:\Test\Modules
```

```Output
    Directory: C:\Test\Modules

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         7/1/2019     13:31                PackageManagement
d-----         7/1/2019     13:31                PowerShellGet
```

`Save-Module` 使用 **Name** 參數來指定模組（ **PowerShellGet**）。 **Path** 參數指定要儲存已下載模組的位置。 存放 **庫** 參數會指定已註冊的存放庫 **PSGallery**。 下載完成之後，會 `Get-ChildItem` 顯示儲存檔案的 **路徑** 內容。

### 範例2：儲存特定版本的模組

此範例示範如何使用參數（例如 **MaximumVersion** 或 **RequiredVersion** ）來指定模組版本。

```powershell
Save-Module -Name PowerShellGet -Path C:\Test\Modules -Repository PSGallery -MaximumVersion 2.1.0
Get-ChildItem -Path C:\Test\Modules\PowerShellGet\
```

```Output
    Directory: C:\Test\Modules\PowerShellGet

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         7/1/2019     13:40                2.1.0
```

`Save-Module` 使用 **Name** 參數來指定模組（ **PowerShellGet**）。 **Path** 參數指定要儲存已下載模組的位置。 存放 **庫** 參數會指定已註冊的存放庫 **PSGallery**。 **MaximumVersion** 指定下載並儲存版本 **2.1.0** 。 下載完成之後，會 `Get-ChildItem` 顯示儲存檔案的 **路徑** 內容。

### 範例3：尋找並儲存特定版本的模組

在此範例中，在存放庫中找到必要的模組版本，並儲存到本機電腦。

```powershell
Find-Module -Name PowerShellGet -Repository PSGallery -RequiredVersion 1.6.5 |
  Save-Module -Path C:\Test\Modules
Get-ChildItem -Path C:\Test\Modules\PowerShellGet
```

```Output
    Directory: C:\Test\Modules\PowerShellGet

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         7/1/2019     14:04                1.6.5
```

`Find-Module` 使用 **Name** 參數來指定模組（ **PowerShellGet**）。 存放 **庫** 參數會指定已註冊的存放庫 **PSGallery**。 **RequiredVersion** 指定版本 **1.6.5**。

物件會向下傳送到管線 `Save-Module` 。 **Path** 參數指定要儲存已下載模組的位置。 下載完成之後，會 `Get-ChildItem` 顯示儲存檔案的 **路徑** 內容。

## PARAMETERS

### -AcceptLicense

如果套件需要，則自動接受授權合約。

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

可讓您儲存標記為發行前版本的模組。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

在執行之前提示您確認 `Save-Module` 。

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

指定有權儲存模組的使用者帳戶。

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

強制 `Save-Module` 執行而不要求使用者確認。

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

接受 **PSRepositoryItemInfo** 物件。 例如，輸出 `Find-Module` 到變數，並使用該變數作為 **InputObject** 引數。

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: InputObjectAndLiteralPathParameterSet, InputObjectAndPathParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -LiteralPath

指定一個或多個位置的路徑。 **LiteralPath** 參數的值會完全依照輸入的方式使用。 沒有字元會被視為萬用字元。 如果路徑包含 escape 字元，請用單引號括住。 PowerShell 不會將以單引號括住的任何字元視為 escape 序列來解讀。

```yaml
Type: System.String
Parameter Sets: NameAndLiteralPathParameterSet, InputObjectAndLiteralPathParameterSet
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MaximumVersion

指定要儲存之模組的最大或最新版本。 在相同的命令中不能使用 **MaximumVersion** 和 **RequiredVersion** 參數。

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MinimumVersion

指定要儲存之單一模組的最小版本。 如果您嘗試安裝多個模組，就無法新增此參數。 **MinimumVersion** 和 **RequiredVersion** 參數無法在相同的命令中使用。

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

指定要儲存的模組名稱陣列。

```yaml
Type: System.String[]
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

指定本機電腦上儲存已儲存模組的位置。 接受萬用字元。

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, InputObjectAndPathParameterSet
Aliases:

Required: True
Position: 1
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

指定由執行註冊之存放庫的易記名稱 `Register-PSRepository` 。 用 `Get-PSRepository` 來顯示已註冊的存放庫。

```yaml
Type: System.String[]
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -RequiredVersion

指定要儲存之模組的確切版本號碼。

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -WhatIf

顯示執行時所發生的情況 `Save-Module` 。 不會執行此 Cmdlet。

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

### 管理. PSObject []

### System.String

### System.Uri

### System.Management.Automation.PSCredential

## 輸出

### System.Object

## 注意

> [!IMPORTANT]
> 從2020年4月起，PowerShell 資源庫不再支援傳輸層安全性 (TLS) 1.0 和1.1 版。 如果您不是使用 TLS 1.2 或更高版本，當您嘗試存取 PowerShell 資源庫時，將會收到錯誤。 使用下列命令，以確保您使用的是 TLS 1.2：
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> 如需詳細資訊，請參閱 PowerShell blog 中的 [公告](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) 。

## 相關連結
