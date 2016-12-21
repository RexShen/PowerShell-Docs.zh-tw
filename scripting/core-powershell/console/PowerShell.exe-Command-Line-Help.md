---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: "PowerShell.exe 命令列說明"
ms.technology: powershell
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 609682294c344129f96afd0241116bb19154d19e
ms.sourcegitcommit: 8acbf9827ad8f4ef9753f826ecaff58495ca51b0
translationtype: HT
---
# <a name="powershellexe-command-line-help"></a>PowerShell.exe 命令列說明
啟動 Windows PowerShell 工作階段。 您可以使用 PowerShell.exe 從其他工具的命令列 (例如 Cmd.exe) 啟動 Windows PowerShell 工作階段，或在 Windows PowerShell 命令列中使用以啟動新的工作階段。 使用參數可自訂工作階段。

## <a name="syntax"></a>語法

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

## <a name="parameters"></a>參數

### <a name="-encodedcommand-base64encodedcommand"></a>-EncodedCommand <Base64EncodedCommand>
接受 Base-64 編碼字串版本的命令。 使用此參數送出命令至要求要有複雜引號或大括弧的 Windows PowerShell。

### <a name="-executionpolicy-executionpolicy"></a>-ExecutionPolicy <ExecutionPolicy>
設定目前工作階段的預設執行原則並且儲存至 $env:PSExecutionPolicyPreference 環境變數中。 此參數不會變更已在登錄中設定的 Windows PowerShell 執行原則。 如需 Windows PowerShell 執行原則的資訊，包括有效值清單，請參閱 about_Execution_Policies (http://go.microsoft.com/fwlink/?LinkID=135170)。

### <a name="-file-filepath-parameters"></a>-File <FilePath> \[<Parameters>]
在本機領域 (「點來源」) 執行指定指令碼，讓指令碼建立的函式和變數在目前的工作階段可用。 輸入指令碼檔案路徑和任何參數。 **File** 必須是命令中的最後一個參數，因為在 **File** 參數名稱後輸入的所有字元，會解譯為後面加上指令碼參數及其值的指令碼檔案路徑。

您可以將指令碼的參數和參數值包含在 **File** 參數的值中。 例如：`-File .\Get-Script.ps1 -Domain Central`

一般而言，指令碼的切換參數可以包含或省略。 例如，下列命令會使用 Get-Script.ps1 指令碼檔案的 **All** 參數：`-File .\Get-Script.ps1 -All`

在罕見的情況下，您可能需要提供切換參數的布林值。 若要在 **File** 參數的值中提供切換參數值的布林值，請以大括弧括住參數名稱和值，如下所示︰`-File .\Get-Script.ps1 {-All:$False}`

### <a name="-inputformat-text--xml"></a>-InputFormat {Text | XML}
描述傳送至 Windows PowerShell 的資料格式。 有效值為 "Text" (文字字串) 或 "XML" (序列化的 CLIXML 格式)。

### <a name="-mta"></a>-Mta
使用多執行緒 Apartment 啟動 Windows PowerShell。 此參數是在 Windows PowerShell 3.0 引進。 在 Windows PowerShell 3.0 中，單一執行緒 Apartment (STA) 是預設值。 在 Windows PowerShell 2.0 中，多執行緒 Apartment (MTA) 是預設值。

### <a name="-noexit"></a>-NoExit
執行啟動命令後不要結束。

### <a name="-nologo"></a>-NoLogo
啟動時隱藏著作權橫幅。

### <a name="-noninteractive"></a>-NonInteractive
不向使用者顯示互動式提示。

### <a name="-noprofile"></a>-NoProfile
不載入 Windows PowerShell 設定檔。

### <a name="-outputformat-text--xml"></a>-OutputFormat {Text | XML}
決定 Windows PowerShell 的輸出格式。 有效值為 "Text" (文字字串) 或 "XML" (序列化的 CLIXML 格式)。

### <a name="-psconsolefile-filepath"></a>-PSConsoleFile <FilePath>
載入指定的 Windows PowerShell 主控台檔案。 輸入主控台檔案的路徑和名稱。 若要建立主控台檔案，請在 Windows PowerShell 中使用 [Export-Console](https://technet.microsoft.com/en-us/library/4bab1c02-9e61-4aaf-9957-11d1934ef4ef) Cmdlet。

### <a name="-sta"></a>-Sta
使用單一執行緒 Apartment 啟動 Windows PowerShell。 在 Windows PowerShell 3.0 中，單一執行緒 Apartment (STA) 是預設值。 在 Windows PowerShell 2.0 中，多執行緒 Apartment (MTA) 是預設值。

### <a name="-version-windows-powershell-version"></a>-Version <Windows PowerShell Version>
啟動指定的 Windows PowerShell 版本。 您指定的版本必須安裝在系統上。 如果 Windows PowerShell 3.0 已安裝於電腦上，有效值為 "2.0" 和 "3.0"。 預設值為 "3.0"。

如果未安裝 Windows PowerShell 3.0，唯一有效的值為 "2.0"。 其他值會被忽略。

如需詳細資訊，請參閱[開始使用 Windows PowerShell [舊版 MSDN]](https://technet.microsoft.com/en-us/library/69555d95-b481-43e1-86e7-b46d68b3e2dd)中的＜安裝 Windows PowerShell＞。

### <a name="-windowstyle-window-style"></a>-WindowStyle <Window style>
設定工作階段的視窗樣式。 有效值為 Normal、Minimized、Maximized 和 Hidden。

### <a name="-command"></a>-Command
就如同在 Windows PowerShell 命令提示字元輸入一樣，執行指定的命令 (和任何參數)，然後結束，除非指定了 NoExit 參數。

Command 的值可以是 "-"、字串。 或指令碼區塊。 如果 Command 的值是 "-"，則會從標準輸入讀取命令文字。

指令碼區塊必須以大括弧 ({}) 括住。 只有在 Windows PowerShell 中執行 PowerShell.exe 時，您才可以指定指令碼區塊。 指令碼的結果會當做已還原序列化的 XML 物件 (而不是即時物件) 傳回到父殼層。

如果 Command 的值是字串，**Command** 必須是命令中的最後一個參數，因為在命令後輸入的任何字元，會解譯為命令引數。

若要寫入執行 Windows PowerShell 命令的字串，請使用下列格式︰

```
"& {<command>}"
```

其中的引號代表字串，它會呼叫 (&) 運算子，使命令執行。

### <a name="-help---"></a>-Help, -?, /?
顯示此訊息。 如果您正在 Windows PowerShell 中輸入 PowerShell.exe 命令，命令參數之前要加上連字號 (-)，而不是正斜線 (/)。 在 Cmd.exe 中，您可以使用連字號或正斜線。

> [!NOTE]
> 疑難排解注意事項︰在 Windows PowerShell 2.0 中，啟動 Windows PowerShell 主控台中的某些程式會失敗，LastExitCode 為 0xc0000142。

## <a name="examples"></a>範例

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

