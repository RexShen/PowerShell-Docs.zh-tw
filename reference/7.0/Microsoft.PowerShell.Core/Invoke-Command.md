---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/invoke-command?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-Command
ms.openlocfilehash: b4e065ba0055c43a0ab4475878a049e4f9fde3e2
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205708"
---
# Invoke-Command

## 概要
在本機與遠端電腦上執行命令。

## SYNTAX

###  (預設) 的進程

```
Invoke-Command [-ScriptBlock] <ScriptBlock> [-NoNewScope] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### FilePathRunspace

```
Invoke-Command [[-Session] <PSSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-FilePath] <String> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### 工作階段

```
Invoke-Command [[-Session] <PSSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-ScriptBlock] <ScriptBlock> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### FilePathComputerName

```
Invoke-Command [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-Port <Int32>] [-UseSSL]
 [-ConfigurationName <String>] [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-AsJob]
 [-InDisconnectedSession] [-SessionName <String[]>] [-HideComputerName] [-JobName <String>]
 [-FilePath] <String> [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-EnableNetworkAccess] [-RemoteDebug] [-InputObject <PSObject>] [-ArgumentList <Object[]>]
 [<CommonParameters>]
```

### ComputerName

```
Invoke-Command [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-Port <Int32>] [-UseSSL]
 [-ConfigurationName <String>] [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-AsJob]
 [-InDisconnectedSession] [-SessionName <String[]>] [-HideComputerName] [-JobName <String>]
 [-ScriptBlock] <ScriptBlock> [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-EnableNetworkAccess] [-RemoteDebug]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

### Uri

```
Invoke-Command [-Credential <PSCredential>] [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [[-ConnectionUri] <Uri[]>] [-AsJob] [-InDisconnectedSession] [-HideComputerName]
 [-JobName <String>] [-ScriptBlock] <ScriptBlock> [-AllowRedirection]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-EnableNetworkAccess] [-RemoteDebug] [-InputObject <PSObject>] [-ArgumentList <Object[]>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### FilePathUri

```
Invoke-Command [-Credential <PSCredential>] [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [[-ConnectionUri] <Uri[]>] [-AsJob] [-InDisconnectedSession] [-HideComputerName]
 [-JobName <String>] [-FilePath] <String> [-AllowRedirection] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-EnableNetworkAccess] [-RemoteDebug]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### VMId

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-ScriptBlock] <ScriptBlock> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [-VMId] <Guid[]> [<CommonParameters>]
```

### VMName

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-ScriptBlock] <ScriptBlock> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] -VMName <String[]> [<CommonParameters>]
```

### FilePathVMId

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-FilePath] <String> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [-VMId] <Guid[]> [<CommonParameters>]
```

### FilePathVMName

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-FilePath] <String> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] -VMName <String[]> [<CommonParameters>]
```

### SSHHost

```
Invoke-Command [-Port <Int32>] [-AsJob] [-HideComputerName] [-JobName <String>]
 [-ScriptBlock] <ScriptBlock> -HostName <String[]> [-UserName <String>] [-KeyFilePath <String>]
 [-SSHTransport] [-RemoteDebug] [-InputObject <PSObject>] [-ArgumentList <Object[]>]
 [-Subsystem <String>] [<CommonParameters>]
```

### ContainerId

```
Invoke-Command [-ConfigurationName <String>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-ScriptBlock] <ScriptBlock> [-RunAsAdministrator] [-RemoteDebug]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] -ContainerId <String[]> [<CommonParameters>]
```

### FilePathContainerId

```
Invoke-Command [-ConfigurationName <String>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-FilePath] <String> [-RunAsAdministrator] [-RemoteDebug]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] -ContainerId <String[]> [<CommonParameters>]
```

### SSHHostHashParam

```
Invoke-Command [-AsJob] [-HideComputerName] [-JobName <String>] [-ScriptBlock] <ScriptBlock>
 -SSHConnection <Hashtable[]> [-RemoteDebug] [-InputObject <PSObject>] [-ArgumentList <Object[]>]
 [<CommonParameters>]
```

### FilePathSSHHost

```
Invoke-Command [-AsJob] [-HideComputerName] -FilePath <String> -HostName <String[]>
 [-UserName <String>] [-KeyFilePath <String>] [-SSHTransport] [-RemoteDebug]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### FilePathSSHHostHash

```
Invoke-Command [-AsJob] [-HideComputerName] -FilePath <String> -SSHConnection <Hashtable[]>
 [-RemoteDebug] [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

## DESCRIPTION

此 `Invoke-Command` Cmdlet 會在本機或遠端電腦上執行命令，並傳回來自命令的所有輸出，包括錯誤。 `Invoke-Command`您可以使用單一命令，在多部電腦上執行命令。

若要在遠端電腦上執行單一命令，請使用 **ComputerName** 參數。 若要執行一系列共用資料的相關命令，請使用 `New-PSSession` Cmdlet 在遠端電腦上建立 (持續連線) 的 **PSSession** ，然後使用的 **Session** 參數 `Invoke-Command` 在 **PSSession** 中執行命令。 若要在中斷連線的工作階段中執行命令，請使用 **InDisconnectedSession** 參數。 若要在背景工作中執行命令，請使用 **AsJob** 參數。

您也可以使用 `Invoke-Command` 本機電腦上的腳本區塊做為命令。 PowerShell 會在目前範圍的子範圍內立即執行腳本區塊。

使用在 `Invoke-Command` 遠端電腦上執行命令之前，請先閱讀 [about_Remote](./About/about_Remote.md)。

從 PowerShell 6.0 開始，您可以使用安全殼層 (SSH) 來建立與在遠端電腦上叫用命令的連線。 SSH 必須安裝在本機電腦上，而且必須使用 PowerShell SSH 端點來設定遠端電腦。 以 SSH 為基礎之 PowerShell 遠端會話的優點是，它可以跨多個平臺運作， (Windows、Linux、macOS) 。 針對以 SSH 為基礎的會話，您可以使用 **HostName** 或 **SSHConnection** 參數來指定遠端電腦和相關的連接資訊。 如需有關如何設定 PowerShell SSH 遠端的詳細資訊，請參閱透過 [SSH 的 Powershell 遠端](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)功能。

某些程式碼範例會使用展開來縮減行長度。 如需詳細資訊，請參閱 [about_Splatting](./About/about_Splatting.md)。

## 範例

### 範例1：在伺服器上執行腳本

此範例會在 `Test.ps1` Server01 電腦上執行腳本。

```powershell
Invoke-Command -FilePath c:\scripts\test.ps1 -ComputerName Server01
```

**FilePath** 參數指定的腳本位於本機電腦上。 指令碼會在遠端電腦上執行，而結果則會傳回到本機電腦。

### 範例2：在遠端伺服器上執行命令

此範例會 `Get-Culture` 在 Server01 遠端電腦上執行命令。

```powershell
Invoke-Command -ComputerName Server01 -Credential Domain01\User01 -ScriptBlock { Get-Culture }
```

**ComputerName** 參數指定遠端電腦的名稱。 **Credential** 參數是用來在 Domain01\User01 的安全性內容中執行命令，這是具有執行命令之許可權的使用者。 **ScriptBlock** 參數指定要在遠端電腦上執行的命令。

為了回應，PowerShell 要求 User01 帳戶的密碼和驗證方法。
然後，它會在 Server01 電腦上執行命令並傳回結果。

### 範例3：在持續連接中執行命令

此範例會在 `Get-Culture` 名為 Server02 的遠端電腦上，使用持續連線在會話中執行相同的命令。

```powershell
$s = New-PSSession -ComputerName Server02 -Credential Domain01\User01
Invoke-Command -Session $s -ScriptBlock {Get-Culture}
```

此 `New-PSSession` Cmdlet 會在 Server02 遠端電腦上建立會話，並將它儲存在 `$s` 變數中。 一般來說，只有當您在遠端電腦上執行一連串命令時，才會建立會話。

此 `Invoke-Command` Cmdlet 會 `Get-Culture` 在 Server02 上執行命令。 **Session** 參數會指定儲存在變數中的會話 `$s` 。

在回應中，PowerShell 會在 Server02 電腦上的會話中執行命令。

### 範例4：使用會話來執行一系列共用資料的命令

這個範例會比較使用 **ComputerName** 和 **會話** 參數的效果 `Invoke-Command` 。 它示範如何使用工作階段來執行一系列共用相同資料的命令。

```powershell
Invoke-Command -ComputerName Server02 -ScriptBlock {$p = Get-Process PowerShell}
Invoke-Command -ComputerName Server02 -ScriptBlock {$p.VirtualMemorySize}
$s = New-PSSession -ComputerName Server02
Invoke-Command -Session $s -ScriptBlock {$p = Get-Process PowerShell}
Invoke-Command -Session $s -ScriptBlock {$p.VirtualMemorySize}
```

```Output
17930240
```

前兩個命令使用的 **ComputerName** 參數 `Invoke-Command` ，在 Server02 遠端電腦上執行命令。 第一個命令會使用 `Get-Process` Cmdlet 來取得遠端電腦上的 PowerShell 處理常式，並將它儲存在 `$p` 變數中。 第二個命令會取得 PowerShell 處理程序的 **VirtualMemorySize** 屬性值。

當您使用 **ComputerName** 參數時，PowerShell 會建立新的會話來執行命令。
當命令完成時，會話就會關閉。 `$p`變數是在一個連接中建立的，但不存在於為第二個命令所建立的連接中。

問題的解決方式是在遠端電腦上建立持續性會話，然後在相同的會話中執行這兩個命令。

此 `New-PSSession` Cmdlet 會在電腦 Server02 上建立持續性會話，並將會話儲存在 `$s` 變數中。 `Invoke-Command`接下來的幾行使用 **Session** 參數在相同的會話中執行這兩個命令。 因為這兩個命令都在相同的會話中執行，所以此值會維持作用中 `$p` 狀態。

### 範例5：輸入儲存在本機變數中的命令

這個範例示範如何建立一個命令，該命令會以腳本區塊的形式儲存在本機變數中。
當腳本區塊儲存在本機變數中時，您可以將變數指定為 **ScriptBlock** 參數的值。

```powershell
$command = { Get-WinEvent -LogName PowerShellCore/Operational |
  Where-Object {$_.Message -like "*certificate*"} }
Invoke-Command -ComputerName S1, S2 -ScriptBlock $command
```

`$command`變數 `Get-WinEvent` 會儲存格式化為腳本區塊的命令。 會 `Invoke-Command` 執行儲存在 `$command` S1 和 S2 遠端電腦上的命令。

### 範例6：在數部電腦上執行單一命令

此範例示範如何使用 `Invoke-Command` 在多部電腦上執行單一命令。

```powershell
$parameters = @{
  ComputerName = "Server01", "Server02", "TST-0143", "localhost"
  ConfigurationName = 'MySession.PowerShell'
  ScriptBlock = { Get-WinEvent -LogName PowerShellCore/Operational }
}
Invoke-Command @parameters
```

**ComputerName** 參數會指定以逗號分隔的電腦名稱稱清單。 電腦的清單包含 localhost 值（代表本機電腦）。 **ConfigurationName** 參數會指定替代的會話設定。 **ScriptBlock** 參數會執行 `Get-WinEvent` ，以從每一部電腦取得 PowerShellCore/Operational 事件記錄檔。

### 範例7：在多部電腦上取得主機程式的版本

此範例會取得在200遠端電腦上執行之 PowerShell 主機程式的版本。

```powershell
$version = Invoke-Command -ComputerName (Get-Content Machines.txt) -ScriptBlock {(Get-Host).Version}
```

由於只有一個命令執行，因此您不需要為每部電腦建立持續連線。 此命令是改用 **ComputerName** 參數來指出電腦。 為了指定電腦，它會使用 `Get-Content` Cmdlet 來取得 Machine.txt 檔案的內容，也就是電腦名稱稱的檔案。

此 `Invoke-Command` Cmdlet 會 `Get-Host` 在遠端電腦上執行命令。 它會使用點標記法來取得 PowerShell 主機的 **Version** 屬性。

這些命令會一次執行一個。 當命令完成時，所有電腦的命令輸出都會儲存在 `$version` 變數中。 輸出會包括資料的來源電腦名稱。

### 範例8：在數部遠端電腦上執行背景工作

此範例會在兩部遠端電腦上執行命令。 此 `Invoke-Command` 命令會使用 **AsJob** 參數，讓命令以背景工作的形式執行。 這些命令會在遠端電腦上執行，但是該作業存在於本機電腦上。 結果會傳輸到本機電腦。

```powershell
$s = New-PSSession -ComputerName Server01, Server02
Invoke-Command -Session $s -ScriptBlock {Get-EventLog system} -AsJob
```

```Output
Id   Name    State      HasMoreData   Location           Command
---  ----    -----      -----         -----------        ---------------
1    Job1    Running    True          Server01,Server02  Get-EventLog system
```

```powershell
$j = Get-Job
$j | Format-List -Property *
```

```Output
HasMoreData   : True
StatusMessage :
Location      : Server01,Server02
Command       : Get-EventLog system
JobStateInfo  : Running
Finished      : System.Threading.ManualResetEvent
InstanceId    : e124bb59-8cb2-498b-a0d2-2e07d4e030ca
Id            : 1
Name          : Job1
ChildJobs     : {Job2, Job3}
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
StateChanged  :
```

```powershell
$results = $j | Receive-Job
```

此 `New-PSSession` Cmdlet 會在 Server01 和 Server02 遠端電腦上建立會話。 此 `Invoke-Command` Cmdlet 會在每個會話中執行背景工作。 此命令使用 **AsJob** 參數將命令當作背景工作來執行。 這個命令會傳回一個工作物件，其中包含兩個子工作物件，分別用於在兩部遠端電腦上執行的每個工作。

此 `Get-Job` 命令會將工作物件儲存在 `$j` 變數中。 然後，會使用管線 `$j` 將變數輸送到 `Format-List` Cmdlet，以顯示清單中工作物件的所有屬性。 最後一個命令會取得工作的結果。 它會以管線將工作物件傳送 `$j` 至 `Receive-Job` Cmdlet，並將結果儲存在 `$results` 變數中。

### 範例9：在遠端電腦上執行的命令中包含本機變數

這個範例示範如何將區域變數的值包含在遠端電腦上執行的命令中。 此命令會使用 `Using` 範圍修飾符來識別遠端命令中的本機變數。 預設會假設所有變數都已在遠端工作階段中定義。 `Using`範圍修飾詞是在 PowerShell 3.0 中引進。 如需範圍修飾符的詳細資訊 `Using` ，請參閱 [about_Remote_Variables](./About/about_Remote_Variables.md) 和 [about_Scopes](./about/about_scopes.md)。

```powershell
$Log = "PowerShellCore/Operational"
Invoke-Command -ComputerName Server01 -ScriptBlock {Get-WinEvent -LogName $Using:Log -MaxEvents 10}
```

`$Log`變數會儲存事件記錄檔（PowerShellCore/Operational）的名稱。 `Invoke-Command`Cmdlet 會 `Get-WinEvent` 在 Server01 上執行，以從事件記錄檔取得十個最新的事件。 **LogName** 參數的值是 `$Log` 前面加上範圍修飾符的變數， `Using` 表示它是在本機會話中建立，而不是在遠端會話中建立的。

### 範例10：隱藏電腦名稱稱

此範例顯示使用的 **HideComputerName** 參數的效果 `Invoke-Command` 。
**HideComputerName** 不會變更此 Cmdlet 所傳回的物件。 它只會變更顯示。 您仍然可以使用 **Format** Cmdlet 來顯示任何受影響物件的 **PsComputerName** 屬性。

```powershell
Invoke-Command -ComputerName S1, S2 -ScriptBlock {Get-Process PowerShell}
```

```Output
PSComputerName    Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id   ProcessName
--------------    -------  ------    -----      ----- -----   ------     --   -----------
S1                575      15        45100      40988   200     4.68     1392 PowerShell
S2                777      14        35100      30988   150     3.68     67   PowerShell
```

```powershell
Invoke-Command -ComputerName S1, S2 -ScriptBlock {Get-Process PowerShell} -HideComputerName
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id   ProcessName
-------  ------    -----      ----- -----   ------     --   -----------
575      15        45100      40988   200     4.68     1392 PowerShell
777      14        35100      30988   150     3.68     67   PowerShell
```

前兩個命令會用 `Invoke-Command` 來執行 `Get-Process` PowerShell 處理常式的命令。 第一個命令的輸出包括 **PsComputerName** 屬性，這包含命令執行所在的電腦名稱。 第二個命令的輸出（使用 **HideComputerName** ）不包含 **PsComputerName** 資料行。

### 範例11：在腳本區塊中使用 Param 關鍵字

`Param`關鍵字和 **ArgumentList** 參數是用來將變數值傳遞至腳本區塊中的具名引數。 此範例會顯示以字母開頭 `a` 且副檔名為的檔案名 `.pdf` 。

如需關鍵字的詳細資訊 `Param` ，請參閱 [about_Language_Keywords](./about/about_language_keywords.md#param)。

```powershell
$parameters = @{
    ComputerName = "Server01"
    ScriptBlock = { Param ($param1,$param2) Get-ChildItem -Name $param1 -Include $param2 }
    ArgumentList = "a*", "*.pdf"
}
Invoke-Command @parameters
```

```Output
aa.pdf
ab.pdf
ac.pdf
az.pdf
```

`Invoke-Command` 使用定義兩個變數的 **ScriptBlock** 參數： `$param1` 和 `$param2` 。 `Get-ChildItem` 使用具名引數、 **名稱** 和 **包含** 變數名稱。 **ArgumentList** 會將這些值傳遞給變數。

### 範例12：在腳本區塊中使用 $args 自動變數

`$args`自動變數和 **ArgumentList** 參數是用來將陣列值傳遞至腳本區塊中的參數位置。 此範例會顯示伺服器的目錄內容 `.txt` 。 `Get-ChildItem`**路徑** 參數為位置0，而 **篩選** 參數為位置
1.

如需變數的詳細資訊 `$args` ，請參閱 [about_Automatic_Variables](./about/about_automatic_variables.md#args)

```powershell
$parameters = @{
    ComputerName = "Server01"
    ScriptBlock = { Get-ChildItem $args[0] $args[1] }
    ArgumentList = "C:\Test", "*.txt*"
}
Invoke-Command @parameters
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           6/12/2019    15:15            128 alog.txt
-a---           7/27/2019    15:16            256 blog.txt
-a---           9/28/2019    17:10             64 zlog.txt
```

`Invoke-Command` 使用 **ScriptBlock** 參數，並 `Get-ChildItem` 指定 `$args[0]` 和 `$args[1]` 陣列值。 **ArgumentList** 會將 `$args` 陣列值傳遞給 `Get-ChildItem` **Path** 和 **Filter** 的參數位置。

### 範例13：在文字檔中列出的所有電腦上執行腳本

這個範例會使用 `Invoke-Command` Cmdlet，在檔案 `Sample.ps1` 中列出的所有電腦上執行腳本 `Servers.txt` 。 此命令使用 **FilePath** 參數來指定指令檔。 此命令可讓您在遠端電腦上執行腳本，即使遠端電腦無法存取腳本檔也是如此。

```powershell
Invoke-Command -ComputerName (Get-Content Servers.txt) -FilePath C:\Scripts\Sample.ps1 -ArgumentList Process, Service
```

當您提交命令時，會將檔案的內容 `Sample.ps1` 複製到腳本區塊中，而腳本區塊則會在每部遠端電腦上執行。 這個程序相當於使用 **ScriptBlock** 參數來送出指令碼的內容。

### 範例14：使用 URI 在遠端電腦上執行命令

此範例示範如何在遠端電腦上執行命令，該遠端電腦的 (URI) 的統一資源識別元。 這個特定的範例會 `Set-Mailbox` 在遠端 Exchange 伺服器上執行命令。

```powershell
$LiveCred = Get-Credential
$parameters = @{
  ConfigurationName = 'Microsoft.Exchange'
  ConnectionUri = 'https://ps.exchangelabs.com/PowerShell'
  Credential = $LiveCred
  Authentication = 'Basic'
  ScriptBlock = {Set-Mailbox Dan -DisplayName "Dan Park"}
}
Invoke-Command @parameters
```

第一行使用 Cmdlet 將 `Get-Credential` Windows LIVE ID 認證儲存在 `$LiveCred` 變數中。 PowerShell 會提示使用者輸入 Windows Live ID 認證。

`$parameters`變數是包含要傳遞給 Cmdlet 之參數的雜湊表 `Invoke-Command` 。 此 `Invoke-Command` Cmdlet 會 `Set-Mailbox` 使用 **Microsoft. Exchange** 會話設定來執行命令。 **ConnectionURI** 參數指定 Exchange 伺服器端點的 URL。 **Credential** 參數會指定儲存在變數中的認證 `$LiveCred` 。 **AuthenticationMechanism** 參數指定使用基本驗證。 **ScriptBlock** 參數指定包含命令的指令碼區塊。

### 範例15：使用會話選項

此範例顯示如何建立和使用 **SessionOption** 參數。

```powershell
$so = New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck
Invoke-Command -ComputerName server01 -UseSSL -ScriptBlock { Get-HotFix } -SessionOption $so -Credential server01\user01
```

此 `New-PSSessionOption` Cmdlet 會建立會話選項物件，此物件會導致遠端端點在評估連入的 HTTPS 連線時，不會驗證憑證授權單位單位、標準名稱和撤銷清單。 **SessionOption** 物件會儲存在變數中 `$so` 。

> [!NOTE]
> 停用這些檢查對於疑難排解很方便，但顯然並不安全。

`Invoke-Command`Cmdlet 會 `Get-HotFix` 從遠端執行命令。 提供變數給 **SessionOption** 參數 `$so` 。

### 範例16：管理遠端命令中的 URI 重新導向

此範例示範如何使用 **AllowRedirection** 和 **SessionOption** 參數來管理遠端命令中的 URI 重新導向。

```powershell
$max = New-PSSessionOption -MaximumRedirection 1
$parameters = @{
  ConnectionUri = "https://ps.exchangelabs.com/PowerShell"
  ScriptBlock = { Get-Mailbox dan }
  AllowRedirection = $true
  SessionOption = $max
}
Invoke-Command @parameters
```

此 `New-PSSessionOption` Cmdlet 會建立儲存在變數中的 **PSSessionOption** 物件 `$max` 。 此命令使用 **MaximumRedirection** 參數將 **PSSessionOption** 物件的 **MaximumConnectionRedirectionCount** 屬性設定為 1。

此 `Invoke-Command` Cmdlet 會 `Get-Mailbox` 在遠端 Microsoft Exchange 伺服器上執行命令。 **AllowRedirection** 參數提供明確的許可權，以將連接重新導向至替代端點。 **SessionOption** 參數會使用儲存在變數中的會話物件 `$max` 。

如此一來，如果 **ConnectionURI** 所指定的遠端電腦傳回重新導向訊息，則 PowerShell 會將連接重新導向，但是如果新的目的地傳回另一個重新導向訊息，則會超過重新導向計數值1，並傳回 `Invoke-Command` 非終止錯誤。

### 範例17：在遠端會話中存取網路共用

此範例說明如何從遠端會話存取網路共用。 使用三部電腦來示範範例。 Server01 是本機電腦、Server02 是遠端電腦，而 Net03 則包含網路共用。 Server01 會連線到 Server02，然後 Server02 會執行第二個躍點來 Net03 來存取網路共用。 如需 PowerShell 遠端功能如何支援電腦之間的躍點的詳細資訊，請參閱 [在 Powershell 遠端中進行第二個躍點](/powershell/scripting/learn/remoting/ps-remoting-second-hop)。

在本機電腦的用戶端設定中，以及遠端電腦上的服務設定中，已啟用必要的認證安全性支援提供者 (CredSSP) 委派。 若要執行此範例中的命令，您必須是本機電腦和遠端電腦上的 **Administrators** 群組成員。

```powershell
Enable-WSManCredSSP -Role Client -DelegateComputer Server02
$s = New-PSSession Server02
Invoke-Command -Session $s -ScriptBlock {Enable-WSManCredSSP -Role Server -Force}
$parameters = @{
  Session = $s
  ScriptBlock = { Get-Item \\Net03\Scripts\LogFiles.ps1 }
  Authentication = "CredSSP"
  Credential = "Domain01\Admin01"
}
Invoke-Command @parameters
```

此 `Enable-WSManCredSSP` Cmdlet 會啟用從 Server01 本機電腦至 Server02 遠端電腦的 CredSSP 委派。 **Role** 參數會指定 **用戶端** ，以在本機電腦上設定 CredSSP 用戶端設定。

`New-PSSession` 建立 Server02 的 **PSSession** 物件，並將物件儲存在 `$s` 變數中。

此 `Invoke-Command` Cmdlet 會使用 `$s` 變數來連線到遠端電腦 Server02。 **ScriptBlock** 參數會 `Enable-WSManCredSSP` 在遠端電腦上執行。 **Role** 參數指定要在遠端電腦上設定 CredSSP 伺服器設定的 **伺服器** 。

`$parameters`變數包含用來連接到網路共用的參數值。 Cmdlet 會在 `Invoke-Command` `Get-Item` 的會話中執行命令 `$s` 。 此命令會從 `\\Net03\Scripts` 網路共用取得腳本。 此命令會使用具有 **CredSSP** 值的 **驗證** 參數，並使用 **Domain01\Admin01** 的值來使用 **Credential** 參數。

### 範例18：在許多遠端電腦上啟動腳本

此範例會在一百部以上的電腦上執行腳本。 為了將對本機電腦的影響降到最低，它會連線到每一部電腦、啟動指令碼，然後再與每一部電腦中斷連線。
指令碼會繼續在中斷連線的工作階段中執行。

```powershell
$parameters = @{
  ComputerName = (Get-Content -Path C:\Test\Servers.txt)
  InDisconnectedSession = $true
  FilePath = "\\Scripts\Public\ConfigInventory.ps1"
  SessionOption = @{OutputBufferingMode="Drop";IdleTimeout=43200000}
}
Invoke-Command @parameters
```

命令使用 `Invoke-Command` 來執行腳本。 **ComputerName** 參數的值是 `Get-Content` 從文字檔取得遠端電腦名稱稱的命令。 **InDisconnectedSession** 參數會在一啟動命令時就將工作階段中斷連線。 **FilePath** 參數的值是 `Invoke-Command` 在每部電腦上執行的腳本。

**SessionOption** 的值是雜湊表。 **OutputBufferingMode** 值設定為 **Drop** ，且 **IdleTimeout** 值設定為 **43200000** 毫秒 (12 小時) 。

若要取得在已中斷連線的會話中執行的命令和腳本結果，請使用 `Receive-PSSession` Cmdlet。

### 範例19：使用 SSH 在遠端電腦上執行命令

此範例說明如何使用安全殼層 (SSH) 在遠端電腦上執行命令。 如果在遠端電腦上設定 SSH 以提示輸入密碼，則您會收到密碼提示。
否則，您必須使用以 SSH 金鑰為基礎的使用者驗證。

```powershell
Invoke-Command -HostName UserA@LinuxServer01 -ScriptBlock { Get-MailBox * }
```

### 範例20：使用 SSH 在遠端電腦上執行命令，並指定使用者驗證金鑰

此範例示範如何使用 SSH 在遠端電腦上執行命令，並指定金鑰檔以進行使用者驗證。 除非金鑰驗證失敗，且遠端電腦設定為允許基本密碼驗證，否則系統不會提示您輸入密碼。

```powershell
Invoke-Command -HostName UserA@LinuxServer01 -ScriptBlock { Get-MailBox * } -KeyFilePath /UserA/UserAKey_rsa
```

### 範例21：在多部遠端電腦上使用 SSH 作為作業來執行腳本檔案

此範例示範如何使用 SSH 和 **SSHConnection** 參數集在多部遠端電腦上執行腳本檔案。 **SSHConnection** 參數會採用雜湊表的陣列，其中包含每一部電腦的連接資訊。 此範例會要求目標遠端電腦必須設定 SSH 以支援以金鑰為基礎的使用者驗證。

```powershell
$sshConnections =
@{ HostName="WinServer1"; UserName="Domain\UserA"; KeyFilePath="C:\Users\UserA\id_rsa" },
@{ HostName="UserB@LinuxServer5"; KeyFilePath="/Users/UserB/id_rsa" }
$results = Invoke-Command -FilePath c:\Scripts\CollectEvents.ps1 -SSHConnection $sshConnections
```

## PARAMETERS

### -AllowRedirection

允許重新導向此連線至替代「統一資源識別項 (URI)」。

使用 **ConnectionURI** 參數時，遠端目的地可傳回重新導向至不同 URI 的指示。 根據預設，PowerShell 不會重新導向連線，但是您可以使用此參數允許它重新導向連接。

您也可以變更 **MaximumConnectionRedirectionCount** 工作階段選項值，限制連線重新導向的次數。 使用 Cmdlet 的 **MaximumRedirection** 參數， `New-PSSessionOption` 或設定喜好設定變數的 **MaximumConnectionRedirectionCount** 屬性 `$PSSessionOption` 。 預設值為 5。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Uri, FilePathUri
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -ApplicationName

指定連線 URI 的應用程式名稱區段。 當您未在命令中使用 **ConnectionURI** 參數時，請使用此參數來指定應用程式名稱。

預設值是 `$PSSessionApplicationName` 本機電腦上喜好設定變數的值。 如果未定義此喜好設定變數，則預設值為 WSMAN。 這個值適用於大部分用途。 如需詳細資訊，請參閱 [about_Preference_Variables](./About/about_Preference_Variables.md)。

WinRM 服務會使用應用程式名稱來選取要用來為連線要求提供服務的接聽程式。
此參數的值應該符合遠端電腦上接聽程式之 **URLPrefix** 屬性的值。

```yaml
Type: System.String
Parameter Sets: ComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: $PSSessionApplicationName if set on the local computer, otherwise WSMAN
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ArgumentList

提供命令中區域變數的值。 在遠端電腦上執行命令之前，會先以這些值取代命令中的變數。 以逗號分隔的清單方式輸入值。 值會依照其列出的順序與變數相關聯。 **ArgumentList** 的別名是 Args。

**ArgumentList** 參數中的值可以是實際值（例如1024），也可以是區域變數（例如）的參考 `$max` 。

若要在命令中使用區域變數，請使用下列命令格式：

`{param($<name1>[, $<name2>]...) <command-with-local-variables>} -ArgumentList <value>` -或- `<local-variable>`

**Param** 關鍵字會列出命令中使用的本機變數。 **ArgumentList** 會依列出的順序提供變數的值。 如需有關 **ArgumentList** 行為的詳細資訊，請參閱 [about_Splatting](about/about_Splatting.md#splatting-with-arrays)。

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsJob

指出此 Cmdlet 會在遠端電腦上以背景工作的方式執行命令。 您可以使用此參數執行需要很長時間才能完成的命令。

當您使用 **AsJob** 參數時，此命令會傳回代表工作的物件，然後顯示命令提示字元。 工作完成後，您可以繼續在工作階段中工作。 若要管理工作，請使用 `*-Job` Cmdlet。 若要取得工作結果，請使用 `Receive-Job` Cmdlet。

**AsJob** 參數類似于使用 `Invoke-Command` Cmdlet `Start-Job` 從遠端執行 Cmdlet。 不過，使用 **AsJob** 時，會在本機電腦上建立作業，即使是在遠端電腦上執行作業也一樣。 遠端作業的結果會自動傳回到本機電腦。

如需 PowerShell 背景工作的詳細資訊，請參閱 [about_Jobs](About/about_Jobs.md) 和 [about_Remote_Jobs](About/about_Remote_Jobs.md)。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FilePathRunspace, Session, ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, SSHHost, ContainerId, FilePathContainerId, SSHHostHashParam, FilePathSSHHost, FilePathSSHHostHash
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Authentication

指定用來驗證使用者認證的機制。 CredSSP 驗證僅適用于 Windows Vista、Windows Server 2008 和更新版本的 Windows 作業系統。

此參數可接受的值如下：

- 預設
- 基本
- Credssp
- Digest
- Kerberos
- 交涉
- NegotiateWithImplicitCredential

預設值為 Default。

如需此參數值的詳細資訊，請參閱 [AuthenticationMechanism 列舉](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)。

> [!CAUTION]
> 使用者認證會傳遞至要驗證之遠端電腦的「認證安全性支援提供者 (CredSSP)」驗證，是設計用於需要在一個以上資源進行驗證的命令，例如存取遠端網路共用。 此機制會使得遠端作業的安全性風險變高。 若遠端電腦遭到入侵，傳遞給它的認證便可用來控制網路工作階段。 如需詳細資訊，請參閱 [認證安全性支援提供者](/windows/win32/secauthn/credential-security-support-provider)。

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri
Aliases:
Accepted values: Basic, Default, Credssp, Digest, Kerberos, Negotiate, NegotiateWithImplicitCredential

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -CertificateThumbprint

指定具有連線至已中斷連線工作階段權限之使用者帳戶的數位公開金鑰憑證 (X509)。 請輸入憑證的憑證指紋。

憑證將用於用戶端憑證式驗證。 這些帳戶只能對應至本機使用者帳戶，而且無法使用網域帳戶。

若要取得憑證指紋，請使用 `Get-Item` `Get-ChildItem` PowerShell Cert：磁片磁碟機中的或命令。

```yaml
Type: System.String
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

指定命令執行所在的電腦。 預設是本機電腦。

當您使用 **ComputerName** 參數時，PowerShell 會建立僅用來執行指定命令的暫時連接，然後關閉。 如果您需要持續連線，請使用 **Session** 參數。

請輸入一或多部電腦的 NETBIOS 名稱、IP 位址或完整網域名稱 (以逗號分隔的清單方式)。 若要指定本機電腦，請輸入電腦名稱稱、localhost 或點 (`.`) 。

若要在 **ComputerName** 的值中使用 IP 位址，命令必須包含 **Credential** 參數。 電腦必須設定為 HTTPS 傳輸，或必須在本機電腦的 WinRM **TrustedHosts** 清單中包含遠端電腦的 IP 位址。 如需將電腦名稱稱新增到 **TrustedHosts** 清單的指示，請參閱 [如何將電腦新增到信任的主機清單](./about/about_remote_troubleshooting.md#how-to-add-a-computer-to-the-trusted-hosts-list)。

在 Windows Vista 和更新版本的 Windows 作業系統上，若要在 **ComputerName** 的值中包含本機電腦，您必須使用 [以 **系統管理員身分執行** ] 選項來執行 PowerShell。

```yaml
Type: System.String[]
Parameter Sets: ComputerName, FilePathComputerName
Aliases: Cn

Required: False
Position: 0
Default value: Local computer
Accept pipeline input: False
Accept wildcard characters: False
```

### -ConfigurationName

指定用於新 **PSSession** 的會話設定。

輸入工作階段設定的設定名稱或完整資源 URI。 如果您只指定設定名稱，則會在前面加上下列架構 URI： `http://schemas.microsoft.com/PowerShell` 。

搭配 SSH 使用時，此參數會指定要在目標上使用的子系統（如所定義） `sshd_config` 。 SSH 的預設值是 `powershell` 子系統。

工作階段的工作階段設定是位於遠端電腦上。 如果遠端電腦上不存在指定的會話設定，則命令會失敗。

預設值是 `$PSSessionConfigurationName` 本機電腦上喜好設定變數的值。 如果未設定此喜好設定變數，則預設值為 [ **Microsoft. PowerShell** ]。 如需詳細資訊，請參閱 [about_Preference_Variables](about/about_Preference_Variables.md)。

```yaml
Type: System.String
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, ContainerId, FilePathContainerId
Aliases:

Required: False
Position: Named
Default value: $PSSessionConfigurationName if set on the local computer, otherwise Microsoft.PowerShell
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ConnectionUri

指定定義工作階段之連線端點的「統一資源識別項」(URI)。
此 URI 必須是完整的 URI。

這個字串的格式如下所示：

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

預設值如下：

`http://localhost:5985/WSMAN`

如果您未指定連接 URI，您可以使用 **UseSSL** 和 **Port** 參數來指定連接 uri 值。

URI 的 **Transport** 區段有效值為 HTTP 與 HTTPS。 如果您指定具有傳輸區段的連線 URI，但未指定埠，則會使用標準埠：80（適用于 HTTP）和443（適用于 HTTPS）來建立會話。 若要使用 PowerShell 遠端的預設埠，請指定 HTTP 的埠5985或 HTTPS 的5986。

如果目的地電腦將連線重新導向至不同的 URI，除非您在命令中使用 **AllowRedirection** 參數，否則 PowerShell 會禁止重新導向。

```yaml
Type: System.Uri[]
Parameter Sets: Uri, FilePathUri
Aliases: URI, CU

Required: False
Position: 0
Default value: http://localhost:5985/WSMAN
Accept pipeline input: False
Accept wildcard characters: False
```

### -ContainerId

指定容器識別碼的陣列。

```yaml
Type: System.String[]
Parameter Sets: ContainerId, FilePathContainerId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Credential

指定具有執行此動作權限的使用者帳戶。 預設為目前使用者。

輸入使用者名稱（例如 **User01** 或 **Domain01\User01** ），或輸入 Cmdlet 所產生的 **PSCredential** 物件 `Get-Credential` 。 如果您輸入使用者名稱，系統就會提示您輸入密碼。

認證會儲存在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 物件中，而密碼會儲存為 [SecureString](/dotnet/api/system.security.securestring)。

> [!NOTE]
> 如需有關 **SecureString** 資料保護的詳細資訊，請參閱 [如何 SecureString 安全？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName
Aliases:

Required: True (VMId, VMName, FilePathVMId, FilePathVMName), False (ComputerName, FilePathComputerName, Uri, FilePathUri)
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -EnableNetworkAccess

指出此 Cmdlet 會將互動式安全性權杖新增至回送會話。 互動式權杖可讓您在會從其他電腦取得資料的回送工作階段中執行命令。 例如，您可以在會將 XML 檔案從遠端電腦複製到本機電腦的工作階段中執行命令。

回送會話是在同一部電腦上產生和結束的 **PSSession** 。 若要建立回送會話，請省略 **ComputerName** 參數，或將其值設為點 (`.`) 、localhost 或本機電腦的名稱。

根據預設，系統會使用網路權杖建立回送會話，這可能不會提供足夠的許可權來驗證遠端電腦。

**EnableNetworkAccess** 參數只在回送工作階段中有效。 如果您在遠端電腦上建立會話時使用 **EnableNetworkAccess** ，則命令會成功，但是會忽略參數。

您可以使用 **驗證** 參數的 **CredSSP** 值（將會話認證委派給其他電腦），允許回送會話中的遠端存取。

為了保護電腦免于惡意存取，具有互動式權杖的已中斷連線回送會話（使用 **EnableNetworkAccess** 所建立的權杖）只能從建立會話的電腦重新連接。 使用 CredSSP 驗證且已中斷連線的工作階段可從其他電腦重新連線。 如需詳細資訊，請參閱`Disconnect-PSSession`。

此參數是在 PowerShell 3.0 中引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

指定此 Cmdlet 在一或多部遠端電腦上執行的本機腳本。 輸入腳本的路徑和檔案名，或使用管線將腳本路徑傳送至 `Invoke-Command` 。 腳本必須存在於本機電腦或本機電腦可以存取的目錄中。 使用 **ArgumentList** 來指定腳本中參數的值。

當您使用此參數時，PowerShell 會將指定之指令檔的內容轉換成腳本區塊、將腳本區塊傳輸到遠端電腦，然後在遠端電腦上執行它。

```yaml
Type: System.String
Parameter Sets: FilePathRunspace, FilePathComputerName, FilePathUri, FilePathVMId, FilePathVMName, FilePathContainerId, FilePathSSHHost, FilePathSSHHostHash
Aliases: PSPath

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -HideComputerName

指出此 Cmdlet 會從輸出顯示中省略每個物件的電腦名稱稱。 預設會在顯示中出現產生物件的電腦名稱。

這個參數只會影響輸出顯示。 它不會變更物件。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FilePathRunspace, Session, ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, SSHHost, ContainerId, FilePathContainerId, SSHHostHashParam, FilePathSSHHost, FilePathSSHHostHash
Aliases: HCN

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -HostName

針對安全殼層 (SSH) 基礎的連線，指定電腦名稱稱的陣列。 這類似于 **ComputerName** 參數，不同之處在于遠端電腦的連線是使用 SSH 而非 Windows WinRM 進行。

此參數是在 PowerShell 6.0 中引進。

```yaml
Type: System.String[]
Parameter Sets: SSHHost, FilePathSSHHost
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InDisconnectedSession

指出此 Cmdlet 會在已中斷連線的會話中執行命令或腳本。

當您使用 **InDisconnectedSession** 參數時，會 `Invoke-Command` 在每一部遠端電腦上建立持續性會話、啟動 **ScriptBlock** 或 **FilePath** 參數所指定的命令，然後與會話中斷連線。 命令會繼續在中斷連線的會話中執行。 **InDisconnectedSession** 可讓您執行命令，而不需要維護遠端會話的連接。 而且，由於會話會在傳回任何結果之前中斷連線，因此 **InDisconnectedSession** 會確定所有命令結果都會傳回到重新連線的會話，而不是在會話之間進行分割。

您無法使用 **InDisconnectedSession** 搭配 **Session** 參數或 **AsJob** 參數。

使用 **InDisconnectedSession** 的命令會傳回代表中斷連接之會話的 **PSSession** 物件。 它們不會傳回命令輸出。 若要連接到中斷連線的會話，請使用 `Connect-PSSession` 或 `Receive-PSSession` Cmdlet。 若要取得會話中執行之命令的結果，請使用 `Receive-PSSession` Cmdlet。 若要在中斷連線的會話中執行產生輸出的命令，請將 **OutputBufferingMode** 會話選項的值設為 **Drop** 。 如果您想要連線到中斷連線的會話，請在會話中設定閒置超時，讓它提供足夠的時間讓您能夠在刪除會話之前先連接。

您可以在 **SessionOption** 參數或喜好設定變數中設定輸出緩衝處理模式和閒置超時時間 `$PSSessionOption` 。 如需會話選項的詳細資訊，請參閱 `New-PSSessionOption` 和 [about_Preference_Variables](./about/about_preference_variables.md)。

如需中斷連線工作階段功能的詳細資訊，請參閱 [about_Remote_Disconnected_Sessions](about/about_Remote_Disconnected_Sessions.md)。

此參數是在 PowerShell 3.0 中引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri
Aliases: Disconnected

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

指定命令的輸入。 輸入包含物件的變數，或輸入可取得物件的命令或運算式。

使用 **InputObject** 參數時，請 `$Input` 在 **ScriptBlock** 參數的值中使用自動變數來代表輸入物件。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -JobName

指定背景工作的好記名稱。 依預設，作業會命名為 `Job<n>` ，其中 `<n>` 是序號。

如果您在命令中使用 **JobName** 參數，命令就會以工作的形式執行，並傳回 `Invoke-Command` 工作物件，即使您未在命令中包含 **AsJob** 也一樣。

如需 PowerShell 背景工作的詳細資訊，請參閱 [about_Jobs](./About/about_Jobs.md)。

```yaml
Type: System.String
Parameter Sets: FilePathRunspace, Session, ComputerName, FilePathComputerName, Uri, FilePathUri, SSHHost, ContainerId, FilePathContainerId, SSHHostHashParam
Aliases:

Required: False
Position: Named
Default value: Job<n>
Accept pipeline input: False
Accept wildcard characters: False
```

### -KeyFilePath

指定安全殼層 (SSH) 用來驗證遠端電腦上使用者的金鑰檔路徑。

SSH 可讓使用者透過私用金鑰或公開金鑰執行使用者驗證，作為基本密碼驗證的替代方案。 如果遠端電腦設定為進行金鑰驗證，則此參數可以用來提供識別使用者的金鑰。

此參數是在 PowerShell 6.0 中引進。

```yaml
Type: System.String
Parameter Sets: SSHHost, FilePathSSHHost
Aliases: IdentityFilePath

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoNewScope

指出此 Cmdlet 會在目前的範圍中執行指定的命令。 依預設，會 `Invoke-Command` 在自己的範圍中執行命令。

這個參數只有在於目前的工作階段中執行的命令 (亦即省略 **ComputerName** 和 **Session** 這兩個參數的命令) 中才有效。

此參數是在 PowerShell 3.0 中引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: InProcess
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Port

指定遠端電腦上用於此命令的網路埠。 若要連線到遠端電腦，遠端電腦必須接聽連線使用的連接埠。 預設通訊埠為 5985 (WinRM 埠（適用于 HTTP）) 和 5986 (適用于 HTTPS) 的 WinRM 埠。

使用替代連接埠之前，必須先將遠端電腦上的 WinRM 接聽程式設定為在該連接埠進行接聽。 若要設定接聽程式，請在 PowerShell 提示字元中輸入下列兩個命令：

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

除非您必須這樣做，否則請勿使用 **Port** 參數。 在命令中設定的連接埠，將套用於執行命令所在的所有電腦或工作階段。 替代的連接埠設定可能使得命令無法在全部電腦上執行。

```yaml
Type: System.Int32
Parameter Sets: ComputerName, FilePathComputerName, SSHHost
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Remotedebug.js

用來在遠端 PowerShell 會話的偵測模式中執行已叫用的命令。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FilePathRunspace, Session, ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, SSHHost, ContainerId, FilePathContainerId, SSHHostHashParam, FilePathSSHHost, FilePathSSHHostHash
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunAsAdministrator

指出此 Cmdlet 會以系統管理員的身分叫用命令。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ContainerId, FilePathContainerId
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScriptBlock

指定要執行的命令。 以大括弧括住命令 `{ }` 以建立腳本區塊。
這是必要參數。

預設會在遠端電腦上評估命令中的所有變數。 若要在命令中包含區域變數，請使用 **ArgumentList** 。

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: InProcess, Session, ComputerName, Uri, VMId, VMName, SSHHost, ContainerId, SSHHostHashParam
Aliases: Command

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Session

指定此 Cmdlet 在其中執行命令的會話陣列。 輸入包含 **pssession** 物件的變數，或輸入可建立或取得 **pssession** 物件的命令，例如 `New-PSSession` 或 `Get-PSSession` 命令。

當您建立 **PSSession** 時，PowerShell 會建立與遠端電腦的持續連線。 使用 **PSSession** 來執行一系列共用資料的相關命令。 若要執行單一命令或一系列不相關的命令，請使用 **ComputerName** 參數。 如需詳細資訊，請參閱 [about_PSSessions](./About/about_PSSessions.md)。

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: FilePathRunspace, Session
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SessionName

指定中斷連線之工作階段的好記名稱。 您可以使用此名稱，在後續命令中參考會話，例如 `Get-PSSession` 命令。 這個參數是只有搭配 **InDisconnectedSession** 參數時才有效。

此參數是在 PowerShell 3.0 中引進。

```yaml
Type: System.String[]
Parameter Sets: ComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SessionOption

指定會話的 advanced 選項。 輸入 **SessionOption** 物件（例如您使用 Cmdlet 建立的物件 `New-PSSessionOption` ）或雜湊表，其中索引鍵為會話選項名稱，而值為會話選項值。

選項的預設值取決於 `$PSSessionOption` 喜好設定變數的值（如果已設定）。 否則，將以工作階段設定中設定的選項建立預設值。

會話選項值的優先順序高於 `$PSSessionOption` 喜好設定變數和會話設定中設定之會話的預設值。 不過，它們的優先順序不會高於會話設定中所設定的最大值、配額或限制。

如需包含預設值之會話選項的描述，請參閱 `New-PSSessionOption` 。 如需喜好設定變數的詳細資訊 `$PSSessionOption` ，請參閱 [about_Preference_Variables](About/about_Preference_Variables.md)。
如需會話設定的詳細資訊，請參閱 [about_Session_Configurations](About/about_Session_Configurations.md)。

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SSHConnection

此參數會採用雜湊表的陣列，其中每個雜湊表包含建立安全殼層 (SSH) 連接所需的一或多個連接參數。 **SSHConnection** 參數適用于建立多個會話，其中每個會話都需要不同的連接資訊。

雜湊表具有下列成員：

- **ComputerName** (或 **主機名稱** ) 
- **通訊埠**
- **使用者名稱**
- **KeyFilePath** (或 **IdentityFilePath** ) 

**ComputerName** (或 **HostName** ) 是唯一需要的機碼值組。

此參數是在 PowerShell 6.0 中引進。

```yaml
Type: System.Collections.Hashtable[]
Parameter Sets: SSHHostHashParam, FilePathSSHHostHash
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SSHTransport

指出使用安全殼層 (SSH) 來建立遠端連線。

PowerShell 預設會使用 Windows WinRM 連接到遠端電腦。 此參數會強制 PowerShell 使用 **HostName** 參數來建立以 SSH 為基礎的遠端連線。

此參數是在 PowerShell 6.0 中引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SSHHost, FilePathSSHHost
Aliases:
Accepted values: true

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

指定為執行此命令可建立的最大同時連線數。
若省略此參數，或輸入值為 0，則會使用預設值 32。

節流限制僅適用於目前命令，不適用於工作階段或電腦。

```yaml
Type: System.Int32
Parameter Sets: FilePathRunspace, Session, ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, ContainerId, FilePathContainerId
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### -UserName

針對用來在遠端電腦上執行命令的帳戶指定使用者名稱。 使用者驗證方法取決於遠端電腦上如何設定安全殼層 (SSH) 。

如果已針對基本密碼驗證設定 SSH，則系統會提示您輸入使用者密碼。

如果已針對金鑰型使用者驗證設定 SSH，則可透過 **KeyFilePath** 參數提供金鑰檔案路徑，而且不會出現任何密碼提示。 如果用戶端使用者金鑰檔位於 SSH 已知位置，則不需要 **KeyFilePath** 參數進行金鑰型驗證，而且使用者驗證會根據使用者名稱自動進行。 如需詳細資訊，請參閱平臺的 SSH 檔中有關金鑰型使用者驗證的資訊。

這不是必要的參數。 如果未指定 **UserName** 參數，則會使用目前登入的使用者名稱來進行連接。

此參數是在 PowerShell 6.0 中引進。

```yaml
Type: System.String
Parameter Sets: SSHHost, FilePathSSHHost
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSSL

指出此 Cmdlet 會使用安全通訊端層 (SSL) 通訊協定來建立與遠端電腦的連線。 預設不會使用 SSL。

WS-Management 加密透過網路傳輸的所有 PowerShell 內容。 **UseSSL** 參數是額外的保護，可跨 HTTPS （而非 HTTP）傳送資料。

如果您使用此參數，但是命令所用的埠上無法使用 SSL，則命令會失敗。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -VMId

指定虛擬機器的識別碼陣列。

```yaml
Type: System.Guid[]
Parameter Sets: VMId, FilePathVMId
Aliases: VMGuid

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -VMName

指定虛擬機器名稱的陣列。

```yaml
Type: System.String[]
Parameter Sets: VMName, FilePathVMName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -子系統

指定用於新 **PSSession** 的 SSH 子系統。

這會指定要在目標上使用的子系統，如 sshd_config 中所定義。
子系統會使用預先定義的參數啟動特定版本的 PowerShell。
如果指定的子系統不存在於遠端電腦上，則命令會失敗。

如果未使用此參數，則預設值為 ' powershell ' 子系統。

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases:

Required: False
Position: Named
Default value: powershell
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 系統管理. ScriptBlock

您可以使用管線將腳本區塊中的命令傳送至 `Invoke-Command` 。 使用 `$Input` 自動變數來代表命令中的輸入物件。

## 輸出

### PSRemotingJob、system.servicemodel 或已叫用之命令的輸出（或輸出）。

如果您使用 **AsJob** 參數，此 Cmdlet 會傳回工作物件。 如果您指定 **InDisconnectedSession** 參數，則會傳回 `Invoke-Command` **PSSession** 物件。 否則，它會傳回叫用命令的輸出，這是 **ScriptBlock** 參數的值。

## 注意

在 Windows Vista 和更新版本的 Windows 作業系統上，若要使用的 **ComputerName** 參數在 `Invoke-Command` 本機電腦上執行命令，您必須使用 [以 **系統管理員身分執行** ] 選項來執行 PowerShell。

當您在多部電腦上執行命令時，PowerShell 會依它們出現在清單中的順序連接到電腦。 但是，命令輸出會以從遠端電腦收到的順序顯示，可能會不同。

執行命令所產生的錯誤 `Invoke-Command` 會包含在命令結果中。
在本機命令中會是終止錯誤的錯誤在遠端命令中會被視為非終止錯誤。 此策略可確保一部電腦上的終止錯誤不會在其執行所在的所有電腦上關閉命令。 甚至是在單一電腦上執行遠端命令時，也會採用這種做法。

如果遠端電腦不是在本機電腦信任的網域中，則電腦可能無法驗證使用者的認證。 若要將遠端電腦新增至 WS-MANAGEMENT 中受信任的主機清單，請在提供者中使用下列命令 `WSMAN` ，其中 `<Remote-Computer-Name>` 是遠端電腦的名稱：

`Set-Item -Path WSMan:\Localhost\Client\TrustedHosts -Value \<Remote-Computer-Name\>`

當您使用 **InDisconnectedSession** 參數中斷連接 **PSSession** 時，會話狀態會 **中斷** 連線，而且可用性為 **None** 。 **State** 屬性的值是相對於目前工作階段。 值為「已 **中斷** 連線」表示 **PSSession** 未連接到目前的會話。 但是，它並不表示 **PSSession** 與所有會話中斷連接。 它可能連線不同的工作階段。 若要判斷是否可以連線或重新連線工作階段，請使用 **Availability** 屬性。

**Availability** 值為 **None** 表示您可以連線工作階段。 「 **忙碌** 」值表示您無法連接到 **PSSession** ，因為它已連接到另一個會話。 如需會話的 **State** 屬性值的詳細資訊，請參閱 [ runspacestate](/dotnet/api/system.management.automation.runspaces.runspacestate)。 如需會話的 **Availability** 屬性值的詳細資訊，請參閱 [RunspaceAvailability](/dotnet/api/system.management.automation.runspaces.runspaceavailability)。

**主機名稱** 和 **SSHConnection** 參數已包含在 PowerShell 6.0 的開頭。 已新增它們，以根據安全殼層 (SSH) 提供 PowerShell 遠端功能。 在多個平臺上支援 PowerShell 和 SSH (Windows、Linux、macOS) 和 PowerShell 遠端處理可在安裝和設定 PowerShell 和 SSH 的平臺上運作。 這與先前僅限 Windows 的遠端處理（以 WinRM 為基礎）和許多 WinRM 特定功能和限制都不適用。 例如，目前不支援以 WinRM 為基礎的配額、會話選項、自訂端點設定以及中斷連線/重新連線功能。 如需有關如何設定 PowerShell SSH 遠端的詳細資訊，請參閱透過 [SSH 的 Powershell 遠端](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)功能。

## 相關連結

[about_PSSessions](./About/about_PSSessions.md)

[about_Remote](./About/about_Remote.md)

[about_Remote_Disconnected_Sessions](./About/about_Remote_Disconnected_Sessions.md)

[about_Remote_Troubleshooting](./About/about_remote_troubleshooting.md)

[about_Remote_Variables](./About/about_Remote_Variables.md)

[about_Scopes](./About/about_scopes.md)

[Enter-PSSession](Enter-PSSession.md)

[Exit-PSSession](Exit-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Invoke-Item](../Microsoft.PowerShell.Management/Invoke-Item.md)

[New-PSSession](New-PSSession.md)

[Remove-PSSession](Remove-PSSession.md)

[WSMan 提供者](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)
