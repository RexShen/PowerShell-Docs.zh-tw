---
title: 說明系統
description: 掌握說明系統是順利使用 PowerShell 的關鍵。
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 43d2de7e1f59ce5e980c192decb5309d3f6d0ff8
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2020
ms.locfileid: "84438109"
---
# <a name="chapter-2---the-help-system"></a>第 2 章 - 說明系統

兩組 IT 專業人員在無法存取電腦的情況下參加筆試，以確定其 PowerShell 技能等級。 PowerShell 初學者一組，專家在另一組。
根據測試結果，這兩組之間的技能等級似乎差異不大。 這兩組又接受一次與上次類似的測試。 這一次他們可使用搭載 PowerShell 但無法存取網際網路的電腦。 第二次測試的結果顯示這兩組的技能等級有相當大的差異。 專家不一定知道答案，但他們知道如何找到答案。

這兩組人員的第一次和第二次測試結果有何差異？

這兩次測試結果的差異在於，專家並不記得如何使用 PowerShell 中的數千種命令。 他們十分瞭解如何使用 PowerShell 中的說明系統。
因此，他們可以在需要時找到必要的命令，並且在找到命令後，知道如何使用這些命令。

我聽說 PowerShell 的發明人 Jeffrey Snover 也曾數次提到類似的故事。

掌握說明系統是順利使用 PowerShell 的關鍵。

## <a name="discoverability"></a>可搜尋性

PowerShell 中的編譯命令稱為 Cmdlet。 Cmdlet 發音為「command-let」(而非 CMD-let)。 Cmdlet 名稱為單數形式的「動詞-名詞」命令，因此更易於發掘。 例如，用來判斷正在執行哪些流程的 Cmdlet 是 `Get-Process`，而用來擷取服務清單及其狀態的 Cmdlet 則是 `Get-Service`。 PowerShell 中還有其他類型的命令，例如本書稍後將提到的別名和函式。 「PowerShell 命令」一詞是通稱，通常用來泛指在 PowerShell 中任何類型的命令，不論是 Cmdlet、函式或別名。

## <a name="the-three-core-cmdlets-in-powershell"></a>PowerShell 中的三個核心 Cmdlet

- `Get-Command`
- `Get-Help`
- `Get-Member` (在第 3 章介紹)

我經常被問到的一個問題是，要如何確定 PowerShell 中的命令為何？ `Get-Command` 和 `Get-Help` 都可以用來判斷命令。

## <a name="get-help"></a>Get-Help

`Get-Help` 是多用途命令。 `Get-Help` 可協助您瞭解在找到命令後如何使用。 `Get-Help` 也可以用來協助您找到命令，但相較於 `Get-Command`，其使用不同但更間接的方式。

使用 `Get-Help` 來尋找命令時，它會先根據提供的輸入來搜尋命令名稱的萬用字元相符項目。 如果找不到相符的結果，則會搜尋說明主題本身，如果還是找不到相符的結果，則會傳回錯誤。 相對於普遍的看法，`Get-Help` 可用來尋找沒有說明主題的命令。

關於 PowerShell 中的說明系統，首先您需要瞭解如何使用 `Get-Help` Cmdlet。 下列命令可用來顯示 `Get-Help` 的說明主題。

```powershell
Get-Help -Name Get-Help
```

```Outpout
Do you want to run Update-Help?
The Update-Help cmdlet downloads the most current Help files for Windows PowerShell
modules, and installs them on your computer. For more information about the Update-Help
cmdlet, see http://go.microsoft.com/fwlink/?LinkId=210614.
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

從 PowerShell 第 3 版開始，PowerShell 說明不會隨附於作業系統。 第一次為命令執行 `Get-Help` 時，會顯示上一則訊息。 如果使用的是 `help` 函式或 `man` 別名，而不是 `Get-Help` Cmdlet，就不會收到此提示。

若按 <kbd>Y</kbd> 來表示「是」，則會執行 `Update-Help` Cmdlet，預設需要網際網路存取權限。 可以大寫或小寫指定 `Y`。

下載說明並完成更新之後，就會針對指定的命令傳回說明主題：

```powershell
Get-Help -Name Get-Help
```

請花一些時間在電腦上執行該範例，檢閱輸出，並記下資訊的分組方式：

- NAME
- 概要
- SYNTAX
- DESCRIPTION
- 相關連結
- REMARKS

如您所見，說明主題可能包含大量的資訊，這甚至不是全部的說明主題。

雖然參數不是 PowerShell 所特有，但可用來向命令提供輸入。 `Get-Help` 有許多參數，可指定參數以傳回整個說明主題或其中的子集。

顯示在上一組結果中說明主題的語法部分，列出 `Get-Help` 的所有參數。 乍看之下，似乎相同的參數被列了六次。 語法部分中的每個不同區塊都是參數集。 這表示 `Get-Help` Cmdlet 有六個不同的參數集。 如果仔細查看，您會注意到每個參數集中至少有一個不同的參數。

參數集是互斥的。 一旦使用了某個參數集所獨有的參數，就只能使用包含在該參數集中的參數。 例如，不能同時指定 **Full** 和 **Detailed** 參數，因為其分別來自不同的參數集。

下列每個參數都位於不同的參數集內：

- 完整
- 詳細
- 範例
- 線上
- 參數
- ShowWindow

在語法區段中，所有晦澀的語法 (例如方括弧和角括弧) 均分別代表某些含義，我們將在本書的附錄 A 中討論。 儘管這些語法很重要，但對於不熟悉且不常用到 PowerShell 的使用者而言，通常很難記住這些晦澀的語法。

如需更深入瞭解晦澀語法，請參閱[附錄 A][]。

對於初學者來說，除了使用一般語言之外，還有更簡單的方法可以取得相同的資訊。

指定 `Get-Help` 的 **Full** 參數後，會傳回整個說明主題。

```powershell
Get-Help -Name Get-Help -Full
```

請花一些時間在電腦上執行該範例，檢閱輸出，並記下資訊的分組方式：

- NAME
- 概要
- SYNTAX
- DESCRIPTION
- PARAMETERS
- 輸入
- 輸出
- 注意
- 範例
- 相關連結

請注意，使用 **Full** 參數會傳回數個額外的區段，其中一個是 PARAMETERS 區段，其提供的資訊比晦澀的 SYNTAX 區段更多。

**Full** 參數是切換參數。 不需要值的參數稱為「切換參數」。 已指定切換參數時，其值為 true，否則為 false。

如果您已在 PowerShell 主控台中完成本章的作業，會注意到在您還來不及閱讀前畫面上已掠過上一個顯示 `Get-Help` 完整說明主題的命令。 還有一個更好的辦法。

`Help` 函式透過管道將 `Get-Help` 傳送至名為 `more` ，其傳送的對象是 Windows 中 `more.com` 可執行檔的包裝函式。 在 PowerShell 主控台中，`help` 一次可提供一頁說明。 在 ISE 中，其運作方式與 `Get-Help`相同。 建議您使用 `help` 函式，而不是 `Get-Help` Cmdlet，因為前者可提供較好的體驗，而只需要較少的輸入。

不過，輸入較少不一定是件好事。 如果您要將命令另存為指令碼或與其他人共用，請務必使用完整的 Cmdlet 和參數名稱。 完整名稱為自我描述，讓它們更容易瞭解。 試想要如何讓下一個人看得懂這個命令。 可能是您。 您的同事和將來您自己會因此而感謝您。

嘗試在 Windows 10 實驗室環境電腦上的 PowerShell 主控台中執行下列命令。

```powershell
Get-Help -Name Get-Help -Full
help -Name Get-Help -Full
help Get-Help -Full
```

當您在 Windows 10 實驗室環境的電腦上執行上述這些命令時，您是否注意到其輸出有任何差異？

除了最後兩項一次傳回一頁結果外，並無任何差異。
使用 `Help` 函式和 <kbd>Ctrl</kbd>+<kbd>C</kbd> 會取消在 PowerShell 主控台中執行的命令時，會使用 <kbd>空格鍵</kbd> 來顯示下一頁的內容。

第一個範例使用 `Get-Help` Cmdlet，第二個範例使用 `Help` 函式，而第三個範例在使用 `Help` 函式時會省略 **Name** 參數。 **Name** 是位置參數，在該範例中是按照位置來使用此參數。 這表示您可以指定值，而不需指定參數名稱，只要值本身是在正確的位置中指定即可。 如何得知要在哪個位置指定值？ 如下列範例所示，透過閱讀說明來瞭解。

```powershell
help Get-Help -Parameter Name
```

```Output
-Name <String>
    Gets help about the specified command or concept. Enter the name of a cmdlet, function,
    provider, script, or workflow, such as Get-Member, a conceptual article name, such as
    about_Objects, or an alias, such as ls. Wildcard characters are permitted in cmdlet and
    provider names, but you can't use wildcard characters to find the names of function help and
    script help articles.

    To get help for a script that isn't located in a path that's listed in the $env:Path
    environment variable, type the script's path and file name.

    If you enter the exact name of a help article, Get-Help displays the article contents.

    If you enter a word or word pattern that appears in several help article titles, Get-Help
    displays a list of the matching titles.

    If you enter a word that doesn't match any help article titles, Get-Help displays a list of
    articles that include that word in their contents.

    The names of conceptual articles, such as about_Objects, must be entered in English, even in
    non-English versions of PowerShell.

    Required?                    false
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByPropertyName)
    Accept wildcard characters?  true
```

請注意，在上一個範例中搭配使用 **Parameter** 參數與 Help 函數時，只會傳回 **Name** 參數的說明主題中的資訊。 比起嘗試手動篩選動輒上百頁說明主題，這種方式更為簡便。

根據這些結果，您可以看到 **Name** 參數是位置參數，而且在按位置使用時必須在位置零 (第一個位置) 指定。 如果指定了參數名稱，則參數的指定順序並不重要。

另一個重要的資訊是，**Name** 參數值的預期資料類型必須是單一字串，並且以 `<String>` 表示。 如果它接受多個字串，則資料類型會列為 `<String[]>`。

有時候您不想要顯示命令的所有說明主題。 除了 **Full** 外，還可以使用 `Get-Help` 或 `Help` 等其他參數來指定。 嘗試在 Windows 10 實驗室環境電腦上執行下列命令：

```powershell
Get-Help -Name Get-Command -Full
Get-Help -Name Get-Command -Detailed
Get-Help -Name Get-Command -Examples
Get-Help -Name Get-Command -Online
Get-Help -Name Get-Command -Parameter Noun
Get-Help -Name Get-Command -ShowWindow
```

我通常會將 `help <command name>` 與 **Full** 或 **Online** 參數搭配使用。 如果只對範例感興趣，可使用 **Examples** 參數，如果只對特定參數感興趣，可使用 **Parameter** 參數。 **ShowWindow** 參數可在單獨的搜尋視窗中開啟說明主題，如果您有多個監視器，可以在另一台監視器上顯示此視窗。 我會避免使用 **ShowWindow** 參數，因為存在不會顯示整個說明主題的已知錯誤。

如果要在個別的視窗中顯示說明，建議使用 **Online** 參數，或使用 **Full** 參數，然後透過管道將結果傳送至 `Out-GridView`，如下列範例所示。

```powershell
help Get-Command -Full | Out-GridView
```

`Out-GridView` Cmdlet 和 `Get-Help` Cmdlet 的 **ShowWindow** 參數都需要具備 GUI (圖形化使用者介面) 的作業系統。 如果嘗試在使用伺服器核心 (無 GUI) 安裝選項安裝的 Windows Server 上使用其中一種，則會產生錯誤訊息。

若要使用 `Get-Help` 來尋找命令，請在 **Name** 參數中使用星號 (`*`) 萬用字元。 指定搜尋命令所使用的字詞，做為 **Name** 參數的值，如下列範例所示。

```powershell
help *process*
```

```Output
Name                              Category  Module                    Synopsis
----                              --------  ------                    --------
Enter-PSHostProcess               Cmdlet    Microsoft.PowerShell.Core Connects to and ...
Exit-PSHostProcess                Cmdlet    Microsoft.PowerShell.Core Closes an intera...
Get-PSHostProcessInfo             Cmdlet    Microsoft.PowerShell.Core
Debug-Process                     Cmdlet    Microsoft.PowerShell.M... Debugs one or mo...
Get-Process                       Cmdlet    Microsoft.PowerShell.M... Gets the process...
Start-Process                     Cmdlet    Microsoft.PowerShell.M... Starts one or mo...
Stop-Process                      Cmdlet    Microsoft.PowerShell.M... Stops one or mor...
Wait-Process                      Cmdlet    Microsoft.PowerShell.M... Waits for the pr...
Get-AppvVirtualProcess            Function  AppvClient                ...
Start-AppvVirtualProcess          Function  AppvClient                ...
```

在上述範例中，不需要 `*` 萬用字元，而且省略後產生的結果相同。 `Get-Help` 會自動在背景中加入萬用字元。

```powershell
help process
```

上一個命令會與在處理序兩端指定 `*` 萬用字元產生相同的結果。

我偏好加上這些萬用字元，因為這個選項向來可以得到一致的結果。 另外，在某些情況下需要用到這些萬用字元，而其他情況則不需要。 如果在值的中間加入萬用字元，就不會再對您指定的值自動加入萬用字元。

```powershell
help pr*cess
```

除非將 `*` 萬用字元加入至 `pr*cess` 的開頭、結尾或開頭和結尾，否則該命令不會傳回任何結果。

如果指定的值是以破折號開頭，則會產生錯誤，因為 PowerShell 會將其轉譯為參數名稱，但 `Get-Help` Cmdlet 沒有這類的參數名稱。

```powershell
help -process
```

如果嘗試尋找以 `-process` 結尾的命令，您只需要將 `*` 萬用字元新增至值的開頭。

```powershell
help *-process
```

使用 `Get-Help` 搜尋 PowerShell 命令時，請使用較為模糊而不要太特定的搜尋內容。

先前搜尋 `process` 時只找到名稱中包含 `process` 的命令，並且只傳回這些結果。 使用 `Get-Help` 來搜尋 `processes` 時，它找不到與命令名稱相符的項目，因此它會搜尋系統上 PowerShell 中的每個說明主題，並傳回找到的任何相符項目。 這會導致傳回大量的結果。

```powershell
Get-Help processes
```

```Output
Name                              Category  Module                    Synopsis
----                              --------  ------                    --------
Disconnect-PSSession              Cmdlet    Microsoft.PowerShell.Core Disconnects from...
Enter-PSHostProcess               Cmdlet    Microsoft.PowerShell.Core Connects to and ...
ForEach-Object                    Cmdlet    Microsoft.PowerShell.Core Performs an oper...
Get-PSSessionConfiguration        Cmdlet    Microsoft.PowerShell.Core Gets the registe...
New-PSTransportOption             Cmdlet    Microsoft.PowerShell.Core Creates an objec...
Out-Host                          Cmdlet    Microsoft.PowerShell.Core Sends output to ...
Where-Object                      Cmdlet    Microsoft.PowerShell.Core Selects objects ...
Clear-Variable                    Cmdlet    Microsoft.PowerShell.U... Deletes the valu...
Compare-Object                    Cmdlet    Microsoft.PowerShell.U... Compares two set...
Convert-String                    Cmdlet    Microsoft.PowerShell.U... Formats a string...
ConvertFrom-Csv                   Cmdlet    Microsoft.PowerShell.U... Converts object ...
ConvertTo-Html                    Cmdlet    Microsoft.PowerShell.U... Converts Microso...
ConvertTo-Xml                     Cmdlet    Microsoft.PowerShell.U... Creates an XML-b...
Debug-Runspace                    Cmdlet    Microsoft.PowerShell.U... Starts an intera...
Export-Csv                        Cmdlet    Microsoft.PowerShell.U... Converts objects...
Export-FormatData                 Cmdlet    Microsoft.PowerShell.U... Saves formatting...
Format-List                       Cmdlet    Microsoft.PowerShell.U... Formats the outp...
Format-Table                      Cmdlet    Microsoft.PowerShell.U... Formats the outp...
Get-Random                        Cmdlet    Microsoft.PowerShell.U... Gets a random nu...
Get-Unique                        Cmdlet    Microsoft.PowerShell.U... Returns unique i...
Group-Object                      Cmdlet    Microsoft.PowerShell.U... Groups objects t...
Import-Clixml                     Cmdlet    Microsoft.PowerShell.U... Imports a CLIXML...
Import-Csv                        Cmdlet    Microsoft.PowerShell.U... Creates table-li...
Measure-Object                    Cmdlet    Microsoft.PowerShell.U... Calculates the n...
Out-File                          Cmdlet    Microsoft.PowerShell.U... Sends output to ...
Out-GridView                      Cmdlet    Microsoft.PowerShell.U... Sends output to ...
Select-Object                     Cmdlet    Microsoft.PowerShell.U... Selects objects ...
Set-Variable                      Cmdlet    Microsoft.PowerShell.U... Sets the value o...
Sort-Object                       Cmdlet    Microsoft.PowerShell.U... Sorts objects by...
Tee-Object                        Cmdlet    Microsoft.PowerShell.U... Saves command ou...
Trace-Command                     Cmdlet    Microsoft.PowerShell.U... Configures and s...
Write-Output                      Cmdlet    Microsoft.PowerShell.U... Sends the specif...
Debug-Process                     Cmdlet    Microsoft.PowerShell.M... Debugs one or mo...
Get-Process                       Cmdlet    Microsoft.PowerShell.M... Gets the process...
Get-WmiObject                     Cmdlet    Microsoft.PowerShell.M... Gets instances o...
Start-Process                     Cmdlet    Microsoft.PowerShell.M... Starts one or mo...
Stop-Process                      Cmdlet    Microsoft.PowerShell.M... Stops one or mor...
Wait-Process                      Cmdlet    Microsoft.PowerShell.M... Waits for the pr...
Get-Counter                       Cmdlet    Microsoft.PowerShell.D... Gets performance...
Invoke-WSManAction                Cmdlet    Microsoft.WSMan.Manage... Invokes an actio...
Remove-WSManInstance              Cmdlet    Microsoft.WSMan.Manage... Deletes a manage...
Get-WSManInstance                 Cmdlet    Microsoft.WSMan.Manage... Displays managem...
New-WSManInstance                 Cmdlet    Microsoft.WSMan.Manage... Creates a new in...
Set-WSManInstance                 Cmdlet    Microsoft.WSMan.Manage... Modifies the man...
about_Arithmetic_Operators        HelpFile                            Describes the op...
about_Arrays                      HelpFile                            Describes arrays...
about_Debuggers                   HelpFile                            Describes the Wi...
about_Execution_Policies          HelpFile                            Describes the Wi...
about_ForEach-Parallel            HelpFile                            Describes the Fo...
about_Foreach                     HelpFile                            Describes a lang...
about_Functions                   HelpFile                            Describes how to...
about_Language_Keywords           HelpFile                            Describes the ke...
about_Methods                     HelpFile                            Describes how to...
about_Objects                     HelpFile                            Provides essenti...
about_Parallel                    HelpFile                            Describes the Pa...
about_Pipelines                   HelpFile                            Combining comman...
about_Preference_Variables        HelpFile                            Variables that c...
about_Remote                      HelpFile                            Describes how to...
about_Remote_Output               HelpFile                            Describes how to...
about_Sequence                    HelpFile                            Describes the Se...
about_Session_Configuration_Files HelpFile                            Describes sessio...
about_Variables                   HelpFile                            Describes how va...
about_Windows_PowerShell_5.0      HelpFile                            Describes new fe...
about_WQL                         HelpFile                            Describes WMI Qu...
about_WS-Management_Cmdlets       HelpFile                            Provides an over...
about_ForEach-Parallel            HelpFile                            Describes the Fo...
about_Parallel                    HelpFile                            Describes the Pa...
about_Sequence                    HelpFile                            Describes the Se...
```

使用 `Help` 來搜尋 `process`，傳回 10 個結果，而使用該命令來搜尋 `processes`，則會傳回 68 個結果。 如果只找到一個結果，將會顯示說明主題本身，而不會顯示命令清單。

```powershell
get-help *hotfix*
```

```Output
NAME
    Get-HotFix

SYNOPSIS
    Gets the hotfixes that have been applied to the local and remote computers.


SYNTAX
    Get-HotFix [-ComputerName <String[]>] [-Credential <PSCredential>] [-Description
    <String[]>] [<CommonParameters>]

    Get-HotFix [[-Id] <String[]>] [-ComputerName <String[]>] [-Credential
    <PSCredential>] [<CommonParameters>]


DESCRIPTION
    The Get-Hotfix cmdlet gets hotfixes (also called updates) that have been installed
    on either the local computer (or on specified remote computers) by Windows Update,
    Microsoft Update, or Windows Server Update Services; the cmdlet also gets hotfixes
    or updates that have been installed manually by users.


RELATED LINKS
    Online Version: http://go.microsoft.com/fwlink/?LinkId=821586
    Win32_QuickFixEngineering http://go.microsoft.com/fwlink/?LinkID=145071
    Get-ComputerRestorePoint
    Add-Content

REMARKS
    To see the examples, type: "get-help Get-HotFix -examples".
    For more information, type: "get-help Get-HotFix -detailed".
    For technical information, type: "get-help Get-HotFix -full".
    For online help, type: "get-help Get-HotFix -online"
```

現在來破解一個迷思，亦即在 PowerShell 中的 `Help` 只能找到有說明主題的命令。

```powershell
help *more*
```

```Output
NAME
    more

SYNTAX
    more [[-paths] <string[]>]


ALIASES
    None


REMARKS
    None
```

請注意，在上一個範例中，`more` 沒有說明主題，但是 PowerShell 中的 `Help` 系統可以找到它。 它只會找到一個相符的項目，並傳回基本語法資訊，因此，當命令沒有說明主題時，您就會看到基本語法資訊。

PowerShell 包含許多概念 (關於) 的說明主題。 下列命令可用來傳回有關系統上所有**關於**說明主題的清單。

```powershell
help About_*
```

將結果限制為一個「關於」說明主題，會顯示實際的說明主題，而不是傳回清單。

```powershell
help about_Updatable_Help
```

您必須更新 PowerShell 中的說明系統，才會顯示**關於**的說明主題。 若因為某些原因而導致電腦上的說明系統初始更新失敗，則在 `Update-Help` Cmdlet 成功執行之前，檔案將無法使用。

## <a name="get-command"></a>Get-Command

`Get-Command` 的設計目的是要協助您尋找命令。 執行不含任何參數的 `Get-Command` 會傳回系統上所有命令的清單。 下列範例示範如何使用 `Get-Command` Cmdlet 來判斷命令可用於處理流程的命令：

```powershell
Get-Command -Noun Process
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Debug-Process                                      3.1.0.0    Microsof...
Cmdlet          Get-Process                                        3.1.0.0    Microsof...
Cmdlet          Start-Process                                      3.1.0.0    Microsof...
Cmdlet          Stop-Process                                       3.1.0.0    Microsof...
Cmdlet          Wait-Process                                       3.1.0.0    Microsof...
```

請注意，在上一個範例執行 `Get-Command` 時，使用 **Noun** 參數，並將 `Process` 指定為 **Noun** 參數的值。 如果您不知道如何使用 `Get-Command` Cmdlet，該怎麼辦？ 您可以使用 `Get-Help` 來顯示 `Get-Command` 的說明主題。

**Name**、**Noun** 和 **Verb** 參數都接受萬用字元。 下列範例會顯示如何搭配使用 **Name** 參數和萬用字元：

```Output
Get-Command -Name *service*
```

```powershell
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Function        Get-NetFirewallServiceFilter                       2.0.0.0    NetSecurity
Function        Set-NetFirewallServiceFilter                       2.0.0.0    NetSecurity
Cmdlet          Get-Service                                        3.1.0.0    Microsof...
Cmdlet          New-Service                                        3.1.0.0    Microsof...
Cmdlet          New-WebServiceProxy                                3.1.0.0    Microsof...
Cmdlet          Restart-Service                                    3.1.0.0    Microsof...
Cmdlet          Resume-Service                                     3.1.0.0    Microsof...
Cmdlet          Set-Service                                        3.1.0.0    Microsof...
Cmdlet          Start-Service                                      3.1.0.0    Microsof...
Cmdlet          Stop-Service                                       3.1.0.0    Microsof...
Cmdlet          Suspend-Service                                    3.1.0.0    Microsof...
Application     AgentService.exe                                   10.0.14... C:\Windo...
Application     SensorDataService.exe                              10.0.14... C:\Windo...
Application     services.exe                                       10.0.14... C:\Windo...
Application     services.msc                                       0.0.0.0    C:\Windo...
Application     TieringEngineService.exe                           10.0.14... C:\Windo...
```

我不喜歡搭配使用萬用字元與 `Get-Command` 的 **Name** 參數，因為它也會傳回不是原生 PowerShell 命令的可執行檔。

如果您要搭配使用 **Name** 參數與萬用字元，我議使用 **CommandType** 參數來限制結果。

```powershell
Get-Command -Name *service* -CommandType Cmdlet, Function, Alias
```

更好的選項是使用 **Verb** 或 **Noun** 參數或兩者，因為只有 PowerShell 命令同時具有動詞和名詞。

在說明主題中發現錯誤嗎？ 好消息是，PowerShell 的說明主題為已開放原始碼，可以在 GitHub 上的 [PowerShell-Docs][] 存放庫中取得。 公開修正結果，您不只可為自己修正不正確的資訊，還可以幫助其他人。 您只要派生 GitHub 上的 PowerShell 文件存放庫，更新說明主題，並提交提取要求即可。
接受提取要求之後，所有人都可以使用已更正的文件。

## <a name="updating-help"></a>更新說明

有關請求的命令的首次說明，在 PowerShell 說明主題的本機複本中已更新。 建議定期更新說明系統，因為「說明」內容可能會不定時更新。 `Update-Help` Cmdlet 是用來更新說明主題。
根據預設，它需要存取網際網路，而且您需要以系統管理員的身分提高權限來執行 PowerShell。

```powershell
Update-Help
```

```Output
Update-Help : Failed to update Help for the module(s) 'BitsTransfer' with UI culture(s)
{en-US} : The value of the HelpInfoUri key in the module manifest must resolve to a
container or root URL on a website where the help files are stored. The HelpInfoUri
'https://technet.microsoft.com/en-us/library/dd819413.aspx' does not resolve to a
container.
At line:1 char:1
+ Update-Help
+
    + CategoryInfo          : InvalidOperation: (:) [Update-Help], Exception
    + FullyQualifiedErrorId : InvalidHelpInfoUri,Microsoft.PowerShell.Commands.UpdateHel
   pCommand

Update-Help : Failed to update Help for the module(s) 'NetworkControllerDiagnostics,
StorageReplica' with UI culture(s) {en-US} : Unable to retrieve the HelpInfo XML file
for UI culture en-US. Make sure the HelpInfoUri property in the module manifest is valid
or check your network connection and then try the command again.
At line:1 char:1
+ Update-Help
+
    + CategoryInfo          : ResourceUnavailable: (:) [Update-Help], Exception
    + FullyQualifiedErrorId : UnableToRetrieveHelpInfoXml,Microsoft.PowerShell.Commands.
   UpdateHelpCommand
```

有幾個模組傳回錯誤，這種情況並不常見。 如果電腦無法存取網際網路，您可以在另一部可存取網際網路的電腦上使用 `Save-Help` Cmdlet，先將已更新的說明資訊儲存到網路上的檔案共用，然後使用 `Update-Help` 的 **SourcePath** 參數為說明主題指定此網路位置。

請考慮在 PowerShell 中設定排程工作，或將一些邏輯新增至您的設定檔指令碼，以定期更新電腦上的說明內容。 設定檔指令碼將於後續章節中討論。

## <a name="summary"></a>摘要

在本章中，您已瞭解如何使用 `Get-Help` 和 `Get-Command` 尋找命令。 您已學會藉由說明系統，瞭解如何在找到命令後使用這些命令。 您也已瞭解如何在有可用的更新時，更新說明主題的內容。

建議您可以一天學習一個 PowerShell 命令。

```powershell
Get-Command | Get-Random | Get-Help -Full
```

## <a name="review"></a>檢閱

1. `Get-Service` 的 **DisplayName** 參數是否為按照位置使用的參數？
1. `Get-Process` Cmdlet 有多少個參數集合？
1. 有哪些 PowerShell 命令可用來處理事件記錄檔？
1. 有哪些 PowerShell 命令可用來傳回在電腦上執行的 PowerShell 流程的清單？
1. 如何更新儲存在電腦上的 PowerShell 說明內容？

## <a name="recommended-reading"></a>建議閱讀資料

若需深入瞭解本章所提到的主題，建議閱讀下列 PowerShell 說明主題。

- [Get-Help][]
- [Get-Command][]
- [Update-Help][]
- [Save-Help][]
- [about_Updatable_Help][]
- [about_Command_Syntax][]

在下一章中，您將瞭解 `Get-Member` Cmdlet 以及物件、屬性和方法。

<!-- link references -->
[Get-Help]: /powershell/module/microsoft.powershell.core/get-help
[Get-Command]: /powershell/module/microsoft.powershell.core/get-command
[Update-Help]: /powershell/module/microsoft.powershell.core/update-help
[Save-Help]: /powershell/module/microsoft.powershell.core/save-help
[about_Updatable_Help]: /powershell/module/microsoft.powershell.core/about/about_updatable_help
[about_Command_Syntax]: /powershell/module/microsoft.powershell.core/about/about_command_syntax
[PowerShell-Docs]: https://github.com/powershell/powershell
[附錄 A]: appendix-a.md
