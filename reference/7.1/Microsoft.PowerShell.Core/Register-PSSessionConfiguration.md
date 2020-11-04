---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/register-pssessionconfiguration?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-PSSessionConfiguration
ms.openlocfilehash: e3b8a075b42d7d612aed1acd6c8c71452d842cb6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204800"
---
# <span data-ttu-id="cc0cb-103">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="cc0cb-103">Register-PSSessionConfiguration</span></span>

## <span data-ttu-id="cc0cb-104">概要</span><span class="sxs-lookup"><span data-stu-id="cc0cb-104">SYNOPSIS</span></span>
<span data-ttu-id="cc0cb-105">建立並登錄新的工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-105">Creates and registers a new session configuration.</span></span>

## <span data-ttu-id="cc0cb-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="cc0cb-106">SYNTAX</span></span>

### <span data-ttu-id="cc0cb-107">NameParameterSet (預設值)</span><span class="sxs-lookup"><span data-stu-id="cc0cb-107">NameParameterSet (Default)</span></span>

```
Register-PSSessionConfiguration [-ProcessorArchitecture <String>] [-Name] <String> [-ApplicationBase <String>]
 [-RunAsCredential <PSCredential>] [-ThreadApartmentState <ApartmentState>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>] [-TransportOption <PSTransportOption>]
 [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="cc0cb-108">AssemblyNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="cc0cb-108">AssemblyNameParameterSet</span></span>

```
Register-PSSessionConfiguration [-ProcessorArchitecture <String>] [-Name] <String> [-AssemblyName] <String>
 [-ApplicationBase <String>] [-ConfigurationTypeName] <String> [-RunAsCredential <PSCredential>]
 [-ThreadApartmentState <ApartmentState>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>] [-TransportOption <PSTransportOption>]
 [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="cc0cb-109">SessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="cc0cb-109">SessionConfigurationFile</span></span>

```
Register-PSSessionConfiguration [-ProcessorArchitecture <String>] [-Name] <String>
 [-RunAsCredential <PSCredential>] [-ThreadApartmentState <ApartmentState>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-TransportOption <PSTransportOption>] -Path <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="cc0cb-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="cc0cb-110">DESCRIPTION</span></span>

<span data-ttu-id="cc0cb-111">此 `Register-PSSessionConfiguration` Cmdlet 會在本機電腦上建立並註冊新的會話設定。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-111">The `Register-PSSessionConfiguration` cmdlet creates and registers a new session configuration on the local computer.</span></span> <span data-ttu-id="cc0cb-112">這是您可以用來為遠端使用者建立自訂會話的 advanced Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-112">This is an advanced cmdlet that you can use to create custom sessions for remote users.</span></span>

<span data-ttu-id="cc0cb-113">每個 PowerShell 會話 ( **PSSession** ) 都會使用會話設定，也稱為端點。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-113">Every PowerShell session ( **PSSession** ) uses a session configuration, also known as an endpoint.</span></span>
<span data-ttu-id="cc0cb-114">當使用者建立連線到電腦的會話時，他們可以選取會話設定，或使用當您啟用 PowerShell 遠端功能時所註冊的預設會話設定。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-114">When users create a session that connects to the computer, they can select a session configuration or use the default session configuration that is registered when you enable PowerShell remoting.</span></span>
<span data-ttu-id="cc0cb-115">使用者也可以設定 $PSSessionConfigurationName 喜好設定變數，指定目前工作階段中所建立的遠端工作階段預設設定。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-115">Users can also set the $PSSessionConfigurationName preference variable, which specifies a default configuration for remote sessions created in the current session.</span></span>

<span data-ttu-id="cc0cb-116">工作階段設定定義遠端工作階段的環境。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-116">The session configuration defines the environment for the remote session.</span></span> <span data-ttu-id="cc0cb-117">設定可以決定哪些命令和語言元素可用於工作階段，並且可包含用來保護電腦的設定，例如工作階段在單一物件或命令中可以遠端接收的資料量限制。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-117">The configuration can determine which commands and language elements are available in the session, and it can include settings that protect the computer, such as those that limit the amount of data that the session can receive remotely in a single object or command.</span></span> <span data-ttu-id="cc0cb-118">會話設定的安全描述項會決定哪些使用者有權使用會話設定。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-118">The security descriptor of the session configuration determines which users have permission to use the session configuration.</span></span>

<span data-ttu-id="cc0cb-119">您可以使用實作新設定類別的組件，以及使用在工作階段中執行的指令碼來定義設定元素。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-119">You can define the elements of configuration by using an assembly that implements a new configuration class and by using a script that runs in the session.</span></span> <span data-ttu-id="cc0cb-120">從 PowerShell 3.0 開始，您也可以使用會話設定檔來定義會話設定。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-120">Beginning in PowerShell 3.0, you can also use a session configuration file to define the session configuration.</span></span>

<span data-ttu-id="cc0cb-121">如需會話設定的詳細資訊，請參閱 [about_Session_Configurations](About/about_Session_Configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-121">For information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>
<span data-ttu-id="cc0cb-122">如需會話設定檔的詳細資訊，請參閱 [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-122">For information about session configuration files, see [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span></span>

## <span data-ttu-id="cc0cb-123">範例</span><span class="sxs-lookup"><span data-stu-id="cc0cb-123">EXAMPLES</span></span>

### <span data-ttu-id="cc0cb-124">範例1：註冊 NewShell 會話設定</span><span class="sxs-lookup"><span data-stu-id="cc0cb-124">Example 1: Register a NewShell session configuration</span></span>

<span data-ttu-id="cc0cb-125">在此範例中，我們會註冊 **NewShell** 會話設定。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-125">In this example, we register the **NewShell** session configuration.</span></span> <span data-ttu-id="cc0cb-126">**AssemblyName** 和 **ApplicationBase** 參數會指定 **MyShell.dll** 檔的位置，以指定會話設定中的 Cmdlet 和提供者。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-126">The **AssemblyName** and **ApplicationBase** parameters specify the location of the **MyShell.dll** file, which specifies the cmdlets and providers in the session configuration.</span></span> <span data-ttu-id="cc0cb-127">**ConfigurationTypeName** 參數會指定要從元件使用的設定類別。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-127">The **ConfigurationTypeName** parameter specifies the configuration class to use from the assembly.</span></span>

```powershell
$sessionConfiguration = @{
    Name='NewShell'
    ApplicationBase='c:\MyShells\'
    AssemblyName='MyShell.dll'
    ConfigurationTypeName='MyClass'
}
Register-PSSessionConfiguration @sessionConfiguration
```

<span data-ttu-id="cc0cb-128">若要使用此設定，請輸入 `New-PSSession -ConfigurationName newshell` 。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-128">To use this configuration, type `New-PSSession -ConfigurationName newshell`.</span></span>

### <span data-ttu-id="cc0cb-129">範例2：註冊 MaintenanceShell 會話設定</span><span class="sxs-lookup"><span data-stu-id="cc0cb-129">Example 2: Register a MaintenanceShell session configuration</span></span>

<span data-ttu-id="cc0cb-130">此範例會在本機電腦上註冊 **MaintenanceShell** 會話設定。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-130">This example registers the **MaintenanceShell** session configuration on the local computer.</span></span> <span data-ttu-id="cc0cb-131">**StartupScript** 參數會指定 `Maintenance.ps1` 腳本。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-131">The **StartupScript** parameter specifies the `Maintenance.ps1` script.</span></span>

```powershell
Register-PSSessionConfiguration -Name MaintenanceShell -StartupScript C:\ps-test\Maintenance.ps1
```

<span data-ttu-id="cc0cb-132">當使用者使用 `New-PSSession` 命令並選取 **MaintenanceShell** 設定時， `Maintenance.ps1` 腳本會在新的會話中執行。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-132">When a user uses a `New-PSSession` command and selects the **MaintenanceShell** configuration, the `Maintenance.ps1` script runs in the new session.</span></span> <span data-ttu-id="cc0cb-133">腳本可以設定會話。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-133">The script can configure the session.</span></span> <span data-ttu-id="cc0cb-134">這包括匯入模組，以及設定會話的執行原則。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-134">This includes importing modules and setting the execution policy for the session.</span></span> <span data-ttu-id="cc0cb-135">如果腳本產生任何錯誤（包括非終止錯誤），則 `New-PSSession` 命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-135">If the script generates any errors, including non-terminating errors, the `New-PSSession` command fails.</span></span>

### <span data-ttu-id="cc0cb-136">範例3：註冊會話設定</span><span class="sxs-lookup"><span data-stu-id="cc0cb-136">Example 3: Register a session configuration</span></span>

<span data-ttu-id="cc0cb-137">此範例會註冊 **AdminShell** 會話設定。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-137">This example registers the **AdminShell** session configuration.</span></span>

<span data-ttu-id="cc0cb-138">`$sessionParams`變數是包含所有參數值的雜湊表。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-138">The `$sessionParams` variable is a hashtable containing all the parameter values.</span></span> <span data-ttu-id="cc0cb-139">此雜湊表會使用 PowerShell 展開傳遞給 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-139">This hashtable is passed to the cmdlet using PowerShell splatting.</span></span> <span data-ttu-id="cc0cb-140">此 `Register-PSSessionConfiguration` 命令會使用 **SecurityDescritorSDDL** 參數在變數的值中指定 SDDL `$sddl` ，並使用 **MaximumReceivedObjectSizeMB** 參數來增加物件大小限制。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-140">The `Register-PSSessionConfiguration` command uses the **SecurityDescritorSDDL** parameter to specify the SDDL in the value of the `$sddl` variable and the **MaximumReceivedObjectSizeMB** parameter to increase the object size limit.</span></span> <span data-ttu-id="cc0cb-141">它也使用 **StartupScript** 參數，指定設定工作階段的指令碼。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-141">It also uses the **StartupScript** parameter to specify a script that configures the session.</span></span>

```powershell
$sddl = "O:NSG:BAD:P(A;;GA;;;BA)S:P(AU;FA;GA;;;WD)(AU;FA;SA;GWGX;;WD)"
$sessionParams = @{
    Name="AdminShell"
    SecurityDescriptorSDDL=$sddl
    MaximumReceivedObjectSizeMB=20
    StartupScript="C:\scripts\AdminShell.ps1"
}
Register-PSSessionConfiguration @sessionParams
```

### <span data-ttu-id="cc0cb-142">範例4：傳回設定容器元素</span><span class="sxs-lookup"><span data-stu-id="cc0cb-142">Example 4: Return a configuration container element</span></span>

<span data-ttu-id="cc0cb-143">此範例說明如何註冊 **MaintenanceShell** 設定。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-143">This example shows how to register the **MaintenanceShell** configuration.</span></span>
<span data-ttu-id="cc0cb-144">`Register-PSSessionConfiguration` 傳回儲存在變數中的 **WSManConfigContainerElement** 物件 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-144">`Register-PSSessionConfiguration` returns a **WSManConfigContainerElement** object stored in the `$s` variable.</span></span> <span data-ttu-id="cc0cb-145">`Format-List` 顯示傳回物件的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-145">`Format-List` displays all the properties of the returned object.</span></span> <span data-ttu-id="cc0cb-146">**PSPath** 屬性顯示物件會儲存在 WSMan: 磁碟機的目錄中。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-146">The **PSPath** property shows that the object is stored in a directory of the WSMan: drive.</span></span> <span data-ttu-id="cc0cb-147">`Get-ChildItem` (別名 `dir`) 顯示路徑中的專案 `WSMan:\LocalHost\PlugIn` 。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-147">`Get-ChildItem` (alias `dir`) displays the items in the `WSMan:\LocalHost\PlugIn` path.</span></span> <span data-ttu-id="cc0cb-148">其中包括新的 **MaintenanceShell** 設定，以及 PowerShell 隨附的兩個預設設定。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-148">These include the new **MaintenanceShell** configuration and the two default configurations that come with PowerShell.</span></span>

```powershell
$s = Register-PSSessionConfiguration -Name MaintenanceShell -StartupScript C:\ps-test\Maintenance.ps1
$s | Format-List -Property *
dir WSMan:\LocalHost\Plugin
```

```Output
PSPath            : Microsoft.WSMan.Management\WSMan::localhost\Plugin\MaintenanceShell
PSParentPath      : Microsoft.WSMan.Management\WSMan::localhost\Plugin
PSChildName       : MaintenanceShell
PSDrive           : WSMan
PSProvider        : Microsoft.WSMan.Management\WSMan
PSIsContainer     : True
Keys              : {Name=MaintenanceShell}
Name              : MaintenanceShell
TypeNameOfElement : Container

Name                      Type                 Keys
----                      ----                 ----
MaintenanceShell          Container            {Name=MaintenanceShell}
microsoft.powershell      Container            {Name=microsoft.powershell}
microsoft.powershell32    Container            {Name=microsoft.powershell32}
```

### <span data-ttu-id="cc0cb-149">範例5：使用啟動腳本註冊會話設定</span><span class="sxs-lookup"><span data-stu-id="cc0cb-149">Example 5: Register a session configuration with a startup script</span></span>

<span data-ttu-id="cc0cb-150">在此範例中，我們會建立並註冊 **WithProfile** 會話設定。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-150">In this example we create and register the **WithProfile** session configuration.</span></span> <span data-ttu-id="cc0cb-151">**StartupScript** 參數會指示 PowerShell 針對任何使用會話設定的會話執行指定的腳本。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-151">The **StartupScript** parameter directs PowerShell to run the specified script for any session that uses the session configuration.</span></span>

```powershell
Register-PSSessionConfiguration -Name WithProfile -StartupScript Add-Profile.ps1
```

<span data-ttu-id="cc0cb-152">指令碼包含在目前工作階段範圍內使用點執行來執行使用者 **CurrentUserAllHosts** 設定檔的單一命令。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-152">The script contains a single command that uses dot sourcing to run the user's **CurrentUserAllHosts** profile in the current scope of the session.</span></span>

<span data-ttu-id="cc0cb-153">如需設定檔的詳細資訊，請參閱 [about_Profiles](./About/about_Profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-153">For more information about profiles, see [about_Profiles](./About/about_Profiles.md).</span></span> <span data-ttu-id="cc0cb-154">如需點執行的詳細資訊，請參閱 [about_Scopes](./About/about_Scopes.md)。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-154">For more information about dot sourcing, see [about_Scopes](./About/about_Scopes.md).</span></span>

## <span data-ttu-id="cc0cb-155">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cc0cb-155">PARAMETERS</span></span>

### <span data-ttu-id="cc0cb-156">-AccessMode</span><span class="sxs-lookup"><span data-stu-id="cc0cb-156">-AccessMode</span></span>

<span data-ttu-id="cc0cb-157">啟用和停用工作階段設定，並判斷是否可以用於電腦上的遠端或本機工作階段。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-157">Enables and disables the session configuration and determines whether it can be used for remote or local sessions on the computer.</span></span> <span data-ttu-id="cc0cb-158">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="cc0cb-158">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="cc0cb-159">停用。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-159">Disabled.</span></span> <span data-ttu-id="cc0cb-160">停用工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-160">Disables the session configuration.</span></span> <span data-ttu-id="cc0cb-161">它不能用於電腦的遠端或本機存取。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-161">It cannot be used for remote or local access to the computer.</span></span>
- <span data-ttu-id="cc0cb-162">本機。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-162">Local.</span></span> <span data-ttu-id="cc0cb-163">允許本機電腦的使用者使用會話設定在同一部電腦上建立本機回送會話，但拒絕遠端使用者的存取。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-163">Allows users of the local computer to use the session configuration to create a local loopback session on the same computer, but denies access to remote users.</span></span>
- <span data-ttu-id="cc0cb-164">遠端。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-164">Remote.</span></span> <span data-ttu-id="cc0cb-165">允許本機和遠端使用者使用工作階段設定，在此電腦上建立工作階段與執行命令。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-165">Allows local and remote users to use the session configuration to create sessions and run commands on this computer.</span></span>

<span data-ttu-id="cc0cb-166">預設值為 [遠端]。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-166">The default value is Remote.</span></span>

<span data-ttu-id="cc0cb-167">其他 Cmdlet 稍後可以覆寫這個參數的值。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-167">Other cmdlets can override the value of this parameter later.</span></span> <span data-ttu-id="cc0cb-168">例如，此 Cmdlet 可讓您從 `Enable-PSRemoting` 遠端存取所有會話設定，此 `Enable-PSSessionConfiguration` Cmdlet 會啟用會話設定，而此 `Disable-PSRemoting` Cmdlet 會防止遠端存取所有會話設定。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-168">For example, the `Enable-PSRemoting` cmdlet allows for remote access to all session configurations, the `Enable-PSSessionConfiguration` cmdlet enables session configurations, and the `Disable-PSRemoting` cmdlet prevents remote access to all session configurations.</span></span>

<span data-ttu-id="cc0cb-169">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-169">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="cc0cb-170">-ApplicationBase</span><span class="sxs-lookup"><span data-stu-id="cc0cb-170">-ApplicationBase</span></span>

<span data-ttu-id="cc0cb-171">指定 \* 在 **AssemblyName** 參數的值中指定之元件檔 (.dll) 的路徑。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-171">Specifies the path of the assembly file (\*.dll) that is specified in the value of the **AssemblyName** parameter.</span></span> <span data-ttu-id="cc0cb-172">當 **AssemblyName** 參數值不包含路徑時使用此參數。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-172">Use this parameter when the value of the **AssemblyName** parameter does not include a path.</span></span> <span data-ttu-id="cc0cb-173">預設值是目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-173">The default is the current directory.</span></span>

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

### <span data-ttu-id="cc0cb-174">-AssemblyName</span><span class="sxs-lookup"><span data-stu-id="cc0cb-174">-AssemblyName</span></span>

<span data-ttu-id="cc0cb-175">指定定義設定類型之組件檔 (\*.dll) 的名稱。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-175">Specifies the name of an assembly file (\*.dll) in which the configuration type is defined.</span></span> <span data-ttu-id="cc0cb-176">您可以在此參數或 **ApplicationBase** 參數的值中指定 .dll 的路徑。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-176">You can specify the path of the .dll in this parameter or in the value of the **ApplicationBase** parameter.</span></span>

<span data-ttu-id="cc0cb-177">當您指定 **ConfigurationTypeName** 參數時，此參數為必要參數。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-177">This parameter is required when you specify the **ConfigurationTypeName** parameter.</span></span>

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

### <span data-ttu-id="cc0cb-178">-ConfigurationTypeName</span><span class="sxs-lookup"><span data-stu-id="cc0cb-178">-ConfigurationTypeName</span></span>

<span data-ttu-id="cc0cb-179">指定用於此設定之 Microsoft .NET Framework 類型的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-179">Specifies the fully qualified name of the Microsoft .NET Framework type that is used for this configuration.</span></span> <span data-ttu-id="cc0cb-180">您指定的類型必須實作 **System.Management.Automation.Remoting.PSSessionConfiguration** 類別。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-180">The type that you specify must implement the **System.Management.Automation.Remoting.PSSessionConfiguration** class.</span></span>

<span data-ttu-id="cc0cb-181">若要指定可執行設定類型的元件檔 (\* .dll) ，請指定 **AssemblyName** 和 **ApplicationBase** 參數。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-181">To specify the assembly file (\*.dll) that implements the configuration type, specify the **AssemblyName** and **ApplicationBase** parameters.</span></span>

<span data-ttu-id="cc0cb-182">建立類型可讓您控制更多方面的會話設定，例如公開或隱藏 Cmdlet 的特定參數，或設定使用者無法覆寫的資料大小和物件大小限制。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-182">Creating a type lets you control more aspects of the session configuration, such as exposing or hiding certain parameters of cmdlets, or setting data size and object size limits that users cannot override.</span></span>

<span data-ttu-id="cc0cb-183">如果您省略這個參數， **DefaultRemotePowerShellConfiguration** 類別會用於工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-183">If you omit this parameter, the **DefaultRemotePowerShellConfiguration** class is used for the session configuration.</span></span>

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

### <span data-ttu-id="cc0cb-184">-Force</span><span class="sxs-lookup"><span data-stu-id="cc0cb-184">-Force</span></span>

<span data-ttu-id="cc0cb-185">抑制所有使用者提示，並在不提示的情況下重新開機 **WinRM** 服務。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-185">Suppresses all user prompts and restarts the **WinRM** service without prompting.</span></span> <span data-ttu-id="cc0cb-186">重新啟動服務可讓設定變更生效。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-186">Restarting the service makes the configuration change effective.</span></span>

<span data-ttu-id="cc0cb-187">若要防止重新開機並抑制重新開機提示，請指定 **NoServiceRestart** 參數。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-187">To prevent a restart and suppress the restart prompt, specify the **NoServiceRestart** parameter.</span></span>

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

### <span data-ttu-id="cc0cb-188">-MaximumReceivedDataSizePerCommandMB</span><span class="sxs-lookup"><span data-stu-id="cc0cb-188">-MaximumReceivedDataSizePerCommandMB</span></span>

<span data-ttu-id="cc0cb-189">指定可在任何單一遠端命令中傳送給這部電腦的資料量限制。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-189">Specifies a limit for the amount of data that can be sent to this computer in any single remote command.</span></span> <span data-ttu-id="cc0cb-190">輸入資料大小 (單位為 MB)。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-190">Enter the data size in megabytes (MB).</span></span> <span data-ttu-id="cc0cb-191">預設值為 50 MB。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-191">The default is 50 MB.</span></span>

<span data-ttu-id="cc0cb-192">如果資料大小限制定義於 **ConfigurationTypeName** 參數中指定的設定類型，則會使用設定類型中的限制並忽略此參數的值。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-192">If a data size limit is defined in the configuration type that is specified in the **ConfigurationTypeName** parameter, the limit in the configuration type is used and the value of this parameter is ignored.</span></span>

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

### <span data-ttu-id="cc0cb-193">-MaximumReceivedObjectSizeMB</span><span class="sxs-lookup"><span data-stu-id="cc0cb-193">-MaximumReceivedObjectSizeMB</span></span>

<span data-ttu-id="cc0cb-194">指定可在任何單一物件中傳送給這部電腦的資料量限制。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-194">Specifies a limit for the amount of data that can be sent to this computer in any single object.</span></span>
<span data-ttu-id="cc0cb-195">輸入資料大小（以 mb 為單位）。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-195">Enter the data size in megabytes.</span></span> <span data-ttu-id="cc0cb-196">預設值為 10 MB。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-196">The default is 10 MB.</span></span>

<span data-ttu-id="cc0cb-197">如果物件大小限制定義於 **ConfigurationTypeName** 參數中指定的設定類型，則會使用設定類型中的限制並忽略此參數的值。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-197">If an object size limit is defined in the configuration type that is specified in the **ConfigurationTypeName** parameter, the limit in the configuration type is used and the value of this parameter is ignored.</span></span>

```yaml
Type: System.Nullable`1[System.Double]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 10
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cc0cb-198">-ModulesToImport</span><span class="sxs-lookup"><span data-stu-id="cc0cb-198">-ModulesToImport</span></span>

<span data-ttu-id="cc0cb-199">指定自動匯入至使用會話設定之會話的模組。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-199">Specifies the modules that are automatically imported into sessions that use the session configuration.</span></span>

<span data-ttu-id="cc0cb-200">依預設，只會將 **Microsoft. Core** 匯入會話。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-200">By default, only **Microsoft.PowerShell.Core** is imported into sessions.</span></span> <span data-ttu-id="cc0cb-201">除非已排除 Cmdlet，否則您可以使用將 `Import-Module` 模組加入至會話。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-201">Unless the cmdlets are excluded, you can use `Import-Module` to add modules to the session.</span></span>

<span data-ttu-id="cc0cb-202">此參數值中指定的模組會匯入至 **SessionType** 參數所指定的模組新增中，以及在會話設定檔中的 **ModulesToImport** 索引鍵中列出的模組 (`New-PSSessionConfigurationFile`) 。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-202">The modules specified in this parameter value are imported in additions to modules that are specified by the **SessionType** parameter and those listed in the **ModulesToImport** key in the session configuration file (`New-PSSessionConfigurationFile`).</span></span> <span data-ttu-id="cc0cb-203">不過，工作階段設定檔中的設定可以隱藏模組所匯出的命令，或是防止使用者使用它們。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-203">However, settings in the session configuration file can hide the commands exported by modules or prevent users from using them.</span></span>

<span data-ttu-id="cc0cb-204">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-204">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="cc0cb-205">-Name</span><span class="sxs-lookup"><span data-stu-id="cc0cb-205">-Name</span></span>

<span data-ttu-id="cc0cb-206">指定工作階段設定的名稱。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-206">Specifies a name for the session configuration.</span></span> <span data-ttu-id="cc0cb-207">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-207">This parameter is required.</span></span>

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

### <span data-ttu-id="cc0cb-208">-NoServiceRestart</span><span class="sxs-lookup"><span data-stu-id="cc0cb-208">-NoServiceRestart</span></span>

<span data-ttu-id="cc0cb-209">不會重新開機 **WinRM** 服務，並抑制重新開機服務的提示。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-209">Does not restart the **WinRM** service, and suppresses the prompt to restart the service.</span></span>

<span data-ttu-id="cc0cb-210">依預設，當您執行 `Register-PSSessionConfiguration` 命令時，系統會提示您重新開機 **WinRM** 服務，讓新的會話設定生效。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-210">By default, when you run a `Register-PSSessionConfiguration` command, you are prompted to restart the **WinRM** service to make the new session configuration effective.</span></span> <span data-ttu-id="cc0cb-211">在 **WinRM** 服務重新開機之前，新的會話設定不會生效。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-211">Until the **WinRM** service is restarted, the new session configuration is not effective.</span></span>

<span data-ttu-id="cc0cb-212">若要重新啟動 **WinRM** 服務而不提示，請指定 **Force** 參數。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-212">To restart the **WinRM** service without prompting, specify the **Force** parameter.</span></span> <span data-ttu-id="cc0cb-213">若要手動重新開機 **WinRM** 服務，請使用 `Restart-Service` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-213">To restart the **WinRM** service manually, use the `Restart-Service` cmdlet.</span></span>

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

### <span data-ttu-id="cc0cb-214">-Path</span><span class="sxs-lookup"><span data-stu-id="cc0cb-214">-Path</span></span>

<span data-ttu-id="cc0cb-215">指定會話設定檔的路徑和檔案名 (. .pssc) ，例如所建立的檔案 `New-PSSessionConfigurationFile` 。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-215">Specifies the path and filename of a session configuration file (.pssc), such as one created by `New-PSSessionConfigurationFile`.</span></span> <span data-ttu-id="cc0cb-216">若省略路徑，則預設為目前目錄。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-216">If you omit the path, the default is the current directory.</span></span>

<span data-ttu-id="cc0cb-217">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-217">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="cc0cb-218">-ProcessorArchitecture</span><span class="sxs-lookup"><span data-stu-id="cc0cb-218">-ProcessorArchitecture</span></span>

<span data-ttu-id="cc0cb-219">判斷在使用此會話設定的會話中，是否已啟動32位或64位版本的 PowerShell 進程。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-219">Determines whether a 32-bit or 64-bit version of the PowerShell process is started in sessions that use this session configuration.</span></span> <span data-ttu-id="cc0cb-220">此參數可接受的值為： x86 (32 位) 和 AMD64 (64 位) 。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-220">The acceptable values for this parameter are: x86 (32-bit) and AMD64 (64-bit).</span></span> <span data-ttu-id="cc0cb-221">預設值是由裝載工作階段設定之電腦的處理器架構決定。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-221">The default value is determined by the processor architecture of the computer that hosts the session configuration.</span></span>

<span data-ttu-id="cc0cb-222">您可以使用此參數，在 64 位元電腦上建立 32 位元的工作階段。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-222">You can use this parameter to create a 32-bit session on a 64-bit computer.</span></span> <span data-ttu-id="cc0cb-223">嘗試在 32 位元電腦上建立 64 位元處理程序將會失敗。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-223">Attempts to create a 64-bit process on a 32-bit computer fail.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PA
Accepted values: x86, amd64

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="cc0cb-224">-PSVersion</span><span class="sxs-lookup"><span data-stu-id="cc0cb-224">-PSVersion</span></span>

<span data-ttu-id="cc0cb-225">指定使用此會話設定之會話中的 PowerShell 版本。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-225">Specifies the version of PowerShell in sessions that use this session configuration.</span></span>

<span data-ttu-id="cc0cb-226">此參數的值優先順序高於工作階段設定檔中的 **PowerShellVersion** 索引鍵值。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-226">The value of this parameter takes precedence over the value of the **PowerShellVersion** key in the session configuration file.</span></span>

<span data-ttu-id="cc0cb-227">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-227">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="cc0cb-228">-RunAsCredential</span><span class="sxs-lookup"><span data-stu-id="cc0cb-228">-RunAsCredential</span></span>

<span data-ttu-id="cc0cb-229">指定會話中命令的認證。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-229">Specifies credentials for commands in the session.</span></span> <span data-ttu-id="cc0cb-230">根據預設，命令以目前使用者的權限執行。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-230">By default, commands run with the permissions of the current user.</span></span>

<span data-ttu-id="cc0cb-231">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-231">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="cc0cb-232">-SecurityDescriptorSddl</span><span class="sxs-lookup"><span data-stu-id="cc0cb-232">-SecurityDescriptorSddl</span></span>

<span data-ttu-id="cc0cb-233">指定設定的 Security Descriptor Definition Language (SDDL) 字串。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-233">Specifies a Security Descriptor Definition Language (SDDL) string for the configuration.</span></span>

<span data-ttu-id="cc0cb-234">此字串會決定使用新工作階段設定的必要權限。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-234">This string determines the permissions that are required to use the new session configuration.</span></span> <span data-ttu-id="cc0cb-235">若要在會話中使用會話設定，使用者至少必須有設定的 Execute (Invoke) 許可權。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-235">To use a session configuration in a session, users must have at least Execute (Invoke) permission for the configuration.</span></span>

<span data-ttu-id="cc0cb-236">如果安全性描述元很複雜，請考慮使用 **ShowSecurityDescriptorUI** 參數而非此參數。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-236">If the security descriptor is complex, consider using the **ShowSecurityDescriptorUI** parameter instead of this parameter.</span></span> <span data-ttu-id="cc0cb-237">您無法在相同的命令中使用這兩個參數。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-237">You cannot use both parameters in the same command.</span></span>

<span data-ttu-id="cc0cb-238">如果您省略這個參數， **WinRM** 服務的根 SDDL 會用於此設定。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-238">If you omit this parameter, the root SDDL for the **WinRM** service is used for this configuration.</span></span>
<span data-ttu-id="cc0cb-239">若要檢視或變更根 SDDL，請使用 WSMan 提供者。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-239">To view or change the root SDDL, use the WSMan provider.</span></span> <span data-ttu-id="cc0cb-240">例如 `Get-Item wsman:\localhost\service\rootSDDL` 。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-240">For example `Get-Item wsman:\localhost\service\rootSDDL`.</span></span> <span data-ttu-id="cc0cb-241">如需 WSMan 提供者的詳細資訊，請輸入 `Get-Help wsman` 。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-241">For more information about the WSMan provider, type `Get-Help wsman`.</span></span>

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

### <span data-ttu-id="cc0cb-242">-SessionTypeOption</span><span class="sxs-lookup"><span data-stu-id="cc0cb-242">-SessionTypeOption</span></span>

<span data-ttu-id="cc0cb-243">指定會話設定的特定類型選項。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-243">Specifies type-specific options for the session configuration.</span></span> <span data-ttu-id="cc0cb-244">輸入會話類型選項物件，例如 Cmdlet 所傳回的 **new-psworkflowexecutionoption** 物件 `New-PSWorkflowExecutionOption` 。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-244">Enter a session type options object, such as the **PSWorkflowExecutionOption** object that the `New-PSWorkflowExecutionOption` cmdlet returns.</span></span>

<span data-ttu-id="cc0cb-245">使用工作階段設定之工作階段的選項，取決於工作階段選項和工作階段設定選項的值。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-245">The options of sessions that use the session configuration are determined by the values of session options and the session configuration options.</span></span> <span data-ttu-id="cc0cb-246">除非已指定，否則會話中設定的選項（例如使用 `New-PSSessionOption` Cmdlet）優先于會話設定中設定的選項。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-246">Unless specified, options set in the session, such as by using the `New-PSSessionOption` cmdlet, take precedence over options set in the session configuration.</span></span> <span data-ttu-id="cc0cb-247">不過，工作階段選項值不能超過工作階段設定中設定的最大值。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-247">However, session option values cannot exceed maximum values set in the session configuration.</span></span>

<span data-ttu-id="cc0cb-248">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-248">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="cc0cb-249">-ShowSecurityDescriptorUI</span><span class="sxs-lookup"><span data-stu-id="cc0cb-249">-ShowSecurityDescriptorUI</span></span>

<span data-ttu-id="cc0cb-250">指出此 Cmdlet 會顯示可協助您建立會話設定之 SDDL 的屬性工作表。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-250">Indicates that this cmdlet displays a property sheet that helps you create the SDDL for the session configuration.</span></span> <span data-ttu-id="cc0cb-251">當您輸入 `Register-PSSessionConfiguration` 命令並重新啟動 **WinRM** 服務之後，就會顯示內容表。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-251">The property sheet appears after you enter the `Register-PSSessionConfiguration` command and then restart the **WinRM** service.</span></span>

<span data-ttu-id="cc0cb-252">設定設定的許可權時，請記住，使用者必須至少擁有 Execute (Invoke) 許可權，才能在會話中使用會話設定。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-252">When setting the permissions for the configuration, remember that users must have at least Execute (Invoke) permission to use the session configuration in a session.</span></span>

<span data-ttu-id="cc0cb-253">您無法在相同的命令中使用 **SecurityDescriptorSDDL** 參數與此參數。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-253">You cannot use the **SecurityDescriptorSDDL** parameter and this parameter in the same command.</span></span>

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

### <span data-ttu-id="cc0cb-254">-StartupScript</span><span class="sxs-lookup"><span data-stu-id="cc0cb-254">-StartupScript</span></span>

<span data-ttu-id="cc0cb-255">指定 PowerShell 腳本的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-255">Specifies the fully qualified path of a PowerShell script.</span></span> <span data-ttu-id="cc0cb-256">指定的指令碼會在使用工作階段設定的新工作階段中執行。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-256">The specified script runs in the new session that uses the session configuration.</span></span>

<span data-ttu-id="cc0cb-257">您可以使用腳本來額外設定會話。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-257">You can use the script to additionally configure the session.</span></span> <span data-ttu-id="cc0cb-258">如果腳本產生錯誤（即使是非終止錯誤），則不會建立會話，且 `New-PSSession` 命令會失敗。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-258">If the script generates an error, even a non-terminating error, the session is not created and the `New-PSSession` command fails.</span></span>

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

### <span data-ttu-id="cc0cb-259">-ThreadOptions</span><span class="sxs-lookup"><span data-stu-id="cc0cb-259">-ThreadOptions</span></span>

<span data-ttu-id="cc0cb-260">指定當命令在會話中執行時，如何建立及使用執行緒。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-260">Specifies how threads are created and used when a command runs in the session.</span></span> <span data-ttu-id="cc0cb-261">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="cc0cb-261">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="cc0cb-262">預設</span><span class="sxs-lookup"><span data-stu-id="cc0cb-262">Default</span></span>
- <span data-ttu-id="cc0cb-263">ReuseThread</span><span class="sxs-lookup"><span data-stu-id="cc0cb-263">ReuseThread</span></span>
- <span data-ttu-id="cc0cb-264">UseCurrentThread</span><span class="sxs-lookup"><span data-stu-id="cc0cb-264">UseCurrentThread</span></span>
- <span data-ttu-id="cc0cb-265">UseNewThread</span><span class="sxs-lookup"><span data-stu-id="cc0cb-265">UseNewThread</span></span>

<span data-ttu-id="cc0cb-266">預設值為 **UseCurrentThread** 。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-266">The default value is **UseCurrentThread** .</span></span>

<span data-ttu-id="cc0cb-267">如需詳細資訊，請參閱 [ Psthreadoptions 列舉](/dotnet/api/system.management.automation.runspaces.psthreadoptions?view=powershellsdk-1.1.0)。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-267">For more information, see [PSThreadOptions Enumeration](/dotnet/api/system.management.automation.runspaces.psthreadoptions?view=powershellsdk-1.1.0).</span></span>

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

### <span data-ttu-id="cc0cb-268">-TransportOption</span><span class="sxs-lookup"><span data-stu-id="cc0cb-268">-TransportOption</span></span>

<span data-ttu-id="cc0cb-269">指定傳輸選項。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-269">Specifies the transport option.</span></span>

<span data-ttu-id="cc0cb-270">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-270">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="cc0cb-271">-UseSharedProcess</span><span class="sxs-lookup"><span data-stu-id="cc0cb-271">-UseSharedProcess</span></span>

<span data-ttu-id="cc0cb-272">只使用一個進程來裝載由相同使用者啟動的所有會話，並使用相同的會話設定。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-272">Use only one process to host all sessions that are started by the same user and use the same session configuration.</span></span> <span data-ttu-id="cc0cb-273">根據預設，每個工作階段會裝載於自己的處理程序。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-273">By default, each session is hosted in its own process.</span></span>

<span data-ttu-id="cc0cb-274">此參數是在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-274">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="cc0cb-275">-Confirm</span><span class="sxs-lookup"><span data-stu-id="cc0cb-275">-Confirm</span></span>

<span data-ttu-id="cc0cb-276">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-276">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="cc0cb-277">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="cc0cb-277">-WhatIf</span></span>

<span data-ttu-id="cc0cb-278">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-278">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="cc0cb-279">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-279">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="cc0cb-280">-ThreadApartmentState</span><span class="sxs-lookup"><span data-stu-id="cc0cb-280">-ThreadApartmentState</span></span>

<span data-ttu-id="cc0cb-281">指定要使用之執行緒模組的單元狀態。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-281">Specifies the apartment state of the threading module to be used.</span></span> <span data-ttu-id="cc0cb-282">可接受的值如下：</span><span class="sxs-lookup"><span data-stu-id="cc0cb-282">Acceptable values are:</span></span>

- <span data-ttu-id="cc0cb-283">Unknown</span><span class="sxs-lookup"><span data-stu-id="cc0cb-283">Unknown</span></span>
- <span data-ttu-id="cc0cb-284">MTA</span><span class="sxs-lookup"><span data-stu-id="cc0cb-284">MTA</span></span>
- <span data-ttu-id="cc0cb-285">STA</span><span class="sxs-lookup"><span data-stu-id="cc0cb-285">STA</span></span>

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

### <span data-ttu-id="cc0cb-286">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cc0cb-286">CommonParameters</span></span>

<span data-ttu-id="cc0cb-287">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-287">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cc0cb-288">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-288">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cc0cb-289">輸入</span><span class="sxs-lookup"><span data-stu-id="cc0cb-289">INPUTS</span></span>

### <span data-ttu-id="cc0cb-290">無</span><span class="sxs-lookup"><span data-stu-id="cc0cb-290">None</span></span>

<span data-ttu-id="cc0cb-291">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-291">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="cc0cb-292">輸出</span><span class="sxs-lookup"><span data-stu-id="cc0cb-292">OUTPUTS</span></span>

### <span data-ttu-id="cc0cb-293">Microsoft.WSMan.Management.WSManConfigContainerElement</span><span class="sxs-lookup"><span data-stu-id="cc0cb-293">Microsoft.WSMan.Management.WSManConfigContainerElement</span></span>

## <span data-ttu-id="cc0cb-294">注意</span><span class="sxs-lookup"><span data-stu-id="cc0cb-294">NOTES</span></span>

<span data-ttu-id="cc0cb-295">若要執行此 Cmdlet，您必須使用 [ **以系統管理員身分執行** ] 選項啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-295">To run this cmdlet you must start PowerShell by using the **Run as administrator** option.</span></span>

<span data-ttu-id="cc0cb-296">此 Cmdlet 會產生代表 Management (WS-MANAGEMENT) 外掛程式設定之 Web 服務的 XML，並將 XML 傳送至 WS-MANAGEMENT，以在本機電腦上註冊外掛程式 (`New-Item wsman:\localhost\plugin`) 。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-296">This cmdlet generates XML that represents a Web Services for Management (WS-Management) plug-in configuration and sends the XML to WS-Management, which registers the plug-in on the local computer (`New-Item wsman:\localhost\plugin`).</span></span>

<span data-ttu-id="cc0cb-297">工作階段設定物件的屬性取決於工作階段設定所設定的選項，以及這些選項的值。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-297">The properties of a session configuration object vary with the options set for the session configuration and the values of those options.</span></span> <span data-ttu-id="cc0cb-298">此外，使用工作階段設定檔的工作階段設定會有額外的屬性。</span><span class="sxs-lookup"><span data-stu-id="cc0cb-298">Also, session configurations that use a session configuration file have additional properties.</span></span>

## <span data-ttu-id="cc0cb-299">相關連結</span><span class="sxs-lookup"><span data-stu-id="cc0cb-299">RELATED LINKS</span></span>

[<span data-ttu-id="cc0cb-300">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="cc0cb-300">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="cc0cb-301">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="cc0cb-301">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="cc0cb-302">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="cc0cb-302">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="cc0cb-303">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="cc0cb-303">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="cc0cb-304">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="cc0cb-304">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="cc0cb-305">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="cc0cb-305">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="cc0cb-306">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="cc0cb-306">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="cc0cb-307">WSMan 提供者</span><span class="sxs-lookup"><span data-stu-id="cc0cb-307">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="cc0cb-308">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="cc0cb-308">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="cc0cb-309">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="cc0cb-309">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)
