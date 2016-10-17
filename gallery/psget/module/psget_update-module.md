# Update-Module

將來自線上組件庫之指定模組的最新版本下載並安裝至本機電腦。

## 描述

Update-Module Cmdlet 會在本機電腦上執行 Install-Module，以安裝已從線上組件庫安裝的較新 Windows PowerShell 模組版本。

除非您指定所需的版本，否則預設會安裝線上組件庫中可用指定模組的最新版本。 您可以指定模組名稱來更新現有的已安裝模組；Update-Module 會搜尋 $env:PSModulePath 中是否有您要更新的模組。

執行不含 Name 參數的 Update-Module 會更新可在本機電腦上更新的所有模組。

### 附註

- 這個 Cmdlet 會在 Windows PowerShell 3.0 或更新版本的 Windows PowerShell、Windows 7 或 Windows 2008 R2 和更新版本的 Windows 上執行。
- 如果未使用 Install-Module 來安裝利用 Name 參數所指定的模組，則會發生錯誤。 您只能在執行 Install-Module 以從線上組件庫所安裝的模組上執行 Update-Module。
- 如果 Update-Module 嘗試更新使用中的二進位檔，Update-Module 會傳回錯誤以識別問題程序，以及通知使用者在停止程序之後重試 Update-Module。
- 在 PowerShell 5.0 或更新版本上，當 Update-Module 更新模組時，會新增最新 (或指定) 版本的模組，因此新舊版本現在會並存在相同的目錄中。 這十分有用，而且可用來顯示這些命令的輸出範例。


## Cmdlet 語法
```powershell
Get-Command -Name Update-Module -Module PowerShellGet -Syntax
```

## Cmdlet 線上說明參考資料

[Update-Module](http://go.microsoft.com/fwlink/?LinkID=398576)


## 範例命令

```powershell
PS C:\\windows\\system32> Update-Module -Name ContosoServer -RequiredVersion 1.5
PS C:\\windows\\system32> Get-Module -ListAvailable -Name ContosoServer | Format-List Name,Version,ModuleBase
Name : ContosoServer
Version : 2.0
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\2.0
Name : ContosoServer
Version : 1.5
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\1.5
Name : ContosoServer
Version : 1.0
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\1.0
PS C:\\windows\\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
PS C:\\windows\\system32> Update-Module -Name ContosoServer
PS C:\\windows\\system32> Get-Module -ListAvailable -Name ContosoServer | Format-List Name,Version,ModuleBase
Name : ContosoServer
Version : 2.8.1
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\2.8.1
Name : ContosoServer
Version : 2.0
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\2.0
Name : ContosoServer
Version : 1.5
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\1.5
Name : ContosoServer
Version : 1.0
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\1.0
PS C:\\windows\\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
2.8.1 ContosoServer MSPSGallery ContosoServer module
```


###  更新具相依性的 TestDepWithNestedRequiredModules1 模組。
```powershell
Find-Module -Name TestDepWithNestedRequiredModules1 -Repository LocalRepo -AllVersions

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module

Update-Module -Name TestDepWithNestedRequiredModules1 -RequiredVersion 2.0
Get-InstalledModule

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        NestedRequiredModule1               LocalRepo   NestedRequiredModule1 module
2.5        NestedRequiredModule2               LocalRepo   NestedRequiredModule2 module
2.0        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
2.5        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
1.0        RequiredModule1                     LocalRepo   RequiredModule1 module
2.5        RequiredModule2                     LocalRepo   RequiredModule2 module
2.0        RequiredModule3                     LocalRepo   RequiredModule3 module
2.5        RequiredModule3                     LocalRepo   RequiredModule3 module
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
```

<!--HONumber=Aug16_HO3-->


