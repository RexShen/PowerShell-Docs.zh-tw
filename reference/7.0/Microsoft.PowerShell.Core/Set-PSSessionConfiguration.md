---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/set-pssessionconfiguration?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSSessionConfiguration
ms.openlocfilehash: c1d0d0bc2452e7f05fd47574dedeb4a1b9686fad
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205619"
---
# <span data-ttu-id="6a064-103">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="6a064-103">Set-PSSessionConfiguration</span></span>

## <span data-ttu-id="6a064-104">概要</span><span class="sxs-lookup"><span data-stu-id="6a064-104">SYNOPSIS</span></span>
<span data-ttu-id="6a064-105">變更已登錄的工作階段設定屬性。</span><span class="sxs-lookup"><span data-stu-id="6a064-105">Changes the properties of a registered session configuration.</span></span>

## <span data-ttu-id="6a064-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6a064-106">SYNTAX</span></span>

### <span data-ttu-id="6a064-107">NameParameterSet (預設值)</span><span class="sxs-lookup"><span data-stu-id="6a064-107">NameParameterSet (Default)</span></span>

```
Set-PSSessionConfiguration [-Name] <String> [-ApplicationBase <String>] [-RunAsCredential <PSCredential>]
 [-ThreadApartmentState <ApartmentState>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>] [-TransportOption <PSTransportOption>]
 [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6a064-108">AssemblyNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="6a064-108">AssemblyNameParameterSet</span></span>

```
Set-PSSessionConfiguration [-Name] <String> [-AssemblyName] <String> [-ApplicationBase <String>]
 [-ConfigurationTypeName] <String> [-RunAsCredential <PSCredential>] [-ThreadApartmentState <ApartmentState>]
 [-ThreadOptions <PSThreadOptions>] [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess]
 [-StartupScript <String>] [-MaximumReceivedDataSizePerCommandMB <Double>]
 [-MaximumReceivedObjectSizeMB <Double>] [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI]
 [-Force] [-NoServiceRestart] [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>]
 [-TransportOption <PSTransportOption>] [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6a064-109">SessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="6a064-109">SessionConfigurationFile</span></span>

```
Set-PSSessionConfiguration [-Name] <String> [-RunAsCredential <PSCredential>]
 [-ThreadApartmentState <ApartmentState>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-TransportOption <PSTransportOption>] -Path <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="6a064-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="6a064-110">DESCRIPTION</span></span>

<span data-ttu-id="6a064-111">`Set-PSSessionConfiguration`Cmdlet 會變更本機電腦上會話設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="6a064-111">The `Set-PSSessionConfiguration` cmdlet changes the properties of the session configurations on the local computer.</span></span>

<span data-ttu-id="6a064-112">使用 **Name** 參數可以識別您想要變更的工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="6a064-112">Use the **Name** parameter to identify the session configuration that you want to change.</span></span> <span data-ttu-id="6a064-113">使用其他參數可以為工作階段設定的屬性指定新值。</span><span class="sxs-lookup"><span data-stu-id="6a064-113">Use the other parameters to specify new values for the properties of the session configuration.</span></span> <span data-ttu-id="6a064-114">若要刪除設定中的屬性值，並使用預設值，請輸入空字串 ( "" ) 或對應參數的值 `$Null` 。</span><span class="sxs-lookup"><span data-stu-id="6a064-114">To delete a property value from the configuration, and use the default value, enter an empty string ("") or a value of `$Null` for the corresponding parameter.</span></span>

<span data-ttu-id="6a064-115">從 PowerShell 3.0 開始，您可以使用會話設定檔來定義會話設定。</span><span class="sxs-lookup"><span data-stu-id="6a064-115">Starting in PowerShell 3.0, you can use a session configuration file to define a session configuration.</span></span> <span data-ttu-id="6a064-116">此功能為使用工作階段設定的工作階段，提供一個簡單且可探索的方法來設定和變更其屬性。</span><span class="sxs-lookup"><span data-stu-id="6a064-116">This feature provides a simple and discoverable method for setting and changing the properties of sessions that use the session configuration.</span></span> <span data-ttu-id="6a064-117">若要指定會話設定檔，請使用的 **Path** 參數 `Set-PSSessionConfiguration` 。</span><span class="sxs-lookup"><span data-stu-id="6a064-117">To specify a session configuration file, use the **Path** parameter of `Set-PSSessionConfiguration`.</span></span> <span data-ttu-id="6a064-118">如需會話設定檔的詳細資訊，請參閱 [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)。</span><span class="sxs-lookup"><span data-stu-id="6a064-118">For information about session configuration files, see [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span></span>
<span data-ttu-id="6a064-119">如需有關如何建立和修改會話設定檔的詳細資訊，請參閱 `New-PSSessionConfigurationFile` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6a064-119">For information about how to create and modify a session configuration file, see the `New-PSSessionConfigurationFile` cmdlet.</span></span>

<span data-ttu-id="6a064-120">會話設定定義遠端會話的環境， ( **pssession** ) 連接到本機電腦。</span><span class="sxs-lookup"><span data-stu-id="6a064-120">Session configurations define the environment of remote sessions ( **PSSessions** ) that connect to the local computer.</span></span> <span data-ttu-id="6a064-121">每個 **PSSession** 都會使用會話設定。</span><span class="sxs-lookup"><span data-stu-id="6a064-121">Every **PSSession** uses a session configuration.</span></span> <span data-ttu-id="6a064-122">會話設定會決定 **PSSession** 的功能，例如會話中可用的模組、允許執行的 Cmdlet、語言模式、配額和超時。</span><span class="sxs-lookup"><span data-stu-id="6a064-122">The session configuration determines the features of the **PSSession** , such as the modules that are available in the session, the cmdlets that are permitted to run, the language mode, quotas, and timeouts.</span></span> <span data-ttu-id="6a064-123">會話設定的安全描述項會決定可以使用會話設定連接到本機電腦的人員。</span><span class="sxs-lookup"><span data-stu-id="6a064-123">The security descriptor of the session configuration determines who can use the session configuration to connect to the local computer.</span></span> <span data-ttu-id="6a064-124">如需會話設定的詳細資訊，請參閱 [about_Session_Configurations](About/about_Session_Configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="6a064-124">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

<span data-ttu-id="6a064-125">若要查看會話設定的屬性，請使用 `Get-PSSessionConfiguration` Cmdlet 或 WSMan 提供者。</span><span class="sxs-lookup"><span data-stu-id="6a064-125">To see the properties of a session configuration, use the `Get-PSSessionConfiguration` cmdlet or the WSMan Provider.</span></span> <span data-ttu-id="6a064-126">如需 WSMan 提供者的詳細資訊，請輸入 `Get-Help WSMan` 。</span><span class="sxs-lookup"><span data-stu-id="6a064-126">For more information about the WSMan Provider, type `Get-Help WSMan`.</span></span>

## <span data-ttu-id="6a064-127">範例</span><span class="sxs-lookup"><span data-stu-id="6a064-127">EXAMPLES</span></span>

### <span data-ttu-id="6a064-128">範例1：建立和變更會話設定</span><span class="sxs-lookup"><span data-stu-id="6a064-128">Example 1: Create and change a session configuration</span></span>

<span data-ttu-id="6a064-129">此範例示範如何在設定中新增和移除啟動腳本。</span><span class="sxs-lookup"><span data-stu-id="6a064-129">This example shows how to add and remove a startup script from a configuration.</span></span>

<span data-ttu-id="6a064-130">第一個命令會建立 **AdminShell** 設定。</span><span class="sxs-lookup"><span data-stu-id="6a064-130">The first command creates the **AdminShell** configuration.</span></span> <span data-ttu-id="6a064-131">第二個命令會將 `AdminConfig.ps1` 腳本新增至設定。</span><span class="sxs-lookup"><span data-stu-id="6a064-131">The second command adds the `AdminConfig.ps1` script to the configuration.</span></span> <span data-ttu-id="6a064-132">當您重新開機 **WinRM** 時，變更會生效。</span><span class="sxs-lookup"><span data-stu-id="6a064-132">The change is effective when you restart **WinRM** .</span></span>
<span data-ttu-id="6a064-133">第三個命令會 `AdminConfig.ps1` 從設定中移除腳本。</span><span class="sxs-lookup"><span data-stu-id="6a064-133">The third command removes the `AdminConfig.ps1` script from the configuration.</span></span>

```powershell
Register-PSSessionConfiguration -Name "AdminShell" -AssemblyName "C:\Shells\AdminShell.dll" -ConfigurationTypeName "AdminClass"
Set-PSSessionConfiguration -Name "AdminShell" -StartupScript "AdminConfig.ps1"
Set-PSSessionConfiguration -Name "AdminShell" -StartupScript $Null
```

### <span data-ttu-id="6a064-134">範例2：顯示結果</span><span class="sxs-lookup"><span data-stu-id="6a064-134">Example 2: Display results</span></span>

<span data-ttu-id="6a064-135">此範例會將 **MaximumReceivedObjectSizeMB** 屬性的值增加為20。</span><span class="sxs-lookup"><span data-stu-id="6a064-135">This example increases the value of the **MaximumReceivedObjectSizeMB** property to 20.</span></span> <span data-ttu-id="6a064-136">此命令也會提示您重新開機 **WinRM** 服務。</span><span class="sxs-lookup"><span data-stu-id="6a064-136">This command also prompts you to restart the **WinRM** service.</span></span> <span data-ttu-id="6a064-137">在 **WinRM** 服務重新開機之前，變更將不會生效。</span><span class="sxs-lookup"><span data-stu-id="6a064-137">The change is not effective until the **WinRM** service is restarted.</span></span>

```powershell
Set-PSSessionConfiguration -Name "IncObj" -MaximumReceivedObjectSizeMB 20
```

```Output
WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin\IncObj\InitializationParameters

ParamName                       ParamValue
---------                       ----------
psmaximumreceivedobjectsizemb   20

"Restart WinRM service"
WinRM service need to be restarted to make the changes effective. Do you want to run the command "restart-service winrm"?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): y
```

### <span data-ttu-id="6a064-138">範例3：以不同方式顯示結果</span><span class="sxs-lookup"><span data-stu-id="6a064-138">Example 3: Display results in different ways</span></span>

<span data-ttu-id="6a064-139">在此範例中，會將 `Set-PSSessionConfiguration` **MaintenanceShell** 會話設定中的啟動腳本變更為 `Maintenance.ps1` 。</span><span class="sxs-lookup"><span data-stu-id="6a064-139">In this example, `Set-PSSessionConfiguration` changes the startup script in the **MaintenanceShell** session configuration to `Maintenance.ps1`.</span></span> <span data-ttu-id="6a064-140">輸出會顯示變更，並提示您重新開機 **WinRM** 服務。</span><span class="sxs-lookup"><span data-stu-id="6a064-140">The output shows the change and prompts you to restart the **WinRM** service.</span></span> <span data-ttu-id="6a064-141">回應是 "y" (是)。</span><span class="sxs-lookup"><span data-stu-id="6a064-141">The response is "y" (yes).</span></span>

<span data-ttu-id="6a064-142">`Get-PSSessionConfiguration` 取得 **MaintenanceShell** 會話設定。</span><span class="sxs-lookup"><span data-stu-id="6a064-142">`Get-PSSessionConfiguration` gets the **MaintenanceShell** session configuration.</span></span> <span data-ttu-id="6a064-143">管線運算子 (|) 將命令的結果傳送至，這會將設定 `Format-List` 物件的所有屬性顯示在清單中。</span><span class="sxs-lookup"><span data-stu-id="6a064-143">The pipeline operator (|) sends the results of the command to `Format-List`, which displays all the properties of the configuration object in a list.</span></span> <span data-ttu-id="6a064-144">接下來，使用 WSMan 提供者來查看 **MaintenanceShell** 設定的初始化參數。</span><span class="sxs-lookup"><span data-stu-id="6a064-144">Next, using the WSMan provider, we view the initialization parameters for the **MaintenanceShell** configuration.</span></span> <span data-ttu-id="6a064-145">`Get-ChildItem` (別名 `dir`) 取得 **MaintenanceShell** 外掛程式 **InitializationParameters** 節點中的子專案。</span><span class="sxs-lookup"><span data-stu-id="6a064-145">`Get-ChildItem` (alias `dir`) gets the child items in the **InitializationParameters** node for the **MaintenanceShell** plug-in.</span></span> <span data-ttu-id="6a064-146">如需 WSMan 提供者的詳細資訊，請輸入 `Get-Help wsman` 。</span><span class="sxs-lookup"><span data-stu-id="6a064-146">For more information about the WSMan provider, type `Get-Help wsman`.</span></span>

```powershell
Set-PSSessionConfiguration -Name "MaintenanceShell" -StartupScript "C:\ps-test\Maintenance.ps1"
```

```Output
WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin\MaintenanceShell\InitializationParameters

ParamName            ParamValue
---------            ----------
startupscript        c:\ps-test\Mainte...

"Restart WinRM service"
WinRM service need to be restarted to make the changes effective. Do you want to run
the command "restart-service winrm"?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): y

```

```powershell
Get-PSSessionConfiguration MaintenanceShell | Format-List -Property *
```

```Output
xmlns            : http://schemas.microsoft.com/wbem/wsman/1/config/PluginConfiguration
Name             : MaintenanceShell
Filename         : %windir%\system32\pwrshplugin.dll
SDKVersion       : 1
XmlRenderingType : text
lang             : en-US
PSVersion        : 2.0
startupscript    : c:\ps-test\Maintenance.ps1
ResourceUri      : http://schemas.microsoft.com/powershell/MaintenanceShell
SupportsOptions  : true
ExactMatch       : true
Capability       : {Shell}
Permission       :
```

```powershell
dir WSMan:\localhost\Plugin\MaintenanceShell\InitializationParameters
```

```Output
ParamName     ParamValue
---------     ----------
PSVersion     2.0
startupscript c:\ps-test\Maintenance.ps1
```

## <span data-ttu-id="6a064-147">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6a064-147">PARAMETERS</span></span>

### <span data-ttu-id="6a064-148">-AccessMode</span><span class="sxs-lookup"><span data-stu-id="6a064-148">-AccessMode</span></span>

<span data-ttu-id="6a064-149">啟用和停用工作階段設定，並判斷是否可以用於電腦上的遠端或本機工作階段。</span><span class="sxs-lookup"><span data-stu-id="6a064-149">Enables and disables the session configuration and determines whether it can be used for remote or local sessions on the computer.</span></span> <span data-ttu-id="6a064-150">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="6a064-150">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="6a064-151">停用。</span><span class="sxs-lookup"><span data-stu-id="6a064-151">Disabled.</span></span> <span data-ttu-id="6a064-152">停用工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="6a064-152">Disables the session configuration.</span></span> <span data-ttu-id="6a064-153">它不能用於電腦的遠端或本機存取。</span><span class="sxs-lookup"><span data-stu-id="6a064-153">It cannot be used for remote or local access to the computer.</span></span> <span data-ttu-id="6a064-154">此值會將會話設定的 **Enabled** 屬性 (`WSMan:\<ComputerName>\PlugIn\<SessionConfigurationName>\Enabled`) 設定為 **False** 。</span><span class="sxs-lookup"><span data-stu-id="6a064-154">This value sets the **Enabled** property of the session configuration (`WSMan:\<ComputerName>\PlugIn\<SessionConfigurationName>\Enabled`) to **False** .</span></span>
- <span data-ttu-id="6a064-155">本機。</span><span class="sxs-lookup"><span data-stu-id="6a064-155">Local.</span></span> <span data-ttu-id="6a064-156">將 **Network_Deny_All** 項目新增到工作階段設定的安全性描述元。</span><span class="sxs-lookup"><span data-stu-id="6a064-156">Adds a **Network_Deny_All** entry to security descriptor of the session configuration.</span></span>
  <span data-ttu-id="6a064-157">本機電腦的使用者可以使用會話設定在同一部電腦上建立本機回送會話，但是遠端使用者會被拒絕存取。</span><span class="sxs-lookup"><span data-stu-id="6a064-157">Users of the local computer can use the session configuration to create a local loopback session on the same computer, but remote users are denied access.</span></span>
- <span data-ttu-id="6a064-158">遠端。</span><span class="sxs-lookup"><span data-stu-id="6a064-158">Remote.</span></span> <span data-ttu-id="6a064-159">將 **Deny_All** 和 **Network_Deny_All** 項目從工作階段設定的安全性描述元中移除。</span><span class="sxs-lookup"><span data-stu-id="6a064-159">Removes **Deny_All** and **Network_Deny_All** entries from the security descriptors of the session configuration.</span></span> <span data-ttu-id="6a064-160">本機電腦和遠端電腦的使用者可以使用工作階段設定來建立工作階段，並在這部電腦上執行命令。</span><span class="sxs-lookup"><span data-stu-id="6a064-160">Users of local and remote computers can use the session configuration to create sessions and run commands on this computer.</span></span>

<span data-ttu-id="6a064-161">預設值為 [ **遠端** ]。</span><span class="sxs-lookup"><span data-stu-id="6a064-161">The default value is **Remote** .</span></span>

<span data-ttu-id="6a064-162">其他 Cmdlet 稍後可以覆寫這個參數的值。</span><span class="sxs-lookup"><span data-stu-id="6a064-162">Other cmdlets can override the value of this parameter later.</span></span> <span data-ttu-id="6a064-163">例如，Cmdlet 會 `Enable-PSRemoting` 啟用電腦上的所有會話設定，並允許遠端存取，而此 `Disable-PSRemoting` Cmdlet 只允許本機存取電腦上的所有會話設定。</span><span class="sxs-lookup"><span data-stu-id="6a064-163">For example, the `Enable-PSRemoting` cmdlet enables all session configurations on the computer and permits remote access to them, and the `Disable-PSRemoting` cmdlet permits only local access to all session configurations on the computer.</span></span>

<span data-ttu-id="6a064-164">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="6a064-164">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSessionConfigurationAccessMode
Parameter Sets: (All)
Aliases:
Accepted values: Disabled, Local, Remote

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a064-165">-ApplicationBase</span><span class="sxs-lookup"><span data-stu-id="6a064-165">-ApplicationBase</span></span>

<span data-ttu-id="6a064-166">指定 \* 在 **AssemblyName** 參數的值中指定之元件檔 (.dll) 的路徑。</span><span class="sxs-lookup"><span data-stu-id="6a064-166">Specifies the path of the assembly file (\*.dll) that is specified in the value of the **AssemblyName** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a064-167">-AssemblyName</span><span class="sxs-lookup"><span data-stu-id="6a064-167">-AssemblyName</span></span>

<span data-ttu-id="6a064-168">指定組件名稱。</span><span class="sxs-lookup"><span data-stu-id="6a064-168">Specifies the assembly name.</span></span> <span data-ttu-id="6a064-169">此 Cmdlet 會根據元件中定義的類別建立會話設定。</span><span class="sxs-lookup"><span data-stu-id="6a064-169">This cmdlet creates a session configuration based on a class that is defined in an assembly.</span></span>

<span data-ttu-id="6a064-170">輸入定義會話設定之元件 .dll 檔案的檔案名或完整路徑。</span><span class="sxs-lookup"><span data-stu-id="6a064-170">Enter the filename or full path of an assembly .dll file that defines a session configuration.</span></span> <span data-ttu-id="6a064-171">如果您只輸入檔案名，您可以在 **ApplicationBase** 參數的值中輸入路徑。</span><span class="sxs-lookup"><span data-stu-id="6a064-171">If you enter only the file name, you can enter the path in the value of the **ApplicationBase** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: AssemblyNameParameterSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a064-172">-ConfigurationTypeName</span><span class="sxs-lookup"><span data-stu-id="6a064-172">-ConfigurationTypeName</span></span>

<span data-ttu-id="6a064-173">指定 **AssemblyName** 參數內的組件中定義的工作階段設定類型。</span><span class="sxs-lookup"><span data-stu-id="6a064-173">Specifies the type of the session configuration that is defined in the assembly in the **AssemblyName** parameter.</span></span> <span data-ttu-id="6a064-174">您指定的類型必須實作 **System.Management.Automation.Remoting.PSSessionConfiguration** 類別。</span><span class="sxs-lookup"><span data-stu-id="6a064-174">The type that you specify must implement the **System.Management.Automation.Remoting.PSSessionConfiguration** class.</span></span>

<span data-ttu-id="6a064-175">指定組件名稱時，此參數是必要的。</span><span class="sxs-lookup"><span data-stu-id="6a064-175">This parameter is required when you specify an assembly name.</span></span>

```yaml
Type: System.String
Parameter Sets: AssemblyNameParameterSet
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a064-176">-Force</span><span class="sxs-lookup"><span data-stu-id="6a064-176">-Force</span></span>

<span data-ttu-id="6a064-177">抑制所有使用者提示，並在不提示的情況下重新開機 **WinRM** 服務。</span><span class="sxs-lookup"><span data-stu-id="6a064-177">Suppresses all user prompts, and restarts the **WinRM** service without prompting.</span></span> <span data-ttu-id="6a064-178">重新啟動服務可讓設定變更生效。</span><span class="sxs-lookup"><span data-stu-id="6a064-178">Restarting the service makes the configuration change effective.</span></span>

<span data-ttu-id="6a064-179">若要避免重新啟動並抑制重新啟動提示，請使用 **NoServiceRestart** 參數。</span><span class="sxs-lookup"><span data-stu-id="6a064-179">To prevent a restart and suppress the restart prompt, use the **NoServiceRestart** parameter.</span></span>

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

### <span data-ttu-id="6a064-180">-MaximumReceivedDataSizePerCommandMB</span><span class="sxs-lookup"><span data-stu-id="6a064-180">-MaximumReceivedDataSizePerCommandMB</span></span>

<span data-ttu-id="6a064-181">指定可在任何單一遠端命令中傳送給這部電腦的資料量限制。</span><span class="sxs-lookup"><span data-stu-id="6a064-181">Specifies the limit on the amount of data that can be sent to this computer in any single remote command.</span></span> <span data-ttu-id="6a064-182">輸入資料大小 (單位為 MB)。</span><span class="sxs-lookup"><span data-stu-id="6a064-182">Enter the data size in megabytes (MB).</span></span> <span data-ttu-id="6a064-183">預設值為 50 MB。</span><span class="sxs-lookup"><span data-stu-id="6a064-183">The default is 50 MB.</span></span>

<span data-ttu-id="6a064-184">如果資料大小限制定義于 **ConfigurationTypeName** 參數中指定的設定類型，則會使用設定類型中的限制。</span><span class="sxs-lookup"><span data-stu-id="6a064-184">If a data size limit is defined in the configuration type that is specified in the **ConfigurationTypeName** parameter, the limit in the configuration type is used.</span></span> <span data-ttu-id="6a064-185">此參數的值會被忽略。</span><span class="sxs-lookup"><span data-stu-id="6a064-185">The value of this parameter is ignored.</span></span>

```yaml
Type: System.Nullable`1[System.Double]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a064-186">-MaximumReceivedObjectSizeMB</span><span class="sxs-lookup"><span data-stu-id="6a064-186">-MaximumReceivedObjectSizeMB</span></span>

<span data-ttu-id="6a064-187">指定可在任何單一物件中傳送給這部電腦的資料量限制。</span><span class="sxs-lookup"><span data-stu-id="6a064-187">Specifies the limits on the amount of data that can be sent to this computer in any single object.</span></span>
<span data-ttu-id="6a064-188">輸入資料大小（以 mb 為單位）。</span><span class="sxs-lookup"><span data-stu-id="6a064-188">Enter the data size in megabytes.</span></span> <span data-ttu-id="6a064-189">預設值為 10 MB。</span><span class="sxs-lookup"><span data-stu-id="6a064-189">The default is 10 MB.</span></span>

<span data-ttu-id="6a064-190">如果物件大小限制定義于 **ConfigurationTypeName** 參數中指定的設定類型，則會使用設定類型中的限制。</span><span class="sxs-lookup"><span data-stu-id="6a064-190">If an object size limit is defined in the configuration type that is specified in the **ConfigurationTypeName** parameter, the limit in the configuration type is used.</span></span> <span data-ttu-id="6a064-191">此參數的值會被忽略。</span><span class="sxs-lookup"><span data-stu-id="6a064-191">The value of this parameter is ignored.</span></span>

```yaml
Type: System.Nullable`1[System.Double]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a064-192">-ModulesToImport</span><span class="sxs-lookup"><span data-stu-id="6a064-192">-ModulesToImport</span></span>

<span data-ttu-id="6a064-193">指定要自動匯入使用工作階段設定之工作階段的模組和嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="6a064-193">Specifies the modules and snap-ins that are automatically imported into sessions that use the session configuration.</span></span> <span data-ttu-id="6a064-194">請輸入模組和嵌入式管理單元名稱。</span><span class="sxs-lookup"><span data-stu-id="6a064-194">Enter the module and snap-in names.</span></span>

<span data-ttu-id="6a064-195">依預設，只有在會話中會匯入 [ **Microsoft** ]，但除非已排除 Cmdlet，否則您可以使用 `Import-Module` 和 Add-PSSnapin Cmdlet，將模組和嵌入式管理單元新增至會話。</span><span class="sxs-lookup"><span data-stu-id="6a064-195">By default, only the **Microsoft.PowerShell.Core** snap-in is imported into sessions, but unless the cmdlets are excluded, you can use the `Import-Module` and Add-PSSnapin cmdlets to add modules and snap-ins to the session.</span></span>

<span data-ttu-id="6a064-196">此參數值中指定的模組會匯入至會話設定檔中指定的模組新增 (`New-PSSessionConfigurationFile`) 。</span><span class="sxs-lookup"><span data-stu-id="6a064-196">The modules specified in this parameter value are imported in additions to modules specified in the session configuration file (`New-PSSessionConfigurationFile`).</span></span> <span data-ttu-id="6a064-197">不過，工作階段設定檔中的設定可以隱藏模組所匯出的命令，或是防止使用者使用它們。</span><span class="sxs-lookup"><span data-stu-id="6a064-197">However, settings in the session configuration file can hide the commands exported by modules or prevent users from using them.</span></span>

<span data-ttu-id="6a064-198">此參數值中指定的模組會使用 Cmdlet 的 **ModulesToImport** 參數來取代指定的模組清單 `Register-PSSessionConfiguration` 。</span><span class="sxs-lookup"><span data-stu-id="6a064-198">The modules specified in this parameter value replace the list of modules specified by using the **ModulesToImport** parameter of the `Register-PSSessionConfiguration` cmdlet.</span></span>

<span data-ttu-id="6a064-199">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="6a064-199">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a064-200">-Name</span><span class="sxs-lookup"><span data-stu-id="6a064-200">-Name</span></span>

<span data-ttu-id="6a064-201">指定您想要變更之工作階段設定的名稱。</span><span class="sxs-lookup"><span data-stu-id="6a064-201">Specifies the name of the session configuration that you want to change.</span></span>

<span data-ttu-id="6a064-202">您無法使用這個參數來變更工作階段設定的名稱。</span><span class="sxs-lookup"><span data-stu-id="6a064-202">You cannot use this parameter to change the name of the session configuration.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6a064-203">-NoServiceRestart</span><span class="sxs-lookup"><span data-stu-id="6a064-203">-NoServiceRestart</span></span>

<span data-ttu-id="6a064-204">不會重新開機 **WinRM** 服務，並抑制重新開機服務的提示。</span><span class="sxs-lookup"><span data-stu-id="6a064-204">Does not restart the **WinRM** service, and suppresses the prompt to restart the service.</span></span>

<span data-ttu-id="6a064-205">依預設，當您執行時 `Set-PSSessionConfiguration` ，系統會提示您重新開機 **WinRM** 服務，讓新的會話設定生效。</span><span class="sxs-lookup"><span data-stu-id="6a064-205">By default, when you run `Set-PSSessionConfiguration`, you are prompted to restart the **WinRM** service to make the new session configuration effective.</span></span> <span data-ttu-id="6a064-206">在 **WinRM** 服務重新開機之前，新的會話設定不會生效。</span><span class="sxs-lookup"><span data-stu-id="6a064-206">Until the **WinRM** service is restarted, the new session configuration is not effective.</span></span>

<span data-ttu-id="6a064-207">若要重新開機 **WinRM** 服務而不提示，請使用 **Force** 參數。</span><span class="sxs-lookup"><span data-stu-id="6a064-207">To restart the **WinRM** service without prompting, use the **Force** parameter.</span></span> <span data-ttu-id="6a064-208">若要手動重新開機 **WinRM** 服務，請使用 `Restart-Service` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6a064-208">To restart the **WinRM** service manually, use the `Restart-Service` cmdlet.</span></span>

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

### <span data-ttu-id="6a064-209">-Path</span><span class="sxs-lookup"><span data-stu-id="6a064-209">-Path</span></span>

<span data-ttu-id="6a064-210">指定會話設定檔 ( .pssc) 的路徑，例如 Cmdlet 所建立的檔案 `New-PSSessionConfigurationFile` 。</span><span class="sxs-lookup"><span data-stu-id="6a064-210">Specifies the path of a session configuration file (.pssc), such as one created by the `New-PSSessionConfigurationFile` cmdlet.</span></span> <span data-ttu-id="6a064-211">若省略路徑，則預設為目前目錄。</span><span class="sxs-lookup"><span data-stu-id="6a064-211">If you omit the path, the default is the current directory.</span></span>

<span data-ttu-id="6a064-212">如需有關如何修改會話設定檔的詳細資訊，請參閱 Cmdlet 的說明主題 `New-PSSessionConfigurationFile` 。</span><span class="sxs-lookup"><span data-stu-id="6a064-212">For information about how to modify a session configuration file, see the help topic for the `New-PSSessionConfigurationFile` cmdlet.</span></span>

<span data-ttu-id="6a064-213">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="6a064-213">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: SessionConfigurationFile
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a064-214">-PSVersion</span><span class="sxs-lookup"><span data-stu-id="6a064-214">-PSVersion</span></span>

<span data-ttu-id="6a064-215">指定使用此會話設定之會話中的 PowerShell 版本。</span><span class="sxs-lookup"><span data-stu-id="6a064-215">Specifies the version of PowerShell in sessions that use this session configuration.</span></span>

<span data-ttu-id="6a064-216">此參數的值優先順序高於工作階段設定檔中的 **PowerShellVersion** 索引鍵值。</span><span class="sxs-lookup"><span data-stu-id="6a064-216">The value of this parameter takes precedence over the value of the **PowerShellVersion** key in the session configuration file.</span></span>

<span data-ttu-id="6a064-217">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="6a064-217">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Version
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases: PowerShellVersion

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a064-218">-RunAsCredential</span><span class="sxs-lookup"><span data-stu-id="6a064-218">-RunAsCredential</span></span>

<span data-ttu-id="6a064-219">指定會話中命令的認證。</span><span class="sxs-lookup"><span data-stu-id="6a064-219">Specifies credentials for commands in the session.</span></span> <span data-ttu-id="6a064-220">根據預設，命令以目前使用者的權限執行。</span><span class="sxs-lookup"><span data-stu-id="6a064-220">By default, commands run with the permissions of the current user.</span></span>

<span data-ttu-id="6a064-221">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="6a064-221">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a064-222">-SecurityDescriptorSddl</span><span class="sxs-lookup"><span data-stu-id="6a064-222">-SecurityDescriptorSddl</span></span>

<span data-ttu-id="6a064-223">為設定指定不同的 Security Descriptor Definition Language (SDDL) 字串。</span><span class="sxs-lookup"><span data-stu-id="6a064-223">Specifies a different Security Descriptor Definition Language (SDDL) string for the configuration.</span></span>

<span data-ttu-id="6a064-224">此字串會決定使用新工作階段設定的必要權限。</span><span class="sxs-lookup"><span data-stu-id="6a064-224">This string determines the permissions that are required to use the new session configuration.</span></span> <span data-ttu-id="6a064-225">若要在會話中使用會話設定，使用者至少必須有設定的 Execute (Invoke) 許可權。</span><span class="sxs-lookup"><span data-stu-id="6a064-225">To use a session configuration in a session, users must have at least Execute(Invoke) permission for the configuration.</span></span>

<span data-ttu-id="6a064-226">若要使用設定的預設安全描述項，請輸入空字串 ( "" ) 或的值 `$Null` 。</span><span class="sxs-lookup"><span data-stu-id="6a064-226">To use the default security descriptor for the configuration, enter an empty string ("") or a value of `$Null`.</span></span> <span data-ttu-id="6a064-227">預設值為 WSMan: 磁碟機中的根 SDDL。</span><span class="sxs-lookup"><span data-stu-id="6a064-227">The default is the root SDDL in the WSMan: drive.</span></span>

<span data-ttu-id="6a064-228">如果安全描述項很複雜，請考慮使用 **ShowSecurityDescriptorUI** 參數而非此參數。</span><span class="sxs-lookup"><span data-stu-id="6a064-228">If the security descriptor is complex, consider using the **ShowSecurityDescriptorUI** parameter instead of this one.</span></span> <span data-ttu-id="6a064-229">您無法在相同的命令中使用這兩個參數。</span><span class="sxs-lookup"><span data-stu-id="6a064-229">You cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="6a064-230">-SessionTypeOption</span><span class="sxs-lookup"><span data-stu-id="6a064-230">-SessionTypeOption</span></span>

<span data-ttu-id="6a064-231">指定會話設定的特定類型選項。</span><span class="sxs-lookup"><span data-stu-id="6a064-231">Specifies type-specific options for the session configuration.</span></span> <span data-ttu-id="6a064-232">輸入會話類型選項物件，例如 Cmdlet 所傳回的 **new-psworkflowexecutionoption** 物件 `New-PSWorkflowExecutionOption` 。</span><span class="sxs-lookup"><span data-stu-id="6a064-232">Enter a session type options object, such as the **PSWorkflowExecutionOption** object that the `New-PSWorkflowExecutionOption` cmdlet returns.</span></span>

<span data-ttu-id="6a064-233">使用工作階段設定之工作階段的選項，取決於工作階段選項和工作階段設定選項的值。</span><span class="sxs-lookup"><span data-stu-id="6a064-233">The options of sessions that use the session configuration are determined by the values of session options and the session configuration options.</span></span> <span data-ttu-id="6a064-234">除非已指定，否則會話中設定的選項（例如使用 `New-PSSessionOption` Cmdlet）優先于會話設定中設定的選項。</span><span class="sxs-lookup"><span data-stu-id="6a064-234">Unless specified, options set in the session, such as by using the `New-PSSessionOption` cmdlet, take precedence over options set in the session configuration.</span></span> <span data-ttu-id="6a064-235">不過，工作階段選項值不能超過工作階段設定中設定的最大值。</span><span class="sxs-lookup"><span data-stu-id="6a064-235">However, session option values cannot exceed maximum values set in the session configuration.</span></span>

<span data-ttu-id="6a064-236">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="6a064-236">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSSessionTypeOption
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a064-237">-ShowSecurityDescriptorUI</span><span class="sxs-lookup"><span data-stu-id="6a064-237">-ShowSecurityDescriptorUI</span></span>

<span data-ttu-id="6a064-238">指出此 Cmdlet 是可協助您為會話設定建立新 SDDL 的屬性工作表。</span><span class="sxs-lookup"><span data-stu-id="6a064-238">Indicates that this cmdlet a property sheet that helps you create a new SDDL for the session configuration.</span></span> <span data-ttu-id="6a064-239">當您執行 `Set-PSSessionConfiguration` 命令並重新啟動 **WinRM** 服務之後，就會顯示內容表。</span><span class="sxs-lookup"><span data-stu-id="6a064-239">The property sheet appears after you run the `Set-PSSessionConfiguration` command and then restart the **WinRM** service.</span></span>

<span data-ttu-id="6a064-240">當您將許可權設定為設定時，請記住，使用者必須至少擁有 Execute (Invoke) 許可權，才能在會話中使用會話設定。</span><span class="sxs-lookup"><span data-stu-id="6a064-240">When you set permissions to the configuration, remember that users must have at least Execute(Invoke) permission to use the session configuration in a session.</span></span>

<span data-ttu-id="6a064-241">您無法在相同的命令中使用 **SecurityDescriptorSDDL** 參數與此參數。</span><span class="sxs-lookup"><span data-stu-id="6a064-241">You cannot use the **SecurityDescriptorSDDL** parameter and this parameter in the same command.</span></span>

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

### <span data-ttu-id="6a064-242">-StartupScript</span><span class="sxs-lookup"><span data-stu-id="6a064-242">-StartupScript</span></span>

<span data-ttu-id="6a064-243">指定設定的啟動腳本。</span><span class="sxs-lookup"><span data-stu-id="6a064-243">Specifies the startup script for the configuration.</span></span> <span data-ttu-id="6a064-244">輸入 PowerShell 腳本的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="6a064-244">Enter the fully qualified path of a PowerShell script.</span></span> <span data-ttu-id="6a064-245">指定的指令碼會在使用工作階段設定的新工作階段中執行。</span><span class="sxs-lookup"><span data-stu-id="6a064-245">The specified script runs in the new session that uses the session configuration.</span></span>

<span data-ttu-id="6a064-246">若要將啟動腳本從會話設定中刪除，請輸入空字串 ( "" ) 或的值 `$Null` 。</span><span class="sxs-lookup"><span data-stu-id="6a064-246">To delete a startup script from a session configuration, enter an empty string ("") or a value of `$Null`.</span></span>

<span data-ttu-id="6a064-247">您可以使用啟動腳本來進一步設定使用者會話。</span><span class="sxs-lookup"><span data-stu-id="6a064-247">You can use a startup script to further configure the user session.</span></span> <span data-ttu-id="6a064-248">如果腳本產生錯誤（即使是非終止錯誤），則不會建立會話，且 `New-PSSession` 命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="6a064-248">If the script generates an error, even a non-terminating error, the session is not created and the `New-PSSession` command fails.</span></span>

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

### <span data-ttu-id="6a064-249">-ThreadOptions</span><span class="sxs-lookup"><span data-stu-id="6a064-249">-ThreadOptions</span></span>

<span data-ttu-id="6a064-250">指定設定中的執行緒選項設定。</span><span class="sxs-lookup"><span data-stu-id="6a064-250">Specifies the thread options setting in the configuration.</span></span> <span data-ttu-id="6a064-251">此設定會定義在工作階段中執行某個命令時，要如何建立及使用執行緒。</span><span class="sxs-lookup"><span data-stu-id="6a064-251">This setting defines how threads are created and used when a command is executed in the session.</span></span> <span data-ttu-id="6a064-252">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="6a064-252">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="6a064-253">預設</span><span class="sxs-lookup"><span data-stu-id="6a064-253">Default</span></span>
- <span data-ttu-id="6a064-254">ReuseThread</span><span class="sxs-lookup"><span data-stu-id="6a064-254">ReuseThread</span></span>
- <span data-ttu-id="6a064-255">UseCurrentThread</span><span class="sxs-lookup"><span data-stu-id="6a064-255">UseCurrentThread</span></span>
- <span data-ttu-id="6a064-256">UseNewThread</span><span class="sxs-lookup"><span data-stu-id="6a064-256">UseNewThread</span></span>

<span data-ttu-id="6a064-257">預設值為 **UseCurrentThread** 。</span><span class="sxs-lookup"><span data-stu-id="6a064-257">The default value is **UseCurrentThread** .</span></span>

<span data-ttu-id="6a064-258">如需詳細資訊，請參閱 [ Psthreadoptions 列舉](/dotnet/api/system.management.automation.runspaces.psthreadoptions)。</span><span class="sxs-lookup"><span data-stu-id="6a064-258">For more information, see [PSThreadOptions Enumeration](/dotnet/api/system.management.automation.runspaces.psthreadoptions).</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSThreadOptions
Parameter Sets: (All)
Aliases:
Accepted values: Default, UseNewThread, ReuseThread, UseCurrentThread

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a064-259">-TransportOption</span><span class="sxs-lookup"><span data-stu-id="6a064-259">-TransportOption</span></span>

<span data-ttu-id="6a064-260">指定會話設定的傳輸選項。</span><span class="sxs-lookup"><span data-stu-id="6a064-260">Specifies the transport options for the session configuration.</span></span> <span data-ttu-id="6a064-261">輸入傳輸選項物件，例如 Cmdlet 所傳回的 **WSManConfigurationOption** 物件 `New-PSTransportOption` 。</span><span class="sxs-lookup"><span data-stu-id="6a064-261">Enter a transport options object, such as the **WSManConfigurationOption** object that the `New-PSTransportOption` cmdlet returns.</span></span>

<span data-ttu-id="6a064-262">使用工作階段設定之工作階段的選項，取決於工作階段選項和工作階段設定選項的值。</span><span class="sxs-lookup"><span data-stu-id="6a064-262">The options of sessions that use the session configuration are determined by the values of session options and the session configuration options.</span></span> <span data-ttu-id="6a064-263">除非已指定，否則會話中設定的選項（例如使用 `New-PSSessionOption` Cmdlet）優先于會話設定中設定的選項。</span><span class="sxs-lookup"><span data-stu-id="6a064-263">Unless specified, options set in the session, such as by using the `New-PSSessionOption` cmdlet, take precedence over options set in the session configuration.</span></span> <span data-ttu-id="6a064-264">不過，工作階段選項值不能超過工作階段設定中設定的最大值。</span><span class="sxs-lookup"><span data-stu-id="6a064-264">However, session option values cannot exceed maximum values set in the session configuration.</span></span>

<span data-ttu-id="6a064-265">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="6a064-265">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSTransportOption
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a064-266">-UseSharedProcess</span><span class="sxs-lookup"><span data-stu-id="6a064-266">-UseSharedProcess</span></span>

<span data-ttu-id="6a064-267">只使用一個進程來裝載由相同使用者啟動的所有會話，並使用相同的會話設定。</span><span class="sxs-lookup"><span data-stu-id="6a064-267">Use only one process to host all sessions that are started by the same user and use the same session configuration.</span></span> <span data-ttu-id="6a064-268">根據預設，每個工作階段會裝載於自己的處理程序。</span><span class="sxs-lookup"><span data-stu-id="6a064-268">By default, each session is hosted in its own process.</span></span>

<span data-ttu-id="6a064-269">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="6a064-269">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="6a064-270">-Confirm</span><span class="sxs-lookup"><span data-stu-id="6a064-270">-Confirm</span></span>

<span data-ttu-id="6a064-271">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="6a064-271">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a064-272">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="6a064-272">-WhatIf</span></span>

<span data-ttu-id="6a064-273">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="6a064-273">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="6a064-274">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="6a064-274">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a064-275">-ThreadApartmentState</span><span class="sxs-lookup"><span data-stu-id="6a064-275">-ThreadApartmentState</span></span>

<span data-ttu-id="6a064-276">指定要使用之執行緒模組的單元狀態。</span><span class="sxs-lookup"><span data-stu-id="6a064-276">Specifies the apartment state of the threading module to be used.</span></span> <span data-ttu-id="6a064-277">可接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="6a064-277">Acceptable values are:</span></span>

- <span data-ttu-id="6a064-278">Unknown</span><span class="sxs-lookup"><span data-stu-id="6a064-278">Unknown</span></span>
- <span data-ttu-id="6a064-279">MTA</span><span class="sxs-lookup"><span data-stu-id="6a064-279">MTA</span></span>
- <span data-ttu-id="6a064-280">STA</span><span class="sxs-lookup"><span data-stu-id="6a064-280">STA</span></span>

```yaml
Type: System.Threading.ApartmentState
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a064-281">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6a064-281">CommonParameters</span></span>

<span data-ttu-id="6a064-282">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="6a064-282">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6a064-283">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="6a064-283">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6a064-284">輸入</span><span class="sxs-lookup"><span data-stu-id="6a064-284">INPUTS</span></span>

### <span data-ttu-id="6a064-285">無</span><span class="sxs-lookup"><span data-stu-id="6a064-285">None</span></span>

<span data-ttu-id="6a064-286">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6a064-286">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="6a064-287">輸出</span><span class="sxs-lookup"><span data-stu-id="6a064-287">OUTPUTS</span></span>

### <span data-ttu-id="6a064-288">Microsoft.wsman.management.wsmanconfigleafelement。</span><span class="sxs-lookup"><span data-stu-id="6a064-288">Microsoft.WSMan.Management.WSManConfigLeafElement</span></span>

## <span data-ttu-id="6a064-289">注意</span><span class="sxs-lookup"><span data-stu-id="6a064-289">NOTES</span></span>

<span data-ttu-id="6a064-290">若要執行此 Cmdlet，請使用 [以系統管理員身分執行] 選項啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="6a064-290">To run this cmdlet, start PowerShell by using the Run as administrator option.</span></span>

<span data-ttu-id="6a064-291">此 `Set-PSSessionConfiguration` Cmdlet 不會變更設定名稱，且 **WSMan** 提供者不支援此 `Rename-Item` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6a064-291">The `Set-PSSessionConfiguration` cmdlet does not change the configuration name and the **WSMan** provider does not support the `Rename-Item` cmdlet.</span></span> <span data-ttu-id="6a064-292">若要變更會話設定的名稱，請使用 `Unregister-PSSessionConfiguration` Cmdlet 來刪除設定，然後使用指令程式 `Register-PSSessionConfiguration` 來建立及註冊新的會話設定。</span><span class="sxs-lookup"><span data-stu-id="6a064-292">To change the name of a session configuration, use the `Unregister-PSSessionConfiguration` cmdlet to delete the configuration and then use the `Register-PSSessionConfiguration` cmdlet to create and register a new session configuration.</span></span>

<span data-ttu-id="6a064-293">您可以使用 `Set-PSSessionConfiguration` Cmdlet 來變更預設的 microsoft.powershell32 會話設定。</span><span class="sxs-lookup"><span data-stu-id="6a064-293">You can use the `Set-PSSessionConfiguration` cmdlet to change the default Microsoft.PowerShell and Microsoft.PowerShell32 session configurations.</span></span> <span data-ttu-id="6a064-294">它們並不受保護。</span><span class="sxs-lookup"><span data-stu-id="6a064-294">They are not protected.</span></span> <span data-ttu-id="6a064-295">若要還原為預設會話設定的原始版本，請使用 `Unregister-PSSessionConfiguration` Cmdlet 來刪除預設會話設定，然後使用指令程式 `Enable-PSRemoting` 來還原它。</span><span class="sxs-lookup"><span data-stu-id="6a064-295">To revert to the original version of a default session configuration, use the `Unregister-PSSessionConfiguration` cmdlet to delete the default session configuration and then use the `Enable-PSRemoting` cmdlet to restore it.</span></span>

<span data-ttu-id="6a064-296">工作階段設定物件的屬性取決於工作階段設定所設定的選項，以及這些選項的值。</span><span class="sxs-lookup"><span data-stu-id="6a064-296">The properties of a session configuration object vary with the options set for the session configuration and the values of those options.</span></span> <span data-ttu-id="6a064-297">此外，使用工作階段設定檔的工作階段設定會有額外的屬性。</span><span class="sxs-lookup"><span data-stu-id="6a064-297">Also, session configurations that use a session configuration file have additional properties.</span></span>

<span data-ttu-id="6a064-298">您可以使用 WSMan: 磁碟機中的命令來變更工作階段設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="6a064-298">You can use commands in the WSMan: drive to change the properties of session configurations.</span></span>
<span data-ttu-id="6a064-299">不過，您無法使用 PowerShell 2.0 中的 WSMan：磁片磁碟機來變更 PowerShell 3.0 中引進的會話設定屬性，例如 **OutputBufferingMode** 。</span><span class="sxs-lookup"><span data-stu-id="6a064-299">However, you cannot use the WSMan: drive in PowerShell 2.0 to change session configuration properties that are introduced in PowerShell 3.0, such as **OutputBufferingMode** .</span></span> <span data-ttu-id="6a064-300">Windows PowerShell 2.0 命令不會產生錯誤，但它們沒有效果。</span><span class="sxs-lookup"><span data-stu-id="6a064-300">Windows PowerShell 2.0 commands do not generate an error, but they are ineffective.</span></span> <span data-ttu-id="6a064-301">若要變更 PowerShell 3.0 中引進的屬性，請使用 PowerShell 3.0 中的 WSMan：磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="6a064-301">To change properties introduced in PowerShell 3.0, use the WSMan: drive in PowerShell 3.0.</span></span>

## <span data-ttu-id="6a064-302">相關連結</span><span class="sxs-lookup"><span data-stu-id="6a064-302">RELATED LINKS</span></span>

[<span data-ttu-id="6a064-303">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="6a064-303">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="6a064-304">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="6a064-304">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="6a064-305">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="6a064-305">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="6a064-306">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="6a064-306">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="6a064-307">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="6a064-307">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="6a064-308">New-PSTransportOption</span><span class="sxs-lookup"><span data-stu-id="6a064-308">New-PSTransportOption</span></span>](New-PSTransportOption.md)

[<span data-ttu-id="6a064-309">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="6a064-309">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="6a064-310">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="6a064-310">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="6a064-311">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="6a064-311">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="6a064-312">WSMan 提供者</span><span class="sxs-lookup"><span data-stu-id="6a064-312">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="6a064-313">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="6a064-313">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="6a064-314">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="6a064-314">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)
