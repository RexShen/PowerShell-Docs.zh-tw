---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/24/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pssessionconfigurationfile?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSSessionConfigurationFile
ms.openlocfilehash: 98dd55175321c2b7ebd98d1fb2420993d8aabe97
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202268"
---
# <span data-ttu-id="f2d35-103">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="f2d35-103">New-PSSessionConfigurationFile</span></span>

## <span data-ttu-id="f2d35-104">概要</span><span class="sxs-lookup"><span data-stu-id="f2d35-104">SYNOPSIS</span></span>
<span data-ttu-id="f2d35-105">建立定義工作階段設定的檔案。</span><span class="sxs-lookup"><span data-stu-id="f2d35-105">Creates a file that defines a session configuration.</span></span>

## <span data-ttu-id="f2d35-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f2d35-106">SYNTAX</span></span>

```
New-PSSessionConfigurationFile [-Path] <String> [-SchemaVersion <Version>] [-Guid <Guid>]
 [-Author <String>] [-Description <String>] [-CompanyName <String>] [-Copyright <String>]
 [-SessionType <SessionType>] [-TranscriptDirectory <String>] [-RunAsVirtualAccount]
 [-RunAsVirtualAccountGroups <String[]>] [-MountUserDrive] [-UserDriveMaximumSize <Int64>]
 [-GroupManagedServiceAccount <String>] [-ScriptsToProcess <String[]>]
 [-RoleDefinitions <IDictionary>] [-RequiredGroups <IDictionary>] [-LanguageMode <PSLanguageMode>]
 [-ExecutionPolicy <ExecutionPolicy>] [-PowerShellVersion <Version>] [-ModulesToImport <Object[]>]
 [-VisibleAliases <String[]>] [-VisibleCmdlets <Object[]>] [-VisibleFunctions <Object[]>]
 [-VisibleExternalCommands <String[]>] [-VisibleProviders <String[]>]
 [-AliasDefinitions <IDictionary[]>] [-FunctionDefinitions <IDictionary[]>]
 [-VariableDefinitions <Object>] [-EnvironmentVariables <IDictionary>] [-TypesToProcess <String[]>]
 [-FormatsToProcess <String[]>] [-AssembliesToLoad <String[]>] [-Full] [<CommonParameters>]
```

## <span data-ttu-id="f2d35-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="f2d35-107">DESCRIPTION</span></span>

<span data-ttu-id="f2d35-108">此 `New-PSSessionConfigurationFile` Cmdlet 會建立設定的檔案，這些設定會定義會話設定，以及使用會話設定建立之會話的環境。</span><span class="sxs-lookup"><span data-stu-id="f2d35-108">The `New-PSSessionConfigurationFile` cmdlet creates a file of settings that define a session configuration and the environment of sessions that are created by using the session configuration.</span></span>
<span data-ttu-id="f2d35-109">若要在會話設定中使用此檔案，請使用或 Cmdlet 的 **Path** 參數 `Register-PSSessionConfiguration` `Set-PSSessionConfiguration` 。</span><span class="sxs-lookup"><span data-stu-id="f2d35-109">To use the file in a session configuration, use the **Path** parameter of the `Register-PSSessionConfiguration` or `Set-PSSessionConfiguration` cmdlets.</span></span>

<span data-ttu-id="f2d35-110">建立的會話設定檔 `New-PSSessionConfigurationFile` 是人們可讀取的文字檔，其中包含會話設定屬性和值的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="f2d35-110">The session configuration file that `New-PSSessionConfigurationFile` creates is a human-readable text file that contains a hash table of the session configuration properties and values.</span></span> <span data-ttu-id="f2d35-111">檔案的副檔名為 `.pssc` 副檔名。</span><span class="sxs-lookup"><span data-stu-id="f2d35-111">The file has a `.pssc` filename extension.</span></span>

<span data-ttu-id="f2d35-112">的所有參數 `New-PSSessionConfigurationFile` 都是選擇性的，但 **Path** 參數除外。</span><span class="sxs-lookup"><span data-stu-id="f2d35-112">All parameters of `New-PSSessionConfigurationFile` are optional, except for the **Path** parameter.</span></span>
<span data-ttu-id="f2d35-113">如果您省略某個參數，除了在參數描述中註明之外，將會在工作階段設定檔中相對應的索引鍵上加上註解使它無效。</span><span class="sxs-lookup"><span data-stu-id="f2d35-113">If you omit a parameter, the corresponding key in the session configuration file is commented-out, except where noted in the parameter description.</span></span>

<span data-ttu-id="f2d35-114">會話設定（也稱為端點）是本機電腦上的一組設定集合，用來定義 PowerShell 會話的環境， ( **pssession** ) 連接到電腦。</span><span class="sxs-lookup"><span data-stu-id="f2d35-114">A session configuration, also known as an endpoint, is a collection of settings on the local computer that define the environment for PowerShell sessions ( **PSSessions** ) that connect to the computer.</span></span> <span data-ttu-id="f2d35-115">所有 **pssession** 都會使用會話設定。</span><span class="sxs-lookup"><span data-stu-id="f2d35-115">All **PSSessions** use a session configuration.</span></span> <span data-ttu-id="f2d35-116">若要指定特定的會話設定，請使用建立會話之 Cmdlet 的 **ConfigurationName** 參數，例如 `New-PSSession` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f2d35-116">To specify a particular session configuration, use the **ConfigurationName** parameter of cmdlets that create a session, such as the `New-PSSession` cmdlet.</span></span>

<span data-ttu-id="f2d35-117">session configuration file 不需要複雜的指令碼或程式碼組件，就能輕鬆定義工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="f2d35-117">A session configuration file makes it easy to define a session configuration without complex scripts or code assemblies.</span></span> <span data-ttu-id="f2d35-118">檔案中的設定會搭配選用的啟動腳本和會話設定中的任何元件使用。</span><span class="sxs-lookup"><span data-stu-id="f2d35-118">The settings in the file are used with the optional startup script and any assemblies in the session configuration.</span></span>

<span data-ttu-id="f2d35-119">如需會話設定和會話設定檔的詳細資訊，請參閱 [about_Session_Configurations](About/about_Session_Configurations.md) 和 [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)。</span><span class="sxs-lookup"><span data-stu-id="f2d35-119">For more information about session configurations and session configuration files, see [about_Session_Configurations](About/about_Session_Configurations.md) and [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span></span>

<span data-ttu-id="f2d35-120">此 Cmdlet 是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="f2d35-120">This cmdlet was introduced in PowerShell 3.0.</span></span>

## <span data-ttu-id="f2d35-121">範例</span><span class="sxs-lookup"><span data-stu-id="f2d35-121">EXAMPLES</span></span>

### <span data-ttu-id="f2d35-122">範例1：建立和使用 NoLanguage 會話</span><span class="sxs-lookup"><span data-stu-id="f2d35-122">Example 1: Creating and using a NoLanguage session</span></span>

<span data-ttu-id="f2d35-123">這個範例示範如何建立使用無語言會話的效果。</span><span class="sxs-lookup"><span data-stu-id="f2d35-123">This example show how to create and the effects of using a no-language session.</span></span>

<span data-ttu-id="f2d35-124">步驟包括：</span><span class="sxs-lookup"><span data-stu-id="f2d35-124">The steps include:</span></span>

1. <span data-ttu-id="f2d35-125">建立新的設定檔。</span><span class="sxs-lookup"><span data-stu-id="f2d35-125">Create a new configuration file.</span></span>
1. <span data-ttu-id="f2d35-126">註冊設定。</span><span class="sxs-lookup"><span data-stu-id="f2d35-126">Register the configuration.</span></span>
1. <span data-ttu-id="f2d35-127">建立使用設定的新會話。</span><span class="sxs-lookup"><span data-stu-id="f2d35-127">Create a new session that uses the configuration.</span></span>
1. <span data-ttu-id="f2d35-128">在新的會話中執行命令。</span><span class="sxs-lookup"><span data-stu-id="f2d35-128">Run commands in that new session.</span></span>

<span data-ttu-id="f2d35-129">若要執行此範例中的命令，請使用 [以系統管理員身分執行] 選項啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="f2d35-129">To run the commands in this example, start PowerShell by using the Run as administrator option.</span></span> <span data-ttu-id="f2d35-130">需要此選項才能執行 `Register-PSSessionConfiguration` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f2d35-130">This option is required to run the `Register-PSSessionConfiguration` cmdlet.</span></span>

```powershell
New-PSSessionConfigurationFile -Path .\NoLanguage.pssc -LanguageMode NoLanguage
Register-PSSessionConfiguration -Path .\NoLanguage.pssc -Name NoLanguage -Force
$NoLanguageSession = New-PSSession -ComputerName Srv01 -ConfigurationName NoLanguage
Invoke-Command -Session $NoLanguageSession -ScriptBlock {
  if ((Get-Date) -lt '1January2099') {'Before'} else {'After'}
}
```

```Output
The syntax is not supported by this runspace. This might be because it is in no-language mode.
    + CategoryInfo          : ParserError: (if ((Get-Date) ...') {'Before'}  :String) [], ParseException
    + FullyQualifiedErrorId : ScriptsNotAllowed
    + PSComputerName        : localhost
```

<span data-ttu-id="f2d35-131">在此範例中， `Invoke-Command` 因為 **LanguageMode** 設定為 **NoLanguage** ，所以失敗。</span><span class="sxs-lookup"><span data-stu-id="f2d35-131">In this example, the `Invoke-Command` fails because the **LanguageMode** is set to **NoLanguage** .</span></span>

### <span data-ttu-id="f2d35-132">範例2：建立和使用 RestrictedLanguage 會話</span><span class="sxs-lookup"><span data-stu-id="f2d35-132">Example 2: Creating and using a RestrictedLanguage session</span></span>

<span data-ttu-id="f2d35-133">這個範例示範如何建立使用無語言會話的效果。</span><span class="sxs-lookup"><span data-stu-id="f2d35-133">This example show how to create and the effects of using a no-language session.</span></span>

<span data-ttu-id="f2d35-134">步驟包括：</span><span class="sxs-lookup"><span data-stu-id="f2d35-134">The steps include:</span></span>

1. <span data-ttu-id="f2d35-135">建立新的設定檔。</span><span class="sxs-lookup"><span data-stu-id="f2d35-135">Create a new configuration file.</span></span>
1. <span data-ttu-id="f2d35-136">註冊設定。</span><span class="sxs-lookup"><span data-stu-id="f2d35-136">Register the configuration.</span></span>
1. <span data-ttu-id="f2d35-137">建立使用設定的新會話。</span><span class="sxs-lookup"><span data-stu-id="f2d35-137">Create a new session that uses the configuration.</span></span>
1. <span data-ttu-id="f2d35-138">在新的會話中執行命令。</span><span class="sxs-lookup"><span data-stu-id="f2d35-138">Run commands in that new session.</span></span>

<span data-ttu-id="f2d35-139">若要執行此範例中的命令，請使用 [以系統管理員身分執行] 選項啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="f2d35-139">To run the commands in this example, start PowerShell by using the Run as administrator option.</span></span> <span data-ttu-id="f2d35-140">需要此選項才能執行 `Register-PSSessionConfiguration` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f2d35-140">This option is required to run the `Register-PSSessionConfiguration` cmdlet.</span></span>

```powershell
New-PSSessionConfigurationFile -Path .\NoLanguage.pssc -LanguageMode RestrictedLanguage
Register-PSSessionConfiguration -Path .\NoLanguage.pssc -Name RestrictedLanguage -Force
$RestrictedSession = New-PSSession -ComputerName Srv01 -ConfigurationName RestrictedLanguage
Invoke-Command -Session $RestrictedSession -ScriptBlock {
  if ((Get-Date) -lt '1January2099') {'Before'} else {'After'}
}
```

```Output
Before
```

<span data-ttu-id="f2d35-141">在此範例中， `Invoke-Command` 會成功，因為 **LanguageMode** 設定為 **RestrictedLanguage** 。</span><span class="sxs-lookup"><span data-stu-id="f2d35-141">In this example, the `Invoke-Command` succeeds because the **LanguageMode** is set to **RestrictedLanguage** .</span></span>

### <span data-ttu-id="f2d35-142">範例3：變更會話設定檔</span><span class="sxs-lookup"><span data-stu-id="f2d35-142">Example 3: Changing a Session Configuration File</span></span>

<span data-ttu-id="f2d35-143">此範例顯示如何變更在名為 "ITTasks" 的現有會話中使用的會話設定檔。</span><span class="sxs-lookup"><span data-stu-id="f2d35-143">This example shows how to change the session configuration file that is used in an existing session named "ITTasks".</span></span> <span data-ttu-id="f2d35-144">之前，這些會話只有核心模組和內部 **ITTasks** 模組。</span><span class="sxs-lookup"><span data-stu-id="f2d35-144">Previously, these sessions had only the core modules and an internal **ITTasks** module.</span></span> <span data-ttu-id="f2d35-145">系統管理員想要將 **PSScheduledJob** 模組新增至使用 ITTasks 會話設定建立的會話。</span><span class="sxs-lookup"><span data-stu-id="f2d35-145">The administrator wants to add the **PSScheduledJob** module to sessions created by using the ITTasks session configuration.</span></span>

```powershell
New-PSSessionConfigurationFile -Path .\New-ITTasks.pssc -ModulesToImport Microsoft*, ITTasks, PSScheduledJob
Set-PSSessionConfiguration -Name ITTasks -Path .\New-ITTasks.pssc
```

<span data-ttu-id="f2d35-146">此 `New-PSSessionConfigurationFile` Cmdlet 會建立可匯入必要模組的會話設定檔。</span><span class="sxs-lookup"><span data-stu-id="f2d35-146">The `New-PSSessionConfigurationFile` cmdlet to create a session configuration file that imports the required modules.</span></span> <span data-ttu-id="f2d35-147">Cmdlet 會將 `Set-PSSessionConfiguration` 目前的設定檔取代為新的設定檔。</span><span class="sxs-lookup"><span data-stu-id="f2d35-147">The `Set-PSSessionConfiguration` cmdlet replaces the current configuration file with the new one.</span></span> <span data-ttu-id="f2d35-148">這種新設定只會影響變更後所建立的新會話。</span><span class="sxs-lookup"><span data-stu-id="f2d35-148">This new configuration only affects new sessions created after the change.</span></span>
<span data-ttu-id="f2d35-149">現有的「ITTasks」會話不會受到影響。</span><span class="sxs-lookup"><span data-stu-id="f2d35-149">Existing "ITTasks" sessions are not affected.</span></span>

### <span data-ttu-id="f2d35-150">範例4：編輯會話設定檔</span><span class="sxs-lookup"><span data-stu-id="f2d35-150">Example 4: Editing a Session Configuration File</span></span>

<span data-ttu-id="f2d35-151">此範例說明如何透過編輯設定檔的使用中工作階段設定複本，來變更工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="f2d35-151">This example shows how to change a session configuration by editing the active session configuration copy of the configuration file.</span></span> <span data-ttu-id="f2d35-152">若要修改設定檔的會話設定複本，您必須擁有該檔案的「完全控制」存取權限。</span><span class="sxs-lookup"><span data-stu-id="f2d35-152">To modify the session configuration copy of the configuration file, you must have full control access to the file.</span></span> <span data-ttu-id="f2d35-153">這可能需要您變更檔案的許可權。</span><span class="sxs-lookup"><span data-stu-id="f2d35-153">This may require you to change the permissions on the file.</span></span>

<span data-ttu-id="f2d35-154">在此案例中，我們想要藉 `Select-String` 由編輯使用中的設定檔來新增 Cmdlet 的別名。</span><span class="sxs-lookup"><span data-stu-id="f2d35-154">In this scenario, we want to add a new alias for the `Select-String` cmdlet by editing the active configuration file.</span></span>

<span data-ttu-id="f2d35-155">下列程式碼範例會執行下列步驟來進行這項變更：</span><span class="sxs-lookup"><span data-stu-id="f2d35-155">The example code below performs the following steps to make this change:</span></span>

1. <span data-ttu-id="f2d35-156">取得 ITConfig 會話的設定檔路徑。</span><span class="sxs-lookup"><span data-stu-id="f2d35-156">Get the configuration file path for the ITConfig session.</span></span>
1. <span data-ttu-id="f2d35-157">使用者使用 **Notepad.exe** 編輯設定檔，以變更 **AliasDefinitions** 值，如下所示： `AliasDefinitions = @(@{Name='slst';Value='Select-String'})` 。</span><span class="sxs-lookup"><span data-stu-id="f2d35-157">The user edits the configuration file using **Notepad.exe** to change the **AliasDefinitions** value as follows: `AliasDefinitions = @(@{Name='slst';Value='Select-String'})`.</span></span>
1. <span data-ttu-id="f2d35-158">測試已更新的設定檔。</span><span class="sxs-lookup"><span data-stu-id="f2d35-158">Test the updated configuration file.</span></span>

```powershell
$ITConfig = Get-PSSessionConfiguration -Name ITConfig
notepad.exe $ITConfig.ConfigFilePath
Test-PSSessionConfigurationFile -Path $ITConfig.ConfigFilePath
```

```Output
True
```

<span data-ttu-id="f2d35-159">使用 **Verbose** 參數搭配 `Test-PSSessionConfigurationFile` 來顯示任何偵測到的錯誤。</span><span class="sxs-lookup"><span data-stu-id="f2d35-159">Use the **Verbose** parameter with `Test-PSSessionConfigurationFile` to display any errors that are detected.</span></span> <span data-ttu-id="f2d35-160">`$True`如果未在檔案中偵測到錯誤，則 Cmdlet 會傳回。</span><span class="sxs-lookup"><span data-stu-id="f2d35-160">The cmdlet returns `$True` if no errors are detected in the file.</span></span>

### <span data-ttu-id="f2d35-161">範例5：建立範例設定檔</span><span class="sxs-lookup"><span data-stu-id="f2d35-161">Example 5: Create a sample configuration file</span></span>

<span data-ttu-id="f2d35-162">此範例顯示 `New-PSSessionConfigurationFile` 使用所有 Cmdlet 參數的命令。</span><span class="sxs-lookup"><span data-stu-id="f2d35-162">This example shows a `New-PSSessionConfigurationFile` command that uses all the cmdlet parameters.</span></span>
<span data-ttu-id="f2d35-163">它也會顯示每個參數的正確輸入格式。</span><span class="sxs-lookup"><span data-stu-id="f2d35-163">It is included to show the correct input format for each parameter.</span></span>

<span data-ttu-id="f2d35-164">輸出中會顯示產生的 SampleFile.pssc。</span><span class="sxs-lookup"><span data-stu-id="f2d35-164">The resulting SampleFile.pssc is displayed in the output.</span></span>

```powershell
$configSettings = @{
    Path = '.\SampleFile.pssc'
    SchemaVersion = '1.0.0.0'
    Author = 'User01'
    Copyright = '(c) Fabrikam Corporation. All rights reserved.'
    CompanyName = 'Fabrikam Corporation'
    Description = 'This is a sample file.'
    ExecutionPolicy = 'AllSigned'
    PowerShellVersion = '3.0'
    LanguageMode = 'FullLanguage'
    SessionType = 'Default'
    EnvironmentVariables = @{TESTSHARE='\\Test2\Test'}
    ModulesToImport = @{ModuleName='PSScheduledJob'; ModuleVersion='1.0.0.0'; GUID='50cdb55f-5ab7-489f-9e94-4ec21ff51e59'},'PSDiagnostics'
    AssembliesToLoad = 'System.Web.Services','FSharp.Compiler.CodeDom.dll'
    TypesToProcess = 'Types1.ps1xml','Types2.ps1xml'
    FormatsToProcess = 'CustomFormats.ps1xml'
    ScriptsToProcess = 'Get-Inputs.ps1'
    AliasDefinitions = @{Name='hlp';Value='Get-Help';Description='Gets help.';Options='AllScope'},
        @{Name='Update';Value='Update-Help';Description='Updates help';Options='ReadOnly'}
    FunctionDefinitions = @{Name='Get-Function';ScriptBlock={Get-Command -CommandType Function};Options='ReadOnly'}
    VariableDefinitions = @{Name='WarningPreference';Value='SilentlyContinue'}
    VisibleAliases = 'c*','g*','i*','s*'
    VisibleCmdlets = 'Get*'
    VisibleFunctions = 'Get*'
    VisibleProviders = 'FileSystem','Function','Variable'
    RunAsVirtualAccount = $true
    RunAsVirtualAccountGroups = 'Backup Operators'
}
New-PSSessionConfigurationFile @configSettings
Get-Content SampleFile.pssc
```

```Output
@{

# Version number of the schema used for this document
SchemaVersion = '1.0.0.0'

# ID used to uniquely identify this document
GUID = '1caeff7f-27ca-4360-97cf-37846f594235'

# Author of this document
Author = 'User01'

# Description of the functionality provided by these settings
Description = 'This is a sample file.'

# Company associated with this document
CompanyName = 'Fabrikam Corporation'

# Copyright statement for this document
Copyright = '(c) Fabrikam Corporation. All rights reserved.'

# Session type defaults to apply for this session configuration. Can be 'RestrictedRemoteServer' (recommended), 'Empty', or 'Default'
SessionType = 'Default'

# Directory to place session transcripts for this session configuration
# TranscriptDirectory = 'C:\Transcripts\'

# Whether to run this session configuration as the machine's (virtual) administrator account
RunAsVirtualAccount = $true

# Groups associated with machine's (virtual) administrator account
RunAsVirtualAccountGroups = 'Backup Operators'

# Scripts to run when applied to a session
ScriptsToProcess = 'Get-Inputs.ps1'

# User roles (security groups), and the role capabilities that should be applied to them when applied to a session
# RoleDefinitions = @{ 'CONTOSO\SqlAdmins' = @{ RoleCapabilities = 'SqlAdministration' }; 'CONTOSO\SqlManaged' = @{ RoleCapabilityFiles = 'C:\RoleCapability\SqlManaged.psrc' }; 'CONTOSO\ServerMonitors' = @{ VisibleCmdlets = 'Get-Process' } }

# Language mode to apply when applied to a session. Can be 'NoLanguage' (recommended), 'RestrictedLanguage', 'ConstrainedLanguage', or 'FullLanguage'
LanguageMode = 'FullLanguage'

# Execution policy to apply when applied to a session
ExecutionPolicy = 'AllSigned'

# Version of the PowerShell engine to use when applied to a session
PowerShellVersion = '3.0'

# Modules to import when applied to a session
ModulesToImport = @{
    'GUID' = '50cdb55f-5ab7-489f-9e94-4ec21ff51e59'
    'ModuleName' = 'PSScheduledJob'
    'ModuleVersion' = '1.0.0.0' }, 'PSDiagnostics'

# Aliases to make visible when applied to a session
VisibleAliases = 'c*', 'g*', 'i*', 's*'

# Cmdlets to make visible when applied to a session
VisibleCmdlets = 'Get*'

# Functions to make visible when applied to a session
VisibleFunctions = 'Get*'

# Providers to make visible when applied to a session
VisibleProviders = 'FileSystem', 'Function', 'Variable'

# Aliases to be defined when applied to a session
AliasDefinitions = @{
    'Description' = 'Gets help.'
    'Name' = 'hlp'
    'Options' = 'AllScope'
    'Value' = 'Get-Help' }, @{
    'Description' = 'Updates help'
    'Name' = 'Update'
    'Options' = 'ReadOnly'
    'Value' = 'Update-Help' }

# Functions to define when applied to a session
FunctionDefinitions = @{
    'Name' = 'Get-Function'
    'Options' = 'ReadOnly'
    'ScriptBlock' = {Get-Command -CommandType Function} }

# Variables to define when applied to a session
VariableDefinitions = @{
    'Name' = 'WarningPreference'
    'Value' = 'SilentlyContinue' }

# Environment variables to define when applied to a session
EnvironmentVariables = @{
    'TESTSHARE' = '\\Test2\Test' }

# Type files (.ps1xml) to load when applied to a session
TypesToProcess = 'Types1.ps1xml', 'Types2.ps1xml'

# Format files (.ps1xml) to load when applied to a session
FormatsToProcess = 'CustomFormats.ps1xml'

# Assemblies to load when applied to a session
AssembliesToLoad = 'System.Web.Services', 'FSharp.Compiler.CodeDom.dll'

}
```

## <span data-ttu-id="f2d35-165">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f2d35-165">PARAMETERS</span></span>

### <span data-ttu-id="f2d35-166">-AliasDefinitions</span><span class="sxs-lookup"><span data-stu-id="f2d35-166">-AliasDefinitions</span></span>

<span data-ttu-id="f2d35-167">將指定的別名新增至使用工作階段設定的工作階段。</span><span class="sxs-lookup"><span data-stu-id="f2d35-167">Adds the specified aliases to sessions that use the session configuration.</span></span> <span data-ttu-id="f2d35-168">輸入包含下列索引鍵的雜湊表：</span><span class="sxs-lookup"><span data-stu-id="f2d35-168">Enter a hash table with the following keys:</span></span>

- <span data-ttu-id="f2d35-169">名稱-別名的名稱。</span><span class="sxs-lookup"><span data-stu-id="f2d35-169">Name - Name of the alias.</span></span> <span data-ttu-id="f2d35-170">此為必要索引鍵。</span><span class="sxs-lookup"><span data-stu-id="f2d35-170">This key is required.</span></span>
- <span data-ttu-id="f2d35-171">Value-別名所代表的命令。</span><span class="sxs-lookup"><span data-stu-id="f2d35-171">Value - The command that the alias represents.</span></span> <span data-ttu-id="f2d35-172">此為必要索引鍵。</span><span class="sxs-lookup"><span data-stu-id="f2d35-172">This key is required.</span></span>
- <span data-ttu-id="f2d35-173">描述-描述別名的文字字串。</span><span class="sxs-lookup"><span data-stu-id="f2d35-173">Description - A text string that describes the alias.</span></span> <span data-ttu-id="f2d35-174">此為選擇性索引鍵。</span><span class="sxs-lookup"><span data-stu-id="f2d35-174">This key is optional.</span></span>
- <span data-ttu-id="f2d35-175">選項-別名選項。</span><span class="sxs-lookup"><span data-stu-id="f2d35-175">Options - Alias options.</span></span> <span data-ttu-id="f2d35-176">此為選擇性索引鍵。</span><span class="sxs-lookup"><span data-stu-id="f2d35-176">This key is optional.</span></span> <span data-ttu-id="f2d35-177">預設值為 **None** 。</span><span class="sxs-lookup"><span data-stu-id="f2d35-177">The default value is **None** .</span></span> <span data-ttu-id="f2d35-178">此參數可接受的值為： None、ReadOnly、常數、私用或 AllScope。</span><span class="sxs-lookup"><span data-stu-id="f2d35-178">The acceptable values for this parameter are: None, ReadOnly, Constant, Private, or AllScope.</span></span>

<span data-ttu-id="f2d35-179">例如：`@{Name='hlp';Value='Get-Help';Description='Gets help';Options='ReadOnly'}`</span><span class="sxs-lookup"><span data-stu-id="f2d35-179">For example: `@{Name='hlp';Value='Get-Help';Description='Gets help';Options='ReadOnly'}`</span></span>

```yaml
Type: System.Collections.IDictionary[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2d35-180">-AssembliesToLoad</span><span class="sxs-lookup"><span data-stu-id="f2d35-180">-AssembliesToLoad</span></span>

<span data-ttu-id="f2d35-181">指定要載入至使用工作階段設定之工作階段的組件。</span><span class="sxs-lookup"><span data-stu-id="f2d35-181">Specifies the assemblies to load into the sessions that use the session configuration.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2d35-182">-作者</span><span class="sxs-lookup"><span data-stu-id="f2d35-182">-Author</span></span>

<span data-ttu-id="f2d35-183">指定會話設定或設定檔案的作者。</span><span class="sxs-lookup"><span data-stu-id="f2d35-183">Specifies the author of the session configuration or the configuration file.</span></span> <span data-ttu-id="f2d35-184">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="f2d35-184">The default is the current user.</span></span> <span data-ttu-id="f2d35-185">此參數的值會出現在工作階段設定中，但它不是工作階段物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="f2d35-185">The value of this parameter is visible in the session configuration file, but it is not a property of the session configuration object.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2d35-186">-公司名稱</span><span class="sxs-lookup"><span data-stu-id="f2d35-186">-CompanyName</span></span>

<span data-ttu-id="f2d35-187">指定建立會話設定或設定檔的公司。</span><span class="sxs-lookup"><span data-stu-id="f2d35-187">Specifies the company that created the session configuration or the configuration file.</span></span> <span data-ttu-id="f2d35-188">預設值為 [未知]  。</span><span class="sxs-lookup"><span data-stu-id="f2d35-188">The default value is **Unknown** .</span></span> <span data-ttu-id="f2d35-189">此參數的值會出現在工作階段設定中，但它不是工作階段物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="f2d35-189">The value of this parameter is visible in the session configuration file, but it is not a property of the session configuration object.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Unknown
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2d35-190">-著作權</span><span class="sxs-lookup"><span data-stu-id="f2d35-190">-Copyright</span></span>

<span data-ttu-id="f2d35-191">指定會話設定檔的著作權。</span><span class="sxs-lookup"><span data-stu-id="f2d35-191">Specifies a copyright the session configuration file.</span></span> <span data-ttu-id="f2d35-192">此參數的值會出現在工作階段設定中，但它不是工作階段物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="f2d35-192">The value of this parameter is visible in the session configuration file, but it is not a property of the session configuration object.</span></span>

<span data-ttu-id="f2d35-193">如果您省略此參數，則會 `New-PSSessionConfigurationFile` 使用 **Author** 參數的值產生著作權語句。</span><span class="sxs-lookup"><span data-stu-id="f2d35-193">If you omit this parameter, `New-PSSessionConfigurationFile` generates a copyright statement by using the value of the **Author** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2d35-194">-Description</span><span class="sxs-lookup"><span data-stu-id="f2d35-194">-Description</span></span>

<span data-ttu-id="f2d35-195">指定會話設定或會話設定檔的描述。</span><span class="sxs-lookup"><span data-stu-id="f2d35-195">Specifies a description of the session configuration or the session configuration file.</span></span> <span data-ttu-id="f2d35-196">此參數的值會出現在工作階段設定中，但它不是工作階段物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="f2d35-196">The value of this parameter is visible in the session configuration file, but it is not a property of the session configuration object.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2d35-197">-EnvironmentVariables</span><span class="sxs-lookup"><span data-stu-id="f2d35-197">-EnvironmentVariables</span></span>

<span data-ttu-id="f2d35-198">新增環境變數至工作階段。</span><span class="sxs-lookup"><span data-stu-id="f2d35-198">Adds environment variables to the session.</span></span> <span data-ttu-id="f2d35-199">輸入雜湊表，其中索引鍵為環境變數名稱，值為環境變數值。</span><span class="sxs-lookup"><span data-stu-id="f2d35-199">Enter a hash table in which the keys are the environment variable names and the values are the environment variable values.</span></span>

<span data-ttu-id="f2d35-200">例如：`EnvironmentVariables=@{TestShare='\\Server01\TestShare'}`</span><span class="sxs-lookup"><span data-stu-id="f2d35-200">For example: `EnvironmentVariables=@{TestShare='\\Server01\TestShare'}`</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2d35-201">-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="f2d35-201">-ExecutionPolicy</span></span>

<span data-ttu-id="f2d35-202">指定使用工作階段設定之工作階段的執行原則。</span><span class="sxs-lookup"><span data-stu-id="f2d35-202">Specifies the execution policy of sessions that use the session configuration.</span></span> <span data-ttu-id="f2d35-203">如果您省略此參數，會話設定檔中的 **ExecutionPolicy** 索引鍵值會 **受到限制** 。</span><span class="sxs-lookup"><span data-stu-id="f2d35-203">If you omit this parameter, the value of the **ExecutionPolicy** key in the session configuration file is **Restricted** .</span></span> <span data-ttu-id="f2d35-204">如需 PowerShell 中執行原則的詳細資訊，請參閱 [about_Execution_Policies](about/about_Execution_Policies.md)。</span><span class="sxs-lookup"><span data-stu-id="f2d35-204">For information about execution policies in PowerShell, see [about_Execution_Policies](about/about_Execution_Policies.md).</span></span>

```yaml
Type: Microsoft.PowerShell.ExecutionPolicy
Parameter Sets: (All)
Aliases:
Accepted values: Unrestricted, RemoteSigned, AllSigned, Restricted, Default, Bypass, Undefined

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2d35-205">-FormatsToProcess</span><span class="sxs-lookup"><span data-stu-id="f2d35-205">-FormatsToProcess</span></span>

<span data-ttu-id="f2d35-206">指定在使用工作階段設定的工作階段中執行的格式化檔案 (.ps1xml)。</span><span class="sxs-lookup"><span data-stu-id="f2d35-206">Specifies the formatting files (.ps1xml) that run in sessions that use the session configuration.</span></span>
<span data-ttu-id="f2d35-207">此參數的值必須是格式化檔案的完整路徑或絕對路徑。</span><span class="sxs-lookup"><span data-stu-id="f2d35-207">The value of this parameter must be a full or absolute path of the formatting files.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2d35-208">-Full</span><span class="sxs-lookup"><span data-stu-id="f2d35-208">-Full</span></span>

<span data-ttu-id="f2d35-209">指出此作業會在會話設定檔中包含所有可能的設定屬性。</span><span class="sxs-lookup"><span data-stu-id="f2d35-209">Indicates that this operation includes all possible configuration properties in the session configuration file.</span></span>

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

### <span data-ttu-id="f2d35-210">-FunctionDefinitions</span><span class="sxs-lookup"><span data-stu-id="f2d35-210">-FunctionDefinitions</span></span>

<span data-ttu-id="f2d35-211">將指定函式新增至使用工作階段設定的工作階段。</span><span class="sxs-lookup"><span data-stu-id="f2d35-211">Adds the specified functions to sessions that use the session configuration.</span></span> <span data-ttu-id="f2d35-212">輸入包含下列索引鍵的雜湊表：</span><span class="sxs-lookup"><span data-stu-id="f2d35-212">Enter a hash table with the following keys:</span></span>

- <span data-ttu-id="f2d35-213">名稱-函數的名稱。</span><span class="sxs-lookup"><span data-stu-id="f2d35-213">Name - Name of the function.</span></span> <span data-ttu-id="f2d35-214">此為必要索引鍵。</span><span class="sxs-lookup"><span data-stu-id="f2d35-214">This key is required.</span></span>
- <span data-ttu-id="f2d35-215">ScriptBlock 函數主體。</span><span class="sxs-lookup"><span data-stu-id="f2d35-215">ScriptBlock - Function body.</span></span> <span data-ttu-id="f2d35-216">輸入指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="f2d35-216">Enter a script block.</span></span> <span data-ttu-id="f2d35-217">此為必要索引鍵。</span><span class="sxs-lookup"><span data-stu-id="f2d35-217">This key is required.</span></span>
- <span data-ttu-id="f2d35-218">選項功能選項。</span><span class="sxs-lookup"><span data-stu-id="f2d35-218">Options - Function options.</span></span> <span data-ttu-id="f2d35-219">此為選擇性索引鍵。</span><span class="sxs-lookup"><span data-stu-id="f2d35-219">This key is optional.</span></span> <span data-ttu-id="f2d35-220">預設值為 **None** 。</span><span class="sxs-lookup"><span data-stu-id="f2d35-220">The default value is **None** .</span></span> <span data-ttu-id="f2d35-221">此參數可接受的值為： None、ReadOnly、常數、私用或 AllScope。</span><span class="sxs-lookup"><span data-stu-id="f2d35-221">The acceptable values for this parameter are: None, ReadOnly, Constant, Private, or AllScope.</span></span>

<span data-ttu-id="f2d35-222">例如：`@{Name='Get-PowerShellProcess';ScriptBlock={Get-Process PowerShell};Options='AllScope'}`</span><span class="sxs-lookup"><span data-stu-id="f2d35-222">For example: `@{Name='Get-PowerShellProcess';ScriptBlock={Get-Process PowerShell};Options='AllScope'}`</span></span>

```yaml
Type: System.Collections.IDictionary[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2d35-223">-Msds-groupmanagedserviceaccount</span><span class="sxs-lookup"><span data-stu-id="f2d35-223">-GroupManagedServiceAccount</span></span>

<span data-ttu-id="f2d35-224">使用此會話設定來設定會話，以在指定群組受管理的服務帳戶的內容下執行。</span><span class="sxs-lookup"><span data-stu-id="f2d35-224">Configures sessions using this session configuration to run under the context of the specified Group Managed Service Account.</span></span> <span data-ttu-id="f2d35-225">註冊此會話設定的電腦必須具有要求 gMSA 密碼的許可權，才能成功建立會話。</span><span class="sxs-lookup"><span data-stu-id="f2d35-225">The machine where this session configuration is registered must have permission to request the gMSA password in order for sessions to be created successfully.</span></span> <span data-ttu-id="f2d35-226">這個欄位不能搭配 **將 runasvirtualaccount 設** 參數使用。</span><span class="sxs-lookup"><span data-stu-id="f2d35-226">This field cannot be used with the **RunAsVirtualAccount** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2d35-227">-Guid</span><span class="sxs-lookup"><span data-stu-id="f2d35-227">-Guid</span></span>

<span data-ttu-id="f2d35-228">指定工作階段設定檔的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="f2d35-228">Specifies a unique identifier for the session configuration file.</span></span> <span data-ttu-id="f2d35-229">如果您省略此參數，則會產生檔案的 `New-PSSessionConfigurationFile` GUID。</span><span class="sxs-lookup"><span data-stu-id="f2d35-229">If you omit this parameter, `New-PSSessionConfigurationFile` generates a GUID for the file.</span></span> <span data-ttu-id="f2d35-230">若要在 PowerShell 中建立新的 GUID，請輸入 `New-Guid` 。</span><span class="sxs-lookup"><span data-stu-id="f2d35-230">To create a new GUID in PowerShell, type `New-Guid`.</span></span>

```yaml
Type: System.Guid
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2d35-231">-LanguageMode</span><span class="sxs-lookup"><span data-stu-id="f2d35-231">-LanguageMode</span></span>

<span data-ttu-id="f2d35-232">判斷使用此會話設定的會話中允許的 PowerShell 語言元素。</span><span class="sxs-lookup"><span data-stu-id="f2d35-232">Determines which elements of the PowerShell language are permitted in sessions that use this session configuration.</span></span> <span data-ttu-id="f2d35-233">您可以使用此參數來限制特定使用者可在電腦上執行的命令。</span><span class="sxs-lookup"><span data-stu-id="f2d35-233">You can use this parameter to restrict the commands that particular users can run on the computer.</span></span>

<span data-ttu-id="f2d35-234">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="f2d35-234">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="f2d35-235">>fulllanguage-允許所有語言元素。</span><span class="sxs-lookup"><span data-stu-id="f2d35-235">FullLanguage - All language elements are permitted.</span></span>
- <span data-ttu-id="f2d35-236">ConstrainedLanguage：不允許包含要評估之腳本的命令。</span><span class="sxs-lookup"><span data-stu-id="f2d35-236">ConstrainedLanguage - Commands that contain scripts to be evaluated are not allowed.</span></span> <span data-ttu-id="f2d35-237">ConstrainedLanguage 模式會限制使用者存取 Microsoft .NET Framework 類型、物件或方法。</span><span class="sxs-lookup"><span data-stu-id="f2d35-237">The ConstrainedLanguage mode restricts user access to Microsoft .NET Framework types, objects, or methods.</span></span>
- <span data-ttu-id="f2d35-238">NoLanguage-使用者可以執行 Cmdlet 和函式，但不允許使用任何語言專案，例如腳本區塊、變數或運算子。</span><span class="sxs-lookup"><span data-stu-id="f2d35-238">NoLanguage - Users may run cmdlets and functions, but are not permitted to use any language elements, such as script blocks, variables, or operators.</span></span>
- <span data-ttu-id="f2d35-239">RestrictedLanguage-使用者可以執行 Cmdlet 和函式，但不允許使用腳本區塊或變數，除了下列允許的變數： `$PSCulture` 、 `$PSUICulture` 、 `$True` 、 `$False` 和 `$Null` 。</span><span class="sxs-lookup"><span data-stu-id="f2d35-239">RestrictedLanguage - Users may run cmdlets and functions, but are not permitted to use script blocks or variables except for the following permitted variables: `$PSCulture`, `$PSUICulture`, `$True`, `$False`, and `$Null`.</span></span> <span data-ttu-id="f2d35-240">使用者只能使用基本的比較運算子 (`-eq` 、 `-gt` `-lt`) 。</span><span class="sxs-lookup"><span data-stu-id="f2d35-240">Users may use only the basic comparison operators (`-eq`, `-gt`, `-lt`).</span></span> <span data-ttu-id="f2d35-241">不允許指派陳述式、屬性參照及方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="f2d35-241">Assignment statements, property references, and method calls are not permitted.</span></span>

<span data-ttu-id="f2d35-242">**LanguageMode** 參數的預設值需視 **SessionType** 參數的值而定。</span><span class="sxs-lookup"><span data-stu-id="f2d35-242">The default value of the **LanguageMode** parameter depends on the value of the **SessionType** parameter.</span></span>

- <span data-ttu-id="f2d35-243">空白-NoLanguage</span><span class="sxs-lookup"><span data-stu-id="f2d35-243">Empty - NoLanguage</span></span>
- <span data-ttu-id="f2d35-244">RestrictedRemoteServer-NoLanguage</span><span class="sxs-lookup"><span data-stu-id="f2d35-244">RestrictedRemoteServer - NoLanguage</span></span>
- <span data-ttu-id="f2d35-245">預設值->fulllanguage</span><span class="sxs-lookup"><span data-stu-id="f2d35-245">Default - FullLanguage</span></span>

```yaml
Type: System.Management.Automation.PSLanguageMode
Parameter Sets: (All)
Aliases:
Accepted values: FullLanguage, RestrictedLanguage, NoLanguage, ConstrainedLanguage

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2d35-246">-ModulesToImport</span><span class="sxs-lookup"><span data-stu-id="f2d35-246">-ModulesToImport</span></span>

<span data-ttu-id="f2d35-247">指定要自動匯入使用工作階段設定之工作階段的模組和嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="f2d35-247">Specifies the modules and snap-ins that are automatically imported into sessions that use the session configuration.</span></span>

<span data-ttu-id="f2d35-248">依預設，只會將 **Microsoft 的 PowerShell** 嵌入式管理單元匯入至遠端會話，但除非排除 Cmdlet，否則使用者可以使用 `Import-Module` 和 `Add-PSSnapin` Cmdlet 將模組和嵌入式管理單元新增至會話。</span><span class="sxs-lookup"><span data-stu-id="f2d35-248">By default, only the **Microsoft.PowerShell.Core** snap-in is imported into remote sessions, but unless the cmdlets are excluded, users can use the `Import-Module` and `Add-PSSnapin` cmdlets to add modules and snap-ins to the session.</span></span>

<span data-ttu-id="f2d35-249">此參數值中的每個模組或嵌入式管理單元都可以用字串或雜湊表代表。</span><span class="sxs-lookup"><span data-stu-id="f2d35-249">Each module or snap-in in the value of this parameter can be represented by a string or as a hash table.</span></span> <span data-ttu-id="f2d35-250">模組字串只包含模組或嵌入式管理單元的名稱。</span><span class="sxs-lookup"><span data-stu-id="f2d35-250">A module string consists only of the name of the module or snap-in.</span></span> <span data-ttu-id="f2d35-251">模組雜湊表可包括 **ModuleName** 、 **ModuleVersion** 和 **GUID** 索引鍵。</span><span class="sxs-lookup"><span data-stu-id="f2d35-251">A module hash table can include **ModuleName** , **ModuleVersion** , and **GUID** keys.</span></span> <span data-ttu-id="f2d35-252">只有 **ModuleName** 索引鍵是必要的。</span><span class="sxs-lookup"><span data-stu-id="f2d35-252">Only the **ModuleName** key is required.</span></span>

<span data-ttu-id="f2d35-253">例如，以下的值包含字串和雜湊表。</span><span class="sxs-lookup"><span data-stu-id="f2d35-253">For example, the following value consists of a string and a hash table.</span></span> <span data-ttu-id="f2d35-254">字串或雜湊表以任何順序組成的任何組合都是有效的。</span><span class="sxs-lookup"><span data-stu-id="f2d35-254">Any combination of strings and hash tables, in any order, is valid.</span></span>

`'TroubleshootingPack', @{ModuleName='PSDiagnostics'; ModuleVersion='1.0.0.0';GUID='c61d6278-02a3-4618-ae37-a524d40a7f44'}`

<span data-ttu-id="f2d35-255">Cmdlet 的 **ModulesToImport** 參數值 `Register-PSSessionConfiguration` 優先順序高於會話設定檔中的 **ModulesToImport** 索引鍵值。</span><span class="sxs-lookup"><span data-stu-id="f2d35-255">The value of the **ModulesToImport** parameter of the `Register-PSSessionConfiguration` cmdlet takes precedence over the value of the **ModulesToImport** key in the session configuration file.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2d35-256">-MountUserDrive</span><span class="sxs-lookup"><span data-stu-id="f2d35-256">-MountUserDrive</span></span>

<span data-ttu-id="f2d35-257">設定使用此會話設定的會話，以公開 `User:` new-psdrive。</span><span class="sxs-lookup"><span data-stu-id="f2d35-257">Configures sessions that use this session configuration to expose the `User:` PSDrive.</span></span> <span data-ttu-id="f2d35-258">使用者磁片磁碟機對於每個連線的使用者都是唯一的，而且即使檔案系統提供者未公開，也可讓使用者在 PowerShell 端點之間複製資料。</span><span class="sxs-lookup"><span data-stu-id="f2d35-258">User drives are unique for each connecting user and allow users to copy data to and from PowerShell endpoints even if the File System provider is not exposed.</span></span> <span data-ttu-id="f2d35-259">建立使用者磁片磁碟機根目錄 `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\` 。</span><span class="sxs-lookup"><span data-stu-id="f2d35-259">User drive roots are created under `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\`.</span></span> <span data-ttu-id="f2d35-260">對於每位連線到端點的使用者，都會建立名為 `$env:USERDOMAIN_$env:USERNAME` 的資料夾。</span><span class="sxs-lookup"><span data-stu-id="f2d35-260">For each user connecting to the endpoint, a folder is created with the name `$env:USERDOMAIN_$env:USERNAME`.</span></span>

<span data-ttu-id="f2d35-261">使用者磁片磁碟機中的內容會在使用者會話中保存，且不會自動移除。</span><span class="sxs-lookup"><span data-stu-id="f2d35-261">Contents in the user drive persist across user sessions and are not automatically removed.</span></span> <span data-ttu-id="f2d35-262">根據預設，使用者只能在使用者磁片磁碟機中儲存最多50MB 的資料。</span><span class="sxs-lookup"><span data-stu-id="f2d35-262">By default, users can only store up to 50MB of data in the user drive.</span></span> <span data-ttu-id="f2d35-263">您可以使用 **UserDriveMaximumSize** 參數自訂此參數。</span><span class="sxs-lookup"><span data-stu-id="f2d35-263">This can be customized with the **UserDriveMaximumSize** parameter.</span></span>

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

### <span data-ttu-id="f2d35-264">-Path</span><span class="sxs-lookup"><span data-stu-id="f2d35-264">-Path</span></span>

<span data-ttu-id="f2d35-265">指定會話設定檔的路徑和檔案名。</span><span class="sxs-lookup"><span data-stu-id="f2d35-265">Specifies the path and filename of the session configuration file.</span></span> <span data-ttu-id="f2d35-266">檔案的副檔名必須是 `.pssc` 副檔名。</span><span class="sxs-lookup"><span data-stu-id="f2d35-266">The file must have a `.pssc` file name extension.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2d35-267">-PowerShellVersion</span><span class="sxs-lookup"><span data-stu-id="f2d35-267">-PowerShellVersion</span></span>

<span data-ttu-id="f2d35-268">在使用會話設定的會話中指定 PowerShell 引擎的版本。</span><span class="sxs-lookup"><span data-stu-id="f2d35-268">Specifies the version of the PowerShell engine in sessions that use the session configuration.</span></span> <span data-ttu-id="f2d35-269">此參數可接受的值為：2.0 和3.0。</span><span class="sxs-lookup"><span data-stu-id="f2d35-269">The acceptable values for this parameter are: 2.0 and 3.0.</span></span> <span data-ttu-id="f2d35-270">如果您省略此參數，則會將 **PowerShellVersion** 金鑰批註化，並在會話中執行最新版的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="f2d35-270">If you omit this parameter, the **PowerShellVersion** key is commented-out and newest version of PowerShell runs in the session.</span></span>

<span data-ttu-id="f2d35-271">Cmdlet 的 **PSVersion** 參數值 `Register-PSSessionConfiguration` 優先順序高於會話設定檔中的 **PowerShellVersion** 索引鍵值。</span><span class="sxs-lookup"><span data-stu-id="f2d35-271">The value of the **PSVersion** parameter of the `Register-PSSessionConfiguration` cmdlet takes precedence over the value of the **PowerShellVersion** key in the session configuration file.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2d35-272">-RequiredGroups</span><span class="sxs-lookup"><span data-stu-id="f2d35-272">-RequiredGroups</span></span>

<span data-ttu-id="f2d35-273">為連接到使用此會話設定之會話的使用者指定條件式存取規則。</span><span class="sxs-lookup"><span data-stu-id="f2d35-273">Specifies conditional access rules for users connecting to sessions that use this session configuration.</span></span>

<span data-ttu-id="f2d35-274">輸入雜湊表，以使用每個雜湊表 ' 和 ' 或 ' Or ' 的1個索引鍵來撰寫規則清單，然後將值設定為安全性群組名稱或其他雜湊表的陣列。</span><span class="sxs-lookup"><span data-stu-id="f2d35-274">Enter a hashtable to compose your list of rules using only 1 key per hashtable, 'And' or 'Or', and set the value to an array of security group names or additional hashtables.</span></span>

<span data-ttu-id="f2d35-275">要求將使用者連接到單一群組成員的範例： `@{ And = 'MyRequiredGroup' }`</span><span class="sxs-lookup"><span data-stu-id="f2d35-275">Example requiring connecting users to be members of a single group: `@{ And = 'MyRequiredGroup' }`</span></span>

<span data-ttu-id="f2d35-276">要求使用者屬於群組 A （或群組 B 和 C）以存取端點的範例： `@{ Or = 'GroupA', @{ And = 'GroupB', 'GroupC' } }`</span><span class="sxs-lookup"><span data-stu-id="f2d35-276">Example requiring users to belong to group A, or both groups B and C, to access the endpoint: `@{ Or = 'GroupA', @{ And = 'GroupB', 'GroupC' } }`</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2d35-277">-RoleDefinitions</span><span class="sxs-lookup"><span data-stu-id="f2d35-277">-RoleDefinitions</span></span>

<span data-ttu-id="f2d35-278">指定安全性群組 (或使用者) 與角色功能之間的對應。</span><span class="sxs-lookup"><span data-stu-id="f2d35-278">Specifies the mapping between security groups (or users) and role capabilities.</span></span> <span data-ttu-id="f2d35-279">使用者將被授與在會話建立時套用至其群組成員資格的所有角色功能的存取權。</span><span class="sxs-lookup"><span data-stu-id="f2d35-279">Users will be granted access to all role capabilities which apply to their group membership at the time the session is created.</span></span>

<span data-ttu-id="f2d35-280">輸入雜湊表，其中索引鍵為安全性群組的名稱，而值為雜湊表，其中包含應提供給安全性群組的角色功能清單。</span><span class="sxs-lookup"><span data-stu-id="f2d35-280">Enter a hash table in which the keys are the name of the security group and the values are hash tables that contain a list of role capabilities that should be made available to the security group.</span></span>

<span data-ttu-id="f2d35-281">例如：`@{'Contoso\Level 2 Helpdesk Users' = @{ RoleCapabilities = 'Maintenance', 'ADHelpDesk' }}`</span><span class="sxs-lookup"><span data-stu-id="f2d35-281">For example: `@{'Contoso\Level 2 Helpdesk Users' = @{ RoleCapabilities = 'Maintenance', 'ADHelpDesk' }}`</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2d35-282">-將 runasvirtualaccount 設</span><span class="sxs-lookup"><span data-stu-id="f2d35-282">-RunAsVirtualAccount</span></span>

<span data-ttu-id="f2d35-283">設定使用此會話設定的會話，以電腦的 (virtual) 系統管理員帳戶執行。</span><span class="sxs-lookup"><span data-stu-id="f2d35-283">Configures sessions using this session configuration to be run as the computer's (virtual) administrator account.</span></span> <span data-ttu-id="f2d35-284">這個欄位不能搭配 **msds-groupmanagedserviceaccount** 參數使用。</span><span class="sxs-lookup"><span data-stu-id="f2d35-284">This field cannot be used with the **GroupManagedServiceAccount** parameter.</span></span>

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

### <span data-ttu-id="f2d35-285">-RunAsVirtualAccountGroups</span><span class="sxs-lookup"><span data-stu-id="f2d35-285">-RunAsVirtualAccountGroups</span></span>

<span data-ttu-id="f2d35-286">當使用會話設定的會話以虛擬帳戶的形式執行時，指定要與虛擬帳戶相關聯的安全性群組。</span><span class="sxs-lookup"><span data-stu-id="f2d35-286">Specifies the security groups to be associated with the virtual account when a session that uses the session configuration is run as a virtual account.</span></span> <span data-ttu-id="f2d35-287">如果省略，虛擬帳戶屬於網域控制站上的 Domain Admins 和所有其他電腦上的系統管理員。</span><span class="sxs-lookup"><span data-stu-id="f2d35-287">If omitted, the virtual account belongs to Domain Admins on domain controllers and Administrators on all other computers.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2d35-288">-SchemaVersion</span><span class="sxs-lookup"><span data-stu-id="f2d35-288">-SchemaVersion</span></span>

<span data-ttu-id="f2d35-289">指定工作階段設定檔架構的版本。</span><span class="sxs-lookup"><span data-stu-id="f2d35-289">Specifies the version of the session configuration file schema.</span></span> <span data-ttu-id="f2d35-290">預設值為 "1.0.0.0"。</span><span class="sxs-lookup"><span data-stu-id="f2d35-290">The default value is "1.0.0.0".</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2d35-291">-ScriptsToProcess</span><span class="sxs-lookup"><span data-stu-id="f2d35-291">-ScriptsToProcess</span></span>

<span data-ttu-id="f2d35-292">將指定指令碼新增至使用工作階段設定的工作階段。</span><span class="sxs-lookup"><span data-stu-id="f2d35-292">Adds the specified scripts to sessions that use the session configuration.</span></span> <span data-ttu-id="f2d35-293">輸入指令碼的路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="f2d35-293">Enter the path and file names of the scripts.</span></span> <span data-ttu-id="f2d35-294">此參數的值必須是指令檔名的完整路徑或絕對路徑。</span><span class="sxs-lookup"><span data-stu-id="f2d35-294">The value of this parameter must be a full or absolute path of script file names.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2d35-295">-SessionType</span><span class="sxs-lookup"><span data-stu-id="f2d35-295">-SessionType</span></span>

<span data-ttu-id="f2d35-296">指定使用工作階段設定建立之工作階段的類型。</span><span class="sxs-lookup"><span data-stu-id="f2d35-296">Specifies the type of session that is created by using the session configuration.</span></span> <span data-ttu-id="f2d35-297">預設值為 Default。</span><span class="sxs-lookup"><span data-stu-id="f2d35-297">The default value is Default.</span></span> <span data-ttu-id="f2d35-298">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="f2d35-298">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="f2d35-299">空白-預設不會將任何模組新增至會話。</span><span class="sxs-lookup"><span data-stu-id="f2d35-299">Empty - No modules are added to session by default.</span></span> <span data-ttu-id="f2d35-300">使用此 Cmdlet 的參數將模組、函式、指令碼及其他功能新增至工作階段。</span><span class="sxs-lookup"><span data-stu-id="f2d35-300">Use the parameters of this cmdlet to add modules, functions, scripts, and other features to the session.</span></span> <span data-ttu-id="f2d35-301">此選項的設計目的是要讓您藉由新增選取的命令來建立自訂會話。</span><span class="sxs-lookup"><span data-stu-id="f2d35-301">This option is designed for you to create custom sessions by adding selected commands.</span></span> <span data-ttu-id="f2d35-302">如果您沒有新增命令至空的工作階段，工作階段會限制只能使用運算式，因此可能無法使用。</span><span class="sxs-lookup"><span data-stu-id="f2d35-302">If you do not add commands to an empty session, the session is limited to expressions and might not be usable.</span></span>
- <span data-ttu-id="f2d35-303">預設值-將 Microsoft. Core 模組新增至會話。</span><span class="sxs-lookup"><span data-stu-id="f2d35-303">Default - Adds the Microsoft.PowerShell.Core module to the session.</span></span> <span data-ttu-id="f2d35-304">此模組包含 `Import-Module` 使用者可以用來匯入其他模組的 Cmdlet，除非您明確禁止此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f2d35-304">This module includes the `Import-Module` cmdlet that users can use to import other modules unless you explicitly prohibit this cmdlet.</span></span>
- <span data-ttu-id="f2d35-305">RestrictedRemoteServer.</span><span class="sxs-lookup"><span data-stu-id="f2d35-305">RestrictedRemoteServer.</span></span> <span data-ttu-id="f2d35-306">只包含下列 proxy 函數： `Exit-PSSession` 、 `Get-Command` 、 `Get-FormatData` 、 `Get-Help` 、 `Measure-Object` 、 `Out-Default` 和 `Select-Object` 。</span><span class="sxs-lookup"><span data-stu-id="f2d35-306">Includes only the following proxy functions: `Exit-PSSession`, `Get-Command`, `Get-FormatData`, `Get-Help`, `Measure-Object`, `Out-Default`, and `Select-Object`.</span></span>
  <span data-ttu-id="f2d35-307">使用此 Cmdlet 的參數將模組、函式、指令碼及其他功能新增至工作階段。</span><span class="sxs-lookup"><span data-stu-id="f2d35-307">Use the parameters of this cmdlet to add modules, functions, scripts, and other features to the session.</span></span>

```yaml
Type: System.Management.Automation.Remoting.SessionType
Parameter Sets: (All)
Aliases:
Accepted values: Empty, RestrictedRemoteServer, Default

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2d35-308">-TranscriptDirectory</span><span class="sxs-lookup"><span data-stu-id="f2d35-308">-TranscriptDirectory</span></span>

<span data-ttu-id="f2d35-309">指定使用此會話設定為會話放置會話文字記錄的目錄。</span><span class="sxs-lookup"><span data-stu-id="f2d35-309">Specifies the directory to place session transcripts for sessions using this session configuration.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2d35-310">-TypesToProcess</span><span class="sxs-lookup"><span data-stu-id="f2d35-310">-TypesToProcess</span></span>

<span data-ttu-id="f2d35-311">將指定的 `.ps1xml` 類型檔案加入至使用會話設定的會話。</span><span class="sxs-lookup"><span data-stu-id="f2d35-311">Adds the specified `.ps1xml` type files to sessions that use the session configuration.</span></span> <span data-ttu-id="f2d35-312">輸入類型檔案名。</span><span class="sxs-lookup"><span data-stu-id="f2d35-312">Enter the type filenames.</span></span> <span data-ttu-id="f2d35-313">此參數的值必須是類型檔案名的完整路徑或絕對路徑。</span><span class="sxs-lookup"><span data-stu-id="f2d35-313">The value of this parameter must be a full or absolute path to type filenames.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2d35-314">-UserDriveMaximumSize</span><span class="sxs-lookup"><span data-stu-id="f2d35-314">-UserDriveMaximumSize</span></span>

<span data-ttu-id="f2d35-315">指定在使用此會話設定的會話中，所公開使用者磁片磁碟機的大小上限。</span><span class="sxs-lookup"><span data-stu-id="f2d35-315">Specifies the maximum size for user drives exposed in sessions that use this session configuration.</span></span>
<span data-ttu-id="f2d35-316">若省略，則會50MB 每個 `User:` 磁片磁碟機根目錄的預設大小。</span><span class="sxs-lookup"><span data-stu-id="f2d35-316">When omitted, the default size of each `User:` drive root is 50MB.</span></span>

<span data-ttu-id="f2d35-317">此參數應與 **MountUserDrive** 搭配使用。</span><span class="sxs-lookup"><span data-stu-id="f2d35-317">This parameter should be used with **MountUserDrive** .</span></span>

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2d35-318">-VariableDefinitions</span><span class="sxs-lookup"><span data-stu-id="f2d35-318">-VariableDefinitions</span></span>

<span data-ttu-id="f2d35-319">將指定變數新增至使用工作階段設定的工作階段。</span><span class="sxs-lookup"><span data-stu-id="f2d35-319">Adds the specified variables to sessions that use the session configuration.</span></span> <span data-ttu-id="f2d35-320">輸入包含下列索引鍵的雜湊表：</span><span class="sxs-lookup"><span data-stu-id="f2d35-320">Enter a hash table with the following keys:</span></span>

- <span data-ttu-id="f2d35-321">名稱：變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="f2d35-321">Name - Name of the variable.</span></span> <span data-ttu-id="f2d35-322">此為必要索引鍵。</span><span class="sxs-lookup"><span data-stu-id="f2d35-322">This key is required.</span></span>
- <span data-ttu-id="f2d35-323">值變數值。</span><span class="sxs-lookup"><span data-stu-id="f2d35-323">Value - Variable value.</span></span> <span data-ttu-id="f2d35-324">此為必要索引鍵。</span><span class="sxs-lookup"><span data-stu-id="f2d35-324">This key is required.</span></span>
- <span data-ttu-id="f2d35-325">選項-變數選項。</span><span class="sxs-lookup"><span data-stu-id="f2d35-325">Options - Variable options.</span></span> <span data-ttu-id="f2d35-326">此為選擇性索引鍵。</span><span class="sxs-lookup"><span data-stu-id="f2d35-326">This key is optional.</span></span> <span data-ttu-id="f2d35-327">預設值為 **None** 。</span><span class="sxs-lookup"><span data-stu-id="f2d35-327">The default value is **None** .</span></span> <span data-ttu-id="f2d35-328">此參數可接受的值為： None、ReadOnly、常數、私用或 AllScope。</span><span class="sxs-lookup"><span data-stu-id="f2d35-328">The acceptable values for this parameter are: None, ReadOnly, Constant, Private, or AllScope.</span></span>

<span data-ttu-id="f2d35-329">例如：`@{Name='WarningPreference';Value='SilentlyContinue';Options='AllScope'}`</span><span class="sxs-lookup"><span data-stu-id="f2d35-329">For example: `@{Name='WarningPreference';Value='SilentlyContinue';Options='AllScope'}`</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2d35-330">-Visiblealiase</span><span class="sxs-lookup"><span data-stu-id="f2d35-330">-VisibleAliases</span></span>

<span data-ttu-id="f2d35-331">將工作階段中的別名限制為此參數的值中指定的別名，以及您在 **AliasDefinition** 參數中定義的任何別名。</span><span class="sxs-lookup"><span data-stu-id="f2d35-331">Limits the aliases in the session to those specified in the value of this parameter, plus any aliases that you define in the **AliasDefinition** parameter.</span></span> <span data-ttu-id="f2d35-332">支援使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="f2d35-332">Wildcard characters are supported.</span></span> <span data-ttu-id="f2d35-333">根據預設，會話中會顯示所有由 PowerShell 引擎定義的別名，以及模組匯出的所有別名。</span><span class="sxs-lookup"><span data-stu-id="f2d35-333">By default, all aliases that are defined by the PowerShell engine and all aliases that modules export are visible in the session.</span></span>

<span data-ttu-id="f2d35-334">例如：`VisibleAliases='gcm', 'gp'`</span><span class="sxs-lookup"><span data-stu-id="f2d35-334">For example: `VisibleAliases='gcm', 'gp'`</span></span>

<span data-ttu-id="f2d35-335">當會話設定檔中包含任何 **可見** 的參數時，PowerShell 會 `Import-Module` 從會話中移除此 Cmdlet 和其 ipmo 別名。</span><span class="sxs-lookup"><span data-stu-id="f2d35-335">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its ipmo alias from the session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="f2d35-336">-VisibleCmdlets</span><span class="sxs-lookup"><span data-stu-id="f2d35-336">-VisibleCmdlets</span></span>

<span data-ttu-id="f2d35-337">將工作階段中的 Cmdlet 限制為此參數的值中指定的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f2d35-337">Limits the cmdlets in the session to those specified in the value of this parameter.</span></span> <span data-ttu-id="f2d35-338">支援萬用字元和模組限定名稱。</span><span class="sxs-lookup"><span data-stu-id="f2d35-338">Wildcard characters and Module Qualified Names are supported.</span></span>

<span data-ttu-id="f2d35-339">根據預設，在工作階段中可以看見工作階段中的模組匯出的所有 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f2d35-339">By default, all cmdlets that modules in the session export are visible in the session.</span></span> <span data-ttu-id="f2d35-340">使用 **SessionType** 和 **ModulesToImport** 參數決定要在工作階段中匯入哪些模組和嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="f2d35-340">Use the **SessionType** and **ModulesToImport** parameters to determine which modules and snap-ins are imported into the session.</span></span> <span data-ttu-id="f2d35-341">如果 **ModulesToImport** 中沒有任何模組公開 Cmdlet，則會嘗試自動載入適當的模組。</span><span class="sxs-lookup"><span data-stu-id="f2d35-341">If no modules in **ModulesToImport** expose the cmdlet, the appropriate module will attempt to be autoloaded.</span></span>

<span data-ttu-id="f2d35-342">當會話設定檔中包含任何 **可見** 的參數時，PowerShell 會 `Import-Module` 從會話中移除此 Cmdlet 和其 ipmo 別名。</span><span class="sxs-lookup"><span data-stu-id="f2d35-342">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its ipmo alias from the session.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2d35-343">-了 visibleexternalcommands</span><span class="sxs-lookup"><span data-stu-id="f2d35-343">-VisibleExternalCommands</span></span>

<span data-ttu-id="f2d35-344">將會話中可執行檔外部二進位檔、腳本和命令限制為此參數值中指定的二進位檔、腳本和命令。</span><span class="sxs-lookup"><span data-stu-id="f2d35-344">Limits the external binaries, scripts, and commands that can be executed in the session to those specified in the value of this parameter.</span></span> <span data-ttu-id="f2d35-345">支援使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="f2d35-345">Wildcard characters are supported.</span></span>

<span data-ttu-id="f2d35-346">依預設，會話中不會顯示任何外部命令。</span><span class="sxs-lookup"><span data-stu-id="f2d35-346">By default, no external commands are visible in the session.</span></span>

<span data-ttu-id="f2d35-347">當會話設定檔中包含任何 **可見** 的參數時，PowerShell 會 `Import-Module` 從會話中移除 Cmdlet 和其 ipmo 別名。</span><span class="sxs-lookup"><span data-stu-id="f2d35-347">When any **Visible** parameter is included in the session configuration file, PowerShell, removes the `Import-Module` cmdlet and its ipmo alias from the session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="f2d35-348">-VisibleFunctions</span><span class="sxs-lookup"><span data-stu-id="f2d35-348">-VisibleFunctions</span></span>

<span data-ttu-id="f2d35-349">將工作階段中的函式限制為此參數的值中指定的函式，以及您在 **FunctionDefinition** 參數中定義的任何函式。</span><span class="sxs-lookup"><span data-stu-id="f2d35-349">Limits the functions in the session to those specified in the value of this parameter, plus any functions that you define in the **FunctionDefinition** parameter.</span></span> <span data-ttu-id="f2d35-350">支援使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="f2d35-350">Wildcard characters are supported.</span></span>

<span data-ttu-id="f2d35-351">根據預設，在工作階段中可以看見工作階段中的模組匯出的所有函式。</span><span class="sxs-lookup"><span data-stu-id="f2d35-351">By default, all functions that modules in the session export are visible in the session.</span></span> <span data-ttu-id="f2d35-352">使用 **SessionType** 和 **ModulesToImport** 參數決定要在工作階段中匯入哪些模組和嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="f2d35-352">Use the **SessionType** and **ModulesToImport** parameters to determine which modules and snap-ins are imported into the session.</span></span>

<span data-ttu-id="f2d35-353">當會話設定檔中包含任何 **可見** 的參數時，PowerShell 會 `Import-Module` 從會話中移除此 Cmdlet 和其 ipmo 別名。</span><span class="sxs-lookup"><span data-stu-id="f2d35-353">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its ipmo alias from the session.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="f2d35-354">-VisibleProviders</span><span class="sxs-lookup"><span data-stu-id="f2d35-354">-VisibleProviders</span></span>

<span data-ttu-id="f2d35-355">將會話中的 PowerShell 提供者限制為此參數的值中指定的提供者。</span><span class="sxs-lookup"><span data-stu-id="f2d35-355">Limits the PowerShell providers in the session to those specified in the value of this parameter.</span></span>
<span data-ttu-id="f2d35-356">支援使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="f2d35-356">Wildcard characters are supported.</span></span>

<span data-ttu-id="f2d35-357">根據預設，在工作階段中可以看見工作階段中的模組匯出的所有提供者。</span><span class="sxs-lookup"><span data-stu-id="f2d35-357">By default, all providers that modules in the session export are visible in the session.</span></span> <span data-ttu-id="f2d35-358">您可以使用 **SessionType** 和 **ModulesToImport** 參數來判斷要將哪些模組匯入到會話中。</span><span class="sxs-lookup"><span data-stu-id="f2d35-358">Use the **SessionType** and **ModulesToImport** parameters to determine which modules are imported into the session.</span></span>

<span data-ttu-id="f2d35-359">當會話設定檔中包含任何 **可見** 的參數時，PowerShell 會 `Import-Module` 從會話中移除該 Cmdlet 和其 `ipmo` 別名。</span><span class="sxs-lookup"><span data-stu-id="f2d35-359">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="f2d35-360">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f2d35-360">CommonParameters</span></span>

<span data-ttu-id="f2d35-361">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="f2d35-361">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f2d35-362">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="f2d35-362">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f2d35-363">輸入</span><span class="sxs-lookup"><span data-stu-id="f2d35-363">INPUTS</span></span>

### <span data-ttu-id="f2d35-364">無</span><span class="sxs-lookup"><span data-stu-id="f2d35-364">None</span></span>

<span data-ttu-id="f2d35-365">您無法透過管線將任何物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f2d35-365">You cannot pipe any objects to this cmdlet.</span></span>

## <span data-ttu-id="f2d35-366">輸出</span><span class="sxs-lookup"><span data-stu-id="f2d35-366">OUTPUTS</span></span>

### <span data-ttu-id="f2d35-367">無</span><span class="sxs-lookup"><span data-stu-id="f2d35-367">None</span></span>

<span data-ttu-id="f2d35-368">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="f2d35-368">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="f2d35-369">注意</span><span class="sxs-lookup"><span data-stu-id="f2d35-369">NOTES</span></span>

- <span data-ttu-id="f2d35-370">參數（例如 **VisibleCmdlets** 和 **VisibleProviders** ）不會將專案匯入到會話中。</span><span class="sxs-lookup"><span data-stu-id="f2d35-370">Parameters, such as **VisibleCmdlets** and **VisibleProviders** , do not import items into the session.</span></span> <span data-ttu-id="f2d35-371">而是會從匯入工作階段的項目中選取。</span><span class="sxs-lookup"><span data-stu-id="f2d35-371">Instead, they select from among the items imported into the session.</span></span> <span data-ttu-id="f2d35-372">例如，如果 **VisibleProviders** 參數的值為 certificate 提供者，但 **ModulesToImport** 參數未指定包含憑證提供者的 **安全性** 模組，則會話中不會顯示憑證提供者。</span><span class="sxs-lookup"><span data-stu-id="f2d35-372">For example, if the value of the **VisibleProviders** parameter is the Certificate provider, but the **ModulesToImport** parameter does not specify the **Microsoft.PowerShell.Security** module that contains the Certificate provider, the Certificate provider is not visible in the session.</span></span>
- <span data-ttu-id="f2d35-373">`New-PSSessionConfigurationFile` 在您于 **path** 參數中指定的路徑中，建立副檔名為 .pssc 的會話設定檔。</span><span class="sxs-lookup"><span data-stu-id="f2d35-373">`New-PSSessionConfigurationFile` creates a session configuration file that has a .pssc file name extension in the path that you specify in the **Path** parameter.</span></span> <span data-ttu-id="f2d35-374">當您使用會話設定檔建立會話設定時，此 Cmdlet 會 `Register-PSSessionConfiguration` 複製設定檔，並將檔案的使用中複本儲存在目錄的 **SessionConfig** 子目錄中 `$PSHOME` 。</span><span class="sxs-lookup"><span data-stu-id="f2d35-374">When you use the session configuration file to create a session configuration, the `Register-PSSessionConfiguration` cmdlet copies the configuration file and saves an active copy of the file in the **SessionConfig** subdirectory of the `$PSHOME` directory.</span></span>

  <span data-ttu-id="f2d35-375">會話設定的 **ConfigFilePath** 屬性包含使用中會話設定檔的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="f2d35-375">The **ConfigFilePath** property of the session configuration contains the fully qualified path of the active session configuration file.</span></span> <span data-ttu-id="f2d35-376">您可以隨時 `$PSHOME` 使用任何文字編輯器來修改目錄中的使用中設定檔。</span><span class="sxs-lookup"><span data-stu-id="f2d35-376">You can modify the active configuration file in the `$PSHOME` directory at any time using any text editor.</span></span> <span data-ttu-id="f2d35-377">您所做的變更會影響所有使用工作階段設定的新工作階段，但不會影響現有的工作階段。</span><span class="sxs-lookup"><span data-stu-id="f2d35-377">The changes that you make affect all new sessions that use the session configuration, but not existing sessions.</span></span>

  <span data-ttu-id="f2d35-378">使用已編輯的會話設定檔之前，請使用 `Test-PSSessionConfigurationFile` Cmdlet 來確認設定檔案專案是否有效。</span><span class="sxs-lookup"><span data-stu-id="f2d35-378">Before using an edited session configuration file, use the `Test-PSSessionConfigurationFile` cmdlet to verify that the configuration file entries are valid.</span></span>

## <span data-ttu-id="f2d35-379">相關連結</span><span class="sxs-lookup"><span data-stu-id="f2d35-379">RELATED LINKS</span></span>

[<span data-ttu-id="f2d35-380">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="f2d35-380">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="f2d35-381">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="f2d35-381">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="f2d35-382">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="f2d35-382">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="f2d35-383">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="f2d35-383">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="f2d35-384">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="f2d35-384">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="f2d35-385">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="f2d35-385">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="f2d35-386">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="f2d35-386">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="f2d35-387">WSMan 提供者</span><span class="sxs-lookup"><span data-stu-id="f2d35-387">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="f2d35-388">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="f2d35-388">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="f2d35-389">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="f2d35-389">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)
