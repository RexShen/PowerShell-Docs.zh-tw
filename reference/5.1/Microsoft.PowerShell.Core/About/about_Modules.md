---
description: 說明如何安裝、匯入及使用 PowerShell 模組。
Locale: en-US
ms.date: 12/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_modules?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Modules
ms.openlocfilehash: 30af4ed84e2332aecd60838f3bcd7741965c2ba1
ms.sourcegitcommit: 7b376314e7640c39a53aac9f0db8bb935514a960
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2020
ms.locfileid: "96564334"
---
# <a name="about-modules"></a>關於模組

## <a name="short-description"></a>簡短描述
說明如何安裝、匯入及使用 PowerShell 模組。

## <a name="long-description"></a>完整描述

模組是包含 PowerShell 成員（例如 Cmdlet、提供者、函式、工作流程、變數和別名）的套件。

撰寫命令者可以使用模組來組織其命令，並與其他人分享。 接收模組的人員可以將模組中的命令新增至其 PowerShell 會話，並如同內建命令一般使用它們。

本主題說明如何使用 PowerShell 模組。 如需如何撰寫 PowerShell 模組的詳細資訊，請參閱 [撰寫 Powershell 模組](/powershell/scripting/developer/module/writing-a-windows-powershell-module)。

## <a name="what-is-a-module"></a>什麼是模組？

模組是包含 PowerShell 成員（例如 Cmdlet、提供者、函式、工作流程、變數和別名）的套件。 此封裝的成員可以在 PowerShell 腳本、已編譯的 DLL 或兩者的組合中執行。 這些檔案通常會在單一目錄中群組在一起。 如需詳細資訊，請參閱 SDK 檔中的 [瞭解 Windows PowerShell 模組](/powershell/scripting/developer/module/understanding-a-windows-powershell-module) 。

## <a name="module-auto-loading"></a>模組自動載入

從 PowerShell 3.0 開始，當您第一次在已安裝的模組中執行任何命令時，PowerShell 會自動匯入模組。 您現在可以使用模組中的命令，而不需要任何設定或設定檔設定，因此在電腦上安裝模組之後不需要進行管理。

模組中的命令也比較容易找到。 `Get-Command`Cmdlet 現在會取得所有已安裝模組中的所有命令，即使它們尚未在會話中也一樣。 您可以尋找命令並使用它，而不需要先匯入模組。

下列每個範例都會將包含的 CimCmdlets 模組匯 `Get-CimInstance` 入到您的會話。

- 執行命令

  ```powershell
  Get-CimInstance Win32_OperatingSystem
  ```

- 取得命令

  ```powershell
  Get-Command Get-CimInstance
  ```

- 命令的取得協助

  ```powershell
  Get-Help Get-CimInstance
  ```

`Get-Command` 包含萬用字元 () 的命令 `*` 會被視為用於探索、不使用，且不會匯入任何模組。

只有儲存在 PSModulePath 環境變數所指定之位置中的模組才會自動匯入。 您必須執行 Cmdlet 來匯入其他位置中的模組 `Import-Module` 。

此外，使用 PowerShell 提供者的命令不會自動匯入模組。 例如，如果您使用需要 WSMan：磁片磁碟機的命令（例如 `Get-PSSessionConfiguration` Cmdlet），您可能需要執行指令程式 `Import-Module` 來匯入包含該磁片磁碟機的「 **Microsoft WSMan. 管理**」模組。 `WSMan:`

您仍然可以執行 `Import-Module` 命令以匯入模組，並使用 `$PSModuleAutoloadingPreference` 變數來啟用、停用及設定自動匯入模組。 如需詳細資訊，請參閱 [about_Preference_Variables](about_Preference_Variables.md)。

## <a name="how-to-use-a-module"></a>如何使用模組

若要使用模組，請執行下列工作：

1. 安裝模組 (這通常會為您完成)。
1. 尋找模組所新增的命令。
1. 使用模組所新增的命令。

此主題說明如何執行這些工作。 它也包含管理模組的其他實用資訊。

## <a name="how-to-install-a-module"></a>如何安裝模組

如果您以資料夾的形式接收模組，則必須先將它安裝在您的電腦上，才能在 PowerShell 中使用。

大部分的模組會為您安裝。 PowerShell 隨附數個預先安裝的模組，有時稱為 _核心_ 模組。 在以 Windows 為基礎的電腦上，如果作業系統隨附的功能具有管理它們的 Cmdlet，則會預先安裝這些模組。 當您使用安裝 Windows 功能時，您可以使用伺服器管理員中的 [新增角色及功能]，或主控台中的 [開啟或關閉 Windows 功能] 對話方塊，安裝任何屬於功能的 PowerShell 模組。 其他許多模組則包含在安裝模組的安裝程式或 Setup 程式中。

使用下列命令來建立目前使用者的 **模組** 目錄：

```powershell
New-Item -Type Directory -Path $HOME\Documents\WindowsPowerShell\Modules
```

將整個模組資料夾複製到 Modules 目錄中。 您可以使用任何方法複製資料夾，包括 Windows 檔案總管和 Cmd.exe，以及 PowerShell。 在 PowerShell 中，請使用 `Copy-Item` Cmdlet。 例如，若要將 MyModule 資料夾從複製 `C:\ps-test\MyModule` 到模組目錄，請輸入：

```powershell
Copy-Item -Path C:\ps-test\MyModule -Destination `
    $HOME\Documents\WindowsPowerShell\Modules
```

您可以在任何位置安裝模組，但在預設模組位置安裝模組可讓您更輕鬆地管理模組。 如需預設模組位置的詳細資訊，請參閱 [模組和 DSC 資源位置，以及 PSModulePath](#module-and-dsc-resource-locations-and-psmodulepath) 一節。

## <a name="how-to-find-installed-modules"></a>如何尋找已安裝的模組

若要尋找已安裝在預設模組位置，但尚未匯入到您工作階段的模組，請輸入：

```powershell
Get-Module -ListAvailable
```

若要尋找已匯入至會話的模組，請在 PowerShell 提示字元中輸入：

```powershell
Get-Module
```

如需有關 Cmdlet 的詳細資訊 `Get-Module` ，請參閱 [get-help](xref:Microsoft.PowerShell.Core.Get-Module)。

## <a name="how-to-find-the-commands-in-a-module"></a>如何尋找模組中的命令

使用 `Get-Command` Cmdlet 來尋找所有可用的命令。 您可以使用 Cmdlet 的參數 `Get-Command` 來篩選命令，例如依模組、名稱和名詞。

若要尋找模組中的所有命令，請輸入：

```powershell
Get-Command -Module <module-name>
```

例如，若要尋找 BitsTransfer 模組中的命令，請輸入：

```powershell
Get-Command -Module BitsTransfer
```

如需有關 Cmdlet 的詳細資訊 `Get-Command` ，請參閱 [Get 命令](xref:Microsoft.PowerShell.Core.Get-Command)。

## <a name="how-to-get-help-for-the-commands-in-a-module"></a>如何針對模組中的命令取得協助

如果模組包含所匯出命令的說明檔，則 `Get-Help` Cmdlet 會顯示說明主題。 使用您在 `Get-Help` PowerShell 中用來取得任何命令之說明的相同命令格式。

從 PowerShell 3.0 開始，您可以下載模組的說明檔，並下載說明檔的更新，讓它們永遠不會過時。

若要取得模組中之命令的說明，請輸入：

```powershell
Get-Help <command-name>
```

若要取得模組中命令的線上說明，請輸入：

```powershell
Get-Help <command-name> -Online
```

若要下載並安裝模組中命令的說明檔，請輸入：

```powershell
Update-Help -Module <module-name>
```

如需詳細資訊，請參閱 [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 和 [update-help](xref:Microsoft.PowerShell.Core.Update-Help)。

## <a name="how-to-import-a-module"></a>如何匯入模組

您可能必須匯入模組或匯入模組檔案。 當模組不是安裝在 **PSModulePath** 環境變數所指定的位置， `$env:PSModulePath` 或模組是由檔案（例如 .dll 或 .psm1 檔案）所組成，而非以資料夾形式傳遞的一般模組時，就需要匯入。

您也可以選擇匯入模組，讓您可以使用命令的參數 `Import-Module` ，例如 Prefix 參數，將特殊的前置詞加入至所有匯入命令的名詞名稱，或 **NoClobber** 參數，以防止模組加入將隱藏或取代會話中現有命令的命令。

若要匯入模組，請使用 `Import-Module` Cmdlet。

若要將 PSModulePath 位置中的模組匯入到目前的工作階段，請使用下列命令格式。

```powershell
Import-Module <module-name>
```

例如，下列命令會將 BitsTransfer 模組匯入到目前的會話。

```powershell
Import-Module BitsTransfer
```

若要匯入不在預設模組位置中的模組，請在命令中使用模組資料夾的完整路徑。

例如，若要將目錄中的 TestCmdlets 模組新增 `C:\ps-test` 至您的會話，請輸入：

```powershell
Import-Module C:\ps-test\TestCmdlets
```

若要匯入未包含在模組資料夾中的模組檔案，請在命令中使用模組檔案的完整路徑。

例如，若要將目錄中的 TestCmdlets.dll 模組新增 `C:\ps-test` 至您的會話，請輸入：

```powershell
Import-Module C:\ps-test\TestCmdlets.dll
```

如需有關將模組加入至會話的詳細資訊，請參閱 [import-module](xref:Microsoft.PowerShell.Core.Import-Module)。

## <a name="how-to-import-a-module-into-every-session"></a>如何將模組匯入到每個會話

此 `Import-Module` 命令會將模組匯入到您目前的 PowerShell 會話。 若要將模組匯入到您啟動的每個 PowerShell 會話，請將 `Import-Module` 命令新增至您的 powershell 設定檔。

如需設定檔的詳細資訊，請參閱 [about_Profiles](about_Profiles.md)。

## <a name="how-to-remove-a-module"></a>如何移除模組

當您移除模組時，會從工作階段刪除模組所加入的命令。

若要從您的會話移除模組，請使用下列命令格式。

```powershell
Remove-Module <module-name>
```

例如，下列命令會從目前的會話移除 BitsTransfer 模組。

```powershell
Remove-Module BitsTransfer
```

移除模組會反轉匯入模組的作業。 移除模組並不會解除安裝模組。 如需詳細資訊，請參閱 [移除模組](xref:Microsoft.PowerShell.Core.Remove-Module)。

## <a name="module-and-dsc-resource-locations-and-psmodulepath"></a>模組和 DSC 資源位置，以及 PSModulePath

`$env:PSModulePath`環境變數包含要搜尋以尋找模組和資源的資料夾位置清單。

依預設，指派給的有效位置 `$env:PSModulePath` 為：

- 全系統位置： `$PSHOME\Modules`

  這些資料夾包含隨附于 Windows 和 PowerShell 的模組。

  PowerShell 隨附的 DSC 資源會儲存在 `$PSHOME\Modules\PSDesiredStateConfiguration\DSCResources` 資料夾中。

- 使用者專屬的模組：這些是使用者在使用者範圍內所安裝的模組。 `Install-Module` 具有 **範圍** 參數，可讓您指定是否為目前的使用者或所有使用者安裝模組。 如需詳細資訊，請參閱 [Install 模組](xref:PowerShellGet.Install-Module)。

  Windows 上使用者專屬的 **CurrentUser** 位置是 `PowerShell\Modules` 位於使用者設定檔中檔位置的資料夾。 該位置的特定路徑會因 Windows 版本而異，以及您是否正在使用資料夾重新導向。 Microsoft OneDrive 也可以變更您的 [ **檔** ] 資料夾的位置。

  根據預設，在 Windows 10 上，該位置為 `$HOME\Documents\PowerShell\Modules` 。 在 Linux 或 Mac 上， **CurrentUser** 位置為 `$HOME/.local/share/powershell/Modules` 。

  > [!NOTE]
  > 您可以使用下列命令來確認 [ **檔** ] 資料夾的位置： `[Environment]::GetFolderPath('MyDocuments')` 。

- **AllUsers** 位置是 `$env:PROGRAMFILES\PowerShell\Modules` 在 Windows 上。 在 Linux 或 Mac 上，模組會儲存在中 `/usr/local/share/powershell/Modules` 。

> [!NOTE]
> 若要在目錄中新增或變更檔案 `$env:Windir\System32` ，請使用 [以 **系統管理員身分執行** ] 選項啟動 PowerShell。

您可以藉由變更 **PSModulePath** 環境變數的值，變更系統上的預設模組位置 `$Env:PSModulePath` 。 **PSModulePath** 環境變數是以 Path 環境變數為模型，而且具有相同的格式。

若要檢視預設模組位置，請輸入：

```powershell
$Env:PSModulePath
```

若要新增預設模組位置，請使用下列命令格式。

```powershell
$Env:PSModulePath = $Env:PSModulePath + ";<path>"
```

命令中的分號 (`;`) 會將新路徑與清單中該路徑前面的路徑隔開。

例如，若要新增 `C:\ps-test\Modules` 目錄，請輸入：

```powershell
$Env:PSModulePath + ";C:\ps-test\Modules"
```

當您新增 **PSModulePath** 的路徑時， `Get-Module` `Import-Module` 命令會包含該路徑中的模組。

您所設定的值只會影響目前的工作階段。 若要讓變更持續發生，請將命令新增至 PowerShell 設定檔，或使用主控台中的系統來變更登錄中 **PSModulePath** 環境變數的值。

此外，若要讓變更持續進行，您也可以使用 **System. 環境** 類別的 **SetEnvironmentVariable** 方法，將路徑加入至 **PSModulePath** 環境變數。

如需有關 **PSModulePath** 變數的詳細資訊，請參閱 [about_Environment_Variables](about_Environment_Variables.md)。

## <a name="modules-and-name-conflicts"></a>模組和名稱衝突

工作階段中的多個命令擁有相同名稱時，會發生名稱衝突。 當模組中的命令與工作階段中的命令或項目擁有相同的名稱時，匯入模組會造成名稱衝突。

名稱衝突可能會導致隱藏或取代命令。

### <a name="hidden"></a>Hidden

當某個命令不是您輸入命令名稱時執行的命令，但是您可以使用其他方法 (例如，使用起源自該命令之模組或嵌入式管理單元的名稱限定命令名稱) 執行它時，就會隱藏該命令。

### <a name="replaced"></a>已取代

當您因為具有相同名稱的命令覆寫某個命令而無法執行時，會取代該命令。 即使您移除造成衝突的模組，除非您重新啟動工作階段，否則還是無法執行遭到取代的命令。

`Import-Module` 可能會加入隱藏和取代目前會話中命令的命令。 此外，您工作階段中的命令可以隱藏模組所加入的命令。

若要偵測名稱衝突，請使用 Cmdlet 的 **All** 參數 `Get-Command` 。 從 PowerShell 3.0 開始， `Get-Command` 只會取得您輸入命令名稱時所執行的命令。 **All** 參數會取得會話中具有特定名稱的所有命令。

若要避免名稱衝突，請使用 Cmdlet 的 **NoClobber** 或 **Prefix** 參數 `Import-Module` 。 **Prefix** 參數會將前置詞加入至已匯入命令的名稱，使其在會話中是唯一的。 **NoClobber** 參數不會匯入任何會隱藏或取代會話中現有命令的命令。

您也可以使用的 **Alias**、 **Cmdlet**、 **Function** 和 **Variable** 參數， `Import-Module` 只選取您要匯入的命令，而且您可以排除在您的會話中造成名稱衝突的命令。

模組作者可以使用模組資訊清單的 **DefaultCommandPrefix** 屬性，將預設前置詞加入至所有命令名稱，藉以防止名稱衝突。
**Prefix** 參數的值會優先于 **DefaultCommandPrefix** 的值。

即使隱藏某個命令，您還是可以透過使用起源自該命令之模組或嵌入式管理單元的名稱限定命令名稱來執行。

PowerShell 命令優先順序規則可決定會話包含具有相同名稱的命令時，所執行的命令。

例如，當會話包含具有相同名稱的函式和 Cmdlet 時，PowerShell 預設會執行函式。 當工作階段預設包含具有相同名稱之相同類型的命令 (例如，具有相同名稱的兩個 Cmdlet) 時，它會執行最近加入的命令。

如需詳細資訊，包括優先順序規則的說明和執行隱藏命令的指示，請參閱 [about_Command_Precedence](about_Command_Precedence.md)。

## <a name="modules-and-snap-ins"></a>模組與嵌入式管理單元

您可以從模組和嵌入式管理單元將命令新增至您的會話。模組可以加入所有類型的命令，包括 Cmdlet、提供者和函式，以及專案，例如變數、別名和 PowerShell 磁片磁碟機。 嵌入式管理單元只能加入 Cmdlet 和提供者。

從您的工作階段移除模組或嵌入式管理單元之前，請使用下列命令判斷將會移除哪些命令。

若要在您的會話中尋找 Cmdlet 的來源，請使用下列命令格式：

```powershell
Get-Command <cmdlet-name> | Format-List -Property verb,noun,pssnapin,module
```

例如，若要尋找 Cmdlet 的來源 `Get-Date` ，請輸入：

```powershell
Get-Command Get-Date | Format-List -Property verb,noun,module
```

如需 PowerShell 嵌入式管理單元的詳細資訊，請參閱 [about_PSSnapins](about_PSSnapins.md)。

## <a name="module-related-warnings-and-errors"></a>模組相關警告和錯誤

模組所匯出的命令應遵循 PowerShell 命令命名規則。 如果您匯入的模組會匯出其名稱中具有未核准之動詞的 Cmdlet 或函式，則此 `Import-Module` Cmdlet 會顯示下列警告訊息。

> 警告：某些匯入的命令名稱包含未核准的動詞命令，可能會讓它們更不容易探索。 請使用 Verbose 參數取得詳細資訊，或輸入 Get-Verb 查看核准的動詞清單。

這則訊息只是一個警告。 模組仍然完整匯入，包括不合格的命令。 雖然訊息是顯示給模組的使用者，但命名的問題應該由模組作者修正。

若要隱藏警告訊息，請使用 Cmdlet 的 **DisableNameChecking** 參數 `Import-Module` 。

## <a name="built-in-modules-and-snap-ins"></a>內建模組和嵌入式管理單元

在 powershell 2.0 和 PowerShell 3.0 和更新版本中舊版的主機程式中，隨 PowerShell 安裝的核心命令會封裝在自動加入至每個 PowerShell 會話的嵌入式管理單元中。

從 PowerShell 3.0 開始，針對執行 `InitialSessionState.CreateDefault2` 初始會話狀態 API 的主機程式，預設會將 Microsoft. 核心嵌入式管理單元加入至每個會話。 第一次使用時，會自動載入模組。

> [!NOTE]
> 遠端會話（包括使用 Cmdlet 啟動的會話 `New-PSSession` ）是較舊的會話，其中內建命令會封裝在嵌入式管理單元中。

下列模組 (或嵌入式管理單元) 與 PowerShell 一起安裝。

- CimCmdlets
- Microsoft.PowerShell.Archive
- Microsoft.PowerShell.Core
- Microsoft.PowerShell.Diagnostics
- Microsoft.PowerShell.Host
- Microsoft.PowerShell.Management
- Microsoft.PowerShell.ODataUtils
- Microsoft.PowerShell.Security
- Microsoft.PowerShell.Utility
- Microsoft.WSMan.Management
- PackageManagement
- PowerShellGet
- PSDesiredStateConfiguration
- PSDiagnostics
- PSScheduledJob
- PSWorkflow
- PSWorkflowUtility
- ISE

## <a name="logging-module-events"></a>記錄模組事件

從 PowerShell 3.0 開始，您可以藉由將模組和嵌入式管理單元的 **LogPipelineExecutionDetails** 屬性設定為，來記錄 powershell 模組和嵌入式管理單元中的 Cmdlet 和函式的執行事件 `$True` 。
您也可以使用群組原則設定，開啟模組記錄，以在所有 PowerShell 會話中啟用模組記錄。 如需詳細資訊，請參閱 [about_EventLogs](about_EventLogs.md) 和 [about_Group_Policy_Settings](about_Group_Policy_Settings.md)。

## <a name="see-also"></a>另請參閱

[about_Command_Precedence](about_Command_Precedence.md)

[about_Group_Policy_Settings](about_Group_Policy_Settings.md)

[about_PSSnapins](about_PSSnapins.md)

[Get-Command](xref:Microsoft.PowerShell.Core.Get-Command)

[Get-Help](xref:Microsoft.PowerShell.Core.Get-Help)

[Get-Module](xref:Microsoft.PowerShell.Core.Get-Module)

[Import-Module](xref:Microsoft.PowerShell.Core.Import-Module)

[Remove-Module](xref:Microsoft.PowerShell.Core.Remove-Module)
