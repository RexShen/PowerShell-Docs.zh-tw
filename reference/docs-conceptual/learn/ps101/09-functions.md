---
title: 函式
description: PowerShell 函式可讓您建立可在指令碼中重複使用的工具。
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: ca48f3020fa306f8a24328bd18648d5954c48a94
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2020
ms.locfileid: "84438199"
---
# <a name="chapter-9---functions"></a>第 9 章 - 函式

如果您要撰寫 PowerShell 一行程式碼或指令碼，而且發現您經常需要針對不同的案例進行修改，將它轉換成可重複使用的函式應很合適。

如果可能，我偏好撰寫函式，因為它們更具工具導向。 我可以將函式放在指令碼模組中，將該模組放在 `$env:PSModulePath` 中並呼叫函式，而不需要實際找出其儲存位置。 使用 PowerShellGet 模組，要在 NuGet 存放庫中共用這些模組非常容易。 PowerShellGet 隨附 PowerShell 5.0 版和更新版本。 其以 PowerShell 3.0 版和更新版本的個別下載形式提供。

不要太過複雜。 將它保持簡單，並使用最直接的方式來完成工作。 避免在您重複使用的任何程式碼中使用別名和位置參數。 將您的程式碼格式化，以易於閱讀。 不要將值硬式編碼；使用參數和變數。 請勿撰寫不必要的程式碼，即使它不會損及任何項目。 這會增加不必要的複雜度。 注意細節對撰寫任何 PowerShell 程式碼很有幫助。

## <a name="naming"></a>命名

在 PowerShell 中命名您的函式時，請使用 [Pascal 命名法的大小寫][] 名稱搭配已核准的動詞和單數名詞。 我也建議為名詞加上前置詞。 例如： `<ApprovedVerb>-<Prefix><SingularNoun>` 。

在 PowerShell 中，您可以藉由執行 `Get-Verb` 來取得已核准的特定動詞清單。

```powershell
Get-Verb | Sort-Object -Property Verb
```

```Output
Verb        Group
----        -----
Add         Common
Approve     Lifecycle
Assert      Lifecycle
Backup      Data
Block       Security
Checkpoint  Data
Clear       Common
Close       Common
Compare     Data
Complete    Lifecycle
Compress    Data
Confirm     Lifecycle
Connect     Communications
Convert     Data
ConvertFrom Data
ConvertTo   Data
Copy        Common
Debug       Diagnostic
Deny        Lifecycle
Disable     Lifecycle
Disconnect  Communications
Dismount    Data
Edit        Data
Enable      Lifecycle
Enter       Common
Exit        Common
Expand      Data
Export      Data
Find        Common
Format      Common
Get         Common
Grant       Security
Group       Data
Hide        Common
Import      Data
Initialize  Data
Install     Lifecycle
Invoke      Lifecycle
Join        Common
Limit       Data
Lock        Common
Measure     Diagnostic
Merge       Data
Mount       Data
Move        Common
New         Common
Open        Common
Optimize    Common
Out         Data
Ping        Diagnostic
Pop         Common
Protect     Security
Publish     Data
Push        Common
Read        Communications
Receive     Communications
Redo        Common
Register    Lifecycle
Remove      Common
Rename      Common
Repair      Diagnostic
Request     Lifecycle
Reset       Common
Resize      Common
Resolve     Diagnostic
Restart     Lifecycle
Restore     Data
Resume      Lifecycle
Revoke      Security
Save        Data
Search      Common
Select      Common
Send        Communications
Set         Common
Show        Common
Skip        Common
Split       Common
Start       Lifecycle
Step        Common
Stop        Lifecycle
Submit      Lifecycle
Suspend     Lifecycle
Switch      Common
Sync        Data
Test        Diagnostic
Trace       Diagnostic
Unblock     Security
Undo        Common
Uninstall   Lifecycle
Unlock      Common
Unprotect   Security
Unpublish   Data
Unregister  Lifecycle
Update      Data
Use         Other
Wait        Lifecycle
Watch       Common
Write       Communications
```

在上述範例中，我已依照**動詞**資料行排序結果。 **群組**資料行可讓您對於如何使用這些動詞有些概念。 將函式新增至模組時，請務必在 PowerShell 中選擇已核准的動詞。 如果您選擇未核准的動詞，模組會在載入時產生警告訊息。 該警告訊息會讓您的函式看起來不專業。 未核准的動詞也會限制函式的可探索性。

## <a name="a-simple-function"></a>簡單函式

PowerShell 中的函式會使用 function 關鍵字來宣告，後面接著函式名稱，然後是左和右大括弧。 函式將執行的程式碼會包含在這些大括弧內。

```powershell
function Get-Version {
    $PSVersionTable.PSVersion
}
```

顯示的函式是一個會傳回 PowerShell 版本的簡單範例。

```powershell
Get-Version
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  693
```

名稱很可能會與名為 `Get-Version` 之類的函式和 PowerShell 中的預設命令，或其他人可能寫入的命令發生衝突。 這就是為什麼我建議您在函式的名詞部分前面加上前置詞，以協助避免命名衝突。 在下列範例中，我將使用前置詞 "PS"。

```powershell
function Get-PSVersion {
    $PSVersionTable.PSVersion
}
```

除了名稱之外，此函式與上一個函式完全相同。

```powershell
Get-PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  693
```

即使是在名詞前面加上 PS 之類項目，還是有可能發生名稱衝突。 我通常會在我的函式名詞前面加上我的姓名縮寫。 發展一個標準並持續使用它。

```powershell
function Get-MrPSVersion {
    $PSVersionTable.PSVersion
}
```

除了使用更合理的名稱來嘗試避免與其他 PowerShell 命令的命名衝突以外，此函式與前兩個函式沒有不同。

```powershell
Get-MrPSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  693
```

載入記憶體之後，您可以在 **Function** PSDrive 上查看函式。

```powershell
Get-ChildItem -Path Function:\Get-*Version
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Function        Get-Version
Function        Get-PSVersion
Function        Get-MrPSVersion
```

如果您想要從目前的工作階段移除這些函式，您必須從 **Function** PSDrive 中移除它們，或關閉並重新開啟 PowerShell。

```powershell
Get-ChildItem -Path Function:\Get-*Version | Remove-Item
```

確認已確實移除這些函式。

```powershell
Get-ChildItem -Path Function:\Get-*Version
```

如果函式已載入為模組的一部分，則可以卸載模組以將其移除。

```powershell
Remove-Module -Name <ModuleName>
```

`Remove-Module` Cmdlet 會從您目前的 PowerShell 工作階段的記憶體移中除模組，而不會從您的系統或磁碟中移除它們。

## <a name="parameters"></a>參數

不要以靜態方式指派值！ 使用參數和變數。 為參數命名時，請盡可能使用相同名稱做為參數名稱的預設 Cmdlet。

```powershell
function Test-MrParameter {

    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

為什麼我使用 **ComputerName** 而不是 **Computer**、**ServerName** 或 **Host** 做為參數名稱？ 這是因為我希望將我的函式如同預設 Cmdlet 般標準化。

我要建立一個函式來查詢系統上的所有命令，並傳回具有特定參數名稱的函式數目。

```powershell
function Get-MrParameterCount {
    param (
        [string[]]$ParameterName
    )

    foreach ($Parameter in $ParameterName) {
        $Results = Get-Command -ParameterName $Parameter -ErrorAction SilentlyContinue

        [pscustomobject]@{
            ParameterName = $Parameter
            NumberOfCmdlets = $Results.Count
        }
    }
}
```

如您在下面所示的結果中所見，有 39 個命令具有 **ComputerName** 參數。 沒有任何 Cmdlet 具有參數 (例如**Computer**、**ServerName**、**Host** 或 **Machine**)。

```powershell
Get-MrParameterCount -ParameterName ComputerName, Computer, ServerName, Host, Machine
```

```Output
ParameterName NumberOfCmdlets
------------- ---------------
ComputerName               39
Computer                    0
ServerName                  0
Host                        0
Machine                     0
```

我也建議對您的參數名稱使用相同的大小寫做為預設 Cmdlet。 使用 `ComputerName`，而不是 `computername`。 這會讓您的函式看起來像是預設 Cmdlet。 已熟悉 PowerShell 的人員就會覺得再習慣不過。

## <a name="advanced-functions"></a>進階函式

將 PowerShell 中的函式轉換成進階函式真的很簡單。 函式與進階函式之間的其中一項差異是，進階函式具有許多會自動新增至函式的一般參數。 這些一般參數包括 **Verbose** 和 **Debug** 之類的參數。

我將從上一節中使用的 `Test-MrParameter` 函式開始。

```powershell
function Test-MrParameter {

    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

我想要您注意的是，`Test-MrParameter` 函式沒有任何一般參數。 要查看一般參數有幾個不同的方式。 其中一個是使用 `Get-Command` 來檢視語法。

```powershell
Get-Command -Name Test-MrParameter -Syntax
```

```Output
Test-MrParameter [[-ComputerName] <Object>]
```

另一個是使用 `Get-Command` 向下切入參數。

```powershell
(Get-Command -Name Test-MrParameter).Parameters.Keys
```

```Output
ComputerName
```

新增 `CmdletBinding` 以將函式轉換為進階函式。

```powershell
function Test-MrCmdletBinding {

    [CmdletBinding()] #<<-- This turns a regular function into an advanced function
    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

新增 `CmdletBinding` 會自動新增一般參數。 `CmdletBinding` 需要 `param` 區塊，但 `param` 區塊可以是空的。

```powershell
Get-Command -Name Test-MrCmdletBinding -Syntax
```

```Output
Test-MrCmdletBinding [[-ComputerName] <Object>] [<CommonParameters>]
```

向下切入具有 `Get-Command` 的參數，會顯示實際參數名稱，包括一般參數名稱。

```powershell
(Get-Command -Name Test-MrCmdletBinding).Parameters.Keys
```

```Output
ComputerName
Verbose
Debug
ErrorAction
WarningAction
InformationAction
ErrorVariable
WarningVariable
InformationVariable
OutVariable
OutBuffer
PipelineVariable
```

## <a name="supportsshouldprocess"></a>SupportsShouldProcess

`SupportsShouldProcess` 新增 **WhatIf** 和 **Confirm** 參數。 只有會進行變更的命令才需要這些。

```powershell
function Test-MrSupportsShouldProcess {

    [CmdletBinding(SupportsShouldProcess)]
    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

請注意，現在已有 **WhatIf** 和 **Confirm** 參數。

```powershell
Get-Command -Name Test-MrSupportsShouldProcess -Syntax
```

```Output
Test-MrSupportsShouldProcess [[-ComputerName] <Object>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

同樣地，您也可以使用 `Get-Command` 來傳回包含實際參數名稱的清單，包括一般參數與 WhatIf 和 Confirm。

```powershell
(Get-Command -Name Test-MrSupportsShouldProcess).Parameters.Keys
```

```Output
ComputerName
Verbose
Debug
ErrorAction
WarningAction
InformationAction
ErrorVariable
WarningVariable
InformationVariable
OutVariable
OutBuffer
PipelineVariable
WhatIf
Confirm
```

## <a name="parameter-validation"></a>參數驗證

及早驗證輸入。 當程式碼在沒有有效輸入的情況下無法執行時，為什麼要讓程式碼繼續在某路徑上執行？

一律輸入要用於參數的變數 (指定資料類型)。

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [string]$ComputerName
    )

    Write-Output $ComputerName

}
```

在上述範例中，我指定 **String** 做為 **ComputerName** 參數的資料類型。 這會使得它只允許指定單一電腦名稱。 如果透過逗號分隔清單指定多個電腦名稱，則會產生錯誤。

```powershell
Test-MrParameterValidation -ComputerName Server01, Server02
```

```Output
Test-MrParameterValidation : Cannot process argument transformation on parameter
'ComputerName'. Cannot convert value to type System.String.
At line:1 char:42
+ Test-MrParameterValidation -ComputerName Server01, Server02
+
    + CategoryInfo          : InvalidData: (:) [Test-MrParameterValidation], ParameterBindingArg
     umentTransformationException
    + FullyQualifiedErrorId : ParameterArgumentTransformationError,Test-MrParameterValidation
```

目前的定義有個問題，就是省略 **ComputerName** 參數的值是有效的，但需要值，函式才能成功完成。 這就是 `Mandatory` 參數屬性派上用場的地方。

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory)]
        [string]$ComputerName
    )

    Write-Output $ComputerName

}
```

上一個範例中使用的語法可與 PowerShell 3.0 版和更新版本相容。
您可以改為指定 `[Parameter(Mandatory=$true)]`，使函式與 PowerShell 2.0 版和更新版本相容。 既然現在需要 **ComputerName** (如果未指定)，則函式會提示您輸入一個。

```powershell
Test-MrParameterValidation
```

```Output
cmdlet Test-MrParameterValidation at command pipeline position 1
Supply values for the following parameters:
ComputerName:
```

如果您想要允許 **ComputerName** 參數有多個值，請使用 **String** 資料類型，但在資料類型中加入左方括弧和右方括弧，以允許字串陣列。

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory)]
        [string[]]$ComputerName
    )

    Write-Output $ComputerName

}
```

您可能想要為 **ComputerName** 參數指定預設值 (如果未指定的話)。
問題在於，預設值無法與強制參數搭配使用。 相反地，您必須使用 `ValidateNotNullOrEmpty` 參數驗證屬性搭配預設值。

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [ValidateNotNullOrEmpty()]
        [string[]]$ComputerName = $env:COMPUTERNAME
    )

    Write-Output $ComputerName

}
```

即使是設定預設值，也請嘗試不要使用靜態值。 在上述範例中，使用 `$env:COMPUTERNAME` 做為預設值，如果未提供值，則會自動轉譯為本機電腦名稱。

## <a name="verbose-output"></a>詳細資訊輸出

雖然內嵌註解很實用，特別是當您撰寫一些複雜的程式碼時，使用者永遠不會看到這些註解，除非使用者查看程式碼本身。

下列範例中所示的函式在 `foreach` 迴圈中具有內嵌註解。 雖然這個特定的註解可能不太難找到，但想像一下若函式包含數百行程式碼。

```powershell
function Test-MrVerboseOutput {

    [CmdletBinding()]
    param (
        [ValidateNotNullOrEmpty()]
        [string[]]$ComputerName = $env:COMPUTERNAME
    )

    foreach ($Computer in $ComputerName) {
        #Attempting to perform some action on $Computer <<-- Don't use
        #inline comments like this, use write verbose instead.
        Write-Output $Computer
    }

}
```

較好的選項是使用 `Write-Verbose`，而不是內嵌註解。

```powershell
function Test-MrVerboseOutput {

    [CmdletBinding()]
    param (
        [ValidateNotNullOrEmpty()]
        [string[]]$ComputerName = $env:COMPUTERNAME
    )

    foreach ($Computer in $ComputerName) {
        Write-Verbose -Message "Attempting to perform some action on $Computer"
        Write-Output $Computer
    }

}
```

呼叫函式而未使用 **Verbose** 參數時，將不會顯示詳細資訊輸出。

```powershell
Test-MrVerboseOutput -ComputerName Server01, Server02
```

使用 **Verbose** 參數呼叫時，將會顯示詳細資訊輸出。

```powershell
Test-MrVerboseOutput -ComputerName Server01, Server02 -Verbose
```

## <a name="pipeline-input"></a>管線輸入

想要函式接受管線輸入時，需要一些額外的程式碼。 如本書稍早所述，命令可以接受管線輸入 **by value** (by type)，或 **by property name**。 您可以撰寫函式，就像原生命令一樣，使得它們會接受這兩個類型中的一或兩個輸入。

若要接受輸入 **by value**，請為該特定參數指定 `ValueFromPipeline` 參數屬性。 請記住，您只能透過每個資料類型中的一個來接受管線輸入 **by value**。 例如，如果您有會接受字串輸入的兩個參數，則其中只有一個可接受管線輸入 **by value**，因為如果您同時為這兩個字串參數指定它，則管線輸入不會知道要繫結的是哪一個。 這是我將這種管線輸入稱為 _by type_ 而非 **by value** 的另一個原因。

管線輸入一次會出現在一個項目中，與 `foreach` 迴圈中處理項目的方式類似。
如果您接受陣列做為輸入，則至少需要 `process` 區塊來處理每個項目。 如果您只接受單一值做為輸入，則不需要 `process` 區塊，但仍建議您為了一致性而指定它。

```powershell
function Test-MrPipelineInput {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipeline)]
        [string[]]$ComputerName
    )

    PROCESS {
        Write-Output $ComputerName
    }

}
```

接受管線輸入 **by property name** 也是類似的，但它是使用 `ValueFromPipelineByPropertyName` 參數屬性指定，且不論資料類型為何，都可以為任何數目的參數指定。 關鍵在於要以管線送入的命令輸出必須具有符合參數名稱的屬性名稱，或您函式的參數別名。

```powershell
function Test-MrPipelineInput {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipelineByPropertyName)]
        [string[]]$ComputerName
    )

    PROCESS {
            Write-Output $ComputerName
    }

}
```

`BEGIN` 和 `END` 區塊是選擇性的。 `BEGIN` 會在 `PROCESS` 區塊之前指定，並在從管線收到項目之前，用來執行任何初始工作。 務必了解這點。 以管線送入的值無法在 `BEGIN` 區塊中存取。 `END` 區塊會在 `PROCESS` 區塊之後指定，且會在以管線送入的所有項目都經過處理之後用於清除。

## <a name="error-handling"></a>錯誤處理

下列範例中所顯示的函式會在無法連絡電腦時產生未處理的例外狀況。

```powershell
function Test-MrErrorHandling {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipeline,
                   ValueFromPipelineByPropertyName)]
        [string[]]$ComputerName
    )

    PROCESS {
        foreach ($Computer in $ComputerName) {
            Test-WSMan -ComputerName $Computer
        }
    }

}
```

有幾種不同的方式可以處理 PowerShell 中的錯誤。 `Try/Catch` 是處理錯誤的更現代化方式。

```powershell
function Test-MrErrorHandling {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipeline,
                   ValueFromPipelineByPropertyName)]
        [string[]]$ComputerName
    )

    PROCESS {
        foreach ($Computer in $ComputerName) {
            try {
                Test-WSMan -ComputerName $Computer
            }
            catch {
                Write-Warning -Message "Unable to connect to Computer: $Computer"
            }
        }
    }

}
```

雖然上述範例中顯示的函式使用錯誤處理，但它也會產生未處理的例外狀況，因為命令未產生終止錯誤。 也務必了解這點。 只攔截到終止錯誤。 指定 **ErrorAction** 參數搭配 **Stop** 做為值，以將非終止錯誤轉換成會終止的錯誤。

```powershell
function Test-MrErrorHandling {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipeline,
                   ValueFromPipelineByPropertyName)]
        [string[]]$ComputerName
    )

    PROCESS {
        foreach ($Computer in $ComputerName) {
            try {
                Test-WSMan -ComputerName $Computer -ErrorAction Stop
            }
            catch {
                Write-Warning -Message "Unable to connect to Computer: $Computer"
            }
        }
    }

}
```

除非絕對必要，否則請勿修改全域 `$ErrorActionPreference` 變數。 如果您直接從 PowerShell 函式內使用類似 .NET 的項目，就無法在命令本身上指定 **ErrorAction**。 在該情況下，您可能需要變更全域 `$ErrorActionPreference` 變數，但如果您的確變更它，請在嘗試命令之後立即將它變更回來。

## <a name="comment-based-help"></a>註解型說明

將註解型說明新增至您的函式是最佳做法，這能夠讓您所共用的人員知道如何使用內容。

```powershell
function Get-MrAutoStoppedService {

<#
.SYNOPSIS
    Returns a list of services that are set to start automatically, are not
    currently running, excluding the services that are set to delayed start.

.DESCRIPTION
    Get-MrAutoStoppedService is a function that returns a list of services from
    the specified remote computer(s) that are set to start automatically, are not
    currently running, and it excludes the services that are set to start automatically
    with a delayed startup.

.PARAMETER ComputerName
    The remote computer(s) to check the status of the services on.

.PARAMETER Credential
    Specifies a user account that has permission to perform this action. The default
    is the current user.

.EXAMPLE
     Get-MrAutoStoppedService -ComputerName 'Server1', 'Server2'

.EXAMPLE
     'Server1', 'Server2' | Get-MrAutoStoppedService

.EXAMPLE
     Get-MrAutoStoppedService -ComputerName 'Server1' -Credential (Get-Credential)

.INPUTS
    String

.OUTPUTS
    PSCustomObject

.NOTES
    Author:  Mike F Robbins
    Website: http://mikefrobbins.com
    Twitter: @mikefrobbins
#>

    [CmdletBinding()]
    param (

    )

    #Function Body

}
```

將註解型說明新增至函式時，可以擷取其說明，就像預設的內建命令一樣。

用於在 PowerShell 中撰寫函式的所有語法，可能顯得過於困難，尤其是對於剛開始的新手來說。 有時候，如果我不記得某個項目的語法，我會在個別監視器上開啟第二個 ISE 複本，並在輸入我的函式的程式碼時，檢視「Cmdlet (進階函式) - 完整」程式碼片段。 您可以使用 <kbd>Ctrl</kbd>+<kbd>J</kbd> 按鍵組合，在 PowerShell ISE 中存取程式碼片段。

## <a name="summary"></a>摘要

在本章中，您已了解在 PowerShell 中撰寫函式的基本概念，包括如何將函式轉換成進階函式，以及在撰寫 PowerShell 函式時應該考慮的一些更重要的元素，例如，參數驗證、詳細資訊輸出、管線輸入、錯誤處理和註解型說明。

## <a name="review"></a>檢閱

1. 如何在 PowerShell 中取得核准的動詞清單？
1. 如何將 PowerShell 函式轉換成進階函式？
1. 何時應該將 **WhatIf** 和 **Confirm** 參數新增至您的 PowerShell 函式？
1. 如何將非終止錯誤轉變成終止的錯誤？
1. 為什麼您應該在函式中新增註解型說明？

## <a name="recommended-reading"></a>建議閱讀資料

- [about_Functions][]
- [about_Functions_Advanced_Parameters][]
- [about_CommonParameters][]
- [about_Functions_CmdletBindingAttribute][]
- [about_Functions_Advanced][]
- [about_Try_Catch_Finally][]
- [about_Comment_Based_Help][]
- [影片：使用進階函式和指令碼模組的 PowerShell 工具製作][]

<!-- link references -->
[about_Functions]: /powershell/module/microsoft.powershell.core/about/about_functions
[about_Functions_Advanced_Parameters]: /powershell/module/microsoft.powershell.core/about/about_functions_advanced_parameters
[about_CommonParameters]: /powershell/module/microsoft.powershell.core/about/about_commonparameters
[about_Functions_CmdletBindingAttribute]: /powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute
[about_Functions_Advanced]: /powershell/module/microsoft.powershell.core/about/about_functions_advanced
[about_Try_Catch_Finally]: /powershell/module/microsoft.powershell.core/about/about_try_catch_finally
[about_Comment_Based_Help]: /powershell/module/microsoft.powershell.core/about/about_comment_based_help
[影片：使用進階函式和指令碼模組的 PowerShell 工具製作]： https://mikefrobbins.com/2016/05/26/video-powershell-toolmaking-with-advanced-functions-and-script-modules/) [Pascal 命名法的大小寫]：/dotnet/standard/design-guidelines/capitalization-conventionss
