---
title: 匯入 PowerShell 模組 |Microsoft Docs
ms.date: 02/03/2020
ms.openlocfilehash: 8cd1938d0a7b49b4a594753d8ce5ebe60625025d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784872"
---
# <a name="importing-a-powershell-module"></a>匯入 PowerShell 模組

在系統上安裝模組之後，您可能會想要匯入模組。 匯入是將模組載入使用中記憶體的程式，讓使用者可以在其 PowerShell 會話中存取該模組。 在 PowerShell 2.0 中，您可以使用[import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet 的呼叫匯入新安裝的 PowerShell 模組。 在 PowerShell 3.0 中，當使用者呼叫模組中的其中一個函式或 Cmdlet 時，PowerShell 可以隱含地匯入模組。 請注意，這兩個版本都假設您將模組安裝在 PowerShell 能夠找到它的位置;如需詳細資訊，請參閱[安裝 PowerShell 模組](./installing-a-powershell-module.md)。
您可以使用模組資訊清單來限制要匯出模組的哪些部分，而且您可以使用呼叫的參數 `Import-Module` 來限制要匯入的元件。

## <a name="importing-a-snap-in-powershell-10"></a>匯入嵌入式管理單元 (PowerShell 1.0) 

模組不存在於 PowerShell 1.0 中：相反地，您必須註冊並使用嵌入式管理單元。不過，我們不建議您在此時使用這項技術，因為模組通常較容易安裝和匯入。 如需詳細資訊，請參閱[如何建立 Windows PowerShell 嵌入式管理單元](../cmdlet/how-to-create-a-windows-powershell-snap-in.md)。

## <a name="importing-a-module-with-import-module-powershell-20"></a>使用 Import-module 匯入模組 (PowerShell 2.0) 

PowerShell 2.0 使用適當命名的[import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet 來匯入模組。 執行此 Cmdlet 時，Windows PowerShell 會在變數中指定的目錄內搜尋指定的模組 `PSModulePath` 。 找到指定的目錄時，Windows PowerShell 會依下列順序搜尋檔案：模組資訊清單檔案 ( .psd1) 、腳本模組檔案 (. .psm1) 、二進位模組檔案 (。 如需將目錄新增至搜尋的詳細資訊，請參閱[修改 PSModulePath 安裝路徑](./modifying-the-psmodulepath-installation-path.md)。
下列程式碼說明如何匯入模組：

```powershell
Import-Module myModule
```

假設 myModule 位於 `PSModulePath` ，則 PowerShell 會將 myModule 載入至使用中的記憶體。 如果 myModule 不在 `PSModulePath` 路徑上，您仍然可以明確告知 PowerShell 哪裡可以找到它：

```powershell
Import-Module -Name C:\myRandomDirectory\myModule -Verbose
```

您也可以使用 `-Verbose` 參數來識別要從模組匯出的內容，以及要匯入到使用中記憶體的內容。 匯出和匯入都會限制對使用者公開的內容：其差異在於控制可見度的物件。 基本上，匯出是由模組內的程式碼所控制。 相反地，匯入是由呼叫所控制 `Import-Module` 。 如需詳細資訊，請參閱下方的**限制匯入的成員**。

## <a name="implicitly-importing-a-module-powershell-30"></a>以隱含方式將模組匯入 (PowerShell 3.0) 

從 Windows PowerShell 3.0 開始，模組會在命令中使用模組中的任何 Cmdlet 或函數時自動匯入。 這項功能適用于目錄中的任何模組，其包含在**PSModulePath**環境變數的值中。 不過，如果您未將模組儲存在有效的路徑上，您仍然可以使用上述的明確匯[入模組](/powershell/module/Microsoft.PowerShell.Core/Import-Module)選項來載入它們。

下列動作會觸發自動匯入模組（也稱為「模組自動載入」）。

- 在命令中使用 Cmdlet。 例如，輸入 `Get-ExecutionPolicy` 會匯入包含 Cmdlet 的 Microsoft. PowerShell. Security 模組 `Get-ExecutionPolicy` 。

- 使用[get-command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) Cmdlet 來取得命令。 例如，輸入 `Get-Command Get-JobTrigger` 會匯入包含 Cmdlet 的**PSScheduledJob**模組 `Get-JobTrigger` 。 `Get-Command`包含萬用字元的命令會被視為探索，而且不會觸發模組的匯入。

- 使用[get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) Cmdlet 取得 Cmdlet 的說明。 例如，輸入 `Get-Help Get-WinEvent` 會匯入包含 Cmdlet 的 Microsoft. PowerShell 診斷模組 `Get-WinEvent` 。

為了支援自動匯入模組，此 `Get-Command` Cmdlet 會取得所有已安裝模組中的所有 Cmdlet 和函式，即使模組未匯入會話中也一樣。 如需詳細資訊，請參閱[Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) Cmdlet 的說明主題。

## <a name="the-importing-process"></a>匯入程式

匯入模組時，系統會為模組建立新的會話狀態，並在記憶體中建立[PSModuleInfo](/dotnet/api/System.Management.Automation.PSModuleInfo)物件。 會針對匯入的每個模組建立會話狀態 (這包括根模組和任何) 的嵌套模組。 從根模組匯出的成員（包括任何由任何嵌套模組匯出到根模組的成員），接著會匯入至呼叫者的會話狀態。

從模組匯出之成員的中繼資料具有 ModuleName 屬性。 這個屬性會以匯出它們的模組名稱填入。

> [!WARNING]
> 如果匯出成員的名稱使用未核准的動詞命令，或如果成員的名稱使用限制的字元，則會在執行[import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet 時顯示警告。

根據預設， [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet 不會將任何物件傳回至管線。 不過，此 Cmdlet 支援**PassThru**參數，可以用來針對每個匯入的模組傳回[PSModuleInfo](/dotnet/api/System.Management.Automation.PSModuleInfo)物件。 若要將輸出傳送至主機，使用者應該執行「[寫入主機](/powershell/module/Microsoft.PowerShell.Utility/Write-Host)」 Cmdlet。

## <a name="restricting--the-members-that-are-imported"></a>限制已匯入的成員

使用[import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet 匯入模組時，預設會將所有匯出的模組成員匯入到會話中，包括由嵌套模組匯出至模組的任何命令。 預設不會匯出變數和別名。 若要限制匯出的成員，請使用[模組資訊清單](./how-to-write-a-powershell-module-manifest.md)。
若要限制匯入的成員，請使用 Cmdlet 的下列參數 `Import-Module` 。

- **Function**：這個參數會限制匯出的函式。  (如果您使用模組資訊清單，請參閱 FunctionsToExport 鍵。 ) 

- `**Cmdlet**：如果您使用模組資訊清單，此參數會限制匯出 (的 Cmdlet，請參閱 CmdletsToExport 鍵。 ) 

- **變數**：如果您使用模組資訊清單，此參數會限制匯出 (的變數，請參閱 VariablesToExport 鍵。 ) 

- **Alias**：此參數會限制匯出的別名 (如果您使用模組資訊清單，請參閱 AliasesToExport 鍵。 ) 

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell 模組](./writing-a-windows-powershell-module.md)
