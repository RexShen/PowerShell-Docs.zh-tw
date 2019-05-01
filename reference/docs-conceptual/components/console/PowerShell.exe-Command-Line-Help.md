---
ms.date: 08/14/2018
keywords: powershell,cmdlet
title: PowerShell.exe 命令列說明
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 0a11ebb11d29adf5853c232b3aa10bc72f92bf0c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058508"
---
# <a name="powershellexe-command-line-help"></a><span data-ttu-id="9c3b4-103">PowerShell.exe 命令列說明</span><span class="sxs-lookup"><span data-stu-id="9c3b4-103">PowerShell.exe Command-Line Help</span></span>

<span data-ttu-id="9c3b4-104">您可以使用 PowerShell.exe 從其他工具的命令列 (例如 Cmd.exe) 啟動 PowerShell 工作階段，或在 PowerShell 命令列中使用以啟動新的工作階段。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-104">You can use PowerShell.exe to start a PowerShell session from the command line of another tool, such as Cmd.exe, or use it at the PowerShell command line to start a new session.</span></span> <span data-ttu-id="9c3b4-105">使用參數可自訂工作階段。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-105">Use the parameters to customize the session.</span></span>

## <a name="syntax"></a><span data-ttu-id="9c3b4-106">語法</span><span class="sxs-lookup"><span data-stu-id="9c3b4-106">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="9c3b4-107">參數</span><span class="sxs-lookup"><span data-stu-id="9c3b4-107">Parameters</span></span>

### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="9c3b4-108">-EncodedCommand <Base64EncodedCommand></span><span class="sxs-lookup"><span data-stu-id="9c3b4-108">-EncodedCommand <Base64EncodedCommand></span></span>

<span data-ttu-id="9c3b4-109">接受 Base-64 編碼字串版本的命令。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-109">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="9c3b4-110">使用此參數以將命令傳送至要求複雜引號或大括弧的 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-110">Use this parameter to submit commands to PowerShell that require complex quotation marks or curly braces.</span></span>

### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="9c3b4-111">-ExecutionPolicy <ExecutionPolicy></span><span class="sxs-lookup"><span data-stu-id="9c3b4-111">-ExecutionPolicy <ExecutionPolicy></span></span>

<span data-ttu-id="9c3b4-112">設定目前工作階段的預設執行原則並且儲存至 $env:PSExecutionPolicyPreference 環境變數中。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-112">Sets the default execution policy for the current session and saves it in the $env:PSExecutionPolicyPreference environment variable.</span></span> <span data-ttu-id="9c3b4-113">此參數不會變更已在登錄中設定的 PowerShell 執行原則。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-113">This parameter doesn't change the PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="9c3b4-114">如需 PowerShell 執行原則的資訊，包括有效值清單，請參閱 [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies)。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-114">For information about PowerShell execution policies, including a list of valid values, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

### <a name="-file-filepath-parameters"></a><span data-ttu-id="9c3b4-115">-File <FilePath> \[<Parameters>]</span><span class="sxs-lookup"><span data-stu-id="9c3b4-115">-File <FilePath> \[<Parameters>]</span></span>

<span data-ttu-id="9c3b4-116">在本機領域 (「點來源」) 執行指定指令碼，讓指令碼建立的函式和變數在目前的工作階段可用。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-116">Runs the specified script in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="9c3b4-117">輸入指令碼檔案路徑和任何參數。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-117">Enter the script file path and any parameters.</span></span> <span data-ttu-id="9c3b4-118">**File** 必須是命令中的最後一個參數。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-118">**File** must be the last parameter in the command.</span></span> <span data-ttu-id="9c3b4-119">在 **-File** 參數之後輸入的所有值都會解譯為指令碼檔案路徑以及要傳遞給該指令碼的參數。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-119">All values typed after the **-File** parameter are interpreted as the script file path and parameters passed to that script.</span></span>

<span data-ttu-id="9c3b4-120">參數會以常值字串形式 (經過目前的殼層解譯後) 傳遞至指令碼。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-120">Parameters passed to the script are passed as literal strings, after interpretation by the current shell.</span></span> <span data-ttu-id="9c3b4-121">例如，如果您在 cmd.exe 中且想要傳遞環境變數值，您會使用 cmd.exe 語法：`powershell.exe -File .\test.ps1 -TestParam %windir%`</span><span class="sxs-lookup"><span data-stu-id="9c3b4-121">For example, if you are in cmd.exe and want to pass an environment variable value, you would use the cmd.exe syntax: `powershell.exe -File .\test.ps1 -TestParam %windir%`</span></span>

<span data-ttu-id="9c3b4-122">相較之下，在 cmd.exe 中執行 `powershell.exe -File .\test.ps1 -TestParam $env:windir` 會導致指令碼接收常值字串 `$env:windir`，因為它對於目前的 cmd.exe 殼層沒有任何特殊意義。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-122">In contrast, running `powershell.exe -File .\test.ps1 -TestParam $env:windir` in cmd.exe results in the script receiving the literal string `$env:windir` because it has no special meaning to the current cmd.exe shell.</span></span>
<span data-ttu-id="9c3b4-123">環境變數參考的 `$env:windir` 樣式「可以」在 `-Command` 參數內部使用，因為它將在該處解譯為 PowerShell 程式碼。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-123">The `$env:windir` style of environment variable reference _can_ be used inside a `-Command` parameter, since there it will be interpreted as PowerShell code.</span></span>

### <a name="-inputformat-text--xml"></a><span data-ttu-id="9c3b4-124">\-InputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="9c3b4-124">\-InputFormat {Text | XML}</span></span>

<span data-ttu-id="9c3b4-125">描述傳送至 PowerShell 的資料格式。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-125">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="9c3b4-126">有效值為 "Text" (文字字串) 或 "XML" (序列化的 CLIXML 格式)。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-126">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-mta"></a><span data-ttu-id="9c3b4-127">-Mta</span><span class="sxs-lookup"><span data-stu-id="9c3b4-127">-Mta</span></span>

<span data-ttu-id="9c3b4-128">使用多執行緒 Apartment 啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-128">Starts PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="9c3b4-129">此參數在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-129">This parameter is introduced in PowerShell 3.0.</span></span> <span data-ttu-id="9c3b4-130">在 PowerShell 3.0 中，預設為單一執行緒 Apartment (STA)。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-130">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="9c3b4-131">在 PowerShell 2.0 中，預設為多執行緒 Apartment (MTA)。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-131">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-noexit"></a><span data-ttu-id="9c3b4-132">-NoExit</span><span class="sxs-lookup"><span data-stu-id="9c3b4-132">-NoExit</span></span>

<span data-ttu-id="9c3b4-133">執行啟動命令後不要結束。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-133">Doesn't exit after running startup commands.</span></span>

### <a name="-nologo"></a><span data-ttu-id="9c3b4-134">-NoLogo</span><span class="sxs-lookup"><span data-stu-id="9c3b4-134">-NoLogo</span></span>

<span data-ttu-id="9c3b4-135">啟動時隱藏著作權橫幅。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-135">Hides the copyright banner at startup.</span></span>

### <a name="-noninteractive"></a><span data-ttu-id="9c3b4-136">-NonInteractive</span><span class="sxs-lookup"><span data-stu-id="9c3b4-136">-NonInteractive</span></span>

<span data-ttu-id="9c3b4-137">不向使用者顯示互動式提示。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-137">Doesn't present an interactive prompt to the user.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="9c3b4-138">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="9c3b4-138">-NoProfile</span></span>

<span data-ttu-id="9c3b4-139">不載入 PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-139">Doesn't load the PowerShell profile.</span></span>

### <a name="-outputformat-text--xml"></a><span data-ttu-id="9c3b4-140">-OutputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="9c3b4-140">-OutputFormat {Text | XML}</span></span>

<span data-ttu-id="9c3b4-141">決定 PowerShell 的輸出格式。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-141">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="9c3b4-142">有效值為 "Text" (文字字串) 或 "XML" (序列化的 CLIXML 格式)。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-142">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-psconsolefile-filepath"></a><span data-ttu-id="9c3b4-143">-PSConsoleFile <FilePath></span><span class="sxs-lookup"><span data-stu-id="9c3b4-143">-PSConsoleFile <FilePath></span></span>

<span data-ttu-id="9c3b4-144">載入指定的 PowerShell 主控台檔案。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-144">Loads the specified PowerShell console file.</span></span> <span data-ttu-id="9c3b4-145">輸入主控台檔案的路徑和名稱。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-145">Enter the path and name of the console file.</span></span> <span data-ttu-id="9c3b4-146">若要建立主控台檔案，請在 PowerShell 中使用 [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-146">To create a console file, use the [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet in PowerShell.</span></span>

### <a name="-sta"></a><span data-ttu-id="9c3b4-147">-Sta</span><span class="sxs-lookup"><span data-stu-id="9c3b4-147">-Sta</span></span>

<span data-ttu-id="9c3b4-148">使用單一執行緒 Apartment 啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-148">Starts PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="9c3b4-149">在 PowerShell 3.0 中，預設為單一執行緒 Apartment (STA)。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-149">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="9c3b4-150">在 PowerShell 2.0 中，預設為多執行緒 Apartment (MTA)。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-150">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-version-powershell-version"></a><span data-ttu-id="9c3b4-151">-Version <PowerShell Version></span><span class="sxs-lookup"><span data-stu-id="9c3b4-151">-Version <PowerShell Version></span></span>

<span data-ttu-id="9c3b4-152">啟動指定版本的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-152">Starts the specified version of PowerShell.</span></span> <span data-ttu-id="9c3b4-153">您指定的版本必須安裝在系統上。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-153">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="9c3b4-154">如果 PowerShell 3.0 已安裝於電腦上，有效值為 "2.0" 和 "3.0"。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-154">If PowerShell 3.0 is installed on the computer, valid values are "2.0" and "3.0".</span></span> <span data-ttu-id="9c3b4-155">預設值為 "3.0"。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-155">The default value is "3.0".</span></span>

<span data-ttu-id="9c3b4-156">如果未安裝 PowerShell 3.0，唯一有效的值為 "2.0"。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-156">If PowerShell 3.0 isn't installed, the only valid value is "2.0".</span></span> <span data-ttu-id="9c3b4-157">其他值會被忽略。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-157">Other values are ignored.</span></span>

<span data-ttu-id="9c3b4-158">如需詳細資訊，請參閱[安裝 Windows PowerShell](../../setup/installing-windows-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-158">For more information, see [Installing Windows PowerShell](../../setup/installing-windows-powershell.md).</span></span>

### <a name="-windowstyle-window-style"></a><span data-ttu-id="9c3b4-159">-WindowStyle <Window style></span><span class="sxs-lookup"><span data-stu-id="9c3b4-159">-WindowStyle <Window style></span></span>

<span data-ttu-id="9c3b4-160">設定工作階段的視窗樣式。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-160">Sets the window style for the session.</span></span> <span data-ttu-id="9c3b4-161">有效值為 Normal、Minimized、Maximized 與 Hidden。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-161">Valid values are Normal, Minimized, Maximized, and Hidden.</span></span>

### <a name="-command"></a><span data-ttu-id="9c3b4-162">-Command</span><span class="sxs-lookup"><span data-stu-id="9c3b4-162">-Command</span></span>

<span data-ttu-id="9c3b4-163">執行指定的命令 (搭配任何參數)，就如同在 PowerShell 命令提示字元中輸入它們一樣。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-163">Executes the specified commands (with any parameters) as though they were typed at the PowerShell command prompt.</span></span>
<span data-ttu-id="9c3b4-164">執行之後，除非指定了 **NoExit** 參數，否則 PowerShell 就會結束。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-164">After execution, PowerShell exits unless the **NoExit** parameter is specified.</span></span>
<span data-ttu-id="9c3b4-165">`-Command` 之後的任何文字都會以單一命令列形式傳送至 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-165">Any text after `-Command` is sent as a single command line to PowerShell.</span></span>
<span data-ttu-id="9c3b4-166">這與 `-File` 處理要傳送至指令碼之參數的方法不同。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-166">This is different from how `-File` handles parameters sent to a script.</span></span>

<span data-ttu-id="9c3b4-167">`-Command` 的值可以是 "-"、字串或指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-167">The value of `-Command` can be "-", a string, or a script block.</span></span>
<span data-ttu-id="9c3b4-168">命令的結果會當做已還原序列化的 XML 物件 (而不是即時物件) 傳回到父殼層。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-168">The results of the command are returned to the parent shell as deserialized XML objects, not live objects.</span></span>

<span data-ttu-id="9c3b4-169">如果 `-Command` 的值是 "-"，則會從標準輸入讀取命令文字。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-169">If the value of `-Command` is "-", the command text is read from standard input.</span></span>

<span data-ttu-id="9c3b4-170">當 `-Command` 的值是字串時，**Command**「必須」是指定的最後一個參數，因為在命令後輸入的任何字元皆會解譯為命令引數。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-170">When the value of `-Command` is a string, **Command** _must_ be the last parameter specified because any characters typed after the command are interpreted as the command arguments.</span></span>

<span data-ttu-id="9c3b4-171">**Command** 參數只會在它可將傳遞給 `-Command` 的值辨識為 ScriptBlock 類型時，接受指令碼區塊執行。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-171">The **Command** parameter only accepts a script block for execution when it can recognize the value passed to `-Command` as a ScriptBlock type.</span></span>
<span data-ttu-id="9c3b4-172">這「只有」在從另一部 PowerShell 主機執行 PowerShell.exe 時才可行。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-172">This is _only_ possible when running PowerShell.exe from another PowerShell host.</span></span>
<span data-ttu-id="9c3b4-173">ScriptBlock 類型可能包含於現有的變數中、從運算式傳回，或透過 PowerShell 主機剖析為常值指令碼區塊 (以大括號 `{}` 括住)，之後才能傳遞給 PowerShell.exe。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-173">The ScriptBlock type may be contained in an existing variable, returned from an expression, or parsed by the PowerShell host as a literal script block enclosed in curly braces `{}`, before being passed to PowerShell.exe.</span></span>

<span data-ttu-id="9c3b4-174">在 cmd.exe 中，沒有指令碼區塊 (或 ScriptBlock 類型) 之類的項目，因此傳遞給 **Command** 的值將「一律」為字串。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-174">In cmd.exe, there is no such thing as a script block (or ScriptBlock type), so the value passed to **Command** will _always_ be a string.</span></span>
<span data-ttu-id="9c3b4-175">您可以在字串內撰寫指令碼區塊，但它不會執行，其行為完全就像您在一般 PowerShell 提示字元中輸入它一樣，將指令碼區塊的內容印回給您。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-175">You can write a script block inside the string, but instead of being executed it will behave exactly as though you typed it at a typical PowerShell prompt, printing the contents of the script block back out to you.</span></span>

<span data-ttu-id="9c3b4-176">傳遞給 `-Command` 的字串仍會以 PowerShell 執行，因此，一開始從 cmd.exe 執行時通常不需要指令碼區塊大括號。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-176">A string passed to `-Command` will still be executed as PowerShell, so the script block curly braces are often not required in the first place when running from cmd.exe.</span></span>
<span data-ttu-id="9c3b4-177">若要執行字串內定義的內嵌指令碼區塊，可以使用[呼叫運算子](/powershell/module/microsoft.powershell.core/about/about_operators#call-operator-)`&`：</span><span class="sxs-lookup"><span data-stu-id="9c3b4-177">To execute an inline script block defined inside a string, the [call operator](/powershell/module/microsoft.powershell.core/about/about_operators#call-operator-) `&` can be used:</span></span>

```console
"& {<command>}"
```

### <a name="-help---"></a><span data-ttu-id="9c3b4-178">-Help, -?, /?</span><span class="sxs-lookup"><span data-stu-id="9c3b4-178">-Help, -?, /?</span></span>

<span data-ttu-id="9c3b4-179">顯示 powershell.exe 的語法。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-179">Shows the syntax of powershell.exe.</span></span> <span data-ttu-id="9c3b4-180">若要在 PowerShell 中鍵入 PowerShell.exe 命令，命令參數之前要加上連字號 (-)，而不是正斜線 (/)。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-180">If you are typing a PowerShell.exe command in PowerShell, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="9c3b4-181">在 Cmd.exe 中，您可以使用連字號或正斜線。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-181">You can use either a hyphen or forward slash in Cmd.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="9c3b4-182">疑難排解注意事項：在 PowerShell 2.0，於 Windows PowerShell 主控台中啟動某些程式會失敗，LastExitCode 為 0xc0000142。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-182">Troubleshooting Note: In PowerShell 2.0, starting some programs in the Windows PowerShell console fails with a LastExitCode of 0xc0000142.</span></span>

## <a name="examples"></a><span data-ttu-id="9c3b4-183">範例</span><span class="sxs-lookup"><span data-stu-id="9c3b4-183">EXAMPLES</span></span>

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
