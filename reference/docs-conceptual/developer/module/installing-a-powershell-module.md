---
title: 安裝 PowerShell 模組 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb82827e-fdb7-4cbf-b3d4-093e72b3ff0e
caps.latest.revision: 28
ms.openlocfilehash: 60ac4bf9089232a9fa879e835e32da53422489fd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367067"
---
# <a name="installing-a-powershell-module"></a>安裝 PowerShell 模組

建立 PowerShell 模組之後，您可能會想要在系統上安裝模組，讓您或其他人可以使用它。 一般來說，這是由將模組檔案（即 .psm1 或二進位元件、模組資訊清單，以及任何其他相關聯的檔案）複製到該電腦上的目錄。 對於非常小型的專案，這可能就像是將檔案以 Windows Explorer 複製並貼到單一遠端電腦一樣簡單;不過，對於較大型的解決方案，您可能會想要使用更複雜的安裝程式。 無論您如何將模組放入系統，PowerShell 都可以使用一些技術，讓使用者尋找和使用您的模組。 因此，安裝的主要問題是確保 PowerShell 能夠找到您的模組。 如需詳細資訊，請參閱匯[入 PowerShell 模組](./importing-a-powershell-module.md)。

## <a name="rules-for-installing-modules"></a>安裝模組的規則

下列資訊適用于所有模組，包括您為自己的用途所建立的模組、從其他方取得的模組，以及您散發給其他人的模組。

### <a name="install-modules-in-psmodulepath"></a>在 PSModulePath 中安裝模組

盡可能將所有模組安裝在**PSModulePath**環境變數中所列的路徑，或將模組路徑新增至**PSModulePath**環境變數值。

**PSModulePath**環境變數（$Env:P smodulepath）包含 Windows PowerShell 模組的位置。 Cmdlet 會依賴此環境變數的值來尋找模組。

根據預設， **PSModulePath**環境變數值包含下列系統和使用者模組目錄，但是您可以加入並編輯值。

- `$PSHome\Modules` （%Windir%\System32\WindowsPowerShell\v1.0\Modules）

  > [!WARNING]
  > 這個位置會保留給 Windows 隨附的模組。 請勿將模組安裝到這個位置。

- `$Home\Documents\WindowsPowerShell\Modules` （%UserProfile%\Documents\WindowsPowerShell\Modules）

- `$Env:ProgramFiles\WindowsPowerShell\Modules` （%ProgramFiles%\WindowsPowerShell\Modules）

  若要取得**PSModulePath**環境變數的值，請使用下列其中一個命令。

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  若要將模組路徑新增至**PSModulePath**環境變數值的值，請使用下列命令格式。 此格式會使用**system.object**類別的**SetEnvironmentVariable**方法，對**PSModulePath**環境變數進行與會話無關的變更。

  ```powershell
  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > 將路徑新增至**PSModulePath**之後，您應該廣播有關此變更的環境訊息。 廣播變更可讓其他應用程式（例如 shell）收取變更。 若要廣播變更，請讓您的產品安裝程式碼傳送**WM_SETTINGCHANGE**訊息，並將 `lParam` 設定為字串 "環境"。 在您的模組安裝程式碼更新**PSModulePath**之後，請務必傳送該訊息。

### <a name="use-the-correct-module-directory-name"></a>使用正確的模組目錄名稱

格式正確的模組是儲存在目錄中的模組，其名稱與模組目錄中至少一個檔案的基底名稱相同。 如果模組的格式不正確，Windows PowerShell 就無法將它辨識為模組。

檔案的「基底名稱」是沒有副檔名的名稱。 在格式正確的模組中，包含模組檔案的目錄名稱必須符合模組中至少一個檔案的基底名稱。

例如，在範例 Fabrikam 模組中，包含模組檔案的目錄會命名為 "Fabrikam"，而且至少有一個檔案包含 "Fabrikam" 基底名稱。 在此情況下，.psd1 和 Fabrikam 都會有 "Fabrikam" 基底名稱。

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

### <a name="effect-of-incorrect-installation"></a>安裝不正確的效果

如果模組的格式不正確，且其位置並未包含在**PSModulePath**環境變數的值中，則 Windows PowerShell 的基本探索功能（如下列）將無法運作。

- 模組自動載入功能無法自動匯入模組。

- [取得模組](/powershell/module/Microsoft.PowerShell.Core/Get-Module)Cmdlet 的 `ListAvailable` 參數找不到模組。

- [Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet 找不到模組。 若要匯入模組，您必須提供根模組檔案或模組資訊清單檔案的完整路徑。

  除非將模組匯入會話，否則其他功能（例如下列）無法正常執行。 在**PSModulePath**環境變數中格式正確的模組中，即使模組未匯入會話，這些功能仍可運作。

- [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) Cmdlet 在模組中找不到命令。

- [Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)和[Save-help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) Cmdlet 無法更新或儲存模組的說明。

- [顯示命令](/powershell/module/Microsoft.PowerShell.Utility/Show-Command)Cmdlet 找不到並顯示模組中的命令。

  Windows PowerShell 整合式腳本環境（ISE）中的 `Show-Command` 視窗遺失模組中的命令。

## <a name="where-to-install-modules"></a>模組的安裝位置

本節說明檔案系統中安裝 Windows PowerShell 模組的位置。 位置取決於模組的使用方式。

### <a name="installing-modules-for-a-specific-user"></a>為特定使用者安裝模組

如果您建立自己的模組，或從另一方取得模組，例如 Windows PowerShell 社區網站，而且您想要讓模組僅供您的使用者帳戶使用，請在您的使用者特定模組目錄中安裝模組。

`$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

根據預設，會將使用者特定的模組目錄新增至**PSModulePath**環境變數的值。

### <a name="installing-modules-for-all-users-in-program-files"></a>針對 Program Files 中的所有使用者安裝模組

如果您想要將模組提供給電腦上的所有使用者帳戶，請將模組安裝在 Program Files 位置。

`$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

> [!NOTE]
> 在 Windows PowerShell 4.0 和更新版本中，預設會將 Program Files 位置新增至 PSModulePath 環境變數的值。 對於舊版的 Windows PowerShell，您可以手動建立程式檔案位置（（%ProgramFiles%\WindowsPowerShell\Modules），並將此路徑新增至您的 PSModulePath 環境變數，如上所述。

### <a name="installing-modules-in-a-product-directory"></a>在產品目錄中安裝模組

如果您要將課程模組散發給其他人，請使用上述的預設程式檔案位置，或建立您自己的公司專屬或產品特定的% ProgramFiles% 目錄子目錄。

例如，Fabrikam 技術是一家虛構的公司，它會為其 Fabrikam Manager 產品運送 Windows PowerShell 模組。 其模組安裝程式會在 Fabrikam Manager 產品子目錄中建立模組子目錄。

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

若要啟用 Windows PowerShell 模組探索功能以尋找 Fabrikam 模組，Fabrikam 模組安裝程式會將模組位置新增至**PSModulePath**環境變數的值。

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam Technologies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a>在通用檔案目錄中安裝模組

如果產品的多個元件或產品的多個版本使用模組，請在%ProgramFiles%\Common Files\Modules 子目錄的模組特定子目錄中安裝模組。

在下列範例中，Fabrikam 模組會安裝在 `%ProgramFiles%\Common Files\Modules` 子目錄的 Fabrikam 子目錄中。 請注意，每個模組都位於模組子目錄中自己的子目錄中。

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)
```

然後，安裝程式會確保**PSModulePath**環境變數的值包含 common files 模組子目錄的路徑。

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

## <a name="installing-multiple-versions-of-a-module"></a>安裝多個版本的模組

若要安裝相同模組的多個版本，請使用下列程式。

1. 為每個模組版本建立一個目錄。 在目錄名稱中包含版本號碼。
2. 為模組的每個版本建立模組資訊清單。 在資訊清單中**ModuleVersion**索引鍵的值，輸入模組版本號碼。 將資訊清單檔案（. .psd1）儲存在模組的版本特定目錄中。
3. 將模組根資料夾路徑新增至**PSModulePath**環境變數的值，如下列範例所示。

若要匯入特定版本的模組，終端使用者可以使用[import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet 的 `MinimumVersion` 或 `RequiredVersion` 參數。

例如，如果在8.0 和9.0 版中提供 Fabrikam 模組，Fabrikam 模組目錄結構可能如下所示。

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

安裝程式會將這兩個模組路徑新增至**PSModulePath**環境變數值。

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

當這些步驟完成時， [get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Module) Cmdlet 的**ListAvailable**參數會取得這兩個 Fabrikam 模組。 若要匯入特定模組，請使用[import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet 的 `MinimumVersion` 或 `RequiredVersion` 參數。

如果這兩個模組都匯入相同的會話中，而且模組包含具有相同名稱的 Cmdlet，則最後匯入的 Cmdlet 就會在會話中生效。

## <a name="handling-command-name-conflicts"></a>處理命令名稱衝突

當模組匯出的命令與使用者會話中的命令同名時，可能會發生命令名稱衝突。

當會話包含兩個具有相同名稱的命令時，Windows PowerShell 會執行優先的命令類型。 當會話包含兩個具有相同名稱和相同類型的命令時，Windows PowerShell 會執行最近新增至會話的命令。 若要執行預設不會執行的命令，使用者可以使用模組名稱來限定命令名稱。

例如，如果會話包含 `Get-Date` 函式和 `Get-Date` Cmdlet，Windows PowerShell 預設會執行此功能。 若要執行此 Cmdlet，請在命令前面加上模組名稱，例如：

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

為避免名稱衝突，模組作者可以使用模組資訊清單中的**DefaultCommandPrefix**索引鍵，為從模組匯出的所有命令指定名詞前置詞。

使用者可以使用 `Import-Module` Cmdlet 的**prefix**參數來使用替代的前置詞。 **Prefix**參數的值會優先于**DefaultCommandPrefix**索引鍵的值。

## <a name="see-also"></a>另請參閱

[about_Command_Precedence](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[撰寫 Windows PowerShell 模組](./writing-a-windows-powershell-module.md)
