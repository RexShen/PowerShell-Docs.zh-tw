# Unregister-PSRepository

取消註冊存放庫。

## 描述

Unregister-PSRepository Cmdlet 會取消註冊目前使用者的存放庫。
- 企業和中斷連線的案例允許取消註冊和重新註冊 PSGallery 存放庫。
- 使用者只要執行下列命令，就可以重新註冊 PSGallery `Register-PSRepository -Default`
- 因為 PSGallery 是 Publish-Module 和 Publish-Script Cmdlet 中的預設發行存放庫，所以如果已註冊的存放庫清單中沒有 PSGallery，則會擲回錯誤。

## Cmdlet 語法

```powershell
Get-Command -Name Unregister-PSRepository -Module PowerShellGet -Syntax
```
## Cmdlet 線上說明參考資料

[Unregister-PSRepository](http://go.microsoft.com/fwlink/?LinkID=517130)

## 範例命令

```powershell
Unregister-PSRepository -Name "MyPrivateGallery"

Get-PSRepository exp | Unregister-PSRepository
```

### 企業和中斷連線的案例允許取消註冊和重新註冊 PSGallery 存放庫。
```powershell

# Unregister PSGallery repository
Unregister-PSRepository PSGallery

# Publish-Module throws an error when PSGallery is not a registered repository
Publish-Module -Name MyModule
publish-module : Unable to find repository 'PSGallery'. Use Get-PSRepository to see all available repositories. Try again after specifying a valid repository name. You can use 'Register-PSRepository -Default' to register the PSGallery repository.
At line:1 char:1
+ publish-module -name mymodule
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (PSGallery:String) [Publish-Module], ArgumentException
    + FullyQualifiedErrorId : PSGalleryNotFound,Publish-Module

# Re-register PSGallery repository
Register-PSRepository -Default
```

<!--HONumber=Aug16_HO3-->


