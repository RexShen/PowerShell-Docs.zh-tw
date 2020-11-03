---
description: PowerShell Core 的設定檔，取代登錄設定。
keywords: powershell
Locale: en-US
ms.date: 11/02/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PowerShell_Config
ms.openlocfilehash: e1eabd71dde71f0191ca8bb991b5bee8f615c312
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206976"
---
# <a name="about-powershell-config"></a><span data-ttu-id="bf810-104">關於 PowerShell 設定</span><span class="sxs-lookup"><span data-stu-id="bf810-104">About PowerShell Config</span></span>

## <a name="short-description"></a><span data-ttu-id="bf810-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="bf810-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="bf810-106">PowerShell Core 的設定檔，取代登錄設定。</span><span class="sxs-lookup"><span data-stu-id="bf810-106">Configuration files for PowerShell Core, replacing Registry configuration.</span></span>

## <a name="long-description"></a><span data-ttu-id="bf810-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="bf810-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="bf810-108">檔案 `powershell.config.json` 包含 PowerShell Core 的設定。</span><span class="sxs-lookup"><span data-stu-id="bf810-108">The `powershell.config.json` file contains configuration settings for PowerShell Core.</span></span> <span data-ttu-id="bf810-109">PowerShell 會在啟動時載入此設定。</span><span class="sxs-lookup"><span data-stu-id="bf810-109">PowerShell loads this configuration at startup.</span></span> <span data-ttu-id="bf810-110">您也可以在執行時間修改這些設定。</span><span class="sxs-lookup"><span data-stu-id="bf810-110">The settings can also be modified at runtime.</span></span> <span data-ttu-id="bf810-111">先前，這些設定會儲存在適用于 PowerShell 的 Windows 登錄中，但現在會包含在檔案中，以啟用 macOS 和 Linux 上的設定。</span><span class="sxs-lookup"><span data-stu-id="bf810-111">Previously, these settings were stored in the Windows Registry for PowerShell, but are now contained in a file to enable configuration on macOS and Linux.</span></span>

> [!WARNING]
> <span data-ttu-id="bf810-112">如果檔案 `powershell.config.json` 包含不正確 JSON PowerShell，則無法啟動互動式會話。</span><span class="sxs-lookup"><span data-stu-id="bf810-112">If the `powershell.config.json` file contains invalid JSON PowerShell cannot start an interactive session.</span></span>
> <span data-ttu-id="bf810-113">如果發生這種情況，您必須修正設定檔案。</span><span class="sxs-lookup"><span data-stu-id="bf810-113">If this occurs, you must fix the configuration file.</span></span>

> [!NOTE]
> <span data-ttu-id="bf810-114">無法辨識的金鑰或設定檔中的無效值將會以無訊息方式略過。</span><span class="sxs-lookup"><span data-stu-id="bf810-114">Unrecognized keys or invalid values in the configuration file will be silently ignored.</span></span>

### <a name="allusers-shared-configuration"></a><span data-ttu-id="bf810-115">AllUsers (共用) 設定</span><span class="sxs-lookup"><span data-stu-id="bf810-115">AllUsers (shared) configuration</span></span>

<span data-ttu-id="bf810-116">`powershell.config.json`目錄中的檔案 `$PSHOME` 會定義從該 PowerShell Core 安裝執行的所有 PowerShell Core 會話的設定。</span><span class="sxs-lookup"><span data-stu-id="bf810-116">A `powershell.config.json` file in the `$PSHOME` directory defines the configuration for all PowerShell Core sessions running from that PowerShell Core installation.</span></span>

> [!NOTE]
> <span data-ttu-id="bf810-117">`$PSHOME`位置會定義為與執行中 System.Management.Automation.dll 元件相同的目錄。</span><span class="sxs-lookup"><span data-stu-id="bf810-117">The `$PSHOME` location is defined as the same directory as the executing System.Management.Automation.dll assembly.</span></span> <span data-ttu-id="bf810-118">這也適用于託管的 PowerShell SDK 實例。</span><span class="sxs-lookup"><span data-stu-id="bf810-118">This applies to hosted PowerShell SDK instances as well.</span></span>

### <a name="currentuser-per-user-configurations"></a><span data-ttu-id="bf810-119">CurrentUser (每位使用者) 設定</span><span class="sxs-lookup"><span data-stu-id="bf810-119">CurrentUser (per-user) configurations</span></span>

<span data-ttu-id="bf810-120">您也可以將檔案放在使用者範圍設定目錄中，以每個使用者為基礎來設定 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="bf810-120">You can also configure PowerShell on a per-user basis by placing the file in the user-scope configuration directory.</span></span> <span data-ttu-id="bf810-121">您可以使用命令，在各平臺上找到使用者設定目錄 `Split-Path $PROFILE.CurrentUserCurrentHost` 。</span><span class="sxs-lookup"><span data-stu-id="bf810-121">The user configuration directory can be found across platforms with the command `Split-Path $PROFILE.CurrentUserCurrentHost`.</span></span>

## <a name="general-configuration-settings"></a><span data-ttu-id="bf810-122">一般組態設定</span><span class="sxs-lookup"><span data-stu-id="bf810-122">General configuration settings</span></span>

### <a name="executionpolicy"></a><span data-ttu-id="bf810-123">ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="bf810-123">ExecutionPolicy</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bf810-124">此設定僅適用于 Windows 平臺。</span><span class="sxs-lookup"><span data-stu-id="bf810-124">This configuration only applies on Windows platforms.</span></span>

<span data-ttu-id="bf810-125">設定 PowerShell 會話的執行原則，以決定可執行檔腳本。</span><span class="sxs-lookup"><span data-stu-id="bf810-125">Configures the execution policy for PowerShell sessions, determining what scripts can be run.</span></span> <span data-ttu-id="bf810-126">根據預設，PowerShell 會使用現有的執行原則。</span><span class="sxs-lookup"><span data-stu-id="bf810-126">By default, PowerShell uses the existing execution policy.</span></span>

<span data-ttu-id="bf810-127">針對 AllUsers 設定，這會設定 **LocalMachine** 執行原則。</span><span class="sxs-lookup"><span data-stu-id="bf810-127">For AllUsers configurations, this sets the **LocalMachine** execution policy.</span></span>
<span data-ttu-id="bf810-128">針對 CurrentUser 設定，這會設定 **currentuser** 執行原則。</span><span class="sxs-lookup"><span data-stu-id="bf810-128">For CurrentUser configurations, this sets the **CurrentUser** execution policy.</span></span>

> [!NOTE]
> <span data-ttu-id="bf810-129">[`Set-ExecutionPolicy`](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)當以叫用時，此 Cmdlet 會修改 AllUsers 設定檔中的這項設定 `-Scope LocalMachine` ，並在使用叫用時，修改 CurrentUser 設定檔中的這項設定 `-Scope CurrentUser` 。</span><span class="sxs-lookup"><span data-stu-id="bf810-129">The [`Set-ExecutionPolicy`](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy) cmdlet modifies this setting in the AllUsers configuration file when invoked with `-Scope LocalMachine`, and modifies this setting in the CurrentUser configuration file when invoked with `-Scope CurrentUser`.</span></span>

```Schema
"<shell-id>:ExecutionPolicy": "<execution-policy>"
```

<span data-ttu-id="bf810-130">其中：</span><span class="sxs-lookup"><span data-stu-id="bf810-130">Where:</span></span>

- <span data-ttu-id="bf810-131">`<shell-id>` 指的是目前 PowerShell 主機的識別碼。</span><span class="sxs-lookup"><span data-stu-id="bf810-131">`<shell-id>` refers to the ID of the current PowerShell host.</span></span>
  <span data-ttu-id="bf810-132">若是正常 PowerShell Core，則為 `Microsoft.PowerShell` 。</span><span class="sxs-lookup"><span data-stu-id="bf810-132">For normal PowerShell Core, this is `Microsoft.PowerShell`.</span></span>
  <span data-ttu-id="bf810-133">在任何 PowerShell 會話中，您都可以使用來探索它 `$ShellId` 。</span><span class="sxs-lookup"><span data-stu-id="bf810-133">In any PowerShell session, you can discover it with `$ShellId`.</span></span>
- <span data-ttu-id="bf810-134">`<execution-policy>` 參考有效的執行原則名稱。</span><span class="sxs-lookup"><span data-stu-id="bf810-134">`<execution-policy>` refers to a valid execution policy name.</span></span>

<span data-ttu-id="bf810-135">下列範例會將 PowerShell 的執行原則設定為 `RemoteSigned` 。</span><span class="sxs-lookup"><span data-stu-id="bf810-135">The following example sets the execution policy of PowerShell to `RemoteSigned`.</span></span>

```json
{
  "Microsoft.PowerShell.ExecutionPolicy": "RemoteSigned"
}
```

<span data-ttu-id="bf810-136">在 Windows 中，可以在和下找到對等的登錄機碼 `\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell` `HKEY_LOCAL_MACHINE` `HKEY_CURRENT_USER` 。</span><span class="sxs-lookup"><span data-stu-id="bf810-136">In Windows, the equivalent registry keys can be found in `\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell` under `HKEY_LOCAL_MACHINE` and `HKEY_CURRENT_USER`.</span></span>

### <a name="psmodulepath"></a><span data-ttu-id="bf810-137">PSModulePath</span><span class="sxs-lookup"><span data-stu-id="bf810-137">PSModulePath</span></span>

<span data-ttu-id="bf810-138">覆寫此 PowerShell 會話的 PSModulePath 元件。</span><span class="sxs-lookup"><span data-stu-id="bf810-138">Overrides a PSModulePath component for this PowerShell session.</span></span> <span data-ttu-id="bf810-139">如果設定是針對目前的使用者，則設定 CurrentUser 模組路徑。</span><span class="sxs-lookup"><span data-stu-id="bf810-139">If the configuration is for the current user, sets the CurrentUser module path.</span></span> <span data-ttu-id="bf810-140">如果設定適用于所有使用者，請設定 AllUser 模組路徑。</span><span class="sxs-lookup"><span data-stu-id="bf810-140">If the configuration is for all users, sets the AllUser module path.</span></span>

> [!WARNING]
> <span data-ttu-id="bf810-141">在這裡設定 AllUsers 或 CurrentUser 模組路徑，並不會變更 PowerShellGet 模組的限域安裝位置，例如 [Install 模組](/powershell/module/powershellget/install-module)。</span><span class="sxs-lookup"><span data-stu-id="bf810-141">Configuring an AllUsers or CurrentUser module path here will not change the scoped installation location for PowerShellGet modules like [Install-Module](/powershell/module/powershellget/install-module).</span></span>
> <span data-ttu-id="bf810-142">這些 Cmdlet 一律會使用 *預設* 的模組路徑。</span><span class="sxs-lookup"><span data-stu-id="bf810-142">These cmdlets always use the *default* module paths.</span></span>

<span data-ttu-id="bf810-143">如果未設定任何值，則會使用各自模組路徑元件的預設值。</span><span class="sxs-lookup"><span data-stu-id="bf810-143">If no value is set, the default value for the respective module path component will be used.</span></span> <span data-ttu-id="bf810-144">如需這些預設值的詳細資訊，請參閱 [about_Modules](./about_Modules.md#module-and-dsc-resource-locations-and-psmodulepath) 。</span><span class="sxs-lookup"><span data-stu-id="bf810-144">See [about_Modules](./about_Modules.md#module-and-dsc-resource-locations-and-psmodulepath) for more details on these defaults.</span></span>

<span data-ttu-id="bf810-145">這項設定可讓您使用環境變數，方法是將它們嵌入 `%` 字元（例如 `"%HOME%\Documents\PowerShell\Modules"` ），方法與 CMD 允許的相同。</span><span class="sxs-lookup"><span data-stu-id="bf810-145">This setting allows environment variables to be used by embedding them between `%` characters, like `"%HOME%\Documents\PowerShell\Modules"`, in the same way as CMD allows.</span></span> <span data-ttu-id="bf810-146">此語法也適用于 Linux 和 macOS。</span><span class="sxs-lookup"><span data-stu-id="bf810-146">This syntax also applies on Linux and macOS.</span></span> <span data-ttu-id="bf810-147">如需範例，請參閱下文。</span><span class="sxs-lookup"><span data-stu-id="bf810-147">See below for examples.</span></span>

```Schema
"PSModulePath": "<ps-module-path>"
```

<span data-ttu-id="bf810-148">其中：</span><span class="sxs-lookup"><span data-stu-id="bf810-148">Where:</span></span>

- <span data-ttu-id="bf810-149">`<ps-module-path>` 這是模組目錄的絕對路徑。</span><span class="sxs-lookup"><span data-stu-id="bf810-149">`<ps-module-path>` is the absolute path to a module directory.</span></span> <span data-ttu-id="bf810-150">針對所有使用者設定，這是 AllUsers 共用模組目錄。</span><span class="sxs-lookup"><span data-stu-id="bf810-150">For all user configurations, this is the AllUsers shared module directory.</span></span> <span data-ttu-id="bf810-151">針對目前的使用者設定，這是 CurrentUser 模組目錄。</span><span class="sxs-lookup"><span data-stu-id="bf810-151">For current user configurations, this is CurrentUser module directory.</span></span>

<span data-ttu-id="bf810-152">此範例顯示 Windows 環境的 PSModulePath 設定：</span><span class="sxs-lookup"><span data-stu-id="bf810-152">This example shows a PSModulePath configuration for a Windows environment:</span></span>

```json
{
  "PSModulePath": "C:\\Program Files\\PowerShell\\6\\Modules"
}
```

<span data-ttu-id="bf810-153">此範例顯示 macOS 或 Linux 環境的 PSModulePath 設定：</span><span class="sxs-lookup"><span data-stu-id="bf810-153">This example shows a PSModulePath configuration for a macOS or Linux environment:</span></span>

```json
{
  "PSModulePath": "/opt/powershell/6/Modules"
}
```

<span data-ttu-id="bf810-154">此範例示範如何在 PSModulePath 設定中內嵌環境變數。</span><span class="sxs-lookup"><span data-stu-id="bf810-154">This example shows embedding an environment variable in a PSModulePath configuration.</span></span> <span data-ttu-id="bf810-155">請注意，使用 `HOME` 環境變數和 `/` 目錄分隔符號時，這會在 Windows、MacOS 和 Linux 上運作。</span><span class="sxs-lookup"><span data-stu-id="bf810-155">Note that using the `HOME` environment variable and the `/` directory separator, this will work on Windows, macOS and Linux.</span></span>

```json
{
  "PSModulePath": "%HOME%/Documents/PowerShell/Modules"
}
```

<span data-ttu-id="bf810-156">此範例示範如何在 PSModulePath 設定中內嵌環境變數，此環境變數只會在 macOS 和 Linux 上運作：</span><span class="sxs-lookup"><span data-stu-id="bf810-156">This example shows embedding an environment variable in a PSModulePath configuration that will only work on macOS and Linux:</span></span>

```json
{
  "PSModulePath": "%XDG_CONFIG_HOME%/powershell/Modules"
}
```

> [!NOTE]
> <span data-ttu-id="bf810-157">PowerShell 變數無法內嵌在 PSModulePath 設定中。</span><span class="sxs-lookup"><span data-stu-id="bf810-157">PowerShell variables cannot be embedded in PSModulePath configurations.</span></span>
> <span data-ttu-id="bf810-158">Linux 和 macOS 上的 PSModulePath 設定會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="bf810-158">PSModulePath configurations on Linux and macOS are case-sensitive.</span></span> <span data-ttu-id="bf810-159">PSModulePath 設定必須針對平臺使用有效的目錄分隔符號。</span><span class="sxs-lookup"><span data-stu-id="bf810-159">A PSModulePath configuration must use valid directory separators for the platform.</span></span> <span data-ttu-id="bf810-160">在 macOS 和 Linux 上，這表示 `/` 。</span><span class="sxs-lookup"><span data-stu-id="bf810-160">On macOS and Linux, this means `/`.</span></span> <span data-ttu-id="bf810-161">在 Windows 中， `/` 和都 `\` 可以運作。</span><span class="sxs-lookup"><span data-stu-id="bf810-161">On Windows, both `/` and `\` will work.</span></span>

### <a name="experimentalfeatures"></a><span data-ttu-id="bf810-162">ExperimentalFeatures</span><span class="sxs-lookup"><span data-stu-id="bf810-162">ExperimentalFeatures</span></span>

<span data-ttu-id="bf810-163">要在 PowerShell 中啟用的實驗性功能名稱。</span><span class="sxs-lookup"><span data-stu-id="bf810-163">The names of the experimental features to enable in PowerShell.</span></span>
<span data-ttu-id="bf810-164">依預設，不會啟用任何實驗性功能。</span><span class="sxs-lookup"><span data-stu-id="bf810-164">By default, no experimental features are enabled.</span></span>
<span data-ttu-id="bf810-165">預設值為空陣列。</span><span class="sxs-lookup"><span data-stu-id="bf810-165">The default value is an empty array.</span></span>

```Schema
"ExperimentalFeatures": ["<experimental-feature-name>", ...]
```

<span data-ttu-id="bf810-166">其中：</span><span class="sxs-lookup"><span data-stu-id="bf810-166">Where:</span></span>

- <span data-ttu-id="bf810-167">`<experimental-feature-name>` 這是要啟用的實驗性功能名稱。</span><span class="sxs-lookup"><span data-stu-id="bf810-167">`<experimental-feature-name>` is the name of an experimental feature to enable.</span></span>

<span data-ttu-id="bf810-168">下列範例會啟用 PowerShell 啟動時的 **PSImplicitRemoting** 和 **PSUseAbbreviationExpansion** 實驗性功能。</span><span class="sxs-lookup"><span data-stu-id="bf810-168">The following example enables the **PSImplicitRemoting** and **PSUseAbbreviationExpansion** experimental features when PowerShell starts up.</span></span>

```json
{
  "ExperimentalFeatures": [
    "PSImplicitRemotingBatching",
    "PSUseAbbreviationExpansion"
  ]
}
```

<span data-ttu-id="bf810-169">如需實驗性功能的詳細資訊，請參閱 [POWERSHELL RFC 29][RFC0029]。</span><span class="sxs-lookup"><span data-stu-id="bf810-169">For more information on experimental features, see [PowerShell RFC 29][RFC0029].</span></span>

## <a name="non-windows-logging-configuration"></a><span data-ttu-id="bf810-170">非 Windows 記錄設定</span><span class="sxs-lookup"><span data-stu-id="bf810-170">Non-Windows logging configuration</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bf810-171">本節中的設定選項僅適用于 macOS 和 Linux。</span><span class="sxs-lookup"><span data-stu-id="bf810-171">The configuration options in this section only apply to macOS and Linux.</span></span>
> <span data-ttu-id="bf810-172">Windows 的記錄是由 Windows 事件檢視器所管理。</span><span class="sxs-lookup"><span data-stu-id="bf810-172">Logging for Windows is managed by the Windows Event Viewer.</span></span>

<span data-ttu-id="bf810-173">您可以在 PowerShell 設定檔中設定 PowerShell 在 macOS 和 Linux 上的記錄。</span><span class="sxs-lookup"><span data-stu-id="bf810-173">PowerShell's logging on macOS and Linux can be configured in the PowerShell configuration file.</span></span> <span data-ttu-id="bf810-174">如需非 Windows 系統 PowerShell 記錄的完整說明，請參閱 [關於記錄](./about_Logging_Non-Windows.md)。</span><span class="sxs-lookup"><span data-stu-id="bf810-174">For a full description of PowerShell logging for non-Windows systems, see [About Logging](./about_Logging_Non-Windows.md).</span></span>

### <a name="logidentity"></a><span data-ttu-id="bf810-175">LogIdentity</span><span class="sxs-lookup"><span data-stu-id="bf810-175">LogIdentity</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bf810-176">這項設定只能在 macOS 和 Linux 中使用。</span><span class="sxs-lookup"><span data-stu-id="bf810-176">This setting can only be used in macOS and Linux.</span></span>

<span data-ttu-id="bf810-177">設定用來寫入系統記錄檔的身分識別名稱。</span><span class="sxs-lookup"><span data-stu-id="bf810-177">Sets the identity name used to write to the system log.</span></span> <span data-ttu-id="bf810-178">預設值為 "powershell"。</span><span class="sxs-lookup"><span data-stu-id="bf810-178">The default value is "powershell".</span></span>

```Schema
"LogIdentity": "<log-identity>"
```

<span data-ttu-id="bf810-179">其中：</span><span class="sxs-lookup"><span data-stu-id="bf810-179">Where:</span></span>

- <span data-ttu-id="bf810-180">`<log-identity>` 這是 PowerShell 應用來寫入 syslog 的字串識別。</span><span class="sxs-lookup"><span data-stu-id="bf810-180">`<log-identity>` is the string identity that PowerShell should use for writing to syslog.</span></span>

> [!NOTE]
> <span data-ttu-id="bf810-181">您可能會想要針對每個已安裝的不同 PowerShell 實例，各有不同的 **LogIdentity** 值。</span><span class="sxs-lookup"><span data-stu-id="bf810-181">You may want to have different **LogIdentity** values for each different instance of PowerShell you have installed.</span></span>

<span data-ttu-id="bf810-182">在此範例中，我們會設定 PowerShell 預覽版本的 **LogIdentity** 。</span><span class="sxs-lookup"><span data-stu-id="bf810-182">In this example, we are configuring the **LogIdentity** for a preview release of PowerShell.</span></span>

```json
{
  "LogIdentity": "powershell-preview"
}
```

### <a name="loglevel"></a><span data-ttu-id="bf810-183">LogLevel</span><span class="sxs-lookup"><span data-stu-id="bf810-183">LogLevel</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bf810-184">這項設定只能在 macOS 和 Linux 中使用。</span><span class="sxs-lookup"><span data-stu-id="bf810-184">This setting can only be used in macOS and Linux.</span></span>

<span data-ttu-id="bf810-185">指定 PowerShell 應記錄的最低嚴重性層級。</span><span class="sxs-lookup"><span data-stu-id="bf810-185">Specifies the minimum severity level at which PowerShell should log.</span></span>

```Schema
"LogLevel": "<log-level>|default"
```

<span data-ttu-id="bf810-186">其中：</span><span class="sxs-lookup"><span data-stu-id="bf810-186">Where:</span></span>

- <span data-ttu-id="bf810-187">`<log-level>` 是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="bf810-187">`<log-level>` is one of:</span></span>
  - <span data-ttu-id="bf810-188">一律</span><span class="sxs-lookup"><span data-stu-id="bf810-188">Always</span></span>
  - <span data-ttu-id="bf810-189">重大</span><span class="sxs-lookup"><span data-stu-id="bf810-189">Critical</span></span>
  - <span data-ttu-id="bf810-190">[錯誤]</span><span class="sxs-lookup"><span data-stu-id="bf810-190">Error</span></span>
  - <span data-ttu-id="bf810-191">警告</span><span class="sxs-lookup"><span data-stu-id="bf810-191">Warning</span></span>
  - <span data-ttu-id="bf810-192">資訊</span><span class="sxs-lookup"><span data-stu-id="bf810-192">Informational</span></span>
  - <span data-ttu-id="bf810-193">「詳細資訊」</span><span class="sxs-lookup"><span data-stu-id="bf810-193">Verbose</span></span>
  - <span data-ttu-id="bf810-194">偵錯</span><span class="sxs-lookup"><span data-stu-id="bf810-194">Debug</span></span>

> [!NOTE]
> <span data-ttu-id="bf810-195">設定記錄層級會啟用其上方的所有記錄層級。</span><span class="sxs-lookup"><span data-stu-id="bf810-195">Setting a the log level enables all log levels above it.</span></span>

<span data-ttu-id="bf810-196">將此設定設為 [ **預設** 值]，將會被視為預設值。</span><span class="sxs-lookup"><span data-stu-id="bf810-196">Setting this setting to **default** will be interpreted as the default value.</span></span>
<span data-ttu-id="bf810-197">預設值為 [ **資訊** ]。</span><span class="sxs-lookup"><span data-stu-id="bf810-197">The default value is **Informational** .</span></span>

<span data-ttu-id="bf810-198">下列範例會將值設定為 **Verbose** 。</span><span class="sxs-lookup"><span data-stu-id="bf810-198">The following example sets the value to **Verbose** .</span></span>

```json
{
  "LogLevel": "Verbose"
}
```

### <a name="logchannels"></a><span data-ttu-id="bf810-199">LogChannels</span><span class="sxs-lookup"><span data-stu-id="bf810-199">LogChannels</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bf810-200">這項設定只能在 macOS 和 Linux 中使用。</span><span class="sxs-lookup"><span data-stu-id="bf810-200">This setting can only be used in macOS and Linux.</span></span>

<span data-ttu-id="bf810-201">決定要啟用的記錄通道。</span><span class="sxs-lookup"><span data-stu-id="bf810-201">Determines which logging channels are enabled.</span></span>

```Schema
"LogChannels": "<log-channel>,..."
```

<span data-ttu-id="bf810-202">其中：</span><span class="sxs-lookup"><span data-stu-id="bf810-202">Where:</span></span>

- <span data-ttu-id="bf810-203">`<log-channel>` 是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="bf810-203">`<log-channel>` is one of:</span></span>
  - <span data-ttu-id="bf810-204">操作-記錄 PowerShell 活動的基本資訊</span><span class="sxs-lookup"><span data-stu-id="bf810-204">Operational - logs basic information about PowerShell activities</span></span>
  - <span data-ttu-id="bf810-205">分析-記錄更詳細的診斷資訊</span><span class="sxs-lookup"><span data-stu-id="bf810-205">Analytic - logs more detailed diagnostic information</span></span>

<span data-ttu-id="bf810-206">預設值為 [可 **操作** ]。</span><span class="sxs-lookup"><span data-stu-id="bf810-206">The default value is **Operational** .</span></span> <span data-ttu-id="bf810-207">若要同時啟用這兩個通道，請將這兩個值都包含為以逗號分隔的單一字串。</span><span class="sxs-lookup"><span data-stu-id="bf810-207">To enable both channels, include both values as a single comma-separated string.</span></span> <span data-ttu-id="bf810-208">例如：</span><span class="sxs-lookup"><span data-stu-id="bf810-208">For example:</span></span>

```json
{
  "LogChannels": "Operational,Analytic"
}
```

### <a name="logkeywords"></a><span data-ttu-id="bf810-209">LogKeywords</span><span class="sxs-lookup"><span data-stu-id="bf810-209">LogKeywords</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bf810-210">這項設定只能在 macOS 和 Linux 中使用。</span><span class="sxs-lookup"><span data-stu-id="bf810-210">This setting can only be used in macOS and Linux.</span></span>

<span data-ttu-id="bf810-211">決定要記錄的 PowerShell 部分。</span><span class="sxs-lookup"><span data-stu-id="bf810-211">Determines which parts of PowerShell are logged.</span></span> <span data-ttu-id="bf810-212">預設會啟用所有的記錄關鍵字。</span><span class="sxs-lookup"><span data-stu-id="bf810-212">By default, all log keywords are enabled.</span></span> <span data-ttu-id="bf810-213">若要啟用多個關鍵字，請以單一逗號分隔字串列出值。</span><span class="sxs-lookup"><span data-stu-id="bf810-213">To enable multiple keywords, list the values in a single comma-separated string.</span></span>

```Schema
"LogKeywords": "<log-keyword>,..."
```

<span data-ttu-id="bf810-214">其中：</span><span class="sxs-lookup"><span data-stu-id="bf810-214">Where:</span></span>

- <span data-ttu-id="bf810-215">`<log-keyword>` 是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="bf810-215">`<log-keyword>` is one of:</span></span>
  - <span data-ttu-id="bf810-216">運行時-運行時管理</span><span class="sxs-lookup"><span data-stu-id="bf810-216">Runspace - runspace management</span></span>
  - <span data-ttu-id="bf810-217">管線管線作業</span><span class="sxs-lookup"><span data-stu-id="bf810-217">Pipeline - pipeline operations</span></span>
  - <span data-ttu-id="bf810-218">通訊協定通訊通訊協定處理，例如 PSRP</span><span class="sxs-lookup"><span data-stu-id="bf810-218">Protocol - communication protocol handling, such as PSRP</span></span>
  - <span data-ttu-id="bf810-219">傳輸-傳輸層支援，例如 SSH</span><span class="sxs-lookup"><span data-stu-id="bf810-219">Transport - transport layer support, such as SSH</span></span>
  - <span data-ttu-id="bf810-220">主機-PowerShell 主機功能，例如主控台互動</span><span class="sxs-lookup"><span data-stu-id="bf810-220">Host - PowerShell host functionality, for example console interaction</span></span>
  - <span data-ttu-id="bf810-221">Cmdlet-PowerShell 內建 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="bf810-221">Cmdlets -PowerShell builtin cmdlets</span></span>
  - <span data-ttu-id="bf810-222">序列化程式-序列化邏輯</span><span class="sxs-lookup"><span data-stu-id="bf810-222">Serializer - serialization logic</span></span>
  - <span data-ttu-id="bf810-223">會話-PowerShell 會話狀態</span><span class="sxs-lookup"><span data-stu-id="bf810-223">Session - PowerShell session state</span></span>
  - <span data-ttu-id="bf810-224">ManagedPlugin-WSMan 外掛程式</span><span class="sxs-lookup"><span data-stu-id="bf810-224">ManagedPlugin - WSMan plugin</span></span>

> [!NOTE]
> <span data-ttu-id="bf810-225">通常建議您將此值保留為未設定，除非您嘗試在 PowerShell 的已知部分中診斷特定行為。</span><span class="sxs-lookup"><span data-stu-id="bf810-225">It is generally advised to leave this value unset unless you are trying to diagnose a specific behavior in a known part of PowerShell.</span></span>
> <span data-ttu-id="bf810-226">變更此值只會減少記錄的資訊量。</span><span class="sxs-lookup"><span data-stu-id="bf810-226">Changing this value only decreases the amount of information logged.</span></span>

<span data-ttu-id="bf810-227">此範例會將記錄限制為運行空間作業、管線邏輯和 Cmdlet 使用。</span><span class="sxs-lookup"><span data-stu-id="bf810-227">This example limits the logging to runspace operations, pipeline logic, and cmdlet use.</span></span> <span data-ttu-id="bf810-228">將會忽略所有其他記錄。</span><span class="sxs-lookup"><span data-stu-id="bf810-228">All other logging will be omitted.</span></span>

```json
"LogKeywords": "Runspace,Pipeline,Cmdlets"
```

<!--

## Group policy configuration

### ScriptExecution

### ScriptBlockLogging

### ProtectedEventLogging

### Transcription

### UpdateableHelp

### ConsoleSessionConfiguration

-->

## <a name="more-example-configurations"></a><span data-ttu-id="bf810-229">更多範例設定</span><span class="sxs-lookup"><span data-stu-id="bf810-229">More example configurations</span></span>

### <a name="example-windows-configuration"></a><span data-ttu-id="bf810-230">Windows 設定範例</span><span class="sxs-lookup"><span data-stu-id="bf810-230">Example Windows configuration</span></span>

<span data-ttu-id="bf810-231">此設定會明確設定更多設定：</span><span class="sxs-lookup"><span data-stu-id="bf810-231">This configuration has more settings explicitly set:</span></span>

- <span data-ttu-id="bf810-232">此 PowerShell 安裝的執行原則是 `AllSigned`</span><span class="sxs-lookup"><span data-stu-id="bf810-232">Execution policy for this PowerShell installation is `AllSigned`</span></span>
- <span data-ttu-id="bf810-233">CurrentUser 模組路徑設定為共用磁片磁碟機上的模組目錄</span><span class="sxs-lookup"><span data-stu-id="bf810-233">The CurrentUser module path is set to a module directory on a shared drive</span></span>
- <span data-ttu-id="bf810-234">`PSImplicitRemotingBatching`實驗性功能已啟用</span><span class="sxs-lookup"><span data-stu-id="bf810-234">The `PSImplicitRemotingBatching` experimental feature is enabled</span></span>

> [!NOTE]
> <span data-ttu-id="bf810-235">`ExecutionPolicy`這裡的和 `PSModulePath` 設定只能在 Windows 平臺上運作，因為模組路徑使用 `\` 和 `;` 分隔字元，而且執行原則不 `Unrestricted` () UNIX 平臺上唯一允許的原則。</span><span class="sxs-lookup"><span data-stu-id="bf810-235">The `ExecutionPolicy` and `PSModulePath` settings here would only work on a Windows platform, since the module path uses `\` and `;` separator characters and the execution policy is not `Unrestricted` (the only policy allowed on UNIX-like platforms).</span></span>

```json
{
  "Microsoft.PowerShell.ExecutionPolicy": "AllSigned",
  "PSModulePath": "Z:\\Marisol's Shared Drive\\Modules",
  "ExperimentalFeatures": ["PSImplicitRemotingBatching"],
}
```

### <a name="example-non-windows-configuration"></a><span data-ttu-id="bf810-236">非 Windows 設定範例</span><span class="sxs-lookup"><span data-stu-id="bf810-236">Example non-Windows configuration</span></span>

<span data-ttu-id="bf810-237">這項設定會設定一些選項，這些選項只適用于 macOS 或 Linux：</span><span class="sxs-lookup"><span data-stu-id="bf810-237">This configuration sets a number of options that only work in macOS or Linux:</span></span>

- <span data-ttu-id="bf810-238">CurrentUser 模組路徑設定為中的自訂模組目錄 `$HOME`</span><span class="sxs-lookup"><span data-stu-id="bf810-238">The CurrentUser module path is set to a custom module directory in `$HOME`</span></span>
- <span data-ttu-id="bf810-239">已啟用 **PSImplicitRemotingBatching** 實驗性功能</span><span class="sxs-lookup"><span data-stu-id="bf810-239">The **PSImplicitRemotingBatching** experimental feature is enabled</span></span>
- <span data-ttu-id="bf810-240">PowerShell 記錄層級設定為 [ **詳細** 資訊]，以進行詳細記錄</span><span class="sxs-lookup"><span data-stu-id="bf810-240">The PowerShell logging level is set to **Verbose** , for more logging</span></span>
- <span data-ttu-id="bf810-241">此 PowerShell 安裝會使用 **home PowerShell** 身分識別來寫入記錄。</span><span class="sxs-lookup"><span data-stu-id="bf810-241">This PowerShell installation writes to the logs using the **home-powershell** identity.</span></span>

```json
{
  "PSModulePath": "%HOME%/.powershell/Modules",
  "ExperimentalFeatures": ["PSImplicitRemotingBatching"],
  "LogLevel": "Verbose",
  "LogIdentity": "home-powershell"
}
```

## <a name="see-also"></a><span data-ttu-id="bf810-242">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf810-242">See also</span></span>

[<span data-ttu-id="bf810-243">關於執行原則</span><span class="sxs-lookup"><span data-stu-id="bf810-243">About Execution Policies</span></span>](./about_Execution_Policies.md)

[<span data-ttu-id="bf810-244">關於自動變數</span><span class="sxs-lookup"><span data-stu-id="bf810-244">About Automatic Variables</span></span>](./about_Automatic_Variables.md)

[RFC0029]: https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md
