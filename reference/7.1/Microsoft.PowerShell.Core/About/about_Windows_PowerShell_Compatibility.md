---
description: 描述 PowerShell 7 的 Windows PowerShell 相容性功能。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_windows_powershell_compatibility?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Windows_PowerShell_Compatibility
ms.openlocfilehash: 522c9d2169e49584915450813ad28dfc5e0d5ca2
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206695"
---
# <a name="about-windows-powershell-compatibility"></a><span data-ttu-id="99917-104">關於 Windows PowerShell 相容性</span><span class="sxs-lookup"><span data-stu-id="99917-104">About Windows PowerShell compatibility</span></span>

## <a name="short-description"></a><span data-ttu-id="99917-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="99917-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="99917-106">描述 PowerShell 7 的 Windows PowerShell 相容性功能。</span><span class="sxs-lookup"><span data-stu-id="99917-106">Describes the Windows PowerShell Compatibility functionality for PowerShell 7.</span></span>

## <a name="long-description"></a><span data-ttu-id="99917-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="99917-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="99917-108">除非模組資訊清單指出模組與 PowerShell Core 相容，否則 `%windir%\system32\WindowsPowerShell\v1.0\Modules` 會 Windows PowerShell 相容性功能，在背景 Windows PowerShell 5.1 進程中載入資料夾中的模組。</span><span class="sxs-lookup"><span data-stu-id="99917-108">Unless the module manifest indicates that module is compatible with PowerShell Core, modules in the `%windir%\system32\WindowsPowerShell\v1.0\Modules` folder are loaded in a background Windows PowerShell 5.1 process by Windows PowerShell Compatibility feature.</span></span>

### <a name="using-the-compatibility-feature"></a><span data-ttu-id="99917-109">使用相容性功能</span><span class="sxs-lookup"><span data-stu-id="99917-109">Using the Compatibility feature</span></span>

<span data-ttu-id="99917-110">使用 Windows PowerShell 相容性功能匯入第一個模組時，PowerShell 會建立名為的遠端會話， `WinPSCompatSession` 該會話會在背景 Windows PowerShell 5.1 進程中執行。</span><span class="sxs-lookup"><span data-stu-id="99917-110">When the first module is imported using Windows PowerShell Compatibility feature, PowerShell creates a remote session named `WinPSCompatSession` that is running in a background Windows PowerShell 5.1 process.</span></span> <span data-ttu-id="99917-111">當相容性功能匯入第一個模組時，就會建立此進程。</span><span class="sxs-lookup"><span data-stu-id="99917-111">This process is created when the Compatibility feature imports the first module.</span></span> <span data-ttu-id="99917-112">移除最後一個此類別模組時， (使用 `Remove-Module`) 或 PowerShell 進程結束時，會關閉此進程。</span><span class="sxs-lookup"><span data-stu-id="99917-112">The process is closed when the last such module is removed (using `Remove-Module`) or when PowerShell process exits.</span></span>

<span data-ttu-id="99917-113">會話中載入的模組 `WinPSCompatSession` 會透過隱含遠端處理來使用，並反映到目前的 PowerShell 會話。</span><span class="sxs-lookup"><span data-stu-id="99917-113">The modules loaded in the `WinPSCompatSession` session are used via implicit remoting and reflected into current PowerShell session.</span></span> <span data-ttu-id="99917-114">這與用於 PowerShell 作業的傳輸方法相同。</span><span class="sxs-lookup"><span data-stu-id="99917-114">This is the same transport method used for PowerShell jobs.</span></span>

<span data-ttu-id="99917-115">將模組匯入 `WinPSCompatSession` 會話時，隱含的遠端會在使用者的目錄中產生 proxy 模組， `$env:Temp` 並將此 proxy 模組匯入到目前的 PowerShell 會話。</span><span class="sxs-lookup"><span data-stu-id="99917-115">When a module is imported into the `WinPSCompatSession` session, implicit remoting generates a proxy module in the user's `$env:Temp` directory and imports this proxy module into current PowerShell session.</span></span> <span data-ttu-id="99917-116">這可讓 PowerShell 偵測模組是使用 Windows PowerShell 相容性功能載入的。</span><span class="sxs-lookup"><span data-stu-id="99917-116">This allows PowerShell to detect that the module was loaded using Windows PowerShell Compatibility functionality.</span></span>

<span data-ttu-id="99917-117">一旦建立會話之後，就可以將它用於無法在已還原序列化的物件上正常運作的作業。</span><span class="sxs-lookup"><span data-stu-id="99917-117">Once the session is created, it can be used for operations that don't work correctly on deserialized objects.</span></span> <span data-ttu-id="99917-118">整個管線會在 Windows PowerShell 中執行，而且只會傳回最終結果。</span><span class="sxs-lookup"><span data-stu-id="99917-118">The entire pipeline is executed in Windows PowerShell and only the final result is returned.</span></span> <span data-ttu-id="99917-119">例如：</span><span class="sxs-lookup"><span data-stu-id="99917-119">For example:</span></span>

```powershell
$s = Get-PSSession -Name WinPSCompatSession
Invoke-Command -Session $s -ScriptBlock {
  "Running in Windows PowerShell version $($PSVersionTable.PSVersion)"
}
```

<span data-ttu-id="99917-120">您可以透過兩種方式叫用相容性功能：</span><span class="sxs-lookup"><span data-stu-id="99917-120">The Compatibility feature can be invoked in two ways:</span></span>

- <span data-ttu-id="99917-121">使用 **UseWindowsPowerShell** 參數匯入模組以明確地進行</span><span class="sxs-lookup"><span data-stu-id="99917-121">Explicitly by importing a module using the **UseWindowsPowerShell** parameter</span></span>

   ```powershell
   Import-Module -Name ScheduledTasks -UseWindowsPowerShell
   ```

- <span data-ttu-id="99917-122">依模組名稱、路徑或自動載入功能透過命令探索，以隱含方式匯入 Windows PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="99917-122">Implicitly by importing a Windows PowerShell module by module name, path, or autoloading via command discovery.</span></span>

   ```powershell
   Import-Module -Name ServerManager
   Get-AppLockerPolicy -Local
   ```

   <span data-ttu-id="99917-123">如果尚未載入，則會在您執行時自動載入 AppLocker 模組  `Get-AppLockerPolicy` 。</span><span class="sxs-lookup"><span data-stu-id="99917-123">If not already loaded, the AppLocker module is autoloaded when you run  `Get-AppLockerPolicy`.</span></span>

<span data-ttu-id="99917-124">Windows PowerShell 相容性會封鎖載入 `WindowsPowerShellCompatibilityModuleDenyList` PowerShell 設定檔中設定所列出的模組。</span><span class="sxs-lookup"><span data-stu-id="99917-124">Windows PowerShell Compatibility blocks loading of modules that are listed in the `WindowsPowerShellCompatibilityModuleDenyList` setting in PowerShell configuration file.</span></span>

<span data-ttu-id="99917-125">此設定的預設值為：</span><span class="sxs-lookup"><span data-stu-id="99917-125">The default value of this setting is:</span></span>

```json
"WindowsPowerShellCompatibilityModuleDenyList":  [
   "PSScheduledJob","BestPractices","UpdateServices"
]
```

### <a name="managing-implicit-module-loading"></a><span data-ttu-id="99917-126">管理隱含模組載入</span><span class="sxs-lookup"><span data-stu-id="99917-126">Managing implicit module loading</span></span>

<span data-ttu-id="99917-127">若要停用 Windows PowerShell 相容性功能的隱含匯入行為，請使用 `DisableImplicitWinCompat` PowerShell 設定檔中的設定。</span><span class="sxs-lookup"><span data-stu-id="99917-127">To disable implicit import behavior of the Windows PowerShell Compatibility feature, use the `DisableImplicitWinCompat` setting in a PowerShell configuration file.</span></span> <span data-ttu-id="99917-128">此設定可新增至檔案 `powershell.config.json` 。</span><span class="sxs-lookup"><span data-stu-id="99917-128">This setting can be added to the `powershell.config.json` file.</span></span> <span data-ttu-id="99917-129">如需詳細資訊，請參閱 [about_powershell_config](about_powershell_config.md)。</span><span class="sxs-lookup"><span data-stu-id="99917-129">For more information, see [about_powershell_config](about_powershell_config.md).</span></span>

<span data-ttu-id="99917-130">這個範例示範如何建立設定檔，以停用 Windows PowerShell 相容性的隱含模組載入功能。</span><span class="sxs-lookup"><span data-stu-id="99917-130">This example shows how to create a configuration file that disables the implicit module-loading feature of Windows PowerShell Compatibility.</span></span>

```powershell
$ConfigPath = "$PSHOME\DisableWinCompat.powershell.config.json"
$ConfigJSON = ConvertTo-Json -InputObject @{
  "DisableImplicitWinCompat" = $true
  "Microsoft.PowerShell:ExecutionPolicy" = "RemoteSigned"
}
$ConfigJSON | Out-File -Force $ConfigPath
pwsh -settingsFile $ConfigPath
```

<span data-ttu-id="99917-131">如需有關模組相容性的最新資訊，請參閱 [PowerShell 7 模組相容性](https://aka.ms/PSModuleCompat) 清單。</span><span class="sxs-lookup"><span data-stu-id="99917-131">For more the latest information about module compatibility, see the [PowerShell 7 module compatibility](https://aka.ms/PSModuleCompat) list.</span></span>

### <a name="managing-cmdlet-clobbering"></a><span data-ttu-id="99917-132">管理 Cmdlet 阻礙</span><span class="sxs-lookup"><span data-stu-id="99917-132">Managing cmdlet clobbering</span></span>

<span data-ttu-id="99917-133">Windows PowerShell 相容性功能會使用隱含的遠端處理功能，在相容性模式中載入模組。</span><span class="sxs-lookup"><span data-stu-id="99917-133">The Windows PowerShell Compatibility feature uses implicit remoting to load modules in compatibility mode.</span></span> <span data-ttu-id="99917-134">結果是模組所匯出的命令優先于目前 PowerShell 7 會話中相同名稱的命令。</span><span class="sxs-lookup"><span data-stu-id="99917-134">The result is that commands exported by the module take precedence over commands of the same name in the current PowerShell 7 session.</span></span> <span data-ttu-id="99917-135">在 PowerShell 7.0.0 版中，這包含了 PowerShell 隨附的核心模組。</span><span class="sxs-lookup"><span data-stu-id="99917-135">In the PowerShell 7.0.0 release, this included the core modules that ship with PowerShell.</span></span>

<span data-ttu-id="99917-136">在 PowerShell 7.1 中，行為已變更，因此不會事情下列核心 PowerShell 模組：</span><span class="sxs-lookup"><span data-stu-id="99917-136">In PowerShell 7.1, the behavior was changed so that the following core PowerShell modules are not clobbered:</span></span>

- <span data-ttu-id="99917-137">ConsoleHost</span><span class="sxs-lookup"><span data-stu-id="99917-137">Microsoft.PowerShell.ConsoleHost</span></span>
- <span data-ttu-id="99917-138">Microsoft.PowerShell.Diagnostics</span><span class="sxs-lookup"><span data-stu-id="99917-138">Microsoft.PowerShell.Diagnostics</span></span>
- <span data-ttu-id="99917-139">Microsoft.PowerShell.Host</span><span class="sxs-lookup"><span data-stu-id="99917-139">Microsoft.PowerShell.Host</span></span>
- <span data-ttu-id="99917-140">Microsoft.PowerShell.Management</span><span class="sxs-lookup"><span data-stu-id="99917-140">Microsoft.PowerShell.Management</span></span>
- <span data-ttu-id="99917-141">Microsoft.PowerShell.Security</span><span class="sxs-lookup"><span data-stu-id="99917-141">Microsoft.PowerShell.Security</span></span>
- <span data-ttu-id="99917-142">Microsoft.PowerShell.Utility</span><span class="sxs-lookup"><span data-stu-id="99917-142">Microsoft.PowerShell.Utility</span></span>
- <span data-ttu-id="99917-143">Microsoft.WSMan.Management</span><span class="sxs-lookup"><span data-stu-id="99917-143">Microsoft.WSMan.Management</span></span>

<span data-ttu-id="99917-144">PowerShell 7.1 也加入了列出其他模組的功能，這些模組不應由相容性模式事情。</span><span class="sxs-lookup"><span data-stu-id="99917-144">PowerShell 7.1 also added the ability to list additional modules that should not be clobbered by compatibility mode.</span></span>

<span data-ttu-id="99917-145">您可以將 `WindowsPowerShellCompatibilityNoClobberModuleList` 設定新增至 PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="99917-145">You can add the `WindowsPowerShellCompatibilityNoClobberModuleList` setting to PowerShell configuration file.</span></span> <span data-ttu-id="99917-146">這項設定的值是以逗號分隔的模組名稱清單。</span><span class="sxs-lookup"><span data-stu-id="99917-146">The value of this setting is a comma-separated list of module names.</span></span> <span data-ttu-id="99917-147">此設定的預設值為：</span><span class="sxs-lookup"><span data-stu-id="99917-147">The default value of this setting is:</span></span>

```json
"WindowsPowerShellCompatibilityNoClobberModuleList": [ ]
```

## <a name="limitations"></a><span data-ttu-id="99917-148">限制</span><span class="sxs-lookup"><span data-stu-id="99917-148">Limitations</span></span>

<span data-ttu-id="99917-149">Windows PowerShell 相容性功能：</span><span class="sxs-lookup"><span data-stu-id="99917-149">The Windows PowerShell Compatibility functionality:</span></span>

1. <span data-ttu-id="99917-150">只能在 Windows 電腦本機上運作</span><span class="sxs-lookup"><span data-stu-id="99917-150">Only works locally on Windows computers</span></span>
1. <span data-ttu-id="99917-151">需要 Windows PowerShell 5。1</span><span class="sxs-lookup"><span data-stu-id="99917-151">Requires that Windows PowerShell 5.1</span></span>
1. <span data-ttu-id="99917-152">在序列化的 Cmdlet 參數和傳回值上運作，而不是在即時物件上操作</span><span class="sxs-lookup"><span data-stu-id="99917-152">Operates on serialized cmdlet parameters and return values, not on live objects</span></span>
1. <span data-ttu-id="99917-153">匯入 Windows PowerShell 遠端會話的所有模組都會共用相同的運行時。</span><span class="sxs-lookup"><span data-stu-id="99917-153">All modules imported into the Windows PowerShell remoting session share the same runspace.</span></span>

## <a name="keywords"></a><span data-ttu-id="99917-154">關鍵字</span><span class="sxs-lookup"><span data-stu-id="99917-154">Keywords</span></span>

<span data-ttu-id="99917-155">about_Windows_PowerShell_Compatibility</span><span class="sxs-lookup"><span data-stu-id="99917-155">about_Windows_PowerShell_Compatibility</span></span>

## <a name="see-also"></a><span data-ttu-id="99917-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99917-156">See also</span></span>

[<span data-ttu-id="99917-157">about_Modules</span><span class="sxs-lookup"><span data-stu-id="99917-157">about_Modules</span></span>](about_Modules.md)

[<span data-ttu-id="99917-158">Import-Module</span><span class="sxs-lookup"><span data-stu-id="99917-158">Import-Module</span></span>](xref:Microsoft.PowerShell.Core.Import-Module)

