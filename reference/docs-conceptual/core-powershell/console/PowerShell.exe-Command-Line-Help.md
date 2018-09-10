---
ms.date: 08/14/2018
keywords: powershell,cmdlet
title: PowerShell.exe 命令列說明
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: c7f35511e876e8e5189d8a2b949555603d43f731
ms.sourcegitcommit: 56b9be8503a5a1342c0b85b36f5ba6f57c281b63
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2018
ms.locfileid: "43133080"
---
# <a name="powershellexe-command-line-help"></a><span data-ttu-id="55f41-103">PowerShell.exe 命令列說明</span><span class="sxs-lookup"><span data-stu-id="55f41-103">PowerShell.exe Command-Line Help</span></span>

<span data-ttu-id="55f41-104">您可以使用 PowerShell.exe 從其他工具的命令列 (例如 Cmd.exe) 啟動 PowerShell 工作階段，或在 PowerShell 命令列中使用以啟動新的工作階段。</span><span class="sxs-lookup"><span data-stu-id="55f41-104">You can use PowerShell.exe to start a PowerShell session from the command line of another tool, such as Cmd.exe, or use it at the PowerShell command line to start a new session.</span></span> <span data-ttu-id="55f41-105">使用參數可自訂工作階段。</span><span class="sxs-lookup"><span data-stu-id="55f41-105">Use the parameters to customize the session.</span></span>

## <a name="syntax"></a><span data-ttu-id="55f41-106">語法</span><span class="sxs-lookup"><span data-stu-id="55f41-106">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="55f41-107">參數</span><span class="sxs-lookup"><span data-stu-id="55f41-107">Parameters</span></span>

### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="55f41-108">-EncodedCommand <Base64EncodedCommand></span><span class="sxs-lookup"><span data-stu-id="55f41-108">-EncodedCommand <Base64EncodedCommand></span></span>

<span data-ttu-id="55f41-109">接受 Base-64 編碼字串版本的命令。</span><span class="sxs-lookup"><span data-stu-id="55f41-109">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="55f41-110">使用此參數以將命令傳送至要求複雜引號或大括弧的 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="55f41-110">Use this parameter to submit commands to PowerShell that require complex quotation marks or curly braces.</span></span>

### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="55f41-111">-ExecutionPolicy <ExecutionPolicy></span><span class="sxs-lookup"><span data-stu-id="55f41-111">-ExecutionPolicy <ExecutionPolicy></span></span>

<span data-ttu-id="55f41-112">設定目前工作階段的預設執行原則並且儲存至 $env:PSExecutionPolicyPreference 環境變數中。</span><span class="sxs-lookup"><span data-stu-id="55f41-112">Sets the default execution policy for the current session and saves it in the $env:PSExecutionPolicyPreference environment variable.</span></span> <span data-ttu-id="55f41-113">此參數不會變更已在登錄中設定的 PowerShell 執行原則。</span><span class="sxs-lookup"><span data-stu-id="55f41-113">This parameter doesn't change the PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="55f41-114">如需 PowerShell 執行原則的資訊，包括有效值清單，請參閱 [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies)。</span><span class="sxs-lookup"><span data-stu-id="55f41-114">For information about PowerShell execution policies, including a list of valid values, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

### <a name="-file-filepath-parameters"></a><span data-ttu-id="55f41-115">-File <FilePath> \[<Parameters>]</span><span class="sxs-lookup"><span data-stu-id="55f41-115">-File <FilePath> \[<Parameters>]</span></span>

<span data-ttu-id="55f41-116">在本機領域 (「點來源」) 執行指定指令碼，讓指令碼建立的函式和變數在目前的工作階段可用。</span><span class="sxs-lookup"><span data-stu-id="55f41-116">Runs the specified script in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="55f41-117">輸入指令碼檔案路徑和任何參數。</span><span class="sxs-lookup"><span data-stu-id="55f41-117">Enter the script file path and any parameters.</span></span> <span data-ttu-id="55f41-118">**File** 必須是命令中的最後一個參數。</span><span class="sxs-lookup"><span data-stu-id="55f41-118">**File** must be the last parameter in the command.</span></span> <span data-ttu-id="55f41-119">在 **-File** 參數之後輸入的所有值都會解譯為指令碼檔案路徑以及要傳遞給該指令碼的參數。</span><span class="sxs-lookup"><span data-stu-id="55f41-119">All values typed after the **-File** parameter are interpreted as the script file path and parameters passed to that script.</span></span>

<span data-ttu-id="55f41-120">參數會以常值字串形式 (經過目前的殼層解譯後) 傳遞至指令碼。</span><span class="sxs-lookup"><span data-stu-id="55f41-120">Parameters passed to the script are passed as literal strings (after interpretation by the current shell).</span></span> <span data-ttu-id="55f41-121">例如，如果您想要在 cmd.exe 中傳遞環境變數值，應使用 cmd.exe 語法：`powershell -File .\test.ps1 -Sample %windir%`。在此範例中，指令碼會接收到常值字串 `$env:windir`，而非該環境變數的值：`powershell -File .\test.ps1 -Sample $env:windir`</span><span class="sxs-lookup"><span data-stu-id="55f41-121">For example, if you are in cmd.exe and want to pass an environment variable value, you would use the cmd.exe syntax: `powershell -File .\test.ps1 -Sample %windir%` In this example, the script receives the literal string `$env:windir` and not the value of that environmental variable: `powershell -File .\test.ps1 -Sample $env:windir`</span></span>

### <a name="-inputformat-text--xml"></a><span data-ttu-id="55f41-122">\-InputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="55f41-122">\-InputFormat {Text | XML}</span></span>

<span data-ttu-id="55f41-123">描述傳送至 PowerShell 的資料格式。</span><span class="sxs-lookup"><span data-stu-id="55f41-123">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="55f41-124">有效值為 "Text" (文字字串) 或 "XML" (序列化的 CLIXML 格式)。</span><span class="sxs-lookup"><span data-stu-id="55f41-124">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-mta"></a><span data-ttu-id="55f41-125">-Mta</span><span class="sxs-lookup"><span data-stu-id="55f41-125">-Mta</span></span>

<span data-ttu-id="55f41-126">使用多執行緒 Apartment 啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="55f41-126">Starts PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="55f41-127">此參數在 PowerShell 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="55f41-127">This parameter is introduced in PowerShell 3.0.</span></span> <span data-ttu-id="55f41-128">在 PowerShell 3.0 中，預設為單一執行緒 Apartment (STA)。</span><span class="sxs-lookup"><span data-stu-id="55f41-128">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="55f41-129">在 PowerShell 2.0 中，預設為多執行緒 Apartment (MTA)。</span><span class="sxs-lookup"><span data-stu-id="55f41-129">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-noexit"></a><span data-ttu-id="55f41-130">-NoExit</span><span class="sxs-lookup"><span data-stu-id="55f41-130">-NoExit</span></span>

<span data-ttu-id="55f41-131">執行啟動命令後不要結束。</span><span class="sxs-lookup"><span data-stu-id="55f41-131">Doesn't exit after running startup commands.</span></span>

### <a name="-nologo"></a><span data-ttu-id="55f41-132">-NoLogo</span><span class="sxs-lookup"><span data-stu-id="55f41-132">-NoLogo</span></span>

<span data-ttu-id="55f41-133">啟動時隱藏著作權橫幅。</span><span class="sxs-lookup"><span data-stu-id="55f41-133">Hides the copyright banner at startup.</span></span>

### <a name="-noninteractive"></a><span data-ttu-id="55f41-134">-NonInteractive</span><span class="sxs-lookup"><span data-stu-id="55f41-134">-NonInteractive</span></span>

<span data-ttu-id="55f41-135">不向使用者顯示互動式提示。</span><span class="sxs-lookup"><span data-stu-id="55f41-135">Doesn't present an interactive prompt to the user.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="55f41-136">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="55f41-136">-NoProfile</span></span>

<span data-ttu-id="55f41-137">不載入 PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="55f41-137">Doesn't load the PowerShell profile.</span></span>

### <a name="-outputformat-text--xml"></a><span data-ttu-id="55f41-138">-OutputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="55f41-138">-OutputFormat {Text | XML}</span></span>

<span data-ttu-id="55f41-139">決定 PowerShell 的輸出格式。</span><span class="sxs-lookup"><span data-stu-id="55f41-139">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="55f41-140">有效值為 "Text" (文字字串) 或 "XML" (序列化的 CLIXML 格式)。</span><span class="sxs-lookup"><span data-stu-id="55f41-140">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-psconsolefile-filepath"></a><span data-ttu-id="55f41-141">-PSConsoleFile <FilePath></span><span class="sxs-lookup"><span data-stu-id="55f41-141">-PSConsoleFile <FilePath></span></span>

<span data-ttu-id="55f41-142">載入指定的 PowerShell 主控台檔案。</span><span class="sxs-lookup"><span data-stu-id="55f41-142">Loads the specified PowerShell console file.</span></span> <span data-ttu-id="55f41-143">輸入主控台檔案的路徑和名稱。</span><span class="sxs-lookup"><span data-stu-id="55f41-143">Enter the path and name of the console file.</span></span> <span data-ttu-id="55f41-144">若要建立主控台檔案，請在 PowerShell 中使用 [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="55f41-144">To create a console file, use the [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet in PowerShell.</span></span>

### <a name="-sta"></a><span data-ttu-id="55f41-145">-Sta</span><span class="sxs-lookup"><span data-stu-id="55f41-145">-Sta</span></span>

<span data-ttu-id="55f41-146">使用單一執行緒 Apartment 啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="55f41-146">Starts PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="55f41-147">在 PowerShell 3.0 中，預設為單一執行緒 Apartment (STA)。</span><span class="sxs-lookup"><span data-stu-id="55f41-147">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="55f41-148">在 PowerShell 2.0 中，預設為多執行緒 Apartment (MTA)。</span><span class="sxs-lookup"><span data-stu-id="55f41-148">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-version-powershell-version"></a><span data-ttu-id="55f41-149">-Version <PowerShell Version></span><span class="sxs-lookup"><span data-stu-id="55f41-149">-Version <PowerShell Version></span></span>

<span data-ttu-id="55f41-150">啟動指定版本的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="55f41-150">Starts the specified version of PowerShell.</span></span> <span data-ttu-id="55f41-151">您指定的版本必須安裝在系統上。</span><span class="sxs-lookup"><span data-stu-id="55f41-151">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="55f41-152">如果 PowerShell 3.0 已安裝於電腦上，有效值為 "2.0" 和 "3.0"。</span><span class="sxs-lookup"><span data-stu-id="55f41-152">If PowerShell 3.0 is installed on the computer, valid values are "2.0" and "3.0".</span></span> <span data-ttu-id="55f41-153">預設值為 "3.0"。</span><span class="sxs-lookup"><span data-stu-id="55f41-153">The default value is "3.0".</span></span>

<span data-ttu-id="55f41-154">如果未安裝 PowerShell 3.0，唯一有效的值為 "2.0"。</span><span class="sxs-lookup"><span data-stu-id="55f41-154">If PowerShell 3.0 isn't installed, the only valid value is "2.0".</span></span> <span data-ttu-id="55f41-155">其他值會被忽略。</span><span class="sxs-lookup"><span data-stu-id="55f41-155">Other values are ignored.</span></span>

<span data-ttu-id="55f41-156">如需詳細資訊，請參閱[安裝 Windows PowerShell](../../setup/installing-windows-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="55f41-156">For more information, see [Installing Windows PowerShell](../../setup/installing-windows-powershell.md).</span></span>

### <a name="-windowstyle-window-style"></a><span data-ttu-id="55f41-157">-WindowStyle <Window style></span><span class="sxs-lookup"><span data-stu-id="55f41-157">-WindowStyle <Window style></span></span>

<span data-ttu-id="55f41-158">設定工作階段的視窗樣式。</span><span class="sxs-lookup"><span data-stu-id="55f41-158">Sets the window style for the session.</span></span> <span data-ttu-id="55f41-159">有效值為 Normal、Minimized、Maximized 與 Hidden。</span><span class="sxs-lookup"><span data-stu-id="55f41-159">Valid values are Normal, Minimized, Maximized, and Hidden.</span></span>

### <a name="-command"></a><span data-ttu-id="55f41-160">-Command</span><span class="sxs-lookup"><span data-stu-id="55f41-160">-Command</span></span>

<span data-ttu-id="55f41-161">執行指定的命令 (搭配任何參數)，就如同在 PowerShell 命令提示字元中輸入它們一樣。</span><span class="sxs-lookup"><span data-stu-id="55f41-161">Executes the specified commands (with any parameters) as though they were typed at the PowerShell command prompt.</span></span> <span data-ttu-id="55f41-162">執行之後，除非指定了 `-NoExit` 參數，否則 PowerShell 就會結束。</span><span class="sxs-lookup"><span data-stu-id="55f41-162">After execution, PowerShell exits unless the `-NoExit` parameter is specified.</span></span>
<span data-ttu-id="55f41-163">`-Command` 之後的任何文字都會以單一命令列形式傳送至 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="55f41-163">Any text after `-Command` is sent as a single command line to PowerShell.</span></span> <span data-ttu-id="55f41-164">這與 `-File` 處理要傳送至指令碼之參數的方法不同。</span><span class="sxs-lookup"><span data-stu-id="55f41-164">This is different from how `-File` handles parameters sent to a script.</span></span>

<span data-ttu-id="55f41-165">Command 的值可以是 "-"、字串。</span><span class="sxs-lookup"><span data-stu-id="55f41-165">The value of Command can be "-", a string.</span></span> <span data-ttu-id="55f41-166">或指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="55f41-166">or a script block.</span></span> <span data-ttu-id="55f41-167">如果 Command 的值是 "-"，則會從標準輸入讀取命令文字。</span><span class="sxs-lookup"><span data-stu-id="55f41-167">If the value of Command is "-", the command text is read from standard input.</span></span>

<span data-ttu-id="55f41-168">指令碼區塊必須以大括弧 ({}) 括住。</span><span class="sxs-lookup"><span data-stu-id="55f41-168">Script blocks must be enclosed in braces ({}).</span></span> <span data-ttu-id="55f41-169">只有在 PowerShell 中執行 PowerShell.exe 時，才可以指定指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="55f41-169">You can specify a script block only when running PowerShell.exe in PowerShell.</span></span> <span data-ttu-id="55f41-170">指令碼的結果會當做已還原序列化的 XML 物件 (而不是即時物件) 傳回到父殼層。</span><span class="sxs-lookup"><span data-stu-id="55f41-170">The results of the script are returned to the parent shell as deserialized XML objects, not live objects.</span></span>

<span data-ttu-id="55f41-171">如果 Command 的值是字串，因為在命令後輸入的任何字元皆會解譯為命令引數，所以 **Command** 必須是命令中的最後一個參數。</span><span class="sxs-lookup"><span data-stu-id="55f41-171">If the value of Command is a string, **Command** must be the last parameter in the command, because any characters typed after the command are interpreted as the command arguments.</span></span>

<span data-ttu-id="55f41-172">若要編寫執行 Windows PowerShell 命令的字串，請使用下列格式：</span><span class="sxs-lookup"><span data-stu-id="55f41-172">To write a string that runs a PowerShell command, use the format:</span></span>

```powershell
"& {<command>}"
```

<span data-ttu-id="55f41-173">引號代表字串，而叫用運算子 (&) 會導致命令執行。</span><span class="sxs-lookup"><span data-stu-id="55f41-173">The quotation marks indicate a string and the invoke operator (&) causes the command to be executed.</span></span>

### <a name="-help---"></a><span data-ttu-id="55f41-174">-Help, -?, /?</span><span class="sxs-lookup"><span data-stu-id="55f41-174">-Help, -?, /?</span></span>

<span data-ttu-id="55f41-175">顯示 powershell.exe 的語法。</span><span class="sxs-lookup"><span data-stu-id="55f41-175">Shows the syntax of powershell.exe.</span></span> <span data-ttu-id="55f41-176">若要在 PowerShell 中輸入 PowerShell.exe 命令，命令參數之前要加上連字號 (-)，而不是正斜線 (/)。</span><span class="sxs-lookup"><span data-stu-id="55f41-176">If you are typing a PowerShell.exe command in PowerShell, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="55f41-177">在 Cmd.exe 中，您可以使用連字號或正斜線。</span><span class="sxs-lookup"><span data-stu-id="55f41-177">You can use either a hyphen or forward slash in Cmd.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="55f41-178">疑難排解注意事項︰在 PowerShell 2.0 中，啟動 Windows PowerShell 主控台中的某些程式會失敗，LastExitCode 為 0xc0000142。</span><span class="sxs-lookup"><span data-stu-id="55f41-178">Troubleshooting Note: In PowerShell 2.0, starting some programs in the Windows PowerShell console fails with a LastExitCode of 0xc0000142.</span></span>

## <a name="examples"></a><span data-ttu-id="55f41-179">範例</span><span class="sxs-lookup"><span data-stu-id="55f41-179">EXAMPLES</span></span>

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
