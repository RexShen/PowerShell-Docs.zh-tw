---
title: 註解型說明關鍵字
ms.date: 06/09/2020
ms.openlocfilehash: fb737c19d7b7f4d003af3ba36bb396bac52d94e7
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893147"
---
# <a name="comment-based-help-keywords"></a>註解型說明關鍵字

本主題列出並描述以批註為基礎的說明中的關鍵字。

## <a name="keywords-in-comment-based-help"></a>以批註為基礎的說明中的關鍵字

下列是以批註為基礎的有效說明關鍵字。 它們會依照其一般出現在說明主題中的順序來列出，以及其預期的用途。 這些關鍵字可以依任何順序出現在以批註為基礎的說明中，而且不會區分大小寫。

請注意， `.EXTERNALHELP` 關鍵字的優先順序高於所有其他以批註為基礎的說明關鍵字。
當 `.EXTERNALHELP` 出現時， [GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) Cmdlet 不會顯示以批註為基礎的說明，即使找不到符合關鍵字值的說明檔也一樣。

## <a name="synopsis"></a>.摘要

函數或腳本的簡短描述。 這個關鍵字在每個主題中只能使用一次。

## <a name="description"></a>.描述

函數或腳本的詳細描述。 這個關鍵字在每個主題中只能使用一次。

## <a name="parameter-parameter-name"></a>.實參\<Parameter-Name>

參數的描述。 您可以在函式 `.PARAMETER` 或腳本中包含每個參數的關鍵字。

`.PARAMETER`關鍵字可以依任何順序出現在批註區塊中，但參數出現在 `Param` 語句或函式宣告中的順序會決定參數出現在說明主題中的順序。 若要變更說明主題中參數的順序，請變更 `Param` 語句或函式宣告中參數的順序。

您也可以將批註放在 `Param` 參數變數名稱前面的語句中，以指定參數描述。 如果您同時使用 `Param` 語句批註和 `.PARAMETER` 關鍵字，則會使用與關鍵字相關聯的描述 `.PARAMETER` ，而 `Param` 語句批註會被忽略。

## <a name="example"></a>.實例

使用函式或腳本的範例命令，選擇性地後面接著範例輸出和描述。 針對每個範例重複此關鍵字。

## <a name="inputs"></a>.輸入

Microsoft .NET Framework 類型的物件，可透過管道傳送至函式或腳本。 您也可以包含輸入物件的描述。

## <a name="outputs"></a>.產出

Cmdlet 所傳回之物件的 .NET Framework 類型。 您也可以包含傳回之物件的描述。

## <a name="notes"></a>.紀錄

函數或腳本的其他相關資訊。

## <a name="link"></a>.LINK

相關主題的名稱。 針對每個相關主題重複此關鍵字。 此內容會出現在說明主題的 [相關連結] 區段中。

`.LINK`關鍵字內容也可以包含統一資源識別元（URI）至相同說明主題的線上版本。 當您使用的參數時，就會開啟線上版本 `Online` `Get-Help` 。 URI 必須以 "HTTP" 或 "HTTPs" 開頭。

## <a name="component"></a>.成分

函式或腳本所使用的技術或功能名稱，或其相關的。
的**元件**參數會 `Get-Help` 使用這個值來篩選所傳回的搜尋結果 `Get-Help` 。

## <a name="role"></a>.角色

說明主題的使用者角色名稱。 的**Role**參數會 `Get-Help` 使用這個值來篩選所傳回的搜尋結果 `Get-Help` 。

## <a name="functionality"></a>.功能

描述函數用途的關鍵字。 的**功能**參數會 `Get-Help` 使用這個值來篩選所傳回的搜尋結果 `Get-Help` 。

## <a name="forwardhelptargetname-command-name"></a>.FORWARDHELPTARGETNAME\<Command-Name>

重新導向至指定之命令的說明主題。 您可以將使用者重新導向至任何說明主題，包括功能、腳本、Cmdlet 或提供者的說明主題。

## <a name="forwardhelpcategory-category"></a>.FORWARDHELPCATEGORY\<Category>

指定中專案的 [說明] 分類 `.FORWARDHELPTARGETNAME` 。 使用此關鍵字可在有相同名稱的命令時，避免發生衝突。

有效值為：

- Alias
- Cmdlet
- HelpFile
- 函式
- 提供者
- 一般
- 常見問題集
- 字彙表
- ScriptCommand
- ExternalScript
- Filter
- 全部

## <a name="remotehelprunspace-pssession-variable"></a>.REMOTEHELPRUNSPACE\<PSSession-variable>

指定包含說明主題的會話。 輸入包含 PSSession 的變數。 Cmdlet 會使用這個關鍵字 `Export-PSSession` 來尋找已匯出命令的說明主題。

## <a name="externalhelp-xml-help-file"></a>..EXTERNALHELP\<XML Help File>

指定腳本或函式之 XML 架構說明檔的路徑和（或）名稱。

`.EXTERNALHELP`關鍵字會告知[GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) Cmdlet，以在 XML 檔案中取得腳本或函式的說明。 `.EXTERNALHELP`使用腳本或函式的 XML 說明檔時，需要關鍵字。 若沒有此功能，將找不到函式或腳本的說明檔 `Get-Help` 。

`.EXTERNALHELP`關鍵字優先于其他所有以批註為基礎的說明關鍵字。 當 `.EXTERNALHELP` 出現時， [GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) Cmdlet 不會顯示以批註為基礎的說明，即使找不到符合關鍵字值的說明檔也一樣。

當腳本模組匯出函數時，的值 `.EXTERNALHELP` 應該是不含路徑的檔案名。 `Get-Help`在模組目錄的地區設定特定子目錄中尋找檔案。 檔案名沒有任何需求，但最佳作法是使用下列檔案名格式： `<ScriptModule>.psm1-help.xml` 。

當函式未與模組相關聯時，請在關鍵字的值中包含路徑和檔案名 `.EXTERNALHELP` 。 如果指定的 XML 檔案路徑包含 UI 文化特性特定的子目錄，則 `Get-Help` 會以遞迴方式使用腳本或函式的名稱來搜尋子目錄中的 xml 檔案，就如同所有以 XML 為基礎的說明主題一樣。

如需有關 Cmdlet 說明 XML 型說明檔案格式的詳細資訊，請參閱[撰寫 Windows PowerShell Cmdlet](./writing-help-for-windows-powershell-cmdlets.md)說明。
