# Get-PSRepository

取得電腦上的已註冊存放庫。

## 描述

Get-PSRepository Cmdlet 會取得電腦上針對目前使用者所註冊的 PowerShell 模組存放庫。

針對每個已註冊的存放庫，Get-PSRepository 會傳回 PSRepository 物件，而您可以將這個物件選擇性地傳送至 Unregister-PSRepository 來取消註冊已註冊的存放庫。

## Cmdlet 語法
```powershell
Get-Command -Name Get-PSRepository -Module PowerShellGet -Syntax
```

## Cmdlet 線上說明參考資料

[Get-PSRepository](http://go.microsoft.com/fwlink/?LinkID=517127)

## 範例命令

```powershell

# Properties of Get-PSRepository returned object
Get-PSRepository PSGallery | Format-List * -Force

Name                      : PSGallery
SourceLocation            : https://www.powershellgallery.com/api/v2/
Trusted                   : False
Registered                : True
InstallationPolicy        : Untrusted
PackageManagementProvider : NuGet
PublishLocation           : https://www.powershellgallery.com/api/v2/package/
ScriptSourceLocation      : https://www.powershellgallery.com/api/v2/items/psscript/
ScriptPublishLocation     : https://www.powershellgallery.com/api/v2/package/
ProviderOptions           : {}

# Get all registered repositories
Get-PSRepository

# Get a specific registered repository
Get-PSRepository PSGallery

Name                      InstallationPolicy   SourceLocation
----                      ------------------   --------------
PSGallery                 Untrusted            https://www.powershellgallery.com/api/v2/

# Get registered repository with wildcards
Get-PSRepository *Gallery*

```

<!--HONumber=Aug16_HO3-->


