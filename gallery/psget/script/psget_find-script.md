# Find-Script

尋找來自線上組件庫且符合所指定準則的 PowerShell 指令檔。

## 描述

Find-Script 會探索已註冊存放庫中符合所指定準則的指令檔。
針對每個找到的指令碼，Find-Script 會傳回可選擇性地傳送至 Install-Script 以安裝指令碼的 PSRepositoryItemInfo 物件。
Find-Script Cmdlet 可讓您使用不同的搜尋準則探索指令碼檔案，例如名稱、標記、篩選、命令名稱、版本範圍、正確版本、所有版本，包括其相依性和特定或所有已註冊的存放庫。

- Find-Script 可以使用 -Command 和 -Includes 參數根據指令碼內容進行篩選。
- Find-Script 可以使用版本參數 MinimumVersion、MaximumVersion、RequiredVersion、AllVersions 進行篩選。
  - 這些參數互斥 (MinmimumVersion 和 MaximumVersion 除外)。
  - 只有不含任何萬用字元的單一指令碼名稱才允許使用這些版本參數。
  - 如果未指定 RequiredVersion 參數，Find-Script 會傳回等於或大於所指定最小版本之指令碼的最新版本，或未指定最小版本之指令碼的最新版本。 
  - 如果指定 RequiredVersion 參數，Find-Script 只會傳回完全符合所指定版本之指令碼的版本。
- Find-Script 可以使用 -Tag 參數篩選指令碼中繼資料。
- Find-Script 可以使用 -Filter 參數篩選存放庫特定的搜尋語言。
- Find-Script 可以篩選所有或部分已註冊存放庫中的指令碼。

**注意：**已註冊的 PSRepository 應該會有有效的 ScriptSourceLocation。 您可以使用 Set-PSRepository 設定 ScriptSourceLocation 值。

## Cmdlet 語法

```powershell
Get-Command -Name Find-Script -Module PowerShellGet -Syntax
```

## Cmdlet 線上說明參考資料

[Find-Script](http://go.microsoft.com/fwlink/?LinkId=619785)

## 範例命令

```powershell
# Find a script from the registered repository with ScriptSourceLocation
Find-Script Connect-AzureVM

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0        Connect-AzureVM                     PSGallery            This runbook sets up a connection to an Azure vi...

# Find multiple scripts
Find-Script -Name Connect-AzureVM, Show-Tree, Connect-O365

# Find scripts with wildcards in -Name
Find-Script -Name *Azure*

# Find all versions of a script
Find-Script -Name Connect-O365 -AllVersions

# Find a script with -MinimumVersion. 
# With MinimumVersion we can find a script whose version is greate than or equal to the specified MinimumVersion value.
Find-Script Connect-O365 -MinimumVersion 1.4

# Find a script with MaximumVersion
Find-Script -Name Connect-O365 -MaximumVersion 1.6.2

# Find a script with both MinimumVersion and MaximumVersion range.
Find-Script -Name Connect-O365 -MinimumVersion 1.1 -MaximumVersion 1.6.2

# Find a script with exact version
Find-Script -Name Connect-O365 -RequiredVersion 1.5.7

# Find a script from the specified repository
Find-Script -Name Fabrikam-ServerScript -Repository MyLocalRepo

# Find available scripts from all registered repositories
Find-Script

# Find available scripts from few registered repositories
Find-Script -Repository PSGallery, PrivatePSGallery

# Find a script along with its dependent modules and scripts
Find-Script -Name Connect-AzureVM -IncludeDependencies

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0        Connect-AzureVM                     PSGallery            This runbook sets up a connection to an Azure vi...
1.4.0      Azure                               PSGallery            Microsoft Azure PowerShell - Service Management
1.1.2      Azure.Storage                       PSGallery            Microsoft Azure PowerShell - Storage service cmd...
1.0.8      AzureRM.profile                     PSGallery            Microsoft Azure PowerShell - Profile credential ...

# Find all scripts with workflows
Find-Script -Includes Workflow

# Find all scripts with functions
Find-Script -Includes Function

# Find scripts with specific commands
Find-Script -Command Log-Message
Find-Script -Command Log-Message, Show-Tree -Includes Function
Find-Script -Command Connect-AzureVM -Includes Workflow

# Find scripts with -Filter based search. -Filter searches in description and names
Find-Script -Filter Windows
Find-Script -Filter Azure

# Find all scripts with tags O365 or Nano
Find-Script -Tag O365, Nano

# Properties of Find-Script returned object
Find-Script Show-Tree | Format-List * -Force
Name                       : Show-Tree
Version                    : 1.0.0
Type                       : Script
Description                : Script to show the layout of PowerShell namespaces (Trees) using ASCII
Author                     : Jeffrey Snover
CompanyName                : jsnover
Copyright                  : (C) Microsoft Corporation. All rights reserved.
PublishedDate              : 2/15/2016 10:15:35 PM
InstalledDate              :
UpdatedDate                :
LicenseUri                 :
ProjectUri                 :
IconUri                    :
Tags                       : {Nano, PSScript}
Includes                   : {Function, RoleCapability, Command, DscResource...}
PowerShellGetFormatVersion :
ReleaseNotes               :
Dependencies               : {}
RepositorySourceLocation   : https://www.powershellgallery.com/api/v2/
Repository                 : PSGallery
PackageManagementProvider  : NuGet
AdditionalMetadata         : {versionDownloadCount, ItemType, copyright, PackageManagementProvider...}


# Includes property on PSRepositoryItemInfo object
$t = Find-Script -Includes Workflow -Repository INT -Name Fabrikam-ClientScript
$t.Includes

Name                           Value
----                           -----
Function                       {Test-FunctionFromScript_Fabrikam-ClientScript}
RoleCapability                 {}
Command                        {Test-FunctionFromScript_Fabrikam-ClientScript, Test-WorkflowFromScript_Fabrikam-Clie...
DscResource                    {}
Workflow                       {Test-WorkflowFromScript_Fabrikam-ClientScript}
Cmdlet                         {}


```


<!--HONumber=Aug16_HO3-->


