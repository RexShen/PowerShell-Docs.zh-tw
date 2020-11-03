---
description: 說明如何使用 `powershell.exe` 命令列介面。 顯示命令列參數並描述語法。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/05/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_powershell_exe?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PowerShell_exe
ms.openlocfilehash: ef03558a6b58868b98c9da488934b0bfbbce9fe7
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207952"
---
# <a name="about-powershellexe"></a><span data-ttu-id="e6f06-105">關於 PowerShell.exe</span><span class="sxs-lookup"><span data-stu-id="e6f06-105">About PowerShell.exe</span></span>

## <a name="short-description"></a><span data-ttu-id="e6f06-106">簡短描述</span><span class="sxs-lookup"><span data-stu-id="e6f06-106">Short Description</span></span>
<span data-ttu-id="e6f06-107">說明如何使用 `powershell.exe` 命令列介面。</span><span class="sxs-lookup"><span data-stu-id="e6f06-107">Explains how to use the `powershell.exe` command-line interface.</span></span> <span data-ttu-id="e6f06-108">顯示命令列參數並描述語法。</span><span class="sxs-lookup"><span data-stu-id="e6f06-108">Displays the command-line parameters and describes the syntax.</span></span>

## <a name="long-description"></a><span data-ttu-id="e6f06-109">完整描述</span><span class="sxs-lookup"><span data-stu-id="e6f06-109">Long Description</span></span>

### <a name="syntax"></a><span data-ttu-id="e6f06-110">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e6f06-110">SYNTAX</span></span>

```
PowerShell[.exe]
    [-PSConsoleFile <file> | -Version <version>]
    [-NoLogo]
    [-NoExit]
    [-Sta]
    [-Mta]
    [-NoProfile]
    [-NonInteractive]
    [-InputFormat {Text | XML}]
    [-OutputFormat {Text | XML}]
    [-WindowStyle <style>]
    [-EncodedCommand <Base64EncodedCommand>]
    [-ConfigurationName <string>]
    [-File - | <filePath> <args>]
    [-ExecutionPolicy <ExecutionPolicy>]
    [-Command - | { <script-block> [-args <arg-array>] }
                | { <string> [<CommandParameters>] } ]

PowerShell[.exe] -Help | -? | /?
```

### <a name="parameters"></a><span data-ttu-id="e6f06-111">參數</span><span class="sxs-lookup"><span data-stu-id="e6f06-111">Parameters</span></span>

#### <a name="-psconsolefile-filepath"></a><span data-ttu-id="e6f06-112">-PSConsoleFile \<FilePath\></span><span class="sxs-lookup"><span data-stu-id="e6f06-112">-PSConsoleFile \<FilePath\></span></span>

<span data-ttu-id="e6f06-113">載入指定的 PowerShell 主控台檔案。</span><span class="sxs-lookup"><span data-stu-id="e6f06-113">Loads the specified PowerShell console file.</span></span> <span data-ttu-id="e6f06-114">輸入主控台檔案的路徑和名稱。</span><span class="sxs-lookup"><span data-stu-id="e6f06-114">Enter the path and name of the console file.</span></span> <span data-ttu-id="e6f06-115">若要建立主控台檔案，請在 PowerShell 中使用 Export-Console Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e6f06-115">To create a console file, use the Export-Console cmdlet in PowerShell.</span></span>

#### <a name="-version-powershell-version"></a><span data-ttu-id="e6f06-116">-Version \<PowerShell Version\></span><span class="sxs-lookup"><span data-stu-id="e6f06-116">-Version \<PowerShell Version\></span></span>

<span data-ttu-id="e6f06-117">啟動指定版本的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="e6f06-117">Starts the specified version of PowerShell.</span></span> <span data-ttu-id="e6f06-118">有效值為 2.0 和 3.0。</span><span class="sxs-lookup"><span data-stu-id="e6f06-118">Valid values are 2.0 and 3.0.</span></span> <span data-ttu-id="e6f06-119">您指定的版本必須安裝在系統上。</span><span class="sxs-lookup"><span data-stu-id="e6f06-119">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="e6f06-120">如果 Windows PowerShell 3.0 安裝在電腦上，則預設版本為 "3.0"。</span><span class="sxs-lookup"><span data-stu-id="e6f06-120">If Windows PowerShell 3.0 is installed on the computer, "3.0" is the default version.</span></span>
<span data-ttu-id="e6f06-121">否則，預設版本為 "2.0"。</span><span class="sxs-lookup"><span data-stu-id="e6f06-121">Otherwise, "2.0" is the default version.</span></span> <span data-ttu-id="e6f06-122">如需詳細資訊，請參閱 [安裝 PowerShell](/powershell/scripting/install/installing-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="e6f06-122">For more information, see [Installing PowerShell](/powershell/scripting/install/installing-windows-powershell).</span></span>

#### <a name="-nologo"></a><span data-ttu-id="e6f06-123">-NoLogo</span><span class="sxs-lookup"><span data-stu-id="e6f06-123">-NoLogo</span></span>

<span data-ttu-id="e6f06-124">啟動時隱藏著作權橫幅。</span><span class="sxs-lookup"><span data-stu-id="e6f06-124">Hides the copyright banner at startup.</span></span>

#### <a name="-noexit"></a><span data-ttu-id="e6f06-125">-NoExit</span><span class="sxs-lookup"><span data-stu-id="e6f06-125">-NoExit</span></span>

<span data-ttu-id="e6f06-126">執行啟動命令後不要結束。</span><span class="sxs-lookup"><span data-stu-id="e6f06-126">Does not exit after running startup commands.</span></span>

#### <a name="-sta"></a><span data-ttu-id="e6f06-127">-Sta</span><span class="sxs-lookup"><span data-stu-id="e6f06-127">-Sta</span></span>

<span data-ttu-id="e6f06-128">使用單一執行緒 Apartment 啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="e6f06-128">Starts PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="e6f06-129">在 Windows PowerShell 2.0 中，多執行緒 Apartment (MTA) 是預設值。</span><span class="sxs-lookup"><span data-stu-id="e6f06-129">In Windows PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span> <span data-ttu-id="e6f06-130">在 Windows PowerShell 3.0 中，單一執行緒 Apartment (STA) 是預設值。</span><span class="sxs-lookup"><span data-stu-id="e6f06-130">In Windows PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span>

#### <a name="-mta"></a><span data-ttu-id="e6f06-131">-Mta</span><span class="sxs-lookup"><span data-stu-id="e6f06-131">-Mta</span></span>

<span data-ttu-id="e6f06-132">使用多執行緒 Apartment 啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="e6f06-132">Starts PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="e6f06-133">此參數在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="e6f06-133">This parameter is introduced in PowerShell 3.0.</span></span> <span data-ttu-id="e6f06-134">在 PowerShell 2.0 中，預設為多執行緒 Apartment (MTA)。</span><span class="sxs-lookup"><span data-stu-id="e6f06-134">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span> <span data-ttu-id="e6f06-135">在 PowerShell 3.0 中，預設為單一執行緒 Apartment (STA)。</span><span class="sxs-lookup"><span data-stu-id="e6f06-135">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span>

#### <a name="-noprofile"></a><span data-ttu-id="e6f06-136">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="e6f06-136">-NoProfile</span></span>

<span data-ttu-id="e6f06-137">不載入 PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="e6f06-137">Does not load the PowerShell profile.</span></span>

#### <a name="-noninteractive"></a><span data-ttu-id="e6f06-138">-NonInteractive</span><span class="sxs-lookup"><span data-stu-id="e6f06-138">-NonInteractive</span></span>

<span data-ttu-id="e6f06-139">不向使用者顯示互動式提示。</span><span class="sxs-lookup"><span data-stu-id="e6f06-139">Does not present an interactive prompt to the user.</span></span>

#### <a name="-inputformat-text--xml"></a><span data-ttu-id="e6f06-140">-InputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="e6f06-140">-InputFormat {Text | XML}</span></span>

<span data-ttu-id="e6f06-141">描述傳送至 PowerShell 的資料格式。</span><span class="sxs-lookup"><span data-stu-id="e6f06-141">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="e6f06-142">有效值為 "Text" (文字字串) 或 "XML" (序列化的 CLIXML 格式)。</span><span class="sxs-lookup"><span data-stu-id="e6f06-142">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

#### <a name="-outputformat-text--xml"></a><span data-ttu-id="e6f06-143">-OutputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="e6f06-143">-OutputFormat {Text | XML}</span></span>

<span data-ttu-id="e6f06-144">決定 PowerShell 的輸出格式。</span><span class="sxs-lookup"><span data-stu-id="e6f06-144">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="e6f06-145">有效值為 "Text" (文字字串) 或 "XML" (序列化的 CLIXML 格式)。</span><span class="sxs-lookup"><span data-stu-id="e6f06-145">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

#### <a name="-windowstyle-window-style"></a><span data-ttu-id="e6f06-146">-WindowStyle \<Window style\></span><span class="sxs-lookup"><span data-stu-id="e6f06-146">-WindowStyle \<Window style\></span></span>

<span data-ttu-id="e6f06-147">設定工作階段的視窗樣式。</span><span class="sxs-lookup"><span data-stu-id="e6f06-147">Sets the window style for the session.</span></span> <span data-ttu-id="e6f06-148">有效值為 Normal、Minimized、Maximized 和 Hidden。</span><span class="sxs-lookup"><span data-stu-id="e6f06-148">Valid values are Normal, Minimized, Maximized and Hidden.</span></span>

#### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="e6f06-149">-EncodedCommand \<Base64EncodedCommand\></span><span class="sxs-lookup"><span data-stu-id="e6f06-149">-EncodedCommand \<Base64EncodedCommand\></span></span>

<span data-ttu-id="e6f06-150">接受 Base-64 編碼字串版本的命令。</span><span class="sxs-lookup"><span data-stu-id="e6f06-150">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="e6f06-151">使用此參數以將命令傳送至要求複雜引號或大括弧的 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="e6f06-151">Use this parameter to submit commands to PowerShell that require complex quotation marks or curly braces.</span></span> <span data-ttu-id="e6f06-152">字串必須使用 UTF UTF-16LE 字元編碼來格式化。</span><span class="sxs-lookup"><span data-stu-id="e6f06-152">The string must be formatted using UTF-16LE character encoding.</span></span>

#### <a name="-configurationname-string"></a><span data-ttu-id="e6f06-153">-ConfigurationName \<string\></span><span class="sxs-lookup"><span data-stu-id="e6f06-153">-ConfigurationName \<string\></span></span>

<span data-ttu-id="e6f06-154">指定 PowerShell 執行所在的設定端點。</span><span class="sxs-lookup"><span data-stu-id="e6f06-154">Specifies a configuration endpoint in which PowerShell is run.</span></span> <span data-ttu-id="e6f06-155">這可以是在本機電腦上註冊的任何端點，包括預設的 PowerShell 遠端端點，或具有特定使用者角色功能的自訂端點。</span><span class="sxs-lookup"><span data-stu-id="e6f06-155">This can be any endpoint registered on the local machine including the default PowerShell remoting endpoints or a custom endpoint having specific user role capabilities.</span></span>

#### <a name="-file----filepath-args"></a><span data-ttu-id="e6f06-156">-File-|\<filePath\>\<args\></span><span class="sxs-lookup"><span data-stu-id="e6f06-156">-File - | \<filePath\> \<args\></span></span>

<span data-ttu-id="e6f06-157">如果 **File** 的值是 "-"，則會從標準輸入讀取命令文字。</span><span class="sxs-lookup"><span data-stu-id="e6f06-157">If the value of **File** is "-", the command text is read from standard input.</span></span>
<span data-ttu-id="e6f06-158">如果 `powershell -File -` 執行時沒有重新導向的標準輸入，則會啟動一般會話。</span><span class="sxs-lookup"><span data-stu-id="e6f06-158">Running `powershell -File -` without redirected standard input starts a regular session.</span></span> <span data-ttu-id="e6f06-159">這與完全不指定 **File** 參數相同。</span><span class="sxs-lookup"><span data-stu-id="e6f06-159">This is the same as not specifying the **File** parameter at all.</span></span>

<span data-ttu-id="e6f06-160">如果 [檔案] **的值為檔案** 路徑，腳本會在區域範圍中執行 ( 「點來源」 ) ，如此腳本所建立的函式和變數就會在目前的會話中使用。</span><span class="sxs-lookup"><span data-stu-id="e6f06-160">If the value of **File** is a file path, the script runs in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="e6f06-161">輸入指令碼檔案路徑和任何參數。</span><span class="sxs-lookup"><span data-stu-id="e6f06-161">Enter the script file path and any parameters.</span></span> <span data-ttu-id="e6f06-162">**File** 必須是命令中的最後一個參數。</span><span class="sxs-lookup"><span data-stu-id="e6f06-162">**File** must be the last parameter in the command.</span></span> <span data-ttu-id="e6f06-163">在 **File** 參數之後輸入的所有值，都會被解釋為傳遞給該腳本的腳本檔案路徑和參數。</span><span class="sxs-lookup"><span data-stu-id="e6f06-163">All values typed after the **File** parameter are interpreted as the script file path and parameters passed to that script.</span></span>

<span data-ttu-id="e6f06-164">參數會以常值字串形式 (經過目前的殼層解譯後) 傳遞至指令碼。</span><span class="sxs-lookup"><span data-stu-id="e6f06-164">Parameters passed to the script are passed as literal strings, after interpretation by the current shell.</span></span> <span data-ttu-id="e6f06-165">例如，如果您在 **cmd.exe** ，而且想要傳遞環境變數值，您可以使用 **cmd.exe** 語法： `powershell.exe -File .\test.ps1 -TestParam %windir%`</span><span class="sxs-lookup"><span data-stu-id="e6f06-165">For example, if you are in **cmd.exe** and want to pass an environment variable value, you would use the **cmd.exe** syntax: `powershell.exe -File .\test.ps1 -TestParam %windir%`</span></span>

<span data-ttu-id="e6f06-166">相反地，在 `powershell.exe -File .\test.ps1 -TestParam $env:windir` **cmd.exe** 中執行會導致腳本接收常值字串， `$env:windir` 因為它對目前的 **cmd.exe** shell 沒有特殊意義。</span><span class="sxs-lookup"><span data-stu-id="e6f06-166">In contrast, running `powershell.exe -File .\test.ps1 -TestParam $env:windir` in **cmd.exe** results in the script receiving the literal string `$env:windir` because it has no special meaning to the current **cmd.exe** shell.</span></span> <span data-ttu-id="e6f06-167">`$env:windir`環境變數參考的樣式 _可以_ 在 **命令** 參數中使用，因為它會被視為 PowerShell 程式碼。</span><span class="sxs-lookup"><span data-stu-id="e6f06-167">The `$env:windir` style of environment variable reference _can_ be used inside a **Command** parameter, since there it will be interpreted as PowerShell code.</span></span>

<span data-ttu-id="e6f06-168">同樣地，如果您想要從 **批次腳本** 執行相同的命令，您可以使用 `%~dp0` 而 `.\` 非 `$PSScriptRoot` 或來表示目前的執行目錄： `powershell.exe -File %~dp0test.ps1 -TestParam %windir%` 。</span><span class="sxs-lookup"><span data-stu-id="e6f06-168">Similarly, if you want to execute the same command from a **Batch script** , you would use `%~dp0` instead of `.\` or `$PSScriptRoot` to represent the current execution directory: `powershell.exe -File %~dp0test.ps1 -TestParam %windir%`.</span></span>
<span data-ttu-id="e6f06-169">如果您改 `.\test.ps1` 為使用，則 PowerShell 會擲回錯誤，因為它找不到常值路徑 `.\test.ps1`</span><span class="sxs-lookup"><span data-stu-id="e6f06-169">If you instead used `.\test.ps1`, PowerShell would throw an error because it cannot find the literal path `.\test.ps1`</span></span>

<span data-ttu-id="e6f06-170">當 **file** 的值為檔案路徑 **時，檔案**_必須_ 是命令中的最後一個參數， **因為在檔案參數名稱** 之後輸入的任何字元都會被解釋為腳本檔案路徑，後面接著腳本參數。</span><span class="sxs-lookup"><span data-stu-id="e6f06-170">When the value of **File** is a file path, **File** _must_ be the last parameter in the command because any characters typed after the **File** parameter name are interpreted as the script file path followed by the script parameters.</span></span>

<span data-ttu-id="e6f06-171">您可以將腳本參數和值包含在 **File** 參數的值中。</span><span class="sxs-lookup"><span data-stu-id="e6f06-171">You can include the script parameters and values in the value of the **File** parameter.</span></span> <span data-ttu-id="e6f06-172">例如：`-File .\Get-Script.ps1 -Domain Central`</span><span class="sxs-lookup"><span data-stu-id="e6f06-172">For example: `-File .\Get-Script.ps1 -Domain Central`</span></span>

<span data-ttu-id="e6f06-173">一般而言，指令碼的切換參數可以包含或省略。</span><span class="sxs-lookup"><span data-stu-id="e6f06-173">Typically, the switch parameters of a script are either included or omitted.</span></span>
<span data-ttu-id="e6f06-174">例如，下列命令會使用腳本檔案的 **All** 參數 `Get-Script.ps1` ： `-File .\Get-Script.ps1 -All`</span><span class="sxs-lookup"><span data-stu-id="e6f06-174">For example, the following command uses the **All** parameter of the `Get-Script.ps1` script file: `-File .\Get-Script.ps1 -All`</span></span>

<span data-ttu-id="e6f06-175">在罕見的情況下，您可能需要為參數提供 **布林** 值。</span><span class="sxs-lookup"><span data-stu-id="e6f06-175">In rare cases, you might need to provide a **Boolean** value for a parameter.</span></span>
<span data-ttu-id="e6f06-176">以這種方式執行腳本時，不可能傳遞 switch 參數的明確布林值。</span><span class="sxs-lookup"><span data-stu-id="e6f06-176">It is not possible to pass an explicit boolean value for a switch parameter when running a script in this way.</span></span> <span data-ttu-id="e6f06-177">PowerShell 6 () 已移除這項限制 `pwsh.exe` 。</span><span class="sxs-lookup"><span data-stu-id="e6f06-177">This limitation was removed in PowerShell 6 (`pwsh.exe`).</span></span>

#### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="e6f06-178">-ExecutionPolicy \<ExecutionPolicy\></span><span class="sxs-lookup"><span data-stu-id="e6f06-178">-ExecutionPolicy \<ExecutionPolicy\></span></span>

<span data-ttu-id="e6f06-179">設定目前會話的預設執行原則，並將它儲存在 `$env:PSExecutionPolicyPreference` 環境變數中。</span><span class="sxs-lookup"><span data-stu-id="e6f06-179">Sets the default execution policy for the current session and saves it in the `$env:PSExecutionPolicyPreference` environment variable.</span></span> <span data-ttu-id="e6f06-180">此參數不會變更已在登錄中設定的 PowerShell 執行原則。</span><span class="sxs-lookup"><span data-stu-id="e6f06-180">This parameter does not change the PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="e6f06-181">如需 PowerShell 執行原則的資訊，包括有效值清單，請參閱 [about_Execution_Policies](about_Execution_Policies.md)。</span><span class="sxs-lookup"><span data-stu-id="e6f06-181">For information about PowerShell execution policies, including a list of valid values, see [about_Execution_Policies](about_Execution_Policies.md).</span></span>

#### <a name="-command"></a><span data-ttu-id="e6f06-182">-Command</span><span class="sxs-lookup"><span data-stu-id="e6f06-182">-Command</span></span>

<span data-ttu-id="e6f06-183">執行指定的命令 (和任何參數) 如同在 PowerShell 命令提示字元中輸入，然後結束，除非 `NoExit` 指定了參數。</span><span class="sxs-lookup"><span data-stu-id="e6f06-183">Executes the specified commands (and any parameters) as though they were typed at the PowerShell command prompt, and then exits, unless the `NoExit` parameter is specified.</span></span>

<span data-ttu-id="e6f06-184">**命令** 的值可以是 `-` 、腳本區塊或字串。</span><span class="sxs-lookup"><span data-stu-id="e6f06-184">The value of **Command** can be `-`, a script block, or a string.</span></span> <span data-ttu-id="e6f06-185">如果 **command** 的值為 `-` ，則會從標準輸入讀取命令文字。</span><span class="sxs-lookup"><span data-stu-id="e6f06-185">If the value of **Command** is `-`, the command text is read from standard input.</span></span>

<span data-ttu-id="e6f06-186">**命令** 參數只接受腳本區塊，以便在可辨識傳遞給 **命令** 的值做為 **ScriptBlock** 類型時執行。</span><span class="sxs-lookup"><span data-stu-id="e6f06-186">The **Command** parameter only accepts a script block for execution when it can recognize the value passed to **Command** as a **ScriptBlock** type.</span></span> <span data-ttu-id="e6f06-187">_只有_ `powershell.exe` 從另一個 PowerShell 主機執行時，才有可能發生此情況。</span><span class="sxs-lookup"><span data-stu-id="e6f06-187">This is _only_ possible when running `powershell.exe` from another PowerShell host.</span></span> <span data-ttu-id="e6f06-188">**ScriptBlock** 類型可以包含在現有的變數中，從運算式傳回，或由 PowerShell 主機剖析為常值腳本區塊（以大括弧括住 (`{}`) ），然後再傳遞至 `powershell.exe` 。</span><span class="sxs-lookup"><span data-stu-id="e6f06-188">The **ScriptBlock** type may be contained in an existing variable, returned from an expression, or parsed by the PowerShell host as a literal script block enclosed in curly braces (`{}`), before being passed to `powershell.exe`.</span></span>

```powershell
powershell -Command {Get-WinEvent -LogName security}
```

<span data-ttu-id="e6f06-189">在中 `cmd.exe` ，沒有腳本區塊 (或 **ScriptBlock** 類型) ，因此傳遞給 **命令** 的值 _一律_ 會是字串。</span><span class="sxs-lookup"><span data-stu-id="e6f06-189">In `cmd.exe`, there is no such thing as a script block (or **ScriptBlock** type), so the value passed to **Command** will _always_ be a string.</span></span> <span data-ttu-id="e6f06-190">您可以在字串內撰寫指令碼區塊，但它不會執行，其行為完全就像您在一般 PowerShell 提示字元中輸入它一樣，將指令碼區塊的內容印回給您。</span><span class="sxs-lookup"><span data-stu-id="e6f06-190">You can write a script block inside the string, but instead of being executed it will behave exactly as though you typed it at a typical PowerShell prompt, printing the contents of the script block back out to you.</span></span>

<span data-ttu-id="e6f06-191">傳遞給 **命令** 的字串仍會以 PowerShell 程式碼的形式執行，因此從執行時，在第一個位置通常不需要腳本區塊大括弧 `cmd.exe` 。</span><span class="sxs-lookup"><span data-stu-id="e6f06-191">A string passed to **Command** is still executed as PowerShell code, so the script block curly braces are often not required in the first place when running from `cmd.exe`.</span></span> <span data-ttu-id="e6f06-192">若要執行字串內定義的內嵌指令碼區塊，可以使用[呼叫運算子](about_operators.md#special-operators) `&`：</span><span class="sxs-lookup"><span data-stu-id="e6f06-192">To execute an inline script block defined inside a string, the [call operator](about_operators.md#special-operators) `&` can be used:</span></span>

```cmd
pwsh -Command "& {Get-WinEvent -LogName security}"
```

<span data-ttu-id="e6f06-193">如果 **command** 的值是字串， **命令** 必須是 pwsh 的最後一個參數，因為它後面的所有引數都會轉譯為要執行之命令的一部分。</span><span class="sxs-lookup"><span data-stu-id="e6f06-193">If the value of **Command** is a string, **Command** must be the last parameter for pwsh, because all arguments following it are interpreted as part of the command to execute.</span></span>

<span data-ttu-id="e6f06-194">從現有的 PowerShell 會話內呼叫時，結果會以還原序列化的 XML 物件（而不是即時物件）傳回到父 shell。</span><span class="sxs-lookup"><span data-stu-id="e6f06-194">When called from within an existing PowerShell session, the results are returned to the parent shell as deserialized XML objects, not live objects.</span></span> <span data-ttu-id="e6f06-195">若為其他 shell，則會以字串形式傳回結果。</span><span class="sxs-lookup"><span data-stu-id="e6f06-195">For other shells, the results are returned as strings.</span></span>

<span data-ttu-id="e6f06-196">如果 **command** 的值為 `-` ，則會從標準輸入讀取命令文字。</span><span class="sxs-lookup"><span data-stu-id="e6f06-196">If the value of **Command** is `-`, the command text is read from standard input.</span></span> <span data-ttu-id="e6f06-197">使用 **命令** 參數搭配標準輸入時，您必須重新導向標準輸入。</span><span class="sxs-lookup"><span data-stu-id="e6f06-197">You must redirect standard input when using the **Command** parameter with standard input.</span></span> <span data-ttu-id="e6f06-198">例如：</span><span class="sxs-lookup"><span data-stu-id="e6f06-198">For example:</span></span>

```powershell
@'
"in"

"hi" |
  % { "$_ there" }

"out"
'@ | powershell -NoProfile -Command -
```

<span data-ttu-id="e6f06-199">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="e6f06-199">This example produces the following output:</span></span>

```Output
in
hi there
out
```

<span data-ttu-id="e6f06-200">進程結束碼取決於腳本區塊內最後 (執行) 命令的狀態。</span><span class="sxs-lookup"><span data-stu-id="e6f06-200">The process exit code is determined by status of the last (executed) command within the script block.</span></span> <span data-ttu-id="e6f06-201">`0`當是 `$?` `$true` 或 `1` 時， `$?` 結束代碼為 `$false` 。</span><span class="sxs-lookup"><span data-stu-id="e6f06-201">The exit code is `0` when `$?` is `$true` or `1` when `$?` is `$false`.</span></span> <span data-ttu-id="e6f06-202">如果最後一個命令是外部程式或 PowerShell 腳本，其會明確地設定或以外的結束 `0` 代碼 `1` ，則會將結束代碼轉換為，以 `1` 進行進程結束代碼。</span><span class="sxs-lookup"><span data-stu-id="e6f06-202">If the last command is an external program or a PowerShell script that explicitly sets an exit code other than `0` or `1`, that exit code is converted to `1` for process exit code.</span></span> <span data-ttu-id="e6f06-203">若要保留特定的結束代碼，請加入 `exit $LASTEXITCODE` 至您的命令字串或腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="e6f06-203">To preserve the specific exit code, add `exit $LASTEXITCODE` to your command string or script block.</span></span>

<span data-ttu-id="e6f06-204">同樣地，當腳本終止 (的執行時間終止) 錯誤（例如 `throw` 或 `-ErrorAction Stop` ），或執行與<kbd>Ctrl</kbd> - <kbd>C</kbd>中斷時，就會傳回值1。</span><span class="sxs-lookup"><span data-stu-id="e6f06-204">Similarly, the value 1 is returned when a script-terminating (runspace-terminating) error, such as a `throw` or `-ErrorAction Stop`, occurs or when execution is interrupted with <kbd>Ctrl</kbd>-<kbd>C</kbd>.</span></span>

<span data-ttu-id="e6f06-205">_只有_ 在從另一個 PowerShell 主機執行 **PowerShell.exe** 時才有可能。</span><span class="sxs-lookup"><span data-stu-id="e6f06-205">_only_ possible when running **PowerShell.exe** from another PowerShell host.</span></span>
<span data-ttu-id="e6f06-206">**ScriptBlock** 類型可以包含在現有的變數中，從運算式傳回，或由 PowerShell 主機剖析為以大括弧括住的常值腳本區塊 `{}` ，然後再傳遞至 **PowerShell.exe** 。</span><span class="sxs-lookup"><span data-stu-id="e6f06-206">The **ScriptBlock** type may be contained in an existing variable, returned from an expression, or parsed by the PowerShell host as a literal script block enclosed in curly braces `{}`, before being passed to **PowerShell.exe** .</span></span>

<span data-ttu-id="e6f06-207">在 **cmd.exe** 中，沒有腳本區塊 (或 **ScriptBlock** 類型) 的這種情況，因此傳遞給 **命令** 的值 _一律_ 會是字串。</span><span class="sxs-lookup"><span data-stu-id="e6f06-207">In **cmd.exe** , there is no such thing as a script block (or **ScriptBlock** type), so the value passed to **Command** will _always_ be a string.</span></span> <span data-ttu-id="e6f06-208">您可以在字串內撰寫指令碼區塊，但它不會執行，其行為完全就像您在一般 PowerShell 提示字元中輸入它一樣，將指令碼區塊的內容印回給您。</span><span class="sxs-lookup"><span data-stu-id="e6f06-208">You can write a script block inside the string, but instead of being executed it will behave exactly as though you typed it at a typical PowerShell prompt, printing the contents of the script block back out to you.</span></span>

<span data-ttu-id="e6f06-209">傳遞給 **命令** 的字串仍會以 PowerShell 的形式執行，因此從 **cmd.exe** 執行時，通常不需要腳本區塊大括弧。</span><span class="sxs-lookup"><span data-stu-id="e6f06-209">A string passed to **Command** will still be executed as PowerShell, so the script block curly braces are often not required in the first place when running from **cmd.exe** .</span></span> <span data-ttu-id="e6f06-210">若要執行在字串內定義的內嵌腳本區塊，可以使用[呼叫運算子](about_operators.md#special-operators) 
 `&` ：</span><span class="sxs-lookup"><span data-stu-id="e6f06-210">To execute an inline script block defined inside a string, the [call operator](about_operators.md#special-operators)
`&` can be used:</span></span>

```console
"& {<command>}"
```

#### <a name="-help---"></a><span data-ttu-id="e6f06-211">-Help, -?, /?</span><span class="sxs-lookup"><span data-stu-id="e6f06-211">-Help, -?, /?</span></span>

<span data-ttu-id="e6f06-212">顯示 **PowerShell.exe** 的說明。</span><span class="sxs-lookup"><span data-stu-id="e6f06-212">Displays help for **PowerShell.exe** .</span></span> <span data-ttu-id="e6f06-213">如果您在 PowerShell 會話中輸入 **PowerShell.exe** 命令，請在命令參數前面加上連字號 ( ) ，而不是正斜線 (/) 。</span><span class="sxs-lookup"><span data-stu-id="e6f06-213">If you are typing a **PowerShell.exe** command in a PowerShell session, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="e6f06-214">您可以在 **cmd.exe** 中使用連字號或正斜線。</span><span class="sxs-lookup"><span data-stu-id="e6f06-214">You can use either a hyphen or forward slash in **cmd.exe** .</span></span>

### <a name="remarks"></a><span data-ttu-id="e6f06-215">REMARKS</span><span class="sxs-lookup"><span data-stu-id="e6f06-215">REMARKS</span></span>

<span data-ttu-id="e6f06-216">疑難排解注意事項：在 PowerShell 2.0 中，從 PowerShell 主控台啟動某些程式會失敗，並出現 **LastExitCode** 的0xc0000142。</span><span class="sxs-lookup"><span data-stu-id="e6f06-216">Troubleshooting note: In PowerShell 2.0, starting some programs from the PowerShell console fails with a **LastExitCode** of 0xc0000142.</span></span>

### <a name="examples"></a><span data-ttu-id="e6f06-217">範例</span><span class="sxs-lookup"><span data-stu-id="e6f06-217">EXAMPLES</span></span>

```powershell
# Create a new PowerShell session and load a saved console file
PowerShell -PSConsoleFile sqlsnapin.psc1

# Create a new PowerShell V2 session with text input, XML output, and no logo
PowerShell -Version 2.0 -NoLogo -InputFormat text -OutputFormat XML

# Execute a PowerShell Command in a session
PowerShell -Command "Get-EventLog -LogName security"

# Run a script block in a session
PowerShell -Command {Get-EventLog -LogName security}

# An alternate way to run a command in a new session
PowerShell -Command "& {Get-EventLog -LogName security}"

# To use the -EncodedCommand parameter:
$command = "dir 'c:\program files' "
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
powershell.exe -encodedCommand $encodedCommand
```
