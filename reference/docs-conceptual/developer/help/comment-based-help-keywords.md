---
ms.date: 06/09/2020
ms.topic: reference
title: 註解型說明關鍵字
description: 註解型說明關鍵字
ms.openlocfilehash: d87dde8700813767f6c09cfce70ed06c7964ebc7
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645465"
---
# <a name="comment-based-help-keywords"></a>註解型說明關鍵字

本主題會列出並描述以批註為基礎的說明中的關鍵字。

## <a name="keywords-in-comment-based-help"></a>Comment-Based 說明中的關鍵字

以下是以批註為基礎的有效說明關鍵字。 這些清單會依照它們一般出現在說明主題中的順序列出，以及其預期的用途。 這些關鍵字在批註式說明中可依任何順序出現，而且不區分大小寫。

請注意， `.EXTERNALHELP` 關鍵字優先于所有其他以批註為基礎的說明關鍵字。
當 `.EXTERNALHELP` 出現時， [GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) Cmdlet 不會顯示以批註為基礎的說明，即使找不到符合關鍵字值的說明檔也是如此。

## <a name="synopsis"></a>.簡介

函數或腳本的簡短描述。 在每個主題中，這個關鍵字只能使用一次。

## <a name="description"></a>.描述

函數或腳本的詳細描述。 在每個主題中，這個關鍵字只能使用一次。

## <a name="parameter-parameter-name"></a>.參數 \<Parameter-Name>

參數的描述。 您可以 `.PARAMETER` 針對函數或腳本中的每個參數包含關鍵字。

`.PARAMETER`關鍵字可以依任何順序出現在批註區塊中，但參數出現在 `Param` 語句或函式宣告中的順序會決定參數在說明主題中的出現順序。 若要變更說明主題中參數的順序，請變更 `Param` 語句或函式宣告中參數的順序。

您也可以將批註放在 `Param` 參數變數名稱之前的語句中，以指定參數描述。 如果您同時使用 `Param` 語句批註和 `.PARAMETER` 關鍵字，則會使用與關鍵字相關聯的描述 `.PARAMETER` ，而 `Param` 語句批註會被忽略。

## <a name="example"></a>.例子

使用函數或腳本的範例命令，選擇性地接著範例輸出和描述。 針對每個範例重複此關鍵字。

## <a name="inputs"></a>.輸入

Microsoft .NET Framework 可輸送至函式或腳本的物件類型。 您也可以包含輸入物件的描述。

## <a name="outputs"></a>.輸出

Cmdlet 傳回之物件的 .NET Framework 類型。 您也可以包含所傳回物件的描述。

## <a name="notes"></a>.筆記

函數或腳本的其他相關資訊。

## <a name="link"></a>.連結

相關主題的名稱。 針對每個相關主題重複此關鍵字。 此內容會顯示在說明主題的 [相關連結] 區段中。

`.LINK`關鍵字內容也可以包含統一資源識別項 (URI) 至相同說明主題的線上版本。 當您使用的參數時，就會開啟線上版本 `Online` `Get-Help` 。 URI 的開頭必須是 "HTTP" 或 "HTTPs"。

## <a name="component"></a>.元件

函數或腳本所使用的技術或功能名稱，或其相關的名稱。
的 **元件** 參數會 `Get-Help` 使用這個值來篩選所傳回的搜尋結果 `Get-Help` 。

## <a name="role"></a>.作用

說明主題的使用者角色名稱。 的 **Role** 參數會 `Get-Help` 使用這個值來篩選所傳回的搜尋結果 `Get-Help` 。

## <a name="functionality"></a>.功能

描述函式用途的關鍵字。 的 **功能** 參數會 `Get-Help` 使用這個值來篩選所傳回的搜尋結果 `Get-Help` 。

## <a name="forwardhelptargetname-command-name"></a>.FORWARDHELPTARGETNAME \<Command-Name>

重新導向至指定命令的說明主題。 您可以將使用者重新導向至任何說明主題，包括函數、腳本、Cmdlet 或提供者的說明主題。

## <a name="forwardhelpcategory-category"></a>.FORWARDHELPCATEGORY \<Category>

指定中專案的 [說明] 類別 `.FORWARDHELPTARGETNAME` 。 使用這個關鍵字可避免在具有相同名稱的命令時產生衝突。

有效值為：

- Alias
- Cmdlet
- HelpFile
- 函式
- 提供者
- 一般
- 常見問題集
- 詞彙
- ScriptCommand
- ExternalScript
- 篩選
- 全部

## <a name="remotehelprunspace-pssession-variable"></a>.REMOTEHELPRUNSPACE \<PSSession-variable>

指定包含說明主題的會話。 輸入包含 PSSession 的變數。 Cmdlet 會使用這個關鍵字 `Export-PSSession` 來尋找匯出命令的說明主題。

## <a name="externalhelp-xml-help-file"></a>..EXTERNALHELP \<XML Help File>

指定腳本或函式之 XML 架構說明檔的路徑和（或）名稱。

`.EXTERNALHELP`關鍵字會告訴[GetHelpCommand 指令](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand)程式，以取得以 XML 為基礎之檔案中的腳本或函數的說明。 `.EXTERNALHELP`針對腳本或函式使用以 XML 為基礎的說明檔時，需要關鍵字。 如果沒有它， `Get-Help` 就不會找到函數或腳本的說明檔。

`.EXTERNALHELP`關鍵字優先于所有其他以批註為基礎的說明關鍵字。 當 `.EXTERNALHELP` 出現時， [GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) Cmdlet 不會顯示以批註為基礎的說明，即使找不到符合關鍵字值的說明檔也是如此。

當腳本模組匯出函式時，的值 `.EXTERNALHELP` 應該是沒有路徑的檔案名。 `Get-Help` 在模組目錄的地區設定特定子目錄中尋找檔案。 檔案名沒有任何需求，但最佳做法是使用下列檔案名格式： `<ScriptModule>.psm1-help.xml` 。

當函數未與模組相關聯時，請在關鍵字的值中包含路徑和檔案名 `.EXTERNALHELP` 。 如果 XML 檔案的指定路徑包含 UI 文化特性特定的子目錄，則 `Get-Help` 會以遞迴方式在子目錄中搜尋具有腳本或函式名稱的 xml 檔案，就像是針對所有以 XML 為基礎的說明主題所建立的語言回溯標準一樣。

如需有關 Cmdlet 說明 XML 架構說明檔格式的詳細資訊，請參閱 [撰寫 Windows PowerShell Cmdlet](./writing-help-for-windows-powershell-cmdlets.md)說明。
