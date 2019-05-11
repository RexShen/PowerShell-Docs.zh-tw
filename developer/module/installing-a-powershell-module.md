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
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229445"
---
# <a name="installing-a-powershell-module"></a>安裝 PowerShell 模組

您已建立您的 PowerShell 模組之後，您可能會想，在系統上，安裝模組，讓您或其他人可能會使用它。 一般而言，這包含複製的模組檔案 （亦即，.psm1，或二進位組件、 模組資訊清單和任何相關聯的檔案） 至目錄在該電腦上。 對於非常小的專案中，這可能是簡單，只要複製並貼上與 Windows 檔案總管檔案到單一遠端電腦;不過，較大的解決方案，您可能想要使用更複雜的安裝程序。 不論如何，您會取得您系統上的模組，PowerShell 可以使用一些技巧，讓使用者尋找並使用您的模組。 因此，安裝的主要問題確保 PowerShell 能夠找到您的模組。 如需詳細資訊，請參閱 <<c0> [ 匯入 PowerShell 模組](./importing-a-powershell-module.md)。

## <a name="rules-for-installing-modules"></a>安裝模組的規則

下列資訊與所有模組，包括您建立您自己使用，您從其他合作對象，取得的模組和模組散發給其他人的模組。

### <a name="install-modules-in-psmodulepath"></a>在 PSModulePath 中安裝模組

可能的話，則安裝所有模組中所列路徑中**PSModulePath**環境變數或新增的模組路徑**PSModulePath**環境變數的值。

**PSModulePath**環境變數 ($Env: PSModulePath) 包含 Windows PowerShell 模組的位置。 指令程式會依賴此環境變數的值來尋找模組。

根據預設， **PSModulePath**環境變數的值包含下列的系統和使用者的模組目錄，但您可以加入和編輯值。

- `$PSHome\Modules` (%Windir%\System32\WindowsPowerShell\v1.0\Modules)

  > [!WARNING]
  > 此位置會保留給 Windows 隨附的模組。 請勿將模組安裝到這個位置。

- `$Home\Documents\WindowsPowerShell\Modules` （%userprofile%\documents\windowspowershell\modules)

- `$Env:ProgramFiles\WindowsPowerShell\Modules` (%ProgramFiles%\WindowsPowerShell\Modules)

  若要取得的值**PSModulePath**環境變數，使用下列命令。

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  若要加入的值中的模組路徑**PSModulePath**環境變數值，請使用下列命令格式。 此格式會使用**SetEnvironmentVariable**方法**System.Environment**類別，以獨立於工作階段的變更**PSModulePath**環境變數。

  ```powershell
  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > 一旦您加入的路徑**PSModulePath**，您應該廣播與變更相關的環境訊息。 廣播變更可讓其他應用程式，例如殼層，來取得變更。 若要廣播變更，已傳送您產品的安裝程式碼**WM_SETTINGCHANGE**訊息，其`lParam`設為 「 環境 」 的字串。 傳送訊息之後已更新您的模組安裝程式碼，請務必**PSModulePath**。

### <a name="use-the-correct-module-directory-name"></a>使用正確的模組目錄名稱

語式正確的模組是儲存在具有至少一個檔案，在模組目錄中的基底名稱與同名的目錄中的模組。 如果模組不是語式正確的 Windows PowerShell 無法辨識其為模組。

檔案的 「 基底名稱 」 是不含副檔名的名稱。 語式正確的模組中包含的模組檔案的目錄名稱必須符合模組中至少一個檔案的基底名稱。

比方說，在 Fabrikam 模組範例包含的模組檔案的目錄名為"Fabrikam"，至少一個檔案的"Fabrikam"基底名稱。 在此情況下，Fabrikam.psd1 和 Fabrikam.dll 有"Fabrikam"基底名稱。

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

### <a name="effect-of-incorrect-installation"></a>安裝錯誤的影響

如果模組不是語式正確，而且它的位置不會納入的值**PSModulePath**環境變數，如下所示，Windows PowerShell 中，基本的探索功能無法運作。

- 模組自動載入功能無法自動匯入模組。

- `ListAvailable`的參數[Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet 找不到模組。

- [Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet 找不到模組。 若要匯入模組，您必須提供根模組檔案或模組資訊清單檔案的完整路徑。

  其他功能，例如下列程式碼，將無法運作除非模組匯入工作階段。 語式正確的模組中**PSModulePath**環境變數，這些功能運作，即使模組不會匯入工作階段。

- [Get-command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet 模組中找不到命令。

- [Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)並[Save-help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet 無法更新或儲存模組的說明。

- [Show-command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet 無法尋找並顯示在模組中的命令。

  模組中的命令中遺漏的`Show-Command`視窗在 Windows PowerShell 整合式指令碼環境 (ISE)。

## <a name="where-to-install-modules"></a>如何安裝模組

本節說明在何處安裝 Windows PowerShell 模組的檔案系統中。 位置取決於如何使用模組。

### <a name="installing-modules-for-a-specific-user"></a>適用於特定使用者安裝的模組

如果您建立您自己的模組，或從另一個合作對象，例如 Windows PowerShell 社群網站，取得模組，您想要的模組，可供您的使用者帳戶只能安裝模組，在使用者專屬的 Modules 目錄中。

`$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

使用者專屬 Modules 目錄加入至值**PSModulePath**預設的環境變數。

### <a name="installing-modules-for-all-users-in-program-files"></a>安裝程式檔案中的所有使用者的模組

如果您想要可供電腦上的所有使用者帳戶的模組，請在程式檔案的位置安裝模組。

`$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

> [!NOTE]
> 程式檔案的位置加入 PSModulePath 環境變數的值，根據預設，在 Windows PowerShell 4.0 和更新版本。 對於舊版的 Windows PowerShell 中，可以手動建立的程式檔案位置 ((%ProgramFiles%\WindowsPowerShell\Modules) 並將此路徑新增至 PSModulePath 環境變數，如上面所述。

### <a name="installing-modules-in-a-product-directory"></a>產品目錄中安裝模組

在散發給其他對象的模組時，如果使用上面所述的預設程式檔案位置，或建立您自己公司專屬或產品特定子目錄的 %programfiles%目錄。

例如，Fabrikam 技術，這家虛構公司的會出貨 Fabrikam Manager 產品的 Windows PowerShell 模組。 其模組安裝程式會建立模組子目錄，Fabrikam Manager 產品子目錄中。

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

若要啟用 Windows PowerShell 模組探索功能，若要尋找 Fabrikam 模組，Fabrikam 模組安裝程式會將模組位置的值**PSModulePath**環境變數。

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam Technologies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a>在 [Common Files] 目錄中安裝模組

如果模組使用由多個元件的產品或產品的多個版本，請 %ProgramFiles%\Common Files\Modules 子目錄的特定模組的子目錄中安裝模組。

在下列範例中，「 Fabrikam 」 安裝模組的 Fabrikam 子目錄中`%ProgramFiles%\Common Files\Modules`子目錄。 請注意每個模組都位於自己的模組子目錄中的子目錄。

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)
```

然後，安裝程式可確保 windows 7 **PSModulePath**環境變數包含一般的檔案模組子目錄的路徑。

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

若要安裝之相同模組的多個版本，請使用下列程序。

1. 建立每個版本的模組目錄。 目錄名稱中包含的版本號碼。
2. 建立模組的每個版本的模組資訊清單。 中的值**ModuleVersion**金鑰資訊清單中，請輸入模組的版本號碼。 模組的版本特定目錄中儲存資訊清單檔案 (.psd1)。
3. 將模組的根資料夾路徑新增至 windows 7 **PSModulePath**環境變數，如下列範例所示。

若要匯入特定版本的模組，使用者可以使用`MinimumVersion`或是`RequiredVersion`的參數[Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet。

例如，Fabrikam 模組是否可在 8.0 及 9.0 版本中，Fabrikam 的模組目錄結構可能會如下所示。

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

安裝程式將這兩個模組路徑**PSModulePath**環境變數的值。

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

完成這些步驟時**ListAvailable**的參數[Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet 會取得這兩個 Fabrikam 模組。 若要匯入特定模組，請使用`MinimumVersion`或是`RequiredVersion`的參數[Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet。

如果這兩個模組匯入相同的工作階段中，模組會包含具有相同名稱的 cmdlet，最後匯入的 cmdlet 會在工作階段中有效。

## <a name="handling-command-name-conflicts"></a>處理命令名稱衝突

模組匯出的命令會在使用者工作階段中的命令相同的名稱，就會發生命令名稱衝突。

當工作階段包含兩個具有相同名稱的命令時，Windows PowerShell 會執行會優先使用的命令類型。 當工作階段包含兩個具有相同名稱和相同類型的命令時，Windows PowerShell 就會執行已加入至最近的工作階段的命令。 若要執行的命令，預設不會執行，使用者可以限定命令名稱的模組名稱。

例如，如果工作階段包含`Get-Date`函式和`Get-Date`cmdlet，Windows PowerShell 預設會執行函式。 若要執行此 cmdlet，命令前面加上模組名稱，例如：

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

若要避免名稱衝突，可以使用模組作者**DefaultCommandPrefix**從模組匯出的模組資訊清單來指定所有命令的名詞前置詞中的索引鍵。

使用者可以使用**前置詞**參數`Import-Module`cmdlet 以使用替代的前置詞。 值**前置詞**參數的值會優先**DefaultCommandPrefix**索引鍵。

## <a name="see-also"></a>另請參閱

[about_Command_Precedence](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[撰寫 Windows PowerShell 模組](./writing-a-windows-powershell-module.md)
