# 建立及連接到 JEA 端點
若要建立 JEA 端點，您必須建立並註冊特別設定的 PowerShell 工作階段組態檔，該組態檔可使用 **New-PSSessionConfigurationFile** Cmdlet 產生，

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -TranscriptDirectory "C:\ProgramData\JEATranscripts" -RunAsVirtualAccount -RoleDefinitions @{ 'CONTOSO\NonAdmin_Operators' = @{ RoleCapabilities = 'Maintenance' }} -Path "$env:ProgramData\JEAConfiguration\Demo.pssc" 
```

如此會建立工作階段組態檔，看起來像這樣︰ 
```powershell
@{

# Version number of the schema used for this document
SchemaVersion = '2.0.0.0'

# ID used to uniquely identify this document
GUID = 'a384fdd3-5830-4a2c-ac86-cdd1822c3afd'

# Author of this document
Author = 'Administrator'

# Description of the functionality provided by these settings
# Description = ''

# Session type defaults to apply for this session configuration. Can be 'RestrictedRemoteServer' (recommended), 'Empty', or 'Default'
SessionType = 'RestrictedRemoteServer'

# Directory to place session transcripts for this session configuration
TranscriptDirectory = 'C:\ProgramData\JEATranscripts'

# Whether to run this session configuration as the machine's (virtual) administrator account
RunAsVirtualAccount = $true

# Groups associated with machine's (virtual) administrator account
# RunAsVirtualAccountGroups = 'Remote Desktop Users', 'Remote Management Users'

# Scripts to run when applied to a session
# ScriptsToProcess = 'C:\ConfigData\InitScript1.ps1', 'C:\ConfigData\InitScript2.ps1'

# User roles (security groups), and the Role Capabilities that should be applied to them when applied to a session
RoleDefinitions = @{
    'CONTOSO\NonAdmin_Operators' = @{
        'RoleCapabilities' = 'Maintenance' } }

} 
```
建立 JEA 端點時，必須設定下列參數的命令 (和檔案中的對應金鑰)︰
1.  將 SessionType 設為 RestrictedRemoteServer
2.  將 RunAsVirtualAccount 設為 **$true**
3.  將 TranscriptPath 設為將在每個工作階段之後儲存 "Over The Shoulder" 文字記錄之目錄
4.  將 RoleDefinitions 設為定義群組與可存取之 "Role Capabilities" 對應關係的雜湊表。  此欄位會定義各種**人員**可以在此端點上執行的各種**動作**。   角色功能是特殊的檔案，將在稍後說明。


RoleDefinitions 欄位會定義群組與角色功能的存取權之對應關係。  角色功能是一個檔案，定義將向連接的使用者公開的一組功能。  您可以使用 **New-PSRoleCapabilityFile** 命令建立角色功能，

```powershell
New-PSRoleCapabilityFile -Path "$env:ProgramFiles\WindowsPowerShell\Modules\DemoModule\RoleCapabilities\Maintenance.psrc" 
```

如此將產生一種範本角色功能，看起來像這樣︰
```
@{

# ID used to uniquely identify this document
GUID = '9287a34f-3f0e-4fbe-9dd7-f1361ba9fd65'

# Author of this document
Author = 'Administrator'

# Description of the functionality provided by these settings
# Description = ''

# Company associated with this document
CompanyName = 'Unknown'

# Copyright statement for this document
Copyright = '(c) 2015 Administrator. All rights reserved.'

# Modules to import when applied to a session
# ModulesToImport = 'MyCustomModule', @{ ModuleName = 'MyCustomModule'; ModuleVersion = '1.0.0.0'; GUID = '4d30d5f0-cb16-4898-812d-f20a6c596bdf' }

# Aliases to make visible when applied to a session
# VisibleAliases = 'Item1', 'Item2'

# Cmdlets to make visible when applied to a session
# VisibleCmdlets = 'Invoke-Cmdlet1', @{ Name = 'Invoke-Cmdlet2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }

# Functions to make visible when applied to a session
# VisibleFunctions = 'Invoke-Function1', @{ Name = 'Invoke-Function2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }

# External commands (scripts and applications) to make visible when applied to a session
# VisibleExternalCommands = 'Item1', 'Item2'

# Providers to make visible when applied to a session
# VisibleProviders = 'Item1', 'Item2'

# Scripts to run when applied to a session
# ScriptsToProcess = 'C:\ConfigData\InitScript1.ps1', 'C:\ConfigData\InitScript2.ps1'

# Aliases to be defined when applied to a session
# AliasDefinitions = @{ Name = 'Alias1'; Value = 'Invoke-Alias1'}, @{ Name = 'Alias2'; Value = 'Invoke-Alias2'}

# Functions to define when applied to a session
# FunctionDefinitions = @{ Name = 'MyFunction'; ScriptBlock = { param($MyInput) $MyInput } }

# Variables to define when applied to a session
# VariableDefinitions = @{ Name = 'Variable1'; Value = { 'Dynamic' + 'InitialValue' } }, @{ Name = 'Variable2'; Value = 'StaticInitialValue' }

# Environment variables to define when applied to a session
# EnvironmentVariables = @{ Variable1 = 'Value1'; Variable2 = 'Value2' }

# Type files (.ps1xml) to load when applied to a session
# TypesToProcess = 'C:\ConfigData\MyTypes.ps1xml', 'C:\ConfigData\OtherTypes.ps1xml'

# Format files (.ps1xml) to load when applied to a session
# FormatsToProcess = 'C:\ConfigData\MyFormats.ps1xml', 'C:\ConfigData\OtherFormats.ps1xml'

# Assemblies to load when applied to a session
# AssembliesToLoad = 'System.Web', 'System.OtherAssembly, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a'

} 

```
若要供 JEA 工作階段組態使用，必須在名為 “RoleCapabilities” 的資料夾中，將角色功能儲存為有效的 PowerShell 模組。 如有需要，模組可能會有多個角色功能檔案。

若要開始設定使用者可存取的哪些 Cmdlet、函數、別名及指令碼可在連接到 JEA 工作階段時存取，請遵循註解化的範本，將您自己的規則加入角色功能檔案中。 如需深入了解如何設定角色功能，請參閱完整的[體驗指南](http://aka.ms/JEA)。

最後，當您完成自訂工作階段組態和相關角色功能後，請執行 **Register-PSSessionConfiguration** 註冊此工作階段組態並建立端點。

```powershell
Register-PSSessionConfiguration -Name Maintenance -Path "C:\ProgramData\JEAConfiguration\Demo.pssc" 
```

## 連接到 JEA 端點
連接到 JEA 端點與連接到其他 PowerShell 端點的運作方式一樣。  您只需要提供您的 JEA 端點名稱作為 **New-PSSession**、**Invoke-Command**或 **Enter-PSSession** 的 "ConfigurationName" 參數。

```powershell
Enter-PSSession -ConfigurationName Maintenance -ComputerName localhost
```
一旦您已經連接到 JEA 工作階段，將限制您可執行的命令，這些命令必須列在您可存取之角色功能中的白名單。 如果您嘗試執行任何您的角色不允許的命令，將會發生錯誤。<!--HONumber=Mar16_HO2-->
