---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/16/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/update-help?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-Help
ms.openlocfilehash: 4ef0865e81e01746fed77b73e265e68086a7a9e1
ms.sourcegitcommit: d3f78120bdc9096c72aa0dfdbdd91efaf254c738
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "93205847"
---
# <span data-ttu-id="2a240-103">Update-Help</span><span class="sxs-lookup"><span data-stu-id="2a240-103">Update-Help</span></span>

## <span data-ttu-id="2a240-104">概要</span><span class="sxs-lookup"><span data-stu-id="2a240-104">SYNOPSIS</span></span>
<span data-ttu-id="2a240-105">下載最新的說明檔並安裝於電腦上。</span><span class="sxs-lookup"><span data-stu-id="2a240-105">Downloads and installs the newest help files on your computer.</span></span>

## <span data-ttu-id="2a240-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2a240-106">SYNTAX</span></span>

### <span data-ttu-id="2a240-107">路徑 (預設值)</span><span class="sxs-lookup"><span data-stu-id="2a240-107">Path (Default)</span></span>

```
Update-Help [[-Module] <String[]>] [-FullyQualifiedModule <ModuleSpecification[]>]
 [[-SourcePath] <String[]>] [-Recurse] [[-UICulture] <CultureInfo[]>] [-Credential <PSCredential>]
 [-UseDefaultCredentials] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="2a240-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="2a240-108">LiteralPath</span></span>

```
Update-Help [[-Module] <String[]>] [-FullyQualifiedModule <ModuleSpecification[]>]
 [-LiteralPath <String[]>] [-Recurse] [[-UICulture] <CultureInfo[]>] [-Credential <PSCredential>]
 [-UseDefaultCredentials] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="2a240-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="2a240-109">DESCRIPTION</span></span>

<span data-ttu-id="2a240-110">`Update-Help`Cmdlet 會下載適用于 PowerShell 模組的最新說明檔案，並將其安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="2a240-110">The `Update-Help` cmdlet downloads the newest help files for PowerShell modules and installs them on your computer.</span></span> <span data-ttu-id="2a240-111">您不需要重新開機 PowerShell 來使變更生效。</span><span class="sxs-lookup"><span data-stu-id="2a240-111">You need not restart PowerShell to make the change effective.</span></span> <span data-ttu-id="2a240-112">您可以使用 `Get-Help` Cmdlet 立即查看新的說明檔。</span><span class="sxs-lookup"><span data-stu-id="2a240-112">You can use the `Get-Help` cmdlet to view the new help files immediately.</span></span>

<span data-ttu-id="2a240-113">`Update-Help` 檢查電腦上的說明檔版本。</span><span class="sxs-lookup"><span data-stu-id="2a240-113">`Update-Help` checks the version of the help files on your computer.</span></span> <span data-ttu-id="2a240-114">如果您沒有模組的說明檔，或您的說明檔已過期，則會 `Update-Help` 下載最新的說明檔。</span><span class="sxs-lookup"><span data-stu-id="2a240-114">If you don't have help files for a module or if your help files are outdated, `Update-Help` downloads the newest help files.</span></span> <span data-ttu-id="2a240-115">您可以從網際網路或檔案共用下載和安裝說明檔。</span><span class="sxs-lookup"><span data-stu-id="2a240-115">The help files can be downloaded and installed from the internet or a file share.</span></span>

<span data-ttu-id="2a240-116">如果沒有參數， `Update-Help` 則會更新會話中模組的說明檔，以及所有支援「可更新的說明」的已安裝模組。</span><span class="sxs-lookup"><span data-stu-id="2a240-116">Without parameters, `Update-Help` updates the help files for modules in the session and for all installed modules that support Updatable Help.</span></span> <span data-ttu-id="2a240-117">包含在目前會話中安裝但未載入的模組。</span><span class="sxs-lookup"><span data-stu-id="2a240-117">Modules that are installed but not loaded in the current session are included.</span></span> <span data-ttu-id="2a240-118">PowerShell 模組會儲存在環境變數中所列的位置 `$env:PSModulePath` 。</span><span class="sxs-lookup"><span data-stu-id="2a240-118">PowerShell modules are stored in a location listed in the `$env:PSModulePath` environment variable.</span></span> <span data-ttu-id="2a240-119">如需詳細資訊，請參閱 [about_Updatable_Help](./About/about_Updatable_Help.md)。</span><span class="sxs-lookup"><span data-stu-id="2a240-119">For more information, see [about_Updatable_Help](./About/about_Updatable_Help.md).</span></span>

<span data-ttu-id="2a240-120">您可以使用 **Module** 參數來更新特定模組的說明檔。</span><span class="sxs-lookup"><span data-stu-id="2a240-120">You can use the **Module** parameter to update help files for a particular module.</span></span> <span data-ttu-id="2a240-121">使用 **UICulture** 參數以多種語言和地區設定下載說明檔。</span><span class="sxs-lookup"><span data-stu-id="2a240-121">Use the **UICulture** parameter to download help files in multiple languages and locales.</span></span>

<span data-ttu-id="2a240-122">您也可以 `Update-Help` 在未連線到網際網路的電腦上使用。</span><span class="sxs-lookup"><span data-stu-id="2a240-122">You can also use `Update-Help` on computers that are not connected to the internet.</span></span> <span data-ttu-id="2a240-123">首先，使用 `Save-Help` Cmdlet 從網際網路下載說明檔，並將其儲存在未連線至網際網路之系統可存取的共用資料夾中。</span><span class="sxs-lookup"><span data-stu-id="2a240-123">First, use the `Save-Help`cmdlet to download help files from the internet and save them in a shared folder that is accessible to the system not connected to the internet.</span></span> <span data-ttu-id="2a240-124">然後使用的 **SourcePath** 參數 `Update-Help` ，從共用下載已更新的說明檔，並安裝在電腦上。</span><span class="sxs-lookup"><span data-stu-id="2a240-124">Then use the **SourcePath** parameter of `Update-Help` to download the updated help files from the shared and install them on the computer.</span></span>

<span data-ttu-id="2a240-125">您可以藉由將指令程式新增 `Update-Help` 至 PowerShell 設定檔，將說明更新自動化。</span><span class="sxs-lookup"><span data-stu-id="2a240-125">You can automate help updates by adding the `Update-Help` cmdlet to your PowerShell profile.</span></span> <span data-ttu-id="2a240-126">依預設， `Update-Help` 每一部電腦上只會執行一次一次。</span><span class="sxs-lookup"><span data-stu-id="2a240-126">By default, `Update-Help` runs only one time per day on each computer.</span></span> <span data-ttu-id="2a240-127">若要覆寫每天一次的限制，請使用 **Force** 參數。</span><span class="sxs-lookup"><span data-stu-id="2a240-127">To override the once-per-day limit, use the **Force** parameter.</span></span>

<span data-ttu-id="2a240-128">`Update-Help`Cmdlet 是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="2a240-128">The `Update-Help` cmdlet was introduced in Windows PowerShell 3.0.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2a240-129">`Update-Help` 需要系統管理許可權。</span><span class="sxs-lookup"><span data-stu-id="2a240-129">`Update-Help` requires administrative privileges.</span></span>
>
> <span data-ttu-id="2a240-130">您必須是電腦上 Administrators 群組的成員，才能更新 PowerShell Core 模組的說明檔。</span><span class="sxs-lookup"><span data-stu-id="2a240-130">You must be a member of the Administrators group on the computer to update the help files for the PowerShell Core modules.</span></span>
>
> <span data-ttu-id="2a240-131">若要下載或更新 PowerShell 安裝目錄中模組的說明檔 (`$PSHOME\Modules`) （包括 PowerShell Core 模組），請使用 [以系統管理員身分執行] 選項啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="2a240-131">To download or update the help files for modules in the PowerShell installation directory (`$PSHOME\Modules`), including the PowerShell Core modules, start PowerShell by using the Run as administrator option.</span></span>
> <span data-ttu-id="2a240-132">例如： `Start-Process powershell.exe -Verb RunAs` 。</span><span class="sxs-lookup"><span data-stu-id="2a240-132">For example: `Start-Process powershell.exe -Verb RunAs`.</span></span>
>
> <span data-ttu-id="2a240-133">您也可以在 Windows PowerShell 整合式腳本環境 (ISE) 的 [說明] 功能表中，使用 [說明] 功能表中的 [更新 Windows PowerShell 說明] 功能表項目來更新說明檔。</span><span class="sxs-lookup"><span data-stu-id="2a240-133">You can also update help files by using the Update Windows PowerShell Help menu item in the Help menu in Windows PowerShell Integrated Scripting Environment (ISE).</span></span>
>
> <span data-ttu-id="2a240-134">Update Windows PowerShell Help 專案 `Update-Help` 會執行沒有參數的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2a240-134">The Update Windows PowerShell Help item runs an `Update-Help` cmdlet without parameters.</span></span>
> <span data-ttu-id="2a240-135">若要更新目錄中模組的說明 `$PSHOME` ，請使用 [以系統管理員身分執行] 選項啟動 Windows PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="2a240-135">To update help for modules in the `$PSHOME` directory, start Windows PowerShell ISE by using the Run as administrator option.</span></span>

## <span data-ttu-id="2a240-136">範例</span><span class="sxs-lookup"><span data-stu-id="2a240-136">EXAMPLES</span></span>

### <span data-ttu-id="2a240-137">範例1：更新所有模組的說明檔</span><span class="sxs-lookup"><span data-stu-id="2a240-137">Example 1: Update help files for all modules</span></span>

<span data-ttu-id="2a240-138">指令 `Update-Help` 程式會更新支援「可更新的說明」之已安裝模組的說明檔。</span><span class="sxs-lookup"><span data-stu-id="2a240-138">The `Update-Help` cmdlet updates help files for installed modules that support Updatable Help.</span></span> <span data-ttu-id="2a240-139">系統會在作業系統中設定使用者介面 (UI) 文化特性語言。</span><span class="sxs-lookup"><span data-stu-id="2a240-139">The user-interface (UI) culture language is set in the operating system.</span></span>

```powershell
Update-Help
```

### <span data-ttu-id="2a240-140">範例2：更新指定模組的說明檔</span><span class="sxs-lookup"><span data-stu-id="2a240-140">Example 2: Update help files for specified modules</span></span>

<span data-ttu-id="2a240-141">此 `Update-Help` Cmdlet 只會更新以 **Microsoft. PowerShell** 開頭之模組名稱的說明檔。</span><span class="sxs-lookup"><span data-stu-id="2a240-141">The `Update-Help` cmdlet updates help files only for module names that begin with **Microsoft.PowerShell** .</span></span>

```powershell
Update-Help -Module Microsoft.PowerShell*
```

### <span data-ttu-id="2a240-142">範例3：更新不同語言的說明檔</span><span class="sxs-lookup"><span data-stu-id="2a240-142">Example 3: Update help files for different languages</span></span>

<span data-ttu-id="2a240-143">此 `Update-Help` Cmdlet 會為所有模組更新日文 (ja-jp) 和英文 (en-us) 說明檔。</span><span class="sxs-lookup"><span data-stu-id="2a240-143">The `Update-Help` cmdlet updates the Japanese (ja-JP) and English (en-US) help files for all modules.</span></span>

<span data-ttu-id="2a240-144">如果模組未提供指定 UI 文化特性的說明檔，則會顯示模組和 UI 文化特性的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="2a240-144">If a module doesn't provide help files for a specified UI culture, an error message is displayed for the module and UI culture.</span></span> <span data-ttu-id="2a240-145">在此範例中，錯誤訊息會指出找不 **到模組的** **ja-jp** 說明檔。</span><span class="sxs-lookup"><span data-stu-id="2a240-145">In this example, the error message indicates that the **ja-JP** help files were not found for module **Microsoft.PowerShell.Utility** .</span></span>

```powershell
Update-Help -UICulture ja-JP, en-US
```

```Output
Update-Help : Failed to update Help for the module(s) 'Microsoft.PowerShell.Utility' with UI culture(s) {ja-JP}
No UI culture was found that matches the following pattern: ja-JP.
```

### <span data-ttu-id="2a240-146">範例4：自動更新說明檔</span><span class="sxs-lookup"><span data-stu-id="2a240-146">Example 4: Update help files automatically</span></span>

<span data-ttu-id="2a240-147">這個範例會建立排程工作，以在每天上午3:00 更新所有模組的說明。</span><span class="sxs-lookup"><span data-stu-id="2a240-147">This example creates a scheduled job that updates help for all modules every day at 3:00 AM.</span></span>

```powershell
$jobParams = @{
  Name = 'UpdateHelpJob'
  Credential = 'Domain01\User01'
  ScriptBlock = '{Update-Help}'
  Trigger = (New-JobTrigger -Daily -At "3 AM")
}
Register-ScheduledJob @jobParams
```

```Output
Id         Name            JobTriggers     Command                                  Enabled
--         ----            -----------     -------                                  -------
1          UpdateHelpJob   1               Update-Help                              True
```

<span data-ttu-id="2a240-148">此 `Register-ScheduledJob` Cmdlet 會建立執行命令的排程工作 `Update-Help` 。</span><span class="sxs-lookup"><span data-stu-id="2a240-148">The `Register-ScheduledJob` cmdlet creates a scheduled job that runs an `Update-Help` command.</span></span> <span data-ttu-id="2a240-149">此命令會使用 **Credential** `Update-Help` 電腦上 Administrators 群組成員的認證來執行 Credential 參數。</span><span class="sxs-lookup"><span data-stu-id="2a240-149">The command uses the **Credential** parameter to run `Update-Help` by using the credentials of a member of the Administrators group on the computer.</span></span> <span data-ttu-id="2a240-150">**觸發** 程式參數的值是一個 `New-JobTrigger` 命令，此命令會建立工作觸發程式，以在每天上午3:00 啟動工作。</span><span class="sxs-lookup"><span data-stu-id="2a240-150">The value of the **Trigger** parameter is a `New-JobTrigger` command that creates a job trigger that starts the job every day at 3:00 AM.</span></span>

<span data-ttu-id="2a240-151">若要執行 `Register-ScheduledJob` 命令，請使用 [以 **系統管理員身分執行** ] 選項啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="2a240-151">To run the `Register-ScheduledJob` command, start PowerShell by using the **Run as administrator** option.</span></span> <span data-ttu-id="2a240-152">PowerShell 會提示您輸入 **Credential** 參數中所指定使用者的密碼。</span><span class="sxs-lookup"><span data-stu-id="2a240-152">PowerShell prompts you for the password of the user specified in the **Credential** parameter.</span></span> <span data-ttu-id="2a240-153">認證會與排程工作一起儲存。</span><span class="sxs-lookup"><span data-stu-id="2a240-153">The credentials are stored with the scheduled job.</span></span> <span data-ttu-id="2a240-154">當工作執行時，系統不會提示您。</span><span class="sxs-lookup"><span data-stu-id="2a240-154">You aren't prompted when the job runs.</span></span>

<span data-ttu-id="2a240-155">您可以使用 `Get-ScheduledJob` Cmdlet 來查看排程工作，使用 `Set-ScheduledJob` Cmdlet 進行變更，然後使用 `Unregister-ScheduledJob` Cmdlet 來刪除它。</span><span class="sxs-lookup"><span data-stu-id="2a240-155">You can use the `Get-ScheduledJob` cmdlet to view the scheduled job, use the `Set-ScheduledJob` cmdlet to change it, and use the `Unregister-ScheduledJob` cmdlet to delete it.</span></span> <span data-ttu-id="2a240-156">您也可以在下列路徑，利用 [工作排程器] 檢視與管理排程工作：</span><span class="sxs-lookup"><span data-stu-id="2a240-156">You can also view and manage the scheduled job in Task Scheduler in the following path:</span></span>

<span data-ttu-id="2a240-157">`Task Scheduler Library\Microsoft\Windows\PowerShell\ScheduledJobs`.</span><span class="sxs-lookup"><span data-stu-id="2a240-157">`Task Scheduler Library\Microsoft\Windows\PowerShell\ScheduledJobs`.</span></span>

### <span data-ttu-id="2a240-158">範例5：從檔案共用更新多部電腦上的說明檔</span><span class="sxs-lookup"><span data-stu-id="2a240-158">Example 5: Update help files on multiple computers from a file share</span></span>

<span data-ttu-id="2a240-159">在此範例中，會從網際網路下載已更新的說明檔，並將其儲存在檔案共用中。</span><span class="sxs-lookup"><span data-stu-id="2a240-159">In this example, updated help files are downloaded from the internet and saved in a file share.</span></span> <span data-ttu-id="2a240-160">需要擁有存取檔案共用和安裝更新之許可權的使用者認證。</span><span class="sxs-lookup"><span data-stu-id="2a240-160">User credentials are needed that have permissions to access the file share and install updates.</span></span> <span data-ttu-id="2a240-161">使用檔案共用時，可以更新位於防火牆後方或未連線到網際網路的電腦。</span><span class="sxs-lookup"><span data-stu-id="2a240-161">When a file share is used, it's possible to update computers that are behind firewalls or aren't connected to the internet.</span></span>

```powershell
Save-Help -DestinationPath \\Server01\Share\PSHelp -Credential Domain01\Admin01
Invoke-Command -ComputerName (Get-Content Servers.txt) -ScriptBlock {
     Update-Help -SourcePath \\Server01\Share\PSHelp -Credential Domain01\Admin01
}
```

<span data-ttu-id="2a240-162">此 `Save-Help` 命令會為所有支援「可更新的說明」的模組下載最新的說明檔。</span><span class="sxs-lookup"><span data-stu-id="2a240-162">The `Save-Help` command downloads the newest help files for all modules that support Updatable Help.</span></span>
<span data-ttu-id="2a240-163">**DestinationPath** 參數會將檔案儲存在檔案 `\\Server01\Share\PSHelp` 共用中。</span><span class="sxs-lookup"><span data-stu-id="2a240-163">The **DestinationPath** parameter saves the files in the `\\Server01\Share\PSHelp` file share.</span></span> <span data-ttu-id="2a240-164">**Credential** 參數指定有權存取檔案共用的使用者。</span><span class="sxs-lookup"><span data-stu-id="2a240-164">The **Credential** parameter specifies a user who has permission to access the file share.</span></span>

<span data-ttu-id="2a240-165">此 `Invoke-Command` Cmdlet 會 `Update-Help` 在多部電腦上執行遠端命令。</span><span class="sxs-lookup"><span data-stu-id="2a240-165">The `Invoke-Command` cmdlet runs remote `Update-Help` commands on multiple computers.</span></span> <span data-ttu-id="2a240-166">**ComputerName** 參數會從 **Servers.txt** 檔案取得遠端電腦的清單。</span><span class="sxs-lookup"><span data-stu-id="2a240-166">The **ComputerName** parameter gets a list of remote computers from the **Servers.txt** file.</span></span> <span data-ttu-id="2a240-167">**ScriptBlock** 參數會執行 `Update-Help` 命令，並使用 **SourcePath** 參數指定包含已更新說明檔的檔案共用。</span><span class="sxs-lookup"><span data-stu-id="2a240-167">The **ScriptBlock** parameter runs the `Update-Help` command and uses the **SourcePath** parameter to specify the file share that contains the updated help files.</span></span> <span data-ttu-id="2a240-168">**Credential** 參數會指定可以存取檔案共用並執行遠端命令的使用者 `Update-Help` 。</span><span class="sxs-lookup"><span data-stu-id="2a240-168">The **Credential** parameter specifies a user who can access the file share and run the remote `Update-Help` command.</span></span>

### <span data-ttu-id="2a240-169">範例6：取得已更新說明檔的清單</span><span class="sxs-lookup"><span data-stu-id="2a240-169">Example 6: Get a list of updated help files</span></span>

<span data-ttu-id="2a240-170">此 `Update-Help` Cmdlet 會更新指定模組的說明。</span><span class="sxs-lookup"><span data-stu-id="2a240-170">The `Update-Help` cmdlet updates help for a specified module.</span></span> <span data-ttu-id="2a240-171">此 Cmdlet 會使用 **Verbose** 一般參數來顯示已更新的說明檔清單。</span><span class="sxs-lookup"><span data-stu-id="2a240-171">The cmdlet uses the **Verbose** common parameter to display the list of help files that were updated.</span></span> <span data-ttu-id="2a240-172">您可以使用 [ **詳細** 資訊] 來查看特定模組的所有說明檔或說明檔的輸出。</span><span class="sxs-lookup"><span data-stu-id="2a240-172">You can use **Verbose** to view output for all help files or help files for a specific module.</span></span>

<span data-ttu-id="2a240-173">如果沒有 **Verbose** 參數，則 `Update-Help` 不會顯示命令的結果。</span><span class="sxs-lookup"><span data-stu-id="2a240-173">Without the **Verbose** parameter, `Update-Help` doesn't display the results of the command.</span></span> <span data-ttu-id="2a240-174">**詳細** 資訊參數輸出適用于驗證說明檔是否已更新，或是否已安裝最新版本。</span><span class="sxs-lookup"><span data-stu-id="2a240-174">The **Verbose** parameter output is useful to verify that the help files were updated or if the latest version is installed.</span></span>

```powershell
Update-Help -Module Microsoft.PowerShell.Utility -Verbose
```

### <span data-ttu-id="2a240-175">範例7：尋找支援「可更新的說明」的模組</span><span class="sxs-lookup"><span data-stu-id="2a240-175">Example 7: Find modules that support Updatable Help</span></span>

<span data-ttu-id="2a240-176">此範例會列出支援「可更新的說明」的模組。</span><span class="sxs-lookup"><span data-stu-id="2a240-176">This example lists modules that support Updatable Help.</span></span> <span data-ttu-id="2a240-177">此命令會使用模組的 **HelpInfoUri** 屬性，識別支援「可更新的說明」的模組。</span><span class="sxs-lookup"><span data-stu-id="2a240-177">The command uses the module's **HelpInfoUri** property to identify modules that support Updatable Help.</span></span> <span data-ttu-id="2a240-178">**HelpInfoUri** 屬性包含在執行 Cmdlet 時重新導向的位址 `Update-Help` 。</span><span class="sxs-lookup"><span data-stu-id="2a240-178">The **HelpInfoUri** property contains an address that is redirected when the `Update-Help` cmdlet is run.</span></span>

```powershell
Get-Module -ListAvailable | Where-Object -Property HelpInfoUri
```

```output
   Directory: C:\program files\powershell\6\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   6.1.0.0    CimCmdlets                          Core      {Get-CimAssociatedInstance... }
Manifest   1.2.2.0    Microsoft.PowerShell.Archive        Desk      {Compress-Archive... }
Manifest   6.1.0.0    Microsoft.PowerShell.Diagnostics    Core      {Get-WinEvent, New-WinEvent}

    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   2.0.1.0    Appx                                Core,Desk {Add-AppxPackage, ... }
Script     1.0.0.0    AssignedAccess                      Core,Desk {Clear-AssignedAccess, ... }
Manifest   1.0.0.0    BitLocker                           Core,Desk {Unlock-BitLocker, ... }
```

### <span data-ttu-id="2a240-179">範例8：清查已更新的說明檔</span><span class="sxs-lookup"><span data-stu-id="2a240-179">Example 8: Inventory updated help files</span></span>

<span data-ttu-id="2a240-180">在此範例中，腳本會 `Get-UpdateHelpVersion.ps1` 為每個模組和其版本號碼建立可更新說明檔的清查。</span><span class="sxs-lookup"><span data-stu-id="2a240-180">In this example, the script `Get-UpdateHelpVersion.ps1` creates an inventory of the Updatable Help files for each module and their version numbers.</span></span>

<span data-ttu-id="2a240-181">腳本會使用模組的 **HelpInfoUri** 屬性，識別支援「可更新的說明」的模組。</span><span class="sxs-lookup"><span data-stu-id="2a240-181">The script identifies modules that support Updatable Help by using the **HelpInfoUri** property of modules.</span></span> <span data-ttu-id="2a240-182">針對支援「可更新的說明」的模組，腳本會尋找並剖析說明資訊檔 ( \* helpinfo.xml) 以尋找最新的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="2a240-182">For modules that support Updatable Help, the script looks for and parses the help information file (\*helpinfo.xml) to find the latest version number.</span></span>

<span data-ttu-id="2a240-183">腳本會使用 **PSCustomObject** 類別和雜湊表來建立自訂輸出物件。</span><span class="sxs-lookup"><span data-stu-id="2a240-183">The script uses the **PSCustomObject** class and a hash table to create a custom output object.</span></span>

```powershell
# Get-UpdateHelpVersion.ps1
Param(
    [parameter(Mandatory=$False)]
    [String[]]
    $Module
)
$HelpInfoNamespace = @{helpInfo='http://schemas.microsoft.com/powershell/help/2010/05'}

if ($Module) { $Modules = Get-Module $Module -ListAvailable | where {$_.HelpInfoUri} }
else { $Modules = Get-Module -ListAvailable | where {$_.HelpInfoUri} }

foreach ($mModule in $Modules)
{
    $mDir = $mModule.ModuleBase

    if (Test-Path $mdir\*helpinfo.xml)
    {
        $mName=$mModule.Name
        $mNodes = dir $mdir\*helpinfo.xml -ErrorAction SilentlyContinue |
            Select-Xml -Namespace $HelpInfoNamespace -XPath "//helpInfo:UICulture"
        foreach ($mNode in $mNodes)
        {
            $mCulture=$mNode.Node.UICultureName
            $mVer=$mNode.Node.UICultureVersion

            [PSCustomObject]@{"ModuleName"=$mName; "Culture"=$mCulture; "Version"=$mVer}
        }
    }
}
```

```Output
ModuleName                              Culture                                 Version
----------                              -------                                 -------
ActiveDirectory                         en-US                                   3.0.0.0
ADCSAdministration                      en-US                                   3.0.0.0
ADCSDeployment                          en-US                                   3.0.0.0
ADDSDeployment                          en-US                                   3.0.0.0
ADFS                                    en-US                                   3.0.0.0
```

## <span data-ttu-id="2a240-184">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2a240-184">PARAMETERS</span></span>

### <span data-ttu-id="2a240-185">-Credential</span><span class="sxs-lookup"><span data-stu-id="2a240-185">-Credential</span></span>

<span data-ttu-id="2a240-186">指定有權存取 **SourcePath** 所指定之檔案系統位置的使用者認證。</span><span class="sxs-lookup"><span data-stu-id="2a240-186">Specifies credentials of a user who has permission to access the file system location specified by **SourcePath** .</span></span> <span data-ttu-id="2a240-187">只有當命令中使用 **SourcePath** 或 **LiteralPath** 參數時，此參數才有效。</span><span class="sxs-lookup"><span data-stu-id="2a240-187">This parameter is valid only when the **SourcePath** or **LiteralPath** parameter is used in the command.</span></span>

<span data-ttu-id="2a240-188">**Credential** 參數可讓您 `Update-Help` 在遠端電腦上執行具有 **SourcePath** 參數的命令。</span><span class="sxs-lookup"><span data-stu-id="2a240-188">The **Credential** parameter enables you to run `Update-Help` commands with the **SourcePath** parameter on remote computers.</span></span> <span data-ttu-id="2a240-189">藉由提供明確的認證，您可以在遠端電腦上執行命令，並存取第三部電腦上的檔案共用，而不會遇到拒絕存取錯誤，或使用 CredSSP 驗證來委派認證。</span><span class="sxs-lookup"><span data-stu-id="2a240-189">By providing explicit credentials, you can run the command on a remote computer and access a file share on a third computer without encountering an access denied error or using CredSSP authentication to delegate credentials.</span></span>

<span data-ttu-id="2a240-190">輸入使用者名稱（例如 **User01** 或 **Domain01\User01** ），或輸入 Cmdlet 所產生的 **PSCredential** 物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="2a240-190">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="2a240-191">如果您輸入使用者名稱，系統就會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="2a240-191">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="2a240-192">認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="2a240-192">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="2a240-193">如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="2a240-193">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2a240-194">-Force</span><span class="sxs-lookup"><span data-stu-id="2a240-194">-Force</span></span>

<span data-ttu-id="2a240-195">指出此 Cmdlet 不會遵循每天一次的限制、略過版本檢查，以及下載超過 1 GB 限制的檔案。</span><span class="sxs-lookup"><span data-stu-id="2a240-195">Indicates that this cmdlet doesn't follow the once-per-day limitation, skips version checking, and downloads files that exceed the 1 GB limit.</span></span>

<span data-ttu-id="2a240-196">如果沒有這個參數，則 `Update-Help` 每24小時內只會執行一次。</span><span class="sxs-lookup"><span data-stu-id="2a240-196">Without this parameter, `Update-Help` runs only once in each 24-hour period.</span></span> <span data-ttu-id="2a240-197">每個模組的下載限制為 1 GB 的未壓縮內容，而且說明檔只有在比電腦上的現有檔案更新時才會安裝。</span><span class="sxs-lookup"><span data-stu-id="2a240-197">Downloads are limited to 1 GB of uncompressed content per module and help files are only installed when they're newer than the existing files on the computer.</span></span>

<span data-ttu-id="2a240-198">每日一次的限制可保護裝載說明檔的伺服器，並讓您能夠將 `Update-Help` 命令新增至 PowerShell 設定檔，而不會產生重複連線或下載的資源成本。</span><span class="sxs-lookup"><span data-stu-id="2a240-198">The once-per-day limit protects the servers that host the help files and makes it practical for you to add an `Update-Help` command to your PowerShell profile without incurring the resource cost of repeated connections or downloads.</span></span>

<span data-ttu-id="2a240-199">若要不使用 **Force** 參數來更新多重 UI 文化特性中的模組說明，請在同一個命令中包含所有 UI 文化特性，例如：</span><span class="sxs-lookup"><span data-stu-id="2a240-199">To update help for a module in multiple UI cultures without the **Force** parameter, include all UI cultures in the same command, such as:</span></span>

`Update-Help -Module PSScheduledJobs -UICulture en-US, fr-FR, pt-BR`

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

### <span data-ttu-id="2a240-200">-FullyQualifiedModule</span><span class="sxs-lookup"><span data-stu-id="2a240-200">-FullyQualifiedModule</span></span>

<span data-ttu-id="2a240-201">指定以 **ModuleSpecification** 物件形式指定之名稱的模組。</span><span class="sxs-lookup"><span data-stu-id="2a240-201">Specifies modules with names that are specified in the form of **ModuleSpecification** objects.</span></span>
<span data-ttu-id="2a240-202">這些模組會在 [ModuleSpecification (雜湊表) ](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_)的「備註」一節中描述。</span><span class="sxs-lookup"><span data-stu-id="2a240-202">These modules are described in the Remarks section of [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>

<span data-ttu-id="2a240-203">例如， **FullyQualifiedModule** 參數會接受以下列格式指定的模組名稱：</span><span class="sxs-lookup"><span data-stu-id="2a240-203">For example, the **FullyQualifiedModule** parameter accepts a module name that is specified in the format:</span></span>

`@{ModuleName = "modulename"; ModuleVersion = "version_number"}`

<span data-ttu-id="2a240-204">或</span><span class="sxs-lookup"><span data-stu-id="2a240-204">or</span></span>

`@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}.`

<span data-ttu-id="2a240-205">**ModuleName** 和 **ModuleVersion** 是必要參數，但 **Guid** 是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="2a240-205">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span>

<span data-ttu-id="2a240-206">您無法在與 **模組** 參數相同的命令中指定 **FullyQualifiedModule** 參數。</span><span class="sxs-lookup"><span data-stu-id="2a240-206">You can't specify the **FullyQualifiedModule** parameter in the same command as a **Module** parameter.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2a240-207">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="2a240-207">-LiteralPath</span></span>

<span data-ttu-id="2a240-208">指定已更新說明檔的資料夾，而不是從網際網路下載。</span><span class="sxs-lookup"><span data-stu-id="2a240-208">Specifies the folder for updated help files instead of downloading them from the internet.</span></span> <span data-ttu-id="2a240-209">如果您已使用此 Cmdlet 將說明檔下載至目錄，請使用此參數或 **SourcePath** `Save-Help` 。</span><span class="sxs-lookup"><span data-stu-id="2a240-209">Use this parameter or **SourcePath** if you've used the `Save-Help` cmdlet to download help files to a directory.</span></span>

<span data-ttu-id="2a240-210">您可以將目錄物件（例如從 `Get-Item` 或 `Get-ChildItem` Cmdlet）管線至 `Update-Help` 。</span><span class="sxs-lookup"><span data-stu-id="2a240-210">You can pipeline a directory object, such as from the `Get-Item` or `Get-ChildItem` cmdlets, to `Update-Help`.</span></span>

<span data-ttu-id="2a240-211">與 **SourcePath** 的值不同， **LiteralPath** 的值會完全依照其輸入值來使用。</span><span class="sxs-lookup"><span data-stu-id="2a240-211">Unlike the value of **SourcePath** , the value of **LiteralPath** is used exactly as it's typed.</span></span> <span data-ttu-id="2a240-212">沒有字元會被視為萬用字元。</span><span class="sxs-lookup"><span data-stu-id="2a240-212">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="2a240-213">如果路徑包含逸出字元，請將它括在單引號中。</span><span class="sxs-lookup"><span data-stu-id="2a240-213">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="2a240-214">單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="2a240-214">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2a240-215">-Module</span><span class="sxs-lookup"><span data-stu-id="2a240-215">-Module</span></span>

<span data-ttu-id="2a240-216">更新指定模組的說明。</span><span class="sxs-lookup"><span data-stu-id="2a240-216">Updates help for the specified modules.</span></span> <span data-ttu-id="2a240-217">在以逗號分隔的清單中輸入一或多個模組名稱或名稱模式，或指定每一行列出一個模組名稱的檔案。</span><span class="sxs-lookup"><span data-stu-id="2a240-217">Enter one or more module names or name patterns in a comma-separated list, or specify a file that lists one module name on each line.</span></span> <span data-ttu-id="2a240-218">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="2a240-218">Wildcard characters are permitted.</span></span> <span data-ttu-id="2a240-219">您可以從 Cmdlet 將模組管線 `Get-Module` 到 `Update-Help` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2a240-219">You can pipeline modules from the `Get-Module` cmdlet to the `Update-Help` cmdlet.</span></span>

<span data-ttu-id="2a240-220">您所指定的模組必須安裝在電腦上，但不需要將它們匯入到目前的會話。</span><span class="sxs-lookup"><span data-stu-id="2a240-220">The modules that you specify must be installed on the computer, but they don't have to be imported into the current session.</span></span> <span data-ttu-id="2a240-221">您可以指定會話中的任何模組，或安裝在環境變數所列位置中的任何模組 `$env:PSModulePath` 。</span><span class="sxs-lookup"><span data-stu-id="2a240-221">You can specify any module in the session or any module that is installed in a location listed in the `$env:PSModulePath` environment variable.</span></span>

<span data-ttu-id="2a240-222">`*`所有) 的值 (會嘗試更新電腦上所安裝之所有模組的說明。</span><span class="sxs-lookup"><span data-stu-id="2a240-222">A value of `*` (all) attempts to update help for all modules that are installed on the computer.</span></span>
<span data-ttu-id="2a240-223">包含不支援「可更新的說明」的模組。</span><span class="sxs-lookup"><span data-stu-id="2a240-223">Modules that don't support Updatable Help are included.</span></span> <span data-ttu-id="2a240-224">當命令遇到不支援「可更新的說明」的模組時，這個值可能會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="2a240-224">This value might generate errors when the command encounters modules that don't support Updatable Help.</span></span> <span data-ttu-id="2a240-225">請改為執行 `Update-Help` 但不包含參數。</span><span class="sxs-lookup"><span data-stu-id="2a240-225">Instead, run `Update-Help` without parameters.</span></span>

<span data-ttu-id="2a240-226">Cmdlet 的 **module** 參數 `Update-Help` 不接受模組檔案或模組資訊清單檔案的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="2a240-226">The **Module** parameter of the `Update-Help` cmdlet doesn't accept the full path of a module file or module manifest file.</span></span> <span data-ttu-id="2a240-227">若要更新不在某個位置的模組說明 `$env:PSModulePath` ，請在執行命令之前將模組匯入到目前的會話 `Update-Help` 。</span><span class="sxs-lookup"><span data-stu-id="2a240-227">To update help for a module that isn't in a `$env:PSModulePath` location, import the module into the current session before you run the `Update-Help` command.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Name

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="2a240-228">-Recurse</span><span class="sxs-lookup"><span data-stu-id="2a240-228">-Recurse</span></span>

<span data-ttu-id="2a240-229">在指定的目錄中執行說明檔的遞迴搜尋。</span><span class="sxs-lookup"><span data-stu-id="2a240-229">Performs a recursive search for help files in the specified directory.</span></span> <span data-ttu-id="2a240-230">只有當命令使用 **SourcePath** 參數時，此參數才有效。</span><span class="sxs-lookup"><span data-stu-id="2a240-230">This parameter is valid only when the command uses the **SourcePath** parameter.</span></span>

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

### <span data-ttu-id="2a240-231">-SourcePath</span><span class="sxs-lookup"><span data-stu-id="2a240-231">-SourcePath</span></span>

<span data-ttu-id="2a240-232">指定可取得已更新說明檔的檔系統資料夾 `Update-Help` ，而不是從網際網路下載。</span><span class="sxs-lookup"><span data-stu-id="2a240-232">Specifies a file system folder where `Update-Help` gets updated help files, instead of downloading them from the internet.</span></span> <span data-ttu-id="2a240-233">輸入資料夾的路徑。</span><span class="sxs-lookup"><span data-stu-id="2a240-233">Enter the path of a folder.</span></span> <span data-ttu-id="2a240-234">請勿指定檔案名或副檔名。</span><span class="sxs-lookup"><span data-stu-id="2a240-234">Don't specify a file name or file name extension.</span></span> <span data-ttu-id="2a240-235">您可以將資料夾（例如）從 `Get-Item` 或 `Get-ChildItem` Cmdlet 管線至 `Update-Help` 。</span><span class="sxs-lookup"><span data-stu-id="2a240-235">You can pipeline a folder, such as one from the `Get-Item` or `Get-ChildItem` cmdlets, to `Update-Help`.</span></span>

<span data-ttu-id="2a240-236">根據預設，會 `Update-Help` 從網際網路下載已更新的說明檔。</span><span class="sxs-lookup"><span data-stu-id="2a240-236">By default, `Update-Help` downloads updated help files from the internet.</span></span> <span data-ttu-id="2a240-237">當 **SourcePath** 您使用此 `Save-Help` Cmdlet 將已更新的說明檔下載至目錄時，請使用 SourcePath。</span><span class="sxs-lookup"><span data-stu-id="2a240-237">Use **SourcePath** when you've used the `Save-Help` cmdlet to download updated help files to a directory.</span></span>

<span data-ttu-id="2a240-238">若要指定 **SourcePath** 的預設值，請移至 **群組原則** 、 **電腦** 設定，並 **設定 update-help 的預設來源路徑** 。</span><span class="sxs-lookup"><span data-stu-id="2a240-238">To specify a default value for **SourcePath** , go to **Group Policy** , **Computer Configuration** , and **Set the default source path for Update-Help** .</span></span> <span data-ttu-id="2a240-239">此群組原則設定可防止使用者使用 `Update-Help` 從網際網路下載說明檔。</span><span class="sxs-lookup"><span data-stu-id="2a240-239">This Group Policy setting prevents users from using `Update-Help` to download help files from the internet.</span></span>
<span data-ttu-id="2a240-240">如需詳細資訊，請參閱 [about_Group_Policy_Settings](./About/about_Group_Policy_Settings.md)。</span><span class="sxs-lookup"><span data-stu-id="2a240-240">For more information, see [about_Group_Policy_Settings](./About/about_Group_Policy_Settings.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2a240-241">-UICulture</span><span class="sxs-lookup"><span data-stu-id="2a240-241">-UICulture</span></span>

<span data-ttu-id="2a240-242">指定 `Update-Help` 用來取得已更新說明檔的 UI 文化特性值。</span><span class="sxs-lookup"><span data-stu-id="2a240-242">Specifies UI culture values that `Update-Help` uses to get updated help files.</span></span> <span data-ttu-id="2a240-243">輸入一或多個語言代碼（例如 **es** ）、包含文化特性物件的變數，或可取得文化特性物件的命令，例如 `Get-Culture` 或 `Get-UICulture` 命令。</span><span class="sxs-lookup"><span data-stu-id="2a240-243">Enter one or more language codes, such as **es-ES** , a variable that contains culture objects, or a command that gets culture objects, such as a `Get-Culture` or `Get-UICulture` command.</span></span> <span data-ttu-id="2a240-244">不允許使用萬用字元，且您無法提交部分語言代碼，例如 **de** 。</span><span class="sxs-lookup"><span data-stu-id="2a240-244">Wildcard characters aren't permitted and you can't submit a partial language code, such as **de** .</span></span>

<span data-ttu-id="2a240-245">根據預設，會 `Update-Help` 取得為作業系統設定的 UI 文化特性中的說明檔。</span><span class="sxs-lookup"><span data-stu-id="2a240-245">By default, `Update-Help` gets help files in the UI culture set for the operating system.</span></span> <span data-ttu-id="2a240-246">如果您指定 **UICulture** 參數，只會尋找 `Update-Help` 所指定 UI 文化特性的說明。</span><span class="sxs-lookup"><span data-stu-id="2a240-246">If you specify the **UICulture** parameter, `Update-Help` looks for help only for the specified UI culture.</span></span>

<span data-ttu-id="2a240-247">只有當模組有提供所指定 UI 文化特性的說明檔時，使用 **UICulture** 參數的命令才會成功。</span><span class="sxs-lookup"><span data-stu-id="2a240-247">Commands that use the **UICulture** parameter succeed only when the module provides help files for the specified UI culture.</span></span> <span data-ttu-id="2a240-248">如果命令因為不支援指定的 UI 文化特性而失敗，則會顯示錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="2a240-248">If the command fails because the specified UI culture isn't supported, an error message is displayed.</span></span>

```yaml
Type: System.Globalization.CultureInfo[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2a240-249">-UseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="2a240-249">-UseDefaultCredentials</span></span>

<span data-ttu-id="2a240-250">表示 `Update-Help` 使用目前使用者的認證執行命令，包括網際網路下載。</span><span class="sxs-lookup"><span data-stu-id="2a240-250">Indicates that `Update-Help` runs the command, including the internet download, by using the credentials of the current user.</span></span> <span data-ttu-id="2a240-251">根據預設，該命令執行時不會使用明確宣告的認證。</span><span class="sxs-lookup"><span data-stu-id="2a240-251">By default, the command runs without explicit credentials.</span></span>

<span data-ttu-id="2a240-252">只有當 web 下載使用 NT LAN Manager (NTLM) 、negotiate 或 Kerberos 驗證時，此參數才有效。</span><span class="sxs-lookup"><span data-stu-id="2a240-252">This parameter is effective only when the web download uses NT LAN Manager (NTLM), negotiate, or Kerberos-based authentication.</span></span>

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

### <span data-ttu-id="2a240-253">-Confirm</span><span class="sxs-lookup"><span data-stu-id="2a240-253">-Confirm</span></span>

<span data-ttu-id="2a240-254">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="2a240-254">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="2a240-255">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="2a240-255">-WhatIf</span></span>

<span data-ttu-id="2a240-256">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="2a240-256">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="2a240-257">不會執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2a240-257">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="2a240-258">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2a240-258">CommonParameters</span></span>

<span data-ttu-id="2a240-259">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="2a240-259">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2a240-260">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="2a240-260">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2a240-261">輸入</span><span class="sxs-lookup"><span data-stu-id="2a240-261">INPUTS</span></span>

### <span data-ttu-id="2a240-262">DirectoryInfo</span><span class="sxs-lookup"><span data-stu-id="2a240-262">System.IO.DirectoryInfo</span></span>

<span data-ttu-id="2a240-263">您可以使用管線將目錄路徑傳送至 `Update-Help` 。</span><span class="sxs-lookup"><span data-stu-id="2a240-263">You can pipe a directory path to `Update-Help`.</span></span>

### <span data-ttu-id="2a240-264">System.Management.Automation.PSModuleInfo</span><span class="sxs-lookup"><span data-stu-id="2a240-264">System.Management.Automation.PSModuleInfo</span></span>

<span data-ttu-id="2a240-265">您可以使用管線將模組物件從 `Get-Module` Cmdlet 傳送至 `Update-Help` 。</span><span class="sxs-lookup"><span data-stu-id="2a240-265">You can pipe a module object from the `Get-Module` cmdlet to `Update-Help`.</span></span>

## <span data-ttu-id="2a240-266">輸出</span><span class="sxs-lookup"><span data-stu-id="2a240-266">OUTPUTS</span></span>

### <span data-ttu-id="2a240-267">無</span><span class="sxs-lookup"><span data-stu-id="2a240-267">None</span></span>

<span data-ttu-id="2a240-268">`Update-Help` 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="2a240-268">`Update-Help` doesn't generate any output.</span></span>

## <span data-ttu-id="2a240-269">注意</span><span class="sxs-lookup"><span data-stu-id="2a240-269">NOTES</span></span>

<span data-ttu-id="2a240-270">若要更新 PowerShell Core 模組的說明，其中包含與 PowerShell 一起安裝的命令，或目錄中的任何模組 `$PSHOME\Modules` ，請啟動 PowerShell 並使用 [以 **系統管理員身分執行** ] 選項。</span><span class="sxs-lookup"><span data-stu-id="2a240-270">To update help for the PowerShell Core modules, that contain the commands that are installed with PowerShell, or any module in the `$PSHOME\Modules` directory, start PowerShell with the option to **Run as administrator** .</span></span>

<span data-ttu-id="2a240-271">只有電腦上 Administrators 群組的成員可以更新 PowerShell Core 模組的說明、隨 PowerShell 一起安裝的命令，以及資料夾中的模組 `$PSHOME\Modules` 。</span><span class="sxs-lookup"><span data-stu-id="2a240-271">Only members of the Administrators group on the computer can update help for the PowerShell Core modules, the commands that are installed together with PowerShell, and for modules in the `$PSHOME\Modules` folder.</span></span> <span data-ttu-id="2a240-272">如果您沒有更新說明檔的許可權，您可以在線上閱讀說明檔。</span><span class="sxs-lookup"><span data-stu-id="2a240-272">If you don't have permission to update help files, you can read the help files online.</span></span> <span data-ttu-id="2a240-273">例如： `Get-Help Update-Help -Online` 。</span><span class="sxs-lookup"><span data-stu-id="2a240-273">For example, `Get-Help Update-Help -Online`.</span></span>

<span data-ttu-id="2a240-274">模組是可更新的說明之最小單位。</span><span class="sxs-lookup"><span data-stu-id="2a240-274">Modules are the smallest unit of updatable help.</span></span> <span data-ttu-id="2a240-275">您無法更新特定 Cmdlet 的說明。</span><span class="sxs-lookup"><span data-stu-id="2a240-275">You can't update help for a particular cmdlet.</span></span> <span data-ttu-id="2a240-276">若要尋找包含特定 Cmdlet 的模組，請使用 Cmdlet 的 **ModuleName** 屬性 `Get-Command` ，例如 `(Get-Command Update-Help).ModuleName` 。</span><span class="sxs-lookup"><span data-stu-id="2a240-276">To find the module that contains a particular cmdlet, use the **ModuleName** property of the `Get-Command` cmdlet, for example, `(Get-Command Update-Help).ModuleName`.</span></span>

<span data-ttu-id="2a240-277">因為說明檔安裝在模組目錄中，此 `Update-Help` Cmdlet 只能針對安裝在電腦上的模組安裝已更新的說明檔。</span><span class="sxs-lookup"><span data-stu-id="2a240-277">Because help files are installed in the module directory, the `Update-Help` cmdlet can install updated help file only for modules that are installed on the computer.</span></span> <span data-ttu-id="2a240-278">不過，此 `Save-Help` Cmdlet 可以儲存未安裝在電腦上之模組的說明。</span><span class="sxs-lookup"><span data-stu-id="2a240-278">However, the `Save-Help` cmdlet can save help for modules that aren't installed on the computer.</span></span>

<span data-ttu-id="2a240-279">如果找 `Update-Help` 不到模組的已更新說明檔，或找不到指定語言的已更新說明檔，它會繼續以無訊息模式繼續，而不會顯示錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="2a240-279">If `Update-Help` can't find updated help files for a module, or can't find updated help in the specified language, it continues silently without displaying an error message.</span></span> <span data-ttu-id="2a240-280">若要查看狀態和進度的詳細資訊，請使用 **Verbose** 參數。</span><span class="sxs-lookup"><span data-stu-id="2a240-280">To see status and progress details, use the **Verbose** parameter.</span></span>

<span data-ttu-id="2a240-281">`Update-Help`Cmdlet 是在 Windows PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="2a240-281">The `Update-Help` cmdlet was introduced in Windows PowerShell 3.0.</span></span> <span data-ttu-id="2a240-282">不適用於舊版 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="2a240-282">It doesn't work in earlier versions of PowerShell.</span></span> <span data-ttu-id="2a240-283">在同時具有 Windows PowerShell 2.0 和 Windows PowerShell 3.0 的電腦上，請使用 `Update-Help` Windows PowerShell 3.0 會話中的 Cmdlet 來下載和更新說明檔。</span><span class="sxs-lookup"><span data-stu-id="2a240-283">On computers that have both Windows PowerShell 2.0 and Windows PowerShell 3.0, use the `Update-Help` cmdlet in a Windows PowerShell 3.0 session to download and update help files.</span></span> <span data-ttu-id="2a240-284">Windows PowerShell 2.0 和 Windows PowerShell 3.0 都提供說明檔。</span><span class="sxs-lookup"><span data-stu-id="2a240-284">The help files are available to both Windows PowerShell 2.0 and Windows PowerShell 3.0.</span></span>

<span data-ttu-id="2a240-285">`Update-Help`和 `Save-Help` Cmdlet 使用下列埠下載說明檔：適用于 HTTP 的埠80和 HTTPS 的埠443。</span><span class="sxs-lookup"><span data-stu-id="2a240-285">The `Update-Help` and `Save-Help` cmdlets use the following ports to download help files: Port 80 for HTTP and port 443 for HTTPS.</span></span>

<span data-ttu-id="2a240-286">`Update-Help` 支援所有模組和 PowerShell Core 嵌入式管理單元。它不支援任何其他嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="2a240-286">`Update-Help` supports all modules and the PowerShell Core snap-ins. It doesn't support any other snap-ins.</span></span>

<span data-ttu-id="2a240-287">若要更新未列在環境變數中之位置的模組說明 `$env:PSModulePath` ，請將模組匯入目前的會話，然後執行 `Update-Help` 命令。</span><span class="sxs-lookup"><span data-stu-id="2a240-287">To update help for a module in a location that isn't listed in the `$env:PSModulePath` environment variable, import the module into the current session and then run an `Update-Help` command.</span></span> <span data-ttu-id="2a240-288">`Update-Help`在不使用參數的情況下執行，或使用 **module** 參數指定模組名稱。</span><span class="sxs-lookup"><span data-stu-id="2a240-288">Run `Update-Help` without parameters or use the **Module** parameter to specify the module name.</span></span> <span data-ttu-id="2a240-289">和 Cmdlet 的 **module** 參數 `Update-Help` `Save-Help` 不接受模組檔案或模組資訊清單檔案的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="2a240-289">The **Module** parameter of the `Update-Help` and `Save-Help` cmdlets doesn't accept the full path of a module file or module manifest file.</span></span>

<span data-ttu-id="2a240-290">任何模組都能支援「可更新的說明」。</span><span class="sxs-lookup"><span data-stu-id="2a240-290">Any module can support Updatable Help.</span></span> <span data-ttu-id="2a240-291">如需在您撰寫的模組中支援「可更新的說明」的指示，請參閱 [支援可更新](/powershell/scripting/developer/module/supporting-updatable-help)的說明。</span><span class="sxs-lookup"><span data-stu-id="2a240-291">For instructions for supporting Updatable Help in the modules that you author, see [Supporting Updatable Help](/powershell/scripting/developer/module/supporting-updatable-help).</span></span>

<span data-ttu-id="2a240-292">`Update-Help` `Save-Help` Windows 預先安裝環境 (Windows PE) 不支援和 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2a240-292">The `Update-Help` and `Save-Help` cmdlets are not supported on Windows Preinstallation Environment (Windows PE).</span></span>

## <span data-ttu-id="2a240-293">相關連結</span><span class="sxs-lookup"><span data-stu-id="2a240-293">RELATED LINKS</span></span>

[<span data-ttu-id="2a240-294">Get-Culture</span><span class="sxs-lookup"><span data-stu-id="2a240-294">Get-Culture</span></span>](../Microsoft.PowerShell.Utility/Get-Culture.md)

[<span data-ttu-id="2a240-295">Get-Help</span><span class="sxs-lookup"><span data-stu-id="2a240-295">Get-Help</span></span>](Get-Help.md)

[<span data-ttu-id="2a240-296">Get-Module</span><span class="sxs-lookup"><span data-stu-id="2a240-296">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="2a240-297">Get-UICulture</span><span class="sxs-lookup"><span data-stu-id="2a240-297">Get-UICulture</span></span>](../Microsoft.PowerShell.Utility/Get-UICulture.md)

[<span data-ttu-id="2a240-298">Start-Job</span><span class="sxs-lookup"><span data-stu-id="2a240-298">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="2a240-299">Save-Help</span><span class="sxs-lookup"><span data-stu-id="2a240-299">Save-Help</span></span>](Save-Help.md)
