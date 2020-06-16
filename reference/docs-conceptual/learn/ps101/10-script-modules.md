---
title: 指令碼模組
description: 指令碼模組是將指令碼和函式封裝成可重複使用工具的簡單方法。
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 661ba725764e1f31df628f6c5f2d58d760656e37
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2020
ms.locfileid: "84438279"
---
# <a name="chapter-10---script-modules"></a>第 10 章 - 指令碼模組

如果是您要經常執行的動作，將 PowerShell 中的一行程式碼和指令碼轉換成可重複使用的工具，即變得更為重要。 將您的函式封裝在指令碼模組中，讓它們看起來更專業，並使其更容易共用。

## <a name="dot-sourcing-functions"></a>點執行函式

在上一章中，我們未討論的項目是點執行函式。 當指令碼中的函式不是模組的一部分時，將它載入記憶體的唯一方法就是對儲存在所在的 `.PS1` 檔案進行點執行。

下列函式已儲存為 `Get-MrPSVersion.ps1`。

```powershell
function Get-MrPSVersion {
    $PSVersionTable
}
```

執行指令碼時，沒有發生任何動作。

```powershell
.\Get-MrPSVersion.ps1
```

如果您嘗試呼叫函式，其會產生錯誤訊息。

```powershell
Get-MrPSVersion
```

```Output
Get-MrPSVersion : The term 'Get-MrPSVersion' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or if a path
was included, verify that the path is correct and try again.
At line:1 char:1
+ Get-MrPSVersion
    + CategoryInfo          : ObjectNotFound: (Get-MrPSVersion:String) [], CommandNotFou
   ndException
    + FullyQualifiedErrorId : CommandNotFoundException

```

您可以藉由檢查函式是否存在於 **Function** PSDrive，判斷是否已將函式載入記憶體。

```powershell
Get-ChildItem -Path Function:\Get-MrPSVersion
```

```Output
Get-ChildItem : Cannot find path 'Get-MrPSVersion' because it does not exist.
At line:1 char:1
+ Get-ChildItem -Path Function:\Get-MrPSVersion
    + CategoryInfo          : ObjectNotFound: (Get-MrPSVersion:String) [Get-ChildItem],
   ItemNotFoundException
    + FullyQualifiedErrorId : PathNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
```

呼叫包含函式之指令碼的問題是，函式會在 _Script_ 範圍中載入。 當指令碼完成時，就會移除該範圍，並隨著它移除函式。

必須將函式載入 _Global_ 範圍。 這可以透過對包含函式的指令碼進行點執行來完成。 可以使用相對路徑。

```powershell
. .\Get-MrPSVersion.ps1
```

也可以使用完整路徑。

```powershell
. C:\Demo\Get-MrPSVersion.ps1
```

如果路徑的某部分儲存在變數中，則可以與路徑的其餘部分結合。
不需要使用字串串連，將變數與路徑的其餘部分結合在一起。

```powershell
$Path = 'C:\'
. $Path\Get-MrPSVersion.ps1
```

現在當我檢查 **Function** PSDrive 時，`Get-MrPSVersion` 函式會存在。

```powershell
Get-ChildItem -Path Function:\Get-MrPSVersion
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Function        Get-MrPSVersion
```

## <a name="script-modules"></a>指令碼模組

PowerShell 中的指令碼模組只是一個檔案，其中包含一或多個儲存為 `.PSM1` 檔案而不是 `.PS1` 檔案的函式。

如何建立指令碼模組？ 您可能會猜測使用名為 `New-Module` 之類的命令。 您的假設會是錯誤的。 雖然 PowerShell 中有一個名為 `New-Module` 的命令，該命令會建立動態模組，而不是指令碼模組。 請務必閱讀命令的說明，即使您認為已找到所需的命令也是如此。

```powershell
help New-Module
```

```Output
NAME
    New-Module

SYNOPSIS
    Creates a new dynamic module that exists only in memory.

SYNTAX
    New-Module [-Name] <String> [-ScriptBlock] <ScriptBlock> [-ArgumentList <Object[]>]
    [-AsCustomObject] [-Cmdlet <String[]>] [-Function <String[]>] [-ReturnResult]
    [<CommonParameters>]

DESCRIPTION
    The New-Module cmdlet creates a dynamic module from a script block. The members of
    the dynamic module, such as functions and variables, are immediately available in
    the session and remain available until you close the session.

    Like static modules, by default, the cmdlets and functions in a dynamic module are
    exported and the variables and aliases are not. However, you can use the
    Export-ModuleMember cmdlet and the parameters of New-Module to override the defaults.

    You can also use the AsCustomObject parameter of New-Module to return the dynamic
    module as a custom object. The members of the modules, such as functions, are
    implemented as script methods of the custom object instead of being imported into
    the session.

    Dynamic modules exist only in memory, not on disk. Like all modules, the members of
    dynamic modules run in a private module scope that is a child of the global scope.
    Get-Module cannot get a dynamic module, but Get-Command can get the exported members.

    To make a dynamic module available to Get-Module , pipe a New-Module command to
    Import-Module, or pipe the module object that New-Module returns to Import-Module .
    This action adds the dynamic module to the Get-Module list, but it does not save the
    module to disk or make it persistent.

RELATED LINKS
    Online Version: http://go.microsoft.com/fwlink/?LinkId=821495
    Export-ModuleMember
    Get-Module
    Import-Module
    Remove-Module

REMARKS
    To see the examples, type: "get-help New-Module -examples".
    For more information, type: "get-help New-Module -detailed".
    For technical information, type: "get-help New-Module -full".
    For online help, type: "get-help New-Module -online"
```

在上一章中，我提到函式應該使用已核准的動詞，否則會在匯入模組時產生警告訊息。 下列程式碼會使用 `New-Module` Cmdlet，在記憶體中建立動態模組。 此課程模組示範未核准的動詞警告。

```powershell
New-Module -Name MyModule -ScriptBlock {

    function Return-MrOsVersion {
        Get-CimInstance -ClassName Win32_OperatingSystem |
        Select-Object -Property @{label='OperatingSystem';expression={$_.Caption}}
    }

    Export-ModuleMember -Function Return-MrOsVersion

} | Import-Module
```

```Output
WARNING: The names of some imported commands from the module 'MyModule' include
unapproved verbs that might make them less discoverable. To find the commands with
unapproved verbs, run the Import-Module command again with the Verbose parameter. For a
list of approved verbs, type Get-Verb.
```

只是要重申，雖然先前的範例中使用了 `New-Module` Cmdlet，但這並不是用來在 PowerShell 中建立指令碼模組的命令。

將下列兩個函式儲存在名為 `MyScriptModule.psm1` 的檔案中。

```powershell
function Get-MrPSVersion {
    $PSVersionTable
}

function Get-MrComputerName {
    $env:COMPUTERNAME
}
```

嘗試呼叫其中一個函式。

```powershell
Get-MrComputerName
```

```Output
Get-MrComputerName : The term 'Get-MrComputerName' is not recognized as the name of a
cmdlet, function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
At line:1 char:1
+ Get-MrComputerName
    + CategoryInfo          : ObjectNotFound: (Get-MrComputerName:String) [], CommandNot
   FoundException
    + FullyQualifiedErrorId : CommandNotFoundException
```

系統會產生錯誤訊息，指出找不到函式。 您也可以像之前一樣檢查 **Function** PSDrive，而您也會發現也它不存在於其中。

您可以使用 `Import-Module` Cmdlet 手動匯入檔案。

```powershell
Import-Module C:\MyScriptModule.psm1
```

模組自動載入功能是在 PowerShell 版本 3 中推出。 若要利用模組自動載入，必須將指令碼模組儲存在與 `.PSM1` 檔案具有相同基礎名稱的資料夾，以及在 `$env:PSModulePath` 中指定的位置。

```powershell
$env:PSModulePath
```

```Output
C:\Users\mike-ladm\Documents\WindowsPowerShell\Modules;C:\Program Files\WindowsPowerShell\
Modules;C:\Windows\system32\WindowsPowerShell\v1.0\Modules;C:\Program Files (x86)\Microsof
t SQL Server\130\Tools\PowerShell\Modules\
```

結果難以閱讀。 由於路徑是以分號分隔，因此您可以分割結果，以在個別行上傳回每個路徑。 這會讓它們更容易閱讀。

```powershell
$env:PSModulePath -split ';'
```

```Output
C:\Users\mike-ladm\Documents\WindowsPowerShell\Modules
C:\Program Files\WindowsPowerShell\Modules
C:\Windows\system32\WindowsPowerShell\v1.0\Modules
C:\Program Files (x86)\Microsoft SQL Server\130\Tools\PowerShell\Modules\
```

清單中的前三個路徑是預設值。 安裝 SQL Server Management Studio 時，會新增最後一個路徑。 若要讓模組自動載入正常執行，`MyScriptModule.psm1` 檔案必須位於其中一個路徑內名為 `MyScriptModule` 的資料夾中。

慢著。 就我的情況，我目前的使用者路徑不是清單中的第一個。 我幾乎從不會使用該路徑，因為我用來登入 Windows 的使用者與用來執行 PowerShell 的使用者不同。 這表示它不在一般的 [我的文件] 資料夾中。

第二個路徑是 **AllUsers** 路徑。 這是我用來儲存所有模組的位置。

第三個路徑在 `C:\Windows\System32` 之下。 只有 Microsoft 應該將模組儲存在該位置，因為它位於作業系統資料夾內。

一旦 `.PSM1` 檔案位於正確的路徑中，則在呼叫其中一個命令時，模組就會自動載入。

## <a name="module-manifests"></a>模組資訊清單

所有模組都應該有模組資訊清單。 模組資訊清單包含關於模組的中繼資料。
模組資訊清單檔案的副檔名為 `.PSD1`。 並非具有 `.PSD1` 副檔名的所有檔案都是模組資訊清單。 它們也可以用於儲存 DSC 設定的環境部分等項目。 `New-ModuleManifest` 用來建立模組資訊清單。 **Path** 是唯一需要的值。 不過，如果未指定 **RootModule**，模組將無法正常執行。 如果您決定使用 PowerShellGet 將模組上傳至 NuGet 存放庫，則最好指定 **Author** 和 **Description**，因為在該案例中，這些值是必要的。

沒有資訊清單的模組版本為 0.0。 模組沒有資訊清單這點實在很明顯。

```powershell
Get-Module -Name MyScriptModule
```

```Output
ModuleType Version    Name                                ExportedCommands
---------- -------    ----                                ----------------
Script     0.0        myscriptmodule                      {Get-MrComputerName, Get-MrP...
```

您可以使用所有建議的資訊來建立模組資訊清單。

```powershell
New-ModuleManifest -Path $env:ProgramFiles\WindowsPowerShell\Modules\MyScriptModule\MyScriptModule.psd1 -RootModule MyScriptModule -Author 'Mike F Robbins' -Description 'MyScriptModule' -CompanyName 'mikefrobbins.com'
```

如果在模組資訊清單初始建立期間遺漏了任何這項資訊，則可以稍後使用 `Update-ModuleManifest` 來新增或更新。 資訊清單建立之後，請勿使用 `New-ModuleManifest` 重新建立資訊清單，因為 GUID 會變更。

## <a name="defining-public-and-private-functions"></a>定義公用和私人函式

您可能會有想要設為私人的協助程式函式，而且只能由模組內的其他函式存取。 它們無法供您模組的使用者存取。 有幾個不同方式可以完成此操作。

如果您未遵循最佳做法，而且只有一個 `.PSM1` 檔案，則您唯一的選項是使用 `Export-ModuleMember` Cmdlet。

```powershell
function Get-MrPSVersion {
    $PSVersionTable
}

function Get-MrComputerName {
    $env:COMPUTERNAME
}

Export-ModuleMember -Function Get-MrPSVersion
```

在上述範例中，只有 `Get-MrPSVersion` 函式可供您模組的使用者使用，但 `Get-MrComputerName` 函式可供模組本身內的其他函式使用。

```powershell
Get-Command -Module MyScriptModule

CommandType     Name                        Version    Source
-----------     ----                        -------    ------
Function        Get-MrPSVersion             1.0        MyScript...
```

如果您已將模組資訊清單新增至模組 (而且您應該這麼做)，則建議您在模組資訊清單的 **FunctionsToExport** 區段中，指定您想要匯出的個別函式。

```powershell
FunctionsToExport = 'Get-MrPSVersion'
```

不需要在 `.PSM1` 檔案和模組資訊清單的 **FunctionsToExport** 區段中同時使用 `Export-ModuleMember`。 在其中一個中使用已足夠。

## <a name="summary"></a>摘要

在本章中，您已了解如何在 PowerShell 中將您的函式轉換成指令碼模組。 您也已了解一些建立指令碼模組的最佳做法，例如，建立指令碼模組的模組資訊清單。

## <a name="review"></a>檢閱

1. 如何在 PowerShell 中建立指令碼模組？
1. 為何您的函式務必需要使用已核准的動詞？
1. 如何在 PowerShell 中建立模組資訊清單？
1. 用於從您的模組匯出僅特定函式的兩個選項為何？
1. 呼叫命令時，模組需要哪些項目才能自動載入？

## <a name="recommended-reading"></a>建議閱讀資料

- [如何建立 PowerShell 指令碼模組和模組資訊清單][]
- [about_Modules][]
- [New-ModuleManifest][]
- [Export-ModuleMember][]

<!-- link references -->
[如何建立 PowerShell 指令碼模組和模組資訊清單]: https://mikefrobbins.com/2013/07/04/how-to-create-powershell-script-modules-and-module-manifests/
[about_Modules]: /powershell/module/microsoft.powershell.core/about/about_modules
[New-ModuleManifest]: /powershell/module/microsoft.powershell.core/new-modulemanifest
[Export-ModuleMember]: /powershell/module/microsoft.powershell.core/export-modulemember
