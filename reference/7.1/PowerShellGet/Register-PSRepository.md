---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/register-psrepository?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-PSRepository
ms.openlocfilehash: 300d3388c39a86cb732d50404ad7d8c28bd3034e
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2020
ms.locfileid: "94892186"
---
# Register-PSRepository

## 概要
註冊 PowerShell 存放庫。

## SYNTAX

### NameParameterSet (預設值)

```
Register-PSRepository [-Name] <String> [-SourceLocation] <Uri> [-PublishLocation <Uri>]
 [-ScriptSourceLocation <Uri>] [-ScriptPublishLocation <Uri>] [-Credential <PSCredential>]
 [-InstallationPolicy <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-PackageManagementProvider <String>] [<CommonParameters>]
```

### PSGalleryParameterSet

```
Register-PSRepository [-Default] [-InstallationPolicy <String>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [<CommonParameters>]
```

## DESCRIPTION

此 `Register-PSRepository` Cmdlet 會註冊 PowerShell 模組的預設存放庫。 註冊存放庫之後，您可以從 `Find-Module` 、和 Cmdlet 參考它 `Install-Module` `Publish-Module` 。 已註冊的存放庫會成為和中的預設存放庫 `Find-Module` `Install-Module` 。

已註冊的存放庫是使用者特有的。 它們並未註冊在整個系統內容中。

每個已註冊的存放庫都會與 OneGet 封裝提供者相關聯，該提供者會使用 **PackageManagementProvider** 參數來指定。 每個 OneGet 提供者都是設計來與特定類型的存放庫互動。 例如，NuGet 提供者是設計來與以 NuGet 為基礎的存放庫互動。 如果在註冊期間未指定 OneGet 提供者，PowerShellGet 會嘗試尋找可處理指定來源位置的 OneGet 提供者。

## 範例

### 範例1：註冊存放庫

```powershell
$parameters = @{
  Name = "myNuGetSource"
  SourceLocation = "https://www.myget.org/F/powershellgetdemo/api/v2"
  PublishLocation = "https://www.myget.org/F/powershellgetdemo/api/v2/Packages"
  InstallationPolicy = 'Trusted'
}
Register-PSRepository @parameters
Get-PSRepository
```

```Output
Name                SourceLocation          OneGetProvider       InstallationPolicy
----                --------------          --------------       ------------------
PSGallery           http://go.micro...      NuGet                Untrusted
myNuGetSource       https://myget.c...      NuGet                Trusted
```

第一個命令會註冊 `https://www.myget.org/F/powershellgetdemo/` 為目前使用者的存放庫。 註冊 myNuGetSource 之後，您可以在搜尋、安裝和發佈模組時明確參考它。 因為未指定 **PackageManagementProvider** 參數，所以儲存機制未明確與 OneGet 封裝提供者相關聯，因此 PowerShellGet 會輪詢可用的套件提供者，並將它與 NuGet 提供者產生關聯。

第二個命令會取得已註冊的存放庫，並顯示結果。

## PARAMETERS

### -Credential

指定有權註冊存放庫之帳戶的認證。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Default

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PSGalleryParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### ->installationpolicy

指定安裝原則。 有效的值為：信任、不受信任。 預設值為 [不受信任]。

存放庫的安裝原則會指定從該存放庫安裝時的 PowerShell 行為。 從不受信任的存放庫安裝模組時，系統會提示使用者進行確認。

您可以使用 Cmdlet 來設定 >installationpolicy `Set-PSRepository` 。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Trusted, Untrusted

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

指定要註冊的儲存機制名稱。 您可以使用這個名稱來指定 Cmdlet 中的儲存機制，例如 `Find-Module` 和 `Install-Module` 。

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PackageManagementProvider

指定 OneGet 封裝提供者。 如果您未指定此參數的值，PowerShellGet 會輪詢可用的封裝提供者，並將此存放庫與第一個表示它可以處理存放庫的封裝提供者產生關聯。

```yaml
Type: System.String
Parameter Sets: NameParameterSet
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

### -PublishLocation

指定發佈位置的 URI。 例如，針對以 NuGet 為基礎的存放庫，發佈位置類似于 `https://someNuGetUrl.com/api/v2/Packages` 。

```yaml
Type: System.Uri
Parameter Sets: NameParameterSet
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
Type: System.Uri
Parameter Sets: NameParameterSet
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
Type: System.Uri
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SourceLocation

指定從這個存放庫探索和安裝模組的 URI。 URI 可以是 NuGet 伺服器摘要， (最常見的情況) 、HTTP、HTTPS、FTP 或檔案位置。

例如，針對以 NuGet 為基礎的存放庫，來源位置類似于 `https://someNuGetUrl.com/api/v2` 。

```yaml
Type: System.Uri
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.Management.Automation.PSCredential

### System.Uri

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

[Get-PSRepository](Get-PSRepository.md)

[Set-PSRepository](Set-PSRepository.md)

[Unregister-PSRepository](Unregister-PSRepository.md)
