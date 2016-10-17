# Set-PSRepository

Set-PSRepository 會設定已註冊存放庫的值。

## 描述

Set-PSRepository Cmdlet 會設定已註冊模組存放庫的值。

## Cmdlet 語法

```powershell
Get-Command -Name Set-PSRepository -Module PowerShellGet -Syntax
```
## Cmdlet 線上說明參考資料

[Set-PSRepository](http://go.microsoft.com/fwlink/?LinkID=517128)

## 範例命令

```powershell
PS C:\> Register-PSRepository -Name myRepository -SourceLocation "https://www.myget.org/F/powershellgetdemo/api/v2" -InstallationPolicy Trusted
PS C:\> Get-PSRepository
Name                      InstallationPolicy   SourceLocation
----                      ------------------   --------------
myRepository              Trusted              https://www.myget.org/F/powershellgetdemo/api/v2

# Set installation Policy for a repository
PS C:\> Set-PSRepository -Name myRepository -InstallationPolicy Untrusted
PS C:\> Get-PSRepository

Name                      InstallationPolicy   SourceLocation
----                      ------------------   --------------
myRepository              Untrusted            https://www.myget.org/F/powershellgetdemo/api/v2
```


### 具有指令碼共用支援的 Set-PSRepository Cmdlet

使用 Set-PSRepository Cmdlet 將 **ScriptSourceLocation** 和 **ScriptPublishLocation** 新增至 PSRepository。
```powershell
# Add script sharing locations to an existing PSRepository using Set-PSRepository object.
Set-PSRepository -Name MyGallery `
                 -ScriptSourceLocation https://MyGallery.com/api/v2/items/psscript/ `
                 -ScriptPublishLocation https://MyGallery.com/api/v2/package/

Get-PSRepository -Name GalleryINT | Format-List * -Force

Name : GalleryINT
SourceLocation : https://MyGallery.com/api/v2/
Trusted : True
Registered : True
InstallationPolicy : Trusted
PackageManagementProvider : NuGet
PublishLocation : https://MyGallery.com/api/v2/package/
ScriptSourceLocation : https://MyGallery.com/api/v2/items/psscript/
ScriptPublishLocation : https://MyGallery.com/api/v2/package/
ProviderOptions : {}

```


<!--HONumber=Aug16_HO3-->


