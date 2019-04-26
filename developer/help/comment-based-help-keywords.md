---
title: 註解型說明關鍵字 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab90ec96-77f5-42e3-9c7e-2f4156ec207f
caps.latest.revision: 6
ms.openlocfilehash: af8a151070d26ffe236800076115c964f625e572
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083530"
---
# <a name="comment-based-help-keywords"></a>註解型說明關鍵字

本主題列出並描述註解型說明中的關鍵字。

## <a name="keywords-in-comment-based-help"></a>註解型說明中的關鍵字

以下是有效的註解型說明關鍵字。 它們會列在通常出現以及其預定的使用說明主題中的順序。 這些關鍵字可以出現在註解型說明中，依任何順序並不會區分大小寫。

請注意，`.ExternalHelp`關鍵字的優先順序高於所有其他註解型說明關鍵字。 當`.ExternalHelp`存在， [Microsoft.PowerShell.Commands.Get 說明](/dotnet/api/Microsoft.PowerShell.Commands.Get-Help)cmdlet 不會顯示註解型說明，即使找不到說明檔符合關鍵字的值。

`.Synopsis` 函式或指令碼的簡短描述。 這個關鍵字可以使用每個主題中的僅一次。

`.Description` 函式或指令碼的詳細的描述。 這個關鍵字可以使用每個主題中的僅一次。

`.Parameter` *\<參數名稱 >* 參數的描述。 您可以包含`.Parameter`函式或指令碼中每個參數的關鍵字。

`.Parameter`關鍵字可以出現在註解區塊中，依任何順序，但參數中出現的順序`Param`陳述式或函式宣告會決定參數出現在 [說明] 主題中的順序。 若要變更之說明主題中的參數的順序，變更參數的順序`Param`陳述式或函式宣告。

您也可以藉由將放在註解指定參數描述`Param`之前參數的變數名稱的陳述式。 如果您同時使用`Param`陳述式的註解和`.Parameter`關鍵字，描述相關聯`.Parameter`使用關鍵字，而`Param`陳述式的註解會被忽略。

`.Example` 使用函式或指令碼，並且選擇性地加範例輸出和描述的範例命令。 針對每個範例中重複此關鍵字。

`.Inputs` Microsoft.NET Framework 的類型可以使用管線傳送至函式或指令碼的物件。 您也可以包含輸入物件的描述。

`.Outputs` 此 cmdlet 會傳回物件的.NET Framework 型別。 您也可以包含傳回的物件的描述。

`.Notes` 其他資訊的函式或指令碼的詳細資訊。

`.Link` 相關主題的名稱。 重複此關鍵字，針對每個相關的主題。 此內容會出現在 說明 主題的相關連結 區段中。

`.Link`關鍵字內容也可以包含統一資源識別元 (URI)，以相同的 [說明] 主題的線上版本。 當您使用時，會開啟線上版本`Online`Get-help 的參數。 URI 必須以"http"或"https"開頭。

`.Component` 技術或函式或指令碼使用，或與其相關的功能。 Get-help 命令包含時會顯示此內容`Component`Get-help 的參數。

`.Role` 說明主題的 「 使用者角色。 Get-help 命令包含時會顯示此內容`Role`Get-help 的參數。

`.Functionality` 想要的使用的函式。 Get-help 命令包含時會顯示此內容`Functionality`Get-help 的參數。

`.ForwardHelpTargetName` `<Command-Name>` 重新導向至指定的命令之說明主題。 您可以將使用者重新導向至任何說明主題，包括函式、 指令碼、 cmdlet 或提供者的說明主題。

`.ForwardHelpCategory` `<Category>` 指定項目的說明類別 ForwardHelpTargetName 中。 有效值為別名、 Cmdlet、 HelpFile、 函式、 提供者、 一般、 常見問題集、 字彙、 指令碼命令、 ExternalScript、 篩選或所有。 使用此關鍵字，以避免發生衝突，當有同名的命令。

`.RemoteHelpRunspace` `<PSSession-variable>` 指定包含 [說明] 主題的工作階段。 輸入包含 PSSession 的變數。 這個關鍵字由`Export-PSSession`cmdlet 來尋找匯出的命令中的 [說明] 主題。

`.ExternalHelp` `<XML Help File>` 指定的路徑及/或指令碼或函式以 XML 為基礎的說明檔的名稱。

`.ExternalHelp`關鍵字會指示[Microsoft.PowerShell.Commands.Get 說明](/dotnet/api/Microsoft.PowerShell.Commands.Get-Help)cmdlet 來取得的指令碼或函式的說明，以 XML 為基礎的檔案中。 **。ExternalHelp**關鍵字時，必須使用以 XML 為基礎的說明檔案的指令碼或函式。 否則，`Get-Help`會不到函式或指令碼的說明檔。

`.ExternalHelp`關鍵字的優先順序高於所有其他註解型說明關鍵字。 當`.ExternalHelp`存在， [Microsoft.PowerShell.Commands.Get 說明](/dotnet/api/Microsoft.PowerShell.Commands.Get-Help)cmdlet 不會顯示註解型說明，即使找不到說明檔符合關鍵字的值。

當匯出指令碼模組，值的函式`.ExternalHelp`應該是不具路徑的檔案名稱。 `Get-Help` 會尋找在模組目錄的地區設定特定子目錄中的檔案。 沒有任何需求，檔案名稱，但最佳做法是使用下列的檔案名稱格式： `<ScriptModule>.psm1-help.xml`。

不與模組相關聯函式時，包含路徑和檔案名稱的值中 **。ExternalHelp**關鍵字。 如果指定的 XML 檔案的路徑包含 UI 文化特性專屬子目錄`Get-Help`XML 檔案的指令碼或根據為建立標準後援語言的函式名稱的子目錄以遞迴方式搜尋Windows，因為它會為所有以 XML 為基礎的說明主題。

如需 cmdlet 的說明 XML 為基礎的說明檔案格式的詳細資訊，請參閱[撰寫 Windows PowerShell 指令程式說明](./writing-help-for-windows-powershell-cmdlets.md)。