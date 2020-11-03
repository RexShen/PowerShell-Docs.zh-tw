---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssessionconfiguration?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSessionConfiguration
ms.openlocfilehash: 300fc3dee2e0d625e5aea42bfdcf45ea2e8b5a7f
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205675"
---
# <span data-ttu-id="0f17c-103">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="0f17c-103">Get-PSSessionConfiguration</span></span>

## <span data-ttu-id="0f17c-104">概要</span><span class="sxs-lookup"><span data-stu-id="0f17c-104">SYNOPSIS</span></span>
<span data-ttu-id="0f17c-105">取得電腦上已登錄的工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="0f17c-105">Gets the registered session configurations on the computer.</span></span>

## <span data-ttu-id="0f17c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0f17c-106">SYNTAX</span></span>

```
Get-PSSessionConfiguration [[-Name] <String[]>] [-Force] [<CommonParameters>]
```

## <span data-ttu-id="0f17c-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0f17c-107">DESCRIPTION</span></span>

<span data-ttu-id="0f17c-108">此 `Get-PSSessionConfiguration` Cmdlet 會取得已在本機電腦上註冊的會話設定。</span><span class="sxs-lookup"><span data-stu-id="0f17c-108">The `Get-PSSessionConfiguration` cmdlet gets the session configurations that have been registered on the local computer.</span></span> <span data-ttu-id="0f17c-109">這是一個進階的 Cmdlet，專門設計給系統管理員用於管理其使用者的自訂工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="0f17c-109">This is an advanced cmdlet that is designed to be used by system administrators to manage customized session configurations for their users.</span></span>

<span data-ttu-id="0f17c-110">從 PowerShell 3.0 開始，您可以使用會話設定 ( .pssc) 檔來定義會話設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="0f17c-110">Beginning in PowerShell 3.0, you can define the properties of a session configuration by using a session configuration (.pssc) file.</span></span> <span data-ttu-id="0f17c-111">此功能可讓您不必撰寫電腦程式，就能建立自訂且受限制的工作階段。</span><span class="sxs-lookup"><span data-stu-id="0f17c-111">This feature lets you create customized and restricted sessions without writing a computer program.</span></span> <span data-ttu-id="0f17c-112">如需有關工作階段設定檔的詳細資訊，請參閱 [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)。</span><span class="sxs-lookup"><span data-stu-id="0f17c-112">For more information about session configuration files, see [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span></span>

<span data-ttu-id="0f17c-113">此外，從 PowerShell 3.0 開始，已將新的附注屬性新增至傳回的會話設定物件 `Get-PSSessionConfiguration` 。</span><span class="sxs-lookup"><span data-stu-id="0f17c-113">Also, beginning in PowerShell 3.0, new note properties have been added to the session configuration object that `Get-PSSessionConfiguration` returns.</span></span> <span data-ttu-id="0f17c-114">這些屬性讓使用者和工作階段設定作者，能夠更輕鬆地檢查和比較工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="0f17c-114">These properties make it easier for users and session configuration authors to examine and compare session configurations.</span></span>

<span data-ttu-id="0f17c-115">若要建立並註冊會話設定，請使用 `Register-PSSessionConfiguration` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0f17c-115">To create and register a session configuration, use the `Register-PSSessionConfiguration` cmdlet.</span></span>
<span data-ttu-id="0f17c-116">如需會話設定的詳細資訊，請參閱 [about_Session_Configurations](About/about_Session_Configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="0f17c-116">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

## <span data-ttu-id="0f17c-117">範例</span><span class="sxs-lookup"><span data-stu-id="0f17c-117">EXAMPLES</span></span>

### <span data-ttu-id="0f17c-118">範例 1-取得本機電腦上的會話設定</span><span class="sxs-lookup"><span data-stu-id="0f17c-118">Example 1 - Get session configurations on the local computer</span></span>

```powershell
Get-PSSessionConfiguration
```

### <span data-ttu-id="0f17c-119">範例 2-取得兩個預設會話設定</span><span class="sxs-lookup"><span data-stu-id="0f17c-119">Example 2 - Get the two default session configurations</span></span>

<span data-ttu-id="0f17c-120">命令使用的 **Name** 參數 `Get-PSSessionConfiguration` ，只取得名稱開頭為 "Microsoft" 的會話設定。</span><span class="sxs-lookup"><span data-stu-id="0f17c-120">The command uses the **Name** parameter of `Get-PSSessionConfiguration` to get only the session configurations with names that begin with "Microsoft".</span></span>

```powershell
Get-PSSessionConfiguration -Name Microsoft*
```

```Output
Name                      PSVersion  StartupScript        Permission
----                      ---------  -------------        ----------
microsoft.powershell      5.1                             BUILTIN\Administrators AccessAll...
microsoft.powershell32    5.1                             BUILTIN\Administrators AccessAll...
```

### <span data-ttu-id="0f17c-121">範例 3-取得會話設定的屬性和值</span><span class="sxs-lookup"><span data-stu-id="0f17c-121">Example 3 - Get the properties and values of a session configuration</span></span>

<span data-ttu-id="0f17c-122">此範例示範使用工作階段設定檔建立工作階段設定的屬性和屬性值。</span><span class="sxs-lookup"><span data-stu-id="0f17c-122">This example shows the properties and property values of a session configuration that was created by using a session configuration file.</span></span>

```powershell
Get-PSSessionConfiguration -Name Full  | Format-List -Property *
```

```Output
Copyright                     : (c) 2011 User01. All rights reserved.
AliasDefinitions              : {System.Collections.Hashtable}
SessionType                   : Default
CompanyName                   : Unknown
GUID                          : 1e9cb265-dae0-4bd3-89a9-8338a47698a1
Author                        : User01
ExecutionPolicy               : Restricted
SchemaVersion                 : 1.0.0.0
LanguageMode                  : FullLanguage
Architecture                  : 64
Filename                      : %windir%\system32\pwrshplugin.dll
ResourceUri                   : http://schemas.microsoft.com/powershell/Full
MaxConcurrentCommandsPerShell : 1500
UseSharedProcess              : false
ProcessIdleTimeoutSec         : 0
xmlns                         : http://schemas.microsoft.com/wbem/wsman/1/config/PluginConfiguration
MaxConcurrentUsers            : 10
lang                          : en-US
SupportsOptions               : true
ExactMatch                    : true
configfilepath                : C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\Full_1e9cb265-dae0-4bd3-89a9-8338a47698a1.pssc
RunAsUser                     :
IdleTimeoutms                 : 7200000
PSVersion                     : 3.0
OutputBufferingMode           : Block
AutoRestart                   : false
MaxShells                     : 300
MaxMemoryPerShellMB           : 1024
MaxIdleTimeoutms              : 43200000
SDKVersion                    : 1
Name                          : Full
XmlRenderingType              : text
Capability                    : {Shell}
RunAsPassword                 :
MaxProcessesPerShell          : 25
Enabled                       : True
MaxShellsPerUser              : 30
Permission                    :
```

<span data-ttu-id="0f17c-123">此範例會使用 `Get-PSSessionConfiguration` Cmdlet 來取得完整的會話設定。</span><span class="sxs-lookup"><span data-stu-id="0f17c-123">The example uses the `Get-PSSessionConfiguration` cmdlet to get the full session configuration.</span></span> <span data-ttu-id="0f17c-124">管線運算子會將完整會話設定傳送至 `Format-List` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0f17c-124">A pipeline operator sends the Full session configuration to the `Format-List` cmdlet.</span></span> <span data-ttu-id="0f17c-125">**Property** 參數的值為 `*` (all) 會指示 `Format-List` 在清單中顯示物件的所有屬性和值。</span><span class="sxs-lookup"><span data-stu-id="0f17c-125">The **Property** parameter with a value of `*` (all) directs `Format-List` to display all the properties and values of the object in a list.</span></span>

<span data-ttu-id="0f17c-126">輸出中會包含有用的資訊，包括會話設定的作者、會話類型、語言模式，以及使用此會話設定建立之會話的執行原則、會話配額和會話設定檔的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="0f17c-126">The output includes useful information, including the author of the session configuration, the session type, language mode, and execution policy of sessions that are created with this session configuration, session quotas, and the full path to the session configuration file.</span></span>

<span data-ttu-id="0f17c-127">此工作階段設定的檢視可用於包含工作階段設定檔的工作階段。</span><span class="sxs-lookup"><span data-stu-id="0f17c-127">This view of a session configuration is used for sessions that include a session configuration file.</span></span>
<span data-ttu-id="0f17c-128">如需有關工作階段設定檔的詳細資訊，請參閱 [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)。</span><span class="sxs-lookup"><span data-stu-id="0f17c-128">For more information about session configuration files, see [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span></span>

### <span data-ttu-id="0f17c-129">範例 4-查看會話設定的另一種方式</span><span class="sxs-lookup"><span data-stu-id="0f17c-129">Example 4 - Another way to look at the session configurations</span></span>

<span data-ttu-id="0f17c-130">此範例會使用 `Get-ChildItem` `dir` WSMan： provider 磁片磁碟機中的 Cmdlet (別名) 來查看外掛程式節點的內容。</span><span class="sxs-lookup"><span data-stu-id="0f17c-130">This example uses the `Get-ChildItem` cmdlet (alias `dir`) in the WSMan: provider drive to look at the content of the Plugin node.</span></span> <span data-ttu-id="0f17c-131">這是另一個檢視電腦上工作階段設定的方法。</span><span class="sxs-lookup"><span data-stu-id="0f17c-131">This is another way to look at the session configurations on the computer.</span></span>

```powershell
dir wsman:\localhost\plugin
```

```Output
Type            Keys                                Name
----            ----                                ----
Container       {Name=Event Forwarding Plugin}      Event Forwarding Plugin
Container       {Name=Full}                         Full
Container       {Name=microsoft.powershell}         microsoft.powershell
Container       {Name=microsoft.powershell.workf... microsoft.powershell.workflow
Container       {Name=microsoft.powershell32}       microsoft.powershell32
Container       {Name=microsoft.ServerManager}      microsoft.ServerManager
Container       {Name=WMI Provider}                 WMI Provider
```

<span data-ttu-id="0f17c-132">**外掛程式** 節點包含 **ContainerElement** 物件 (WSManConfigContainerElement) ，代表已註冊的 PowerShell 會話設定，以及適用于 ws-management 的其他外掛程式。</span><span class="sxs-lookup"><span data-stu-id="0f17c-132">The **PlugIn** node contains **ContainerElement** objects (Microsoft.WSMan.Management.WSManConfigContainerElement) that represent the registered PowerShell session configurations, along with other plug-ins for WS-Management.</span></span>

### <span data-ttu-id="0f17c-133">範例 6-查看遠端電腦上的會話設定</span><span class="sxs-lookup"><span data-stu-id="0f17c-133">Example 6 - View session configurations on a remote computer</span></span>

<span data-ttu-id="0f17c-134">此範例示範如何使用 WSMan 提供者檢視遠端電腦上的工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="0f17c-134">This example shows how to use the WSMan provider to view the session configurations on a remote computer.</span></span> <span data-ttu-id="0f17c-135">這個方法不會提供與命令一樣多的資訊 `Get-PSSessionConfiguration` ，但使用者不需要是 Administrators 群組的成員就能執行這個 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0f17c-135">This method does not provide as much information as a `Get-PSSessionConfiguration` command, but the user does not need to be a member of the Administrators group to run this cmdlet.</span></span>

```powershell
Connect-WSMan -ComputerName Server01
dir WSMan:\Server01\Plugin
```

```Output
   WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin

Type            Keys                                Name
----            ----                                ----
Container       {Name=Empty}                        Empty
Container       {Name=Event Forwarding Plugin}      Event Forwarding Plugin
Container       {Name=Full}                         Full
Container       {Name=microsoft.powershell}         microsoft.powershell
Container       {Name=microsoft.powershell.workf... microsoft.powershell.workflow
Container       {Name=microsoft.powershell32}       microsoft.powershell32
Container       {Name=microsoft.ServerManager}      microsoft.ServerManager
Container       {Name=NoLanguage}                   NoLanguage
Container       {Name=RestrictedLang}               RestrictedLang
Container       {Name=RRS}                          RRS
Container       {Name=SEL Plugin}                   SEL Plugin
Container       {Name=WithProfile}                  WithProfile
Container       {Name=WMI Provider}                 WMI Provider
```

<span data-ttu-id="0f17c-136">`Connect-WSMan`Cmdlet 會連接到 Server01 遠端電腦上的 WinRM 服務。</span><span class="sxs-lookup"><span data-stu-id="0f17c-136">The `Connect-WSMan` cmdlet connects to the WinRM service on the Server01 remote computer.</span></span> <span data-ttu-id="0f17c-137">`Get-ChildItem` `dir` WSMan：磁片磁碟機 (別名) 的 Cmdlet 會取得 **Server01\Plugin** 路徑中的專案。</span><span class="sxs-lookup"><span data-stu-id="0f17c-137">The `Get-ChildItem` cmdlet (alias `dir`) of the WSMan: drive gets the items in the **Server01\Plugin** path.</span></span> <span data-ttu-id="0f17c-138">輸出會顯示 Server01 電腦上 Plugin 目錄中的項目。</span><span class="sxs-lookup"><span data-stu-id="0f17c-138">The output shows the items in the Plugin directory on the Server01 computer.</span></span> <span data-ttu-id="0f17c-139">此項目包含工作階段設定 (一種 WSMan 外掛程式) 及電腦上其他類型的外掛程式。</span><span class="sxs-lookup"><span data-stu-id="0f17c-139">The items include the session configurations, which are a type of WSMan plug-in, along with other types of plug-ins on the computer.</span></span>

### <span data-ttu-id="0f17c-140">範例 7-從遠端電腦取得詳細的會話設定</span><span class="sxs-lookup"><span data-stu-id="0f17c-140">Example 7 - Get detailed session configurations from a remote computer</span></span>

<span data-ttu-id="0f17c-141">此範例顯示如何 `Get-PSSessionConfiguration` 在遠端電腦上執行命令。</span><span class="sxs-lookup"><span data-stu-id="0f17c-141">This example shows how to run a `Get-PSSessionConfiguration` command on a remote computer.</span></span> <span data-ttu-id="0f17c-142">此命令會要求在本機電腦上的用戶端設定及遠端電腦上的服務設定中啟用 CredSSP 委派。</span><span class="sxs-lookup"><span data-stu-id="0f17c-142">The command requires that CredSSP delegation be enabled in the client settings on the local computer and in the service settings on the remote computer.</span></span>

<span data-ttu-id="0f17c-143">若要執行此範例中的命令，您必須是本機電腦和遠端電腦上 Administrators 群組的成員，而且必須使用 [以 **系統管理員身分執行** ] 選項啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="0f17c-143">To run the commands in this example, you must be a member of the Administrators group on the local and remote computers and you must start PowerShell with the **Run as administrator** option.</span></span>

```powershell
Enable-WSManCredSSP -Delegate Server02
Connect-WSMan Server02
Set-Item WSMan:\Server02*\Service\Auth\CredSSP -Value $true
Invoke-Command -ScriptBlock {Get-PSSessionConfiguration} -ComputerName Server02 -Authentication CredSSP -Credential Domain01\Admin01
```

```Output
Name                      PSVersion  StartupScript        Permission                          PSComputerName
----                      ---------  -------------        ----------                          --------------
microsoft.powershell      5.1                             BUILTIN\Administrators AccessAll... server02.corp.fabrikam.com
microsoft.powershell32    5.1                             BUILTIN\Administrators AccessAll... server02.corp.fabrikam.com
MyX86Shell                5.1        c:\test\x86Shell.ps1 BUILTIN\Administrators AccessAll... server02.corp.fabrikam.com
```

<span data-ttu-id="0f17c-144">此 `Enable-WSManCredSSP` Cmdlet 會在本機電腦上啟用 **CredSSP** 委派 Server01。</span><span class="sxs-lookup"><span data-stu-id="0f17c-144">The `Enable-WSManCredSSP` cmdlet enables **CredSSP** delegation on Server01, the local computer.</span></span> <span data-ttu-id="0f17c-145">`Connect-WSMan`Cmdlet 會連接到 Server02 電腦。</span><span class="sxs-lookup"><span data-stu-id="0f17c-145">The `Connect-WSMan` cmdlet connects to Server02 computer.</span></span> <span data-ttu-id="0f17c-146">此動作會將 Server02 的節點新增至本機電腦上的 WSMan：磁片磁碟機，讓您可以查看和變更 Server02 電腦上的 WS-Management 設定。</span><span class="sxs-lookup"><span data-stu-id="0f17c-146">This action adds a node for Server02 to the WSMan: drive on the local computer, allowing you to view and change the WS-Management settings on the Server02 computer.</span></span> <span data-ttu-id="0f17c-147">此 `Set-Item` Cmdlet 會將 Server02 電腦服務節點中的 **CredSSP** 專案值變更為 **True** 。</span><span class="sxs-lookup"><span data-stu-id="0f17c-147">The `Set-Item` cmdlet changes the value of the **CredSSP** item in the Service node of the Server02 computer to **True** .</span></span> <span data-ttu-id="0f17c-148">這會設定遠端電腦上的服務設定。</span><span class="sxs-lookup"><span data-stu-id="0f17c-148">This configures the service settings on the remote computer.</span></span> <span data-ttu-id="0f17c-149">此 `Invoke-Command` Cmdlet 會 `Get-PSSessionConfiguration` 在 Server02 電腦上執行命令。</span><span class="sxs-lookup"><span data-stu-id="0f17c-149">The `Invoke-Command` cmdlet runs the`Get-PSSessionConfiguration` command on the Server02 computer.</span></span> <span data-ttu-id="0f17c-150">此命令使用 **Credential** 參數，並且使用 **Authentication** 參數搭配 **CredSSP** 值。</span><span class="sxs-lookup"><span data-stu-id="0f17c-150">The command uses the **Credential** parameter, and it uses the **Authentication** parameter with a value of **CredSSP** .</span></span> <span data-ttu-id="0f17c-151">輸出結果顯示 Server02 遠端電腦上的工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="0f17c-151">The output shows the session configurations on the Server02 remote computer.</span></span>

### <span data-ttu-id="0f17c-152">範例 8-取得會話設定的資源 URI</span><span class="sxs-lookup"><span data-stu-id="0f17c-152">Example 8 - Get the resource URI of a session configuration</span></span>

<span data-ttu-id="0f17c-153">此範例適用于設定喜好設定變數的值 `$PSSessionConfigurationName` ，此值會接受資源 URI。</span><span class="sxs-lookup"><span data-stu-id="0f17c-153">This example is useful for setting the value of the `$PSSessionConfigurationName` preference variable, which takes a resource URI.</span></span>

```powershell
(Get-PSSessionConfiguration -Name CustomShell).resourceURI
```

```Output
http://schemas.microsoft.com/powershell/microsoft.CustomShell
```

<span data-ttu-id="0f17c-154">`$PSSessionConfigurationName`變數會指定當您建立會話時使用的預設設定。</span><span class="sxs-lookup"><span data-stu-id="0f17c-154">The `$PSSessionConfigurationName` variable specifies the default configuration that is used when you create a session.</span></span> <span data-ttu-id="0f17c-155">此變數設定在本機電腦上，但它會指定遠端電腦上的設定。</span><span class="sxs-lookup"><span data-stu-id="0f17c-155">This variable is set on the local computer, but it specifies a configuration on the remote computer.</span></span> <span data-ttu-id="0f17c-156">如需變數的詳細資訊 `$PSSessionConfiguration` ，請參閱 [about_Preference_Variables](About/about_Preference_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="0f17c-156">For more information about the `$PSSessionConfiguration` variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

## <span data-ttu-id="0f17c-157">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0f17c-157">PARAMETERS</span></span>

### <span data-ttu-id="0f17c-158">-Force</span><span class="sxs-lookup"><span data-stu-id="0f17c-158">-Force</span></span>

<span data-ttu-id="0f17c-159">若服務尚未執行，抑制重新啟動 WinRM 服務的提示。</span><span class="sxs-lookup"><span data-stu-id="0f17c-159">Suppresses the prompt to restart the WinRM service, if the service is not already running.</span></span>

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

### <span data-ttu-id="0f17c-160">-Name</span><span class="sxs-lookup"><span data-stu-id="0f17c-160">-Name</span></span>

<span data-ttu-id="0f17c-161">只取得具有指定名稱或名稱模式的工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="0f17c-161">Gets only the session configurations with the specified name or name pattern.</span></span> <span data-ttu-id="0f17c-162">輸入一或多個工作階段設定名稱。</span><span class="sxs-lookup"><span data-stu-id="0f17c-162">Enter one or more session configuration names.</span></span> <span data-ttu-id="0f17c-163">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="0f17c-163">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: All session configurations on the local computer
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="0f17c-164">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0f17c-164">CommonParameters</span></span>

<span data-ttu-id="0f17c-165">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="0f17c-165">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0f17c-166">如需詳細資訊，請參閱 [about_CommonParameters](./About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="0f17c-166">For more information, see [about_CommonParameters](./About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="0f17c-167">輸入</span><span class="sxs-lookup"><span data-stu-id="0f17c-167">INPUTS</span></span>

### <span data-ttu-id="0f17c-168">無</span><span class="sxs-lookup"><span data-stu-id="0f17c-168">None</span></span>

<span data-ttu-id="0f17c-169">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0f17c-169">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="0f17c-170">輸出</span><span class="sxs-lookup"><span data-stu-id="0f17c-170">OUTPUTS</span></span>

### <span data-ttu-id="0f17c-171">Microsoft.PowerShell.Commands.PSSessionConfigurationCommands#PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="0f17c-171">Microsoft.PowerShell.Commands.PSSessionConfigurationCommands#PSSessionConfiguration</span></span>

## <span data-ttu-id="0f17c-172">注意</span><span class="sxs-lookup"><span data-stu-id="0f17c-172">NOTES</span></span>

- <span data-ttu-id="0f17c-173">若要執行此 Cmdlet，請使用 [以 **系統管理員身分執行** ] 選項啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="0f17c-173">To run this cmdlet, start PowerShell with the **Run as administrator** option.</span></span>

- <span data-ttu-id="0f17c-174">若要檢視電腦上的工作階段設定，您必須是電腦上 Administrators 群組的成員。</span><span class="sxs-lookup"><span data-stu-id="0f17c-174">To view the session configurations on the computer, you must be a member of the Administrators group on the computer.</span></span>

- <span data-ttu-id="0f17c-175">若要 `Get-PSSessionConfiguration` 在遠端電腦上執行命令，您必須在本機 (電腦的用戶端設定中，使用指令程式 `Enable-WSManCredSSP`) 和遠端電腦上的服務設定中，啟用「認證安全性服務提供者」 (CredSSP) 驗證。</span><span class="sxs-lookup"><span data-stu-id="0f17c-175">To run a `Get-PSSessionConfiguration` command on a remote computer, Credential Security Service Provider (CredSSP) authentication must be enabled in the client settings on the local computer (by using the `Enable-WSManCredSSP` cmdlet) and in the service settings on the remote computer.</span></span> <span data-ttu-id="0f17c-176">此外，在建立遠端會話時，您必須使用 **驗證** 參數的 **CredSSP** 值。</span><span class="sxs-lookup"><span data-stu-id="0f17c-176">Also, you must use the **CredSSP** value of the **Authentication** parameter when establishing the remote session.</span></span> <span data-ttu-id="0f17c-177">否則，會拒絕存取。</span><span class="sxs-lookup"><span data-stu-id="0f17c-177">Otherwise, access is denied.</span></span>

- <span data-ttu-id="0f17c-178">`Get-PSSessionConfiguration`只有當物件具有值時，才會傳回物件的附注屬性。</span><span class="sxs-lookup"><span data-stu-id="0f17c-178">The note properties of the object that `Get-PSSessionConfiguration` returns appear on the object only when they have a value.</span></span> <span data-ttu-id="0f17c-179">只有使用會話設定檔建立的會話設定，才具有所有已定義的屬性。</span><span class="sxs-lookup"><span data-stu-id="0f17c-179">Only session configurations that were created by using a session configuration file have all the defined properties.</span></span>

- <span data-ttu-id="0f17c-180">工作階段設定物件的屬性取決於工作階段設定所設定的選項，以及這些選項的值。</span><span class="sxs-lookup"><span data-stu-id="0f17c-180">The properties of a session configuration object vary with the options set for the session configuration and the values of those options.</span></span> <span data-ttu-id="0f17c-181">此外，使用工作階段設定檔的工作階段設定會有額外的屬性。</span><span class="sxs-lookup"><span data-stu-id="0f17c-181">Also, session configurations that use a session configuration file have additional properties.</span></span>

- <span data-ttu-id="0f17c-182">您可以使用 WSMan: 磁碟機中的命令來變更工作階段設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="0f17c-182">You can use commands in the WSMan: drive to change the properties of session configurations.</span></span>
  <span data-ttu-id="0f17c-183">不過，您無法使用 PowerShell 2.0 中的 WSMan：磁片磁碟機來變更 PowerShell 3.0 中引進的會話設定屬性，例如 **OutputBufferingMode** 。</span><span class="sxs-lookup"><span data-stu-id="0f17c-183">However, you cannot use the WSMan: drive in PowerShell 2.0 to change session configuration properties that are introduced in PowerShell 3.0, such as **OutputBufferingMode** .</span></span> <span data-ttu-id="0f17c-184">PowerShell 2.0 命令不會產生錯誤，但它們是不正確。</span><span class="sxs-lookup"><span data-stu-id="0f17c-184">PowerShell 2.0 commands do not generate an error, but they are ineffective.</span></span> <span data-ttu-id="0f17c-185">若要變更 PowerShell 3.0 中引進的屬性，請使用 PowerShell 3.0 中的 WSMan：磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="0f17c-185">To change properties introduced in PowerShell 3.0, use the WSMan: drive in PowerShell 3.0.</span></span>

## <span data-ttu-id="0f17c-186">相關連結</span><span class="sxs-lookup"><span data-stu-id="0f17c-186">RELATED LINKS</span></span>

[<span data-ttu-id="0f17c-187">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="0f17c-187">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="0f17c-188">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="0f17c-188">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="0f17c-189">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="0f17c-189">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="0f17c-190">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="0f17c-190">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="0f17c-191">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="0f17c-191">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="0f17c-192">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="0f17c-192">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="0f17c-193">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="0f17c-193">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="0f17c-194">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="0f17c-194">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="0f17c-195">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="0f17c-195">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="0f17c-196">WSMan 提供者</span><span class="sxs-lookup"><span data-stu-id="0f17c-196">WSMan Provider</span></span>](../microsoft.wsman.management/about/about_WSMan_Provider.md)

[<span data-ttu-id="0f17c-197">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="0f17c-197">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="0f17c-198">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="0f17c-198">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)

