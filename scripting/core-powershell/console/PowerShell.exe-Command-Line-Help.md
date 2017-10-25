---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "PowerShell.exe 命令列說明"
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 9c56f09ac186b0c3a64cce6700740ca1ba6abd06
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2017
---
# <a name="powershellexe-command-line-help"></a><span data-ttu-id="c6eb9-103">PowerShell.exe 命令列說明</span><span class="sxs-lookup"><span data-stu-id="c6eb9-103">PowerShell.exe Command-Line Help</span></span>
<span data-ttu-id="c6eb9-104">啟動 Windows PowerShell 工作階段。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-104">Starts a Windows PowerShell session.</span></span> <span data-ttu-id="c6eb9-105">您可以使用 PowerShell.exe 從其他工具的命令列 (例如 Cmd.exe) 啟動 Windows PowerShell 工作階段，或在 Windows PowerShell 命令列中使用以啟動新的工作階段。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-105">You can use PowerShell.exe to start a Windows PowerShell session from the command line of another tool, such as Cmd.exe, or use it at the Windows PowerShell command line to start a new session.</span></span> <span data-ttu-id="c6eb9-106">使用參數可自訂工作階段。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-106">Use the parameters to customize the session.</span></span>

## <a name="syntax"></a><span data-ttu-id="c6eb9-107">語法</span><span class="sxs-lookup"><span data-stu-id="c6eb9-107">Syntax</span></span>

```
PowerShell[.exe]
       [-EncodedCommand <Base64EncodedCommand>]
       [-ExecutionPolicy <ExecutionPolicy>]
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
       [-File <FilePath> [<Args>]]
       [-Command { - | <script-block> [-args <arg-array>]
                     | <string> [<CommandParameters>] } ]

PowerShell[.exe] -Help | -? | /?
```

## <a name="parameters"></a><span data-ttu-id="c6eb9-108">參數</span><span class="sxs-lookup"><span data-stu-id="c6eb9-108">Parameters</span></span>

### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="c6eb9-109">-EncodedCommand <Base64EncodedCommand></span><span class="sxs-lookup"><span data-stu-id="c6eb9-109">-EncodedCommand <Base64EncodedCommand></span></span>
<span data-ttu-id="c6eb9-110">接受 Base-64 編碼字串版本的命令。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-110">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="c6eb9-111">使用此參數送出命令至要求要有複雜引號或大括弧的 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-111">Use this parameter to submit commands to Windows PowerShell that require complex quotation marks or curly braces.</span></span>

### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="c6eb9-112">-ExecutionPolicy <ExecutionPolicy></span><span class="sxs-lookup"><span data-stu-id="c6eb9-112">-ExecutionPolicy <ExecutionPolicy></span></span>
<span data-ttu-id="c6eb9-113">設定目前工作階段的預設執行原則並且儲存至 $env:PSExecutionPolicyPreference 環境變數中。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-113">Sets the default execution policy for the current session and saves it in the $env:PSExecutionPolicyPreference environment variable.</span></span> <span data-ttu-id="c6eb9-114">此參數不會變更已在登錄中設定的 Windows PowerShell 執行原則。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-114">This parameter does not change the Windows PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="c6eb9-115">如需 Windows PowerShell 執行原則的資訊，包括有效值清單，請參閱 about_Execution_Policies (http://go.microsoft.com/fwlink/?LinkID=135170)。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-115">For information about Windows PowerShell execution policies, including a list of valid values, see about_Execution_Policies (http://go.microsoft.com/fwlink/?LinkID=135170).</span></span>

### <a name="-file-filepath-parameters"></a><span data-ttu-id="c6eb9-116">-File <FilePath> \[<Parameters>]</span><span class="sxs-lookup"><span data-stu-id="c6eb9-116">-File <FilePath> \[<Parameters>]</span></span>
<span data-ttu-id="c6eb9-117">在本機領域 (「點來源」) 執行指定指令碼，讓指令碼建立的函式和變數在目前的工作階段可用。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-117">Runs the specified script in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="c6eb9-118">輸入指令碼檔案路徑和任何參數。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-118">Enter the script file path and any parameters.</span></span> <span data-ttu-id="c6eb9-119">**File** 必須是命令中的最後一個參數，因為在 **File** 參數名稱後輸入的所有字元，會解譯為後面加上指令碼參數及其值的指令碼檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-119">**File** must be the last parameter in the command, because all characters typed after the **File** parameter name are interpreted as the script file path followed by the script parameters and their values.</span></span>

<span data-ttu-id="c6eb9-120">您可以將指令碼的參數和參數值包含在 **File** 參數的值中。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-120">You can include the parameters of a script, and parameter values, in the value of the **File** parameter.</span></span> <span data-ttu-id="c6eb9-121">例如：`-File .\Get-Script.ps1 -Domain Central`</span><span class="sxs-lookup"><span data-stu-id="c6eb9-121">For example: `-File .\Get-Script.ps1 -Domain Central`</span></span>

<span data-ttu-id="c6eb9-122">一般而言，指令碼的切換參數可以包含或省略。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-122">Typically, the switch parameters of a script are either included or omitted.</span></span> <span data-ttu-id="c6eb9-123">例如，下列命令會使用 Get-Script.ps1 指令碼檔案的 **All** 參數：`-File .\Get-Script.ps1 -All`</span><span class="sxs-lookup"><span data-stu-id="c6eb9-123">For example, the following command uses the **All** parameter of the Get-Script.ps1 script file: `-File .\Get-Script.ps1 -All`</span></span>

<span data-ttu-id="c6eb9-124">在罕見的情況下，您可能需要提供切換參數的布林值。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-124">In rare cases, you might need to provide a Boolean value for a switch parameter.</span></span> <span data-ttu-id="c6eb9-125">若要在 **File** 參數的值中提供切換參數值的布林值，請以大括弧括住參數名稱和值，如下所示︰`-File .\Get-Script.ps1 {-All:$False}`</span><span class="sxs-lookup"><span data-stu-id="c6eb9-125">To provide a Boolean value for a switch parameter in the value of the **File** parameter, enclose the parameter name and value in curly braces, such as the following: `-File .\Get-Script.ps1 {-All:$False}`</span></span>

### <a name="-inputformat-text--xml"></a><span data-ttu-id="c6eb9-126">-InputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="c6eb9-126">-InputFormat {Text | XML}</span></span>
<span data-ttu-id="c6eb9-127">描述傳送至 Windows PowerShell 的資料格式。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-127">Describes the format of data sent to Windows PowerShell.</span></span> <span data-ttu-id="c6eb9-128">有效值為 "Text" (文字字串) 或 "XML" (序列化的 CLIXML 格式)。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-128">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-mta"></a><span data-ttu-id="c6eb9-129">-Mta</span><span class="sxs-lookup"><span data-stu-id="c6eb9-129">-Mta</span></span>
<span data-ttu-id="c6eb9-130">使用多執行緒 Apartment 啟動 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-130">Starts Windows PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="c6eb9-131">此參數是在 Windows PowerShell 3.0 引進。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-131">This parameter is introduced in Windows PowerShell 3.0.</span></span> <span data-ttu-id="c6eb9-132">在 Windows PowerShell 3.0 中，單一執行緒 Apartment (STA) 是預設值。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-132">In Windows PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="c6eb9-133">在 Windows PowerShell 2.0 中，多執行緒 Apartment (MTA) 是預設值。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-133">In Windows PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-noexit"></a><span data-ttu-id="c6eb9-134">-NoExit</span><span class="sxs-lookup"><span data-stu-id="c6eb9-134">-NoExit</span></span>
<span data-ttu-id="c6eb9-135">執行啟動命令後不要結束。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-135">Does not exit after running startup commands.</span></span>

### <a name="-nologo"></a><span data-ttu-id="c6eb9-136">-NoLogo</span><span class="sxs-lookup"><span data-stu-id="c6eb9-136">-NoLogo</span></span>
<span data-ttu-id="c6eb9-137">啟動時隱藏著作權橫幅。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-137">Hides the copyright banner at startup.</span></span>

### <a name="-noninteractive"></a><span data-ttu-id="c6eb9-138">-NonInteractive</span><span class="sxs-lookup"><span data-stu-id="c6eb9-138">-NonInteractive</span></span>
<span data-ttu-id="c6eb9-139">不向使用者顯示互動式提示。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-139">Does not present an interactive prompt to the user.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="c6eb9-140">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="c6eb9-140">-NoProfile</span></span>
<span data-ttu-id="c6eb9-141">不載入 Windows PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-141">Does not load the Windows PowerShell profile.</span></span>

### <a name="-outputformat-text--xml"></a><span data-ttu-id="c6eb9-142">-OutputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="c6eb9-142">-OutputFormat {Text | XML}</span></span>
<span data-ttu-id="c6eb9-143">決定 Windows PowerShell 的輸出格式。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-143">Determines how output from Windows PowerShell is formatted.</span></span> <span data-ttu-id="c6eb9-144">有效值為 "Text" (文字字串) 或 "XML" (序列化的 CLIXML 格式)。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-144">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-psconsolefile-filepath"></a><span data-ttu-id="c6eb9-145">-PSConsoleFile <FilePath></span><span class="sxs-lookup"><span data-stu-id="c6eb9-145">-PSConsoleFile <FilePath></span></span>
<span data-ttu-id="c6eb9-146">載入指定的 Windows PowerShell 主控台檔案。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-146">Loads the specified Windows PowerShell console file.</span></span> <span data-ttu-id="c6eb9-147">輸入主控台檔案的路徑和名稱。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-147">Enter the path and name of the console file.</span></span> <span data-ttu-id="c6eb9-148">若要建立主控台檔案，請在 Windows PowerShell 中使用 [Export-Console](https://technet.microsoft.com/en-us/library/4bab1c02-9e61-4aaf-9957-11d1934ef4ef) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-148">To create a console file, use the [Export-Console](https://technet.microsoft.com/en-us/library/4bab1c02-9e61-4aaf-9957-11d1934ef4ef) cmdlet in Windows PowerShell.</span></span>

### <a name="-sta"></a><span data-ttu-id="c6eb9-149">-Sta</span><span class="sxs-lookup"><span data-stu-id="c6eb9-149">-Sta</span></span>
<span data-ttu-id="c6eb9-150">使用單一執行緒 Apartment 啟動 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-150">Starts Windows PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="c6eb9-151">在 Windows PowerShell 3.0 中，單一執行緒 Apartment (STA) 是預設值。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-151">In Windows PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="c6eb9-152">在 Windows PowerShell 2.0 中，多執行緒 Apartment (MTA) 是預設值。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-152">In Windows PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-version-windows-powershell-version"></a><span data-ttu-id="c6eb9-153">-Version <Windows PowerShell Version></span><span class="sxs-lookup"><span data-stu-id="c6eb9-153">-Version <Windows PowerShell Version></span></span>
<span data-ttu-id="c6eb9-154">啟動指定的 Windows PowerShell 版本。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-154">Starts the specified version of Windows PowerShell.</span></span> <span data-ttu-id="c6eb9-155">您指定的版本必須安裝在系統上。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-155">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="c6eb9-156">如果 Windows PowerShell 3.0 已安裝於電腦上，有效值為 "2.0" 和 "3.0"。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-156">If Windows PowerShell 3.0 is installed on the computer, valid values are "2.0" and "3.0".</span></span> <span data-ttu-id="c6eb9-157">預設值為 "3.0"。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-157">The default value is "3.0".</span></span>

<span data-ttu-id="c6eb9-158">如果未安裝 Windows PowerShell 3.0，唯一有效的值為 "2.0"。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-158">If Windows PowerShell 3.0 is not installed, the only valid value is "2.0".</span></span> <span data-ttu-id="c6eb9-159">其他值會被忽略。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-159">Other values are ignored.</span></span>

<span data-ttu-id="c6eb9-160">如需詳細資訊，請參閱[開始使用 Windows PowerShell [舊版 MSDN]](https://technet.microsoft.com/en-us/library/69555d95-b481-43e1-86e7-b46d68b3e2dd)中的＜安裝 Windows PowerShell＞。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-160">For more information, see "Installing Windows PowerShell" in the [Getting Started with Windows PowerShell [OLD MSDN]](https://technet.microsoft.com/en-us/library/69555d95-b481-43e1-86e7-b46d68b3e2dd).</span></span>

### <a name="-windowstyle-window-style"></a><span data-ttu-id="c6eb9-161">-WindowStyle <Window style></span><span class="sxs-lookup"><span data-stu-id="c6eb9-161">-WindowStyle <Window style></span></span>
<span data-ttu-id="c6eb9-162">設定工作階段的視窗樣式。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-162">Sets the window style for the session.</span></span> <span data-ttu-id="c6eb9-163">有效值為 Normal、Minimized、Maximized 和 Hidden。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-163">Valid values are Normal, Minimized, Maximized and Hidden.</span></span>

### <a name="-command"></a><span data-ttu-id="c6eb9-164">-Command</span><span class="sxs-lookup"><span data-stu-id="c6eb9-164">-Command</span></span>
<span data-ttu-id="c6eb9-165">就如同在 Windows PowerShell 命令提示字元輸入一樣，執行指定的命令 (和任何參數)，然後結束，除非指定了 NoExit 參數。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-165">Executes the specified commands (and any parameters) as though they were typed at the Windows PowerShell command prompt, and then exits, unless the NoExit parameter is specified.</span></span>

<span data-ttu-id="c6eb9-166">Command 的值可以是 "-"、字串。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-166">The value of Command can be "-", a string.</span></span> <span data-ttu-id="c6eb9-167">或指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-167">or a script block.</span></span> <span data-ttu-id="c6eb9-168">如果 Command 的值是 "-"，則會從標準輸入讀取命令文字。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-168">If the value of Command is "-", the command text is read from standard input.</span></span>

<span data-ttu-id="c6eb9-169">指令碼區塊必須以大括弧 ({}) 括住。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-169">Script blocks must be enclosed in braces ({}).</span></span> <span data-ttu-id="c6eb9-170">只有在 Windows PowerShell 中執行 PowerShell.exe 時，您才可以指定指令碼區塊。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-170">You can specify a script block only when running PowerShell.exe in Windows PowerShell.</span></span> <span data-ttu-id="c6eb9-171">指令碼的結果會當做已還原序列化的 XML 物件 (而不是即時物件) 傳回到父殼層。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-171">The results of the script are returned to the parent shell as deserialized XML objects, not live objects.</span></span>

<span data-ttu-id="c6eb9-172">如果 Command 的值是字串，**Command** 必須是命令中的最後一個參數，因為在命令後輸入的任何字元，會解譯為命令引數。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-172">If the value of Command is a string, **Command** must be the last parameter in the command , because any characters typed after the command are interpreted as the command arguments.</span></span>

<span data-ttu-id="c6eb9-173">若要寫入執行 Windows PowerShell 命令的字串，請使用下列格式︰</span><span class="sxs-lookup"><span data-stu-id="c6eb9-173">To write a string that runs a Windows PowerShell command, use the format:</span></span>

```
"& {<command>}"
```

<span data-ttu-id="c6eb9-174">其中的引號代表字串，它會呼叫 (&) 運算子，使命令執行。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-174">where the quotation marks indicate a string and the invoke operator (&) causes the command to be executed.</span></span>

### <a name="-help---"></a><span data-ttu-id="c6eb9-175">-Help, -?, /?</span><span class="sxs-lookup"><span data-stu-id="c6eb9-175">-Help, -?, /?</span></span>
<span data-ttu-id="c6eb9-176">顯示此訊息。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-176">Shows this message.</span></span> <span data-ttu-id="c6eb9-177">如果您正在 Windows PowerShell 中輸入 PowerShell.exe 命令，命令參數之前要加上連字號 (-)，而不是正斜線 (/)。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-177">If you are typing a PowerShell.exe command in Windows PowerShell, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="c6eb9-178">在 Cmd.exe 中，您可以使用連字號或正斜線。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-178">You can use either a hyphen or forward slash in Cmd.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="c6eb9-179">疑難排解注意事項︰在 Windows PowerShell 2.0 中，啟動 Windows PowerShell 主控台中的某些程式會失敗，LastExitCode 為 0xc0000142。</span><span class="sxs-lookup"><span data-stu-id="c6eb9-179">Troubleshooting Note: In Windows PowerShell 2.0, starting some programs in the Windows PowerShell console fails with a LastExitCode of 0xc0000142.</span></span>

## <a name="examples"></a><span data-ttu-id="c6eb9-180">範例</span><span class="sxs-lookup"><span data-stu-id="c6eb9-180">EXAMPLES</span></span>

```
PowerShell -PSConsoleFile sqlsnapin.psc1

PowerShell -Version 2.0 -NoLogo -InputFormat text -OutputFormat XML

PowerShell -Command "Get-EventLog -LogName security"

# in an existing PowerShell session that understands the curly braces mean a script block
PowerShell -Command {Get-EventLog -LogName security}

PowerShell -Command "& {Get-EventLog -LogName security}"

# To use the -EncodedCommand parameter:
$command = "dir 'c:\program files' "
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
powershell.exe -encodedCommand $encodedCommand
```

