---
ms.date: 09/13/2016
ms.topic: reference
title: 安裝 PowerShell 模組
description: 安裝 PowerShell 模組
ms.openlocfilehash: 3c7a4413168934ca4de1912c9615a6ae0fc45788
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645337"
---
# <a name="installing-a-powershell-module"></a>安裝 PowerShell 模組

在您建立 PowerShell 模組之後，您可能想要將該模組安裝到系統上，讓您或其他人可以加以使用。 一般來說，這包含將模組檔案 (也就是 .psm1 或二進位組件、模組資訊清單，以及任何其他相關聯的檔案) 複製到該電腦上的目錄中。 對於非常小的專案來說，您可能只需使用 [Windows 檔案總管] 將這些檔案複製並貼到單一遠端電腦即可；不過，對於較大型的解決方案來說，您可能需要使用更複雜的安裝程序。 無論您是以何種方式將模組移至系統上，PowerShell 都可以使用數種技術來讓使用者尋找並使用您的模組。 因此，安裝的主要問題在於確保 PowerShell 能夠找到您的模組。 如需詳細資訊，請參閱[匯入 PowerShell 模組](./importing-a-powershell-module.md)。

## <a name="rules-for-installing-modules"></a>安裝模組的規則

下列資訊適用於所有模組，包括您建立以供自己使用的模組、從其他合作對象取得的模組，以及您發佈給其他人的模組。

### <a name="install-modules-in-psmodulepath"></a>在 PSModulePath 中安裝模組

請盡可能將所有模組安裝到列於 **PSModulePath** 環境變數中的路徑，或是將模組路徑新增到 **PSModulePath** 環境變數值。

**PSModulePath** 環境變數 ($Env:PSModulePath) 包含 Windows PowerShell 模組的位置。 Cmdlet 需仰賴此環境變數的值來尋找模組。

根據預設， **PSModulePath** 環境變數值包含下列系統與使用者模組目錄，但您可以對該值進行新增及編輯。

- `$PSHome\Modules` (%Windir%\System32\WindowsPowerShell\v1.0\Modules)

  > [!WARNING]
  > 此位置是保留給 Windows 隨附的模組。 請勿將模組安裝到此位置。

- `$Home\Documents\WindowsPowerShell\Modules` (%UserProfile%\Documents\WindowsPowerShell\Modules)

- `$Env:ProgramFiles\WindowsPowerShell\Modules` (%ProgramFiles%\WindowsPowerShell\Modules)

  若要取得 **PSModulePath** 環境變數的值，請使用下列其中一個命令。

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  若要將模組路徑新增到 **PSModulePath** 環境變數值的值，請使用下列命令格式。 此格式使用 **System.Environment** 類別的 **SetEnvironmentVariable** 方法，來對 **PSModulePath** 環境變數進行與工作階段無關的變更。

  ```powershell
  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > 在您將路徑新增到 **PSModulePath** 之後，便應該廣播關於該變更的環境訊息。 廣播變更可讓其他應用程式 (例如殼層) 取得該變更。 若要廣播變更，請讓您的產品安裝程式碼傳送將 `lParam` 設定為 "Environment" 字串的 **WM_SETTINGCHANGE** 訊息。 請務必在模組安裝程式碼具有更新的 **PSModulePath** 之後傳送該訊息。

### <a name="use-the-correct-module-directory-name"></a>使用正確的模組目錄名稱

一個格式正確的模組，應該要儲存在與模組目錄中至少一個檔案的基底名稱具有相同名稱的目錄中。 如果模組的格式不正確，Windows PowerShell 便無法將其辨識為模組。

檔案的「基底名稱」是不含副檔名的名稱。 在格式正確的模組中，包含模組檔案之目錄的名稱必須符合模組中至少一個檔案的基底名稱。

例如，在範例 Fabrikam 模組中，包含模組檔案的目錄名為 "Fabrikam"，且至少有一個檔案具有 "Fabrikam" 基底名稱。 在此情況下，Fabrikam.psd1 與 Fabrikam.dll 都具有 "Fabrikam" 基底名稱。

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

### <a name="effect-of-incorrect-installation"></a>不正確安裝的影響

如果模組格式不正確，且其位置未包含在 **PSModulePath** 環境變數的值中，則 Windows PowerShell 的基本探索功能 (例如下列功能) 將無法運作。

- 模組自動載入功能無法自動匯入模組。

- [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) Cmdlet 的 `ListAvailable` 參數找不到模組。

- [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet 找不到模組。 若要匯入模組，您必須提供根模組檔案或模組資訊清單檔的完整路徑。

  除非將模組匯入工作階段，否則其他功能 (例如下列功能) 將無法運作。 對於位於 **PSModulePath** 環境變數中且格式正確的模組來說，即使模組未匯入工作階段，這些功能也仍然可以運作。

- [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) Cmdlet 無法在模組中找到命令。

- [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) 與 [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) Cmdlet 無法更新或儲存模組的說明。

- [Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) Cmdlet 無法在模組中找到並顯示命令。

  Windows PowerShell 整合式指令碼環境 (ISE) 中的 `Show-Command` 視窗遺失模組中的命令。

## <a name="where-to-install-modules"></a>安裝模組的位置

此節說明在檔案系統中安裝 Windows PowerShell 模組的位置。 該位置會取決於模組的使用方式。

### <a name="installing-modules-for-a-specific-user"></a>為特定使用者安裝模組

如果您是自行建立模組，或是從另一個合作對象 (例如 Windows PowerShell 社群網站) 取得模組，且您只想要讓該模組供您的使用者帳戶使用，請將模組安裝到您的使用者特定 [Modules] 目錄中。

`$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

使用者特定 [Modules] 目錄預設已新增至 **PSModulePath** 環境變數的值中。

### <a name="installing-modules-for-all-users-in-program-files"></a>為所有使用者在 [Program Files] 中安裝模組

如果您想要讓模組供電腦上所有使用者帳戶使用，請將模組安裝到 [Program Files] 位置中。

`$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

> [!NOTE]
> 在 Windows PowerShell 4.0 與更新版本中，[Program Files] 位置預設已新增至 PSModulePath 環境變數的值中。 針對舊版的 Windows PowerShell，您可以手動建立 [Program Files] 位置 (%ProgramFiles%\WindowsPowerShell\Modules)，並以上述方式將此路徑新增至您的 PSModulePath 環境變數。

### <a name="installing-modules-in-a-product-directory"></a>在產品目錄中安裝模組

如果您是要將模組發佈至其他合作對象，請使用上述的預設 [Program Files] 位置，或是在 %ProgramFiles% 目錄中自行建立公司特定或產品特定的子目錄。

例如，假設 Fabrikam Technologies 這家虛構公司正在為他們的 Fabrikam Manager 產品推出 Windows PowerShell 模組。 他們的模組安裝程式會在 Fabrikam Manager 產品子目錄中建立 [Modules] 子目錄。

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

為了讓 Windows PowerShell 模組探索功能找到 Fabrikam 模組，Fabrikam 模組安裝程式會將該模組位置新增到 **PSModulePath** 環境變數的值中。

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam Technologies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a>在 [Common Files] 目錄中安裝模組

如果模組會用於某個產品的多個元件或多個版本，請將該模組安裝到 %ProgramFiles%\Common Files\Modules 的模組特定子目錄中。

在下列範例中，Fabrikam 模組會安裝到 `%ProgramFiles%\Common Files\Modules` 子目錄的 [Fabrikam] 子目錄中。 請注意，在 [Modules] 子目錄中，每個模組都位於其自己的子目錄中。

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)
```

然後，安裝程式會確保 **PSModulePath** 環境變數的值會包含 Common Files\Modules 子目錄的路徑。

```powershell
$m = $env:ProgramFiles + '\Common Files\Modules'
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$q = $p -split ';'
if ($q -notContains $m) {
    $q += ";$m"
}
$p = $q -join ';'
[Environment]::SetEnvironmentVariable("PSModulePath", $p)
```

## <a name="installing-multiple-versions-of-a-module"></a>安裝模組的多個版本

若要安裝相同模組的多個版本，請使用下列程序。

1. 為模組的每個版本建立目錄。 在目錄名稱中包含版本號碼。
2. 為模組的每個版本建立模組資訊清單。 在資訊清單 **ModuleVersion** 機碼的值中，輸入模組版本號碼。 將資訊清單檔 (.psd1) 儲存到該模組的版本特定目錄中。
3. 將模組根資料夾路徑新增到 **PSModulePath** 環境變數的值中，如下列範例所示。

若要匯入模組的特定版本，終端使用者可以使用 [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet 的 `MinimumVersion` 或 `RequiredVersion` 參數。

例如，如果 Fabrikam 模組提供 8.0 與 9.0 版，Fabrikam 模組目錄結構可能如下所示。

 ```
C:\Program Files
Fabrikam Manager
  Fabrikam8
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "8.0")
      Fabrikam.dll (module assembly)
  Fabrikam9
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "9.0")
      Fabrikam.dll (module assembly)
```

安裝程式會將這兩個模組路徑新增到 **PSModulePath** 環境變數值。

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

完成這些步驟時， [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) Cmdlet 的 **ListAvailable** 參數便會取得這兩個 Fabrikam 模組。 若要匯入特定模組，請使用 [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet 的 `MinimumVersion` 或 `RequiredVersion` 參數。

如果這兩個模組都匯入相同的工作階段，且兩個模組都包含具有相同名稱的 Cmdlet，則最後匯入的 Cmdlet 便會在工作階段中生效。

## <a name="handling-command-name-conflicts"></a>處理命令名稱衝突

命令名稱衝突可能會在模組匯出的命令與使用者工作階段中的命令具有相同名稱時發生。

當工作階段包含兩個具有相同名稱的命令時，Windows PowerShell 會執行具優先順序的命令類型。 當工作階段包含兩個具有相同名稱與相同類型的命令時，Windows PowerShell 會執行最近新增到工作階段的命令。 若要執行預設不會執行的命令，使用者可以使用模組名稱來限定命令名稱。

例如，若某個工作階段包含 `Get-Date` 函式與 `Get-Date` Cmdlet，Windows PowerShell 預設會執行函式。 若要執行 Cmdlet，請在命令前面加上模組名稱，例如：

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

若要避免名稱衝突，模組作者可以在模組資訊清單中使用 **DefaultCommandPrefix** 機碼，來針對從模組匯出的所有命令指定名詞前置詞。

使用者可以使用 `Import-Module` Cmdlet 的 **Prefix** 參數來使用替代的前置詞。 **Prefix** 參數的值會優先於 **DefaultCommandPrefix** 機碼的值。

## <a name="see-also"></a>另請參閱

[about_Command_Precedence](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[撰寫 Windows PowerShell 模組](./writing-a-windows-powershell-module.md)
