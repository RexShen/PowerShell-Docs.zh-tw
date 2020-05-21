---
title: 以批註為基礎的 Help 關鍵字 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab90ec96-77f5-42e3-9c7e-2f4156ec207f
caps.latest.revision: 6
ms.openlocfilehash: 3c5736be7066a749744482cb79edad2f53705f07
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564114"
---
# <a name="comment-based-help-keywords"></a>註解型說明關鍵字

本主題列出並描述以批註為基礎的說明中的關鍵字。

## <a name="keywords-in-comment-based-help"></a>以批註為基礎的說明中的關鍵字

下列是以批註為基礎的有效說明關鍵字。 它們會依照其一般出現在說明主題中的順序來列出，以及其預期的用途。 這些關鍵字可以依任何順序出現在以批註為基礎的說明中，而且不會區分大小寫。

請注意， `.ExternalHelp` 關鍵字的優先順序高於所有其他以批註為基礎的說明關鍵字。 當 `.ExternalHelp` 出現時， [GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) Cmdlet 不會顯示以批註為基礎的說明，即使找不到符合關鍵字值的說明檔也一樣。

`.Synopsis`函數或腳本的簡短描述。 這個關鍵字在每個主題中只能使用一次。

`.Description`函數或腳本的詳細描述。 這個關鍵字在每個主題中只能使用一次。

`.Parameter`* \< 參數-名稱>* 參數的描述。 您可以在函式 `.Parameter` 或腳本中包含每個參數的關鍵字。

`.Parameter`關鍵字可以依任何順序出現在批註區塊中，但參數出現在 `Param` 語句或函式宣告中的順序會決定參數出現在說明主題中的順序。 若要變更說明主題中參數的順序，請變更 `Param` 語句或函式宣告中參數的順序。

您也可以將批註放在 `Param` 參數變數名稱前面的語句中，以指定參數描述。 如果您同時使用 `Param` 語句批註和 `.Parameter` 關鍵字，則會使用與關鍵字相關聯的描述 `.Parameter` ，而 `Param` 語句批註會被忽略。

`.Example`使用函式或腳本的範例命令，選擇性地後面接著範例輸出和描述。 針對每個範例重複此關鍵字。

`.Inputs`Microsoft .NET Framework 類型的物件，可透過管道傳送至函式或腳本。 您也可以包含輸入物件的描述。

`.Outputs`Cmdlet 所傳回之物件的 .NET Framework 類型。 您也可以包含傳回之物件的描述。

`.Notes`函數或腳本的其他相關資訊。

`.Link`相關主題的名稱。 針對每個相關主題重複此關鍵字。 此內容會出現在說明主題的 [相關連結] 區段中。

`.Link`關鍵字內容也可以包含統一資源識別元（URI）至相同說明主題的線上版本。 當您使用 Get-help 的參數時，就會開啟線上版本 `Online` 。 URI 必須以 "HTTP" 或 "HTTPs" 開頭。

`.Component`函數或腳本所使用的技術或功能，或與其相關的功能。 當 Get-help 命令包含 Get-help 的參數時，就會顯示此內容 `Component` 。

`.Role`說明主題的使用者角色。 當 Get-help 命令包含 Get-help 的參數時，就會顯示此內容 `Role` 。

`.Functionality`函數的預期用法。 當 Get-help 命令包含 Get-help 的參數時，就會顯示此內容 `Functionality` 。

`.ForwardHelpTargetName`重新 `<Command-Name>` 導向至指定之命令的說明主題。 您可以將使用者重新導向至任何說明主題，包括功能、腳本、Cmdlet 或提供者的說明主題。

`.ForwardHelpCategory``<Category>`在 ForwardHelpTargetName 中指定專案的 [說明] 分類。 有效值為 Alias、Cmdlet、「提供者」、「函式」、「一般」、「常見問題」、「詞彙」、ScriptCommand、ExternalScript、「篩選」或「全部」。 使用此關鍵字可在有相同名稱的命令時，避免發生衝突。

`.RemoteHelpRunspace``<PSSession-variable>`指定包含說明主題的會話。 輸入包含 PSSession 的變數。 Cmdlet 會使用這個關鍵字 `Export-PSSession` 來尋找已匯出命令的說明主題。

`.ExternalHelp``<XML Help File>`指定腳本或函式之 XML 架構說明檔的路徑和（或）名稱。

`.ExternalHelp`關鍵字會告知[GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) Cmdlet，以在 XML 檔案中取得腳本或函式的說明。 **。** 針對腳本或函式使用以 XML 為基礎的說明檔時，需要 .externalhelp 關鍵字。 若沒有此功能，將找不到函式或腳本的說明檔 `Get-Help` 。

`.ExternalHelp`關鍵字優先于其他所有以批註為基礎的說明關鍵字。 當 `.ExternalHelp` 出現時， [GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) Cmdlet 不會顯示以批註為基礎的說明，即使找不到符合關鍵字值的說明檔也一樣。

當腳本模組匯出函數時，的值 `.ExternalHelp` 應該是不含路徑的檔案名。 `Get-Help`在模組目錄的地區設定特定子目錄中尋找檔案。 檔案名沒有任何需求，但最佳作法是使用下列檔案名格式： `<ScriptModule>.psm1-help.xml` 。

當函式未與模組相關聯時，請在的值中包含路徑和檔案名 **。.Externalhelp**關鍵字。 如果指定的 XML 檔案路徑包含 UI 文化特性特定的子目錄，則 `Get-Help` 會以遞迴方式使用腳本或函式的名稱來搜尋子目錄中的 xml 檔案，就如同所有以 XML 為基礎的說明主題一樣。

如需有關 Cmdlet 說明 XML 型說明檔案格式的詳細資訊，請參閱[撰寫 Windows PowerShell Cmdlet](./writing-help-for-windows-powershell-cmdlets.md)說明。
