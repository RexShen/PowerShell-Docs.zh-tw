---
title: 了解 Windows PowerShell 模組 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d4e38235-9987-4347-afd2-0f7d1dc8f64a
caps.latest.revision: 19
ms.openlocfilehash: cff50d415c4c90182fa1cf015a5a5ba84d4d613a
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/03/2019
ms.locfileid: "66470783"
---
# <a name="understanding-a-windows-powershell-module"></a>了解 Windows PowerShell 模組

A*模組*是一組相關的 Windows PowerShell 功能，群組成種便利的單位 （通常儲存在單一目錄中）。 藉由為模組中定義一組相關的指令碼檔案、 組件和相關的資源，您可以參考、 載入、 保存和共用程式碼變得比您就。

模組的主要目的是允許的 Windows PowerShell 程式碼模組化 （亦即，重複使用和抽象概念）。 例如，建立模組的最基本的方式是只是儲存為.psm1 檔案的 Windows PowerShell 指令碼。 這麼做因此可讓您控制 （亦即，讓公用或私用） 的函式和指令碼中包含的變數。 將指令碼儲存為.psm1 檔案也可讓您控制特定變數的範圍。 最後，您也可以使用 cmdlet 這類[Install-module](/powershell/module/PowershellGet/Install-Module)來組織，安裝及使用您的指令碼當做建置組塊，較大的解決方案。

## <a name="module-components-and-types"></a>模組元件和類型

模組是四個基本元件組成：

1. 部分排序的程式碼檔-通常是 PowerShell 指令碼或的受管理的指令程式組件。

2. 任何上述的程式碼檔案可能需要例如其他組件，協助檔案或指令碼。

3. 資訊清單檔案，說明上述的檔案，以及儲存中繼資料，例如作者和版本設定資訊...

4. 目錄，包含所有上述內容，並且位於 PowerShell 可以合理地找到它。

   請注意，沒有任何這些元件，單獨，確實有必要。 例如，模組就技術上而言可以是.psm1 檔案中儲存的指令碼。 您也可以有資訊清單的檔案，主要是用於組織的目的只是一個模組。 您也可以撰寫指令碼，以動態方式建立模組，並因此實際上不需要可儲存任何項目中的目錄。 下列各節說明您可以透過混合並比對不同的模組可能部分一起取得的模組的類型。

### <a name="script-modules"></a>指令碼模組

如同名稱所暗示*指令碼模組*是包含任何有效的 Windows PowerShell 程式碼檔案 (.psm1)。 指令碼開發人員和管理員可以使用這種類型的模組來建立其成員包括函式、 變數等等的模組。 在核心中，指令碼模組是只具有不同的延伸模組，讓系統管理員在其上使用匯入、 匯出和管理功能的 Windows PowerShell 指令碼。

此外，您可以使用資訊清單檔，以在您的模組，例如資料檔案、 其他相依的模組或執行階段指令碼中包含其他資源。 資訊清單檔案也適合用於追蹤中繼資料，例如編寫及版本管理的資訊。

最後，指令碼模組，像任何其他模組不以動態方式建立，都必須儲存在 PowerShell 可以合理地探索的資料夾。 通常，這是 PowerShell 模組路徑中;不過，必要時您可以明確地描述您的模組已安裝。 如需詳細資訊，請參閱 <<c0> [ 如何撰寫 PowerShell 指令碼模組](./how-to-write-a-powershell-script-module.md)。

### <a name="binary-modules"></a>二進位模組

A*二進位模組*是.NET Framework 組件 (.dll)，包含已編譯的程式碼，例如C#。 Cmdlet 開發人員可以使用這種類型的模組，共用的 cmdlet、 提供者，和更多功能。 （現有的嵌入式管理單元也可用來當做二進位模組。）相較於指令碼模組，二進位模組可讓您建立更快，或使用功能的 cmdlet (例如多執行緒) 不是 Windows PowerShell 指令碼中的程式碼一樣簡單。

您可以使用指令碼模組，包含資訊清單檔案來描述您的模組所使用的其他資源，以及追蹤您的模組的相關中繼資料。 同樣地，您可能應該二進位模組在資料夾中安裝 PowerShell 模組路徑上的某處。 如需詳細資訊，請參閱如何[如何撰寫 PowerShell 二進位模組](./how-to-write-a-powershell-binary-module.md)。

### <a name="manifest-modules"></a>資訊清單模組

A*資訊清單模組*是在資訊清單檔案中描述的所有元件，但沒有任何類型的核心組件或指令碼的模組。 (正式地說，資訊清單模組離開`ModuleToProcess`或`RootModule`空的資訊清單的項目。)不過，您仍然可以使用模組，例如能夠載入相依組件，或自動執行某些前置處理指令碼的其他功能。 您也可以使用資訊清單模組做為封裝將使用的其他模組，例如巢狀的模組、 組件、 類型或格式的資源的便利方式。 如需詳細資訊，請參閱 <<c0> [ 如何撰寫 PowerShell 模組資訊清單](./how-to-write-a-powershell-module-manifest.md)。

### <a name="dynamic-modules"></a>動態模組

A*動態模組*是模組未載入，或儲存至檔案。 相反地，它們會以動態方式建立指令碼，使用[New-module](/powershell/module/Microsoft.PowerShell.Core/New-Module) cmdlet。 這種類型的模組可讓指令碼來建立模組上不需要載入或儲存至永續性儲存體的需求。 本質上，動態模組預期短期，並因此無法存取`Get-Module`cmdlet。 同樣地，它們通常不需要模組資訊清單中，使用者也不可能需要永久的資料夾來儲存其相關的組件。

## <a name="module-manifests"></a>模組資訊清單

A*模組資訊清單*是包含雜湊表的.psd1 檔案。 金鑰和雜湊表中的值執行下列動作：

- 描述的內容和屬性的模組。

- 定義必要條件。

- 決定元件的處理方式。

  資訊清單對於模組並非必要。 模組可以參考指令碼檔案 (.ps1)、 指令碼模組檔案 (.psm1) 資訊清單檔案 (.psd1) 格式和輸入檔案 (.ps1xml)、 cmdlet 和提供者的組件 (.dll)、 資源檔、 說明檔案、 當地語系化檔案或任何其他類型的檔案或資源，會打包成模組的一部分。 國際化的指令碼，[模組] 資料夾也包含一組訊息的類別目錄檔案。 如果您加入資訊清單檔案的模組資料夾時，可以參考了資訊清單，以參考為單一單位的多個檔案。

  資訊清單本身會說明下列類別的資訊：

- 模組，例如模組版本號碼、 作者和描述的相關中繼資料。

- 若要匯入模組，例如 Windows PowerShell 版本，common language runtime (CLR) 版本中，以及所需的模組所需的必要條件。

- 處理指示詞，例如指令碼、 格式和類型來處理。

- 限制在成員上要匯出的模組，例如別名、 函式、 變數和 cmdlet 來匯出。

  如需詳細資訊，請參閱 <<c0> [ 如何撰寫 PowerShell 模組資訊清單](./how-to-write-a-powershell-module-manifest.md)。

## <a name="storing-and-installing-a-module"></a>儲存並安裝模組

當您建立的指令碼、 二進位或資訊清單模組之後時，您可以將您的工作儲存的位置，其他人可以存取它。 比方說，您的模組可以儲存在其中已安裝 Windows PowerShell，或它可以儲存在使用者資料夾中的 [system] 資料夾中。

一般而言，您可以判斷您應該在其中安裝使用其中一個路徑儲存在您的模組`$ENV:PSModulePath`變數。 使用這些路徑表示 PowerShell 可以自動尋找並載入您的模組，當使用者在他們的程式碼中進行的呼叫。 如果您儲存在其他地方的模組，您可以明確地讓知道在您的模組位置，做為參數傳遞，當您呼叫 PowerShell `Install-Module`。

不論如何，資料夾的路徑指*基底*(ModuleBase)，此模組和指令碼的名稱，二進位或資訊清單模組檔案應與模組資料夾名稱相同，但有下列例外狀況：

- 所建立的動態模組`New-Module`cmdlet 可以用來命名`Name`cmdlet 的參數。

- 從組件物件匯入的模組 **`Import-Module` -組件**命令會命名為根據的下列語法： `"dynamic_code_module_" + assembly.GetName()`。

  如需詳細資訊，請參閱 <<c0> [ 安裝 PowerShell 模組](./installing-a-powershell-module.md)並[修改 PSModulePath 安裝路徑](./modifying-the-psmodulepath-installation-path.md)。

## <a name="module-cmdlets-and-variables"></a>模組 Cmdlet 和變數

下列的 cmdlet 和變數會提供 Windows PowerShell 來建立和管理的模組。

[新模組](/powershell/module/Microsoft.PowerShell.Core/New-Module)cmdlet 這個指令程式建立新的動態模組存在於只在記憶體中。 模組會建立從指令碼區塊，並匯出的成員，例如其函式和變數，可立即在工作階段中，並在關閉工作階段之前保持可用。

[新 ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet 此 cmdlet 會建立新的模組資訊清單 (.psd1) 檔案、 填入其值，並將資訊清單檔案儲存至指定的路徑。 此 cmdlet 也可用來建立模組資訊清單範本，可以手動填入。

[匯入模組](/powershell/module/Microsoft.PowerShell.Core/Import-Module)cmdlet 此 cmdlet 會將一或多個模組新增到目前的工作階段。

[取得模組](/powershell/module/Microsoft.PowerShell.Core/Get-Module)cmdlet 此 cmdlet 會擷取的模組，都已經或，可以匯入目前工作階段的相關資訊。

[Export-modulemember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) cmdlet 會指定從指令碼模組 (.psm1) 檔案或使用所建立的動態模組匯出的模組成員 （例如 cmdlet、 函式、 變數和別名） 這個指令程式`New-Module`cmdlet。

[Remove-module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) cmdlet 此 cmdlet 會移除目前工作階段中的模組。

[測試 ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest) cmdlet，此 cmdlet 會驗證模組資訊清單正確驗證會列在模組資訊清單檔案 (.psd1) 檔案實際存在於指定的路徑描述模組的元件。

$PSScriptRoot 此變數包含要從中執行指令碼模組的目錄。 它可讓指令碼使用的模組路徑來存取其他資源。

$env: PSModulePath 這個環境變數包含的模組會儲存在哪一個 Windows PowerShell 中的目錄清單。 Windows PowerShell 會使用自動匯入模組和更新模組的說明主題時，此變數的值。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell 模組](./writing-a-windows-powershell-module.md)
