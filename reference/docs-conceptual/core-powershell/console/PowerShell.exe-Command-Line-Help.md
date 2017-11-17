---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "PowerShell.exe 命令列說明"
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: c2583dac14f32db414f0a4377b1694ab7fa7523b
ms.sourcegitcommit: cd66d4f49ea762a31887af2c72d087b219ddbe10
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/11/2017
---
# <a name="powershellexe-command-line-help"></a><span data-ttu-id="bd5b5-103">PowerShell.exe 命令列說明</span><span class="sxs-lookup"><span data-stu-id="bd5b5-103">PowerShell.exe Command-Line Help</span></span>
<span data-ttu-id="bd5b5-104">啟動 Windows PowerShell 工作階段。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-104">Starts a Windows PowerShell session.</span></span> <span data-ttu-id="bd5b5-105">您可以使用 PowerShell.exe 從其他工具的命令列 (例如 Cmd.exe) 啟動 Windows PowerShell 工作階段，或在 Windows PowerShell 命令列中使用以啟動新的工作階段。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-105">You can use PowerShell.exe to start a Windows PowerShell session from the command line of another tool, such as Cmd.exe, or use it at the Windows PowerShell command line to start a new session.</span></span> <span data-ttu-id="bd5b5-106">使用參數可自訂工作階段。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-106">Use the parameters to customize the session.</span></span>

## <a name="syntax"></a><span data-ttu-id="bd5b5-107">語法</span><span class="sxs-lookup"><span data-stu-id="bd5b5-107">Syntax</span></span>

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
       [-PSConsoleFile <FilePath> | -Version <Windows PowerShell version>]
       [-Sta]
       [-WindowStyle <style>]
        

PowerShell[.exe] -Help | -? | /?
```

## <a name="parameters"></a><span data-ttu-id="bd5b5-108">參數</span><span class="sxs-lookup"><span data-stu-id="bd5b5-108">Parameters</span></span>

### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="bd5b5-109">-EncodedCommand <Base64EncodedCommand></span><span class="sxs-lookup"><span data-stu-id="bd5b5-109">-EncodedCommand <Base64EncodedCommand></span></span>
<span data-ttu-id="bd5b5-110">接受 Base-64 編碼字串版本的命令。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-110">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="bd5b5-111">使用此參數送出命令至要求要有複雜引號或大括弧的 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-111">Use this parameter to submit commands to Windows PowerShell that require complex quotation marks or curly braces.</span></span>

### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="bd5b5-112">-ExecutionPolicy <ExecutionPolicy></span><span class="sxs-lookup"><span data-stu-id="bd5b5-112">-ExecutionPolicy <ExecutionPolicy></span></span>
<span data-ttu-id="bd5b5-113">設定目前工作階段的預設執行原則並且儲存至 $env:PSExecutionPolicyPreference 環境變數中。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-113">Sets the default execution policy for the current session and saves it in the $env:PSExecutionPolicyPreference environment variable.</span></span> <span data-ttu-id="bd5b5-114">此參數不會變更已在登錄中設定的 Windows PowerShell 執行原則。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-114">This parameter does not change the Windows PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="bd5b5-115">如需 Windows PowerShell 執行原則的資訊，包括有效值清單，請參閱 about_Execution_Policies (http://go.microsoft.com/fwlink/?LinkID=135170)。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-115">For information about Windows PowerShell execution policies, including a list of valid values, see about_Execution_Policies (http://go.microsoft.com/fwlink/?LinkID=135170).</span></span>

### <a name="-file-filepath-parameters"></a><span data-ttu-id="bd5b5-116">-File <FilePath> \[<Parameters>]</span><span class="sxs-lookup"><span data-stu-id="bd5b5-116">-File <FilePath> \[<Parameters>]</span></span>
<span data-ttu-id="bd5b5-117">在本機領域 (「點來源」) 執行指定指令碼，讓指令碼建立的函式和變數在目前的工作階段可用。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-117">Runs the specified script in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="bd5b5-118">輸入指令碼檔案路徑和任何參數。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-118">Enter the script file path and any parameters.</span></span> <span data-ttu-id="bd5b5-119">**File** 必須是命令中的最後一個參數，因為在 **File** 參數名稱後輸入的所有字元，會解譯為後面加上指令碼參數及其值的指令碼檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-119">**File** must be the last parameter in the command, because all characters typed after the **File** parameter name are interpreted as the script file path followed by the script parameters and their values.</span></span>

<span data-ttu-id="bd5b5-120">您可以將指令碼的參數和參數值包含在 **File** 參數的值中。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-120">You can include the parameters of a script, and parameter values, in the value of the **File** parameter.</span></span> <span data-ttu-id="bd5b5-121">例如：`-File .\Get-Script.ps1 -Domain Central`。請注意，參數會以常值字串形式 (經過目前的殼層解譯後) 傳遞至指令碼。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-121">For example: `-File .\Get-Script.ps1 -Domain Central` Note that parameters passed to the script are passed as literal strings (after interpretation by the current shell).</span></span>
<span data-ttu-id="bd5b5-122">舉例來說，如果您想要在 cmd.exe 中傳遞環境變數值，應使用 cmd.exe 語法：`powershell -File .\test.ps1 -Sample %windir%`。反之，若您在此範例中使用 PowerShell 語法，則會收到 "$env:windir" 常值，而非該環境變數的值：`powershell -File .\test.ps1 -Sample $env:windir`</span><span class="sxs-lookup"><span data-stu-id="bd5b5-122">For example, if you are in cmd.exe and want to pass an environment variable value, you would use the cmd.exe syntax: `powershell -File .\test.ps1 -Sample %windir%` If you were to use PowerShell syntax, then in this example your script would receive the literal "$env:windir" and not the value of that environmental variable: `powershell -File .\test.ps1 -Sample $env:windir`</span></span>

<span data-ttu-id="bd5b5-123">一般而言，指令碼的切換參數可以包含或省略。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-123">Typically, the switch parameters of a script are either included or omitted.</span></span> <span data-ttu-id="bd5b5-124">例如，下列命令會使用 Get-Script.ps1 指令碼檔案的 **All** 參數：`-File .\Get-Script.ps1 -All`</span><span class="sxs-lookup"><span data-stu-id="bd5b5-124">For example, the following command uses the **All** parameter of the Get-Script.ps1 script file: `-File .\Get-Script.ps1 -All`</span></span>

### <a name="-inputformat-text--xml"></a><span data-ttu-id="bd5b5-125">\-InputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="bd5b5-125">\-InputFormat {Text | XML}</span></span>
<span data-ttu-id="bd5b5-126">描述傳送至 Windows PowerShell 的資料格式。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-126">Describes the format of data sent to Windows PowerShell.</span></span> <span data-ttu-id="bd5b5-127">有效值為 "Text" (文字字串) 或 "XML" (序列化的 CLIXML 格式)。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-127">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-mta"></a><span data-ttu-id="bd5b5-128">-Mta</span><span class="sxs-lookup"><span data-stu-id="bd5b5-128">-Mta</span></span>
<span data-ttu-id="bd5b5-129">使用多執行緒 Apartment 啟動 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-129">Starts Windows PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="bd5b5-130">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-130">This parameter is introduced in Windows PowerShell 3.0.</span></span> <span data-ttu-id="bd5b5-131">在 Windows PowerShell 3.0 中，單一執行緒 Apartment (STA) 是預設值。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-131">In Windows PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="bd5b5-132">在 Windows PowerShell 2.0 中，多執行緒 Apartment (MTA) 是預設值。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-132">In Windows PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-noexit"></a><span data-ttu-id="bd5b5-133">-NoExit</span><span class="sxs-lookup"><span data-stu-id="bd5b5-133">-NoExit</span></span>
<span data-ttu-id="bd5b5-134">執行啟動命令後不要結束。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-134">Does not exit after running startup commands.</span></span>

### <a name="-nologo"></a><span data-ttu-id="bd5b5-135">-NoLogo</span><span class="sxs-lookup"><span data-stu-id="bd5b5-135">-NoLogo</span></span>
<span data-ttu-id="bd5b5-136">啟動時隱藏著作權橫幅。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-136">Hides the copyright banner at startup.</span></span>

### <a name="-noninteractive"></a><span data-ttu-id="bd5b5-137">-NonInteractive</span><span class="sxs-lookup"><span data-stu-id="bd5b5-137">-NonInteractive</span></span>
<span data-ttu-id="bd5b5-138">不向使用者顯示互動式提示。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-138">Does not present an interactive prompt to the user.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="bd5b5-139">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="bd5b5-139">-NoProfile</span></span>
<span data-ttu-id="bd5b5-140">不載入 Windows PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-140">Does not load the Windows PowerShell profile.</span></span>

### <a name="-outputformat-text--xml"></a><span data-ttu-id="bd5b5-141">-OutputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="bd5b5-141">-OutputFormat {Text | XML}</span></span>
<span data-ttu-id="bd5b5-142">決定 Windows PowerShell 的輸出格式。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-142">Determines how output from Windows PowerShell is formatted.</span></span> <span data-ttu-id="bd5b5-143">有效值為 "Text" (文字字串) 或 "XML" (序列化的 CLIXML 格式)。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-143">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-psconsolefile-filepath"></a><span data-ttu-id="bd5b5-144">-PSConsoleFile <FilePath></span><span class="sxs-lookup"><span data-stu-id="bd5b5-144">-PSConsoleFile <FilePath></span></span>
<span data-ttu-id="bd5b5-145">載入指定的 Windows PowerShell 主控台檔案。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-145">Loads the specified Windows PowerShell console file.</span></span> <span data-ttu-id="bd5b5-146">輸入主控台檔案的路徑和名稱。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-146">Enter the path and name of the console file.</span></span> <span data-ttu-id="bd5b5-147">若要建立主控台檔案，請在 Windows PowerShell 中使用 [Export-Console](https://technet.microsoft.com/en-us/library/4bab1c02-9e61-4aaf-9957-11d1934ef4ef) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-147">To create a console file, use the [Export-Console](https://technet.microsoft.com/en-us/library/4bab1c02-9e61-4aaf-9957-11d1934ef4ef) cmdlet in Windows PowerShell.</span></span>

### <a name="-sta"></a><span data-ttu-id="bd5b5-148">-Sta</span><span class="sxs-lookup"><span data-stu-id="bd5b5-148">-Sta</span></span>
<span data-ttu-id="bd5b5-149">使用單一執行緒 Apartment 啟動 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-149">Starts Windows PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="bd5b5-150">在 Windows PowerShell 3.0 中，單一執行緒 Apartment (STA) 是預設值。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-150">In Windows PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="bd5b5-151">在 Windows PowerShell 2.0 中，多執行緒 Apartment (MTA) 是預設值。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-151">In Windows PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-version-windows-powershell-version"></a><span data-ttu-id="bd5b5-152">-Version <Windows PowerShell Version></span><span class="sxs-lookup"><span data-stu-id="bd5b5-152">-Version <Windows PowerShell Version></span></span>
<span data-ttu-id="bd5b5-153">啟動指定的 Windows PowerShell 版本。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-153">Starts the specified version of Windows PowerShell.</span></span> <span data-ttu-id="bd5b5-154">您指定的版本必須安裝在系統上。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-154">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="bd5b5-155">如果 Windows PowerShell 3.0 已安裝於電腦上，有效值為 "2.0" 和 "3.0"。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-155">If Windows PowerShell 3.0 is installed on the computer, valid values are "2.0" and "3.0".</span></span> <span data-ttu-id="bd5b5-156">預設值為 "3.0"。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-156">The default value is "3.0".</span></span>

<span data-ttu-id="bd5b5-157">如果未安裝 Windows PowerShell 3.0，唯一有效的值為 "2.0"。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-157">If Windows PowerShell 3.0 is not installed, the only valid value is "2.0".</span></span> <span data-ttu-id="bd5b5-158">其他值會被忽略。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-158">Other values are ignored.</span></span>

<span data-ttu-id="bd5b5-159">如需詳細資訊，請參閱[開始使用 Windows PowerShell [舊版 MSDN]](https://technet.microsoft.com/en-us/library/69555d95-b481-43e1-86e7-b46d68b3e2dd)中的＜安裝 Windows PowerShell＞。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-159">For more information, see "Installing Windows PowerShell" in the [Getting Started with Windows PowerShell [OLD MSDN]](https://technet.microsoft.com/en-us/library/69555d95-b481-43e1-86e7-b46d68b3e2dd).</span></span>

### <a name="-windowstyle-window-style"></a><span data-ttu-id="bd5b5-160">-WindowStyle <Window style></span><span class="sxs-lookup"><span data-stu-id="bd5b5-160">-WindowStyle <Window style></span></span>
<span data-ttu-id="bd5b5-161">設定工作階段的視窗樣式。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-161">Sets the window style for the session.</span></span> <span data-ttu-id="bd5b5-162">有效值為 Normal、Minimized、Maximized 和 Hidden。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-162">Valid values are Normal, Minimized, Maximized and Hidden.</span></span>

### <a name="-command"></a><span data-ttu-id="bd5b5-163">-Command</span><span class="sxs-lookup"><span data-stu-id="bd5b5-163">-Command</span></span>
<span data-ttu-id="bd5b5-164">就如同在 Windows PowerShell 命令提示字元輸入一樣，執行指定的命令 (和任何參數)，然後結束，除非指定了 NoExit 參數。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-164">Executes the specified commands (and any parameters) as though they were typed at the Windows PowerShell command prompt, and then exits, unless the NoExit parameter is specified.</span></span>
<span data-ttu-id="bd5b5-165">基本上，任何在 `-Command` 之後的文字都會作為單一命令列傳送至 PowerShell，這與 `-File` 處理傳送至指令碼之參數的方法不同。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-165">Essentially, any text after `-Command` is sent as a single command line to PowerShell (this is different from how `-File` handles parameters sent to a script).</span></span>

<span data-ttu-id="bd5b5-166">Command 的值可以是 "-"、字串。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-166">The value of Command can be "-", a string.</span></span> <span data-ttu-id="bd5b5-167">或指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-167">or a script block.</span></span> <span data-ttu-id="bd5b5-168">如果 Command 的值是 "-"，則會從標準輸入讀取命令文字。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-168">If the value of Command is "-", the command text is read from standard input.</span></span>

<span data-ttu-id="bd5b5-169">指令碼區塊必須以大括弧 ({}) 括住。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-169">Script blocks must be enclosed in braces ({}).</span></span> <span data-ttu-id="bd5b5-170">只有在 Windows PowerShell 中執行 PowerShell.exe 時，您才可以指定指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-170">You can specify a script block only when running PowerShell.exe in Windows PowerShell.</span></span> <span data-ttu-id="bd5b5-171">指令碼的結果會當做已還原序列化的 XML 物件 (而不是即時物件) 傳回到父殼層。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-171">The results of the script are returned to the parent shell as deserialized XML objects, not live objects.</span></span>

<span data-ttu-id="bd5b5-172">如果 Command 的值是字串，因為在命令後輸入的任何字元皆會解譯為命令引數，所以 **Command** 必須是命令中的最後一個參數。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-172">If the value of Command is a string, **Command** must be the last parameter in the command, because any characters typed after the command are interpreted as the command arguments.</span></span>

<span data-ttu-id="bd5b5-173">若要寫入執行 Windows PowerShell 命令的字串，請使用下列格式︰</span><span class="sxs-lookup"><span data-stu-id="bd5b5-173">To write a string that runs a Windows PowerShell command, use the format:</span></span>

```
"& {<command>}"
```

<span data-ttu-id="bd5b5-174">其中的引號代表字串，它會呼叫 (&) 運算子，使命令執行。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-174">where the quotation marks indicate a string and the invoke operator (&) causes the command to be executed.</span></span>

### <a name="-help---"></a><span data-ttu-id="bd5b5-175">-Help, -?, /?</span><span class="sxs-lookup"><span data-stu-id="bd5b5-175">-Help, -?, /?</span></span>
<span data-ttu-id="bd5b5-176">顯示此訊息。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-176">Shows this message.</span></span> <span data-ttu-id="bd5b5-177">如果您正在 Windows PowerShell 中輸入 PowerShell.exe 命令，命令參數之前要加上連字號 (-)，而不是正斜線 (/)。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-177">If you are typing a PowerShell.exe command in Windows PowerShell, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="bd5b5-178">在 Cmd.exe 中，您可以使用連字號或正斜線。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-178">You can use either a hyphen or forward slash in Cmd.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="bd5b5-179">疑難排解注意事項︰在 Windows PowerShell 2.0 中，啟動 Windows PowerShell 主控台中的某些程式會失敗，LastExitCode 為 0xc0000142。</span><span class="sxs-lookup"><span data-stu-id="bd5b5-179">Troubleshooting Note: In Windows PowerShell 2.0, starting some programs in the Windows PowerShell console fails with a LastExitCode of 0xc0000142.</span></span>

## <a name="examples"></a><span data-ttu-id="bd5b5-180">範例</span><span class="sxs-lookup"><span data-stu-id="bd5b5-180">EXAMPLES</span></span>

```
# Create a new PowerShell session and load a saved console file
PowerShell -PSConsoleFile sqlsnapin.psc1

# Create a new PowerShell V2 session with text input, XML output, and no logo
PowerShell -Version 2.0 -NoLogo -InputFormat text -OutputFormat XML

# Execute a Powerhell Command in a session
PowerShell -Command "Get-EventLog -LogName security"

# Run a script block in a session
PowerShell -Command {Get-EventLog -LogName security}

# An alternate wayh to run a command in a new session
PowerShell -Command "& {Get-EventLog -LogName security}"

# To use the -EncodedCommand parameter:
$command = "dir 'c:\program files' "
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
powershell.exe -encodedCommand $encodedCommand
```

