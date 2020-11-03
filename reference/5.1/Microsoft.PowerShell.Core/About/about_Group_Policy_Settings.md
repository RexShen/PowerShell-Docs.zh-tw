---
description: 描述 Windows PowerShell 的群組原則設定
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_group_policy_settings?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Group_Policy_Settings
ms.openlocfilehash: e55db2000f63170d7aef82a7b7223c6998b24602
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208019"
---
# <a name="about-group-policy-settings"></a><span data-ttu-id="e3c5b-104">關於群組原則設定</span><span class="sxs-lookup"><span data-stu-id="e3c5b-104">About Group Policy Settings</span></span>

## <a name="short-description"></a><span data-ttu-id="e3c5b-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="e3c5b-105">Short description</span></span>
<span data-ttu-id="e3c5b-106">描述 Windows PowerShell 的群組原則設定</span><span class="sxs-lookup"><span data-stu-id="e3c5b-106">Describes the Group Policy settings for Windows PowerShell</span></span>

## <a name="long-description"></a><span data-ttu-id="e3c5b-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="e3c5b-107">Long description</span></span>

<span data-ttu-id="e3c5b-108">Windows PowerShell 包含群組原則設定，可協助您在企業環境中為 Windows 電腦定義一致的設定值。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-108">Windows PowerShell includes Group Policy settings to help you define consistent configuration values for Windows computers in an enterprise environment.</span></span>

<span data-ttu-id="e3c5b-109">PowerShell 群組原則設定位於下列群組原則路徑：</span><span class="sxs-lookup"><span data-stu-id="e3c5b-109">The PowerShell Group Policy settings are in the following Group Policy paths:</span></span>

```
Computer Configuration\
  Administrative Templates\
    Windows Components\
      Windows PowerShell

User Configuration\
  Administrative Templates\
    Windows Components\
      Windows PowerShell
```

<span data-ttu-id="e3c5b-110">使用者設定路徑中的群組原則設定優先于電腦設定路徑中群組原則的設定。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-110">Group policy settings in the User Configuration path take precedence over Group Policy settings in the Computer Configuration path.</span></span>

<span data-ttu-id="e3c5b-111">原則如下所示：</span><span class="sxs-lookup"><span data-stu-id="e3c5b-111">The policies are as follows:</span></span>

- <span data-ttu-id="e3c5b-112">開啟模組記錄：設定模組的 **LogPipelineExecutionDetails** 屬性。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-112">Turn on Module Logging: Sets the **LogPipelineExecutionDetails** property of modules.</span></span>
- <span data-ttu-id="e3c5b-113">開啟 PowerShell 指令碼區塊記錄：啟用所有 PowerShell 指令碼的詳細記錄。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-113">Turn on PowerShell Script Block Logging: Enables detailed logging of all PowerShell scripts.</span></span>
- <span data-ttu-id="e3c5b-114">開啟指令碼執行：設定 PowerShell 執行原則。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-114">Turn on Script Execution: Sets the PowerShell execution policy.</span></span>
- <span data-ttu-id="e3c5b-115">開啟 PowerShell 轉譯：將 PowerShell 命令的輸入和輸出，擷取到以文字為基礎的文字記錄。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-115">Turn on PowerShell Transcription: enables capturing of input and output of PowerShell commands into text-based transcripts.</span></span>
- <span data-ttu-id="e3c5b-116">設定的預設來源路徑 `Update-Help` ：將可更新的說明的來源設定為目錄，而不是網際網路。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-116">Set the default source path for `Update-Help`: Sets the source for Updatable Help to a directory, not the Internet.</span></span>

<span data-ttu-id="e3c5b-117">如需取得其他範本及設定群組原則的詳細資訊，請參閱 [如何在 Windows 中建立和管理群組原則系統管理範本的集中存放區][gpstore]。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-117">For more information about acquiring other templates and configuring Group policy, see [How to create and manage the Central Store for Group Policy Administrative Templates in Windows][gpstore].</span></span>

## <a name="turn-on-module-logging"></a><span data-ttu-id="e3c5b-118">開啟模組記錄</span><span class="sxs-lookup"><span data-stu-id="e3c5b-118">Turn on module logging</span></span>

<span data-ttu-id="e3c5b-119">[ **開啟模組記錄** ] 原則設定會開啟所選 PowerShell 模組的記錄功能。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-119">The **Turn on Module Logging** policy setting turns on logging for selected PowerShell modules.</span></span> <span data-ttu-id="e3c5b-120">設定在所有受影響電腦上的所有會話中都有效。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-120">The setting is effective in all sessions on all affected computers.</span></span>

<span data-ttu-id="e3c5b-121">如果您啟用此原則設定並指定一或多個模組，則會在事件檢視器的 Windows PowerShell 記錄檔中記錄指定模組的管線執行事件。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-121">If you enable this policy setting and specify one or more modules, pipeline execution events for the specified modules are recorded in the Windows PowerShell log in Event Viewer.</span></span>

<span data-ttu-id="e3c5b-122">如果您停用此原則設定，則會停用所有 PowerShell 模組的執行事件記錄。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-122">If you disable this policy setting, logging of execution events is disabled for all PowerShell modules.</span></span>

<span data-ttu-id="e3c5b-123">如果未設定此原則設定，則每個模組的 **LogPipelineExecutionDetails** 屬性會決定是否要記錄模組的執行事件。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-123">If this policy setting is not configured, the **LogPipelineExecutionDetails** property of each module determines whether the execution events of a module are logged.</span></span> <span data-ttu-id="e3c5b-124">依預設，所有模組的 **LogPipelineExecutionDetails** 屬性都設定為 False。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-124">By default, the **LogPipelineExecutionDetails** property of all modules is set to False.</span></span>

<span data-ttu-id="e3c5b-125">若要開啟模組的模組記錄，請使用下列命令格式。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-125">To turn on module logging for a module, use the following command format.</span></span> <span data-ttu-id="e3c5b-126">模組必須匯入會話中，而且此設定只會在目前的會話中生效。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-126">The module must be imported into the session and the setting is effective only in the current session.</span></span>

```powershell
Import-Module <Module-Name>
(Get-Module <Module-Name>).LogPipelineExecutionDetails = $true
```

<span data-ttu-id="e3c5b-127">若要為特定電腦上的所有會話開啟模組記錄，請將上述命令新增至 [所有使用者的 PowerShell 設定檔] (`$Profile.AllUsersAllHosts`) 。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-127">To turn on module logging for all sessions on a particular computer, add the previous commands to the 'All Users' PowerShell profile (`$Profile.AllUsersAllHosts`).</span></span>

<span data-ttu-id="e3c5b-128">如需模組記錄的詳細資訊，請參閱 [about_Modules](about_Modules.md)。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-128">For more information about module logging, see [about_Modules](about_Modules.md).</span></span>

## <a name="turn-on-powershell-script-block-logging"></a><span data-ttu-id="e3c5b-129">開啟 PowerShell 腳本區塊記錄</span><span class="sxs-lookup"><span data-stu-id="e3c5b-129">Turn on PowerShell script block logging</span></span>

<span data-ttu-id="e3c5b-130">**開啟 Powershell 腳本區塊記錄** 原則設定可讓您將所有 PowerShell 腳本輸入記錄到 Microsoft Windows Powershell/操作事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-130">The **Turn on PowerShell Script Block Logging** policy setting enables logging of all PowerShell script input to the Microsoft-Windows-PowerShell/Operational event log.</span></span> <span data-ttu-id="e3c5b-131">如果您啟用此原則設定，PowerShell Core 將會記錄命令、腳本區塊、函式和腳本的處理（無論是以互動方式叫用，還是透過 automation）。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-131">If you enable this policy setting, PowerShell Core will log the processing of commands, script blocks, functions, and scripts - whether invoked interactively, or through automation.</span></span>

<span data-ttu-id="e3c5b-132">如果您停用此原則設定，則會停用 PowerShell 指令碼輸入的記錄功能。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-132">If you disable this policy setting, logging of PowerShell script input is disabled.</span></span> <span data-ttu-id="e3c5b-133">如果您啟用指令碼區塊引動過程記錄，PowerShell 會額外記錄命令、指令碼區塊、函式或指令碼啟動或停止時的事件。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-133">If you enable the Script Block Invocation Logging, PowerShell additionally logs events when invocation of a command, script block, function, or script starts or stops.</span></span> <span data-ttu-id="e3c5b-134">啟用引動過程記錄會產生大量的事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-134">Enabling Invocation Logging generates a high volume of event logs.</span></span>

## <a name="turn-on-script-execution"></a><span data-ttu-id="e3c5b-135">開啟腳本執行</span><span class="sxs-lookup"><span data-stu-id="e3c5b-135">Turn on script execution</span></span>

<span data-ttu-id="e3c5b-136">[ **開啟腳本執行** ] 原則設定會設定電腦和使用者的執行原則，以決定允許執行的腳本。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-136">The **Turn on Script Execution** policy setting sets the execution policy for computers and users, which determines which scripts are permitted to run.</span></span>

<span data-ttu-id="e3c5b-137">如果您啟用此原則設定，您可以從下列原則設定中進行選取。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-137">If you enable the policy setting, you can select from among the following policy settings.</span></span>

- <span data-ttu-id="e3c5b-138">只有 **已簽署的腳本** 才能讓腳本只有在由受信任的發行者簽署時才能執行。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-138">**Allow only signed scripts** allows scripts to execute only if they are signed by a trusted publisher.</span></span> <span data-ttu-id="e3c5b-139">此原則設定相當於 AllSigned 執行原則。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-139">This policy setting is equivalent to the AllSigned execution policy.</span></span>

- <span data-ttu-id="e3c5b-140">**允許本機腳本和遠端簽署的腳本** 允許執行所有本機腳本。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-140">**Allow local scripts and remote signed scripts** allows all local scripts to run.</span></span> <span data-ttu-id="e3c5b-141">源自網際網路的腳本必須由信任的發行者簽署。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-141">Scripts that originate from the Internet must be signed by a trusted publisher.</span></span> <span data-ttu-id="e3c5b-142">此原則設定相當於 RemoteSigned 執行原則。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-142">This policy setting is equivalent to the RemoteSigned execution policy.</span></span>

- <span data-ttu-id="e3c5b-143">**允許** 所有腳本都可執行所有腳本。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-143">**Allow all scripts** allows all scripts to run.</span></span> <span data-ttu-id="e3c5b-144">此原則設定相當於不受限制的執行原則。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-144">This policy setting is equivalent to the Unrestricted execution policy.</span></span>

<span data-ttu-id="e3c5b-145">如果您停用此原則設定，則不允許執行任何腳本。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-145">If you disable this policy setting, no scripts are allowed to run.</span></span> <span data-ttu-id="e3c5b-146">此原則設定等同于限制的執行原則。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-146">This policy setting is equivalent to the Restricted execution policy.</span></span>

<span data-ttu-id="e3c5b-147">如果您停用或未設定此原則設定，則 Cmdlet 為電腦或使用者設定的執行原則會 `Set-ExecutionPolicy` 決定是否允許執行腳本。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-147">If you disable or do not configure this policy setting, the execution policy that is set for the computer or user by the `Set-ExecutionPolicy` cmdlet determines whether scripts are permitted to run.</span></span> <span data-ttu-id="e3c5b-148">預設值為 [受限制]。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-148">The default value is Restricted.</span></span>

<span data-ttu-id="e3c5b-149">如需詳細資訊，請參閱 [about_Execution_Policies](about_Execution_Policies.md)。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-149">For more information, see [about_Execution_Policies](about_Execution_Policies.md).</span></span>

## <a name="turn-on-powershell-transcription"></a><span data-ttu-id="e3c5b-150">開啟 powershell 轉譯</span><span class="sxs-lookup"><span data-stu-id="e3c5b-150">Turn on powershell transcription</span></span>

<span data-ttu-id="e3c5b-151">[ **開啟 PowerShell** 轉譯原則] 設定可讓您將 PowerShell Core 命令的輸入和輸出，捕捉到文字型文字記錄中。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-151">The **Turn on PowerShell Transcription** policy setting lets you capture the input and output of PowerShell Core commands into text-based transcripts.</span></span> <span data-ttu-id="e3c5b-152">如果您啟用此原則設定，PowerShell Core 將會啟用 PowerShell Core 的轉譯記錄，以及利用 PowerShell Core 引擎的任何其他應用程式。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-152">If you enable this policy setting, PowerShell Core will enable transcription logging for PowerShell Core and any other applications that leverage the PowerShell Core engine.</span></span> <span data-ttu-id="e3c5b-153">根據預設，PowerShell Core 會將文字記錄輸出記錄到每個使用者的我的檔目錄中，檔案名會包含 ' PowerShell_transcript '，以及電腦名稱稱和開始時間。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-153">By default, PowerShell Core will record transcript output to each users' My Documents directory, with a file name that includes 'PowerShell_transcript', along with the computer name and time started.</span></span>
<span data-ttu-id="e3c5b-154">啟用此原則相當於在每個 PowerShell Core 會話上呼叫 Start-Transcript Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-154">Enabling this policy is equivalent to calling the Start-Transcript cmdlet on each PowerShell Core session.</span></span>

<span data-ttu-id="e3c5b-155">如果您停用此原則設定，則預設會停用以 PowerShell 為基礎之應用程式的轉譯記錄，不過仍然可以透過 Start-Transcript Cmdlet 啟用轉譯。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-155">If you disable this policy setting, transcription logging of PowerShell-based applications is disabled by default, although transcripting can still be enabled through the Start-Transcript cmdlet.</span></span>

<span data-ttu-id="e3c5b-156">如果您使用 OutputDirectory 設定來啟用將記錄記錄到共用位置，請務必限制對該目錄的存取，以防止使用者查看其他使用者或電腦的文字記錄。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-156">If you use the OutputDirectory setting to enable transcription logging to a shared location, be sure to limit access to that directory to prevent users from viewing the transcripts of other users or computers.</span></span>

## <a name="set-the-default-source-path-for-update-help"></a><span data-ttu-id="e3c5b-157">設定 Update-Help 的預設來源路徑</span><span class="sxs-lookup"><span data-stu-id="e3c5b-157">Set the default source path for Update-Help</span></span>

<span data-ttu-id="e3c5b-158">[ **設定 update-help 的預設來源路徑** ] 原則設定會設定 Cmdlet 之 **SourcePath** 參數的預設值 `Update-Help` 。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-158">The **Set the Default Source Path for Update-Help** policy setting sets a default value for the **SourcePath** parameter of the `Update-Help` cmdlet.</span></span>
<span data-ttu-id="e3c5b-159">此設定可防止使用者使用此 `Update-Help` Cmdlet 從網際網路下載說明檔。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-159">This setting prevents users from using the `Update-Help` cmdlet to download help files from the Internet.</span></span>

> [!NOTE]
> <span data-ttu-id="e3c5b-160">此群組原則設定會出現在 [ **電腦** 設定和 **使用者** 設定] 之下。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-160">This Group Policy setting appears under **Computer Configuration** and **User Configuration** .</span></span> <span data-ttu-id="e3c5b-161">不過，只有 [ **電腦** 設定] 下的群組原則設定才會生效。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-161">However, only the Group Policy setting under **Computer Configuration** is effective.</span></span> <span data-ttu-id="e3c5b-162">[ **使用者** 設定] 下的群組原則設定會被忽略。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-162">The Group Policy setting under **User Configuration** is ignored.</span></span>

<span data-ttu-id="e3c5b-163">指令 `Update-Help` 程式會下載並安裝適用于 PowerShell 模組的最新說明檔案，並將它們安裝在電腦上。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-163">The `Update-Help` cmdlet downloads and installs the newest help files for PowerShell modules and installs them on the computer.</span></span> <span data-ttu-id="e3c5b-164">根據預設，會 `Update-Help` 從模組所指定的網際網路位置下載新的說明檔。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-164">By default, `Update-Help` downloads new help files from an Internet location specified by the module.</span></span>

<span data-ttu-id="e3c5b-165">不過，您可以使用 `Save-Help` Cmdlet 將最新的說明檔下載到檔案系統位置（例如網路共用），然後使用指令程式 `Update-Help` 從檔案系統位置取得說明檔，並將它們安裝在電腦上。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-165">However, you can use the `Save-Help` cmdlet to download the newest help files to a file system location, such as a network share, and then use the `Update-Help` cmdlet to get the help files from the file system location and install them on the computer.</span></span> <span data-ttu-id="e3c5b-166">Cmdlet 的 **SourcePath** 參數會 `Update-Help` 指定檔案系統位置。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-166">The **SourcePath** parameter of the `Update-Help` cmdlet specifies the file system location.</span></span>

<span data-ttu-id="e3c5b-167">藉由提供 **sourcepath** 參數的預設值，此群組原則設定會以隱含方式將 **sourcepath** 參數新增至所有 `Update-Help` 命令。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-167">By providing a default value for the **SourcePath** parameter, this Group Policy setting implicitly adds the **SourcePath** parameter to all `Update-Help` commands.</span></span> <span data-ttu-id="e3c5b-168">使用者可以藉由輸入不同的檔案系統位置，覆寫指定為預設值的特定檔案系統位置。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-168">Users can override the particular file system location specified as the default value by entering a different file system location.</span></span>
<span data-ttu-id="e3c5b-169">但它們無法從命令移除 **SourcePath** 參數 `Update-Help` 。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-169">But they cannot remove the **SourcePath** parameter from the `Update-Help` command.</span></span>

<span data-ttu-id="e3c5b-170">如果您啟用此原則設定，您可以指定 **SourcePath** 參數的預設值。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-170">If you enable this policy setting, you can specify a default value for the **SourcePath** parameter.</span></span> <span data-ttu-id="e3c5b-171">輸入檔案系統位置。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-171">Enter a file system location.</span></span>

<span data-ttu-id="e3c5b-172">如果此原則設定已停用或未設定，則 Cmdlet 的 **SourcePath** 參數沒有預設值 `Update-Help` 。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-172">If this policy setting is disabled or not configured, there is no default value for the **SourcePath** parameter of the `Update-Help` cmdlet.</span></span> <span data-ttu-id="e3c5b-173">使用者可以從網際網路或任何檔案系統位置下載說明。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-173">Users can download help from the Internet or from any file system location.</span></span>

<span data-ttu-id="e3c5b-174">如需詳細資訊，請參閱 [about_Updatable_Help](about_Updatable_Help.md)。</span><span class="sxs-lookup"><span data-stu-id="e3c5b-174">For more information, see [about_Updatable_Help](about_Updatable_Help.md).</span></span>

## <a name="keywords"></a><span data-ttu-id="e3c5b-175">關鍵字</span><span class="sxs-lookup"><span data-stu-id="e3c5b-175">Keywords</span></span>

<span data-ttu-id="e3c5b-176">about_Group_Policies about_GroupPolicy</span><span class="sxs-lookup"><span data-stu-id="e3c5b-176">about_Group_Policies about_GroupPolicy</span></span>

## <a name="see-also"></a><span data-ttu-id="e3c5b-177">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3c5b-177">See also</span></span>

[<span data-ttu-id="e3c5b-178">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="e3c5b-178">about_Execution_Policies</span></span>](about_Execution_Policies.md)

[<span data-ttu-id="e3c5b-179">about_Modules</span><span class="sxs-lookup"><span data-stu-id="e3c5b-179">about_Modules</span></span>](about_Modules.md)

[<span data-ttu-id="e3c5b-180">about_Updatable_Help</span><span class="sxs-lookup"><span data-stu-id="e3c5b-180">about_Updatable_Help</span></span>](about_Updatable_Help.md)

[<span data-ttu-id="e3c5b-181">Get-executionpolicy</span><span class="sxs-lookup"><span data-stu-id="e3c5b-181">Get-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Get-ExecutionPolicy)

[<span data-ttu-id="e3c5b-182">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="e3c5b-182">Set-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)

[<span data-ttu-id="e3c5b-183">Get-Module</span><span class="sxs-lookup"><span data-stu-id="e3c5b-183">Get-Module</span></span>](xref:Microsoft.PowerShell.Core.Get-Module)

[<span data-ttu-id="e3c5b-184">Update-Help</span><span class="sxs-lookup"><span data-stu-id="e3c5b-184">Update-Help</span></span>](xref:Microsoft.PowerShell.Core.Update-Help)

[<span data-ttu-id="e3c5b-185">Save-Help</span><span class="sxs-lookup"><span data-stu-id="e3c5b-185">Save-Help</span></span>](xref:Microsoft.PowerShell.Core.Save-Help)

<!-- link references -->
[gpstore]: https://support.microsoft.com/help/3087759
