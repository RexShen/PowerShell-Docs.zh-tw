---
description: 說明如何使用 `pwsh` 命令列介面。 顯示命令列參數並描述語法。
keywords: powershell,cmdlet
ms.date: 10/05/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pwsh?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Pwsh
ms.openlocfilehash: c71848e327822f7cbc659310d3fa47a5a46a37a2
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207748"
---
# <a name="about-pwsh"></a><span data-ttu-id="1b2c3-105">關於 pwsh</span><span class="sxs-lookup"><span data-stu-id="1b2c3-105">About pwsh</span></span>

## <a name="short-description"></a><span data-ttu-id="1b2c3-106">簡短描述</span><span class="sxs-lookup"><span data-stu-id="1b2c3-106">Short Description</span></span>
<span data-ttu-id="1b2c3-107">說明如何使用 `pwsh` 命令列介面。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-107">Explains how to use the `pwsh` command-line interface.</span></span> <span data-ttu-id="1b2c3-108">顯示命令列參數並描述語法。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-108">Displays the command-line parameters and describes the syntax.</span></span>

## <a name="long-description"></a><span data-ttu-id="1b2c3-109">完整描述</span><span class="sxs-lookup"><span data-stu-id="1b2c3-109">Long Description</span></span>

## <a name="syntax"></a><span data-ttu-id="1b2c3-110">語法</span><span class="sxs-lookup"><span data-stu-id="1b2c3-110">Syntax</span></span>

```
pwsh[.exe]
   [[-File] <filePath> [args]]
   [-Command { - | <script-block> [-args <arg-array>]
                 | <string> [<CommandParameters>] } ]
   [-ConfigurationName <string>]
   [-CustomPipeName <string>]
   [-EncodedCommand <Base64EncodedCommand>]
   [-ExecutionPolicy <ExecutionPolicy>]
   [-InputFormat {Text | XML}]
   [-Interactive]
   [-Login]
   [-MTA]
   [-NoExit]
   [-NoLogo]
   [-NonInteractive]
   [-NoProfile]
   [-OutputFormat {Text | XML}]
   [-SettingsFile <SettingsFilePath>]
   [-SSHServerMode]
   [-STA]
   [-Version]
   [-WindowStyle <style>]
   [-WorkingDirectory <directoryPath>]

pwsh[.exe] -h | -Help | -? | /?
```

## <a name="parameters"></a><span data-ttu-id="1b2c3-111">參數</span><span class="sxs-lookup"><span data-stu-id="1b2c3-111">Parameters</span></span>

<span data-ttu-id="1b2c3-112">所有參數都不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-112">All parameters are case-insensitive.</span></span>

### <a name="-file---f"></a><span data-ttu-id="1b2c3-113">-File |-f</span><span class="sxs-lookup"><span data-stu-id="1b2c3-113">-File | -f</span></span>

<span data-ttu-id="1b2c3-114">如果的值 `File` 為 `-` ，則會從標準輸入讀取命令文字。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-114">If the value of `File` is `-`, the command text is read from standard input.</span></span>
<span data-ttu-id="1b2c3-115">如果 `pwsh -File -` 執行時沒有重新導向的標準輸入，則會啟動一般會話。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-115">Running `pwsh -File -` without redirected standard input starts a regular session.</span></span> <span data-ttu-id="1b2c3-116">這與完全不指定 `File` 參數相同。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-116">This is the same as not specifying the `File` parameter at all.</span></span>

<span data-ttu-id="1b2c3-117">如果沒有任何參數存在，但命令列中有值，則這是預設參數。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-117">This is the default parameter if no parameters are present but values are present in the command line.</span></span> <span data-ttu-id="1b2c3-118">指定的腳本會在區域範圍中執行 ( 「點來源」 ) ，如此腳本所建立的函式和變數就會在目前的會話中使用。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-118">The specified script runs in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="1b2c3-119">輸入指令碼檔案路徑和任何參數。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-119">Enter the script file path and any parameters.</span></span> <span data-ttu-id="1b2c3-120">File 必須是命令中的最後一個參數，因為在檔案參數名稱之後輸入的所有字元都會被解釋為腳本檔案路徑，後面接著腳本參數。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-120">File must be the last parameter in the command, because all characters typed after the File parameter name are interpreted as the script file path followed by the script parameters.</span></span>

<span data-ttu-id="1b2c3-121">一般而言，指令碼的切換參數可以包含或省略。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-121">Typically, the switch parameters of a script are either included or omitted.</span></span>
<span data-ttu-id="1b2c3-122">例如，下列命令會使用 Get-Script.ps1 腳本檔案的 All 參數： `-File .\Get-Script.ps1 -All`</span><span class="sxs-lookup"><span data-stu-id="1b2c3-122">For example, the following command uses the All parameter of the Get-Script.ps1 script file: `-File .\Get-Script.ps1 -All`</span></span>

<span data-ttu-id="1b2c3-123">在罕見的情況下，您可能需要提供切換參數的 **布林** 值。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-123">In rare cases, you might need to provide a **Boolean** value for a switch parameter.</span></span> <span data-ttu-id="1b2c3-124">若要在 **File** 參數的值中提供切換參數的 **布林** 值，請使用通常緊接在冒號和布林值的參數，如下所示： `-File .\Get-Script.ps1 -All:$False` 。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-124">To provide a **Boolean** value for a switch parameter in the value of the **File** parameter, Use the parameter normally followed immediately by a colon and the boolean value, such as the following: `-File .\Get-Script.ps1 -All:$False`.</span></span>

<span data-ttu-id="1b2c3-125">參數會以常值字串形式 (經過目前的殼層解譯後) 傳遞至指令碼。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-125">Parameters passed to the script are passed as literal strings, after interpretation by the current shell.</span></span> <span data-ttu-id="1b2c3-126">例如，如果您在中， `cmd.exe` 而且想要傳遞環境變數值，您可以使用 `cmd.exe` 下列語法： `pwsh -File .\test.ps1 -TestParam %windir%`</span><span class="sxs-lookup"><span data-stu-id="1b2c3-126">For example, if you are in `cmd.exe` and want to pass an environment variable value, you would use the `cmd.exe` syntax: `pwsh -File .\test.ps1 -TestParam %windir%`</span></span>

<span data-ttu-id="1b2c3-127">相反地，在 `pwsh -File .\test.ps1 -TestParam $env:windir` `cmd.exe` 接收常值字串的腳本中執行會產生， `$env:windir` 因為它對目前的 shell 沒有任何特殊意義 `cmd.exe` 。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-127">In contrast, running `pwsh -File .\test.ps1 -TestParam $env:windir` in `cmd.exe` results in the script receiving the literal string `$env:windir` because it has no special meaning to the current `cmd.exe` shell.</span></span> <span data-ttu-id="1b2c3-128">`$env:windir`環境變數參考的樣式 _可以_ 在 **命令** 參數中使用，因為它會被視為 PowerShell 程式碼。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-128">The `$env:windir` style of environment variable reference _can_ be used inside a **Command** parameter, since there it is interpreted as PowerShell code.</span></span>

<span data-ttu-id="1b2c3-129">同樣地，如果您想要從 _批次腳本_ 執行相同的命令，您可以使用 `%~dp0` 而 `.\` 非 `$PSScriptRoot` 或來表示目前的執行目錄： `pwsh -File %~dp0test.ps1 -TestParam %windir%` 。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-129">Similarly, if you want to execute the same command from a _Batch script_ , you would use `%~dp0` instead of `.\` or `$PSScriptRoot` to represent the current execution directory: `pwsh -File %~dp0test.ps1 -TestParam %windir%`.</span></span> <span data-ttu-id="1b2c3-130">如果您改 `.\test.ps1` 為使用，則 PowerShell 會擲回錯誤，因為它找不到常值路徑 `.\test.ps1`</span><span class="sxs-lookup"><span data-stu-id="1b2c3-130">If you instead used `.\test.ps1`, PowerShell would throw an error because it cannot find the literal path `.\test.ps1`</span></span>

<span data-ttu-id="1b2c3-131">當腳本檔案以命令結束時 `exit` ，進程結束代碼會設定為與命令搭配使用的數值引數 `exit` 。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-131">When the script file terminates with an `exit` command, the process exit code is set to the numeric argument used with the `exit` command.</span></span> <span data-ttu-id="1b2c3-132">使用正常終止時，結束代碼一律為 `0` 。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-132">With normal termination, the exit code is always `0`.</span></span>

<span data-ttu-id="1b2c3-133">類似于 `-Command` ，當腳本終止錯誤發生時，結束代碼會設定為 `1` 。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-133">Similar to `-Command`, when a script-terminating error occurs, the exit code is set to `1`.</span></span> <span data-ttu-id="1b2c3-134">不過，與不同的是 `-Command` ，當使用<kbd>Ctrl</kbd>C 中斷執行時，結束 - <kbd>C</kbd>代碼為 `0` 。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-134">However, unlike with `-Command`, when the execution is interrupted with <kbd>Ctrl</kbd>-<kbd>C</kbd> the exit code is `0`.</span></span>

### <a name="-command---c"></a><span data-ttu-id="1b2c3-135">-Command |-c</span><span class="sxs-lookup"><span data-stu-id="1b2c3-135">-Command | -c</span></span>

<span data-ttu-id="1b2c3-136">執行指定的命令 (和任何參數) 如同在 PowerShell 命令提示字元中輸入，然後結束，除非 `NoExit` 指定了參數。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-136">Executes the specified commands (and any parameters) as though they were typed at the PowerShell command prompt, and then exits, unless the `NoExit` parameter is specified.</span></span>

<span data-ttu-id="1b2c3-137">**命令** 的值可以是 `-` 、腳本區塊或字串。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-137">The value of **Command** can be `-`, a script block, or a string.</span></span> <span data-ttu-id="1b2c3-138">如果 **command** 的值為 `-` ，則會從標準輸入讀取命令文字。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-138">If the value of **Command** is `-`, the command text is read from standard input.</span></span>

<span data-ttu-id="1b2c3-139">**命令** 參數只接受腳本區塊，以便在可辨識傳遞給 **命令** 的值做為 **ScriptBlock** 類型時執行。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-139">The **Command** parameter only accepts a script block for execution when it can recognize the value passed to **Command** as a **ScriptBlock** type.</span></span> <span data-ttu-id="1b2c3-140">_只有_ `pwsh` 從另一個 PowerShell 主機執行時，才有可能發生此情況。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-140">This is _only_ possible when running `pwsh` from another PowerShell host.</span></span> <span data-ttu-id="1b2c3-141">**ScriptBlock** 類型可以包含在現有的變數中，從運算式傳回，或由 PowerShell 主機剖析為常值腳本區塊（以大括弧括住 (`{}`) ），然後再傳遞至 `pwsh` 。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-141">The **ScriptBlock** type may be contained in an existing variable, returned from an expression, or parsed by the PowerShell host as a literal script block enclosed in curly braces (`{}`), before being passed to `pwsh`.</span></span>

```powershell
pwsh -Command {Get-WinEvent -LogName security}
```

<span data-ttu-id="1b2c3-142">在中 `cmd.exe` ，沒有腳本區塊 (或 **ScriptBlock** 類型) ，因此傳遞給 **命令** 的值 _一律_ 會是字串。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-142">In `cmd.exe`, there is no such thing as a script block (or **ScriptBlock** type), so the value passed to **Command** will _always_ be a string.</span></span> <span data-ttu-id="1b2c3-143">您可以在字串內撰寫指令碼區塊，但它不會執行，其行為完全就像您在一般 PowerShell 提示字元中輸入它一樣，將指令碼區塊的內容印回給您。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-143">You can write a script block inside the string, but instead of being executed it will behave exactly as though you typed it at a typical PowerShell prompt, printing the contents of the script block back out to you.</span></span>

<span data-ttu-id="1b2c3-144">傳遞給 **命令** 的字串仍會以 PowerShell 程式碼的形式執行，因此從執行時，在第一個位置通常不需要腳本區塊大括弧 `cmd.exe` 。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-144">A string passed to **Command** is still executed as PowerShell code, so the script block curly braces are often not required in the first place when running from `cmd.exe`.</span></span> <span data-ttu-id="1b2c3-145">若要執行字串內定義的內嵌指令碼區塊，可以使用[呼叫運算子](about_operators.md#special-operators) `&`：</span><span class="sxs-lookup"><span data-stu-id="1b2c3-145">To execute an inline script block defined inside a string, the [call operator](about_operators.md#special-operators) `&` can be used:</span></span>

```
pwsh -Command "& {Get-WinEvent -LogName security}"
```

<span data-ttu-id="1b2c3-146">如果 **command** 的值是字串， **命令** 必須是 pwsh 的最後一個參數，因為它後面的所有引數都會轉譯為要執行之命令的一部分。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-146">If the value of **Command** is a string, **Command** must be the last parameter for pwsh, because all arguments following it are interpreted as part of the command to execute.</span></span>

<span data-ttu-id="1b2c3-147">從現有的 PowerShell 會話內呼叫時，結果會以還原序列化的 XML 物件（而不是即時物件）傳回到父 shell。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-147">When called from within an existing PowerShell session, the results are returned to the parent shell as deserialized XML objects, not live objects.</span></span> <span data-ttu-id="1b2c3-148">若為其他 shell，則會以字串形式傳回結果。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-148">For other shells, the results are returned as strings.</span></span>

<span data-ttu-id="1b2c3-149">如果 **command** 的值為 `-` ，則會從標準輸入讀取命令文字。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-149">If the value of **Command** is `-`, the command text is read from standard input.</span></span> <span data-ttu-id="1b2c3-150">使用 **命令** 參數搭配標準輸入時，您必須重新導向標準輸入。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-150">You must redirect standard input when using the **Command** parameter with standard input.</span></span> <span data-ttu-id="1b2c3-151">例如：</span><span class="sxs-lookup"><span data-stu-id="1b2c3-151">For example:</span></span>

```powershell
@'
"in"

"hi" |
  % { "$_ there" }

"out"
'@ | powershell -NoProfile -Command -
```

<span data-ttu-id="1b2c3-152">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="1b2c3-152">This example produces the following output:</span></span>

```Output
in
hi there
out
```

<span data-ttu-id="1b2c3-153">進程結束碼取決於腳本區塊內最後 (執行) 命令的狀態。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-153">The process exit code is determined by status of the last (executed) command within the script block.</span></span> <span data-ttu-id="1b2c3-154">`0`當是 `$?` `$true` 或 `1` 時， `$?` 結束代碼為 `$false` 。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-154">The exit code is `0` when `$?` is `$true` or `1` when `$?` is `$false`.</span></span> <span data-ttu-id="1b2c3-155">如果最後一個命令是外部程式或 PowerShell 腳本，其會明確地設定或以外的結束 `0` 代碼 `1` ，則會將結束代碼轉換為，以 `1` 進行進程結束代碼。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-155">If the last command is an external program or a PowerShell script that explicitly sets an exit code other than `0` or `1`, that exit code is converted to `1` for process exit code.</span></span> <span data-ttu-id="1b2c3-156">若要保留特定的結束代碼，請加入 `exit $LASTEXITCODE` 至您的命令字串或腳本區塊。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-156">To preserve the specific exit code, add `exit $LASTEXITCODE` to your command string or script block.</span></span>

<span data-ttu-id="1b2c3-157">同樣地，當腳本終止 (的執行時間終止) 錯誤（例如 `throw` 或 `-ErrorAction Stop` ），或執行與<kbd>Ctrl</kbd> - <kbd>C</kbd>中斷時，就會傳回值1。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-157">Similarly, the value 1 is returned when a script-terminating (runspace-terminating) error, such as a `throw` or `-ErrorAction Stop`, occurs or when execution is interrupted with <kbd>Ctrl</kbd>-<kbd>C</kbd>.</span></span>

### <a name="-configurationname---config"></a><span data-ttu-id="1b2c3-158">-ConfigurationName |-config</span><span class="sxs-lookup"><span data-stu-id="1b2c3-158">-ConfigurationName | -config</span></span>

<span data-ttu-id="1b2c3-159">指定 PowerShell 執行所在的設定端點。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-159">Specifies a configuration endpoint in which PowerShell is run.</span></span> <span data-ttu-id="1b2c3-160">這可以是在本機電腦上註冊的任何端點，包括預設的 PowerShell 遠端端點，或具有特定使用者角色功能的自訂端點。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-160">This can be any endpoint registered on the local machine including the default PowerShell remoting endpoints or a custom endpoint having specific user role capabilities.</span></span>

<span data-ttu-id="1b2c3-161">範例： `pwsh -ConfigurationName AdminRoles`</span><span class="sxs-lookup"><span data-stu-id="1b2c3-161">Example: `pwsh -ConfigurationName AdminRoles`</span></span>

### <a name="-custompipename"></a><span data-ttu-id="1b2c3-162">-CustomPipeName</span><span class="sxs-lookup"><span data-stu-id="1b2c3-162">-CustomPipeName</span></span>

<span data-ttu-id="1b2c3-163">指定要用於額外的 IPC 伺服器 (具名管道) 用於偵錯工具和其他跨進程通訊的名稱。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-163">Specifies the name to use for an additional IPC server (named pipe) used for debugging and other cross-process communication.</span></span> <span data-ttu-id="1b2c3-164">這會提供可預測的機制，以連接到其他 PowerShell 實例。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-164">This offers a predictable mechanism for connecting to other PowerShell instances.</span></span> <span data-ttu-id="1b2c3-165">通常搭配上的 **CustomPipeName** 參數使用 `Enter-PSHostProcess` 。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-165">Typically used with the **CustomPipeName** parameter on `Enter-PSHostProcess`.</span></span>

<span data-ttu-id="1b2c3-166">此參數是在 PowerShell 6.2 中引進。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-166">This parameter was introduced in PowerShell 6.2.</span></span>

<span data-ttu-id="1b2c3-167">例如：</span><span class="sxs-lookup"><span data-stu-id="1b2c3-167">For example:</span></span>

```powershell
# PowerShell instance 1
pwsh -CustomPipeName mydebugpipe
# PowerShell instance 2
Enter-PSHostProcess -CustomPipeName mydebugpipe
```

### <a name="-encodedcommand---e---ec"></a><span data-ttu-id="1b2c3-168">-EncodedCommand |-e |-ec</span><span class="sxs-lookup"><span data-stu-id="1b2c3-168">-EncodedCommand | -e | -ec</span></span>

<span data-ttu-id="1b2c3-169">接受 Base64 編碼字串版本的命令。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-169">Accepts a Base64-encoded string version of a command.</span></span> <span data-ttu-id="1b2c3-170">使用這個參數將命令提交至需要複雜、嵌套引號的 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-170">Use this parameter to submit commands to PowerShell that require complex, nested quoting.</span></span> <span data-ttu-id="1b2c3-171">Base64 標記法必須是 UTF-16 編碼的字串。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-171">The Base64 representation must be a UTF-16 encoded string.</span></span>

<span data-ttu-id="1b2c3-172">例如：</span><span class="sxs-lookup"><span data-stu-id="1b2c3-172">For example:</span></span>

```powershell
$command = 'dir "c:\program files" '
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
pwsh -encodedcommand $encodedCommand
```

### <a name="-executionpolicy---ex---ep"></a><span data-ttu-id="1b2c3-173">-ExecutionPolicy |-ex |-ep</span><span class="sxs-lookup"><span data-stu-id="1b2c3-173">-ExecutionPolicy | -ex | -ep</span></span>

<span data-ttu-id="1b2c3-174">設定目前會話的預設執行原則，並將它儲存在 `$env:PSExecutionPolicyPreference` 環境變數中。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-174">Sets the default execution policy for the current session and saves it in the `$env:PSExecutionPolicyPreference` environment variable.</span></span> <span data-ttu-id="1b2c3-175">此參數不會變更持續設定的執行原則。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-175">This parameter does not change the persistently configured execution policies.</span></span>

<span data-ttu-id="1b2c3-176">此參數只適用于 Windows 電腦。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-176">This parameter only applies to Windows computers.</span></span> <span data-ttu-id="1b2c3-177">`$env:PSExecutionPolicyPreference`環境變數不存在於非 Windows 平臺上。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-177">The `$env:PSExecutionPolicyPreference` environment variable does not exist on non-Windows platforms.</span></span>

### <a name="-inputformat---inp---if"></a><span data-ttu-id="1b2c3-178">-InputFormat |-sct.inp |-如果</span><span class="sxs-lookup"><span data-stu-id="1b2c3-178">-InputFormat | -inp | -if</span></span>

<span data-ttu-id="1b2c3-179">描述傳送至 PowerShell 的資料格式。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-179">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="1b2c3-180">有效值為 "Text" (文字字串) 或 "XML" (序列化的 CLIXML 格式)。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-180">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-interactive---i"></a><span data-ttu-id="1b2c3-181">-Interactive |-i</span><span class="sxs-lookup"><span data-stu-id="1b2c3-181">-Interactive | -i</span></span>

<span data-ttu-id="1b2c3-182">向使用者顯示互動式提示。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-182">Present an interactive prompt to the user.</span></span> <span data-ttu-id="1b2c3-183">非互動式參數的反向。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-183">Inverse for NonInteractive parameter.</span></span>

### <a name="-login---l"></a><span data-ttu-id="1b2c3-184">-Login |-l</span><span class="sxs-lookup"><span data-stu-id="1b2c3-184">-Login | -l</span></span>

<span data-ttu-id="1b2c3-185">在 Linux 和 macOS 上，使用/bin/sh 來執行登入設定檔（例如/etc/profile 和 ~/.profile.），以登入命令介面啟動 PowerShell</span><span class="sxs-lookup"><span data-stu-id="1b2c3-185">On Linux and macOS, starts PowerShell as a login shell, using /bin/sh to execute login profiles such as /etc/profile and ~/.profile.</span></span>
<span data-ttu-id="1b2c3-186">在 Windows 上，此參數不會執行任何動作。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-186">On Windows, this switch does nothing.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1b2c3-187">此參數必須先開始，才能以登入命令介面啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-187">This parameter must come first to start PowerShell as a login shell.</span></span>
> <span data-ttu-id="1b2c3-188">在另一個位置傳遞這個參數將會被忽略。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-188">Passing this parameter in another position will be ignored.</span></span>

<span data-ttu-id="1b2c3-189">若要 `pwsh` 在類似 UNIX 的作業系統上設定為登入命令介面：</span><span class="sxs-lookup"><span data-stu-id="1b2c3-189">To set up `pwsh` as the login shell on UNIX-like operating systems:</span></span>

- <span data-ttu-id="1b2c3-190">確認的完整絕對路徑 `pwsh` 列在 `/etc/shells`</span><span class="sxs-lookup"><span data-stu-id="1b2c3-190">Verify that the full absolute path to `pwsh` is listed under `/etc/shells`</span></span>
  - <span data-ttu-id="1b2c3-191">此路徑通常類似于 `/usr/bin/pwsh` Linux 或 `/usr/local/bin/pwsh` macOS</span><span class="sxs-lookup"><span data-stu-id="1b2c3-191">This path is usually something like `/usr/bin/pwsh` on Linux or `/usr/local/bin/pwsh` on macOS</span></span>
  - <span data-ttu-id="1b2c3-192">使用某些安裝方法時，會在安裝時自動新增此專案</span><span class="sxs-lookup"><span data-stu-id="1b2c3-192">With some installation methods, this entry will be added automatically at installation time</span></span>
  - <span data-ttu-id="1b2c3-193">如果 `pwsh` 不存在於中 `/etc/shells` ，請使用編輯器將路徑附加到 `pwsh` 最後一行。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-193">If `pwsh` is not present in `/etc/shells`, use an editor to append the path to `pwsh` on the last line.</span></span> <span data-ttu-id="1b2c3-194">這需要較高的許可權才能編輯。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-194">This requires elevated privileges to edit.</span></span>
- <span data-ttu-id="1b2c3-195">使用 [chsh](https://linux.die.net/man/1/chsh) 公用程式，將您目前使用者的 shell 設定為 `pwsh` ：</span><span class="sxs-lookup"><span data-stu-id="1b2c3-195">Use the [chsh](https://linux.die.net/man/1/chsh) utility to set your current user's shell to `pwsh`:</span></span>

  ```sh
  chsh -s /usr/bin/pwsh
  ```

> [!WARNING]
> <span data-ttu-id="1b2c3-196">`pwsh`Windows 子系統 Linux 版 (WSL) 上目前不支援設定為登入 shell，而且嘗試設定 `pwsh` 為登入命令介面，可能會導致無法以互動方式啟動 WSL。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-196">Setting `pwsh` as the login shell is currently not supported on Windows Subsystem for Linux (WSL), and attempting to set `pwsh` as the login shell there may lead to being unable to start WSL interactively.</span></span>

### <a name="-mta"></a><span data-ttu-id="1b2c3-197">-MTA</span><span class="sxs-lookup"><span data-stu-id="1b2c3-197">-MTA</span></span>

<span data-ttu-id="1b2c3-198">使用多執行緒的單元啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-198">Start PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="1b2c3-199">這個參數只能在 Windows 上使用。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-199">This switch is only available on Windows.</span></span>

### <a name="-noexit---noe"></a><span data-ttu-id="1b2c3-200">-NoExit |-noe</span><span class="sxs-lookup"><span data-stu-id="1b2c3-200">-NoExit | -noe</span></span>

<span data-ttu-id="1b2c3-201">執行啟動命令後不要結束。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-201">Does not exit after running startup commands.</span></span>

<span data-ttu-id="1b2c3-202">範例： `pwsh -NoExit -Command Get-Date`</span><span class="sxs-lookup"><span data-stu-id="1b2c3-202">Example: `pwsh -NoExit -Command Get-Date`</span></span>

### <a name="-nologo---nol"></a><span data-ttu-id="1b2c3-203">-NoLogo |-nol</span><span class="sxs-lookup"><span data-stu-id="1b2c3-203">-NoLogo | -nol</span></span>

<span data-ttu-id="1b2c3-204">在互動式會話啟動時隱藏著作權橫幅。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-204">Hides the copyright banner at startup of interactive sessions.</span></span>

### <a name="-noninteractive---noni"></a><span data-ttu-id="1b2c3-205">-非互動式 |-noni</span><span class="sxs-lookup"><span data-stu-id="1b2c3-205">-NonInteractive | -noni</span></span>

<span data-ttu-id="1b2c3-206">不向使用者顯示互動式提示。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-206">Does not present an interactive prompt to the user.</span></span> <span data-ttu-id="1b2c3-207">任何嘗試使用互動式功能（例如 `Read-Host` 或確認提示）都會導致語句終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-207">Any attempts to use interactive features, like `Read-Host` or confirmation prompts, result in statement-terminating errors.</span></span>

### <a name="-noprofile---nop"></a><span data-ttu-id="1b2c3-208">-NoProfile |-nop</span><span class="sxs-lookup"><span data-stu-id="1b2c3-208">-NoProfile | -nop</span></span>

<span data-ttu-id="1b2c3-209">不會載入 PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-209">Does not load the PowerShell profiles.</span></span>

### <a name="-outputformat---o---of"></a><span data-ttu-id="1b2c3-210">->outputformat |-o |-/</span><span class="sxs-lookup"><span data-stu-id="1b2c3-210">-OutputFormat | -o | -of</span></span>

<span data-ttu-id="1b2c3-211">決定 PowerShell 的輸出格式。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-211">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="1b2c3-212">有效值為 "Text" (文字字串) 或 "XML" (序列化的 CLIXML 格式)。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-212">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

<span data-ttu-id="1b2c3-213">範例： `pwsh -o XML -c Get-Date`</span><span class="sxs-lookup"><span data-stu-id="1b2c3-213">Example: `pwsh -o XML -c Get-Date`</span></span>

<span data-ttu-id="1b2c3-214">當呼叫遷移 PowerShell 會話時，您會取得還原序列化的物件，做為輸出，而不是純文字字串。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-214">When called withing a PowerShell session, you get deserialized objects as output rather plain strings.</span></span> <span data-ttu-id="1b2c3-215">從其他 shell 呼叫時，輸出是格式化為 CLIXML 文字的字串資料。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-215">When called from other shells, the output is string data formatted as CLIXML text.</span></span>

### <a name="-settingsfile---settings"></a><span data-ttu-id="1b2c3-216">-SettingsFile |-設定</span><span class="sxs-lookup"><span data-stu-id="1b2c3-216">-SettingsFile | -settings</span></span>

<span data-ttu-id="1b2c3-217">覆寫會話的全系統 `powershell.config.json` 設定檔案。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-217">Overrides the system-wide `powershell.config.json` settings file for the session.</span></span> <span data-ttu-id="1b2c3-218">根據預設，系統會從目錄中讀取整個系統的設定 `powershell.config.json` `$PSHOME` 。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-218">By default, system-wide settings are read from the `powershell.config.json` in the `$PSHOME` directory.</span></span>

<span data-ttu-id="1b2c3-219">請注意，引數所指定的端點不會使用這些設定 `-ConfigurationName` 。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-219">Note that these settings are not used by the endpoint specified by the `-ConfigurationName` argument.</span></span>

<span data-ttu-id="1b2c3-220">範例： `pwsh -SettingsFile c:\myproject\powershell.config.json`</span><span class="sxs-lookup"><span data-stu-id="1b2c3-220">Example: `pwsh -SettingsFile c:\myproject\powershell.config.json`</span></span>

### <a name="-sshservermode---sshs"></a><span data-ttu-id="1b2c3-221">-SSHServerMode |-sshs</span><span class="sxs-lookup"><span data-stu-id="1b2c3-221">-SSHServerMode | -sshs</span></span>

<span data-ttu-id="1b2c3-222">用於以 SSH 子系統的形式執行 PowerShell 的 sshd_config。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-222">Used in sshd_config for running PowerShell as an SSH subsystem.</span></span> <span data-ttu-id="1b2c3-223">不適合或不支援任何其他用途。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-223">It is not intended or supported for any other use.</span></span>

### <a name="-sta"></a><span data-ttu-id="1b2c3-224">-STA</span><span class="sxs-lookup"><span data-stu-id="1b2c3-224">-STA</span></span>

<span data-ttu-id="1b2c3-225">使用單一執行緒的單元啟動 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-225">Start PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="1b2c3-226">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-226">This is the default.</span></span> <span data-ttu-id="1b2c3-227">這個參數只能在 Windows 上使用。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-227">This switch is only available on Windows.</span></span>

### <a name="-version---v"></a><span data-ttu-id="1b2c3-228">-Version |-v</span><span class="sxs-lookup"><span data-stu-id="1b2c3-228">-Version | -v</span></span>

<span data-ttu-id="1b2c3-229">顯示 PowerShell 的版本。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-229">Displays the version of PowerShell.</span></span> <span data-ttu-id="1b2c3-230">系統會忽略其他參數。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-230">Additional parameters are ignored.</span></span>

### <a name="-windowstyle---w"></a><span data-ttu-id="1b2c3-231">-System.windows.window.windowstyle |-w</span><span class="sxs-lookup"><span data-stu-id="1b2c3-231">-WindowStyle | -w</span></span>

<span data-ttu-id="1b2c3-232">設定工作階段的視窗樣式。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-232">Sets the window style for the session.</span></span> <span data-ttu-id="1b2c3-233">有效值為 Normal、Minimized、Maximized 和 Hidden。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-233">Valid values are Normal, Minimized, Maximized and Hidden.</span></span>

### <a name="-workingdirectory---wd"></a><span data-ttu-id="1b2c3-234">-WorkingDirectory |-wd</span><span class="sxs-lookup"><span data-stu-id="1b2c3-234">-WorkingDirectory | -wd</span></span>

<span data-ttu-id="1b2c3-235">藉由在啟動時執行來設定初始工作目錄。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-235">Sets the initial working directory by executing at startup.</span></span> <span data-ttu-id="1b2c3-236">支援任何有效的 PowerShell 檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-236">Any valid PowerShell file path is supported.</span></span>

<span data-ttu-id="1b2c3-237">若要在主目錄中啟動 PowerShell，請使用： `pwsh -WorkingDirectory ~`</span><span class="sxs-lookup"><span data-stu-id="1b2c3-237">To start PowerShell in your home directory, use: `pwsh -WorkingDirectory ~`</span></span>

### <a name="-help---"></a><span data-ttu-id="1b2c3-238">-Help, -?, /?</span><span class="sxs-lookup"><span data-stu-id="1b2c3-238">-Help, -?, /?</span></span>

<span data-ttu-id="1b2c3-239">顯示的說明 `pwsh` 。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-239">Displays help for `pwsh`.</span></span> <span data-ttu-id="1b2c3-240">如果您在 PowerShell 中輸入 pwsh 命令，請在命令參數前面加上連字號 (`-`) ，而不是正斜線 (`/`) 。</span><span class="sxs-lookup"><span data-stu-id="1b2c3-240">If you are typing a pwsh command in PowerShell, prepend the command parameters with a hyphen (`-`), not a forward slash (`/`).</span></span>
