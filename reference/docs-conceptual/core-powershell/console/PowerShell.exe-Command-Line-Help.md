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
# <a name="powershellexe-command-line-help"></a>PowerShell.exe 命令列說明

您可以使用 PowerShell.exe 從其他工具的命令列 (例如 Cmd.exe) 啟動 PowerShell 工作階段，或在 PowerShell 命令列中使用以啟動新的工作階段。 使用參數可自訂工作階段。

## <a name="syntax"></a>語法

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

## <a name="parameters"></a>參數

### <a name="-encodedcommand-base64encodedcommand"></a>-EncodedCommand <Base64EncodedCommand>

接受 Base-64 編碼字串版本的命令。 使用此參數以將命令傳送至要求複雜引號或大括弧的 Windows PowerShell。

### <a name="-executionpolicy-executionpolicy"></a>-ExecutionPolicy <ExecutionPolicy>

設定目前工作階段的預設執行原則並且儲存至 $env:PSExecutionPolicyPreference 環境變數中。 此參數不會變更已在登錄中設定的 PowerShell 執行原則。 如需 PowerShell 執行原則的資訊，包括有效值清單，請參閱 [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies)。

### <a name="-file-filepath-parameters"></a>-File <FilePath> \[<Parameters>]

在本機領域 (「點來源」) 執行指定指令碼，讓指令碼建立的函式和變數在目前的工作階段可用。 輸入指令碼檔案路徑和任何參數。 **File** 必須是命令中的最後一個參數。 在 **-File** 參數之後輸入的所有值都會解譯為指令碼檔案路徑以及要傳遞給該指令碼的參數。

參數會以常值字串形式 (經過目前的殼層解譯後) 傳遞至指令碼。 例如，如果您在 cmd.exe 中，並想要傳遞環境變數值，您會使用 cmd.exe 語法： `powershell.exe -File .\test.ps1 -TestParam %windir%`

相較之下，執行`powershell.exe -File .\test.ps1 -TestParam $env:windir`接收的常值字串的指令碼中的 cmd.exe 結果中`$env:windir`因為它沒有任何特殊的意義，到目前的 cmd.exe 殼層。
`$env:windir`環境變數參考的樣式_可以_能在內部使用`-Command`參數，因為那里將被解譯為 PowerShell 程式碼。

### <a name="-inputformat-text--xml"></a>\-InputFormat {Text | XML}

描述傳送至 PowerShell 的資料格式。 有效值為 "Text" (文字字串) 或 "XML" (序列化的 CLIXML 格式)。

### <a name="-mta"></a>-Mta

使用多執行緒 Apartment 啟動 PowerShell。 此參數在 PowerShell 3.0 中引進。 在 PowerShell 3.0 中，預設為單一執行緒 Apartment (STA)。 在 PowerShell 2.0 中，預設為多執行緒 Apartment (MTA)。

### <a name="-noexit"></a>-NoExit

執行啟動命令後不要結束。

### <a name="-nologo"></a>-NoLogo

啟動時隱藏著作權橫幅。

### <a name="-noninteractive"></a>-NonInteractive

不向使用者顯示互動式提示。

### <a name="-noprofile"></a>-NoProfile

不載入 PowerShell 設定檔。

### <a name="-outputformat-text--xml"></a>-OutputFormat {Text | XML}

決定 PowerShell 的輸出格式。 有效值為 "Text" (文字字串) 或 "XML" (序列化的 CLIXML 格式)。

### <a name="-psconsolefile-filepath"></a>-PSConsoleFile <FilePath>

載入指定的 PowerShell 主控台檔案。 輸入主控台檔案的路徑和名稱。 若要建立主控台檔案，請在 PowerShell 中使用 [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) Cmdlet。

### <a name="-sta"></a>-Sta

使用單一執行緒 Apartment 啟動 PowerShell。 在 PowerShell 3.0 中，預設為單一執行緒 Apartment (STA)。 在 PowerShell 2.0 中，預設為多執行緒 Apartment (MTA)。

### <a name="-version-powershell-version"></a>-Version <PowerShell Version>

啟動指定版本的 PowerShell。 您指定的版本必須安裝在系統上。 如果 PowerShell 3.0 已安裝於電腦上，有效值為 "2.0" 和 "3.0"。 預設值為 "3.0"。

如果未安裝 PowerShell 3.0，唯一有效的值為 "2.0"。 其他值會被忽略。

如需詳細資訊，請參閱[安裝 Windows PowerShell](../../setup/installing-windows-powershell.md)。

### <a name="-windowstyle-window-style"></a>-WindowStyle <Window style>

設定工作階段的視窗樣式。 有效值為 Normal、Minimized、Maximized 與 Hidden。

### <a name="-command"></a>-Command

執行指定的命令 (搭配任何參數)，就如同在 PowerShell 命令提示字元中輸入它們一樣。
執行之後，PowerShell 會結束除非**NoExit**指定參數。
`-Command` 之後的任何文字都會以單一命令列形式傳送至 PowerShell。
這與 `-File` 處理要傳送至指令碼之參數的方法不同。

值`-Command`可以是"-"、 字串或指令碼區塊。
命令的結果會回到父殼層為已還原序列化的 XML 物件，不是即時物件。

如果值`-Command`是"-"，從標準輸入讀取命令文字。

當 windows 7`-Command`是一個字串，**命令**_必須_是最後一個命令會被解譯為命令引數之後輸入的任何字元，因此指定的參數。

**命令**參數只接受執行指令碼區塊，就可以識別傳遞給的值時`-Command`做為指令碼區塊類型。
這是_只_可能從另一個 PowerShell 主機中執行 PowerShell.exe 時。
裝載為常值的指令碼區塊，大括號括住的類型可能包含在現有的變數，傳回運算式，或剖析的 powershell 指令碼區塊`{}`，才能傳遞至 PowerShell.exe。

在 cmd.exe，沒有這類的指令碼區塊中 （或指令碼區塊型別），因此值傳遞給**命令**會_一律_是字串。
您可以撰寫指令碼區塊內的字串，但是而不是正在執行它的行為與完全如同您在一般的 PowerShell 提示字元下輸入，指令碼的內容列印封鎖回給您。

字串傳遞至`-Command`仍然會執行 powershell，因此指令碼區塊大括號通常不需要在一開始從 cmd.exe 執行時。
若要執行內的字串，定義為內嵌指令碼區塊[呼叫運算子](/powershell/module/microsoft.powershell.core/about/about_operators#call-operator-)`&`可用：

```console
"& {<command>}"
```

### <a name="-help---"></a>-Help, -?, /?

顯示 powershell.exe 的語法。 若要在 PowerShell 中鍵入 PowerShell.exe 命令，命令參數之前要加上連字號 (-)，而不是正斜線 (/)。 在 Cmd.exe 中，您可以使用連字號或正斜線。

> [!NOTE]
> 疑難排解注意事項︰在 PowerShell 2.0 中，啟動 Windows PowerShell 主控台中的某些程式會失敗，LastExitCode 為 0xc0000142。

## <a name="examples"></a>範例

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
