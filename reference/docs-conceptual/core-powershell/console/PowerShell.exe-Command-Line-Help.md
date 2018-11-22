---
ms.date: 08/14/2018
keywords: powershell,cmdlet
title: PowerShell.exe 命令列說明
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 0a11ebb11d29adf5853c232b3aa10bc72f92bf0c
ms.sourcegitcommit: 03c7672ee72698fe88a73e99702ceaadf87e702f
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2018
ms.locfileid: "51691825"
---
# <a name="powershellexe-command-line-help"></a><span data-ttu-id="f5e01-103">PowerShell.exe 命令列說明</span><span class="sxs-lookup"><span data-stu-id="f5e01-103">PowerShell.exe Command-Line Help</span></span>

<span data-ttu-id="f5e01-104">您可以使用 PowerShell.exe 從其他工具的命令列 (例如 Cmd.exe) 啟動 PowerShell 工作階段，或在 PowerShell 命令列中使用以啟動新的工作階段。</span><span class="sxs-lookup"><span data-stu-id="f5e01-104">You can use PowerShell.exe to start a PowerShell session from the command line of another tool, such as Cmd.exe, or use it at the PowerShell command line to start a new session.</span></span> <span data-ttu-id="f5e01-105">使用參數可自訂工作階段。</span><span class="sxs-lookup"><span data-stu-id="f5e01-105">Use the parameters to customize the session.</span></span>

## <a name="syntax"></a><span data-ttu-id="f5e01-106">語法</span><span class="sxs-lookup"><span data-stu-id="f5e01-106">Syntax</span></span>

```syntax
PowerShell[.exe]
       [-Command { - | <script-block> [-args <arg-array>]
                     | <string> [<CommandParameters>] } ]
       [-EncodedCommand <Base64EncodedCommand>]
       [-ExecutionPolicy <ExecutionPolicy>]
       [-File <FilePath> [<Args>]]
       [-InputFormat {Text | XML}]
       [-Mta]
       [-NoExit]
       [-NoLogo]
       [-NonInteractive]
       [-NoProfile]
       [-OutputFormat {Text | XML}]
       [-PSConsoleFile <FilePath> | -Version <PowerShell version>]
       [-Sta]
       [-WindowStyle <style>]

PowerShell[.exe] -Help | -? | /?
```

## <a name="parameters"></a><span data-ttu-id="f5e01-107">參數</span><span class="sxs-lookup"><span data-stu-id="f5e01-107">Parameters</span></span>

### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="f5e01-108">-EncodedCommand <Base64EncodedCommand></span><span class="sxs-lookup"><span data-stu-id="f5e01-108">-EncodedCommand <Base64EncodedCommand></span></span>

<span data-ttu-id="f5e01-109">接受 Base-64 編碼字串版本的命令。</span><span class="sxs-lookup"><span data-stu-id="f5e01-109">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="f5e01-110">使用此參數以將命令傳送至要求複雜引號或大括弧的 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="f5e01-110">Use this parameter to submit commands to PowerShell that require complex quotation marks or curly braces.</span></span>

### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="f5e01-111">-ExecutionPolicy <ExecutionPolicy></span><span class="sxs-lookup"><span data-stu-id="f5e01-111">-ExecutionPolicy <ExecutionPolicy></span></span>

<span data-ttu-id="f5e01-112">設定目前工作階段的預設執行原則並且儲存至 $env:PSExecutionPolicyPreference 環境變數中。</span><span class="sxs-lookup"><span data-stu-id="f5e01-112">Sets the default execution policy for the current session and saves it in the $env:PSExecutionPolicyPreference environment variable.</span></span> <span data-ttu-id="f5e01-113">此參數不會變更已在登錄中設定的 PowerShell 執行原則。</span><span class="sxs-lookup"><span data-stu-id="f5e01-113">This parameter doesn't change the PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="f5e01-114">如需 PowerShell 執行原則的資訊，包括有效值清單，請參閱 [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies)。</span><span class="sxs-lookup"><span data-stu-id="f5e01-114">For information about PowerShell execution policies, including a list of valid values, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

### <a name="-file-filepath-parameters"></a><span data-ttu-id="f5e01-115">-File <FilePath> \[<Parameters>]</span><span class="sxs-lookup"><span data-stu-id="f5e01-115">-File <FilePath> \[<Parameters>]</span></span>

<span data-ttu-id="f5e01-116">在本機領域 (「點來源」) 執行指定指令碼，讓指令碼建立的函式和變數在目前的工作階段可用。</span><span class="sxs-lookup"><span data-stu-id="f5e01-116">Runs the specified script in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="f5e01-117">輸入指令碼檔案路徑和任何參數。</span><span class="sxs-lookup"><span data-stu-id="f5e01-117">Enter the script file path and any parameters.</span></span> <span data-ttu-id="f5e01-118">**File** 必須是命令中的最後一個參數。</span><span class="sxs-lookup"><span data-stu-id="f5e01-118">**File** must be the last parameter in the command.</span></span> <span data-ttu-id="f5e01-119">在 **-File** 參數之後輸入的所有值都會解譯為指令碼檔案路徑以及要傳遞給該指令碼的參數。</span><span class="sxs-lookup"><span data-stu-id="f5e01-119">All values typed after the **-File** parameter are interpreted as the script file path and parameters passed to that script.</span></span>

<span data-ttu-id="f5e01-120">參數會以常值字串形式 (經過目前的殼層解譯後) 傳遞至指令碼。</span><span class="sxs-lookup"><span data-stu-id="f5e01-120">Parameters passed to the script are passed as literal strings, after interpretation by the current shell.</span></span> <span data-ttu-id="f5e01-121">例如，如果您在 cmd.exe 中，並想要傳遞環境變數值，您會使用 cmd.exe 語法： `powershell.exe -File .\test.ps1 -TestParam %windir%`</span><span class="sxs-lookup"><span data-stu-id="f5e01-121">For example, if you are in cmd.exe and want to pass an environment variable value, you would use the cmd.exe syntax: `powershell.exe -File .\test.ps1 -TestParam %windir%`</span></span>

<span data-ttu-id="f5e01-122">相較之下，執行`powershell.exe -File .\test.ps1 -TestParam $env:windir`接收的常值字串的指令碼中的 cmd.exe 結果中`$env:windir`因為它沒有任何特殊的意義，到目前的 cmd.exe 殼層。</span><span class="sxs-lookup"><span data-stu-id="f5e01-122">In contrast, running `powershell.exe -File .\test.ps1 -TestParam $env:windir` in cmd.exe results in the script receiving the literal string `$env:windir` because it has no special meaning to the current cmd.exe shell.</span></span>
<span data-ttu-id="f5e01-123">`$env:windir`環境變數參考的樣式_可以_能在內部使用`-Command`參數，因為那里將被解譯為 PowerShell 程式碼。</span><span class="sxs-lookup"><span data-stu-id="f5e01-123">The `$env:windir` style of environment variable reference _can_ be used inside a `-Command` parameter, since there it will be interpreted as PowerShell code.</span></span>

### <a name="-inputformat-text--xml"></a><span data-ttu-id="f5e01-124">\-InputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="f5e01-124">\-InputFormat {Text | XML}</span></span>

<span data-ttu-id="f5e01-125">描述傳送至 PowerShell 的資料格式。</span><span class="sxs-lookup"><span data-stu-id="f5e01-125">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="f5e01-126">有效值為 "Text" (文字字串) 或 "XML" (序列化的 CLIXML 格式)。</span><span class="sxs-lookup"><span data-stu-id="f5e01-126">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-mta"></a><span data-ttu-id="f5e01-127">-Mta</span><span class="sxs-lookup"><span data-stu-id="f5e01-127">-Mta</span></span>

<span data-ttu-id="f5e01-128">使用多執行緒 Apartment 啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="f5e01-128">Starts PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="f5e01-129">此參數在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="f5e01-129">This parameter is introduced in PowerShell 3.0.</span></span> <span data-ttu-id="f5e01-130">在 PowerShell 3.0 中，預設為單一執行緒 Apartment (STA)。</span><span class="sxs-lookup"><span data-stu-id="f5e01-130">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="f5e01-131">在 PowerShell 2.0 中，預設為多執行緒 Apartment (MTA)。</span><span class="sxs-lookup"><span data-stu-id="f5e01-131">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-noexit"></a><span data-ttu-id="f5e01-132">-NoExit</span><span class="sxs-lookup"><span data-stu-id="f5e01-132">-NoExit</span></span>

<span data-ttu-id="f5e01-133">執行啟動命令後不要結束。</span><span class="sxs-lookup"><span data-stu-id="f5e01-133">Doesn't exit after running startup commands.</span></span>

### <a name="-nologo"></a><span data-ttu-id="f5e01-134">-NoLogo</span><span class="sxs-lookup"><span data-stu-id="f5e01-134">-NoLogo</span></span>

<span data-ttu-id="f5e01-135">啟動時隱藏著作權橫幅。</span><span class="sxs-lookup"><span data-stu-id="f5e01-135">Hides the copyright banner at startup.</span></span>

### <a name="-noninteractive"></a><span data-ttu-id="f5e01-136">-NonInteractive</span><span class="sxs-lookup"><span data-stu-id="f5e01-136">-NonInteractive</span></span>

<span data-ttu-id="f5e01-137">不向使用者顯示互動式提示。</span><span class="sxs-lookup"><span data-stu-id="f5e01-137">Doesn't present an interactive prompt to the user.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="f5e01-138">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="f5e01-138">-NoProfile</span></span>

<span data-ttu-id="f5e01-139">不載入 PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="f5e01-139">Doesn't load the PowerShell profile.</span></span>

### <a name="-outputformat-text--xml"></a><span data-ttu-id="f5e01-140">-OutputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="f5e01-140">-OutputFormat {Text | XML}</span></span>

<span data-ttu-id="f5e01-141">決定 PowerShell 的輸出格式。</span><span class="sxs-lookup"><span data-stu-id="f5e01-141">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="f5e01-142">有效值為 "Text" (文字字串) 或 "XML" (序列化的 CLIXML 格式)。</span><span class="sxs-lookup"><span data-stu-id="f5e01-142">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-psconsolefile-filepath"></a><span data-ttu-id="f5e01-143">-PSConsoleFile <FilePath></span><span class="sxs-lookup"><span data-stu-id="f5e01-143">-PSConsoleFile <FilePath></span></span>

<span data-ttu-id="f5e01-144">載入指定的 PowerShell 主控台檔案。</span><span class="sxs-lookup"><span data-stu-id="f5e01-144">Loads the specified PowerShell console file.</span></span> <span data-ttu-id="f5e01-145">輸入主控台檔案的路徑和名稱。</span><span class="sxs-lookup"><span data-stu-id="f5e01-145">Enter the path and name of the console file.</span></span> <span data-ttu-id="f5e01-146">若要建立主控台檔案，請在 PowerShell 中使用 [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f5e01-146">To create a console file, use the [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet in PowerShell.</span></span>

### <a name="-sta"></a><span data-ttu-id="f5e01-147">-Sta</span><span class="sxs-lookup"><span data-stu-id="f5e01-147">-Sta</span></span>

<span data-ttu-id="f5e01-148">使用單一執行緒 Apartment 啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="f5e01-148">Starts PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="f5e01-149">在 PowerShell 3.0 中，預設為單一執行緒 Apartment (STA)。</span><span class="sxs-lookup"><span data-stu-id="f5e01-149">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="f5e01-150">在 PowerShell 2.0 中，預設為多執行緒 Apartment (MTA)。</span><span class="sxs-lookup"><span data-stu-id="f5e01-150">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-version-powershell-version"></a><span data-ttu-id="f5e01-151">-Version <PowerShell Version></span><span class="sxs-lookup"><span data-stu-id="f5e01-151">-Version <PowerShell Version></span></span>

<span data-ttu-id="f5e01-152">啟動指定版本的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="f5e01-152">Starts the specified version of PowerShell.</span></span> <span data-ttu-id="f5e01-153">您指定的版本必須安裝在系統上。</span><span class="sxs-lookup"><span data-stu-id="f5e01-153">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="f5e01-154">如果 PowerShell 3.0 已安裝於電腦上，有效值為 "2.0" 和 "3.0"。</span><span class="sxs-lookup"><span data-stu-id="f5e01-154">If PowerShell 3.0 is installed on the computer, valid values are "2.0" and "3.0".</span></span> <span data-ttu-id="f5e01-155">預設值為 "3.0"。</span><span class="sxs-lookup"><span data-stu-id="f5e01-155">The default value is "3.0".</span></span>

<span data-ttu-id="f5e01-156">如果未安裝 PowerShell 3.0，唯一有效的值為 "2.0"。</span><span class="sxs-lookup"><span data-stu-id="f5e01-156">If PowerShell 3.0 isn't installed, the only valid value is "2.0".</span></span> <span data-ttu-id="f5e01-157">其他值會被忽略。</span><span class="sxs-lookup"><span data-stu-id="f5e01-157">Other values are ignored.</span></span>

<span data-ttu-id="f5e01-158">如需詳細資訊，請參閱[安裝 Windows PowerShell](../../setup/installing-windows-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="f5e01-158">For more information, see [Installing Windows PowerShell](../../setup/installing-windows-powershell.md).</span></span>

### <a name="-windowstyle-window-style"></a><span data-ttu-id="f5e01-159">-WindowStyle <Window style></span><span class="sxs-lookup"><span data-stu-id="f5e01-159">-WindowStyle <Window style></span></span>

<span data-ttu-id="f5e01-160">設定工作階段的視窗樣式。</span><span class="sxs-lookup"><span data-stu-id="f5e01-160">Sets the window style for the session.</span></span> <span data-ttu-id="f5e01-161">有效值為 Normal、Minimized、Maximized 與 Hidden。</span><span class="sxs-lookup"><span data-stu-id="f5e01-161">Valid values are Normal, Minimized, Maximized, and Hidden.</span></span>

### <a name="-command"></a><span data-ttu-id="f5e01-162">-Command</span><span class="sxs-lookup"><span data-stu-id="f5e01-162">-Command</span></span>

<span data-ttu-id="f5e01-163">執行指定的命令 (搭配任何參數)，就如同在 PowerShell 命令提示字元中輸入它們一樣。</span><span class="sxs-lookup"><span data-stu-id="f5e01-163">Executes the specified commands (with any parameters) as though they were typed at the PowerShell command prompt.</span></span>
<span data-ttu-id="f5e01-164">執行之後，PowerShell 會結束除非**NoExit**指定參數。</span><span class="sxs-lookup"><span data-stu-id="f5e01-164">After execution, PowerShell exits unless the **NoExit** parameter is specified.</span></span>
<span data-ttu-id="f5e01-165">`-Command` 之後的任何文字都會以單一命令列形式傳送至 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="f5e01-165">Any text after `-Command` is sent as a single command line to PowerShell.</span></span>
<span data-ttu-id="f5e01-166">這與 `-File` 處理要傳送至指令碼之參數的方法不同。</span><span class="sxs-lookup"><span data-stu-id="f5e01-166">This is different from how `-File` handles parameters sent to a script.</span></span>

<span data-ttu-id="f5e01-167">值`-Command`可以是"-"、 字串或指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="f5e01-167">The value of `-Command` can be "-", a string, or a script block.</span></span>
<span data-ttu-id="f5e01-168">命令的結果會回到父殼層為已還原序列化的 XML 物件，不是即時物件。</span><span class="sxs-lookup"><span data-stu-id="f5e01-168">The results of the command are returned to the parent shell as deserialized XML objects, not live objects.</span></span>

<span data-ttu-id="f5e01-169">如果值`-Command`是"-"，從標準輸入讀取命令文字。</span><span class="sxs-lookup"><span data-stu-id="f5e01-169">If the value of `-Command` is "-", the command text is read from standard input.</span></span>

<span data-ttu-id="f5e01-170">當 windows 7`-Command`是一個字串，**命令**_必須_是最後一個命令會被解譯為命令引數之後輸入的任何字元，因此指定的參數。</span><span class="sxs-lookup"><span data-stu-id="f5e01-170">When the value of `-Command` is a string, **Command** _must_ be the last parameter specified because any characters typed after the command are interpreted as the command arguments.</span></span>

<span data-ttu-id="f5e01-171">**命令**參數只接受執行指令碼區塊，就可以識別傳遞給的值時`-Command`做為指令碼區塊類型。</span><span class="sxs-lookup"><span data-stu-id="f5e01-171">The **Command** parameter only accepts a script block for execution when it can recognize the value passed to `-Command` as a ScriptBlock type.</span></span>
<span data-ttu-id="f5e01-172">這是_只_可能從另一個 PowerShell 主機中執行 PowerShell.exe 時。</span><span class="sxs-lookup"><span data-stu-id="f5e01-172">This is _only_ possible when running PowerShell.exe from another PowerShell host.</span></span>
<span data-ttu-id="f5e01-173">裝載為常值的指令碼區塊，大括號括住的類型可能包含在現有的變數，傳回運算式，或剖析的 powershell 指令碼區塊`{}`，才能傳遞至 PowerShell.exe。</span><span class="sxs-lookup"><span data-stu-id="f5e01-173">The ScriptBlock type may be contained in an existing variable, returned from an expression, or parsed by the PowerShell host as a literal script block enclosed in curly braces `{}`, before being passed to PowerShell.exe.</span></span>

<span data-ttu-id="f5e01-174">在 cmd.exe，沒有這類的指令碼區塊中 （或指令碼區塊型別），因此值傳遞給**命令**會_一律_是字串。</span><span class="sxs-lookup"><span data-stu-id="f5e01-174">In cmd.exe, there is no such thing as a script block (or ScriptBlock type), so the value passed to **Command** will _always_ be a string.</span></span>
<span data-ttu-id="f5e01-175">您可以撰寫指令碼區塊內的字串，但是而不是正在執行它的行為與完全如同您在一般的 PowerShell 提示字元下輸入，指令碼的內容列印封鎖回給您。</span><span class="sxs-lookup"><span data-stu-id="f5e01-175">You can write a script block inside the string, but instead of being executed it will behave exactly as though you typed it at a typical PowerShell prompt, printing the contents of the script block back out to you.</span></span>

<span data-ttu-id="f5e01-176">字串傳遞至`-Command`仍然會執行 powershell，因此指令碼區塊大括號通常不需要在一開始從 cmd.exe 執行時。</span><span class="sxs-lookup"><span data-stu-id="f5e01-176">A string passed to `-Command` will still be executed as PowerShell, so the script block curly braces are often not required in the first place when running from cmd.exe.</span></span>
<span data-ttu-id="f5e01-177">若要執行內的字串，定義為內嵌指令碼區塊[呼叫運算子](/powershell/module/microsoft.powershell.core/about/about_operators#call-operator-)`&`可用：</span><span class="sxs-lookup"><span data-stu-id="f5e01-177">To execute an inline script block defined inside a string, the [call operator](/powershell/module/microsoft.powershell.core/about/about_operators#call-operator-) `&` can be used:</span></span>

```console
"& {<command>}"
```

### <a name="-help---"></a><span data-ttu-id="f5e01-178">-Help, -?, /?</span><span class="sxs-lookup"><span data-stu-id="f5e01-178">-Help, -?, /?</span></span>

<span data-ttu-id="f5e01-179">顯示 powershell.exe 的語法。</span><span class="sxs-lookup"><span data-stu-id="f5e01-179">Shows the syntax of powershell.exe.</span></span> <span data-ttu-id="f5e01-180">若要在 PowerShell 中鍵入 PowerShell.exe 命令，命令參數之前要加上連字號 (-)，而不是正斜線 (/)。</span><span class="sxs-lookup"><span data-stu-id="f5e01-180">If you are typing a PowerShell.exe command in PowerShell, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="f5e01-181">在 Cmd.exe 中，您可以使用連字號或正斜線。</span><span class="sxs-lookup"><span data-stu-id="f5e01-181">You can use either a hyphen or forward slash in Cmd.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="f5e01-182">疑難排解注意事項︰在 PowerShell 2.0 中，啟動 Windows PowerShell 主控台中的某些程式會失敗，LastExitCode 為 0xc0000142。</span><span class="sxs-lookup"><span data-stu-id="f5e01-182">Troubleshooting Note: In PowerShell 2.0, starting some programs in the Windows PowerShell console fails with a LastExitCode of 0xc0000142.</span></span>

## <a name="examples"></a><span data-ttu-id="f5e01-183">範例</span><span class="sxs-lookup"><span data-stu-id="f5e01-183">EXAMPLES</span></span>

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
