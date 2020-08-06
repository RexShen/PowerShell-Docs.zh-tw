---
title: 瞭解 Windows PowerShell 模組 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 9308ad0fd41aa67ffa8510ae7a3c9cd6a13f4220
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779228"
---
# <a name="understanding-a-windows-powershell-module"></a>了解 Windows PowerShell 模組

*模組*是一組相關的 Windows PowerShell 功能，群組在一起成為方便的單元， (通常會儲存在單一目錄) 中。 藉由定義一組相關的腳本檔案、元件和相關資源做為模組，您可以更輕鬆地參考、載入、保存和共用程式碼。

模組的主要用途是允許模組化 (ie、重複使用和抽象) Windows PowerShell 程式碼。 例如，建立模組的最基本方式，就是將 Windows PowerShell 腳本儲存為 .psm1 檔案。 這麼做可讓您控制 (ie、讓公用或私用) 包含在腳本中的函式和變數。 將腳本儲存為 .psm1 檔案也可讓您控制特定變數的範圍。 最後，您也可以使用指令程式（如[Install 模組](/powershell/module/PowershellGet/Install-Module)）來組織、安裝和使用您的腳本作為較大型解決方案的建立區塊。

## <a name="module-components-and-types"></a>模組元件和類型

模組是由四個基本元件所組成：

1. 某些程式碼檔案-通常是 PowerShell 腳本或受管理的 Cmdlet 元件。

2. 上述程式碼檔案可能需要的任何其他專案，例如其他元件、說明檔或腳本。

3. 描述上述檔案的資訊清單檔，以及儲存中繼資料，例如作者和版本設定資訊。

4. 目錄，其中包含上述所有內容，且位於 PowerShell 可合理尋找的位置。

   請注意，這些元件本身都不是必要的。 例如，模組在技術上可能只是儲存在 .psm1 檔案中的腳本。 您也可以有一個不是資訊清單檔案的模組，主要用於組織用途。 您也可以撰寫可動態建立模組的腳本，因此實際上不需要目錄來儲存任何專案。 下列各節將說明您可以藉由混合和比對模組的不同可能元件來取得的模組類型。

### <a name="script-modules"></a>指令碼模組

如其名所示，*腳本模組* ( 是包含任何有效 Windows PowerShell 程式碼的 .psm1) 檔案。 腳本開發人員和系統管理員可以使用這種類型的模組來建立其成員包含函式、變數等的模組。 就核心而言，腳本模組只是具有不同副檔名的 Windows PowerShell 腳本，可讓系統管理員在其上使用匯入、匯出和管理功能。

此外，您可以使用資訊清單檔案，在模組中包含其他資源，例如資料檔案、其他相依模組或執行時間腳本。 資訊清單檔案也適用于追蹤中繼資料，例如撰寫和版本設定資訊。

最後，您必須將腳本模組儲存在 PowerShell 可合理探索的資料夾中，就像任何其他未動態建立的模組一樣。 通常，這是在 PowerShell 模組路徑上;但如有需要，您可以明確描述模組的安裝位置。 如需詳細資訊，請參閱[如何撰寫 PowerShell 腳本模組](./how-to-write-a-powershell-script-module.md)。

### <a name="binary-modules"></a>二進位模組

*二進位模組*是包含已編譯器代碼（例如 c #）的 .NET Framework 元件 ( .dll) 。 Cmdlet 開發人員可以使用這種類型的模組來共用 Cmdlet、提供者等。  (現有的嵌入式管理單元也可以當做二進位模組使用。 ) 相較于腳本模組，二進位模組可讓您建立更快速或使用功能的 Cmdlet (例如多執行緒) ，而不容易在 Windows PowerShell 腳本中撰寫程式碼。

如同腳本模組，您可以包含資訊清單檔案來描述模組所使用的其他資源，以及追蹤模組的相關中繼資料。 同樣地，您可能會在 PowerShell 模組路徑的某處資料夾中安裝您的二進位模組。 如需詳細資訊，請參閱如何[撰寫 PowerShell 二進位模組](./how-to-write-a-powershell-binary-module.md)。

### <a name="manifest-modules"></a>資訊清單模組

*資訊清單模組*是使用資訊清單檔來描述其所有元件的模組，但不會有任何類型的核心元件或腳本。  (正式地說，資訊清單模組 `ModuleToProcess` `RootModule` 會將資訊清單的或元素保留空白 ) 。不過，您仍然可以使用模組的其他功能，例如載入相依元件或自動執行特定前置處理腳本的能力。 您也可以使用資訊清單模組，將其他模組將使用的資源（例如，嵌套模組、元件、類型或格式）封裝成方便的方式。 如需詳細資訊，請參閱[如何撰寫 PowerShell 模組資訊清單](./how-to-write-a-powershell-module-manifest.md)。

### <a name="dynamic-modules"></a>動態模組

*動態模組*是指未從檔案載入或儲存到檔案的模組。 相反地，它們是由腳本以[新的模組](/powershell/module/Microsoft.PowerShell.Core/New-Module)Cmdlet 來動態建立的。 這種類型的模組可讓腳本建立不需要載入或儲存至持續性儲存體的隨選模組。 就本質而言，動態模組的目的是短期，因此 Cmdlet 無法存取 `Get-Module` 。 同樣地，它們通常不需要模組資訊清單，也可能需要永久資料夾來儲存其相關的元件。

## <a name="module-manifests"></a>模組資訊清單

*模組資訊清單*是包含雜湊表的 .psd1 檔案。 雜湊表中的索引鍵和值會執行下列動作：

- 描述模組的內容和屬性。

- 定義必要條件。

- 決定元件的處理方式。

  資訊清單對於模組並非必要。 模組可以參考腳本檔案 (. ps1) 、腳本模組檔案 (. .psm1) 、資訊清單檔 (. .psd1) 、格式和類型檔案 (. types.ps1xml) 、Cmdlet 和提供者元件 ( .dll) 、資源檔、說明檔案、當地語系化檔案，或任何其他類型的檔或資源（隨附于模組中）。 針對國際化腳本，模組資料夾也包含一組訊息目錄檔案。 如果您將資訊清單檔案新增至模組資料夾，您可以藉由參考資訊清單，將多個檔案當做單一單位來參考。

  資訊清單本身會描述下列類別的資訊：

- 模組的相關中繼資料，例如模組版本號碼、作者和描述。

- 匯入模組所需的必要條件，例如 Windows PowerShell 版本、common language runtime (CLR) 版本和必要的模組。

- 處理指示詞，例如要處理的腳本、格式和類型。

- 要匯出之模組的成員限制，例如要匯出的別名、函式、變數和 Cmdlet。

  如需詳細資訊，請參閱[如何撰寫 PowerShell 模組資訊清單](./how-to-write-a-powershell-module-manifest.md)。

## <a name="storing-and-installing-a-module"></a>儲存和安裝模組

建立腳本、二進位或資訊清單模組之後，您可以將工作儲存在其他人可以存取的位置。 例如，您的模組可以儲存在安裝 Windows PowerShell 的系統資料夾中，也可以儲存在使用者資料夾中。

一般來說，您可以使用儲存在變數中的其中一個路徑，判斷您應該在何處安裝模組 `$ENV:PSModulePath` 。 使用其中一個路徑，表示當使用者在其程式碼中呼叫它時，PowerShell 可以自動尋找並載入您的模組。 如果您將模組儲存在其他位置，您可以在呼叫時，將模組的位置傳入作為參數，以明確地讓 PowerShell 知道 `Install-Module` 。

無論如何，資料夾的路徑稱為模組的*基底* (ModuleBase) ，而腳本、二進位或資訊清單模組檔案的名稱應該與模組資料夾名稱相同，但有下列例外狀況：

- Cmdlet 所建立的動態模組 `New-Module` 可以使用 Cmdlet 的參數來命名 `Name` 。

- 由** `Import-Module` -assembly**命令從元件物件匯入的模組會根據下列語法來命名： `"dynamic_code_module_" + assembly.GetName()` 。

  如需詳細資訊，請參閱[安裝 PowerShell 模組](./installing-a-powershell-module.md)和[修改 PSModulePath 安裝路徑](./modifying-the-psmodulepath-installation-path.md)。

## <a name="module-cmdlets-and-variables"></a>模組 Cmdlet 和變數

Windows PowerShell 會提供下列 Cmdlet 和變數，以建立和管理模組。

[新模組](/powershell/module/Microsoft.PowerShell.Core/New-Module)Cmdlet 此 Cmdlet 會建立只存在於記憶體中的新動態模組。 模組是從腳本區塊所建立，而其匯出的成員（例如其函式和變數）會立即在會話中提供，直到會話關閉為止。

[New-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) Cmdlet：此 Cmdlet 會建立新的模組資訊清單， (. .psd1) 檔案、填入其值，並將資訊清單檔案儲存至指定的路徑。 此 Cmdlet 也可以用來建立可手動填入的模組資訊清單範本。

[Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet 這個 Cmdlet 會將一或多個模組新增至目前的會話。

[Get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Module) Cmdlet 此 Cmdlet 會抓取已或可匯入目前會話之模組的相關資訊。

[Export-modulemember 指令程式：](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember)此 Cmdlet 會指定模組成員 (例如 Cmdlet、函式、變數和別名) 從腳本模組匯出 (. .psm1) 檔案，或從使用 Cmdlet 所建立的動態模組。 `New-Module`

[Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) Cmdlet 此 Cmdlet 會從目前的會話移除模組。

[New-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest) Cmdlet 此 Cmdlet 會驗證模組資訊清單是否已正確描述模組的元件，方法是確認模組資訊清單檔案中所列出的檔案 (. .psd1) 確實存在於指定的路徑中。

$PSScriptRoot 此變數包含執行腳本模組的目錄。 它可讓腳本使用模組路徑來存取其他資源。

$env:P SModulePath 此環境變數包含用來儲存 Windows PowerShell 模組的目錄清單。 當自動匯入模組並更新模組的說明主題時，Windows PowerShell 會使用此變數的值。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell 模組](./writing-a-windows-powershell-module.md)
