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

參數會以常值字串形式 (經過目前的殼層解譯後) 傳遞至指令碼。 例如，如果您在 cmd.exe 中且想要傳遞環境變數值，您會使用 cmd.exe 語法：`powershell.exe -File .\test.ps1 -TestParam %windir%`

相較之下，在 cmd.exe 中執行 `powershell.exe -File .\test.ps1 -TestParam $env:windir` 會導致指令碼接收常值字串 `$env:windir`，因為它對於目前的 cmd.exe 殼層沒有任何特殊意義。
環境變數參考的 `$env:windir` 樣式「可以」在 `-Command` 參數內部使用，因為它將在該處解譯為 PowerShell 程式碼。

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
執行之後，除非指定了 **NoExit** 參數，否則 PowerShell 就會結束。
`-Command` 之後的任何文字都會以單一命令列形式傳送至 PowerShell。
這與 `-File` 處理要傳送至指令碼之參數的方法不同。

`-Command` 的值可以是 "-"、字串或指令碼區塊。
命令的結果會當做已還原序列化的 XML 物件 (而不是即時物件) 傳回到父殼層。

如果 `-Command` 的值是 "-"，則會從標準輸入讀取命令文字。

當 `-Command` 的值是字串時，**Command**「必須」是指定的最後一個參數，因為在命令後輸入的任何字元皆會解譯為命令引數。

**Command** 參數只會在它可將傳遞給 `-Command` 的值辨識為 ScriptBlock 類型時，接受指令碼區塊執行。
這「只有」在從另一部 PowerShell 主機執行 PowerShell.exe 時才可行。
ScriptBlock 類型可能包含於現有的變數中、從運算式傳回，或透過 PowerShell 主機剖析為常值指令碼區塊 (以大括號 `{}` 括住)，之後才能傳遞給 PowerShell.exe。

在 cmd.exe 中，沒有指令碼區塊 (或 ScriptBlock 類型) 之類的項目，因此傳遞給 **Command** 的值將「一律」為字串。
您可以在字串內撰寫指令碼區塊，但它不會執行，其行為完全就像您在一般 PowerShell 提示字元中輸入它一樣，將指令碼區塊的內容印回給您。

傳遞給 `-Command` 的字串仍會以 PowerShell 執行，因此，一開始從 cmd.exe 執行時通常不需要指令碼區塊大括號。
若要執行字串內定義的內嵌指令碼區塊，可以使用[呼叫運算子](/powershell/module/microsoft.powershell.core/about/about_operators#call-operator-)`&`：

```console
"& {<command>}"
```

### <a name="-help---"></a>-Help, -?, /?

顯示 powershell.exe 的語法。 若要在 PowerShell 中鍵入 PowerShell.exe 命令，命令參數之前要加上連字號 (-)，而不是正斜線 (/)。 在 Cmd.exe 中，您可以使用連字號或正斜線。

> [!NOTE]
> 疑難排解注意事項：在 PowerShell 2.0，於 Windows PowerShell 主控台中啟動某些程式會失敗，LastExitCode 為 0xc0000142。

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
