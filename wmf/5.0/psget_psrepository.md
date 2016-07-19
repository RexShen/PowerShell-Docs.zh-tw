# 註冊 PowerShell 存放庫
您可以設定 PowerShellGet 操作內部存放庫。 做法是使用新增下列項目︰
- Register-PSRepository：為目前的使用者註冊存放庫。
- Unregister-PSRepository：移除目前使用者已註冊的存放庫。
- Set-PSRepository：為已註冊的存放庫設定值。
- Get-PSRepository：為目前的使用者取得所有已註冊的存放庫。

註冊存放庫後，您可以使用 Find-Module 和 Install-Module 搭配存放庫。

```powershell
\#Register a default repository
Register-PSRepository –Name DemoRepo –SourceLocation “https://www.myget.org/F/powershellgetdemo/api/v2” –PublishLocation “<https://www.myget.org/F/powershellgetdemo/api/v2>/package” –InstallationPolicy –Trusted

\#Get all of the registered repositories
Get-PSRepository
Name SourceLocation
---- --------------
PSGallery https://msconfiggallery.cloudapp...
DemoRepo https://www.myget.org/F/powershe...

\#Search only the new repository for modules
Find-Module -Repository DemoRepo
Repository Version Name
---------- ------- ----
DemoRepo 1.0.1 xActiveDirectory
DemoRepo 1.1.1 SomeModule

\#By default, PowerShellGet operates against all registered repositories when none is specified. In this example, the “SomeModule” module is installed from the DemoRepo.
Install-Module SomeModule

\#Removing a repository
Unregister-PSRepository DemoRepo
```

<!--HONumber=Jun16_HO4-->


