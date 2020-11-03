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
# <a name="about-powershellexe"></a>關於 PowerShell.exe

## <a name="short-description"></a>簡短描述
說明如何使用 `powershell.exe` 命令列介面。 顯示命令列參數並描述語法。

## <a name="long-description"></a>完整描述

### <a name="syntax"></a>SYNTAX

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

### <a name="parameters"></a>參數

#### <a name="-psconsolefile-filepath"></a>-PSConsoleFile \<FilePath\>

載入指定的 PowerShell 主控台檔案。 輸入主控台檔案的路徑和名稱。 若要建立主控台檔案，請在 PowerShell 中使用 Export-Console Cmdlet。

#### <a name="-version-powershell-version"></a>-Version \<PowerShell Version\>

啟動指定版本的 PowerShell。 有效值為 2.0 和 3.0。 您指定的版本必須安裝在系統上。 如果 Windows PowerShell 3.0 安裝在電腦上，則預設版本為 "3.0"。
否則，預設版本為 "2.0"。 如需詳細資訊，請參閱 [安裝 PowerShell](/powershell/scripting/install/installing-windows-powershell)。

#### <a name="-nologo"></a>-NoLogo

啟動時隱藏著作權橫幅。

#### <a name="-noexit"></a>-NoExit

執行啟動命令後不要結束。

#### <a name="-sta"></a>-Sta

使用單一執行緒 Apartment 啟動 PowerShell。 在 Windows PowerShell 2.0 中，多執行緒 Apartment (MTA) 是預設值。 在 Windows PowerShell 3.0 中，單一執行緒 Apartment (STA) 是預設值。

#### <a name="-mta"></a>-Mta

使用多執行緒 Apartment 啟動 PowerShell。 此參數在 PowerShell 3.0 中引進。 在 PowerShell 2.0 中，預設為多執行緒 Apartment (MTA)。 在 PowerShell 3.0 中，預設為單一執行緒 Apartment (STA)。

#### <a name="-noprofile"></a>-NoProfile

不載入 PowerShell 設定檔。

#### <a name="-noninteractive"></a>-NonInteractive

不向使用者顯示互動式提示。

#### <a name="-inputformat-text--xml"></a>-InputFormat {Text | XML}

描述傳送至 PowerShell 的資料格式。 有效值為 "Text" (文字字串) 或 "XML" (序列化的 CLIXML 格式)。

#### <a name="-outputformat-text--xml"></a>-OutputFormat {Text | XML}

決定 PowerShell 的輸出格式。 有效值為 "Text" (文字字串) 或 "XML" (序列化的 CLIXML 格式)。

#### <a name="-windowstyle-window-style"></a>-WindowStyle \<Window style\>

設定工作階段的視窗樣式。 有效值為 Normal、Minimized、Maximized 和 Hidden。

#### <a name="-encodedcommand-base64encodedcommand"></a>-EncodedCommand \<Base64EncodedCommand\>

接受 Base-64 編碼字串版本的命令。 使用此參數以將命令傳送至要求複雜引號或大括弧的 Windows PowerShell。 字串必須使用 UTF UTF-16LE 字元編碼來格式化。

#### <a name="-configurationname-string"></a>-ConfigurationName \<string\>

指定 PowerShell 執行所在的設定端點。 這可以是在本機電腦上註冊的任何端點，包括預設的 PowerShell 遠端端點，或具有特定使用者角色功能的自訂端點。

#### <a name="-file----filepath-args"></a>-File-|\<filePath\>\<args\>

如果 **File** 的值是 "-"，則會從標準輸入讀取命令文字。
如果 `powershell -File -` 執行時沒有重新導向的標準輸入，則會啟動一般會話。 這與完全不指定 **File** 參數相同。

如果 [檔案] **的值為檔案** 路徑，腳本會在區域範圍中執行 ( 「點來源」 ) ，如此腳本所建立的函式和變數就會在目前的會話中使用。 輸入指令碼檔案路徑和任何參數。 **File** 必須是命令中的最後一個參數。 在 **File** 參數之後輸入的所有值，都會被解釋為傳遞給該腳本的腳本檔案路徑和參數。

參數會以常值字串形式 (經過目前的殼層解譯後) 傳遞至指令碼。 例如，如果您在 **cmd.exe** ，而且想要傳遞環境變數值，您可以使用 **cmd.exe** 語法： `powershell.exe -File .\test.ps1 -TestParam %windir%`

相反地，在 `powershell.exe -File .\test.ps1 -TestParam $env:windir` **cmd.exe** 中執行會導致腳本接收常值字串， `$env:windir` 因為它對目前的 **cmd.exe** shell 沒有特殊意義。 `$env:windir`環境變數參考的樣式 _可以_ 在 **命令** 參數中使用，因為它會被視為 PowerShell 程式碼。

同樣地，如果您想要從 **批次腳本** 執行相同的命令，您可以使用 `%~dp0` 而 `.\` 非 `$PSScriptRoot` 或來表示目前的執行目錄： `powershell.exe -File %~dp0test.ps1 -TestParam %windir%` 。
如果您改 `.\test.ps1` 為使用，則 PowerShell 會擲回錯誤，因為它找不到常值路徑 `.\test.ps1`

當 **file** 的值為檔案路徑 **時，檔案**_必須_ 是命令中的最後一個參數， **因為在檔案參數名稱** 之後輸入的任何字元都會被解釋為腳本檔案路徑，後面接著腳本參數。

您可以將腳本參數和值包含在 **File** 參數的值中。 例如：`-File .\Get-Script.ps1 -Domain Central`

一般而言，指令碼的切換參數可以包含或省略。
例如，下列命令會使用腳本檔案的 **All** 參數 `Get-Script.ps1` ： `-File .\Get-Script.ps1 -All`

在罕見的情況下，您可能需要為參數提供 **布林** 值。
以這種方式執行腳本時，不可能傳遞 switch 參數的明確布林值。 PowerShell 6 () 已移除這項限制 `pwsh.exe` 。

#### <a name="-executionpolicy-executionpolicy"></a>-ExecutionPolicy \<ExecutionPolicy\>

設定目前會話的預設執行原則，並將它儲存在 `$env:PSExecutionPolicyPreference` 環境變數中。 此參數不會變更已在登錄中設定的 PowerShell 執行原則。 如需 PowerShell 執行原則的資訊，包括有效值清單，請參閱 [about_Execution_Policies](about_Execution_Policies.md)。

#### <a name="-command"></a>-Command

執行指定的命令 (和任何參數) 如同在 PowerShell 命令提示字元中輸入，然後結束，除非 `NoExit` 指定了參數。

**命令** 的值可以是 `-` 、腳本區塊或字串。 如果 **command** 的值為 `-` ，則會從標準輸入讀取命令文字。

**命令** 參數只接受腳本區塊，以便在可辨識傳遞給 **命令** 的值做為 **ScriptBlock** 類型時執行。 _只有_ `powershell.exe` 從另一個 PowerShell 主機執行時，才有可能發生此情況。 **ScriptBlock** 類型可以包含在現有的變數中，從運算式傳回，或由 PowerShell 主機剖析為常值腳本區塊（以大括弧括住 (`{}`) ），然後再傳遞至 `powershell.exe` 。

```powershell
powershell -Command {Get-WinEvent -LogName security}
```

在中 `cmd.exe` ，沒有腳本區塊 (或 **ScriptBlock** 類型) ，因此傳遞給 **命令** 的值 _一律_ 會是字串。 您可以在字串內撰寫指令碼區塊，但它不會執行，其行為完全就像您在一般 PowerShell 提示字元中輸入它一樣，將指令碼區塊的內容印回給您。

傳遞給 **命令** 的字串仍會以 PowerShell 程式碼的形式執行，因此從執行時，在第一個位置通常不需要腳本區塊大括弧 `cmd.exe` 。 若要執行字串內定義的內嵌指令碼區塊，可以使用[呼叫運算子](about_operators.md#special-operators) `&`：

```cmd
pwsh -Command "& {Get-WinEvent -LogName security}"
```

如果 **command** 的值是字串， **命令** 必須是 pwsh 的最後一個參數，因為它後面的所有引數都會轉譯為要執行之命令的一部分。

從現有的 PowerShell 會話內呼叫時，結果會以還原序列化的 XML 物件（而不是即時物件）傳回到父 shell。 若為其他 shell，則會以字串形式傳回結果。

如果 **command** 的值為 `-` ，則會從標準輸入讀取命令文字。 使用 **命令** 參數搭配標準輸入時，您必須重新導向標準輸入。 例如：

```powershell
@'
"in"

"hi" |
  % { "$_ there" }

"out"
'@ | powershell -NoProfile -Command -
```

這個範例會產生下列輸出：

```Output
in
hi there
out
```

進程結束碼取決於腳本區塊內最後 (執行) 命令的狀態。 `0`當是 `$?` `$true` 或 `1` 時， `$?` 結束代碼為 `$false` 。 如果最後一個命令是外部程式或 PowerShell 腳本，其會明確地設定或以外的結束 `0` 代碼 `1` ，則會將結束代碼轉換為，以 `1` 進行進程結束代碼。 若要保留特定的結束代碼，請加入 `exit $LASTEXITCODE` 至您的命令字串或腳本區塊。

同樣地，當腳本終止 (的執行時間終止) 錯誤（例如 `throw` 或 `-ErrorAction Stop` ），或執行與<kbd>Ctrl</kbd> - <kbd>C</kbd>中斷時，就會傳回值1。

_只有_ 在從另一個 PowerShell 主機執行 **PowerShell.exe** 時才有可能。
**ScriptBlock** 類型可以包含在現有的變數中，從運算式傳回，或由 PowerShell 主機剖析為以大括弧括住的常值腳本區塊 `{}` ，然後再傳遞至 **PowerShell.exe** 。

在 **cmd.exe** 中，沒有腳本區塊 (或 **ScriptBlock** 類型) 的這種情況，因此傳遞給 **命令** 的值 _一律_ 會是字串。 您可以在字串內撰寫指令碼區塊，但它不會執行，其行為完全就像您在一般 PowerShell 提示字元中輸入它一樣，將指令碼區塊的內容印回給您。

傳遞給 **命令** 的字串仍會以 PowerShell 的形式執行，因此從 **cmd.exe** 執行時，通常不需要腳本區塊大括弧。 若要執行在字串內定義的內嵌腳本區塊，可以使用[呼叫運算子](about_operators.md#special-operators) 
 `&` ：

```console
"& {<command>}"
```

#### <a name="-help---"></a>-Help, -?, /?

顯示 **PowerShell.exe** 的說明。 如果您在 PowerShell 會話中輸入 **PowerShell.exe** 命令，請在命令參數前面加上連字號 ( ) ，而不是正斜線 (/) 。 您可以在 **cmd.exe** 中使用連字號或正斜線。

### <a name="remarks"></a>REMARKS

疑難排解注意事項：在 PowerShell 2.0 中，從 PowerShell 主控台啟動某些程式會失敗，並出現 **LastExitCode** 的0xc0000142。

### <a name="examples"></a>範例

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
