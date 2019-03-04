---
title: 匯入 PowerShell 模組 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 697791b3-2135-4a39-b9d7-8566ed67acf2
caps.latest.revision: 13
ms.openlocfilehash: bb5d036e5658c365a4fafa2cac05c0bba9f87019
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854054"
---
# <a name="importing-a-powershell-module"></a>匯入 PowerShell 模組

一旦您已安裝模組的系統上，您可能想要匯入模組。 匯入到作用中的記憶體中，載入模組的處理序是使用者可以存取該模組在其 PowerShell 工作階段。 在 PowerShell 2.0 中，您可以匯入的新安裝 PowerShell 模組，藉由呼叫[Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet。 在 PowerShell 3.0 中，PowerShell 是能夠隱含地匯入模組，當使用者呼叫的其中一個函式或模組中的 cmdlet。 請注意，這兩個版本會假設您在 PowerShell 能夠找到; 它的位置安裝模組如需詳細資訊，請參閱 <<c0> [ 安裝 PowerShell 模組](./installing-a-powershell-module.md)。 您可以使用模組資訊清單來限制會匯出模組的哪些部分，以及您可以使用參數的`Import-Module`限制哪些部分會匯入的呼叫。

## <a name="importing-a-snap-in-powershell-10"></a>匯入嵌入式管理單元 (PowerShell 1.0)

模組不存在於 PowerShell 1.0： 因此，您必須註冊並使用嵌入式管理單元。不過，不建議您到目前為止，使用這項技術通常更容易安裝並匯入模組時。 如需詳細資訊，請參閱 <<c0> [ 如何建立 Windows PowerShell 嵌入式管理單元](../cmdlet/how-to-create-a-windows-powershell-snap-in.md)。

## <a name="importing-a-module-with-import-module-powershell-20"></a>匯入模組匯入模組 (PowerShell 2.0)

PowerShell 2.0 會使用適當命名[Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet 匯入模組。 Windows PowerShell 執行這個指令程式時，搜尋指定的模組中指定的目錄內`PSModulePath`變數。 找到指定的目錄時，Windows PowerShell 會搜尋以下列順序的檔案： 模組資訊清單檔案 (.psd1) 指令碼模組檔案 (.psm1) 二進位模組檔案 (.dll)。 如需有關如何將目錄新增至搜尋的詳細資訊，請參閱[修改 PSModulePath 安裝路徑](./modifying-the-psmodulepath-installation-path.md)。 下列程式碼說明如何匯入模組：

```powershell
Import-Module myModule
```

假設位於 myModule `PSModulePath`，PowerShell 會將 myModule 載入至使用中記憶體。 如果並非位於 myModule`PSModulePath`路徑，您可能仍會明確告訴 PowerShell 哪裡可以找到它：

```powershell
Import-Module -Name C:\myRandomDirectory\myModule -Verbose
```

您也可以使用-verbose 參數來識別哪些模組，從正在匯出和項目已匯入使用中記憶體。 匯出和匯入限制公開給使用者： 不同的是誰控制可見性。 基本上，匯出由模組內的程式碼所控制。 相反地，匯入所控制的`Import-Module`呼叫。 如需詳細資訊，請參閱 <<c0>  **限制，會匯入成員**底下。

## <a name="implicitly-importing-a-module-powershell-30"></a>隱含匯入模組 (PowerShell 3.0)

從 Windows PowerShell 3.0 開始，模組會自動匯入命令中使用任何 cmdlet 或在模組中的函式時。 此功能適用於此值中包含的目錄中的任何模組**PSModulePath**環境變數。 如果您沒有儲存您的模組上有效的路徑。 不過，您可以仍然載入使用明確[Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module)上面所述的選項。

下列動作會觸發自動匯入模組時，也稱為 「 模組自動載入。 」

- 在命令中使用 cmdlet。 例如，輸入`Get-ExecutionPolicy`包含將 Microsoft.PowerShell.Security 模組匯入`Get-ExecutionPolicy`cmdlet。

- 使用[Get-command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet 來取得命令。  例如，輸入`Get-Command Get-JobTrigger`匯入**PSScheduledJob**包含的模組`Get-JobTrigger`cmdlet。 A`Get-Command`包含萬用字元的命令會被視為探索，並不會觸發模組的匯入。

- 使用[Get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet 來取得 cmdlet 的說明。 例如，輸入`Get-Help Get-WinEvent`匯入包含 Microsoft.PowerShell.Diagnostics 模組`Get-WinEvent`cmdlet。

若要支援自動匯入模組， `Get-Command` cmdlet 會取得所有 cmdlet 和函式中所有已安裝的模組，即使模組不會匯入工作階段。 如需詳細資訊，請參閱 [說明] 主題[Get-command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet。

## <a name="the-importing-process"></a>匯入程序

匯入模組時，建立新的工作階段狀態模組，以及[System.Management.Automation.PSModuleInfo](/dotnet/api/System.Management.Automation.PSModuleInfo)在記憶體中建立物件。 匯入的每個模組建立工作階段狀態 （包括根模組和任何巢狀的模組）。 成員，從根模組，包括匯出根模組使用的任何巢狀模組中，任何成員匯出然後匯入呼叫者工作階段狀態。

從模組匯出的成員的中繼資料具有模組名稱屬性。 這個屬性會填入匯出它們的模組名稱。

> [!WARNING]
> 如果匯出的成員名稱使用未核准的動詞，或是如果成員名稱使用限制的字元，則會顯示警告時[Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module)執行 cmdlet。

根據預設， [Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet 不會傳回任何物件到管線。 不過，此 cmdlet 支援`PassThru`可以用來傳回的參數[System.Management.Automation.PSModuleInfo](/dotnet/api/System.Management.Automation.PSModuleInfo)匯入的每個模組的物件。 若要將輸出傳送至主應用程式中，使用者應該執行[Write-host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet。

## <a name="restricting--the-members-that-are-imported"></a>限制會匯入的成員

當使用匯入模組[Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet，根據預設，所有匯出的模組成員匯入工作階段，包括任何命令匯出至巢狀模組的模組。 根據預設，變數和別名不會匯出。 若要限制匯出的成員，請使用[模組資訊清單](./how-to-write-a-powershell-module-manifest.md)。 若要限制匯入的成員，請使用下列參數的`Import-Module`cmdlet。

- `Function`:此參數會限制匯出的函式。 （如果您使用模組資訊清單，請參閱 FunctionsToExport 索引鍵）。

- `Cmdlet`:此參數會限制 （如果您使用模組資訊清單，請參閱 CmdletsToExport 索引鍵。） 匯出的 cmdlet

- `Variable`:此參數會限制 （如果您使用模組資訊清單，請參閱 VariablesToExport 索引鍵。） 匯出的變數

- `Alias`:此參數會限制 （如果您使用模組資訊清單，請參閱 AliasesToExport 索引鍵。） 匯出的別名

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell 模組](./writing-a-windows-powershell-module.md)
