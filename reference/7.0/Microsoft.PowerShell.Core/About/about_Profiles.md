---
description: 說明如何建立和使用 PowerShell 設定檔。
keywords: powershell,cmdlet
ms.date: 11/30/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Profiles
ms.openlocfilehash: 3fb6a67e160281f60f20c187bf37c6920a506705
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206616"
---
# <a name="about-profiles"></a>關於設定檔

## <a name="short-description"></a>簡短描述
說明如何建立和使用 PowerShell 設定檔。

## <a name="long-description"></a>完整描述

您可以建立 PowerShell 設定檔來自訂您的環境，並將工作階段特定項目新增至您啟動的每一個 PowerShell 工作階段。

PowerShell 設定檔是在 PowerShell 啟動時執行的指令碼。 您可以使用設定檔做為登入腳本來自訂環境。 您可以新增命令、別名、函式、變數、嵌入式管理單元、模組和 PowerShell 磁片磁碟機。 您也可以將其他會話專屬的元素新增至您的設定檔，以便在每個會話中都能使用它們，而不需要匯入或重新建立它們。

PowerShell 支援使用者和主機程式的數個設定檔。 不過，它不會為您建立設定檔。 本主題說明這些設定檔，並說明如何在您的電腦上建立及維護設定檔。

它說明如何使用 PowerShell 主控台的 **NoProfile** 參數 ( # A0) 來啟動 powershell，而不需要任何設定檔。 而且，它會說明 PowerShell 執行原則對設定檔的影響。

## <a name="the-profile-files"></a>設定檔

PowerShell 支援數個設定檔。 此外，PowerShell 主機程式可以支援自己的主機專屬設定檔。

例如，PowerShell 主控台支援下列基本設定檔。 設定檔會依優先順序列出。 第一個設定檔的優先順序最高。

|Description               | 路徑                                          |
|--------------------------|-----------------------------------------------|
|所有使用者、所有主機      |$PSHOME \\Profile.ps1                           |
|所有使用者、目前的主機   |$PSHOME \\Microsoft.PowerShell_profile.ps1      |
|目前的使用者，所有主機   |$Home \\ [My] 檔 \\ PowerShell \\Profile.ps1 |
|目前的使用者，目前的主機|$Home \\ [My] 檔 \\ PowerShell\\<br>Microsoft.PowerShell_profile.ps1 |

設定檔路徑包含下列變數：

- `$PSHOME`變數，儲存 PowerShell 的安裝目錄
- `$Home`變數，用來儲存目前使用者的主目錄

此外，裝載 PowerShell 的其他程式也可以支援自己的設定檔。 例如，Visual Studio Code 支援下列主機特定設定檔。

|Description               | 路徑                                     |
|--------------------------|------------------------------------------|
|所有使用者、目前的主機   |$PSHOME \\Microsoft.VSCode_profile.ps1|
|目前的使用者，目前的主機|$Home \\ [My] 檔 \\ PowerShell\\<br>Microsoft.VSCode_profile.ps1|

在 PowerShell 說明中，「CurrentUser，Current Host」設定檔是最常稱為「您的 PowerShell 設定檔」的設定檔。

## <a name="the-profile-variable"></a>$PROFILE 變數

`$PROFILE`自動變數會儲存目前會話中可用之 PowerShell 設定檔的路徑。

若要查看設定檔路徑，請顯示變數的值 `$PROFILE` 。 您也可以 `$PROFILE` 在命令中使用變數來代表路徑。

`$PROFILE`變數會儲存「目前使用者、目前主機」設定檔的路徑。 其他設定檔會儲存在變數的附注屬性中 `$PROFILE` 。

例如，在 `$PROFILE` Windows PowerShell 主控台中，變數具有下列值。

|描述                |Name                              |
|---------------------------|----------------------------------|
|目前的使用者，目前的主機 |`$PROFILE`                        |
|目前的使用者，目前的主機 |`$PROFILE.CurrentUserCurrentHost` |
|目前的使用者，所有主機    |`$PROFILE.CurrentUserAllHosts`    |
|所有使用者、目前的主機    |`$PROFILE.AllUsersCurrentHost`    |
|所有使用者、所有主機       |`$PROFILE.AllUsersAllHosts`       |

由於變數的值會隨著每個 `$PROFILE` 使用者和每個主應用程式而變更，因此請務必在您使用的每個 PowerShell 主應用程式中顯示設定檔變數的值。

若要查看變數目前的值 `$PROFILE` ，請輸入：

```powershell
$PROFILE | Get-Member -Type NoteProperty
```

您可以使用 `$PROFILE` 多個命令中的變數。 例如，下列命令會在 [記事本] 中開啟「目前的使用者、目前的主機」設定檔：

```powershell
notepad $PROFILE
```

下列命令會判斷是否已在本機電腦上建立 "All Users，All Hosts" 設定檔：

```powershell
Test-Path -Path $PROFILE.AllUsersAllHosts
```

## <a name="how-to-create-a-profile"></a>如何建立設定檔

若要建立 PowerShell 設定檔，請使用下列命令格式：

```powershell
if (!(Test-Path -Path <profile-name>)) {
  New-Item -ItemType File -Path <profile-name> -Force
}
```

例如，若要在目前的 PowerShell 主應用程式中建立目前使用者的設定檔，請使用下列命令：

```powershell
if (!(Test-Path -Path $PROFILE)) {
  New-Item -ItemType File -Path $PROFILE -Force
}
```

在這個命令中， `If` 語句會防止您覆寫現有的設定檔。 將預留位置的值取代 \<profile-path\> 為您想要建立之設定檔檔案的路徑。

> [!NOTE]
> 若要在 Windows Vista 和更新版本的 Windows 中建立「所有使用者」設定檔，請使用 [以 **系統管理員身分執行** ] 選項啟動 PowerShell。

## <a name="how-to-edit-a-profile"></a>如何編輯設定檔

您可以在文字編輯器（例如 [記事本]）中開啟任何 PowerShell 設定檔。

若要在 [記事本] 的目前 PowerShell 主應用程式中開啟目前使用者的設定檔，請輸入：

```powershell
notepad $PROFILE
```

若要開啟其他設定檔，請指定設定檔名稱。 例如，若要為所有主機應用程式的所有使用者開啟設定檔，請輸入：

```powershell
notepad $PROFILE.AllUsersAllHosts
```

若要套用變更，請儲存設定檔，然後重新開機 PowerShell。

## <a name="how-to-choose-a-profile"></a>如何選擇設定檔

如果您使用多個主應用程式，請將您在所有主機應用程式中使用的專案放入 `$PROFILE.CurrentUserAllHosts` 設定檔中。 放置主機應用程式特定的專案，例如，設定主應用程式之背景色彩的命令（位於該主應用程式專用的設定檔中）。

如果您是為許多使用者自訂 PowerShell 的系統管理員，請遵循下列指導方針：

- 將一般專案儲存在 `$PROFILE.AllUsersAllHosts` 設定檔中
- 將主應用程式專用的專案儲存在 `$PROFILE.AllUsersCurrentHost` 主機應用程式專用的設定檔中
- 在使用者特定的設定檔中儲存特定使用者的專案

請務必查看主機應用程式檔，以瞭解 PowerShell 設定檔的任何特殊執行。

## <a name="how-to-use-a-profile"></a>如何使用設定檔

您在 PowerShell 中建立的許多專案和大部分執行的命令只會影響目前的會話。 當您結束會話時，會刪除專案。

會話專屬的命令和專案包括變數、喜好設定變數、別名、函式、命令 (除了 [ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)) 之外，以及您新增至會話的 PowerShell 模組。

若要儲存這些專案並讓這些專案可在所有未來的會話中使用，請將它們新增至 PowerShell 設定檔。

設定檔的另一個常見用途是儲存經常使用的函式、別名和變數。 當您將專案儲存在設定檔時，可以在任何適用的會話中使用它們，而不需要重新建立。

## <a name="how-to-start-a-profile"></a>如何啟動設定檔

當您開啟設定檔時，它是空白的。 不過，您可以使用經常使用的變數、別名和命令來填入它。

以下是一些協助您入門的建議。

### <a name="add-commands-that-make-it-easy-to-open-your-profile"></a>新增可讓您輕鬆開啟設定檔的命令

如果您使用「目前使用者」、「目前的主機」設定檔以外的設定檔，這會特別有用。 例如，新增下列命令：

```powershell
function Pro {notepad $PROFILE.CurrentUserAllHosts}
```

### <a name="add-a-function-that-lists-the-aliases-for-any-cmdlet"></a>新增可列出任何 Cmdlet 之別名的函式

```powershell
function Get-CmdletAlias ($cmdletname) {
  Get-Alias |
    Where-Object -FilterScript {$_.Definition -like "$cmdletname"} |
      Format-Table -Property Definition, Name -AutoSize
}
```

### <a name="customize-your-console"></a>自訂您的主控台

```powershell
function Color-Console {
  $Host.ui.rawui.backgroundcolor = "white"
  $Host.ui.rawui.foregroundcolor = "black"
  $hosttime = (Get-ChildItem -Path $PSHOME\PowerShell.exe).CreationTime
  $hostversion="$($Host.Version.Major)`.$($Host.Version.Minor)"
  $Host.UI.RawUI.WindowTitle = "PowerShell $hostversion ($hosttime)"
  Clear-Host
}
Color-Console
```

### <a name="add-a-customized-powershell-prompt"></a>新增自訂的 PowerShell 提示字元

```powershell
function Prompt
{
$env:COMPUTERNAME + "\" + (Get-Location) + "> "
}
```

如需 PowerShell 提示的詳細資訊，請參閱 [about_Prompts](about_Prompts.md)。

## <a name="the-noprofile-parameter"></a>NoProfile 參數

若要啟動沒有設定檔的 PowerShell，請使用 **PowerShell.exe** 的 **NoProfile** 參數，也就是啟動 powershell 的程式。

若要開始，請開啟可以啟動 PowerShell 的程式，例如 Cmd.exe 或 PowerShell 本身。 您也可以使用 Windows 中的 [執行] 對話方塊。

輸入：

```
PowerShell -NoProfile
```

如需 PowerShell.exe 之參數的完整清單，請輸入：

```
PowerShell -?
```

## <a name="profiles-and-execution-policy"></a>設定檔和執行原則

PowerShell 執行原則會決定您是否可以執行腳本並載入設定檔，包括設定檔。 **受限制** 的執行原則是預設值。 它可防止所有腳本執行，包括設定檔。 如果您使用「受限」原則，則不會執行設定檔，而且不會套用其內容。

`Set-ExecutionPolicy`命令會設定並變更您的執行原則。 它是在所有 PowerShell 會話中套用的幾個命令之一，因為該值會儲存在登錄中。 當您開啟主控台時，不需要進行設定，也不需要 `Set-ExecutionPolicy` 在設定檔中儲存命令。

## <a name="profiles-and-remote-sessions"></a>設定檔和遠端會話

PowerShell 設定檔不會自動在遠端會話中執行，因此設定檔新增的命令不會出現在遠端會話中。 此外，在 `$PROFILE` 遠端會話中不會填入自動變數。

若要在會話中執行設定檔，請使用 [Invoke 命令](xref:Microsoft.PowerShell.Core.Invoke-Command) Cmdlet。

例如，下列命令會從會話中的本機電腦執行「目前使用者、目前的主機」設定檔 `$s` 。

```powershell
Invoke-Command -Session $s -FilePath $PROFILE
```

下列命令會從會話中的遠端電腦執行「目前使用者、目前的主機」設定檔 `$s` 。 因為 `$PROFILE` 未填入變數，所以命令會使用設定檔的明確路徑。 我們會使用點出運算子，讓設定檔在遠端電腦上的目前範圍中執行，而不是在它自己的範圍中執行。

```powershell
Invoke-Command -Session $s -ScriptBlock {
  . "$HOME\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1"
}
```

執行此命令之後，就可以在中使用設定檔新增至會話的命令 `$s` 。

## <a name="see-also"></a>另請參閱

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_Functions](about_Functions.md)

[about_Prompts](about_Prompts.md)

[about_Execution_Policies](about_Execution_Policies.md)

[about_Signing](about_Signing.md)

[about_Remote](about_Remote.md)

[about_Scopes](about_Scopes.md)

[Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)
