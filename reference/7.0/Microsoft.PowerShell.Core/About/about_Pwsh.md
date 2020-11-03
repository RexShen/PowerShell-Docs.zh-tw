---
description: 說明如何使用 `pwsh` 命令列介面。 顯示命令列參數並描述語法。
keywords: powershell,cmdlet
ms.date: 10/05/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pwsh?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Pwsh
ms.openlocfilehash: 2aa1c4ec033b8e7294c269b53c4fe20205a47d7f
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207827"
---
# <a name="about-pwsh"></a>關於 pwsh

## <a name="short-description"></a>簡短描述
說明如何使用 `pwsh` 命令列介面。 顯示命令列參數並描述語法。

## <a name="long-description"></a>完整描述

## <a name="syntax"></a>語法

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

## <a name="parameters"></a>參數

所有參數都不區分大小寫。

### <a name="-file---f"></a>-File |-f

如果的值 `File` 為 `-` ，則會從標準輸入讀取命令文字。
如果 `pwsh -File -` 執行時沒有重新導向的標準輸入，則會啟動一般會話。 這與完全不指定 `File` 參數相同。

如果沒有任何參數存在，但命令列中有值，則這是預設參數。 指定的腳本會在區域範圍中執行 ( 「點來源」 ) ，如此腳本所建立的函式和變數就會在目前的會話中使用。 輸入指令碼檔案路徑和任何參數。 File 必須是命令中的最後一個參數，因為在檔案參數名稱之後輸入的所有字元都會被解釋為腳本檔案路徑，後面接著腳本參數。

一般而言，指令碼的切換參數可以包含或省略。
例如，下列命令會使用 Get-Script.ps1 腳本檔案的 All 參數： `-File .\Get-Script.ps1 -All`

在罕見的情況下，您可能需要提供切換參數的 **布林** 值。 若要在 **File** 參數的值中提供切換參數的 **布林** 值，請使用通常緊接在冒號和布林值的參數，如下所示： `-File .\Get-Script.ps1 -All:$False` 。

參數會以常值字串形式 (經過目前的殼層解譯後) 傳遞至指令碼。 例如，如果您在中， `cmd.exe` 而且想要傳遞環境變數值，您可以使用 `cmd.exe` 下列語法： `pwsh -File .\test.ps1 -TestParam %windir%`

相反地，在 `pwsh -File .\test.ps1 -TestParam $env:windir` `cmd.exe` 接收常值字串的腳本中執行會產生， `$env:windir` 因為它對目前的 shell 沒有任何特殊意義 `cmd.exe` 。 `$env:windir`環境變數參考的樣式 _可以_ 在 **命令** 參數中使用，因為它會被視為 PowerShell 程式碼。

同樣地，如果您想要從 _批次腳本_ 執行相同的命令，您可以使用 `%~dp0` 而 `.\` 非 `$PSScriptRoot` 或來表示目前的執行目錄： `pwsh -File %~dp0test.ps1 -TestParam %windir%` 。 如果您改 `.\test.ps1` 為使用，則 PowerShell 會擲回錯誤，因為它找不到常值路徑 `.\test.ps1`

當腳本檔案以命令結束時 `exit` ，進程結束代碼會設定為與命令搭配使用的數值引數 `exit` 。 使用正常終止時，結束代碼一律為 `0` 。

類似于 `-Command` ，當腳本終止錯誤發生時，結束代碼會設定為 `1` 。 不過，與不同的是 `-Command` ，當使用<kbd>Ctrl</kbd>C 中斷執行時，結束 - <kbd>C</kbd>代碼為 `0` 。

### <a name="-command---c"></a>-Command |-c

執行指定的命令 (和任何參數) 如同在 PowerShell 命令提示字元中輸入，然後結束，除非 `NoExit` 指定了參數。

**命令** 的值可以是 `-` 、腳本區塊或字串。 如果 **command** 的值為 `-` ，則會從標準輸入讀取命令文字。

**命令** 參數只接受腳本區塊，以便在可辨識傳遞給 **命令** 的值做為 **ScriptBlock** 類型時執行。 _只有_ `pwsh` 從另一個 PowerShell 主機執行時，才有可能發生此情況。 **ScriptBlock** 類型可以包含在現有的變數中，從運算式傳回，或由 PowerShell 主機剖析為常值腳本區塊（以大括弧括住 (`{}`) ），然後再傳遞至 `pwsh` 。

```powershell
pwsh -Command {Get-WinEvent -LogName security}
```

在中 `cmd.exe` ，沒有腳本區塊 (或 **ScriptBlock** 類型) ，因此傳遞給 **命令** 的值 _一律_ 會是字串。 您可以在字串內撰寫指令碼區塊，但它不會執行，其行為完全就像您在一般 PowerShell 提示字元中輸入它一樣，將指令碼區塊的內容印回給您。

傳遞給 **命令** 的字串仍會以 PowerShell 程式碼的形式執行，因此從執行時，在第一個位置通常不需要腳本區塊大括弧 `cmd.exe` 。 若要執行字串內定義的內嵌指令碼區塊，可以使用[呼叫運算子](about_operators.md#special-operators) `&`：

```
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

### <a name="-configurationname---config"></a>-ConfigurationName |-config

指定 PowerShell 執行所在的設定端點。 這可以是在本機電腦上註冊的任何端點，包括預設的 PowerShell 遠端端點，或具有特定使用者角色功能的自訂端點。

範例： `pwsh -ConfigurationName AdminRoles`

### <a name="-custompipename"></a>-CustomPipeName

指定要用於額外的 IPC 伺服器 (具名管道) 用於偵錯工具和其他跨進程通訊的名稱。 這會提供可預測的機制，以連接到其他 PowerShell 實例。 通常搭配上的 **CustomPipeName** 參數使用 `Enter-PSHostProcess` 。

此參數是在 PowerShell 6.2 中引進。

例如：

```powershell
# PowerShell instance 1
pwsh -CustomPipeName mydebugpipe
# PowerShell instance 2
Enter-PSHostProcess -CustomPipeName mydebugpipe
```

### <a name="-encodedcommand---e---ec"></a>-EncodedCommand |-e |-ec

接受 Base64 編碼字串版本的命令。 使用這個參數將命令提交至需要複雜、嵌套引號的 PowerShell。 Base64 標記法必須是 UTF-16 編碼的字串。

例如：

```powershell
$command = 'dir "c:\program files" '
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
pwsh -encodedcommand $encodedCommand
```

### <a name="-executionpolicy---ex---ep"></a>-ExecutionPolicy |-ex |-ep

設定目前會話的預設執行原則，並將它儲存在 `$env:PSExecutionPolicyPreference` 環境變數中。 此參數不會變更持續設定的執行原則。

此參數只適用于 Windows 電腦。 `$env:PSExecutionPolicyPreference`環境變數不存在於非 Windows 平臺上。

### <a name="-inputformat---inp---if"></a>-InputFormat |-sct.inp |-如果

描述傳送至 PowerShell 的資料格式。 有效值為 "Text" (文字字串) 或 "XML" (序列化的 CLIXML 格式)。

### <a name="-interactive---i"></a>-Interactive |-i

向使用者顯示互動式提示。 非互動式參數的反向。

### <a name="-login---l"></a>-Login |-l

在 Linux 和 macOS 上，使用/bin/sh 來執行登入設定檔（例如/etc/profile 和 ~/.profile.），以登入命令介面啟動 PowerShell
在 Windows 上，此參數不會執行任何動作。

> [!IMPORTANT]
> 此參數必須先開始，才能以登入命令介面啟動 PowerShell。
> 在另一個位置傳遞這個參數將會被忽略。

若要 `pwsh` 在類似 UNIX 的作業系統上設定為登入命令介面：

- 確認的完整絕對路徑 `pwsh` 列在 `/etc/shells`
  - 此路徑通常類似于 `/usr/bin/pwsh` Linux 或 `/usr/local/bin/pwsh` macOS
  - 使用某些安裝方法時，會在安裝時自動新增此專案
  - 如果 `pwsh` 不存在於中 `/etc/shells` ，請使用編輯器將路徑附加到 `pwsh` 最後一行。 這需要較高的許可權才能編輯。
- 使用 [chsh](https://linux.die.net/man/1/chsh) 公用程式，將您目前使用者的 shell 設定為 `pwsh` ：

  ```sh
  chsh -s /usr/bin/pwsh
  ```

> [!WARNING]
> `pwsh`Windows 子系統 Linux 版 (WSL) 上目前不支援設定為登入 shell，而且嘗試設定 `pwsh` 為登入命令介面，可能會導致無法以互動方式啟動 WSL。

### <a name="-mta"></a>-MTA

使用多執行緒的單元啟動 PowerShell。 這個參數只能在 Windows 上使用。

### <a name="-noexit---noe"></a>-NoExit |-noe

執行啟動命令後不要結束。

範例： `pwsh -NoExit -Command Get-Date`

### <a name="-nologo---nol"></a>-NoLogo |-nol

在互動式會話啟動時隱藏著作權橫幅。

### <a name="-noninteractive---noni"></a>-非互動式 |-noni

不向使用者顯示互動式提示。 任何嘗試使用互動式功能（例如 `Read-Host` 或確認提示）都會導致語句終止錯誤。

### <a name="-noprofile---nop"></a>-NoProfile |-nop

不會載入 PowerShell 設定檔。

### <a name="-outputformat---o---of"></a>->outputformat |-o |-/

決定 PowerShell 的輸出格式。 有效值為 "Text" (文字字串) 或 "XML" (序列化的 CLIXML 格式)。

範例： `pwsh -o XML -c Get-Date`

當呼叫遷移 PowerShell 會話時，您會取得還原序列化的物件，做為輸出，而不是純文字字串。 從其他 shell 呼叫時，輸出是格式化為 CLIXML 文字的字串資料。

### <a name="-settingsfile---settings"></a>-SettingsFile |-設定

覆寫會話的全系統 `powershell.config.json` 設定檔案。 根據預設，系統會從目錄中讀取整個系統的設定 `powershell.config.json` `$PSHOME` 。

請注意，引數所指定的端點不會使用這些設定 `-ConfigurationName` 。

範例： `pwsh -SettingsFile c:\myproject\powershell.config.json`

### <a name="-sshservermode---sshs"></a>-SSHServerMode |-sshs

用於以 SSH 子系統的形式執行 PowerShell 的 sshd_config。 不適合或不支援任何其他用途。

### <a name="-sta"></a>-STA

使用單一執行緒的單元啟動 PowerShell。 這是預設值。 這個參數只能在 Windows 上使用。

### <a name="-version---v"></a>-Version |-v

顯示 PowerShell 的版本。 系統會忽略其他參數。

### <a name="-windowstyle---w"></a>-System.windows.window.windowstyle |-w

設定工作階段的視窗樣式。 有效值為 Normal、Minimized、Maximized 和 Hidden。

### <a name="-workingdirectory---wd"></a>-WorkingDirectory |-wd

藉由在啟動時執行來設定初始工作目錄。 支援任何有效的 PowerShell 檔案路徑。

若要在主目錄中啟動 PowerShell，請使用： `pwsh -WorkingDirectory ~`

### <a name="-help---"></a>-Help, -?, /?

顯示的說明 `pwsh` 。 如果您在 PowerShell 中輸入 pwsh 命令，請在命令參數前面加上連字號 (`-`) ，而不是正斜線 (`/`) 。
