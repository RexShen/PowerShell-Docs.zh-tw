---
ms.date: 02/03/2020
ms.topic: reference
title: 匯入 PowerShell 模組
description: 匯入 PowerShell 模組
ms.openlocfilehash: 688509c0943a9a0289e75b80543f278e16cfedfe
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92658783"
---
# <a name="importing-a-powershell-module"></a>匯入 PowerShell 模組

當您在系統上安裝模組之後，您可能會想要匯入模組。 匯入是將模組載入至使用中記憶體的程式，讓使用者可以在其 PowerShell 會話中存取該模組。 在 PowerShell 2.0 中，您可以透過呼叫 [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet 匯入剛安裝的 powershell 模組。 在 PowerShell 3.0 中，當使用者呼叫模組中的其中一個函式或 Cmdlet 時，PowerShell 可以隱含地匯入模組。 請注意，這兩個版本都假設您將模組安裝在 PowerShell 可找到它的位置。如需詳細資訊，請參閱 [安裝 PowerShell 模組](./installing-a-powershell-module.md)。
您可以使用模組資訊清單來限制模組匯出的部分，也可以使用呼叫的參數 `Import-Module` 來限制匯入的部分。

## <a name="importing-a-snap-in-powershell-10"></a>匯入 Snap-In (PowerShell 1.0) 

模組不存在於 PowerShell 1.0 中：您必須改為註冊並使用嵌入式管理單元。不過，我們不建議您在此時使用這項技術，因為模組通常更容易安裝和匯入。 如需詳細資訊，請參閱 [如何建立 Windows PowerShell 嵌入式管理單元](../cmdlet/how-to-create-a-windows-powershell-snap-in.md)。

## <a name="importing-a-module-with-import-module-powershell-20"></a>匯入具有 Import-Module (PowerShell 2.0) 的模組

PowerShell 2.0 使用已適當命名的 [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet 來匯入模組。 當執行此 Cmdlet 時，Windows PowerShell 會在變數中指定的目錄內搜尋指定的模組 `PSModulePath` 。 找到指定的目錄時，Windows PowerShell 會依下列順序搜尋檔案： ( 的模組資訊清單檔。 .psd1) 、腳本模組檔案 (. .psm1) 、二進位模組檔案 ( .dll) 。 如需有關將目錄新增至搜尋的詳細資訊，請參閱 [修改 PSModulePath 安裝路徑](./modifying-the-psmodulepath-installation-path.md)。
下列程式碼說明如何匯入模組：

```powershell
Import-Module myModule
```

假設 myModule 是位於中，則 `PSModulePath` PowerShell 會將 myModule 載入至使用中的記憶體。 如果 myModule 不在 `PSModulePath` 路徑上，您仍然可以明確地告訴 PowerShell 要在哪裡找到它：

```powershell
Import-Module -Name C:\myRandomDirectory\myModule -Verbose
```

您也可以使用 `-Verbose` 參數來識別從模組中匯出的內容，以及要匯入至使用中記憶體的內容。 匯出和匯入會限制對使用者公開的內容：差異在於控制可見度的物件。 基本上，匯出是由模組內的程式碼所控制。 相反地，匯入是由 `Import-Module` 呼叫控制。 如需詳細資訊，請參閱下方的 **限制匯入的成員**。

## <a name="implicitly-importing-a-module-powershell-30"></a>以隱含方式將模組匯入 (PowerShell 3.0) 

從 Windows PowerShell 3.0 開始，模組會在命令中使用模組中的任何 Cmdlet 或函數時自動匯入。 這項功能適用于目錄中的任何模組，其包含在 **PSModulePath** 環境變數的值中。 但是，如果您沒有將模組儲存在有效的路徑上，仍然可以使用上述的明確 [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) 選項來載入模組。

下列動作會觸發自動匯入模組，也稱為「模組自動載入」。

- 在命令中使用 Cmdlet。 例如，輸入 `Get-ExecutionPolicy` 會匯入包含 Cmdlet 的 Microsoft. Security 模組。 `Get-ExecutionPolicy`

- 使用 [Get 命令](/powershell/module/Microsoft.PowerShell.Core/Get-Command) Cmdlet 來取得命令。 例如，輸入 `Get-Command Get-JobTrigger` 會匯入包含 Cmdlet 的 **PSScheduledJob** 模組 `Get-JobTrigger` 。 `Get-Command`包含萬用字元的命令會被視為探索，且不會觸發模組的匯入。

- 使用 [get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) Cmdlet 取得 Cmdlet 的說明。 例如，輸入 `Get-Help Get-WinEvent` 會匯入包含 Cmdlet 的 Microsoft. Diagnostics 模組。 `Get-WinEvent`

為了支援自動匯入模組， `Get-Command` Cmdlet 會取得所有已安裝模組中的所有 Cmdlet 和函式，即使模組未匯入會話中也一樣。 如需詳細資訊，請參閱 [取得命令](/powershell/module/Microsoft.PowerShell.Core/Get-Command) Cmdlet 的說明主題。

## <a name="the-importing-process"></a>匯入流程

匯入模組時，系統會為模組建立新的會話狀態，並在記憶體中建立 [PSModuleInfo](/dotnet/api/System.Management.Automation.PSModuleInfo) 物件。 針對匯入的每個模組建立會話狀態 (這包括根模組和任何) 的嵌套模組。 從根模組匯出的成員（包括任何由任何嵌套模組匯出到根模組的成員）接著會匯入到呼叫者的會話狀態。

從模組匯出之成員的中繼資料具有 ModuleName 屬性。 這個屬性會填入匯出它們的模組名稱。

> [!WARNING]
> 如果匯出成員的名稱使用未核准的動詞，或如果成員名稱使用受限制的字元，則會在執行 [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet 時顯示警告。

根據預設， [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet 不會將任何物件傳回至管線。 不過，此 Cmdlet 支援 **PassThru** 參數，可用來傳回所匯入之每個模組的 [PSModuleInfo](/dotnet/api/System.Management.Automation.PSModuleInfo) 物件。 若要將輸出傳送至主機，使用者應該執行 [寫入主機](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) Cmdlet。

## <a name="restricting--the-members-that-are-imported"></a>限制匯入的成員

使用 [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet 匯入模組時，根據預設，所有匯出的模組成員都會匯入到會話中，包括由嵌套模組匯出至模組的任何命令。 依預設，不會匯出變數和別名。 若要限制匯出的成員，請使用 [模組資訊清單](./how-to-write-a-powershell-module-manifest.md)。
若要限制匯入的成員，請使用 Cmdlet 的下列參數 `Import-Module` 。

- **Function**：這個參數會限制匯出的函式。  (如果您使用模組資訊清單，請參閱 FunctionsToExport 機碼。 ) 

- `**Cmdlet**：此參數會限制匯出的 Cmdlet (如果您使用模組資訊清單，請參閱 CmdletsToExport 機碼。 ) 

- **變數**：此參數會限制匯出的變數 (如果您使用模組資訊清單，請參閱 VariablesToExport 索引鍵。 ) 

- **Alias**：此參數會限制匯出的別名 (如果您使用模組資訊清單，請參閱 AliasesToExport 機碼。 ) 

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell 模組](./writing-a-windows-powershell-module.md)
