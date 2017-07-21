---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,設定"
ms.openlocfilehash: c3645a6ba83081bd5ac31a13af0f67f6538db22a
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="creating-and-connecting-to-a-jea-endpoint"></a><span data-ttu-id="c7400-102">建立及連接到 JEA 端點</span><span class="sxs-lookup"><span data-stu-id="c7400-102">Creating and Connecting to a JEA Endpoint</span></span>
<span data-ttu-id="c7400-103">若要建立 JEA 端點，您必須建立並註冊特別設定的 PowerShell 工作階段組態檔，該組態檔可使用 **New-PSSessionConfigurationFile** Cmdlet 產生，</span><span class="sxs-lookup"><span data-stu-id="c7400-103">To create a JEA endpoint, you need to create and register a specially-configured PowerShell Session Configuration file, which can be generated with the **New-PSSessionConfigurationFile** cmdlet.</span></span>

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -TranscriptDirectory "C:\ProgramData\JEATranscripts" -RunAsVirtualAccount -RoleDefinitions @{ 'CONTOSO\NonAdmin_Operators' = @{ RoleCapabilities = 'Maintenance' }} -Path "$env:ProgramData\JEAConfiguration\Demo.pssc" 
```

<span data-ttu-id="c7400-104">如此會建立工作階段組態檔，看起來像這樣︰</span><span class="sxs-lookup"><span data-stu-id="c7400-104">This will create a session configuration file that looks like this:</span></span> 
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
<span data-ttu-id="c7400-105">建立 JEA 端點時，必須設定下列參數的命令 (和檔案中的對應金鑰)︰</span><span class="sxs-lookup"><span data-stu-id="c7400-105">When creating a JEA endpoint, the following parameters of the command (and corresponding keys in the file) must be set:</span></span>
1.  <span data-ttu-id="c7400-106">將 SessionType 設為 RestrictedRemoteServer</span><span class="sxs-lookup"><span data-stu-id="c7400-106">SessionType to RestrictedRemoteServer</span></span>
2.  <span data-ttu-id="c7400-107">將 RunAsVirtualAccount 設為 **$true**</span><span class="sxs-lookup"><span data-stu-id="c7400-107">RunAsVirtualAccount to **$true**</span></span>
3.  <span data-ttu-id="c7400-108">將 TranscriptPath 設為將在每個工作階段之後儲存 "Over The Shoulder" 文字記錄之目錄</span><span class="sxs-lookup"><span data-stu-id="c7400-108">TranscriptPath to the directory where “over the shoulder” transcripts will be saved after each session</span></span>
4.  <span data-ttu-id="c7400-109">將 RoleDefinitions 設為定義群組與可存取之 "Role Capabilities" 對應關係的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="c7400-109">RoleDefinitions to a hashtable that defines which groups have access to which “Role Capabilities.”</span></span>  <span data-ttu-id="c7400-110">此欄位會定義各種**人員**可以在此端點上執行的各種**動作**。</span><span class="sxs-lookup"><span data-stu-id="c7400-110">This field defines **who** can do **what** on this endpoint.</span></span>   <span data-ttu-id="c7400-111">角色功能是特殊的檔案，將在稍後說明。</span><span class="sxs-lookup"><span data-stu-id="c7400-111">Role Capabilities are special files that will be explained shortly.</span></span>


<span data-ttu-id="c7400-112">RoleDefinitions 欄位會定義群組與角色功能的存取權之對應關係。</span><span class="sxs-lookup"><span data-stu-id="c7400-112">The RoleDefinitions field defines which groups had access to which Role Capabilities.</span></span>  <span data-ttu-id="c7400-113">角色功能是一個檔案，定義將向連接的使用者公開的一組功能。</span><span class="sxs-lookup"><span data-stu-id="c7400-113">A Role Capability is a file that defines a set of capabilities that will be exposed to connecting users.</span></span>  <span data-ttu-id="c7400-114">您可以使用 **New-PSRoleCapabilityFile** 命令建立角色功能，</span><span class="sxs-lookup"><span data-stu-id="c7400-114">You can create Role Capabilities with the **New-PSRoleCapabilityFile** command.</span></span>

```powershell
New-PSRoleCapabilityFile -Path "$env:ProgramFiles\WindowsPowerShell\Modules\DemoModule\RoleCapabilities\Maintenance.psrc" 
```

<span data-ttu-id="c7400-115">如此將產生一種範本角色功能，看起來像這樣︰</span><span class="sxs-lookup"><span data-stu-id="c7400-115">This will generate a template role capability that looks like this:</span></span>
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
<span data-ttu-id="c7400-116">若要供 JEA 工作階段組態使用，必須在名為 “RoleCapabilities” 的資料夾中，將角色功能儲存為有效的 PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="c7400-116">To be used by a JEA session configuration, Role Capabilities must be saved as a valid PowerShell module in a directory named “RoleCapabilities”.</span></span> <span data-ttu-id="c7400-117">如有需要，模組可能會有多個角色功能檔案。</span><span class="sxs-lookup"><span data-stu-id="c7400-117">A module may have multiple role capability files, if desired.</span></span>

<span data-ttu-id="c7400-118">若要開始設定使用者可存取的哪些 Cmdlet、函數、別名及指令碼可在連接到 JEA 工作階段時存取，請遵循註解化的範本，將您自己的規則加入角色功能檔案中。</span><span class="sxs-lookup"><span data-stu-id="c7400-118">To start configuring which cmdlets, functions, aliases, and scripts a user may access when connecting to a JEA session, add your own rules to the Role Capability file following the commented out templates.</span></span> <span data-ttu-id="c7400-119">如需深入了解如何設定角色功能，請參閱完整的[體驗指南](http://aka.ms/JEA)。</span><span class="sxs-lookup"><span data-stu-id="c7400-119">For a deeper look into how you can configure Role Capabilities, check out the full [experience guide](http://aka.ms/JEA).</span></span>

<span data-ttu-id="c7400-120">最後，當您完成自訂工作階段組態和相關角色功能後，請執行 **Register-PSSessionConfiguration** 註冊此工作階段組態並建立端點。</span><span class="sxs-lookup"><span data-stu-id="c7400-120">Finally, once you have finished customizing your session configuration and related Role Capabilities, register this session configuration and create the endpoint by running **Register-PSSessionConfiguration**.</span></span>

```powershell
Register-PSSessionConfiguration -Name Maintenance -Path "C:\ProgramData\JEAConfiguration\Demo.pssc" 
```

## <a name="connect-to-a-jea-endpoint"></a><span data-ttu-id="c7400-121">連接到 JEA 端點</span><span class="sxs-lookup"><span data-stu-id="c7400-121">Connect to a JEA Endpoint</span></span>
<span data-ttu-id="c7400-122">連接到 JEA 端點與連接到其他 PowerShell 端點的運作方式一樣。</span><span class="sxs-lookup"><span data-stu-id="c7400-122">Connecting to a JEA Endpoint works the same way connecting to any other PowerShell endpoint works.</span></span>  <span data-ttu-id="c7400-123">您只需要提供您的 JEA 端點名稱作為 **New-PSSession**、**Invoke-Command**或 **Enter-PSSession** 的 "ConfigurationName" 參數。</span><span class="sxs-lookup"><span data-stu-id="c7400-123">You simply have to give your JEA endpoint name as the “ConfigurationName” parameter for **New-PSSession**, **Invoke-Command**, or **Enter-PSSession**.</span></span>

```powershell
Enter-PSSession -ConfigurationName Maintenance -ComputerName localhost
```
<span data-ttu-id="c7400-124">一旦您已經連接到 JEA 工作階段，將限制您可執行的命令，這些命令必須列在您可存取之角色功能中的允許清單。</span><span class="sxs-lookup"><span data-stu-id="c7400-124">Once you have connected to the JEA session, you will be limited to running the commands whitelisted in the Role Capabilities that you have access to.</span></span> <span data-ttu-id="c7400-125">如果您嘗試執行任何您的角色不允許的命令，將會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="c7400-125">If you try to run any command not allowed for your role, you will encounter an error.</span></span>

